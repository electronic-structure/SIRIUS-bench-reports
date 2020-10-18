# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      132.78 s  →      128.86 s    (-2.95%) |       1   →       1              |      132.78 s  →      128.86 s    (-2.95%) | 
  ├ sirius::initialize                                                  |        2.75 s  →        2.74 s    (-0.23%) |       1   →       1              |        2.75 s  →        2.74 s    (-0.23%) | 
  ├ sirius::Simulation_context::initialize                              |        2.92 s  →        3.03 s    (+3.75%) |       1   →       1              |        2.92 s  →        3.03 s    (+3.75%) | 
- │ ├ sirius::Simulation_context::init_comm                             |      200.48 μs →       48.63 ms (+24155.75%) |       1   →       1              |      200.48 μs →       48.63 ms (+24155.75%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      166.80 ms →      203.37 ms  (+21.93%) |       1   →       1              |      166.80 ms →      203.37 ms  (+21.93%) | 
- │ │ ├ sirius::Atom_type::init                                         |       71.16 ms →       89.64 ms  (+25.96%) |       2   →       2              |      142.33 ms →      179.27 ms  (+25.96%) | 
  │ │ └ sirius::Unit_cell::update                                       |       24.39 ms →       24.01 ms   (-1.55%) |       1   →       1              |       24.39 ms →       24.01 ms   (-1.55%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.42 ms →        6.64 ms   (+3.44%) |       1   →       1              |        6.42 ms →        6.64 ms   (+3.44%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       17.93 ms →       17.32 ms   (-3.40%) |       1   →       1              |       17.93 ms →       17.32 ms   (-3.40%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       17.91 ms →       17.30 ms   (-3.41%) |       1   →       1              |       17.91 ms →       17.30 ms   (-3.41%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.16 ms →        4.15 ms   (-0.24%) |       1   →       1              |        4.16 ms →        4.15 ms   (-0.24%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.35 ms   (+0.79%) |       1   →       1              |        2.33 ms →        2.35 ms   (+0.79%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      100.93 μs →      101.70 μs   (+0.77%) |       1   →       1              |      100.93 μs →      101.70 μs   (+0.77%) | 
  │ └ sirius::Simulation_context::update                                |        2.71 s  →        2.73 s    (+0.87%) |       1   →       1              |        2.71 s  →        2.73 s    (+0.87%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.85 ms →       10.84 ms   (-0.10%) |       1   →       1              |       10.85 ms →       10.84 ms   (-0.10%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.38 ms →        4.45 ms   (+1.74%) |       1   →       1              |        4.38 ms →        4.45 ms   (+1.74%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.44 ms →        6.35 ms   (-1.40%) |       1   →       1              |        6.44 ms →        6.35 ms   (-1.40%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.42 ms →        6.33 ms   (-1.41%) |       1   →       1              |        6.42 ms →        6.33 ms   (-1.41%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.93 ms →        3.84 ms   (-2.41%) |       1   →       1              |        3.93 ms →        3.84 ms   (-2.41%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.32 ms   (+0.23%) |       1   →       1              |        2.32 ms →        2.32 ms   (+0.23%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      100.70 μs →       99.62 μs   (-1.08%) |       1   →       1              |      100.70 μs →       99.62 μs   (-1.08%) | 
- │   ├ sirius::Radial_integrals|aug                                    |       62.68 ms →       80.42 ms  (+28.30%) |       2   →       2              |      125.36 ms →      160.84 ms  (+28.30%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.16 ms →        5.13 ms   (-0.48%) |       2   →       2              |       10.32 ms →       10.27 ms   (-0.48%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.48 ms →        4.48 ms   (-0.14%) |       1   →       1              |        4.48 ms →        4.48 ms   (-0.14%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.93 ms →       21.76 ms   (-0.77%) |       2   →       2              |       43.86 ms →       43.52 ms   (-0.77%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.84 ms →       14.86 ms   (+0.14%) |       2   →       2              |       29.67 ms →       29.72 ms   (+0.14%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.74 ms →       19.69 ms   (-0.25%) |       4   →       4              |       78.96 ms →       78.77 ms   (-0.25%) | 
  │   ├ sddk::Gvec::init                                                |      172.93 ms →      171.77 ms   (-0.67%) |       2   →       2              |      345.86 ms →      343.54 ms   (-0.67%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      130.93 ms →      129.13 ms   (-1.37%) |       2   →       2              |      261.86 ms →      258.26 ms   (-1.37%) | 
  │   ├ sddk::Gvec_shells                                               |      162.51 ms →      176.35 ms   (+8.51%) |       1   →       1              |      162.51 ms →      176.35 ms   (+8.51%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.33 ms →        1.32 ms   (-0.60%) |       1   →       1              |        1.33 ms →        1.32 ms   (-0.60%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      291.49 ms →      297.65 ms   (+2.11%) |       2   →       2              |      582.99 ms →      595.31 ms   (+2.11%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       36.00 ms →       36.01 ms   (+0.04%) |       1   →       1              |       36.00 ms →       36.01 ms   (+0.04%) | 
- │ ├ sirius::K_point::K_point                                          |        2.25 μs →        2.56 μs  (+13.63%) |       4   →       4              |        9.02 μs →       10.24 μs  (+13.63%) | 
  │ └ sirius::K_point_set::initialize                                   |       35.90 ms →       35.90 ms   (+0.00%) |       1   →       1              |       35.90 ms →       35.90 ms   (+0.00%) | 
  │   └ sirius::K_point::initialize                                     |       35.81 ms →       35.80 ms   (-0.02%) |       1   →       1              |       35.81 ms →       35.80 ms   (-0.02%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       18.00 ms →       18.13 ms   (+0.68%) |       1   →       1              |       18.00 ms →       18.13 ms   (+0.68%) | 
  │     │ └ sddk::Gvec::init                                            |        8.06 ms →        8.13 ms   (+0.88%) |       1   →       1              |        8.06 ms →        8.13 ms   (+0.88%) | 
+ │     ├ sddk::matrix_storage::matrix_storage                          |       11.17 μs →        9.98 μs  (-10.62%) |       1   →       1              |       11.17 μs →        9.98 μs  (-10.62%) | 
  │     └ sirius::K_point::update                                       |       12.76 ms →       12.64 ms   (-1.01%) |       1   →       1              |       12.76 ms →       12.64 ms   (-1.01%) | 
  │       └ sirius::Beta_projectors                                     |        6.31 ms →        6.32 ms   (+0.17%) |       1   →       1              |        6.31 ms →        6.32 ms   (+0.17%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.73 ms →        3.72 ms   (-0.26%) |       1   →       1              |        3.73 ms →        3.72 ms   (-0.26%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.22 ms →        5.54 ms   (+6.08%) |       2   →       2              |       10.44 ms →       11.07 ms   (+6.08%) | 
  ├ sirius::Potential                                                   |      153.06 ms →      158.53 ms   (+3.58%) |       1   →       1              |      153.06 ms →      158.53 ms   (+3.58%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.91 ms →        5.93 ms   (+0.43%) |       6   →       6              |       35.44 ms →       35.59 ms   (+0.43%) | 
  │ └ sirius::Potential::update                                         |      116.86 ms →      122.21 ms   (+4.58%) |       1   →       1              |      116.86 ms →      122.21 ms   (+4.58%) | 
  │   └ sirius::Potential::generate_local_potential                     |      116.12 ms →      121.41 ms   (+4.55%) |       1   →       1              |      116.12 ms →      121.41 ms   (+4.55%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      108.93 ms →      110.21 ms   (+1.18%) |       1   →       1              |      108.93 ms →      110.21 ms   (+1.18%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        6.30 ms →       10.30 ms  (+63.46%) |       1   →       1              |        6.30 ms →       10.30 ms  (+63.46%) | 
  ├ sirius::Density                                                     |      128.77 ms →      135.21 ms   (+5.00%) |       1   →       1              |      128.77 ms →      135.21 ms   (+5.00%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.21 ms →        5.25 ms   (+0.77%) |       2   →       2              |       10.42 ms →       10.50 ms   (+0.77%) | 
  │ └ sirius::Density::update                                           |      118.07 ms →      124.44 ms   (+5.39%) |       1   →       1              |      118.07 ms →      124.44 ms   (+5.39%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      117.64 ms →      124.00 ms   (+5.41%) |       1   →       1              |      117.64 ms →      124.00 ms   (+5.41%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |      102.84 μs →      103.46 μs   (+0.60%) |       1   →       1              |      102.84 μs →      103.46 μs   (+0.60%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      111.95 ms →      111.71 ms   (-0.22%) |       1   →       1              |      111.95 ms →      111.71 ms   (-0.22%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        5.12 ms →       11.74 ms (+129.35%) |       1   →       1              |        5.12 ms →       11.74 ms (+129.35%) | 
  ├ sirius::Density::initial_density                                    |      167.48 ms →      174.77 ms   (+4.35%) |       1   →       1              |      167.48 ms →      174.77 ms   (+4.35%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      111.14 ms →      110.13 ms   (-0.90%) |       1   →       1              |      111.14 ms →      110.13 ms   (-0.90%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.96 ms →       11.17 ms (+125.16%) |       2   →       2              |        9.93 ms →       22.35 ms (+125.16%) | 
  │ └ sirius::Periodic_function::integrate                              |       10.86 ms →        9.80 ms   (-9.74%) |       1   →       1              |       10.86 ms →        9.80 ms   (-9.74%) | 
  ├ sirius::Potential::generate                                         |      581.23 ms →      592.34 ms   (+1.91%) |       1   →       1              |      581.23 ms →      592.34 ms   (+1.91%) | 
  │ ├ sirius::Potential::poisson                                        |      126.17 ms →      136.61 ms   (+8.27%) |       1   →       1              |      126.17 ms →      136.61 ms   (+8.27%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.23 ms →       16.95 ms (+224.05%) |       1   →       1              |        5.23 ms →       16.95 ms (+224.05%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.20 ms →        9.99 ms   (-2.08%) |       1   →       1              |       10.20 ms →        9.99 ms   (-2.08%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        9.82 ms →        9.89 ms   (+0.75%) |       1   →       1              |        9.82 ms →        9.89 ms   (+0.75%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.81 ms →        9.88 ms   (+0.76%) |       1   →       1              |        9.81 ms →        9.88 ms   (+0.76%) | 
  │ ├ sirius::Periodic_function::add                                    |      551.10 μs →      552.92 μs   (+0.33%) |       2   →       2              |        1.10 ms →        1.11 ms   (+0.33%) | 
  │ ├ sirius::Potential::xc                                             |       54.27 ms →       53.78 ms   (-0.91%) |       1   →       1              |       54.27 ms →       53.78 ms   (-0.91%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.86 ms →       51.39 ms   (-0.91%) |       1   →       1              |       51.86 ms →       51.39 ms   (-0.91%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.78 ms →        5.72 ms   (-1.08%) |       2   →       2              |       11.57 ms →       11.44 ms   (-1.08%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.20 ms →        5.29 ms   (+1.79%) |       1   →       1              |        5.20 ms →        5.29 ms   (+1.79%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.83 ms →        5.73 ms   (-1.59%) |       1   →       1              |        5.83 ms →        5.73 ms   (-1.59%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.69 ms →       92.77 ms   (+0.08%) |       1   →       1              |       92.69 ms →       92.77 ms   (+0.08%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      299.72 ms →      300.98 ms   (+0.42%) |       1   →       1              |      299.72 ms →      300.98 ms   (+0.42%) | 
  ├ sirius::Hamiltonian0                                                |        8.51 ms →        8.44 ms   (-0.78%) |       1   →       1              |        8.51 ms →        8.44 ms   (-0.78%) | 
  │ ├ sirius::Local_operator                                            |        8.16 ms →        8.09 ms   (-0.88%) |       1   →       1              |        8.16 ms →        8.09 ms   (-0.88%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.86 ms →        4.80 ms   (-1.23%) |       1   →       1              |        4.86 ms →        4.80 ms   (-1.23%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.38 ms →        2.37 ms   (-0.51%) |       1   →       1              |        2.38 ms →        2.37 ms   (-0.51%) | 
  │ ├ sirius::Non_local_operator                                        |       63.50 μs →       62.68 μs   (-1.30%) |       2   →       2              |      127.00 μs →      125.35 μs   (-1.30%) | 
  │ ├ sirius::D_operator::initialize                                    |       89.40 μs →       94.89 μs   (+6.15%) |       1   →       1              |       89.40 μs →       94.89 μs   (+6.15%) | 
  │ └ sirius::Q_operator::initialize                                    |       76.83 μs →       75.85 μs   (-1.28%) |       1   →       1              |       76.83 μs →       75.85 μs   (-1.28%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.87 s  →        1.87 s    (+0.04%) |       1   →       1              |        1.87 s  →        1.87 s    (+0.04%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.67 ms →       18.68 ms   (+0.06%) |       1   →       1              |       18.67 ms →       18.68 ms   (+0.06%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      167.12 μs →      175.33 μs   (+4.91%) |       1   →       1              |      167.12 μs →      175.33 μs   (+4.91%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       18.50 ms →       18.50 ms   (+0.02%) |       1   →       1              |       18.50 ms →       18.50 ms   (+0.02%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.85 s  →        1.85 s    (+0.04%) |       1   →       1              |        1.85 s  →        1.85 s    (+0.04%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      127.16 ms →      130.73 ms   (+2.81%) |       4   →       4              |      508.64 ms →      522.94 ms   (+2.81%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       53.14 ms →       52.35 ms   (-1.49%) |       1   →       1              |       53.14 ms →       52.35 ms   (-1.49%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.62 ms →       20.99 ms   (-2.92%) |       1   →       1              |       21.62 ms →       20.99 ms   (-2.92%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      634.50 ms →      634.77 ms   (+0.04%) |       1   →       1              |      634.50 ms →      634.77 ms   (+0.04%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      297.50 ms →      297.65 ms   (+0.05%) |       1   →       1              |      297.50 ms →      297.65 ms   (+0.05%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.22 μs →        3.40 μs   (+5.49%) |       1   →       1              |        3.22 μs →        3.40 μs   (+5.49%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.31 μs →        2.36 μs   (+1.90%) |       1   →       1              |        2.31 μs →        2.36 μs   (+1.90%) | 
- │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      329.00 ns →      365.00 ns  (+10.94%) |       1   →       1              |      329.00 ns →      365.00 ns  (+10.94%) | 
- │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      509.00 ns →      564.00 ns  (+10.81%) |       1   →       1              |      509.00 ns →      564.00 ns  (+10.81%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.22 ms →        9.22 ms   (+0.04%) |       1   →       1              |        9.22 ms →        9.22 ms   (+0.04%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      120.76 ms →      120.69 ms   (-0.06%) |       1   →       1              |      120.76 ms →      120.69 ms   (-0.06%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      103.49 ms →      103.58 ms   (+0.09%) |       2   →       2              |      206.99 ms →      207.17 ms   (+0.09%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       40.16 ms →       40.14 ms   (-0.05%) |       2   →       2              |       80.32 ms →       80.28 ms   (-0.05%) | 
  │ │ │ └ sddk::wf_inner                                                |       39.60 ms →       39.58 ms   (-0.06%) |       2   →       2              |       79.20 ms →       79.15 ms   (-0.06%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       12.00 ns →       79.00 ns (+558.33%) |       2   →       2              |       24.00 ns →      158.00 ns (+558.33%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       39.12 ms →       39.10 ms   (-0.05%) |       2   →       2              |       78.24 ms →       78.20 ms   (-0.05%) | 
+ │ │ │   └ sddk::wf_inner|scale_back                                   |       29.00 ns →       25.50 ns  (-12.07%) |       2   →       2              |       58.00 ns →       51.00 ns  (-12.07%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       57.23 ms →       56.60 ms   (-1.09%) |       1   →       1              |       57.23 ms →       56.60 ms   (-1.09%) | 
  │ │ └ sddk::wf_trans                                                  |       30.74 ms →       30.73 ms   (-0.02%) |       1   →       1              |       30.74 ms →       30.73 ms   (-0.02%) | 
  │ │   └ sddk::wf_trans|pw                                             |       30.74 ms →       30.73 ms   (-0.02%) |       1   →       1              |       30.74 ms →       30.73 ms   (-0.02%) | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      562.00 ns →      608.00 ns   (+8.19%) |       1   →       1              |      562.00 ns →      608.00 ns   (+8.19%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      123.12 s  →      119.12 s    (-3.25%) |       1   →       1              |      123.12 s  →      119.12 s    (-3.25%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.91 ms →        5.89 ms   (-0.40%) |      19   →      19              |      112.36 ms →      111.91 ms   (-0.40%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.72 s  →        4.57 s    (-3.23%) |      26   →      26              |      122.74 s  →      118.78 s    (-3.23%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        4.86 ms →        5.31 ms   (+9.35%) |      26   →      26              |      126.24 ms →      138.04 ms   (+9.35%) | 
- │ │ │ ├ sirius::Local_operator                                        |        4.49 ms →        4.95 ms  (+10.20%) |      26   →      26              |      116.68 ms →      128.58 ms  (+10.20%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |        1.03 ms →      942.18 μs   (-8.62%) |      26   →      26              |       26.81 ms →       24.50 ms   (-8.62%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.57 ms →        3.11 ms  (+21.32%) |      26   →      26              |       66.75 ms →       80.98 ms  (+21.32%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.51 μs →       64.87 μs   (+0.56%) |      52   →      52              |        3.35 ms →        3.37 ms   (+0.56%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       88.56 μs →       87.35 μs   (-1.37%) |      26   →      26              |        2.30 ms →        2.27 ms   (-1.37%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       78.78 μs →       78.36 μs   (-0.54%) |      26   →      26              |        2.05 ms →        2.04 ms   (-0.54%) | 
  │ │ ├ sirius::Band::solve                                             |        2.76 s  →        2.60 s    (-5.63%) |      26   →      26              |       71.70 s  →       67.67 s    (-5.63%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      155.62 μs →      154.22 μs   (-0.90%) |      26   →      26              |        4.05 ms →        4.01 ms   (-0.90%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      149.15 μs →      146.85 μs   (-1.54%) |      26   →      26              |        3.88 ms →        3.82 ms   (-1.54%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.57 μs →        5.47 μs  (+19.74%) |      26   →      26              |      118.80 μs →      142.25 μs  (+19.74%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.60 s  →        2.47 s    (-5.21%) |      26   →      26              |       67.72 s  →       64.19 s    (-5.21%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       95.70 ms →       95.16 ms   (-0.56%) |      26   →      26              |        2.49 s  →        2.47 s    (-0.56%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.60 ms →        7.69 ms   (+1.20%) |     156   →     156              |        1.19 s  →        1.20 s    (+1.20%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        5.99 ms →        5.91 ms   (-1.21%) |      26   →      26              |      155.66 ms →      153.77 ms   (-1.21%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      351.29 μs →      349.51 μs   (-0.51%) |      26   →      26              |        9.13 ms →        9.09 ms   (-0.51%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.31 ms →        2.29 ms   (-0.69%) |      52   →      52              |      120.11 ms →      119.28 ms   (-0.69%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.47 s  →        2.33 s    (-5.48%) |      26   →      26              |       64.15 s  →       60.64 s    (-5.48%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      126.10 ms →      136.76 ms   (+8.45%) |     278   →     262     (-5.76%) |       35.06 s  →       35.83 s    (+2.21%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       50.48 ms →       55.72 ms  (+10.39%) |     278   →     262     (-5.76%) |       14.03 s  →       14.60 s    (+4.04%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.84 μs →        1.92 μs   (+4.46%) |     278   →     262     (-5.76%) |      510.28 μs →      502.37 μs   (-1.55%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.58 μs →        1.61 μs   (+2.17%) |     278   →     262     (-5.76%) |      438.63 μs →      422.33 μs   (-3.71%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      342.03 ns →      394.14 ns  (+15.24%) |     278   →     262     (-5.76%) |       95.08 μs →      103.27 μs   (+8.60%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      388.29 ns →      478.38 ns  (+23.20%) |     278   →     262     (-5.76%) |      107.94 μs →      125.34 μs  (+16.11%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.42 ms →        7.45 ms   (+0.47%) |     278   →     262     (-5.76%) |        2.06 s  →        1.95 s    (-5.31%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       22.75 ms →       24.65 ms   (+8.37%) |     278   →     262     (-5.76%) |        6.32 s  →        6.46 s    (+2.14%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       22.72 ms →       24.46 ms   (+7.63%) |     556   →     524     (-5.76%) |       12.63 s  →       12.82 s    (+1.44%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       34.16 ms →       35.85 ms   (+4.95%) |     278   →     262     (-5.76%) |        9.50 s  →        9.39 s    (-1.09%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        5.93 ms →        6.22 ms   (+4.86%) |     530   →     498     (-6.04%) |        3.14 s  →        3.10 s    (-1.47%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       70.62 ns →       58.34 ns  (-17.39%) |     530   →     498     (-6.04%) |       37.43 μs →       29.05 μs  (-22.38%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        4.82 ms →        5.11 ms   (+6.01%) |     530   →     498     (-6.04%) |        2.55 s  →        2.54 s    (-0.39%) | 
+ │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       60.73 ns →       28.49 ns  (-53.09%) |     530   →     498     (-6.04%) |       32.19 μs →       14.19 μs  (-55.92%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      611.62 μs →      662.77 μs   (+8.36%) |     278   →     262     (-5.76%) |      170.03 ms →      173.64 ms   (+2.13%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        9.51 ms →       10.31 ms   (+8.35%) |     278   →     262     (-5.76%) |        2.64 s  →        2.70 s    (+2.11%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |       14.04 ms →       14.50 ms   (+3.27%) |     252   →     236     (-6.35%) |        3.54 s  →        3.42 s    (-3.29%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        4.68 ms →        4.83 ms   (+3.27%) |     756   →     708     (-6.35%) |        3.54 s  →        3.42 s    (-3.29%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       10.29 ms →       10.37 ms   (+0.85%) |     278   →     262     (-5.76%) |        2.86 s  →        2.72 s    (-4.95%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |       10.02 ms →       10.17 ms   (+1.53%) |     278   →     262     (-5.76%) |        2.78 s  →        2.66 s    (-4.32%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       47.58 ns →       27.81 ns  (-41.56%) |     278   →     262     (-5.76%) |       13.23 μs →        7.29 μs  (-44.92%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        8.90 ms →        9.06 ms   (+1.74%) |     278   →     262     (-5.76%) |        2.47 s  →        2.37 s    (-4.11%) | 
+ │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       82.96 ns →       49.75 ns  (-40.03%) |     278   →     262     (-5.76%) |       23.06 μs →       13.03 μs  (-43.49%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       32.88 ms →       18.37 ms  (-44.13%) |     278   →     262     (-5.76%) |        9.14 s  →        4.81 s   (-47.35%) | 
  │ │ │ │   ├ sirius::residuals                                         |       13.46 ms →       13.14 ms   (-2.37%) |     269   →     252     (-6.32%) |        3.62 s  →        3.31 s    (-8.54%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       12.10 ms →       11.71 ms   (-3.21%) |     260   →     242     (-6.92%) |        3.15 s  →        2.83 s    (-9.91%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        6.05 ms →        5.85 ms   (-3.21%) |     520   →     484     (-6.92%) |        3.15 s  →        2.83 s    (-9.91%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.58 ms →        1.71 ms   (+8.29%) |     260   →     242     (-6.92%) |      410.85 ms →      414.11 ms   (+0.79%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       74.92 ms →       53.72 ms  (-28.30%) |      53   →      85    (+60.38%) |        3.97 s  →        4.57 s   (+14.99%) | 
- │ │ │ │     └ sddk::wf_trans                                          |       49.40 ms →       31.44 ms  (-36.34%) |      80   →     144    (+80.00%) |        3.95 s  →        4.53 s   (+14.58%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |       36.93 ms →       22.30 ms  (-39.61%) |     107   →     203    (+89.72%) |        3.95 s  →        4.53 s   (+14.58%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      630.50 ns →      417.92 ns  (-33.72%) |      26   →      26              |       16.39 μs →       10.87 μs  (-33.72%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       29.72 μs →       31.41 μs   (+5.66%) |      26   →      26              |      772.83 μs →      816.57 μs   (+5.66%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      596.08 μs →      616.72 μs   (+3.46%) |      26   →      26              |       15.50 ms →       16.03 ms   (+3.46%) | 
  │ │ ├ sirius::Density::generate                                       |      776.75 ms →      769.44 ms   (-0.94%) |      26   →      26              |       20.20 s  →       20.01 s    (-0.94%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      403.71 ms →      402.04 ms   (-0.42%) |      26   →      26              |       10.50 s  →       10.45 s    (-0.42%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.33 μs →        9.58 μs  (+14.95%) |      26   →      26              |      216.68 μs →      249.07 μs  (+14.95%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.78 μs →        8.99 μs  (+15.51%) |      26   →      26              |      202.27 μs →      233.65 μs  (+15.51%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |      100.15 ms →      100.18 ms   (+0.03%) |      26   →      26              |        2.60 s  →        2.60 s    (+0.03%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.41 μs →        7.80 μs   (+5.24%) |      26   →      26              |      192.63 μs →      202.72 μs   (+5.24%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.11 ms →        7.12 ms   (+0.04%) |      26   →      26              |      184.98 ms →      185.05 ms   (+0.04%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       91.12 ms →       91.15 ms   (+0.02%) |      26   →      26              |        2.37 s  →        2.37 s    (+0.02%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      666.73 ns →      559.27 ns  (-16.12%) |      26   →      26              |       17.34 μs →       14.54 μs  (-16.12%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      163.10 ms →      162.73 ms   (-0.22%) |      26   →      26              |        4.24 s  →        4.23 s    (-0.22%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.65 ms →        1.63 ms   (-1.15%) |      26   →      26              |       42.92 ms →       42.43 ms   (-1.15%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.36 ms →       88.26 ms   (-0.11%) |      26   →      26              |        2.30 s  →        2.29 s    (-0.11%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.12 ms →       88.04 ms   (-0.10%) |      26   →      26              |        2.29 s  →        2.29 s    (-0.10%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      274.39 ms →      275.45 ms   (+0.39%) |      26   →      26              |        7.13 s  →        7.16 s    (+0.39%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      274.39 ms →      275.45 ms   (+0.39%) |      26   →      26              |        7.13 s  →        7.16 s    (+0.39%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.27 ms →       24.67 ms   (+1.63%) |      26   →      26              |      631.05 ms →      641.35 ms   (+1.63%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      225.79 ms →      226.65 ms   (+0.38%) |      26   →      26              |        5.87 s  →        5.89 s    (+0.38%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       23.13 ms →       22.95 ms   (-0.77%) |      26   →      26              |      601.37 ms →      596.71 ms   (-0.77%) | 
+ │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       89.67 ms →       80.15 ms  (-10.61%) |      26   →      26              |        2.33 s  →        2.08 s   (-10.61%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        5.38 ms →        8.21 ms  (+52.41%) |      26   →      26              |      139.98 ms →      213.34 ms  (+52.41%) | 
  │ │ ├ sirius::Density::mix                                            |      217.41 ms →      213.51 ms   (-1.80%) |      26   →      26              |        5.65 s  →        5.55 s    (-1.80%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      981.65 μs →      947.74 μs   (-3.45%) |      26   →      26              |       25.52 ms →       24.64 ms   (-3.45%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.59 ms →       10.31 ms   (-2.64%) |     334   →     334              |        3.54 s  →        3.44 s    (-2.64%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.33 ms →        9.96 ms   (-3.61%) |     334   →     334              |        3.45 s  →        3.33 s    (-3.61%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.33 ms →        9.95 ms   (-3.61%) |     334   →     334              |        3.45 s  →        3.32 s    (-3.61%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        6.39 ms →        6.42 ms   (+0.35%) |      26   →      26              |      166.23 ms →      166.81 ms   (+0.35%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.53 ms →        5.61 ms   (+1.46%) |      26   →      26              |      143.66 ms →      145.76 ms   (+1.46%) | 
  │ │ ├ sirius::Potential::generate                                     |      567.02 ms →      579.06 ms   (+2.12%) |      26   →      26              |       14.74 s  →       15.06 s    (+2.12%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      126.11 ms →      137.87 ms   (+9.32%) |      26   →      26              |        3.28 s  →        3.58 s    (+9.32%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        5.14 ms →       16.95 ms (+229.81%) |      26   →      26              |      133.60 ms →      440.64 ms (+229.81%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.21 ms →       11.10 ms   (+8.72%) |      26   →      26              |      265.52 ms →      288.68 ms   (+8.72%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        9.92 ms →        9.93 ms   (+0.15%) |      26   →      26              |      257.80 ms →      258.20 ms   (+0.15%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        9.91 ms →        9.93 ms   (+0.16%) |      26   →      26              |      257.78 ms →      258.18 ms   (+0.16%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      556.76 μs →      550.75 μs   (-1.08%) |      52   →      52              |       28.95 ms →       28.64 ms   (-1.08%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       48.91 ms →       48.81 ms   (-0.21%) |      26   →      26              |        1.27 s  →        1.27 s    (-0.21%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.49 ms →       46.52 ms   (+0.07%) |      26   →      26              |        1.21 s  →        1.21 s    (+0.07%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.09 ms →        2.99 ms   (-3.09%) |      52   →      52              |      160.56 ms →      155.60 ms   (-3.09%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.46 ms →        5.44 ms   (-0.38%) |      26   →      26              |      141.98 ms →      141.43 ms   (-0.38%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.47 ms →        6.43 ms   (-0.50%) |      26   →      26              |      168.10 ms →      167.26 ms   (-0.50%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.91 ms →       91.00 ms   (+0.10%) |      26   →      26              |        2.36 s  →        2.37 s    (+0.10%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      292.14 ms →      292.59 ms   (+0.15%) |      26   →      26              |        7.60 s  →        7.61 s    (+0.15%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      276.88 ms →      278.59 ms   (+0.62%) |      26   →      26              |        7.20 s  →        7.24 s    (+0.62%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      276.88 ms →      278.59 ms   (+0.62%) |      26   →      26              |        7.20 s  →        7.24 s    (+0.62%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.10 ms →       27.30 ms   (+0.74%) |      26   →      26              |      704.51 ms →      709.73 ms   (+0.74%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      222.24 ms →      223.80 ms   (+0.70%) |      26   →      26              |        5.78 s  →        5.82 s    (+0.70%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.72 ms →       23.72 ms   (+0.03%) |      26   →      26              |      616.62 ms →      616.82 ms   (+0.03%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.56 ms →        5.45 ms   (-2.02%) |      26   →      26              |      144.56 ms →      141.64 ms   (-2.02%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.12 ms →       10.24 ms   (+1.25%) |     182   →     182              |        1.84 s  →        1.86 s    (+1.25%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.72 ms →        9.77 ms   (+0.52%) |     182   →     182              |        1.77 s  →        1.78 s    (+0.52%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.72 ms →        9.77 ms   (+0.53%) |     182   →     182              |        1.77 s  →        1.78 s    (+0.53%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       11.01 ms →       10.57 ms   (-4.05%) |      78   →      78              |      858.92 ms →      824.11 ms   (-4.05%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.52 ms →       10.14 ms   (-3.58%) |      78   →      78              |      820.57 ms →      791.23 ms   (-3.58%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        9.89 ms →       10.01 ms   (+1.12%) |      26   →      26              |      257.26 ms →      260.13 ms   (+1.12%) | 
  │ │ └ sirius::Density::get_magnetisation                              |      111.82 μs →      114.43 μs   (+2.34%) |      26   →      26              |        2.91 ms →        2.98 ms   (+2.34%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |      107.04 μs →      109.72 μs   (+2.51%) |      26   →      26              |        2.78 ms →        2.85 ms   (+2.51%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.06 ms →        5.08 ms   (+0.52%) |       2   →       2              |       10.11 ms →       10.17 ms   (+0.52%) | 
  │ ├ sirius::Periodic_function|inner                                   |        9.75 ms →        9.70 ms   (-0.48%) |       6   →       6              |       58.50 ms →       58.22 ms   (-0.48%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        9.71 ms →        9.66 ms   (-0.54%) |       6   →       6              |       58.25 ms →       57.94 ms   (-0.54%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        9.71 ms →        9.66 ms   (-0.54%) |       6   →       6              |       58.25 ms →       57.94 ms   (-0.54%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.83 ms →       10.12 ms   (-6.58%) |       3   →       3              |       32.50 ms →       30.37 ms   (-6.58%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.56 ms →       10.06 ms   (-4.71%) |       3   →       3              |       31.68 ms →       30.19 ms   (-4.71%) | 
  ├ sirius::Periodic_function|inner                                     |        9.71 ms →        9.69 ms   (-0.23%) |       2   →       2              |       19.42 ms →       19.37 ms   (-0.23%) | 
  │ └ sirius::Periodic_function|inner_local                             |        9.69 ms →        9.66 ms   (-0.31%) |       2   →       2              |       19.38 ms →       19.32 ms   (-0.31%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.69 ms →        9.66 ms   (-0.31%) |       2   →       2              |       19.38 ms →       19.32 ms   (-0.31%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.58 ms →       10.06 ms   (-4.87%) |       1   →       1              |       10.58 ms →       10.06 ms   (-4.87%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.48 ms →       10.06 ms   (-4.03%) |       1   →       1              |       10.48 ms →       10.06 ms   (-4.03%) | 
+ └ sirius::finalize                                                    |      222.54 ms →      187.31 ms  (-15.83%) |       1   →       1              |      222.54 ms →      187.31 ms  (-15.83%) | 
  ====================================================================================================================================================================================================
```
