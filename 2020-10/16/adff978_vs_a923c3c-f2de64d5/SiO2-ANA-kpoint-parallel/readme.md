# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      133.28 s  →      126.43 s    (-5.14%) |       1   →       1              |      133.28 s  →      126.43 s    (-5.14%) | 
  ├ sirius::initialize                                                  |        2.71 s  →        2.72 s    (+0.60%) |       1   →       1              |        2.71 s  →        2.72 s    (+0.60%) | 
  ├ sirius::Simulation_context::initialize                              |        2.98 s  →        2.93 s    (-1.63%) |       1   →       1              |        2.98 s  →        2.93 s    (-1.63%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       53.43 ms →       30.98 ms  (-42.03%) |       1   →       1              |       53.43 ms →       30.98 ms  (-42.03%) | 
  │ ├ sirius::Unit_cell::initialize                                     |      148.68 ms →      138.28 ms   (-6.99%) |       1   →       1              |      148.68 ms →      138.28 ms   (-6.99%) | 
  │ │ ├ sirius::Atom_type::init                                         |       62.20 ms →       57.77 ms   (-7.11%) |       2   →       2              |      124.39 ms →      115.54 ms   (-7.11%) | 
  │ │ └ sirius::Unit_cell::update                                       |       24.21 ms →       22.67 ms   (-6.40%) |       1   →       1              |       24.21 ms →       22.67 ms   (-6.40%) | 
+ │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.24 ms →        5.48 ms  (-12.10%) |       1   →       1              |        6.24 ms →        5.48 ms  (-12.10%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       17.93 ms →       17.14 ms   (-4.43%) |       1   →       1              |       17.93 ms →       17.14 ms   (-4.43%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       17.91 ms →       17.12 ms   (-4.42%) |       1   →       1              |       17.91 ms →       17.12 ms   (-4.42%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.13 ms →        4.13 ms   (+0.02%) |       1   →       1              |        4.13 ms →        4.13 ms   (+0.02%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.34 ms →        2.34 ms   (-0.21%) |       1   →       1              |        2.34 ms →        2.34 ms   (-0.21%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      105.46 μs →      100.59 μs   (-4.62%) |       1   →       1              |      105.46 μs →      100.59 μs   (-4.62%) | 
  │ └ sirius::Simulation_context::update                                |        2.73 s  →        2.72 s    (-0.45%) |       1   →       1              |        2.73 s  →        2.72 s    (-0.45%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.81 ms →       10.82 ms   (+0.10%) |       1   →       1              |       10.81 ms →       10.82 ms   (+0.10%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.44 ms →        4.45 ms   (+0.28%) |       1   →       1              |        4.44 ms →        4.45 ms   (+0.28%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.34 ms →        6.34 ms   (-0.03%) |       1   →       1              |        6.34 ms →        6.34 ms   (-0.03%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.32 ms →        6.32 ms   (-0.01%) |       1   →       1              |        6.32 ms →        6.32 ms   (-0.01%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.83 ms →        3.83 ms   (+0.17%) |       1   →       1              |        3.83 ms →        3.83 ms   (+0.17%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.31 ms   (-0.61%) |       1   →       1              |        2.32 ms →        2.31 ms   (-0.61%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      100.67 μs →       98.92 μs   (-1.74%) |       1   →       1              |      100.67 μs →       98.92 μs   (-1.74%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       63.88 ms →       63.62 ms   (-0.40%) |       2   →       2              |      127.75 ms →      127.24 ms   (-0.40%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.15 ms →        5.23 ms   (+1.51%) |       2   →       2              |       10.30 ms →       10.46 ms   (+1.51%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.50 ms →        4.55 ms   (+1.24%) |       1   →       1              |        4.50 ms →        4.55 ms   (+1.24%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.83 ms →       21.77 ms   (-0.26%) |       2   →       2              |       43.65 ms →       43.54 ms   (-0.26%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.85 ms →       14.99 ms   (+0.89%) |       2   →       2              |       29.71 ms →       29.97 ms   (+0.89%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.69 ms →       19.49 ms   (-1.03%) |       4   →       4              |       78.76 ms →       77.95 ms   (-1.03%) | 
  │   ├ sddk::Gvec::init                                                |      174.08 ms →      181.01 ms   (+3.98%) |       2   →       2              |      348.17 ms →      362.02 ms   (+3.98%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      129.55 ms →      138.20 ms   (+6.68%) |       2   →       2              |      259.10 ms →      276.40 ms   (+6.68%) | 
- │   ├ sddk::Gvec_shells                                               |      183.90 ms →      206.78 ms  (+12.44%) |       1   →       1              |      183.90 ms →      206.78 ms  (+12.44%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.32 ms →        1.33 ms   (+0.23%) |       1   →       1              |        1.32 ms →        1.33 ms   (+0.23%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      292.72 ms →      290.81 ms   (-0.65%) |       2   →       2              |      585.43 ms →      581.62 ms   (-0.65%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       36.08 ms →       35.76 ms   (-0.91%) |       1   →       1              |       36.08 ms →       35.76 ms   (-0.91%) | 
- │ ├ sirius::K_point::K_point                                          |        2.10 μs →        2.46 μs  (+17.09%) |       4   →       4              |        8.39 μs →        9.82 μs  (+17.09%) | 
  │ └ sirius::K_point_set::initialize                                   |       35.98 ms →       35.66 ms   (-0.89%) |       1   →       1              |       35.98 ms →       35.66 ms   (-0.89%) | 
  │   └ sirius::K_point::initialize                                     |       35.88 ms →       35.56 ms   (-0.90%) |       1   →       1              |       35.88 ms →       35.56 ms   (-0.90%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       18.41 ms →       18.14 ms   (-1.44%) |       1   →       1              |       18.41 ms →       18.14 ms   (-1.44%) | 
  │     │ └ sddk::Gvec::init                                            |        8.32 ms →        8.19 ms   (-1.54%) |       1   →       1              |        8.32 ms →        8.19 ms   (-1.54%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |       10.03 μs →       10.12 μs   (+0.88%) |       1   →       1              |       10.03 μs →       10.12 μs   (+0.88%) | 
  │     └ sirius::K_point::update                                       |       12.43 ms →       12.65 ms   (+1.80%) |       1   →       1              |       12.43 ms →       12.65 ms   (+1.80%) | 
  │       └ sirius::Beta_projectors                                     |        6.09 ms →        6.47 ms   (+6.20%) |       1   →       1              |        6.09 ms →        6.47 ms   (+6.20%) | 
- │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.50 ms →        3.86 ms  (+10.32%) |       1   →       1              |        3.50 ms →        3.86 ms  (+10.32%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.27 ms →        5.36 ms   (+1.67%) |       2   →       2              |       10.54 ms →       10.72 ms   (+1.67%) | 
  ├ sirius::Potential                                                   |      158.95 ms →      158.66 ms   (-0.18%) |       1   →       1              |      158.95 ms →      158.66 ms   (-0.18%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.93 ms →        5.85 ms   (-1.24%) |       6   →       6              |       35.56 ms →       35.12 ms   (-1.24%) | 
  │ └ sirius::Potential::update                                         |      122.62 ms →      122.80 ms   (+0.14%) |       1   →       1              |      122.62 ms →      122.80 ms   (+0.14%) | 
  │   └ sirius::Potential::generate_local_potential                     |      121.81 ms →      121.99 ms   (+0.15%) |       1   →       1              |      121.81 ms →      121.99 ms   (+0.15%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      106.93 ms →      106.30 ms   (-0.59%) |       1   →       1              |      106.93 ms →      106.30 ms   (-0.59%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |       13.96 ms →       14.80 ms   (+6.02%) |       1   →       1              |       13.96 ms →       14.80 ms   (+6.02%) | 
  ├ sirius::Density                                                     |      135.98 ms →      134.99 ms   (-0.72%) |       1   →       1              |      135.98 ms →      134.99 ms   (-0.72%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.25 ms →        5.12 ms   (-2.38%) |       2   →       2              |       10.50 ms →       10.25 ms   (-2.38%) | 
  │ └ sirius::Density::update                                           |      125.21 ms →      124.47 ms   (-0.58%) |       1   →       1              |      125.21 ms →      124.47 ms   (-0.58%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      124.78 ms →      124.03 ms   (-0.60%) |       1   →       1              |      124.78 ms →      124.03 ms   (-0.60%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |      105.01 μs →      103.70 μs   (-1.25%) |       1   →       1              |      105.01 μs →      103.70 μs   (-1.25%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      109.58 ms →      109.36 ms   (-0.19%) |       1   →       1              |      109.58 ms →      109.36 ms   (-0.19%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |       14.63 ms →       14.11 ms   (-3.56%) |       1   →       1              |       14.63 ms →       14.11 ms   (-3.56%) | 
  ├ sirius::Density::initial_density                                    |      175.51 ms →      177.86 ms   (+1.34%) |       1   →       1              |      175.51 ms →      177.86 ms   (+1.34%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      109.60 ms →      109.13 ms   (-0.43%) |       1   →       1              |      109.60 ms →      109.13 ms   (-0.43%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |       11.70 ms →       11.90 ms   (+1.68%) |       2   →       2              |       23.41 ms →       23.80 ms   (+1.68%) | 
- │ └ sirius::Periodic_function::integrate                              |       10.24 ms →       12.40 ms  (+21.03%) |       1   →       1              |       10.24 ms →       12.40 ms  (+21.03%) | 
  ├ sirius::Potential::generate                                         |      593.51 ms →      594.04 ms   (+0.09%) |       1   →       1              |      593.51 ms →      594.04 ms   (+0.09%) | 
  │ ├ sirius::Potential::poisson                                        |      136.63 ms →      136.76 ms   (+0.10%) |       1   →       1              |      136.63 ms →      136.76 ms   (+0.10%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       18.63 ms →       18.23 ms   (-2.19%) |       1   →       1              |       18.63 ms →       18.23 ms   (-2.19%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.24 ms →        9.95 ms   (-2.78%) |       1   →       1              |       10.24 ms →        9.95 ms   (-2.78%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        9.95 ms →        9.83 ms   (-1.15%) |       1   →       1              |        9.95 ms →        9.83 ms   (-1.15%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.94 ms →        9.82 ms   (-1.12%) |       1   →       1              |        9.94 ms →        9.82 ms   (-1.12%) | 
  │ ├ sirius::Periodic_function::add                                    |      558.94 μs →      557.70 μs   (-0.22%) |       2   →       2              |        1.12 ms →        1.12 ms   (-0.22%) | 
  │ ├ sirius::Potential::xc                                             |       54.12 ms →       53.82 ms   (-0.57%) |       1   →       1              |       54.12 ms →       53.82 ms   (-0.57%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.72 ms →       51.40 ms   (-0.61%) |       1   →       1              |       51.72 ms →       51.40 ms   (-0.61%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.72 ms →        5.71 ms   (-0.06%) |       2   →       2              |       11.43 ms →       11.42 ms   (-0.06%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.24 ms →        5.15 ms   (-1.82%) |       1   →       1              |        5.24 ms →        5.15 ms   (-1.82%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        6.09 ms →        5.77 ms   (-5.24%) |       1   →       1              |        6.09 ms →        5.77 ms   (-5.24%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.71 ms →       95.52 ms   (+3.03%) |       1   →       1              |       92.71 ms →       95.52 ms   (+3.03%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      301.46 ms →      299.67 ms   (-0.60%) |       1   →       1              |      301.46 ms →      299.67 ms   (-0.60%) | 
  ├ sirius::Hamiltonian0                                                |        8.46 ms →        8.48 ms   (+0.29%) |       1   →       1              |        8.46 ms →        8.48 ms   (+0.29%) | 
  │ ├ sirius::Local_operator                                            |        8.11 ms →        8.13 ms   (+0.29%) |       1   →       1              |        8.11 ms →        8.13 ms   (+0.29%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.75 ms →        4.79 ms   (+0.76%) |       1   →       1              |        4.75 ms →        4.79 ms   (+0.76%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.44 ms →        2.43 ms   (-0.52%) |       1   →       1              |        2.44 ms →        2.43 ms   (-0.52%) | 
  │ ├ sirius::Non_local_operator                                        |       62.18 μs →       62.94 μs   (+1.21%) |       2   →       2              |      124.36 μs →      125.88 μs   (+1.21%) | 
  │ ├ sirius::D_operator::initialize                                    |       96.23 μs →       97.41 μs   (+1.22%) |       1   →       1              |       96.23 μs →       97.41 μs   (+1.22%) | 
  │ └ sirius::Q_operator::initialize                                    |       75.28 μs →       75.25 μs   (-0.04%) |       1   →       1              |       75.28 μs →       75.25 μs   (-0.04%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.85 s  →        1.85 s    (-0.04%) |       1   →       1              |        1.85 s  →        1.85 s    (-0.04%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.70 ms →       18.67 ms   (-0.17%) |       1   →       1              |       18.70 ms →       18.67 ms   (-0.17%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      187.93 μs →      193.44 μs   (+2.93%) |       1   →       1              |      187.93 μs →      193.44 μs   (+2.93%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       18.51 ms →       18.47 ms   (-0.20%) |       1   →       1              |       18.51 ms →       18.47 ms   (-0.20%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.83 s  →        1.83 s    (-0.04%) |       1   →       1              |        1.83 s  →        1.83 s    (-0.04%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      125.94 ms →      125.85 ms   (-0.07%) |       4   →       4              |      503.77 ms →      503.40 ms   (-0.07%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       52.29 ms →       52.66 ms   (+0.71%) |       1   →       1              |       52.29 ms →       52.66 ms   (+0.71%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.11 ms →       21.07 ms   (-0.20%) |       1   →       1              |       21.11 ms →       21.07 ms   (-0.20%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      634.60 ms →      634.07 ms   (-0.08%) |       1   →       1              |      634.60 ms →      634.07 ms   (-0.08%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      297.53 ms →      297.24 ms   (-0.10%) |       1   →       1              |      297.53 ms →      297.24 ms   (-0.10%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.92 μs →        3.64 μs   (-7.14%) |       1   →       1              |        3.92 μs →        3.64 μs   (-7.14%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.03 μs →        2.48 μs  (-18.28%) |       1   →       1              |        3.03 μs →        2.48 μs  (-18.28%) | 
+ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      430.00 ns →      353.00 ns  (-17.91%) |       1   →       1              |      430.00 ns →      353.00 ns  (-17.91%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      487.00 ns →      484.00 ns   (-0.62%) |       1   →       1              |      487.00 ns →      484.00 ns   (-0.62%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.22 ms →        9.22 ms   (+0.06%) |       1   →       1              |        9.22 ms →        9.22 ms   (+0.06%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      120.85 ms →      120.59 ms   (-0.21%) |       1   →       1              |      120.85 ms →      120.59 ms   (-0.21%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      103.48 ms →      103.49 ms   (+0.00%) |       2   →       2              |      206.97 ms →      206.98 ms   (+0.00%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       40.11 ms →       40.12 ms   (+0.04%) |       2   →       2              |       80.21 ms →       80.24 ms   (+0.04%) | 
  │ │ │ └ sddk::wf_inner                                                |       39.57 ms →       39.59 ms   (+0.04%) |       2   →       2              |       79.14 ms →       79.17 ms   (+0.04%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       19.00 ns →       34.50 ns  (+81.58%) |       2   →       2              |       38.00 ns →       69.00 ns  (+81.58%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       39.09 ms →       39.11 ms   (+0.04%) |       2   →       2              |       78.19 ms →       78.22 ms   (+0.04%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       19.00 ns →       29.00 ns  (+52.63%) |       2   →       2              |       38.00 ns →       58.00 ns  (+52.63%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       56.28 ms →       56.17 ms   (-0.19%) |       1   →       1              |       56.28 ms →       56.17 ms   (-0.19%) | 
  │ │ └ sddk::wf_trans                                                  |       30.73 ms →       30.75 ms   (+0.06%) |       1   →       1              |       30.73 ms →       30.75 ms   (+0.06%) | 
  │ │   └ sddk::wf_trans|pw                                             |       30.73 ms →       30.75 ms   (+0.06%) |       1   →       1              |       30.73 ms →       30.75 ms   (+0.06%) | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      394.00 ns →      477.00 ns  (+21.07%) |       1   →       1              |      394.00 ns →      477.00 ns  (+21.07%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      123.55 s  →      116.76 s    (-5.50%) |       1   →       1              |      123.55 s  →      116.76 s    (-5.50%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.86 ms →        5.86 ms   (+0.08%) |      19   →      19              |      111.34 ms →      111.43 ms   (+0.08%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.74 s  →        4.66 s    (-1.78%) |      26   →      25     (-3.85%) |      123.23 s  →      116.38 s    (-5.56%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        5.69 ms →        5.85 ms   (+2.89%) |      26   →      25     (-3.85%) |      147.93 ms →      146.35 ms   (-1.07%) | 
  │ │ │ ├ sirius::Local_operator                                        |        5.32 ms →        5.49 ms   (+3.05%) |      26   →      25     (-3.85%) |      138.43 ms →      137.17 ms   (-0.91%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |        1.01 ms →        1.03 ms   (+1.64%) |      26   →      25     (-3.85%) |       26.29 ms →       25.69 ms   (-2.27%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.42 ms →        3.57 ms   (+4.14%) |      26   →      25     (-3.85%) |       89.02 ms →       89.14 ms   (+0.14%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.32 μs →       63.72 μs   (-0.93%) |      52   →      50     (-3.85%) |        3.34 ms →        3.19 ms   (-4.74%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       88.21 μs →       89.55 μs   (+1.52%) |      26   →      25     (-3.85%) |        2.29 ms →        2.24 ms   (-2.38%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       77.91 μs →       78.72 μs   (+1.05%) |      26   →      25     (-3.85%) |        2.03 ms →        1.97 ms   (-2.84%) | 
  │ │ ├ sirius::Band::solve                                             |        2.76 s  →        2.67 s    (-3.22%) |      26   →      25     (-3.85%) |       71.64 s  →       66.67 s    (-6.94%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      152.02 μs →      155.03 μs   (+1.97%) |      26   →      25     (-3.85%) |        3.95 ms →        3.88 ms   (-1.95%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      145.68 μs →      148.06 μs   (+1.63%) |      26   →      25     (-3.85%) |        3.79 ms →        3.70 ms   (-2.28%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.48 μs →        5.08 μs  (+13.40%) |      26   →      25     (-3.85%) |      116.46 μs →      126.98 μs   (+9.04%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.60 s  →        2.55 s    (-1.77%) |      26   →      25     (-3.85%) |       67.63 s  →       63.87 s    (-5.55%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       95.61 ms →       96.32 ms   (+0.74%) |      26   →      25     (-3.85%) |        2.49 s  →        2.41 s    (-3.13%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.74 ms →        7.89 ms   (+1.88%) |     156   →     150     (-3.85%) |        1.21 s  →        1.18 s    (-2.04%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        5.94 ms →        5.97 ms   (+0.43%) |      26   →      25     (-3.85%) |      154.49 ms →      149.19 ms   (-3.44%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      350.71 μs →      350.40 μs   (-0.09%) |      26   →      25     (-3.85%) |        9.12 ms →        8.76 ms   (-3.93%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.30 ms →        2.30 ms   (-0.33%) |      52   →      50     (-3.85%) |      119.80 ms →      114.82 ms   (-4.16%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.46 s  →        2.42 s    (-1.90%) |      26   →      25     (-3.85%) |       64.05 s  →       60.42 s    (-5.67%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      129.55 ms →      119.92 ms   (-7.43%) |     271   →     298     (+9.96%) |       35.11 s  →       35.74 s    (+1.79%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       52.08 ms →       47.56 ms   (-8.67%) |     271   →     298     (+9.96%) |       14.11 s  →       14.17 s    (+0.43%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.86 μs →        1.83 μs   (-1.19%) |     271   →     298     (+9.96%) |      503.08 μs →      546.64 μs   (+8.66%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.59 μs →        1.52 μs   (-4.40%) |     271   →     298     (+9.96%) |      430.04 μs →      452.06 μs   (+5.12%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      350.23 ns →      308.19 ns  (-12.00%) |     271   →     298     (+9.96%) |       94.91 μs →       91.84 μs   (-3.24%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      448.48 ns →      430.98 ns   (-3.90%) |     271   →     298     (+9.96%) |      121.54 μs →      128.43 μs   (+5.67%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.43 ms →        7.40 ms   (-0.42%) |     271   →     298     (+9.96%) |        2.01 s  →        2.20 s    (+9.50%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       23.45 ms →       21.39 ms   (-8.81%) |     271   →     298     (+9.96%) |        6.36 s  →        6.37 s    (+0.28%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       23.29 ms →       21.78 ms   (-6.49%) |     542   →     596     (+9.96%) |       12.62 s  →       12.98 s    (+2.83%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       34.91 ms →       31.77 ms   (-9.01%) |     271   →     298     (+9.96%) |        9.46 s  →        9.47 s    (+0.05%) | 
! │ │ │ │   │ ├ sddk::wf_inner                                          |        6.06 ms →        5.54 ms   (-8.57%) |     516   →     571    (+10.66%) |        3.13 s  →        3.16 s    (+1.17%) | 
! │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       68.15 ns →       61.33 ns  (-10.00%) |     516   →     571    (+10.66%) |       35.16 μs →       35.02 μs   (-0.40%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        4.95 ms →        4.42 ms  (-10.55%) |     516   →     571    (+10.66%) |        2.55 s  →        2.53 s    (-1.02%) | 
+ │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       54.34 ns →       43.66 ns  (-19.66%) |     516   →     571    (+10.66%) |       28.04 μs →       24.93 μs  (-11.09%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      630.28 μs →      578.33 μs   (-8.24%) |     271   →     298     (+9.96%) |      170.81 ms →      172.34 ms   (+0.90%) | 
+ │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        9.77 ms →        8.79 ms  (-10.01%) |     271   →     298     (+9.96%) |        2.65 s  →        2.62 s    (-1.05%) | 
+ │ │ │ │   │ └ sddk::wf_trans                                          |       14.36 ms →       12.86 ms  (-10.40%) |     245   →     273    (+11.43%) |        3.52 s  →        3.51 s    (-0.16%) | 
+ │ │ │ │   │   └ sddk::wf_trans|pw                                     |        4.78 ms →        4.29 ms  (-10.41%) |     735   →     819    (+11.43%) |        3.52 s  →        3.51 s    (-0.17%) | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       10.50 ms →        9.07 ms  (-13.68%) |     271   →     298     (+9.96%) |        2.85 s  →        2.70 s    (-5.08%) | 
+ │ │ │ │   │ └ sddk::wf_inner                                          |       10.23 ms →        8.88 ms  (-13.23%) |     271   →     298     (+9.96%) |        2.77 s  →        2.65 s    (-4.59%) | 
- │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       46.82 ns →       52.56 ns  (+12.26%) |     271   →     298     (+9.96%) |       12.69 μs →       15.66 μs  (+23.45%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        9.12 ms →        7.77 ms  (-14.85%) |     271   →     298     (+9.96%) |        2.47 s  →        2.31 s    (-6.37%) | 
+ │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       73.94 ns →       36.44 ns  (-50.71%) |     271   →     298     (+9.96%) |       20.04 μs →       10.86 μs  (-45.80%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       33.40 ms →       15.54 ms  (-53.47%) |     271   →     298     (+9.96%) |        9.05 s  →        4.63 s   (-48.84%) | 
+ │ │ │ │   ├ sirius::residuals                                         |       13.77 ms →       11.46 ms  (-16.75%) |     262   →     286     (+9.16%) |        3.61 s  →        3.28 s    (-9.13%) | 
+ │ │ │ │   │ ├ sddk::wf_trans                                          |       12.44 ms →        9.97 ms  (-19.81%) |     252   →     280    (+11.11%) |        3.13 s  →        2.79 s   (-10.90%) | 
+ │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        6.22 ms →        4.99 ms  (-19.82%) |     504   →     560    (+11.11%) |        3.13 s  →        2.79 s   (-10.91%) | 
! │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.62 ms →        1.50 ms   (-7.60%) |     252   →     280    (+11.11%) |      408.83 ms →      419.75 ms   (+2.67%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       74.91 ms →       50.58 ms  (-32.48%) |      53   →      91    (+71.70%) |        3.97 s  →        4.60 s   (+15.93%) | 
- │ │ │ │     └ sddk::wf_trans                                          |       49.39 ms →       29.05 ms  (-41.19%) |      80   →     157    (+96.25%) |        3.95 s  →        4.56 s   (+15.41%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |       36.93 ms →       20.45 ms  (-44.62%) |     107   →     223   (+108.41%) |        3.95 s  →        4.56 s   (+15.41%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      652.31 ns →      427.72 ns  (-34.43%) |      26   →      25     (-3.85%) |       16.96 μs →       10.69 μs  (-36.95%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       48.59 μs →       51.02 μs   (+5.00%) |      26   →      25     (-3.85%) |        1.26 ms →        1.28 ms   (+0.97%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      596.78 μs →      583.46 μs   (-2.23%) |      26   →      25     (-3.85%) |       15.52 ms →       14.59 ms   (-5.99%) | 
  │ │ ├ sirius::Density::generate                                       |      774.71 ms →      782.34 ms   (+0.99%) |      26   →      25     (-3.85%) |       20.14 s  →       19.56 s    (-2.90%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      403.14 ms →      402.15 ms   (-0.24%) |      26   →      25     (-3.85%) |       10.48 s  →       10.05 s    (-4.08%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.19 μs →        8.77 μs   (+7.00%) |      26   →      25     (-3.85%) |      213.00 μs →      219.14 μs   (+2.88%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.69 μs →        8.29 μs   (+7.82%) |      26   →      25     (-3.85%) |      199.93 μs →      207.27 μs   (+3.68%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |      100.19 ms →      100.18 ms   (-0.01%) |      26   →      25     (-3.85%) |        2.60 s  →        2.50 s    (-3.86%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.06 μs →        7.77 μs   (+9.96%) |      26   →      25     (-3.85%) |      183.65 μs →      194.17 μs   (+5.73%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.12 ms →        7.12 ms   (-0.04%) |      26   →      25     (-3.85%) |      185.09 ms →      177.90 ms   (-3.89%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       91.15 ms →       91.14 ms   (-0.01%) |      26   →      25     (-3.85%) |        2.37 s  →        2.28 s    (-3.86%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      717.15 ns →      606.08 ns  (-15.49%) |      26   →      25     (-3.85%) |       18.65 μs →       15.15 μs  (-18.74%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      162.67 ms →      162.45 ms   (-0.13%) |      26   →      25     (-3.85%) |        4.23 s  →        4.06 s    (-3.97%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.65 ms   (+0.60%) |      26   →      25     (-3.85%) |       42.68 ms →       41.29 ms   (-3.26%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.33 ms →       88.32 ms   (-0.01%) |      26   →      25     (-3.85%) |        2.30 s  →        2.21 s    (-3.86%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.10 ms →       88.10 ms   (+0.00%) |      26   →      25     (-3.85%) |        2.29 s  →        2.20 s    (-3.84%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      276.19 ms →      288.25 ms   (+4.37%) |      26   →      25     (-3.85%) |        7.18 s  →        7.21 s    (+0.35%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      276.19 ms →      288.25 ms   (+4.37%) |      26   →      25     (-3.85%) |        7.18 s  →        7.21 s    (+0.35%) | 
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       26.45 ms →       30.28 ms  (+14.48%) |      26   →      25     (-3.85%) |      687.65 ms →      756.92 ms  (+10.07%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      225.50 ms →      228.09 ms   (+1.15%) |      26   →      25     (-3.85%) |        5.86 s  →        5.70 s    (-2.74%) | 
- │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       23.05 ms →       28.68 ms  (+24.43%) |      26   →      25     (-3.85%) |      599.20 ms →      716.93 ms  (+19.65%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       85.45 ms →       80.59 ms   (-5.69%) |      26   →      25     (-3.85%) |        2.22 s  →        2.01 s    (-9.32%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        6.34 ms →        7.70 ms  (+21.44%) |      26   →      25     (-3.85%) |      164.83 ms →      192.47 ms  (+16.77%) | 
  │ │ ├ sirius::Density::mix                                            |      219.30 ms →      212.27 ms   (-3.21%) |      26   →      25     (-3.85%) |        5.70 s  →        5.31 s    (-6.93%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      916.46 μs →      931.40 μs   (+1.63%) |      26   →      25     (-3.85%) |       23.83 ms →       23.28 ms   (-2.28%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.78 ms →       10.27 ms   (-4.69%) |     334   →     319     (-4.49%) |        3.60 s  →        3.28 s    (-8.97%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.38 ms →        9.95 ms   (-4.21%) |     334   →     319     (-4.49%) |        3.47 s  →        3.17 s    (-8.51%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.38 ms →        9.94 ms   (-4.21%) |     334   →     319     (-4.49%) |        3.47 s  →        3.17 s    (-8.51%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        6.22 ms →        6.55 ms   (+5.28%) |      26   →      25     (-3.85%) |      161.70 ms →      163.69 ms   (+1.23%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.37 ms →        5.73 ms   (+6.84%) |      26   →      25     (-3.85%) |      139.50 ms →      143.31 ms   (+2.73%) | 
  │ │ ├ sirius::Potential::generate                                     |      578.52 ms →      578.22 ms   (-0.05%) |      26   →      25     (-3.85%) |       15.04 s  →       14.46 s    (-3.90%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      137.00 ms →      136.90 ms   (-0.07%) |      26   →      25     (-3.85%) |        3.56 s  →        3.42 s    (-3.92%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       19.08 ms →       18.11 ms   (-5.11%) |      26   →      25     (-3.85%) |      496.10 ms →      452.63 ms   (-8.76%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.31 ms →       10.23 ms   (-0.78%) |      26   →      25     (-3.85%) |      268.03 ms →      255.70 ms   (-4.60%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.00 ms →        9.87 ms   (-1.31%) |      26   →      25     (-3.85%) |      259.93 ms →      246.66 ms   (-5.11%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.00 ms →        9.87 ms   (-1.31%) |      26   →      25     (-3.85%) |      259.92 ms →      246.65 ms   (-5.11%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      549.44 μs →      552.43 μs   (+0.54%) |      52   →      50     (-3.85%) |       28.57 ms →       27.62 ms   (-3.32%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       49.24 ms →       48.91 ms   (-0.66%) |      26   →      25     (-3.85%) |        1.28 s  →        1.22 s    (-4.48%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.82 ms →       46.52 ms   (-0.64%) |      26   →      25     (-3.85%) |        1.22 s  →        1.16 s    (-4.46%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.06 ms →        3.09 ms   (+0.87%) |      52   →      50     (-3.85%) |      159.38 ms →      154.58 ms   (-3.01%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.32 ms →        5.40 ms   (+1.38%) |      26   →      25     (-3.85%) |      138.37 ms →      134.88 ms   (-2.52%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.65 ms →        6.57 ms   (-1.25%) |      26   →      25     (-3.85%) |      172.91 ms →      164.19 ms   (-5.04%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.96 ms →       90.99 ms   (+0.04%) |      26   →      25     (-3.85%) |        2.36 s  →        2.27 s    (-3.81%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      292.25 ms →      292.44 ms   (+0.06%) |      26   →      25     (-3.85%) |        7.60 s  →        7.31 s    (-3.79%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      281.81 ms →      291.58 ms   (+3.47%) |      26   →      25     (-3.85%) |        7.33 s  →        7.29 s    (-0.51%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      281.81 ms →      291.58 ms   (+3.47%) |      26   →      25     (-3.85%) |        7.33 s  →        7.29 s    (-0.51%) | 
- │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       29.28 ms →       33.08 ms  (+12.98%) |      26   →      25     (-3.85%) |      761.30 ms →      827.07 ms   (+8.64%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      224.94 ms →      225.08 ms   (+0.06%) |      26   →      25     (-3.85%) |        5.85 s  →        5.63 s    (-3.79%) | 
- │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.76 ms →       29.61 ms  (+24.62%) |      26   →      25     (-3.85%) |      617.74 ms →      740.25 ms  (+19.83%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        8.55 ms →        6.02 ms  (-29.62%) |      26   →      25     (-3.85%) |      222.41 ms →      150.51 ms  (-32.33%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.22 ms →       10.02 ms   (-1.98%) |     182   →     175     (-3.85%) |        1.86 s  →        1.75 s    (-5.75%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.81 ms →        9.76 ms   (-0.50%) |     182   →     175     (-3.85%) |        1.78 s  →        1.71 s    (-4.33%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.81 ms →        9.76 ms   (-0.50%) |     182   →     175     (-3.85%) |        1.78 s  →        1.71 s    (-4.33%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       11.02 ms →       10.36 ms   (-5.98%) |      78   →      75     (-3.85%) |      859.84 ms →      777.32 ms   (-9.60%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.62 ms →       10.13 ms   (-4.59%) |      78   →      75     (-3.85%) |      827.99 ms →      759.62 ms   (-8.26%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        9.98 ms →        9.84 ms   (-1.49%) |      26   →      25     (-3.85%) |      259.60 ms →      245.89 ms   (-5.28%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      114.53 μs →      144.77 μs  (+26.40%) |      26   →      25     (-3.85%) |        2.98 ms →        3.62 ms  (+21.54%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      109.65 μs →      140.31 μs  (+27.96%) |      26   →      25     (-3.85%) |        2.85 ms →        3.51 ms  (+23.04%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.32 ms →        5.24 ms   (-1.59%) |       2   →       2              |       10.64 ms →       10.47 ms   (-1.59%) | 
  │ ├ sirius::Periodic_function|inner                                   |        9.69 ms →        9.76 ms   (+0.79%) |       6   →       6              |       58.12 ms →       58.58 ms   (+0.79%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        9.67 ms →        9.61 ms   (-0.64%) |       6   →       6              |       58.04 ms →       57.67 ms   (-0.64%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        9.67 ms →        9.61 ms   (-0.64%) |       6   →       6              |       58.04 ms →       57.67 ms   (-0.64%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.55 ms →       10.13 ms   (-3.99%) |       3   →       3              |       31.64 ms →       30.38 ms   (-3.99%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.49 ms →       10.02 ms   (-4.45%) |       3   →       3              |       31.47 ms →       30.07 ms   (-4.45%) | 
  ├ sirius::Periodic_function|inner                                     |        9.86 ms →        9.82 ms   (-0.46%) |       2   →       2              |       19.73 ms →       19.64 ms   (-0.46%) | 
  │ └ sirius::Periodic_function|inner_local                             |        9.85 ms →        9.79 ms   (-0.60%) |       2   →       2              |       19.71 ms →       19.59 ms   (-0.60%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.85 ms →        9.79 ms   (-0.61%) |       2   →       2              |       19.71 ms →       19.59 ms   (-0.61%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.61 ms →       10.23 ms   (-3.53%) |       1   →       1              |       10.61 ms →       10.23 ms   (-3.53%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.48 ms →       10.02 ms   (-4.41%) |       1   →       1              |       10.48 ms →       10.02 ms   (-4.41%) | 
  └ sirius::finalize                                                    |      221.14 ms →      221.09 ms   (-0.02%) |       1   →       1              |      221.14 ms →      221.09 ms   (-0.02%) | 
  ====================================================================================================================================================================================================
```
