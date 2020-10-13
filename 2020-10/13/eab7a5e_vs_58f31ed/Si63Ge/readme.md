# Benchmark 58f31ed08f2b4e9e6d289f9ed116027f00413e03 vs eab7a5e09a790e571ffec2b67e8d778bf317b1b5
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
- sirius                                                                |       71.75 s  →       81.41 s   (+13.47%) |       1   →       1              |       71.75 s  →       81.41 s   (+13.47%) | 
  ├ sirius::initialize                                                  |        2.94 s  →        2.99 s    (+1.94%) |       1   →       1              |        2.94 s  →        2.99 s    (+1.94%) | 
  ├ sirius::Simulation_context::initialize                              |        3.50 s  →        3.74 s    (+6.76%) |       1   →       1              |        3.50 s  →        3.74 s    (+6.76%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       16.33 ms →      448.43 μs  (-97.25%) |       1   →       1              |       16.33 ms →      448.43 μs  (-97.25%) | 
  │ ├ sirius::Unit_cell::initialize                                     |      127.11 ms →      121.56 ms   (-4.37%) |       1   →       1              |      127.11 ms →      121.56 ms   (-4.37%) | 
  │ │ ├ sirius::Atom_type::init                                         |       54.04 ms →       49.96 ms   (-7.55%) |       2   →       2              |      108.08 ms →       99.92 ms   (-7.55%) | 
- │ │ └ sirius::Unit_cell::update                                       |       18.94 ms →       21.55 ms  (+13.75%) |       1   →       1              |       18.94 ms →       21.55 ms  (+13.75%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        5.22 ms →        4.97 ms   (-4.66%) |       1   →       1              |        5.22 ms →        4.97 ms   (-4.66%) | 
- │ │   └ sirius::Unit_cell::get_symmetry                               |       13.66 ms →       16.50 ms  (+20.87%) |       1   →       1              |       13.66 ms →       16.50 ms  (+20.87%) | 
- │ │     └ sirius::Unit_cell_symmetry                                  |       13.56 ms →       16.43 ms  (+21.18%) |       1   →       1              |       13.56 ms →       16.43 ms  (+21.18%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.74 ms →        2.76 ms   (+0.83%) |       1   →       1              |        2.74 ms →        2.76 ms   (+0.83%) | 
- │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      596.17 μs →        2.46 ms (+311.97%) |       1   →       1              |      596.17 μs →        2.46 ms (+311.97%) | 
+ │ │       └ sirius::Unit_cell_symmetry|mag                            |       27.52 μs →       16.97 μs  (-38.31%) |       1   →       1              |       27.52 μs →       16.97 μs  (-38.31%) | 
  │ └ sirius::Simulation_context::update                                |        3.23 s  →        3.50 s    (+8.48%) |       1   →       1              |        3.23 s  →        3.50 s    (+8.48%) | 
  │   ├ sirius::Unit_cell::update                                       |        7.01 ms →        6.85 ms   (-2.21%) |       1   →       1              |        7.01 ms →        6.85 ms   (-2.21%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.65 ms →        3.41 ms   (-6.43%) |       1   →       1              |        3.65 ms →        3.41 ms   (-6.43%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.31 ms →        3.38 ms   (+2.18%) |       1   →       1              |        3.31 ms →        3.38 ms   (+2.18%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.26 ms →        3.33 ms   (+2.19%) |       1   →       1              |        3.26 ms →        3.33 ms   (+2.19%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.71 ms →        2.78 ms   (+2.64%) |       1   →       1              |        2.71 ms →        2.78 ms   (+2.64%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      517.06 μs →      516.33 μs   (-0.14%) |       1   →       1              |      517.06 μs →      516.33 μs   (-0.14%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       14.80 μs →       14.36 μs   (-2.97%) |       1   →       1              |       14.80 μs →       14.36 μs   (-2.97%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      212.61 ms →      211.69 ms   (-0.44%) |       2   →       2              |      425.23 ms →      423.37 ms   (-0.44%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.50 ms →       15.21 ms   (-1.92%) |       2   →       2              |       31.01 ms →       30.41 ms   (-1.92%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.27 ms →       13.26 ms   (-0.06%) |       1   →       1              |       13.27 ms →       13.26 ms   (-0.06%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.33 ms →       56.32 ms   (-0.03%) |       2   →       2              |      112.67 ms →      112.64 ms   (-0.03%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.27 ms →       45.17 ms   (-0.22%) |       2   →       2              |       90.54 ms →       90.34 ms   (-0.22%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.20 ms →       60.30 ms   (+0.16%) |       4   →       4              |      240.80 ms →      241.19 ms   (+0.16%) | 
  │   ├ sddk::Gvec::init                                                |       93.68 ms →       92.65 ms   (-1.10%) |       2   →       2              |      187.36 ms →      185.29 ms   (-1.10%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       70.19 ms →       69.34 ms   (-1.22%) |       2   →       2              |      140.39 ms →      138.68 ms   (-1.22%) | 
  │   ├ sddk::Gvec_shells                                               |      101.18 ms →       91.47 ms   (-9.59%) |       1   →       1              |      101.18 ms →       91.47 ms   (-9.59%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.95 ms →        1.94 ms   (-0.55%) |       1   →       1              |        1.95 ms →        1.94 ms   (-0.55%) | 
- │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      466.72 ms →      605.48 ms  (+29.73%) |       2   →       2              |      933.45 ms →        1.21 s   (+29.73%) | 
+ ├ sirius::K_point_set::create_k_mesh                                  |      222.92 ms →      129.82 ms  (-41.76%) |       1   →       1              |      222.92 ms →      129.82 ms  (-41.76%) | 
+ │ ├ sirius::K_point::K_point                                          |        2.35 μs →        1.17 μs  (-50.29%) |       4   →       4              |        9.41 μs →        4.68 μs  (-50.29%) | 
+ │ └ sirius::K_point_set::initialize                                   |      222.84 ms →      129.73 ms  (-41.78%) |       1   →       1              |      222.84 ms →      129.73 ms  (-41.78%) | 
  │   └ sirius::K_point::initialize                                     |       28.35 ms →       28.64 ms   (+1.00%) |       1   →       1              |       28.35 ms →       28.64 ms   (+1.00%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       11.41 ms →       11.17 ms   (-2.10%) |       1   →       1              |       11.41 ms →       11.17 ms   (-2.10%) | 
  │     │ └ sddk::Gvec::init                                            |        4.95 ms →        4.92 ms   (-0.51%) |       1   →       1              |        4.95 ms →        4.92 ms   (-0.51%) | 
+ │     ├ sddk::matrix_storage::matrix_storage                          |        7.44 μs →        6.63 μs  (-10.89%) |       1   →       1              |        7.44 μs →        6.63 μs  (-10.89%) | 
  │     └ sirius::K_point::update                                       |       14.06 ms →       14.61 ms   (+3.94%) |       1   →       1              |       14.06 ms →       14.61 ms   (+3.94%) | 
  │       └ sirius::Beta_projectors                                     |       10.18 ms →       10.77 ms   (+5.70%) |       1   →       1              |       10.18 ms →       10.77 ms   (+5.70%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.21 ms →        8.63 ms   (+5.13%) |       1   →       1              |        8.21 ms →        8.63 ms   (+5.13%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.55 ms →        2.54 ms   (-0.34%) |       2   →       2              |        5.11 ms →        5.09 ms   (-0.34%) | 
  ├ sirius::Potential                                                   |       53.48 ms →       49.60 ms   (-7.25%) |       1   →       1              |       53.48 ms →       49.60 ms   (-7.25%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.89 ms →        2.89 ms   (+0.04%) |       6   →       6              |       17.35 ms →       17.36 ms   (+0.04%) | 
+ │ └ sirius::Potential::update                                         |       35.55 ms →       31.66 ms  (-10.96%) |       1   →       1              |       35.55 ms →       31.66 ms  (-10.96%) | 
+ │   └ sirius::Potential::generate_local_potential                     |       35.16 ms →       31.25 ms  (-11.11%) |       1   →       1              |       35.16 ms →       31.25 ms  (-11.11%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       26.75 ms →       26.76 ms   (+0.05%) |       1   →       1              |       26.75 ms →       26.76 ms   (+0.05%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        7.90 ms →        3.96 ms  (-49.90%) |       1   →       1              |        7.90 ms →        3.96 ms  (-49.90%) | 
  ├ sirius::Density                                                     |       40.39 ms →       38.39 ms   (-4.96%) |       1   →       1              |       40.39 ms →       38.39 ms   (-4.96%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.84 ms →        2.80 ms   (-1.17%) |       2   →       2              |        5.67 ms →        5.61 ms   (-1.17%) | 
  │ └ sirius::Density::update                                           |       34.58 ms →       32.64 ms   (-5.60%) |       1   →       1              |       34.58 ms →       32.64 ms   (-5.60%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       34.29 ms →       32.42 ms   (-5.46%) |       1   →       1              |       34.29 ms →       32.42 ms   (-5.46%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |       76.34 μs →       76.96 μs   (+0.82%) |       1   →       1              |       76.34 μs →       76.96 μs   (+0.82%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       26.37 ms →       26.97 ms   (+2.26%) |       1   →       1              |       26.37 ms →       26.97 ms   (+2.26%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        7.55 ms →        5.07 ms  (-32.74%) |       1   →       1              |        7.55 ms →        5.07 ms  (-32.74%) | 
  ├ sirius::Density::initial_density                                    |       60.83 ms →       56.21 ms   (-7.59%) |       1   →       1              |       60.83 ms →       56.21 ms   (-7.59%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       26.77 ms →       28.52 ms   (+6.53%) |       1   →       1              |       26.77 ms →       28.52 ms   (+6.53%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        7.95 ms →        4.34 ms  (-45.37%) |       2   →       2              |       15.90 ms →        8.69 ms  (-45.37%) | 
- │ └ sirius::Periodic_function::integrate                              |        4.50 ms →        5.40 ms  (+19.93%) |       1   →       1              |        4.50 ms →        5.40 ms  (+19.93%) | 
  ├ sirius::Potential::generate                                         |      370.20 ms →      362.67 ms   (-2.03%) |       1   →       1              |      370.20 ms →      362.67 ms   (-2.03%) | 
+ │ ├ sirius::Potential::poisson                                        |       43.22 ms →       35.78 ms  (-17.21%) |       1   →       1              |       43.22 ms →       35.78 ms  (-17.21%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       11.63 ms →        4.01 ms  (-65.54%) |       1   →       1              |       11.63 ms →        4.01 ms  (-65.54%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        5.89 ms →        5.43 ms   (-7.72%) |       1   →       1              |        5.89 ms →        5.43 ms   (-7.72%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.64 ms →        4.65 ms   (+0.16%) |       1   →       1              |        4.64 ms →        4.65 ms   (+0.16%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.63 ms →        4.64 ms   (+0.21%) |       1   →       1              |        4.63 ms →        4.64 ms   (+0.21%) | 
  │ ├ sirius::Periodic_function::add                                    |      787.33 μs →      774.00 μs   (-1.69%) |       2   →       2              |        1.57 ms →        1.55 ms   (-1.69%) | 
  │ ├ sirius::Potential::xc                                             |       50.91 ms →       50.87 ms   (-0.08%) |       1   →       1              |       50.91 ms →       50.87 ms   (-0.08%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       49.74 ms →       49.69 ms   (-0.10%) |       1   →       1              |       49.74 ms →       49.69 ms   (-0.10%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.55 ms →        2.54 ms   (-0.19%) |       2   →       2              |        5.10 ms →        5.09 ms   (-0.19%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.08 ms →        4.01 ms   (-1.56%) |       1   →       1              |        4.08 ms →        4.01 ms   (-1.56%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.44 ms →        3.83 ms  (+11.41%) |       1   →       1              |        3.44 ms →        3.83 ms  (+11.41%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      269.63 ms →      269.26 ms   (-0.14%) |       1   →       1              |      269.63 ms →      269.26 ms   (-0.14%) | 
+ │ └ sirius::Potential::generate_PAW_effective_potential               |      352.00 ns →      299.00 ns  (-15.06%) |       1   →       1              |      352.00 ns →      299.00 ns  (-15.06%) | 
  ├ sirius::Hamiltonian0                                                |        8.64 ms →        8.59 ms   (-0.51%) |       1   →       1              |        8.64 ms →        8.59 ms   (-0.51%) | 
  │ ├ sirius::Local_operator                                            |        7.74 ms →        7.81 ms   (+0.94%) |       1   →       1              |        7.74 ms →        7.81 ms   (+0.94%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.74 ms →        2.74 ms   (+0.03%) |       1   →       1              |        2.74 ms →        2.74 ms   (+0.03%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        3.85 ms →        3.85 ms   (-0.07%) |       1   →       1              |        3.85 ms →        3.85 ms   (-0.07%) | 
+ │ ├ sirius::Non_local_operator                                        |      320.86 μs →      257.01 μs  (-19.90%) |       2   →       2              |      641.73 μs →      514.02 μs  (-19.90%) | 
- │ ├ sirius::D_operator::initialize                                    |       98.47 μs →      111.65 μs  (+13.38%) |       1   →       1              |       98.47 μs →      111.65 μs  (+13.38%) | 
  │ └ sirius::Q_operator::initialize                                    |       92.53 μs →       93.88 μs   (+1.46%) |       1   →       1              |       92.53 μs →       93.88 μs   (+1.46%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.30 s  →        1.30 s    (+0.17%) |       1   →       1              |        1.30 s  →        1.30 s    (+0.17%) | 
- │ ├ sirius::Hamiltonian_k                                             |       58.83 ms →       65.21 ms  (+10.84%) |       1   →       1              |       58.83 ms →       65.21 ms  (+10.84%) | 
- │ │ ├ sirius::Local_operator::prepare_k                               |      222.75 μs →      271.64 μs  (+21.95%) |       1   →       1              |      222.75 μs →      271.64 μs  (+21.95%) | 
- │ │ └ sirius::Beta_projectors_base::prepare                           |       58.60 ms →       64.93 ms  (+10.80%) |       1   →       1              |       58.60 ms →       64.93 ms  (+10.80%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.24 s  →        1.23 s    (-0.33%) |       1   →       1              |        1.24 s  →        1.23 s    (-0.33%) | 
- │ │ ├ sddk::matrix_storage::matrix_storage                            |       78.39 ms →       94.10 ms  (+20.04%) |       4   →       4              |      313.55 ms →      376.39 ms  (+20.04%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       43.61 ms →       41.19 ms   (-5.56%) |       1   →       1              |       43.61 ms →       41.19 ms   (-5.56%) | 
+ │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        8.83 ms →        7.90 ms  (-10.54%) |       1   →       1              |        8.83 ms →        7.90 ms  (-10.54%) | 
- │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      337.32 ms →      383.23 ms  (+13.61%) |       1   →       1              |      337.32 ms →      383.23 ms  (+13.61%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      248.58 ms →      272.66 ms   (+9.68%) |       1   →       1              |      248.58 ms →      272.66 ms   (+9.68%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        4.04 μs →        4.16 μs   (+2.95%) |       1   →       1              |        4.04 μs →        4.16 μs   (+2.95%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.10 μs →        3.28 μs   (+5.88%) |       1   →       1              |        3.10 μs →        3.28 μs   (+5.88%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      492.00 ns →      522.00 ns   (+6.10%) |       1   →       1              |      492.00 ns →      522.00 ns   (+6.10%) | 
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      754.00 ns →      560.00 ns  (-25.73%) |       1   →       1              |      754.00 ns →      560.00 ns  (-25.73%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.21 ms →        3.05 ms   (-5.10%) |       1   →       1              |        3.21 ms →        3.05 ms   (-5.10%) | 
- │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.29 ms →       38.38 ms  (+80.28%) |       1   →       1              |       21.29 ms →       38.38 ms  (+80.28%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       32.10 ms →       34.55 ms   (+7.66%) |       2   →       2              |       64.19 ms →       69.11 ms   (+7.66%) | 
+ │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.79 ms →        7.61 ms  (-48.55%) |       2   →       2              |       29.58 ms →       15.22 ms  (-48.55%) | 
+ │ │ │ └ sddk::wf_inner                                                |       14.58 ms →        7.40 ms  (-49.25%) |       2   →       2              |       29.16 ms →       14.80 ms  (-49.25%) | 
  │ │ │   ├ sddk::wf_inner|scale                                        |       21.00 ns →       20.00 ns   (-4.76%) |       2   →       2              |       42.00 ns →       40.00 ns   (-4.76%) | 
+ │ │ │   ├ sddk::wf_inner|pw                                           |       14.45 ms →        7.27 ms  (-49.72%) |       2   →       2              |       28.91 ms →       14.53 ms  (-49.72%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       22.50 ns →       27.50 ns  (+22.22%) |       2   →       2              |       45.00 ns →       55.00 ns  (+22.22%) | 
+ │ │ ├ Eigensolver_cuda|zhegvdx                                        |      234.50 ms →      197.56 ms  (-15.75%) |       1   →       1              |      234.50 ms →      197.56 ms  (-15.75%) | 
  │ │ └ sddk::wf_trans                                                  |        2.61 ms →        2.59 ms   (-0.58%) |       1   →       1              |        2.61 ms →        2.59 ms   (-0.58%) | 
  │ │   └ sddk::wf_trans|pw                                             |        2.61 ms →        2.59 ms   (-0.55%) |       1   →       1              |        2.61 ms →        2.59 ms   (-0.55%) | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      531.00 ns →      800.00 ns  (+50.66%) |       1   →       1              |      531.00 ns →      800.00 ns  (+50.66%) | 
- ├ sirius::DFT_ground_state::scf_loop                                  |       62.15 s  →       71.63 s   (+15.25%) |       1   →       1              |       62.15 s  →       71.63 s   (+15.25%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.46 ms →        2.45 ms   (-0.44%) |      19   →      19              |       46.83 ms →       46.62 ms   (-0.44%) | 
- │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.26 s  →        3.10 s    (-4.85%) |      19   →      23    (+21.05%) |       61.95 s  →       71.36 s   (+15.18%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        5.34 ms →        4.87 ms   (-8.67%) |      19   →      23    (+21.05%) |      101.37 ms →      112.07 ms  (+10.56%) | 
- │ │ │ ├ sirius::Local_operator                                        |        4.64 ms →        4.23 ms   (-8.91%) |      19   →      23    (+21.05%) |       88.21 ms →       97.27 ms  (+10.27%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function                            |      547.04 μs →      534.34 μs   (-2.32%) |      19   →      23    (+21.05%) |       10.39 ms →       12.29 ms  (+18.24%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.82 ms →        2.69 ms   (-4.63%) |      19   →      23    (+21.05%) |       53.52 ms →       61.79 ms  (+15.45%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |      202.42 μs →      163.91 μs  (-19.02%) |      38   →      46    (+21.05%) |        7.69 ms →        7.54 ms   (-1.98%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |      117.96 μs →      130.90 μs  (+10.97%) |      19   →      23    (+21.05%) |        2.24 ms →        3.01 ms  (+34.33%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       91.18 μs →       95.01 μs   (+4.21%) |      19   →      23    (+21.05%) |        1.73 ms →        2.19 ms  (+26.15%) | 
- │ │ ├ sirius::Band::solve                                             |        2.03 s  →        1.88 s    (-7.56%) |      19   →      23    (+21.05%) |       38.59 s  →       43.19 s   (+11.90%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      210.73 μs →      254.99 μs  (+21.00%) |      19   →      23    (+21.05%) |        4.00 ms →        5.86 ms  (+46.48%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      201.71 μs →      245.45 μs  (+21.69%) |      19   →      23    (+21.05%) |        3.83 ms →        5.65 ms  (+47.30%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        6.60 μs →        7.06 μs   (+6.98%) |      19   →      23    (+21.05%) |      125.34 μs →      162.31 μs  (+29.50%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.97 s  →        1.75 s   (-10.88%) |      19   →      23    (+21.05%) |       37.36 s  →       40.31 s    (+7.89%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       76.91 ms →       68.06 ms  (-11.51%) |      19   →      23    (+21.05%) |        1.46 s  →        1.57 s    (+7.12%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.95 ms →        6.61 ms  (-16.82%) |     114   →     138    (+21.05%) |      906.12 ms →      912.36 ms   (+0.69%) | 
- │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       17.19 ms →       18.27 ms   (+6.27%) |      19   →      23    (+21.05%) |      326.66 ms →      420.23 ms  (+28.65%) | 
- │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      461.85 μs →      453.32 μs   (-1.85%) |      19   →      23    (+21.05%) |        8.78 ms →       10.43 ms  (+18.82%) | 
- │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        7.73 ms →        8.31 ms   (+7.53%) |      38   →      46    (+21.05%) |      293.72 ms →      382.32 ms  (+30.16%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.86 s  →        1.65 s   (-11.27%) |      19   →      23    (+21.05%) |       35.43 s  →       38.06 s    (+7.41%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       49.94 ms →       62.19 ms  (+24.54%) |     356   →     298    (-16.29%) |       17.78 s  →       18.53 s    (+4.25%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       28.43 ms →       36.17 ms  (+27.23%) |     356   →     298    (-16.29%) |       10.12 s  →       10.78 s    (+6.50%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.22 μs →        2.38 μs   (+7.36%) |     356   →     298    (-16.29%) |      788.78 μs →      708.90 μs  (-10.13%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.89 μs →        2.03 μs   (+7.12%) |     356   →     298    (-16.29%) |      673.08 μs →      603.57 μs  (-10.33%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      458.35 ns →      459.17 ns   (+0.18%) |     356   →     298    (-16.29%) |      163.17 μs →      136.83 μs  (-16.14%) | 
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      644.08 ns →      655.80 ns   (+1.82%) |     356   →     298    (-16.29%) |      229.29 μs →      195.43 μs  (-14.77%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.83 ms →        2.88 ms   (+1.46%) |     356   →     298    (-16.29%) |        1.01 s  →      856.91 ms  (-15.07%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.05 ms →        3.70 ms  (+21.18%) |     356   →     298    (-16.29%) |        1.09 s  →        1.10 s    (+1.44%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.80 ms →        9.71 ms  (+24.50%) |     712   →     596    (-16.29%) |        5.56 s  →        5.79 s    (+4.22%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |        7.00 ms →        7.71 ms  (+10.23%) |     356   →     298    (-16.29%) |        2.49 s  →        2.30 s    (-7.73%) | 
+ │ │ │ │   │ ├ sddk::wf_inner                                          |        1.15 ms →        1.22 ms   (+6.83%) |     693   →     573    (-17.32%) |      793.96 ms →      701.34 ms  (-11.67%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       57.58 ns →       38.42 ns  (-33.27%) |     693   →     573    (-17.32%) |       39.90 μs →       22.02 μs  (-44.82%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |      985.17 μs →        1.06 ms   (+7.75%) |     693   →     573    (-17.32%) |      682.72 ms →      608.24 ms  (-10.91%) | 
+ │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       45.30 ns →       37.36 ns  (-17.52%) |     693   →     573    (-17.32%) |       31.39 μs →       21.41 μs  (-31.81%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      141.65 μs →      169.33 μs  (+19.54%) |     356   →     298    (-16.29%) |       50.43 ms →       50.46 ms   (+0.07%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        2.21 ms →        2.79 ms  (+26.21%) |     356   →     298    (-16.29%) |      788.00 ms →      832.50 ms   (+5.65%) | 
+ │ │ │ │   │ └ sddk::wf_trans                                          |        2.54 ms →        2.59 ms   (+1.93%) |     337   →     275    (-18.40%) |      856.26 ms →      712.22 ms  (-16.82%) | 
+ │ │ │ │   │   └ sddk::wf_trans|pw                                     |      846.15 μs →      862.47 μs   (+1.93%) |    1.01 K →     825    (-18.40%) |      855.45 ms →      711.53 ms  (-16.82%) | 
- │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.52 ms →        1.75 ms  (+14.74%) |     356   →     298    (-16.29%) |      541.86 ms →      520.44 ms   (-3.95%) | 
- │ │ │ │   │ └ sddk::wf_inner                                          |        1.45 ms →        1.64 ms  (+13.20%) |     356   →     298    (-16.29%) |      516.92 ms →      489.81 ms   (-5.24%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       39.81 ns →       32.50 ns  (-18.38%) |     356   →     298    (-16.29%) |       14.17 μs →        9.68 μs  (-31.68%) | 
- │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        1.29 ms →        1.48 ms  (+14.78%) |     356   →     298    (-16.29%) |      459.18 ms →      441.20 ms   (-3.92%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       39.28 ns →       72.78 ns  (+85.26%) |     356   →     298    (-16.29%) |       13.98 μs →       21.69 μs  (+55.07%) | 
- │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       37.60 ms →       51.47 ms  (+36.88%) |     356   →     298    (-16.29%) |       13.39 s  →       15.34 s   (+14.58%) | 
- │ │ │ │   ├ sirius::residuals                                         |        2.51 ms →        3.12 ms  (+24.71%) |     340   →     289    (-15.00%) |      851.87 ms →      903.03 ms   (+6.01%) | 
- │ │ │ │   │ ├ sddk::wf_trans                                          |        1.33 ms →        1.75 ms  (+30.90%) |     337   →     278    (-17.51%) |      449.59 ms →      485.48 ms   (+7.98%) | 
- │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      665.62 μs →      871.73 μs  (+30.97%) |     674   →     556    (-17.51%) |      448.63 ms →      484.68 ms   (+8.04%) | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.05 ms →        1.34 ms  (+27.28%) |     337   →     278    (-17.51%) |      355.12 ms →      372.86 ms   (+5.00%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        6.89 ms →        7.95 ms  (+15.35%) |      54   →      57     (+5.56%) |      372.16 ms →      453.15 ms  (+21.76%) | 
- │ │ │ │     └ sddk::wf_trans                                          |        4.13 ms →        4.93 ms  (+19.37%) |      89   →      91     (+2.25%) |      367.65 ms →      448.74 ms  (+22.06%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |        2.96 ms →        3.59 ms  (+21.09%) |     124   →     125     (+0.81%) |      367.48 ms →      448.55 ms  (+22.06%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      352.58 ns →      377.52 ns   (+7.07%) |      19   →      23    (+21.05%) |        6.70 μs →        8.68 μs  (+29.62%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       19.32 μs →       20.15 μs   (+4.29%) |      19   →      23    (+21.05%) |      367.04 μs →      463.37 μs  (+26.25%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.51 ms →        1.49 ms   (-1.93%) |      19   →      23    (+21.05%) |       28.77 ms →       34.16 ms  (+18.72%) | 
- │ │ ├ sirius::Density::generate                                       |      572.78 ms →      569.88 ms   (-0.50%) |      19   →      23    (+21.05%) |       10.88 s  →       13.11 s   (+20.44%) | 
- │ │ │ ├ sirius::Density::generate_valence                             |      405.82 ms →      407.36 ms   (+0.38%) |      19   →      23    (+21.05%) |        7.71 s  →        9.37 s   (+21.51%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.25 μs →        9.03 μs   (+9.53%) |      19   →      23    (+21.05%) |      156.69 μs →      207.75 μs  (+32.58%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.70 μs →        8.42 μs   (+9.40%) |      19   →      23    (+21.05%) |      146.32 μs →      193.77 μs  (+32.43%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       40.34 ms →       28.92 ms  (-28.30%) |      19   →      23    (+21.05%) |      766.43 ms →      665.21 ms  (-13.21%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.46 μs →        7.98 μs   (+6.95%) |      19   →      23    (+21.05%) |      141.80 μs →      183.58 μs  (+29.47%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        6.74 ms →        4.36 ms  (-35.23%) |      19   →      23    (+21.05%) |      127.99 ms →      100.35 ms  (-21.60%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       32.53 ms →       23.49 ms  (-27.79%) |      19   →      23    (+21.05%) |      618.14 ms →      540.32 ms  (-12.59%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      640.37 ns →      506.83 ns  (-20.85%) |      19   →      23    (+21.05%) |       12.17 μs →       11.66 μs   (-4.19%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      105.76 ms →      117.08 ms  (+10.71%) |      19   →      23    (+21.05%) |        2.01 s  →        2.69 s   (+34.02%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.86 ms →        2.00 ms   (+7.91%) |      19   →      23    (+21.05%) |       35.28 ms →       46.08 ms  (+30.63%) | 
- │ │ │ │ └ sirius::Density::augment                                    |      220.81 ms →      218.82 ms   (-0.90%) |      19   →      23    (+21.05%) |        4.20 s  →        5.03 s   (+19.96%) | 
- │ │ │ │   └ sirius::Density::generate_rho_aug                         |      220.59 ms →      218.60 ms   (-0.90%) |      19   →      23    (+21.05%) |        4.19 s  →        5.03 s   (+19.96%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      138.04 ms →      135.11 ms   (-2.13%) |      19   →      23    (+21.05%) |        2.62 s  →        3.11 s   (+18.48%) | 
- │ │ │ │ └ sirius::symmetrize_function|fpw                             |      138.04 ms →      135.11 ms   (-2.13%) |      19   →      23    (+21.05%) |        2.62 s  →        3.11 s   (+18.48%) | 
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       52.97 ms →       51.08 ms   (-3.57%) |      19   →      23    (+21.05%) |        1.01 s  →        1.17 s   (+16.73%) | 
- │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       71.80 ms →       70.74 ms   (-1.48%) |      19   →      23    (+21.05%) |        1.36 s  →        1.63 s   (+19.26%) | 
- │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.62 ms →       12.64 ms   (+0.15%) |      19   →      23    (+21.05%) |      239.84 ms →      290.76 ms  (+21.23%) | 
- │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.84 ms →       23.59 ms   (-1.02%) |      19   →      23    (+21.05%) |      452.90 ms →      542.64 ms  (+19.81%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        5.07 ms →        3.82 ms  (-24.62%) |      19   →      23    (+21.05%) |       96.28 ms →       87.85 ms   (-8.75%) | 
- │ │ ├ sirius::Density::mix                                            |      132.10 ms →      139.03 ms   (+5.25%) |      19   →      23    (+21.05%) |        2.51 s  →        3.20 s   (+27.41%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      802.13 μs →      769.17 μs   (-4.11%) |      19   →      23    (+21.05%) |       15.24 ms →       17.69 ms  (+16.08%) | 
- │ │ │ ├ sirius::Periodic_function|inner                               |        4.90 ms →        4.89 ms   (-0.09%) |     229   →     289    (+26.20%) |        1.12 s  →        1.41 s   (+26.09%) | 
- │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.84 ms →        4.81 ms   (-0.52%) |     229   →     289    (+26.20%) |        1.11 s  →        1.39 s   (+25.54%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.84 ms →        4.81 ms   (-0.52%) |     229   →     289    (+26.20%) |        1.11 s  →        1.39 s   (+25.54%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        6.29 ms →        5.79 ms   (-8.08%) |      19   →      23    (+21.05%) |      119.59 ms →      133.07 ms  (+11.28%) | 
! │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.52 ms →        5.00 ms   (-9.39%) |      19   →      23    (+21.05%) |      104.93 ms →      115.10 ms   (+9.69%) | 
- │ │ ├ sirius::Potential::generate                                     |      363.52 ms →      355.84 ms   (-2.11%) |      19   →      23    (+21.05%) |        6.91 s  →        8.18 s   (+18.50%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |       43.17 ms →       35.74 ms  (-17.21%) |      19   →      23    (+21.05%) |      820.27 ms →      822.08 ms   (+0.22%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       11.55 ms →        3.66 ms  (-68.28%) |      19   →      23    (+21.05%) |      219.39 ms →       84.23 ms  (-61.61%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |        5.81 ms →        5.72 ms   (-1.55%) |      19   →      23    (+21.05%) |      110.33 ms →      131.49 ms  (+19.18%) | 
- │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.64 ms →        4.63 ms   (-0.16%) |      19   →      23    (+21.05%) |       88.12 ms →      106.50 ms  (+20.86%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.64 ms →        4.63 ms   (-0.15%) |      19   →      23    (+21.05%) |       88.10 ms →      106.48 ms  (+20.87%) | 
- │ │ │ ├ sirius::Periodic_function::add                                |      792.40 μs →      826.93 μs   (+4.36%) |      38   →      46    (+21.05%) |       30.11 ms →       38.04 ms  (+26.33%) | 
- │ │ │ ├ sirius::Potential::xc                                         |       44.89 ms →       44.54 ms   (-0.79%) |      19   →      23    (+21.05%) |      852.99 ms →        1.02 s   (+20.10%) | 
- │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       43.71 ms →       43.36 ms   (-0.79%) |      19   →      23    (+21.05%) |      830.47 ms →      997.39 ms  (+20.10%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function                          |      684.26 μs →      669.25 μs   (-2.19%) |      38   →      46    (+21.05%) |       26.00 ms →       30.79 ms  (+18.40%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.23 ms →        4.10 ms   (-3.18%) |      19   →      23    (+21.05%) |       80.42 ms →       94.25 ms  (+17.20%) | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.48 ms →        3.82 ms   (+9.90%) |      19   →      23    (+21.05%) |       66.11 ms →       87.96 ms  (+33.04%) | 
- │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.95 ms →      268.71 ms   (-0.09%) |      19   →      23    (+21.05%) |        5.11 s  →        6.18 s   (+20.94%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      316.05 ns →      307.43 ns   (-2.73%) |      19   →      23    (+21.05%) |        6.00 μs →        7.07 μs  (+17.75%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |       97.86 ms →       97.06 ms   (-0.82%) |      19   →      23    (+21.05%) |        1.86 s  →        2.23 s   (+20.06%) | 
- │ │ │ └ sirius::symmetrize_function|fpw                               |       97.86 ms →       97.06 ms   (-0.82%) |      19   →      23    (+21.05%) |        1.86 s  →        2.23 s   (+20.06%) | 
- │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.28 ms →       13.21 ms   (-0.59%) |      19   →      23    (+21.05%) |      252.41 ms →      303.73 ms  (+20.33%) | 
- │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       71.33 ms →       70.64 ms   (-0.97%) |      19   →      23    (+21.05%) |        1.36 s  →        1.62 s   (+19.88%) | 
- │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.62 ms →       12.58 ms   (-0.31%) |      19   →      23    (+21.05%) |      239.77 ms →      289.34 ms  (+20.67%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        4.50 ms →        3.82 ms  (-15.00%) |      19   →      23    (+21.05%) |       85.49 ms →       87.96 ms   (+2.89%) | 
- │ │ ├ sirius::Periodic_function|inner                                 |        4.60 ms →        4.74 ms   (+3.07%) |     133   →     161    (+21.05%) |      611.95 ms →      763.49 ms  (+24.76%) | 
- │ │ │ └ sirius::Periodic_function|inner_local                         |        4.58 ms →        4.56 ms   (-0.43%) |     133   →     161    (+21.05%) |      608.62 ms →      733.58 ms  (+20.53%) | 
- │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.58 ms →        4.56 ms   (-0.43%) |     133   →     161    (+21.05%) |      608.53 ms →      733.49 ms  (+20.53%) | 
- │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.95 ms →        4.95 ms   (-0.03%) |      57   →      69    (+21.05%) |      282.40 ms →      341.74 ms  (+21.02%) | 
- │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.95 ms →        4.93 ms   (-0.36%) |      57   →      69    (+21.05%) |      281.95 ms →      340.06 ms  (+20.61%) | 
- │ │ ├ sirius::Periodic_function::integrate                            |        4.56 ms →        4.53 ms   (-0.60%) |      19   →      23    (+21.05%) |       86.58 ms →      104.17 ms  (+20.33%) | 
- │ │ └ sirius::Density::get_magnetisation                              |       77.65 μs →       76.38 μs   (-1.64%) |      19   →      23    (+21.05%) |        1.48 ms →        1.76 ms  (+19.07%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |       72.78 μs →       71.43 μs   (-1.85%) |      19   →      23    (+21.05%) |        1.38 ms →        1.64 ms  (+18.81%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.58 ms →        5.16 ms   (-7.55%) |       2   →       2              |       11.16 ms →       10.32 ms   (-7.55%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.82 ms →        4.66 ms   (-3.42%) |       6   →       6              |       28.94 ms →       27.95 ms   (-3.42%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.81 ms →        4.63 ms   (-3.79%) |       6   →       6              |       28.88 ms →       27.79 ms   (-3.79%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.81 ms →        4.63 ms   (-3.75%) |       6   →       6              |       28.86 ms →       27.78 ms   (-3.75%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        5.18 ms →        5.08 ms   (-2.02%) |       3   →       3              |       15.55 ms →       15.23 ms   (-2.02%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        5.18 ms →        5.07 ms   (-2.02%) |       3   →       3              |       15.53 ms →       15.22 ms   (-2.02%) | 
  ├ sirius::Periodic_function|inner                                     |        4.77 ms →        4.53 ms   (-4.84%) |       2   →       2              |        9.53 ms →        9.07 ms   (-4.84%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.76 ms →        4.53 ms   (-4.85%) |       2   →       2              |        9.52 ms →        9.06 ms   (-4.85%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.76 ms →        4.53 ms   (-4.85%) |       2   →       2              |        9.52 ms →        9.06 ms   (-4.85%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        5.23 ms →        4.92 ms   (-5.98%) |       1   →       1              |        5.23 ms →        4.92 ms   (-5.98%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        5.22 ms →        4.91 ms   (-6.02%) |       1   →       1              |        5.22 ms →        4.91 ms   (-6.02%) | 
  └ sirius::finalize                                                    |      153.63 ms →      154.24 ms   (+0.40%) |       1   →       1              |      153.63 ms →      154.24 ms   (+0.40%) | 
  ====================================================================================================================================================================================================
```
