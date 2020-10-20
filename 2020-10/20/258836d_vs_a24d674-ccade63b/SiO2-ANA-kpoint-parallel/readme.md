# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs 258836d5fa5c76a93fd859e0c659f3d24f54ca95
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      160.45 s  →      129.51 s   (-19.28%) |       1   →       1              |      160.45 s  →      129.51 s   (-19.28%) | 
  ├ sirius::initialize                                                  |        2.64 s  →        2.66 s    (+0.43%) |       1   →       1              |        2.64 s  →        2.66 s    (+0.43%) | 
  ├ sirius::Simulation_context::initialize                              |        3.01 s  →        2.93 s    (-2.61%) |       1   →       1              |        3.01 s  →        2.93 s    (-2.61%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |      327.63 μs →      197.49 μs  (-39.72%) |       1   →       1              |      327.63 μs →      197.49 μs  (-39.72%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      204.01 ms →      172.14 ms  (-15.62%) |       1   →       1              |      204.01 ms →      172.14 ms  (-15.62%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       90.36 ms →       73.84 ms  (-18.29%) |       2   →       2              |      180.72 ms →      147.67 ms  (-18.29%) | 
  │ │ └ sirius::Unit_cell::update                                       |       23.22 ms →       24.38 ms   (+4.98%) |       1   →       1              |       23.22 ms →       24.38 ms   (+4.98%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.37 ms →        6.29 ms   (-1.21%) |       1   →       1              |        6.37 ms →        6.29 ms   (-1.21%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       16.81 ms →       18.04 ms   (+7.33%) |       1   →       1              |       16.81 ms →       18.04 ms   (+7.33%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       16.78 ms →       18.02 ms   (+7.36%) |       1   →       1              |       16.78 ms →       18.02 ms   (+7.36%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.14 ms →        4.15 ms   (+0.14%) |       1   →       1              |        4.14 ms →        4.15 ms   (+0.14%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.34 ms →        2.35 ms   (+0.72%) |       1   →       1              |        2.34 ms →        2.35 ms   (+0.72%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      102.48 μs →      106.06 μs   (+3.49%) |       1   →       1              |      102.48 μs →      106.06 μs   (+3.49%) | 
  │ └ sirius::Simulation_context::update                                |        2.76 s  →        2.71 s    (-1.58%) |       1   →       1              |        2.76 s  →        2.71 s    (-1.58%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.85 ms →       10.67 ms   (-1.68%) |       1   →       1              |       10.85 ms →       10.67 ms   (-1.68%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.45 ms →        4.25 ms   (-4.52%) |       1   →       1              |        4.45 ms →        4.25 ms   (-4.52%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.37 ms →        6.39 ms   (+0.32%) |       1   →       1              |        6.37 ms →        6.39 ms   (+0.32%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.35 ms →        6.37 ms   (+0.32%) |       1   →       1              |        6.35 ms →        6.37 ms   (+0.32%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.85 ms →        3.88 ms   (+0.98%) |       1   →       1              |        3.85 ms →        3.88 ms   (+0.98%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.32 ms   (+0.11%) |       1   →       1              |        2.32 ms →        2.32 ms   (+0.11%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       99.86 μs →      101.33 μs   (+1.47%) |       1   →       1              |       99.86 μs →      101.33 μs   (+1.47%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       62.82 ms →       62.33 ms   (-0.78%) |       2   →       2              |      125.64 ms →      124.67 ms   (-0.78%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.16 ms →        5.14 ms   (-0.38%) |       2   →       2              |       10.32 ms →       10.28 ms   (-0.38%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.47 ms →        4.48 ms   (+0.26%) |       1   →       1              |        4.47 ms →        4.48 ms   (+0.26%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.76 ms →       21.94 ms   (+0.85%) |       2   →       2              |       43.51 ms →       43.88 ms   (+0.85%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.80 ms →       14.82 ms   (+0.07%) |       2   →       2              |       29.61 ms →       29.63 ms   (+0.07%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.83 ms →       19.68 ms   (-0.77%) |       4   →       4              |       79.34 ms →       78.72 ms   (-0.77%) | 
  │   ├ sddk::Gvec::init                                                |      187.32 ms →      172.70 ms   (-7.80%) |       2   →       2              |      374.64 ms →      345.41 ms   (-7.80%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      139.79 ms →      129.38 ms   (-7.45%) |       2   →       2              |      279.57 ms →      258.75 ms   (-7.45%) | 
+ │   ├ sddk::Gvec_shells                                               |      205.18 ms →      163.25 ms  (-20.43%) |       1   →       1              |      205.18 ms →      163.25 ms  (-20.43%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.33 ms →        1.34 ms   (+0.10%) |       1   →       1              |        1.33 ms →        1.34 ms   (+0.10%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      291.51 ms →      293.12 ms   (+0.55%) |       2   →       2              |      583.02 ms →      586.25 ms   (+0.55%) | 
+ ├ sirius::K_point_set::create_k_mesh                                  |       43.12 ms →       35.54 ms  (-17.59%) |       1   →       1              |       43.12 ms →       35.54 ms  (-17.59%) | 
- │ ├ sirius::K_point::K_point                                          |        2.23 μs →        2.49 μs  (+11.63%) |       4   →       4              |        8.92 μs →        9.96 μs  (+11.63%) | 
+ │ └ sirius::K_point_set::initialize                                   |       43.02 ms →       35.44 ms  (-17.64%) |       1   →       1              |       43.02 ms →       35.44 ms  (-17.64%) | 
+ │   └ sirius::K_point::initialize                                     |       42.92 ms →       35.34 ms  (-17.67%) |       1   →       1              |       42.92 ms →       35.34 ms  (-17.67%) | 
+ │     ├ sirius::K_point::generate_gkvec                               |       22.39 ms →       18.01 ms  (-19.56%) |       1   →       1              |       22.39 ms →       18.01 ms  (-19.56%) | 
+ │     │ └ sddk::Gvec::init                                            |        9.99 ms →        8.20 ms  (-17.92%) |       1   →       1              |        9.99 ms →        8.20 ms  (-17.92%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        9.95 μs →       10.72 μs   (+7.72%) |       1   →       1              |        9.95 μs →       10.72 μs   (+7.72%) | 
+ │     └ sirius::K_point::update                                       |       14.28 ms →       12.53 ms  (-12.22%) |       1   →       1              |       14.28 ms →       12.53 ms  (-12.22%) | 
  │       └ sirius::Beta_projectors                                     |        6.41 ms →        6.19 ms   (-3.40%) |       1   →       1              |        6.41 ms →        6.19 ms   (-3.40%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.81 ms →        3.54 ms   (-7.22%) |       1   →       1              |        3.81 ms →        3.54 ms   (-7.22%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.36 ms →        5.27 ms   (-1.75%) |       2   →       2              |       10.72 ms →       10.53 ms   (-1.75%) | 
  ├ sirius::Potential                                                   |      167.95 ms →      159.21 ms   (-5.21%) |       1   →       1              |      167.95 ms →      159.21 ms   (-5.21%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.90 ms →        5.88 ms   (-0.34%) |       6   →       6              |       35.42 ms →       35.30 ms   (-0.34%) | 
  │ └ sirius::Potential::update                                         |      131.81 ms →      123.16 ms   (-6.57%) |       1   →       1              |      131.81 ms →      123.16 ms   (-6.57%) | 
  │   └ sirius::Potential::generate_local_potential                     |      131.01 ms →      122.41 ms   (-6.57%) |       1   →       1              |      131.01 ms →      122.41 ms   (-6.57%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      113.55 ms →      115.13 ms   (+1.39%) |       1   →       1              |      113.55 ms →      115.13 ms   (+1.39%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       16.91 ms →        6.38 ms  (-62.28%) |       1   →       1              |       16.91 ms →        6.38 ms  (-62.28%) | 
  ├ sirius::Density                                                     |      141.09 ms →      135.97 ms   (-3.63%) |       1   →       1              |      141.09 ms →      135.97 ms   (-3.63%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.24 ms →        5.20 ms   (-0.95%) |       2   →       2              |       10.49 ms →       10.39 ms   (-0.95%) | 
  │ └ sirius::Density::update                                           |      130.29 ms →      125.30 ms   (-3.83%) |       1   →       1              |      130.29 ms →      125.30 ms   (-3.83%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      129.85 ms →      124.88 ms   (-3.83%) |       1   →       1              |      129.85 ms →      124.88 ms   (-3.83%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |                       103.18 μs            |                   1              |                       103.18 μs            | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      113.04 ms →      119.17 ms   (+5.42%) |       1   →       1              |      113.04 ms →      119.17 ms   (+5.42%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       16.34 ms →        5.15 ms  (-68.50%) |       1   →       1              |       16.34 ms →        5.15 ms  (-68.50%) | 
  ├ sirius::Density::initial_density                                    |      175.20 ms →      176.00 ms   (+0.46%) |       1   →       1              |      175.20 ms →      176.00 ms   (+0.46%) | 
- │ ├ sirius::Simulation_context::make_periodic_function                |      111.65 ms →      123.48 ms  (+10.60%) |       1   →       1              |      111.65 ms →      123.48 ms  (+10.60%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |       10.39 ms →        5.03 ms  (-51.60%) |       2   →       2              |       20.78 ms →       10.06 ms  (-51.60%) | 
  │ └ sirius::Periodic_function::integrate                              |       10.69 ms →       10.05 ms   (-6.00%) |       1   →       1              |       10.69 ms →       10.05 ms   (-6.00%) | 
  ├ sirius::Potential::generate                                         |      583.80 ms →      594.54 ms   (+1.84%) |       1   →       1              |      583.80 ms →      594.54 ms   (+1.84%) | 
  │ ├ sirius::Potential::poisson                                        |      136.30 ms →      137.65 ms   (+0.99%) |       1   →       1              |      136.30 ms →      137.65 ms   (+0.99%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       15.04 ms →        5.30 ms  (-64.77%) |       1   →       1              |       15.04 ms →        5.30 ms  (-64.77%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        9.97 ms →       10.89 ms   (+9.19%) |       1   →       1              |        9.97 ms →       10.89 ms   (+9.19%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        9.93 ms →        9.92 ms   (-0.07%) |       1   →       1              |        9.93 ms →        9.92 ms   (-0.07%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.93 ms →        9.92 ms   (-0.13%) |       1   →       1              |        9.93 ms →        9.92 ms   (-0.13%) | 
  │ ├ sirius::Periodic_function::add                                    |      560.93 μs →      551.67 μs   (-1.65%) |       2   →       2              |        1.12 ms →        1.10 ms   (-1.65%) | 
  │ ├ sirius::Potential::xc                                             |       51.75 ms →       55.92 ms   (+8.05%) |       1   →       1              |       51.75 ms →       55.92 ms   (+8.05%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.75 ms →       53.48 ms   (+3.35%) |       1   →       1              |       51.75 ms →       53.48 ms   (+3.35%) | 
- │ │   ├ sirius::Smooth_periodic_function                              |        5.67 ms →        6.27 ms  (+10.62%) |       2   →       2              |       11.34 ms →       12.54 ms  (+10.62%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.02 ms →        5.14 ms   (+2.42%) |       1   →       1              |        5.02 ms →        5.14 ms   (+2.42%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.93 ms →        5.95 ms   (+0.29%) |       1   →       1              |        5.93 ms →        5.95 ms   (+0.29%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.81 ms →       92.71 ms   (-0.10%) |       1   →       1              |       92.81 ms →       92.71 ms   (-0.10%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      294.50 ms →      299.81 ms   (+1.80%) |       1   →       1              |      294.50 ms →      299.81 ms   (+1.80%) | 
  ├ sirius::Hamiltonian0                                                |        8.44 ms →        8.67 ms   (+2.71%) |       1   →       1              |        8.44 ms →        8.67 ms   (+2.71%) | 
  │ ├ sirius::Local_operator                                            |        8.10 ms →        8.31 ms   (+2.70%) |       1   →       1              |        8.10 ms →        8.31 ms   (+2.70%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.83 ms →        4.74 ms   (-1.86%) |       1   →       1              |        4.83 ms →        4.74 ms   (-1.86%) | 
- │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.34 ms →        2.65 ms  (+13.46%) |       1   →       1              |        2.34 ms →        2.65 ms  (+13.46%) | 
  │ ├ sirius::Non_local_operator                                        |       62.46 μs →       61.65 μs   (-1.31%) |       2   →       2              |      124.93 μs →      123.29 μs   (-1.31%) | 
  │ ├ sirius::D_operator::initialize                                    |       92.08 μs →       96.04 μs   (+4.30%) |       1   →       1              |       92.08 μs →       96.04 μs   (+4.30%) | 
  │ └ sirius::Q_operator::initialize                                    |       73.33 μs →       79.99 μs   (+9.08%) |       1   →       1              |       73.33 μs →       79.99 μs   (+9.08%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.84 s  →        1.86 s    (+0.79%) |       1   →       1              |        1.84 s  →        1.86 s    (+0.79%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.62 ms →       18.61 ms   (-0.07%) |       1   →       1              |       18.62 ms →       18.61 ms   (-0.07%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      182.20 μs →      184.18 μs   (+1.09%) |       1   →       1              |      182.20 μs →      184.18 μs   (+1.09%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       18.44 ms →       18.42 ms   (-0.08%) |       1   →       1              |       18.44 ms →       18.42 ms   (-0.08%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.83 s  →        1.84 s    (+0.80%) |       1   →       1              |        1.83 s  →        1.84 s    (+0.80%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      124.97 ms →      127.61 ms   (+2.11%) |       4   →       4              |      499.87 ms →      510.43 ms   (+2.11%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       52.36 ms →       52.17 ms   (-0.37%) |       1   →       1              |       52.36 ms →       52.17 ms   (-0.37%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.03 ms →       21.17 ms   (+0.67%) |       1   →       1              |       21.03 ms →       21.17 ms   (+0.67%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      633.94 ms →      637.57 ms   (+0.57%) |       1   →       1              |      633.94 ms →      637.57 ms   (+0.57%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      297.11 ms →      297.01 ms   (-0.03%) |       1   →       1              |      297.11 ms →      297.01 ms   (-0.03%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.81 μs →        3.17 μs  (-16.81%) |       1   →       1              |        3.81 μs →        3.17 μs  (-16.81%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.88 μs →        1.97 μs  (-31.75%) |       1   →       1              |        2.88 μs →        1.97 μs  (-31.75%) | 
+ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      415.00 ns →      366.00 ns  (-11.81%) |       1   →       1              |      415.00 ns →      366.00 ns  (-11.81%) | 
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      997.00 ns →      564.00 ns  (-43.43%) |       1   →       1              |      997.00 ns →      564.00 ns  (-43.43%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.23 ms →        9.23 ms   (-0.11%) |       1   →       1              |        9.23 ms →        9.23 ms   (-0.11%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      120.63 ms →      122.03 ms   (+1.16%) |       1   →       1              |      120.63 ms →      122.03 ms   (+1.16%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      103.47 ms →      104.64 ms   (+1.13%) |       2   →       2              |      206.94 ms →      209.28 ms   (+1.13%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       38.39 ms →       40.23 ms   (+4.79%) |       2   →       2              |       76.78 ms →       80.46 ms   (+4.79%) | 
  │ │ │ ├ sddk::inner                                                   |       37.85 ms                             |       2                          |       75.69 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       23.63 μs                             |       2                          |       47.26 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        39.67 ms            |                   2              |                        79.33 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        29.00 ns            |                   2              |                        58.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        39.20 ms            |                   2              |                        78.39 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                        24.00 ns            |                   2              |                        48.00 ns            | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       55.87 ms →       56.28 ms   (+0.72%) |       1   →       1              |       55.87 ms →       56.28 ms   (+0.72%) | 
  │ │ ├ sddk::transform                                                 |       31.55 ms                             |       1                          |       31.55 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       11.47 μs                             |       1                          |       11.47 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       12.26 μs                             |       1                          |       12.26 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                        30.75 ms            |                   1              |                        30.75 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                        30.75 ms            |                   1              |                        30.75 ms            | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      637.00 ns →      431.00 ns  (-32.34%) |       1   →       1              |      637.00 ns →      431.00 ns  (-32.34%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      150.39 s  →      119.86 s   (-20.30%) |       1   →       1              |      150.39 s  →      119.86 s   (-20.30%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.85 ms →        5.85 ms   (-0.07%) |      19   →      19              |      111.20 ms →      111.13 ms   (-0.07%) | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.69 s  →        4.59 s    (-1.99%) |      32   →      26    (-18.75%) |      150.01 s  →      119.45 s   (-20.37%) | 
+ │ │ ├ sirius::Hamiltonian0                                            |        4.84 ms →        4.82 ms   (-0.28%) |      32   →      26    (-18.75%) |      154.73 ms →      125.36 ms  (-18.98%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        4.47 ms →        4.45 ms   (-0.41%) |      32   →      26    (-18.75%) |      143.03 ms →      115.73 ms  (-19.08%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function                            |      978.75 μs →      955.42 μs   (-2.38%) |      32   →      26    (-18.75%) |       31.32 ms →       24.84 ms  (-20.69%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.60 ms →        2.61 ms   (+0.26%) |      32   →      26    (-18.75%) |       83.15 ms →       67.74 ms  (-18.54%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |       64.05 μs →       64.12 μs   (+0.11%) |      64   →      52    (-18.75%) |        4.10 ms →        3.33 ms  (-18.66%) | 
+ │ │ │ ├ sirius::D_operator::initialize                                |       93.85 μs →       95.36 μs   (+1.61%) |      32   →      26    (-18.75%) |        3.00 ms →        2.48 ms  (-17.44%) | 
+ │ │ │ └ sirius::Q_operator::initialize                                |       74.59 μs →       76.63 μs   (+2.74%) |      32   →      26    (-18.75%) |        2.39 ms →        1.99 ms  (-16.52%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.74 s  →        2.61 s    (-4.72%) |      32   →      26    (-18.75%) |       87.66 s  →       67.86 s   (-22.59%) | 
+ │ │ │ ├ sirius::Hamiltonian_k                                         |      155.21 μs →      153.48 μs   (-1.12%) |      32   →      26    (-18.75%) |        4.97 ms →        3.99 ms  (-19.66%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      148.20 μs →      146.37 μs   (-1.24%) |      32   →      26    (-18.75%) |        4.74 ms →        3.81 ms  (-19.76%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.39 μs →        5.03 μs   (-6.65%) |      32   →      26    (-18.75%) |      172.53 μs →      130.85 μs  (-24.16%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.66 s  →        2.48 s    (-7.01%) |      32   →      26    (-18.75%) |       85.28 s  →       64.43 s   (-24.44%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |      105.03 ms →       95.44 ms   (-9.13%) |      32   →      26    (-18.75%) |        3.36 s  →        2.48 s   (-26.17%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        9.27 ms →        7.67 ms  (-17.29%) |     192   →     156    (-18.75%) |        1.78 s  →        1.20 s   (-32.80%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        5.98 ms →        5.94 ms   (-0.61%) |      32   →      26    (-18.75%) |      191.29 ms →      154.48 ms  (-19.24%) | 
+ │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      349.72 μs →      350.80 μs   (+0.31%) |      32   →      26    (-18.75%) |       11.19 ms →        9.12 ms  (-18.50%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.31 ms →        2.30 ms   (-0.67%) |      64   →      52    (-18.75%) |      147.89 ms →      119.35 ms  (-19.29%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.52 s  →        2.34 s    (-7.03%) |      32   →      26    (-18.75%) |       80.58 s  →       60.87 s   (-24.46%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      103.27 ms →      137.57 ms  (+33.21%) |     357   →     262    (-26.61%) |       36.87 s  →       36.04 s    (-2.23%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       39.89 ms →       55.67 ms  (+39.57%) |     357   →     262    (-26.61%) |       14.24 s  →       14.59 s    (+2.43%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.99 μs →        2.04 μs   (+2.52%) |     357   →     262    (-26.61%) |      710.44 μs →      534.54 μs  (-24.76%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.65 μs →        1.72 μs   (+4.31%) |     357   →     262    (-26.61%) |      589.68 μs →      451.42 μs  (-23.45%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      316.50 ns →      408.50 ns  (+29.07%) |     357   →     262    (-26.61%) |      112.99 μs →      107.03 μs   (-5.28%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      435.23 ns →      537.05 ns  (+23.39%) |     357   →     262    (-26.61%) |      155.38 μs →      140.71 μs   (-9.44%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.35 ms →        7.45 ms   (+1.44%) |     357   →     262    (-26.61%) |        2.62 s  →        1.95 s   (-25.56%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       18.31 ms →       25.49 ms  (+39.21%) |     357   →     262    (-26.61%) |        6.54 s  →        6.68 s    (+2.16%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       18.85 ms →       24.46 ms  (+29.78%) |     714   →     524    (-26.61%) |       13.46 s  →       12.82 s    (-4.76%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |       29.41 ms →       35.89 ms  (+22.02%) |     357   →     262    (-26.61%) |       10.50 s  →        9.40 s   (-10.45%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        4.33 ms                             |     682                          |        2.95 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       23.37 μs                             |     682                          |       15.94 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                         6.23 ms            |                 498              |                         3.10 s             | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                        48.53 ns            |                 498              |                        24.17 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                         5.12 ms            |                 498              |                         2.55 s             | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                        27.33 ns            |                 498              |                        13.61 μs            | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      487.22 μs →      660.59 μs  (+35.58%) |     357   →     262    (-26.61%) |      173.94 ms →      173.08 ms   (-0.50%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        7.83 ms →       10.32 ms  (+31.81%) |     357   →     262    (-26.61%) |        2.79 s  →        2.70 s    (-3.26%) | 
  │ │ │ │   │ ├ sddk::transform                                         |       14.09 ms                             |     325                          |        4.58 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       29.00 μs                             |     325                          |        9.43 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       33.74 μs                             |     975                          |       32.89 ms                             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                        14.51 ms            |                 236              |                         3.42 s             | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                         4.84 ms            |                 708              |                         3.42 s             | 
- │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        9.21 ms →       10.40 ms  (+12.90%) |     357   →     262    (-26.61%) |        3.29 s  →        2.72 s   (-17.15%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        8.39 ms                             |     357                          |        3.00 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       28.40 μs                             |     357                          |       10.14 ms                             | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                        10.19 ms            |                 262              |                         2.67 s             | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                        26.89 ns            |                 262              |                         7.04 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                         9.07 ms            |                 262              |                         2.38 s             | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                        48.24 ns            |                 262              |                        12.64 μs            | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       65.23 ms →       18.33 ms  (-71.90%) |     357   →     262    (-26.61%) |       23.29 s  →        4.80 s   (-79.38%) | 
+ │ │ │ │   ├ sirius::residuals                                         |       13.58 ms →       13.14 ms   (-3.24%) |     346   →     252    (-27.17%) |        4.70 s  →        3.31 s   (-29.53%) | 
  │ │ │ │   │ ├ sddk::transform                                         |       12.54 ms                             |     333                          |        4.18 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       15.81 μs                             |     333                          |        5.26 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       34.33 μs                             |     666                          |       22.87 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                        11.72 ms            |                 242              |                         2.84 s             | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                         5.86 ms            |                 484              |                         2.83 s             | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.35 ms →        1.71 ms  (+26.14%) |     333   →     242    (-27.33%) |      450.92 ms →      413.35 ms   (-8.33%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       56.58 ms →       53.86 ms   (-4.80%) |      34   →      85   (+150.00%) |        1.92 s  →        4.58 s  (+137.99%) | 
  │ │ │ │     ├ sddk::transform                                         |       53.21 ms                             |      36                          |        1.92 s                              | 
  │ │ │ │     │ ├ sddk::transform|init                                  |       12.39 μs                             |      36                          |      445.98 μs                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       14.63 μs                             |      38                          |      556.11 μs                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                        31.52 ms            |                 144              |                         4.54 s             | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                        22.36 ms            |                 203              |                         4.54 s             | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      467.34 ns →      458.58 ns   (-1.88%) |      32   →      26    (-18.75%) |       14.96 μs →       11.92 μs  (-20.27%) | 
+ │ │ │ └ sirius::K_point_set::sync_band_energies                       |       30.74 μs →       29.90 μs   (-2.74%) |      32   →      26    (-18.75%) |      983.77 μs →      777.38 μs  (-20.98%) | 
+ │ │ ├ sirius::K_point_set::find_band_occupancies                      |      617.20 μs →      603.93 μs   (-2.15%) |      32   →      26    (-18.75%) |       19.75 ms →       15.70 ms  (-20.50%) | 
+ │ │ ├ sirius::Density::generate                                       |      772.01 ms →      775.70 ms   (+0.48%) |      32   →      26    (-18.75%) |       24.70 s  →       20.17 s   (-18.36%) | 
+ │ │ │ ├ sirius::Density::generate_valence                             |      402.78 ms →      404.04 ms   (+0.31%) |      32   →      26    (-18.75%) |       12.89 s  →       10.50 s   (-18.50%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        7.99 μs →        8.21 μs   (+2.76%) |      32   →      26    (-18.75%) |      255.56 μs →      213.38 μs  (-16.51%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.15 μs →        7.71 μs   (+7.77%) |      32   →      26    (-18.75%) |      228.90 μs →      200.44 μs  (-12.43%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       99.76 ms →      100.56 ms   (+0.80%) |      32   →      26    (-18.75%) |        3.19 s  →        2.61 s   (-18.10%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.54 μs →        8.02 μs   (+6.40%) |      32   →      26    (-18.75%) |      241.20 μs →      208.51 μs  (-13.55%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.12 ms →        7.12 ms   (-0.07%) |      32   →      26    (-18.75%) |      227.98 ms →      185.10 ms  (-18.81%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       90.69 ms →       91.51 ms   (+0.91%) |      32   →      26    (-18.75%) |        2.90 s  →        2.38 s   (-18.01%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      569.41 ns →      541.04 ns   (-4.98%) |      32   →      26    (-18.75%) |       18.22 μs →       14.07 μs  (-22.80%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      162.26 ms →      162.95 ms   (+0.42%) |      32   →      26    (-18.75%) |        5.19 s  →        4.24 s   (-18.41%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.65 ms →        1.63 ms   (-0.69%) |      32   →      26    (-18.75%) |       52.67 ms →       42.50 ms  (-19.31%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |       88.23 ms →       88.34 ms   (+0.13%) |      32   →      26    (-18.75%) |        2.82 s  →        2.30 s   (-18.64%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.00 ms →       88.05 ms   (+0.06%) |      32   →      26    (-18.75%) |        2.82 s  →        2.29 s   (-18.70%) | 
+ │ │ │ ├ sirius::Field4D::symmetrize                                   |      276.90 ms →      279.90 ms   (+1.08%) |      32   →      26    (-18.75%) |        8.86 s  →        7.28 s   (-17.87%) | 
+ │ │ │ │ └ sirius::symmetrize_function|fpw                             |      276.90 ms →      279.90 ms   (+1.08%) |      32   →      26    (-18.75%) |        8.86 s  →        7.28 s   (-17.87%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       27.92 ms →       24.37 ms  (-12.70%) |      32   →      26    (-18.75%) |      893.39 ms →      633.69 ms  (-29.07%) | 
+ │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      220.24 ms →      231.50 ms   (+5.11%) |      32   →      26    (-18.75%) |        7.05 s  →        6.02 s   (-14.60%) | 
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       27.54 ms →       22.84 ms  (-17.05%) |      32   →      26    (-18.75%) |      881.13 ms →      593.85 ms  (-32.60%) | 
+ │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       81.18 ms →       80.79 ms   (-0.49%) |      32   →      26    (-18.75%) |        2.60 s  →        2.10 s   (-19.15%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        7.45 ms →        7.39 ms   (-0.82%) |      32   →      26    (-18.75%) |      238.30 ms →      192.04 ms  (-19.41%) | 
+ │ │ ├ sirius::Density::mix                                            |      220.22 ms →      219.70 ms   (-0.24%) |      32   →      26    (-18.75%) |        7.05 s  →        5.71 s   (-18.94%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      928.88 μs →      944.98 μs   (+1.73%) |      32   →      26    (-18.75%) |       29.72 ms →       24.57 ms  (-17.34%) | 
+ │ │ │ ├ sirius::Periodic_function|inner                               |       10.41 ms →       10.77 ms   (+3.43%) |     424   →     334    (-21.23%) |        4.41 s  →        3.60 s   (-18.53%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.18 ms →       10.39 ms   (+2.07%) |     424   →     334    (-21.23%) |        4.32 s  →        3.47 s   (-19.59%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.18 ms →       10.39 ms   (+2.07%) |     424   →     334    (-21.23%) |        4.32 s  →        3.47 s   (-19.59%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        6.45 ms →        7.21 ms  (+11.75%) |      32   →      26    (-18.75%) |      206.37 ms →      187.37 ms   (-9.20%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.64 ms →        6.36 ms  (+12.70%) |      32   →      26    (-18.75%) |      180.47 ms →      165.25 ms   (-8.43%) | 
+ │ │ ├ sirius::Potential::generate                                     |      557.29 ms →      579.21 ms   (+3.93%) |      32   →      26    (-18.75%) |       17.83 s  →       15.06 s   (-15.55%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |      136.70 ms →      137.00 ms   (+0.22%) |      32   →      26    (-18.75%) |        4.37 s  →        3.56 s   (-18.57%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       15.55 ms →        5.17 ms  (-66.74%) |      32   →      26    (-18.75%) |      497.63 ms →      134.47 ms  (-72.98%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner                             |       10.21 ms →       10.27 ms   (+0.57%) |      32   →      26    (-18.75%) |      326.66 ms →      266.93 ms  (-18.29%) | 
+ │ │ │ │   └ sirius::Periodic_function|inner_local                     |        9.88 ms →       10.17 ms   (+2.96%) |      32   →      26    (-18.75%) |      316.11 ms →      264.44 ms  (-16.34%) | 
+ │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        9.88 ms →       10.17 ms   (+2.96%) |      32   →      26    (-18.75%) |      316.09 ms →      264.43 ms  (-16.34%) | 
+ │ │ │ ├ sirius::Periodic_function::add                                |      553.26 μs →      553.60 μs   (+0.06%) |      64   →      52    (-18.75%) |       35.41 ms →       28.79 ms  (-18.70%) | 
- │ │ │ ├ sirius::Potential::xc                                         |       34.73 ms →       49.29 ms  (+41.93%) |      32   →      26    (-18.75%) |        1.11 s  →        1.28 s   (+15.32%) | 
- │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       34.73 ms →       46.94 ms  (+35.17%) |      32   →      26    (-18.75%) |        1.11 s  →        1.22 s    (+9.83%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function                          |        1.24 ms →        3.02 ms (+143.60%) |      64   →      52    (-18.75%) |       79.22 ms →      156.80 ms  (+97.93%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.16 ms →        5.47 ms   (+6.05%) |      32   →      26    (-18.75%) |      165.19 ms →      142.35 ms  (-13.83%) | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        4.67 ms →        6.50 ms  (+39.33%) |      32   →      26    (-18.75%) |      149.34 ms →      169.06 ms  (+13.20%) | 
+ │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       91.05 ms →       90.89 ms   (-0.17%) |      32   →      26    (-18.75%) |        2.91 s  →        2.36 s   (-18.89%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      287.75 ms →      293.10 ms   (+1.86%) |      32   →      26    (-18.75%) |        9.21 s  →        7.62 s   (-17.24%) | 
+ │ │ ├ sirius::Field4D::symmetrize                                     |      274.62 ms →      284.60 ms   (+3.63%) |      32   →      26    (-18.75%) |        8.79 s  →        7.40 s   (-15.80%) | 
+ │ │ │ └ sirius::symmetrize_function|fpw                               |      274.62 ms →      284.60 ms   (+3.63%) |      32   →      26    (-18.75%) |        8.79 s  →        7.40 s   (-15.80%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.47 ms →       27.87 ms   (+1.48%) |      32   →      26    (-18.75%) |      878.89 ms →      724.66 ms  (-17.55%) | 
+ │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      219.50 ms →      229.01 ms   (+4.33%) |      32   →      26    (-18.75%) |        7.02 s  →        5.95 s   (-15.23%) | 
+ │ │ │   └ sddk::Gvec_shells::remap_backward                           |       26.50 ms →       23.91 ms   (-9.78%) |      32   →      26    (-18.75%) |      847.96 ms →      621.55 ms  (-26.70%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.65 ms →        6.50 ms  (+15.16%) |      32   →      26    (-18.75%) |      180.64 ms →      169.02 ms   (-6.43%) | 
+ │ │ ├ sirius::Periodic_function|inner                                 |       10.14 ms →       10.22 ms   (+0.83%) |     224   →     182    (-18.75%) |        2.27 s  →        1.86 s   (-18.07%) | 
+ │ │ │ └ sirius::Periodic_function|inner_local                         |        9.73 ms →        9.92 ms   (+1.96%) |     224   →     182    (-18.75%) |        2.18 s  →        1.81 s   (-17.15%) | 
+ │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.73 ms →        9.92 ms   (+1.97%) |     224   →     182    (-18.75%) |        2.18 s  →        1.81 s   (-17.15%) | 
+ │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.48 ms →       10.54 ms   (+0.60%) |      96   →      78    (-18.75%) |        1.01 s  →      822.12 ms  (-18.26%) | 
+ │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.12 ms →       10.26 ms   (+1.43%) |      96   →      78    (-18.75%) |      971.08 ms →      800.27 ms  (-17.59%) | 
+ │ │ ├ sirius::Periodic_function::integrate                            |       10.64 ms →        9.92 ms   (-6.69%) |      32   →      26    (-18.75%) |      340.34 ms →      258.03 ms  (-24.18%) | 
+ │ │ └ sirius::Density::get_magnetisation                              |      109.82 μs →      112.89 μs   (+2.79%) |      32   →      26    (-18.75%) |        3.51 ms →        2.94 ms  (-16.48%) | 
+ │ │   └ sirius::Density::compute_atomic_mag_mom                       |      104.70 μs →      107.90 μs   (+3.05%) |      32   →      26    (-18.75%) |        3.35 ms →        2.81 ms  (-16.27%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        4.94 ms →        5.20 ms   (+5.17%) |       2   →       2              |        9.88 ms →       10.39 ms   (+5.17%) | 
- │ ├ sirius::Periodic_function|inner                                   |        9.77 ms →       10.85 ms  (+11.09%) |       6   →       6              |       58.60 ms →       65.10 ms  (+11.09%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        9.75 ms →        9.87 ms   (+1.19%) |       6   →       6              |       58.52 ms →       59.22 ms   (+1.19%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        9.75 ms →        9.87 ms   (+1.19%) |       6   →       6              |       58.52 ms →       59.22 ms   (+1.19%) | 
- │ └ sirius::Smooth_periodic_function|inner                            |       10.07 ms →       11.32 ms  (+12.42%) |       3   →       3              |       30.21 ms →       33.96 ms  (+12.42%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.06 ms →       10.13 ms   (+0.75%) |       3   →       3              |       30.17 ms →       30.39 ms   (+0.75%) | 
- ├ sirius::Periodic_function|inner                                     |        9.69 ms →       10.84 ms  (+11.83%) |       2   →       2              |       19.39 ms →       21.68 ms  (+11.83%) | 
  │ └ sirius::Periodic_function|inner_local                             |        9.68 ms →       10.00 ms   (+3.29%) |       2   →       2              |       19.37 ms →       20.00 ms   (+3.29%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.68 ms →       10.00 ms   (+3.29%) |       2   →       2              |       19.37 ms →       20.00 ms   (+3.29%) | 
- ├ sirius::Smooth_periodic_function|inner                              |       10.23 ms →       11.33 ms  (+10.71%) |       1   →       1              |       10.23 ms →       11.33 ms  (+10.71%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.03 ms →       10.36 ms   (+3.37%) |       1   →       1              |       10.03 ms →       10.36 ms   (+3.37%) | 
- └ sirius::finalize                                                    |      178.92 ms →      228.51 ms  (+27.72%) |       1   →       1              |      178.92 ms →      228.51 ms  (+27.72%) | 
  ====================================================================================================================================================================================================
```
