# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |       72.12 s  →       69.95 s    (-3.01%) |       1   →       1              |       72.12 s  →       69.95 s    (-3.01%) | 
  ├ sirius::initialize                                                  |        2.86 s  →        2.59 s    (-9.65%) |       1   →       1              |        2.86 s  →        2.59 s    (-9.65%) | 
  ├ sirius::Simulation_context::initialize                              |        3.73 s  →        3.82 s    (+2.38%) |       1   →       1              |        3.73 s  →        3.82 s    (+2.38%) | 
- │ ├ sirius::Simulation_context::init_comm                             |       32.00 ms →      184.43 ms (+476.26%) |       1   →       1              |       32.00 ms →      184.43 ms (+476.26%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      174.76 ms →      150.36 ms  (-13.96%) |       1   →       1              |      174.76 ms →      150.36 ms  (-13.96%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       78.67 ms →       66.00 ms  (-16.10%) |       2   →       2              |      157.33 ms →      132.00 ms  (-16.10%) | 
  │ │ └ sirius::Unit_cell::update                                       |       17.34 ms →       18.27 ms   (+5.40%) |       1   →       1              |       17.34 ms →       18.27 ms   (+5.40%) | 
+ │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.62 ms →        5.24 ms  (-20.77%) |       1   →       1              |        6.62 ms →        5.24 ms  (-20.77%) | 
- │ │   └ sirius::Unit_cell::get_symmetry                               |       10.64 ms →       12.98 ms  (+22.00%) |       1   →       1              |       10.64 ms →       12.98 ms  (+22.00%) | 
- │ │     └ sirius::Unit_cell_symmetry                                  |       10.57 ms →       12.91 ms  (+22.15%) |       1   →       1              |       10.57 ms →       12.91 ms  (+22.15%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.76 ms →        2.73 ms   (-1.07%) |       1   →       1              |        2.76 ms →        2.73 ms   (-1.07%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      497.76 μs →      519.55 μs   (+4.38%) |       1   →       1              |      497.76 μs →      519.55 μs   (+4.38%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       15.74 μs →       15.40 μs   (-2.17%) |       1   →       1              |       15.74 μs →       15.40 μs   (-2.17%) | 
  │ └ sirius::Simulation_context::update                                |        3.32 s  →        3.27 s    (-1.62%) |       1   →       1              |        3.32 s  →        3.27 s    (-1.62%) | 
  │   ├ sirius::Unit_cell::update                                       |        6.99 ms →        6.74 ms   (-3.55%) |       1   →       1              |        6.99 ms →        6.74 ms   (-3.55%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.64 ms →        3.41 ms   (-6.42%) |       1   →       1              |        3.64 ms →        3.41 ms   (-6.42%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.27 ms →        3.29 ms   (+0.50%) |       1   →       1              |        3.27 ms →        3.29 ms   (+0.50%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.23 ms →        3.25 ms   (+0.65%) |       1   →       1              |        3.23 ms →        3.25 ms   (+0.65%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.69 ms →        2.72 ms   (+1.07%) |       1   →       1              |        2.69 ms →        2.72 ms   (+1.07%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      497.96 μs →      494.41 μs   (-0.71%) |       1   →       1              |      497.96 μs →      494.41 μs   (-0.71%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       14.39 μs →       13.47 μs   (-6.37%) |       1   →       1              |       14.39 μs →       13.47 μs   (-6.37%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      212.87 ms →      211.82 ms   (-0.49%) |       2   →       2              |      425.74 ms →      423.63 ms   (-0.49%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.15 ms →       15.18 ms   (+0.15%) |       2   →       2              |       30.31 ms →       30.35 ms   (+0.15%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.27 ms →       13.28 ms   (+0.06%) |       1   →       1              |       13.27 ms →       13.28 ms   (+0.06%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.31 ms →       56.37 ms   (+0.10%) |       2   →       2              |      112.62 ms →      112.74 ms   (+0.10%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.05 ms →       45.14 ms   (+0.19%) |       2   →       2              |       90.10 ms →       90.27 ms   (+0.19%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.38 ms →       60.25 ms   (-0.22%) |       4   →       4              |      241.52 ms →      240.98 ms   (-0.22%) | 
  │   ├ sddk::Gvec::init                                                |       95.16 ms →       93.37 ms   (-1.89%) |       2   →       2              |      190.33 ms →      186.74 ms   (-1.89%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       71.19 ms →       69.63 ms   (-2.20%) |       2   →       2              |      142.39 ms →      139.25 ms   (-2.20%) | 
  │   ├ sddk::Gvec_shells                                               |       92.02 ms →       94.00 ms   (+2.16%) |       1   →       1              |       92.02 ms →       94.00 ms   (+2.16%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.95 ms →        1.94 ms   (-0.97%) |       1   →       1              |        1.95 ms →        1.94 ms   (-0.97%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      508.16 ms →      507.18 ms   (-0.19%) |       2   →       2              |        1.02 s  →        1.01 s    (-0.19%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |      150.82 ms →      137.02 ms   (-9.16%) |       1   →       1              |      150.82 ms →      137.02 ms   (-9.16%) | 
+ │ ├ sirius::K_point::K_point                                          |        1.89 μs →        1.34 μs  (-29.50%) |       4   →       4              |        7.58 μs →        5.34 μs  (-29.50%) | 
  │ └ sirius::K_point_set::initialize                                   |      150.74 ms →      136.91 ms   (-9.17%) |       1   →       1              |      150.74 ms →      136.91 ms   (-9.17%) | 
  │   └ sirius::K_point::initialize                                     |       28.31 ms →       28.33 ms   (+0.09%) |       1   →       1              |       28.31 ms →       28.33 ms   (+0.09%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       11.19 ms →       11.07 ms   (-1.07%) |       1   →       1              |       11.19 ms →       11.07 ms   (-1.07%) | 
  │     │ └ sddk::Gvec::init                                            |        5.00 ms →        5.07 ms   (+1.33%) |       1   →       1              |        5.00 ms →        5.07 ms   (+1.33%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        7.34 μs →        7.93 μs   (+8.02%) |       1   →       1              |        7.34 μs →        7.93 μs   (+8.02%) | 
  │     └ sirius::K_point::update                                       |       14.28 ms →       14.40 ms   (+0.82%) |       1   →       1              |       14.28 ms →       14.40 ms   (+0.82%) | 
  │       └ sirius::Beta_projectors                                     |       10.33 ms →       10.40 ms   (+0.62%) |       1   →       1              |       10.33 ms →       10.40 ms   (+0.62%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.42 ms →        8.32 ms   (-1.30%) |       1   →       1              |        8.42 ms →        8.32 ms   (-1.30%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.55 ms →        2.61 ms   (+2.42%) |       2   →       2              |        5.10 ms →        5.23 ms   (+2.42%) | 
  ├ sirius::Potential                                                   |       53.40 ms →       52.11 ms   (-2.41%) |       1   →       1              |       53.40 ms →       52.11 ms   (-2.41%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.89 ms →        2.94 ms   (+1.67%) |       6   →       6              |       17.34 ms →       17.63 ms   (+1.67%) | 
  │ └ sirius::Potential::update                                         |       35.48 ms →       33.93 ms   (-4.38%) |       1   →       1              |       35.48 ms →       33.93 ms   (-4.38%) | 
  │   └ sirius::Potential::generate_local_potential                     |       35.09 ms →       33.53 ms   (-4.46%) |       1   →       1              |       35.09 ms →       33.53 ms   (-4.46%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       30.71 ms →       26.76 ms  (-12.86%) |       1   →       1              |       30.71 ms →       26.76 ms  (-12.86%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        3.84 ms →        6.22 ms  (+62.13%) |       1   →       1              |        3.84 ms →        6.22 ms  (+62.13%) | 
  ├ sirius::Density                                                     |       40.95 ms →       42.80 ms   (+4.52%) |       1   →       1              |       40.95 ms →       42.80 ms   (+4.52%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.82 ms →        2.80 ms   (-0.65%) |       2   →       2              |        5.64 ms →        5.61 ms   (-0.65%) | 
  │ └ sirius::Density::update                                           |       35.17 ms →       37.05 ms   (+5.36%) |       1   →       1              |       35.17 ms →       37.05 ms   (+5.36%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       34.89 ms →       36.83 ms   (+5.57%) |       1   →       1              |       34.89 ms →       36.83 ms   (+5.57%) | 
- │     ├ sirius::rho_core_ri_pseudo|values                             |       78.87 μs →       87.21 μs  (+10.56%) |       1   →       1              |       78.87 μs →       87.21 μs  (+10.56%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       31.14 ms →       26.63 ms  (-14.50%) |       1   →       1              |       31.14 ms →       26.63 ms  (-14.50%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        3.32 ms →        9.82 ms (+195.34%) |       1   →       1              |        3.32 ms →        9.82 ms (+195.34%) | 
  ├ sirius::Density::initial_density                                    |       64.33 ms →       62.21 ms   (-3.29%) |       1   →       1              |       64.33 ms →       62.21 ms   (-3.29%) | 
+ │ ├ sirius::Simulation_context::make_periodic_function                |       36.45 ms →       27.06 ms  (-25.75%) |       1   →       1              |       36.45 ms →       27.06 ms  (-25.75%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.49 ms →        7.88 ms  (+75.62%) |       2   →       2              |        8.97 ms →       15.75 ms  (+75.62%) | 
  │ └ sirius::Periodic_function::integrate                              |        5.27 ms →        5.77 ms   (+9.52%) |       1   →       1              |        5.27 ms →        5.77 ms   (+9.52%) | 
  ├ sirius::Potential::generate                                         |      373.28 ms →      369.37 ms   (-1.05%) |       1   →       1              |      373.28 ms →      369.37 ms   (-1.05%) | 
  │ ├ sirius::Potential::poisson                                        |       44.43 ms →       42.54 ms   (-4.24%) |       1   →       1              |       44.43 ms →       42.54 ms   (-4.24%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.31 ms →       10.70 ms (+223.70%) |       1   →       1              |        3.31 ms →       10.70 ms (+223.70%) | 
- │ │ └ sirius::Periodic_function|inner                                 |        5.02 ms →        5.92 ms  (+18.03%) |       1   →       1              |        5.02 ms →        5.92 ms  (+18.03%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.63 ms →        4.63 ms   (-0.08%) |       1   →       1              |        4.63 ms →        4.63 ms   (-0.08%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.63 ms →        4.62 ms   (-0.15%) |       1   →       1              |        4.63 ms →        4.62 ms   (-0.15%) | 
  │ ├ sirius::Periodic_function::add                                    |      765.09 μs →      767.67 μs   (+0.34%) |       2   →       2              |        1.53 ms →        1.54 ms   (+0.34%) | 
  │ ├ sirius::Potential::xc                                             |       52.58 ms →       51.50 ms   (-2.06%) |       1   →       1              |       52.58 ms →       51.50 ms   (-2.06%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.36 ms →       50.34 ms   (-1.99%) |       1   →       1              |       51.36 ms →       50.34 ms   (-1.99%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.54 ms →        2.55 ms   (+0.63%) |       2   →       2              |        5.07 ms →        5.11 ms   (+0.63%) | 
- │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.11 ms →        4.54 ms  (+10.43%) |       1   →       1              |        4.11 ms →        4.54 ms  (+10.43%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.91 ms →        3.74 ms   (-4.54%) |       1   →       1              |        3.91 ms →        3.74 ms   (-4.54%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      269.45 ms →      268.69 ms   (-0.28%) |       1   →       1              |      269.45 ms →      268.69 ms   (-0.28%) | 
+ │ └ sirius::Potential::generate_PAW_effective_potential               |      199.00 ns →      170.00 ns  (-14.57%) |       1   →       1              |      199.00 ns →      170.00 ns  (-14.57%) | 
  ├ sirius::Hamiltonian0                                                |        6.51 ms →        6.47 ms   (-0.60%) |       1   →       1              |        6.51 ms →        6.47 ms   (-0.60%) | 
  │ ├ sirius::Local_operator                                            |        6.05 ms →        5.90 ms   (-2.50%) |       1   →       1              |        6.05 ms →        5.90 ms   (-2.50%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.74 ms →        2.76 ms   (+0.79%) |       1   →       1              |        2.74 ms →        2.76 ms   (+0.79%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.55 ms →        2.38 ms   (-6.71%) |       1   →       1              |        2.55 ms →        2.38 ms   (-6.71%) | 
- │ ├ sirius::Non_local_operator                                        |       72.68 μs →      114.34 μs  (+57.33%) |       2   →       2              |      145.35 μs →      228.69 μs  (+57.33%) | 
- │ ├ sirius::D_operator::initialize                                    |      113.02 μs →      139.27 μs  (+23.23%) |       1   →       1              |      113.02 μs →      139.27 μs  (+23.23%) | 
  │ └ sirius::Q_operator::initialize                                    |      118.56 μs →      119.76 μs   (+1.01%) |       1   →       1              |      118.56 μs →      119.76 μs   (+1.01%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.26 s  →        1.32 s    (+4.24%) |       1   →       1              |        1.26 s  →        1.32 s    (+4.24%) | 
- │ ├ sirius::Hamiltonian_k                                             |       28.90 ms →       60.89 ms (+110.70%) |       1   →       1              |       28.90 ms →       60.89 ms (+110.70%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      359.28 μs →      373.67 μs   (+4.01%) |       1   →       1              |      359.28 μs →      373.67 μs   (+4.01%) | 
- │ │ └ sirius::Beta_projectors_base::prepare                           |       28.53 ms →       60.52 ms (+112.08%) |       1   →       1              |       28.53 ms →       60.52 ms (+112.08%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.23 s  →        1.25 s    (+1.74%) |       1   →       1              |        1.23 s  →        1.25 s    (+1.74%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       82.48 ms →       84.58 ms   (+2.55%) |       4   →       4              |      329.93 ms →      338.33 ms   (+2.55%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       35.16 ms →       38.40 ms   (+9.23%) |       1   →       1              |       35.16 ms →       38.40 ms   (+9.23%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        6.73 ms →        6.86 ms   (+1.97%) |       1   →       1              |        6.73 ms →        6.86 ms   (+1.97%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      312.93 ms →      310.39 ms   (-0.81%) |       1   →       1              |      312.93 ms →      310.39 ms   (-0.81%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      245.20 ms →      243.55 ms   (-0.67%) |       1   →       1              |      245.20 ms →      243.55 ms   (-0.67%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        4.03 μs →        3.65 μs   (-9.46%) |       1   →       1              |        4.03 μs →        3.65 μs   (-9.46%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.09 μs →        2.51 μs  (-18.72%) |       1   →       1              |        3.09 μs →        2.51 μs  (-18.72%) | 
+ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      646.00 ns →      474.00 ns  (-26.63%) |       1   →       1              |      646.00 ns →      474.00 ns  (-26.63%) | 
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      632.00 ns →      523.00 ns  (-17.25%) |       1   →       1              |      632.00 ns →      523.00 ns  (-17.25%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.13 ms →        3.21 ms   (+2.59%) |       1   →       1              |        3.13 ms →        3.21 ms   (+2.59%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.26 ms →       21.31 ms   (+0.23%) |       1   →       1              |       21.26 ms →       21.31 ms   (+0.23%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       21.64 ms →       21.14 ms   (-2.34%) |       2   →       2              |       43.29 ms →       42.27 ms   (-2.34%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       16.73 ms →       16.57 ms   (-0.94%) |       2   →       2              |       33.46 ms →       33.14 ms   (-0.94%) | 
  │ │ │ └ sddk::wf_inner                                                |       16.52 ms →       16.35 ms   (-1.01%) |       2   →       2              |       33.04 ms →       32.71 ms   (-1.01%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       20.00 ns →       31.00 ns  (+55.00%) |       2   →       2              |       40.00 ns →       62.00 ns  (+55.00%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       16.40 ms →       16.22 ms   (-1.09%) |       2   →       2              |       32.79 ms →       32.43 ms   (-1.09%) | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |       27.50 ns →       28.50 ns   (+3.64%) |       2   →       2              |       55.00 ns →       57.00 ns   (+3.64%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      249.47 ms →      253.98 ms   (+1.81%) |       1   →       1              |      249.47 ms →      253.98 ms   (+1.81%) | 
- │ │ └ sddk::wf_trans                                                  |        2.61 ms →        4.93 ms  (+89.01%) |       1   →       1              |        2.61 ms →        4.93 ms  (+89.01%) | 
- │ │   └ sddk::wf_trans|pw                                             |        2.61 ms →        4.93 ms  (+89.17%) |       1   →       1              |        2.61 ms →        4.93 ms  (+89.17%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      732.00 ns →      622.00 ns  (-15.03%) |       1   →       1              |      732.00 ns →      622.00 ns  (-15.03%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |       62.45 s  →       60.46 s    (-3.19%) |       1   →       1              |       62.45 s  →       60.46 s    (-3.19%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.46 ms →        2.47 ms   (+0.30%) |      19   →      19              |       46.70 ms →       46.84 ms   (+0.30%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.26 s  →        3.16 s    (-2.94%) |      19   →      19              |       61.95 s  →       60.13 s    (-2.94%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        5.60 ms →        5.54 ms   (-1.02%) |      19   →      19              |      106.38 ms →      105.30 ms   (-1.02%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.83 ms →        4.67 ms   (-3.19%) |      19   →      19              |       91.74 ms →       88.82 ms   (-3.19%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      558.93 μs →      543.50 μs   (-2.76%) |      19   →      19              |       10.62 ms →       10.33 ms   (-2.76%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.19 ms →        2.95 ms   (-7.50%) |      19   →      19              |       60.57 ms →       56.02 ms   (-7.50%) | 
- │ │ │ ├ sirius::Non_local_operator                                    |      242.23 μs →      292.54 μs  (+20.77%) |      38   →      38              |        9.20 ms →       11.12 ms  (+20.77%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |      114.87 μs →      111.25 μs   (-3.15%) |      19   →      19              |        2.18 ms →        2.11 ms   (-3.15%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       93.47 μs →       91.91 μs   (-1.68%) |      19   →      19              |        1.78 ms →        1.75 ms   (-1.68%) | 
  │ │ ├ sirius::Band::solve                                             |        2.03 s  →        1.94 s    (-4.43%) |      19   →      19              |       38.59 s  →       36.88 s    (-4.43%) | 
+ │ │ │ ├ sirius::Hamiltonian_k                                         |      215.18 μs →      189.50 μs  (-11.94%) |      19   →      19              |        4.09 ms →        3.60 ms  (-11.94%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      205.92 μs →      182.50 μs  (-11.38%) |      19   →      19              |        3.91 ms →        3.47 ms  (-11.38%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        6.80 μs →        4.94 μs  (-27.29%) |      19   →      19              |      129.15 μs →       93.90 μs  (-27.29%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.97 s  →        1.80 s    (-8.25%) |      19   →      19              |       37.35 s  →       34.27 s    (-8.25%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       77.18 ms →       77.60 ms   (+0.54%) |      19   →      19              |        1.47 s  →        1.47 s    (+0.54%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        8.13 ms →        7.98 ms   (-1.90%) |     114   →     114              |      927.38 ms →      909.73 ms   (-1.90%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       18.15 ms →       17.96 ms   (-1.04%) |      19   →      19              |      344.78 ms →      341.18 ms   (-1.04%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      476.39 μs →      470.58 μs   (-1.22%) |      19   →      19              |        9.05 ms →        8.94 ms   (-1.22%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        8.26 ms →        8.12 ms   (-1.67%) |      38   →      38              |      313.76 ms →      308.53 ms   (-1.67%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.86 s  →        1.70 s    (-8.78%) |      19   →      19              |       35.38 s  →       32.27 s    (-8.78%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       51.09 ms →       59.14 ms  (+15.75%) |     356   →     312    (-12.36%) |       18.19 s  →       18.45 s    (+1.44%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       28.67 ms →       32.91 ms  (+14.77%) |     356   →     312    (-12.36%) |       10.21 s  →       10.27 s    (+0.58%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.09 μs →        2.06 μs   (-1.57%) |     356   →     312    (-12.36%) |      745.69 μs →      643.27 μs  (-13.74%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.79 μs →        1.78 μs   (-0.96%) |     356   →     312    (-12.36%) |      638.43 μs →      554.17 μs  (-13.20%) | 
! │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      434.35 ns →      465.54 ns   (+7.18%) |     356   →     312    (-12.36%) |      154.63 μs →      145.25 μs   (-6.07%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      610.69 ns →      678.14 ns  (+11.05%) |     356   →     312    (-12.36%) |      217.41 μs →      211.58 μs   (-2.68%) | 
! │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.84 ms →        3.04 ms   (+7.06%) |     356   →     312    (-12.36%) |        1.01 s  →      950.00 ms   (-6.17%) | 
! │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.31 ms →        3.58 ms   (+8.18%) |     356   →     312    (-12.36%) |        1.18 s  →        1.12 s    (-5.19%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        8.12 ms →        9.79 ms  (+20.54%) |     712   →     624    (-12.36%) |        5.78 s  →        6.11 s    (+5.64%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |        6.41 ms →        8.13 ms  (+26.76%) |     356   →     312    (-12.36%) |        2.28 s  →        2.54 s   (+11.10%) | 
- │ │ │ │   │ ├ sddk::wf_inner                                          |        1.03 ms →        1.40 ms  (+35.96%) |     693   →     605    (-12.70%) |      712.68 ms →      845.91 ms  (+18.69%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       53.07 ns →       69.18 ns  (+30.37%) |     693   →     605    (-12.70%) |       36.77 μs →       41.86 μs  (+13.82%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |      866.49 μs →        1.23 ms  (+42.32%) |     693   →     605    (-12.70%) |      600.48 ms →      746.10 ms  (+24.25%) | 
+ │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       49.48 ns →       46.33 ns   (-6.38%) |     693   →     605    (-12.70%) |       34.29 μs →       28.03 μs  (-18.27%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      133.90 μs →      158.88 μs  (+18.65%) |     356   →     312    (-12.36%) |       47.67 ms →       49.57 ms   (+3.99%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        2.08 ms →        2.63 ms  (+26.28%) |     356   →     312    (-12.36%) |      741.50 ms →      820.66 ms  (+10.68%) | 
- │ │ │ │   │ └ sddk::wf_trans                                          |        2.31 ms →        2.80 ms  (+20.81%) |     337   →     293    (-13.06%) |      779.71 ms →      818.98 ms   (+5.04%) | 
- │ │ │ │   │   └ sddk::wf_trans|pw                                     |      770.45 μs →      930.90 μs  (+20.83%) |    1.01 K →     879    (-13.06%) |      778.92 ms →      818.26 ms   (+5.05%) | 
! │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.49 ms →        1.56 ms   (+4.65%) |     356   →     312    (-12.36%) |      529.01 ms →      485.20 ms   (-8.28%) | 
! │ │ │ │   │ └ sddk::wf_inner                                          |        1.41 ms →        1.50 ms   (+6.25%) |     356   →     312    (-12.36%) |      503.68 ms →      469.01 ms   (-6.88%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       42.83 ns →       32.47 ns  (-24.19%) |     356   →     312    (-12.36%) |       15.25 μs →       10.13 μs  (-33.56%) | 
! │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        1.25 ms →        1.34 ms   (+6.72%) |     356   →     312    (-12.36%) |      445.65 ms →      416.80 ms   (-6.47%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       39.37 ns →       54.51 ns  (+38.44%) |     356   →     312    (-12.36%) |       14.02 μs →       17.01 μs  (+21.33%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       36.73 ms →       30.08 ms  (-18.11%) |     356   →     312    (-12.36%) |       13.08 s  →        9.39 s   (-28.23%) | 
- │ │ │ │   ├ sirius::residuals                                         |        2.66 ms →        3.18 ms  (+19.59%) |     340   →     299    (-12.06%) |      904.43 ms →      951.16 ms   (+5.17%) | 
- │ │ │ │   │ ├ sddk::wf_trans                                          |        1.38 ms →        1.52 ms  (+10.17%) |     337   →     293    (-13.06%) |      465.06 ms →      445.48 ms   (-4.21%) | 
- │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      688.61 μs →      758.74 μs  (+10.19%) |     674   →     586    (-13.06%) |      464.12 ms →      444.62 ms   (-4.20%) | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.19 ms →        1.60 ms  (+34.32%) |     337   →     293    (-13.06%) |      400.80 ms →      468.06 ms  (+16.78%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        7.16 ms →        6.91 ms   (-3.48%) |      54   →      66    (+22.22%) |      386.44 ms →      455.88 ms  (+17.97%) | 
- │ │ │ │     └ sddk::wf_trans                                          |        4.29 ms →        3.98 ms   (-7.28%) |      89   →     113    (+26.97%) |      382.16 ms →      449.89 ms  (+17.72%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |        3.08 ms →        2.81 ms   (-8.77%) |     124   →     160    (+29.03%) |      382.00 ms →      449.67 ms  (+17.71%) | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      366.47 ns →      375.26 ns   (+2.40%) |      19   →      19              |        6.96 μs →        7.13 μs   (+2.40%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       19.69 μs →       19.10 μs   (-3.01%) |      19   →      19              |      374.09 μs →      362.82 μs   (-3.01%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.51 ms →        1.57 ms   (+3.67%) |      19   →      19              |       28.77 ms →       29.83 ms   (+3.67%) | 
  │ │ ├ sirius::Density::generate                                       |      570.55 ms →      570.87 ms   (+0.06%) |      19   →      19              |       10.84 s  →       10.85 s    (+0.06%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      418.87 ms →      442.14 ms   (+5.55%) |      19   →      19              |        7.96 s  →        8.40 s    (+5.55%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.23 μs →        6.66 μs  (-19.14%) |      19   →      19              |      156.41 μs →      126.47 μs  (-19.14%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.68 μs →        6.24 μs  (-18.79%) |      19   →      19              |      145.93 μs →      118.51 μs  (-18.79%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       46.02 ms →       42.31 ms   (-8.08%) |      19   →      19              |      874.47 ms →      803.82 ms   (-8.08%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.37 μs →        5.88 μs  (-20.13%) |      19   →      19              |      139.99 μs →      111.80 μs  (-20.13%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        8.06 ms →        6.99 ms  (-13.20%) |      19   →      19              |      153.05 ms →      132.84 ms  (-13.20%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       36.90 ms →       34.28 ms   (-7.12%) |      19   →      19              |      701.15 ms →      651.23 ms   (-7.12%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      589.58 ns →      521.05 ns  (-11.62%) |      19   →      19              |       11.20 μs →        9.90 μs  (-11.62%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      100.31 ms →      103.20 ms   (+2.88%) |      19   →      19              |        1.91 s  →        1.96 s    (+2.88%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.20 ms →        2.52 ms  (+14.48%) |      19   →      19              |       41.80 ms →       47.85 ms  (+14.48%) | 
  │ │ │ │ └ sirius::Density::augment                                    |      238.21 ms →      257.96 ms   (+8.29%) |      19   →      19              |        4.53 s  →        4.90 s    (+8.29%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |      237.99 ms →      257.74 ms   (+8.30%) |      19   →      19              |        4.52 s  →        4.90 s    (+8.30%) | 
+ │ │ │ ├ sirius::Field4D::symmetrize                                   |      123.29 ms →      100.40 ms  (-18.56%) |      19   →      19              |        2.34 s  →        1.91 s   (-18.56%) | 
+ │ │ │ │ └ sirius::symmetrize_function|fpw                             |      123.28 ms →      100.40 ms  (-18.56%) |      19   →      19              |        2.34 s  →        1.91 s   (-18.56%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       40.45 ms →       16.44 ms  (-59.35%) |      19   →      19              |      768.47 ms →      312.39 ms  (-59.35%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       69.51 ms →       70.70 ms   (+1.70%) |      19   →      19              |        1.32 s  →        1.34 s    (+1.70%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.67 ms →       12.61 ms   (-0.44%) |      19   →      19              |      240.71 ms →      239.65 ms   (-0.44%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.67 ms →       23.64 ms   (-0.12%) |      19   →      19              |      449.73 ms →      449.17 ms   (-0.12%) | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        4.72 ms →        4.68 ms   (-0.78%) |      19   →      19              |       89.69 ms →       88.99 ms   (-0.78%) | 
  │ │ ├ sirius::Density::mix                                            |      134.37 ms →      130.58 ms   (-2.82%) |      19   →      19              |        2.55 s  →        2.48 s    (-2.82%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      280.77 μs →      683.91 μs (+143.58%) |      19   →      19              |        5.33 ms →       12.99 ms (+143.58%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |        5.01 ms →        4.70 ms   (-6.28%) |     229   →     229              |        1.15 s  →        1.08 s    (-6.28%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.83 ms →        4.62 ms   (-4.30%) |     229   →     229              |        1.11 s  →        1.06 s    (-4.30%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.83 ms →        4.62 ms   (-4.29%) |     229   →     229              |        1.11 s  →        1.06 s    (-4.29%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        4.91 ms →        5.19 ms   (+5.75%) |      19   →      19              |       93.22 ms →       98.58 ms   (+5.75%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        4.15 ms →        4.50 ms   (+8.44%) |      19   →      19              |       78.77 ms →       85.41 ms   (+8.44%) | 
  │ │ ├ sirius::Potential::generate                                     |      364.60 ms →      363.09 ms   (-0.41%) |      19   →      19              |        6.93 s  →        6.90 s    (-0.41%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |       44.35 ms →       42.89 ms   (-3.31%) |      19   →      19              |      842.69 ms →      814.83 ms   (-3.31%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        3.23 ms →       10.99 ms (+239.91%) |      19   →      19              |       61.41 ms →      208.75 ms (+239.91%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |        5.08 ms →        5.91 ms  (+16.40%) |      19   →      19              |       96.53 ms →      112.36 ms  (+16.40%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.63 ms →        4.63 ms   (+0.01%) |      19   →      19              |       88.00 ms →       88.00 ms   (+0.01%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.63 ms →        4.63 ms   (+0.02%) |      19   →      19              |       87.97 ms →       87.98 ms   (+0.02%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      780.14 μs →      790.01 μs   (+1.27%) |      38   →      38              |       29.65 ms →       30.02 ms   (+1.27%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       44.56 ms →       45.07 ms   (+1.15%) |      19   →      19              |      846.68 ms →      856.42 ms   (+1.15%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       43.37 ms →       43.91 ms   (+1.24%) |      19   →      19              |      824.00 ms →      834.23 ms   (+1.24%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |      687.90 μs →      678.83 μs   (-1.32%) |      38   →      38              |       26.14 ms →       25.80 ms   (-1.32%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.18 ms →        4.68 ms  (+12.05%) |      19   →      19              |       79.35 ms →       88.91 ms  (+12.05%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.83 ms →        3.66 ms   (-4.43%) |      19   →      19              |       72.76 ms →       69.53 ms   (-4.43%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.87 ms →      268.47 ms   (-0.15%) |      19   →      19              |        5.11 s  →        5.10 s    (-0.15%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      346.21 ns →      194.42 ns  (-43.84%) |      19   →      19              |        6.58 μs →        3.69 μs  (-43.84%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |       95.89 ms →       96.70 ms   (+0.84%) |      19   →      19              |        1.82 s  →        1.84 s    (+0.84%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |       95.89 ms →       96.70 ms   (+0.84%) |      19   →      19              |        1.82 s  →        1.84 s    (+0.84%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.50 ms →       13.34 ms   (-1.15%) |      19   →      19              |      256.44 ms →      253.49 ms   (-1.15%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       69.19 ms →       70.17 ms   (+1.42%) |      19   →      19              |        1.31 s  →        1.33 s    (+1.42%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.58 ms →       12.57 ms   (-0.13%) |      19   →      19              |      239.08 ms →      238.76 ms   (-0.13%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        4.41 ms →        4.50 ms   (+2.00%) |      19   →      19              |       83.81 ms →       85.49 ms   (+2.00%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.72 ms →        4.58 ms   (-2.94%) |     133   →     133              |      627.91 ms →      609.44 ms   (-2.94%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.66 ms →        4.55 ms   (-2.30%) |     133   →     133              |      619.69 ms →      605.42 ms   (-2.30%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.66 ms →        4.55 ms   (-2.30%) |     133   →     133              |      619.60 ms →      605.34 ms   (-2.30%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.96 ms →        4.75 ms   (-4.15%) |      57   →      57              |      282.44 ms →      270.71 ms   (-4.15%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.94 ms →        4.73 ms   (-4.22%) |      57   →      57              |      281.36 ms →      269.49 ms   (-4.22%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.54 ms →        4.54 ms   (-0.02%) |      19   →      19              |       86.33 ms →       86.31 ms   (-0.02%) | 
  │ │ └ sirius::Density::get_magnetisation                              |       76.26 μs →       72.95 μs   (-4.34%) |      19   →      19              |        1.45 ms →        1.39 ms   (-4.34%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |       71.24 μs →       69.20 μs   (-2.87%) |      19   →      19              |        1.35 ms →        1.31 ms   (-2.87%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.50 ms →        5.67 ms   (+3.19%) |       2   →       2              |       11.00 ms →       11.35 ms   (+3.19%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.67 ms →        4.62 ms   (-1.07%) |       6   →       6              |       28.05 ms →       27.75 ms   (-1.07%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.55 ms →        4.62 ms   (+1.58%) |       6   →       6              |       27.27 ms →       27.70 ms   (+1.58%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.54 ms →        4.62 ms   (+1.62%) |       6   →       6              |       27.26 ms →       27.70 ms   (+1.62%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.94 ms →        4.82 ms   (-2.39%) |       3   →       3              |       14.81 ms →       14.45 ms   (-2.39%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.93 ms →        4.81 ms   (-2.41%) |       3   →       3              |       14.79 ms →       14.44 ms   (-2.41%) | 
  ├ sirius::Periodic_function|inner                                     |        4.53 ms →        4.62 ms   (+1.89%) |       2   →       2              |        9.07 ms →        9.24 ms   (+1.89%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.53 ms →        4.61 ms   (+1.85%) |       2   →       2              |        9.06 ms →        9.23 ms   (+1.85%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.53 ms →        4.61 ms   (+1.85%) |       2   →       2              |        9.06 ms →        9.23 ms   (+1.85%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.92 ms →        4.83 ms   (-1.82%) |       1   →       1              |        4.92 ms →        4.83 ms   (-1.82%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.91 ms →        4.82 ms   (-1.81%) |       1   →       1              |        4.91 ms →        4.82 ms   (-1.81%) | 
+ └ sirius::finalize                                                    |      559.46 ms →      185.11 ms  (-66.91%) |       1   →       1              |      559.46 ms →      185.11 ms  (-66.91%) | 
  ====================================================================================================================================================================================================
```
