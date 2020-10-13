# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs a923c3c8853d846138a8b9a9c096494004b8d208
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      176.38 s  →      133.76 s   (-24.16%) |       1   →       1              |      176.38 s  →      133.76 s   (-24.16%) | 
  ├ sirius::initialize                                                  |        2.82 s  →        2.72 s    (-3.36%) |       1   →       1              |        2.82 s  →        2.72 s    (-3.36%) | 
  ├ sirius::Simulation_context::initialize                              |        3.10 s  →        3.05 s    (-1.66%) |       1   →       1              |        3.10 s  →        3.05 s    (-1.66%) | 
- │ ├ sirius::Simulation_context::init_comm                             |      236.88 μs →       65.39 ms (+27504.04%) |       1   →       1              |      236.88 μs →       65.39 ms (+27504.04%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      251.51 ms →      211.29 ms  (-15.99%) |       1   →       1              |      251.51 ms →      211.29 ms  (-15.99%) | 
+ │ │ ├ sirius::Atom_type::init                                         |      112.84 ms →       93.74 ms  (-16.93%) |       2   →       2              |      225.69 ms →      187.48 ms  (-16.93%) | 
  │ │ └ sirius::Unit_cell::update                                       |       25.73 ms →       23.74 ms   (-7.76%) |       1   →       1              |       25.73 ms →       23.74 ms   (-7.76%) | 
+ │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.76 ms →        5.64 ms  (-16.49%) |       1   →       1              |        6.76 ms →        5.64 ms  (-16.49%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       18.93 ms →       18.05 ms   (-4.63%) |       1   →       1              |       18.93 ms →       18.05 ms   (-4.63%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       18.90 ms →       18.03 ms   (-4.61%) |       1   →       1              |       18.90 ms →       18.03 ms   (-4.61%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.16 ms →        4.15 ms   (-0.20%) |       1   →       1              |        4.16 ms →        4.15 ms   (-0.20%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.35 ms →        2.33 ms   (-0.66%) |       1   →       1              |        2.35 ms →        2.33 ms   (-0.66%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      103.96 μs →      103.02 μs   (-0.91%) |       1   →       1              |      103.96 μs →      103.02 μs   (-0.91%) | 
  │ └ sirius::Simulation_context::update                                |        2.80 s  →        2.73 s    (-2.72%) |       1   →       1              |        2.80 s  →        2.73 s    (-2.72%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.96 ms →       10.65 ms   (-2.79%) |       1   →       1              |       10.96 ms →       10.65 ms   (-2.79%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.54 ms →        4.24 ms   (-6.68%) |       1   →       1              |        4.54 ms →        4.24 ms   (-6.68%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.38 ms →        6.38 ms   (-0.01%) |       1   →       1              |        6.38 ms →        6.38 ms   (-0.01%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.36 ms →        6.36 ms   (+0.02%) |       1   →       1              |        6.36 ms →        6.36 ms   (+0.02%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.86 ms →        3.87 ms   (+0.31%) |       1   →       1              |        3.86 ms →        3.87 ms   (+0.31%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.32 ms   (-0.37%) |       1   →       1              |        2.33 ms →        2.32 ms   (-0.37%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      103.48 μs →      102.18 μs   (-1.25%) |       1   →       1              |      103.48 μs →      102.18 μs   (-1.25%) | 
+ │   ├ sirius::Radial_integrals|aug                                    |       73.83 ms →       63.80 ms  (-13.59%) |       2   →       2              |      147.66 ms →      127.60 ms  (-13.59%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.22 ms →        5.15 ms   (-1.38%) |       2   →       2              |       10.44 ms →       10.30 ms   (-1.38%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.66 ms →        4.49 ms   (-3.67%) |       1   →       1              |        4.66 ms →        4.49 ms   (-3.67%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.77 ms →       21.81 ms   (+0.20%) |       2   →       2              |       43.53 ms →       43.62 ms   (+0.20%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.85 ms →       15.15 ms   (+2.02%) |       2   →       2              |       29.70 ms →       30.30 ms   (+2.02%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.87 ms →       19.76 ms   (-0.53%) |       4   →       4              |       79.48 ms →       79.06 ms   (-0.53%) | 
  │   ├ sddk::Gvec::init                                                |      181.70 ms →      171.09 ms   (-5.84%) |       2   →       2              |      363.40 ms →      342.19 ms   (-5.84%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      134.76 ms →      128.98 ms   (-4.29%) |       2   →       2              |      269.52 ms →      257.95 ms   (-4.29%) | 
  │   ├ sddk::Gvec_shells                                               |      191.98 ms →      187.75 ms   (-2.20%) |       1   →       1              |      191.98 ms →      187.75 ms   (-2.20%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.35 ms →        1.32 ms   (-2.24%) |       1   →       1              |        1.35 ms →        1.32 ms   (-2.24%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      293.80 ms →      292.52 ms   (-0.43%) |       2   →       2              |      587.60 ms →      585.05 ms   (-0.43%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       38.98 ms →       35.35 ms   (-9.31%) |       1   →       1              |       38.98 ms →       35.35 ms   (-9.31%) | 
+ │ ├ sirius::K_point::K_point                                          |        2.78 μs →        2.25 μs  (-19.22%) |       4   →       4              |       11.13 μs →        8.99 μs  (-19.22%) | 
  │ └ sirius::K_point_set::initialize                                   |       38.89 ms →       35.26 ms   (-9.35%) |       1   →       1              |       38.89 ms →       35.26 ms   (-9.35%) | 
  │   └ sirius::K_point::initialize                                     |       38.80 ms →       35.17 ms   (-9.35%) |       1   →       1              |       38.80 ms →       35.17 ms   (-9.35%) | 
+ │     ├ sirius::K_point::generate_gkvec                               |       20.04 ms →       17.95 ms  (-10.44%) |       1   →       1              |       20.04 ms →       17.95 ms  (-10.44%) | 
  │     │ └ sddk::Gvec::init                                            |        8.92 ms →        8.03 ms   (-9.96%) |       1   →       1              |        8.92 ms →        8.03 ms   (-9.96%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        9.21 μs →       10.07 μs   (+9.36%) |       1   →       1              |        9.21 μs →       10.07 μs   (+9.36%) | 
  │     └ sirius::K_point::update                                       |       13.12 ms →       12.46 ms   (-5.01%) |       1   →       1              |       13.12 ms →       12.46 ms   (-5.01%) | 
  │       └ sirius::Beta_projectors                                     |        6.09 ms →        6.22 ms   (+2.15%) |       1   →       1              |        6.09 ms →        6.22 ms   (+2.15%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.49 ms →        3.68 ms   (+5.44%) |       1   →       1              |        3.49 ms →        3.68 ms   (+5.44%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.40 ms →        5.16 ms   (-4.38%) |       2   →       2              |       10.79 ms →       10.32 ms   (-4.38%) | 
  ├ sirius::Potential                                                   |      171.76 ms →      158.83 ms   (-7.52%) |       1   →       1              |      171.76 ms →      158.83 ms   (-7.52%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        6.21 ms →        5.80 ms   (-6.70%) |       6   →       6              |       37.29 ms →       34.79 ms   (-6.70%) | 
  │ └ sirius::Potential::update                                         |      133.75 ms →      123.29 ms   (-7.82%) |       1   →       1              |      133.75 ms →      123.29 ms   (-7.82%) | 
  │   └ sirius::Potential::generate_local_potential                     |      133.05 ms →      122.55 ms   (-7.89%) |       1   →       1              |      133.05 ms →      122.55 ms   (-7.89%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |      126.21 ms →      111.47 ms  (-11.67%) |       1   →       1              |      126.21 ms →      111.47 ms  (-11.67%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        6.31 ms →       10.20 ms  (+61.62%) |       1   →       1              |        6.31 ms →       10.20 ms  (+61.62%) | 
  ├ sirius::Density                                                     |      140.82 ms →      134.88 ms   (-4.22%) |       1   →       1              |      140.82 ms →      134.88 ms   (-4.22%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.14 ms →        5.10 ms   (-0.82%) |       2   →       2              |       10.27 ms →       10.19 ms   (-0.82%) | 
  │ └ sirius::Density::update                                           |      130.28 ms →      124.42 ms   (-4.50%) |       1   →       1              |      130.28 ms →      124.42 ms   (-4.50%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      129.87 ms →      123.99 ms   (-4.52%) |       1   →       1              |      129.87 ms →      123.99 ms   (-4.52%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |                       102.77 μs            |                   1              |                       102.77 μs            | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      124.18 ms →      112.86 ms   (-9.12%) |       1   →       1              |      124.18 ms →      112.86 ms   (-9.12%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        5.25 ms →       10.57 ms (+101.37%) |       1   →       1              |        5.25 ms →       10.57 ms (+101.37%) | 
  ├ sirius::Density::initial_density                                    |      180.62 ms →      178.64 ms   (-1.10%) |       1   →       1              |      180.62 ms →      178.64 ms   (-1.10%) | 
+ │ ├ sirius::Simulation_context::make_periodic_function                |      123.96 ms →      111.25 ms  (-10.25%) |       1   →       1              |      123.96 ms →      111.25 ms  (-10.25%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.92 ms →       11.22 ms (+128.04%) |       2   →       2              |        9.84 ms →       22.44 ms (+128.04%) | 
  │ └ sirius::Periodic_function::integrate                              |       11.67 ms →       12.44 ms   (+6.61%) |       1   →       1              |       11.67 ms →       12.44 ms   (+6.61%) | 
  ├ sirius::Potential::generate                                         |      584.94 ms →      598.30 ms   (+2.28%) |       1   →       1              |      584.94 ms →      598.30 ms   (+2.28%) | 
  │ ├ sirius::Potential::poisson                                        |      137.97 ms →      136.40 ms   (-1.14%) |       1   →       1              |      137.97 ms →      136.40 ms   (-1.14%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.24 ms →       16.77 ms (+219.90%) |       1   →       1              |        5.24 ms →       16.77 ms (+219.90%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        9.96 ms →       10.39 ms   (+4.29%) |       1   →       1              |        9.96 ms →       10.39 ms   (+4.29%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        9.88 ms →        9.90 ms   (+0.20%) |       1   →       1              |        9.88 ms →        9.90 ms   (+0.20%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.88 ms →        9.89 ms   (+0.12%) |       1   →       1              |        9.88 ms →        9.89 ms   (+0.12%) | 
  │ ├ sirius::Periodic_function::add                                    |      567.43 μs →      555.90 μs   (-2.03%) |       2   →       2              |        1.13 ms →        1.11 ms   (-2.03%) | 
  │ ├ sirius::Potential::xc                                             |       51.09 ms →       55.89 ms   (+9.39%) |       1   →       1              |       51.09 ms →       55.89 ms   (+9.39%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.08 ms →       53.50 ms   (+4.73%) |       1   →       1              |       51.08 ms →       53.50 ms   (+4.73%) | 
- │ │   ├ sirius::Smooth_periodic_function                              |        5.66 ms →        6.26 ms  (+10.73%) |       2   →       2              |       11.32 ms →       12.53 ms  (+10.73%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.17 ms →        5.22 ms   (+1.10%) |       1   →       1              |        5.17 ms →        5.22 ms   (+1.10%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.90 ms →        6.21 ms   (+5.26%) |       1   →       1              |        5.90 ms →        6.21 ms   (+5.26%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.85 ms →       93.69 ms   (+0.91%) |       1   →       1              |       92.85 ms →       93.69 ms   (+0.91%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      294.66 ms →      303.63 ms   (+3.05%) |       1   →       1              |      294.66 ms →      303.63 ms   (+3.05%) | 
  ├ sirius::Hamiltonian0                                                |        8.51 ms →        8.68 ms   (+2.01%) |       1   →       1              |        8.51 ms →        8.68 ms   (+2.01%) | 
  │ ├ sirius::Local_operator                                            |        8.15 ms →        8.32 ms   (+2.05%) |       1   →       1              |        8.15 ms →        8.32 ms   (+2.05%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.70 ms →        5.09 ms   (+8.26%) |       1   →       1              |        4.70 ms →        5.09 ms   (+8.26%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.53 ms →        2.31 ms   (-8.37%) |       1   →       1              |        2.53 ms →        2.31 ms   (-8.37%) | 
  │ ├ sirius::Non_local_operator                                        |       63.23 μs →       62.57 μs   (-1.04%) |       2   →       2              |      126.46 μs →      125.14 μs   (-1.04%) | 
  │ ├ sirius::D_operator::initialize                                    |      105.59 μs →       97.87 μs   (-7.31%) |       1   →       1              |      105.59 μs →       97.87 μs   (-7.31%) | 
  │ └ sirius::Q_operator::initialize                                    |       76.00 μs →       79.73 μs   (+4.91%) |       1   →       1              |       76.00 μs →       79.73 μs   (+4.91%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.87 s  →        1.87 s    (+0.12%) |       1   →       1              |        1.87 s  →        1.87 s    (+0.12%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.72 ms →       18.14 ms   (-3.08%) |       1   →       1              |       18.72 ms →       18.14 ms   (-3.08%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      209.28 μs →      195.57 μs   (-6.55%) |       1   →       1              |      209.28 μs →      195.57 μs   (-6.55%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       18.50 ms →       17.94 ms   (-3.04%) |       1   →       1              |       18.50 ms →       17.94 ms   (-3.04%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.85 s  →        1.85 s    (+0.15%) |       1   →       1              |        1.85 s  →        1.85 s    (+0.15%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      129.09 ms →      128.88 ms   (-0.17%) |       4   →       4              |      516.37 ms →      515.51 ms   (-0.17%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       53.02 ms →       51.93 ms   (-2.07%) |       1   →       1              |       53.02 ms →       51.93 ms   (-2.07%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.39 ms →       21.04 ms   (-1.61%) |       1   →       1              |       21.39 ms →       21.04 ms   (-1.61%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      647.51 ms →      640.87 ms   (-1.03%) |       1   →       1              |      647.51 ms →      640.87 ms   (-1.03%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      297.94 ms →      302.11 ms   (+1.40%) |       1   →       1              |      297.94 ms →      302.11 ms   (+1.40%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.12 μs →        2.87 μs   (-7.95%) |       1   →       1              |        3.12 μs →        2.87 μs   (-7.95%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        1.96 μs →        1.96 μs   (+0.15%) |       1   →       1              |        1.96 μs →        1.96 μs   (+0.15%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      435.00 ns →      397.00 ns   (-8.74%) |       1   →       1              |      435.00 ns →      397.00 ns   (-8.74%) | 
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                        |        1.22 μs →      514.00 ns  (-57.87%) |       1   →       1              |        1.22 μs →      514.00 ns  (-57.87%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.25 ms →        9.22 ms   (-0.27%) |       1   →       1              |        9.25 ms →        9.22 ms   (-0.27%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      123.46 ms →      120.56 ms   (-2.34%) |       1   →       1              |      123.46 ms →      120.56 ms   (-2.34%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      108.41 ms →      104.47 ms   (-3.63%) |       2   →       2              |      216.82 ms →      208.94 ms   (-3.63%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       38.78 ms →       40.19 ms   (+3.64%) |       2   →       2              |       77.56 ms →       80.38 ms   (+3.64%) | 
  │ │ │ ├ sddk::inner                                                   |       38.24 ms                             |       2                          |       76.47 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       45.25 μs                             |       2                          |       90.49 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        39.64 ms            |                   2              |                        79.27 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        22.50 ns            |                   2              |                        45.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        39.18 ms            |                   2              |                        78.36 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                        19.50 ns            |                   2              |                        39.00 ns            | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       57.52 ms →       63.25 ms   (+9.96%) |       1   →       1              |       57.52 ms →       63.25 ms   (+9.96%) | 
  │ │ ├ sddk::transform                                                 |       31.84 ms                             |       1                          |       31.84 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       12.77 μs                             |       1                          |       12.77 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       16.18 μs                             |       1                          |       16.18 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                        30.74 ms            |                   1              |                        30.74 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                        30.73 ms            |                   1              |                        30.73 ms            | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      569.00 ns →      540.00 ns   (-5.10%) |       1   →       1              |      569.00 ns →      540.00 ns   (-5.10%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      166.07 s  →      123.97 s   (-25.35%) |       1   →       1              |      166.07 s  →      123.97 s   (-25.35%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.72 ms →        5.80 ms   (+1.44%) |      19   →      19              |      108.60 ms →      110.15 ms   (+1.44%) | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.48 s  →        4.75 s    (+6.12%) |      37   →      26    (-29.73%) |      165.62 s  →      123.51 s   (-25.43%) | 
+ │ │ ├ sirius::Hamiltonian0                                            |        4.90 ms →        4.50 ms   (-8.09%) |      37   →      26    (-29.73%) |      181.29 ms →      117.08 ms  (-35.42%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        4.52 ms →        4.14 ms   (-8.52%) |      37   →      26    (-29.73%) |      167.34 ms →      107.57 ms  (-35.72%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function                            |      945.28 μs →      972.36 μs   (+2.86%) |      37   →      26    (-29.73%) |       34.98 ms →       25.28 ms  (-27.72%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.68 ms →        2.28 ms  (-15.19%) |      37   →      26    (-29.73%) |       99.30 ms →       59.18 ms  (-40.40%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |       64.98 μs →       64.60 μs   (-0.58%) |      74   →      52    (-29.73%) |        4.81 ms →        3.36 ms  (-30.14%) | 
+ │ │ │ ├ sirius::D_operator::initialize                                |      101.67 μs →       87.80 μs  (-13.64%) |      37   →      26    (-29.73%) |        3.76 ms →        2.28 ms  (-39.32%) | 
+ │ │ │ └ sirius::Q_operator::initialize                                |       77.10 μs →       78.27 μs   (+1.51%) |      37   →      26    (-29.73%) |        2.85 ms →        2.04 ms  (-28.67%) | 
- │ │ ├ sirius::Band::solve                                             |        2.51 s  →        2.77 s   (+10.33%) |      37   →      26    (-29.73%) |       92.77 s  →       71.92 s   (-22.47%) | 
+ │ │ │ ├ sirius::Hamiltonian_k                                         |      174.85 μs →      152.03 μs  (-13.06%) |      37   →      26    (-29.73%) |        6.47 ms →        3.95 ms  (-38.90%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      168.48 μs →      145.13 μs  (-13.86%) |      37   →      26    (-29.73%) |        6.23 ms →        3.77 ms  (-39.47%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.63 μs →        5.00 μs   (+7.87%) |      37   →      26    (-29.73%) |      171.49 μs →      129.99 μs  (-24.20%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.45 s  →        2.63 s    (+7.32%) |      37   →      26    (-29.73%) |       90.74 s  →       68.43 s   (-24.59%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       98.86 ms →       94.90 ms   (-4.01%) |      37   →      26    (-29.73%) |        3.66 s  →        2.47 s   (-32.55%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        8.23 ms →        7.69 ms   (-6.55%) |     222   →     156    (-29.73%) |        1.83 s  →        1.20 s   (-34.33%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        5.89 ms →        5.93 ms   (+0.68%) |      37   →      26    (-29.73%) |      217.90 ms →      154.15 ms  (-29.26%) | 
+ │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      351.64 μs →      348.06 μs   (-1.02%) |      37   →      26    (-29.73%) |       13.01 ms →        9.05 ms  (-30.45%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.29 ms →        2.31 ms   (+0.73%) |      74   →      52    (-29.73%) |      169.36 ms →      119.88 ms  (-29.21%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.31 s  →        2.49 s    (+7.86%) |      37   →      26    (-29.73%) |       85.53 s  →       64.83 s   (-24.21%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      109.92 ms →      127.82 ms  (+16.28%) |     366   →     277    (-24.32%) |       40.23 s  →       35.41 s   (-11.99%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       42.39 ms →       51.16 ms  (+20.71%) |     366   →     277    (-24.32%) |       15.51 s  →       14.17 s    (-8.65%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.99 μs →        1.99 μs   (-0.14%) |     366   →     277    (-24.32%) |      729.18 μs →      551.09 μs  (-24.42%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.64 μs →        1.70 μs   (+4.17%) |     366   →     277    (-24.32%) |      598.59 μs →      471.94 μs  (-21.16%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      325.79 ns →      374.28 ns  (+14.89%) |     366   →     277    (-24.32%) |      119.24 μs →      103.68 μs  (-13.05%) | 
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      457.80 ns →      471.19 ns   (+2.92%) |     366   →     277    (-24.32%) |      167.55 μs →      130.52 μs  (-22.10%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.39 ms →        7.42 ms   (+0.35%) |     366   →     277    (-24.32%) |        2.71 s  →        2.06 s   (-24.05%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       20.31 ms →       23.30 ms  (+14.72%) |     366   →     277    (-24.32%) |        7.43 s  →        6.45 s   (-13.18%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       19.91 ms →       22.96 ms  (+15.33%) |     732   →     554    (-24.32%) |       14.57 s  →       12.72 s   (-12.71%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |       30.00 ms →       34.32 ms  (+14.40%) |     366   →     277    (-24.32%) |       10.98 s  →        9.51 s   (-13.42%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        4.48 ms                             |     695                          |        3.11 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       23.94 μs                             |     695                          |       16.63 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                         5.96 ms            |                 528              |                         3.15 s             | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                        72.64 ns            |                 528              |                        38.35 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                         4.85 ms            |                 528              |                         2.56 s             | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                        72.67 ns            |                 528              |                        38.37 μs            | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      519.24 μs →      608.94 μs  (+17.28%) |     366   →     277    (-24.32%) |      190.04 ms →      168.68 ms  (-11.24%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        8.39 ms →        9.56 ms  (+13.93%) |     366   →     277    (-24.32%) |        3.07 s  →        2.65 s   (-13.78%) | 
  │ │ │ │   │ ├ sddk::transform                                         |       13.99 ms                             |     329                          |        4.60 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       20.16 μs                             |     329                          |        6.63 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       48.27 μs                             |     987                          |       47.64 ms                             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                        14.11 ms            |                 251              |                         3.54 s             | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                         4.70 ms            |                 753              |                         3.54 s             | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        9.43 ms →       10.33 ms   (+9.55%) |     366   →     277    (-24.32%) |        3.45 s  →        2.86 s   (-17.09%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        8.63 ms                             |     366                          |        3.16 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       29.94 μs                             |     366                          |       10.96 ms                             | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                        10.06 ms            |                 277              |                         2.79 s             | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                        47.49 ns            |                 277              |                        13.15 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                         8.95 ms            |                 277              |                         2.48 s             | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                        63.14 ns            |                 277              |                        17.49 μs            | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       65.13 ms →       34.19 ms  (-47.51%) |     366   →     277    (-24.32%) |       23.84 s  →        9.47 s   (-60.27%) | 
+ │ │ │ │   ├ sirius::residuals                                         |       14.00 ms →       13.45 ms   (-3.88%) |     354   →     268    (-24.29%) |        4.95 s  →        3.61 s   (-27.23%) | 
  │ │ │ │   │ ├ sddk::transform                                         |       12.90 ms                             |     340                          |        4.39 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       15.99 μs                             |     340                          |        5.44 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       40.16 μs                             |     680                          |       27.31 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                        12.11 ms            |                 259              |                         3.14 s             | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                         6.05 ms            |                 518              |                         3.13 s             | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.42 ms →        1.57 ms  (+10.94%) |     340   →     259    (-23.82%) |      482.66 ms →      407.91 ms  (-15.49%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       52.81 ms →       74.90 ms  (+41.83%) |      39   →      53    (+35.90%) |        2.06 s  →        3.97 s   (+92.74%) | 
  │ │ │ │     ├ sddk::transform                                         |       50.04 ms                             |      41                          |        2.05 s                              | 
  │ │ │ │     │ ├ sddk::transform|init                                  |       13.58 μs                             |      41                          |      556.98 μs                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       14.20 μs                             |      43                          |      610.65 μs                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                        49.39 ms            |                  80              |                         3.95 s             | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                        36.93 ms            |                 107              |                         3.95 s             | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      484.92 ns →      870.38 ns  (+79.49%) |      37   →      26    (-29.73%) |       17.94 μs →       22.63 μs  (+26.13%) | 
+ │ │ │ └ sirius::K_point_set::sync_band_energies                       |       42.28 μs →       37.06 μs  (-12.35%) |      37   →      26    (-29.73%) |        1.56 ms →      963.57 μs  (-38.41%) | 
+ │ │ ├ sirius::K_point_set::find_band_occupancies                      |      614.36 μs →      610.13 μs   (-0.69%) |      37   →      26    (-29.73%) |       22.73 ms →       15.86 ms  (-30.21%) | 
+ │ │ ├ sirius::Density::generate                                       |      776.40 ms →      773.28 ms   (-0.40%) |      37   →      26    (-29.73%) |       28.73 s  →       20.11 s   (-30.01%) | 
+ │ │ │ ├ sirius::Density::generate_valence                             |      402.85 ms →      403.74 ms   (+0.22%) |      37   →      26    (-29.73%) |       14.91 s  →       10.50 s   (-29.57%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.29 μs →        8.43 μs   (+1.65%) |      37   →      26    (-29.73%) |      306.88 μs →      219.20 μs  (-28.57%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.45 μs →        7.90 μs   (+6.12%) |      37   →      26    (-29.73%) |      275.48 μs →      205.43 μs  (-25.43%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |      100.77 ms →      100.27 ms   (-0.49%) |      37   →      26    (-29.73%) |        3.73 s  →        2.61 s   (-30.07%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.29 μs →        7.43 μs   (+1.95%) |      37   →      26    (-29.73%) |      269.59 μs →      193.13 μs  (-28.36%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.15 ms →        7.12 ms   (-0.45%) |      37   →      26    (-29.73%) |      264.65 ms →      185.13 ms  (-30.05%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       91.75 ms →       91.24 ms   (-0.56%) |      37   →      26    (-29.73%) |        3.39 s  →        2.37 s   (-30.12%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      522.57 ns →      732.08 ns  (+40.09%) |      37   →      26    (-29.73%) |       19.34 μs →       19.03 μs   (-1.56%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      163.07 ms →      162.60 ms   (-0.29%) |      37   →      26    (-29.73%) |        6.03 s  →        4.23 s   (-29.93%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.65 ms →        1.65 ms   (-0.28%) |      37   →      26    (-29.73%) |       61.04 ms →       42.77 ms  (-29.92%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |       88.27 ms →       88.27 ms   (+0.00%) |      37   →      26    (-29.73%) |        3.27 s  →        2.30 s   (-29.73%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.04 ms →       88.04 ms   (+0.00%) |      37   →      26    (-29.73%) |        3.26 s  →        2.29 s   (-29.73%) | 
+ │ │ │ ├ sirius::Field4D::symmetrize                                   |      280.96 ms →      274.15 ms   (-2.42%) |      37   →      26    (-29.73%) |       10.40 s  →        7.13 s   (-31.43%) | 
+ │ │ │ │ └ sirius::symmetrize_function|fpw                             |      280.96 ms →      274.15 ms   (-2.42%) |      37   →      26    (-29.73%) |       10.40 s  →        7.13 s   (-31.43%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       29.36 ms →       26.47 ms   (-9.84%) |      37   →      26    (-29.73%) |        1.09 s  →      688.24 ms  (-36.64%) | 
+ │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      223.55 ms →      223.40 ms   (-0.07%) |      37   →      26    (-29.73%) |        8.27 s  →        5.81 s   (-29.78%) | 
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       26.85 ms →       23.10 ms  (-13.96%) |      37   →      26    (-29.73%) |      993.52 ms →      600.72 ms  (-39.54%) | 
+ │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       81.32 ms →       82.17 ms   (+1.05%) |      37   →      26    (-29.73%) |        3.01 s  →        2.14 s   (-28.99%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        7.69 ms →        9.61 ms  (+25.07%) |      37   →      26    (-29.73%) |      284.38 ms →      249.93 ms  (-12.11%) | 
+ │ │ ├ sirius::Density::mix                                            |      215.94 ms →      217.51 ms   (+0.73%) |      37   →      26    (-29.73%) |        7.99 s  →        5.66 s   (-29.22%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      939.01 μs →      946.88 μs   (+0.84%) |      37   →      26    (-29.73%) |       34.74 ms →       24.62 ms  (-29.14%) | 
+ │ │ │ ├ sirius::Periodic_function|inner                               |       10.20 ms →       10.69 ms   (+4.82%) |     485   →     334    (-31.13%) |        4.95 s  →        3.57 s   (-27.81%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner_local                       |        9.97 ms →       10.35 ms   (+3.77%) |     485   →     334    (-31.13%) |        4.84 s  →        3.46 s   (-28.54%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        9.97 ms →       10.35 ms   (+3.76%) |     485   →     334    (-31.13%) |        4.84 s  →        3.46 s   (-28.54%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        6.45 ms →        6.26 ms   (-2.92%) |      37   →      26    (-29.73%) |      238.75 ms →      162.87 ms  (-31.78%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.64 ms →        5.42 ms   (-3.93%) |      37   →      26    (-29.73%) |      208.70 ms →      140.90 ms  (-32.49%) | 
+ │ │ ├ sirius::Potential::generate                                     |      570.68 ms →      584.19 ms   (+2.37%) |      37   →      26    (-29.73%) |       21.12 s  →       15.19 s   (-28.07%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |      138.20 ms →      136.34 ms   (-1.35%) |      37   →      26    (-29.73%) |        5.11 s  →        3.54 s   (-30.68%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        5.13 ms →       16.15 ms (+214.81%) |      37   →      26    (-29.73%) |      189.78 ms →      419.83 ms (+121.22%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner                             |       10.33 ms →       10.14 ms   (-1.85%) |      37   →      26    (-29.73%) |      382.25 ms →      263.64 ms  (-31.03%) | 
+ │ │ │ │   └ sirius::Periodic_function|inner_local                     |        9.96 ms →        9.84 ms   (-1.21%) |      37   →      26    (-29.73%) |      368.53 ms →      255.84 ms  (-30.58%) | 
+ │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        9.96 ms →        9.84 ms   (-1.21%) |      37   →      26    (-29.73%) |      368.51 ms →      255.82 ms  (-30.58%) | 
+ │ │ │ ├ sirius::Periodic_function::add                                |      566.05 μs →      548.17 μs   (-3.16%) |      74   →      52    (-29.73%) |       41.89 ms →       28.51 ms  (-31.95%) | 
+ │ │ │ ├ sirius::Potential::xc                                         |       44.93 ms →       48.59 ms   (+8.17%) |      37   →      26    (-29.73%) |        1.66 s  →        1.26 s   (-23.99%) | 
+ │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       44.92 ms →       46.24 ms   (+2.92%) |      37   →      26    (-29.73%) |        1.66 s  →        1.20 s   (-27.68%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function                          |        1.20 ms →        2.99 ms (+149.54%) |      74   →      52    (-29.73%) |       88.81 ms →      155.73 ms  (+75.35%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |       11.71 ms →        5.36 ms  (-54.21%) |      37   →      26    (-29.73%) |      433.41 ms →      139.46 ms  (-67.82%) | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        7.75 ms →        6.53 ms  (-15.65%) |      37   →      26    (-29.73%) |      286.59 ms →      169.87 ms  (-40.73%) | 
+ │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.95 ms →       90.97 ms   (+0.02%) |      37   →      26    (-29.73%) |        3.37 s  →        2.37 s   (-29.71%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      286.48 ms →      299.38 ms   (+4.50%) |      37   →      26    (-29.73%) |       10.60 s  →        7.78 s   (-26.56%) | 
+ │ │ ├ sirius::Field4D::symmetrize                                     |      283.35 ms →      280.64 ms   (-0.96%) |      37   →      26    (-29.73%) |       10.48 s  →        7.30 s   (-30.40%) | 
+ │ │ │ └ sirius::symmetrize_function|fpw                               |      283.35 ms →      280.64 ms   (-0.96%) |      37   →      26    (-29.73%) |       10.48 s  →        7.30 s   (-30.40%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       31.21 ms →       29.45 ms   (-5.66%) |      37   →      26    (-29.73%) |        1.15 s  →      765.67 ms  (-33.71%) | 
+ │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      222.63 ms →      223.63 ms   (+0.45%) |      37   →      26    (-29.73%) |        8.24 s  →        5.81 s   (-29.42%) | 
+ │ │ │   └ sddk::Gvec_shells::remap_backward                           |       28.36 ms →       23.79 ms  (-16.10%) |      37   →      26    (-29.73%) |        1.05 s  →      618.58 ms  (-41.05%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.38 ms →        8.66 ms  (+61.01%) |      37   →      26    (-29.73%) |      199.08 ms →      225.25 ms  (+13.14%) | 
+ │ │ ├ sirius::Periodic_function|inner                                 |       10.00 ms →       10.21 ms   (+2.10%) |     259   →     182    (-29.73%) |        2.59 s  →        1.86 s   (-28.25%) | 
+ │ │ │ └ sirius::Periodic_function|inner_local                         |        9.75 ms →        9.75 ms   (+0.04%) |     259   →     182    (-29.73%) |        2.53 s  →        1.78 s   (-29.70%) | 
+ │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.75 ms →        9.75 ms   (+0.04%) |     259   →     182    (-29.73%) |        2.53 s  →        1.78 s   (-29.70%) | 
+ │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.30 ms →       11.00 ms   (+6.71%) |     111   →      78    (-29.73%) |        1.14 s  →      857.67 ms  (-25.02%) | 
+ │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.11 ms →       10.56 ms   (+4.52%) |     111   →      78    (-29.73%) |        1.12 s  →      823.98 ms  (-26.55%) | 
+ │ │ ├ sirius::Periodic_function::integrate                            |       10.60 ms →        9.98 ms   (-5.87%) |      37   →      26    (-29.73%) |      392.13 ms →      259.37 ms  (-33.85%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      120.53 μs →      139.46 μs  (+15.70%) |      37   →      26    (-29.73%) |        4.46 ms →        3.63 ms  (-18.70%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      115.31 μs →      134.53 μs  (+16.67%) |      37   →      26    (-29.73%) |        4.27 ms →        3.50 ms  (-18.02%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.24 ms →        5.44 ms   (+3.72%) |       2   →       2              |       10.48 ms →       10.87 ms   (+3.72%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.09 ms →        9.93 ms   (-1.55%) |       6   →       6              |       60.52 ms →       59.58 ms   (-1.55%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.08 ms →        9.69 ms   (-3.82%) |       6   →       6              |       60.47 ms →       58.15 ms   (-3.82%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.08 ms →        9.69 ms   (-3.83%) |       6   →       6              |       60.46 ms →       58.15 ms   (-3.83%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.61 ms →       10.56 ms   (-0.47%) |       3   →       3              |       31.84 ms →       31.69 ms   (-0.47%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.59 ms →       10.51 ms   (-0.76%) |       3   →       3              |       31.76 ms →       31.52 ms   (-0.76%) | 
  ├ sirius::Periodic_function|inner                                     |        9.69 ms →        9.71 ms   (+0.13%) |       2   →       2              |       19.39 ms →       19.41 ms   (+0.13%) | 
  │ └ sirius::Periodic_function|inner_local                             |        9.68 ms →        9.70 ms   (+0.17%) |       2   →       2              |       19.37 ms →       19.40 ms   (+0.17%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.68 ms →        9.70 ms   (+0.17%) |       2   →       2              |       19.37 ms →       19.40 ms   (+0.17%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.11 ms →       10.51 ms   (+3.90%) |       1   →       1              |       10.11 ms →       10.51 ms   (+3.90%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.02 ms →       10.50 ms   (+4.77%) |       1   →       1              |       10.02 ms →       10.50 ms   (+4.77%) | 
  └ sirius::finalize                                                    |      223.75 ms →      208.18 ms   (-6.96%) |       1   →       1              |      223.75 ms →      208.18 ms   (-6.96%) | 
  ====================================================================================================================================================================================================
```
