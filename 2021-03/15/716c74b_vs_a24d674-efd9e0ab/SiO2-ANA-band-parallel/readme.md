# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs 716c74b9e40f2dc514547b13861ce8c977f50e6c
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      819.71 s  →      325.93 s   (-60.24%) |       1   →       1              |      819.71 s  →      325.93 s   (-60.24%) | 
  ├ sirius::initialize                                                  |        2.73 s  →        2.73 s    (+0.11%) |       1   →       1              |        2.73 s  →        2.73 s    (+0.11%) | 
  ├ sirius::Simulation_context::initialize                              |        2.93 s  →        2.91 s    (-0.78%) |       1   →       1              |        2.93 s  →        2.91 s    (-0.78%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       23.86 ms →       18.04 ms  (-24.41%) |       1   →       1              |       23.86 ms →       18.04 ms  (-24.41%) | 
  │ ├ sirius::Unit_cell::initialize                                     |      153.75 ms →      156.49 ms   (+1.78%) |       1   →       1              |      153.75 ms →      156.49 ms   (+1.78%) | 
  │ │ ├ sirius::Atom_type::init                                         |       64.41 ms →       65.57 ms   (+1.80%) |       2   →       2              |      128.82 ms →      131.14 ms   (+1.80%) | 
  │ │ └ sirius::Unit_cell::update                                       |       24.86 ms →       25.16 ms   (+1.19%) |       1   →       1              |       24.86 ms →       25.16 ms   (+1.19%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.28 ms →        6.41 ms   (+2.14%) |       1   →       1              |        6.28 ms →        6.41 ms   (+2.14%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       18.54 ms →       18.71 ms   (+0.89%) |       1   →       1              |       18.54 ms →       18.71 ms   (+0.89%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       18.52 ms →       18.68 ms   (+0.87%) |       1   →       1              |       18.52 ms →       18.68 ms   (+0.87%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        5.32 ms →        5.22 ms   (-1.97%) |       1   →       1              |        5.32 ms →        5.22 ms   (-1.97%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.35 ms →        2.35 ms   (+0.19%) |       1   →       1              |        2.35 ms →        2.35 ms   (+0.19%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      100.55 μs →      105.98 μs   (+5.40%) |       1   →       1              |      100.55 μs →      105.98 μs   (+5.40%) | 
  │ └ sirius::Simulation_context::update                                |        2.71 s  →        2.69 s    (-0.84%) |       1   →       1              |        2.71 s  →        2.69 s    (-0.84%) | 
  │   ├ sirius::Unit_cell::update                                       |       11.86 ms →       11.78 ms   (-0.62%) |       1   →       1              |       11.86 ms →       11.78 ms   (-0.62%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.33 ms →        4.45 ms   (+2.76%) |       1   →       1              |        4.33 ms →        4.45 ms   (+2.76%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        7.49 ms →        7.30 ms   (-2.55%) |       1   →       1              |        7.49 ms →        7.30 ms   (-2.55%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        7.47 ms →        7.28 ms   (-2.61%) |       1   →       1              |        7.47 ms →        7.28 ms   (-2.61%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        4.98 ms →        4.79 ms   (-3.91%) |       1   →       1              |        4.98 ms →        4.79 ms   (-3.91%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.32 ms   (-0.22%) |       1   →       1              |        2.32 ms →        2.32 ms   (-0.22%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       99.74 μs →      103.23 μs   (+3.50%) |       1   →       1              |       99.74 μs →      103.23 μs   (+3.50%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       64.99 ms →       66.08 ms   (+1.69%) |       2   →       2              |      129.98 ms →      132.17 ms   (+1.69%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.12 ms →        5.15 ms   (+0.72%) |       2   →       2              |       10.24 ms →       10.31 ms   (+0.72%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.55 ms →        4.46 ms   (-1.92%) |       1   →       1              |        4.55 ms →        4.46 ms   (-1.92%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.75 ms →       21.73 ms   (-0.10%) |       2   →       2              |       43.49 ms →       43.45 ms   (-0.10%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.75 ms →       14.75 ms   (-0.02%) |       2   →       2              |       29.51 ms →       29.50 ms   (-0.02%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.78 ms →       19.81 ms   (+0.16%) |       4   →       4              |       79.13 ms →       79.26 ms   (+0.16%) | 
  │   ├ sddk::Gvec::init                                                |      173.23 ms →      174.89 ms   (+0.95%) |       2   →       2              |      346.46 ms →      349.77 ms   (+0.95%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      130.58 ms →      132.15 ms   (+1.21%) |       2   →       2              |      261.16 ms →      264.31 ms   (+1.21%) | 
  │   ├ sddk::Gvec_shells                                               |      177.19 ms →      171.01 ms   (-3.49%) |       1   →       1              |      177.19 ms →      171.01 ms   (-3.49%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.32 ms →        1.33 ms   (+0.41%) |       1   →       1              |        1.32 ms →        1.33 ms   (+0.41%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      293.06 ms →      295.51 ms   (+0.84%) |       2   →       2              |      586.12 ms →      591.02 ms   (+0.84%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       81.07 ms →       77.21 ms   (-4.76%) |       1   →       1              |       81.07 ms →       77.21 ms   (-4.76%) | 
- │ ├ sirius::K_point::K_point                                          |        2.91 μs →        6.87 μs (+136.59%) |       4   →       4              |       11.62 μs →       27.50 μs (+136.59%) | 
  │ └ sirius::K_point_set::initialize                                   |       80.98 ms →       77.04 ms   (-4.86%) |       1   →       1              |       80.98 ms →       77.04 ms   (-4.86%) | 
  │   └ sirius::K_point::initialize                                     |       20.23 ms →       19.25 ms   (-4.86%) |       4   →       4              |       80.93 ms →       77.00 ms   (-4.86%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       15.66 ms →       14.63 ms   (-6.55%) |       4   →       4              |       62.63 ms →       58.53 ms   (-6.55%) | 
  │     │ └ sddk::Gvec::init                                            |        3.90 ms →        3.84 ms   (-1.69%) |       4   →       4              |       15.62 ms →       15.35 ms   (-1.69%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        8.96 μs                             |       4                          |       35.85 μs                             | 
  │     └ sirius::K_point::update                                       |        3.27 ms →        3.29 ms   (+0.57%) |       4   →       4              |       13.10 ms →       13.17 ms   (+0.57%) | 
  │       └ sirius::Beta_projectors                                     |        1.76 ms →        1.79 ms   (+1.53%) |       4   →       4              |        7.04 ms →        7.14 ms   (+1.53%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      927.61 μs →      958.71 μs   (+3.35%) |       4   →       4              |        3.71 ms →        3.83 ms   (+3.35%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.34 ms                             |       2                          |       10.67 ms                             | 
+ ├ sirius::Potential                                                   |      172.11 ms →      153.37 ms  (-10.89%) |       1   →       1              |      172.11 ms →      153.37 ms  (-10.89%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.90 ms                             |       6                          |       35.39 ms                             | 
  │ └ sirius::Potential::update                                         |      136.02 ms →      123.15 ms   (-9.46%) |       1   →       1              |      136.02 ms →      123.15 ms   (-9.46%) | 
  │   └ sirius::Potential::generate_local_potential                     |      135.24 ms →      122.38 ms   (-9.51%) |       1   →       1              |      135.24 ms →      122.38 ms   (-9.51%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      112.07 ms →      111.18 ms   (-0.80%) |       1   →       1              |      112.07 ms →      111.18 ms   (-0.80%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       22.63 ms →        5.49 ms  (-75.72%) |       1   →       1              |       22.63 ms →        5.49 ms  (-75.72%) | 
  ├ sirius::Density                                                     |      140.12 ms →      131.31 ms   (-6.29%) |       1   →       1              |      140.12 ms →      131.31 ms   (-6.29%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.54 ms                             |       2                          |       11.09 ms                             | 
  │ └ sirius::Density::update                                           |      128.74 ms →      120.62 ms   (-6.30%) |       1   →       1              |      128.74 ms →      120.62 ms   (-6.30%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      128.29 ms →      120.19 ms   (-6.32%) |       1   →       1              |      128.29 ms →      120.19 ms   (-6.32%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      112.47 ms →      113.08 ms   (+0.55%) |       1   →       1              |      112.47 ms →      113.08 ms   (+0.55%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       15.38 ms →        5.18 ms  (-66.29%) |       1   →       1              |       15.38 ms →        5.18 ms  (-66.29%) | 
  ├ sirius::Density::initial_density                                    |      177.06 ms →      165.98 ms   (-6.25%) |       1   →       1              |      177.06 ms →      165.98 ms   (-6.25%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      110.98 ms →      111.14 ms   (+0.15%) |       1   →       1              |      110.98 ms →      111.14 ms   (+0.15%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |       10.91 ms →        5.62 ms  (-48.50%) |       2   →       2              |       21.83 ms →       11.24 ms  (-48.50%) | 
  │ └ sirius::Periodic_function::integrate                              |       10.29 ms →       10.05 ms   (-2.32%) |       1   →       1              |       10.29 ms →       10.05 ms   (-2.32%) | 
  ├ sirius::Potential::generate                                         |      704.13 ms →      672.30 ms   (-4.52%) |       1   →       1              |      704.13 ms →      672.30 ms   (-4.52%) | 
  │ ├ sirius::Potential::poisson                                        |      138.28 ms →      127.24 ms   (-7.98%) |       1   →       1              |      138.28 ms →      127.24 ms   (-7.98%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       17.20 ms →        6.39 ms  (-62.84%) |       1   →       1              |       17.20 ms →        6.39 ms  (-62.84%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       11.70 ms                             |       1                          |       11.70 ms                             | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |       10.22 ms                             |       1                          |       10.22 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |       10.22 ms                             |       1                          |       10.22 ms                             | 
  │ │ └ sirius::inner                                                   |                        10.64 ms            |                   1              |                        10.64 ms            | 
+ │ ├ sirius::Periodic_function::add                                    |      544.65 μs →      472.66 μs  (-13.22%) |       2   →       2              |        1.09 ms →      945.31 μs  (-13.22%) | 
+ │ ├ sirius::Potential::xc                                             |       59.01 ms →       39.14 ms  (-33.67%) |       1   →       1              |       59.01 ms →       39.14 ms  (-33.67%) | 
+ │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       59.01 ms →       36.72 ms  (-37.77%) |       1   →       1              |       59.01 ms →       36.72 ms  (-37.77%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.66 ms                             |       2                          |       11.31 ms                             | 
  │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        5.21 ms                             |       1                          |        5.21 ms                             | 
  │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                    |                        12.14 ms            |                   2              |                        24.27 ms            | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.86 ms →        4.96 ms  (-15.23%) |       1   →       1              |        5.86 ms →        4.96 ms  (-15.23%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.55 ms →       93.68 ms   (+1.22%) |       1   →       1              |       92.55 ms →       93.68 ms   (+1.22%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      405.97 ms →      402.27 ms   (-0.91%) |       1   →       1              |      405.97 ms →      402.27 ms   (-0.91%) | 
- ├ sirius::Hamiltonian0                                                |        8.40 ms →       12.13 ms  (+44.34%) |       1   →       1              |        8.40 ms →       12.13 ms  (+44.34%) | 
  │ ├ sirius::Local_operator                                            |        8.06 ms →        8.27 ms   (+2.63%) |       1   →       1              |        8.06 ms →        8.27 ms   (+2.63%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.78 ms                             |       1                          |        4.78 ms                             | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.36 ms →        2.32 ms   (-1.70%) |       1   →       1              |        2.36 ms →        2.32 ms   (-1.70%) | 
  │ ├ sirius::Non_local_operator                                        |       62.22 μs →       61.51 μs   (-1.15%) |       2   →       2              |      124.44 μs →      123.02 μs   (-1.15%) | 
- │ ├ sirius::D_operator::initialize                                    |       92.59 μs →        1.25 ms (+1247.91%) |       1   →       1              |       92.59 μs →        1.25 ms (+1247.91%) | 
- │ └ sirius::Q_operator::initialize                                    |       70.82 μs →        2.42 ms (+3313.96%) |       1   →       1              |       70.82 μs →        2.42 ms (+3313.96%) | 
  ├ sirius::Band::initialize_subspace                                   |        3.98 s  →        3.97 s    (-0.22%) |       1   →       1              |        3.98 s  →        3.97 s    (-0.22%) | 
- │ ├ sirius::Hamiltonian_k                                             |      210.28 μs →      768.74 μs (+265.59%) |       4   →       4              |      841.10 μs →        3.07 ms (+265.59%) | 
- │ │ ├ sirius::Local_operator::prepare_k                               |      205.30 μs →      760.51 μs (+270.45%) |       4   →       4              |      821.18 μs →        3.04 ms (+270.45%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        3.45 μs →        3.77 μs   (+9.22%) |       4   →       4              |       13.80 μs →       15.08 μs   (+9.22%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |      994.25 ms →      991.11 ms   (-0.32%) |       4   →       4              |        3.98 s  →        3.96 s    (-0.32%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       32.74 ms                             |      16                          |      523.88 ms                             | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       14.45 ms →       14.47 ms   (+0.10%) |       4   →       4              |       57.81 ms →       57.87 ms   (+0.10%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        5.27 ms →        5.32 ms   (+0.89%) |       4   →       4              |       21.09 ms →       21.28 ms   (+0.89%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      352.57 ms →      356.29 ms   (+1.06%) |       4   →       4              |        1.41 s  →        1.43 s    (+1.06%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      255.92 ms →      259.75 ms   (+1.50%) |       4   →       4              |        1.02 s  →        1.04 s    (+1.50%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       62.92 ms →       64.35 ms   (+2.27%) |       4   →       4              |      251.69 ms →      257.40 ms   (+2.27%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       16.52 ms                             |       4                          |       66.09 ms                             | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       16.52 ms                             |       4                          |       66.08 ms                             | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       39.94 ms →       41.18 ms   (+3.08%) |       4   →       4              |      159.77 ms →      164.70 ms   (+3.08%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |       16.34 ms                             |       4                          |       65.35 ms                             | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |       16.33 ms                             |       4                          |       65.33 ms                             | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |       52.46 ms →       54.13 ms   (+3.20%) |       4   →       4              |      209.82 ms →      216.53 ms   (+3.20%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |       34.42 ms →       36.09 ms   (+4.86%) |       4   →       4              |      137.68 ms →      144.37 ms   (+4.86%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        1.96 ms →        1.96 ms   (+0.01%) |       4   →       4              |        7.84 ms →        7.84 ms   (+0.01%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       40.44 ms →       40.23 ms   (-0.51%) |       4   →       4              |      161.77 ms →      160.94 ms   (-0.51%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |        7.19 ms →        7.04 ms   (-2.11%) |       4   →       4              |       28.77 ms →       28.17 ms   (-2.11%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       27.11 ms →       27.15 ms   (+0.15%) |       8   →       8              |      216.85 ms →      217.16 ms   (+0.15%) | 
- │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.21 ms →       16.09 ms  (+13.21%) |       8   →       8              |      113.70 ms →      128.72 ms  (+13.21%) | 
  │ │ │ ├ sddk::inner                                                   |       14.15 ms                             |       8                          |      113.23 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       53.11 μs                             |       8                          |      424.86 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        16.04 ms            |                   8              |                       128.34 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        90.13 ns            |                   8              |                       721.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        15.74 ms            |                   8              |                       125.88 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                       366.38 ns            |                   8              |                         2.93 μs            | 
  │ │ ├ Eigensolver_scalapack|pzhegvx                                   |      341.66 ms →      320.60 ms   (-6.17%) |       4   →       4              |        1.37 s  →        1.28 s    (-6.17%) | 
  │ │ ├ sddk::transform                                                 |       27.63 ms                             |       4                          |      110.53 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       34.42 μs                             |       4                          |      137.69 μs                             | 
  │ │ │ ├ sddk::transform|mpi                                           |      953.83 μs                             |       4                          |        3.82 ms                             | 
  │ │ │ └ sddk::transform|local                                         |       23.77 μs                             |       4                          |       95.08 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                        28.12 ms            |                   4              |                       112.50 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                        27.89 ms            |                   4              |                       111.54 ms            | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |        1.49 μs →      408.50 ns  (-72.58%) |       4   →       4              |        5.96 μs →        1.63 μs  (-72.58%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      807.84 s  →      314.28 s   (-61.10%) |       1   →       1              |      807.84 s  →      314.28 s   (-61.10%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.80 ms                             |      19                          |      110.13 ms                             | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |       21.25 s                              |      38                          |      807.45 s                              | 
  │ │ ├ sirius::Hamiltonian0                                            |        4.52 ms                             |      38                          |      171.85 ms                             | 
  │ │ │ ├ sirius::Local_operator                                        |        4.16 ms                             |      38                          |      158.25 ms                             | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      977.43 μs                             |      38                          |       37.14 ms                             | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.30 ms                             |      38                          |       87.37 ms                             | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.35 μs                             |      76                          |        4.89 ms                             | 
  │ │ │ ├ sirius::D_operator::initialize                                |       92.49 μs                             |      38                          |        3.51 ms                             | 
  │ │ │ └ sirius::Q_operator::initialize                                |       70.65 μs                             |      38                          |        2.68 ms                             | 
  │ │ ├ sirius::Band::solve                                             |       19.01 s                              |      38                          |      722.50 s                              | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      214.25 μs                             |     152                          |       32.57 ms                             | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      208.09 μs                             |     152                          |       31.63 ms                             | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.73 μs                             |     152                          |      718.86 μs                             | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        4.75 s                              |     152                          |      722.47 s                              | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       15.29 ms                             |     152                          |        2.32 s                              | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |      552.00 μs                             |     912                          |      503.42 ms                             | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.85 ms                             |     152                          |      280.72 ms                             | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      356.33 μs                             |     152                          |       54.16 ms                             | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      545.38 μs                             |     304                          |      165.80 ms                             | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        4.73 s                              |     152                          |      718.49 s                              | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       78.62 ms                             |     861                          |       67.69 s                              | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       50.24 ms                             |     861                          |       43.26 s                              | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        9.10 ms                             |     861                          |        7.84 s                              | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |       63.21 μs                             |     861                          |       54.42 ms                             | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |      346.38 μs                             |     152                          |       52.65 ms                             | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |        7.52 ms                             |     861                          |        6.47 s                              | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |       64.13 μs                             |     861                          |       55.22 ms                             | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |      349.36 μs                             |     152                          |       53.10 ms                             | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       10.85 ms                             |     861                          |        9.34 s                              | 
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |        6.62 ms                             |     861                          |        5.70 s                              | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        1.55 ms                             |     861                          |        1.33 s                              | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       10.03 ms                             |     861                          |        8.63 s                              | 
  │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        1.56 ms                             |     861                          |        1.34 s                              | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        8.39 ms                             |    1.72 K                        |       14.45 s                              | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       22.34 ms                             |     861                          |       19.23 s                              | 
  │ │ │ │   │ ├ sddk::inner                                             |        2.52 ms                             |    1.57 K                        |        3.96 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       33.24 μs                             |    1.73 K                        |       57.33 ms                             | 
  │ │ │ │   │ ├ sddk::orthogonalize|potrf                               |        1.15 ms                             |     861                          |      987.02 ms                             | 
  │ │ │ │   │ ├ sddk::orthogonalize|trtri                               |        1.82 ms                             |     861                          |        1.56 s                              | 
  │ │ │ │   │ └ sddk::transform                                         |        3.37 ms                             |    3.29 K                        |       11.08 s                              | 
  │ │ │ │   │   ├ sddk::transform|init                                  |       14.30 μs                             |    3.29 K                        |       47.07 ms                             | 
  │ │ │ │   │   ├ sddk::transform|mpi                                   |      184.61 μs                             |    3.29 K                        |      607.73 ms                             | 
  │ │ │ │   │   └ sddk::transform|local                                 |       10.37 μs                             |    4.71 K                        |       48.82 ms                             | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        6.39 ms                             |     861                          |        5.51 s                              | 
  │ │ │ │   │ └ sddk::inner                                             |        4.64 ms                             |     861                          |        4.00 s                              | 
  │ │ │ │   │   └ sddk::inner|local                                     |       28.42 μs                             |    1.05 K                        |       29.87 ms                             | 
  │ │ │ │   ├ Eigensolver_scalapack|pzheevx                             |      715.23 ms                             |     861                          |      615.81 s                              | 
  │ │ │ │   ├ sirius::residuals                                         |        8.55 ms                             |     850                          |        7.27 s                              | 
  │ │ │ │   │ ├ sddk::transform                                         |        7.74 ms                             |     788                          |        6.10 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       24.29 μs                             |     788                          |       19.14 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|mpi                                   |      316.17 μs                             |     788                          |      249.14 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       15.26 μs                             |    1.58 K                        |       24.05 ms                             | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      981.53 μs                             |     788                          |      773.45 ms                             | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       18.36 ms                             |     160                          |        2.94 s                              | 
  │ │ │ │     └ sddk::transform                                         |       17.44 ms                             |     168                          |        2.93 s                              | 
  │ │ │ │       ├ sddk::transform|init                                  |       22.04 μs                             |     168                          |        3.70 ms                             | 
  │ │ │ │       ├ sddk::transform|mpi                                   |        1.25 ms                             |     168                          |      210.23 ms                             | 
  │ │ │ │       └ sddk::transform|local                                 |       18.11 μs                             |     176                          |        3.19 ms                             | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      600.93 ns                             |     152                          |       91.34 μs                             | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       20.11 μs                             |      38                          |      764.25 μs                             | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      587.08 μs                             |      38                          |       22.31 ms                             | 
  │ │ ├ sirius::Density::generate                                       |      895.17 ms                             |      38                          |       34.02 s                              | 
  │ │ │ ├ sirius::Density::generate_valence                             |      519.44 ms                             |      38                          |       19.74 s                              | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       23.19 ms                             |     152                          |        3.53 s                              | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |        7.88 μs                             |     152                          |        1.20 ms                             | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       14.57 μs                             |       8                          |      116.54 μs                             | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       19.15 ms                             |     152                          |        2.91 s                              | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       29.89 ms                             |     152                          |        4.54 s                              | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.02 μs                             |     152                          |        1.37 ms                             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        1.46 ms                             |     152                          |      221.50 ms                             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       27.96 ms                             |     152                          |        4.25 s                              | 
  │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        3.74 ms                             |     152                          |      568.43 ms                             | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      584.24 ns                             |     152                          |       88.80 μs                             | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       42.65 ms                             |     152                          |        6.48 s                              | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.63 ms                             |      38                          |       62.10 ms                             | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.29 ms                             |      38                          |        3.36 s                              | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.06 ms                             |      38                          |        3.35 s                              | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      281.88 ms                             |      38                          |       10.71 s                              | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      281.88 ms                             |      38                          |       10.71 s                              | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.31 ms                             |      38                          |      923.85 ms                             | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      231.61 ms                             |      38                          |        8.80 s                              | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       24.26 ms                             |      38                          |      921.93 ms                             | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       82.06 ms                             |      38                          |        3.12 s                              | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        8.23 ms                             |      38                          |      312.74 ms                             | 
  │ │ ├ sirius::Density::mix                                            |      235.72 ms                             |      38                          |        8.96 s                              | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      942.50 μs                             |      38                          |       35.81 ms                             | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       11.14 ms                             |     514                          |        5.73 s                              | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.89 ms                             |     514                          |        5.60 s                              | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.89 ms                             |     514                          |        5.60 s                              | 
  │ │ │ └ sirius::Density::mixer_output                                 |        7.49 ms                             |      38                          |      284.44 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        6.63 ms                             |      38                          |      252.02 ms                             | 
  │ │ ├ sirius::Potential::generate                                     |      689.99 ms                             |      38                          |       26.22 s                              | 
  │ │ │ ├ sirius::Potential::poisson                                    |      137.35 ms                             |      38                          |        5.22 s                              | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       17.12 ms                             |      38                          |      650.60 ms                             | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.77 ms                             |      38                          |      409.30 ms                             | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.36 ms                             |      38                          |      393.77 ms                             | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.36 ms                             |      38                          |      393.75 ms                             | 
  │ │ │ ├ sirius::Periodic_function::add                                |      552.96 μs                             |      76                          |       42.02 ms                             | 
  │ │ │ ├ sirius::Potential::xc                                         |       53.51 ms                             |      38                          |        2.03 s                              | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       53.50 ms                             |      38                          |        2.03 s                              | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.01 ms                             |      76                          |      228.70 ms                             | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.29 ms                             |      38                          |      201.03 ms                             | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.73 ms                             |      38                          |      255.67 ms                             | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.89 ms                             |      38                          |        3.45 s                              | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      399.12 ms                             |      38                          |       15.17 s                              | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      285.42 ms                             |      38                          |       10.85 s                              | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      285.42 ms                             |      38                          |       10.85 s                              | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.33 ms                             |      38                          |        1.04 s                              | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      230.31 ms                             |      38                          |        8.75 s                              | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.98 ms                             |      38                          |      911.16 ms                             | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.99 ms                             |      38                          |      227.58 ms                             | 
  │ │ ├ sirius::Periodic_function|inner                                 |       11.03 ms                             |     266                          |        2.94 s                              | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |       10.66 ms                             |     266                          |        2.83 s                              | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |       10.66 ms                             |     266                          |        2.83 s                              | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.16 ms                             |     114                          |        1.16 s                              | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        9.88 ms                             |     114                          |        1.13 s                              | 
  │ │ ├ sirius::Periodic_function::integrate                            |        9.96 ms                             |      38                          |      378.61 ms                             | 
  │ │ └ sirius::Density::get_magnetisation                              |      114.31 μs                             |      38                          |        4.34 ms                             | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |      109.28 μs                             |      38                          |        4.15 ms                             | 
  │ ├ sirius::Density                                                   |                       133.95 ms            |                   1              |                       133.95 ms            | 
  │ │ └ sirius::Density::update                                         |                       123.39 ms            |                   1              |                       123.39 ms            | 
  │ │   └ sirius::Density::generate_pseudo_core_charge_density          |                       122.98 ms            |                   1              |                       122.98 ms            | 
  │ │     ├ sirius::Simulation_context::make_periodic_function          |                       112.92 ms            |                   1              |                       112.92 ms            | 
  │ │     └ sirius::Smooth_periodic_function::fft_transform             |                         5.28 ms            |                   1              |                         5.28 ms            | 
  │ ├ sirius::Hamiltonian0                                              |                         7.88 ms            |                  29              |                       228.43 ms            | 
  │ │ ├ sirius::Local_operator                                          |                         4.08 ms            |                  29              |                       118.32 ms            | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |                         2.22 ms            |                  29              |                        64.27 ms            | 
  │ │ ├ sirius::Non_local_operator                                      |                        64.40 μs            |                  58              |                         3.74 ms            | 
  │ │ ├ sirius::D_operator::initialize                                  |                         1.24 ms            |                  29              |                        35.90 ms            | 
  │ │ └ sirius::Q_operator::initialize                                  |                         2.37 ms            |                  29              |                        68.61 ms            | 
  │ ├ sirius::Band::solve                                               |                         8.68 s             |                  29              |                       251.84 s             | 
  │ │ ├ sirius::Hamiltonian_k                                           |                       320.91 μs            |                 116              |                        37.23 ms            | 
  │ │ │ ├ sirius::Local_operator::prepare_k                             |                       313.39 μs            |                 116              |                        36.35 ms            | 
  │ │ │ └ sirius::Beta_projectors_base::prepare                         |                         4.17 μs            |                 116              |                       483.51 μs            | 
  │ │ ├ sirius::Band::diag_pseudo_potential_davidson                    |                         2.17 s             |                 116              |                       251.79 s             | 
  │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                           |                         1.84 ms            |                 116              |                       212.93 ms            | 
  │ │ │ ├ sirius::Hamiltonian_k::apply_h_s                              |                        59.58 ms            |                1.12 K            |                        66.49 s             | 
  │ │ │ │ ├ sirius::Local_operator::apply_h                             |                        37.56 ms            |                1.12 K            |                        41.92 s             | 
  │ │ │ │ │ ├ sddk::matrix_storage::remap_forward                       |                         7.74 ms            |                1.12 K            |                         8.64 s             | 
  │ │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                 |                         5.92 ms            |                1.12 K            |                         6.60 s             | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_backward                      |                         8.19 ms            |                1.12 K            |                         9.14 s             | 
  │ │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                |                         5.19 ms            |                1.12 K            |                         5.79 s             | 
  │ │ │ │ ├ sirius::Beta_projectors_base::generate                      |                         1.51 ms            |                1.12 K            |                         1.68 s             | 
  │ │ │ │ ├ sirius::Beta_projectors_base::inner                         |                         7.27 ms            |                1.12 K            |                         8.12 s             | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                  |                         1.05 ms            |                1.12 K            |                         1.17 s             | 
  │ │ │ │ └ sirius::Non_local_operator::apply                           |                         6.60 ms            |                2.23 K            |                        14.74 s             | 
  │ │ │ ├ sddk::orthogonalize                                           |                        24.22 ms            |                1.12 K            |                        27.03 s             | 
  │ │ │ │ ├ sddk::wf_inner                                              |                         1.52 ms            |                2.12 K            |                         3.21 s             | 
  │ │ │ │ │ ├ sddk::wf_inner|scale                                      |                       130.25 ns            |                2.12 K            |                       275.62 μs            | 
  │ │ │ │ │ ├ sddk::wf_inner|pw                                         |                         1.49 ms            |                2.12 K            |                         3.15 s             | 
  │ │ │ │ │ └ sddk::wf_inner|scale_back                                 |                       314.23 ns            |                2.12 K            |                       664.91 μs            | 
  │ │ │ │ ├ sddk::orthogonalize|potrf                                   |                       709.25 μs            |                1.12 K            |                       791.52 ms            | 
  │ │ │ │ ├ sddk::orthogonalize|trtri                                   |                         1.15 ms            |                1.12 K            |                         1.28 s             | 
  │ │ │ │ └ sddk::wf_trans                                              |                         4.66 ms            |                4.35 K            |                        20.27 s             | 
  │ │ │ │   └ sddk::wf_trans|pw                                         |                         3.16 ms            |                6.35 K            |                        20.09 s             | 
  │ │ │ ├ sirius::Band::set_subspace_mtrx                               |                         3.53 ms            |                1.12 K            |                         3.94 s             | 
  │ │ │ │ └ sddk::wf_inner                                              |                         2.83 ms            |                1.12 K            |                         3.16 s             | 
  │ │ │ │   ├ sddk::wf_inner|scale                                      |                       133.75 ns            |                1.12 K            |                       149.26 μs            | 
  │ │ │ │   ├ sddk::wf_inner|pw                                         |                         2.81 ms            |                1.12 K            |                         3.13 s             | 
  │ │ │ │   └ sddk::wf_inner|scale_back                                 |                       362.93 ns            |                1.12 K            |                       405.03 μs            | 
  │ │ │ ├ Eigensolver_scalapack|pzheevx                                 |                       117.54 ms            |                1.12 K            |                       131.18 s             | 
  │ │ │ ├ sirius::residuals                                             |                         6.81 ms            |                1.09 K            |                         7.46 s             | 
  │ │ │ │ ├ sddk::wf_trans                                              |                         6.36 ms            |                1.00 K            |                         6.36 s             | 
  │ │ │ │ │ └ sddk::wf_trans|pw                                         |                         3.16 ms            |                2.00 K            |                         6.31 s             | 
  │ │ │ │ └ sirius::normalized_preconditioned_residuals                 |                       509.93 μs            |                1.00 K            |                       509.93 ms            | 
  │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|update_phi       |                        32.62 ms            |                 397              |                        12.95 s             | 
  │ │ │   └ sddk::wf_trans                                              |                        18.97 ms            |                 678              |                        12.86 s             | 
  │ │ │     └ sddk::wf_trans|pw                                         |                        13.32 ms            |                 959              |                        12.78 s             | 
  │ │ ├ sirius::Beta_projectors_base::dismiss                           |                       462.22 ns            |                 116              |                        53.62 μs            | 
  │ │ └ sirius::K_point_set::sync_band                                  |                       248.90 μs            |                  29              |                         7.22 ms            | 
  │ ├ sirius::K_point_set::find_band_occupancies                        |                       749.58 μs            |                  29              |                        21.74 ms            | 
  │ │ └ sirius::K_point_set::sync_band                                  |                        23.79 μs            |                  29              |                       689.81 μs            | 
  │ ├ sirius::Density::generate                                         |                       882.24 ms            |                  29              |                        25.59 s             | 
  │ │ ├ sirius::Density::generate_valence                               |                       526.08 ms            |                  29              |                        15.26 s             | 
  │ │ │ ├ sddk::matrix_storage::remap_forward                           |                        24.12 ms            |                 116              |                         2.80 s             | 
  │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                     |                        20.08 ms            |                 116              |                         2.33 s             | 
  │ │ │ ├ sirius::Density::add_k_point_contribution_dm                  |                        29.73 ms            |                 116              |                         3.45 s             | 
  │ │ │ │ ├ sirius::Beta_projectors_base::prepare                       |                        10.35 μs            |                 116              |                         1.20 ms            | 
  │ │ │ │ ├ sirius::Beta_projectors_base::generate                      |                         1.46 ms            |                 116              |                       168.88 ms            | 
  │ │ │ │ ├ sirius::Beta_projectors_base::inner                         |                        27.74 ms            |                 116              |                         3.22 s             | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                  |                         3.70 ms            |                 116              |                       428.63 ms            | 
  │ │ │ │ └ sirius::Beta_projectors_base::dismiss                       |                       480.31 ns            |                 116              |                        55.72 μs            | 
  │ │ │ ├ sirius::Density::add_k_point_contribution_rg                  |                        42.92 ms            |                 116              |                         4.98 s             | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |                         1.64 ms            |                  29              |                        47.61 ms            | 
  │ │ │ └ sirius::Density::augment                                      |                        88.93 ms            |                  29              |                         2.58 s             | 
  │ │ │   └ sirius::Density::generate_rho_aug                           |                        88.70 ms            |                  29              |                         2.57 s             | 
  │ │ ├ sirius::Field4D::symmetrize                                     |                       262.27 ms            |                  29              |                         7.61 s             | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |                       262.26 ms            |                  29              |                         7.61 s             | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |                        25.59 ms            |                  29              |                       742.07 ms            | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |                       211.11 ms            |                  29              |                         6.12 s             | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |                        24.33 ms            |                  29              |                       705.57 ms            | 
  │ │ ├ sirius::Density::symmetrize_density_matrix                      |                        81.17 ms            |                  29              |                         2.35 s             | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |                         9.06 ms            |                  29              |                       262.69 ms            | 
  │ ├ sirius::inner                                                     |                        10.42 ms            |                 357              |                         3.72 s             | 
  │ ├ sirius::Density::mix                                              |                       163.38 ms            |                  29              |                         4.74 s             | 
  │ │ ├ sirius::Density::mixer_input                                    |                         1.11 ms            |                  29              |                        32.27 ms            | 
  │ │ ├ sirius::inner                                                   |                        10.57 ms            |                 379              |                         4.00 s             | 
  │ │ └ sirius::Density::mixer_output                                   |                         6.57 ms            |                  29              |                       190.39 ms            | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |                         5.45 ms            |                  29              |                       158.01 ms            | 
  │ ├ sirius::Potential::generate                                       |                       662.86 ms            |                  29              |                        19.22 s             | 
  │ │ ├ sirius::Potential::poisson                                      |                       126.93 ms            |                  29              |                         3.68 s             | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |                         6.17 ms            |                  29              |                       178.91 ms            | 
  │ │ │ └ sirius::inner                                                 |                        10.81 ms            |                  29              |                       313.39 ms            | 
  │ │ ├ sirius::Periodic_function::add                                  |                       463.95 μs            |                  58              |                        26.91 ms            | 
  │ │ ├ sirius::Potential::xc                                           |                        34.52 ms            |                  29              |                         1.00 s             | 
  │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                          |                        32.17 ms            |                  29              |                       932.92 ms            | 
  │ │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                  |                        11.92 ms            |                  58              |                       691.08 ms            | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |                         5.08 ms            |                  29              |                       147.23 ms            | 
  │ │ ├ sirius::Potential::generate_D_operator_matrix                   |                        90.87 ms            |                  29              |                         2.64 s             | 
  │ │ └ sirius::Potential::generate_PAW_effective_potential             |                       400.56 ms            |                  29              |                        11.62 s             | 
  │ ├ sirius::Field4D::symmetrize                                       |                       260.21 ms            |                  29              |                         7.55 s             | 
  │ │ └ sirius::symmetrize_function|fpw                                 |                       260.20 ms            |                  29              |                         7.55 s             | 
  │ │   ├ sddk::Gvec_shells::remap_forward                              |                        23.84 ms            |                  29              |                       691.27 ms            | 
  │ │   ├ sirius::symmetrize_function|fpw|local                         |                       211.27 ms            |                  29              |                         6.13 s             | 
  │ │   └ sddk::Gvec_shells::remap_backward                             |                        23.95 ms            |                  29              |                       694.45 ms            | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |                         5.74 ms            |                  29              |                       166.49 ms            | 
  │ ├ sirius::Periodic_function::integrate                              |                        10.26 ms            |                  29              |                       297.43 ms            | 
  │ ├ sirius::Density::get_magnetisation                                |                        13.59 ms            |                  29              |                       394.14 ms            | 
  │ │ └ sirius::Density::compute_atomic_mag_mom                         |                        13.58 ms            |                  29              |                       393.95 ms            | 
+ │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.39 ms →        4.63 ms  (-14.25%) |       2   →       2              |       10.79 ms →        9.25 ms  (-14.25%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.25 ms                             |       6                          |       61.48 ms                             | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.23 ms                             |       6                          |       61.41 ms                             | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.23 ms                             |       6                          |       61.41 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner                            |        9.81 ms                             |       3                          |       29.43 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.74 ms                             |       3                          |       29.23 ms                             | 
  ├ sirius::Periodic_function|inner                                     |       10.20 ms                             |       2                          |       20.41 ms                             | 
  │ └ sirius::Periodic_function|inner_local                             |       10.20 ms                             |       2                          |       20.40 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.20 ms                             |       2                          |       20.40 ms                             | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.00 ms                             |       1                          |       10.00 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        9.71 ms                             |       1                          |        9.71 ms                             | 
  ├ sirius::inner                                                       |                        10.56 ms            |                   3              |                        31.69 ms            | 
+ └ sirius::finalize                                                    |      396.49 ms →      324.87 ms  (-18.06%) |       1   →       1              |      396.49 ms →      324.87 ms  (-18.06%) | 
  ====================================================================================================================================================================================================
```
