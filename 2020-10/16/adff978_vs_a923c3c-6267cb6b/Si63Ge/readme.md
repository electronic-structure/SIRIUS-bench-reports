# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |       71.90 s  →       72.90 s    (+1.40%) |       1   →       1              |       71.90 s  →       72.90 s    (+1.40%) | 
  ├ sirius::initialize                                                  |        3.10 s  →        2.87 s    (-7.62%) |       1   →       1              |        3.10 s  →        2.87 s    (-7.62%) | 
  ├ sirius::Simulation_context::initialize                              |        3.62 s  →        3.82 s    (+5.33%) |       1   →       1              |        3.62 s  →        3.82 s    (+5.33%) | 
- │ ├ sirius::Simulation_context::init_comm                             |       10.03 ms →       33.60 ms (+235.02%) |       1   →       1              |       10.03 ms →       33.60 ms (+235.02%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      125.59 ms →      229.14 ms  (+82.45%) |       1   →       1              |      125.59 ms →      229.14 ms  (+82.45%) | 
- │ │ ├ sirius::Atom_type::init                                         |       54.17 ms →      105.88 ms  (+95.48%) |       2   →       2              |      108.33 ms →      211.77 ms  (+95.48%) | 
  │ │ └ sirius::Unit_cell::update                                       |       17.17 ms →       17.29 ms   (+0.68%) |       1   →       1              |       17.17 ms →       17.29 ms   (+0.68%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.60 ms →        3.59 ms   (-0.43%) |       1   →       1              |        3.60 ms →        3.59 ms   (-0.43%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       13.48 ms →       13.63 ms   (+1.13%) |       1   →       1              |       13.48 ms →       13.63 ms   (+1.13%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       13.41 ms →       13.57 ms   (+1.18%) |       1   →       1              |       13.41 ms →       13.57 ms   (+1.18%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.75 ms →        2.75 ms   (+0.22%) |       1   →       1              |        2.75 ms →        2.75 ms   (+0.22%) | 
- │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      503.19 μs →      570.04 μs  (+13.29%) |       1   →       1              |      503.19 μs →      570.04 μs  (+13.29%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       15.76 μs →       16.00 μs   (+1.54%) |       1   →       1              |       15.76 μs →       16.00 μs   (+1.54%) | 
  │ └ sirius::Simulation_context::update                                |        3.43 s  →        3.46 s    (+0.69%) |       1   →       1              |        3.43 s  →        3.46 s    (+0.69%) | 
  │   ├ sirius::Unit_cell::update                                       |        6.89 ms →        6.87 ms   (-0.33%) |       1   →       1              |        6.89 ms →        6.87 ms   (-0.33%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.52 ms →        3.48 ms   (-1.32%) |       1   →       1              |        3.52 ms →        3.48 ms   (-1.32%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.31 ms →        3.34 ms   (+0.96%) |       1   →       1              |        3.31 ms →        3.34 ms   (+0.96%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.26 ms →        3.27 ms   (+0.05%) |       1   →       1              |        3.26 ms →        3.27 ms   (+0.05%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.72 ms →        2.72 ms   (-0.22%) |       1   →       1              |        2.72 ms →        2.72 ms   (-0.22%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      502.97 μs →      510.44 μs   (+1.48%) |       1   →       1              |      502.97 μs →      510.44 μs   (+1.48%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       14.45 μs →       14.68 μs   (+1.65%) |       1   →       1              |       14.45 μs →       14.68 μs   (+1.65%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      211.56 ms →      223.57 ms   (+5.68%) |       2   →       2              |      423.12 ms →      447.14 ms   (+5.68%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.15 ms →       15.18 ms   (+0.17%) |       2   →       2              |       30.30 ms →       30.35 ms   (+0.17%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.25 ms →       13.28 ms   (+0.22%) |       1   →       1              |       13.25 ms →       13.28 ms   (+0.22%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.34 ms →       56.35 ms   (+0.01%) |       2   →       2              |      112.69 ms →      112.70 ms   (+0.01%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.11 ms →       45.12 ms   (+0.02%) |       2   →       2              |       90.22 ms →       90.24 ms   (+0.02%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.56 ms →       60.34 ms   (-0.36%) |       4   →       4              |      242.22 ms →      241.36 ms   (-0.36%) | 
  │   ├ sddk::Gvec::init                                                |       95.00 ms →       92.64 ms   (-2.49%) |       2   →       2              |      190.00 ms →      185.28 ms   (-2.49%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       71.22 ms →       69.25 ms   (-2.76%) |       2   →       2              |      142.43 ms →      138.50 ms   (-2.76%) | 
- │   ├ sddk::Gvec_shells                                               |       94.74 ms →      112.63 ms  (+18.88%) |       1   →       1              |       94.74 ms →      112.63 ms  (+18.88%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.95 ms →        1.94 ms   (-0.45%) |       1   →       1              |        1.95 ms →        1.94 ms   (-0.45%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      565.94 ms →      570.26 ms   (+0.76%) |       2   →       2              |        1.13 s  →        1.14 s    (+0.76%) | 
- ├ sirius::K_point_set::create_k_mesh                                  |       87.91 ms →      149.03 ms  (+69.53%) |       1   →       1              |       87.91 ms →      149.03 ms  (+69.53%) | 
- │ ├ sirius::K_point::K_point                                          |        1.36 μs →        2.60 μs  (+91.13%) |       4   →       4              |        5.45 μs →       10.41 μs  (+91.13%) | 
- │ └ sirius::K_point_set::initialize                                   |       87.83 ms →      148.95 ms  (+69.59%) |       1   →       1              |       87.83 ms →      148.95 ms  (+69.59%) | 
  │   └ sirius::K_point::initialize                                     |       27.77 ms →       28.64 ms   (+3.12%) |       1   →       1              |       27.77 ms →       28.64 ms   (+3.12%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       10.91 ms →       11.14 ms   (+2.04%) |       1   →       1              |       10.91 ms →       11.14 ms   (+2.04%) | 
  │     │ └ sddk::Gvec::init                                            |        4.93 ms →        5.01 ms   (+1.70%) |       1   →       1              |        4.93 ms →        5.01 ms   (+1.70%) | 
- │     ├ sddk::matrix_storage::matrix_storage                          |        9.88 μs →       31.79 μs (+221.90%) |       1   →       1              |        9.88 μs →       31.79 μs (+221.90%) | 
  │     └ sirius::K_point::update                                       |       14.02 ms →       14.68 ms   (+4.70%) |       1   →       1              |       14.02 ms →       14.68 ms   (+4.70%) | 
  │       └ sirius::Beta_projectors                                     |       10.14 ms →       10.76 ms   (+6.09%) |       1   →       1              |       10.14 ms →       10.76 ms   (+6.09%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.28 ms →        8.76 ms   (+5.90%) |       1   →       1              |        8.28 ms →        8.76 ms   (+5.90%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.54 ms →        2.61 ms   (+2.86%) |       2   →       2              |        5.07 ms →        5.22 ms   (+2.86%) | 
  ├ sirius::Potential                                                   |       52.11 ms →       51.88 ms   (-0.45%) |       1   →       1              |       52.11 ms →       51.88 ms   (-0.45%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.90 ms →        2.90 ms   (+0.25%) |       6   →       6              |       17.38 ms →       17.43 ms   (+0.25%) | 
  │ └ sirius::Potential::update                                         |       34.13 ms →       33.84 ms   (-0.87%) |       1   →       1              |       34.13 ms →       33.84 ms   (-0.87%) | 
  │   └ sirius::Potential::generate_local_potential                     |       33.75 ms →       33.43 ms   (-0.93%) |       1   →       1              |       33.75 ms →       33.43 ms   (-0.93%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       29.30 ms →       24.03 ms  (-17.98%) |       1   →       1              |       29.30 ms →       24.03 ms  (-17.98%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        3.92 ms →        8.89 ms (+126.75%) |       1   →       1              |        3.92 ms →        8.89 ms (+126.75%) | 
  ├ sirius::Density                                                     |       42.27 ms →       39.83 ms   (-5.76%) |       1   →       1              |       42.27 ms →       39.83 ms   (-5.76%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.81 ms →        2.81 ms   (+0.16%) |       2   →       2              |        5.62 ms →        5.63 ms   (+0.16%) | 
  │ └ sirius::Density::update                                           |       36.51 ms →       34.06 ms   (-6.69%) |       1   →       1              |       36.51 ms →       34.06 ms   (-6.69%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       36.29 ms →       33.84 ms   (-6.75%) |       1   →       1              |       36.29 ms →       33.84 ms   (-6.75%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |       78.10 μs →       77.93 μs   (-0.22%) |       1   →       1              |       78.10 μs →       77.93 μs   (-0.22%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       29.57 ms →       24.25 ms  (-18.01%) |       1   →       1              |       29.57 ms →       24.25 ms  (-18.01%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        6.31 ms →        9.22 ms  (+46.04%) |       1   →       1              |        6.31 ms →        9.22 ms  (+46.04%) | 
  ├ sirius::Density::initial_density                                    |       61.41 ms →       58.76 ms   (-4.31%) |       1   →       1              |       61.41 ms →       58.76 ms   (-4.31%) | 
+ │ ├ sirius::Simulation_context::make_periodic_function                |       33.01 ms →       25.14 ms  (-23.86%) |       1   →       1              |       33.01 ms →       25.14 ms  (-23.86%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.08 ms →        7.15 ms  (+40.72%) |       2   →       2              |       10.16 ms →       14.30 ms  (+40.72%) | 
- │ └ sirius::Periodic_function::integrate                              |        4.60 ms →        5.71 ms  (+24.30%) |       1   →       1              |        4.60 ms →        5.71 ms  (+24.30%) | 
  ├ sirius::Potential::generate                                         |      368.51 ms →      364.26 ms   (-1.15%) |       1   →       1              |      368.51 ms →      364.26 ms   (-1.15%) | 
+ │ ├ sirius::Potential::poisson                                        |       41.50 ms →       37.22 ms  (-10.32%) |       1   →       1              |       41.50 ms →       37.22 ms  (-10.32%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        4.71 ms →        8.41 ms  (+78.44%) |       1   →       1              |        4.71 ms →        8.41 ms  (+78.44%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        5.91 ms →        5.90 ms   (-0.16%) |       1   →       1              |        5.91 ms →        5.90 ms   (-0.16%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.65 ms →        4.65 ms   (+0.01%) |       1   →       1              |        4.65 ms →        4.65 ms   (+0.01%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.64 ms →        4.64 ms   (+0.02%) |       1   →       1              |        4.64 ms →        4.64 ms   (+0.02%) | 
  │ ├ sirius::Periodic_function::add                                    |      794.51 μs →      791.85 μs   (-0.34%) |       2   →       2              |        1.59 ms →        1.58 ms   (-0.34%) | 
  │ ├ sirius::Potential::xc                                             |       51.46 ms →       51.35 ms   (-0.22%) |       1   →       1              |       51.46 ms →       51.35 ms   (-0.22%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       50.27 ms →       50.14 ms   (-0.25%) |       1   →       1              |       50.27 ms →       50.14 ms   (-0.25%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.53 ms →        2.57 ms   (+1.45%) |       2   →       2              |        5.07 ms →        5.14 ms   (+1.45%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.54 ms →        4.36 ms   (-3.78%) |       1   →       1              |        4.54 ms →        4.36 ms   (-3.78%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.71 ms →        3.87 ms   (+4.31%) |       1   →       1              |        3.71 ms →        3.87 ms   (+4.31%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      268.83 ms →      268.78 ms   (-0.02%) |       1   →       1              |      268.83 ms →      268.78 ms   (-0.02%) | 
- │ └ sirius::Potential::generate_PAW_effective_potential               |      151.00 ns →      227.00 ns  (+50.33%) |       1   →       1              |      151.00 ns →      227.00 ns  (+50.33%) | 
+ ├ sirius::Hamiltonian0                                                |        8.37 ms →        6.32 ms  (-24.52%) |       1   →       1              |        8.37 ms →        6.32 ms  (-24.52%) | 
+ │ ├ sirius::Local_operator                                            |        7.29 ms →        5.85 ms  (-19.74%) |       1   →       1              |        7.29 ms →        5.85 ms  (-19.74%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.74 ms →        2.74 ms   (+0.13%) |       1   →       1              |        2.74 ms →        2.74 ms   (+0.13%) | 
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        3.49 ms →        2.34 ms  (-32.96%) |       1   →       1              |        3.49 ms →        2.34 ms  (-32.96%) | 
+ │ ├ sirius::Non_local_operator                                        |      407.04 μs →       72.76 μs  (-82.12%) |       2   →       2              |      814.08 μs →      145.52 μs  (-82.12%) | 
  │ ├ sirius::D_operator::initialize                                    |      110.75 μs →      112.14 μs   (+1.25%) |       1   →       1              |      110.75 μs →      112.14 μs   (+1.25%) | 
- │ └ sirius::Q_operator::initialize                                    |       89.16 μs →      125.84 μs  (+41.14%) |       1   →       1              |       89.16 μs →      125.84 μs  (+41.14%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.28 s  →        1.27 s    (-0.17%) |       1   →       1              |        1.28 s  →        1.27 s    (-0.17%) | 
+ │ ├ sirius::Hamiltonian_k                                             |       51.77 ms →       32.05 ms  (-38.08%) |       1   →       1              |       51.77 ms →       32.05 ms  (-38.08%) | 
- │ │ ├ sirius::Local_operator::prepare_k                               |      265.44 μs →      378.08 μs  (+42.43%) |       1   →       1              |      265.44 μs →      378.08 μs  (+42.43%) | 
+ │ │ └ sirius::Beta_projectors_base::prepare                           |       51.50 ms →       31.67 ms  (-38.50%) |       1   →       1              |       51.50 ms →       31.67 ms  (-38.50%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.22 s  →        1.24 s    (+1.43%) |       1   →       1              |        1.22 s  →        1.24 s    (+1.43%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       78.45 ms →       78.53 ms   (+0.11%) |       4   →       4              |      313.78 ms →      314.14 ms   (+0.11%) | 
- │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       37.41 ms →       52.62 ms  (+40.66%) |       1   →       1              |       37.41 ms →       52.62 ms  (+40.66%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        7.05 ms →        7.73 ms   (+9.54%) |       1   →       1              |        7.05 ms →        7.73 ms   (+9.54%) | 
+ │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      354.05 ms →      314.00 ms  (-11.31%) |       1   →       1              |      354.05 ms →      314.00 ms  (-11.31%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      248.86 ms →      245.47 ms   (-1.36%) |       1   →       1              |      248.86 ms →      245.47 ms   (-1.36%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        4.82 μs →        3.82 μs  (-20.62%) |       1   →       1              |        4.82 μs →        3.82 μs  (-20.62%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.86 μs →        2.79 μs  (-27.72%) |       1   →       1              |        3.86 μs →        2.79 μs  (-27.72%) | 
+ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      710.00 ns →      431.00 ns  (-39.30%) |       1   →       1              |      710.00 ns →      431.00 ns  (-39.30%) | 
- │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      572.00 ns →      632.00 ns  (+10.49%) |       1   →       1              |      572.00 ns →      632.00 ns  (+10.49%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.22 ms →        3.12 ms   (-3.15%) |       1   →       1              |        3.22 ms →        3.12 ms   (-3.15%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       23.52 ms →       21.31 ms   (-9.39%) |       1   →       1              |       23.52 ms →       21.31 ms   (-9.39%) | 
+ │ │ │ └ sirius::Non_local_operator::apply                             |       39.20 ms →       22.03 ms  (-43.81%) |       2   →       2              |       78.40 ms →       44.05 ms  (-43.81%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       16.89 ms →       16.51 ms   (-2.24%) |       2   →       2              |       33.78 ms →       33.02 ms   (-2.24%) | 
  │ │ │ └ sddk::wf_inner                                                |       16.68 ms →       16.30 ms   (-2.29%) |       2   →       2              |       33.37 ms →       32.60 ms   (-2.29%) | 
  │ │ │   ├ sddk::wf_inner|scale                                        |       21.00 ns →       21.50 ns   (+2.38%) |       2   →       2              |       42.00 ns →       43.00 ns   (+2.38%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       16.56 ms →       16.18 ms   (-2.32%) |       2   →       2              |       33.12 ms →       32.35 ms   (-2.32%) | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |       20.00 ns →       21.50 ns   (+7.50%) |       2   →       2              |       40.00 ns →       43.00 ns   (+7.50%) | 
- │ │ ├ Eigensolver_cuda|zhegvdx                                        |      209.15 ms →      250.40 ms  (+19.72%) |       1   →       1              |      209.15 ms →      250.40 ms  (+19.72%) | 
  │ │ └ sddk::wf_trans                                                  |        2.60 ms →        2.61 ms   (+0.36%) |       1   →       1              |        2.60 ms →        2.61 ms   (+0.36%) | 
  │ │   └ sddk::wf_trans|pw                                             |        2.59 ms →        2.61 ms   (+0.40%) |       1   →       1              |        2.59 ms →        2.61 ms   (+0.40%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      626.00 ns →      370.00 ns  (-40.89%) |       1   →       1              |      626.00 ns →      370.00 ns  (-40.89%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |       62.17 s  →       63.14 s    (+1.57%) |       1   →       1              |       62.17 s  →       63.14 s    (+1.57%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.44 ms →        2.46 ms   (+0.61%) |      19   →      19              |       46.37 ms →       46.65 ms   (+0.61%) | 
! │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.26 s  →        2.99 s    (-8.13%) |      19   →      21    (+10.53%) |       61.92 s  →       62.87 s    (+1.54%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        5.72 ms →        5.78 ms   (+1.05%) |      19   →      21    (+10.53%) |      108.75 ms →      121.46 ms  (+11.69%) | 
- │ │ │ ├ sirius::Local_operator                                        |        4.95 ms →        4.99 ms   (+0.84%) |      19   →      21    (+10.53%) |       94.09 ms →      104.87 ms  (+11.46%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function                            |      548.89 μs →      553.80 μs   (+0.89%) |      19   →      21    (+10.53%) |       10.43 ms →       11.63 ms  (+11.51%) | 
! │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.15 ms →        3.12 ms   (-1.20%) |      19   →      21    (+10.53%) |       59.91 ms →       65.42 ms   (+9.20%) | 
- │ │ │ ├ sirius::Non_local_operator                                    |      247.56 μs →      252.29 μs   (+1.91%) |      38   →      42    (+10.53%) |        9.41 ms →       10.60 ms  (+12.64%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |      110.07 μs →      114.28 μs   (+3.83%) |      19   →      21    (+10.53%) |        2.09 ms →        2.40 ms  (+14.76%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       89.63 μs →       90.94 μs   (+1.46%) |      19   →      21    (+10.53%) |        1.70 ms →        1.91 ms  (+12.14%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.03 s  →        1.76 s   (-13.32%) |      19   →      21    (+10.53%) |       38.58 s  →       36.97 s    (-4.19%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      199.94 μs →      202.55 μs   (+1.30%) |      19   →      21    (+10.53%) |        3.80 ms →        4.25 ms  (+11.97%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      191.35 μs →      193.00 μs   (+0.86%) |      19   →      21    (+10.53%) |        3.64 ms →        4.05 ms  (+11.48%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        6.17 μs →        7.04 μs  (+14.20%) |      19   →      21    (+10.53%) |      117.14 μs →      147.87 μs  (+26.22%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.97 s  →        1.64 s   (-16.56%) |      19   →      21    (+10.53%) |       37.34 s  →       34.44 s    (-7.78%) | 
! │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       78.85 ms →       73.01 ms   (-7.40%) |      19   →      21    (+10.53%) |        1.50 s  →        1.53 s    (+2.35%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        8.60 ms →        7.63 ms  (-11.22%) |     114   →     126    (+10.53%) |      980.16 ms →      961.81 ms   (-1.87%) | 
- │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       17.85 ms →       18.83 ms   (+5.49%) |      19   →      21    (+10.53%) |      339.11 ms →      395.39 ms  (+16.59%) | 
- │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      474.86 μs →      474.39 μs   (-0.10%) |      19   →      21    (+10.53%) |        9.02 ms →        9.96 ms  (+10.42%) | 
- │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        8.10 ms →        8.72 ms   (+7.68%) |      38   →      42    (+10.53%) |      307.80 ms →      366.35 ms  (+19.02%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.86 s  →        1.54 s   (-17.24%) |      19   →      21    (+10.53%) |       35.35 s  →       32.34 s    (-8.52%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       51.96 ms →       58.35 ms  (+12.29%) |     356   →     361     (+1.40%) |       18.50 s  →       21.06 s   (+13.87%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       29.89 ms →       32.75 ms   (+9.56%) |     356   →     361     (+1.40%) |       10.64 s  →       11.82 s   (+11.10%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.96 μs →        2.19 μs  (+12.02%) |     356   →     361     (+1.40%) |      696.53 μs →      791.21 μs  (+13.59%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.68 μs →        1.82 μs   (+8.77%) |     356   →     361     (+1.40%) |      596.84 μs →      658.29 μs  (+10.30%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      376.42 ns →      472.81 ns  (+25.61%) |     356   →     361     (+1.40%) |      134.01 μs →      170.69 μs  (+27.37%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      435.65 ns →      722.24 ns  (+65.78%) |     356   →     361     (+1.40%) |      155.09 μs →      260.73 μs  (+68.11%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.89 ms →        3.22 ms  (+11.17%) |     356   →     361     (+1.40%) |        1.03 s  →        1.16 s   (+12.74%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.19 ms →        3.40 ms   (+6.52%) |     356   →     361     (+1.40%) |        1.14 s  →        1.23 s    (+8.01%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.98 ms →        9.48 ms  (+18.74%) |     712   →     722     (+1.40%) |        5.69 s  →        6.85 s   (+20.40%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |        6.35 ms →        6.27 ms   (-1.39%) |     356   →     361     (+1.40%) |        2.26 s  →        2.26 s    (-0.00%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        1.19 ms →        1.11 ms   (-6.90%) |     693   →     701     (+1.15%) |      827.57 ms →      779.39 ms   (-5.82%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       53.62 ns →       52.41 ns   (-2.27%) |     693   →     701     (+1.15%) |       37.16 μs →       36.74 μs   (-1.15%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        1.03 ms →      948.69 μs   (-8.18%) |     693   →     701     (+1.15%) |      716.03 ms →      665.03 ms   (-7.12%) | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       44.92 ns →       45.94 ns   (+2.26%) |     693   →     701     (+1.15%) |       31.13 μs →       32.20 μs   (+3.44%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      130.79 μs →      137.60 μs   (+5.21%) |     356   →     361     (+1.40%) |       46.56 ms →       49.67 ms   (+6.68%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        1.75 ms →        1.89 ms   (+8.16%) |     356   →     361     (+1.40%) |      622.24 ms →      682.48 ms   (+9.68%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |        2.27 ms →        2.20 ms   (-2.87%) |     337   →     340     (+0.89%) |      764.16 ms →      748.83 ms   (-2.01%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |      755.10 μs →      733.27 μs   (-2.89%) |    1.01 K →    1.02 K   (+0.89%) |      763.40 ms →      747.94 ms   (-2.03%) | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.49 ms →        1.16 ms  (-21.73%) |     356   →     361     (+1.40%) |      529.13 ms →      419.98 ms  (-20.63%) | 
+ │ │ │ │   │ └ sddk::wf_inner                                          |        1.42 ms →        1.12 ms  (-21.15%) |     356   →     361     (+1.40%) |      504.12 ms →      403.06 ms  (-20.05%) | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       41.72 ns →       41.14 ns   (-1.40%) |     356   →     361     (+1.40%) |       14.85 μs →       14.85 μs   (-0.01%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        1.25 ms →      952.26 μs  (-24.11%) |     356   →     361     (+1.40%) |      446.69 ms →      343.77 ms  (-23.04%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       38.43 ns →       44.44 ns  (+15.64%) |     356   →     361     (+1.40%) |       13.68 μs →       16.04 μs  (+17.26%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       35.74 ms →       19.98 ms  (-44.09%) |     356   →     361     (+1.40%) |       12.72 s  →        7.21 s   (-43.31%) | 
  │ │ │ │   ├ sirius::residuals                                         |        2.76 ms →        2.76 ms   (+0.16%) |     340   →     346     (+1.76%) |      937.27 ms →      955.31 ms   (+1.92%) | 
+ │ │ │ │   │ ├ sddk::wf_trans                                          |        1.41 ms →        1.23 ms  (-12.46%) |     337   →     342     (+1.48%) |      474.92 ms →      421.92 ms  (-11.16%) | 
+ │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      703.30 μs →      615.32 μs  (-12.51%) |     674   →     684     (+1.48%) |      474.02 ms →      420.88 ms  (-11.21%) | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.25 ms →        1.41 ms  (+12.75%) |     337   →     342     (+1.48%) |      422.58 ms →      483.53 ms  (+14.42%) | 
+ │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        7.24 ms →        4.61 ms  (-36.36%) |      54   →      90    (+66.67%) |      391.16 ms →      414.87 ms   (+6.06%) | 
+ │ │ │ │     └ sddk::wf_trans                                          |        4.35 ms →        2.55 ms  (-41.24%) |      89   →     159    (+78.65%) |      386.91 ms →      406.16 ms   (+4.97%) | 
+ │ │ │ │       └ sddk::wf_trans|pw                                     |        3.12 ms →        1.78 ms  (-42.93%) |     124   →     228    (+83.87%) |      386.75 ms →      405.81 ms   (+4.93%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      401.53 ns →      531.29 ns  (+32.32%) |      19   →      21    (+10.53%) |        7.63 μs →       11.16 μs  (+46.24%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       20.23 μs →       20.16 μs   (-0.34%) |      19   →      21    (+10.53%) |      384.31 μs →      423.31 μs  (+10.15%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.52 ms →        1.54 ms   (+0.89%) |      19   →      21    (+10.53%) |       28.95 ms →       32.28 ms  (+11.51%) | 
- │ │ ├ sirius::Density::generate                                       |      571.93 ms →      577.03 ms   (+0.89%) |      19   →      21    (+10.53%) |       10.87 s  →       12.12 s   (+11.51%) | 
! │ │ │ ├ sirius::Density::generate_valence                             |      441.60 ms →      427.12 ms   (-3.28%) |      19   →      21    (+10.53%) |        8.39 s  →        8.97 s    (+6.90%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        9.83 μs →        8.20 μs  (-16.58%) |      19   →      21    (+10.53%) |      186.71 μs →      172.15 μs   (-7.80%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        9.29 μs →        7.68 μs  (-17.28%) |      19   →      21    (+10.53%) |      176.46 μs →      161.33 μs   (-8.58%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       33.86 ms →       36.93 ms   (+9.08%) |      19   →      21    (+10.53%) |      643.27 ms →      775.52 ms  (+20.56%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.33 μs →        8.14 μs  (+10.93%) |      19   →      21    (+10.53%) |      139.35 μs →      170.85 μs  (+22.61%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        5.11 ms →        5.90 ms  (+15.48%) |      19   →      21    (+10.53%) |       97.09 ms →      123.92 ms  (+27.63%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       27.68 ms →       29.96 ms   (+8.24%) |      19   →      21    (+10.53%) |      525.91 ms →      629.17 ms  (+19.63%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      513.89 ns →      760.90 ns  (+48.07%) |      19   →      21    (+10.53%) |        9.76 μs →       15.98 μs  (+63.65%) | 
! │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      111.84 ms →      109.00 ms   (-2.54%) |      19   →      21    (+10.53%) |        2.12 s  →        2.29 s    (+7.72%) | 
! │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.52 ms →        2.35 ms   (-6.98%) |      19   →      21    (+10.53%) |       47.94 ms →       49.29 ms   (+2.81%) | 
! │ │ │ │ └ sirius::Density::augment                                    |      250.80 ms →      243.38 ms   (-2.96%) |      19   →      21    (+10.53%) |        4.77 s  →        5.11 s    (+7.26%) | 
! │ │ │ │   └ sirius::Density::generate_rho_aug                         |      250.59 ms →      243.16 ms   (-2.96%) |      19   →      21    (+10.53%) |        4.76 s  →        5.11 s    (+7.25%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      101.59 ms →      118.59 ms  (+16.73%) |      19   →      21    (+10.53%) |        1.93 s  →        2.49 s   (+29.02%) | 
- │ │ │ │ └ sirius::symmetrize_function|fpw                             |      101.59 ms →      118.58 ms  (+16.73%) |      19   →      21    (+10.53%) |        1.93 s  →        2.49 s   (+29.02%) | 
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       17.62 ms →       34.57 ms  (+96.22%) |      19   →      21    (+10.53%) |      334.72 ms →      725.91 ms (+116.87%) | 
- │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       70.74 ms →       70.71 ms   (-0.04%) |      19   →      21    (+10.53%) |        1.34 s  →        1.48 s   (+10.49%) | 
- │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.58 ms →       12.65 ms   (+0.60%) |      19   →      21    (+10.53%) |      238.98 ms →      265.72 ms  (+11.19%) | 
- │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.63 ms →       23.53 ms   (-0.43%) |      19   →      21    (+10.53%) |      449.02 ms →      494.13 ms  (+10.05%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        5.10 ms →        7.79 ms  (+52.80%) |      19   →      21    (+10.53%) |       96.93 ms →      163.69 ms  (+68.88%) | 
- │ │ ├ sirius::Density::mix                                            |      132.29 ms →      133.71 ms   (+1.08%) |      19   →      21    (+10.53%) |        2.51 s  →        2.81 s   (+11.72%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      724.47 μs →      892.60 μs  (+23.21%) |      19   →      21    (+10.53%) |       13.77 ms →       18.74 ms  (+36.18%) | 
! │ │ │ ├ sirius::Periodic_function|inner                               |        4.86 ms →        4.64 ms   (-4.48%) |     229   →     259    (+13.10%) |        1.11 s  →        1.20 s    (+8.03%) | 
! │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.81 ms →        4.61 ms   (-4.06%) |     229   →     259    (+13.10%) |        1.10 s  →        1.19 s    (+8.51%) | 
! │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.81 ms →        4.61 ms   (-4.06%) |     229   →     259    (+13.10%) |        1.10 s  →        1.19 s    (+8.51%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        6.13 ms →        4.48 ms  (-26.97%) |      19   →      21    (+10.53%) |      116.46 ms →       94.00 ms  (-19.28%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.37 ms →        3.90 ms  (-27.51%) |      19   →      21    (+10.53%) |      102.10 ms →       81.80 ms  (-19.88%) | 
! │ │ ├ sirius::Potential::generate                                     |      362.90 ms →      357.13 ms   (-1.59%) |      19   →      21    (+10.53%) |        6.90 s  →        7.50 s    (+8.77%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |       42.39 ms →       37.98 ms  (-10.41%) |      19   →      21    (+10.53%) |      805.38 ms →      797.53 ms   (-0.97%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        5.63 ms →        9.02 ms  (+60.33%) |      19   →      21    (+10.53%) |      106.88 ms →      189.39 ms  (+77.20%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |        5.89 ms →        5.90 ms   (+0.09%) |      19   →      21    (+10.53%) |      111.91 ms →      123.80 ms  (+10.62%) | 
- │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.63 ms →        4.63 ms   (+0.04%) |      19   →      21    (+10.53%) |       88.01 ms →       97.31 ms  (+10.57%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.63 ms →        4.63 ms   (+0.03%) |      19   →      21    (+10.53%) |       87.99 ms →       97.29 ms  (+10.56%) | 
- │ │ │ ├ sirius::Periodic_function::add                                |      791.29 μs →      797.10 μs   (+0.74%) |      38   →      42    (+10.53%) |       30.07 ms →       33.48 ms  (+11.34%) | 
! │ │ │ ├ sirius::Potential::xc                                         |       45.31 ms →       44.38 ms   (-2.03%) |      19   →      21    (+10.53%) |      860.80 ms →      932.07 ms   (+8.28%) | 
! │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       44.12 ms →       43.20 ms   (-2.09%) |      19   →      21    (+10.53%) |      838.27 ms →      907.18 ms   (+8.22%) | 
! │ │ │ │   ├ sirius::Smooth_periodic_function                          |      683.25 μs →      677.26 μs   (-0.88%) |      38   →      42    (+10.53%) |       25.96 ms →       28.44 ms   (+9.56%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.84 ms →        4.87 ms   (+0.61%) |      19   →      21    (+10.53%) |       92.00 ms →      102.31 ms  (+11.20%) | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.68 ms →        3.70 ms   (+0.58%) |      19   →      21    (+10.53%) |       69.89 ms →       77.69 ms  (+11.17%) | 
- │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.52 ms →      268.01 ms   (-0.19%) |      19   →      21    (+10.53%) |        5.10 s  →        5.63 s   (+10.32%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      296.58 ns →      225.19 ns  (-24.07%) |      19   →      21    (+10.53%) |        5.63 μs →        4.73 μs  (-16.08%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |       97.18 ms →      100.04 ms   (+2.95%) |      19   →      21    (+10.53%) |        1.85 s  →        2.10 s   (+13.79%) | 
- │ │ │ └ sirius::symmetrize_function|fpw                               |       97.17 ms →      100.04 ms   (+2.95%) |      19   →      21    (+10.53%) |        1.85 s  →        2.10 s   (+13.79%) | 
- │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.25 ms →       16.56 ms  (+25.03%) |      19   →      21    (+10.53%) |      251.66 ms →      347.76 ms  (+38.19%) | 
! │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       70.73 ms →       70.27 ms   (-0.65%) |      19   →      21    (+10.53%) |        1.34 s  →        1.48 s    (+9.81%) | 
- │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.58 ms →       12.59 ms   (+0.10%) |      19   →      21    (+10.53%) |      238.94 ms →      264.35 ms  (+10.63%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        4.31 ms →        7.29 ms  (+69.26%) |      19   →      21    (+10.53%) |       81.88 ms →      153.18 ms  (+87.07%) | 
! │ │ ├ sirius::Periodic_function|inner                                 |        4.63 ms →        4.60 ms   (-0.55%) |     133   →     147    (+10.53%) |      615.16 ms →      676.20 ms   (+9.92%) | 
- │ │ │ └ sirius::Periodic_function|inner_local                         |        4.56 ms →        4.55 ms   (-0.22%) |     133   →     147    (+10.53%) |      606.90 ms →      669.33 ms  (+10.29%) | 
- │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.56 ms →        4.55 ms   (-0.21%) |     133   →     147    (+10.53%) |      606.80 ms →      669.25 ms  (+10.29%) | 
! │ │ ├ sirius::Smooth_periodic_function|inner                          |        5.04 ms →        4.73 ms   (-6.13%) |      57   →      63    (+10.53%) |      287.01 ms →      297.78 ms   (+3.75%) | 
! │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        5.03 ms →        4.72 ms   (-6.14%) |      57   →      63    (+10.53%) |      286.65 ms →      297.38 ms   (+3.74%) | 
- │ │ ├ sirius::Periodic_function::integrate                            |        4.55 ms →        4.53 ms   (-0.36%) |      19   →      21    (+10.53%) |       86.38 ms →       95.13 ms  (+10.13%) | 
! │ │ └ sirius::Density::get_magnetisation                              |       77.65 μs →       75.18 μs   (-3.18%) |      19   →      21    (+10.53%) |        1.48 ms →        1.58 ms   (+7.02%) | 
! │ │   └ sirius::Density::compute_atomic_mag_mom                       |       72.59 μs →       70.18 μs   (-3.32%) |      19   →      21    (+10.53%) |        1.38 ms →        1.47 ms   (+6.85%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.15 ms →        5.48 ms   (+6.51%) |       2   →       2              |       10.30 ms →       10.97 ms   (+6.51%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.59 ms →        4.91 ms   (+6.97%) |       6   →       6              |       27.53 ms →       29.45 ms   (+6.97%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.58 ms →        4.91 ms   (+7.03%) |       6   →       6              |       27.50 ms →       29.43 ms   (+7.03%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.58 ms →        4.91 ms   (+7.06%) |       6   →       6              |       27.49 ms →       29.43 ms   (+7.06%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.93 ms →        5.10 ms   (+3.49%) |       3   →       3              |       14.79 ms →       15.31 ms   (+3.49%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.93 ms →        5.10 ms   (+3.47%) |       3   →       3              |       14.78 ms →       15.29 ms   (+3.47%) | 
  ├ sirius::Periodic_function|inner                                     |        4.79 ms →        4.88 ms   (+1.88%) |       2   →       2              |        9.58 ms →        9.76 ms   (+1.88%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.79 ms →        4.88 ms   (+1.90%) |       2   →       2              |        9.57 ms →        9.75 ms   (+1.90%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.79 ms →        4.88 ms   (+1.90%) |       2   →       2              |        9.57 ms →        9.75 ms   (+1.90%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        5.17 ms →        5.08 ms   (-1.61%) |       1   →       1              |        5.17 ms →        5.08 ms   (-1.61%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        5.16 ms →        5.08 ms   (-1.59%) |       1   →       1              |        5.16 ms →        5.08 ms   (-1.59%) | 
+ └ sirius::finalize                                                    |      181.93 ms →      152.73 ms  (-16.05%) |       1   →       1              |      181.93 ms →      152.73 ms  (-16.05%) | 
  ====================================================================================================================================================================================================
```
