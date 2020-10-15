# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs 40e9e6046ebfdd2424926f76cb043caae175bee0
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      132.90 s  →      129.08 s    (-2.87%) |       1   →       1              |      132.90 s  →      129.08 s    (-2.87%) | 
  ├ sirius::initialize                                                  |        2.71 s  →        2.72 s    (+0.39%) |       1   →       1              |        2.71 s  →        2.72 s    (+0.39%) | 
  ├ sirius::Simulation_context::initialize                              |        2.96 s  →        2.90 s    (-2.14%) |       1   →       1              |        2.96 s  →        2.90 s    (-2.14%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       64.18 ms →      676.84 μs  (-98.95%) |       1   →       1              |       64.18 ms →      676.84 μs  (-98.95%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      137.18 ms →      154.91 ms  (+12.93%) |       1   →       1              |      137.18 ms →      154.91 ms  (+12.93%) | 
- │ │ ├ sirius::Atom_type::init                                         |       56.30 ms →       64.98 ms  (+15.42%) |       2   →       2              |      112.60 ms →      129.96 ms  (+15.42%) | 
  │ │ └ sirius::Unit_cell::update                                       |       24.50 ms →       24.87 ms   (+1.50%) |       1   →       1              |       24.50 ms →       24.87 ms   (+1.50%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.21 ms →        6.39 ms   (+2.91%) |       1   →       1              |        6.21 ms →        6.39 ms   (+2.91%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       18.24 ms →       18.42 ms   (+1.00%) |       1   →       1              |       18.24 ms →       18.42 ms   (+1.00%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       18.22 ms →       18.40 ms   (+1.00%) |       1   →       1              |       18.22 ms →       18.40 ms   (+1.00%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.15 ms →        4.14 ms   (-0.35%) |       1   →       1              |        4.15 ms →        4.14 ms   (-0.35%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.35 ms   (+0.56%) |       1   →       1              |        2.33 ms →        2.35 ms   (+0.56%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      105.42 μs →      105.05 μs   (-0.34%) |       1   →       1              |      105.42 μs →      105.05 μs   (-0.34%) | 
  │ └ sirius::Simulation_context::update                                |        2.71 s  →        2.70 s    (-0.66%) |       1   →       1              |        2.71 s  →        2.70 s    (-0.66%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.85 ms →       10.83 ms   (-0.26%) |       1   →       1              |       10.85 ms →       10.83 ms   (-0.26%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.46 ms →        4.44 ms   (-0.42%) |       1   →       1              |        4.46 ms →        4.44 ms   (-0.42%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.36 ms →        6.35 ms   (-0.26%) |       1   →       1              |        6.36 ms →        6.35 ms   (-0.26%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.34 ms →        6.33 ms   (-0.26%) |       1   →       1              |        6.34 ms →        6.33 ms   (-0.26%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.86 ms →        3.82 ms   (-0.89%) |       1   →       1              |        3.86 ms →        3.82 ms   (-0.89%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.31 ms →        2.34 ms   (+1.13%) |       1   →       1              |        2.31 ms →        2.34 ms   (+1.13%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      100.70 μs →      100.50 μs   (-0.20%) |       1   →       1              |      100.70 μs →      100.50 μs   (-0.20%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       62.78 ms →       62.72 ms   (-0.09%) |       2   →       2              |      125.56 ms →      125.44 ms   (-0.09%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.14 ms →        5.28 ms   (+2.60%) |       2   →       2              |       10.28 ms →       10.55 ms   (+2.60%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.47 ms →        4.48 ms   (+0.15%) |       1   →       1              |        4.47 ms →        4.48 ms   (+0.15%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.74 ms →       21.77 ms   (+0.16%) |       2   →       2              |       43.48 ms →       43.55 ms   (+0.16%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.85 ms →       14.87 ms   (+0.15%) |       2   →       2              |       29.70 ms →       29.74 ms   (+0.15%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.88 ms →       19.81 ms   (-0.34%) |       4   →       4              |       79.52 ms →       79.25 ms   (-0.34%) | 
  │   ├ sddk::Gvec::init                                                |      184.28 ms →      174.44 ms   (-5.34%) |       2   →       2              |      368.57 ms →      348.87 ms   (-5.34%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      141.09 ms →      131.99 ms   (-6.46%) |       2   →       2              |      282.19 ms →      263.97 ms   (-6.46%) | 
  │   ├ sddk::Gvec_shells                                               |      164.00 ms →      167.67 ms   (+2.24%) |       1   →       1              |      164.00 ms →      167.67 ms   (+2.24%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.32 ms →        1.33 ms   (+1.09%) |       1   →       1              |        1.32 ms →        1.33 ms   (+1.09%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      301.54 ms →      291.87 ms   (-3.21%) |       2   →       2              |      603.09 ms →      583.75 ms   (-3.21%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       35.22 ms →       35.53 ms   (+0.89%) |       1   →       1              |       35.22 ms →       35.53 ms   (+0.89%) | 
  │ ├ sirius::K_point::K_point                                          |        2.27 μs →        2.44 μs   (+7.64%) |       4   →       4              |        9.07 μs →        9.76 μs   (+7.64%) | 
  │ └ sirius::K_point_set::initialize                                   |       35.12 ms →       35.43 ms   (+0.90%) |       1   →       1              |       35.12 ms →       35.43 ms   (+0.90%) | 
  │   └ sirius::K_point::initialize                                     |       35.03 ms →       35.33 ms   (+0.86%) |       1   →       1              |       35.03 ms →       35.33 ms   (+0.86%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       17.97 ms →       17.98 ms   (+0.07%) |       1   →       1              |       17.97 ms →       17.98 ms   (+0.07%) | 
  │     │ └ sddk::Gvec::init                                            |        8.04 ms →        8.06 ms   (+0.20%) |       1   →       1              |        8.04 ms →        8.06 ms   (+0.20%) | 
+ │     ├ sddk::matrix_storage::matrix_storage                          |       10.48 μs →        9.38 μs  (-10.46%) |       1   →       1              |       10.48 μs →        9.38 μs  (-10.46%) | 
  │     └ sirius::K_point::update                                       |       12.30 ms →       12.52 ms   (+1.80%) |       1   →       1              |       12.30 ms →       12.52 ms   (+1.80%) | 
  │       └ sirius::Beta_projectors                                     |        6.09 ms →        6.29 ms   (+3.36%) |       1   →       1              |        6.09 ms →        6.29 ms   (+3.36%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.52 ms →        3.71 ms   (+5.41%) |       1   →       1              |        3.52 ms →        3.71 ms   (+5.41%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.12 ms →        5.54 ms   (+8.06%) |       2   →       2              |       10.25 ms →       11.07 ms   (+8.06%) | 
  ├ sirius::Potential                                                   |      153.59 ms →      161.95 ms   (+5.44%) |       1   →       1              |      153.59 ms →      161.95 ms   (+5.44%) | 
- │ ├ sirius::Smooth_periodic_function                                  |        5.80 ms →        6.40 ms  (+10.51%) |       6   →       6              |       34.78 ms →       38.43 ms  (+10.51%) | 
  │ └ sirius::Potential::update                                         |      118.06 ms →      122.74 ms   (+3.96%) |       1   →       1              |      118.06 ms →      122.74 ms   (+3.96%) | 
  │   └ sirius::Potential::generate_local_potential                     |      117.33 ms →      122.02 ms   (+3.99%) |       1   →       1              |      117.33 ms →      122.02 ms   (+3.99%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      110.19 ms →      114.65 ms   (+4.04%) |       1   →       1              |      110.19 ms →      114.65 ms   (+4.04%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        6.25 ms →        6.43 ms   (+2.89%) |       1   →       1              |        6.25 ms →        6.43 ms   (+2.89%) | 
  ├ sirius::Density                                                     |      130.90 ms →      134.88 ms   (+3.04%) |       1   →       1              |      130.90 ms →      134.88 ms   (+3.04%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.09 ms →        5.24 ms   (+2.92%) |       2   →       2              |       10.19 ms →       10.49 ms   (+2.92%) | 
  │ └ sirius::Density::update                                           |      120.44 ms →      124.12 ms   (+3.05%) |       1   →       1              |      120.44 ms →      124.12 ms   (+3.05%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      120.02 ms →      123.68 ms   (+3.05%) |       1   →       1              |      120.02 ms →      123.68 ms   (+3.05%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |      102.65 μs →      103.37 μs   (+0.70%) |       1   →       1              |      102.65 μs →      103.37 μs   (+0.70%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      112.48 ms →      117.90 ms   (+4.82%) |       1   →       1              |      112.48 ms →      117.90 ms   (+4.82%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        6.98 ms →        5.22 ms  (-25.21%) |       1   →       1              |        6.98 ms →        5.22 ms  (-25.21%) | 
  ├ sirius::Density::initial_density                                    |      163.67 ms →      177.67 ms   (+8.56%) |       1   →       1              |      163.67 ms →      177.67 ms   (+8.56%) | 
- │ ├ sirius::Simulation_context::make_periodic_function                |      110.36 ms →      122.09 ms  (+10.63%) |       1   →       1              |      110.36 ms →      122.09 ms  (+10.63%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.34 ms →        5.83 ms   (+9.14%) |       2   →       2              |       10.68 ms →       11.65 ms   (+9.14%) | 
- │ └ sirius::Periodic_function::integrate                              |       10.28 ms →       11.88 ms  (+15.54%) |       1   →       1              |       10.28 ms →       11.88 ms  (+15.54%) | 
  ├ sirius::Potential::generate                                         |      583.99 ms →      592.44 ms   (+1.45%) |       1   →       1              |      583.99 ms →      592.44 ms   (+1.45%) | 
  │ ├ sirius::Potential::poisson                                        |      126.43 ms →      137.15 ms   (+8.48%) |       1   →       1              |      126.43 ms →      137.15 ms   (+8.48%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.46 ms →        5.31 ms   (-2.67%) |       1   →       1              |        5.46 ms →        5.31 ms   (-2.67%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.34 ms →       10.67 ms   (+3.14%) |       1   →       1              |       10.34 ms →       10.67 ms   (+3.14%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        9.90 ms →       10.65 ms   (+7.57%) |       1   →       1              |        9.90 ms →       10.65 ms   (+7.57%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.89 ms →       10.64 ms   (+7.57%) |       1   →       1              |        9.89 ms →       10.64 ms   (+7.57%) | 
  │ ├ sirius::Periodic_function::add                                    |      555.14 μs →      570.27 μs   (+2.73%) |       2   →       2              |        1.11 ms →        1.14 ms   (+2.73%) | 
  │ ├ sirius::Potential::xc                                             |       54.86 ms →       53.89 ms   (-1.77%) |       1   →       1              |       54.86 ms →       53.89 ms   (-1.77%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       52.49 ms →       51.58 ms   (-1.74%) |       1   →       1              |       52.49 ms →       51.58 ms   (-1.74%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.66 ms →        5.75 ms   (+1.63%) |       2   →       2              |       11.31 ms →       11.50 ms   (+1.63%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.26 ms →        5.23 ms   (-0.64%) |       1   →       1              |        5.26 ms →        5.23 ms   (-0.64%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.85 ms →        5.86 ms   (+0.07%) |       1   →       1              |        5.85 ms →        5.86 ms   (+0.07%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       93.71 ms →       92.66 ms   (-1.13%) |       1   →       1              |       93.71 ms →       92.66 ms   (-1.13%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      300.65 ms →      300.38 ms   (-0.09%) |       1   →       1              |      300.65 ms →      300.38 ms   (-0.09%) | 
  ├ sirius::Hamiltonian0                                                |        8.45 ms →        8.40 ms   (-0.61%) |       1   →       1              |        8.45 ms →        8.40 ms   (-0.61%) | 
  │ ├ sirius::Local_operator                                            |        8.09 ms →        8.05 ms   (-0.44%) |       1   →       1              |        8.09 ms →        8.05 ms   (-0.44%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.72 ms →        4.75 ms   (+0.48%) |       1   →       1              |        4.72 ms →        4.75 ms   (+0.48%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.43 ms →        2.39 ms   (-1.87%) |       1   →       1              |        2.43 ms →        2.39 ms   (-1.87%) | 
  │ ├ sirius::Non_local_operator                                        |       62.90 μs →       62.31 μs   (-0.93%) |       2   →       2              |      125.79 μs →      124.62 μs   (-0.93%) | 
  │ ├ sirius::D_operator::initialize                                    |       94.60 μs →       95.28 μs   (+0.71%) |       1   →       1              |       94.60 μs →       95.28 μs   (+0.71%) | 
  │ └ sirius::Q_operator::initialize                                    |       79.17 μs →       75.36 μs   (-4.81%) |       1   →       1              |       79.17 μs →       75.36 μs   (-4.81%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.86 s  →        1.86 s    (+0.15%) |       1   →       1              |        1.86 s  →        1.86 s    (+0.15%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.12 ms →       18.65 ms   (+2.92%) |       1   →       1              |       18.12 ms →       18.65 ms   (+2.92%) | 
+ │ │ ├ sirius::Local_operator::prepare_k                               |      196.19 μs →      161.03 μs  (-17.92%) |       1   →       1              |      196.19 μs →      161.03 μs  (-17.92%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       17.92 ms →       18.49 ms   (+3.15%) |       1   →       1              |       17.92 ms →       18.49 ms   (+3.15%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.84 s  →        1.84 s    (+0.12%) |       1   →       1              |        1.84 s  →        1.84 s    (+0.12%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      128.05 ms →      125.83 ms   (-1.73%) |       4   →       4              |      512.20 ms →      503.33 ms   (-1.73%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       52.21 ms →       53.31 ms   (+2.09%) |       1   →       1              |       52.21 ms →       53.31 ms   (+2.09%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.18 ms →       21.50 ms   (+1.52%) |       1   →       1              |       21.18 ms →       21.50 ms   (+1.52%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      642.22 ms →      636.03 ms   (-0.96%) |       1   →       1              |      642.22 ms →      636.03 ms   (-0.96%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      302.56 ms →      297.76 ms   (-1.59%) |       1   →       1              |      302.56 ms →      297.76 ms   (-1.59%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.14 μs →        3.28 μs   (+4.33%) |       1   →       1              |        3.14 μs →        3.28 μs   (+4.33%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.29 μs →        2.43 μs   (+6.03%) |       1   →       1              |        2.29 μs →        2.43 μs   (+6.03%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      436.00 ns →      437.00 ns   (+0.23%) |       1   →       1              |      436.00 ns →      437.00 ns   (+0.23%) | 
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      630.00 ns →      527.00 ns  (-16.35%) |       1   →       1              |      630.00 ns →      527.00 ns  (-16.35%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.22 ms →        9.23 ms   (+0.06%) |       1   →       1              |        9.22 ms →        9.23 ms   (+0.06%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      121.29 ms →      120.93 ms   (-0.30%) |       1   →       1              |      121.29 ms →      120.93 ms   (-0.30%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      104.56 ms →      104.04 ms   (-0.49%) |       2   →       2              |      209.11 ms →      208.08 ms   (-0.49%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       40.61 ms →       40.21 ms   (-0.98%) |       2   →       2              |       81.21 ms →       80.42 ms   (-0.98%) | 
  │ │ │ └ sddk::wf_inner                                                |       40.07 ms →       39.65 ms   (-1.04%) |       2   →       2              |       80.13 ms →       79.30 ms   (-1.04%) | 
+ │ │ │   ├ sddk::wf_inner|scale                                        |       39.00 ns →       25.00 ns  (-35.90%) |       2   →       2              |       78.00 ns →       50.00 ns  (-35.90%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       39.61 ms →       39.17 ms   (-1.11%) |       2   →       2              |       79.22 ms →       78.34 ms   (-1.11%) | 
+ │ │ │   └ sddk::wf_inner|scale_back                                   |       28.00 ns →       19.50 ns  (-30.36%) |       2   →       2              |       56.00 ns →       39.00 ns  (-30.36%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       56.85 ms →       56.62 ms   (-0.41%) |       1   →       1              |       56.85 ms →       56.62 ms   (-0.41%) | 
  │ │ └ sddk::wf_trans                                                  |       30.82 ms →       30.77 ms   (-0.16%) |       1   →       1              |       30.82 ms →       30.77 ms   (-0.16%) | 
  │ │   └ sddk::wf_trans|pw                                             |       30.81 ms →       30.77 ms   (-0.16%) |       1   →       1              |       30.81 ms →       30.77 ms   (-0.16%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      443.00 ns →      395.00 ns  (-10.84%) |       1   →       1              |      443.00 ns →      395.00 ns  (-10.84%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      123.24 s  →      119.45 s    (-3.08%) |       1   →       1              |      123.24 s  →      119.45 s    (-3.08%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.81 ms →        5.82 ms   (+0.11%) |      19   →      19              |      110.38 ms →      110.50 ms   (+0.11%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.73 s  →        4.58 s    (-3.06%) |      26   →      26              |      122.88 s  →      119.12 s    (-3.06%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        4.85 ms →        4.44 ms   (-8.48%) |      26   →      26              |      126.07 ms →      115.38 ms   (-8.48%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.48 ms →        4.07 ms   (-9.11%) |      26   →      26              |      116.56 ms →      105.94 ms   (-9.11%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |        1.03 ms →      958.05 μs   (-6.60%) |      26   →      26              |       26.67 ms →       24.91 ms   (-6.60%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.57 ms →        2.23 ms  (-13.33%) |      26   →      26              |       66.80 ms →       57.89 ms  (-13.33%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.74 μs →       64.59 μs   (-0.23%) |      52   →      52              |        3.37 ms →        3.36 ms   (-0.23%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       86.40 μs →       87.08 μs   (+0.79%) |      26   →      26              |        2.25 ms →        2.26 ms   (+0.79%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       78.84 μs →       77.93 μs   (-1.16%) |      26   →      26              |        2.05 ms →        2.03 ms   (-1.16%) | 
  │ │ ├ sirius::Band::solve                                             |        2.75 s  →        2.60 s    (-5.67%) |      26   →      26              |       71.61 s  →       67.55 s    (-5.67%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      154.57 μs →      153.61 μs   (-0.62%) |      26   →      26              |        4.02 ms →        3.99 ms   (-0.62%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      148.06 μs →      147.04 μs   (-0.69%) |      26   →      26              |        3.85 ms →        3.82 ms   (-0.69%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.49 μs →        4.57 μs   (+1.84%) |      26   →      26              |      116.79 μs →      118.94 μs   (+1.84%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.62 s  →        2.48 s    (-5.67%) |      26   →      26              |       68.23 s  →       64.36 s    (-5.67%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       95.47 ms →       94.75 ms   (-0.75%) |      26   →      26              |        2.48 s  →        2.46 s    (-0.75%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.70 ms →        7.57 ms   (-1.66%) |     156   →     156              |        1.20 s  →        1.18 s    (-1.66%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        5.93 ms →        5.95 ms   (+0.23%) |      26   →      26              |      154.28 ms →      154.64 ms   (+0.23%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      348.17 μs →      354.02 μs   (+1.68%) |      26   →      26              |        9.05 ms →        9.20 ms   (+1.68%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.29 ms →        2.31 ms   (+0.89%) |      52   →      52              |      118.84 ms →      119.90 ms   (+0.89%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.49 s  →        2.34 s    (-5.96%) |      26   →      26              |       64.67 s  →       60.81 s    (-5.96%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      127.91 ms →      137.09 ms   (+7.18%) |     277   →     262     (-5.42%) |       35.43 s  →       35.92 s    (+1.37%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       50.83 ms →       55.94 ms  (+10.06%) |     277   →     262     (-5.42%) |       14.08 s  →       14.66 s    (+4.10%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.86 μs →        2.07 μs  (+11.52%) |     277   →     262     (-5.42%) |      514.93 μs →      543.16 μs   (+5.48%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.58 μs →        1.78 μs  (+12.41%) |     277   →     262     (-5.42%) |      438.87 μs →      466.63 μs   (+6.33%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      339.54 ns →      474.19 ns  (+39.66%) |     277   →     262     (-5.42%) |       94.05 μs →      124.24 μs  (+32.10%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      411.37 ns →      535.27 ns  (+30.12%) |     277   →     262     (-5.42%) |      113.95 μs →      140.24 μs  (+23.07%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.42 ms →        7.45 ms   (+0.42%) |     277   →     262     (-5.42%) |        2.06 s  →        1.95 s    (-5.02%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       23.55 ms →       24.90 ms   (+5.73%) |     277   →     262     (-5.42%) |        6.52 s  →        6.52 s    (+0.01%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       23.05 ms →       24.39 ms   (+5.83%) |     554   →     524     (-5.42%) |       12.77 s  →       12.78 s    (+0.10%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       34.40 ms →       35.84 ms   (+4.18%) |     277   →     262     (-5.42%) |        9.53 s  →        9.39 s    (-1.46%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        5.97 ms →        6.22 ms   (+4.05%) |     528   →     498     (-5.68%) |        3.15 s  →        3.10 s    (-1.86%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       65.57 ns →       44.37 ns  (-32.34%) |     528   →     498     (-5.68%) |       34.62 μs →       22.09 μs  (-36.18%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        4.86 ms →        5.11 ms   (+5.01%) |     528   →     498     (-5.68%) |        2.57 s  →        2.54 s    (-0.95%) | 
+ │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       52.44 ns →       28.87 ns  (-44.95%) |     528   →     498     (-5.68%) |       27.69 μs →       14.38 μs  (-48.08%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      613.70 μs →      656.41 μs   (+6.96%) |     277   →     262     (-5.42%) |      169.99 ms →      171.98 ms   (+1.17%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        9.58 ms →       10.31 ms   (+7.64%) |     277   →     262     (-5.42%) |        2.65 s  →        2.70 s    (+1.81%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |       14.15 ms →       14.49 ms   (+2.45%) |     251   →     236     (-5.98%) |        3.55 s  →        3.42 s    (-3.67%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        4.71 ms →        4.83 ms   (+2.45%) |     753   →     708     (-5.98%) |        3.55 s  →        3.42 s    (-3.67%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       10.36 ms →       10.38 ms   (+0.21%) |     277   →     262     (-5.42%) |        2.87 s  →        2.72 s    (-5.22%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |       10.09 ms →       10.17 ms   (+0.86%) |     277   →     262     (-5.42%) |        2.79 s  →        2.67 s    (-4.60%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       49.27 ns →       27.08 ns  (-45.04%) |     277   →     262     (-5.42%) |       13.65 μs →        7.09 μs  (-48.02%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        8.97 ms →        9.06 ms   (+1.00%) |     277   →     262     (-5.42%) |        2.49 s  →        2.37 s    (-4.47%) | 
+ │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       69.71 ns →       48.55 ns  (-30.36%) |     277   →     262     (-5.42%) |       19.31 μs →       12.72 μs  (-34.13%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       33.32 ms →       18.68 ms  (-43.93%) |     277   →     262     (-5.42%) |        9.23 s  →        4.89 s   (-46.97%) | 
  │ │ │ │   ├ sirius::residuals                                         |       13.53 ms →       13.16 ms   (-2.74%) |     268   →     252     (-5.97%) |        3.63 s  →        3.32 s    (-8.54%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       12.16 ms →       11.73 ms   (-3.57%) |     259   →     242     (-6.56%) |        3.15 s  →        2.84 s    (-9.90%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        6.08 ms →        5.86 ms   (-3.57%) |     518   →     484     (-6.56%) |        3.15 s  →        2.84 s    (-9.90%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.59 ms →        1.72 ms   (+7.86%) |     259   →     242     (-6.56%) |      412.17 ms →      415.40 ms   (+0.78%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       74.95 ms →       53.74 ms  (-28.30%) |      53   →      85    (+60.38%) |        3.97 s  →        4.57 s   (+14.99%) | 
- │ │ │ │     └ sddk::wf_trans                                          |       49.41 ms →       31.45 ms  (-36.34%) |      80   →     144    (+80.00%) |        3.95 s  →        4.53 s   (+14.58%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |       36.94 ms →       22.31 ms  (-39.60%) |     107   →     203    (+89.72%) |        3.95 s  →        4.53 s   (+14.58%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      852.31 ns →      454.31 ns  (-46.70%) |      26   →      26              |       22.16 μs →       11.81 μs  (-46.70%) | 
+ │ │ │ └ sirius::K_point_set::sync_band_energies                       |       38.75 μs →       34.69 μs  (-10.47%) |      26   →      26              |        1.01 ms →      901.92 μs  (-10.47%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      586.79 μs →      601.12 μs   (+2.44%) |      26   →      26              |       15.26 ms →       15.63 ms   (+2.44%) | 
  │ │ ├ sirius::Density::generate                                       |      778.35 ms →      772.40 ms   (-0.76%) |      26   →      26              |       20.24 s  →       20.08 s    (-0.76%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      403.56 ms →      403.20 ms   (-0.09%) |      26   →      26              |       10.49 s  →       10.48 s    (-0.09%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.66 μs →        8.50 μs   (-1.80%) |      26   →      26              |      225.10 μs →      221.05 μs   (-1.80%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        8.08 μs →        8.03 μs   (-0.64%) |      26   →      26              |      210.00 μs →      208.65 μs   (-0.64%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |      100.43 ms →      100.43 ms   (-0.00%) |      26   →      26              |        2.61 s  →        2.61 s    (-0.00%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.45 μs →        7.43 μs   (-0.28%) |      26   →      26              |      193.72 μs →      193.19 μs   (-0.28%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.12 ms →        7.12 ms   (-0.00%) |      26   →      26              |      185.12 ms →      185.11 ms   (-0.00%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       91.38 ms →       91.40 ms   (+0.02%) |      26   →      26              |        2.38 s  →        2.38 s    (+0.02%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      691.81 ns →      577.00 ns  (-16.60%) |      26   →      26              |       17.99 μs →       15.00 μs  (-16.60%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      163.18 ms →      163.24 ms   (+0.03%) |      26   →      26              |        4.24 s  →        4.24 s    (+0.03%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.65 ms →        1.64 ms   (-0.30%) |      26   →      26              |       42.85 ms →       42.72 ms   (-0.30%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.30 ms →       88.24 ms   (-0.07%) |      26   →      26              |        2.30 s  →        2.29 s    (-0.07%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.04 ms →       88.00 ms   (-0.05%) |      26   →      26              |        2.29 s  →        2.29 s    (-0.05%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      276.17 ms →      274.99 ms   (-0.43%) |      26   →      26              |        7.18 s  →        7.15 s    (-0.43%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      276.17 ms →      274.99 ms   (-0.43%) |      26   →      26              |        7.18 s  →        7.15 s    (-0.43%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       23.85 ms →       25.75 ms   (+7.96%) |      26   →      26              |      620.06 ms →      669.44 ms   (+7.96%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      228.48 ms →      224.80 ms   (-1.61%) |      26   →      26              |        5.94 s  →        5.84 s    (-1.61%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       22.63 ms →       23.24 ms   (+2.71%) |      26   →      26              |      588.37 ms →      604.29 ms   (+2.71%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       89.16 ms →       81.63 ms   (-8.44%) |      26   →      26              |        2.32 s  →        2.12 s    (-8.44%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        5.84 ms →        9.00 ms  (+54.12%) |      26   →      26              |      151.75 ms →      233.89 ms  (+54.12%) | 
  │ │ ├ sirius::Density::mix                                            |      218.66 ms →      221.19 ms   (+1.16%) |      26   →      26              |        5.69 s  →        5.75 s    (+1.16%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      954.59 μs →      974.55 μs   (+2.09%) |      26   →      26              |       24.82 ms →       25.34 ms   (+2.09%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.68 ms →       10.87 ms   (+1.77%) |     334   →     334              |        3.57 s  →        3.63 s    (+1.77%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.34 ms →       10.41 ms   (+0.72%) |     334   →     334              |        3.45 s  →        3.48 s    (+0.72%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.34 ms →       10.41 ms   (+0.71%) |     334   →     334              |        3.45 s  →        3.48 s    (+0.71%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        7.22 ms →        7.41 ms   (+2.61%) |      26   →      26              |      187.75 ms →      192.65 ms   (+2.61%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        6.37 ms →        6.59 ms   (+3.46%) |      26   →      26              |      165.54 ms →      171.26 ms   (+3.46%) | 
  │ │ ├ sirius::Potential::generate                                     |      566.92 ms →      579.43 ms   (+2.21%) |      26   →      26              |       14.74 s  →       15.07 s    (+2.21%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      126.05 ms →      137.48 ms   (+9.06%) |      26   →      26              |        3.28 s  →        3.57 s    (+9.06%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        5.32 ms →        5.24 ms   (-1.41%) |      26   →      26              |      138.27 ms →      136.32 ms   (-1.41%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.27 ms →       10.78 ms   (+5.00%) |      26   →      26              |      267.01 ms →      280.36 ms   (+5.00%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        9.98 ms →       10.44 ms   (+4.55%) |      26   →      26              |      259.57 ms →      271.38 ms   (+4.55%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        9.98 ms →       10.44 ms   (+4.55%) |      26   →      26              |      259.55 ms →      271.37 ms   (+4.55%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      552.25 μs →      567.18 μs   (+2.70%) |      52   →      52              |       28.72 ms →       29.49 ms   (+2.70%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       48.98 ms →       49.23 ms   (+0.52%) |      26   →      26              |        1.27 s  →        1.28 s    (+0.52%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.55 ms →       46.91 ms   (+0.77%) |      26   →      26              |        1.21 s  →        1.22 s    (+0.77%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.10 ms →        3.00 ms   (-3.35%) |      52   →      52              |      161.33 ms →      155.92 ms   (-3.35%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.19 ms →        5.39 ms   (+3.68%) |      26   →      26              |      135.04 ms →      140.02 ms   (+3.68%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.39 ms →        6.62 ms   (+3.71%) |      26   →      26              |      166.05 ms →      172.21 ms   (+3.71%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.89 ms →       90.98 ms   (+0.10%) |      26   →      26              |        2.36 s  →        2.37 s    (+0.10%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      292.18 ms →      292.70 ms   (+0.18%) |      26   →      26              |        7.60 s  →        7.61 s    (+0.18%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      282.14 ms →      279.64 ms   (-0.89%) |      26   →      26              |        7.34 s  →        7.27 s    (-0.89%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      282.14 ms →      279.64 ms   (-0.89%) |      26   →      26              |        7.34 s  →        7.27 s    (-0.89%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.17 ms →       28.37 ms   (+4.41%) |      26   →      26              |      706.47 ms →      737.65 ms   (+4.41%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      227.52 ms →      223.68 ms   (-1.69%) |      26   →      26              |        5.92 s  →        5.82 s    (-1.69%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.62 ms →       23.81 ms   (+0.78%) |      26   →      26              |      614.18 ms →      618.96 ms   (+0.78%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.48 ms →        7.97 ms  (+45.38%) |      26   →      26              |      142.49 ms →      207.15 ms  (+45.38%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.20 ms →       10.75 ms   (+5.42%) |     182   →     182              |        1.86 s  →        1.96 s    (+5.42%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.81 ms →       10.29 ms   (+4.87%) |     182   →     182              |        1.79 s  →        1.87 s    (+4.87%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.81 ms →       10.29 ms   (+4.87%) |     182   →     182              |        1.79 s  →        1.87 s    (+4.87%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       11.10 ms →       10.79 ms   (-2.80%) |      78   →      78              |      866.15 ms →      841.93 ms   (-2.80%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.65 ms →       10.23 ms   (-4.00%) |      78   →      78              |      831.03 ms →      797.79 ms   (-4.00%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |       10.00 ms →       10.09 ms   (+0.94%) |      26   →      26              |      260.02 ms →      262.46 ms   (+0.94%) | 
  │ │ └ sirius::Density::get_magnetisation                              |      114.50 μs →      118.89 μs   (+3.84%) |      26   →      26              |        2.98 ms →        3.09 ms   (+3.84%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |      109.75 μs →      114.20 μs   (+4.05%) |      26   →      26              |        2.85 ms →        2.97 ms   (+4.05%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.28 ms →        5.03 ms   (-4.59%) |       2   →       2              |       10.55 ms →       10.07 ms   (-4.59%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.04 ms →       10.24 ms   (+2.00%) |       6   →       6              |       60.22 ms →       61.42 ms   (+2.00%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        9.65 ms →       10.22 ms   (+5.94%) |       6   →       6              |       57.88 ms →       61.32 ms   (+5.94%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        9.65 ms →       10.22 ms   (+5.94%) |       6   →       6              |       57.88 ms →       61.32 ms   (+5.94%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.92 ms →       10.15 ms   (-6.99%) |       3   →       3              |       32.75 ms →       30.46 ms   (-6.99%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.72 ms →       10.11 ms   (-5.62%) |       3   →       3              |       32.15 ms →       30.34 ms   (-5.62%) | 
  ├ sirius::Periodic_function|inner                                     |        9.96 ms →       10.29 ms   (+3.32%) |       2   →       2              |       19.91 ms →       20.57 ms   (+3.32%) | 
  │ └ sirius::Periodic_function|inner_local                             |        9.71 ms →       10.26 ms   (+5.63%) |       2   →       2              |       19.42 ms →       20.51 ms   (+5.63%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.71 ms →       10.26 ms   (+5.63%) |       2   →       2              |       19.42 ms →       20.51 ms   (+5.63%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.82 ms →       10.21 ms   (-5.64%) |       1   →       1              |       10.82 ms →       10.21 ms   (-5.64%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.47 ms →       10.19 ms   (-2.67%) |       1   →       1              |       10.47 ms →       10.19 ms   (-2.67%) | 
  └ sirius::finalize                                                    |      237.35 ms →      223.66 ms   (-5.77%) |       1   →       1              |      237.35 ms →      223.66 ms   (-5.77%) | 
  ====================================================================================================================================================================================================
```
