# Benchmark 392f68b5626168134a99cd6d4a3cc40b87322cb7 vs f3d65506dd217f3bfa11e8357960357f194d258d
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      128.66 s  →      128.83 s    (+0.13%) |       1   →       1              |      128.66 s  →      128.83 s    (+0.13%) | 
  ├ sirius::initialize                                                  |        2.64 s  →        2.71 s    (+2.52%) |       1   →       1              |        2.64 s  →        2.71 s    (+2.52%) | 
  ├ sirius::Simulation_context::initialize                              |        2.92 s  →        2.91 s    (-0.26%) |       1   →       1              |        2.92 s  →        2.91 s    (-0.26%) | 
  │ ├ sirius::Simulation_context::init_comm                             |      320.82 μs →      327.04 μs   (+1.94%) |       1   →       1              |      320.82 μs →      327.04 μs   (+1.94%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      174.32 ms →      154.85 ms  (-11.17%) |       1   →       1              |      174.32 ms →      154.85 ms  (-11.17%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       76.08 ms →       66.00 ms  (-13.25%) |       2   →       2              |      152.15 ms →      132.00 ms  (-13.25%) | 
  │ │ └ sirius::Unit_cell::update                                       |       22.08 ms →       22.77 ms   (+3.10%) |       1   →       1              |       22.08 ms →       22.77 ms   (+3.10%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.37 ms →        6.44 ms   (+0.98%) |       1   →       1              |        6.37 ms →        6.44 ms   (+0.98%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       15.67 ms →       16.29 ms   (+3.93%) |       1   →       1              |       15.67 ms →       16.29 ms   (+3.93%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       15.65 ms →       16.26 ms   (+3.94%) |       1   →       1              |       15.65 ms →       16.26 ms   (+3.94%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.14 ms →        4.14 ms   (-0.11%) |       1   →       1              |        4.14 ms →        4.14 ms   (-0.11%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.35 ms →        2.35 ms   (+0.15%) |       1   →       1              |        2.35 ms →        2.35 ms   (+0.15%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      111.17 μs →      110.68 μs   (-0.44%) |       1   →       1              |      111.17 μs →      110.68 μs   (-0.44%) | 
  │ └ sirius::Simulation_context::update                                |        2.70 s  →        2.71 s    (+0.49%) |       1   →       1              |        2.70 s  →        2.71 s    (+0.49%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.80 ms →       10.80 ms   (+0.04%) |       1   →       1              |       10.80 ms →       10.80 ms   (+0.04%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.40 ms →        4.41 ms   (+0.36%) |       1   →       1              |        4.40 ms →        4.41 ms   (+0.36%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.37 ms →        6.35 ms   (-0.19%) |       1   →       1              |        6.37 ms →        6.35 ms   (-0.19%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.35 ms →        6.33 ms   (-0.19%) |       1   →       1              |        6.35 ms →        6.33 ms   (-0.19%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.84 ms →        3.83 ms   (-0.22%) |       1   →       1              |        3.84 ms →        3.83 ms   (-0.22%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.33 ms   (-0.13%) |       1   →       1              |        2.33 ms →        2.33 ms   (-0.13%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      107.20 μs →      106.89 μs   (-0.29%) |       1   →       1              |      107.20 μs →      106.89 μs   (-0.29%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       62.62 ms →       62.27 ms   (-0.56%) |       2   →       2              |      125.25 ms →      124.54 ms   (-0.56%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.14 ms →        5.29 ms   (+2.97%) |       2   →       2              |       10.27 ms →       10.58 ms   (+2.97%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.46 ms →        4.47 ms   (+0.09%) |       1   →       1              |        4.46 ms →        4.47 ms   (+0.09%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.78 ms →       21.77 ms   (-0.03%) |       2   →       2              |       43.56 ms →       43.54 ms   (-0.03%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.81 ms →       14.77 ms   (-0.25%) |       2   →       2              |       29.62 ms →       29.55 ms   (-0.25%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.76 ms →       19.78 ms   (+0.10%) |       4   →       4              |       79.02 ms →       79.10 ms   (+0.10%) | 
  │   ├ sddk::Gvec::init                                                |      171.16 ms →      171.09 ms   (-0.04%) |       2   →       2              |      342.32 ms →      342.18 ms   (-0.04%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      128.20 ms →      127.72 ms   (-0.37%) |       2   →       2              |      256.40 ms →      255.45 ms   (-0.37%) | 
  │   ├ sddk::Gvec_shells                                               |      181.56 ms →      178.48 ms   (-1.70%) |       1   →       1              |      181.56 ms →      178.48 ms   (-1.70%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.32 ms →        1.31 ms   (-0.49%) |       1   →       1              |        1.32 ms →        1.31 ms   (-0.49%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      292.00 ms →      296.54 ms   (+1.55%) |       2   →       2              |      584.00 ms →      593.07 ms   (+1.55%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       35.56 ms →       36.25 ms   (+1.95%) |       1   →       1              |       35.56 ms →       36.25 ms   (+1.95%) | 
  │ ├ sirius::K_point::K_point                                          |        2.59 μs →        2.49 μs   (-3.74%) |       4   →       4              |       10.36 μs →        9.97 μs   (-3.74%) | 
  │ └ sirius::K_point_set::initialize                                   |       35.45 ms →       36.13 ms   (+1.94%) |       1   →       1              |       35.45 ms →       36.13 ms   (+1.94%) | 
  │   └ sirius::K_point::initialize                                     |       35.35 ms →       36.04 ms   (+1.94%) |       1   →       1              |       35.35 ms →       36.04 ms   (+1.94%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       18.07 ms →       18.58 ms   (+2.81%) |       1   →       1              |       18.07 ms →       18.58 ms   (+2.81%) | 
  │     │ └ sddk::Gvec::init                                            |        8.14 ms →        8.06 ms   (-1.09%) |       1   →       1              |        8.14 ms →        8.06 ms   (-1.09%) | 
+ │     ├ sddk::matrix_storage::matrix_storage                          |        9.64 μs →        8.36 μs  (-13.27%) |       1   →       1              |        9.64 μs →        8.36 μs  (-13.27%) | 
  │     └ sirius::K_point::update                                       |       12.41 ms →       12.62 ms   (+1.75%) |       1   →       1              |       12.41 ms →       12.62 ms   (+1.75%) | 
  │       └ sirius::Beta_projectors                                     |        6.10 ms →        6.31 ms   (+3.50%) |       1   →       1              |        6.10 ms →        6.31 ms   (+3.50%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.51 ms →        3.69 ms   (+5.08%) |       1   →       1              |        3.51 ms →        3.69 ms   (+5.08%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.31 ms →        5.19 ms   (-2.30%) |       2   →       2              |       10.62 ms →       10.37 ms   (-2.30%) | 
  ├ sirius::Potential                                                   |      159.91 ms →      158.74 ms   (-0.73%) |       1   →       1              |      159.91 ms →      158.74 ms   (-0.73%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.72 ms →        5.74 ms   (+0.35%) |       6   →       6              |       34.29 ms →       34.41 ms   (+0.35%) | 
  │ └ sirius::Potential::update                                         |      124.92 ms →      123.62 ms   (-1.04%) |       1   →       1              |      124.92 ms →      123.62 ms   (-1.04%) | 
  │   └ sirius::Potential::generate_local_potential                     |      124.19 ms →      122.91 ms   (-1.03%) |       1   →       1              |      124.19 ms →      122.91 ms   (-1.03%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      111.04 ms →      111.60 ms   (+0.50%) |       1   →       1              |      111.04 ms →      111.60 ms   (+0.50%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       12.27 ms →       10.42 ms  (-15.07%) |       1   →       1              |       12.27 ms →       10.42 ms  (-15.07%) | 
  ├ sirius::Density                                                     |      135.49 ms →      135.27 ms   (-0.16%) |       1   →       1              |      135.49 ms →      135.27 ms   (-0.16%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.62 ms →        5.09 ms   (-9.38%) |       2   →       2              |       11.23 ms →       10.18 ms   (-9.38%) | 
  │ └ sirius::Density::update                                           |      123.96 ms →      124.83 ms   (+0.70%) |       1   →       1              |      123.96 ms →      124.83 ms   (+0.70%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      123.51 ms →      124.42 ms   (+0.73%) |       1   →       1              |      123.51 ms →      124.42 ms   (+0.73%) | 
+ │     ├ sirius::rho_core_ri_pseudo|values                             |      118.10 μs →      105.71 μs  (-10.49%) |       1   →       1              |      118.10 μs →      105.71 μs  (-10.49%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      111.95 ms →      112.65 ms   (+0.63%) |       1   →       1              |      111.95 ms →      112.65 ms   (+0.63%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |       11.01 ms →       11.22 ms   (+1.95%) |       1   →       1              |       11.01 ms →       11.22 ms   (+1.95%) | 
  ├ sirius::Density::initial_density                                    |      175.75 ms →      175.80 ms   (+0.03%) |       1   →       1              |      175.75 ms →      175.80 ms   (+0.03%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      111.22 ms →      110.83 ms   (-0.35%) |       1   →       1              |      111.22 ms →      110.83 ms   (-0.35%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |       11.39 ms →       11.55 ms   (+1.41%) |       2   →       2              |       22.77 ms →       23.09 ms   (+1.41%) | 
  │ └ sirius::Periodic_function::integrate                              |        9.76 ms →        9.89 ms   (+1.34%) |       1   →       1              |        9.76 ms →        9.89 ms   (+1.34%) | 
  ├ sirius::Potential::generate                                         |      596.93 ms →      605.17 ms   (+1.38%) |       1   →       1              |      596.93 ms →      605.17 ms   (+1.38%) | 
  │ ├ sirius::Potential::poisson                                        |      139.94 ms →      138.49 ms   (-1.04%) |       1   →       1              |      139.94 ms →      138.49 ms   (-1.04%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       18.53 ms →       17.80 ms   (-3.94%) |       1   →       1              |       18.53 ms →       17.80 ms   (-3.94%) | 
+ │ │ └ sirius::Periodic_function|inner                                 |       11.38 ms →       10.02 ms  (-11.97%) |       1   →       1              |       11.38 ms →       10.02 ms  (-11.97%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |       10.34 ms →        9.91 ms   (-4.13%) |       1   →       1              |       10.34 ms →        9.91 ms   (-4.13%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |       10.33 ms →        9.90 ms   (-4.14%) |       1   →       1              |       10.33 ms →        9.90 ms   (-4.14%) | 
  │ ├ sirius::Periodic_function::add                                    |      539.66 μs →      550.12 μs   (+1.94%) |       2   →       2              |        1.08 ms →        1.10 ms   (+1.94%) | 
  │ ├ sirius::Potential::xc                                             |       56.11 ms →       53.65 ms   (-4.38%) |       1   →       1              |       56.11 ms →       53.65 ms   (-4.38%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       53.84 ms →       51.39 ms   (-4.55%) |       1   →       1              |       53.84 ms →       51.39 ms   (-4.55%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.66 ms →        5.64 ms   (-0.36%) |       2   →       2              |       11.32 ms →       11.28 ms   (-0.36%) | 
+ │ │   └ sirius::Smooth_periodic_function::fft_transform               |        6.08 ms →        5.34 ms  (-12.22%) |       1   →       1              |        6.08 ms →        5.34 ms  (-12.22%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.64 ms →        5.81 ms   (+3.02%) |       1   →       1              |        5.64 ms →        5.81 ms   (+3.02%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       93.63 ms →       93.52 ms   (-0.11%) |       1   →       1              |       93.63 ms →       93.52 ms   (-0.11%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      299.21 ms →      311.24 ms   (+4.02%) |       1   →       1              |      299.21 ms →      311.24 ms   (+4.02%) | 
  ├ sirius::Hamiltonian0                                                |        8.41 ms →        8.43 ms   (+0.19%) |       1   →       1              |        8.41 ms →        8.43 ms   (+0.19%) | 
  │ ├ sirius::Local_operator                                            |        8.06 ms →        8.08 ms   (+0.28%) |       1   →       1              |        8.06 ms →        8.08 ms   (+0.28%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.71 ms →        4.72 ms   (+0.23%) |       1   →       1              |        4.71 ms →        4.72 ms   (+0.23%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.43 ms →        2.45 ms   (+0.97%) |       1   →       1              |        2.43 ms →        2.45 ms   (+0.97%) | 
  │ ├ sirius::Non_local_operator                                        |       62.56 μs →       62.53 μs   (-0.06%) |       2   →       2              |      125.13 μs →      125.05 μs   (-0.06%) | 
  │ ├ sirius::D_operator::initialize                                    |      101.39 μs →       96.12 μs   (-5.20%) |       1   →       1              |      101.39 μs →       96.12 μs   (-5.20%) | 
  │ └ sirius::Q_operator::initialize                                    |       73.11 μs →       73.28 μs   (+0.24%) |       1   →       1              |       73.11 μs →       73.28 μs   (+0.24%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.85 s  →        1.85 s    (-0.07%) |       1   →       1              |        1.85 s  →        1.85 s    (-0.07%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.62 ms →       18.62 ms   (+0.04%) |       1   →       1              |       18.62 ms →       18.62 ms   (+0.04%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      183.78 μs →      175.75 μs   (-4.37%) |       1   →       1              |      183.78 μs →      175.75 μs   (-4.37%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       18.43 ms →       18.45 ms   (+0.08%) |       1   →       1              |       18.43 ms →       18.45 ms   (+0.08%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.83 s  →        1.83 s    (-0.07%) |       1   →       1              |        1.83 s  →        1.83 s    (-0.07%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      127.17 ms →      127.44 ms   (+0.22%) |       4   →       4              |      508.66 ms →      509.78 ms   (+0.22%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       51.73 ms →       51.96 ms   (+0.45%) |       1   →       1              |       51.73 ms →       51.96 ms   (+0.45%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.07 ms →       21.12 ms   (+0.23%) |       1   →       1              |       21.07 ms →       21.12 ms   (+0.23%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      637.98 ms →      637.75 ms   (-0.04%) |       1   →       1              |      637.98 ms →      637.75 ms   (-0.04%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      297.35 ms →      297.24 ms   (-0.04%) |       1   →       1              |      297.35 ms →      297.24 ms   (-0.04%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.53 μs →        3.60 μs   (+1.81%) |       1   →       1              |        3.53 μs →        3.60 μs   (+1.81%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.23 μs →        2.45 μs  (+10.11%) |       1   →       1              |        2.23 μs →        2.45 μs  (+10.11%) | 
- │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      364.00 ns →      435.00 ns  (+19.51%) |       1   →       1              |      364.00 ns →      435.00 ns  (+19.51%) | 
- │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      455.00 ns →      906.00 ns  (+99.12%) |       1   →       1              |      455.00 ns →      906.00 ns  (+99.12%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.23 ms →        9.23 ms   (+0.08%) |       1   →       1              |        9.23 ms →        9.23 ms   (+0.08%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      122.28 ms →      121.87 ms   (-0.34%) |       1   →       1              |      122.28 ms →      121.87 ms   (-0.34%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      104.55 ms →      104.69 ms   (+0.14%) |       2   →       2              |      209.09 ms →      209.38 ms   (+0.14%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       40.26 ms →       40.28 ms   (+0.04%) |       2   →       2              |       80.53 ms →       80.56 ms   (+0.04%) | 
  │ │ │ └ sddk::wf_inner                                                |       39.73 ms →       39.74 ms   (+0.03%) |       2   →       2              |       79.46 ms →       79.48 ms   (+0.03%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       27.00 ns →       39.00 ns  (+44.44%) |       2   →       2              |       54.00 ns →       78.00 ns  (+44.44%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       39.25 ms →       39.28 ms   (+0.06%) |       2   →       2              |       78.51 ms →       78.55 ms   (+0.06%) | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |       22.50 ns →       24.50 ns   (+8.89%) |       2   →       2              |       45.00 ns →       49.00 ns   (+8.89%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       55.37 ms →       56.26 ms   (+1.60%) |       1   →       1              |       55.37 ms →       56.26 ms   (+1.60%) | 
  │ │ └ sddk::wf_trans                                                  |       30.77 ms →       30.77 ms   (+0.01%) |       1   →       1              |       30.77 ms →       30.77 ms   (+0.01%) | 
  │ │   └ sddk::wf_trans|pw                                             |       30.77 ms →       30.77 ms   (+0.00%) |       1   →       1              |       30.77 ms →       30.77 ms   (+0.00%) | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      316.00 ns →      413.00 ns  (+30.70%) |       1   →       1              |      316.00 ns →      413.00 ns  (+30.70%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      119.15 s  →      119.25 s    (+0.09%) |       1   →       1              |      119.15 s  →      119.25 s    (+0.09%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.73 ms →        5.74 ms   (+0.13%) |      19   →      19              |      108.93 ms →      109.07 ms   (+0.13%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.57 s  →        4.57 s    (+0.09%) |      26   →      26              |      118.76 s  →      118.87 s    (+0.09%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        5.12 ms →        5.10 ms   (-0.35%) |      26   →      26              |      133.10 ms →      132.64 ms   (-0.35%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.76 ms →        4.74 ms   (-0.27%) |      26   →      26              |      123.68 ms →      123.35 ms   (-0.27%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      963.18 μs →      927.39 μs   (-3.72%) |      26   →      26              |       25.04 ms →       24.11 ms   (-3.72%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.90 ms →        2.93 ms   (+1.10%) |      26   →      26              |       75.45 ms →       76.28 ms   (+1.10%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.22 μs →       64.35 μs   (+0.19%) |      52   →      52              |        3.34 ms →        3.35 ms   (+0.19%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       86.25 μs →       85.23 μs   (-1.18%) |      26   →      26              |        2.24 ms →        2.22 ms   (-1.18%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       76.52 μs →       75.28 μs   (-1.62%) |      26   →      26              |        1.99 ms →        1.96 ms   (-1.62%) | 
  │ │ ├ sirius::Band::solve                                             |        2.60 s  →        2.60 s    (-0.16%) |      26   →      26              |       67.71 s  →       67.60 s    (-0.16%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      153.93 μs →      153.51 μs   (-0.28%) |      26   →      26              |        4.00 ms →        3.99 ms   (-0.28%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      146.98 μs →      146.79 μs   (-0.13%) |      26   →      26              |        3.82 ms →        3.82 ms   (-0.13%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.34 μs →        5.14 μs   (-3.91%) |      26   →      26              |      138.97 μs →      133.54 μs   (-3.91%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.47 s  →        2.47 s    (-0.34%) |      26   →      26              |       64.33 s  →       64.12 s    (-0.34%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       95.01 ms →       93.84 ms   (-1.23%) |      26   →      26              |        2.47 s  →        2.44 s    (-1.23%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.64 ms →        7.62 ms   (-0.29%) |     156   →     156              |        1.19 s  →        1.19 s    (-0.29%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        6.19 ms →        5.95 ms   (-3.92%) |      26   →      26              |      160.93 ms →      154.63 ms   (-3.92%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      349.85 μs →      348.14 μs   (-0.49%) |      26   →      26              |        9.10 ms →        9.05 ms   (-0.49%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.39 ms →        2.29 ms   (-4.24%) |      52   →      52              |      124.44 ms →      119.17 ms   (-4.24%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.34 s  →        2.33 s    (-0.29%) |      26   →      26              |       60.77 s  →       60.59 s    (-0.29%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      137.44 ms →      137.26 ms   (-0.13%) |     262   →     262              |       36.01 s  →       35.96 s    (-0.13%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       55.55 ms →       55.32 ms   (-0.41%) |     262   →     262              |       14.55 s  →       14.50 s    (-0.41%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.18 μs →        1.89 μs  (-13.10%) |     262   →     262              |      570.30 μs →      495.58 μs  (-13.10%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.85 μs →        1.55 μs  (-15.82%) |     262   →     262              |      483.41 μs →      406.95 μs  (-15.82%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      389.40 ns →      427.00 ns   (+9.66%) |     262   →     262              |      102.02 μs →      111.87 μs   (+9.66%) | 
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      505.28 ns →      413.73 ns  (-18.12%) |     262   →     262              |      132.38 μs →      108.40 μs  (-18.12%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.45 ms →        7.45 ms   (+0.01%) |     262   →     262              |        1.95 s  →        1.95 s    (+0.01%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       25.36 ms →       25.41 ms   (+0.20%) |     262   →     262              |        6.64 s  →        6.66 s    (+0.20%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       24.53 ms →       24.53 ms   (-0.00%) |     524   →     524              |       12.85 s  →       12.85 s    (-0.00%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       35.93 ms →       35.90 ms   (-0.08%) |     262   →     262              |        9.41 s  →        9.41 s    (-0.08%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        6.23 ms →        6.23 ms   (-0.07%) |     498   →     498              |        3.10 s  →        3.10 s    (-0.07%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       66.68 ns →       64.83 ns   (-2.77%) |     498   →     498              |       33.21 μs →       32.29 μs   (-2.77%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        5.12 ms →        5.12 ms   (-0.08%) |     498   →     498              |        2.55 s  →        2.55 s    (-0.08%) | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       32.05 ns →       31.03 ns   (-3.17%) |     498   →     498              |       15.96 μs →       15.45 μs   (-3.17%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      671.36 μs →      658.13 μs   (-1.97%) |     262   →     262              |      175.90 ms →      172.43 ms   (-1.97%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       10.32 ms →       10.31 ms   (-0.05%) |     262   →     262              |        2.70 s  →        2.70 s    (-0.05%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |       14.53 ms →       14.52 ms   (-0.02%) |     236   →     236              |        3.43 s  →        3.43 s    (-0.02%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        4.84 ms →        4.84 ms   (-0.02%) |     708   →     708              |        3.43 s  →        3.43 s    (-0.02%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       10.40 ms →       10.38 ms   (-0.21%) |     262   →     262              |        2.73 s  →        2.72 s    (-0.21%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |       10.20 ms →       10.18 ms   (-0.19%) |     262   →     262              |        2.67 s  →        2.67 s    (-0.19%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       47.33 ns →       36.42 ns  (-23.05%) |     262   →     262              |       12.40 μs →        9.54 μs  (-23.05%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        9.08 ms →        9.07 ms   (-0.21%) |     262   →     262              |        2.38 s  →        2.38 s    (-0.21%) | 
+ │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       56.03 ns →       48.44 ns  (-13.54%) |     262   →     262              |       14.68 μs →       12.69 μs  (-13.54%) | 
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       18.00 ms →       17.62 ms   (-2.10%) |     262   →     262              |        4.72 s  →        4.62 s    (-2.10%) | 
  │ │ │ │   ├ sirius::residuals                                         |       13.16 ms →       13.14 ms   (-0.16%) |     252   →     252              |        3.32 s  →        3.31 s    (-0.16%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       11.72 ms →       11.71 ms   (-0.08%) |     242   →     242              |        2.84 s  →        2.83 s    (-0.08%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        5.86 ms →        5.85 ms   (-0.08%) |     484   →     484              |        2.84 s  →        2.83 s    (-0.08%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.73 ms →        1.71 ms   (-0.91%) |     242   →     242              |      418.58 ms →      414.79 ms   (-0.91%) | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       53.93 ms →       53.78 ms   (-0.27%) |      85   →      85              |        4.58 s  →        4.57 s    (-0.27%) | 
  │ │ │ │     └ sddk::wf_trans                                          |       31.56 ms →       31.49 ms   (-0.23%) |     144   →     144              |        4.55 s  →        4.53 s    (-0.23%) | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |       22.39 ms →       22.34 ms   (-0.23%) |     203   →     203              |        4.54 s  →        4.53 s    (-0.23%) | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      450.96 ns →      408.46 ns   (-9.42%) |      26   →      26              |       11.73 μs →       10.62 μs   (-9.42%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       29.87 μs →       30.99 μs   (+3.78%) |      26   →      26              |      776.53 μs →      805.87 μs   (+3.78%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      620.23 μs →      611.68 μs   (-1.38%) |      26   →      26              |       16.13 ms →       15.90 ms   (-1.38%) | 
  │ │ ├ sirius::Density::generate                                       |      764.88 ms →      771.45 ms   (+0.86%) |      26   →      26              |       19.89 s  →       20.06 s    (+0.86%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      402.21 ms →      402.02 ms   (-0.05%) |      26   →      26              |       10.46 s  →       10.45 s    (-0.05%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.58 μs →        3.80 μs   (+6.10%) |      26   →      26              |       93.06 μs →       98.74 μs   (+6.10%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.24 μs →        3.48 μs   (+7.44%) |      26   →      26              |       84.27 μs →       90.54 μs   (+7.44%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |      100.64 ms →      100.55 ms   (-0.08%) |      26   →      26              |        2.62 s  →        2.61 s    (-0.08%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       10.51 μs →       10.60 μs   (+0.90%) |      26   →      26              |      273.24 μs →      275.70 μs   (+0.90%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.13 ms →        7.13 ms   (+0.01%) |      26   →      26              |      185.30 ms →      185.32 ms   (+0.01%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       91.56 ms →       91.53 ms   (-0.03%) |      26   →      26              |        2.38 s  →        2.38 s    (-0.03%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      642.96 ns →      542.31 ns  (-15.65%) |      26   →      26              |       16.72 μs →       14.10 μs  (-15.65%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      163.02 ms →      161.32 ms   (-1.04%) |      26   →      26              |        4.24 s  →        4.19 s    (-1.04%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.68 ms →        1.63 ms   (-2.81%) |      26   →      26              |       43.70 ms →       42.47 ms   (-2.81%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.27 ms →       88.28 ms   (+0.00%) |      26   →      26              |        2.30 s  →        2.30 s    (+0.00%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.05 ms →       88.05 ms   (+0.01%) |      26   →      26              |        2.29 s  →        2.29 s    (+0.01%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      270.50 ms →      278.22 ms   (+2.85%) |      26   →      26              |        7.03 s  →        7.23 s    (+2.85%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      270.50 ms →      278.22 ms   (+2.85%) |      26   →      26              |        7.03 s  →        7.23 s    (+2.85%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.43 ms →       24.08 ms   (-1.45%) |      26   →      26              |      635.20 ms →      626.00 ms   (-1.45%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      221.48 ms →      230.11 ms   (+3.90%) |      26   →      26              |        5.76 s  →        5.98 s    (+3.90%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       23.40 ms →       22.87 ms   (-2.29%) |      26   →      26              |      608.48 ms →      594.52 ms   (-2.29%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       81.17 ms →       80.96 ms   (-0.26%) |      26   →      26              |        2.11 s  →        2.10 s    (-0.26%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        7.41 ms →        6.66 ms  (-10.08%) |      26   →      26              |      192.62 ms →      173.21 ms  (-10.08%) | 
  │ │ ├ sirius::Density::mix                                            |      218.73 ms →      212.34 ms   (-2.92%) |      26   →      26              |        5.69 s  →        5.52 s    (-2.92%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      948.75 μs →      944.08 μs   (-0.49%) |      26   →      26              |       24.67 ms →       24.55 ms   (-0.49%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.69 ms →       10.24 ms   (-4.16%) |     334   →     334              |        3.57 s  →        3.42 s    (-4.16%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.36 ms →        9.99 ms   (-3.56%) |     334   →     334              |        3.46 s  →        3.34 s    (-3.56%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.36 ms →        9.99 ms   (-3.56%) |     334   →     334              |        3.46 s  →        3.34 s    (-3.56%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        6.08 ms →        5.94 ms   (-2.31%) |      26   →      26              |      158.13 ms →      154.48 ms   (-2.31%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.26 ms →        5.11 ms   (-2.89%) |      26   →      26              |      136.88 ms →      132.92 ms   (-2.89%) | 
  │ │ ├ sirius::Potential::generate                                     |      581.43 ms →      579.24 ms   (-0.38%) |      26   →      26              |       15.12 s  →       15.06 s    (-0.38%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      139.10 ms →      138.80 ms   (-0.22%) |      26   →      26              |        3.62 s  →        3.61 s    (-0.22%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       18.29 ms →       17.81 ms   (-2.61%) |      26   →      26              |      475.56 ms →      463.13 ms   (-2.61%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.70 ms →       10.40 ms   (-2.76%) |      26   →      26              |      278.17 ms →      270.48 ms   (-2.76%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.29 ms →       10.00 ms   (-2.74%) |      26   →      26              |      267.44 ms →      260.12 ms   (-2.74%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.29 ms →       10.00 ms   (-2.74%) |      26   →      26              |      267.43 ms →      260.11 ms   (-2.74%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      548.06 μs →      547.41 μs   (-0.12%) |      52   →      52              |       28.50 ms →       28.47 ms   (-0.12%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       49.80 ms →       48.65 ms   (-2.32%) |      26   →      26              |        1.29 s  →        1.26 s    (-2.32%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       47.47 ms →       46.35 ms   (-2.36%) |      26   →      26              |        1.23 s  →        1.21 s    (-2.36%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.04 ms →        2.95 ms   (-3.01%) |      52   →      52              |      158.26 ms →      153.50 ms   (-3.01%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.43 ms →        5.35 ms   (-1.39%) |      26   →      26              |      141.11 ms →      139.15 ms   (-1.39%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.54 ms →        6.42 ms   (-1.92%) |      26   →      26              |      170.10 ms →      166.84 ms   (-1.92%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.95 ms →       90.91 ms   (-0.04%) |      26   →      26              |        2.36 s  →        2.36 s    (-0.04%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      292.66 ms →      292.13 ms   (-0.18%) |      26   →      26              |        7.61 s  →        7.60 s    (-0.18%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      273.74 ms →      282.77 ms   (+3.30%) |      26   →      26              |        7.12 s  →        7.35 s    (+3.30%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      273.74 ms →      282.77 ms   (+3.30%) |      26   →      26              |        7.12 s  →        7.35 s    (+3.30%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.07 ms →       27.06 ms   (-0.05%) |      26   →      26              |      703.94 ms →      703.58 ms   (-0.05%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      219.17 ms →      228.21 ms   (+4.13%) |      26   →      26              |        5.70 s  →        5.93 s    (+4.13%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.67 ms →       23.73 ms   (+0.24%) |      26   →      26              |      615.49 ms →      616.99 ms   (+0.24%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.60 ms →        5.33 ms   (-4.91%) |      26   →      26              |      145.64 ms →      138.48 ms   (-4.91%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.22 ms →       10.62 ms   (+3.97%) |     182   →     182              |        1.86 s  →        1.93 s    (+3.97%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.80 ms →       10.27 ms   (+4.79%) |     182   →     182              |        1.78 s  →        1.87 s    (+4.79%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.80 ms →       10.27 ms   (+4.79%) |     182   →     182              |        1.78 s  →        1.87 s    (+4.79%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.57 ms →       10.17 ms   (-3.77%) |      78   →      78              |      824.27 ms →      793.20 ms   (-3.77%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.19 ms →        9.82 ms   (-3.59%) |      78   →      78              |      794.69 ms →      766.19 ms   (-3.59%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        9.95 ms →        9.98 ms   (+0.30%) |      26   →      26              |      258.66 ms →      259.42 ms   (+0.30%) | 
+ │ │ └ sirius::Density::get_magnetisation                              |      220.69 μs →      109.22 μs  (-50.51%) |      26   →      26              |        5.74 ms →        2.84 ms  (-50.51%) | 
+ │ │   └ sirius::Density::compute_atomic_mag_mom                       |      215.58 μs →      104.02 μs  (-51.75%) |      26   →      26              |        5.61 ms →        2.70 ms  (-51.75%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.39 ms →        5.31 ms   (-1.43%) |       2   →       2              |       10.78 ms →       10.62 ms   (-1.43%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.05 ms →       10.17 ms   (+1.21%) |       6   →       6              |       60.29 ms →       61.02 ms   (+1.21%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.04 ms →       10.14 ms   (+1.06%) |       6   →       6              |       60.22 ms →       60.86 ms   (+1.06%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.04 ms →       10.14 ms   (+1.06%) |       6   →       6              |       60.22 ms →       60.85 ms   (+1.06%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.38 ms →        9.69 ms   (-6.67%) |       3   →       3              |       31.14 ms →       29.07 ms   (-6.67%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.37 ms →        9.65 ms   (-6.92%) |       3   →       3              |       31.12 ms →       28.96 ms   (-6.92%) | 
  ├ sirius::Periodic_function|inner                                     |       10.00 ms →       10.44 ms   (+4.38%) |       2   →       2              |       20.01 ms →       20.89 ms   (+4.38%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.00 ms →       10.44 ms   (+4.40%) |       2   →       2              |       19.99 ms →       20.87 ms   (+4.40%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.00 ms →       10.44 ms   (+4.40%) |       2   →       2              |       19.99 ms →       20.87 ms   (+4.40%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.43 ms →       10.03 ms   (-3.83%) |       1   →       1              |       10.43 ms →       10.03 ms   (-3.83%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.43 ms →       10.03 ms   (-3.84%) |       1   →       1              |       10.43 ms →       10.03 ms   (-3.84%) | 
  └ sirius::finalize                                                    |      186.39 ms →      184.59 ms   (-0.97%) |       1   →       1              |      186.39 ms →      184.59 ms   (-0.97%) | 
  ====================================================================================================================================================================================================
```
