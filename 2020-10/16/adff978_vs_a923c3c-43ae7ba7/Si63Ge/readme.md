# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |       71.50 s  →       72.35 s    (+1.19%) |       1   →       1              |       71.50 s  →       72.35 s    (+1.19%) | 
- ├ sirius::initialize                                                  |        2.46 s  →        2.96 s   (+20.15%) |       1   →       1              |        2.46 s  →        2.96 s   (+20.15%) | 
  ├ sirius::Simulation_context::initialize                              |        3.88 s  →        3.65 s    (-5.91%) |       1   →       1              |        3.88 s  →        3.65 s    (-5.91%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |      143.07 ms →      565.25 μs  (-99.60%) |       1   →       1              |      143.07 ms →      565.25 μs  (-99.60%) | 
  │ ├ sirius::Unit_cell::initialize                                     |      165.75 ms →      172.36 ms   (+3.98%) |       1   →       1              |      165.75 ms →      172.36 ms   (+3.98%) | 
  │ │ ├ sirius::Atom_type::init                                         |       74.26 ms →       76.78 ms   (+3.39%) |       2   →       2              |      148.53 ms →      153.56 ms   (+3.39%) | 
  │ │ └ sirius::Unit_cell::update                                       |       17.13 ms →       18.69 ms   (+9.12%) |       1   →       1              |       17.13 ms →       18.69 ms   (+9.12%) | 
- │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.93 ms →        5.03 ms  (+27.96%) |       1   →       1              |        3.93 ms →        5.03 ms  (+27.96%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       13.16 ms →       13.59 ms   (+3.29%) |       1   →       1              |       13.16 ms →       13.59 ms   (+3.29%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       13.09 ms →       13.52 ms   (+3.31%) |       1   →       1              |       13.09 ms →       13.52 ms   (+3.31%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.74 ms →        2.75 ms   (+0.29%) |       1   →       1              |        2.74 ms →        2.75 ms   (+0.29%) | 
+ │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      599.04 μs →      516.57 μs  (-13.77%) |       1   →       1              |      599.04 μs →      516.57 μs  (-13.77%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       15.68 μs →       16.52 μs   (+5.36%) |       1   →       1              |       15.68 μs →       16.52 μs   (+5.36%) | 
  │ └ sirius::Simulation_context::update                                |        3.37 s  →        3.37 s    (+0.04%) |       1   →       1              |        3.37 s  →        3.37 s    (+0.04%) | 
  │   ├ sirius::Unit_cell::update                                       |        6.98 ms →        7.02 ms   (+0.55%) |       1   →       1              |        6.98 ms →        7.02 ms   (+0.55%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.65 ms →        3.65 ms   (-0.01%) |       1   →       1              |        3.65 ms →        3.65 ms   (-0.01%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.29 ms →        3.30 ms   (+0.11%) |       1   →       1              |        3.29 ms →        3.30 ms   (+0.11%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.25 ms →        3.23 ms   (-0.61%) |       1   →       1              |        3.25 ms →        3.23 ms   (-0.61%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.70 ms →        2.70 ms   (-0.12%) |       1   →       1              |        2.70 ms →        2.70 ms   (-0.12%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      510.87 μs →      492.63 μs   (-3.57%) |       1   →       1              |      510.87 μs →      492.63 μs   (-3.57%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       14.41 μs →       14.23 μs   (-1.30%) |       1   →       1              |       14.41 μs →       14.23 μs   (-1.30%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      211.92 ms →      213.40 ms   (+0.70%) |       2   →       2              |      423.83 ms →      426.81 ms   (+0.70%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.20 ms →       15.22 ms   (+0.12%) |       2   →       2              |       30.39 ms →       30.43 ms   (+0.12%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.24 ms →       13.32 ms   (+0.57%) |       1   →       1              |       13.24 ms →       13.32 ms   (+0.57%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.36 ms →       56.32 ms   (-0.06%) |       2   →       2              |      112.72 ms →      112.65 ms   (-0.06%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.21 ms →       45.18 ms   (-0.08%) |       2   →       2              |       90.43 ms →       90.35 ms   (-0.08%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.41 ms →       60.13 ms   (-0.47%) |       4   →       4              |      241.66 ms →      240.52 ms   (-0.47%) | 
  │   ├ sddk::Gvec::init                                                |       93.53 ms →       92.55 ms   (-1.05%) |       2   →       2              |      187.06 ms →      185.09 ms   (-1.05%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       70.10 ms →       69.22 ms   (-1.26%) |       2   →       2              |      140.20 ms →      138.43 ms   (-1.26%) | 
  │   ├ sddk::Gvec_shells                                               |       92.86 ms →       98.72 ms   (+6.31%) |       1   →       1              |       92.86 ms →       98.72 ms   (+6.31%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.94 ms →        1.94 ms   (+0.16%) |       1   →       1              |        1.94 ms →        1.94 ms   (+0.16%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      531.59 ms →      522.41 ms   (-1.73%) |       2   →       2              |        1.06 s  →        1.04 s    (-1.73%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |      154.74 ms →      144.06 ms   (-6.90%) |       1   →       1              |      154.74 ms →      144.06 ms   (-6.90%) | 
  │ ├ sirius::K_point::K_point                                          |        1.30 μs →        1.30 μs   (-0.35%) |       4   →       4              |        5.20 μs →        5.18 μs   (-0.35%) | 
  │ └ sirius::K_point_set::initialize                                   |      154.65 ms →      143.98 ms   (-6.90%) |       1   →       1              |      154.65 ms →      143.98 ms   (-6.90%) | 
  │   └ sirius::K_point::initialize                                     |       28.85 ms →       28.92 ms   (+0.24%) |       1   →       1              |       28.85 ms →       28.92 ms   (+0.24%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       11.07 ms →       11.14 ms   (+0.59%) |       1   →       1              |       11.07 ms →       11.14 ms   (+0.59%) | 
  │     │ └ sddk::Gvec::init                                            |        4.96 ms →        5.01 ms   (+0.95%) |       1   →       1              |        4.96 ms →        5.01 ms   (+0.95%) | 
+ │     ├ sddk::matrix_storage::matrix_storage                          |       10.56 μs →        8.12 μs  (-23.06%) |       1   →       1              |       10.56 μs →        8.12 μs  (-23.06%) | 
  │     └ sirius::K_point::update                                       |       14.89 ms →       14.89 ms   (+0.00%) |       1   →       1              |       14.89 ms →       14.89 ms   (+0.00%) | 
  │       └ sirius::Beta_projectors                                     |       10.89 ms →       10.90 ms   (+0.11%) |       1   →       1              |       10.89 ms →       10.90 ms   (+0.11%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.85 ms →        8.98 ms   (+1.44%) |       1   →       1              |        8.85 ms →        8.98 ms   (+1.44%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.56 ms →        2.56 ms   (+0.12%) |       2   →       2              |        5.12 ms →        5.13 ms   (+0.12%) | 
  ├ sirius::Potential                                                   |       49.76 ms →       52.87 ms   (+6.25%) |       1   →       1              |       49.76 ms →       52.87 ms   (+6.25%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.91 ms →        2.92 ms   (+0.31%) |       6   →       6              |       17.44 ms →       17.49 ms   (+0.31%) | 
  │ └ sirius::Potential::update                                         |       31.73 ms →       34.77 ms   (+9.57%) |       1   →       1              |       31.73 ms →       34.77 ms   (+9.57%) | 
  │   └ sirius::Potential::generate_local_potential                     |       31.34 ms →       34.36 ms   (+9.65%) |       1   →       1              |       31.34 ms →       34.36 ms   (+9.65%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       26.36 ms →       26.31 ms   (-0.20%) |       1   →       1              |       26.36 ms →       26.31 ms   (-0.20%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        4.42 ms →        7.51 ms  (+69.74%) |       1   →       1              |        4.42 ms →        7.51 ms  (+69.74%) | 
- ├ sirius::Density                                                     |       36.63 ms →       40.42 ms  (+10.33%) |       1   →       1              |       36.63 ms →       40.42 ms  (+10.33%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.82 ms →        2.82 ms   (+0.02%) |       2   →       2              |        5.63 ms →        5.63 ms   (+0.02%) | 
- │ └ sirius::Density::update                                           |       30.86 ms →       34.64 ms  (+12.26%) |       1   →       1              |       30.86 ms →       34.64 ms  (+12.26%) | 
- │   └ sirius::Density::generate_pseudo_core_charge_density            |       30.63 ms →       34.35 ms  (+12.13%) |       1   →       1              |       30.63 ms →       34.35 ms  (+12.13%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |       76.58 μs →       77.57 μs   (+1.30%) |       1   →       1              |       76.58 μs →       77.57 μs   (+1.30%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       26.09 ms →       26.43 ms   (+1.30%) |       1   →       1              |       26.09 ms →       26.43 ms   (+1.30%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        4.16 ms →        7.55 ms  (+81.65%) |       1   →       1              |        4.16 ms →        7.55 ms  (+81.65%) | 
- ├ sirius::Density::initial_density                                    |       54.01 ms →       60.95 ms  (+12.86%) |       1   →       1              |       54.01 ms →       60.95 ms  (+12.86%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       26.39 ms →       27.34 ms   (+3.63%) |       1   →       1              |       26.39 ms →       27.34 ms   (+3.63%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.33 ms →        7.73 ms  (+78.50%) |       2   →       2              |        8.66 ms →       15.46 ms  (+78.50%) | 
+ │ └ sirius::Periodic_function::integrate                              |        5.34 ms →        4.51 ms  (-15.41%) |       1   →       1              |        5.34 ms →        4.51 ms  (-15.41%) | 
  ├ sirius::Potential::generate                                         |      362.07 ms →      368.55 ms   (+1.79%) |       1   →       1              |      362.07 ms →      368.55 ms   (+1.79%) | 
- │ ├ sirius::Potential::poisson                                        |       35.10 ms →       41.57 ms  (+18.46%) |       1   →       1              |       35.10 ms →       41.57 ms  (+18.46%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        4.18 ms →       10.52 ms (+151.89%) |       1   →       1              |        4.18 ms →       10.52 ms (+151.89%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        5.34 ms →        5.29 ms   (-0.97%) |       1   →       1              |        5.34 ms →        5.29 ms   (-0.97%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.63 ms →        4.65 ms   (+0.34%) |       1   →       1              |        4.63 ms →        4.65 ms   (+0.34%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.63 ms →        4.64 ms   (+0.35%) |       1   →       1              |        4.63 ms →        4.64 ms   (+0.35%) | 
  │ ├ sirius::Periodic_function::add                                    |      821.59 μs →      764.19 μs   (-6.99%) |       2   →       2              |        1.64 ms →        1.53 ms   (-6.99%) | 
  │ ├ sirius::Potential::xc                                             |       50.68 ms →       50.67 ms   (-0.02%) |       1   →       1              |       50.68 ms →       50.67 ms   (-0.02%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       49.47 ms →       49.48 ms   (+0.03%) |       1   →       1              |       49.47 ms →       49.48 ms   (+0.03%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.53 ms →        2.54 ms   (+0.36%) |       2   →       2              |        5.05 ms →        5.07 ms   (+0.36%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.20 ms →        4.10 ms   (-2.19%) |       1   →       1              |        4.20 ms →        4.10 ms   (-2.19%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.88 ms →        3.47 ms  (-10.58%) |       1   →       1              |        3.88 ms →        3.47 ms  (-10.58%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      269.41 ms →      269.93 ms   (+0.19%) |       1   →       1              |      269.41 ms →      269.93 ms   (+0.19%) | 
+ │ └ sirius::Potential::generate_PAW_effective_potential               |      278.00 ns →      241.00 ns  (-13.31%) |       1   →       1              |      278.00 ns →      241.00 ns  (-13.31%) | 
- ├ sirius::Hamiltonian0                                                |        6.44 ms →        8.45 ms  (+31.25%) |       1   →       1              |        6.44 ms →        8.45 ms  (+31.25%) | 
- │ ├ sirius::Local_operator                                            |        5.86 ms →        7.86 ms  (+34.04%) |       1   →       1              |        5.86 ms →        7.86 ms  (+34.04%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.74 ms →        2.74 ms   (+0.20%) |       1   →       1              |        2.74 ms →        2.74 ms   (+0.20%) | 
- │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.38 ms →        3.88 ms  (+63.34%) |       1   →       1              |        2.38 ms →        3.88 ms  (+63.34%) | 
- │ ├ sirius::Non_local_operator                                        |      118.47 μs →      164.56 μs  (+38.90%) |       2   →       2              |      236.95 μs →      329.12 μs  (+38.90%) | 
+ │ ├ sirius::D_operator::initialize                                    |      145.05 μs →      110.13 μs  (-24.07%) |       1   →       1              |      145.05 μs →      110.13 μs  (-24.07%) | 
+ │ └ sirius::Q_operator::initialize                                    |      114.70 μs →       92.41 μs  (-19.43%) |       1   →       1              |      114.70 μs →       92.41 μs  (-19.43%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.31 s  →        1.28 s    (-2.33%) |       1   →       1              |        1.31 s  →        1.28 s    (-2.33%) | 
- │ ├ sirius::Hamiltonian_k                                             |       51.24 ms →       60.30 ms  (+17.67%) |       1   →       1              |       51.24 ms →       60.30 ms  (+17.67%) | 
+ │ │ ├ sirius::Local_operator::prepare_k                               |      287.87 μs →      249.40 μs  (-13.36%) |       1   →       1              |      287.87 μs →      249.40 μs  (-13.36%) | 
- │ │ └ sirius::Beta_projectors_base::prepare                           |       50.95 ms →       60.05 ms  (+17.85%) |       1   →       1              |       50.95 ms →       60.05 ms  (+17.85%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.26 s  →        1.22 s    (-3.15%) |       1   →       1              |        1.26 s  →        1.22 s    (-3.15%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       80.56 ms →       76.29 ms   (-5.31%) |       4   →       4              |      322.25 ms →      305.15 ms   (-5.31%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       48.86 ms →       44.64 ms   (-8.64%) |       1   →       1              |       48.86 ms →       44.64 ms   (-8.64%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        7.87 ms →        8.52 ms   (+8.38%) |       1   →       1              |        7.87 ms →        8.52 ms   (+8.38%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      355.03 ms →      335.44 ms   (-5.52%) |       1   →       1              |      355.03 ms →      335.44 ms   (-5.52%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      247.88 ms →      247.27 ms   (-0.25%) |       1   →       1              |      247.88 ms →      247.27 ms   (-0.25%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.57 μs →        4.04 μs  (+13.16%) |       1   →       1              |        3.57 μs →        4.04 μs  (+13.16%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.48 μs →        3.12 μs  (+25.68%) |       1   →       1              |        2.48 μs →        3.12 μs  (+25.68%) | 
- │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      421.00 ns →      643.00 ns  (+52.73%) |       1   →       1              |      421.00 ns →      643.00 ns  (+52.73%) | 
- │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      588.00 ns →      705.00 ns  (+19.90%) |       1   →       1              |      588.00 ns →      705.00 ns  (+19.90%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.33 ms →        3.18 ms   (-4.41%) |       1   →       1              |        3.33 ms →        3.18 ms   (-4.41%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.22 ms →       21.25 ms   (+0.11%) |       1   →       1              |       21.22 ms →       21.25 ms   (+0.11%) | 
+ │ │ │ └ sirius::Non_local_operator::apply                             |       41.28 ms →       31.84 ms  (-22.87%) |       2   →       2              |       82.56 ms →       63.68 ms  (-22.87%) | 
+ │ │ ├ sirius::Band::set_subspace_mtrx                                 |       17.52 ms →       14.85 ms  (-15.24%) |       2   →       2              |       35.05 ms →       29.71 ms  (-15.24%) | 
+ │ │ │ └ sddk::wf_inner                                                |       17.31 ms →       14.64 ms  (-15.45%) |       2   →       2              |       34.62 ms →       29.27 ms  (-15.45%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       21.00 ns →       37.00 ns  (+76.19%) |       2   →       2              |       42.00 ns →       74.00 ns  (+76.19%) | 
+ │ │ │   ├ sddk::wf_inner|pw                                           |       17.16 ms →       14.50 ms  (-15.53%) |       2   →       2              |       34.32 ms →       28.99 ms  (-15.53%) | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |       26.00 ns →       27.00 ns   (+3.85%) |       2   →       2              |       52.00 ns →       54.00 ns   (+3.85%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      212.90 ms →      231.20 ms   (+8.60%) |       1   →       1              |      212.90 ms →      231.20 ms   (+8.60%) | 
+ │ │ └ sddk::wf_trans                                                  |        4.94 ms →        2.60 ms  (-47.25%) |       1   →       1              |        4.94 ms →        2.60 ms  (-47.25%) | 
+ │ │   └ sddk::wf_trans|pw                                             |        4.93 ms →        2.60 ms  (-47.31%) |       1   →       1              |        4.93 ms →        2.60 ms  (-47.31%) | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      415.00 ns →      469.00 ns  (+13.01%) |       1   →       1              |      415.00 ns →      469.00 ns  (+13.01%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |       62.08 s  →       62.64 s    (+0.91%) |       1   →       1              |       62.08 s  →       62.64 s    (+0.91%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.45 ms →        2.42 ms   (-1.34%) |      19   →      19              |       46.57 ms →       45.95 ms   (-1.34%) | 
! │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.25 s  →        2.97 s    (-8.72%) |      19   →      21    (+10.53%) |       61.84 s  →       62.39 s    (+0.89%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        4.88 ms →        4.97 ms   (+2.01%) |      19   →      21    (+10.53%) |       92.63 ms →      104.43 ms  (+12.74%) | 
- │ │ │ ├ sirius::Local_operator                                        |        4.24 ms →        4.32 ms   (+1.87%) |      19   →      21    (+10.53%) |       80.52 ms →       90.67 ms  (+12.60%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function                            |      535.86 μs →      562.70 μs   (+5.01%) |      19   →      21    (+10.53%) |       10.18 ms →       11.82 ms  (+16.06%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.56 ms →        2.78 ms   (+8.48%) |      19   →      21    (+10.53%) |       48.66 ms →       58.34 ms  (+19.89%) | 
- │ │ │ ├ sirius::Non_local_operator                                    |      163.63 μs →      171.13 μs   (+4.58%) |      38   →      42    (+10.53%) |        6.22 ms →        7.19 ms  (+15.59%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |      130.72 μs →      134.14 μs   (+2.62%) |      19   →      21    (+10.53%) |        2.48 ms →        2.82 ms  (+13.42%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       91.75 μs →       97.56 μs   (+6.34%) |      19   →      21    (+10.53%) |        1.74 ms →        2.05 ms  (+17.53%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.04 s  →        1.75 s   (-13.88%) |      19   →      21    (+10.53%) |       38.69 s  →       36.83 s    (-4.82%) | 
! │ │ │ ├ sirius::Hamiltonian_k                                         |      231.36 μs →      213.37 μs   (-7.77%) |      19   →      21    (+10.53%) |        4.40 ms →        4.48 ms   (+1.94%) | 
! │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      223.34 μs →      204.35 μs   (-8.50%) |      19   →      21    (+10.53%) |        4.24 ms →        4.29 ms   (+1.13%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.69 μs →        6.26 μs   (+9.90%) |      19   →      21    (+10.53%) |      108.14 μs →      131.36 μs  (+21.47%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.97 s  →        1.63 s   (-17.60%) |      19   →      21    (+10.53%) |       37.52 s  →       34.17 s    (-8.92%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       76.94 ms →       66.29 ms  (-13.83%) |      19   →      21    (+10.53%) |        1.46 s  →        1.39 s    (-4.76%) | 
! │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.97 ms →        7.22 ms   (-9.43%) |     114   →     126    (+10.53%) |      908.83 ms →      909.73 ms   (+0.10%) | 
! │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       18.37 ms →       17.56 ms   (-4.41%) |      19   →      21    (+10.53%) |      349.01 ms →      368.74 ms   (+5.65%) | 
- │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      455.44 μs →      459.68 μs   (+0.93%) |      19   →      21    (+10.53%) |        8.65 ms →        9.65 ms  (+11.56%) | 
! │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        8.42 ms →        7.97 ms   (-5.37%) |      38   →      42    (+10.53%) |      319.93 ms →      334.61 ms   (+4.59%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.87 s  →        1.54 s   (-17.96%) |      19   →      21    (+10.53%) |       35.56 s  →       32.24 s    (-9.32%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       53.25 ms →       49.78 ms   (-6.51%) |     356   →     361     (+1.40%) |       18.96 s  →       17.97 s    (-5.20%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       29.47 ms →       29.98 ms   (+1.73%) |     356   →     361     (+1.40%) |       10.49 s  →       10.82 s    (+3.16%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.12 μs →        1.93 μs   (-8.79%) |     356   →     361     (+1.40%) |      755.26 μs →      698.53 μs   (-7.51%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.80 μs →        1.63 μs   (-9.58%) |     356   →     361     (+1.40%) |      641.60 μs →      588.31 μs   (-8.31%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      487.91 ns →      362.75 ns  (-25.65%) |     356   →     361     (+1.40%) |      173.70 μs →      130.95 μs  (-24.61%) | 
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      668.66 ns →      528.97 ns  (-20.89%) |     356   →     361     (+1.40%) |      238.04 μs →      190.96 μs  (-19.78%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        3.20 ms →        2.85 ms  (-11.08%) |     356   →     361     (+1.40%) |        1.14 s  →        1.03 s    (-9.83%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.20 ms →        3.22 ms   (+0.67%) |     356   →     361     (+1.40%) |        1.14 s  →        1.16 s    (+2.08%) | 
+ │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        8.68 ms →        6.86 ms  (-20.98%) |     712   →     722     (+1.40%) |        6.18 s  →        4.95 s   (-19.87%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |        5.98 ms →        6.17 ms   (+3.13%) |     356   →     361     (+1.40%) |        2.13 s  →        2.23 s    (+4.57%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |      988.35 μs →      990.06 μs   (+0.17%) |     693   →     701     (+1.15%) |      684.93 ms →      694.03 ms   (+1.33%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       52.27 ns →       48.93 ns   (-6.39%) |     693   →     701     (+1.15%) |       36.22 μs →       34.30 μs   (-5.31%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |      828.21 μs →      828.60 μs   (+0.05%) |     693   →     701     (+1.15%) |      573.95 ms →      580.85 ms   (+1.20%) | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       44.47 ns →       45.66 ns   (+2.68%) |     693   →     701     (+1.15%) |       30.82 μs →       32.01 μs   (+3.87%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      133.55 μs →      137.16 μs   (+2.70%) |     356   →     361     (+1.40%) |       47.54 ms →       49.51 ms   (+4.14%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        1.94 ms →        2.09 ms   (+7.68%) |     356   →     361     (+1.40%) |      689.37 ms →      752.78 ms   (+9.20%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |        2.10 ms →        2.14 ms   (+2.34%) |     337   →     340     (+0.89%) |      706.34 ms →      729.28 ms   (+3.25%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |      697.83 μs →      714.21 μs   (+2.35%) |    1.01 K →    1.02 K   (+0.89%) |      705.51 ms →      728.49 ms   (+3.26%) | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.45 ms →        1.27 ms  (-12.32%) |     356   →     361     (+1.40%) |      517.41 ms →      460.02 ms  (-11.09%) | 
+ │ │ │ │   │ └ sddk::wf_inner                                          |        1.38 ms →        1.23 ms  (-10.93%) |     356   →     361     (+1.40%) |      491.62 ms →      444.04 ms   (-9.68%) | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       39.62 ns →       42.16 ns   (+6.40%) |     356   →     361     (+1.40%) |       14.11 μs →       15.22 μs   (+7.89%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        1.22 ms →        1.07 ms  (-12.54%) |     356   →     361     (+1.40%) |      434.18 ms →      385.06 ms  (-11.31%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       39.72 ns →       48.44 ns  (+21.93%) |     356   →     361     (+1.40%) |       14.14 μs →       17.49 μs  (+23.65%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       35.61 ms →       28.78 ms  (-19.20%) |     356   →     361     (+1.40%) |       12.68 s  →       10.39 s   (-18.07%) | 
+ │ │ │ │   ├ sirius::residuals                                         |        2.65 ms →        2.32 ms  (-12.69%) |     340   →     346     (+1.76%) |      901.53 ms →      801.03 ms  (-11.15%) | 
+ │ │ │ │   │ ├ sddk::wf_trans                                          |        1.39 ms →        1.08 ms  (-22.57%) |     337   →     342     (+1.48%) |      470.08 ms →      369.37 ms  (-21.43%) | 
+ │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      696.02 μs →      538.66 μs  (-22.61%) |     674   →     684     (+1.48%) |      469.12 ms →      368.44 ms  (-21.46%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.17 ms →        1.13 ms   (-2.88%) |     337   →     342     (+1.48%) |      393.29 ms →      387.61 ms   (-1.44%) | 
+ │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        6.77 ms →        4.33 ms  (-36.11%) |      54   →      90    (+66.67%) |      365.62 ms →      389.34 ms   (+6.49%) | 
+ │ │ │ │     └ sddk::wf_trans                                          |        4.06 ms →        2.40 ms  (-40.86%) |      89   →     159    (+78.65%) |      361.12 ms →      381.52 ms   (+5.65%) | 
+ │ │ │ │       └ sddk::wf_trans|pw                                     |        2.91 ms →        1.67 ms  (-42.56%) |     124   →     228    (+83.87%) |      360.94 ms →      381.22 ms   (+5.62%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      325.58 ns →      530.86 ns  (+63.05%) |      19   →      21    (+10.53%) |        6.19 μs →       11.15 μs  (+80.21%) | 
! │ │ │ └ sirius::K_point_set::sync_band_energies                       |       20.35 μs →       19.81 μs   (-2.66%) |      19   →      21    (+10.53%) |      386.67 μs →      415.99 μs   (+7.58%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.52 ms →        1.55 ms   (+1.90%) |      19   →      21    (+10.53%) |       28.87 ms →       32.51 ms  (+12.63%) | 
! │ │ ├ sirius::Density::generate                                       |      570.23 ms →      562.47 ms   (-1.36%) |      19   →      21    (+10.53%) |       10.83 s  →       11.81 s    (+9.02%) | 
- │ │ │ ├ sirius::Density::generate_valence                             |      397.22 ms →      412.40 ms   (+3.82%) |      19   →      21    (+10.53%) |        7.55 s  →        8.66 s   (+14.75%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        7.90 μs →        8.85 μs  (+11.95%) |      19   →      21    (+10.53%) |      150.12 μs →      185.75 μs  (+23.73%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.36 μs →        8.38 μs  (+13.76%) |      19   →      21    (+10.53%) |      139.91 μs →      175.92 μs  (+25.74%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       33.70 ms →       17.70 ms  (-47.48%) |      19   →      21    (+10.53%) |      640.31 ms →      371.72 ms  (-41.95%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.11 μs →        7.98 μs  (+12.13%) |      19   →      21    (+10.53%) |      135.13 μs →      167.48 μs  (+23.93%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        5.40 ms →        2.85 ms  (-47.24%) |      19   →      21    (+10.53%) |      102.55 ms →       59.81 ms  (-41.68%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       27.26 ms →       13.79 ms  (-49.41%) |      19   →      21    (+10.53%) |      517.90 ms →      289.58 ms  (-44.09%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      507.37 ns →        1.05 μs (+107.11%) |      19   →      21    (+10.53%) |        9.64 μs →       22.07 μs (+128.91%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      112.43 ms →      127.85 ms  (+13.72%) |      19   →      21    (+10.53%) |        2.14 s  →        2.68 s   (+25.69%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.88 ms →        1.92 ms   (+2.15%) |      19   →      21    (+10.53%) |       35.72 ms →       40.33 ms  (+12.90%) | 
- │ │ │ │ └ sirius::Density::augment                                    |      210.50 ms →      232.64 ms  (+10.51%) |      19   →      21    (+10.53%) |        4.00 s  →        4.89 s   (+22.15%) | 
- │ │ │ │   └ sirius::Density::generate_rho_aug                         |      210.27 ms →      232.43 ms  (+10.53%) |      19   →      21    (+10.53%) |        4.00 s  →        4.88 s   (+22.17%) | 
+ │ │ │ ├ sirius::Field4D::symmetrize                                   |      145.54 ms →      123.01 ms  (-15.47%) |      19   →      21    (+10.53%) |        2.77 s  →        2.58 s    (-6.58%) | 
+ │ │ │ │ └ sirius::symmetrize_function|fpw                             |      145.53 ms →      123.01 ms  (-15.47%) |      19   →      21    (+10.53%) |        2.77 s  →        2.58 s    (-6.58%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       61.54 ms →       39.94 ms  (-35.10%) |      19   →      21    (+10.53%) |        1.17 s  →      838.66 ms  (-28.27%) | 
! │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       70.66 ms →       69.78 ms   (-1.24%) |      19   →      21    (+10.53%) |        1.34 s  →        1.47 s    (+9.15%) | 
- │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.68 ms →       12.64 ms   (-0.33%) |      19   →      21    (+10.53%) |      241.00 ms →      265.49 ms  (+10.16%) | 
! │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.69 ms →       23.57 ms   (-0.50%) |      19   →      21    (+10.53%) |      450.12 ms →      494.99 ms   (+9.97%) | 
! │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        3.78 ms →        3.48 ms   (-8.11%) |      19   →      21    (+10.53%) |       71.91 ms →       73.04 ms   (+1.56%) | 
- │ │ ├ sirius::Density::mix                                            |      133.19 ms →      134.78 ms   (+1.20%) |      19   →      21    (+10.53%) |        2.53 s  →        2.83 s   (+11.85%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      751.63 μs →      309.26 μs  (-58.85%) |      19   →      21    (+10.53%) |       14.28 ms →        6.49 ms  (-54.52%) | 
! │ │ │ ├ sirius::Periodic_function|inner                               |        4.93 ms →        4.78 ms   (-3.06%) |     229   →     259    (+13.10%) |        1.13 s  →        1.24 s    (+9.64%) | 
! │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.82 ms →        4.63 ms   (-3.97%) |     229   →     259    (+13.10%) |        1.10 s  →        1.20 s    (+8.61%) | 
! │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.82 ms →        4.63 ms   (-3.97%) |     229   →     259    (+13.10%) |        1.10 s  →        1.20 s    (+8.61%) | 
! │ │ │ └ sirius::Density::mixer_output                                 |        5.61 ms →        5.37 ms   (-4.30%) |      19   →      21    (+10.53%) |      106.54 ms →      112.69 ms   (+5.77%) | 
! │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        4.88 ms →        4.68 ms   (-4.05%) |      19   →      21    (+10.53%) |       92.65 ms →       98.26 ms   (+6.05%) | 
- │ │ ├ sirius::Potential::generate                                     |      355.43 ms →      361.73 ms   (+1.77%) |      19   →      21    (+10.53%) |        6.75 s  →        7.60 s   (+12.48%) | 
- │ │ │ ├ sirius::Potential::poisson                                    |       34.94 ms →       41.49 ms  (+18.75%) |      19   →      21    (+10.53%) |      663.89 ms →      871.39 ms  (+31.25%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        4.25 ms →       10.65 ms (+150.70%) |      19   →      21    (+10.53%) |       80.70 ms →      223.60 ms (+177.08%) | 
! │ │ │ │ └ sirius::Periodic_function|inner                             |        5.25 ms →        5.10 ms   (-2.74%) |      19   →      21    (+10.53%) |       99.71 ms →      107.18 ms   (+7.50%) | 
- │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.63 ms →        4.67 ms   (+0.97%) |      19   →      21    (+10.53%) |       87.90 ms →       98.10 ms  (+11.60%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.63 ms →        4.67 ms   (+0.97%) |      19   →      21    (+10.53%) |       87.88 ms →       98.08 ms  (+11.60%) | 
! │ │ │ ├ sirius::Periodic_function::add                                |      804.77 μs →      764.99 μs   (-4.94%) |      38   →      42    (+10.53%) |       30.58 ms →       32.13 ms   (+5.06%) | 
- │ │ │ ├ sirius::Potential::xc                                         |       44.52 ms →       44.74 ms   (+0.49%) |      19   →      21    (+10.53%) |      845.93 ms →      939.53 ms  (+11.07%) | 
- │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       43.34 ms →       43.55 ms   (+0.48%) |      19   →      21    (+10.53%) |      823.52 ms →      914.60 ms  (+11.06%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function                          |      672.41 μs →      686.62 μs   (+2.11%) |      38   →      42    (+10.53%) |       25.55 ms →       28.84 ms  (+12.86%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.14 ms →        4.32 ms   (+4.19%) |      19   →      21    (+10.53%) |       78.69 ms →       90.62 ms  (+15.16%) | 
! │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.92 ms →        3.55 ms   (-9.48%) |      19   →      21    (+10.53%) |       74.54 ms →       74.58 ms   (+0.05%) | 
- │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      269.01 ms →      269.00 ms   (-0.00%) |      19   →      21    (+10.53%) |        5.11 s  →        5.65 s   (+10.52%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      282.42 ns →      225.76 ns  (-20.06%) |      19   →      21    (+10.53%) |        5.37 μs →        4.74 μs  (-11.65%) | 
! │ │ ├ sirius::Field4D::symmetrize                                     |       96.79 ms →       96.24 ms   (-0.56%) |      19   →      21    (+10.53%) |        1.84 s  →        2.02 s    (+9.90%) | 
! │ │ │ └ sirius::symmetrize_function|fpw                               |       96.79 ms →       96.24 ms   (-0.56%) |      19   →      21    (+10.53%) |        1.84 s  →        2.02 s    (+9.90%) | 
- │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.23 ms →       13.48 ms   (+1.86%) |      19   →      21    (+10.53%) |      251.37 ms →      283.01 ms  (+12.59%) | 
! │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       70.34 ms →       69.52 ms   (-1.15%) |      19   →      21    (+10.53%) |        1.34 s  →        1.46 s    (+9.25%) | 
- │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.59 ms →       12.61 ms   (+0.22%) |      19   →      21    (+10.53%) |      239.14 ms →      264.88 ms  (+10.77%) | 
! │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.85 ms →        3.73 ms   (-3.16%) |      19   →      21    (+10.53%) |       73.20 ms →       78.35 ms   (+7.03%) | 
- │ │ ├ sirius::Periodic_function|inner                                 |        4.68 ms →        4.69 ms   (+0.08%) |     133   →     147    (+10.53%) |      623.08 ms →      689.19 ms  (+10.61%) | 
- │ │ │ └ sirius::Periodic_function|inner_local                         |        4.56 ms →        4.57 ms   (+0.09%) |     133   →     147    (+10.53%) |      606.74 ms →      671.23 ms  (+10.63%) | 
- │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.56 ms →        4.57 ms   (+0.09%) |     133   →     147    (+10.53%) |      606.66 ms →      671.14 ms  (+10.63%) | 
! │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.95 ms →        4.75 ms   (-4.05%) |      57   →      63    (+10.53%) |      282.00 ms →      299.05 ms   (+6.05%) | 
! │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.94 ms →        4.74 ms   (-4.06%) |      57   →      63    (+10.53%) |      281.62 ms →      298.63 ms   (+6.04%) | 
- │ │ ├ sirius::Periodic_function::integrate                            |        4.53 ms →        4.55 ms   (+0.44%) |      19   →      21    (+10.53%) |       86.05 ms →       95.53 ms  (+11.02%) | 
! │ │ └ sirius::Density::get_magnetisation                              |       75.73 μs →       75.36 μs   (-0.48%) |      19   →      21    (+10.53%) |        1.44 ms →        1.58 ms  (+10.00%) | 
! │ │   └ sirius::Density::compute_atomic_mag_mom                       |       71.78 μs →       70.46 μs   (-1.84%) |      19   →      21    (+10.53%) |        1.36 ms →        1.48 ms   (+8.50%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.48 ms →        5.57 ms   (+1.65%) |       2   →       2              |       10.97 ms →       11.15 ms   (+1.65%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.81 ms →        4.86 ms   (+1.07%) |       6   →       6              |       28.84 ms →       29.15 ms   (+1.07%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.80 ms →        4.81 ms   (+0.02%) |       6   →       6              |       28.82 ms →       28.83 ms   (+0.02%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.80 ms →        4.80 ms   (+0.05%) |       6   →       6              |       28.81 ms →       28.83 ms   (+0.05%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        5.21 ms →        4.99 ms   (-4.16%) |       3   →       3              |       15.63 ms →       14.98 ms   (-4.16%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        5.21 ms →        4.99 ms   (-4.21%) |       3   →       3              |       15.62 ms →       14.96 ms   (-4.21%) | 
  ├ sirius::Periodic_function|inner                                     |        4.54 ms →        4.80 ms   (+5.83%) |       2   →       2              |        9.07 ms →        9.60 ms   (+5.83%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.53 ms →        4.80 ms   (+5.84%) |       2   →       2              |        9.06 ms →        9.59 ms   (+5.84%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.53 ms →        4.80 ms   (+5.83%) |       2   →       2              |        9.06 ms →        9.59 ms   (+5.83%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.92 ms →        4.96 ms   (+0.93%) |       1   →       1              |        4.92 ms →        4.96 ms   (+0.93%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.91 ms →        4.96 ms   (+0.93%) |       1   →       1              |        4.91 ms →        4.96 ms   (+0.93%) | 
- └ sirius::finalize                                                    |      267.84 ms →      415.64 ms  (+55.18%) |       1   →       1              |      267.84 ms →      415.64 ms  (+55.18%) | 
  ====================================================================================================================================================================================================
```
