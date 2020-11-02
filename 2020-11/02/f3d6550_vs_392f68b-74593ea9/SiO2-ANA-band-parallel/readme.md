# Benchmark 392f68b5626168134a99cd6d4a3cc40b87322cb7 vs f3d65506dd217f3bfa11e8357960357f194d258d
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      224.23 s  →      215.89 s    (-3.72%) |       1   →       1              |      224.23 s  →      215.89 s    (-3.72%) | 
  ├ sirius::initialize                                                  |        2.67 s  →        2.65 s    (-0.84%) |       1   →       1              |        2.67 s  →        2.65 s    (-0.84%) | 
  ├ sirius::Simulation_context::initialize                              |        2.92 s  →        2.88 s    (-1.44%) |       1   →       1              |        2.92 s  →        2.88 s    (-1.44%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       22.00 ms →      374.59 μs  (-98.30%) |       1   →       1              |       22.00 ms →      374.59 μs  (-98.30%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      142.84 ms →      108.35 ms  (-24.15%) |       1   →       1              |      142.84 ms →      108.35 ms  (-24.15%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       59.70 ms →       42.76 ms  (-28.39%) |       2   →       2              |      119.41 ms →       85.51 ms  (-28.39%) | 
  │ │ └ sirius::Unit_cell::update                                       |       23.35 ms →       22.76 ms   (-2.55%) |       1   →       1              |       23.35 ms →       22.76 ms   (-2.55%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.75 ms →        6.43 ms   (-4.78%) |       1   →       1              |        6.75 ms →        6.43 ms   (-4.78%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       16.56 ms →       16.29 ms   (-1.61%) |       1   →       1              |       16.56 ms →       16.29 ms   (-1.61%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       16.54 ms →       16.27 ms   (-1.61%) |       1   →       1              |       16.54 ms →       16.27 ms   (-1.61%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.16 ms →        4.17 ms   (+0.14%) |       1   →       1              |        4.16 ms →        4.17 ms   (+0.14%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.35 ms   (+1.21%) |       1   →       1              |        2.32 ms →        2.35 ms   (+1.21%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      105.27 μs →      110.89 μs   (+5.34%) |       1   →       1              |      105.27 μs →      110.89 μs   (+5.34%) | 
  │ └ sirius::Simulation_context::update                                |        2.71 s  →        2.72 s    (+0.50%) |       1   →       1              |        2.71 s  →        2.72 s    (+0.50%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.80 ms →       10.64 ms   (-1.47%) |       1   →       1              |       10.80 ms →       10.64 ms   (-1.47%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.41 ms →        4.26 ms   (-3.49%) |       1   →       1              |        4.41 ms →        4.26 ms   (-3.49%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.35 ms →        6.34 ms   (-0.16%) |       1   →       1              |        6.35 ms →        6.34 ms   (-0.16%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.33 ms →        6.32 ms   (-0.14%) |       1   →       1              |        6.33 ms →        6.32 ms   (-0.14%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.83 ms →        3.82 ms   (-0.11%) |       1   →       1              |        3.83 ms →        3.82 ms   (-0.11%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.32 ms   (-0.31%) |       1   →       1              |        2.33 ms →        2.32 ms   (-0.31%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      108.14 μs →      110.64 μs   (+2.32%) |       1   →       1              |      108.14 μs →      110.64 μs   (+2.32%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       62.78 ms →       62.66 ms   (-0.18%) |       2   →       2              |      125.55 ms →      125.33 ms   (-0.18%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.15 ms →        5.28 ms   (+2.41%) |       2   →       2              |       10.30 ms →       10.55 ms   (+2.41%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.56 ms →        4.49 ms   (-1.43%) |       1   →       1              |        4.56 ms →        4.49 ms   (-1.43%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.77 ms →       21.78 ms   (+0.06%) |       2   →       2              |       43.54 ms →       43.56 ms   (+0.06%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.79 ms →       14.77 ms   (-0.17%) |       2   →       2              |       29.58 ms →       29.53 ms   (-0.17%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.55 ms →       19.67 ms   (+0.61%) |       4   →       4              |       78.19 ms →       78.67 ms   (+0.61%) | 
  │   ├ sddk::Gvec::init                                                |      171.25 ms →      173.52 ms   (+1.32%) |       2   →       2              |      342.50 ms →      347.04 ms   (+1.32%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      128.25 ms →      129.86 ms   (+1.26%) |       2   →       2              |      256.49 ms →      259.72 ms   (+1.26%) | 
  │   ├ sddk::Gvec_shells                                               |      180.35 ms →      197.48 ms   (+9.50%) |       1   →       1              |      180.35 ms →      197.48 ms   (+9.50%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.32 ms →        1.31 ms   (-0.48%) |       1   →       1              |        1.32 ms →        1.31 ms   (-0.48%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      293.83 ms →      294.90 ms   (+0.37%) |       2   →       2              |      587.65 ms →      589.81 ms   (+0.37%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       79.01 ms →       75.72 ms   (-4.16%) |       1   →       1              |       79.01 ms →       75.72 ms   (-4.16%) | 
  │ ├ sirius::K_point::K_point                                          |        2.82 μs →        2.81 μs   (-0.28%) |       4   →       4              |       11.28 μs →       11.25 μs   (-0.28%) | 
  │ └ sirius::K_point_set::initialize                                   |       78.88 ms →       75.61 ms   (-4.15%) |       1   →       1              |       78.88 ms →       75.61 ms   (-4.15%) | 
  │   └ sirius::K_point::initialize                                     |       19.70 ms →       18.88 ms   (-4.15%) |       4   →       4              |       78.80 ms →       75.53 ms   (-4.15%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       15.07 ms →       14.22 ms   (-5.66%) |       4   →       4              |       60.28 ms →       56.86 ms   (-5.66%) | 
  │     │ └ sddk::Gvec::init                                            |        3.86 ms →        3.92 ms   (+1.57%) |       4   →       4              |       15.42 ms →       15.67 ms   (+1.57%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        8.79 μs →        9.00 μs   (+2.43%) |       4   →       4              |       35.16 μs →       36.02 μs   (+2.43%) | 
  │     └ sirius::K_point::update                                       |        3.32 ms →        3.34 ms   (+0.61%) |       4   →       4              |       13.27 ms →       13.35 ms   (+0.61%) | 
  │       └ sirius::Beta_projectors                                     |        1.76 ms →        1.79 ms   (+1.77%) |       4   →       4              |        7.03 ms →        7.15 ms   (+1.77%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      920.83 μs →      924.84 μs   (+0.44%) |       4   →       4              |        3.68 ms →        3.70 ms   (+0.44%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.30 ms →        5.15 ms   (-2.78%) |       2   →       2              |       10.59 ms →       10.30 ms   (-2.78%) | 
  ├ sirius::Potential                                                   |      160.98 ms →      157.93 ms   (-1.89%) |       1   →       1              |      160.98 ms →      157.93 ms   (-1.89%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.89 ms →        5.70 ms   (-3.23%) |       6   →       6              |       35.35 ms →       34.20 ms   (-3.23%) | 
  │ └ sirius::Potential::update                                         |      124.95 ms →      123.03 ms   (-1.53%) |       1   →       1              |      124.95 ms →      123.03 ms   (-1.53%) | 
  │   └ sirius::Potential::generate_local_potential                     |      124.23 ms →      122.32 ms   (-1.54%) |       1   →       1              |      124.23 ms →      122.32 ms   (-1.54%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      111.23 ms →      111.78 ms   (+0.49%) |       1   →       1              |      111.23 ms →      111.78 ms   (+0.49%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       12.14 ms →        9.66 ms  (-20.39%) |       1   →       1              |       12.14 ms →        9.66 ms  (-20.39%) | 
  ├ sirius::Density                                                     |      136.24 ms →      134.77 ms   (-1.08%) |       1   →       1              |      136.24 ms →      134.77 ms   (-1.08%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.11 ms →        5.08 ms   (-0.48%) |       2   →       2              |       10.21 ms →       10.16 ms   (-0.48%) | 
  │ └ sirius::Density::update                                           |      125.77 ms →      124.34 ms   (-1.14%) |       1   →       1              |      125.77 ms →      124.34 ms   (-1.14%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      125.35 ms →      123.93 ms   (-1.13%) |       1   →       1              |      125.35 ms →      123.93 ms   (-1.13%) | 
+ │     ├ sirius::rho_core_ri_pseudo|values                             |      119.54 μs →      106.24 μs  (-11.13%) |       1   →       1              |      119.54 μs →      106.24 μs  (-11.13%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      112.86 ms →      112.31 ms   (-0.49%) |       1   →       1              |      112.86 ms →      112.31 ms   (-0.49%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |       11.93 ms →       10.97 ms   (-8.07%) |       1   →       1              |       11.93 ms →       10.97 ms   (-8.07%) | 
  ├ sirius::Density::initial_density                                    |      174.91 ms →      174.97 ms   (+0.03%) |       1   →       1              |      174.91 ms →      174.97 ms   (+0.03%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      111.67 ms →      111.69 ms   (+0.02%) |       1   →       1              |      111.67 ms →      111.69 ms   (+0.02%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |       10.82 ms →       10.78 ms   (-0.35%) |       2   →       2              |       21.64 ms →       21.56 ms   (-0.35%) | 
  │ └ sirius::Periodic_function::integrate                              |        9.88 ms →        9.72 ms   (-1.64%) |       1   →       1              |        9.88 ms →        9.72 ms   (-1.64%) | 
  ├ sirius::Potential::generate                                         |      593.48 ms →      592.54 ms   (-0.16%) |       1   →       1              |      593.48 ms →      592.54 ms   (-0.16%) | 
  │ ├ sirius::Potential::poisson                                        |      138.72 ms →      138.34 ms   (-0.27%) |       1   →       1              |      138.72 ms →      138.34 ms   (-0.27%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       16.92 ms →       17.94 ms   (+6.03%) |       1   →       1              |       16.92 ms →       17.94 ms   (+6.03%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       11.16 ms →       10.54 ms   (-5.63%) |       1   →       1              |       11.16 ms →       10.54 ms   (-5.63%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |       10.69 ms →        9.81 ms   (-8.24%) |       1   →       1              |       10.69 ms →        9.81 ms   (-8.24%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |       10.69 ms →        9.81 ms   (-8.24%) |       1   →       1              |       10.69 ms →        9.81 ms   (-8.24%) | 
  │ ├ sirius::Periodic_function::add                                    |      545.92 μs →      542.12 μs   (-0.70%) |       2   →       2              |        1.09 ms →        1.08 ms   (-0.70%) | 
  │ ├ sirius::Potential::xc                                             |       53.75 ms →       53.47 ms   (-0.53%) |       1   →       1              |       53.75 ms →       53.47 ms   (-0.53%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.47 ms →       51.17 ms   (-0.59%) |       1   →       1              |       51.47 ms →       51.17 ms   (-0.59%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.58 ms →        5.58 ms   (-0.09%) |       2   →       2              |       11.17 ms →       11.16 ms   (-0.09%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.43 ms →        5.42 ms   (-0.22%) |       1   →       1              |        5.43 ms →        5.42 ms   (-0.22%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.84 ms →        5.81 ms   (-0.44%) |       1   →       1              |        5.84 ms →        5.81 ms   (-0.44%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       93.64 ms →       93.55 ms   (-0.09%) |       1   →       1              |       93.64 ms →       93.55 ms   (-0.09%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      299.11 ms →      298.94 ms   (-0.06%) |       1   →       1              |      299.11 ms →      298.94 ms   (-0.06%) | 
  ├ sirius::Hamiltonian0                                                |        8.40 ms →        8.41 ms   (+0.13%) |       1   →       1              |        8.40 ms →        8.41 ms   (+0.13%) | 
  │ ├ sirius::Local_operator                                            |        8.06 ms →        8.07 ms   (+0.15%) |       1   →       1              |        8.06 ms →        8.07 ms   (+0.15%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.73 ms →        4.69 ms   (-0.73%) |       1   →       1              |        4.73 ms →        4.69 ms   (-0.73%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.41 ms →        2.45 ms   (+1.87%) |       1   →       1              |        2.41 ms →        2.45 ms   (+1.87%) | 
  │ ├ sirius::Non_local_operator                                        |       63.60 μs →       62.91 μs   (-1.10%) |       2   →       2              |      127.21 μs →      125.81 μs   (-1.10%) | 
  │ ├ sirius::D_operator::initialize                                    |       92.39 μs →       91.82 μs   (-0.62%) |       1   →       1              |       92.39 μs →       91.82 μs   (-0.62%) | 
  │ └ sirius::Q_operator::initialize                                    |       66.97 μs →       67.01 μs   (+0.07%) |       1   →       1              |       66.97 μs →       67.01 μs   (+0.07%) | 
  ├ sirius::Band::initialize_subspace                                   |        3.09 s  →        3.09 s    (+0.13%) |       1   →       1              |        3.09 s  →        3.09 s    (+0.13%) | 
  │ ├ sirius::Hamiltonian_k                                             |      382.24 μs →      378.46 μs   (-0.99%) |       4   →       4              |        1.53 ms →        1.51 ms   (-0.99%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      377.36 μs →      373.33 μs   (-1.07%) |       4   →       4              |        1.51 ms →        1.49 ms   (-1.07%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        3.20 μs →        3.43 μs   (+7.00%) |       4   →       4              |       12.82 μs →       13.71 μs   (+7.00%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |      771.47 ms →      772.51 ms   (+0.13%) |       4   →       4              |        3.09 s  →        3.09 s    (+0.13%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       32.35 ms →       32.45 ms   (+0.31%) |      16   →      16              |      517.53 ms →      519.12 ms   (+0.31%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       14.55 ms →       14.38 ms   (-1.19%) |       4   →       4              |       58.20 ms →       57.51 ms   (-1.19%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        5.28 ms →        5.27 ms   (-0.21%) |       4   →       4              |       21.14 ms →       21.09 ms   (-0.21%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      353.45 ms →      354.38 ms   (+0.26%) |       4   →       4              |        1.41 s  →        1.42 s    (+0.26%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      257.10 ms →      257.87 ms   (+0.30%) |       4   →       4              |        1.03 s  →        1.03 s    (+0.30%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       63.23 ms →       64.21 ms   (+1.55%) |       4   →       4              |      252.93 ms →      256.85 ms   (+1.55%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       16.34 ms →       16.62 ms   (+1.76%) |       4   →       4              |       65.35 ms →       66.50 ms   (+1.76%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       16.34 ms →       16.62 ms   (+1.76%) |       4   →       4              |       65.34 ms →       66.49 ms   (+1.76%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       40.38 ms →       41.11 ms   (+1.82%) |       4   →       4              |      161.52 ms →      164.45 ms   (+1.82%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |       16.18 ms →       16.36 ms   (+1.10%) |       4   →       4              |       64.71 ms →       65.42 ms   (+1.10%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |       16.17 ms →       16.35 ms   (+1.10%) |       4   →       4              |       64.70 ms →       65.41 ms   (+1.10%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |       54.01 ms →       53.53 ms   (-0.88%) |       4   →       4              |      216.05 ms →      214.14 ms   (-0.88%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |       35.96 ms →       35.46 ms   (-1.41%) |       4   →       4              |      143.85 ms →      141.82 ms   (-1.41%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        1.97 ms →        1.96 ms   (-0.51%) |       4   →       4              |        7.88 ms →        7.84 ms   (-0.51%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       40.14 ms →       40.11 ms   (-0.06%) |       4   →       4              |      160.55 ms →      160.45 ms   (-0.06%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |        6.97 ms →        6.94 ms   (-0.50%) |       4   →       4              |       27.89 ms →       27.75 ms   (-0.50%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       27.10 ms →       27.20 ms   (+0.35%) |       8   →       8              |      216.84 ms →      217.61 ms   (+0.35%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.89 ms →       14.73 ms   (-1.05%) |       8   →       8              |      119.10 ms →      117.85 ms   (-1.05%) | 
  │ │ │ └ sddk::wf_inner                                                |       14.84 ms →       14.69 ms   (-1.06%) |       8   →       8              |      118.75 ms →      117.49 ms   (-1.06%) | 
+ │ │ │   ├ sddk::wf_inner|scale                                        |       62.13 ns →       42.63 ns  (-31.39%) |       8   →       8              |      497.00 ns →      341.00 ns  (-31.39%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       14.64 ms →       14.51 ms   (-0.94%) |       8   →       8              |      117.16 ms →      116.06 ms   (-0.94%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       22.75 ns →       30.87 ns  (+35.71%) |       8   →       8              |      182.00 ns →      247.00 ns  (+35.71%) | 
  │ │ ├ Eigensolver_scalapack|pzhegvx                                   |      117.03 ms →      116.29 ms   (-0.63%) |       4   →       4              |      468.11 ms →      465.17 ms   (-0.63%) | 
  │ │ └ sddk::wf_trans                                                  |       26.70 ms →       26.64 ms   (-0.22%) |       4   →       4              |      106.80 ms →      106.56 ms   (-0.22%) | 
  │ │   └ sddk::wf_trans|pw                                             |       26.54 ms →       26.54 ms   (+0.02%) |       4   →       4              |      106.15 ms →      106.17 ms   (+0.02%) | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      395.50 ns →      365.50 ns   (-7.59%) |       4   →       4              |        1.58 μs →        1.46 μs   (-7.59%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      213.58 s  →      205.30 s    (-3.88%) |       1   →       1              |      213.58 s  →      205.30 s    (-3.88%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.72 ms →        5.70 ms   (-0.23%) |      19   →      19              |      108.62 ms →      108.37 ms   (-0.23%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        7.90 s  →        8.20 s    (+3.80%) |      27   →      25     (-7.41%) |      213.22 s  →      204.92 s    (-3.89%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        4.56 ms →        4.54 ms   (-0.61%) |      27   →      25     (-7.41%) |      123.24 ms →      113.42 ms   (-7.97%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.21 ms →        4.18 ms   (-0.61%) |      27   →      25     (-7.41%) |      113.65 ms →      104.58 ms   (-7.98%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      985.92 μs →      967.73 μs   (-1.84%) |      27   →      25     (-7.41%) |       26.62 ms →       24.19 ms   (-9.11%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.34 ms →        2.33 ms   (-0.20%) |      27   →      25     (-7.41%) |       63.08 ms →       58.29 ms   (-7.60%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       63.96 μs →       64.39 μs   (+0.67%) |      54   →      50     (-7.41%) |        3.45 ms →        3.22 ms   (-6.78%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       91.10 μs →       90.33 μs   (-0.84%) |      27   →      25     (-7.41%) |        2.46 ms →        2.26 ms   (-8.18%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       65.18 μs →       65.65 μs   (+0.72%) |      27   →      25     (-7.41%) |        1.76 ms →        1.64 ms   (-6.74%) | 
  │ │ ├ sirius::Band::solve                                             |        5.80 s  →        6.07 s    (+4.81%) |      27   →      25     (-7.41%) |      156.49 s  →      151.87 s    (-2.95%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      323.69 μs →      319.78 μs   (-1.21%) |     108   →     100     (-7.41%) |       34.96 ms →       31.98 ms   (-8.53%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      318.32 μs →      314.17 μs   (-1.30%) |     108   →     100     (-7.41%) |       34.38 ms →       31.42 ms   (-8.61%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        3.96 μs →        4.19 μs   (+6.01%) |     108   →     100     (-7.41%) |      427.17 μs →      419.32 μs   (-1.84%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.45 s  →        1.52 s    (+4.81%) |     108   →     100     (-7.41%) |      156.45 s  →      151.84 s    (-2.95%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       11.95 ms →       11.97 ms   (+0.10%) |     108   →     100     (-7.41%) |        1.29 s  →        1.20 s    (-7.31%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |      671.29 ns →      695.97 ns   (+3.68%) |     648   →     600     (-7.41%) |      435.00 μs →      417.58 μs   (-4.00%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.83 ms →        1.82 ms   (-0.22%) |     108   →     100     (-7.41%) |      197.47 ms →      182.45 ms   (-7.61%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      353.09 μs →      354.06 μs   (+0.27%) |     108   →     100     (-7.41%) |       38.13 ms →       35.41 ms   (-7.15%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      552.67 μs →      548.71 μs   (-0.72%) |     216   →     200     (-7.41%) |      119.38 ms →      109.74 ms   (-8.07%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.43 s  →        1.50 s    (+4.89%) |     108   →     100     (-7.41%) |      153.99 s  →      149.55 s    (-2.88%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       69.30 ms →       68.89 ms   (-0.59%) |     954   →     929     (-2.62%) |       66.11 s  →       64.00 s    (-3.20%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       44.35 ms →       44.04 ms   (-0.70%) |     954   →     929     (-2.62%) |       42.31 s  →       40.91 s    (-3.30%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        8.74 ms →        8.75 ms   (+0.12%) |     954   →     929     (-2.62%) |        8.34 s  →        8.13 s    (-2.50%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      220.41 μs →      230.20 μs   (+4.44%) |     954   →     929     (-2.62%) |      210.27 ms →      213.85 ms   (+1.70%) | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        1.93 ms →        2.12 ms   (+9.88%) |     108   →     100     (-7.41%) |      208.47 ms →      212.09 ms   (+1.74%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |        6.75 ms →        6.71 ms   (-0.59%) |     954   →     929     (-2.62%) |        6.44 s  →        6.24 s    (-3.19%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |       85.15 μs →       87.90 μs   (+3.22%) |     954   →     929     (-2.62%) |       81.23 ms →       81.66 ms   (+0.52%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |      730.63 μs →      793.94 μs   (+8.66%) |     108   →     100     (-7.41%) |       78.91 ms →       79.39 ms   (+0.62%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |        9.75 ms →        9.64 ms   (-1.15%) |     954   →     929     (-2.62%) |        9.30 s  →        8.96 s    (-3.74%) | 
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |        6.14 ms →        6.06 ms   (-1.29%) |     954   →     929     (-2.62%) |        5.86 s  →        5.63 s    (-3.88%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        1.53 ms →        1.52 ms   (-0.28%) |     954   →     929     (-2.62%) |        1.46 s  →        1.41 s    (-2.90%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        8.52 ms →        8.45 ms   (-0.79%) |     954   →     929     (-2.62%) |        8.13 s  →        7.85 s    (-3.39%) | 
  │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        1.23 ms →        1.22 ms   (-0.98%) |     954   →     929     (-2.62%) |        1.18 s  →        1.13 s    (-3.58%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.44 ms →        7.42 ms   (-0.17%) |    1.91 K →    1.86 K   (-2.62%) |       14.19 s  →       13.80 s    (-2.79%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       28.91 ms →       28.81 ms   (-0.35%) |     954   →     929     (-2.62%) |       27.58 s  →       26.76 s    (-2.96%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        1.97 ms →        1.94 ms   (-1.76%) |    1.80 K →    1.76 K   (-2.33%) |        3.55 s  →        3.41 s    (-4.05%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       74.90 ns →       75.88 ns   (+1.31%) |    1.80 K →    1.76 K   (-2.33%) |      134.82 μs →      133.40 μs   (-1.06%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        1.96 ms →        1.93 ms   (-1.62%) |    1.80 K →    1.76 K   (-2.33%) |        3.53 s  →        3.40 s    (-3.92%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       67.02 ns →       88.43 ns  (+31.95%) |    1.80 K →    1.76 K   (-2.33%) |      120.63 μs →      155.46 μs  (+28.87%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|potrf                               |      857.80 μs →      811.98 μs   (-5.34%) |     954   →     929     (-2.62%) |      818.34 ms →      754.33 ms   (-7.82%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|trtri                               |      750.45 μs →      732.70 μs   (-2.36%) |     954   →     929     (-2.62%) |      715.93 ms →      680.68 ms   (-4.92%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |        5.66 ms →        5.66 ms   (-0.01%) |    3.71 K →    3.62 K   (-2.48%) |       20.99 s  →       20.47 s    (-2.50%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        3.86 ms →        3.86 ms   (-0.02%) |    5.40 K →    5.27 K   (-2.33%) |       20.84 s  →       20.35 s    (-2.35%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        5.29 ms →        5.31 ms   (+0.44%) |     954   →     929     (-2.62%) |        5.04 s  →        4.93 s    (-2.19%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |        3.51 ms →        3.50 ms   (-0.38%) |     954   →     929     (-2.62%) |        3.35 s  →        3.25 s    (-2.99%) | 
- │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       56.53 ns →       81.01 ns  (+43.31%) |     954   →     929     (-2.62%) |       53.93 μs →       75.26 μs  (+39.55%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        3.50 ms →        3.49 ms   (-0.32%) |     954   →     929     (-2.62%) |        3.34 s  →        3.24 s    (-2.93%) | 
+ │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       66.03 ns →       54.94 ns  (-16.79%) |     954   →     929     (-2.62%) |       62.99 μs →       51.04 μs  (-18.97%) | 
  │ │ │ │   ├ Eigensolver_scalapack|pzheevx                             |       32.64 ms →       32.87 ms   (+0.71%) |     954   →     929     (-2.62%) |       31.14 s  →       30.53 s    (-1.93%) | 
  │ │ │ │   ├ sirius::residuals                                         |       10.80 ms →       10.53 ms   (-2.47%) |     928   →     904     (-2.59%) |       10.02 s  →        9.52 s    (-4.99%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       10.42 ms →       10.21 ms   (-2.05%) |     885   →     858     (-3.05%) |        9.22 s  →        8.76 s    (-5.04%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        5.19 ms →        5.08 ms   (-2.00%) |    1.77 K →    1.72 K   (-3.05%) |        9.18 s  →        8.72 s    (-4.99%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      630.91 μs →      618.63 μs   (-1.95%) |     885   →     858     (-3.05%) |      558.35 ms →      530.78 ms   (-4.94%) | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       40.44 ms →       40.65 ms   (+0.50%) |     348   →     339     (-2.59%) |       14.07 s  →       13.78 s    (-2.09%) | 
  │ │ │ │     └ sddk::wf_trans                                          |       23.81 ms →       23.71 ms   (-0.40%) |     588   →     578     (-1.70%) |       14.00 s  →       13.71 s    (-2.10%) | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |       16.84 ms →       16.71 ms   (-0.75%) |     828   →     817     (-1.33%) |       13.94 s  →       13.65 s    (-2.07%) | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      458.83 ns →      500.04 ns   (+8.98%) |     108   →     100     (-7.41%) |       49.55 μs →       50.00 μs   (+0.91%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       22.52 μs →       23.64 μs   (+4.96%) |      27   →      25     (-7.41%) |      608.08 μs →      590.96 μs   (-2.81%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      594.44 μs →      610.49 μs   (+2.70%) |      27   →      25     (-7.41%) |       16.05 ms →       15.26 ms   (-4.91%) | 
  │ │ ├ sirius::Density::generate                                       |      888.89 ms →      907.01 ms   (+2.04%) |      27   →      25     (-7.41%) |       24.00 s  →       22.68 s    (-5.52%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      524.35 ms →      524.73 ms   (+0.07%) |      27   →      25     (-7.41%) |       14.16 s  →       13.12 s    (-7.34%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       24.40 ms →       24.58 ms   (+0.77%) |     108   →     100     (-7.41%) |        2.63 s  →        2.46 s    (-6.70%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |        5.91 μs →        6.12 μs   (+3.56%) |     108   →     100     (-7.41%) |      638.38 μs →      612.16 μs   (-4.11%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       12.92 μs →       13.65 μs   (+5.58%) |       8   →       8              |      103.40 μs →      109.17 μs   (+5.58%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       20.28 ms →       20.45 ms   (+0.84%) |     108   →     100     (-7.41%) |        2.19 s  →        2.05 s    (-6.63%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       29.81 ms →       29.85 ms   (+0.13%) |     108   →     100     (-7.41%) |        3.22 s  →        2.98 s    (-7.29%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       10.84 μs →       10.98 μs   (+1.32%) |     108   →     100     (-7.41%) |        1.17 ms →        1.10 ms   (-6.18%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        1.47 ms →        1.46 ms   (-0.51%) |     108   →     100     (-7.41%) |      158.62 ms →      146.12 ms   (-7.88%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       27.86 ms →       27.91 ms   (+0.17%) |     108   →     100     (-7.41%) |        3.01 s  →        2.79 s    (-7.25%) | 
  │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        3.72 ms →        3.77 ms   (+1.49%) |     108   →     100     (-7.41%) |      401.44 ms →      377.25 ms   (-6.03%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      587.98 ns →      521.29 ns  (-11.34%) |     108   →     100     (-7.41%) |       63.50 μs →       52.13 μs  (-17.91%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       42.62 ms →       42.51 ms   (-0.27%) |     108   →     100     (-7.41%) |        4.60 s  →        4.25 s    (-7.66%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.63 ms   (-0.55%) |      27   →      25     (-7.41%) |       44.38 ms →       40.87 ms   (-7.92%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.91 ms →       88.96 ms   (+0.06%) |      27   →      25     (-7.41%) |        2.40 s  →        2.22 s    (-7.35%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.68 ms →       88.72 ms   (+0.05%) |      27   →      25     (-7.41%) |        2.39 s  →        2.22 s    (-7.36%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      271.42 ms →      285.02 ms   (+5.01%) |      27   →      25     (-7.41%) |        7.33 s  →        7.13 s    (-2.77%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      271.42 ms →      285.02 ms   (+5.01%) |      27   →      25     (-7.41%) |        7.33 s  →        7.13 s    (-2.77%) | 
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.24 ms →       30.12 ms  (+24.27%) |      27   →      25     (-7.41%) |      654.54 ms →      753.12 ms  (+15.06%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      221.45 ms →      228.92 ms   (+3.37%) |      27   →      25     (-7.41%) |        5.98 s  →        5.72 s    (-4.28%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       23.95 ms →       24.18 ms   (+0.95%) |      27   →      25     (-7.41%) |      646.69 ms →      604.45 ms   (-6.53%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       80.80 ms →       81.65 ms   (+1.06%) |      27   →      25     (-7.41%) |        2.18 s  →        2.04 s    (-6.43%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        8.73 ms →       12.01 ms  (+37.62%) |      27   →      25     (-7.41%) |      235.72 ms →      300.37 ms  (+27.43%) | 
+ │ │ ├ sirius::Density::mix                                            |      220.15 ms →      212.12 ms   (-3.65%) |      27   →      25     (-7.41%) |        5.94 s  →        5.30 s   (-10.79%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      963.01 μs →      936.92 μs   (-2.71%) |      27   →      25     (-7.41%) |       26.00 ms →       23.42 ms   (-9.92%) | 
+ │ │ │ ├ sirius::Periodic_function|inner                               |       10.72 ms →       10.36 ms   (-3.35%) |     349   →     319     (-8.60%) |        3.74 s  →        3.30 s   (-11.66%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.40 ms →       10.01 ms   (-3.73%) |     349   →     319     (-8.60%) |        3.63 s  →        3.19 s   (-12.01%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.40 ms →       10.01 ms   (-3.73%) |     349   →     319     (-8.60%) |        3.63 s  →        3.19 s   (-12.01%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        6.14 ms →        6.53 ms   (+6.33%) |      27   →      25     (-7.41%) |      165.77 ms →      163.20 ms   (-1.55%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.34 ms →        5.68 ms   (+6.35%) |      27   →      25     (-7.41%) |      144.14 ms →      141.94 ms   (-1.53%) | 
  │ │ ├ sirius::Potential::generate                                     |      592.68 ms →      579.83 ms   (-2.17%) |      27   →      25     (-7.41%) |       16.00 s  →       14.50 s    (-9.41%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      138.66 ms →      137.75 ms   (-0.66%) |      27   →      25     (-7.41%) |        3.74 s  →        3.44 s    (-8.02%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       17.01 ms →       17.07 ms   (+0.37%) |      27   →      25     (-7.41%) |      459.31 ms →      426.86 ms   (-7.06%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner                             |       11.07 ms →       10.16 ms   (-8.20%) |      27   →      25     (-7.41%) |      298.84 ms →      254.00 ms  (-15.00%) | 
+ │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.87 ms →        9.95 ms   (-8.45%) |      27   →      25     (-7.41%) |      293.53 ms →      248.82 ms  (-15.23%) | 
+ │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.87 ms →        9.95 ms   (-8.45%) |      27   →      25     (-7.41%) |      293.51 ms →      248.81 ms  (-15.23%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      544.95 μs →      545.00 μs   (+0.01%) |      54   →      50     (-7.41%) |       29.43 ms →       27.25 ms   (-7.40%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       49.87 ms →       49.38 ms   (-0.97%) |      27   →      25     (-7.41%) |        1.35 s  →        1.23 s    (-8.30%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       47.52 ms →       47.05 ms   (-0.99%) |      27   →      25     (-7.41%) |        1.28 s  →        1.18 s    (-8.32%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.02 ms →        3.01 ms   (-0.47%) |      54   →      50     (-7.41%) |      163.27 ms →      150.47 ms   (-7.84%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.33 ms →        5.61 ms   (+5.23%) |      27   →      25     (-7.41%) |      143.92 ms →      140.22 ms   (-2.57%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.69 ms →        6.76 ms   (+0.97%) |      27   →      25     (-7.41%) |      180.68 ms →      168.92 ms   (-6.51%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.91 ms →       90.91 ms   (-0.00%) |      27   →      25     (-7.41%) |        2.45 s  →        2.27 s    (-7.41%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      304.14 ms →      292.67 ms   (-3.77%) |      27   →      25     (-7.41%) |        8.21 s  →        7.32 s   (-10.90%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      272.28 ms →      290.09 ms   (+6.54%) |      27   →      25     (-7.41%) |        7.35 s  →        7.25 s    (-1.35%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      272.27 ms →      290.09 ms   (+6.54%) |      27   →      25     (-7.41%) |        7.35 s  →        7.25 s    (-1.35%) | 
- │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       26.93 ms →       33.26 ms  (+23.51%) |      27   →      25     (-7.41%) |      727.13 ms →      831.57 ms  (+14.36%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      217.69 ms →      229.05 ms   (+5.22%) |      27   →      25     (-7.41%) |        5.88 s  →        5.73 s    (-2.57%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.86 ms →       23.97 ms   (+0.44%) |      27   →      25     (-7.41%) |      644.29 ms →      599.19 ms   (-7.00%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.72 ms →       11.85 ms (+107.11%) |      27   →      25     (-7.41%) |      154.50 ms →      296.28 ms  (+91.76%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.53 ms →       10.68 ms   (+1.43%) |     189   →     175     (-7.41%) |        1.99 s  →        1.87 s    (-6.08%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.89 ms →       10.31 ms   (+4.32%) |     189   →     175     (-7.41%) |        1.87 s  →        1.80 s    (-3.41%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.89 ms →       10.31 ms   (+4.32%) |     189   →     175     (-7.41%) |        1.87 s  →        1.80 s    (-3.41%) | 
+ │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.69 ms →       10.30 ms   (-3.69%) |      81   →      75     (-7.41%) |      866.02 ms →      772.30 ms  (-10.82%) | 
+ │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.26 ms →        9.87 ms   (-3.76%) |      81   →      75     (-7.41%) |      830.85 ms →      740.38 ms  (-10.89%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |       10.05 ms →        9.99 ms   (-0.59%) |      27   →      25     (-7.41%) |      271.26 ms →      249.68 ms   (-7.96%) | 
  │ │ └ sirius::Density::get_magnetisation                              |      112.32 μs →      112.00 μs   (-0.28%) |      27   →      25     (-7.41%) |        3.03 ms →        2.80 ms   (-7.67%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |      106.39 μs →      107.00 μs   (+0.58%) |      27   →      25     (-7.41%) |        2.87 ms →        2.68 ms   (-6.87%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.16 ms →        5.04 ms   (-2.44%) |       2   →       2              |       10.33 ms →       10.08 ms   (-2.44%) | 
  │ ├ sirius::Periodic_function|inner                                   |        9.87 ms →       10.13 ms   (+2.63%) |       6   →       6              |       59.21 ms →       60.76 ms   (+2.63%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        9.83 ms →       10.07 ms   (+2.41%) |       6   →       6              |       58.99 ms →       60.41 ms   (+2.41%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        9.83 ms →       10.07 ms   (+2.41%) |       6   →       6              |       58.99 ms →       60.41 ms   (+2.41%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.29 ms →        9.71 ms   (-5.62%) |       3   →       3              |       30.86 ms →       29.13 ms   (-5.62%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.26 ms →        9.69 ms   (-5.55%) |       3   →       3              |       30.79 ms →       29.08 ms   (-5.55%) | 
  ├ sirius::Periodic_function|inner                                     |       10.10 ms →       10.18 ms   (+0.83%) |       2   →       2              |       20.20 ms →       20.37 ms   (+0.83%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.09 ms →       10.18 ms   (+0.84%) |       2   →       2              |       20.19 ms →       20.36 ms   (+0.84%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.09 ms →       10.18 ms   (+0.84%) |       2   →       2              |       20.19 ms →       20.36 ms   (+0.84%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.53 ms →        9.73 ms   (-7.57%) |       1   →       1              |       10.53 ms →        9.73 ms   (-7.57%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.52 ms →        9.72 ms   (-7.60%) |       1   →       1              |       10.52 ms →        9.72 ms   (-7.60%) | 
  └ sirius::finalize                                                    |      316.37 ms →      329.34 ms   (+4.10%) |       1   →       1              |      316.37 ms →      329.34 ms   (+4.10%) | 
  ====================================================================================================================================================================================================
```
