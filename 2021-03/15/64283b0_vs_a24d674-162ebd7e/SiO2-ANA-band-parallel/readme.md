# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs 64283b0bdde21ce92493e897e38c4105358cbbe3
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      804.44 s  →      301.41 s   (-62.53%) |       1   →       1              |      804.44 s  →      301.41 s   (-62.53%) | 
  ├ sirius::initialize                                                  |        2.76 s  →        2.74 s    (-0.58%) |       1   →       1              |        2.76 s  →        2.74 s    (-0.58%) | 
  ├ sirius::Simulation_context::initialize                              |        2.91 s  →        2.92 s    (+0.35%) |       1   →       1              |        2.91 s  →        2.92 s    (+0.35%) | 
- │ ├ sirius::Simulation_context::init_comm                             |      205.72 μs →      227.42 μs  (+10.55%) |       1   →       1              |      205.72 μs →      227.42 μs  (+10.55%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      136.30 ms →      167.05 ms  (+22.56%) |       1   →       1              |      136.30 ms →      167.05 ms  (+22.56%) | 
- │ │ ├ sirius::Atom_type::init                                         |       56.23 ms →       71.35 ms  (+26.90%) |       2   →       2              |      112.46 ms →      142.71 ms  (+26.90%) | 
  │ │ └ sirius::Unit_cell::update                                       |       23.77 ms →       24.16 ms   (+1.66%) |       1   →       1              |       23.77 ms →       24.16 ms   (+1.66%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.35 ms →        6.27 ms   (-1.22%) |       1   →       1              |        6.35 ms →        6.27 ms   (-1.22%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       17.38 ms →       17.85 ms   (+2.69%) |       1   →       1              |       17.38 ms →       17.85 ms   (+2.69%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       17.36 ms →       17.82 ms   (+2.67%) |       1   →       1              |       17.36 ms →       17.82 ms   (+2.67%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        5.26 ms →        5.19 ms   (-1.18%) |       1   →       1              |        5.26 ms →        5.19 ms   (-1.18%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.35 ms →        2.33 ms   (-0.69%) |       1   →       1              |        2.35 ms →        2.33 ms   (-0.69%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      104.91 μs →      104.27 μs   (-0.61%) |       1   →       1              |      104.91 μs →      104.27 μs   (-0.61%) | 
  │ └ sirius::Simulation_context::update                                |        2.73 s  →        2.71 s    (-0.98%) |       1   →       1              |        2.73 s  →        2.71 s    (-0.98%) | 
  │   ├ sirius::Unit_cell::update                                       |       11.97 ms →       11.85 ms   (-0.96%) |       1   →       1              |       11.97 ms →       11.85 ms   (-0.96%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.45 ms →        4.50 ms   (+1.10%) |       1   →       1              |        4.45 ms →        4.50 ms   (+1.10%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        7.48 ms →        7.32 ms   (-2.20%) |       1   →       1              |        7.48 ms →        7.32 ms   (-2.20%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        7.46 ms →        7.29 ms   (-2.26%) |       1   →       1              |        7.46 ms →        7.29 ms   (-2.26%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        4.96 ms →        4.80 ms   (-3.35%) |       1   →       1              |        4.96 ms →        4.80 ms   (-3.35%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.33 ms   (+0.01%) |       1   →       1              |        2.33 ms →        2.33 ms   (+0.01%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      102.86 μs →       99.84 μs   (-2.94%) |       1   →       1              |      102.86 μs →       99.84 μs   (-2.94%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       66.37 ms →       64.67 ms   (-2.57%) |       2   →       2              |      132.75 ms →      129.33 ms   (-2.57%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.13 ms →        5.14 ms   (+0.19%) |       2   →       2              |       10.27 ms →       10.29 ms   (+0.19%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.58 ms →        4.46 ms   (-2.58%) |       1   →       1              |        4.58 ms →        4.46 ms   (-2.58%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.75 ms →       21.81 ms   (+0.27%) |       2   →       2              |       43.50 ms →       43.62 ms   (+0.27%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.75 ms →       14.76 ms   (+0.08%) |       2   →       2              |       29.50 ms →       29.52 ms   (+0.08%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.90 ms →       19.94 ms   (+0.21%) |       4   →       4              |       79.60 ms →       79.76 ms   (+0.21%) | 
  │   ├ sddk::Gvec::init                                                |      173.45 ms →      173.68 ms   (+0.13%) |       2   →       2              |      346.89 ms →      347.35 ms   (+0.13%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      131.34 ms →      130.96 ms   (-0.29%) |       2   →       2              |      262.67 ms →      261.92 ms   (-0.29%) | 
  │   ├ sddk::Gvec_shells                                               |      169.26 ms →      164.61 ms   (-2.75%) |       1   →       1              |      169.26 ms →      164.61 ms   (-2.75%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.31 ms →        1.32 ms   (+0.59%) |       1   →       1              |        1.31 ms →        1.32 ms   (+0.59%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      292.77 ms →      292.08 ms   (-0.24%) |       2   →       2              |      585.55 ms →      584.15 ms   (-0.24%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       78.49 ms →       75.19 ms   (-4.20%) |       1   →       1              |       78.49 ms →       75.19 ms   (-4.20%) | 
- │ ├ sirius::K_point::K_point                                          |        3.10 μs →        6.83 μs (+120.27%) |       4   →       4              |       12.39 μs →       27.30 μs (+120.27%) | 
  │ └ sirius::K_point_set::initialize                                   |       78.37 ms →       75.04 ms   (-4.24%) |       1   →       1              |       78.37 ms →       75.04 ms   (-4.24%) | 
  │   └ sirius::K_point::initialize                                     |       19.58 ms →       18.75 ms   (-4.25%) |       4   →       4              |       78.32 ms →       75.00 ms   (-4.25%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       15.00 ms →       14.17 ms   (-5.56%) |       4   →       4              |       60.01 ms →       56.67 ms   (-5.56%) | 
  │     │ └ sddk::Gvec::init                                            |        3.83 ms →        3.87 ms   (+1.11%) |       4   →       4              |       15.32 ms →       15.49 ms   (+1.11%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        8.86 μs                             |       4                          |       35.44 μs                             | 
  │     └ sirius::K_point::update                                       |        3.27 ms →        3.28 ms   (+0.50%) |       4   →       4              |       13.06 ms →       13.13 ms   (+0.50%) | 
  │       └ sirius::Beta_projectors                                     |        1.76 ms →        1.77 ms   (+0.47%) |       4   →       4              |        7.03 ms →        7.07 ms   (+0.47%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      936.74 μs →      943.78 μs   (+0.75%) |       4   →       4              |        3.75 ms →        3.78 ms   (+0.75%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.20 ms                             |       2                          |       10.39 ms                             | 
  ├ sirius::Potential                                                   |      174.16 ms →      158.30 ms   (-9.11%) |       1   →       1              |      174.16 ms →      158.30 ms   (-9.11%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.77 ms                             |       6                          |       34.63 ms                             | 
  │ └ sirius::Potential::update                                         |      138.84 ms →      126.01 ms   (-9.24%) |       1   →       1              |      138.84 ms →      126.01 ms   (-9.24%) | 
  │   └ sirius::Potential::generate_local_potential                     |      138.14 ms →      125.27 ms   (-9.32%) |       1   →       1              |      138.14 ms →      125.27 ms   (-9.32%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      124.81 ms →      115.24 ms   (-7.67%) |       1   →       1              |      124.81 ms →      115.24 ms   (-7.67%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       12.79 ms →        5.35 ms  (-58.22%) |       1   →       1              |       12.79 ms →        5.35 ms  (-58.22%) | 
  ├ sirius::Density                                                     |      141.05 ms →      135.51 ms   (-3.93%) |       1   →       1              |      141.05 ms →      135.51 ms   (-3.93%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.05 ms                             |       2                          |       10.10 ms                             | 
  │ └ sirius::Density::update                                           |      130.68 ms →      125.11 ms   (-4.26%) |       1   →       1              |      130.68 ms →      125.11 ms   (-4.26%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      130.27 ms →      124.71 ms   (-4.27%) |       1   →       1              |      130.27 ms →      124.71 ms   (-4.27%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      123.72 ms →      117.28 ms   (-5.20%) |       1   →       1              |      123.72 ms →      117.28 ms   (-5.20%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        6.12 ms →        5.09 ms  (-16.80%) |       1   →       1              |        6.12 ms →        5.09 ms  (-16.80%) | 
  ├ sirius::Density::initial_density                                    |      179.76 ms →      168.95 ms   (-6.02%) |       1   →       1              |      179.76 ms →      168.95 ms   (-6.02%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      122.01 ms →      115.48 ms   (-5.35%) |       1   →       1              |      122.01 ms →      115.48 ms   (-5.35%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.74 ms →        5.17 ms   (-9.97%) |       2   →       2              |       11.48 ms →       10.33 ms   (-9.97%) | 
  │ └ sirius::Periodic_function::integrate                              |       10.86 ms →       10.19 ms   (-6.18%) |       1   →       1              |       10.86 ms →       10.19 ms   (-6.18%) | 
  ├ sirius::Potential::generate                                         |      699.81 ms →      684.84 ms   (-2.14%) |       1   →       1              |      699.81 ms →      684.84 ms   (-2.14%) | 
  │ ├ sirius::Potential::poisson                                        |      137.74 ms →      139.19 ms   (+1.05%) |       1   →       1              |      137.74 ms →      139.19 ms   (+1.05%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        6.66 ms →        6.19 ms   (-7.03%) |       1   →       1              |        6.66 ms →        6.19 ms   (-7.03%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.36 ms                             |       1                          |       10.36 ms                             | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |       10.30 ms                             |       1                          |       10.30 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |       10.30 ms                             |       1                          |       10.30 ms                             | 
  │ │ └ sirius::inner                                                   |                        11.62 ms            |                   1              |                        11.62 ms            | 
+ │ ├ sirius::Periodic_function::add                                    |      552.71 μs →      453.30 μs  (-17.99%) |       2   →       2              |        1.11 ms →      906.59 μs  (-17.99%) | 
+ │ ├ sirius::Potential::xc                                             |       58.09 ms →       39.80 ms  (-31.48%) |       1   →       1              |       58.09 ms →       39.80 ms  (-31.48%) | 
+ │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       58.08 ms →       37.51 ms  (-35.43%) |       1   →       1              |       58.08 ms →       37.51 ms  (-35.43%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.61 ms                             |       2                          |       11.21 ms                             | 
  │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        5.30 ms                             |       1                          |        5.30 ms                             | 
  │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                    |                        12.10 ms            |                   2              |                        24.20 ms            | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.85 ms →        4.92 ms  (-15.88%) |       1   →       1              |        5.85 ms →        4.92 ms  (-15.88%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.62 ms →       93.57 ms   (+1.02%) |       1   →       1              |       92.62 ms →       93.57 ms   (+1.02%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      403.07 ms →      402.52 ms   (-0.14%) |       1   →       1              |      403.07 ms →      402.52 ms   (-0.14%) | 
- ├ sirius::Hamiltonian0                                                |        8.39 ms →       11.86 ms  (+41.40%) |       1   →       1              |        8.39 ms →       11.86 ms  (+41.40%) | 
  │ ├ sirius::Local_operator                                            |        8.03 ms →        8.01 ms   (-0.17%) |       1   →       1              |        8.03 ms →        8.01 ms   (-0.17%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.74 ms                             |       1                          |        4.74 ms                             | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.36 ms →        2.42 ms   (+2.52%) |       1   →       1              |        2.36 ms →        2.42 ms   (+2.52%) | 
  │ ├ sirius::Non_local_operator                                        |       66.32 μs →       63.43 μs   (-4.36%) |       2   →       2              |      132.65 μs →      126.87 μs   (-4.36%) | 
- │ ├ sirius::D_operator::initialize                                    |       97.95 μs →        1.25 ms (+1175.02%) |       1   →       1              |       97.95 μs →        1.25 ms (+1175.02%) | 
- │ └ sirius::Q_operator::initialize                                    |       74.43 μs →        2.42 ms (+3145.19%) |       1   →       1              |       74.43 μs →        2.42 ms (+3145.19%) | 
  ├ sirius::Band::initialize_subspace                                   |        4.07 s  →        4.05 s    (-0.58%) |       1   →       1              |        4.07 s  →        4.05 s    (-0.58%) | 
- │ ├ sirius::Hamiltonian_k                                             |      205.93 μs →      402.21 μs  (+95.31%) |       4   →       4              |      823.73 μs →        1.61 ms  (+95.31%) | 
- │ │ ├ sirius::Local_operator::prepare_k                               |      200.46 μs →      394.79 μs  (+96.95%) |       4   →       4              |      801.82 μs →        1.58 ms  (+96.95%) | 
+ │ │ └ sirius::Beta_projectors_base::prepare                           |        3.93 μs →        3.26 μs  (-16.93%) |       4   →       4              |       15.72 μs →       13.05 μs  (-16.93%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.02 s  →        1.01 s    (-0.64%) |       4   →       4              |        4.07 s  →        4.04 s    (-0.64%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       34.58 ms                             |      16                          |      553.24 ms                             | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       14.61 ms →       14.67 ms   (+0.43%) |       4   →       4              |       58.42 ms →       58.67 ms   (+0.43%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        5.35 ms →        5.30 ms   (-0.76%) |       4   →       4              |       21.38 ms →       21.22 ms   (-0.76%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      355.15 ms →      351.35 ms   (-1.07%) |       4   →       4              |        1.42 s  →        1.41 s    (-1.07%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      258.24 ms →      254.50 ms   (-1.45%) |       4   →       4              |        1.03 s  →        1.02 s    (-1.45%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       64.14 ms →       61.16 ms   (-4.64%) |       4   →       4              |      256.55 ms →      244.65 ms   (-4.64%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       15.86 ms                             |       4                          |       63.42 ms                             | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       15.85 ms                             |       4                          |       63.42 ms                             | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       41.76 ms →       38.24 ms   (-8.42%) |       4   →       4              |      167.02 ms →      152.95 ms   (-8.42%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |       15.95 ms                             |       4                          |       63.79 ms                             | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |       15.94 ms                             |       4                          |       63.77 ms                             | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |       53.56 ms →       52.53 ms   (-1.92%) |       4   →       4              |      214.22 ms →      210.10 ms   (-1.92%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |       35.55 ms →       34.48 ms   (-3.02%) |       4   →       4              |      142.20 ms →      137.90 ms   (-3.02%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        1.94 ms →        1.94 ms   (+0.07%) |       4   →       4              |        7.77 ms →        7.77 ms   (+0.07%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       40.29 ms →       40.58 ms   (+0.72%) |       4   →       4              |      161.17 ms →      162.32 ms   (+0.72%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |        7.19 ms →        7.47 ms   (+3.79%) |       4   →       4              |       28.77 ms →       29.86 ms   (+3.79%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       27.32 ms →       27.14 ms   (-0.67%) |       8   →       8              |      218.55 ms →      217.09 ms   (-0.67%) | 
- │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.11 ms →       16.10 ms  (+14.12%) |       8   →       8              |      112.86 ms →      128.80 ms  (+14.12%) | 
  │ │ │ ├ sddk::inner                                                   |       14.05 ms                             |       8                          |      112.40 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       51.54 μs                             |       8                          |      412.31 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        16.05 ms            |                   8              |                       128.40 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        84.25 ns            |                   8              |                       674.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        15.74 ms            |                   8              |                       125.94 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                       353.38 ns            |                   8              |                         2.83 μs            | 
  │ │ ├ Eigensolver_scalapack|pzhegvx                                   |      353.28 ms →      353.34 ms   (+0.02%) |       4   →       4              |        1.41 s  →        1.41 s    (+0.02%) | 
  │ │ ├ sddk::transform                                                 |       27.63 ms                             |       4                          |      110.52 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       36.91 μs                             |       4                          |      147.65 μs                             | 
  │ │ │ ├ sddk::transform|mpi                                           |      909.99 μs                             |       4                          |        3.64 ms                             | 
  │ │ │ └ sddk::transform|local                                         |       26.93 μs                             |       4                          |      107.72 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                        28.06 ms            |                   4              |                       112.25 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                        27.88 ms            |                   4              |                       111.52 ms            | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      392.25 ns →      362.50 ns   (-7.58%) |       4   →       4              |        1.57 μs →        1.45 μs   (-7.58%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      792.50 s  →      289.62 s   (-63.45%) |       1   →       1              |      792.50 s  →      289.62 s   (-63.45%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.85 ms                             |      19                          |      111.07 ms                             | 
  │ ├ sirius::Density                                                   |                       138.54 ms            |                   1              |                       138.54 ms            | 
  │ │ └ sirius::Density::update                                         |                       126.96 ms            |                   1              |                       126.96 ms            | 
  │ │   └ sirius::Density::generate_pseudo_core_charge_density          |                       126.52 ms            |                   1              |                       126.52 ms            | 
  │ │     ├ sirius::Simulation_context::make_periodic_function          |                       116.80 ms            |                   1              |                       116.80 ms            | 
  │ │     └ sirius::Smooth_periodic_function::fft_transform             |                         5.69 ms            |                   1              |                         5.69 ms            | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |       24.75 s  →       11.12 s   (-55.07%) |      32   →      26    (-18.75%) |      792.06 s  →      289.17 s   (-63.49%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        4.48 ms →        7.97 ms  (+78.02%) |      32   →      26    (-18.75%) |      143.23 ms →      207.18 ms  (+44.64%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        4.12 ms →        4.13 ms   (+0.26%) |      32   →      26    (-18.75%) |      131.76 ms →      107.33 ms  (-18.54%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      983.38 μs                             |      32                          |       31.47 ms                             | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.25 ms →        2.26 ms   (+0.42%) |      32   →      26    (-18.75%) |       71.88 ms →       58.64 ms  (-18.41%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |       64.55 μs →       64.40 μs   (-0.22%) |      64   →      52    (-18.75%) |        4.13 ms →        3.35 ms  (-18.93%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |       92.85 μs →        1.24 ms (+1237.20%) |      32   →      26    (-18.75%) |        2.97 ms →       32.28 ms (+986.47%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       69.88 μs →        2.41 ms (+3344.20%) |      32   →      26    (-18.75%) |        2.24 ms →       62.58 ms (+2698.42%) | 
+ │ │ ├ sirius::Band::solve                                             |       22.51 s  →        8.99 s   (-60.04%) |      32   →      26    (-18.75%) |      720.29 s  →      233.84 s   (-67.54%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      198.66 μs →      326.24 μs  (+64.22%) |     128   →     104    (-18.75%) |       25.43 ms →       33.93 ms  (+33.43%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      192.54 μs →      319.10 μs  (+65.73%) |     128   →     104    (-18.75%) |       24.65 ms →       33.19 ms  (+34.66%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.71 μs →        3.71 μs  (-21.29%) |     128   →     104    (-18.75%) |      602.53 μs →      385.32 μs  (-36.05%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        5.63 s  →        2.25 s   (-60.05%) |     128   →     104    (-18.75%) |      720.27 s  →      233.80 s   (-67.54%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       16.01 ms                             |     128                          |        2.05 s                              | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |      655.45 μs                             |     768                          |      503.39 ms                             | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.85 ms →        1.83 ms   (-1.10%) |     128   →     104    (-18.75%) |      236.80 ms →      190.29 ms  (-19.64%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      356.19 μs                             |     128                          |       45.59 ms                             | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      546.62 μs                             |     256                          |      139.94 ms                             | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        5.60 s  →        2.23 s   (-60.27%) |     128   →     104    (-18.75%) |      716.82 s  →      231.41 s   (-67.72%) | 
+ │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       72.44 ms →       64.12 ms  (-11.48%) |     865   →     940     (+8.67%) |       62.66 s  →       60.28 s    (-3.80%) | 
+ │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       46.22 ms →       40.48 ms  (-12.41%) |     865   →     940     (+8.67%) |       39.98 s  →       38.05 s    (-4.81%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        8.76 ms →        7.97 ms   (-8.98%) |     865   →     940     (+8.67%) |        7.58 s  →        7.50 s    (-1.09%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |       68.15 μs                             |     865                          |       58.95 ms                             | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |      446.51 μs                             |     128                          |       57.15 ms                             | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |        7.31 ms →        6.07 ms  (-17.06%) |     865   →     940     (+8.67%) |        6.33 s  →        5.70 s    (-9.87%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |       63.73 μs                             |     865                          |       55.13 ms                             | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |      414.23 μs                             |     128                          |       53.02 ms                             | 
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       10.03 ms →        8.69 ms  (-13.38%) |     865   →     940     (+8.67%) |        8.68 s  →        8.17 s    (-5.87%) | 
+ │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |        6.20 ms →        5.39 ms  (-13.05%) |     865   →     940     (+8.67%) |        5.36 s  →        5.07 s    (-5.51%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        1.53 ms →        1.51 ms   (-1.63%) |     865   →     940     (+8.67%) |        1.33 s  →        1.42 s    (+6.90%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        9.08 ms →        8.01 ms  (-11.87%) |     865   →     940     (+8.67%) |        7.86 s  →        7.53 s    (-4.22%) | 
  │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        1.35 ms →        1.24 ms   (-8.11%) |     865   →     940     (+8.67%) |        1.16 s  →        1.16 s    (-0.14%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.79 ms →        7.05 ms   (-9.52%) |    1.73 K →    1.88 K   (+8.67%) |       13.48 s  →       13.25 s    (-1.68%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |       20.71 ms →       26.89 ms  (+29.80%) |     865   →     940     (+8.67%) |       17.92 s  →       25.28 s   (+41.06%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        2.32 ms                             |    1.60 K                        |        3.71 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       32.43 μs                             |    1.76 K                        |       56.98 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                         1.70 ms            |                1.78 K            |                         3.02 s             | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                       129.56 ns            |                1.78 K            |                       230.09 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                         1.66 ms            |                1.78 K            |                         2.96 s             | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                       358.90 ns            |                1.78 K            |                       637.40 μs            | 
+ │ │ │ │   │ ├ sddk::orthogonalize|potrf                               |        1.04 ms →      793.94 μs  (-23.63%) |     865   →     940     (+8.67%) |      899.23 ms →      746.30 ms  (-17.01%) | 
+ │ │ │ │   │ ├ sddk::orthogonalize|trtri                               |        1.62 ms →        1.31 ms  (-19.63%) |     865   →     940     (+8.67%) |        1.40 s  →        1.23 s   (-12.66%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        3.13 ms                             |    3.33 K                        |       10.43 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       13.93 μs                             |    3.33 K                        |       46.40 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|mpi                                   |      160.84 μs                             |    3.33 K                        |      535.93 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       10.31 μs                             |    4.81 K                        |       49.57 ms                             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                         5.17 ms            |                3.66 K            |                        18.90 s             | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                         3.52 ms            |                5.33 K            |                        18.73 s             | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        6.25 ms →        3.85 ms  (-38.35%) |     865   →     940     (+8.67%) |        5.41 s  →        3.62 s   (-33.01%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        4.41 ms                             |     865                          |        3.81 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       28.07 μs                             |    1.05 K                        |       29.62 ms                             | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                         3.15 ms            |                 940              |                         2.96 s             | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                       115.39 ns            |                 940              |                       108.47 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                         3.12 ms            |                 940              |                         2.93 s             | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                       333.01 ns            |                 940              |                       313.03 μs            | 
+ │ │ │ │   ├ Eigensolver_scalapack|pzheevx                             |      717.82 ms →      131.08 ms  (-81.74%) |     865   →     940     (+8.67%) |      620.91 s  →      123.21 s   (-80.16%) | 
+ │ │ │ │   ├ sirius::residuals                                         |        8.39 ms →        7.35 ms  (-12.45%) |     853   →     925     (+8.44%) |        7.16 s  →        6.80 s    (-5.06%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        7.56 ms                             |     791                          |        5.98 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       24.30 μs                             |     791                          |       19.22 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|mpi                                   |      308.54 μs                             |     791                          |      244.06 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       15.20 μs                             |    1.58 K                        |       24.05 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                         6.95 ms            |                 836              |                         5.81 s             | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                         3.45 ms            |                1.67 K            |                         5.77 s             | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      946.51 μs →      533.05 μs  (-43.68%) |     791   →     836     (+5.69%) |      748.69 ms →      445.63 ms  (-40.48%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       20.03 ms →       35.17 ms  (+75.57%) |     136   →     345   (+153.68%) |        2.72 s  →       12.14 s  (+345.39%) | 
  │ │ │ │     ├ sddk::transform                                         |       18.86 ms                             |     144                          |        2.72 s                              | 
  │ │ │ │     │ ├ sddk::transform|init                                  |       24.06 μs                             |     144                          |        3.46 ms                             | 
  │ │ │ │     │ ├ sddk::transform|mpi                                   |        1.39 ms                             |     144                          |      199.49 ms                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       19.84 μs                             |     152                          |        3.02 ms                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                        20.58 ms            |                 586              |                        12.06 s             | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                        14.50 ms            |                 827              |                        11.99 s             | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      523.32 ns →      513.47 ns   (-1.88%) |     128   →     104    (-18.75%) |       66.98 μs →       53.40 μs  (-20.28%) | 
  │ │ │ ├ sirius::K_point_set::sync_band_energies                       |       22.62 μs                             |      32                          |      723.72 μs                             | 
  │ │ │ └ sirius::K_point_set::sync_band                                |                       245.15 μs            |                  26              |                         6.37 ms            | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |      600.90 μs →      754.04 μs  (+25.49%) |      32   →      26    (-18.75%) |       19.23 ms →       19.61 ms   (+1.96%) | 
  │ │ │ └ sirius::K_point_set::sync_band                                |                        23.09 μs            |                  26              |                       600.29 μs            | 
+ │ │ ├ sirius::Density::generate                                       |      904.17 ms →      873.86 ms   (-3.35%) |      32   →      26    (-18.75%) |       28.93 s  →       22.72 s   (-21.47%) | 
+ │ │ │ ├ sirius::Density::generate_valence                             |      524.95 ms →      524.47 ms   (-0.09%) |      32   →      26    (-18.75%) |       16.80 s  →       13.64 s   (-18.82%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       24.49 ms →       23.59 ms   (-3.70%) |     128   →     104    (-18.75%) |        3.14 s  →        2.45 s   (-21.75%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |        7.73 μs                             |     128                          |      989.26 μs                             | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       14.29 μs                             |       8                          |      114.29 μs                             | 
+ │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       20.44 ms →       19.54 ms   (-4.39%) |     128   →     104    (-18.75%) |        2.62 s  →        2.03 s   (-22.32%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       29.88 ms →       29.85 ms   (-0.11%) |     128   →     104    (-18.75%) |        3.82 s  →        3.10 s   (-18.84%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.37 μs →        9.49 μs   (+1.24%) |     128   →     104    (-18.75%) |        1.20 ms →      986.56 μs  (-17.74%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        1.46 ms →        1.45 ms   (-0.36%) |     128   →     104    (-18.75%) |      186.31 ms →      150.82 ms  (-19.05%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       27.94 ms →       27.86 ms   (-0.29%) |     128   →     104    (-18.75%) |        3.58 s  →        2.90 s   (-18.98%) | 
+ │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        3.80 ms →        3.83 ms   (+1.00%) |     128   →     104    (-18.75%) |      485.86 ms →      398.69 ms  (-17.94%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      660.26 ns →      509.79 ns  (-22.79%) |     128   →     104    (-18.75%) |       84.51 μs →       53.02 μs  (-37.27%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       42.71 ms →       42.75 ms   (+0.07%) |     128   →     104    (-18.75%) |        5.47 s  →        4.45 s   (-18.69%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.65 ms   (+0.54%) |      32   →      26    (-18.75%) |       52.42 ms →       42.83 ms  (-18.31%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |       88.30 ms →       88.97 ms   (+0.75%) |      32   →      26    (-18.75%) |        2.83 s  →        2.31 s   (-18.14%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.06 ms →       88.74 ms   (+0.77%) |      32   →      26    (-18.75%) |        2.82 s  →        2.31 s   (-18.12%) | 
+ │ │ │ ├ sirius::Field4D::symmetrize                                   |      286.42 ms →      256.32 ms  (-10.51%) |      32   →      26    (-18.75%) |        9.17 s  →        6.66 s   (-27.29%) | 
+ │ │ │ │ └ sirius::symmetrize_function|fpw                             |      286.42 ms →      256.31 ms  (-10.51%) |      32   →      26    (-18.75%) |        9.17 s  →        6.66 s   (-27.29%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.35 ms →       25.06 ms   (+2.93%) |      32   →      26    (-18.75%) |      779.22 ms →      651.66 ms  (-16.37%) | 
+ │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      236.37 ms →      205.22 ms  (-13.18%) |      32   →      26    (-18.75%) |        7.56 s  →        5.34 s   (-29.46%) | 
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       23.90 ms →       24.79 ms   (+3.74%) |      32   →      26    (-18.75%) |      764.71 ms →      644.54 ms  (-15.71%) | 
+ │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       80.79 ms →       81.50 ms   (+0.88%) |      32   →      26    (-18.75%) |        2.59 s  →        2.12 s   (-18.04%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        8.46 ms →        7.90 ms   (-6.62%) |      32   →      26    (-18.75%) |      270.75 ms →      205.43 ms  (-24.13%) | 
  │ │ ├ sirius::inner                                                   |                        10.68 ms            |                 312              |                         3.33 s             | 
+ │ │ ├ sirius::Density::mix                                            |      232.22 ms →      154.88 ms  (-33.31%) |      32   →      26    (-18.75%) |        7.43 s  →        4.03 s   (-45.81%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      969.80 μs →        1.06 ms   (+9.33%) |      32   →      26    (-18.75%) |       31.03 ms →       27.57 ms  (-11.17%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       11.15 ms                             |     424                          |        4.73 s                              | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.89 ms                             |     424                          |        4.62 s                              | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.89 ms                             |     424                          |        4.62 s                              | 
  │ │ │ ├ sirius::inner                                                 |                        10.12 ms            |                 334              |                         3.38 s             | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        7.17 ms →        6.38 ms  (-11.04%) |      32   →      26    (-18.75%) |      229.52 ms →      165.89 ms  (-27.72%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        6.33 ms →        5.24 ms  (-17.23%) |      32   →      26    (-18.75%) |      202.44 ms →      136.14 ms  (-32.75%) | 
+ │ │ ├ sirius::Potential::generate                                     |      687.45 ms →      671.22 ms   (-2.36%) |      32   →      26    (-18.75%) |       22.00 s  →       17.45 s   (-20.67%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |      138.31 ms →      138.89 ms   (+0.42%) |      32   →      26    (-18.75%) |        4.43 s  →        3.61 s   (-18.41%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        6.42 ms →        6.08 ms   (-5.38%) |      32   →      26    (-18.75%) |      205.57 ms →      158.05 ms  (-23.12%) | 
  │ │ │ │ ├ sirius::Periodic_function|inner                             |       11.08 ms                             |      32                          |      354.42 ms                             | 
  │ │ │ │ │ └ sirius::Periodic_function|inner_local                     |       11.05 ms                             |      32                          |      353.65 ms                             | 
  │ │ │ │ │   └ sirius::Smooth_periodic_function|inner_local            |       11.05 ms                             |      32                          |      353.62 ms                             | 
  │ │ │ │ └ sirius::inner                                               |                        11.69 ms            |                  26              |                       304.02 ms            | 
+ │ │ │ ├ sirius::Periodic_function::add                                |      543.97 μs →      459.78 μs  (-15.48%) |      64   →      52    (-18.75%) |       34.81 ms →       23.91 ms  (-31.33%) | 
+ │ │ │ ├ sirius::Potential::xc                                         |       54.20 ms →       34.46 ms  (-36.42%) |      32   →      26    (-18.75%) |        1.73 s  →      895.93 ms  (-48.34%) | 
+ │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       54.20 ms →       32.11 ms  (-40.76%) |      32   →      26    (-18.75%) |        1.73 s  →      834.77 ms  (-51.87%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.03 ms                             |      64                          |      193.70 ms                             | 
  │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |        5.74 ms                             |      32                          |      183.66 ms                             | 
  │ │ │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                |                        11.91 ms            |                  52              |                       619.54 ms            | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.83 ms →        4.97 ms  (-27.29%) |      32   →      26    (-18.75%) |      218.57 ms →      129.12 ms  (-40.93%) | 
+ │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.87 ms →       90.84 ms   (-0.04%) |      32   →      26    (-18.75%) |        2.91 s  →        2.36 s   (-18.79%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      394.85 ms →      397.25 ms   (+0.61%) |      32   →      26    (-18.75%) |       12.64 s  →       10.33 s   (-18.26%) | 
+ │ │ ├ sirius::Field4D::symmetrize                                     |      290.53 ms →      257.86 ms  (-11.25%) |      32   →      26    (-18.75%) |        9.30 s  →        6.70 s   (-27.89%) | 
+ │ │ │ └ sirius::symmetrize_function|fpw                               |      290.53 ms →      257.85 ms  (-11.25%) |      32   →      26    (-18.75%) |        9.30 s  →        6.70 s   (-27.89%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.30 ms →       23.98 ms  (-12.15%) |      32   →      26    (-18.75%) |      873.68 ms →      623.61 ms  (-28.62%) | 
+ │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      235.53 ms →      207.51 ms  (-11.90%) |      32   →      26    (-18.75%) |        7.54 s  →        5.40 s   (-28.42%) | 
+ │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.92 ms →       25.22 ms   (+5.42%) |      32   →      26    (-18.75%) |      765.39 ms →      655.61 ms  (-14.34%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.64 ms →        5.52 ms   (-2.27%) |      32   →      26    (-18.75%) |      180.62 ms →      143.42 ms  (-20.60%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.89 ms                             |     224                          |        2.44 s                              | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |       10.54 ms                             |     224                          |        2.36 s                              | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |       10.54 ms                             |     224                          |        2.36 s                              | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.29 ms                             |      96                          |      987.93 ms                             | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        9.91 ms                             |      96                          |      951.35 ms                             | 
+ │ │ ├ sirius::Periodic_function::integrate                            |       10.07 ms →       10.05 ms   (-0.13%) |      32   →      26    (-18.75%) |      322.19 ms →      261.43 ms  (-18.86%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      110.19 μs →       13.75 ms (+12381.25%) |      32   →      26    (-18.75%) |        3.53 ms →      357.57 ms (+10041.02%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      104.95 μs →       13.75 ms (+12998.29%) |      32   →      26    (-18.75%) |        3.36 ms →      357.43 ms (+10542.36%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.24 ms →        4.86 ms   (-7.42%) |       2   →       2              |       10.49 ms →        9.71 ms   (-7.42%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.47 ms                             |       6                          |       62.82 ms                             | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.43 ms                             |       6                          |       62.59 ms                             | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.43 ms                             |       6                          |       62.58 ms                             | 
  │ ├ sirius::Smooth_periodic_function|inner                            |       10.00 ms                             |       3                          |       29.99 ms                             | 
  │ │ └ sirius::Smooth_periodic_function|inner_local                    |        9.98 ms                             |       3                          |       29.93 ms                             | 
  │ └ sirius::inner                                                     |                        10.31 ms            |                   9              |                        92.77 ms            | 
  ├ sirius::Periodic_function|inner                                     |       10.73 ms                             |       2                          |       21.46 ms                             | 
  │ └ sirius::Periodic_function|inner_local                             |       10.37 ms                             |       2                          |       20.75 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.37 ms                             |       2                          |       20.75 ms                             | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.04 ms                             |       1                          |       10.04 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.04 ms                             |       1                          |       10.04 ms                             | 
  ├ sirius::inner                                                       |                        10.25 ms            |                   3              |                        30.75 ms            | 
  └ sirius::finalize                                                    |      369.97 ms →      346.90 ms   (-6.23%) |       1   →       1              |      369.97 ms →      346.90 ms   (-6.23%) | 
  ====================================================================================================================================================================================================
```
