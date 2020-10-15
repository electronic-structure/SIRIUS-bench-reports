# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
- sirius                                                                |       72.10 s  →       84.78 s   (+17.59%) |       1   →       1              |       72.10 s  →       84.78 s   (+17.59%) | 
  ├ sirius::initialize                                                  |        2.98 s  →        2.90 s    (-2.51%) |       1   →       1              |        2.98 s  →        2.90 s    (-2.51%) | 
  ├ sirius::Simulation_context::initialize                              |        3.81 s  →        3.86 s    (+1.30%) |       1   →       1              |        3.81 s  →        3.86 s    (+1.30%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       34.33 ms →        3.32 ms  (-90.33%) |       1   →       1              |       34.33 ms →        3.32 ms  (-90.33%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      149.46 ms →      189.84 ms  (+27.02%) |       1   →       1              |      149.46 ms →      189.84 ms  (+27.02%) | 
- │ │ ├ sirius::Atom_type::init                                         |       65.44 ms →       85.15 ms  (+30.11%) |       2   →       2              |      130.89 ms →      170.30 ms  (+30.11%) | 
  │ │ └ sirius::Unit_cell::update                                       |       18.48 ms →       19.45 ms   (+5.24%) |       1   →       1              |       18.48 ms →       19.45 ms   (+5.24%) | 
- │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.83 ms →        5.13 ms  (+34.04%) |       1   →       1              |        3.83 ms →        5.13 ms  (+34.04%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       14.57 ms →       14.23 ms   (-2.31%) |       1   →       1              |       14.57 ms →       14.23 ms   (-2.31%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       14.51 ms →       14.17 ms   (-2.29%) |       1   →       1              |       14.51 ms →       14.17 ms   (-2.29%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.83 ms →        2.77 ms   (-1.91%) |       1   →       1              |        2.83 ms →        2.77 ms   (-1.91%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      503.42 μs →      550.84 μs   (+9.42%) |       1   →       1              |      503.42 μs →      550.84 μs   (+9.42%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       15.63 μs →       15.11 μs   (-3.30%) |       1   →       1              |       15.63 μs →       15.11 μs   (-3.30%) | 
  │ └ sirius::Simulation_context::update                                |        3.53 s  →        3.61 s    (+2.53%) |       1   →       1              |        3.53 s  →        3.61 s    (+2.53%) | 
  │   ├ sirius::Unit_cell::update                                       |        6.87 ms →        7.13 ms   (+3.65%) |       1   →       1              |        6.87 ms →        7.13 ms   (+3.65%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.47 ms →        3.72 ms   (+7.19%) |       1   →       1              |        3.47 ms →        3.72 ms   (+7.19%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.35 ms →        3.35 ms   (+0.16%) |       1   →       1              |        3.35 ms →        3.35 ms   (+0.16%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.30 ms →        3.28 ms   (-0.53%) |       1   →       1              |        3.30 ms →        3.28 ms   (-0.53%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.75 ms →        2.72 ms   (-1.07%) |       1   →       1              |        2.75 ms →        2.72 ms   (-1.07%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      513.45 μs →      526.17 μs   (+2.48%) |       1   →       1              |      513.45 μs →      526.17 μs   (+2.48%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       15.23 μs →       14.34 μs   (-5.87%) |       1   →       1              |       15.23 μs →       14.34 μs   (-5.87%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      213.35 ms →      213.55 ms   (+0.10%) |       2   →       2              |      426.70 ms →      427.11 ms   (+0.10%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.14 ms →       15.16 ms   (+0.15%) |       2   →       2              |       30.27 ms →       30.32 ms   (+0.15%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.25 ms →       13.26 ms   (+0.09%) |       1   →       1              |       13.25 ms →       13.26 ms   (+0.09%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.36 ms →       56.24 ms   (-0.20%) |       2   →       2              |      112.71 ms →      112.48 ms   (-0.20%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.14 ms →       45.21 ms   (+0.16%) |       2   →       2              |       90.28 ms →       90.42 ms   (+0.16%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.48 ms →       60.50 ms   (+0.04%) |       4   →       4              |      241.91 ms →      242.00 ms   (+0.04%) | 
  │   ├ sddk::Gvec::init                                                |       93.51 ms →       94.12 ms   (+0.65%) |       2   →       2              |      187.02 ms →      188.24 ms   (+0.65%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       70.10 ms →       70.58 ms   (+0.68%) |       2   →       2              |      140.21 ms →      141.16 ms   (+0.68%) | 
  │   ├ sddk::Gvec_shells                                               |       92.42 ms →       99.01 ms   (+7.14%) |       1   →       1              |       92.42 ms →       99.01 ms   (+7.14%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.94 ms →        1.95 ms   (+0.30%) |       1   →       1              |        1.94 ms →        1.95 ms   (+0.30%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      609.52 ms →      664.44 ms   (+9.01%) |       2   →       2              |        1.22 s  →        1.33 s    (+9.01%) | 
+ ├ sirius::K_point_set::create_k_mesh                                  |      145.47 ms →       89.30 ms  (-38.61%) |       1   →       1              |      145.47 ms →       89.30 ms  (-38.61%) | 
- │ ├ sirius::K_point::K_point                                          |        1.66 μs →        2.42 μs  (+45.90%) |       4   →       4              |        6.64 μs →        9.69 μs  (+45.90%) | 
+ │ └ sirius::K_point_set::initialize                                   |      145.38 ms →       89.22 ms  (-38.63%) |       1   →       1              |      145.38 ms →       89.22 ms  (-38.63%) | 
  │   └ sirius::K_point::initialize                                     |       29.40 ms →       28.27 ms   (-3.86%) |       1   →       1              |       29.40 ms →       28.27 ms   (-3.86%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       11.58 ms →       10.90 ms   (-5.91%) |       1   →       1              |       11.58 ms →       10.90 ms   (-5.91%) | 
  │     │ └ sddk::Gvec::init                                            |        5.38 ms →        4.91 ms   (-8.81%) |       1   →       1              |        5.38 ms →        4.91 ms   (-8.81%) | 
+ │     ├ sddk::matrix_storage::matrix_storage                          |       10.73 μs →        6.85 μs  (-36.21%) |       1   →       1              |       10.73 μs →        6.85 μs  (-36.21%) | 
  │     └ sirius::K_point::update                                       |       14.85 ms →       14.53 ms   (-2.16%) |       1   →       1              |       14.85 ms →       14.53 ms   (-2.16%) | 
  │       └ sirius::Beta_projectors                                     |       10.49 ms →       10.61 ms   (+1.15%) |       1   →       1              |       10.49 ms →       10.61 ms   (+1.15%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.58 ms →        8.75 ms   (+1.99%) |       1   →       1              |        8.58 ms →        8.75 ms   (+1.99%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.58 ms →        2.61 ms   (+0.98%) |       2   →       2              |        5.16 ms →        5.21 ms   (+0.98%) | 
  ├ sirius::Potential                                                   |       54.21 ms →       49.22 ms   (-9.22%) |       1   →       1              |       54.21 ms →       49.22 ms   (-9.22%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.91 ms →        2.93 ms   (+0.38%) |       6   →       6              |       17.48 ms →       17.55 ms   (+0.38%) | 
+ │ └ sirius::Potential::update                                         |       36.12 ms →       31.04 ms  (-14.06%) |       1   →       1              |       36.12 ms →       31.04 ms  (-14.06%) | 
+ │   └ sirius::Potential::generate_local_potential                     |       35.71 ms →       30.65 ms  (-14.15%) |       1   →       1              |       35.71 ms →       30.65 ms  (-14.15%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       31.27 ms →       24.09 ms  (-22.97%) |       1   →       1              |       31.27 ms →       24.09 ms  (-22.97%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        3.85 ms →        6.05 ms  (+57.09%) |       1   →       1              |        3.85 ms →        6.05 ms  (+57.09%) | 
  ├ sirius::Density                                                     |       42.27 ms →       38.10 ms   (-9.84%) |       1   →       1              |       42.27 ms →       38.10 ms   (-9.84%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.84 ms →        2.81 ms   (-1.02%) |       2   →       2              |        5.68 ms →        5.62 ms   (-1.02%) | 
+ │ └ sirius::Density::update                                           |       36.45 ms →       32.35 ms  (-11.25%) |       1   →       1              |       36.45 ms →       32.35 ms  (-11.25%) | 
+ │   └ sirius::Density::generate_pseudo_core_charge_density            |       36.17 ms →       32.09 ms  (-11.28%) |       1   →       1              |       36.17 ms →       32.09 ms  (-11.28%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |       79.16 μs →       77.17 μs   (-2.51%) |       1   →       1              |       79.16 μs →       77.17 μs   (-2.51%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       32.10 ms →       24.28 ms  (-24.35%) |       1   →       1              |       32.10 ms →       24.28 ms  (-24.35%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        3.63 ms →        7.42 ms (+104.19%) |       1   →       1              |        3.63 ms →        7.42 ms (+104.19%) | 
+ ├ sirius::Density::initial_density                                    |       64.08 ms →       56.99 ms  (-11.07%) |       1   →       1              |       64.08 ms →       56.99 ms  (-11.07%) | 
+ │ ├ sirius::Simulation_context::make_periodic_function                |       35.43 ms →       25.14 ms  (-29.04%) |       1   →       1              |       35.43 ms →       25.14 ms  (-29.04%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.01 ms →        6.83 ms  (+36.23%) |       2   →       2              |       10.03 ms →       13.66 ms  (+36.23%) | 
  │ └ sirius::Periodic_function::integrate                              |        4.88 ms →        4.53 ms   (-7.22%) |       1   →       1              |        4.88 ms →        4.53 ms   (-7.22%) | 
  ├ sirius::Potential::generate                                         |      372.48 ms →      362.77 ms   (-2.61%) |       1   →       1              |      372.48 ms →      362.77 ms   (-2.61%) | 
+ │ ├ sirius::Potential::poisson                                        |       43.72 ms →       35.71 ms  (-18.31%) |       1   →       1              |       43.72 ms →       35.71 ms  (-18.31%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.28 ms →        7.94 ms (+141.99%) |       1   →       1              |        3.28 ms →        7.94 ms (+141.99%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        4.91 ms →        4.64 ms   (-5.47%) |       1   →       1              |        4.91 ms →        4.64 ms   (-5.47%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.63 ms →        4.63 ms   (-0.06%) |       1   →       1              |        4.63 ms →        4.63 ms   (-0.06%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.63 ms →        4.62 ms   (-0.06%) |       1   →       1              |        4.63 ms →        4.62 ms   (-0.06%) | 
  │ ├ sirius::Periodic_function::add                                    |      756.73 μs →      761.99 μs   (+0.69%) |       2   →       2              |        1.51 ms →        1.52 ms   (+0.69%) | 
  │ ├ sirius::Potential::xc                                             |       53.13 ms →       51.63 ms   (-2.82%) |       1   →       1              |       53.13 ms →       51.63 ms   (-2.82%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.92 ms →       50.43 ms   (-2.87%) |       1   →       1              |       51.92 ms →       50.43 ms   (-2.87%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.56 ms →        2.53 ms   (-0.93%) |       2   →       2              |        5.11 ms →        5.07 ms   (-0.93%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.66 ms →        4.52 ms   (-2.93%) |       1   →       1              |        4.66 ms →        4.52 ms   (-2.93%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.67 ms →        2.89 ms  (-21.40%) |       1   →       1              |        3.67 ms →        2.89 ms  (-21.40%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      269.10 ms →      269.56 ms   (+0.17%) |       1   →       1              |      269.10 ms →      269.56 ms   (+0.17%) | 
+ │ └ sirius::Potential::generate_PAW_effective_potential               |      296.00 ns →      227.00 ns  (-23.31%) |       1   →       1              |      296.00 ns →      227.00 ns  (-23.31%) | 
  ├ sirius::Hamiltonian0                                                |        6.31 ms →        6.52 ms   (+3.25%) |       1   →       1              |        6.31 ms →        6.52 ms   (+3.25%) | 
  │ ├ sirius::Local_operator                                            |        5.83 ms →        5.98 ms   (+2.64%) |       1   →       1              |        5.83 ms →        5.98 ms   (+2.64%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.78 ms →        2.75 ms   (-0.85%) |       1   →       1              |        2.78 ms →        2.75 ms   (-0.85%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.31 ms →        2.42 ms   (+4.98%) |       1   →       1              |        2.31 ms →        2.42 ms   (+4.98%) | 
  │ ├ sirius::Non_local_operator                                        |       76.21 μs →       73.53 μs   (-3.51%) |       2   →       2              |      152.41 μs →      147.06 μs   (-3.51%) | 
- │ ├ sirius::D_operator::initialize                                    |      134.39 μs →      169.51 μs  (+26.13%) |       1   →       1              |      134.39 μs →      169.51 μs  (+26.13%) | 
  │ └ sirius::Q_operator::initialize                                    |      118.10 μs →      116.82 μs   (-1.08%) |       1   →       1              |      118.10 μs →      116.82 μs   (-1.08%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.28 s  →        1.28 s    (+0.16%) |       1   →       1              |        1.28 s  →        1.28 s    (+0.16%) | 
  │ ├ sirius::Hamiltonian_k                                             |       46.87 ms →       50.96 ms   (+8.74%) |       1   →       1              |       46.87 ms →       50.96 ms   (+8.74%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      282.60 μs →      278.79 μs   (-1.35%) |       1   →       1              |      282.60 μs →      278.79 μs   (-1.35%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       46.58 ms →       50.68 ms   (+8.79%) |       1   →       1              |       46.58 ms →       50.68 ms   (+8.79%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.23 s  →        1.23 s    (-0.16%) |       1   →       1              |        1.23 s  →        1.23 s    (-0.16%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       77.16 ms →       76.98 ms   (-0.24%) |       4   →       4              |      308.63 ms →      307.90 ms   (-0.24%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       47.61 ms →       44.00 ms   (-7.57%) |       1   →       1              |       47.61 ms →       44.00 ms   (-7.57%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        8.04 ms →        8.67 ms   (+7.90%) |       1   →       1              |        8.04 ms →        8.67 ms   (+7.90%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      310.04 ms →      337.13 ms   (+8.74%) |       1   →       1              |      310.04 ms →      337.13 ms   (+8.74%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      242.68 ms →      248.81 ms   (+2.53%) |       1   →       1              |      242.68 ms →      248.81 ms   (+2.53%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        4.02 μs →        3.72 μs   (-7.51%) |       1   →       1              |        4.02 μs →        3.72 μs   (-7.51%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.04 μs →        2.73 μs  (-10.12%) |       1   →       1              |        3.04 μs →        2.73 μs  (-10.12%) | 
+ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      698.00 ns →      440.00 ns  (-36.96%) |       1   →       1              |      698.00 ns →      440.00 ns  (-36.96%) | 
- │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      506.00 ns →      696.00 ns  (+37.55%) |       1   →       1              |      506.00 ns →      696.00 ns  (+37.55%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.14 ms →        3.20 ms   (+2.11%) |       1   →       1              |        3.14 ms →        3.20 ms   (+2.11%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.32 ms →       21.30 ms   (-0.08%) |       1   →       1              |       21.32 ms →       21.30 ms   (-0.08%) | 
- │ │ │ └ sirius::Non_local_operator::apply                             |       21.43 ms →       31.89 ms  (+48.77%) |       2   →       2              |       42.87 ms →       63.78 ms  (+48.77%) | 
- │ │ ├ sirius::Band::set_subspace_mtrx                                 |        6.87 ms →       14.59 ms (+112.31%) |       2   →       2              |       13.74 ms →       29.18 ms (+112.31%) | 
- │ │ │ └ sddk::wf_inner                                                |        6.65 ms →       14.38 ms (+116.24%) |       2   →       2              |       13.30 ms →       28.76 ms (+116.24%) | 
  │ │ │   ├ sddk::wf_inner|scale                                        |       20.50 ns →       21.00 ns   (+2.44%) |       2   →       2              |       41.00 ns →       42.00 ns   (+2.44%) | 
- │ │ │   ├ sddk::wf_inner|pw                                           |        6.50 ms →       14.25 ms (+119.18%) |       2   →       2              |       13.01 ms →       28.51 ms (+119.18%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       21.50 ns →       31.00 ns  (+44.19%) |       2   →       2              |       43.00 ns →       62.00 ns  (+44.19%) | 
+ │ │ ├ Eigensolver_cuda|zhegvdx                                        |      273.51 ms →      230.53 ms  (-15.71%) |       1   →       1              |      273.51 ms →      230.53 ms  (-15.71%) | 
  │ │ └ sddk::wf_trans                                                  |        2.61 ms →        2.62 ms   (+0.20%) |       1   →       1              |        2.61 ms →        2.62 ms   (+0.20%) | 
  │ │   └ sddk::wf_trans|pw                                             |        2.61 ms →        2.61 ms   (+0.17%) |       1   →       1              |        2.61 ms →        2.61 ms   (+0.17%) | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      419.00 ns →      459.00 ns   (+9.55%) |       1   →       1              |      419.00 ns →      459.00 ns   (+9.55%) | 
- ├ sirius::DFT_ground_state::scf_loop                                  |       62.22 s  →       72.34 s   (+16.28%) |       1   →       1              |       62.22 s  →       72.34 s   (+16.28%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.46 ms →        2.45 ms   (-0.50%) |      19   →      19              |       46.71 ms →       46.47 ms   (-0.50%) | 
- │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.26 s  →        2.88 s   (-11.75%) |      19   →      25    (+31.58%) |       61.96 s  →       71.95 s   (+16.12%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        5.41 ms →        5.66 ms   (+4.63%) |      19   →      25    (+31.58%) |      102.76 ms →      141.48 ms  (+37.67%) | 
- │ │ │ ├ sirius::Local_operator                                        |        4.82 ms →        4.79 ms   (-0.51%) |      19   →      25    (+31.58%) |       91.54 ms →      119.83 ms  (+30.90%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function                            |      559.65 μs →      542.73 μs   (-3.02%) |      19   →      25    (+31.58%) |       10.63 ms →       13.57 ms  (+27.60%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.95 ms →        3.01 ms   (+1.94%) |      19   →      25    (+31.58%) |       56.09 ms →       75.24 ms  (+34.13%) | 
- │ │ │ ├ sirius::Non_local_operator                                    |      148.92 μs →      292.73 μs  (+96.56%) |      38   →      50    (+31.58%) |        5.66 ms →       14.64 ms (+158.64%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |      120.00 μs →      117.21 μs   (-2.33%) |      19   →      25    (+31.58%) |        2.28 ms →        2.93 ms  (+28.52%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       93.11 μs →       89.55 μs   (-3.82%) |      19   →      25    (+31.58%) |        1.77 ms →        2.24 ms  (+26.55%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.03 s  →        1.65 s   (-18.56%) |      19   →      25    (+31.58%) |       38.57 s  →       41.33 s    (+7.15%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      221.17 μs →      209.26 μs   (-5.38%) |      19   →      25    (+31.58%) |        4.20 ms →        5.23 ms  (+24.49%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      210.46 μs →      199.86 μs   (-5.04%) |      19   →      25    (+31.58%) |        4.00 ms →        5.00 ms  (+24.95%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        7.76 μs →        6.90 μs  (-11.10%) |      19   →      25    (+31.58%) |      147.42 μs →      172.44 μs  (+16.97%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.97 s  →        1.53 s   (-21.94%) |      19   →      25    (+31.58%) |       37.35 s  →       38.36 s    (+2.71%) | 
- │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       77.30 ms →       65.69 ms  (-15.02%) |      19   →      25    (+31.58%) |        1.47 s  →        1.64 s   (+11.81%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        8.00 ms →        6.43 ms  (-19.56%) |     114   →     150    (+31.58%) |      911.97 ms →      965.22 ms   (+5.84%) | 
- │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       17.78 ms →       17.90 ms   (+0.66%) |      19   →      25    (+31.58%) |      337.89 ms →      447.51 ms  (+32.44%) | 
- │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      470.00 μs →      479.18 μs   (+1.95%) |      19   →      25    (+31.58%) |        8.93 ms →       11.98 ms  (+34.15%) | 
- │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        8.06 ms →        8.17 ms   (+1.43%) |      38   →      50    (+31.58%) |      306.22 ms →      408.70 ms  (+33.46%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.86 s  →        1.44 s   (-22.56%) |      19   →      25    (+31.58%) |       35.39 s  →       36.06 s    (+1.90%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       50.73 ms →       50.35 ms   (-0.76%) |     356   →     451    (+26.69%) |       18.06 s  →       22.71 s   (+25.73%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       28.30 ms →       27.17 ms   (-3.99%) |     356   →     451    (+26.69%) |       10.07 s  →       12.25 s   (+21.63%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.18 μs →        2.16 μs   (-1.11%) |     356   →     451    (+26.69%) |      776.23 μs →      972.42 μs  (+25.28%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.87 μs →        1.81 μs   (-3.27%) |     356   →     451    (+26.69%) |      666.03 μs →      816.17 μs  (+22.54%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      445.26 ns →      495.18 ns  (+11.21%) |     356   →     451    (+26.69%) |      158.51 μs →      223.33 μs  (+40.89%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      573.72 ns →      672.73 ns  (+17.26%) |     356   →     451    (+26.69%) |      204.25 μs →      303.40 μs  (+48.55%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.91 ms →        2.98 ms   (+2.32%) |     356   →     451    (+26.69%) |        1.04 s  →        1.34 s   (+29.63%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.20 ms →        3.05 ms   (-4.61%) |     356   →     451    (+26.69%) |        1.14 s  →        1.38 s   (+20.85%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        8.15 ms →        8.57 ms   (+5.05%) |     712   →     902    (+26.69%) |        5.81 s  →        7.73 s   (+33.08%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |        6.72 ms →        6.39 ms   (-4.95%) |     356   →     451    (+26.69%) |        2.39 s  →        2.88 s   (+20.42%) | 
- │ │ │ │   │ ├ sddk::wf_inner                                          |        1.19 ms →        1.16 ms   (-2.69%) |     693   →     877    (+26.55%) |      824.28 ms →        1.02 s   (+23.15%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       51.85 ns →       34.54 ns  (-33.38%) |     693   →     877    (+26.55%) |       35.93 μs →       30.29 μs  (-15.69%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        1.03 ms →      992.66 μs   (-3.55%) |     693   →     877    (+26.55%) |      713.27 ms →      870.56 ms  (+22.05%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       47.10 ns →       49.08 ns   (+4.19%) |     693   →     877    (+26.55%) |       32.64 μs →       43.04 μs  (+31.85%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      132.95 μs →      126.42 μs   (-4.91%) |     356   →     451    (+26.69%) |       47.33 ms →       57.01 ms  (+20.46%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        2.11 ms →        1.91 ms   (-9.31%) |     356   →     451    (+26.69%) |      751.29 ms →      863.17 ms  (+14.89%) | 
- │ │ │ │   │ └ sddk::wf_trans                                          |        2.28 ms →        2.22 ms   (-2.79%) |     337   →     426    (+26.41%) |      768.64 ms →      944.53 ms  (+22.88%) | 
- │ │ │ │   │   └ sddk::wf_trans|pw                                     |      759.49 μs →      738.22 μs   (-2.80%) |    1.01 K →    1.28 K  (+26.41%) |      767.84 ms →      943.45 ms  (+22.87%) | 
- │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.50 ms →        1.38 ms   (-7.74%) |     356   →     451    (+26.69%) |      533.54 ms →      623.58 ms  (+16.88%) | 
- │ │ │ │   │ └ sddk::wf_inner                                          |        1.43 ms →        1.34 ms   (-6.20%) |     356   →     451    (+26.69%) |      507.98 ms →      603.64 ms  (+18.83%) | 
- │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       49.23 ns →       44.65 ns   (-9.31%) |     356   →     451    (+26.69%) |       17.53 μs →       20.14 μs  (+14.89%) | 
- │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        1.26 ms →        1.17 ms   (-7.16%) |     356   →     451    (+26.69%) |      450.03 ms →      529.31 ms  (+17.62%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       38.26 ns →       40.34 ns   (+5.43%) |     356   →     451    (+26.69%) |       13.62 μs →       18.19 μs  (+33.57%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       36.74 ms →       18.02 ms  (-50.94%) |     356   →     451    (+26.69%) |       13.08 s  →        8.13 s   (-37.84%) | 
- │ │ │ │   ├ sirius::residuals                                         |        2.61 ms →        2.83 ms   (+8.79%) |     340   →     431    (+26.76%) |      885.82 ms →        1.22 s   (+37.91%) | 
- │ │ │ │   │ ├ sddk::wf_trans                                          |        1.36 ms →        1.24 ms   (-9.13%) |     337   →     426    (+26.41%) |      458.65 ms →      526.83 ms  (+14.86%) | 
- │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      679.08 μs →      616.89 μs   (-9.16%) |     674   →     852    (+26.41%) |      457.70 ms →      525.59 ms  (+14.83%) | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.15 ms →        1.49 ms  (+29.88%) |     337   →     426    (+26.41%) |      385.87 ms →      633.52 ms  (+64.18%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        7.98 ms →        4.89 ms  (-38.71%) |      54   →     100    (+85.19%) |      430.86 ms →      489.05 ms  (+13.50%) | 
- │ │ │ │     └ sddk::wf_trans                                          |        4.79 ms →        2.74 ms  (-42.77%) |      89   →     175    (+96.63%) |      426.26 ms →      479.70 ms  (+12.54%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |        3.44 ms →        1.92 ms  (-44.20%) |     124   →     250   (+101.61%) |      426.08 ms →      479.35 ms  (+12.50%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      410.21 ns →      390.08 ns   (-4.91%) |      19   →      25    (+31.58%) |        7.79 μs →        9.75 μs  (+25.12%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       19.18 μs →       19.12 μs   (-0.32%) |      19   →      25    (+31.58%) |      364.50 μs →      478.08 μs  (+31.16%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.51 ms →        1.50 ms   (-0.70%) |      19   →      25    (+31.58%) |       28.70 ms →       37.50 ms  (+30.66%) | 
- │ │ ├ sirius::Density::generate                                       |      571.37 ms →      568.61 ms   (-0.48%) |      19   →      25    (+31.58%) |       10.86 s  →       14.22 s   (+30.94%) | 
- │ │ │ ├ sirius::Density::generate_valence                             |      419.10 ms →      407.12 ms   (-2.86%) |      19   →      25    (+31.58%) |        7.96 s  →       10.18 s   (+27.82%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.07 μs →        8.14 μs   (+0.94%) |      19   →      25    (+31.58%) |      153.26 μs →      203.56 μs  (+32.82%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.53 μs →        7.61 μs   (+1.11%) |      19   →      25    (+31.58%) |      142.99 μs →      190.23 μs  (+33.04%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       29.66 ms →       43.47 ms  (+46.55%) |      19   →      25    (+31.58%) |      563.60 ms →        1.09 s   (+92.82%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.65 μs →        8.10 μs   (+5.92%) |      19   →      25    (+31.58%) |      145.28 μs →      202.47 μs  (+39.37%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        4.39 ms →        7.33 ms  (+67.09%) |      19   →      25    (+31.58%) |       83.38 ms →      183.31 ms (+119.86%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       24.22 ms →       35.06 ms  (+44.75%) |      19   →      25    (+31.58%) |      460.22 ms →      876.52 ms  (+90.46%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      512.32 ns →      533.52 ns   (+4.14%) |      19   →      25    (+31.58%) |        9.73 μs →       13.34 μs  (+37.02%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      115.94 ms →      102.29 ms  (-11.78%) |      19   →      25    (+31.58%) |        2.20 s  →        2.56 s   (+16.08%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.45 ms →        2.43 ms   (-0.79%) |      19   →      25    (+31.58%) |       46.47 ms →       60.66 ms  (+30.54%) | 
- │ │ │ │ └ sirius::Density::augment                                    |      233.21 ms →      223.04 ms   (-4.36%) |      19   →      25    (+31.58%) |        4.43 s  →        5.58 s   (+25.84%) | 
- │ │ │ │   └ sirius::Density::generate_rho_aug                         |      233.00 ms →      222.82 ms   (-4.37%) |      19   →      25    (+31.58%) |        4.43 s  →        5.57 s   (+25.83%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      124.44 ms →      134.24 ms   (+7.88%) |      19   →      25    (+31.58%) |        2.36 s  →        3.36 s   (+41.95%) | 
- │ │ │ │ └ sirius::symmetrize_function|fpw                             |      124.43 ms →      134.24 ms   (+7.88%) |      19   →      25    (+31.58%) |        2.36 s  →        3.36 s   (+41.95%) | 
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       39.79 ms →       50.62 ms  (+27.22%) |      19   →      25    (+31.58%) |      755.96 ms →        1.27 s   (+67.39%) | 
- │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       71.34 ms →       70.38 ms   (-1.35%) |      19   →      25    (+31.58%) |        1.36 s  →        1.76 s   (+29.81%) | 
- │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.65 ms →       12.60 ms   (-0.44%) |      19   →      25    (+31.58%) |      240.43 ms →      314.98 ms  (+31.01%) | 
- │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.64 ms →       23.45 ms   (-0.81%) |      19   →      25    (+31.58%) |      449.12 ms →      586.18 ms  (+30.52%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        4.19 ms →        3.80 ms   (-9.37%) |      19   →      25    (+31.58%) |       79.63 ms →       94.97 ms  (+19.26%) | 
- │ │ ├ sirius::Density::mix                                            |      134.41 ms →      138.93 ms   (+3.36%) |      19   →      25    (+31.58%) |        2.55 s  →        3.47 s   (+36.00%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      301.06 μs →      412.15 μs  (+36.90%) |      19   →      25    (+31.58%) |        5.72 ms →       10.30 ms  (+80.13%) | 
- │ │ │ ├ sirius::Periodic_function|inner                               |        5.01 ms →        4.74 ms   (-5.37%) |     229   →     319    (+39.30%) |        1.15 s  →        1.51 s   (+31.82%) | 
- │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.82 ms →        4.62 ms   (-4.17%) |     229   →     319    (+39.30%) |        1.10 s  →        1.47 s   (+33.50%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.82 ms →        4.62 ms   (-4.17%) |     229   →     319    (+39.30%) |        1.10 s  →        1.47 s   (+33.50%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        5.91 ms →        6.27 ms   (+6.06%) |      19   →      25    (+31.58%) |      112.38 ms →      156.84 ms  (+39.56%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.22 ms →        5.52 ms   (+5.66%) |      19   →      25    (+31.58%) |       99.22 ms →      137.94 ms  (+39.03%) | 
- │ │ ├ sirius::Potential::generate                                     |      364.03 ms →      356.44 ms   (-2.09%) |      19   →      25    (+31.58%) |        6.92 s  →        8.91 s   (+28.83%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |       43.76 ms →       36.47 ms  (-16.65%) |      19   →      25    (+31.58%) |      831.45 ms →      911.87 ms   (+9.67%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        3.52 ms →        8.81 ms (+149.93%) |      19   →      25    (+31.58%) |       66.97 ms →      220.25 ms (+228.85%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |        4.87 ms →        4.67 ms   (-4.07%) |      19   →      25    (+31.58%) |       92.49 ms →      116.74 ms  (+26.22%) | 
- │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.63 ms →        4.62 ms   (-0.02%) |      19   →      25    (+31.58%) |       87.88 ms →      115.61 ms  (+31.56%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.62 ms →        4.62 ms   (-0.01%) |      19   →      25    (+31.58%) |       87.86 ms →      115.59 ms  (+31.56%) | 
- │ │ │ ├ sirius::Periodic_function::add                                |      761.03 μs →      749.90 μs   (-1.46%) |      38   →      50    (+31.58%) |       28.92 ms →       37.50 ms  (+29.66%) | 
- │ │ │ ├ sirius::Potential::xc                                         |       45.00 ms →       45.22 ms   (+0.50%) |      19   →      25    (+31.58%) |      854.93 ms →        1.13 s   (+32.24%) | 
- │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       43.80 ms →       44.04 ms   (+0.56%) |      19   →      25    (+31.58%) |      832.12 ms →        1.10 s   (+32.31%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function                          |      685.31 μs →      675.58 μs   (-1.42%) |      38   →      50    (+31.58%) |       26.04 ms →       33.78 ms  (+29.71%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.66 ms →        4.88 ms   (+4.59%) |      19   →      25    (+31.58%) |       88.56 ms →      121.88 ms  (+37.62%) | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.62 ms →        3.14 ms  (-13.07%) |      19   →      25    (+31.58%) |       68.72 ms →       78.60 ms  (+14.38%) | 
- │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.71 ms →      268.69 ms   (-0.01%) |      19   →      25    (+31.58%) |        5.11 s  →        6.72 s   (+31.57%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      321.05 ns →      541.32 ns  (+68.61%) |      19   →      25    (+31.58%) |        6.10 μs →       13.53 μs (+121.85%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |       97.75 ms →       97.35 ms   (-0.41%) |      19   →      25    (+31.58%) |        1.86 s  →        2.43 s   (+31.03%) | 
- │ │ │ └ sirius::symmetrize_function|fpw                               |       97.75 ms →       97.35 ms   (-0.41%) |      19   →      25    (+31.58%) |        1.86 s  →        2.43 s   (+31.03%) | 
- │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.28 ms →       13.28 ms   (+0.01%) |      19   →      25    (+31.58%) |      252.29 ms →      331.99 ms  (+31.59%) | 
- │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       71.22 ms →       70.87 ms   (-0.49%) |      19   →      25    (+31.58%) |        1.35 s  →        1.77 s   (+30.93%) | 
- │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.62 ms →       12.57 ms   (-0.41%) |      19   →      25    (+31.58%) |      239.87 ms →      314.33 ms  (+31.04%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        4.56 ms →        3.54 ms  (-22.35%) |      19   →      25    (+31.58%) |       86.55 ms →       88.43 ms   (+2.17%) | 
- │ │ ├ sirius::Periodic_function|inner                                 |        4.61 ms →        4.80 ms   (+4.26%) |     133   →     175    (+31.58%) |      612.51 ms →      840.25 ms  (+37.18%) | 
- │ │ │ └ sirius::Periodic_function|inner_local                         |        4.57 ms →        4.54 ms   (-0.57%) |     133   →     175    (+31.58%) |      607.85 ms →      795.27 ms  (+30.83%) | 
- │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.57 ms →        4.54 ms   (-0.57%) |     133   →     175    (+31.58%) |      607.76 ms →      795.17 ms  (+30.84%) | 
- │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.95 ms →        4.72 ms   (-4.61%) |      57   →      75    (+31.58%) |      282.20 ms →      354.20 ms  (+25.51%) | 
- │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.94 ms →        4.71 ms   (-4.62%) |      57   →      75    (+31.58%) |      281.73 ms →      353.56 ms  (+25.49%) | 
- │ │ ├ sirius::Periodic_function::integrate                            |        4.54 ms →        4.53 ms   (-0.20%) |      19   →      25    (+31.58%) |       86.26 ms →      113.27 ms  (+31.32%) | 
- │ │ └ sirius::Density::get_magnetisation                              |       77.35 μs →       77.42 μs   (+0.09%) |      19   →      25    (+31.58%) |        1.47 ms →        1.94 ms  (+31.70%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |       72.39 μs →       72.61 μs   (+0.31%) |      19   →      25    (+31.58%) |        1.38 ms →        1.82 ms  (+31.98%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.54 ms →        5.51 ms   (-0.55%) |       2   →       2              |       11.09 ms →       11.03 ms   (-0.55%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.56 ms →        4.65 ms   (+1.85%) |       6   →       6              |       27.38 ms →       27.89 ms   (+1.85%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.56 ms →        4.54 ms   (-0.36%) |       6   →       6              |       27.35 ms →       27.25 ms   (-0.36%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.56 ms →        4.54 ms   (-0.33%) |       6   →       6              |       27.34 ms →       27.25 ms   (-0.33%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.97 ms →        4.74 ms   (-4.68%) |       3   →       3              |       14.92 ms →       14.22 ms   (-4.68%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.91 ms →        4.71 ms   (-4.05%) |       3   →       3              |       14.74 ms →       14.14 ms   (-4.05%) | 
  ├ sirius::Periodic_function|inner                                     |        4.54 ms →        4.79 ms   (+5.36%) |       2   →       2              |        9.09 ms →        9.58 ms   (+5.36%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.54 ms →        4.52 ms   (-0.37%) |       2   →       2              |        9.08 ms →        9.05 ms   (-0.37%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.54 ms →        4.52 ms   (-0.47%) |       2   →       2              |        9.08 ms →        9.04 ms   (-0.47%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.94 ms →        4.73 ms   (-4.20%) |       1   →       1              |        4.94 ms →        4.73 ms   (-4.20%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.93 ms →        4.72 ms   (-4.23%) |       1   →       1              |        4.93 ms →        4.72 ms   (-4.23%) | 
- └ sirius::finalize                                                    |      250.14 ms →      318.07 ms  (+27.16%) |       1   →       1              |      250.14 ms →      318.07 ms  (+27.16%) | 
  ====================================================================================================================================================================================================
```
