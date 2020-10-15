# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      240.10 s  →      235.00 s    (-2.13%) |       1   →       1              |      240.10 s  →      235.00 s    (-2.13%) | 
  ├ sirius::initialize                                                  |        2.77 s  →        2.69 s    (-2.95%) |       1   →       1              |        2.77 s  →        2.69 s    (-2.95%) | 
  ├ sirius::Simulation_context::initialize                              |        2.97 s  →        3.01 s    (+1.06%) |       1   →       1              |        2.97 s  →        3.01 s    (+1.06%) | 
- │ ├ sirius::Simulation_context::init_comm                             |       45.83 ms →       74.73 ms  (+63.06%) |       1   →       1              |       45.83 ms →       74.73 ms  (+63.06%) | 
  │ ├ sirius::Unit_cell::initialize                                     |      172.87 ms →      182.76 ms   (+5.72%) |       1   →       1              |      172.87 ms →      182.76 ms   (+5.72%) | 
  │ │ ├ sirius::Atom_type::init                                         |       74.81 ms →       79.16 ms   (+5.82%) |       2   →       2              |      149.62 ms →      158.33 ms   (+5.82%) | 
  │ │ └ sirius::Unit_cell::update                                       |       23.18 ms →       24.35 ms   (+5.07%) |       1   →       1              |       23.18 ms →       24.35 ms   (+5.07%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.30 ms →        6.40 ms   (+1.67%) |       1   →       1              |        6.30 ms →        6.40 ms   (+1.67%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       16.83 ms →       17.91 ms   (+6.42%) |       1   →       1              |       16.83 ms →       17.91 ms   (+6.42%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       16.81 ms →       17.88 ms   (+6.33%) |       1   →       1              |       16.81 ms →       17.88 ms   (+6.33%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.16 ms →        4.16 ms   (+0.03%) |       1   →       1              |        4.16 ms →        4.16 ms   (+0.03%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.34 ms →        2.34 ms   (+0.11%) |       1   →       1              |        2.34 ms →        2.34 ms   (+0.11%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      101.29 μs →      106.64 μs   (+5.28%) |       1   →       1              |      101.29 μs →      106.64 μs   (+5.28%) | 
  │ └ sirius::Simulation_context::update                                |        2.70 s  →        2.70 s    (+0.03%) |       1   →       1              |        2.70 s  →        2.70 s    (+0.03%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.83 ms →       10.58 ms   (-2.26%) |       1   →       1              |       10.83 ms →       10.58 ms   (-2.26%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.43 ms →        4.23 ms   (-4.54%) |       1   →       1              |        4.43 ms →        4.23 ms   (-4.54%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.36 ms →        6.32 ms   (-0.67%) |       1   →       1              |        6.36 ms →        6.32 ms   (-0.67%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.34 ms →        6.30 ms   (-0.64%) |       1   →       1              |        6.34 ms →        6.30 ms   (-0.64%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.83 ms →        3.82 ms   (-0.32%) |       1   →       1              |        3.83 ms →        3.82 ms   (-0.32%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.34 ms →        2.31 ms   (-1.27%) |       1   →       1              |        2.34 ms →        2.31 ms   (-1.27%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      100.79 μs →      102.07 μs   (+1.27%) |       1   →       1              |      100.79 μs →      102.07 μs   (+1.27%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       62.67 ms →       62.56 ms   (-0.18%) |       2   →       2              |      125.34 ms →      125.12 ms   (-0.18%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.16 ms →        5.15 ms   (-0.20%) |       2   →       2              |       10.33 ms →       10.31 ms   (-0.20%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.48 ms →        4.48 ms   (+0.13%) |       1   →       1              |        4.48 ms →        4.48 ms   (+0.13%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.73 ms →       21.75 ms   (+0.06%) |       2   →       2              |       43.47 ms →       43.49 ms   (+0.06%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.82 ms →       14.82 ms   (+0.01%) |       2   →       2              |       29.63 ms →       29.64 ms   (+0.01%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.80 ms →       19.80 ms   (+0.01%) |       4   →       4              |       79.18 ms →       79.19 ms   (+0.01%) | 
  │   ├ sddk::Gvec::init                                                |      171.71 ms →      171.18 ms   (-0.31%) |       2   →       2              |      343.42 ms →      342.36 ms   (-0.31%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      129.22 ms →      128.46 ms   (-0.59%) |       2   →       2              |      258.44 ms →      256.92 ms   (-0.59%) | 
  │   ├ sddk::Gvec_shells                                               |      177.56 ms →      162.34 ms   (-8.57%) |       1   →       1              |      177.56 ms →      162.34 ms   (-8.57%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.31 ms →        1.32 ms   (+0.44%) |       1   →       1              |        1.31 ms →        1.32 ms   (+0.44%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      295.33 ms →      296.64 ms   (+0.45%) |       2   →       2              |      590.65 ms →      593.29 ms   (+0.45%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       76.02 ms →       78.01 ms   (+2.61%) |       1   →       1              |       76.02 ms →       78.01 ms   (+2.61%) | 
+ │ ├ sirius::K_point::K_point                                          |        2.70 μs →        2.20 μs  (-18.59%) |       4   →       4              |       10.79 μs →        8.79 μs  (-18.59%) | 
  │ └ sirius::K_point_set::initialize                                   |       75.92 ms →       77.91 ms   (+2.61%) |       1   →       1              |       75.92 ms →       77.91 ms   (+2.61%) | 
  │   └ sirius::K_point::initialize                                     |       18.97 ms →       19.46 ms   (+2.56%) |       4   →       4              |       75.88 ms →       77.82 ms   (+2.56%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       14.42 ms →       14.84 ms   (+2.89%) |       4   →       4              |       57.68 ms →       59.35 ms   (+2.89%) | 
  │     │ └ sddk::Gvec::init                                            |        3.86 ms →        3.91 ms   (+1.14%) |       4   →       4              |       15.45 ms →       15.63 ms   (+1.14%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        8.89 μs →        8.60 μs   (-3.29%) |       4   →       4              |       35.58 μs →       34.41 μs   (-3.29%) | 
  │     └ sirius::K_point::update                                       |        3.26 ms →        3.30 ms   (+1.21%) |       4   →       4              |       13.02 ms →       13.18 ms   (+1.21%) | 
  │       └ sirius::Beta_projectors                                     |        1.76 ms →        1.76 ms   (+0.16%) |       4   →       4              |        7.04 ms →        7.05 ms   (+0.16%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      936.07 μs →      927.41 μs   (-0.92%) |       4   →       4              |        3.74 ms →        3.71 ms   (-0.92%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.18 ms →        5.46 ms   (+5.44%) |       2   →       2              |       10.36 ms →       10.92 ms   (+5.44%) | 
  ├ sirius::Potential                                                   |      163.89 ms →      158.45 ms   (-3.32%) |       1   →       1              |      163.89 ms →      158.45 ms   (-3.32%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.77 ms →        5.77 ms   (-0.06%) |       6   →       6              |       34.61 ms →       34.59 ms   (-0.06%) | 
  │ └ sirius::Potential::update                                         |      128.56 ms →      123.16 ms   (-4.20%) |       1   →       1              |      128.56 ms →      123.16 ms   (-4.20%) | 
  │   └ sirius::Potential::generate_local_potential                     |      127.86 ms →      122.44 ms   (-4.24%) |       1   →       1              |      127.86 ms →      122.44 ms   (-4.24%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      110.85 ms →      114.70 ms   (+3.47%) |       1   →       1              |      110.85 ms →      114.70 ms   (+3.47%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       16.15 ms →        6.83 ms  (-57.72%) |       1   →       1              |       16.15 ms →        6.83 ms  (-57.72%) | 
  ├ sirius::Density                                                     |      136.71 ms →      134.84 ms   (-1.37%) |       1   →       1              |      136.71 ms →      134.84 ms   (-1.37%) | 
- │ ├ sirius::Smooth_periodic_function                                  |        5.09 ms →        5.66 ms  (+11.25%) |       2   →       2              |       10.17 ms →       11.32 ms  (+11.25%) | 
  │ └ sirius::Density::update                                           |      126.26 ms →      123.22 ms   (-2.41%) |       1   →       1              |      126.26 ms →      123.22 ms   (-2.41%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      125.83 ms →      122.75 ms   (-2.45%) |       1   →       1              |      125.83 ms →      122.75 ms   (-2.45%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |      115.81 μs →      118.42 μs   (+2.25%) |       1   →       1              |      115.81 μs →      118.42 μs   (+2.25%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      112.04 ms →      116.76 ms   (+4.22%) |       1   →       1              |      112.04 ms →      116.76 ms   (+4.22%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       13.23 ms →        5.32 ms  (-59.83%) |       1   →       1              |       13.23 ms →        5.32 ms  (-59.83%) | 
  ├ sirius::Density::initial_density                                    |      176.47 ms →      181.57 ms   (+2.89%) |       1   →       1              |      176.47 ms →      181.57 ms   (+2.89%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      111.52 ms →      119.81 ms   (+7.43%) |       1   →       1              |      111.52 ms →      119.81 ms   (+7.43%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |       11.35 ms →        6.60 ms  (-41.82%) |       2   →       2              |       22.70 ms →       13.20 ms  (-41.82%) | 
- │ └ sirius::Periodic_function::integrate                              |       10.10 ms →       12.61 ms  (+24.87%) |       1   →       1              |       10.10 ms →       12.61 ms  (+24.87%) | 
  ├ sirius::Potential::generate                                         |      593.69 ms →      603.13 ms   (+1.59%) |       1   →       1              |      593.69 ms →      603.13 ms   (+1.59%) | 
  │ ├ sirius::Potential::poisson                                        |      137.96 ms →      139.63 ms   (+1.21%) |       1   →       1              |      137.96 ms →      139.63 ms   (+1.21%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       18.95 ms →        7.77 ms  (-59.01%) |       1   →       1              |       18.95 ms →        7.77 ms  (-59.01%) | 
- │ │ └ sirius::Periodic_function|inner                                 |        9.90 ms →       11.21 ms  (+13.20%) |       1   →       1              |        9.90 ms →       11.21 ms  (+13.20%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        9.88 ms →        9.94 ms   (+0.55%) |       1   →       1              |        9.88 ms →        9.94 ms   (+0.55%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.88 ms →        9.94 ms   (+0.55%) |       1   →       1              |        9.88 ms →        9.94 ms   (+0.55%) | 
  │ ├ sirius::Periodic_function::add                                    |      553.85 μs →      549.86 μs   (-0.72%) |       2   →       2              |        1.11 ms →        1.10 ms   (-0.72%) | 
- │ ├ sirius::Potential::xc                                             |       53.65 ms →       61.03 ms  (+13.74%) |       1   →       1              |       53.65 ms →       61.03 ms  (+13.74%) | 
- │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.36 ms →       58.75 ms  (+14.39%) |       1   →       1              |       51.36 ms →       58.75 ms  (+14.39%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.63 ms →        5.72 ms   (+1.57%) |       2   →       2              |       11.26 ms →       11.44 ms   (+1.57%) | 
- │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.31 ms →       10.41 ms  (+96.21%) |       1   →       1              |        5.31 ms →       10.41 ms  (+96.21%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.71 ms →        6.31 ms  (+10.55%) |       1   →       1              |        5.71 ms →        6.31 ms  (+10.55%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       93.49 ms →       92.81 ms   (-0.73%) |       1   →       1              |       93.49 ms →       92.81 ms   (-0.73%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      300.43 ms →      300.93 ms   (+0.17%) |       1   →       1              |      300.43 ms →      300.93 ms   (+0.17%) | 
  ├ sirius::Hamiltonian0                                                |        8.33 ms →        8.40 ms   (+0.75%) |       1   →       1              |        8.33 ms →        8.40 ms   (+0.75%) | 
  │ ├ sirius::Local_operator                                            |        8.00 ms →        8.04 ms   (+0.60%) |       1   →       1              |        8.00 ms →        8.04 ms   (+0.60%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.76 ms →        4.70 ms   (-1.22%) |       1   →       1              |        4.76 ms →        4.70 ms   (-1.22%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.32 ms →        2.41 ms   (+3.84%) |       1   →       1              |        2.32 ms →        2.41 ms   (+3.84%) | 
  │ ├ sirius::Non_local_operator                                        |       62.70 μs →       62.90 μs   (+0.31%) |       2   →       2              |      125.40 μs →      125.80 μs   (+0.31%) | 
  │ ├ sirius::D_operator::initialize                                    |       90.25 μs →       96.44 μs   (+6.86%) |       1   →       1              |       90.25 μs →       96.44 μs   (+6.86%) | 
  │ └ sirius::Q_operator::initialize                                    |       69.48 μs →       71.15 μs   (+2.40%) |       1   →       1              |       69.48 μs →       71.15 μs   (+2.40%) | 
  ├ sirius::Band::initialize_subspace                                   |        3.11 s  →        3.13 s    (+0.68%) |       1   →       1              |        3.11 s  →        3.13 s    (+0.68%) | 
- │ ├ sirius::Hamiltonian_k                                             |      363.59 μs →      691.80 μs  (+90.27%) |       4   →       4              |        1.45 ms →        2.77 ms  (+90.27%) | 
- │ │ ├ sirius::Local_operator::prepare_k                               |      358.66 μs →      685.99 μs  (+91.27%) |       4   →       4              |        1.43 ms →        2.74 ms  (+91.27%) | 
- │ │ └ sirius::Beta_projectors_base::prepare                           |        3.26 μs →        3.90 μs  (+19.46%) |       4   →       4              |       13.04 μs →       15.58 μs  (+19.46%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |      777.55 ms →      782.50 ms   (+0.64%) |       4   →       4              |        3.11 s  →        3.13 s    (+0.64%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       33.46 ms →       32.02 ms   (-4.30%) |      16   →      16              |      535.40 ms →      512.36 ms   (-4.30%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       14.48 ms →       14.55 ms   (+0.44%) |       4   →       4              |       57.92 ms →       58.18 ms   (+0.44%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        5.44 ms →        5.36 ms   (-1.50%) |       4   →       4              |       21.76 ms →       21.43 ms   (-1.50%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      356.17 ms →      358.37 ms   (+0.62%) |       4   →       4              |        1.42 s  →        1.43 s    (+0.62%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      259.92 ms →      260.96 ms   (+0.40%) |       4   →       4              |        1.04 s  →        1.04 s    (+0.40%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       64.81 ms →       65.86 ms   (+1.62%) |       4   →       4              |      259.24 ms →      263.43 ms   (+1.62%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       17.26 ms →       16.14 ms   (-6.53%) |       4   →       4              |       69.06 ms →       64.55 ms   (-6.53%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       17.26 ms →       16.14 ms   (-6.53%) |       4   →       4              |       69.05 ms →       64.54 ms   (-6.53%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       41.12 ms →       43.39 ms   (+5.52%) |       4   →       4              |      164.50 ms →      173.57 ms   (+5.52%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |       16.72 ms →       16.01 ms   (-4.25%) |       4   →       4              |       66.89 ms →       64.04 ms   (-4.25%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |       16.72 ms →       16.01 ms   (-4.25%) |       4   →       4              |       66.87 ms →       64.03 ms   (-4.25%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |       53.38 ms →       53.44 ms   (+0.12%) |       4   →       4              |      213.52 ms →      213.78 ms   (+0.12%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |       35.40 ms →       35.46 ms   (+0.17%) |       4   →       4              |      141.59 ms →      141.83 ms   (+0.17%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        1.94 ms →        1.95 ms   (+0.48%) |       4   →       4              |        7.77 ms →        7.81 ms   (+0.48%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       40.09 ms →       41.15 ms   (+2.64%) |       4   →       4              |      160.35 ms →      164.59 ms   (+2.64%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |        6.99 ms →        8.06 ms  (+15.23%) |       4   →       4              |       27.97 ms →       32.23 ms  (+15.23%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       27.09 ms →       27.14 ms   (+0.17%) |       8   →       8              |      216.72 ms →      217.08 ms   (+0.17%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.78 ms →       14.99 ms   (+1.39%) |       8   →       8              |      118.27 ms →      119.91 ms   (+1.39%) | 
  │ │ │ └ sddk::wf_inner                                                |       14.74 ms →       14.95 ms   (+1.41%) |       8   →       8              |      117.91 ms →      119.58 ms   (+1.41%) | 
  │ │ │   ├ sddk::wf_inner|scale                                        |       27.88 ns →       28.13 ns   (+0.90%) |       8   →       8              |      223.00 ns →      225.00 ns   (+0.90%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       14.56 ms →       14.77 ms   (+1.46%) |       8   →       8              |      116.45 ms →      118.15 ms   (+1.46%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       21.63 ns →       40.25 ns  (+86.13%) |       8   →       8              |      173.00 ns →      322.00 ns  (+86.13%) | 
  │ │ ├ Eigensolver_scalapack|pzhegvx                                   |      118.79 ms →      125.99 ms   (+6.07%) |       4   →       4              |      475.15 ms →      503.98 ms   (+6.07%) | 
  │ │ └ sddk::wf_trans                                                  |       23.57 ms →       23.62 ms   (+0.20%) |       4   →       4              |       94.29 ms →       94.48 ms   (+0.20%) | 
  │ │   └ sddk::wf_trans|pw                                             |       23.40 ms →       23.47 ms   (+0.30%) |       4   →       4              |       93.59 ms →       93.87 ms   (+0.30%) | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      343.25 ns →      336.00 ns   (-2.11%) |       4   →       4              |        1.37 μs →        1.34 μs   (-2.11%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      229.24 s  →      224.09 s    (-2.24%) |       1   →       1              |      229.24 s  →      224.09 s    (-2.24%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.76 ms →        5.67 ms   (-1.44%) |      19   →      19              |      109.35 ms →      107.78 ms   (-1.44%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        8.80 s  →        8.29 s    (-5.86%) |      26   →      27     (+3.85%) |      228.82 s  →      223.71 s    (-2.23%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        4.51 ms →        4.66 ms   (+3.37%) |      26   →      27     (+3.85%) |      117.32 ms →      125.93 ms   (+7.34%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.15 ms →        4.31 ms   (+3.74%) |      26   →      27     (+3.85%) |      107.98 ms →      116.33 ms   (+7.73%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      966.37 μs →      953.99 μs   (-1.28%) |      26   →      27     (+3.85%) |       25.13 ms →       25.76 ms   (+2.52%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.30 ms →        2.47 ms   (+7.28%) |      26   →      27     (+3.85%) |       59.79 ms →       66.61 ms  (+11.41%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.96 μs →       64.79 μs   (-0.26%) |      52   →      54     (+3.85%) |        3.38 ms →        3.50 ms   (+3.58%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       94.32 μs →       94.20 μs   (-0.13%) |      26   →      27     (+3.85%) |        2.45 ms →        2.54 ms   (+3.71%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       65.97 μs →       65.41 μs   (-0.85%) |      26   →      27     (+3.85%) |        1.72 ms →        1.77 ms   (+2.96%) | 
  │ │ ├ sirius::Band::solve                                             |        6.70 s  →        6.18 s    (-7.69%) |      26   →      27     (+3.85%) |      174.14 s  →      166.93 s    (-4.14%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      332.87 μs →      322.57 μs   (-3.09%) |     104   →     108     (+3.85%) |       34.62 ms →       34.84 ms   (+0.63%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      327.22 μs →      317.36 μs   (-3.02%) |     104   →     108     (+3.85%) |       34.03 ms →       34.27 ms   (+0.72%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.14 μs →        3.73 μs   (-9.84%) |     104   →     108     (+3.85%) |      430.59 μs →      403.15 μs   (-6.37%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.67 s  →        1.55 s    (-7.69%) |     104   →     108     (+3.85%) |      174.10 s  →      166.89 s    (-4.14%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       11.87 ms →       11.90 ms   (+0.22%) |     104   →     108     (+3.85%) |        1.23 s  →        1.28 s    (+4.08%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |      660.62 ns →      671.24 ns   (+1.61%) |     624   →     648     (+3.85%) |      412.23 μs →      434.96 μs   (+5.51%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.83 ms →        1.83 ms   (-0.14%) |     104   →     108     (+3.85%) |      190.57 ms →      197.62 ms   (+3.70%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      352.98 μs →      354.91 μs   (+0.55%) |     104   →     108     (+3.85%) |       36.71 ms →       38.33 ms   (+4.42%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      550.74 μs →      549.71 μs   (-0.19%) |     208   →     216     (+3.85%) |      114.55 ms →      118.74 ms   (+3.65%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.65 s  →        1.52 s    (-7.80%) |     104   →     108     (+3.85%) |      171.74 s  →      164.43 s    (-4.25%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       69.83 ms →       67.81 ms   (-2.90%) |     904   →     970     (+7.30%) |       63.13 s  →       65.78 s    (+4.19%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       44.70 ms →       43.03 ms   (-3.74%) |     904   →     970     (+7.30%) |       40.41 s  →       41.74 s    (+3.29%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        8.67 ms →        8.47 ms   (-2.29%) |     904   →     970     (+7.30%) |        7.83 s  →        8.21 s    (+4.84%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      230.38 μs →      216.64 μs   (-5.96%) |     904   →     970     (+7.30%) |      208.26 ms →      210.14 ms   (+0.90%) | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        1.99 ms →        1.93 ms   (-2.87%) |     104   →     108     (+3.85%) |      206.48 ms →      208.28 ms   (+0.87%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |        6.85 ms →        6.53 ms   (-4.58%) |     904   →     970     (+7.30%) |        6.19 s  →        6.34 s    (+2.38%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |       89.25 μs →       82.91 μs   (-7.10%) |     904   →     970     (+7.30%) |       80.68 ms →       80.43 ms   (-0.31%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |      752.71 μs →      721.69 μs   (-4.12%) |     104   →     108     (+3.85%) |       78.28 ms →       77.94 ms   (-0.43%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |        9.84 ms →        9.35 ms   (-5.03%) |     904   →     970     (+7.30%) |        8.90 s  →        9.06 s    (+1.91%) | 
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |        6.18 ms →        5.83 ms   (-5.74%) |     904   →     970     (+7.30%) |        5.59 s  →        5.65 s    (+1.14%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        1.52 ms →        1.52 ms   (-0.01%) |     904   →     970     (+7.30%) |        1.37 s  →        1.48 s    (+7.29%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        8.65 ms →        8.59 ms   (-0.71%) |     904   →     970     (+7.30%) |        7.82 s  →        8.33 s    (+6.54%) | 
- │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        1.24 ms →        1.41 ms  (+14.20%) |     904   →     970     (+7.30%) |        1.12 s  →        1.37 s   (+22.54%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.47 ms →        7.32 ms   (-1.94%) |    1.81 K →    1.94 K   (+7.30%) |       13.50 s  →       14.21 s    (+5.21%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       28.01 ms →       27.26 ms   (-2.71%) |     904   →     970     (+7.30%) |       25.32 s  →       26.44 s    (+4.40%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        2.03 ms →        2.03 ms   (-0.09%) |    1.70 K →    1.83 K   (+7.51%) |        3.47 s  →        3.72 s    (+7.41%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       83.56 ns →       61.82 ns  (-26.02%) |    1.70 K →    1.83 K   (+7.51%) |      142.38 μs →      113.25 μs  (-20.46%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        2.03 ms →        2.02 ms   (-0.35%) |    1.70 K →    1.83 K   (+7.51%) |        3.45 s  →        3.70 s    (+7.14%) | 
+ │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       62.29 ns →       48.20 ns  (-22.63%) |    1.70 K →    1.83 K   (+7.51%) |      106.14 μs →       88.30 μs  (-16.81%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|potrf                               |      831.65 μs →      789.73 μs   (-5.04%) |     904   →     970     (+7.30%) |      751.81 ms →      766.04 ms   (+1.89%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|trtri                               |      771.03 μs →      787.84 μs   (+2.18%) |     904   →     970     (+7.30%) |      697.01 ms →      764.20 ms   (+9.64%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |        5.40 ms →        5.22 ms   (-3.32%) |    3.51 K →    3.77 K   (+7.40%) |       18.96 s  →       19.69 s    (+3.84%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        3.67 ms →        3.55 ms   (-3.25%) |    5.11 K →    5.50 K   (+7.51%) |       18.74 s  →       19.50 s    (+4.02%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        5.44 ms →        5.36 ms   (-1.55%) |     904   →     970     (+7.30%) |        4.92 s  →        5.20 s    (+5.63%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |        3.69 ms →        3.60 ms   (-2.27%) |     904   →     970     (+7.30%) |        3.33 s  →        3.50 s    (+4.86%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       54.85 ns →       42.77 ns  (-22.03%) |     904   →     970     (+7.30%) |       49.58 μs →       41.48 μs  (-16.33%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        3.67 ms →        3.59 ms   (-2.31%) |     904   →     970     (+7.30%) |        3.32 s  →        3.48 s    (+4.82%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       56.27 ns →       65.24 ns  (+15.95%) |     904   →     970     (+7.30%) |       50.87 μs →       63.28 μs  (+24.41%) | 
+ │ │ │ │   ├ Eigensolver_scalapack|pzheevx                             |       64.12 ms →       45.52 ms  (-29.01%) |     904   →     970     (+7.30%) |       57.97 s  →       44.16 s   (-23.83%) | 
  │ │ │ │   ├ sirius::residuals                                         |       10.91 ms →       10.82 ms   (-0.75%) |     884   →     940     (+6.33%) |        9.64 s  →       10.17 s    (+5.54%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       10.56 ms →       10.34 ms   (-2.04%) |     838   →     901     (+7.52%) |        8.85 s  →        9.32 s    (+5.33%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        5.25 ms →        5.13 ms   (-2.30%) |    1.68 K →    1.80 K   (+7.52%) |        8.80 s  →        9.24 s    (+5.04%) | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      645.28 μs →      667.04 μs   (+3.37%) |     838   →     901     (+7.52%) |      540.74 ms →      601.01 ms  (+11.14%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       51.31 ms →       44.12 ms  (-14.01%) |     209   →     287    (+37.32%) |       10.72 s  →       12.66 s   (+18.08%) | 
- │ │ │ │     └ sddk::wf_trans                                          |       34.05 ms →       27.05 ms  (-20.54%) |     314   →     466    (+48.41%) |       10.69 s  →       12.61 s   (+17.93%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |       25.36 ms →       19.42 ms  (-23.43%) |     419   →     645    (+53.94%) |       10.63 s  →       12.52 s   (+17.86%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      622.45 ns →      477.06 ns  (-23.36%) |     104   →     108     (+3.85%) |       64.73 μs →       51.52 μs  (-20.41%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       21.57 μs →       21.62 μs   (+0.24%) |      26   →      27     (+3.85%) |      560.78 μs →      583.72 μs   (+4.09%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      593.08 μs →      601.32 μs   (+1.39%) |      26   →      27     (+3.85%) |       15.42 ms →       16.24 ms   (+5.29%) | 
  │ │ ├ sirius::Density::generate                                       |      896.77 ms →      902.59 ms   (+0.65%) |      26   →      27     (+3.85%) |       23.32 s  →       24.37 s    (+4.52%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      523.78 ms →      525.63 ms   (+0.35%) |      26   →      27     (+3.85%) |       13.62 s  →       14.19 s    (+4.21%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       24.63 ms →       24.44 ms   (-0.76%) |     104   →     108     (+3.85%) |        2.56 s  →        2.64 s    (+3.06%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |        8.47 μs →        8.88 μs   (+4.87%) |     104   →     108     (+3.85%) |      880.62 μs →      958.99 μs   (+8.90%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       15.35 μs →       16.70 μs   (+8.79%) |       8   →       8              |      122.77 μs →      133.56 μs   (+8.79%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       20.46 ms →       20.31 ms   (-0.74%) |     104   →     108     (+3.85%) |        2.13 s  →        2.19 s    (+3.07%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       29.63 ms →       30.11 ms   (+1.63%) |     104   →     108     (+3.85%) |        3.08 s  →        3.25 s    (+5.54%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.56 μs →        9.49 μs   (-0.79%) |     104   →     108     (+3.85%) |      994.36 μs →        1.02 ms   (+3.03%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        1.46 ms →        1.45 ms   (-0.24%) |     104   →     108     (+3.85%) |      151.48 ms →      156.93 ms   (+3.60%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       27.69 ms →       28.17 ms   (+1.75%) |     104   →     108     (+3.85%) |        2.88 s  →        3.04 s    (+5.66%) | 
- │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        3.58 ms →        4.05 ms  (+13.13%) |     104   →     108     (+3.85%) |      371.89 ms →      436.89 ms  (+17.48%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      583.66 ns →      632.33 ns   (+8.34%) |     104   →     108     (+3.85%) |       60.70 μs →       68.29 μs  (+12.51%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       42.46 ms →       42.59 ms   (+0.31%) |     104   →     108     (+3.85%) |        4.42 s  →        4.60 s    (+4.16%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.63 ms   (-0.33%) |      26   →      27     (+3.85%) |       42.62 ms →       44.12 ms   (+3.51%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.88 ms →       88.84 ms   (-0.05%) |      26   →      27     (+3.85%) |        2.31 s  →        2.40 s    (+3.80%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.65 ms →       88.61 ms   (-0.04%) |      26   →      27     (+3.85%) |        2.30 s  →        2.39 s    (+3.80%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      280.55 ms →      274.36 ms   (-2.21%) |      26   →      27     (+3.85%) |        7.29 s  →        7.41 s    (+1.55%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      280.55 ms →      274.36 ms   (-2.21%) |      26   →      27     (+3.85%) |        7.29 s  →        7.41 s    (+1.55%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.80 ms →       24.62 ms   (-0.73%) |      26   →      27     (+3.85%) |      644.80 ms →      664.74 ms   (+3.09%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      230.04 ms →      223.30 ms   (-2.93%) |      26   →      27     (+3.85%) |        5.98 s  →        6.03 s    (+0.80%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       23.93 ms →       24.64 ms   (+2.95%) |      26   →      27     (+3.85%) |      622.16 ms →      665.16 ms   (+6.91%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       82.14 ms →       81.02 ms   (-1.36%) |      26   →      27     (+3.85%) |        2.14 s  →        2.19 s    (+2.43%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        6.71 ms →       17.99 ms (+168.02%) |      26   →      27     (+3.85%) |      174.54 ms →      485.80 ms (+178.33%) | 
  │ │ ├ sirius::Density::mix                                            |      218.94 ms →      216.04 ms   (-1.33%) |      26   →      27     (+3.85%) |        5.69 s  →        5.83 s    (+2.47%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      957.44 μs →      955.52 μs   (-0.20%) |      26   →      27     (+3.85%) |       24.89 ms →       25.80 ms   (+3.64%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.75 ms →       10.35 ms   (-3.67%) |     334   →     349     (+4.49%) |        3.59 s  →        3.61 s    (+0.66%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.36 ms →        9.94 ms   (-4.09%) |     334   →     349     (+4.49%) |        3.46 s  →        3.47 s    (+0.22%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.36 ms →        9.94 ms   (-4.09%) |     334   →     349     (+4.49%) |        3.46 s  →        3.47 s    (+0.22%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        6.25 ms →        6.35 ms   (+1.64%) |      26   →      27     (+3.85%) |      162.47 ms →      171.48 ms   (+5.55%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.40 ms →        5.51 ms   (+2.10%) |      26   →      27     (+3.85%) |      140.36 ms →      148.82 ms   (+6.03%) | 
  │ │ ├ sirius::Potential::generate                                     |      580.07 ms →      579.36 ms   (-0.12%) |      26   →      27     (+3.85%) |       15.08 s  →       15.64 s    (+3.72%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      138.14 ms →      137.24 ms   (-0.65%) |      26   →      27     (+3.85%) |        3.59 s  →        3.71 s    (+3.17%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       18.36 ms →        5.27 ms  (-71.28%) |      26   →      27     (+3.85%) |      477.44 ms →      142.39 ms  (-70.18%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.34 ms →       10.30 ms   (-0.40%) |      26   →      27     (+3.85%) |      268.94 ms →      278.18 ms   (+3.44%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        9.95 ms →        9.96 ms   (+0.18%) |      26   →      27     (+3.85%) |      258.58 ms →      269.02 ms   (+4.04%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        9.94 ms →        9.96 ms   (+0.18%) |      26   →      27     (+3.85%) |      258.57 ms →      269.00 ms   (+4.03%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      555.95 μs →      553.56 μs   (-0.43%) |      52   →      54     (+3.85%) |       28.91 ms →       29.89 ms   (+3.40%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       49.07 ms →       49.15 ms   (+0.17%) |      26   →      27     (+3.85%) |        1.28 s  →        1.33 s    (+4.02%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.73 ms →       46.84 ms   (+0.23%) |      26   →      27     (+3.85%) |        1.22 s  →        1.26 s    (+4.09%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.02 ms →        3.00 ms   (-0.59%) |      52   →      54     (+3.85%) |      157.01 ms →      162.08 ms   (+3.23%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.24 ms →        5.38 ms   (+2.59%) |      26   →      27     (+3.85%) |      136.29 ms →      145.19 ms   (+6.53%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.63 ms →        6.71 ms   (+1.23%) |      26   →      27     (+3.85%) |      172.38 ms →      181.22 ms   (+5.13%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.91 ms →       90.96 ms   (+0.05%) |      26   →      27     (+3.85%) |        2.36 s  →        2.46 s    (+3.90%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      292.90 ms →      292.93 ms   (+0.01%) |      26   →      27     (+3.85%) |        7.62 s  →        7.91 s    (+3.86%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      280.02 ms →      279.68 ms   (-0.12%) |      26   →      27     (+3.85%) |        7.28 s  →        7.55 s    (+3.72%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      280.01 ms →      279.68 ms   (-0.12%) |      26   →      27     (+3.85%) |        7.28 s  →        7.55 s    (+3.72%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.19 ms →       27.27 ms   (+0.27%) |      26   →      27     (+3.85%) |      707.01 ms →      736.22 ms   (+4.13%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      224.61 ms →      224.55 ms   (-0.03%) |      26   →      27     (+3.85%) |        5.84 s  →        6.06 s    (+3.82%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       24.42 ms →       24.06 ms   (-1.45%) |      26   →      27     (+3.85%) |      634.85 ms →      649.71 ms   (+2.34%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.60 ms →        5.42 ms   (-3.12%) |      26   →      27     (+3.85%) |      145.48 ms →      146.36 ms   (+0.60%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.45 ms →       10.32 ms   (-1.18%) |     182   →     189     (+3.85%) |        1.90 s  →        1.95 s    (+2.62%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.80 ms →        9.93 ms   (+1.37%) |     182   →     189     (+3.85%) |        1.78 s  →        1.88 s    (+5.26%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.80 ms →        9.93 ms   (+1.36%) |     182   →     189     (+3.85%) |        1.78 s  →        1.88 s    (+5.26%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       11.08 ms →       10.64 ms   (-3.95%) |      78   →      81     (+3.85%) |      863.90 ms →      861.70 ms   (-0.25%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.60 ms →       10.26 ms   (-3.13%) |      78   →      81     (+3.85%) |      826.49 ms →      831.44 ms   (+0.60%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |       10.02 ms →        9.98 ms   (-0.36%) |      26   →      27     (+3.85%) |      260.53 ms →      269.57 ms   (+3.47%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      110.40 μs →      156.03 μs  (+41.33%) |      26   →      27     (+3.85%) |        2.87 ms →        4.21 ms  (+46.77%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      105.35 μs →      150.81 μs  (+43.15%) |      26   →      27     (+3.85%) |        2.74 ms →        4.07 ms  (+48.66%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.14 ms →        5.27 ms   (+2.43%) |       2   →       2              |       10.29 ms →       10.54 ms   (+2.43%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.09 ms →       10.01 ms   (-0.81%) |       6   →       6              |       60.55 ms →       60.06 ms   (-0.81%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        9.70 ms →       10.00 ms   (+3.10%) |       6   →       6              |       58.20 ms →       60.01 ms   (+3.10%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        9.70 ms →       10.00 ms   (+3.10%) |       6   →       6              |       58.20 ms →       60.00 ms   (+3.10%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.87 ms →       10.41 ms   (-4.21%) |       3   →       3              |       32.61 ms →       31.24 ms   (-4.21%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.51 ms →       10.40 ms   (-0.96%) |       3   →       3              |       31.52 ms →       31.21 ms   (-0.96%) | 
  ├ sirius::Periodic_function|inner                                     |       10.10 ms →        9.99 ms   (-1.14%) |       2   →       2              |       20.21 ms →       19.98 ms   (-1.14%) | 
  │ └ sirius::Periodic_function|inner_local                             |        9.68 ms →        9.98 ms   (+3.15%) |       2   →       2              |       19.35 ms →       19.96 ms   (+3.15%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.68 ms →        9.98 ms   (+3.15%) |       2   →       2              |       19.35 ms →       19.96 ms   (+3.15%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.90 ms →       10.45 ms   (-4.09%) |       1   →       1              |       10.90 ms →       10.45 ms   (-4.09%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.61 ms →       10.44 ms   (-1.56%) |       1   →       1              |       10.61 ms →       10.44 ms   (-1.56%) | 
  └ sirius::finalize                                                    |      314.74 ms →      335.35 ms   (+6.55%) |       1   →       1              |      314.74 ms →      335.35 ms   (+6.55%) | 
  ====================================================================================================================================================================================================
```
