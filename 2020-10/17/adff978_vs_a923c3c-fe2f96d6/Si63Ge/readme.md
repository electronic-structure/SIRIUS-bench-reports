# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |       72.03 s  →       72.37 s    (+0.47%) |       1   →       1              |       72.03 s  →       72.37 s    (+0.47%) | 
  ├ sirius::initialize                                                  |        2.95 s  →        2.95 s    (+0.09%) |       1   →       1              |        2.95 s  →        2.95 s    (+0.09%) | 
  ├ sirius::Simulation_context::initialize                              |        3.57 s  →        3.82 s    (+6.83%) |       1   →       1              |        3.57 s  →        3.82 s    (+6.83%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       37.49 ms →       32.87 ms  (-12.33%) |       1   →       1              |       37.49 ms →       32.87 ms  (-12.33%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      125.09 ms →      164.91 ms  (+31.84%) |       1   →       1              |      125.09 ms →      164.91 ms  (+31.84%) | 
- │ │ ├ sirius::Atom_type::init                                         |       52.90 ms →       73.64 ms  (+39.19%) |       2   →       2              |      105.81 ms →      147.28 ms  (+39.19%) | 
  │ │ └ sirius::Unit_cell::update                                       |       19.18 ms →       17.53 ms   (-8.60%) |       1   →       1              |       19.18 ms →       17.53 ms   (-8.60%) | 
+ │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.97 ms →        3.58 ms  (-27.93%) |       1   →       1              |        4.97 ms →        3.58 ms  (-27.93%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       14.13 ms →       13.88 ms   (-1.74%) |       1   →       1              |       14.13 ms →       13.88 ms   (-1.74%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       14.06 ms →       13.82 ms   (-1.71%) |       1   →       1              |       14.06 ms →       13.82 ms   (-1.71%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.75 ms →        2.75 ms   (-0.01%) |       1   →       1              |        2.75 ms →        2.75 ms   (-0.01%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      541.36 μs →      496.47 μs   (-8.29%) |       1   →       1              |      541.36 μs →      496.47 μs   (-8.29%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       18.17 μs →       16.73 μs   (-7.93%) |       1   →       1              |       18.17 μs →       16.73 μs   (-7.93%) | 
  │ └ sirius::Simulation_context::update                                |        3.32 s  →        3.51 s    (+6.00%) |       1   →       1              |        3.32 s  →        3.51 s    (+6.00%) | 
  │   ├ sirius::Unit_cell::update                                       |        6.79 ms →        6.83 ms   (+0.56%) |       1   →       1              |        6.79 ms →        6.83 ms   (+0.56%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.42 ms →        3.43 ms   (+0.27%) |       1   →       1              |        3.42 ms →        3.43 ms   (+0.27%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.33 ms →        3.35 ms   (+0.39%) |       1   →       1              |        3.33 ms →        3.35 ms   (+0.39%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.27 ms →        3.28 ms   (+0.35%) |       1   →       1              |        3.27 ms →        3.28 ms   (+0.35%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.72 ms →        2.73 ms   (+0.72%) |       1   →       1              |        2.72 ms →        2.73 ms   (+0.72%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      508.06 μs →      503.61 μs   (-0.88%) |       1   →       1              |      508.06 μs →      503.61 μs   (-0.88%) | 
+ │   │     └ sirius::Unit_cell_symmetry|mag                            |       18.95 μs →       14.25 μs  (-24.81%) |       1   →       1              |       18.95 μs →       14.25 μs  (-24.81%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      212.62 ms →      213.16 ms   (+0.25%) |       2   →       2              |      425.25 ms →      426.33 ms   (+0.25%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.24 ms →       15.28 ms   (+0.29%) |       2   →       2              |       30.48 ms →       30.56 ms   (+0.29%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.26 ms →       13.26 ms   (+0.01%) |       1   →       1              |       13.26 ms →       13.26 ms   (+0.01%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.20 ms →       56.31 ms   (+0.20%) |       2   →       2              |      112.40 ms →      112.62 ms   (+0.20%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.10 ms →       45.24 ms   (+0.32%) |       2   →       2              |       90.20 ms →       90.49 ms   (+0.32%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.15 ms →       60.36 ms   (+0.35%) |       4   →       4              |      240.62 ms →      241.46 ms   (+0.35%) | 
  │   ├ sddk::Gvec::init                                                |       94.59 ms →       93.65 ms   (-1.00%) |       2   →       2              |      189.18 ms →      187.30 ms   (-1.00%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       70.55 ms →       70.29 ms   (-0.37%) |       2   →       2              |      141.10 ms →      140.58 ms   (-0.37%) | 
  │   ├ sddk::Gvec_shells                                               |      100.55 ms →       93.79 ms   (-6.72%) |       1   →       1              |      100.55 ms →       93.79 ms   (-6.72%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.95 ms →        1.94 ms   (-0.10%) |       1   →       1              |        1.95 ms →        1.94 ms   (-0.10%) | 
- │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      513.66 ms →      606.53 ms  (+18.08%) |       2   →       2              |        1.03 s  →        1.21 s   (+18.08%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |      149.20 ms →      140.80 ms   (-5.63%) |       1   →       1              |      149.20 ms →      140.80 ms   (-5.63%) | 
- │ ├ sirius::K_point::K_point                                          |        1.90 μs →        2.66 μs  (+39.63%) |       4   →       4              |        7.62 μs →       10.63 μs  (+39.63%) | 
  │ └ sirius::K_point_set::initialize                                   |      149.12 ms →      140.72 ms   (-5.63%) |       1   →       1              |      149.12 ms →      140.72 ms   (-5.63%) | 
  │   └ sirius::K_point::initialize                                     |       28.36 ms →       28.45 ms   (+0.31%) |       1   →       1              |       28.36 ms →       28.45 ms   (+0.31%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       11.33 ms →       10.96 ms   (-3.22%) |       1   →       1              |       11.33 ms →       10.96 ms   (-3.22%) | 
  │     │ └ sddk::Gvec::init                                            |        5.12 ms →        4.99 ms   (-2.46%) |       1   →       1              |        5.12 ms →        4.99 ms   (-2.46%) | 
- │     ├ sddk::matrix_storage::matrix_storage                          |        7.92 μs →       10.95 μs  (+38.31%) |       1   →       1              |        7.92 μs →       10.95 μs  (+38.31%) | 
  │     └ sirius::K_point::update                                       |       14.14 ms →       14.64 ms   (+3.57%) |       1   →       1              |       14.14 ms →       14.64 ms   (+3.57%) | 
  │       └ sirius::Beta_projectors                                     |       10.17 ms →       10.63 ms   (+4.60%) |       1   →       1              |       10.17 ms →       10.63 ms   (+4.60%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.25 ms →        8.76 ms   (+6.18%) |       1   →       1              |        8.25 ms →        8.76 ms   (+6.18%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.56 ms →        2.62 ms   (+2.29%) |       2   →       2              |        5.12 ms →        5.24 ms   (+2.29%) | 
  ├ sirius::Potential                                                   |       51.57 ms →       50.45 ms   (-2.16%) |       1   →       1              |       51.57 ms →       50.45 ms   (-2.16%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.95 ms →        2.93 ms   (-0.46%) |       6   →       6              |       17.67 ms →       17.59 ms   (-0.46%) | 
  │ └ sirius::Potential::update                                         |       33.35 ms →       32.24 ms   (-3.34%) |       1   →       1              |       33.35 ms →       32.24 ms   (-3.34%) | 
  │   └ sirius::Potential::generate_local_potential                     |       32.94 ms →       31.83 ms   (-3.37%) |       1   →       1              |       32.94 ms →       31.83 ms   (-3.37%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       26.23 ms →       26.71 ms   (+1.83%) |       1   →       1              |       26.23 ms →       26.71 ms   (+1.83%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        6.19 ms →        4.59 ms  (-25.83%) |       1   →       1              |        6.19 ms →        4.59 ms  (-25.83%) | 
  ├ sirius::Density                                                     |       40.96 ms →       38.47 ms   (-6.06%) |       1   →       1              |       40.96 ms →       38.47 ms   (-6.06%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.81 ms →        2.83 ms   (+0.84%) |       2   →       2              |        5.62 ms →        5.66 ms   (+0.84%) | 
  │ └ sirius::Density::update                                           |       35.20 ms →       32.67 ms   (-7.19%) |       1   →       1              |       35.20 ms →       32.67 ms   (-7.19%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       34.98 ms →       32.43 ms   (-7.29%) |       1   →       1              |       34.98 ms →       32.43 ms   (-7.29%) | 
+ │     ├ sirius::rho_core_ri_pseudo|values                             |       93.19 μs →       77.21 μs  (-17.14%) |       1   →       1              |       93.19 μs →       77.21 μs  (-17.14%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       26.10 ms →       27.10 ms   (+3.82%) |       1   →       1              |       26.10 ms →       27.10 ms   (+3.82%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        8.49 ms →        4.94 ms  (-41.77%) |       1   →       1              |        8.49 ms →        4.94 ms  (-41.77%) | 
  ├ sirius::Density::initial_density                                    |       59.46 ms →       57.04 ms   (-4.06%) |       1   →       1              |       59.46 ms →       57.04 ms   (-4.06%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       26.34 ms →       27.79 ms   (+5.52%) |       1   →       1              |       26.34 ms →       27.79 ms   (+5.52%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        7.01 ms →        5.37 ms  (-23.34%) |       2   →       2              |       14.02 ms →       10.75 ms  (-23.34%) | 
+ │ └ sirius::Periodic_function::integrate                              |        5.42 ms →        4.85 ms  (-10.58%) |       1   →       1              |        5.42 ms →        4.85 ms  (-10.58%) | 
  ├ sirius::Potential::generate                                         |      369.87 ms →      361.99 ms   (-2.13%) |       1   →       1              |      369.87 ms →      361.99 ms   (-2.13%) | 
+ │ ├ sirius::Potential::poisson                                        |       42.05 ms →       35.22 ms  (-16.25%) |       1   →       1              |       42.05 ms →       35.22 ms  (-16.25%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       10.78 ms →        3.98 ms  (-63.10%) |       1   →       1              |       10.78 ms →        3.98 ms  (-63.10%) | 
+ │ │ └ sirius::Periodic_function|inner                                 |        5.89 ms →        5.01 ms  (-14.93%) |       1   →       1              |        5.89 ms →        5.01 ms  (-14.93%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.64 ms →        4.63 ms   (-0.22%) |       1   →       1              |        4.64 ms →        4.63 ms   (-0.22%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.63 ms →        4.62 ms   (-0.15%) |       1   →       1              |        4.63 ms →        4.62 ms   (-0.15%) | 
  │ ├ sirius::Periodic_function::add                                    |      792.13 μs →      742.61 μs   (-6.25%) |       2   →       2              |        1.58 ms →        1.49 ms   (-6.25%) | 
  │ ├ sirius::Potential::xc                                             |       51.57 ms →       51.69 ms   (+0.24%) |       1   →       1              |       51.57 ms →       51.69 ms   (+0.24%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       50.41 ms →       50.51 ms   (+0.19%) |       1   →       1              |       50.41 ms →       50.51 ms   (+0.19%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.58 ms →        2.60 ms   (+0.77%) |       2   →       2              |        5.16 ms →        5.20 ms   (+0.77%) | 
- │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.03 ms →        4.67 ms  (+15.70%) |       1   →       1              |        4.03 ms →        4.67 ms  (+15.70%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.40 ms →        3.59 ms   (+5.53%) |       1   →       1              |        3.40 ms →        3.59 ms   (+5.53%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      269.88 ms →      268.56 ms   (-0.49%) |       1   →       1              |      269.88 ms →      268.56 ms   (-0.49%) | 
+ │ └ sirius::Potential::generate_PAW_effective_potential               |      283.00 ns →      224.00 ns  (-20.85%) |       1   →       1              |      283.00 ns →      224.00 ns  (-20.85%) | 
  ├ sirius::Hamiltonian0                                                |        6.27 ms →        6.34 ms   (+1.06%) |       1   →       1              |        6.27 ms →        6.34 ms   (+1.06%) | 
  │ ├ sirius::Local_operator                                            |        5.83 ms →        5.88 ms   (+0.76%) |       1   →       1              |        5.83 ms →        5.88 ms   (+0.76%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.73 ms →        2.78 ms   (+1.79%) |       1   →       1              |        2.73 ms →        2.78 ms   (+1.79%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.37 ms →        2.33 ms   (-1.43%) |       1   →       1              |        2.37 ms →        2.33 ms   (-1.43%) | 
  │ ├ sirius::Non_local_operator                                        |       74.11 μs →       71.06 μs   (-4.12%) |       2   →       2              |      148.22 μs →      142.12 μs   (-4.12%) | 
- │ ├ sirius::D_operator::initialize                                    |      124.05 μs →      143.10 μs  (+15.36%) |       1   →       1              |      124.05 μs →      143.10 μs  (+15.36%) | 
  │ └ sirius::Q_operator::initialize                                    |       99.79 μs →      100.88 μs   (+1.09%) |       1   →       1              |       99.79 μs →      100.88 μs   (+1.09%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.28 s  →        1.27 s    (-1.01%) |       1   →       1              |        1.28 s  →        1.27 s    (-1.01%) | 
+ │ ├ sirius::Hamiltonian_k                                             |       43.01 ms →       35.34 ms  (-17.83%) |       1   →       1              |       43.01 ms →       35.34 ms  (-17.83%) | 
- │ │ ├ sirius::Local_operator::prepare_k                               |      261.35 μs →      317.38 μs  (+21.44%) |       1   →       1              |      261.35 μs →      317.38 μs  (+21.44%) | 
+ │ │ └ sirius::Beta_projectors_base::prepare                           |       42.74 ms →       35.02 ms  (-18.07%) |       1   →       1              |       42.74 ms →       35.02 ms  (-18.07%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.24 s  →        1.24 s    (-0.43%) |       1   →       1              |        1.24 s  →        1.24 s    (-0.43%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       80.30 ms →       80.79 ms   (+0.62%) |       4   →       4              |      321.20 ms →      323.18 ms   (+0.62%) | 
+ │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       50.57 ms →       36.75 ms  (-27.31%) |       1   →       1              |       50.57 ms →       36.75 ms  (-27.31%) | 
+ │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        8.00 ms →        6.54 ms  (-18.22%) |       1   →       1              |        8.00 ms →        6.54 ms  (-18.22%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      315.46 ms →      317.00 ms   (+0.49%) |       1   →       1              |      315.46 ms →      317.00 ms   (+0.49%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      245.60 ms →      247.22 ms   (+0.66%) |       1   →       1              |      245.60 ms →      247.22 ms   (+0.66%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        4.01 μs →        4.15 μs   (+3.64%) |       1   →       1              |        4.01 μs →        4.15 μs   (+3.64%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.03 μs →        3.25 μs   (+7.10%) |       1   →       1              |        3.03 μs →        3.25 μs   (+7.10%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      438.00 ns →      459.00 ns   (+4.79%) |       1   →       1              |      438.00 ns →      459.00 ns   (+4.79%) | 
- │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      531.00 ns →      649.00 ns  (+22.22%) |       1   →       1              |      531.00 ns →      649.00 ns  (+22.22%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.17 ms →        3.17 ms   (-0.00%) |       1   →       1              |        3.17 ms →        3.17 ms   (-0.00%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.33 ms →       21.31 ms   (-0.07%) |       1   →       1              |       21.33 ms →       21.31 ms   (-0.07%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       22.66 ms →       22.62 ms   (-0.14%) |       2   →       2              |       45.31 ms →       45.25 ms   (-0.14%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.94 ms →       14.91 ms   (-0.19%) |       2   →       2              |       29.87 ms →       29.82 ms   (-0.19%) | 
  │ │ │ └ sddk::wf_inner                                                |       14.72 ms →       14.70 ms   (-0.19%) |       2   →       2              |       29.45 ms →       29.40 ms   (-0.19%) | 
+ │ │ │   ├ sddk::wf_inner|scale                                        |       22.00 ns →       19.00 ns  (-13.64%) |       2   →       2              |       44.00 ns →       38.00 ns  (-13.64%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       14.58 ms →       14.57 ms   (-0.05%) |       2   →       2              |       29.15 ms →       29.14 ms   (-0.05%) | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |       23.00 ns →       21.00 ns   (-8.70%) |       2   →       2              |       46.00 ns →       42.00 ns   (-8.70%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      250.25 ms →      251.23 ms   (+0.39%) |       1   →       1              |      250.25 ms →      251.23 ms   (+0.39%) | 
- │ │ └ sddk::wf_trans                                                  |        2.61 ms →        4.98 ms  (+91.17%) |       1   →       1              |        2.61 ms →        4.98 ms  (+91.17%) | 
- │ │   └ sddk::wf_trans|pw                                             |        2.60 ms →        4.98 ms  (+91.28%) |       1   →       1              |        2.60 ms →        4.98 ms  (+91.28%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      493.00 ns →      422.00 ns  (-14.40%) |       1   →       1              |      493.00 ns →      422.00 ns  (-14.40%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |       62.45 s  →       62.56 s    (+0.17%) |       1   →       1              |       62.45 s  →       62.56 s    (+0.17%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.44 ms →        2.46 ms   (+0.76%) |      19   →      19              |       46.40 ms →       46.76 ms   (+0.76%) | 
! │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.25 s  →        2.97 s    (-8.72%) |      19   →      21    (+10.53%) |       61.81 s  →       62.36 s    (+0.89%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        5.27 ms →        5.71 ms   (+8.29%) |      19   →      21    (+10.53%) |      100.17 ms →      119.90 ms  (+19.69%) | 
- │ │ │ ├ sirius::Local_operator                                        |        4.59 ms →        4.93 ms   (+7.37%) |      19   →      21    (+10.53%) |       87.27 ms →      103.57 ms  (+18.68%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function                            |      550.32 μs →      568.70 μs   (+3.34%) |      19   →      21    (+10.53%) |       10.46 ms →       11.94 ms  (+14.22%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.11 ms →        3.09 ms   (-0.40%) |      19   →      21    (+10.53%) |       59.00 ms →       64.95 ms  (+10.09%) | 
- │ │ │ ├ sirius::Non_local_operator                                    |      182.70 μs →      249.51 μs  (+36.57%) |      38   →      42    (+10.53%) |        6.94 ms →       10.48 ms  (+50.94%) | 
+ │ │ │ ├ sirius::D_operator::initialize                                |      128.86 μs →      111.54 μs  (-13.44%) |      19   →      21    (+10.53%) |        2.45 ms →        2.34 ms   (-4.33%) | 
+ │ │ │ └ sirius::Q_operator::initialize                                |      100.94 μs →       90.12 μs  (-10.71%) |      19   →      21    (+10.53%) |        1.92 ms →        1.89 ms   (-1.31%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.03 s  →        1.76 s   (-13.43%) |      19   →      21    (+10.53%) |       38.52 s  →       36.86 s    (-4.31%) | 
+ │ │ │ ├ sirius::Hamiltonian_k                                         |      235.45 μs →      196.09 μs  (-16.72%) |      19   →      21    (+10.53%) |        4.47 ms →        4.12 ms   (-7.95%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      224.85 μs →      185.84 μs  (-17.35%) |      19   →      21    (+10.53%) |        4.27 ms →        3.90 ms   (-8.65%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        7.41 μs →        7.61 μs   (+2.69%) |      19   →      21    (+10.53%) |      140.80 μs →      159.80 μs  (+13.50%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.96 s  →        1.64 s   (-16.44%) |      19   →      21    (+10.53%) |       37.21 s  →       34.37 s    (-7.64%) | 
! │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       76.46 ms →       74.72 ms   (-2.29%) |      19   →      21    (+10.53%) |        1.45 s  →        1.57 s    (+8.00%) | 
! │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.91 ms →        7.65 ms   (-3.28%) |     114   →     126    (+10.53%) |      902.23 ms →      964.48 ms   (+6.90%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       17.85 ms →       15.19 ms  (-14.94%) |      19   →      21    (+10.53%) |      339.22 ms →      318.91 ms   (-5.99%) | 
- │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      461.11 μs →      490.74 μs   (+6.43%) |      19   →      21    (+10.53%) |        8.76 ms →       10.31 ms  (+17.63%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        8.08 ms →        6.92 ms  (-14.38%) |      38   →      42    (+10.53%) |      306.95 ms →      290.47 ms   (-5.37%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.86 s  →        1.54 s   (-17.11%) |      19   →      21    (+10.53%) |       35.26 s  →       32.31 s    (-8.38%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       50.28 ms →       59.62 ms  (+18.58%) |     356   →     361     (+1.40%) |       17.90 s  →       21.52 s   (+20.24%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       28.62 ms →       36.32 ms  (+26.89%) |     356   →     361     (+1.40%) |       10.19 s  →       13.11 s   (+28.67%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.96 μs →        2.15 μs   (+9.39%) |     356   →     361     (+1.40%) |      699.39 μs →      775.82 μs  (+10.93%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.68 μs →        1.79 μs   (+7.12%) |     356   →     361     (+1.40%) |      596.52 μs →      647.94 μs   (+8.62%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      383.99 ns →      481.63 ns  (+25.43%) |     356   →     361     (+1.40%) |      136.70 μs →      173.87 μs  (+27.19%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      439.64 ns →      672.73 ns  (+53.02%) |     356   →     361     (+1.40%) |      156.51 μs →      242.86 μs  (+55.17%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.72 ms →        3.00 ms  (+10.17%) |     356   →     361     (+1.40%) |      968.13 ms →        1.08 s   (+11.72%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.25 ms →        3.25 ms   (+0.19%) |     356   →     361     (+1.40%) |        1.16 s  →        1.17 s    (+1.59%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.84 ms →        8.52 ms   (+8.67%) |     712   →     722     (+1.40%) |        5.58 s  →        6.15 s   (+10.19%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |        6.59 ms →        6.30 ms   (-4.43%) |     356   →     361     (+1.40%) |        2.35 s  →        2.27 s    (-3.09%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        1.09 ms →        1.06 ms   (-2.57%) |     693   →     701     (+1.15%) |      755.72 ms →      744.81 ms   (-1.44%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       55.27 ns →       46.29 ns  (-16.26%) |     693   →     701     (+1.15%) |       38.30 μs →       32.45 μs  (-15.29%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |      929.49 μs →      898.57 μs   (-3.33%) |     693   →     701     (+1.15%) |      644.13 ms →      629.90 ms   (-2.21%) | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       45.75 ns →       48.48 ns   (+5.96%) |     693   →     701     (+1.15%) |       31.71 μs →       33.98 μs   (+7.18%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      134.19 μs →      138.97 μs   (+3.56%) |     356   →     361     (+1.40%) |       47.77 ms →       50.17 ms   (+5.02%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        2.13 ms →        1.96 ms   (-8.02%) |     356   →     361     (+1.40%) |      757.94 ms →      706.95 ms   (-6.73%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |        2.32 ms →        2.27 ms   (-2.52%) |     337   →     340     (+0.89%) |      783.24 ms →      770.29 ms   (-1.65%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |      773.98 μs →      754.32 μs   (-2.54%) |    1.01 K →    1.02 K   (+0.89%) |      782.49 ms →      769.41 ms   (-1.67%) | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.40 ms →        1.20 ms  (-14.63%) |     356   →     361     (+1.40%) |      498.92 ms →      431.90 ms  (-13.43%) | 
+ │ │ │ │   │ └ sddk::wf_inner                                          |        1.33 ms →        1.15 ms  (-13.50%) |     356   →     361     (+1.40%) |      473.48 ms →      415.34 ms  (-12.28%) | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       40.49 ns →       41.09 ns   (+1.47%) |     356   →     361     (+1.40%) |       14.41 μs →       14.83 μs   (+2.90%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        1.17 ms →      985.61 μs  (-15.57%) |     356   →     361     (+1.40%) |      415.59 ms →      355.81 ms  (-14.38%) | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       43.13 ns →       45.35 ns   (+5.15%) |     356   →     361     (+1.40%) |       15.35 μs →       16.37 μs   (+6.63%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       37.23 ms →       18.53 ms  (-50.22%) |     356   →     361     (+1.40%) |       13.25 s  →        6.69 s   (-49.52%) | 
- │ │ │ │   ├ sirius::residuals                                         |        2.50 ms →        2.76 ms  (+10.65%) |     340   →     346     (+1.76%) |      848.55 ms →      955.47 ms  (+12.60%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |        1.35 ms →        1.37 ms   (+1.97%) |     337   →     342     (+1.48%) |      454.41 ms →      470.25 ms   (+3.49%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      672.83 μs →      686.00 μs   (+1.96%) |     674   →     684     (+1.48%) |      453.49 ms →      469.22 ms   (+3.47%) | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.06 ms →        1.30 ms  (+22.54%) |     337   →     342     (+1.48%) |      358.52 ms →      445.84 ms  (+24.35%) | 
+ │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        7.54 ms →        4.72 ms  (-37.36%) |      54   →      90    (+66.67%) |      406.94 ms →      424.84 ms   (+4.40%) | 
+ │ │ │ │     └ sddk::wf_trans                                          |        4.52 ms →        2.62 ms  (-42.14%) |      89   →     159    (+78.65%) |      402.72 ms →      416.26 ms   (+3.36%) | 
+ │ │ │ │       └ sddk::wf_trans|pw                                     |        3.25 ms →        1.82 ms  (-43.81%) |     124   →     228    (+83.87%) |      402.56 ms →      415.94 ms   (+3.32%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      408.32 ns →      559.95 ns  (+37.14%) |      19   →      21    (+10.53%) |        7.76 μs →       11.76 μs  (+51.57%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       19.31 μs →       19.55 μs   (+1.29%) |      19   →      21    (+10.53%) |      366.80 μs →      410.64 μs  (+11.95%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.52 ms →        1.54 ms   (+1.42%) |      19   →      21    (+10.53%) |       28.80 ms →       32.29 ms  (+12.10%) | 
! │ │ ├ sirius::Density::generate                                       |      569.70 ms →      564.44 ms   (-0.92%) |      19   →      21    (+10.53%) |       10.82 s  →       11.85 s    (+9.50%) | 
! │ │ │ ├ sirius::Density::generate_valence                             |      402.14 ms →      380.78 ms   (-5.31%) |      19   →      21    (+10.53%) |        7.64 s  →        8.00 s    (+4.65%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        7.98 μs →        8.27 μs   (+3.59%) |      19   →      21    (+10.53%) |      151.59 μs →      173.57 μs  (+14.50%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.46 μs →        7.69 μs   (+3.05%) |      19   →      21    (+10.53%) |      141.76 μs →      161.47 μs  (+13.90%) | 
! │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       40.97 ms →       38.53 ms   (-5.96%) |      19   →      21    (+10.53%) |      778.39 ms →      809.04 ms   (+3.94%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.59 μs →        7.97 μs   (+5.11%) |      19   →      21    (+10.53%) |      144.14 μs →      167.46 μs  (+16.18%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        6.94 ms →       22.55 ms (+225.02%) |      19   →      21    (+10.53%) |      131.82 ms →      473.55 ms (+259.24%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       32.97 ms →       14.91 ms  (-54.76%) |      19   →      21    (+10.53%) |      626.44 ms →      313.21 ms  (-50.00%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      571.05 ns →      993.24 ns  (+73.93%) |      19   →      21    (+10.53%) |       10.85 μs →       20.86 μs  (+92.24%) | 
! │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      105.18 ms →      100.79 ms   (-4.17%) |      19   →      21    (+10.53%) |        2.00 s  →        2.12 s    (+5.92%) | 
! │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.00 ms →        1.94 ms   (-2.81%) |      19   →      21    (+10.53%) |       37.94 ms →       40.75 ms   (+7.42%) | 
! │ │ │ │ └ sirius::Density::augment                                    |      208.42 ms →      194.86 ms   (-6.51%) |      19   →      21    (+10.53%) |        3.96 s  →        4.09 s    (+3.33%) | 
! │ │ │ │   └ sirius::Density::generate_rho_aug                         |      208.20 ms →      194.63 ms   (-6.52%) |      19   →      21    (+10.53%) |        3.96 s  →        4.09 s    (+3.32%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      140.52 ms →      155.65 ms  (+10.77%) |      19   →      21    (+10.53%) |        2.67 s  →        3.27 s   (+22.42%) | 
- │ │ │ │ └ sirius::symmetrize_function|fpw                             |      140.52 ms →      155.65 ms  (+10.77%) |      19   →      21    (+10.53%) |        2.67 s  →        3.27 s   (+22.43%) | 
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       56.74 ms →       71.61 ms  (+26.20%) |      19   →      21    (+10.53%) |        1.08 s  →        1.50 s   (+39.48%) | 
- │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       70.21 ms →       70.77 ms   (+0.79%) |      19   →      21    (+10.53%) |        1.33 s  →        1.49 s   (+11.40%) | 
! │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.91 ms →       12.61 ms   (-2.30%) |      19   →      21    (+10.53%) |      245.28 ms →      264.86 ms   (+7.99%) | 
- │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.61 ms →       23.61 ms   (-0.01%) |      19   →      21    (+10.53%) |      448.62 ms →      495.81 ms  (+10.52%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        3.42 ms →        4.40 ms  (+28.46%) |      19   →      21    (+10.53%) |       65.02 ms →       92.32 ms  (+41.98%) | 
- │ │ ├ sirius::Density::mix                                            |      133.53 ms →      133.96 ms   (+0.32%) |      19   →      21    (+10.53%) |        2.54 s  →        2.81 s   (+10.88%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      667.83 μs →      558.71 μs  (-16.34%) |      19   →      21    (+10.53%) |       12.69 ms →       11.73 ms   (-7.53%) | 
! │ │ │ ├ sirius::Periodic_function|inner                               |        4.92 ms →        4.76 ms   (-3.35%) |     229   →     259    (+13.10%) |        1.13 s  →        1.23 s    (+9.31%) | 
! │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.81 ms →        4.63 ms   (-3.86%) |     229   →     259    (+13.10%) |        1.10 s  →        1.20 s    (+8.73%) | 
! │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.81 ms →        4.63 ms   (-3.87%) |     229   →     259    (+13.10%) |        1.10 s  →        1.20 s    (+8.72%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        6.00 ms →        6.52 ms   (+8.58%) |      19   →      21    (+10.53%) |      114.07 ms →      136.90 ms  (+20.01%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.31 ms →        5.72 ms   (+7.83%) |      19   →      21    (+10.53%) |      100.82 ms →      120.16 ms  (+19.18%) | 
! │ │ ├ sirius::Potential::generate                                     |      363.27 ms →      356.67 ms   (-1.82%) |      19   →      21    (+10.53%) |        6.90 s  →        7.49 s    (+8.52%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |       42.80 ms →       35.97 ms  (-15.95%) |      19   →      21    (+10.53%) |      813.13 ms →      755.40 ms   (-7.10%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       11.72 ms →        4.46 ms  (-61.95%) |      19   →      21    (+10.53%) |      222.65 ms →       93.63 ms  (-57.95%) | 
! │ │ │ │ └ sirius::Periodic_function|inner                             |        5.71 ms →        5.25 ms   (-8.06%) |      19   →      21    (+10.53%) |      108.54 ms →      110.30 ms   (+1.62%) | 
- │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.63 ms →        4.64 ms   (+0.14%) |      19   →      21    (+10.53%) |       87.96 ms →       97.35 ms  (+10.68%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.63 ms →        4.63 ms   (+0.13%) |      19   →      21    (+10.53%) |       87.95 ms →       97.33 ms  (+10.67%) | 
! │ │ │ ├ sirius::Periodic_function::add                                |      793.13 μs →      756.32 μs   (-4.64%) |      38   →      42    (+10.53%) |       30.14 ms →       31.77 ms   (+5.40%) | 
- │ │ │ ├ sirius::Potential::xc                                         |       44.54 ms →       45.72 ms   (+2.64%) |      19   →      21    (+10.53%) |      846.25 ms →      960.05 ms  (+13.45%) | 
- │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       43.37 ms →       44.54 ms   (+2.69%) |      19   →      21    (+10.53%) |      824.04 ms →      935.26 ms  (+13.50%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function                          |      683.83 μs →      692.10 μs   (+1.21%) |      38   →      42    (+10.53%) |       25.99 ms →       29.07 ms  (+11.86%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.11 ms →        4.91 ms  (+19.56%) |      19   →      21    (+10.53%) |       78.00 ms →      103.08 ms  (+32.15%) | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.57 ms →        3.59 ms   (+0.47%) |      19   →      21    (+10.53%) |       67.87 ms →       75.37 ms  (+11.04%) | 
- │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      269.37 ms →      268.48 ms   (-0.33%) |      19   →      21    (+10.53%) |        5.12 s  →        5.64 s   (+10.16%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      345.37 ns →      222.14 ns  (-35.68%) |      19   →      21    (+10.53%) |        6.56 μs →        4.67 μs  (-28.91%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |       96.56 ms →       96.63 ms   (+0.08%) |      19   →      21    (+10.53%) |        1.83 s  →        2.03 s   (+10.61%) | 
- │ │ │ └ sirius::symmetrize_function|fpw                               |       96.56 ms →       96.63 ms   (+0.08%) |      19   →      21    (+10.53%) |        1.83 s  →        2.03 s   (+10.61%) | 
- │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.29 ms →       13.30 ms   (+0.02%) |      19   →      21    (+10.53%) |      252.57 ms →      279.20 ms  (+10.55%) | 
- │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       69.84 ms →       70.05 ms   (+0.31%) |      19   →      21    (+10.53%) |        1.33 s  →        1.47 s   (+10.87%) | 
! │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.80 ms →       12.65 ms   (-1.16%) |      19   →      21    (+10.53%) |      243.22 ms →      265.71 ms   (+9.25%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.60 ms →        4.45 ms  (+23.81%) |      19   →      21    (+10.53%) |       68.31 ms →       93.48 ms  (+36.85%) | 
! │ │ ├ sirius::Periodic_function|inner                                 |        4.69 ms →        4.58 ms   (-2.50%) |     133   →     147    (+10.53%) |      624.12 ms →      672.54 ms   (+7.76%) | 
- │ │ │ └ sirius::Periodic_function|inner_local                         |        4.56 ms →        4.55 ms   (-0.27%) |     133   →     147    (+10.53%) |      606.84 ms →      668.93 ms  (+10.23%) | 
- │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.56 ms →        4.55 ms   (-0.27%) |     133   →     147    (+10.53%) |      606.75 ms →      668.84 ms  (+10.23%) | 
! │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.94 ms →        4.74 ms   (-4.05%) |      57   →      63    (+10.53%) |      281.40 ms →      298.42 ms   (+6.05%) | 
! │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.93 ms →        4.72 ms   (-4.26%) |      57   →      63    (+10.53%) |      280.85 ms →      297.20 ms   (+5.82%) | 
- │ │ ├ sirius::Periodic_function::integrate                            |        4.53 ms →        4.54 ms   (+0.30%) |      19   →      21    (+10.53%) |       86.03 ms →       95.37 ms  (+10.86%) | 
! │ │ └ sirius::Density::get_magnetisation                              |       77.37 μs →       76.74 μs   (-0.80%) |      19   →      21    (+10.53%) |        1.47 ms →        1.61 ms   (+9.64%) | 
! │ │   └ sirius::Density::compute_atomic_mag_mom                       |       72.53 μs →       71.87 μs   (-0.91%) |      19   →      21    (+10.53%) |        1.38 ms →        1.51 ms   (+9.52%) | 
- │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.18 ms →        5.71 ms  (+10.40%) |       2   →       2              |       10.35 ms →       11.43 ms  (+10.40%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.81 ms →        4.62 ms   (-4.07%) |       6   →       6              |       28.88 ms →       27.70 ms   (-4.07%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.81 ms →        4.52 ms   (-5.95%) |       6   →       6              |       28.84 ms →       27.13 ms   (-5.95%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.80 ms →        4.52 ms   (-5.92%) |       6   →       6              |       28.83 ms →       27.12 ms   (-5.92%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        5.18 ms →        4.76 ms   (-8.07%) |       3   →       3              |       15.53 ms →       14.28 ms   (-8.07%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        5.17 ms →        4.75 ms   (-8.21%) |       3   →       3              |       15.52 ms →       14.24 ms   (-8.21%) | 
  ├ sirius::Periodic_function|inner                                     |        4.77 ms →        4.85 ms   (+1.54%) |       2   →       2              |        9.55 ms →        9.70 ms   (+1.54%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.77 ms →        4.85 ms   (+1.55%) |       2   →       2              |        9.54 ms →        9.69 ms   (+1.55%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.77 ms →        4.84 ms   (+1.55%) |       2   →       2              |        9.54 ms →        9.69 ms   (+1.55%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        5.16 ms →        4.71 ms   (-8.88%) |       1   →       1              |        5.16 ms →        4.71 ms   (-8.88%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        5.16 ms →        4.70 ms   (-8.92%) |       1   →       1              |        5.16 ms →        4.70 ms   (-8.92%) | 
  └ sirius::finalize                                                    |      146.34 ms →      158.10 ms   (+8.03%) |       1   →       1              |      146.34 ms →      158.10 ms   (+8.03%) | 
  ====================================================================================================================================================================================================
```
