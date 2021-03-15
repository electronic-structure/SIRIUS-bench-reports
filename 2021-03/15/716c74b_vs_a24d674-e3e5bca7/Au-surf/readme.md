# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs 716c74b9e40f2dc514547b13861ce8c977f50e6c
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      151.04 s  →      124.80 s   (-17.37%) |       1   →       1              |      151.04 s  →      124.80 s   (-17.37%) | 
  ├ sirius::initialize                                                  |        2.75 s  →        2.77 s    (+0.47%) |       1   →       1              |        2.75 s  →        2.77 s    (+0.47%) | 
+ ├ sirius::Simulation_context::initialize                              |        3.04 s  →        2.01 s   (-33.83%) |       1   →       1              |        3.04 s  →        2.01 s   (-33.83%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       34.30 ms →        7.81 ms  (-77.23%) |       1   →       1              |       34.30 ms →        7.81 ms  (-77.23%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |        1.07 s  →       64.45 ms  (-93.96%) |       1   →       1              |        1.07 s  →       64.45 ms  (-93.96%) | 
+ │ │ ├ sirius::Atom_type::init                                         |        1.05 s  →       40.10 ms  (-96.19%) |       1   →       1              |        1.05 s  →       40.10 ms  (-96.19%) | 
- │ │ └ sirius::Unit_cell::update                                       |       15.21 ms →       24.20 ms  (+59.13%) |       1   →       1              |       15.21 ms →       24.20 ms  (+59.13%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        9.28 ms →        9.81 ms   (+5.77%) |       1   →       1              |        9.28 ms →        9.81 ms   (+5.77%) | 
- │ │   └ sirius::Unit_cell::get_symmetry                               |        5.90 ms →       14.36 ms (+143.21%) |       1   →       1              |        5.90 ms →       14.36 ms (+143.21%) | 
- │ │     └ sirius::Unit_cell_symmetry                                  |        5.61 ms →       13.68 ms (+143.72%) |       1   →       1              |        5.61 ms →       13.68 ms (+143.72%) | 
- │ │       ├ sirius::Unit_cell_symmetry|spg                            |        5.40 ms →       13.44 ms (+149.18%) |       1   →       1              |        5.40 ms →       13.44 ms (+149.18%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      201.17 μs →      217.08 μs   (+7.91%) |       1   →       1              |      201.17 μs →      217.08 μs   (+7.91%) | 
- │ │       └ sirius::Unit_cell_symmetry|mag                            |        2.26 μs →        2.76 μs  (+22.16%) |       1   →       1              |        2.26 μs →        2.76 μs  (+22.16%) | 
  │ └ sirius::Simulation_context::update                                |        1.89 s  →        1.89 s    (+0.00%) |       1   →       1              |        1.89 s  →        1.89 s    (+0.00%) | 
  │   ├ sirius::Unit_cell::update                                       |       11.34 ms →       11.51 ms   (+1.47%) |       1   →       1              |       11.34 ms →       11.51 ms   (+1.47%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        8.32 ms →        8.33 ms   (+0.14%) |       1   →       1              |        8.32 ms →        8.33 ms   (+0.14%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.00 ms →        3.16 ms   (+5.16%) |       1   →       1              |        3.00 ms →        3.16 ms   (+5.16%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        2.71 ms →        2.62 ms   (-3.32%) |       1   →       1              |        2.71 ms →        2.62 ms   (-3.32%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.51 ms →        2.41 ms   (-3.78%) |       1   →       1              |        2.51 ms →        2.41 ms   (-3.78%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      199.88 μs →      204.89 μs   (+2.50%) |       1   →       1              |      199.88 μs →      204.89 μs   (+2.50%) | 
- │   │     └ sirius::Unit_cell_symmetry|mag                            |        1.08 μs →        1.22 μs  (+12.53%) |       1   →       1              |        1.08 μs →        1.22 μs  (+12.53%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       18.77 ms →       18.33 ms   (-2.34%) |       2   →       2              |       37.55 ms →       36.67 ms   (-2.34%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        1.10 ms →        1.09 ms   (-0.55%) |       2   →       2              |        2.20 ms →        2.19 ms   (-0.55%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |      955.81 μs →      956.82 μs   (+0.11%) |       1   →       1              |      955.81 μs →      956.82 μs   (+0.11%) | 
- │   ├ sirius::Radial_integrals|vloc                                   |        4.55 ms →        5.25 ms  (+15.38%) |       2   →       2              |        9.10 ms →       10.49 ms  (+15.38%) | 
  │   ├ sirius::Radial_integrals|beta                                   |        3.65 ms →        3.71 ms   (+1.71%) |       2   →       2              |        7.30 ms →        7.43 ms   (+1.71%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       15.57 ms →       15.79 ms   (+1.43%) |       4   →       4              |       62.27 ms →       63.15 ms   (+1.43%) | 
  │   ├ sddk::Gvec::init                                                |      161.86 ms →      157.72 ms   (-2.56%) |       2   →       2              |      323.72 ms →      315.43 ms   (-2.56%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      127.64 ms →      125.30 ms   (-1.83%) |       2   →       2              |      255.28 ms →      250.60 ms   (-1.83%) | 
- │   ├ sddk::Gvec_shells                                               |      116.14 ms →      128.82 ms  (+10.91%) |       1   →       1              |      116.14 ms →      128.82 ms  (+10.91%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.04 ms →        1.03 ms   (-0.74%) |       1   →       1              |        1.04 ms →        1.03 ms   (-0.74%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      217.67 ms →      217.12 ms   (-0.25%) |       1   →       1              |      217.67 ms →      217.12 ms   (-0.25%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       27.27 ms →       25.50 ms   (-6.50%) |       1   →       1              |       27.27 ms →       25.50 ms   (-6.50%) | 
- │ ├ sirius::K_point::K_point                                          |        1.86 μs →        5.24 μs (+182.38%) |       2   →       2              |        3.71 μs →       10.48 μs (+182.38%) | 
  │ └ sirius::K_point_set::initialize                                   |       27.25 ms →       25.45 ms   (-6.58%) |       1   →       1              |       27.25 ms →       25.45 ms   (-6.58%) | 
  │   └ sirius::K_point::initialize                                     |       27.19 ms →       25.40 ms   (-6.61%) |       1   →       1              |       27.19 ms →       25.40 ms   (-6.61%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       20.65 ms →       19.12 ms   (-7.43%) |       1   →       1              |       20.65 ms →       19.12 ms   (-7.43%) | 
+ │     │ └ sddk::Gvec::init                                            |        5.38 ms →        4.64 ms  (-13.64%) |       1   →       1              |        5.38 ms →        4.64 ms  (-13.64%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        8.68 μs                             |       1                          |        8.68 μs                             | 
  │     └ sirius::K_point::update                                       |        4.25 ms →        3.96 ms   (-6.75%) |       1   →       1              |        4.25 ms →        3.96 ms   (-6.75%) | 
  │       └ sirius::Beta_projectors                                     |        1.67 ms →        1.67 ms   (+0.41%) |       1   →       1              |        1.67 ms →        1.67 ms   (+0.41%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      895.80 μs →      904.04 μs   (+0.92%) |       1   →       1              |      895.80 μs →      904.04 μs   (+0.92%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.21 ms                             |       2                          |        4.42 ms                             | 
  ├ sirius::Potential                                                   |       91.37 ms →       92.36 ms   (+1.08%) |       1   →       1              |       91.37 ms →       92.36 ms   (+1.08%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.42 ms                             |       6                          |       14.53 ms                             | 
  │ └ sirius::Potential::update                                         |       76.51 ms →       77.34 ms   (+1.09%) |       1   →       1              |       76.51 ms →       77.34 ms   (+1.09%) | 
  │   └ sirius::Potential::generate_local_potential                     |       76.33 ms →       77.16 ms   (+1.09%) |       1   →       1              |       76.33 ms →       77.16 ms   (+1.09%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       59.61 ms →       50.13 ms  (-15.90%) |       1   →       1              |       59.61 ms →       50.13 ms  (-15.90%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       16.54 ms →       10.22 ms  (-38.19%) |       1   →       1              |       16.54 ms →       10.22 ms  (-38.19%) | 
  ├ sirius::Density                                                     |       71.77 ms →       74.66 ms   (+4.03%) |       1   →       1              |       71.77 ms →       74.66 ms   (+4.03%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        4.75 ms                             |       2                          |        9.51 ms                             | 
  │ └ sirius::Density::update                                           |       62.14 ms →       64.96 ms   (+4.53%) |       1   →       1              |       62.14 ms →       64.96 ms   (+4.53%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       61.95 ms →       64.79 ms   (+4.58%) |       1   →       1              |       61.95 ms →       64.79 ms   (+4.58%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       59.31 ms →       52.53 ms  (-11.42%) |       1   →       1              |       59.31 ms →       52.53 ms  (-11.42%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        2.45 ms →        7.75 ms (+216.60%) |       1   →       1              |        2.45 ms →        7.75 ms (+216.60%) | 
  ├ sirius::Density::initial_density                                    |       79.10 ms →       79.65 ms   (+0.70%) |       1   →       1              |       79.10 ms →       79.65 ms   (+0.70%) | 
+ │ ├ sirius::Simulation_context::make_periodic_function                |       58.60 ms →       51.92 ms  (-11.41%) |       1   →       1              |       58.60 ms →       51.92 ms  (-11.41%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        2.36 ms →        5.65 ms (+139.78%) |       2   →       2              |        4.71 ms →       11.30 ms (+139.78%) | 
  │ └ sirius::Periodic_function::integrate                              |        4.17 ms →        3.89 ms   (-6.79%) |       1   →       1              |        4.17 ms →        3.89 ms   (-6.79%) | 
- ├ sirius::Potential::generate                                         |      195.76 ms →      221.52 ms  (+13.16%) |       1   →       1              |      195.76 ms →      221.52 ms  (+13.16%) | 
  │ ├ sirius::Potential::poisson                                        |       64.64 ms →       64.07 ms   (-0.87%) |       1   →       1              |       64.64 ms →       64.07 ms   (-0.87%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.33 ms →        9.15 ms (+292.07%) |       1   →       1              |        2.33 ms →        9.15 ms (+292.07%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.24 ms                             |       1                          |        4.24 ms                             | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.05 ms                             |       1                          |        4.05 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.05 ms                             |       1                          |        4.05 ms                             | 
  │ │ └ sirius::inner                                                   |                         4.47 ms            |                   1              |                         4.47 ms            | 
+ │ ├ sirius::Periodic_function::add                                    |      238.28 μs →      198.85 μs  (-16.55%) |       2   →       2              |      476.56 μs →      397.71 μs  (-16.55%) | 
- │ ├ sirius::Potential::xc                                             |      104.56 ms →      129.07 ms  (+23.44%) |       1   →       1              |      104.56 ms →      129.07 ms  (+23.44%) | 
- │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |      104.56 ms →      128.02 ms  (+22.44%) |       1   →       1              |      104.56 ms →      128.02 ms  (+22.44%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.25 ms                             |       5                          |       11.26 ms                             | 
- │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        2.65 ms →        2.62 ms   (-1.12%) |       9   →      12    (+33.33%) |       23.86 ms →       31.45 ms  (+31.84%) | 
  │ │   ├ sirius::gradient                                              |        7.50 ms →        7.63 ms   (+1.74%) |       1   →       1              |        7.50 ms →        7.63 ms   (+1.74%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.41 ms                             |       3                          |        7.22 ms                             | 
  │ │   ├ sirius::dot                                                   |        2.77 ms →        2.82 ms   (+2.03%) |       1   →       1              |        2.77 ms →        2.82 ms   (+2.03%) | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.56 ms                             |       1                          |        2.56 ms                             | 
  │ │   ├ sirius::Potential::xc_rg_nonmagnetic|libxc                    |                        11.31 ms            |                   2              |                        22.62 ms            | 
- │ │   └ sirius::divergence                                            |       23.07 ms →       19.58 ms  (-15.15%) |       1   →       2   (+100.00%) |       23.07 ms →       39.15 ms  (+69.70%) | 
  │ │     └ sirius::Smooth_periodic_function                            |        2.41 ms                             |       1                          |        2.41 ms                             | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.27 ms →        3.33 ms   (+1.63%) |       1   →       1              |        3.27 ms →        3.33 ms   (+1.63%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       22.28 ms →       22.83 ms   (+2.48%) |       1   →       1              |       22.28 ms →       22.83 ms   (+2.48%) | 
+ │ └ sirius::Potential::generate_PAW_effective_potential               |      206.00 ns →      132.00 ns  (-35.92%) |       1   →       1              |      206.00 ns →      132.00 ns  (-35.92%) | 
- ├ sirius::Hamiltonian0                                                |       13.87 ms →       16.04 ms  (+15.59%) |       1   →       1              |       13.87 ms →       16.04 ms  (+15.59%) | 
  │ ├ sirius::Local_operator                                            |       13.52 ms →       14.19 ms   (+4.93%) |       1   →       1              |       13.52 ms →       14.19 ms   (+4.93%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        7.07 ms                             |       1                          |        7.07 ms                             | 
- │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        4.98 ms →        5.61 ms  (+12.75%) |       1   →       1              |        4.98 ms →        5.61 ms  (+12.75%) | 
  │ ├ sirius::Non_local_operator                                        |       61.92 μs →       59.03 μs   (-4.68%) |       2   →       2              |      123.85 μs →      118.05 μs   (-4.68%) | 
- │ ├ sirius::D_operator::initialize                                    |       89.21 μs →      592.08 μs (+563.72%) |       1   →       1              |       89.21 μs →      592.08 μs (+563.72%) | 
- │ └ sirius::Q_operator::initialize                                    |       74.29 μs →        1.07 ms (+1343.29%) |       1   →       1              |       74.29 μs →        1.07 ms (+1343.29%) | 
  ├ sirius::Band::initialize_subspace                                   |        2.19 s  →        2.25 s    (+2.46%) |       1   →       1              |        2.19 s  →        2.25 s    (+2.46%) | 
  │ ├ sirius::Hamiltonian_k                                             |        7.14 ms →        7.16 ms   (+0.28%) |       1   →       1              |        7.14 ms →        7.16 ms   (+0.28%) | 
- │ │ ├ sirius::Local_operator::prepare_k                               |      247.78 μs →      278.19 μs  (+12.28%) |       1   →       1              |      247.78 μs →      278.19 μs  (+12.28%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        6.89 ms →        6.87 ms   (-0.19%) |       1   →       1              |        6.89 ms →        6.87 ms   (-0.19%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        2.19 s  →        2.24 s    (+2.38%) |       1   →       1              |        2.19 s  →        2.24 s    (+2.38%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       87.98 ms                             |       4                          |      351.93 ms                             | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       25.04 ms →       25.78 ms   (+2.98%) |       1   →       1              |       25.04 ms →       25.78 ms   (+2.98%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       14.39 ms →       14.95 ms   (+3.85%) |       1   →       1              |       14.39 ms →       14.95 ms   (+3.85%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |        1.21 s  →        1.21 s    (-0.39%) |       1   →       1              |        1.21 s  →        1.21 s    (-0.39%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      991.09 ms →      983.70 ms   (-0.75%) |       1   →       1              |      991.09 ms →      983.70 ms   (-0.75%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |      322.45 ms →      309.56 ms   (-4.00%) |       1   →       1              |      322.45 ms →      309.56 ms   (-4.00%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |      173.88 ms                             |       1                          |      173.88 ms                             | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |      173.87 ms                             |       1                          |      173.87 ms                             | 
+ │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |      130.00 ms →      116.04 ms  (-10.74%) |       1   →       1              |      130.00 ms →      116.04 ms  (-10.74%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      174.36 ms                             |       1                          |      174.36 ms                             | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |      174.35 ms                             |       1                          |      174.35 ms                             | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      160.26 ms →      164.83 ms   (+2.85%) |       1   →       1              |      160.26 ms →      164.83 ms   (+2.85%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |      109.60 ms →      114.43 ms   (+4.41%) |       1   →       1              |      109.60 ms →      114.43 ms   (+4.41%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.72 ms →        3.73 ms   (+0.31%) |       1   →       1              |        3.72 ms →        3.73 ms   (+0.31%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       89.16 ms →       90.98 ms   (+2.04%) |       1   →       1              |       89.16 ms →       90.98 ms   (+2.04%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |       11.48 ms →       13.09 ms  (+14.00%) |       1   →       1              |       11.48 ms →       13.09 ms  (+14.00%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       64.19 ms →       64.58 ms   (+0.61%) |       2   →       2              |      128.37 ms →      129.16 ms   (+0.61%) | 
- │ │ ├ sirius::Band::set_subspace_mtrx                                 |       58.33 ms →       85.18 ms  (+46.03%) |       2   →       2              |      116.67 ms →      170.37 ms  (+46.03%) | 
  │ │ │ ├ sddk::inner                                                   |       58.22 ms                             |       2                          |      116.44 ms                             | 
  │ │ │ │ ├ sddk::inner|local                                           |       21.24 μs                             |       2                          |       42.47 μs                             | 
  │ │ │ │ ├ sddk::inner|device_copy                                     |       25.55 ms                             |       4                          |      102.21 ms                             | 
  │ │ │ │ ├ sddk::inner|store                                           |      688.91 μs                             |       4                          |        2.76 ms                             | 
  │ │ │ │ └ sddk::inner|mpi                                             |        5.71 ms                             |       2                          |       11.41 ms                             | 
  │ │ │ └ sddk::wf_inner                                                |                        85.08 ms            |                   2              |                       170.15 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                       161.50 ns            |                   2              |                       323.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        83.51 ms            |                   2              |                       167.03 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                       642.50 ns            |                   2              |                         1.28 μs            | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      117.91 ms →      118.22 ms   (+0.26%) |       1   →       1              |      117.91 ms →      118.22 ms   (+0.26%) | 
  │ │ ├ sddk::transform                                                 |       36.02 ms                             |       1                          |       36.02 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       16.38 μs                             |       1                          |       16.38 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       20.60 μs                             |       1                          |       20.60 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                        35.32 ms            |                   1              |                        35.32 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                        35.30 ms            |                   1              |                        35.30 ms            | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      460.00 ns →      632.00 ns  (+37.39%) |       1   →       1              |      460.00 ns →      632.00 ns  (+37.39%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      141.34 s  →      116.29 s   (-17.72%) |       1   →       1              |      141.34 s  →      116.29 s   (-17.72%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.13 ms                             |      31                          |       66.02 ms                             | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.28 s                              |      43                          |      141.09 s                              | 
  │ │ ├ sirius::Hamiltonian0                                            |        7.22 ms                             |      43                          |      310.27 ms                             | 
  │ │ │ ├ sirius::Local_operator                                        |        6.88 ms                             |      43                          |      295.64 ms                             | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |        1.51 ms                             |      43                          |       64.87 ms                             | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.91 ms                             |      43                          |      168.24 ms                             | 
  │ │ │ ├ sirius::Non_local_operator                                    |       62.07 μs                             |      86                          |        5.34 ms                             | 
  │ │ │ ├ sirius::D_operator::initialize                                |       84.39 μs                             |      43                          |        3.63 ms                             | 
  │ │ │ └ sirius::Q_operator::initialize                                |       70.69 μs                             |      43                          |        3.04 ms                             | 
  │ │ ├ sirius::Band::solve                                             |        2.61 s                              |      43                          |      112.28 s                              | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      213.37 μs                             |      43                          |        9.18 ms                             | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      206.30 μs                             |      43                          |        8.87 ms                             | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.33 μs                             |      43                          |      229.32 μs                             | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.60 s                              |      43                          |      111.61 s                              | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       69.21 ms                             |      43                          |        2.98 s                              | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        5.44 ms                             |     258                          |        1.40 s                              | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        2.04 ms                             |      43                          |       87.75 ms                             | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      419.00 μs                             |      43                          |       18.02 ms                             | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      947.22 μs                             |      43                          |       40.73 ms                             | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.50 s                              |      43                          |      107.51 s                              | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      214.06 ms                             |     208                          |       44.52 s                              | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |      151.51 ms                             |     208                          |       31.51 s                              | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |       27.26 ms                             |     208                          |        5.67 s                              | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      678.94 μs                             |     208                          |      141.22 ms                             | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        3.27 ms                             |      43                          |      140.79 ms                             | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |       22.09 ms                             |     208                          |        4.59 s                              | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      675.72 μs                             |     208                          |      140.55 ms                             | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |        3.26 ms                             |      43                          |      140.02 ms                             | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       33.93 ms                             |     208                          |        7.06 s                              | 
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |       21.14 ms                             |     208                          |        4.40 s                              | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.66 ms                             |     208                          |      552.92 ms                             | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       22.44 ms                             |     208                          |        4.67 s                              | 
  │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        2.22 ms                             |     208                          |      462.58 ms                             | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       18.71 ms                             |     416                          |        7.78 s                              | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       82.32 ms                             |     208                          |       17.12 s                              | 
  │ │ │ │   │ ├ sddk::inner                                             |       10.42 ms                             |     373                          |        3.89 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|local                                     |       18.90 μs                             |     373                          |        7.05 ms                             | 
  │ │ │ │   │ │ ├ sddk::inner|device_copy                               |        4.46 ms                             |     746                          |        3.33 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|store                                     |      102.33 μs                             |     746                          |       76.34 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|mpi                                       |        1.26 ms                             |     373                          |      471.18 ms                             | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |       30.34 ms                             |     208                          |        6.31 s                              | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       16.23 ms                             |     208                          |        3.38 s                              | 
  │ │ │ │   │ └ sddk::transform                                         |       21.51 ms                             |     165                          |        3.55 s                              | 
  │ │ │ │   │   ├ sddk::transform|init                                  |       19.66 μs                             |     165                          |        3.24 ms                             | 
  │ │ │ │   │   └ sddk::transform|local                                 |       53.36 μs                             |     495                          |       26.41 ms                             | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       24.96 ms                             |     208                          |        5.19 s                              | 
  │ │ │ │   │ └ sddk::inner                                             |       20.79 ms                             |     208                          |        4.32 s                              | 
  │ │ │ │   │   ├ sddk::inner|local                                     |       42.80 μs                             |     208                          |        8.90 ms                             | 
  │ │ │ │   │   ├ sddk::inner|device_copy                               |        7.92 ms                             |     416                          |        3.30 s                              | 
  │ │ │ │   │   ├ sddk::inner|store                                     |      229.25 μs                             |     416                          |       95.37 ms                             | 
  │ │ │ │   │   └ sddk::inner|mpi                                       |        4.44 ms                             |     208                          |      923.93 ms                             | 
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |      165.29 ms                             |     208                          |       34.38 s                              | 
  │ │ │ │   ├ sirius::residuals                                         |       19.43 ms                             |     207                          |        4.02 s                              | 
  │ │ │ │   │ ├ sddk::transform                                         |       20.06 ms                             |     171                          |        3.43 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       15.74 μs                             |     171                          |        2.69 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       55.14 μs                             |     342                          |       18.86 ms                             | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        2.72 ms                             |     171                          |      465.79 ms                             | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       51.25 ms                             |      44                          |        2.26 s                              | 
  │ │ │ │     └ sddk::transform                                         |       49.82 ms                             |      45                          |        2.24 s                              | 
  │ │ │ │       ├ sddk::transform|init                                  |       12.62 μs                             |      45                          |      567.91 μs                             | 
  │ │ │ │       └ sddk::transform|local                                 |       16.18 μs                             |      46                          |      744.46 μs                             | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      568.40 ns                             |      43                          |       24.44 μs                             | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       24.76 μs                             |      43                          |        1.06 ms                             | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |        3.41 ms                             |      43                          |      146.80 ms                             | 
  │ │ ├ sirius::Density::generate                                       |      293.47 ms                             |      43                          |       12.62 s                              | 
  │ │ │ ├ sirius::Density::generate_valence                             |      289.55 ms                             |      43                          |       12.45 s                              | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       67.11 ms                             |      43                          |        2.89 s                              | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       62.29 μs                             |      43                          |        2.68 ms                             | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |        1.18 ms                             |       2                          |        2.36 ms                             | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       55.86 ms                             |      43                          |        2.40 s                              | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       59.83 ms                             |      43                          |        2.57 s                              | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.54 μs                             |      43                          |      410.28 μs                             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        2.31 ms                             |      43                          |       99.24 ms                             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       56.97 ms                             |      43                          |        2.45 s                              | 
  │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        5.55 ms                             |      43                          |      238.65 ms                             | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      560.30 ns                             |      43                          |       24.09 μs                             | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      104.44 ms                             |      43                          |        4.49 s                              | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.40 ms                             |      43                          |      103.36 ms                             | 
  │ │ │ │ └ sirius::Density::augment                                    |       20.07 ms                             |      43                          |      863.17 ms                             | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       19.90 ms                             |      43                          |      855.87 ms                             | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      267.23 ns                             |      43                          |       11.49 μs                             | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |        1.26 ms                             |      43                          |       54.00 ms                             | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        2.66 ms                             |      43                          |      114.49 ms                             | 
  │ │ ├ sirius::Density::mix                                            |      131.69 ms                             |      43                          |        5.66 s                              | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      260.97 μs                             |      43                          |       11.22 ms                             | 
  │ │ │ └ sirius::Density::mixer_output                                 |        3.57 ms                             |      43                          |      153.37 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        3.38 ms                             |      43                          |      145.20 ms                             | 
  │ │ ├ sirius::Potential::generate                                     |      186.08 ms                             |      43                          |        8.00 s                              | 
  │ │ │ ├ sirius::Potential::poisson                                    |       64.73 ms                             |      43                          |        2.78 s                              | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.38 ms                             |      43                          |      102.19 ms                             | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |        4.21 ms                             |      43                          |      181.12 ms                             | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.13 ms                             |      43                          |      177.44 ms                             | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.13 ms                             |      43                          |      177.40 ms                             | 
  │ │ │ ├ sirius::Periodic_function::add                                |      233.74 μs                             |      86                          |       20.10 ms                             | 
  │ │ │ ├ sirius::Potential::xc                                         |       96.11 ms                             |      43                          |        4.13 s                              | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       96.11 ms                             |      43                          |        4.13 s                              | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        1.65 ms                             |     215                          |      354.72 ms                             | 
  │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |        2.34 ms                             |     387                          |      906.44 ms                             | 
  │ │ │ │   ├ sirius::gradient                                          |        2.42 ms                             |      43                          |      103.89 ms                             | 
  │ │ │ │   │ └ sirius::Smooth_periodic_function                        |      713.60 μs                             |     129                          |       92.05 ms                             | 
  │ │ │ │   ├ sirius::dot                                               |        2.81 ms                             |      43                          |      120.79 ms                             | 
  │ │ │ │   │ └ sirius::Smooth_periodic_function                        |        2.56 ms                             |      43                          |      110.18 ms                             | 
  │ │ │ │   └ sirius::divergence                                        |       23.39 ms                             |      43                          |        1.01 s                              | 
  │ │ │ │     └ sirius::Smooth_periodic_function                        |        2.43 ms                             |      43                          |      104.59 ms                             | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.31 ms                             |      43                          |      142.36 ms                             | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       20.92 ms                             |      43                          |      899.40 ms                             | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      221.35 ns                             |      43                          |        9.52 μs                             | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      284.37 ns                             |      43                          |       12.23 μs                             | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.23 ms                             |      43                          |       95.85 ms                             | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.11 ms                             |     301                          |        1.24 s                              | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        3.92 ms                             |     301                          |        1.18 s                              | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        3.92 ms                             |     301                          |        1.18 s                              | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.27 ms                             |     129                          |      551.01 ms                             | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.07 ms                             |     129                          |      524.50 ms                             | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.07 ms                             |      43                          |      174.81 ms                             | 
  │ │ └ sirius::Density::get_magnetisation                              |      102.21 μs                             |      43                          |        4.39 ms                             | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |       98.61 μs                             |      43                          |        4.24 ms                             | 
  │ ├ sirius::Density                                                   |                       116.13 ms            |                   1              |                       116.13 ms            | 
  │ │ └ sirius::Density::update                                         |                       106.64 ms            |                   1              |                       106.64 ms            | 
  │ │   └ sirius::Density::generate_pseudo_core_charge_density          |                       106.46 ms            |                   1              |                       106.46 ms            | 
  │ │     ├ sirius::Simulation_context::make_periodic_function          |                        52.63 ms            |                   1              |                        52.63 ms            | 
  │ │     └ sirius::Smooth_periodic_function::fft_transform             |                         7.73 ms            |                   1              |                         7.73 ms            | 
  │ ├ sirius::Hamiltonian0                                              |                         8.54 ms            |                  45              |                       384.41 ms            | 
  │ │ ├ sirius::Local_operator                                          |                         6.69 ms            |                  45              |                       301.04 ms            | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |                         3.71 ms            |                  45              |                       167.03 ms            | 
  │ │ ├ sirius::Non_local_operator                                      |                        59.57 μs            |                  90              |                         5.36 ms            | 
  │ │ ├ sirius::D_operator::initialize                                  |                       593.69 μs            |                  45              |                        26.72 ms            | 
  │ │ └ sirius::Q_operator::initialize                                  |                         1.08 ms            |                  45              |                        48.64 ms            | 
  │ ├ sirius::Band::solve                                               |                         1.87 s             |                  45              |                        84.31 s             | 
  │ │ ├ sirius::Hamiltonian_k                                           |                       220.58 μs            |                  45              |                         9.93 ms            | 
  │ │ │ ├ sirius::Local_operator::prepare_k                             |                       210.83 μs            |                  45              |                         9.49 ms            | 
  │ │ │ └ sirius::Beta_projectors_base::prepare                         |                         5.16 μs            |                  45              |                       232.06 μs            | 
  │ │ ├ sirius::Band::diag_pseudo_potential_davidson                    |                         1.84 s             |                  45              |                        82.69 s             | 
  │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                           |                         1.63 ms            |                  45              |                        73.13 ms            | 
  │ │ │ ├ sirius::Hamiltonian_k::apply_h_s                              |                       206.09 ms            |                 209              |                        43.07 s             | 
  │ │ │ │ ├ sirius::Local_operator::apply_h                             |                       145.56 ms            |                 209              |                        30.42 s             | 
  │ │ │ │ │ ├ sddk::matrix_storage::remap_forward                       |                        26.42 ms            |                 209              |                         5.52 s             | 
  │ │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                 |                        21.49 ms            |                 209              |                         4.49 s             | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_backward                      |                        33.07 ms            |                 209              |                         6.91 s             | 
  │ │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                |                        20.90 ms            |                 209              |                         4.37 s             | 
  │ │ │ │ ├ sirius::Beta_projectors_base::generate                      |                         2.64 ms            |                 209              |                       551.55 ms            | 
  │ │ │ │ ├ sirius::Beta_projectors_base::inner                         |                        21.95 ms            |                 209              |                         4.59 s             | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                  |                         2.57 ms            |                 209              |                       536.19 ms            | 
  │ │ │ │ └ sirius::Non_local_operator::apply                           |                        17.95 ms            |                 418              |                         7.51 s             | 
  │ │ │ ├ sddk::orthogonalize                                           |                        75.71 ms            |                 209              |                        15.82 s             | 
  │ │ │ │ ├ sddk::wf_inner                                              |                        12.21 ms            |                 373              |                         4.55 s             | 
  │ │ │ │ │ ├ sddk::wf_inner|scale                                      |                       192.35 ns            |                 373              |                        71.75 μs            | 
  │ │ │ │ │ ├ sddk::wf_inner|pw                                         |                         8.73 ms            |                 373              |                         3.26 s             | 
  │ │ │ │ │ └ sddk::wf_inner|scale_back                                 |                       323.89 ns            |                 373              |                       120.81 μs            | 
  │ │ │ │ ├ sddk::orthogonalize|tmtrx                                   |                        27.23 ms            |                 209              |                         5.69 s             | 
  │ │ │ │ ├ sddk::orthogonalize|transform                               |                        15.90 ms            |                 209              |                         3.32 s             | 
  │ │ │ │ └ sddk::wf_trans                                              |                        13.75 ms            |                 164              |                         2.25 s             | 
  │ │ │ │   └ sddk::wf_trans|pw                                         |                         4.55 ms            |                 492              |                         2.24 s             | 
  │ │ │ ├ sirius::Band::set_subspace_mtrx                               |                        21.81 ms            |                 209              |                         4.56 s             | 
  │ │ │ │ └ sddk::wf_inner                                              |                        20.88 ms            |                 209              |                         4.36 s             | 
  │ │ │ │   ├ sddk::wf_inner|scale                                      |                       231.03 ns            |                 209              |                        48.29 μs            | 
  │ │ │ │   ├ sddk::wf_inner|pw                                         |                        14.91 ms            |                 209              |                         3.12 s             | 
  │ │ │ │   └ sddk::wf_inner|scale_back                                 |                       471.21 ns            |                 209              |                        98.48 μs            | 
  │ │ │ ├ Eigensolver_cuda|zheevdx                                      |                        38.62 ms            |                 209              |                         8.07 s             | 
  │ │ │ ├ sirius::residuals                                             |                        15.09 ms            |                 204              |                         3.08 s             | 
  │ │ │ │ ├ sddk::wf_trans                                              |                        14.08 ms            |                 184              |                         2.59 s             | 
  │ │ │ │ │ └ sddk::wf_trans|pw                                         |                         6.85 ms            |                 368              |                         2.52 s             | 
  │ │ │ │ └ sirius::normalized_preconditioned_residuals                 |                         1.41 ms            |                 184              |                       260.32 ms            | 
  │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|update_phi       |                        50.61 ms            |                  86              |                         4.35 s             | 
  │ │ │   └ sddk::wf_trans                                              |                        33.40 ms            |                 127              |                         4.24 s             | 
  │ │ │     └ sddk::wf_trans|pw                                         |                        25.13 ms            |                 168              |                         4.22 s             | 
  │ │ ├ sirius::Beta_projectors_base::dismiss                           |                       554.67 ns            |                  45              |                        24.96 μs            | 
  │ │ └ sirius::K_point_set::sync_band                                  |                        95.28 μs            |                  45              |                         4.29 ms            | 
  │ ├ sirius::K_point_set::find_band_occupancies                        |                       968.35 μs            |                  45              |                        43.58 ms            | 
  │ │ └ sirius::K_point_set::sync_band                                  |                        23.46 μs            |                  45              |                         1.06 ms            | 
  │ ├ sirius::Density::generate                                         |                       301.15 ms            |                  45              |                        13.55 s             | 
  │ │ ├ sirius::Density::generate_valence                               |                       297.19 ms            |                  45              |                        13.37 s             | 
  │ │ │ ├ sddk::matrix_storage::remap_forward                           |                        66.65 ms            |                  45              |                         3.00 s             | 
  │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                     |                        55.42 ms            |                  45              |                         2.49 s             | 
  │ │ │ ├ sirius::Density::add_k_point_contribution_dm                  |                        61.42 ms            |                  45              |                         2.76 s             | 
  │ │ │ │ ├ sirius::Beta_projectors_base::prepare                       |                         9.60 μs            |                  45              |                       431.87 μs            | 
  │ │ │ │ ├ sirius::Beta_projectors_base::generate                      |                         2.31 ms            |                  45              |                       103.74 ms            | 
  │ │ │ │ ├ sirius::Beta_projectors_base::inner                         |                        58.50 ms            |                  45              |                         2.63 s             | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                  |                         7.09 ms            |                  45              |                       319.27 ms            | 
  │ │ │ │ └ sirius::Beta_projectors_base::dismiss                       |                       549.60 ns            |                  45              |                        24.73 μs            | 
  │ │ │ ├ sirius::Density::add_k_point_contribution_rg                  |                       104.63 ms            |                  45              |                         4.71 s             | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |                         2.43 ms            |                  45              |                       109.40 ms            | 
  │ │ │ └ sirius::Density::augment                                      |                        20.33 ms            |                  45              |                       914.75 ms            | 
  │ │ │   └ sirius::Density::generate_rho_aug                           |                        20.16 ms            |                  45              |                       907.30 ms            | 
  │ │ ├ sirius::Field4D::symmetrize                                     |                       369.93 ns            |                  45              |                        16.65 μs            | 
  │ │ ├ sirius::Density::symmetrize_density_matrix                      |                         1.26 ms            |                  45              |                        56.69 ms            | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |                         2.69 ms            |                  45              |                       121.16 ms            | 
  │ ├ sirius::inner                                                     |                         4.36 ms            |                 549              |                         2.39 s             | 
  │ ├ sirius::Density::mix                                              |                       104.48 ms            |                  45              |                         4.70 s             | 
  │ │ ├ sirius::Density::mixer_input                                    |                       218.91 μs            |                  45              |                         9.85 ms            | 
  │ │ └ sirius::Density::mixer_output                                   |                         2.55 ms            |                  45              |                       114.72 ms            | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |                         2.41 ms            |                  45              |                       108.29 ms            | 
  │ ├ sirius::Potential::generate                                       |                       214.21 ms            |                  45              |                         9.64 s             | 
  │ │ ├ sirius::Potential::poisson                                      |                        63.81 ms            |                  45              |                         2.87 s             | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |                         8.98 ms            |                  45              |                       403.90 ms            | 
  │ │ │ └ sirius::inner                                                 |                         4.41 ms            |                  45              |                       198.60 ms            | 
  │ │ ├ sirius::Periodic_function::add                                  |                       202.40 μs            |                  90              |                        18.22 ms            | 
  │ │ ├ sirius::Potential::xc                                           |                       123.86 ms            |                  45              |                         5.57 s             | 
  │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                          |                       122.84 ms            |                  45              |                         5.53 s             | 
  │ │ │   ├ sirius::Smooth_periodic_function::fft_transform             |                         2.66 ms            |                 540              |                         1.44 s             | 
  │ │ │   ├ sirius::gradient                                            |                         1.83 ms            |                  45              |                        82.55 ms            | 
  │ │ │   ├ sirius::dot                                                 |                       693.55 μs            |                  45              |                        31.21 ms            | 
  │ │ │   ├ sirius::Potential::xc_rg_nonmagnetic|libxc                  |                        11.30 ms            |                  90              |                         1.02 s             | 
  │ │ │   └ sirius::divergence                                          |                        19.86 ms            |                  90              |                         1.79 s             | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |                         3.37 ms            |                  45              |                       151.47 ms            | 
  │ │ ├ sirius::Potential::generate_D_operator_matrix                   |                        20.95 ms            |                  45              |                       942.60 ms            | 
  │ │ └ sirius::Potential::generate_PAW_effective_potential             |                       284.04 ns            |                  45              |                        12.78 μs            | 
  │ ├ sirius::Field4D::symmetrize                                       |                       357.76 ns            |                  45              |                        16.10 μs            | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |                         2.28 ms            |                  45              |                       102.45 ms            | 
  │ ├ sirius::Periodic_function::integrate                              |                         4.21 ms            |                  45              |                       189.37 ms            | 
  │ ├ sirius::Density::get_magnetisation                                |                        12.28 ms            |                  45              |                       552.59 ms            | 
  │ │ └ sirius::Density::compute_atomic_mag_mom                         |                        12.27 ms            |                  45              |                       552.28 ms            | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.27 ms →        5.34 ms   (+1.37%) |       2   →       2              |       10.53 ms →       10.68 ms   (+1.37%) | 
  │ ├ sirius::Periodic_function|inner                                   |        3.93 ms                             |       6                          |       23.56 ms                             | 
  │ │ └ sirius::Periodic_function|inner_local                           |        3.90 ms                             |       6                          |       23.40 ms                             | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        3.90 ms                             |       6                          |       23.40 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.11 ms                             |       3                          |       12.34 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.05 ms                             |       3                          |       12.15 ms                             | 
  ├ sirius::Periodic_function|inner                                     |        3.91 ms                             |       2                          |        7.82 ms                             | 
  │ └ sirius::Periodic_function|inner_local                             |        3.86 ms                             |       2                          |        7.72 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        3.86 ms                             |       2                          |        7.72 ms                             | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.09 ms                             |       1                          |        4.09 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.01 ms                             |       1                          |        4.01 ms                             | 
  ├ sirius::inner                                                       |                         4.10 ms            |                   3              |                        12.31 ms            | 
  └ sirius::finalize                                                    |      323.89 ms →      345.13 ms   (+6.56%) |       1   →       1              |      323.89 ms →      345.13 ms   (+6.56%) | 
  ====================================================================================================================================================================================================
```
