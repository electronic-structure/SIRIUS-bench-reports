# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs a923c3c8853d846138a8b9a9c096494004b8d208
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      169.28 s  →      133.94 s   (-20.88%) |       1   →       1              |      169.28 s  →      133.94 s   (-20.88%) | 
  ├ sirius::initialize                                                  |        2.82 s  →        2.91 s    (+2.92%) |       1   →       1              |        2.82 s  →        2.91 s    (+2.92%) | 
  ├ sirius::Simulation_context::initialize                              |        3.01 s  →        2.96 s    (-1.42%) |       1   →       1              |        3.01 s  →        2.96 s    (-1.42%) | 
- │ ├ sirius::Simulation_context::init_comm                             |      199.20 μs →       74.44 ms (+37269.39%) |       1   →       1              |      199.20 μs →       74.44 ms (+37269.39%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      225.51 ms →      147.13 ms  (-34.76%) |       1   →       1              |      225.51 ms →      147.13 ms  (-34.76%) | 
+ │ │ ├ sirius::Atom_type::init                                         |      100.20 ms →       61.55 ms  (-38.58%) |       2   →       2              |      200.40 ms →      123.09 ms  (-38.58%) | 
  │ │ └ sirius::Unit_cell::update                                       |       25.01 ms →       23.96 ms   (-4.17%) |       1   →       1              |       25.01 ms →       23.96 ms   (-4.17%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.43 ms →        6.30 ms   (-2.01%) |       1   →       1              |        6.43 ms →        6.30 ms   (-2.01%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       18.54 ms →       17.62 ms   (-4.96%) |       1   →       1              |       18.54 ms →       17.62 ms   (-4.96%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       18.52 ms →       17.60 ms   (-4.95%) |       1   →       1              |       18.52 ms →       17.60 ms   (-4.95%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.15 ms →        4.14 ms   (-0.36%) |       1   →       1              |        4.15 ms →        4.14 ms   (-0.36%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.34 ms →        2.34 ms   (+0.31%) |       1   →       1              |        2.34 ms →        2.34 ms   (+0.31%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      101.92 μs →      105.08 μs   (+3.10%) |       1   →       1              |      101.92 μs →      105.08 μs   (+3.10%) | 
  │ └ sirius::Simulation_context::update                                |        2.74 s  →        2.70 s    (-1.43%) |       1   →       1              |        2.74 s  →        2.70 s    (-1.43%) | 
  │   ├ sirius::Unit_cell::update                                       |       11.03 ms →       10.84 ms   (-1.66%) |       1   →       1              |       11.03 ms →       10.84 ms   (-1.66%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.65 ms →        4.46 ms   (-3.97%) |       1   →       1              |        4.65 ms →        4.46 ms   (-3.97%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.35 ms →        6.35 ms   (+0.00%) |       1   →       1              |        6.35 ms →        6.35 ms   (+0.00%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.33 ms →        6.33 ms   (+0.03%) |       1   →       1              |        6.33 ms →        6.33 ms   (+0.03%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.82 ms →        3.84 ms   (+0.44%) |       1   →       1              |        3.82 ms →        3.84 ms   (+0.44%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.32 ms   (-0.00%) |       1   →       1              |        2.32 ms →        2.32 ms   (-0.00%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       98.93 μs →      100.62 μs   (+1.71%) |       1   →       1              |       98.93 μs →      100.62 μs   (+1.71%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       64.39 ms →       64.30 ms   (-0.15%) |       2   →       2              |      128.78 ms →      128.59 ms   (-0.15%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.17 ms →        5.15 ms   (-0.39%) |       2   →       2              |       10.33 ms →       10.29 ms   (-0.39%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.49 ms →        4.47 ms   (-0.53%) |       1   →       1              |        4.49 ms →        4.47 ms   (-0.53%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.83 ms →       21.92 ms   (+0.40%) |       2   →       2              |       43.67 ms →       43.84 ms   (+0.40%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       15.04 ms →       14.86 ms   (-1.20%) |       2   →       2              |       30.07 ms →       29.71 ms   (-1.20%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.94 ms →       19.86 ms   (-0.37%) |       4   →       4              |       79.75 ms →       79.46 ms   (-0.37%) | 
  │   ├ sddk::Gvec::init                                                |      182.86 ms →      176.98 ms   (-3.21%) |       2   →       2              |      365.71 ms →      353.97 ms   (-3.21%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      135.53 ms →      134.36 ms   (-0.86%) |       2   →       2              |      271.06 ms →      268.72 ms   (-0.86%) | 
+ │   ├ sddk::Gvec_shells                                               |      197.78 ms →      161.08 ms  (-18.56%) |       1   →       1              |      197.78 ms →      161.08 ms  (-18.56%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.36 ms →        1.31 ms   (-3.37%) |       1   →       1              |        1.36 ms →        1.31 ms   (-3.37%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      296.21 ms →      294.11 ms   (-0.71%) |       2   →       2              |      592.42 ms →      588.22 ms   (-0.71%) | 
+ ├ sirius::K_point_set::create_k_mesh                                  |       40.02 ms →       35.50 ms  (-11.30%) |       1   →       1              |       40.02 ms →       35.50 ms  (-11.30%) | 
+ │ ├ sirius::K_point::K_point                                          |        2.96 μs →        2.47 μs  (-16.41%) |       4   →       4              |       11.83 μs →        9.89 μs  (-16.41%) | 
+ │ └ sirius::K_point_set::initialize                                   |       39.92 ms →       35.39 ms  (-11.34%) |       1   →       1              |       39.92 ms →       35.39 ms  (-11.34%) | 
+ │   └ sirius::K_point::initialize                                     |       39.83 ms →       35.22 ms  (-11.57%) |       1   →       1              |       39.83 ms →       35.22 ms  (-11.57%) | 
+ │     ├ sirius::K_point::generate_gkvec                               |       20.99 ms →       17.97 ms  (-14.39%) |       1   →       1              |       20.99 ms →       17.97 ms  (-14.39%) | 
+ │     │ └ sddk::Gvec::init                                            |        9.02 ms →        8.04 ms  (-10.80%) |       1   →       1              |        9.02 ms →        8.04 ms  (-10.80%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        9.61 μs →        9.65 μs   (+0.40%) |       1   →       1              |        9.61 μs →        9.65 μs   (+0.40%) | 
  │     └ sirius::K_point::update                                       |       13.20 ms →       12.45 ms   (-5.69%) |       1   →       1              |       13.20 ms →       12.45 ms   (-5.69%) | 
  │       └ sirius::Beta_projectors                                     |        6.11 ms →        6.18 ms   (+1.03%) |       1   →       1              |        6.11 ms →        6.18 ms   (+1.03%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.48 ms →        3.58 ms   (+3.01%) |       1   →       1              |        3.48 ms →        3.58 ms   (+3.01%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.35 ms →        5.30 ms   (-0.98%) |       2   →       2              |       10.71 ms →       10.60 ms   (-0.98%) | 
  ├ sirius::Potential                                                   |      159.17 ms →      158.66 ms   (-0.32%) |       1   →       1              |      159.17 ms →      158.66 ms   (-0.32%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.91 ms →        5.77 ms   (-2.46%) |       6   →       6              |       35.48 ms →       34.61 ms   (-2.46%) | 
  │ └ sirius::Potential::update                                         |      122.94 ms →      123.32 ms   (+0.31%) |       1   →       1              |      122.94 ms →      123.32 ms   (+0.31%) | 
  │   └ sirius::Potential::generate_local_potential                     |      122.19 ms →      122.60 ms   (+0.33%) |       1   →       1              |      122.19 ms →      122.60 ms   (+0.33%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      113.13 ms →      114.85 ms   (+1.52%) |       1   →       1              |      113.13 ms →      114.85 ms   (+1.52%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        8.50 ms →        6.83 ms  (-19.66%) |       1   →       1              |        8.50 ms →        6.83 ms  (-19.66%) | 
  ├ sirius::Density                                                     |      130.70 ms →      136.69 ms   (+4.58%) |       1   →       1              |      130.70 ms →      136.69 ms   (+4.58%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.46 ms →        5.67 ms   (+3.86%) |       2   →       2              |       10.93 ms →       11.35 ms   (+3.86%) | 
  │ └ sirius::Density::update                                           |      119.49 ms →      125.05 ms   (+4.65%) |       1   →       1              |      119.49 ms →      125.05 ms   (+4.65%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      119.04 ms →      124.60 ms   (+4.67%) |       1   →       1              |      119.04 ms →      124.60 ms   (+4.67%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |                       116.68 μs            |                   1              |                       116.68 μs            | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      113.32 ms →      118.56 ms   (+4.62%) |       1   →       1              |      113.32 ms →      118.56 ms   (+4.62%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        5.26 ms →        5.49 ms   (+4.33%) |       1   →       1              |        5.26 ms →        5.49 ms   (+4.33%) | 
  ├ sirius::Density::initial_density                                    |      168.75 ms →      175.17 ms   (+3.80%) |       1   →       1              |      168.75 ms →      175.17 ms   (+3.80%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      111.37 ms →      122.36 ms   (+9.87%) |       1   →       1              |      111.37 ms →      122.36 ms   (+9.87%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.93 ms →        5.10 ms  (-14.07%) |       2   →       2              |       11.86 ms →       10.20 ms  (-14.07%) | 
+ │ └ sirius::Periodic_function::integrate                              |       12.74 ms →        9.96 ms  (-21.84%) |       1   →       1              |       12.74 ms →        9.96 ms  (-21.84%) | 
  ├ sirius::Potential::generate                                         |      575.38 ms →      592.99 ms   (+3.06%) |       1   →       1              |      575.38 ms →      592.99 ms   (+3.06%) | 
  │ ├ sirius::Potential::poisson                                        |      127.70 ms →      136.90 ms   (+7.21%) |       1   →       1              |      127.70 ms →      136.90 ms   (+7.21%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.27 ms →        5.33 ms   (+1.09%) |       1   →       1              |        5.27 ms →        5.33 ms   (+1.09%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.82 ms →       10.90 ms   (+0.74%) |       1   →       1              |       10.82 ms →       10.90 ms   (+0.74%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |       10.25 ms →       10.00 ms   (-2.50%) |       1   →       1              |       10.25 ms →       10.00 ms   (-2.50%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |       10.25 ms →        9.99 ms   (-2.56%) |       1   →       1              |       10.25 ms →        9.99 ms   (-2.56%) | 
  │ ├ sirius::Periodic_function::add                                    |      554.68 μs →      557.49 μs   (+0.51%) |       2   →       2              |        1.11 ms →        1.11 ms   (+0.51%) | 
  │ ├ sirius::Potential::xc                                             |       52.55 ms →       53.96 ms   (+2.68%) |       1   →       1              |       52.55 ms →       53.96 ms   (+2.68%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       52.54 ms →       51.67 ms   (-1.67%) |       1   →       1              |       52.54 ms →       51.67 ms   (-1.67%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.78 ms →        5.65 ms   (-2.24%) |       2   →       2              |       11.56 ms →       11.30 ms   (-2.24%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.14 ms →        5.34 ms   (+3.83%) |       1   →       1              |        5.14 ms →        5.34 ms   (+3.83%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.77 ms →        6.14 ms   (+6.37%) |       1   →       1              |        5.77 ms →        6.14 ms   (+6.37%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.75 ms →       92.71 ms   (-0.04%) |       1   →       1              |       92.75 ms →       92.71 ms   (-0.04%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      294.10 ms →      300.83 ms   (+2.29%) |       1   →       1              |      294.10 ms →      300.83 ms   (+2.29%) | 
  ├ sirius::Hamiltonian0                                                |        8.47 ms →        8.66 ms   (+2.26%) |       1   →       1              |        8.47 ms →        8.66 ms   (+2.26%) | 
  │ ├ sirius::Local_operator                                            |        8.11 ms →        8.31 ms   (+2.43%) |       1   →       1              |        8.11 ms →        8.31 ms   (+2.43%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.79 ms →        4.70 ms   (-1.94%) |       1   →       1              |        4.79 ms →        4.70 ms   (-1.94%) | 
- │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.40 ms →        2.70 ms  (+12.56%) |       1   →       1              |        2.40 ms →        2.70 ms  (+12.56%) | 
  │ ├ sirius::Non_local_operator                                        |       62.35 μs →       62.72 μs   (+0.60%) |       2   →       2              |      124.70 μs →      125.44 μs   (+0.60%) | 
  │ ├ sirius::D_operator::initialize                                    |      101.74 μs →       93.63 μs   (-7.97%) |       1   →       1              |      101.74 μs →       93.63 μs   (-7.97%) | 
  │ └ sirius::Q_operator::initialize                                    |       77.62 μs →       74.81 μs   (-3.63%) |       1   →       1              |       77.62 μs →       74.81 μs   (-3.63%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.87 s  →        1.88 s    (+0.79%) |       1   →       1              |        1.87 s  →        1.88 s    (+0.79%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.72 ms →       18.72 ms   (+0.03%) |       1   →       1              |       18.72 ms →       18.72 ms   (+0.03%) | 
+ │ │ ├ sirius::Local_operator::prepare_k                               |      210.65 μs →      182.23 μs  (-13.49%) |       1   →       1              |      210.65 μs →      182.23 μs  (-13.49%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       18.50 ms →       18.54 ms   (+0.18%) |       1   →       1              |       18.50 ms →       18.54 ms   (+0.18%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.85 s  →        1.86 s    (+0.79%) |       1   →       1              |        1.85 s  →        1.86 s    (+0.79%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      128.33 ms →      129.54 ms   (+0.94%) |       4   →       4              |      513.34 ms →      518.14 ms   (+0.94%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       54.02 ms →       53.18 ms   (-1.55%) |       1   →       1              |       54.02 ms →       53.18 ms   (-1.55%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.62 ms →       21.41 ms   (-1.00%) |       1   →       1              |       21.62 ms →       21.41 ms   (-1.00%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      638.45 ms →      636.53 ms   (-0.30%) |       1   →       1              |      638.45 ms →      636.53 ms   (-0.30%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      298.01 ms →      298.37 ms   (+0.12%) |       1   →       1              |      298.01 ms →      298.37 ms   (+0.12%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.64 μs →        2.76 μs  (-24.16%) |       1   →       1              |        3.64 μs →        2.76 μs  (-24.16%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.71 μs →        1.89 μs  (-30.23%) |       1   →       1              |        2.71 μs →        1.89 μs  (-30.23%) | 
+ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      446.00 ns →      384.00 ns  (-13.90%) |       1   →       1              |      446.00 ns →      384.00 ns  (-13.90%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      553.00 ns →      510.00 ns   (-7.78%) |       1   →       1              |      553.00 ns →      510.00 ns   (-7.78%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.22 ms →        9.22 ms   (-0.03%) |       1   →       1              |        9.22 ms →        9.22 ms   (-0.03%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      121.61 ms →      120.52 ms   (-0.89%) |       1   →       1              |      121.61 ms →      120.52 ms   (-0.89%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      104.78 ms →      104.19 ms   (-0.57%) |       2   →       2              |      209.56 ms →      208.38 ms   (-0.57%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       38.42 ms →       40.15 ms   (+4.51%) |       2   →       2              |       76.83 ms →       80.30 ms   (+4.51%) | 
  │ │ │ ├ sddk::inner                                                   |       37.82 ms                             |       2                          |       75.65 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       23.51 μs                             |       2                          |       47.01 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        39.61 ms            |                   2              |                        79.22 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        19.00 ns            |                   2              |                        38.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        39.15 ms            |                   2              |                        78.31 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                        23.00 ns            |                   2              |                        46.00 ns            | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       55.98 ms →       61.33 ms   (+9.57%) |       1   →       1              |       55.98 ms →       61.33 ms   (+9.57%) | 
  │ │ ├ sddk::transform                                                 |       31.55 ms                             |       1                          |       31.55 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       12.24 μs                             |       1                          |       12.24 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       12.08 μs                             |       1                          |       12.08 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                        30.74 ms            |                   1              |                        30.74 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                        30.73 ms            |                   1              |                        30.73 ms            | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      875.00 ns →      528.00 ns  (-39.66%) |       1   →       1              |      875.00 ns →      528.00 ns  (-39.66%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      159.11 s  →      124.06 s   (-22.03%) |       1   →       1              |      159.11 s  →      124.06 s   (-22.03%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.88 ms →        5.78 ms   (-1.64%) |      19   →      19              |      111.66 ms →      109.83 ms   (-1.64%) | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.54 s  →        4.95 s    (+9.09%) |      35   →      25    (-28.57%) |      158.74 s  →      123.70 s   (-22.08%) | 
+ │ │ ├ sirius::Hamiltonian0                                            |        4.77 ms →        4.46 ms   (-6.45%) |      35   →      25    (-28.57%) |      166.89 ms →      111.51 ms  (-33.18%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        4.39 ms →        4.09 ms   (-6.78%) |      35   →      25    (-28.57%) |      153.71 ms →      102.34 ms  (-33.42%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function                            |      963.56 μs →      927.30 μs   (-3.76%) |      35   →      25    (-28.57%) |       33.72 ms →       23.18 ms  (-31.26%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.54 ms →        2.28 ms  (-10.25%) |      35   →      25    (-28.57%) |       88.91 ms →       57.00 ms  (-35.89%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |       64.39 μs →       65.23 μs   (+1.30%) |      70   →      50    (-28.57%) |        4.51 ms →        3.26 ms  (-27.64%) | 
+ │ │ │ ├ sirius::D_operator::initialize                                |      102.94 μs →       88.20 μs  (-14.32%) |      35   →      25    (-28.57%) |        3.60 ms →        2.20 ms  (-38.80%) | 
+ │ │ │ └ sirius::Q_operator::initialize                                |       77.14 μs →       78.92 μs   (+2.32%) |      35   →      25    (-28.57%) |        2.70 ms →        1.97 ms  (-26.91%) | 
- │ │ ├ sirius::Band::solve                                             |        2.57 s  →        2.95 s   (+14.95%) |      35   →      25    (-28.57%) |       89.86 s  →       73.78 s   (-17.89%) | 
+ │ │ │ ├ sirius::Hamiltonian_k                                         |      161.25 μs →      153.88 μs   (-4.57%) |      35   →      25    (-28.57%) |        5.64 ms →        3.85 ms  (-31.83%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      154.84 μs →      146.46 μs   (-5.41%) |      35   →      25    (-28.57%) |        5.42 ms →        3.66 ms  (-32.44%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.88 μs →        5.53 μs  (+13.41%) |      35   →      25    (-28.57%) |      170.66 μs →      138.25 μs  (-18.99%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.50 s  →        2.70 s    (+8.15%) |      35   →      25    (-28.57%) |       87.50 s  →       67.59 s   (-22.75%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |      101.14 ms →       96.38 ms   (-4.71%) |      35   →      25    (-28.57%) |        3.54 s  →        2.41 s   (-31.94%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        8.53 ms →        7.99 ms   (-6.29%) |     210   →     150    (-28.57%) |        1.79 s  →        1.20 s   (-33.07%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        5.94 ms →        5.93 ms   (-0.10%) |      35   →      25    (-28.57%) |      207.81 ms →      148.29 ms  (-28.64%) | 
+ │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      351.89 μs →      350.80 μs   (-0.31%) |      35   →      25    (-28.57%) |       12.32 ms →        8.77 ms  (-28.79%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.27 ms →        2.31 ms   (+1.70%) |      70   →      50    (-28.57%) |      159.23 ms →      115.67 ms  (-27.36%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.36 s  →        2.57 s    (+8.85%) |      35   →      25    (-28.57%) |       82.50 s  →       64.14 s   (-22.25%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      107.07 ms →      125.25 ms  (+16.98%) |     362   →     277    (-23.48%) |       38.76 s  →       34.69 s   (-10.49%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       41.13 ms →       50.17 ms  (+21.97%) |     362   →     277    (-23.48%) |       14.89 s  →       13.90 s    (-6.67%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.96 μs →        2.00 μs   (+2.08%) |     362   →     277    (-23.48%) |      709.34 μs →      554.05 μs  (-21.89%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.59 μs →        1.72 μs   (+7.77%) |     362   →     277    (-23.48%) |      576.48 μs →      475.38 μs  (-17.54%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      327.61 ns →      369.67 ns  (+12.84%) |     362   →     277    (-23.48%) |      118.60 μs →      102.40 μs  (-13.66%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      398.09 ns →      464.08 ns  (+16.58%) |     362   →     277    (-23.48%) |      144.11 μs →      128.55 μs  (-10.80%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.35 ms →        7.42 ms   (+0.86%) |     362   →     277    (-23.48%) |        2.66 s  →        2.05 s   (-22.82%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       19.61 ms →       22.43 ms  (+14.39%) |     362   →     277    (-23.48%) |        7.10 s  →        6.21 s   (-12.47%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       19.49 ms →       22.61 ms  (+16.04%) |     724   →     554    (-23.48%) |       14.11 s  →       12.53 s   (-11.20%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |       29.67 ms →       34.01 ms  (+14.63%) |     362   →     277    (-23.48%) |       10.74 s  →        9.42 s   (-12.28%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        4.40 ms                             |     689                          |        3.03 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       20.84 μs                             |     689                          |       14.36 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                         5.90 ms            |                 529              |                         3.12 s             | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                        79.80 ns            |                 529              |                        42.22 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                         4.79 ms            |                 529              |                         2.53 s             | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                        51.28 ns            |                 529              |                        27.13 μs            | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      508.87 μs →      596.29 μs  (+17.18%) |     362   →     277    (-23.48%) |      184.21 ms →      165.17 ms  (-10.34%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        8.15 ms →        9.37 ms  (+14.99%) |     362   →     277    (-23.48%) |        2.95 s  →        2.59 s   (-12.01%) | 
  │ │ │ │   │ ├ sddk::transform                                         |       13.98 ms                             |     327                          |        4.57 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       18.14 μs                             |     327                          |        5.93 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       33.52 μs                             |     981                          |       32.88 ms                             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                        14.05 ms            |                 252              |                         3.54 s             | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                         4.68 ms            |                 756              |                         3.54 s             | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        9.31 ms →       10.23 ms   (+9.92%) |     362   →     277    (-23.48%) |        3.37 s  →        2.83 s   (-15.89%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        8.50 ms                             |     362                          |        3.08 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       25.95 μs                             |     362                          |        9.40 ms                             | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                         9.96 ms            |                 277              |                         2.76 s             | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                        46.12 ns            |                 277              |                        12.77 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                         8.85 ms            |                 277              |                         2.45 s             | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                        66.70 ns            |                 277              |                        18.48 μs            | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       63.02 ms →       34.94 ms  (-44.56%) |     362   →     277    (-23.48%) |       22.81 s  →        9.68 s   (-57.58%) | 
+ │ │ │ │   ├ sirius::residuals                                         |       13.71 ms →       13.29 ms   (-3.05%) |     350   →     268    (-23.43%) |        4.80 s  →        3.56 s   (-25.76%) | 
  │ │ │ │   │ ├ sddk::transform                                         |       12.69 ms                             |     336                          |        4.26 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       14.11 μs                             |     336                          |        4.74 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       35.26 μs                             |     672                          |       23.69 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                        11.99 ms            |                 258              |                         3.09 s             | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                         5.99 ms            |                 516              |                         3.09 s             | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.38 ms →        1.58 ms  (+14.47%) |     336   →     258    (-23.21%) |      462.51 ms →      406.53 ms  (-12.10%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       54.11 ms →       75.88 ms  (+40.24%) |      37   →      52    (+40.54%) |        2.00 s  →        3.95 s   (+97.09%) | 
  │ │ │ │     ├ sddk::transform                                         |       51.12 ms                             |      39                          |        1.99 s                              | 
  │ │ │ │     │ ├ sddk::transform|init                                  |       11.71 μs                             |      39                          |      456.55 μs                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       13.04 μs                             |      41                          |      534.61 μs                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                        49.72 ms            |                  79              |                         3.93 s             | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                        37.05 ms            |                 106              |                         3.93 s             | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      503.49 ns →      608.00 ns  (+20.76%) |      35   →      25    (-28.57%) |       17.62 μs →       15.20 μs  (-13.74%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       39.45 μs →       45.81 μs  (+16.13%) |      35   →      25    (-28.57%) |        1.38 ms →        1.15 ms  (-17.05%) | 
+ │ │ ├ sirius::K_point_set::find_band_occupancies                      |      617.87 μs →      590.91 μs   (-4.36%) |      35   →      25    (-28.57%) |       21.63 ms →       14.77 ms  (-31.69%) | 
+ │ │ ├ sirius::Density::generate                                       |      777.96 ms →      788.60 ms   (+1.37%) |      35   →      25    (-28.57%) |       27.23 s  →       19.71 s   (-27.60%) | 
+ │ │ │ ├ sirius::Density::generate_valence                             |      403.53 ms →      403.98 ms   (+0.11%) |      35   →      25    (-28.57%) |       14.12 s  →       10.10 s   (-28.49%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        7.97 μs →        8.55 μs   (+7.31%) |      35   →      25    (-28.57%) |      278.95 μs →      213.81 μs  (-23.35%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.12 μs →        7.95 μs  (+11.74%) |      35   →      25    (-28.57%) |      249.14 μs →      198.84 μs  (-20.19%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |      100.03 ms →      100.16 ms   (+0.14%) |      35   →      25    (-28.57%) |        3.50 s  →        2.50 s   (-28.47%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.46 μs →        7.82 μs   (+4.84%) |      35   →      25    (-28.57%) |      261.04 μs →      195.48 μs  (-25.12%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.12 ms →        7.12 ms   (+0.00%) |      35   →      25    (-28.57%) |      249.15 ms →      177.97 ms  (-28.57%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       91.05 ms →       91.13 ms   (+0.09%) |      35   →      25    (-28.57%) |        3.19 s  →        2.28 s   (-28.51%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      548.31 ns →      729.44 ns  (+33.03%) |      35   →      25    (-28.57%) |       19.19 μs →       18.24 μs   (-4.98%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      162.50 ms →      163.38 ms   (+0.54%) |      35   →      25    (-28.57%) |        5.69 s  →        4.08 s   (-28.18%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.65 ms →        1.64 ms   (-0.55%) |      35   →      25    (-28.57%) |       57.60 ms →       40.91 ms  (-28.97%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |       88.31 ms →       88.21 ms   (-0.11%) |      35   →      25    (-28.57%) |        3.09 s  →        2.21 s   (-28.65%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.07 ms →       87.98 ms   (-0.10%) |      35   →      25    (-28.57%) |        3.08 s  →        2.20 s   (-28.64%) | 
+ │ │ │ ├ sirius::Field4D::symmetrize                                   |      282.14 ms →      283.19 ms   (+0.37%) |      35   →      25    (-28.57%) |        9.87 s  →        7.08 s   (-28.31%) | 
+ │ │ │ │ └ sirius::symmetrize_function|fpw                             |      282.14 ms →      283.19 ms   (+0.37%) |      35   →      25    (-28.57%) |        9.87 s  →        7.08 s   (-28.31%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       28.82 ms →       24.10 ms  (-16.40%) |      35   →      25    (-28.57%) |        1.01 s  →      602.41 ms  (-40.29%) | 
+ │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      225.69 ms →      234.85 ms   (+4.06%) |      35   →      25    (-28.57%) |        7.90 s  →        5.87 s   (-25.67%) | 
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       26.45 ms →       23.06 ms  (-12.82%) |      35   →      25    (-28.57%) |      925.88 ms →      576.53 ms  (-37.73%) | 
- │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       81.22 ms →       92.46 ms  (+13.85%) |      35   →      25    (-28.57%) |        2.84 s  →        2.31 s   (-18.68%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        7.48 ms →        5.37 ms  (-28.29%) |      35   →      25    (-28.57%) |      261.91 ms →      134.16 ms  (-48.78%) | 
+ │ │ ├ sirius::Density::mix                                            |      216.42 ms →      215.27 ms   (-0.53%) |      35   →      25    (-28.57%) |        7.57 s  →        5.38 s   (-28.95%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      934.59 μs →      953.43 μs   (+2.02%) |      35   →      25    (-28.57%) |       32.71 ms →       23.84 ms  (-27.13%) | 
+ │ │ │ ├ sirius::Periodic_function|inner                               |       10.36 ms →       10.61 ms   (+2.42%) |     455   →     319    (-29.89%) |        4.71 s  →        3.38 s   (-28.19%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.07 ms →       10.35 ms   (+2.81%) |     455   →     319    (-29.89%) |        4.58 s  →        3.30 s   (-27.92%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.07 ms →       10.35 ms   (+2.81%) |     455   →     319    (-29.89%) |        4.58 s  →        3.30 s   (-27.92%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        6.77 ms →        6.90 ms   (+1.84%) |      35   →      25    (-28.57%) |      237.05 ms →      172.43 ms  (-27.26%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.95 ms →        6.10 ms   (+2.47%) |      35   →      25    (-28.57%) |      208.21 ms →      152.40 ms  (-26.80%) | 
+ │ │ ├ sirius::Potential::generate                                     |      560.95 ms →      578.18 ms   (+3.07%) |      35   →      25    (-28.57%) |       19.63 s  →       14.45 s   (-26.38%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |      127.38 ms →      136.16 ms   (+6.89%) |      35   →      25    (-28.57%) |        4.46 s  →        3.40 s   (-23.65%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        5.18 ms →        5.28 ms   (+1.96%) |      35   →      25    (-28.57%) |      181.14 ms →      131.93 ms  (-27.17%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner                             |       10.46 ms →       10.15 ms   (-2.96%) |      35   →      25    (-28.57%) |      366.05 ms →      253.72 ms  (-30.69%) | 
+ │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.17 ms →       10.01 ms   (-1.60%) |      35   →      25    (-28.57%) |      356.09 ms →      250.29 ms  (-29.71%) | 
+ │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.17 ms →       10.01 ms   (-1.60%) |      35   →      25    (-28.57%) |      356.07 ms →      250.27 ms  (-29.71%) | 
+ │ │ │ ├ sirius::Periodic_function::add                                |      556.32 μs →      546.85 μs   (-1.70%) |      70   →      50    (-28.57%) |       38.94 ms →       27.34 ms  (-29.79%) | 
+ │ │ │ ├ sirius::Potential::xc                                         |       46.48 ms →       48.90 ms   (+5.21%) |      35   →      25    (-28.57%) |        1.63 s  →        1.22 s   (-24.85%) | 
+ │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.48 ms →       46.62 ms   (+0.31%) |      35   →      25    (-28.57%) |        1.63 s  →        1.17 s   (-28.35%) | 
+ │ │ │ │   ├ sirius::Smooth_periodic_function                          |        2.99 ms →        2.97 ms   (-0.80%) |      70   →      50    (-28.57%) |      209.42 ms →      148.39 ms  (-29.15%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.35 ms →        5.45 ms   (+1.80%) |      35   →      25    (-28.57%) |      187.27 ms →      136.17 ms  (-27.29%) | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.45 ms →        6.47 ms   (+0.37%) |      35   →      25    (-28.57%) |      225.72 ms →      161.83 ms  (-28.31%) | 
+ │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.94 ms →       90.98 ms   (+0.05%) |      35   →      25    (-28.57%) |        3.18 s  →        2.27 s   (-28.54%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      287.27 ms →      293.31 ms   (+2.10%) |      35   →      25    (-28.57%) |       10.05 s  →        7.33 s   (-27.07%) | 
+ │ │ ├ sirius::Field4D::symmetrize                                     |      287.20 ms →      288.27 ms   (+0.37%) |      35   →      25    (-28.57%) |       10.05 s  →        7.21 s   (-28.31%) | 
+ │ │ │ └ sirius::symmetrize_function|fpw                               |      287.20 ms →      288.27 ms   (+0.37%) |      35   →      25    (-28.57%) |       10.05 s  →        7.21 s   (-28.31%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       31.31 ms →       27.14 ms  (-13.33%) |      35   →      25    (-28.57%) |        1.10 s  →      678.54 ms  (-38.09%) | 
+ │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      224.27 ms →      233.10 ms   (+3.94%) |      35   →      25    (-28.57%) |        7.85 s  →        5.83 s   (-25.76%) | 
+ │ │ │   └ sddk::Gvec_shells::remap_backward                           |       27.82 ms →       24.25 ms  (-12.85%) |      35   →      25    (-28.57%) |      973.87 ms →      606.23 ms  (-37.75%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.35 ms →        5.35 ms   (-0.02%) |      35   →      25    (-28.57%) |      187.23 ms →      133.71 ms  (-28.58%) | 
+ │ │ ├ sirius::Periodic_function|inner                                 |       10.28 ms →       10.37 ms   (+0.89%) |     245   →     175    (-28.57%) |        2.52 s  →        1.82 s   (-27.93%) | 
+ │ │ │ └ sirius::Periodic_function|inner_local                         |        9.89 ms →        9.78 ms   (-1.17%) |     245   →     175    (-28.57%) |        2.42 s  →        1.71 s   (-29.41%) | 
+ │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.89 ms →        9.78 ms   (-1.17%) |     245   →     175    (-28.57%) |        2.42 s  →        1.71 s   (-29.41%) | 
+ │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.57 ms →       10.98 ms   (+3.83%) |     105   →      75    (-28.57%) |        1.11 s  →      823.29 ms  (-25.83%) | 
+ │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.23 ms →       10.57 ms   (+3.40%) |     105   →      75    (-28.57%) |        1.07 s  →      793.06 ms  (-26.14%) | 
+ │ │ ├ sirius::Periodic_function::integrate                            |       10.73 ms →        9.95 ms   (-7.24%) |      35   →      25    (-28.57%) |      375.54 ms →      248.82 ms  (-33.74%) | 
+ │ │ └ sirius::Density::get_magnetisation                              |      125.87 μs →      131.34 μs   (+4.34%) |      35   →      25    (-28.57%) |        4.41 ms →        3.28 ms  (-25.47%) | 
+ │ │   └ sirius::Density::compute_atomic_mag_mom                       |      120.44 μs →      126.44 μs   (+4.98%) |      35   →      25    (-28.57%) |        4.22 ms →        3.16 ms  (-25.02%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.12 ms →        5.10 ms   (-0.34%) |       2   →       2              |       10.24 ms →       10.20 ms   (-0.34%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.79 ms →        9.87 ms   (-8.54%) |       6   →       6              |       64.75 ms →       59.22 ms   (-8.54%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.34 ms →        9.81 ms   (-5.19%) |       6   →       6              |       62.06 ms →       58.84 ms   (-5.19%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.34 ms →        9.81 ms   (-5.19%) |       6   →       6              |       62.06 ms →       58.84 ms   (-5.19%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.73 ms →       10.57 ms   (-1.45%) |       3   →       3              |       32.18 ms →       31.72 ms   (-1.45%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.42 ms →       10.49 ms   (+0.68%) |       3   →       3              |       31.27 ms →       31.48 ms   (+0.68%) | 
  ├ sirius::Periodic_function|inner                                     |       10.02 ms →        9.77 ms   (-2.48%) |       2   →       2              |       20.03 ms →       19.54 ms   (-2.48%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.01 ms →        9.74 ms   (-2.69%) |       2   →       2              |       20.02 ms →       19.48 ms   (-2.69%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.01 ms →        9.74 ms   (-2.69%) |       2   →       2              |       20.02 ms →       19.48 ms   (-2.69%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.45 ms →       10.53 ms   (+0.81%) |       1   →       1              |       10.45 ms →       10.53 ms   (+0.81%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.44 ms →       10.47 ms   (+0.26%) |       1   →       1              |       10.44 ms →       10.47 ms   (+0.26%) | 
+ └ sirius::finalize                                                    |      217.32 ms →      189.39 ms  (-12.85%) |       1   →       1              |      217.32 ms →      189.39 ms  (-12.85%) | 
  ====================================================================================================================================================================================================
```
