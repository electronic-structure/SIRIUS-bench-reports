# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs a923c3c8853d846138a8b9a9c096494004b8d208
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |       76.83 s  →       71.53 s    (-6.89%) |       1   →       1              |       76.83 s  →       71.53 s    (-6.89%) | 
  ├ sirius::initialize                                                  |        2.85 s  →        2.91 s    (+2.08%) |       1   →       1              |        2.85 s  →        2.91 s    (+2.08%) | 
  ├ sirius::Simulation_context::initialize                              |        3.76 s  →        3.87 s    (+2.83%) |       1   →       1              |        3.76 s  →        3.87 s    (+2.83%) | 
- │ ├ sirius::Simulation_context::init_comm                             |       15.39 ms →       35.76 ms (+132.41%) |       1   →       1              |       15.39 ms →       35.76 ms (+132.41%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      152.96 ms →      191.57 ms  (+25.24%) |       1   →       1              |      152.96 ms →      191.57 ms  (+25.24%) | 
- │ │ ├ sirius::Atom_type::init                                         |       66.28 ms →       85.52 ms  (+29.03%) |       2   →       2              |      132.57 ms →      171.05 ms  (+29.03%) | 
  │ │ └ sirius::Unit_cell::update                                       |       20.30 ms →       20.42 ms   (+0.58%) |       1   →       1              |       20.30 ms →       20.42 ms   (+0.58%) | 
- │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        5.12 ms →        6.49 ms  (+26.96%) |       1   →       1              |        5.12 ms →        6.49 ms  (+26.96%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       15.13 ms →       13.86 ms   (-8.45%) |       1   →       1              |       15.13 ms →       13.86 ms   (-8.45%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       15.05 ms →       13.78 ms   (-8.48%) |       1   →       1              |       15.05 ms →       13.78 ms   (-8.48%) | 
- │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.75 ms →        3.37 ms  (+22.45%) |       1   →       1              |        2.75 ms →        3.37 ms  (+22.45%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      581.14 μs →      633.56 μs   (+9.02%) |       1   →       1              |      581.14 μs →      633.56 μs   (+9.02%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       16.12 μs →       15.78 μs   (-2.11%) |       1   →       1              |       16.12 μs →       15.78 μs   (-2.11%) | 
  │ └ sirius::Simulation_context::update                                |        3.55 s  →        3.53 s    (-0.49%) |       1   →       1              |        3.55 s  →        3.53 s    (-0.49%) | 
  │   ├ sirius::Unit_cell::update                                       |        6.81 ms →        6.99 ms   (+2.60%) |       1   →       1              |        6.81 ms →        6.99 ms   (+2.60%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.48 ms →        3.64 ms   (+4.55%) |       1   →       1              |        3.48 ms →        3.64 ms   (+4.55%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.28 ms →        3.30 ms   (+0.60%) |       1   →       1              |        3.28 ms →        3.30 ms   (+0.60%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.23 ms →        3.25 ms   (+0.65%) |       1   →       1              |        3.23 ms →        3.25 ms   (+0.65%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.71 ms →        2.70 ms   (-0.30%) |       1   →       1              |        2.71 ms →        2.70 ms   (-0.30%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      483.57 μs →      513.79 μs   (+6.25%) |       1   →       1              |      483.57 μs →      513.79 μs   (+6.25%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       14.77 μs →       15.08 μs   (+2.10%) |       1   →       1              |       14.77 μs →       15.08 μs   (+2.10%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      212.63 ms →      221.37 ms   (+4.11%) |       2   →       2              |      425.27 ms →      442.74 ms   (+4.11%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.30 ms →       15.18 ms   (-0.79%) |       2   →       2              |       30.60 ms →       30.36 ms   (-0.79%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.27 ms →       13.27 ms   (-0.01%) |       1   →       1              |       13.27 ms →       13.27 ms   (-0.01%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.61 ms →       56.31 ms   (-0.52%) |       2   →       2              |      113.21 ms →      112.63 ms   (-0.52%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.11 ms →       45.07 ms   (-0.09%) |       2   →       2              |       90.23 ms →       90.14 ms   (-0.09%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.30 ms →       60.50 ms   (+0.33%) |       4   →       4              |      241.20 ms →      242.01 ms   (+0.33%) | 
  │   ├ sddk::Gvec::init                                                |       97.30 ms →       94.12 ms   (-3.27%) |       2   →       2              |      194.61 ms →      188.24 ms   (-3.27%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       71.83 ms →       70.53 ms   (-1.81%) |       2   →       2              |      143.66 ms →      141.06 ms   (-1.81%) | 
+ │   ├ sddk::Gvec_shells                                               |      107.88 ms →       93.34 ms  (-13.47%) |       1   →       1              |      107.88 ms →       93.34 ms  (-13.47%) | 
- │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.71 ms →        1.94 ms  (+13.59%) |       1   →       1              |        1.71 ms →        1.94 ms  (+13.59%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      610.84 ms →      610.52 ms   (-0.05%) |       2   →       2              |        1.22 s  →        1.22 s    (-0.05%) | 
- ├ sirius::K_point_set::create_k_mesh                                  |       89.14 ms →      131.55 ms  (+47.57%) |       1   →       1              |       89.14 ms →      131.55 ms  (+47.57%) | 
  │ ├ sirius::K_point::K_point                                          |        1.22 μs →        1.20 μs   (-2.16%) |       4   →       4              |        4.90 μs →        4.79 μs   (-2.16%) | 
- │ └ sirius::K_point_set::initialize                                   |       89.08 ms →      131.46 ms  (+47.57%) |       1   →       1              |       89.08 ms →      131.46 ms  (+47.57%) | 
  │   └ sirius::K_point::initialize                                     |       29.54 ms →       30.03 ms   (+1.64%) |       1   →       1              |       29.54 ms →       30.03 ms   (+1.64%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       11.91 ms →       10.94 ms   (-8.18%) |       1   →       1              |       11.91 ms →       10.94 ms   (-8.18%) | 
  │     │ └ sddk::Gvec::init                                            |        5.16 ms →        4.93 ms   (-4.48%) |       1   →       1              |        5.16 ms →        4.93 ms   (-4.48%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        7.10 μs →        6.46 μs   (-9.00%) |       1   →       1              |        7.10 μs →        6.46 μs   (-9.00%) | 
- │     └ sirius::K_point::update                                       |       14.38 ms →       16.21 ms  (+12.71%) |       1   →       1              |       14.38 ms →       16.21 ms  (+12.71%) | 
- │       └ sirius::Beta_projectors                                     |       10.09 ms →       12.41 ms  (+23.02%) |       1   →       1              |       10.09 ms →       12.41 ms  (+23.02%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.22 ms →        8.32 ms   (+1.23%) |       1   →       1              |        8.22 ms →        8.32 ms   (+1.23%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.56 ms →        2.55 ms   (-0.25%) |       2   →       2              |        5.12 ms →        5.11 ms   (-0.25%) | 
  ├ sirius::Potential                                                   |       49.38 ms →       50.60 ms   (+2.47%) |       1   →       1              |       49.38 ms →       50.60 ms   (+2.47%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.90 ms →        2.95 ms   (+1.74%) |       6   →       6              |       17.40 ms →       17.70 ms   (+1.74%) | 
  │ └ sirius::Potential::update                                         |       31.38 ms →       32.31 ms   (+2.96%) |       1   →       1              |       31.38 ms →       32.31 ms   (+2.96%) | 
  │   └ sirius::Potential::generate_local_potential                     |       30.99 ms →       31.90 ms   (+2.95%) |       1   →       1              |       30.99 ms →       31.90 ms   (+2.95%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       26.15 ms →       26.60 ms   (+1.70%) |       1   →       1              |       26.15 ms →       26.60 ms   (+1.70%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        4.49 ms →        4.74 ms   (+5.55%) |       1   →       1              |        4.49 ms →        4.74 ms   (+5.55%) | 
+ ├ sirius::Density                                                     |       41.15 ms →       36.72 ms  (-10.76%) |       1   →       1              |       41.15 ms →       36.72 ms  (-10.76%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.82 ms →        2.82 ms   (+0.06%) |       2   →       2              |        5.63 ms →        5.64 ms   (+0.06%) | 
+ │ └ sirius::Density::update                                           |       35.37 ms →       30.94 ms  (-12.52%) |       1   →       1              |       35.37 ms →       30.94 ms  (-12.52%) | 
+ │   └ sirius::Density::generate_pseudo_core_charge_density            |       35.15 ms →       30.67 ms  (-12.73%) |       1   →       1              |       35.15 ms →       30.67 ms  (-12.73%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |                        78.60 μs            |                   1              |                        78.60 μs            | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       27.11 ms →       26.91 ms   (-0.76%) |       1   →       1              |       27.11 ms →       26.91 ms   (-0.76%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        7.74 ms →        3.34 ms  (-56.83%) |       1   →       1              |        7.74 ms →        3.34 ms  (-56.83%) | 
  ├ sirius::Density::initial_density                                    |       57.21 ms →       56.26 ms   (-1.66%) |       1   →       1              |       57.21 ms →       56.26 ms   (-1.66%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       27.04 ms →       27.98 ms   (+3.48%) |       1   →       1              |       27.04 ms →       27.98 ms   (+3.48%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.83 ms →        4.44 ms  (-23.82%) |       2   →       2              |       11.67 ms →        8.89 ms  (-23.82%) | 
- │ └ sirius::Periodic_function::integrate                              |        5.10 ms →        5.75 ms  (+12.85%) |       1   →       1              |        5.10 ms →        5.75 ms  (+12.85%) | 
  ├ sirius::Potential::generate                                         |      363.11 ms →      362.21 ms   (-0.25%) |       1   →       1              |      363.11 ms →      362.21 ms   (-0.25%) | 
  │ ├ sirius::Potential::poisson                                        |       36.51 ms →       34.37 ms   (-5.86%) |       1   →       1              |       36.51 ms →       34.37 ms   (-5.86%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        6.03 ms →        3.33 ms  (-44.67%) |       1   →       1              |        6.03 ms →        3.33 ms  (-44.67%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        5.14 ms →        4.94 ms   (-3.89%) |       1   →       1              |        5.14 ms →        4.94 ms   (-3.89%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.63 ms →        4.65 ms   (+0.35%) |       1   →       1              |        4.63 ms →        4.65 ms   (+0.35%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.63 ms →        4.64 ms   (+0.24%) |       1   →       1              |        4.63 ms →        4.64 ms   (+0.24%) | 
  │ ├ sirius::Periodic_function::add                                    |      765.44 μs →      787.04 μs   (+2.82%) |       2   →       2              |        1.53 ms →        1.57 ms   (+2.82%) | 
  │ ├ sirius::Potential::xc                                             |       50.05 ms →       51.77 ms   (+3.45%) |       1   →       1              |       50.05 ms →       51.77 ms   (+3.45%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       50.04 ms →       50.60 ms   (+1.11%) |       1   →       1              |       50.04 ms →       50.60 ms   (+1.11%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.53 ms →        2.57 ms   (+1.51%) |       2   →       2              |        5.07 ms →        5.14 ms   (+1.51%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.15 ms →        4.44 ms   (+7.13%) |       1   →       1              |        4.15 ms →        4.44 ms   (+7.13%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.47 ms →        3.07 ms  (-11.64%) |       1   →       1              |        3.47 ms →        3.07 ms  (-11.64%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      270.15 ms →      269.96 ms   (-0.07%) |       1   →       1              |      270.15 ms →      269.96 ms   (-0.07%) | 
- │ └ sirius::Potential::generate_PAW_effective_potential               |      120.00 ns →      201.00 ns  (+67.50%) |       1   →       1              |      120.00 ns →      201.00 ns  (+67.50%) | 
- ├ sirius::Hamiltonian0                                                |        6.45 ms →        8.32 ms  (+29.09%) |       1   →       1              |        6.45 ms →        8.32 ms  (+29.09%) | 
- │ ├ sirius::Local_operator                                            |        5.85 ms →        7.62 ms  (+30.24%) |       1   →       1              |        5.85 ms →        7.62 ms  (+30.24%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.74 ms →        2.75 ms   (+0.23%) |       1   →       1              |        2.74 ms →        2.75 ms   (+0.23%) | 
- │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.34 ms →        3.46 ms  (+48.03%) |       1   →       1              |        2.34 ms →        3.46 ms  (+48.03%) | 
- │ ├ sirius::Non_local_operator                                        |      120.87 μs →      218.18 μs  (+80.50%) |       2   →       2              |      241.75 μs →      436.36 μs  (+80.50%) | 
+ │ ├ sirius::D_operator::initialize                                    |      143.96 μs →       98.69 μs  (-31.44%) |       1   →       1              |      143.96 μs →       98.69 μs  (-31.44%) | 
+ │ └ sirius::Q_operator::initialize                                    |      111.38 μs →       93.11 μs  (-16.41%) |       1   →       1              |      111.38 μs →       93.11 μs  (-16.41%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.27 s  →        1.28 s    (+0.86%) |       1   →       1              |        1.27 s  →        1.28 s    (+0.86%) | 
- │ ├ sirius::Hamiltonian_k                                             |       50.83 ms →       58.84 ms  (+15.78%) |       1   →       1              |       50.83 ms →       58.84 ms  (+15.78%) | 
+ │ │ ├ sirius::Local_operator::prepare_k                               |      300.19 μs →      249.64 μs  (-16.84%) |       1   →       1              |      300.19 μs →      249.64 μs  (-16.84%) | 
- │ │ └ sirius::Beta_projectors_base::prepare                           |       50.52 ms →       58.59 ms  (+15.98%) |       1   →       1              |       50.52 ms →       58.59 ms  (+15.98%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.22 s  →        1.23 s    (+0.24%) |       1   →       1              |        1.22 s  →        1.23 s    (+0.24%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       77.03 ms →       77.86 ms   (+1.08%) |       4   →       4              |      308.12 ms →      311.45 ms   (+1.08%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       43.26 ms →       42.56 ms   (-1.61%) |       1   →       1              |       43.26 ms →       42.56 ms   (-1.61%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        8.65 ms →        8.62 ms   (-0.27%) |       1   →       1              |        8.65 ms →        8.62 ms   (-0.27%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      336.04 ms →      316.50 ms   (-5.81%) |       1   →       1              |      336.04 ms →      316.50 ms   (-5.81%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      248.14 ms →      246.04 ms   (-0.84%) |       1   →       1              |      248.14 ms →      246.04 ms   (-0.84%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        4.44 μs →        4.04 μs   (-8.96%) |       1   →       1              |        4.44 μs →        4.04 μs   (-8.96%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.43 μs →        3.15 μs   (-8.25%) |       1   →       1              |        3.43 μs →        3.15 μs   (-8.25%) | 
- │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      425.00 ns →      541.00 ns  (+27.29%) |       1   →       1              |      425.00 ns →      541.00 ns  (+27.29%) | 
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      928.00 ns →      748.00 ns  (-19.40%) |       1   →       1              |      928.00 ns →      748.00 ns  (-19.40%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.09 ms →        3.15 ms   (+1.87%) |       1   →       1              |        3.09 ms →        3.15 ms   (+1.87%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.30 ms →       21.26 ms   (-0.21%) |       1   →       1              |       21.30 ms →       21.26 ms   (-0.21%) | 
+ │ │ │ └ sirius::Non_local_operator::apply                             |       31.73 ms →       23.01 ms  (-27.50%) |       2   →       2              |       63.46 ms →       46.01 ms  (-27.50%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.34 ms →       14.84 ms   (+3.49%) |       2   →       2              |       28.67 ms →       29.67 ms   (+3.49%) | 
  │ │ │ ├ sddk::inner                                                   |       14.12 ms                             |       2                          |       28.24 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       31.32 μs                             |       2                          |       62.64 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        14.62 ms            |                   2              |                        29.25 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        19.50 ns            |                   2              |                        39.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        14.50 ms            |                   2              |                        28.99 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                        21.00 ns            |                   2              |                        42.00 ns            | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      230.85 ms →      250.21 ms   (+8.39%) |       1   →       1              |      230.85 ms →      250.21 ms   (+8.39%) | 
  │ │ ├ sddk::transform                                                 |        2.84 ms                             |       1                          |        2.84 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       13.93 μs                             |       1                          |       13.93 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       18.77 μs                             |       1                          |       18.77 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                         2.60 ms            |                   1              |                         2.60 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                         2.60 ms            |                   1              |                         2.60 ms            | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      455.00 ns →      581.00 ns  (+27.69%) |       1   →       1              |      455.00 ns →      581.00 ns  (+27.69%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |       66.99 s  →       61.70 s    (-7.90%) |       1   →       1              |       66.99 s  →       61.70 s    (-7.90%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.44 ms →        2.46 ms   (+1.12%) |      19   →      19              |       46.29 ms →       46.81 ms   (+1.12%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.33 s  →        3.24 s    (-2.89%) |      20   →      19     (-5.00%) |       66.68 s  →       61.51 s    (-7.75%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        4.99 ms →        5.64 ms  (+13.09%) |      20   →      19     (-5.00%) |       99.81 ms →      107.23 ms   (+7.44%) | 
- │ │ │ ├ sirius::Local_operator                                        |        4.40 ms →        4.94 ms  (+12.28%) |      20   →      19     (-5.00%) |       88.03 ms →       93.90 ms   (+6.66%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      550.51 μs →      556.50 μs   (+1.09%) |      20   →      19     (-5.00%) |       11.01 ms →       10.57 ms   (-3.97%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.81 ms →        3.14 ms  (+11.86%) |      20   →      19     (-5.00%) |       56.22 ms →       59.75 ms   (+6.27%) | 
- │ │ │ ├ sirius::Non_local_operator                                    |      136.95 μs →      206.39 μs  (+50.70%) |      40   →      38     (-5.00%) |        5.48 ms →        7.84 ms  (+43.17%) | 
+ │ │ │ ├ sirius::D_operator::initialize                                |      127.99 μs →      117.79 μs   (-7.97%) |      20   →      19     (-5.00%) |        2.56 ms →        2.24 ms  (-12.57%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       97.76 μs →       92.64 μs   (-5.23%) |      20   →      19     (-5.00%) |        1.96 ms →        1.76 ms   (-9.97%) | 
  │ │ ├ sirius::Band::solve                                             |        2.11 s  →        2.02 s    (-4.26%) |      20   →      19     (-5.00%) |       42.26 s  →       38.44 s    (-9.05%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      212.95 μs →      212.99 μs   (+0.02%) |      20   →      19     (-5.00%) |        4.26 ms →        4.05 ms   (-4.98%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      203.50 μs →      203.21 μs   (-0.14%) |      20   →      19     (-5.00%) |        4.07 ms →        3.86 ms   (-5.13%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        7.54 μs →        7.21 μs   (-4.34%) |      20   →      19     (-5.00%) |      150.79 μs →      137.04 μs   (-9.12%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.96 s  →        1.96 s    (+0.29%) |      20   →      19     (-5.00%) |       39.14 s  →       37.29 s    (-4.73%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       90.31 ms →       79.15 ms  (-12.36%) |      20   →      19     (-5.00%) |        1.81 s  →        1.50 s   (-16.74%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |       11.58 ms →        8.36 ms  (-27.80%) |     120   →     114     (-5.00%) |        1.39 s  →      952.95 ms  (-31.41%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       15.73 ms →       15.98 ms   (+1.56%) |      20   →      19     (-5.00%) |      314.64 ms →      303.57 ms   (-3.52%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      455.83 μs →      492.32 μs   (+8.00%) |      20   →      19     (-5.00%) |        9.12 ms →        9.35 ms   (+2.60%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        7.42 ms →        7.29 ms   (-1.79%) |      40   →      38     (-5.00%) |      296.85 ms →      276.96 ms   (-6.70%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.84 s  →        1.86 s    (+0.87%) |      20   →      19     (-5.00%) |       36.89 s  →       35.35 s    (-4.18%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       52.12 ms →       55.40 ms   (+6.30%) |     250   →     356    (+42.40%) |       13.03 s  →       19.72 s   (+51.38%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       33.73 ms →       33.13 ms   (-1.77%) |     250   →     356    (+42.40%) |        8.43 s  →       11.80 s   (+39.87%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.41 μs →        2.00 μs  (-17.00%) |     250   →     356    (+42.40%) |      602.33 μs →      711.89 μs  (+18.19%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        2.01 μs →        1.71 μs  (-14.95%) |     250   →     356    (+42.40%) |      502.28 μs →      608.32 μs  (+21.11%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      472.58 ns →      424.02 ns  (-10.28%) |     250   →     356    (+42.40%) |      118.15 μs →      150.95 μs  (+27.77%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      577.22 ns →      510.43 ns  (-11.57%) |     250   →     356    (+42.40%) |      144.30 μs →      181.71 μs  (+25.92%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.63 ms →        3.01 ms  (+14.53%) |     250   →     356    (+42.40%) |      657.57 ms →        1.07 s   (+63.09%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.44 ms →        3.36 ms   (-2.13%) |     250   →     356    (+42.40%) |      859.50 ms →        1.20 s   (+39.37%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        6.15 ms →        7.94 ms  (+29.10%) |     500   →     712    (+42.40%) |        3.07 s  →        5.65 s   (+83.83%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |        6.77 ms →        6.17 ms   (-8.77%) |     250   →     356    (+42.40%) |        1.69 s  →        2.20 s   (+29.91%) | 
  │ │ │ │   │ ├ sddk::inner                                             |      893.26 μs                             |     480                          |      428.76 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       25.92 μs                             |     480                          |       12.44 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                         1.06 ms            |                 693              |                       736.88 ms            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                        53.70 ns            |                 693              |                        37.22 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                       903.14 μs            |                 693              |                       625.88 ms            | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                        46.75 ns            |                 693              |                        32.40 μs            | 
+ │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      187.46 μs →      143.02 μs  (-23.71%) |     250   →     356    (+42.40%) |       46.86 ms →       50.91 ms   (+8.64%) | 
+ │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        2.44 ms →        1.76 ms  (-27.93%) |     250   →     356    (+42.40%) |      609.31 ms →      625.35 ms   (+2.63%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        2.63 ms                             |     230                          |      604.96 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       21.36 μs                             |     230                          |        4.91 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |        8.72 μs                             |     690                          |        6.02 ms                             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                         2.32 ms            |                 337              |                       782.36 ms            | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                       773.08 μs            |                1.01 K            |                       781.58 ms            | 
- │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.64 ms →        1.29 ms  (-21.22%) |     250   →     356    (+42.40%) |      408.85 ms →      458.68 ms  (+12.19%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        1.43 ms                             |     250                          |      357.10 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       26.62 μs                             |     250                          |        6.65 ms                             | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                         1.22 ms            |                 356              |                       433.51 ms            | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                        41.28 ns            |                 356              |                        14.70 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                         1.05 ms            |                 356              |                       375.27 ms            | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                        39.55 ns            |                 356              |                        14.08 μs            | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       83.81 ms →       32.75 ms  (-60.92%) |     250   →     356    (+42.40%) |       20.95 s  →       11.66 s   (-44.36%) | 
- │ │ │ │   ├ sirius::residuals                                         |        2.53 ms →        2.66 ms   (+5.30%) |     245   →     340    (+38.78%) |      619.39 ms →      905.08 ms  (+46.12%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        1.70 ms                             |     231                          |      392.21 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       17.46 μs                             |     231                          |        4.03 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       11.67 μs                             |     462                          |        5.39 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                         1.47 ms            |                 337              |                       496.81 ms            | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                       735.71 μs            |                 674              |                       495.87 ms            | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      907.16 μs →        1.10 ms  (+21.31%) |     231   →     337    (+45.89%) |      209.55 ms →      370.84 ms  (+76.97%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        7.09 ms →        7.31 ms   (+3.20%) |      25   →      54   (+116.00%) |      177.15 ms →      394.91 ms (+122.92%) | 
  │ │ │ │     ├ sddk::transform                                         |        5.82 ms                             |      30                          |      174.59 ms                             | 
  │ │ │ │     │ ├ sddk::transform|init                                  |       11.71 μs                             |      30                          |      351.26 μs                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       13.45 μs                             |      35                          |      470.86 μs                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                         4.39 ms            |                  89              |                       390.44 ms            | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                         3.15 ms            |                 124              |                       390.27 ms            | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      390.00 ns →      438.47 ns  (+12.43%) |      20   →      19     (-5.00%) |        7.80 μs →        8.33 μs   (+6.81%) | 
+ │ │ │ └ sirius::K_point_set::sync_band_energies                       |       22.85 μs →       19.91 μs  (-12.88%) |      20   →      19     (-5.00%) |      457.02 μs →      378.27 μs  (-17.23%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.50 ms →        1.53 ms   (+1.75%) |      20   →      19     (-5.00%) |       29.99 ms →       28.99 ms   (-3.34%) | 
  │ │ ├ sirius::Density::generate                                       |      570.98 ms →      565.05 ms   (-1.04%) |      20   →      19     (-5.00%) |       11.42 s  →       10.74 s    (-5.99%) | 
+ │ │ │ ├ sirius::Density::generate_valence                             |      418.04 ms →      385.39 ms   (-7.81%) |      20   →      19     (-5.00%) |        8.36 s  →        7.32 s   (-12.42%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.29 μs →        7.95 μs   (-4.11%) |      20   →      19     (-5.00%) |      165.90 μs →      151.13 μs   (-8.90%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.60 μs →        7.39 μs   (-2.83%) |      20   →      19     (-5.00%) |      152.08 μs →      140.39 μs   (-7.68%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       18.24 ms →       42.74 ms (+134.35%) |      20   →      19     (-5.00%) |      364.75 ms →      812.05 ms (+122.63%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.80 μs →        7.83 μs   (+0.37%) |      20   →      19     (-5.00%) |      156.06 μs →      148.80 μs   (-4.65%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        2.97 ms →       23.50 ms (+690.59%) |      20   →      19     (-5.00%) |       59.44 ms →      446.42 ms (+651.06%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       14.24 ms →       18.19 ms  (+27.75%) |      20   →      19     (-5.00%) |      284.71 ms →      345.54 ms  (+21.37%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      901.95 ns →      691.05 ns  (-23.38%) |      20   →      19     (-5.00%) |       18.04 μs →       13.13 μs  (-27.21%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      127.12 ms →       96.86 ms  (-23.80%) |      20   →      19     (-5.00%) |        2.54 s  →        1.84 s   (-27.61%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.94 ms →        1.92 ms   (-1.01%) |      20   →      19     (-5.00%) |       38.88 ms →       36.56 ms   (-5.96%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |      241.48 ms →      202.74 ms  (-16.04%) |      20   →      19     (-5.00%) |        4.83 s  →        3.85 s   (-20.24%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |      241.26 ms →      202.53 ms  (-16.05%) |      20   →      19     (-5.00%) |        4.83 s  →        3.85 s   (-20.25%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      124.00 ms →      151.71 ms  (+22.35%) |      20   →      19     (-5.00%) |        2.48 s  →        2.88 s   (+16.23%) | 
- │ │ │ │ └ sirius::symmetrize_function|fpw                             |      124.00 ms →      151.71 ms  (+22.35%) |      20   →      19     (-5.00%) |        2.48 s  →        2.88 s   (+16.23%) | 
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       39.25 ms →       67.28 ms  (+71.41%) |      20   →      19     (-5.00%) |      785.06 ms →        1.28 s   (+62.84%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       69.48 ms →       71.13 ms   (+2.39%) |      20   →      19     (-5.00%) |        1.39 s  →        1.35 s    (-2.73%) | 
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       14.62 ms →       12.63 ms  (-13.60%) |      20   →      19     (-5.00%) |      292.45 ms →      240.05 ms  (-17.92%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       24.00 ms →       23.79 ms   (-0.89%) |      20   →      19     (-5.00%) |      480.08 ms →      451.99 ms   (-5.85%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        4.93 ms →        4.16 ms  (-15.57%) |      20   →      19     (-5.00%) |       98.50 ms →       79.01 ms  (-19.79%) | 
  │ │ ├ sirius::Density::mix                                            |      131.65 ms →      133.04 ms   (+1.06%) |      20   →      19     (-5.00%) |        2.63 s  →        2.53 s    (-3.99%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      761.61 μs →      658.40 μs  (-13.55%) |      20   →      19     (-5.00%) |       15.23 ms →       12.51 ms  (-17.87%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |        4.67 ms →        4.91 ms   (+4.99%) |     244   →     229     (-6.15%) |        1.14 s  →        1.12 s    (-1.47%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.61 ms →        4.82 ms   (+4.44%) |     244   →     229     (-6.15%) |        1.13 s  →        1.10 s    (-1.99%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.61 ms →        4.82 ms   (+4.44%) |     244   →     229     (-6.15%) |        1.13 s  →        1.10 s    (-1.98%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        6.01 ms →        5.01 ms  (-16.59%) |      20   →      19     (-5.00%) |      120.11 ms →       95.17 ms  (-20.76%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.28 ms →        4.35 ms  (-17.71%) |      20   →      19     (-5.00%) |      105.63 ms →       82.58 ms  (-21.82%) | 
  │ │ ├ sirius::Potential::generate                                     |      355.71 ms →      355.07 ms   (-0.18%) |      20   →      19     (-5.00%) |        7.11 s  →        6.75 s    (-5.17%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |       36.68 ms →       34.93 ms   (-4.75%) |      20   →      19     (-5.00%) |      733.54 ms →      663.76 ms   (-9.51%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        5.82 ms →        3.65 ms  (-37.33%) |      20   →      19     (-5.00%) |      116.39 ms →       69.30 ms  (-40.46%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |        5.28 ms →        5.18 ms   (-1.88%) |      20   →      19     (-5.00%) |      105.67 ms →       98.50 ms   (-6.78%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.63 ms →        4.63 ms   (+0.06%) |      20   →      19     (-5.00%) |       92.62 ms →       88.04 ms   (-4.94%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.63 ms →        4.63 ms   (+0.06%) |      20   →      19     (-5.00%) |       92.60 ms →       88.02 ms   (-4.94%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      775.87 μs →      787.50 μs   (+1.50%) |      40   →      38     (-5.00%) |       31.03 ms →       29.93 ms   (-3.58%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       43.12 ms →       44.99 ms   (+4.33%) |      20   →      19     (-5.00%) |      862.36 ms →      854.74 ms   (-0.88%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       43.12 ms →       43.80 ms   (+1.59%) |      20   →      19     (-5.00%) |      862.30 ms →      832.22 ms   (-3.49%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |      645.26 μs →      687.81 μs   (+6.59%) |      40   →      38     (-5.00%) |       25.81 ms →       26.14 ms   (+1.26%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.20 ms →        4.53 ms   (+7.84%) |      20   →      19     (-5.00%) |       84.09 ms →       86.14 ms   (+2.45%) | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.45 ms →        2.96 ms  (-14.15%) |      20   →      19     (-5.00%) |       68.91 ms →       56.20 ms  (-18.44%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      269.47 ms →      269.13 ms   (-0.13%) |      20   →      19     (-5.00%) |        5.39 s  →        5.11 s    (-5.12%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      128.50 ns →      223.89 ns  (+74.24%) |      20   →      19     (-5.00%) |        2.57 μs →        4.25 μs  (+65.53%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |       99.80 ms →       97.32 ms   (-2.49%) |      20   →      19     (-5.00%) |        2.00 s  →        1.85 s    (-7.36%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |       99.80 ms →       97.32 ms   (-2.48%) |      20   →      19     (-5.00%) |        2.00 s  →        1.85 s    (-7.36%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       15.48 ms →       13.28 ms  (-14.17%) |      20   →      19     (-5.00%) |      309.51 ms →      252.37 ms  (-18.46%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       69.08 ms →       70.76 ms   (+2.43%) |      20   →      19     (-5.00%) |        1.38 s  →        1.34 s    (-2.69%) | 
+ │ │ │   └ sddk::Gvec_shells::remap_backward                           |       14.61 ms →       12.64 ms  (-13.45%) |      20   →      19     (-5.00%) |      292.18 ms →      240.24 ms  (-17.78%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        4.12 ms →        3.51 ms  (-14.78%) |      20   →      19     (-5.00%) |       82.41 ms →       66.72 ms  (-19.04%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.64 ms →        4.78 ms   (+2.84%) |     140   →     133     (-5.00%) |      650.28 ms →      635.32 ms   (-2.30%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.58 ms →        4.57 ms   (-0.11%) |     140   →     133     (-5.00%) |      641.17 ms →      608.43 ms   (-5.10%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.58 ms →        4.57 ms   (-0.11%) |     140   →     133     (-5.00%) |      641.06 ms →      608.35 ms   (-5.10%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.74 ms →        5.00 ms   (+5.62%) |      60   →      57     (-5.00%) |      284.29 ms →      285.26 ms   (+0.34%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.73 ms →        4.95 ms   (+4.73%) |      60   →      57     (-5.00%) |      283.87 ms →      282.42 ms   (-0.51%) | 
+ │ │ ├ sirius::Periodic_function::integrate                            |        4.92 ms →        4.53 ms   (-7.81%) |      20   →      19     (-5.00%) |       98.37 ms →       86.15 ms  (-12.42%) | 
  │ │ └ sirius::Density::get_magnetisation                              |       76.53 μs →       77.15 μs   (+0.80%) |      20   →      19     (-5.00%) |        1.53 ms →        1.47 ms   (-4.24%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |       71.76 μs →       71.77 μs   (+0.02%) |      20   →      19     (-5.00%) |        1.44 ms →        1.36 ms   (-4.98%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.51 ms →        5.13 ms   (-6.91%) |       2   →       2              |       11.02 ms →       10.26 ms   (-6.91%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.80 ms →        4.72 ms   (-1.59%) |       6   →       6              |       28.80 ms →       28.35 ms   (-1.59%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.80 ms →        4.72 ms   (-1.60%) |       6   →       6              |       28.78 ms →       28.32 ms   (-1.60%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.80 ms →        4.72 ms   (-1.62%) |       6   →       6              |       28.78 ms →       28.31 ms   (-1.62%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.98 ms →        5.14 ms   (+3.21%) |       3   →       3              |       14.94 ms →       15.42 ms   (+3.21%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.97 ms →        5.14 ms   (+3.22%) |       3   →       3              |       14.92 ms →       15.41 ms   (+3.22%) | 
  ├ sirius::Periodic_function|inner                                     |        4.81 ms →        4.56 ms   (-5.30%) |       2   →       2              |        9.62 ms →        9.11 ms   (-5.30%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.81 ms →        4.55 ms   (-5.30%) |       2   →       2              |        9.62 ms →        9.11 ms   (-5.30%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.81 ms →        4.55 ms   (-5.30%) |       2   →       2              |        9.62 ms →        9.11 ms   (-5.30%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.98 ms →        4.99 ms   (+0.19%) |       1   →       1              |        4.98 ms →        4.99 ms   (+0.19%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.97 ms →        4.98 ms   (+0.13%) |       1   →       1              |        4.97 ms →        4.98 ms   (+0.13%) | 
+ └ sirius::finalize                                                    |      938.25 ms →      264.55 ms  (-71.80%) |       1   →       1              |      938.25 ms →      264.55 ms  (-71.80%) | 
  ====================================================================================================================================================================================================
```
