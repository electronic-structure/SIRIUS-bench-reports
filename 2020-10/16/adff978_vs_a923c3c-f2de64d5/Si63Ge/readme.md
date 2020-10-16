# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |       71.83 s  →       72.57 s    (+1.04%) |       1   →       1              |       71.83 s  →       72.57 s    (+1.04%) | 
  ├ sirius::initialize                                                  |        2.99 s  →        2.93 s    (-2.05%) |       1   →       1              |        2.99 s  →        2.93 s    (-2.05%) | 
  ├ sirius::Simulation_context::initialize                              |        3.83 s  →        3.95 s    (+3.24%) |       1   →       1              |        3.83 s  →        3.95 s    (+3.24%) | 
- │ ├ sirius::Simulation_context::init_comm                             |      213.05 μs →       30.73 ms (+14326.18%) |       1   →       1              |      213.05 μs →       30.73 ms (+14326.18%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      217.56 ms →      386.57 ms  (+77.69%) |       1   →       1              |      217.56 ms →      386.57 ms  (+77.69%) | 
- │ │ ├ sirius::Atom_type::init                                         |       98.63 ms →      185.53 ms  (+88.10%) |       2   →       2              |      197.27 ms →      371.05 ms  (+88.10%) | 
+ │ │ └ sirius::Unit_cell::update                                       |       20.19 ms →       15.41 ms  (-23.66%) |       1   →       1              |       20.19 ms →       15.41 ms  (-23.66%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.62 ms →        3.60 ms   (-0.34%) |       1   →       1              |        3.62 ms →        3.60 ms   (-0.34%) | 
+ │ │   └ sirius::Unit_cell::get_symmetry                               |       16.50 ms →       11.74 ms  (-28.81%) |       1   →       1              |       16.50 ms →       11.74 ms  (-28.81%) | 
+ │ │     └ sirius::Unit_cell_symmetry                                  |       16.42 ms →       11.68 ms  (-28.88%) |       1   →       1              |       16.42 ms →       11.68 ms  (-28.88%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.75 ms →        2.75 ms   (-0.28%) |       1   →       1              |        2.75 ms →        2.75 ms   (-0.28%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      505.72 μs →      511.24 μs   (+1.09%) |       1   →       1              |      505.72 μs →      511.24 μs   (+1.09%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       16.50 μs →       15.62 μs   (-5.33%) |       1   →       1              |       16.50 μs →       15.62 μs   (-5.33%) | 
  │ └ sirius::Simulation_context::update                                |        3.51 s  →        3.32 s    (-5.36%) |       1   →       1              |        3.51 s  →        3.32 s    (-5.36%) | 
  │   ├ sirius::Unit_cell::update                                       |        6.75 ms →        7.07 ms   (+4.86%) |       1   →       1              |        6.75 ms →        7.07 ms   (+4.86%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.42 ms →        3.67 ms   (+7.33%) |       1   →       1              |        3.42 ms →        3.67 ms   (+7.33%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.28 ms →        3.36 ms   (+2.54%) |       1   →       1              |        3.28 ms →        3.36 ms   (+2.54%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.23 ms →        3.29 ms   (+1.73%) |       1   →       1              |        3.23 ms →        3.29 ms   (+1.73%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.70 ms →        2.73 ms   (+1.18%) |       1   →       1              |        2.70 ms →        2.73 ms   (+1.18%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      496.33 μs →      518.07 μs   (+4.38%) |       1   →       1              |      496.33 μs →      518.07 μs   (+4.38%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       13.58 μs →       14.41 μs   (+6.14%) |       1   →       1              |       13.58 μs →       14.41 μs   (+6.14%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      213.79 ms →      214.30 ms   (+0.24%) |       2   →       2              |      427.58 ms →      428.61 ms   (+0.24%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.21 ms →       15.18 ms   (-0.22%) |       2   →       2              |       30.42 ms →       30.36 ms   (-0.22%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.24 ms →       13.27 ms   (+0.18%) |       1   →       1              |       13.24 ms →       13.27 ms   (+0.18%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.28 ms →       56.34 ms   (+0.11%) |       2   →       2              |      112.55 ms →      112.67 ms   (+0.11%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.06 ms →       45.26 ms   (+0.44%) |       2   →       2              |       90.12 ms →       90.52 ms   (+0.44%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       61.19 ms →       60.35 ms   (-1.36%) |       4   →       4              |      244.75 ms →      241.41 ms   (-1.36%) | 
  │   ├ sddk::Gvec::init                                                |       93.66 ms →       92.94 ms   (-0.77%) |       2   →       2              |      187.32 ms →      185.87 ms   (-0.77%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       70.17 ms →       69.62 ms   (-0.78%) |       2   →       2              |      140.33 ms →      139.24 ms   (-0.78%) | 
  │   ├ sddk::Gvec_shells                                               |       92.60 ms →       96.28 ms   (+3.98%) |       1   →       1              |       92.60 ms →       96.28 ms   (+3.98%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.95 ms →        1.96 ms   (+0.48%) |       1   →       1              |        1.95 ms →        1.96 ms   (+0.48%) | 
+ │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      599.67 ms →      516.50 ms  (-13.87%) |       2   →       2              |        1.20 s  →        1.03 s   (-13.87%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |      145.56 ms →      142.05 ms   (-2.41%) |       1   →       1              |      145.56 ms →      142.05 ms   (-2.41%) | 
  │ ├ sirius::K_point::K_point                                          |        2.14 μs →        1.99 μs   (-6.66%) |       4   →       4              |        8.54 μs →        7.98 μs   (-6.66%) | 
  │ └ sirius::K_point_set::initialize                                   |      145.47 ms →      141.96 ms   (-2.41%) |       1   →       1              |      145.47 ms →      141.96 ms   (-2.41%) | 
  │   └ sirius::K_point::initialize                                     |       28.53 ms →       28.94 ms   (+1.45%) |       1   →       1              |       28.53 ms →       28.94 ms   (+1.45%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       11.16 ms →       11.09 ms   (-0.57%) |       1   →       1              |       11.16 ms →       11.09 ms   (-0.57%) | 
  │     │ └ sddk::Gvec::init                                            |        5.02 ms →        5.00 ms   (-0.40%) |       1   →       1              |        5.02 ms →        5.00 ms   (-0.40%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |       10.30 μs →       11.06 μs   (+7.37%) |       1   →       1              |       10.30 μs →       11.06 μs   (+7.37%) | 
  │     └ sirius::K_point::update                                       |       14.50 ms →       14.98 ms   (+3.28%) |       1   →       1              |       14.50 ms →       14.98 ms   (+3.28%) | 
  │       └ sirius::Beta_projectors                                     |       10.50 ms →       10.99 ms   (+4.68%) |       1   →       1              |       10.50 ms →       10.99 ms   (+4.68%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.62 ms →        8.90 ms   (+3.19%) |       1   →       1              |        8.62 ms →        8.90 ms   (+3.19%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.54 ms →        2.58 ms   (+1.64%) |       2   →       2              |        5.08 ms →        5.17 ms   (+1.64%) | 
  ├ sirius::Potential                                                   |       55.03 ms →       50.61 ms   (-8.05%) |       1   →       1              |       55.03 ms →       50.61 ms   (-8.05%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.90 ms →        2.93 ms   (+0.79%) |       6   →       6              |       17.42 ms →       17.56 ms   (+0.79%) | 
+ │ └ sirius::Potential::update                                         |       37.00 ms →       32.46 ms  (-12.27%) |       1   →       1              |       37.00 ms →       32.46 ms  (-12.27%) | 
+ │   └ sirius::Potential::generate_local_potential                     |       36.61 ms →       32.06 ms  (-12.41%) |       1   →       1              |       36.61 ms →       32.06 ms  (-12.41%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       32.17 ms →       26.47 ms  (-17.70%) |       1   →       1              |       32.17 ms →       26.47 ms  (-17.70%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        3.86 ms →        5.03 ms  (+30.21%) |       1   →       1              |        3.86 ms →        5.03 ms  (+30.21%) | 
  ├ sirius::Density                                                     |       42.24 ms →       39.55 ms   (-6.37%) |       1   →       1              |       42.24 ms →       39.55 ms   (-6.37%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.82 ms →        2.81 ms   (-0.45%) |       2   →       2              |        5.64 ms →        5.61 ms   (-0.45%) | 
  │ └ sirius::Density::update                                           |       36.46 ms →       33.80 ms   (-7.31%) |       1   →       1              |       36.46 ms →       33.80 ms   (-7.31%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       36.19 ms →       33.58 ms   (-7.22%) |       1   →       1              |       36.19 ms →       33.58 ms   (-7.22%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |       77.63 μs →       77.55 μs   (-0.11%) |       1   →       1              |       77.63 μs →       77.55 μs   (-0.11%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       32.80 ms →       26.44 ms  (-19.41%) |       1   →       1              |       32.80 ms →       26.44 ms  (-19.41%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        2.96 ms →        6.77 ms (+128.82%) |       1   →       1              |        2.96 ms →        6.77 ms (+128.82%) | 
+ ├ sirius::Density::initial_density                                    |       65.25 ms →       57.21 ms  (-12.33%) |       1   →       1              |       65.25 ms →       57.21 ms  (-12.33%) | 
+ │ ├ sirius::Simulation_context::make_periodic_function                |       37.26 ms →       26.60 ms  (-28.60%) |       1   →       1              |       37.26 ms →       26.60 ms  (-28.60%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.56 ms →        5.82 ms  (+27.71%) |       2   →       2              |        9.11 ms →       11.64 ms  (+27.71%) | 
  │ └ sirius::Periodic_function::integrate                              |        5.29 ms →        5.34 ms   (+0.94%) |       1   →       1              |        5.29 ms →        5.34 ms   (+0.94%) | 
  ├ sirius::Potential::generate                                         |      373.27 ms →      365.58 ms   (-2.06%) |       1   →       1              |      373.27 ms →      365.58 ms   (-2.06%) | 
+ │ ├ sirius::Potential::poisson                                        |       45.68 ms →       38.85 ms  (-14.95%) |       1   →       1              |       45.68 ms →       38.85 ms  (-14.95%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.67 ms →        7.42 ms (+102.32%) |       1   →       1              |        3.67 ms →        7.42 ms (+102.32%) | 
- │ │ └ sirius::Periodic_function|inner                                 |        5.11 ms →        5.88 ms  (+15.06%) |       1   →       1              |        5.11 ms →        5.88 ms  (+15.06%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        5.10 ms →        4.64 ms   (-8.92%) |       1   →       1              |        5.10 ms →        4.64 ms   (-8.92%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        5.09 ms →        4.64 ms   (-8.97%) |       1   →       1              |        5.09 ms →        4.64 ms   (-8.97%) | 
  │ ├ sirius::Periodic_function::add                                    |      771.09 μs →      739.05 μs   (-4.15%) |       2   →       2              |        1.54 ms →        1.48 ms   (-4.15%) | 
  │ ├ sirius::Potential::xc                                             |       51.41 ms →       50.92 ms   (-0.96%) |       1   →       1              |       51.41 ms →       50.92 ms   (-0.96%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       50.22 ms →       49.72 ms   (-1.00%) |       1   →       1              |       50.22 ms →       49.72 ms   (-1.00%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.54 ms →        2.53 ms   (-0.09%) |       2   →       2              |        5.07 ms →        5.07 ms   (-0.09%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.38 ms →        4.14 ms   (-5.40%) |       1   →       1              |        4.38 ms →        4.14 ms   (-5.40%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.88 ms →        3.79 ms   (-2.43%) |       1   →       1              |        3.88 ms →        3.79 ms   (-2.43%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      269.35 ms →      269.23 ms   (-0.04%) |       1   →       1              |      269.35 ms →      269.23 ms   (-0.04%) | 
+ │ └ sirius::Potential::generate_PAW_effective_potential               |      306.00 ns →      235.00 ns  (-23.20%) |       1   →       1              |      306.00 ns →      235.00 ns  (-23.20%) | 
- ├ sirius::Hamiltonian0                                                |        6.93 ms →        8.49 ms  (+22.52%) |       1   →       1              |        6.93 ms →        8.49 ms  (+22.52%) | 
- │ ├ sirius::Local_operator                                            |        6.34 ms →        7.43 ms  (+17.21%) |       1   →       1              |        6.34 ms →        7.43 ms  (+17.21%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.74 ms →        2.74 ms   (+0.15%) |       1   →       1              |        2.74 ms →        2.74 ms   (+0.15%) | 
- │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.84 ms →        3.66 ms  (+28.99%) |       1   →       1              |        2.84 ms →        3.66 ms  (+28.99%) | 
- │ ├ sirius::Non_local_operator                                        |      120.14 μs →      395.40 μs (+229.11%) |       2   →       2              |      240.28 μs →      790.79 μs (+229.11%) | 
+ │ ├ sirius::D_operator::initialize                                    |      152.43 μs →      112.91 μs  (-25.93%) |       1   →       1              |      152.43 μs →      112.91 μs  (-25.93%) | 
+ │ └ sirius::Q_operator::initialize                                    |      104.71 μs →       89.54 μs  (-14.48%) |       1   →       1              |      104.71 μs →       89.54 μs  (-14.48%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.28 s  →        1.28 s    (-0.04%) |       1   →       1              |        1.28 s  →        1.28 s    (-0.04%) | 
- │ ├ sirius::Hamiltonian_k                                             |       52.12 ms →       66.44 ms  (+27.47%) |       1   →       1              |       52.12 ms →       66.44 ms  (+27.47%) | 
+ │ │ ├ sirius::Local_operator::prepare_k                               |      295.65 μs →      214.60 μs  (-27.41%) |       1   →       1              |      295.65 μs →      214.60 μs  (-27.41%) | 
- │ │ └ sirius::Beta_projectors_base::prepare                           |       51.82 ms →       66.23 ms  (+27.79%) |       1   →       1              |       51.82 ms →       66.23 ms  (+27.79%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.23 s  →        1.22 s    (-1.20%) |       1   →       1              |        1.23 s  →        1.22 s    (-1.20%) | 
- │ │ ├ sddk::matrix_storage::matrix_storage                            |       76.61 ms →       88.49 ms  (+15.51%) |       4   →       4              |      306.45 ms →      353.98 ms  (+15.51%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       47.50 ms →       45.63 ms   (-3.95%) |       1   →       1              |       47.50 ms →       45.63 ms   (-3.95%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        8.00 ms →        8.74 ms   (+9.14%) |       1   →       1              |        8.00 ms →        8.74 ms   (+9.14%) | 
- │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      337.48 ms →      381.22 ms  (+12.96%) |       1   →       1              |      337.48 ms →      381.22 ms  (+12.96%) | 
- │ │ │ ├ sirius::Local_operator::apply_h                               |      249.64 ms →      307.94 ms  (+23.35%) |       1   →       1              |      249.64 ms →      307.94 ms  (+23.35%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        4.50 μs →        4.22 μs   (-6.24%) |       1   →       1              |        4.50 μs →        4.22 μs   (-6.24%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.56 μs →        2.86 μs  (-19.66%) |       1   →       1              |        3.56 μs →        2.86 μs  (-19.66%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      484.00 ns →      504.00 ns   (+4.13%) |       1   →       1              |      484.00 ns →      504.00 ns   (+4.13%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      665.00 ns →      658.00 ns   (-1.05%) |       1   →       1              |      665.00 ns →      658.00 ns   (-1.05%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.24 ms →        3.16 ms   (-2.50%) |       1   →       1              |        3.24 ms →        3.16 ms   (-2.50%) | 
- │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.28 ms →       24.55 ms  (+15.40%) |       1   →       1              |       21.28 ms →       24.55 ms  (+15.40%) | 
+ │ │ │ └ sirius::Non_local_operator::apply                             |       31.64 ms →       22.77 ms  (-28.04%) |       2   →       2              |       63.27 ms →       45.53 ms  (-28.04%) | 
+ │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.95 ms →        7.57 ms  (-49.37%) |       2   →       2              |       29.90 ms →       15.13 ms  (-49.37%) | 
+ │ │ │ └ sddk::wf_inner                                                |       14.74 ms →        7.35 ms  (-50.13%) |       2   →       2              |       29.47 ms →       14.70 ms  (-50.13%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       23.00 ns →       36.00 ns  (+56.52%) |       2   →       2              |       46.00 ns →       72.00 ns  (+56.52%) | 
+ │ │ │   ├ sddk::wf_inner|pw                                           |       14.60 ms →        7.21 ms  (-50.63%) |       2   →       2              |       29.21 ms →       14.42 ms  (-50.63%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       22.00 ns →       29.00 ns  (+31.82%) |       2   →       2              |       44.00 ns →       58.00 ns  (+31.82%) | 
+ │ │ ├ Eigensolver_cuda|zhegvdx                                        |      231.94 ms →      200.25 ms  (-13.66%) |       1   →       1              |      231.94 ms →      200.25 ms  (-13.66%) | 
+ │ │ └ sddk::wf_trans                                                  |        4.93 ms →        2.61 ms  (-47.17%) |       1   →       1              |        4.93 ms →        2.61 ms  (-47.17%) | 
+ │ │   └ sddk::wf_trans|pw                                             |        4.93 ms →        2.60 ms  (-47.22%) |       1   →       1              |        4.93 ms →        2.60 ms  (-47.22%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      600.00 ns →      380.00 ns  (-36.67%) |       1   →       1              |      600.00 ns →      380.00 ns  (-36.67%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |       61.94 s  →       62.62 s    (+1.10%) |       1   →       1              |       61.94 s  →       62.62 s    (+1.10%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.44 ms →        2.44 ms   (-0.03%) |      19   →      19              |       46.40 ms →       46.38 ms   (-0.03%) | 
! │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.24 s  →        2.97 s    (-8.42%) |      19   →      21    (+10.53%) |       61.63 s  →       62.38 s    (+1.22%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        5.00 ms →        4.99 ms   (-0.20%) |      19   →      21    (+10.53%) |       94.96 ms →      104.75 ms  (+10.31%) | 
! │ │ │ ├ sirius::Local_operator                                        |        4.34 ms →        4.32 ms   (-0.61%) |      19   →      21    (+10.53%) |       82.53 ms →       90.66 ms   (+9.85%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function                            |      553.17 μs →      558.65 μs   (+0.99%) |      19   →      21    (+10.53%) |       10.51 ms →       11.73 ms  (+11.62%) | 
! │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.71 ms →        2.62 ms   (-3.17%) |      19   →      21    (+10.53%) |       51.46 ms →       55.08 ms   (+7.02%) | 
- │ │ │ ├ sirius::Non_local_operator                                    |      186.46 μs →      192.22 μs   (+3.09%) |      38   →      42    (+10.53%) |        7.09 ms →        8.07 ms  (+13.94%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |      109.55 μs →      119.82 μs   (+9.37%) |      19   →      21    (+10.53%) |        2.08 ms →        2.52 ms  (+20.89%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       90.37 μs →       90.41 μs   (+0.04%) |      19   →      21    (+10.53%) |        1.72 ms →        1.90 ms  (+10.57%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.02 s  →        1.75 s   (-13.43%) |      19   →      21    (+10.53%) |       38.41 s  →       36.75 s    (-4.32%) | 
+ │ │ │ ├ sirius::Hamiltonian_k                                         |      268.62 μs →      226.66 μs  (-15.62%) |      19   →      21    (+10.53%) |        5.10 ms →        4.76 ms   (-6.74%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      259.92 μs →      216.41 μs  (-16.74%) |      19   →      21    (+10.53%) |        4.94 ms →        4.54 ms   (-7.97%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        6.46 μs →        6.68 μs   (+3.30%) |      19   →      21    (+10.53%) |      122.79 μs →      140.19 μs  (+14.18%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.96 s  →        1.61 s   (-17.81%) |      19   →      21    (+10.53%) |       37.18 s  →       33.77 s    (-9.16%) | 
- │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       71.08 ms →       71.81 ms   (+1.03%) |      19   →      21    (+10.53%) |        1.35 s  →        1.51 s   (+11.67%) | 
! │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.96 ms →        7.19 ms   (-9.63%) |     114   →     126    (+10.53%) |      907.16 ms →      906.12 ms   (-0.11%) | 
- │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       16.63 ms →       18.87 ms  (+13.51%) |      19   →      21    (+10.53%) |      315.91 ms →      396.35 ms  (+25.46%) | 
- │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      456.41 μs →      461.78 μs   (+1.18%) |      19   →      21    (+10.53%) |        8.67 ms →        9.70 ms  (+11.83%) | 
- │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        7.42 ms →        8.65 ms  (+16.53%) |      38   →      42    (+10.53%) |      282.09 ms →      363.32 ms  (+28.80%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.86 s  →        1.51 s   (-18.96%) |      19   →      21    (+10.53%) |       35.35 s  →       31.66 s   (-10.43%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       44.74 ms →       62.86 ms  (+40.50%) |     356   →     303    (-14.89%) |       15.93 s  →       19.05 s   (+19.58%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       27.22 ms →       35.64 ms  (+30.90%) |     356   →     303    (-14.89%) |        9.69 s  →       10.80 s   (+11.41%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.32 μs →        1.94 μs  (-16.38%) |     356   →     303    (-14.89%) |      826.96 μs →      588.55 μs  (-28.83%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.97 μs →        1.66 μs  (-15.69%) |     356   →     303    (-14.89%) |      702.96 μs →      504.42 μs  (-28.24%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      505.72 ns →      382.04 ns  (-24.46%) |     356   →     303    (-14.89%) |      180.04 μs →      115.76 μs  (-35.70%) | 
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      700.40 ns →      477.74 ns  (-31.79%) |     356   →     303    (-14.89%) |      249.34 μs →      144.76 μs  (-41.95%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.69 ms →        3.05 ms  (+13.49%) |     356   →     303    (-14.89%) |      957.96 ms →      925.36 ms   (-3.40%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.10 ms →        3.64 ms  (+17.29%) |     356   →     303    (-14.89%) |        1.11 s  →        1.10 s    (-0.17%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        5.85 ms →       10.26 ms  (+75.28%) |     712   →     606    (-14.89%) |        4.17 s  →        6.22 s   (+49.19%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |        5.64 ms →        7.77 ms  (+37.80%) |     356   →     303    (-14.89%) |        2.01 s  →        2.35 s   (+17.28%) | 
- │ │ │ │   │ ├ sddk::wf_inner                                          |      881.55 μs →        1.28 ms  (+44.84%) |     693   →     585    (-15.58%) |      610.91 ms →      746.97 ms  (+22.27%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       51.47 ns →       51.40 ns   (-0.13%) |     693   →     585    (-15.58%) |       35.67 μs →       30.07 μs  (-15.70%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |      721.26 μs →        1.11 ms  (+54.22%) |     693   →     585    (-15.58%) |      499.83 ms →      650.72 ms  (+30.19%) | 
+ │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       44.72 ns →       38.26 ns  (-14.45%) |     693   →     585    (-15.58%) |       30.99 μs →       22.38 μs  (-27.78%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      146.96 μs →      168.40 μs  (+14.58%) |     356   →     303    (-14.89%) |       52.32 ms →       51.02 ms   (-2.47%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        1.75 ms →        2.43 ms  (+38.38%) |     356   →     303    (-14.89%) |      624.17 ms →      735.12 ms  (+17.77%) | 
- │ │ │ │   │ └ sddk::wf_trans                                          |        2.13 ms →        2.91 ms  (+36.38%) |     337   →     282    (-16.32%) |      717.93 ms →      819.33 ms  (+14.12%) | 
- │ │ │ │   │   └ sddk::wf_trans|pw                                     |      709.28 μs →      967.73 μs  (+36.44%) |    1.01 K →     846    (-16.32%) |      717.08 ms →      818.70 ms  (+14.17%) | 
- │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.26 ms →        1.59 ms  (+26.16%) |     356   →     303    (-14.89%) |      447.38 ms →      480.37 ms   (+7.38%) | 
- │ │ │ │   │ └ sddk::wf_inner                                          |        1.19 ms →        1.53 ms  (+29.36%) |     356   →     303    (-14.89%) |      422.23 ms →      464.87 ms  (+10.10%) | 
- │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       41.17 ns →       58.17 ns  (+41.30%) |     356   →     303    (-14.89%) |       14.65 μs →       17.63 μs  (+20.27%) | 
- │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        1.03 ms →        1.37 ms  (+33.56%) |     356   →     303    (-14.89%) |      364.94 ms →      414.84 ms  (+13.67%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       38.26 ns →       44.27 ns  (+15.70%) |     356   →     303    (-14.89%) |       13.62 μs →       13.41 μs   (-1.53%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       44.42 ms →       28.07 ms  (-36.81%) |     356   →     303    (-14.89%) |       15.81 s  →        8.51 s   (-46.21%) | 
- │ │ │ │   ├ sirius::residuals                                         |        2.32 ms →        2.91 ms  (+25.18%) |     340   →     292    (-14.12%) |      790.13 ms →      849.44 ms   (+7.51%) | 
+ │ │ │ │   │ ├ sddk::wf_trans                                          |        1.25 ms →        1.32 ms   (+5.31%) |     337   →     282    (-16.32%) |      422.75 ms →      372.54 ms  (-11.88%) | 
+ │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      625.77 μs →      659.19 μs   (+5.34%) |     674   →     564    (-16.32%) |      421.77 ms →      371.78 ms  (-11.85%) | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      985.82 μs →        1.54 ms  (+56.40%) |     337   →     282    (-16.32%) |      332.22 ms →      434.80 ms  (+30.88%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        6.51 ms →        5.29 ms  (-18.77%) |      54   →      79    (+46.30%) |      351.64 ms →      417.87 ms  (+18.84%) | 
- │ │ │ │     └ sddk::wf_trans                                          |        3.90 ms →        3.00 ms  (-23.10%) |      89   →     137    (+53.93%) |      347.18 ms →      410.97 ms  (+18.37%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |        2.80 ms →        2.11 ms  (-24.74%) |     124   →     195    (+57.26%) |      347.01 ms →      410.71 ms  (+18.36%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      320.26 ns →      573.90 ns  (+79.20%) |      19   →      21    (+10.53%) |        6.09 μs →       12.05 μs  (+98.06%) | 
! │ │ │ └ sirius::K_point_set::sync_band_energies                       |       20.88 μs →       19.85 μs   (-4.95%) |      19   →      21    (+10.53%) |      396.79 μs →      416.86 μs   (+5.06%) | 
! │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.52 ms →        1.50 ms   (-0.86%) |      19   →      21    (+10.53%) |       28.80 ms →       31.55 ms   (+9.58%) | 
- │ │ ├ sirius::Density::generate                                       |      563.41 ms →      568.30 ms   (+0.87%) |      19   →      21    (+10.53%) |       10.70 s  →       11.93 s   (+11.49%) | 
! │ │ │ ├ sirius::Density::generate_valence                             |      419.98 ms →      415.06 ms   (-1.17%) |      19   →      21    (+10.53%) |        7.98 s  →        8.72 s    (+9.23%) | 
! │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.35 μs →        8.16 μs   (-2.28%) |      19   →      21    (+10.53%) |      158.60 μs →      171.30 μs   (+8.01%) | 
! │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.80 μs →        7.65 μs   (-1.92%) |      19   →      21    (+10.53%) |      148.21 μs →      160.67 μs   (+8.40%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       21.33 ms →       26.90 ms  (+26.14%) |      19   →      21    (+10.53%) |      405.21 ms →      564.92 ms  (+39.41%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.86 μs →        7.83 μs   (-0.45%) |      19   →      21    (+10.53%) |      149.37 μs →      164.35 μs  (+10.03%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        3.75 ms →        3.81 ms   (+1.56%) |      19   →      21    (+10.53%) |       71.31 ms →       80.05 ms  (+12.25%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       16.53 ms →       22.02 ms  (+33.23%) |      19   →      21    (+10.53%) |      314.02 ms →      462.42 ms  (+47.26%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      870.00 ns →      513.14 ns  (-41.02%) |      19   →      21    (+10.53%) |       16.53 μs →       10.78 μs  (-34.81%) | 
! │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      124.55 ms →      118.80 ms   (-4.62%) |      19   →      21    (+10.53%) |        2.37 s  →        2.49 s    (+5.42%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.27 ms →        1.96 ms  (-13.74%) |      19   →      21    (+10.53%) |       43.09 ms →       41.08 ms   (-4.67%) | 
! │ │ │ │ └ sirius::Density::augment                                    |      245.28 ms →      224.78 ms   (-8.36%) |      19   →      21    (+10.53%) |        4.66 s  →        4.72 s    (+1.29%) | 
! │ │ │ │   └ sirius::Density::generate_rho_aug                         |      245.06 ms →      224.56 ms   (-8.37%) |      19   →      21    (+10.53%) |        4.66 s  →        4.72 s    (+1.28%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      115.91 ms →      126.20 ms   (+8.88%) |      19   →      21    (+10.53%) |        2.20 s  →        2.65 s   (+20.34%) | 
- │ │ │ │ └ sirius::symmetrize_function|fpw                             |      115.91 ms →      126.20 ms   (+8.88%) |      19   →      21    (+10.53%) |        2.20 s  →        2.65 s   (+20.34%) | 
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       32.91 ms →       43.01 ms  (+30.70%) |      19   →      21    (+10.53%) |      625.23 ms →      903.19 ms  (+44.46%) | 
- │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       69.69 ms →       69.91 ms   (+0.31%) |      19   →      21    (+10.53%) |        1.32 s  →        1.47 s   (+10.87%) | 
- │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.66 ms →       12.63 ms   (-0.18%) |      19   →      21    (+10.53%) |      240.48 ms →      265.30 ms  (+10.32%) | 
- │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.64 ms →       23.54 ms   (-0.42%) |      19   →      21    (+10.53%) |      449.22 ms →      494.41 ms  (+10.06%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        3.87 ms →        3.48 ms  (-10.03%) |      19   →      21    (+10.53%) |       73.55 ms →       73.13 ms   (-0.56%) | 
- │ │ ├ sirius::Density::mix                                            |      133.20 ms →      134.47 ms   (+0.96%) |      19   →      21    (+10.53%) |        2.53 s  →        2.82 s   (+11.59%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      868.17 μs →      377.18 μs  (-56.55%) |      19   →      21    (+10.53%) |       16.50 ms →        7.92 ms  (-51.98%) | 
! │ │ │ ├ sirius::Periodic_function|inner                               |        4.96 ms →        4.76 ms   (-4.00%) |     229   →     259    (+13.10%) |        1.14 s  →        1.23 s    (+8.58%) | 
! │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.82 ms →        4.62 ms   (-4.16%) |     229   →     259    (+13.10%) |        1.10 s  →        1.20 s    (+8.39%) | 
! │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.82 ms →        4.62 ms   (-4.16%) |     229   →     259    (+13.10%) |        1.10 s  →        1.20 s    (+8.39%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        6.99 ms →        4.56 ms  (-34.80%) |      19   →      21    (+10.53%) |      132.89 ms →       95.77 ms  (-27.93%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        6.24 ms →        3.88 ms  (-37.90%) |      19   →      21    (+10.53%) |      118.62 ms →       81.42 ms  (-31.37%) | 
! │ │ ├ sirius::Potential::generate                                     |      365.74 ms →      358.59 ms   (-1.95%) |      19   →      21    (+10.53%) |        6.95 s  →        7.53 s    (+8.37%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |       45.17 ms →       38.28 ms  (-15.27%) |      19   →      21    (+10.53%) |      858.28 ms →      803.79 ms   (-6.35%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.89 ms →        6.88 ms (+138.35%) |      19   →      21    (+10.53%) |       54.87 ms →      144.55 ms (+163.44%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |        5.45 ms →        5.87 ms   (+7.78%) |      19   →      21    (+10.53%) |      103.52 ms →      123.31 ms  (+19.12%) | 
! │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.67 ms →        4.63 ms   (-0.78%) |      19   →      21    (+10.53%) |       88.75 ms →       97.33 ms   (+9.66%) | 
! │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.67 ms →        4.63 ms   (-0.78%) |      19   →      21    (+10.53%) |       88.74 ms →       97.31 ms   (+9.66%) | 
! │ │ │ ├ sirius::Periodic_function::add                                |      817.15 μs →      768.22 μs   (-5.99%) |      38   →      42    (+10.53%) |       31.05 ms →       32.27 ms   (+3.91%) | 
- │ │ │ ├ sirius::Potential::xc                                         |       44.68 ms →       44.58 ms   (-0.22%) |      19   →      21    (+10.53%) |      848.83 ms →      936.10 ms  (+10.28%) | 
- │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       43.50 ms →       43.40 ms   (-0.24%) |      19   →      21    (+10.53%) |      826.53 ms →      911.36 ms  (+10.26%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function                          |      678.83 μs →      687.99 μs   (+1.35%) |      38   →      42    (+10.53%) |       25.80 ms →       28.90 ms  (+12.02%) | 
! │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.28 ms →        4.04 ms   (-5.62%) |      19   →      21    (+10.53%) |       81.25 ms →       84.76 ms   (+4.31%) | 
! │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.93 ms →        3.85 ms   (-2.00%) |      19   →      21    (+10.53%) |       74.58 ms →       80.78 ms   (+8.32%) | 
- │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.89 ms →      268.95 ms   (+0.02%) |      19   →      21    (+10.53%) |        5.11 s  →        5.65 s   (+10.55%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      304.11 ns →      249.05 ns  (-18.10%) |      19   →      21    (+10.53%) |        5.78 μs →        5.23 μs   (-9.48%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |       96.07 ms →       95.87 ms   (-0.21%) |      19   →      21    (+10.53%) |        1.83 s  →        2.01 s   (+10.29%) | 
- │ │ │ └ sirius::symmetrize_function|fpw                               |       96.07 ms →       95.87 ms   (-0.21%) |      19   →      21    (+10.53%) |        1.83 s  →        2.01 s   (+10.29%) | 
- │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.33 ms →       13.30 ms   (-0.27%) |      19   →      21    (+10.53%) |      253.34 ms →      279.25 ms  (+10.23%) | 
- │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       69.52 ms →       69.34 ms   (-0.26%) |      19   →      21    (+10.53%) |        1.32 s  →        1.46 s   (+10.24%) | 
- │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.59 ms →       12.59 ms   (+0.07%) |      19   →      21    (+10.53%) |      239.13 ms →      264.48 ms  (+10.60%) | 
! │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.86 ms →        3.73 ms   (-3.51%) |      19   →      21    (+10.53%) |       73.36 ms →       78.23 ms   (+6.64%) | 
- │ │ ├ sirius::Periodic_function|inner                                 |        4.74 ms →        4.79 ms   (+1.22%) |     133   →     147    (+10.53%) |      629.90 ms →      704.66 ms  (+11.87%) | 
- │ │ │ └ sirius::Periodic_function|inner_local                         |        4.57 ms →        4.56 ms   (-0.09%) |     133   →     147    (+10.53%) |      607.44 ms →      670.80 ms  (+10.43%) | 
- │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.57 ms →        4.56 ms   (-0.08%) |     133   →     147    (+10.53%) |      607.35 ms →      670.72 ms  (+10.43%) | 
! │ │ ├ sirius::Smooth_periodic_function|inner                          |        5.05 ms →        4.79 ms   (-5.14%) |      57   →      63    (+10.53%) |      288.07 ms →      302.04 ms   (+4.85%) | 
! │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.93 ms →        4.74 ms   (-3.94%) |      57   →      63    (+10.53%) |      281.14 ms →      298.49 ms   (+6.17%) | 
- │ │ ├ sirius::Periodic_function::integrate                            |        4.52 ms →        4.56 ms   (+0.76%) |      19   →      21    (+10.53%) |       85.93 ms →       95.69 ms  (+11.36%) | 
! │ │ └ sirius::Density::get_magnetisation                              |       78.53 μs →       76.72 μs   (-2.31%) |      19   →      21    (+10.53%) |        1.49 ms →        1.61 ms   (+7.98%) | 
! │ │   └ sirius::Density::compute_atomic_mag_mom                       |       73.73 μs →       71.32 μs   (-3.27%) |      19   →      21    (+10.53%) |        1.40 ms →        1.50 ms   (+6.91%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.61 ms →        5.15 ms   (-8.22%) |       2   →       2              |       11.23 ms →       10.31 ms   (-8.22%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.59 ms →        4.56 ms   (-0.60%) |       6   →       6              |       27.51 ms →       27.35 ms   (-0.60%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.58 ms →        4.55 ms   (-0.62%) |       6   →       6              |       27.49 ms →       27.32 ms   (-0.62%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.58 ms →        4.55 ms   (-0.58%) |       6   →       6              |       27.48 ms →       27.32 ms   (-0.58%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.93 ms →        4.91 ms   (-0.43%) |       3   →       3              |       14.79 ms →       14.73 ms   (-0.43%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.92 ms →        4.90 ms   (-0.40%) |       3   →       3              |       14.77 ms →       14.71 ms   (-0.40%) | 
  ├ sirius::Periodic_function|inner                                     |        4.69 ms →        4.54 ms   (-3.17%) |       2   →       2              |        9.38 ms →        9.08 ms   (-3.17%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.53 ms →        4.54 ms   (+0.08%) |       2   →       2              |        9.07 ms →        9.07 ms   (+0.08%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.53 ms →        4.54 ms   (+0.08%) |       2   →       2              |        9.07 ms →        9.07 ms   (+0.08%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.97 ms →        4.72 ms   (-4.98%) |       1   →       1              |        4.97 ms →        4.72 ms   (-4.98%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.95 ms →        4.72 ms   (-4.75%) |       1   →       1              |        4.95 ms →        4.72 ms   (-4.75%) | 
+ └ sirius::finalize                                                    |      434.75 ms →      140.56 ms  (-67.67%) |       1   →       1              |      434.75 ms →      140.56 ms  (-67.67%) | 
  ====================================================================================================================================================================================================
```
