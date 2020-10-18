# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |       71.76 s  →       72.84 s    (+1.50%) |       1   →       1              |       71.76 s  →       72.84 s    (+1.50%) | 
  ├ sirius::initialize                                                  |        2.86 s  →        2.87 s    (+0.36%) |       1   →       1              |        2.86 s  →        2.87 s    (+0.36%) | 
  ├ sirius::Simulation_context::initialize                              |        3.82 s  →        3.83 s    (+0.15%) |       1   →       1              |        3.82 s  →        3.83 s    (+0.15%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       38.22 ms →       34.01 ms  (-11.00%) |       1   →       1              |       38.22 ms →       34.01 ms  (-11.00%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      239.14 ms →      120.67 ms  (-49.54%) |       1   →       1              |      239.14 ms →      120.67 ms  (-49.54%) | 
+ │ │ ├ sirius::Atom_type::init                                         |      110.64 ms →       51.82 ms  (-53.16%) |       2   →       2              |      221.28 ms →      103.65 ms  (-53.16%) | 
  │ │ └ sirius::Unit_cell::update                                       |       17.77 ms →       16.93 ms   (-4.71%) |       1   →       1              |       17.77 ms →       16.93 ms   (-4.71%) | 
+ │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        5.19 ms →        3.57 ms  (-31.16%) |       1   →       1              |        5.19 ms →        3.57 ms  (-31.16%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       12.50 ms →       13.26 ms   (+6.07%) |       1   →       1              |       12.50 ms →       13.26 ms   (+6.07%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       12.44 ms →       13.19 ms   (+6.05%) |       1   →       1              |       12.44 ms →       13.19 ms   (+6.05%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.76 ms →        2.80 ms   (+1.58%) |       1   →       1              |        2.76 ms →        2.80 ms   (+1.58%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      498.45 μs →      474.73 μs   (-4.76%) |       1   →       1              |      498.45 μs →      474.73 μs   (-4.76%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       15.37 μs →       16.68 μs   (+8.51%) |       1   →       1              |       15.37 μs →       16.68 μs   (+8.51%) | 
  │ └ sirius::Simulation_context::update                                |        3.44 s  →        3.62 s    (+4.99%) |       1   →       1              |        3.44 s  →        3.62 s    (+4.99%) | 
  │   ├ sirius::Unit_cell::update                                       |        7.02 ms →        6.93 ms   (-1.28%) |       1   →       1              |        7.02 ms →        6.93 ms   (-1.28%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.65 ms →        3.54 ms   (-2.96%) |       1   →       1              |        3.65 ms →        3.54 ms   (-2.96%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.33 ms →        3.36 ms   (+0.70%) |       1   →       1              |        3.33 ms →        3.36 ms   (+0.70%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.26 ms →        3.31 ms   (+1.50%) |       1   →       1              |        3.26 ms →        3.31 ms   (+1.50%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.72 ms →        2.76 ms   (+1.60%) |       1   →       1              |        2.72 ms →        2.76 ms   (+1.60%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      506.32 μs →      512.08 μs   (+1.14%) |       1   →       1              |      506.32 μs →      512.08 μs   (+1.14%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       14.34 μs →       14.20 μs   (-1.00%) |       1   →       1              |       14.34 μs →       14.20 μs   (-1.00%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      212.95 ms →      212.18 ms   (-0.36%) |       2   →       2              |      425.90 ms →      424.35 ms   (-0.36%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.15 ms →       15.17 ms   (+0.12%) |       2   →       2              |       30.30 ms →       30.34 ms   (+0.12%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.24 ms →       13.25 ms   (+0.08%) |       1   →       1              |       13.24 ms →       13.25 ms   (+0.08%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.24 ms →       56.29 ms   (+0.10%) |       2   →       2              |      112.47 ms →      112.58 ms   (+0.10%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.02 ms →       45.10 ms   (+0.17%) |       2   →       2              |       90.04 ms →       90.19 ms   (+0.17%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.51 ms →       60.43 ms   (-0.13%) |       4   →       4              |      242.02 ms →      241.71 ms   (-0.13%) | 
  │   ├ sddk::Gvec::init                                                |       93.71 ms →       93.52 ms   (-0.21%) |       2   →       2              |      187.43 ms →      187.04 ms   (-0.21%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       70.21 ms →       70.00 ms   (-0.30%) |       2   →       2              |      140.42 ms →      140.00 ms   (-0.30%) | 
  │   ├ sddk::Gvec_shells                                               |       91.49 ms →       93.84 ms   (+2.57%) |       1   →       1              |       91.49 ms →       93.84 ms   (+2.57%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.95 ms →        1.96 ms   (+0.56%) |       1   →       1              |        1.95 ms →        1.96 ms   (+0.56%) | 
- │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      567.23 ms →      660.79 ms  (+16.49%) |       2   →       2              |        1.13 s  →        1.32 s   (+16.49%) | 
+ ├ sirius::K_point_set::create_k_mesh                                  |      148.36 ms →       87.96 ms  (-40.71%) |       1   →       1              |      148.36 ms →       87.96 ms  (-40.71%) | 
- │ ├ sirius::K_point::K_point                                          |        1.87 μs →        2.45 μs  (+30.81%) |       4   →       4              |        7.48 μs →        9.78 μs  (+30.81%) | 
+ │ └ sirius::K_point_set::initialize                                   |      148.27 ms →       87.88 ms  (-40.73%) |       1   →       1              |      148.27 ms →       87.88 ms  (-40.73%) | 
  │   └ sirius::K_point::initialize                                     |       28.63 ms →       28.34 ms   (-1.03%) |       1   →       1              |       28.63 ms →       28.34 ms   (-1.03%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       11.16 ms →       10.92 ms   (-2.10%) |       1   →       1              |       11.16 ms →       10.92 ms   (-2.10%) | 
  │     │ └ sddk::Gvec::init                                            |        4.99 ms →        4.92 ms   (-1.37%) |       1   →       1              |        4.99 ms →        4.92 ms   (-1.37%) | 
- │     ├ sddk::matrix_storage::matrix_storage                          |        7.89 μs →       11.74 μs  (+48.70%) |       1   →       1              |        7.89 μs →       11.74 μs  (+48.70%) | 
  │     └ sirius::K_point::update                                       |       14.59 ms →       14.55 ms   (-0.33%) |       1   →       1              |       14.59 ms →       14.55 ms   (-0.33%) | 
  │       └ sirius::Beta_projectors                                     |       10.61 ms →       10.63 ms   (+0.21%) |       1   →       1              |       10.61 ms →       10.63 ms   (+0.21%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.71 ms →        8.68 ms   (-0.39%) |       1   →       1              |        8.71 ms →        8.68 ms   (-0.39%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.53 ms →        2.59 ms   (+2.18%) |       2   →       2              |        5.07 ms →        5.18 ms   (+2.18%) | 
  ├ sirius::Potential                                                   |       51.94 ms →       54.33 ms   (+4.61%) |       1   →       1              |       51.94 ms →       54.33 ms   (+4.61%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.89 ms →        2.96 ms   (+2.21%) |       6   →       6              |       17.36 ms →       17.74 ms   (+2.21%) | 
  │ └ sirius::Potential::update                                         |       34.01 ms →       35.95 ms   (+5.71%) |       1   →       1              |       34.01 ms →       35.95 ms   (+5.71%) | 
  │   └ sirius::Potential::generate_local_potential                     |       33.57 ms →       35.55 ms   (+5.89%) |       1   →       1              |       33.57 ms →       35.55 ms   (+5.89%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       29.17 ms →       31.15 ms   (+6.80%) |       1   →       1              |       29.17 ms →       31.15 ms   (+6.80%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        3.85 ms →        3.83 ms   (-0.47%) |       1   →       1              |        3.85 ms →        3.83 ms   (-0.47%) | 
  ├ sirius::Density                                                     |       38.83 ms →       41.30 ms   (+6.35%) |       1   →       1              |       38.83 ms →       41.30 ms   (+6.35%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.82 ms →        2.84 ms   (+0.61%) |       2   →       2              |        5.64 ms →        5.67 ms   (+0.61%) | 
  │ └ sirius::Density::update                                           |       33.05 ms →       35.49 ms   (+7.37%) |       1   →       1              |       33.05 ms →       35.49 ms   (+7.37%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       32.77 ms →       35.21 ms   (+7.45%) |       1   →       1              |       32.77 ms →       35.21 ms   (+7.45%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |       76.92 μs →       78.98 μs   (+2.69%) |       1   →       1              |       76.92 μs →       78.98 μs   (+2.69%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       29.43 ms →       31.87 ms   (+8.31%) |       1   →       1              |       29.43 ms →       31.87 ms   (+8.31%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        2.90 ms →        2.91 ms   (+0.13%) |       1   →       1              |        2.90 ms →        2.91 ms   (+0.13%) | 
  ├ sirius::Density::initial_density                                    |       61.04 ms →       64.53 ms   (+5.72%) |       1   →       1              |       61.04 ms →       64.53 ms   (+5.72%) | 
- │ ├ sirius::Simulation_context::make_periodic_function                |       32.88 ms →       36.84 ms  (+12.02%) |       1   →       1              |       32.88 ms →       36.84 ms  (+12.02%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.54 ms →        4.39 ms   (-3.24%) |       2   →       2              |        9.07 ms →        8.78 ms   (-3.24%) | 
  │ └ sirius::Periodic_function::integrate                              |        5.34 ms →        5.28 ms   (-1.03%) |       1   →       1              |        5.34 ms →        5.28 ms   (-1.03%) | 
  ├ sirius::Potential::generate                                         |      366.54 ms →      373.03 ms   (+1.77%) |       1   →       1              |      366.54 ms →      373.03 ms   (+1.77%) | 
- │ ├ sirius::Potential::poisson                                        |       39.23 ms →       44.42 ms  (+13.22%) |       1   →       1              |       39.23 ms →       44.42 ms  (+13.22%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.88 ms →        3.67 ms  (+27.48%) |       1   →       1              |        2.88 ms →        3.67 ms  (+27.48%) | 
+ │ │ └ sirius::Periodic_function|inner                                 |        5.38 ms →        4.63 ms  (-13.91%) |       1   →       1              |        5.38 ms →        4.63 ms  (-13.91%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.64 ms →        4.62 ms   (-0.39%) |       1   →       1              |        4.64 ms →        4.62 ms   (-0.39%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.63 ms →        4.62 ms   (-0.35%) |       1   →       1              |        4.63 ms →        4.62 ms   (-0.35%) | 
  │ ├ sirius::Periodic_function::add                                    |      826.46 μs →      803.12 μs   (-2.82%) |       2   →       2              |        1.65 ms →        1.61 ms   (-2.82%) | 
  │ ├ sirius::Potential::xc                                             |       51.17 ms →       52.57 ms   (+2.72%) |       1   →       1              |       51.17 ms →       52.57 ms   (+2.72%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       50.00 ms →       51.37 ms   (+2.74%) |       1   →       1              |       50.00 ms →       51.37 ms   (+2.74%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.58 ms →        2.56 ms   (-1.04%) |       2   →       2              |        5.17 ms →        5.11 ms   (-1.04%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.16 ms →        3.95 ms   (-4.89%) |       1   →       1              |        4.16 ms →        3.95 ms   (-4.89%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.85 ms →        3.87 ms   (+0.49%) |       1   →       1              |        3.85 ms →        3.87 ms   (+0.49%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      269.30 ms →      269.18 ms   (-0.05%) |       1   →       1              |      269.30 ms →      269.18 ms   (-0.05%) | 
+ │ └ sirius::Potential::generate_PAW_effective_potential               |      491.00 ns →      225.00 ns  (-54.18%) |       1   →       1              |      491.00 ns →      225.00 ns  (-54.18%) | 
  ├ sirius::Hamiltonian0                                                |        6.43 ms →        6.91 ms   (+7.50%) |       1   →       1              |        6.43 ms →        6.91 ms   (+7.50%) | 
  │ ├ sirius::Local_operator                                            |        5.86 ms →        6.39 ms   (+9.16%) |       1   →       1              |        5.86 ms →        6.39 ms   (+9.16%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.74 ms →        2.75 ms   (+0.46%) |       1   →       1              |        2.74 ms →        2.75 ms   (+0.46%) | 
- │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.33 ms →        2.85 ms  (+22.51%) |       1   →       1              |        2.33 ms →        2.85 ms  (+22.51%) | 
+ │ ├ sirius::Non_local_operator                                        |      125.98 μs →       77.18 μs  (-38.74%) |       2   →       2              |      251.96 μs →      154.36 μs  (-38.74%) | 
- │ ├ sirius::D_operator::initialize                                    |      114.80 μs →      172.91 μs  (+50.63%) |       1   →       1              |      114.80 μs →      172.91 μs  (+50.63%) | 
+ │ └ sirius::Q_operator::initialize                                    |      121.01 μs →      108.03 μs  (-10.72%) |       1   →       1              |      121.01 μs →      108.03 μs  (-10.72%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.28 s  →        1.29 s    (+0.59%) |       1   →       1              |        1.28 s  →        1.29 s    (+0.59%) | 
- │ ├ sirius::Hamiltonian_k                                             |       32.96 ms →       55.35 ms  (+67.93%) |       1   →       1              |       32.96 ms →       55.35 ms  (+67.93%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      274.56 μs →      300.19 μs   (+9.34%) |       1   →       1              |      274.56 μs →      300.19 μs   (+9.34%) | 
- │ │ └ sirius::Beta_projectors_base::prepare                           |       32.68 ms →       55.05 ms  (+68.44%) |       1   →       1              |       32.68 ms →       55.05 ms  (+68.44%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.25 s  →        1.23 s    (-1.19%) |       1   →       1              |        1.25 s  →        1.23 s    (-1.19%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       81.98 ms →       76.95 ms   (-6.14%) |       4   →       4              |      327.92 ms →      307.79 ms   (-6.14%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       52.36 ms →       48.05 ms   (-8.24%) |       1   →       1              |       52.36 ms →       48.05 ms   (-8.24%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        7.45 ms →        7.84 ms   (+5.24%) |       1   →       1              |        7.45 ms →        7.84 ms   (+5.24%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      335.38 ms →      337.04 ms   (+0.49%) |       1   →       1              |      335.38 ms →      337.04 ms   (+0.49%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      247.16 ms →      248.62 ms   (+0.59%) |       1   →       1              |      247.16 ms →      248.62 ms   (+0.59%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        4.06 μs →        4.23 μs   (+4.21%) |       1   →       1              |        4.06 μs →        4.23 μs   (+4.21%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.04 μs →        2.89 μs   (-4.87%) |       1   →       1              |        3.04 μs →        2.89 μs   (-4.87%) | 
+ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      478.00 ns →      394.00 ns  (-17.57%) |       1   →       1              |      478.00 ns →      394.00 ns  (-17.57%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      562.00 ns →      613.00 ns   (+9.07%) |       1   →       1              |      562.00 ns →      613.00 ns   (+9.07%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.16 ms →        3.22 ms   (+1.98%) |       1   →       1              |        3.16 ms →        3.22 ms   (+1.98%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.30 ms →       21.27 ms   (-0.14%) |       1   →       1              |       21.30 ms →       21.27 ms   (-0.14%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       31.86 ms →       31.94 ms   (+0.25%) |       2   →       2              |       63.72 ms →       63.88 ms   (+0.25%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.75 ms →       14.74 ms   (-0.10%) |       2   →       2              |       29.51 ms →       29.48 ms   (-0.10%) | 
  │ │ │ └ sddk::wf_inner                                                |       14.54 ms →       14.53 ms   (-0.10%) |       2   →       2              |       29.09 ms →       29.06 ms   (-0.10%) | 
  │ │ │   ├ sddk::wf_inner|scale                                        |       20.50 ns →       21.00 ns   (+2.44%) |       2   →       2              |       41.00 ns →       42.00 ns   (+2.44%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       14.40 ms →       14.39 ms   (-0.02%) |       2   →       2              |       28.80 ms →       28.79 ms   (-0.02%) | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |       20.50 ns →       18.50 ns   (-9.76%) |       2   →       2              |       41.00 ns →       37.00 ns   (-9.76%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      231.14 ms →      235.44 ms   (+1.86%) |       1   →       1              |      231.14 ms →      235.44 ms   (+1.86%) | 
  │ │ └ sddk::wf_trans                                                  |        2.62 ms →        2.62 ms   (-0.03%) |       1   →       1              |        2.62 ms →        2.62 ms   (-0.03%) | 
  │ │   └ sddk::wf_trans|pw                                             |        2.61 ms →        2.61 ms   (-0.06%) |       1   →       1              |        2.61 ms →        2.61 ms   (-0.06%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      749.00 ns →      399.00 ns  (-46.73%) |       1   →       1              |      749.00 ns →      399.00 ns  (-46.73%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |       62.03 s  →       63.11 s    (+1.75%) |       1   →       1              |       62.03 s  →       63.11 s    (+1.75%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.45 ms →        2.44 ms   (-0.15%) |      19   →      19              |       46.52 ms →       46.45 ms   (-0.15%) | 
! │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.25 s  →        2.99 s    (-8.17%) |      19   →      21    (+10.53%) |       61.83 s  →       62.75 s    (+1.49%) | 
! │ │ ├ sirius::Hamiltonian0                                            |        5.41 ms →        4.92 ms   (-9.09%) |      19   →      21    (+10.53%) |      102.78 ms →      103.27 ms   (+0.48%) | 
! │ │ │ ├ sirius::Local_operator                                        |        4.65 ms →        4.29 ms   (-7.82%) |      19   →      21    (+10.53%) |       88.39 ms →       90.05 ms   (+1.88%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function                            |      544.05 μs →      566.75 μs   (+4.17%) |      19   →      21    (+10.53%) |       10.34 ms →       11.90 ms  (+15.14%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.95 ms →        2.64 ms  (-10.50%) |      19   →      21    (+10.53%) |       56.03 ms →       55.42 ms   (-1.07%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |      224.85 μs →      166.87 μs  (-25.79%) |      38   →      42    (+10.53%) |        8.54 ms →        7.01 ms  (-17.98%) | 
! │ │ │ ├ sirius::D_operator::initialize                                |      129.79 μs →      120.45 μs   (-7.20%) |      19   →      21    (+10.53%) |        2.47 ms →        2.53 ms   (+2.57%) | 
! │ │ │ └ sirius::Q_operator::initialize                                |       94.19 μs →       90.74 μs   (-3.67%) |      19   →      21    (+10.53%) |        1.79 ms →        1.91 ms   (+6.47%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.03 s  →        1.76 s   (-13.26%) |      19   →      21    (+10.53%) |       38.57 s  →       36.98 s    (-4.13%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      226.28 μs →      269.98 μs  (+19.31%) |      19   →      21    (+10.53%) |        4.30 ms →        5.67 ms  (+31.87%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      217.11 μs →      261.37 μs  (+20.38%) |      19   →      21    (+10.53%) |        4.13 ms →        5.49 ms  (+33.06%) | 
! │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        6.76 μs →        6.43 μs   (-4.94%) |      19   →      21    (+10.53%) |      128.46 μs →      134.96 μs   (+5.06%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.97 s  →        1.64 s   (-16.77%) |      19   →      21    (+10.53%) |       37.39 s  →       34.39 s    (-8.01%) | 
! │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       76.97 ms →       72.04 ms   (-6.41%) |      19   →      21    (+10.53%) |        1.46 s  →        1.51 s    (+3.44%) | 
! │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.98 ms →        7.22 ms   (-9.48%) |     114   →     126    (+10.53%) |      909.26 ms →      909.75 ms   (+0.05%) | 
- │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       18.35 ms →       18.46 ms   (+0.61%) |      19   →      21    (+10.53%) |      348.66 ms →      387.71 ms  (+11.20%) | 
! │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      462.22 μs →      453.23 μs   (-1.95%) |      19   →      21    (+10.53%) |        8.78 ms →        9.52 ms   (+8.37%) | 
- │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        8.39 ms →        8.50 ms   (+1.32%) |      38   →      42    (+10.53%) |      318.91 ms →      357.12 ms  (+11.98%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.86 s  →        1.54 s   (-17.41%) |      19   →      21    (+10.53%) |       35.41 s  →       32.32 s    (-8.72%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       50.92 ms →       55.69 ms   (+9.38%) |     356   →     361     (+1.40%) |       18.13 s  →       20.11 s   (+10.92%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       28.85 ms →       31.00 ms   (+7.47%) |     356   →     361     (+1.40%) |       10.27 s  →       11.19 s    (+8.98%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.15 μs →        2.16 μs   (+0.53%) |     356   →     361     (+1.40%) |      766.61 μs →      781.50 μs   (+1.94%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.84 μs →        1.81 μs   (-1.40%) |     356   →     361     (+1.40%) |      655.15 μs →      655.05 μs   (-0.01%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      465.62 ns →      473.77 ns   (+1.75%) |     356   →     361     (+1.40%) |      165.76 μs →      171.03 μs   (+3.18%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      650.15 ns →      702.72 ns   (+8.09%) |     356   →     361     (+1.40%) |      231.45 μs →      253.68 μs   (+9.61%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.77 ms →        2.93 ms   (+5.58%) |     356   →     361     (+1.40%) |      987.40 ms →        1.06 s    (+7.06%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.19 ms →        3.38 ms   (+5.92%) |     356   →     361     (+1.40%) |        1.13 s  →        1.22 s    (+7.41%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        8.04 ms →        9.18 ms  (+14.16%) |     712   →     722     (+1.40%) |        5.73 s  →        6.63 s   (+15.76%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |        6.36 ms →        6.86 ms   (+7.98%) |     356   →     361     (+1.40%) |        2.26 s  →        2.48 s    (+9.50%) | 
- │ │ │ │   │ ├ sddk::wf_inner                                          |        1.07 ms →        1.20 ms  (+12.58%) |     693   →     701     (+1.15%) |      739.43 ms →      842.08 ms  (+13.88%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       50.69 ns →       45.41 ns  (-10.42%) |     693   →     701     (+1.15%) |       35.13 μs →       31.83 μs   (-9.38%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |      907.26 μs →        1.04 ms  (+14.52%) |     693   →     701     (+1.15%) |      628.73 ms →      728.33 ms  (+15.84%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       44.37 ns →       48.50 ns   (+9.31%) |     693   →     701     (+1.15%) |       30.75 μs →       34.00 μs  (+10.57%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      135.51 μs →      146.55 μs   (+8.15%) |     356   →     361     (+1.40%) |       48.24 ms →       52.90 ms   (+9.66%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        1.84 ms →        2.06 ms  (+11.98%) |     356   →     361     (+1.40%) |      656.06 ms →      744.95 ms  (+13.55%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |        2.43 ms →        2.46 ms   (+1.39%) |     337   →     340     (+0.89%) |      817.29 ms →      836.03 ms   (+2.29%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |      807.57 μs →      818.76 μs   (+1.39%) |    1.01 K →    1.02 K   (+0.89%) |      816.45 ms →      835.14 ms   (+2.29%) | 
- │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.46 ms →        1.59 ms   (+8.95%) |     356   →     361     (+1.40%) |      518.68 ms →      573.01 ms  (+10.48%) | 
- │ │ │ │   │ └ sddk::wf_inner                                          |        1.38 ms →        1.54 ms  (+11.25%) |     356   →     361     (+1.40%) |      492.79 ms →      555.91 ms  (+12.81%) | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       39.07 ns →       42.02 ns   (+7.56%) |     356   →     361     (+1.40%) |       13.91 μs →       15.17 μs   (+9.07%) | 
- │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        1.22 ms →        1.38 ms  (+12.55%) |     356   →     361     (+1.40%) |      435.27 ms →      496.77 ms  (+14.13%) | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       42.79 ns →       46.37 ns   (+8.36%) |     356   →     361     (+1.40%) |       15.23 μs →       16.74 μs   (+9.89%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       37.10 ms →       21.21 ms  (-42.84%) |     356   →     361     (+1.40%) |       13.21 s  →        7.66 s   (-42.03%) | 
- │ │ │ │   ├ sirius::residuals                                         |        2.60 ms →        3.02 ms  (+15.97%) |     340   →     346     (+1.76%) |      884.40 ms →        1.04 s   (+18.02%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |        1.40 ms →        1.37 ms   (-1.82%) |     337   →     342     (+1.48%) |      470.27 ms →      468.57 ms   (-0.36%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      696.27 μs →      683.55 μs   (-1.83%) |     674   →     684     (+1.48%) |      469.29 ms →      467.55 ms   (-0.37%) | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.11 ms →        1.54 ms  (+38.78%) |     337   →     342     (+1.48%) |      374.55 ms →      527.53 ms  (+40.84%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        7.45 ms →        5.11 ms  (-31.33%) |      54   →      90    (+66.67%) |      402.09 ms →      460.21 ms  (+14.45%) | 
- │ │ │ │     └ sddk::wf_trans                                          |        4.47 ms →        2.84 ms  (-36.40%) |      89   →     159    (+78.65%) |      397.51 ms →      451.66 ms  (+13.62%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |        3.20 ms →        1.98 ms  (-38.22%) |     124   →     228    (+83.87%) |      397.31 ms →      451.31 ms  (+13.59%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      380.53 ns →      560.24 ns  (+47.23%) |      19   →      21    (+10.53%) |        7.23 μs →       11.76 μs  (+62.72%) | 
! │ │ │ └ sirius::K_point_set::sync_band_energies                       |       19.65 μs →       19.52 μs   (-0.63%) |      19   →      21    (+10.53%) |      373.28 μs →      409.97 μs   (+9.83%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.53 ms →        1.53 ms   (+0.14%) |      19   →      21    (+10.53%) |       28.99 ms →       32.08 ms  (+10.68%) | 
- │ │ ├ sirius::Density::generate                                       |      570.03 ms →      569.21 ms   (-0.14%) |      19   →      21    (+10.53%) |       10.83 s  →       11.95 s   (+10.37%) | 
! │ │ │ ├ sirius::Density::generate_valence                             |      424.73 ms →      410.51 ms   (-3.35%) |      19   →      21    (+10.53%) |        8.07 s  →        8.62 s    (+6.83%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.15 μs →        8.25 μs   (+1.22%) |      19   →      21    (+10.53%) |      154.93 μs →      173.31 μs  (+11.87%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.60 μs →        7.74 μs   (+1.79%) |      19   →      21    (+10.53%) |      144.39 μs →      162.45 μs  (+12.51%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       27.54 ms →       30.51 ms  (+10.76%) |      19   →      21    (+10.53%) |      523.30 ms →      640.62 ms  (+22.42%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.70 μs →        8.31 μs   (+7.97%) |      19   →      21    (+10.53%) |      146.31 μs →      174.60 μs  (+19.34%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        4.06 ms →        4.68 ms  (+15.28%) |      19   →      21    (+10.53%) |       77.11 ms →       98.25 ms  (+27.42%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       22.44 ms →       24.79 ms  (+10.47%) |      19   →      21    (+10.53%) |      426.33 ms →      520.56 ms  (+22.10%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      570.53 ns →      758.38 ns  (+32.93%) |      19   →      21    (+10.53%) |       10.84 μs →       15.93 μs  (+46.92%) | 
! │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      118.37 ms →      115.48 ms   (-2.44%) |      19   →      21    (+10.53%) |        2.25 s  →        2.43 s    (+7.83%) | 
! │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.13 ms →        1.95 ms   (-8.40%) |      19   →      21    (+10.53%) |       40.44 ms →       40.94 ms   (+1.25%) | 
! │ │ │ │ └ sirius::Density::augment                                    |      239.45 ms →      223.16 ms   (-6.80%) |      19   →      21    (+10.53%) |        4.55 s  →        4.69 s    (+3.01%) | 
! │ │ │ │   └ sirius::Density::generate_rho_aug                         |      239.24 ms →      222.93 ms   (-6.81%) |      19   →      21    (+10.53%) |        4.55 s  →        4.68 s    (+2.99%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      117.79 ms →      131.36 ms  (+11.53%) |      19   →      21    (+10.53%) |        2.24 s  →        2.76 s   (+23.26%) | 
- │ │ │ │ └ sirius::symmetrize_function|fpw                             |      117.79 ms →      131.36 ms  (+11.53%) |      19   →      21    (+10.53%) |        2.24 s  →        2.76 s   (+23.27%) | 
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       33.88 ms →       47.83 ms  (+41.17%) |      19   →      21    (+10.53%) |      643.77 ms →        1.00 s   (+56.03%) | 
- │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       70.54 ms →       70.25 ms   (-0.41%) |      19   →      21    (+10.53%) |        1.34 s  →        1.48 s   (+10.08%) | 
! │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.71 ms →       12.63 ms   (-0.61%) |      19   →      21    (+10.53%) |      241.48 ms →      265.27 ms   (+9.85%) | 
! │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.74 ms →       23.59 ms   (-0.63%) |      19   →      21    (+10.53%) |      451.02 ms →      495.33 ms   (+9.82%) | 
! │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        3.77 ms →        3.75 ms   (-0.56%) |      19   →      21    (+10.53%) |       71.70 ms →       78.81 ms   (+9.91%) | 
- │ │ ├ sirius::Density::mix                                            |      133.69 ms →      134.54 ms   (+0.64%) |      19   →      21    (+10.53%) |        2.54 s  →        2.83 s   (+11.23%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      621.39 μs →      756.20 μs  (+21.69%) |      19   →      21    (+10.53%) |       11.81 ms →       15.88 ms  (+34.50%) | 
! │ │ │ ├ sirius::Periodic_function|inner                               |        4.92 ms →        4.71 ms   (-4.31%) |     229   →     259    (+13.10%) |        1.13 s  →        1.22 s    (+8.22%) | 
! │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.82 ms →        4.62 ms   (-4.13%) |     229   →     259    (+13.10%) |        1.10 s  →        1.20 s    (+8.43%) | 
! │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.82 ms →        4.62 ms   (-4.13%) |     229   →     259    (+13.10%) |        1.10 s  →        1.20 s    (+8.43%) | 
! │ │ │ └ sirius::Density::mixer_output                                 |        4.75 ms →        4.69 ms   (-1.31%) |      19   →      21    (+10.53%) |       90.34 ms →       98.54 ms   (+9.07%) | 
! │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        4.09 ms →        3.90 ms   (-4.62%) |      19   →      21    (+10.53%) |       77.79 ms →       82.00 ms   (+5.42%) | 
- │ │ ├ sirius::Potential::generate                                     |      360.23 ms →      364.62 ms   (+1.22%) |      19   →      21    (+10.53%) |        6.84 s  →        7.66 s   (+11.87%) | 
- │ │ │ ├ sirius::Potential::poisson                                    |       39.10 ms →       44.26 ms  (+13.18%) |      19   →      21    (+10.53%) |      742.98 ms →      929.45 ms  (+25.10%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.88 ms →        2.91 ms   (+1.03%) |      19   →      21    (+10.53%) |       54.74 ms →       61.12 ms  (+11.66%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |        5.31 ms →        5.28 ms   (-0.45%) |      19   →      21    (+10.53%) |      100.83 ms →      110.94 ms  (+10.03%) | 
- │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.63 ms →        4.63 ms   (+0.06%) |      19   →      21    (+10.53%) |       87.99 ms →       97.30 ms  (+10.59%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.63 ms →        4.63 ms   (+0.06%) |      19   →      21    (+10.53%) |       87.97 ms →       97.28 ms  (+10.59%) | 
- │ │ │ ├ sirius::Periodic_function::add                                |      815.42 μs →      822.35 μs   (+0.85%) |      38   →      42    (+10.53%) |       30.99 ms →       34.54 ms  (+11.46%) | 
! │ │ │ ├ sirius::Potential::xc                                         |       45.05 ms →       44.60 ms   (-1.01%) |      19   →      21    (+10.53%) |      855.98 ms →      936.52 ms   (+9.41%) | 
! │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       43.86 ms →       43.42 ms   (-1.02%) |      19   →      21    (+10.53%) |      833.42 ms →      911.75 ms   (+9.40%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function                          |      665.57 μs →      686.10 μs   (+3.09%) |      38   →      42    (+10.53%) |       25.29 ms →       28.82 ms  (+13.94%) | 
! │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.10 ms →        4.06 ms   (-1.03%) |      19   →      21    (+10.53%) |       77.91 ms →       85.22 ms   (+9.38%) | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.85 ms →        3.88 ms   (+0.53%) |      19   →      21    (+10.53%) |       73.24 ms →       81.38 ms  (+11.11%) | 
- │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      269.19 ms →      268.79 ms   (-0.15%) |      19   →      21    (+10.53%) |        5.11 s  →        5.64 s   (+10.36%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      319.84 ns →      245.62 ns  (-23.21%) |      19   →      21    (+10.53%) |        6.08 μs →        5.16 μs  (-15.12%) | 
! │ │ ├ sirius::Field4D::symmetrize                                     |       96.88 ms →       96.07 ms   (-0.84%) |      19   →      21    (+10.53%) |        1.84 s  →        2.02 s    (+9.60%) | 
! │ │ │ └ sirius::symmetrize_function|fpw                               |       96.88 ms →       96.07 ms   (-0.84%) |      19   →      21    (+10.53%) |        1.84 s  →        2.02 s    (+9.60%) | 
- │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.29 ms →       13.24 ms   (-0.38%) |      19   →      21    (+10.53%) |      252.50 ms →      278.02 ms  (+10.11%) | 
! │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       70.37 ms →       69.61 ms   (-1.08%) |      19   →      21    (+10.53%) |        1.34 s  →        1.46 s    (+9.33%) | 
- │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.59 ms →       12.59 ms   (+0.01%) |      19   →      21    (+10.53%) |      239.18 ms →      264.40 ms  (+10.54%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.61 ms →        3.70 ms   (+2.44%) |      19   →      21    (+10.53%) |       68.55 ms →       77.61 ms  (+13.22%) | 
- │ │ ├ sirius::Periodic_function|inner                                 |        4.70 ms →        4.79 ms   (+1.84%) |     133   →     147    (+10.53%) |      625.16 ms →      703.68 ms  (+12.56%) | 
- │ │ │ └ sirius::Periodic_function|inner_local                         |        4.56 ms →        4.64 ms   (+1.65%) |     133   →     147    (+10.53%) |      606.96 ms →      681.93 ms  (+12.35%) | 
- │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.56 ms →        4.64 ms   (+1.65%) |     133   →     147    (+10.53%) |      606.87 ms →      681.84 ms  (+12.35%) | 
! │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.95 ms →        4.74 ms   (-4.38%) |      57   →      63    (+10.53%) |      282.29 ms →      298.35 ms   (+5.69%) | 
! │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.95 ms →        4.73 ms   (-4.39%) |      57   →      63    (+10.53%) |      281.89 ms →      297.90 ms   (+5.68%) | 
- │ │ ├ sirius::Periodic_function::integrate                            |        4.54 ms →        4.54 ms   (+0.07%) |      19   →      21    (+10.53%) |       86.23 ms →       95.38 ms  (+10.61%) | 
! │ │ └ sirius::Density::get_magnetisation                              |       78.22 μs →       75.96 μs   (-2.89%) |      19   →      21    (+10.53%) |        1.49 ms →        1.60 ms   (+7.33%) | 
! │ │   └ sirius::Density::compute_atomic_mag_mom                       |       73.20 μs →       71.13 μs   (-2.82%) |      19   →      21    (+10.53%) |        1.39 ms →        1.49 ms   (+7.41%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.19 ms →        5.63 ms   (+8.49%) |       2   →       2              |       10.38 ms →       11.26 ms   (+8.49%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.80 ms →        4.81 ms   (+0.15%) |       6   →       6              |       28.79 ms →       28.83 ms   (+0.15%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.79 ms →        4.80 ms   (+0.16%) |       6   →       6              |       28.77 ms →       28.81 ms   (+0.16%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.79 ms →        4.80 ms   (+0.19%) |       6   →       6              |       28.75 ms →       28.81 ms   (+0.19%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        5.18 ms →        5.09 ms   (-1.61%) |       3   →       3              |       15.53 ms →       15.28 ms   (-1.61%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        5.17 ms →        5.03 ms   (-2.79%) |       3   →       3              |       15.52 ms →       15.09 ms   (-2.79%) | 
  ├ sirius::Periodic_function|inner                                     |        4.54 ms →        4.53 ms   (-0.15%) |       2   →       2              |        9.08 ms →        9.06 ms   (-0.15%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.53 ms →        4.52 ms   (-0.16%) |       2   →       2              |        9.06 ms →        9.05 ms   (-0.16%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.53 ms →        4.52 ms   (-0.16%) |       2   →       2              |        9.06 ms →        9.05 ms   (-0.16%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.97 ms →        4.71 ms   (-5.36%) |       1   →       1              |        4.97 ms →        4.71 ms   (-5.36%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.96 ms →        4.70 ms   (-5.23%) |       1   →       1              |        4.96 ms →        4.70 ms   (-5.23%) | 
- └ sirius::finalize                                                    |      194.67 ms →      283.60 ms  (+45.69%) |       1   →       1              |      194.67 ms →      283.60 ms  (+45.69%) | 
  ====================================================================================================================================================================================================
```
