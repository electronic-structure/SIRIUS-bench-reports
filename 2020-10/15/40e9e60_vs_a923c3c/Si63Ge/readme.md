# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs 40e9e6046ebfdd2424926f76cb043caae175bee0
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |       72.24 s  →       72.47 s    (+0.32%) |       1   →       1              |       72.24 s  →       72.47 s    (+0.32%) | 
  ├ sirius::initialize                                                  |        3.02 s  →        3.03 s    (+0.32%) |       1   →       1              |        3.02 s  →        3.03 s    (+0.32%) | 
  ├ sirius::Simulation_context::initialize                              |        3.78 s  →        3.80 s    (+0.45%) |       1   →       1              |        3.78 s  →        3.80 s    (+0.45%) | 
- │ ├ sirius::Simulation_context::init_comm                             |      228.92 μs →      388.54 μs  (+69.73%) |       1   →       1              |      228.92 μs →      388.54 μs  (+69.73%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      158.38 ms →      119.42 ms  (-24.60%) |       1   →       1              |      158.38 ms →      119.42 ms  (-24.60%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       70.64 ms →       50.24 ms  (-28.88%) |       2   →       2              |      141.29 ms →      100.48 ms  (-28.88%) | 
- │ │ └ sirius::Unit_cell::update                                       |       17.00 ms →       18.85 ms  (+10.89%) |       1   →       1              |       17.00 ms →       18.85 ms  (+10.89%) | 
- │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.61 ms →        4.97 ms  (+37.80%) |       1   →       1              |        3.61 ms →        4.97 ms  (+37.80%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       13.34 ms →       13.81 ms   (+3.53%) |       1   →       1              |       13.34 ms →       13.81 ms   (+3.53%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       13.27 ms →       13.73 ms   (+3.51%) |       1   →       1              |       13.27 ms →       13.73 ms   (+3.51%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.75 ms →        2.74 ms   (-0.21%) |       1   →       1              |        2.75 ms →        2.74 ms   (-0.21%) | 
- │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      501.73 μs →        1.40 ms (+178.44%) |       1   →       1              |      501.73 μs →        1.40 ms (+178.44%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       15.67 μs →       15.40 μs   (-1.75%) |       1   →       1              |       15.67 μs →       15.40 μs   (-1.75%) | 
  │ └ sirius::Simulation_context::update                                |        3.52 s  →        3.62 s    (+2.91%) |       1   →       1              |        3.52 s  →        3.62 s    (+2.91%) | 
  │   ├ sirius::Unit_cell::update                                       |        6.99 ms →        6.99 ms   (+0.10%) |       1   →       1              |        6.99 ms →        6.99 ms   (+0.10%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.64 ms →        3.66 ms   (+0.43%) |       1   →       1              |        3.64 ms →        3.66 ms   (+0.43%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.28 ms →        3.29 ms   (+0.26%) |       1   →       1              |        3.28 ms →        3.29 ms   (+0.26%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.24 ms →        3.24 ms   (+0.17%) |       1   →       1              |        3.24 ms →        3.24 ms   (+0.17%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.70 ms →        2.69 ms   (-0.27%) |       1   →       1              |        2.70 ms →        2.69 ms   (-0.27%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      496.66 μs →      509.42 μs   (+2.57%) |       1   →       1              |      496.66 μs →      509.42 μs   (+2.57%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       14.10 μs →       13.94 μs   (-1.09%) |       1   →       1              |       14.10 μs →       13.94 μs   (-1.09%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      213.82 ms →      213.09 ms   (-0.34%) |       2   →       2              |      427.64 ms →      426.18 ms   (-0.34%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.16 ms →       15.31 ms   (+0.98%) |       2   →       2              |       30.32 ms →       30.62 ms   (+0.98%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.30 ms →       13.23 ms   (-0.46%) |       1   →       1              |       13.30 ms →       13.23 ms   (-0.46%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.29 ms →       56.36 ms   (+0.13%) |       2   →       2              |      112.57 ms →      112.72 ms   (+0.13%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.16 ms →       45.09 ms   (-0.16%) |       2   →       2              |       90.33 ms →       90.18 ms   (-0.16%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.51 ms →       60.36 ms   (-0.25%) |       4   →       4              |      242.05 ms →      241.44 ms   (-0.25%) | 
  │   ├ sddk::Gvec::init                                                |       93.85 ms →       95.23 ms   (+1.46%) |       2   →       2              |      187.71 ms →      190.45 ms   (+1.46%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       70.24 ms →       71.04 ms   (+1.13%) |       2   →       2              |      140.49 ms →      142.08 ms   (+1.13%) | 
  │   ├ sddk::Gvec_shells                                               |       92.23 ms →       94.62 ms   (+2.60%) |       1   →       1              |       92.23 ms →       94.62 ms   (+2.60%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.95 ms →        1.96 ms   (+0.68%) |       1   →       1              |        1.95 ms →        1.96 ms   (+0.68%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      606.70 ms →      663.52 ms   (+9.36%) |       2   →       2              |        1.21 s  →        1.33 s    (+9.36%) | 
+ ├ sirius::K_point_set::create_k_mesh                                  |      144.65 ms →       87.66 ms  (-39.40%) |       1   →       1              |      144.65 ms →       87.66 ms  (-39.40%) | 
+ │ ├ sirius::K_point::K_point                                          |        1.68 μs →        1.17 μs  (-30.38%) |       4   →       4              |        6.74 μs →        4.69 μs  (-30.38%) | 
+ │ └ sirius::K_point_set::initialize                                   |      144.57 ms →       87.58 ms  (-39.42%) |       1   →       1              |      144.57 ms →       87.58 ms  (-39.42%) | 
  │   └ sirius::K_point::initialize                                     |       28.18 ms →       29.53 ms   (+4.79%) |       1   →       1              |       28.18 ms →       29.53 ms   (+4.79%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       11.12 ms →       11.56 ms   (+3.98%) |       1   →       1              |       11.12 ms →       11.56 ms   (+3.98%) | 
  │     │ └ sddk::Gvec::init                                            |        4.99 ms →        5.38 ms   (+7.93%) |       1   →       1              |        4.99 ms →        5.38 ms   (+7.93%) | 
+ │     ├ sddk::matrix_storage::matrix_storage                          |       11.64 μs →        8.16 μs  (-29.92%) |       1   →       1              |       11.64 μs →        8.16 μs  (-29.92%) | 
  │     └ sirius::K_point::update                                       |       14.19 ms →       14.95 ms   (+5.39%) |       1   →       1              |       14.19 ms →       14.95 ms   (+5.39%) | 
  │       └ sirius::Beta_projectors                                     |       10.20 ms →       10.58 ms   (+3.70%) |       1   →       1              |       10.20 ms →       10.58 ms   (+3.70%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.28 ms →        8.73 ms   (+5.44%) |       1   →       1              |        8.28 ms →        8.73 ms   (+5.44%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.59 ms →        2.54 ms   (-2.03%) |       2   →       2              |        5.18 ms →        5.07 ms   (-2.03%) | 
  ├ sirius::Potential                                                   |       55.79 ms →       50.23 ms   (-9.97%) |       1   →       1              |       55.79 ms →       50.23 ms   (-9.97%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.91 ms →        2.89 ms   (-0.53%) |       6   →       6              |       17.44 ms →       17.35 ms   (-0.53%) | 
+ │ └ sirius::Potential::update                                         |       37.73 ms →       32.27 ms  (-14.46%) |       1   →       1              |       37.73 ms →       32.27 ms  (-14.46%) | 
+ │   └ sirius::Potential::generate_local_potential                     |       37.33 ms →       31.87 ms  (-14.63%) |       1   →       1              |       37.33 ms →       31.87 ms  (-14.63%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       32.51 ms →       26.90 ms  (-17.26%) |       1   →       1              |       32.51 ms →       26.90 ms  (-17.26%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        4.24 ms →        4.41 ms   (+3.77%) |       1   →       1              |        4.24 ms →        4.41 ms   (+3.77%) | 
+ ├ sirius::Density                                                     |       42.46 ms →       37.97 ms  (-10.56%) |       1   →       1              |       42.46 ms →       37.97 ms  (-10.56%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.84 ms →        2.82 ms   (-0.78%) |       2   →       2              |        5.68 ms →        5.63 ms   (-0.78%) | 
+ │ └ sirius::Density::update                                           |       36.64 ms →       32.20 ms  (-12.12%) |       1   →       1              |       36.64 ms →       32.20 ms  (-12.12%) | 
+ │   └ sirius::Density::generate_pseudo_core_charge_density            |       36.32 ms →       31.93 ms  (-12.10%) |       1   →       1              |       36.32 ms →       31.93 ms  (-12.10%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |       77.11 μs →       77.99 μs   (+1.14%) |       1   →       1              |       77.11 μs →       77.99 μs   (+1.14%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       33.05 ms →       28.15 ms  (-14.83%) |       1   →       1              |       33.05 ms →       28.15 ms  (-14.83%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        2.85 ms →        3.34 ms  (+17.16%) |       1   →       1              |        2.85 ms →        3.34 ms  (+17.16%) | 
+ ├ sirius::Density::initial_density                                    |       65.25 ms →       57.32 ms  (-12.15%) |       1   →       1              |       65.25 ms →       57.32 ms  (-12.15%) | 
+ │ ├ sirius::Simulation_context::make_periodic_function                |       37.62 ms →       29.36 ms  (-21.97%) |       1   →       1              |       37.62 ms →       29.36 ms  (-21.97%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.35 ms →        4.60 ms   (+5.75%) |       2   →       2              |        8.70 ms →        9.20 ms   (+5.75%) | 
  │ └ sirius::Periodic_function::integrate                              |        5.28 ms →        5.35 ms   (+1.39%) |       1   →       1              |        5.28 ms →        5.35 ms   (+1.39%) | 
  ├ sirius::Potential::generate                                         |      373.67 ms →      366.23 ms   (-1.99%) |       1   →       1              |      373.67 ms →      366.23 ms   (-1.99%) | 
+ │ ├ sirius::Potential::poisson                                        |       45.26 ms →       36.94 ms  (-18.39%) |       1   →       1              |       45.26 ms →       36.94 ms  (-18.39%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.88 ms →        3.32 ms  (+15.32%) |       1   →       1              |        2.88 ms →        3.32 ms  (+15.32%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        5.48 ms →        5.09 ms   (-7.10%) |       1   →       1              |        5.48 ms →        5.09 ms   (-7.10%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.63 ms →        4.84 ms   (+4.52%) |       1   →       1              |        4.63 ms →        4.84 ms   (+4.52%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.62 ms →        4.83 ms   (+4.52%) |       1   →       1              |        4.62 ms →        4.83 ms   (+4.52%) | 
  │ ├ sirius::Periodic_function::add                                    |      798.18 μs →      785.73 μs   (-1.56%) |       2   →       2              |        1.60 ms →        1.57 ms   (-1.56%) | 
  │ ├ sirius::Potential::xc                                             |       52.45 ms →       53.01 ms   (+1.07%) |       1   →       1              |       52.45 ms →       53.01 ms   (+1.07%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.28 ms →       51.80 ms   (+1.03%) |       1   →       1              |       51.28 ms →       51.80 ms   (+1.03%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.56 ms →        2.53 ms   (-1.09%) |       2   →       2              |        5.13 ms →        5.07 ms   (-1.09%) | 
- │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.00 ms →        4.61 ms  (+15.13%) |       1   →       1              |        4.00 ms →        4.61 ms  (+15.13%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.88 ms →        3.04 ms  (-21.54%) |       1   →       1              |        3.88 ms →        3.04 ms  (-21.54%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      269.13 ms →      270.25 ms   (+0.41%) |       1   →       1              |      269.13 ms →      270.25 ms   (+0.41%) | 
- │ └ sirius::Potential::generate_PAW_effective_potential               |      254.00 ns →      340.00 ns  (+33.86%) |       1   →       1              |      254.00 ns →      340.00 ns  (+33.86%) | 
+ ├ sirius::Hamiltonian0                                                |        7.58 ms →        6.57 ms  (-13.42%) |       1   →       1              |        7.58 ms →        6.57 ms  (-13.42%) | 
+ │ ├ sirius::Local_operator                                            |        7.12 ms →        6.06 ms  (-14.98%) |       1   →       1              |        7.12 ms →        6.06 ms  (-14.98%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.75 ms →        2.74 ms   (-0.12%) |       1   →       1              |        2.75 ms →        2.74 ms   (-0.12%) | 
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        3.34 ms →        2.53 ms  (-24.28%) |       1   →       1              |        3.34 ms →        2.53 ms  (-24.28%) | 
+ │ ├ sirius::Non_local_operator                                        |      101.68 μs →       75.86 μs  (-25.39%) |       2   →       2              |      203.36 μs →      151.73 μs  (-25.39%) | 
- │ ├ sirius::D_operator::initialize                                    |      101.04 μs →      148.15 μs  (+46.63%) |       1   →       1              |      101.04 μs →      148.15 μs  (+46.63%) | 
- │ └ sirius::Q_operator::initialize                                    |       88.12 μs →      126.63 μs  (+43.69%) |       1   →       1              |       88.12 μs →      126.63 μs  (+43.69%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.28 s  →        1.27 s    (-1.02%) |       1   →       1              |        1.28 s  →        1.27 s    (-1.02%) | 
+ │ ├ sirius::Hamiltonian_k                                             |       57.42 ms →       48.09 ms  (-16.24%) |       1   →       1              |       57.42 ms →       48.09 ms  (-16.24%) | 
- │ │ ├ sirius::Local_operator::prepare_k                               |      214.06 μs →      394.61 μs  (+84.35%) |       1   →       1              |      214.06 μs →      394.61 μs  (+84.35%) | 
+ │ │ └ sirius::Beta_projectors_base::prepare                           |       57.20 ms →       47.69 ms  (-16.62%) |       1   →       1              |       57.20 ms →       47.69 ms  (-16.62%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.23 s  →        1.22 s    (-0.31%) |       1   →       1              |        1.23 s  →        1.22 s    (-0.31%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       75.87 ms →       74.45 ms   (-1.87%) |       4   →       4              |      303.49 ms →      297.81 ms   (-1.87%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       46.85 ms →       44.48 ms   (-5.06%) |       1   →       1              |       46.85 ms →       44.48 ms   (-5.06%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        8.01 ms →        7.67 ms   (-4.26%) |       1   →       1              |        8.01 ms →        7.67 ms   (-4.26%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      336.86 ms →      335.33 ms   (-0.45%) |       1   →       1              |      336.86 ms →      335.33 ms   (-0.45%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      248.27 ms →      247.70 ms   (-0.23%) |       1   →       1              |      248.27 ms →      247.70 ms   (-0.23%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.85 μs →        4.13 μs   (+7.30%) |       1   →       1              |        3.85 μs →        4.13 μs   (+7.30%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.89 μs →        3.12 μs   (+7.85%) |       1   →       1              |        2.89 μs →        3.12 μs   (+7.85%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      439.00 ns →      443.00 ns   (+0.91%) |       1   →       1              |      439.00 ns →      443.00 ns   (+0.91%) | 
- │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      513.00 ns →      677.00 ns  (+31.97%) |       1   →       1              |      513.00 ns →      677.00 ns  (+31.97%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.29 ms →        3.15 ms   (-4.11%) |       1   →       1              |        3.29 ms →        3.15 ms   (-4.11%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.29 ms →       21.25 ms   (-0.15%) |       1   →       1              |       21.29 ms →       21.25 ms   (-0.15%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       31.99 ms →       31.59 ms   (-1.24%) |       2   →       2              |       63.97 ms →       63.18 ms   (-1.24%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.72 ms →       14.83 ms   (+0.69%) |       2   →       2              |       29.45 ms →       29.65 ms   (+0.69%) | 
  │ │ │ └ sddk::wf_inner                                                |       14.51 ms →       14.61 ms   (+0.69%) |       2   →       2              |       29.03 ms →       29.23 ms   (+0.69%) | 
  │ │ │   ├ sddk::wf_inner|scale                                        |       21.00 ns →       22.50 ns   (+7.14%) |       2   →       2              |       42.00 ns →       45.00 ns   (+7.14%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       14.36 ms →       14.48 ms   (+0.80%) |       2   →       2              |       28.73 ms →       28.96 ms   (+0.80%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       22.50 ns →       28.50 ns  (+26.67%) |       2   →       2              |       45.00 ns →       57.00 ns  (+26.67%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      230.56 ms →      230.16 ms   (-0.17%) |       1   →       1              |      230.56 ms →      230.16 ms   (-0.17%) | 
  │ │ └ sddk::wf_trans                                                  |        2.63 ms →        2.60 ms   (-1.01%) |       1   →       1              |        2.63 ms →        2.60 ms   (-1.01%) | 
  │ │   └ sddk::wf_trans|pw                                             |        2.62 ms →        2.60 ms   (-1.04%) |       1   →       1              |        2.62 ms →        2.60 ms   (-1.04%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      808.00 ns →      399.00 ns  (-50.62%) |       1   →       1              |      808.00 ns →      399.00 ns  (-50.62%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |       62.33 s  →       62.64 s    (+0.50%) |       1   →       1              |       62.33 s  →       62.64 s    (+0.50%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.45 ms →        2.45 ms   (-0.04%) |      19   →      19              |       46.55 ms →       46.54 ms   (-0.04%) | 
! │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.26 s  →        2.97 s    (-8.95%) |      19   →      21    (+10.53%) |       62.02 s  →       62.42 s    (+0.63%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        5.67 ms →        5.66 ms   (-0.23%) |      19   →      21    (+10.53%) |      107.79 ms →      118.87 ms  (+10.28%) | 
- │ │ │ ├ sirius::Local_operator                                        |        4.95 ms →        4.96 ms   (+0.07%) |      19   →      21    (+10.53%) |       94.11 ms →      104.09 ms  (+10.60%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function                            |      556.76 μs →      566.28 μs   (+1.71%) |      19   →      21    (+10.53%) |       10.58 ms →       11.89 ms  (+12.42%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.27 ms →        3.31 ms   (+1.01%) |      19   →      21    (+10.53%) |       62.18 ms →       69.43 ms  (+11.65%) | 
! │ │ │ ├ sirius::Non_local_operator                                    |      214.95 μs →      206.73 μs   (-3.82%) |      38   →      42    (+10.53%) |        8.17 ms →        8.68 ms   (+6.30%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |      119.08 μs →      121.23 μs   (+1.81%) |      19   →      21    (+10.53%) |        2.26 ms →        2.55 ms  (+12.52%) | 
! │ │ │ └ sirius::Q_operator::initialize                                |       90.68 μs →       90.04 μs   (-0.70%) |      19   →      21    (+10.53%) |        1.72 ms →        1.89 ms   (+9.75%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.03 s  →        1.76 s   (-13.61%) |      19   →      21    (+10.53%) |       38.66 s  →       36.91 s    (-4.51%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      220.27 μs →      241.30 μs   (+9.54%) |      19   →      21    (+10.53%) |        4.19 ms →        5.07 ms  (+21.07%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      211.63 μs →      232.85 μs  (+10.03%) |      19   →      21    (+10.53%) |        4.02 ms →        4.89 ms  (+21.61%) | 
! │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        6.33 μs →        6.18 μs   (-2.38%) |      19   →      21    (+10.53%) |      120.23 μs →      129.72 μs   (+7.89%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.97 s  →        1.64 s   (-17.19%) |      19   →      21    (+10.53%) |       37.52 s  →       34.34 s    (-8.48%) | 
! │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       77.05 ms →       74.55 ms   (-3.24%) |      19   →      21    (+10.53%) |        1.46 s  →        1.57 s    (+6.94%) | 
! │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.99 ms →        7.29 ms   (-8.78%) |     114   →     126    (+10.53%) |      911.12 ms →      918.62 ms   (+0.82%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       19.00 ms →       15.67 ms  (-17.50%) |      19   →      21    (+10.53%) |      360.95 ms →      329.14 ms   (-8.81%) | 
- │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      456.70 μs →      479.27 μs   (+4.94%) |      19   →      21    (+10.53%) |        8.68 ms →       10.06 ms  (+15.99%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        8.83 ms →        7.17 ms  (-18.80%) |      38   →      42    (+10.53%) |      335.45 ms →      301.07 ms  (-10.25%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.87 s  →        1.54 s   (-17.86%) |      19   →      21    (+10.53%) |       35.54 s  →       32.26 s    (-9.21%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       54.78 ms →       59.34 ms   (+8.32%) |     356   →     361     (+1.40%) |       19.50 s  →       21.42 s    (+9.84%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       30.38 ms →       36.47 ms  (+20.05%) |     356   →     361     (+1.40%) |       10.81 s  →       13.16 s   (+21.74%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.05 μs →        2.20 μs   (+7.24%) |     356   →     361     (+1.40%) |      730.92 μs →      794.85 μs   (+8.75%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.75 μs →        1.84 μs   (+5.51%) |     356   →     361     (+1.40%) |      621.98 μs →      665.47 μs   (+6.99%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      464.37 ns →      490.57 ns   (+5.64%) |     356   →     361     (+1.40%) |      165.32 μs →      177.09 μs   (+7.12%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      668.10 ns →      657.25 ns   (-1.62%) |     356   →     361     (+1.40%) |      237.84 μs →      237.27 μs   (-0.24%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        3.18 ms →        3.20 ms   (+0.79%) |     356   →     361     (+1.40%) |        1.13 s  →        1.16 s    (+2.21%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.21 ms →        3.28 ms   (+1.92%) |     356   →     361     (+1.40%) |        1.14 s  →        1.18 s    (+3.35%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        9.00 ms →        8.19 ms   (-9.00%) |     712   →     722     (+1.40%) |        6.40 s  →        5.91 s    (-7.72%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |        6.03 ms →        6.14 ms   (+1.85%) |     356   →     361     (+1.40%) |        2.15 s  →        2.22 s    (+3.28%) | 
- │ │ │ │   │ ├ sddk::wf_inner                                          |      999.24 μs →        1.13 ms  (+13.40%) |     693   →     701     (+1.15%) |      692.47 ms →      794.36 ms  (+14.71%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       56.22 ns →       40.91 ns  (-27.23%) |     693   →     701     (+1.15%) |       38.96 μs →       28.68 μs  (-26.39%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |      837.89 μs →      968.88 μs  (+15.63%) |     693   →     701     (+1.15%) |      580.66 ms →      679.18 ms  (+16.97%) | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       46.27 ns →       48.44 ns   (+4.70%) |     693   →     701     (+1.15%) |       32.06 μs →       33.96 μs   (+5.91%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      133.79 μs →      156.44 μs  (+16.93%) |     356   →     361     (+1.40%) |       47.63 ms →       56.48 ms  (+18.58%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        1.71 ms →        1.66 ms   (-2.97%) |     356   →     361     (+1.40%) |      608.83 ms →      599.03 ms   (-1.61%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |        2.36 ms →        2.25 ms   (-4.69%) |     337   →     340     (+0.89%) |      795.07 ms →      764.52 ms   (-3.84%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |      785.57 μs →      748.71 μs   (-4.69%) |    1.01 K →    1.02 K   (+0.89%) |      794.21 ms →      763.69 ms   (-3.84%) | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.38 ms →        1.23 ms  (-11.47%) |     356   →     361     (+1.40%) |      492.74 ms →      442.33 ms  (-10.23%) | 
+ │ │ │ │   │ └ sddk::wf_inner                                          |        1.31 ms →        1.18 ms  (-10.04%) |     356   →     361     (+1.40%) |      466.47 ms →      425.51 ms   (-8.78%) | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       41.29 ns →       43.95 ns   (+6.44%) |     356   →     361     (+1.40%) |       14.70 μs →       15.86 μs   (+7.94%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        1.15 ms →        1.01 ms  (-11.64%) |     356   →     361     (+1.40%) |      408.42 ms →      365.94 ms  (-10.40%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       39.11 ns →       43.08 ns  (+10.16%) |     356   →     361     (+1.40%) |       13.92 μs →       15.55 μs  (+11.71%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       33.93 ms →       18.79 ms  (-44.62%) |     356   →     361     (+1.40%) |       12.08 s  →        6.78 s   (-43.84%) | 
  │ │ │ │   ├ sirius::residuals                                         |        2.76 ms →        2.82 ms   (+2.08%) |     340   →     346     (+1.76%) |      938.79 ms →      975.19 ms   (+3.88%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |        1.37 ms →        1.24 ms   (-9.84%) |     337   →     342     (+1.48%) |      461.98 ms →      422.69 ms   (-8.50%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      683.99 μs →      616.58 μs   (-9.86%) |     674   →     684     (+1.48%) |      461.01 ms →      421.74 ms   (-8.52%) | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.28 ms →        1.50 ms  (+17.65%) |     337   →     342     (+1.48%) |      431.01 ms →      514.59 ms  (+19.39%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        6.90 ms →        4.65 ms  (-32.65%) |      54   →      90    (+66.67%) |      372.50 ms →      418.14 ms  (+12.25%) | 
- │ │ │ │     └ sddk::wf_trans                                          |        4.13 ms →        2.58 ms  (-37.66%) |      89   →     159    (+78.65%) |      367.89 ms →      409.70 ms  (+11.36%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |        2.97 ms →        1.80 ms  (-39.45%) |     124   →     228    (+83.87%) |      367.71 ms →      409.40 ms  (+11.34%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      388.26 ns →      535.71 ns  (+37.98%) |      19   →      21    (+10.53%) |        7.38 μs →       11.25 μs  (+52.50%) | 
! │ │ │ └ sirius::K_point_set::sync_band_energies                       |       20.36 μs →       19.83 μs   (-2.61%) |      19   →      21    (+10.53%) |      386.91 μs →      416.47 μs   (+7.64%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.53 ms →        1.54 ms   (+1.27%) |      19   →      21    (+10.53%) |       28.98 ms →       32.44 ms  (+11.93%) | 
! │ │ ├ sirius::Density::generate                                       |      571.59 ms →      562.78 ms   (-1.54%) |      19   →      21    (+10.53%) |       10.86 s  →       11.82 s    (+8.82%) | 
! │ │ │ ├ sirius::Density::generate_valence                             |      393.60 ms →      386.37 ms   (-1.84%) |      19   →      21    (+10.53%) |        7.48 s  →        8.11 s    (+8.50%) | 
! │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.56 μs →        8.20 μs   (-4.15%) |      19   →      21    (+10.53%) |      162.64 μs →      172.29 μs   (+5.93%) | 
! │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.97 μs →        7.62 μs   (-4.31%) |      19   →      21    (+10.53%) |      151.40 μs →      160.12 μs   (+5.76%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       35.39 ms →       44.52 ms  (+25.79%) |      19   →      21    (+10.53%) |      672.48 ms →      934.96 ms  (+39.03%) | 
! │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        8.26 μs →        7.98 μs   (-3.31%) |      19   →      21    (+10.53%) |      156.87 μs →      167.65 μs   (+6.87%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        5.78 ms →       23.70 ms (+309.89%) |      19   →      21    (+10.53%) |      109.87 ms →      497.74 ms (+353.04%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       28.56 ms →       19.77 ms  (-30.80%) |      19   →      21    (+10.53%) |      542.71 ms →      415.10 ms  (-23.51%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      514.68 ns →      994.33 ns  (+93.19%) |      19   →      21    (+10.53%) |        9.78 μs →       20.88 μs (+113.53%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      110.80 ms →       95.10 ms  (-14.17%) |      19   →      21    (+10.53%) |        2.11 s  →        2.00 s    (-5.13%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.92 ms →        1.98 ms   (+3.46%) |      19   →      21    (+10.53%) |       36.45 ms →       41.68 ms  (+14.35%) | 
! │ │ │ │ └ sirius::Density::augment                                    |      204.70 ms →      201.99 ms   (-1.32%) |      19   →      21    (+10.53%) |        3.89 s  →        4.24 s    (+9.06%) | 
! │ │ │ │   └ sirius::Density::generate_rho_aug                         |      204.47 ms →      201.76 ms   (-1.32%) |      19   →      21    (+10.53%) |        3.88 s  →        4.24 s    (+9.06%) | 
! │ │ │ ├ sirius::Field4D::symmetrize                                   |      148.84 ms →      147.66 ms   (-0.79%) |      19   →      21    (+10.53%) |        2.83 s  →        3.10 s    (+9.65%) | 
! │ │ │ │ └ sirius::symmetrize_function|fpw                             |      148.84 ms →      147.66 ms   (-0.79%) |      19   →      21    (+10.53%) |        2.83 s  →        3.10 s    (+9.65%) | 
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       65.61 ms →       66.62 ms   (+1.55%) |      19   →      21    (+10.53%) |        1.25 s  →        1.40 s   (+12.24%) | 
! │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       69.90 ms →       67.80 ms   (-3.00%) |      19   →      21    (+10.53%) |        1.33 s  →        1.42 s    (+7.21%) | 
! │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.67 ms →       12.59 ms   (-0.67%) |      19   →      21    (+10.53%) |      240.74 ms →      264.31 ms   (+9.79%) | 
! │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.85 ms →       23.66 ms   (-0.78%) |      19   →      21    (+10.53%) |      453.07 ms →      496.88 ms   (+9.67%) | 
! │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        5.30 ms →        5.08 ms   (-4.24%) |      19   →      21    (+10.53%) |      100.74 ms →      106.62 ms   (+5.84%) | 
- │ │ ├ sirius::Density::mix                                            |      132.70 ms →      135.50 ms   (+2.11%) |      19   →      21    (+10.53%) |        2.52 s  →        2.85 s   (+12.86%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      967.10 μs →      825.57 μs  (-14.63%) |      19   →      21    (+10.53%) |       18.37 ms →       17.34 ms   (-5.65%) | 
- │ │ │ ├ sirius::Periodic_function|inner                               |        4.85 ms →        4.87 ms   (+0.54%) |     229   →     259    (+13.10%) |        1.11 s  →        1.26 s   (+13.71%) | 
- │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.81 ms →        4.81 ms   (+0.07%) |     229   →     259    (+13.10%) |        1.10 s  →        1.25 s   (+13.18%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.81 ms →        4.81 ms   (+0.07%) |     229   →     259    (+13.10%) |        1.10 s  →        1.25 s   (+13.18%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        4.13 ms →        5.72 ms  (+38.60%) |      19   →      21    (+10.53%) |       78.45 ms →      120.19 ms  (+53.19%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        3.51 ms →        4.96 ms  (+41.34%) |      19   →      21    (+10.53%) |       66.66 ms →      104.14 ms  (+56.22%) | 
! │ │ ├ sirius::Potential::generate                                     |      365.68 ms →      357.81 ms   (-2.15%) |      19   →      21    (+10.53%) |        6.95 s  →        7.51 s    (+8.15%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |       45.43 ms →       37.06 ms  (-18.43%) |      19   →      21    (+10.53%) |      863.26 ms →      778.26 ms   (-9.85%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        3.08 ms →        3.31 ms   (+7.60%) |      19   →      21    (+10.53%) |       58.44 ms →       69.50 ms  (+18.93%) | 
! │ │ │ │ └ sirius::Periodic_function|inner                             |        5.20 ms →        5.09 ms   (-2.14%) |      19   →      21    (+10.53%) |       98.89 ms →      106.95 ms   (+8.16%) | 
- │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.64 ms →        4.83 ms   (+4.22%) |      19   →      21    (+10.53%) |       88.10 ms →      101.49 ms  (+15.19%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.64 ms →        4.83 ms   (+4.21%) |      19   →      21    (+10.53%) |       88.09 ms →      101.46 ms  (+15.18%) | 
- │ │ │ ├ sirius::Periodic_function::add                                |      772.77 μs →      780.01 μs   (+0.94%) |      38   →      42    (+10.53%) |       29.37 ms →       32.76 ms  (+11.56%) | 
- │ │ │ ├ sirius::Potential::xc                                         |       44.52 ms →       45.33 ms   (+1.80%) |      19   →      21    (+10.53%) |      845.95 ms →      951.86 ms  (+12.52%) | 
- │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       43.35 ms →       44.14 ms   (+1.83%) |      19   →      21    (+10.53%) |      823.61 ms →      926.93 ms  (+12.55%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function                          |      687.10 μs →      686.98 μs   (-0.02%) |      38   →      42    (+10.53%) |       26.11 ms →       28.85 ms  (+10.51%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        3.96 ms →        4.90 ms  (+23.83%) |      19   →      21    (+10.53%) |       75.23 ms →      102.97 ms  (+36.86%) | 
! │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.71 ms →        3.37 ms   (-9.23%) |      19   →      21    (+10.53%) |       70.48 ms →       70.70 ms   (+0.32%) | 
- │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      269.04 ms →      269.07 ms   (+0.01%) |      19   →      21    (+10.53%) |        5.11 s  →        5.65 s   (+10.54%) | 
! │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      289.11 ns →      262.29 ns   (-9.28%) |      19   →      21    (+10.53%) |        5.49 μs →        5.51 μs   (+0.27%) | 
! │ │ ├ sirius::Field4D::symmetrize                                     |       96.13 ms →       94.24 ms   (-1.97%) |      19   →      21    (+10.53%) |        1.83 s  →        1.98 s    (+8.35%) | 
! │ │ │ └ sirius::symmetrize_function|fpw                               |       96.13 ms →       94.24 ms   (-1.97%) |      19   →      21    (+10.53%) |        1.83 s  →        1.98 s    (+8.35%) | 
- │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.27 ms →       13.52 ms   (+1.87%) |      19   →      21    (+10.53%) |      252.20 ms →      283.94 ms  (+12.59%) | 
! │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       69.61 ms →       67.55 ms   (-2.96%) |      19   →      21    (+10.53%) |        1.32 s  →        1.42 s    (+7.25%) | 
! │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.60 ms →       12.54 ms   (-0.53%) |      19   →      21    (+10.53%) |      239.46 ms →      263.26 ms   (+9.94%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.81 ms →        4.52 ms  (+18.76%) |      19   →      21    (+10.53%) |       72.35 ms →       94.97 ms  (+31.26%) | 
- │ │ ├ sirius::Periodic_function|inner                                 |        4.71 ms →        4.78 ms   (+1.53%) |     133   →     147    (+10.53%) |      626.50 ms →      703.02 ms  (+12.21%) | 
- │ │ │ └ sirius::Periodic_function|inner_local                         |        4.57 ms →        4.75 ms   (+3.88%) |     133   →     147    (+10.53%) |      607.94 ms →      697.98 ms  (+14.81%) | 
- │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.57 ms →        4.75 ms   (+3.87%) |     133   →     147    (+10.53%) |      607.87 ms →      697.88 ms  (+14.81%) | 
! │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.95 ms →        4.73 ms   (-4.59%) |      57   →      63    (+10.53%) |      282.42 ms →      297.82 ms   (+5.45%) | 
! │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.94 ms →        4.72 ms   (-4.40%) |      57   →      63    (+10.53%) |      281.40 ms →      297.35 ms   (+5.67%) | 
- │ │ ├ sirius::Periodic_function::integrate                            |        4.54 ms →        4.53 ms   (-0.20%) |      19   →      21    (+10.53%) |       86.26 ms →       95.15 ms  (+10.30%) | 
- │ │ └ sirius::Density::get_magnetisation                              |       76.96 μs →       77.56 μs   (+0.78%) |      19   →      21    (+10.53%) |        1.46 ms →        1.63 ms  (+11.39%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |       71.94 μs →       72.43 μs   (+0.69%) |      19   →      21    (+10.53%) |        1.37 ms →        1.52 ms  (+11.29%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.32 ms →        5.59 ms   (+5.16%) |       2   →       2              |       10.64 ms →       11.19 ms   (+5.16%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.67 ms →        4.84 ms   (+3.59%) |       6   →       6              |       28.02 ms →       29.03 ms   (+3.59%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.67 ms →        4.83 ms   (+3.39%) |       6   →       6              |       28.00 ms →       28.95 ms   (+3.39%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.67 ms →        4.83 ms   (+3.42%) |       6   →       6              |       27.99 ms →       28.95 ms   (+3.42%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        5.04 ms →        4.87 ms   (-3.28%) |       3   →       3              |       15.11 ms →       14.61 ms   (-3.28%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        5.03 ms →        4.83 ms   (-4.07%) |       3   →       3              |       15.09 ms →       14.48 ms   (-4.07%) | 
  ├ sirius::Periodic_function|inner                                     |        4.57 ms →        4.84 ms   (+5.84%) |       2   →       2              |        9.14 ms →        9.67 ms   (+5.84%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.56 ms →        4.82 ms   (+5.66%) |       2   →       2              |        9.13 ms →        9.65 ms   (+5.66%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.56 ms →        4.82 ms   (+5.66%) |       2   →       2              |        9.13 ms →        9.65 ms   (+5.66%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.92 ms →        4.83 ms   (-1.82%) |       1   →       1              |        4.92 ms →        4.83 ms   (-1.82%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.91 ms →        4.82 ms   (-1.69%) |       1   →       1              |        4.91 ms →        4.82 ms   (-1.69%) | 
+ └ sirius::finalize                                                    |      513.30 ms →      157.27 ms  (-69.36%) |       1   →       1              |      513.30 ms →      157.27 ms  (-69.36%) | 
  ====================================================================================================================================================================================================
```
