# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      133.96 s  →      128.79 s    (-3.86%) |       1   →       1              |      133.96 s  →      128.79 s    (-3.86%) | 
  ├ sirius::initialize                                                  |        2.73 s  →        2.73 s    (-0.26%) |       1   →       1              |        2.73 s  →        2.73 s    (-0.26%) | 
  ├ sirius::Simulation_context::initialize                              |        3.04 s  →        2.94 s    (-3.16%) |       1   →       1              |        3.04 s  →        2.94 s    (-3.16%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       91.71 ms →       22.72 ms  (-75.22%) |       1   →       1              |       91.71 ms →       22.72 ms  (-75.22%) | 
  │ ├ sirius::Unit_cell::initialize                                     |      183.01 ms →      193.80 ms   (+5.90%) |       1   →       1              |      183.01 ms →      193.80 ms   (+5.90%) | 
  │ │ ├ sirius::Atom_type::init                                         |       79.19 ms →       84.35 ms   (+6.51%) |       2   →       2              |      158.39 ms →      168.70 ms   (+6.51%) | 
  │ │ └ sirius::Unit_cell::update                                       |       24.54 ms →       25.02 ms   (+1.95%) |       1   →       1              |       24.54 ms →       25.02 ms   (+1.95%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.27 ms →        6.27 ms   (+0.02%) |       1   →       1              |        6.27 ms →        6.27 ms   (+0.02%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       18.23 ms →       18.71 ms   (+2.65%) |       1   →       1              |       18.23 ms →       18.71 ms   (+2.65%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       18.21 ms →       18.69 ms   (+2.65%) |       1   →       1              |       18.21 ms →       18.69 ms   (+2.65%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.17 ms →        4.15 ms   (-0.30%) |       1   →       1              |        4.17 ms →        4.15 ms   (-0.30%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.34 ms   (+0.73%) |       1   →       1              |        2.32 ms →        2.34 ms   (+0.73%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      100.74 μs →      102.32 μs   (+1.57%) |       1   →       1              |      100.74 μs →      102.32 μs   (+1.57%) | 
  │ └ sirius::Simulation_context::update                                |        2.72 s  →        2.68 s    (-1.39%) |       1   →       1              |        2.72 s  →        2.68 s    (-1.39%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.89 ms →       10.91 ms   (+0.19%) |       1   →       1              |       10.89 ms →       10.91 ms   (+0.19%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.43 ms →        4.47 ms   (+0.79%) |       1   →       1              |        4.43 ms →        4.47 ms   (+0.79%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.42 ms →        6.41 ms   (-0.20%) |       1   →       1              |        6.42 ms →        6.41 ms   (-0.20%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.40 ms →        6.39 ms   (-0.12%) |       1   →       1              |        6.40 ms →        6.39 ms   (-0.12%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.90 ms →        3.89 ms   (-0.44%) |       1   →       1              |        3.90 ms →        3.89 ms   (-0.44%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.33 ms   (-0.01%) |       1   →       1              |        2.33 ms →        2.33 ms   (-0.01%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      100.49 μs →       99.14 μs   (-1.34%) |       1   →       1              |      100.49 μs →       99.14 μs   (-1.34%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       62.78 ms →       64.60 ms   (+2.90%) |       2   →       2              |      125.55 ms →      129.19 ms   (+2.90%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.15 ms →        5.14 ms   (-0.09%) |       2   →       2              |       10.29 ms →       10.28 ms   (-0.09%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.49 ms →        4.63 ms   (+3.18%) |       1   →       1              |        4.49 ms →        4.63 ms   (+3.18%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.89 ms →       21.75 ms   (-0.65%) |       2   →       2              |       43.79 ms →       43.50 ms   (-0.65%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.88 ms →       15.07 ms   (+1.27%) |       2   →       2              |       29.77 ms →       30.14 ms   (+1.27%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.49 ms →       19.52 ms   (+0.13%) |       4   →       4              |       77.96 ms →       78.07 ms   (+0.13%) | 
  │   ├ sddk::Gvec::init                                                |      175.87 ms →      171.11 ms   (-2.71%) |       2   →       2              |      351.75 ms →      342.22 ms   (-2.71%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      133.35 ms →      128.66 ms   (-3.52%) |       2   →       2              |      266.69 ms →      257.32 ms   (-3.52%) | 
  │   ├ sddk::Gvec_shells                                               |      172.80 ms →      166.14 ms   (-3.85%) |       1   →       1              |      172.80 ms →      166.14 ms   (-3.85%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.31 ms →        1.33 ms   (+0.83%) |       1   →       1              |        1.31 ms →        1.33 ms   (+0.83%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      297.22 ms →      292.94 ms   (-1.44%) |       2   →       2              |      594.43 ms →      585.87 ms   (-1.44%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       36.39 ms →       35.52 ms   (-2.40%) |       1   →       1              |       36.39 ms →       35.52 ms   (-2.40%) | 
+ │ ├ sirius::K_point::K_point                                          |        2.23 μs →        1.93 μs  (-13.54%) |       4   →       4              |        8.92 μs →        7.71 μs  (-13.54%) | 
  │ └ sirius::K_point_set::initialize                                   |       36.30 ms →       35.42 ms   (-2.41%) |       1   →       1              |       36.30 ms →       35.42 ms   (-2.41%) | 
  │   └ sirius::K_point::initialize                                     |       36.21 ms →       35.32 ms   (-2.45%) |       1   →       1              |       36.21 ms →       35.32 ms   (-2.45%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       18.86 ms →       18.05 ms   (-4.30%) |       1   →       1              |       18.86 ms →       18.05 ms   (-4.30%) | 
  │     │ └ sddk::Gvec::init                                            |        8.03 ms →        8.10 ms   (+0.76%) |       1   →       1              |        8.03 ms →        8.10 ms   (+0.76%) | 
- │     ├ sddk::matrix_storage::matrix_storage                          |        9.11 μs →       10.24 μs  (+12.38%) |       1   →       1              |        9.11 μs →       10.24 μs  (+12.38%) | 
  │     └ sirius::K_point::update                                       |       12.56 ms →       12.48 ms   (-0.66%) |       1   →       1              |       12.56 ms →       12.48 ms   (-0.66%) | 
  │       └ sirius::Beta_projectors                                     |        6.28 ms →        6.22 ms   (-0.85%) |       1   →       1              |        6.28 ms →        6.22 ms   (-0.85%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.67 ms →        3.60 ms   (-2.03%) |       1   →       1              |        3.67 ms →        3.60 ms   (-2.03%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.23 ms →        5.29 ms   (+1.11%) |       2   →       2              |       10.46 ms →       10.58 ms   (+1.11%) | 
  ├ sirius::Potential                                                   |      159.09 ms →      155.40 ms   (-2.32%) |       1   →       1              |      159.09 ms →      155.40 ms   (-2.32%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.82 ms →        5.88 ms   (+0.98%) |       6   →       6              |       34.95 ms →       35.29 ms   (+0.98%) | 
  │ └ sirius::Potential::update                                         |      123.43 ms →      119.37 ms   (-3.29%) |       1   →       1              |      123.43 ms →      119.37 ms   (-3.29%) | 
  │   └ sirius::Potential::generate_local_potential                     |      122.75 ms →      118.67 ms   (-3.33%) |       1   →       1              |      122.75 ms →      118.67 ms   (-3.33%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      114.70 ms →      111.12 ms   (-3.12%) |       1   →       1              |      114.70 ms →      111.12 ms   (-3.12%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        7.18 ms →        6.65 ms   (-7.39%) |       1   →       1              |        7.18 ms →        6.65 ms   (-7.39%) | 
  ├ sirius::Density                                                     |      135.27 ms →      130.37 ms   (-3.62%) |       1   →       1              |      135.27 ms →      130.37 ms   (-3.62%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.22 ms →        5.14 ms   (-1.50%) |       2   →       2              |       10.44 ms →       10.28 ms   (-1.50%) | 
  │ └ sirius::Density::update                                           |      124.56 ms →      119.82 ms   (-3.81%) |       1   →       1              |      124.56 ms →      119.82 ms   (-3.81%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      124.16 ms →      119.36 ms   (-3.87%) |       1   →       1              |      124.16 ms →      119.36 ms   (-3.87%) | 
- │     ├ sirius::rho_core_ri_pseudo|values                             |      102.85 μs →      118.15 μs  (+14.88%) |       1   →       1              |      102.85 μs →      118.15 μs  (+14.88%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      118.17 ms →      112.51 ms   (-4.78%) |       1   →       1              |      118.17 ms →      112.51 ms   (-4.78%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        5.44 ms →        6.27 ms  (+15.33%) |       1   →       1              |        5.44 ms →        6.27 ms  (+15.33%) | 
  ├ sirius::Density::initial_density                                    |      175.38 ms →      166.28 ms   (-5.19%) |       1   →       1              |      175.38 ms →      166.28 ms   (-5.19%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      123.05 ms →      110.97 ms   (-9.81%) |       1   →       1              |      123.05 ms →      110.97 ms   (-9.81%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.83 ms →        5.49 ms  (+13.79%) |       2   →       2              |        9.65 ms →       10.98 ms  (+13.79%) | 
- │ └ sirius::Periodic_function::integrate                              |        9.73 ms →       11.76 ms  (+20.82%) |       1   →       1              |        9.73 ms →       11.76 ms  (+20.82%) | 
  ├ sirius::Potential::generate                                         |      592.24 ms →      584.79 ms   (-1.26%) |       1   →       1              |      592.24 ms →      584.79 ms   (-1.26%) | 
  │ ├ sirius::Potential::poisson                                        |      137.12 ms →      127.03 ms   (-7.36%) |       1   →       1              |      137.12 ms →      127.03 ms   (-7.36%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.21 ms →        6.03 ms  (+15.69%) |       1   →       1              |        5.21 ms →        6.03 ms  (+15.69%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.35 ms →       10.09 ms   (-2.53%) |       1   →       1              |       10.35 ms →       10.09 ms   (-2.53%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |       10.33 ms →        9.82 ms   (-4.97%) |       1   →       1              |       10.33 ms →        9.82 ms   (-4.97%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |       10.33 ms →        9.81 ms   (-4.98%) |       1   →       1              |       10.33 ms →        9.81 ms   (-4.98%) | 
  │ ├ sirius::Periodic_function::add                                    |      567.59 μs →      569.58 μs   (+0.35%) |       2   →       2              |        1.14 ms →        1.14 ms   (+0.35%) | 
  │ ├ sirius::Potential::xc                                             |       53.92 ms →       56.12 ms   (+4.08%) |       1   →       1              |       53.92 ms →       56.12 ms   (+4.08%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.60 ms →       53.80 ms   (+4.26%) |       1   →       1              |       51.60 ms →       53.80 ms   (+4.26%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.68 ms →        5.72 ms   (+0.77%) |       2   →       2              |       11.35 ms →       11.44 ms   (+0.77%) | 
- │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.36 ms →        6.02 ms  (+12.33%) |       1   →       1              |        5.36 ms →        6.02 ms  (+12.33%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.81 ms →        5.74 ms   (-1.12%) |       1   →       1              |        5.81 ms →        5.74 ms   (-1.12%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.69 ms →       93.97 ms   (+1.37%) |       1   →       1              |       92.69 ms →       93.97 ms   (+1.37%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      300.19 ms →      299.39 ms   (-0.27%) |       1   →       1              |      300.19 ms →      299.39 ms   (-0.27%) | 
  ├ sirius::Hamiltonian0                                                |        8.47 ms →        8.40 ms   (-0.77%) |       1   →       1              |        8.47 ms →        8.40 ms   (-0.77%) | 
  │ ├ sirius::Local_operator                                            |        8.12 ms →        8.04 ms   (-1.01%) |       1   →       1              |        8.12 ms →        8.04 ms   (-1.01%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.73 ms →        4.78 ms   (+0.93%) |       1   →       1              |        4.73 ms →        4.78 ms   (+0.93%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.46 ms →        2.33 ms   (-5.48%) |       1   →       1              |        2.46 ms →        2.33 ms   (-5.48%) | 
  │ ├ sirius::Non_local_operator                                        |       62.70 μs →       63.01 μs   (+0.50%) |       2   →       2              |      125.40 μs →      126.03 μs   (+0.50%) | 
  │ ├ sirius::D_operator::initialize                                    |       92.30 μs →       99.83 μs   (+8.16%) |       1   →       1              |       92.30 μs →       99.83 μs   (+8.16%) | 
  │ └ sirius::Q_operator::initialize                                    |       74.54 μs →       79.44 μs   (+6.58%) |       1   →       1              |       74.54 μs →       79.44 μs   (+6.58%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.87 s  →        1.87 s    (-0.21%) |       1   →       1              |        1.87 s  →        1.87 s    (-0.21%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.70 ms →       18.11 ms   (-3.15%) |       1   →       1              |       18.70 ms →       18.11 ms   (-3.15%) | 
- │ │ ├ sirius::Local_operator::prepare_k                               |      189.14 μs →      210.29 μs  (+11.18%) |       1   →       1              |      189.14 μs →      210.29 μs  (+11.18%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       18.51 ms →       17.90 ms   (-3.30%) |       1   →       1              |       18.51 ms →       17.90 ms   (-3.30%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.86 s  →        1.85 s    (-0.18%) |       1   →       1              |        1.86 s  →        1.85 s    (-0.18%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      131.92 ms →      128.90 ms   (-2.29%) |       4   →       4              |      527.69 ms →      515.61 ms   (-2.29%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       52.96 ms →       52.87 ms   (-0.18%) |       1   →       1              |       52.96 ms →       52.87 ms   (-0.18%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.76 ms →       21.77 ms   (+0.03%) |       1   →       1              |       21.76 ms →       21.77 ms   (+0.03%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      638.59 ms →      645.25 ms   (+1.04%) |       1   →       1              |      638.59 ms →      645.25 ms   (+1.04%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      298.04 ms →      302.51 ms   (+1.50%) |       1   →       1              |      298.04 ms →      302.51 ms   (+1.50%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        2.79 μs →        3.26 μs  (+16.61%) |       1   →       1              |        2.79 μs →        3.26 μs  (+16.61%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        1.93 μs →        2.44 μs  (+26.62%) |       1   →       1              |        1.93 μs →        2.44 μs  (+26.62%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      360.00 ns →      325.00 ns   (-9.72%) |       1   →       1              |      360.00 ns →      325.00 ns   (-9.72%) | 
- │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      465.00 ns →      628.00 ns  (+35.05%) |       1   →       1              |      465.00 ns →      628.00 ns  (+35.05%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.22 ms →        9.23 ms   (+0.16%) |       1   →       1              |        9.22 ms →        9.23 ms   (+0.16%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      122.16 ms →      122.13 ms   (-0.02%) |       1   →       1              |      122.16 ms →      122.13 ms   (-0.02%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      104.57 ms →      105.67 ms   (+1.05%) |       2   →       2              |      209.13 ms →      211.34 ms   (+1.05%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       40.47 ms →       40.30 ms   (-0.41%) |       2   →       2              |       80.94 ms →       80.61 ms   (-0.41%) | 
  │ │ │ └ sddk::wf_inner                                                |       39.93 ms →       39.77 ms   (-0.42%) |       2   →       2              |       79.87 ms →       79.53 ms   (-0.42%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       19.50 ns →       36.00 ns  (+84.62%) |       2   →       2              |       39.00 ns →       72.00 ns  (+84.62%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       39.46 ms →       39.31 ms   (-0.38%) |       2   →       2              |       78.92 ms →       78.62 ms   (-0.38%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       15.50 ns →       23.00 ns  (+48.39%) |       2   →       2              |       31.00 ns →       46.00 ns  (+48.39%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       57.09 ms →       60.81 ms   (+6.51%) |       1   →       1              |       57.09 ms →       60.81 ms   (+6.51%) | 
  │ │ └ sddk::wf_trans                                                  |       30.76 ms →       30.74 ms   (-0.09%) |       1   →       1              |       30.76 ms →       30.74 ms   (-0.09%) | 
  │ │   └ sddk::wf_trans|pw                                             |       30.76 ms →       30.73 ms   (-0.09%) |       1   →       1              |       30.76 ms →       30.73 ms   (-0.09%) | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      519.00 ns →      525.00 ns   (+1.16%) |       1   →       1              |      519.00 ns →      525.00 ns   (+1.16%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      124.20 s  →      119.10 s    (-4.11%) |       1   →       1              |      124.20 s  →      119.10 s    (-4.11%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.81 ms →        5.77 ms   (-0.70%) |      19   →      19              |      110.32 ms →      109.55 ms   (-0.70%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.74 s  →        4.57 s    (-3.76%) |      26   →      26              |      123.33 s  →      118.69 s    (-3.76%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        4.68 ms →        4.84 ms   (+3.38%) |      26   →      26              |      121.71 ms →      125.83 ms   (+3.38%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.32 ms →        4.47 ms   (+3.60%) |      26   →      26              |      112.26 ms →      116.30 ms   (+3.60%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      927.12 μs →      935.75 μs   (+0.93%) |      26   →      26              |       24.11 ms →       24.33 ms   (+0.93%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.51 ms →        2.59 ms   (+3.28%) |      26   →      26              |       65.16 ms →       67.30 ms   (+3.28%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       65.01 μs →       65.02 μs   (+0.01%) |      52   →      52              |        3.38 ms →        3.38 ms   (+0.01%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       87.02 μs →       88.02 μs   (+1.14%) |      26   →      26              |        2.26 ms →        2.29 ms   (+1.14%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       77.64 μs →       78.79 μs   (+1.48%) |      26   →      26              |        2.02 ms →        2.05 ms   (+1.48%) | 
  │ │ ├ sirius::Band::solve                                             |        2.77 s  →        2.61 s    (-5.96%) |      26   →      26              |       72.09 s  →       67.79 s    (-5.96%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      154.97 μs →      156.47 μs   (+0.97%) |      26   →      26              |        4.03 ms →        4.07 ms   (+0.97%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      148.02 μs →      148.70 μs   (+0.46%) |      26   →      26              |        3.85 ms →        3.87 ms   (+0.46%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.00 μs →        5.82 μs  (+16.42%) |      26   →      26              |      129.96 μs →      151.31 μs  (+16.42%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.65 s  →        2.48 s    (-6.15%) |      26   →      26              |       68.82 s  →       64.59 s    (-6.15%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       95.89 ms →       95.48 ms   (-0.43%) |      26   →      26              |        2.49 s  →        2.48 s    (-0.43%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.86 ms →        7.75 ms   (-1.45%) |     156   →     156              |        1.23 s  →        1.21 s    (-1.45%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        5.93 ms →        5.91 ms   (-0.32%) |      26   →      26              |      154.08 ms →      153.59 ms   (-0.32%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      349.48 μs →      346.63 μs   (-0.82%) |      26   →      26              |        9.09 ms →        9.01 ms   (-0.82%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.31 ms →        2.31 ms   (-0.06%) |      52   →      52              |      120.08 ms →      120.00 ms   (-0.06%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.51 s  →        2.35 s    (-6.47%) |      26   →      26              |       65.24 s  →       61.02 s    (-6.47%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      128.68 ms →      137.98 ms   (+7.22%) |     277   →     262     (-5.42%) |       35.64 s  →       36.15 s    (+1.42%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       51.14 ms →       55.95 ms   (+9.40%) |     277   →     262     (-5.42%) |       14.17 s  →       14.66 s    (+3.48%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.00 μs →        2.07 μs   (+3.67%) |     277   →     262     (-5.42%) |      554.37 μs →      543.58 μs   (-1.95%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.71 μs →        1.77 μs   (+3.29%) |     277   →     262     (-5.42%) |      474.24 μs →      463.30 μs   (-2.31%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      435.19 ns →      428.35 ns   (-1.57%) |     277   →     262     (-5.42%) |      120.55 μs →      112.23 μs   (-6.90%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      464.55 ns →      499.00 ns   (+7.42%) |     277   →     262     (-5.42%) |      128.68 μs →      130.74 μs   (+1.60%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.42 ms →        7.45 ms   (+0.37%) |     277   →     262     (-5.42%) |        2.06 s  →        1.95 s    (-5.07%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       23.88 ms →       25.44 ms   (+6.54%) |     277   →     262     (-5.42%) |        6.62 s  →        6.67 s    (+0.77%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       23.11 ms →       24.56 ms   (+6.27%) |     554   →     524     (-5.42%) |       12.80 s  →       12.87 s    (+0.52%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       34.38 ms →       35.89 ms   (+4.40%) |     277   →     262     (-5.42%) |        9.52 s  →        9.40 s    (-1.26%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        5.98 ms →        6.23 ms   (+4.18%) |     528   →     498     (-5.68%) |        3.16 s  →        3.10 s    (-1.74%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       65.35 ns →       47.51 ns  (-27.30%) |     528   →     498     (-5.68%) |       34.51 μs →       23.66 μs  (-31.43%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        4.87 ms →        5.12 ms   (+5.17%) |     528   →     498     (-5.68%) |        2.57 s  →        2.55 s    (-0.81%) | 
+ │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       52.58 ns →       30.73 ns  (-41.56%) |     528   →     498     (-5.68%) |       27.76 μs →       15.30 μs  (-44.88%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      611.45 μs →      656.95 μs   (+7.44%) |     277   →     262     (-5.42%) |      169.37 ms →      172.12 ms   (+1.62%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        9.56 ms →       10.32 ms   (+7.91%) |     277   →     262     (-5.42%) |        2.65 s  →        2.70 s    (+2.06%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |       14.13 ms →       14.51 ms   (+2.69%) |     251   →     236     (-5.98%) |        3.55 s  →        3.42 s    (-3.45%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        4.71 ms →        4.84 ms   (+2.69%) |     753   →     708     (-5.98%) |        3.55 s  →        3.42 s    (-3.45%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       10.34 ms →       10.40 ms   (+0.60%) |     277   →     262     (-5.42%) |        2.86 s  →        2.73 s    (-4.84%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |       10.08 ms →       10.20 ms   (+1.24%) |     277   →     262     (-5.42%) |        2.79 s  →        2.67 s    (-4.24%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       44.42 ns →       28.78 ns  (-35.21%) |     277   →     262     (-5.42%) |       12.30 μs →        7.54 μs  (-38.72%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        8.96 ms →        9.09 ms   (+1.41%) |     277   →     262     (-5.42%) |        2.48 s  →        2.38 s    (-4.08%) | 
+ │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       85.40 ns →       57.85 ns  (-32.26%) |     277   →     262     (-5.42%) |       23.66 μs →       15.16 μs  (-35.93%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       34.68 ms →       18.52 ms  (-46.58%) |     277   →     262     (-5.42%) |        9.61 s  →        4.85 s   (-49.48%) | 
  │ │ │ │   ├ sirius::residuals                                         |       13.53 ms →       13.16 ms   (-2.70%) |     268   →     252     (-5.97%) |        3.62 s  →        3.32 s    (-8.51%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       12.16 ms →       11.74 ms   (-3.46%) |     259   →     242     (-6.56%) |        3.15 s  →        2.84 s    (-9.79%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        6.08 ms →        5.87 ms   (-3.46%) |     518   →     484     (-6.56%) |        3.15 s  →        2.84 s    (-9.79%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.60 ms →        1.71 ms   (+7.02%) |     259   →     242     (-6.56%) |      414.57 ms →      414.55 ms   (-0.01%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       74.97 ms →       53.75 ms  (-28.31%) |      53   →      85    (+60.38%) |        3.97 s  →        4.57 s   (+14.98%) | 
- │ │ │ │     └ sddk::wf_trans                                          |       49.44 ms →       31.47 ms  (-36.35%) |      80   →     144    (+80.00%) |        3.96 s  →        4.53 s   (+14.57%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |       36.96 ms →       22.32 ms  (-39.61%) |     107   →     203    (+89.72%) |        3.96 s  →        4.53 s   (+14.56%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      832.38 ns →      426.15 ns  (-48.80%) |      26   →      26              |       21.64 μs →       11.08 μs  (-48.80%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       34.63 μs →       43.10 μs  (+24.45%) |      26   →      26              |      900.39 μs →        1.12 ms  (+24.45%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      594.31 μs →      600.18 μs   (+0.99%) |      26   →      26              |       15.45 ms →       15.60 ms   (+0.99%) | 
  │ │ ├ sirius::Density::generate                                       |      774.95 ms →      772.20 ms   (-0.35%) |      26   →      26              |       20.15 s  →       20.08 s    (-0.35%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      401.92 ms →      402.49 ms   (+0.14%) |      26   →      26              |       10.45 s  →       10.46 s    (+0.14%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.28 μs →        8.58 μs   (+3.63%) |      26   →      26              |      215.35 μs →      223.16 μs   (+3.63%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.75 μs →        8.09 μs   (+4.31%) |      26   →      26              |      201.60 μs →      210.28 μs   (+4.31%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |      100.82 ms →      100.52 ms   (-0.30%) |      26   →      26              |        2.62 s  →        2.61 s    (-0.30%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.57 μs →        8.10 μs   (+6.96%) |      26   →      26              |      196.84 μs →      210.54 μs   (+6.96%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.12 ms →        7.12 ms   (-0.03%) |      26   →      26              |      185.13 ms →      185.07 ms   (-0.03%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       91.79 ms →       91.48 ms   (-0.34%) |      26   →      26              |        2.39 s  →        2.38 s    (-0.34%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      689.58 ns →      603.62 ns  (-12.47%) |      26   →      26              |       17.93 μs →       15.69 μs  (-12.47%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      162.54 ms →      163.73 ms   (+0.73%) |      26   →      26              |        4.23 s  →        4.26 s    (+0.73%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.63 ms →        1.64 ms   (+0.59%) |      26   →      26              |       42.39 ms →       42.64 ms   (+0.59%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.28 ms →       88.25 ms   (-0.04%) |      26   →      26              |        2.30 s  →        2.29 s    (-0.04%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.03 ms →       88.01 ms   (-0.03%) |      26   →      26              |        2.29 s  →        2.29 s    (-0.03%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      274.21 ms →      273.38 ms   (-0.31%) |      26   →      26              |        7.13 s  →        7.11 s    (-0.31%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      274.21 ms →      273.38 ms   (-0.31%) |      26   →      26              |        7.13 s  →        7.11 s    (-0.31%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.34 ms →       24.46 ms   (+0.50%) |      26   →      26              |      632.92 ms →      636.08 ms   (+0.50%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      225.55 ms →      224.81 ms   (-0.33%) |      26   →      26              |        5.86 s  →        5.84 s    (-0.33%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       23.16 ms →       22.92 ms   (-1.02%) |      26   →      26              |      602.14 ms →      596.02 ms   (-1.02%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       89.48 ms →       80.61 ms   (-9.91%) |      26   →      26              |        2.33 s  →        2.10 s    (-9.91%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        5.75 ms →       12.07 ms (+110.14%) |      26   →      26              |      149.40 ms →      313.94 ms (+110.14%) | 
  │ │ ├ sirius::Density::mix                                            |      217.15 ms →      213.66 ms   (-1.61%) |      26   →      26              |        5.65 s  →        5.56 s    (-1.61%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      948.63 μs →      962.17 μs   (+1.43%) |      26   →      26              |       24.66 ms →       25.02 ms   (+1.43%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.66 ms →       10.37 ms   (-2.69%) |     334   →     334              |        3.56 s  →        3.46 s    (-2.69%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.35 ms →        9.95 ms   (-3.86%) |     334   →     334              |        3.46 s  →        3.32 s    (-3.86%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.35 ms →        9.95 ms   (-3.86%) |     334   →     334              |        3.46 s  →        3.32 s    (-3.86%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        6.60 ms →        6.53 ms   (-1.12%) |      26   →      26              |      171.72 ms →      169.79 ms   (-1.12%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.77 ms →        5.72 ms   (-0.86%) |      26   →      26              |      149.91 ms →      148.62 ms   (-0.86%) | 
  │ │ ├ sirius::Potential::generate                                     |      577.26 ms →      568.46 ms   (-1.52%) |      26   →      26              |       15.01 s  →       14.78 s    (-1.52%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      136.91 ms →      126.83 ms   (-7.36%) |      26   →      26              |        3.56 s  →        3.30 s    (-7.36%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        5.16 ms →        5.79 ms  (+12.23%) |      26   →      26              |      134.15 ms →      150.56 ms  (+12.23%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.27 ms →       10.32 ms   (+0.54%) |      26   →      26              |      266.94 ms →      268.38 ms   (+0.54%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.03 ms →       10.03 ms   (+0.01%) |      26   →      26              |      260.68 ms →      260.72 ms   (+0.01%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.03 ms →       10.03 ms   (+0.02%) |      26   →      26              |      260.66 ms →      260.70 ms   (+0.02%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      562.04 μs →      564.35 μs   (+0.41%) |      52   →      52              |       29.23 ms →       29.35 ms   (+0.41%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       48.50 ms →       49.03 ms   (+1.09%) |      26   →      26              |        1.26 s  →        1.27 s    (+1.09%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.21 ms →       46.74 ms   (+1.16%) |      26   →      26              |        1.20 s  →        1.22 s    (+1.16%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        2.96 ms →        2.98 ms   (+0.39%) |      52   →      52              |      154.14 ms →      154.74 ms   (+0.39%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.28 ms →        5.48 ms   (+3.77%) |      26   →      26              |      137.24 ms →      142.41 ms   (+3.77%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.42 ms →        6.42 ms   (-0.05%) |      26   →      26              |      166.87 ms →      166.80 ms   (-0.05%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       91.00 ms →       91.05 ms   (+0.06%) |      26   →      26              |        2.37 s  →        2.37 s    (+0.06%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      291.97 ms →      292.69 ms   (+0.25%) |      26   →      26              |        7.59 s  →        7.61 s    (+0.25%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      278.90 ms →      278.73 ms   (-0.06%) |      26   →      26              |        7.25 s  →        7.25 s    (-0.06%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      278.90 ms →      278.73 ms   (-0.06%) |      26   →      26              |        7.25 s  →        7.25 s    (-0.06%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.16 ms →       27.22 ms   (+0.20%) |      26   →      26              |      706.22 ms →      707.63 ms   (+0.20%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      224.15 ms →      223.99 ms   (-0.07%) |      26   →      26              |        5.83 s  →        5.82 s    (-0.07%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.82 ms →       23.75 ms   (-0.27%) |      26   →      26              |      619.26 ms →      617.60 ms   (-0.27%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.56 ms →        5.62 ms   (+0.93%) |      26   →      26              |      144.69 ms →      146.04 ms   (+0.93%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        9.95 ms →       10.24 ms   (+2.87%) |     182   →     182              |        1.81 s  →        1.86 s    (+2.87%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.79 ms →        9.76 ms   (-0.24%) |     182   →     182              |        1.78 s  →        1.78 s    (-0.24%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.79 ms →        9.76 ms   (-0.24%) |     182   →     182              |        1.78 s  →        1.78 s    (-0.24%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.73 ms →       10.60 ms   (-1.16%) |      78   →      78              |      836.82 ms →      827.09 ms   (-1.16%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.59 ms →       10.15 ms   (-4.20%) |      78   →      78              |      826.15 ms →      791.41 ms   (-4.20%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        9.80 ms →       10.06 ms   (+2.62%) |      26   →      26              |      254.81 ms →      261.49 ms   (+2.62%) | 
  │ │ └ sirius::Density::get_magnetisation                              |      115.56 μs →      126.77 μs   (+9.70%) |      26   →      26              |        3.00 ms →        3.30 ms   (+9.70%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |      110.76 μs →      121.82 μs   (+9.98%) |      26   →      26              |        2.88 ms →        3.17 ms   (+9.98%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.25 ms →        5.43 ms   (+3.50%) |       2   →       2              |       10.49 ms →       10.86 ms   (+3.50%) | 
  │ ├ sirius::Periodic_function|inner                                   |        9.93 ms →        9.71 ms   (-2.26%) |       6   →       6              |       59.57 ms →       58.23 ms   (-2.26%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        9.92 ms →        9.69 ms   (-2.31%) |       6   →       6              |       59.49 ms →       58.12 ms   (-2.31%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        9.92 ms →        9.69 ms   (-2.31%) |       6   →       6              |       59.49 ms →       58.12 ms   (-2.31%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.63 ms →       10.13 ms   (-4.78%) |       3   →       3              |       31.90 ms →       30.38 ms   (-4.78%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.63 ms →       10.03 ms   (-5.61%) |       3   →       3              |       31.88 ms →       30.09 ms   (-5.61%) | 
  ├ sirius::Periodic_function|inner                                     |        9.71 ms →       10.03 ms   (+3.29%) |       2   →       2              |       19.42 ms →       20.06 ms   (+3.29%) | 
  │ └ sirius::Periodic_function|inner_local                             |        9.70 ms →       10.02 ms   (+3.28%) |       2   →       2              |       19.40 ms →       20.04 ms   (+3.28%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.70 ms →       10.02 ms   (+3.28%) |       2   →       2              |       19.40 ms →       20.04 ms   (+3.28%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.63 ms →       10.41 ms   (-2.06%) |       1   →       1              |       10.63 ms →       10.41 ms   (-2.06%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.62 ms →       10.40 ms   (-2.07%) |       1   →       1              |       10.62 ms →       10.40 ms   (-2.07%) | 
- └ sirius::finalize                                                    |      172.68 ms →      221.60 ms  (+28.33%) |       1   →       1              |      172.68 ms →      221.60 ms  (+28.33%) | 
  ====================================================================================================================================================================================================
```
