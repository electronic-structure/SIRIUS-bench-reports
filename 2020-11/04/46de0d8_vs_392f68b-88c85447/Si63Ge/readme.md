# Benchmark 392f68b5626168134a99cd6d4a3cc40b87322cb7 vs 46de0d896d343d7768c9da756627e739ed0717b7
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
- sirius                                                                |       72.48 s  →     1039.70 s  (+1334.52%) |       1   →       1              |       72.48 s  →     1039.70 s  (+1334.52%) | 
  ├ sirius::initialize                                                  |        2.85 s  →        2.81 s    (-1.45%) |       1   →       1              |        2.85 s  →        2.81 s    (-1.45%) | 
- ├ sirius::Simulation_context::initialize                              |        3.62 s  →        3.98 s   (+10.03%) |       1   →       1              |        3.62 s  →        3.98 s   (+10.03%) | 
- │ ├ sirius::Simulation_context::init_comm                             |      867.73 μs →       12.06 ms (+1290.24%) |       1   →       1              |      867.73 μs →       12.06 ms (+1290.24%) | 
  │ ├ sirius::Unit_cell::initialize                                     |      169.66 ms →      161.44 ms   (-4.85%) |       1   →       1              |      169.66 ms →      161.44 ms   (-4.85%) | 
  │ │ ├ sirius::Atom_type::init                                         |       75.52 ms →       72.17 ms   (-4.44%) |       2   →       2              |      151.05 ms →      144.34 ms   (-4.44%) | 
  │ │ └ sirius::Unit_cell::update                                       |       18.53 ms →       17.02 ms   (-8.18%) |       1   →       1              |       18.53 ms →       17.02 ms   (-8.18%) | 
- │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        5.02 ms →        6.59 ms  (+31.16%) |       1   →       1              |        5.02 ms →        6.59 ms  (+31.16%) | 
+ │ │   └ sirius::Unit_cell::get_symmetry                               |       13.44 ms →       10.38 ms  (-22.76%) |       1   →       1              |       13.44 ms →       10.38 ms  (-22.76%) | 
+ │ │     └ sirius::Unit_cell_symmetry                                  |       13.37 ms →       10.31 ms  (-22.86%) |       1   →       1              |       13.37 ms →       10.31 ms  (-22.86%) | 
+ │ │       ├ sirius::Unit_cell_symmetry|spg                            |        3.98 ms →        2.75 ms  (-31.09%) |       1   →       1              |        3.98 ms →        2.75 ms  (-31.09%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      519.12 μs →      508.09 μs   (-2.13%) |       1   →       1              |      519.12 μs →      508.09 μs   (-2.13%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       16.24 μs →       16.65 μs   (+2.52%) |       1   →       1              |       16.24 μs →       16.65 μs   (+2.52%) | 
- │ └ sirius::Simulation_context::update                                |        3.23 s  →        3.76 s   (+16.25%) |       1   →       1              |        3.23 s  →        3.76 s   (+16.25%) | 
  │   ├ sirius::Unit_cell::update                                       |        6.88 ms →        7.01 ms   (+1.98%) |       1   →       1              |        6.88 ms →        7.01 ms   (+1.98%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.55 ms →        3.64 ms   (+2.65%) |       1   →       1              |        3.55 ms →        3.64 ms   (+2.65%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.29 ms →        3.33 ms   (+1.24%) |       1   →       1              |        3.29 ms →        3.33 ms   (+1.24%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.24 ms →        3.29 ms   (+1.53%) |       1   →       1              |        3.24 ms →        3.29 ms   (+1.53%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.70 ms →        2.74 ms   (+1.60%) |       1   →       1              |        2.70 ms →        2.74 ms   (+1.60%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      491.32 μs →      503.78 μs   (+2.53%) |       1   →       1              |      491.32 μs →      503.78 μs   (+2.53%) | 
+ │   │     └ sirius::Unit_cell_symmetry|mag                            |       25.19 μs →       13.92 μs  (-44.75%) |       1   →       1              |       25.19 μs →       13.92 μs  (-44.75%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      214.30 ms →      213.38 ms   (-0.43%) |       2   →       2              |      428.60 ms →      426.76 ms   (-0.43%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.17 ms →       15.14 ms   (-0.18%) |       2   →       2              |       30.34 ms →       30.29 ms   (-0.18%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.27 ms →       13.25 ms   (-0.21%) |       1   →       1              |       13.27 ms →       13.25 ms   (-0.21%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.79 ms →       56.67 ms   (-0.20%) |       2   →       2              |      113.57 ms →      113.34 ms   (-0.20%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.18 ms →       44.97 ms   (-0.46%) |       2   →       2              |       90.36 ms →       89.95 ms   (-0.46%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.44 ms →       60.19 ms   (-0.42%) |       4   →       4              |      241.76 ms →      240.74 ms   (-0.42%) | 
  │   ├ sddk::Gvec::init                                                |       93.49 ms →       92.93 ms   (-0.59%) |       2   →       2              |      186.97 ms →      185.86 ms   (-0.59%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       69.67 ms →       69.20 ms   (-0.68%) |       2   →       2              |      139.34 ms →      138.40 ms   (-0.68%) | 
+ │   ├ sddk::Gvec_shells                                               |      105.18 ms →       92.77 ms  (-11.80%) |       1   →       1              |      105.18 ms →       92.77 ms  (-11.80%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.96 ms →        1.94 ms   (-0.89%) |       1   →       1              |        1.96 ms →        1.94 ms   (-0.89%) | 
- │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      457.83 ms →      715.85 ms  (+56.36%) |       2   →       2              |      915.66 ms →        1.43 s   (+56.36%) | 
+ ├ sirius::K_point_set::create_k_mesh                                  |      134.15 ms →       28.91 ms  (-78.45%) |       1   →       1              |      134.15 ms →       28.91 ms  (-78.45%) | 
+ │ ├ sirius::K_point::K_point                                          |        1.15 μs →        1.00 μs  (-12.55%) |       4   →       4              |        4.58 μs →        4.01 μs  (-12.55%) | 
+ │ └ sirius::K_point_set::initialize                                   |      134.07 ms →       28.83 ms  (-78.50%) |       1   →       1              |      134.07 ms →       28.83 ms  (-78.50%) | 
  │   └ sirius::K_point::initialize                                     |       28.82 ms →       28.55 ms   (-0.92%) |       1   →       1              |       28.82 ms →       28.55 ms   (-0.92%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       10.85 ms →       10.76 ms   (-0.77%) |       1   →       1              |       10.85 ms →       10.76 ms   (-0.77%) | 
  │     │ └ sddk::Gvec::init                                            |        4.91 ms →        4.87 ms   (-0.85%) |       1   →       1              |        4.91 ms →        4.87 ms   (-0.85%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        7.51 μs →        7.22 μs   (-3.81%) |       1   →       1              |        7.51 μs →        7.22 μs   (-3.81%) | 
  │     └ sirius::K_point::update                                       |       14.86 ms →       14.69 ms   (-1.13%) |       1   →       1              |       14.86 ms →       14.69 ms   (-1.13%) | 
  │       └ sirius::Beta_projectors                                     |       10.88 ms →       10.70 ms   (-1.68%) |       1   →       1              |       10.88 ms →       10.70 ms   (-1.68%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.36 ms →        8.68 ms   (+3.83%) |       1   →       1              |        8.36 ms →        8.68 ms   (+3.83%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.55 ms →        2.60 ms   (+1.83%) |       2   →       2              |        5.10 ms →        5.19 ms   (+1.83%) | 
  ├ sirius::Potential                                                   |       54.50 ms →       54.96 ms   (+0.86%) |       1   →       1              |       54.50 ms →       54.96 ms   (+0.86%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.94 ms →        2.93 ms   (-0.45%) |       6   →       6              |       17.66 ms →       17.58 ms   (-0.45%) | 
  │ └ sirius::Potential::update                                         |       36.23 ms →       36.79 ms   (+1.54%) |       1   →       1              |       36.23 ms →       36.79 ms   (+1.54%) | 
  │   └ sirius::Potential::generate_local_potential                     |       35.83 ms →       36.39 ms   (+1.57%) |       1   →       1              |       35.83 ms →       36.39 ms   (+1.57%) | 
- │     ├ sirius::Simulation_context::make_periodic_function            |       26.75 ms →       32.00 ms  (+19.63%) |       1   →       1              |       26.75 ms →       32.00 ms  (+19.63%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        8.56 ms →        3.83 ms  (-55.25%) |       1   →       1              |        8.56 ms →        3.83 ms  (-55.25%) | 
  ├ sirius::Density                                                     |       40.41 ms →       41.21 ms   (+1.98%) |       1   →       1              |       40.41 ms →       41.21 ms   (+1.98%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.83 ms →        2.83 ms   (+0.01%) |       2   →       2              |        5.66 ms →        5.66 ms   (+0.01%) | 
  │ └ sirius::Density::update                                           |       34.61 ms →       35.41 ms   (+2.30%) |       1   →       1              |       34.61 ms →       35.41 ms   (+2.30%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       34.29 ms →       35.13 ms   (+2.43%) |       1   →       1              |       34.29 ms →       35.13 ms   (+2.43%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |       77.38 μs →       80.66 μs   (+4.25%) |       1   →       1              |       77.38 μs →       80.66 μs   (+4.25%) | 
- │     ├ sirius::Simulation_context::make_periodic_function            |       26.58 ms →       31.41 ms  (+18.17%) |       1   →       1              |       26.58 ms →       31.41 ms  (+18.17%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        7.33 ms →        3.28 ms  (-55.26%) |       1   →       1              |        7.33 ms →        3.28 ms  (-55.26%) | 
  ├ sirius::Density::initial_density                                    |       61.43 ms →       64.37 ms   (+4.79%) |       1   →       1              |       61.43 ms →       64.37 ms   (+4.79%) | 
- │ ├ sirius::Simulation_context::make_periodic_function                |       27.40 ms →       36.21 ms  (+32.16%) |       1   →       1              |       27.40 ms →       36.21 ms  (+32.16%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        8.03 ms →        4.95 ms  (-38.33%) |       2   →       2              |       16.05 ms →        9.90 ms  (-38.33%) | 
  │ └ sirius::Periodic_function::integrate                              |        4.57 ms →        4.84 ms   (+5.92%) |       1   →       1              |        4.57 ms →        4.84 ms   (+5.92%) | 
  ├ sirius::Potential::generate                                         |      369.00 ms →      372.16 ms   (+0.86%) |       1   →       1              |      369.00 ms →      372.16 ms   (+0.86%) | 
  │ ├ sirius::Potential::poisson                                        |       41.82 ms →       44.42 ms   (+6.22%) |       1   →       1              |       41.82 ms →       44.42 ms   (+6.22%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       11.21 ms →        3.28 ms  (-70.75%) |       1   →       1              |       11.21 ms →        3.28 ms  (-70.75%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        4.83 ms →        5.08 ms   (+5.00%) |       1   →       1              |        4.83 ms →        5.08 ms   (+5.00%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.82 ms →        4.64 ms   (-3.92%) |       1   →       1              |        4.82 ms →        4.64 ms   (-3.92%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.82 ms →        4.63 ms   (-3.93%) |       1   →       1              |        4.82 ms →        4.63 ms   (-3.93%) | 
  │ ├ sirius::Periodic_function::add                                    |      760.69 μs →      742.07 μs   (-2.45%) |       2   →       2              |        1.52 ms →        1.48 ms   (-2.45%) | 
  │ ├ sirius::Potential::xc                                             |       51.95 ms →       51.79 ms   (-0.31%) |       1   →       1              |       51.95 ms →       51.79 ms   (-0.31%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       50.72 ms →       50.59 ms   (-0.26%) |       1   →       1              |       50.72 ms →       50.59 ms   (-0.26%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.59 ms →        2.56 ms   (-1.11%) |       2   →       2              |        5.17 ms →        5.12 ms   (-1.11%) | 
+ │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.90 ms →        4.38 ms  (-10.63%) |       1   →       1              |        4.90 ms →        4.38 ms  (-10.63%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.33 ms →        3.81 ms  (+14.22%) |       1   →       1              |        3.33 ms →        3.81 ms  (+14.22%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      269.06 ms →      269.27 ms   (+0.08%) |       1   →       1              |      269.06 ms →      269.27 ms   (+0.08%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      140.00 ns →      153.00 ns   (+9.29%) |       1   →       1              |      140.00 ns →      153.00 ns   (+9.29%) | 
  ├ sirius::Hamiltonian0                                                |        6.31 ms →        6.34 ms   (+0.57%) |       1   →       1              |        6.31 ms →        6.34 ms   (+0.57%) | 
  │ ├ sirius::Local_operator                                            |        5.86 ms →        5.88 ms   (+0.34%) |       1   →       1              |        5.86 ms →        5.88 ms   (+0.34%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.74 ms →        2.75 ms   (+0.21%) |       1   →       1              |        2.74 ms →        2.75 ms   (+0.21%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.34 ms →        2.39 ms   (+2.35%) |       1   →       1              |        2.34 ms →        2.39 ms   (+2.35%) | 
  │ ├ sirius::Non_local_operator                                        |       71.01 μs →       74.58 μs   (+5.02%) |       2   →       2              |      142.02 μs →      149.16 μs   (+5.02%) | 
+ │ ├ sirius::D_operator::initialize                                    |      135.03 μs →      111.51 μs  (-17.42%) |       1   →       1              |      135.03 μs →      111.51 μs  (-17.42%) | 
- │ └ sirius::Q_operator::initialize                                    |      106.03 μs →      124.03 μs  (+16.97%) |       1   →       1              |      106.03 μs →      124.03 μs  (+16.97%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.27 s  →        1.28 s    (+0.90%) |       1   →       1              |        1.27 s  →        1.28 s    (+0.90%) | 
- │ ├ sirius::Hamiltonian_k                                             |       32.20 ms →       46.83 ms  (+45.41%) |       1   →       1              |       32.20 ms →       46.83 ms  (+45.41%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      231.42 μs →      251.85 μs   (+8.82%) |       1   →       1              |      231.42 μs →      251.85 μs   (+8.82%) | 
- │ │ └ sirius::Beta_projectors_base::prepare                           |       31.97 ms →       46.57 ms  (+45.67%) |       1   →       1              |       31.97 ms →       46.57 ms  (+45.67%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.24 s  →        1.24 s    (-0.26%) |       1   →       1              |        1.24 s  →        1.24 s    (-0.26%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       80.66 ms →       79.72 ms   (-1.15%) |       4   →       4              |      322.62 ms →      318.90 ms   (-1.15%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       40.88 ms →       41.09 ms   (+0.52%) |       1   →       1              |       40.88 ms →       41.09 ms   (+0.52%) | 
- │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        7.13 ms →        7.99 ms  (+12.07%) |       1   →       1              |        7.13 ms →        7.99 ms  (+12.07%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      316.44 ms →      312.45 ms   (-1.26%) |       1   →       1              |      316.44 ms →      312.45 ms   (-1.26%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      246.55 ms →      244.67 ms   (-0.76%) |       1   →       1              |      246.55 ms →      244.67 ms   (-0.76%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        4.18 μs →        4.85 μs  (+16.13%) |       1   →       1              |        4.18 μs →        4.85 μs  (+16.13%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.28 μs →        3.79 μs  (+15.74%) |       1   →       1              |        3.28 μs →        3.79 μs  (+15.74%) | 
- │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      408.00 ns →      746.00 ns  (+82.84%) |       1   →       1              |      408.00 ns →      746.00 ns  (+82.84%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |        1.41 μs →        1.31 μs   (-7.50%) |       1   →       1              |        1.41 μs →        1.31 μs   (-7.50%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.22 ms →        3.18 ms   (-1.07%) |       1   →       1              |        3.22 ms →        3.18 ms   (-1.07%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.29 ms →       21.33 ms   (+0.21%) |       1   →       1              |       21.29 ms →       21.33 ms   (+0.21%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       22.68 ms →       21.61 ms   (-4.70%) |       2   →       2              |       45.35 ms →       43.22 ms   (-4.70%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.96 ms →       16.16 ms   (+8.04%) |       2   →       2              |       29.91 ms →       32.32 ms   (+8.04%) | 
  │ │ │ └ sddk::wf_inner                                                |       14.75 ms →       15.95 ms   (+8.15%) |       2   →       2              |       29.49 ms →       31.90 ms   (+8.15%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       21.00 ns →       36.00 ns  (+71.43%) |       2   →       2              |       42.00 ns →       72.00 ns  (+71.43%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       14.61 ms →       15.79 ms   (+8.06%) |       2   →       2              |       29.23 ms →       31.58 ms   (+8.06%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       27.00 ns →       39.50 ns  (+46.30%) |       2   →       2              |       54.00 ns →       79.00 ns  (+46.30%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      256.21 ms →      249.51 ms   (-2.62%) |       1   →       1              |      256.21 ms →      249.51 ms   (-2.62%) | 
  │ │ └ sddk::wf_trans                                                  |        2.64 ms →        2.61 ms   (-1.09%) |       1   →       1              |        2.64 ms →        2.61 ms   (-1.09%) | 
  │ │   └ sddk::wf_trans|pw                                             |        2.63 ms →        2.60 ms   (-1.08%) |       1   →       1              |        2.63 ms →        2.60 ms   (-1.08%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      422.00 ns →      241.00 ns  (-42.89%) |       1   →       1              |      422.00 ns →      241.00 ns  (-42.89%) | 
- ├ sirius::DFT_ground_state::scf_loop                                  |       62.93 s  →     1029.90 s  (+1536.49%) |       1   →       1              |       62.93 s  →     1029.90 s  (+1536.49%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.45 ms →        2.47 ms   (+0.84%) |      19   →      19              |       46.55 ms →       46.95 ms   (+0.84%) | 
- │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        2.99 s  →       10.30 s  (+244.88%) |      21   →     100   (+376.19%) |       62.70 s  →     1029.68 s  (+1542.28%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        4.91 ms →        4.72 ms   (-3.84%) |      21   →     100   (+376.19%) |      103.06 ms →      471.93 ms (+357.92%) | 
- │ │ │ ├ sirius::Local_operator                                        |        4.23 ms →        4.05 ms   (-4.30%) |      21   →     100   (+376.19%) |       88.84 ms →      404.87 ms (+355.70%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function                            |      554.38 μs →      542.48 μs   (-2.15%) |      21   →     100   (+376.19%) |       11.64 ms →       54.25 ms (+365.97%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.52 ms →        2.51 ms   (-0.47%) |      21   →     100   (+376.19%) |       52.86 ms →      250.54 ms (+373.95%) | 
- │ │ │ ├ sirius::Non_local_operator                                    |      194.60 μs →      195.65 μs   (+0.54%) |      42   →     200   (+376.19%) |        8.17 ms →       39.13 ms (+378.75%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |      113.37 μs →      116.89 μs   (+3.10%) |      21   →     100   (+376.19%) |        2.38 ms →       11.69 ms (+390.97%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       96.21 μs →       90.71 μs   (-5.71%) |      21   →     100   (+376.19%) |        2.02 ms →        9.07 ms (+348.98%) | 
- │ │ ├ sirius::Band::solve                                             |        1.76 s  →        9.12 s  (+418.60%) |      21   →     100   (+376.19%) |       36.93 s  →      912.11 s  (+2369.55%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      196.49 μs →      307.79 μs  (+56.64%) |      21   →     100   (+376.19%) |        4.13 ms →       30.78 ms (+645.92%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      186.83 μs →      299.07 μs  (+60.08%) |      21   →     100   (+376.19%) |        3.92 ms →       29.91 ms (+662.26%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        7.09 μs →        6.47 μs   (-8.71%) |      21   →     100   (+376.19%) |      148.93 μs →      647.41 μs (+334.70%) | 
- │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.63 s  →        9.10 s  (+458.21%) |      21   →     100   (+376.19%) |       34.22 s  →      909.51 s  (+2558.12%) | 
- │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       71.99 ms →       35.48 ms  (-50.71%) |      21   →     100   (+376.19%) |        1.51 s  →        3.55 s  (+134.69%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.31 ms →        1.50 ms  (-79.47%) |     126   →     600   (+376.19%) |      921.59 ms →      900.97 ms   (-2.24%) | 
- │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       16.83 ms →       17.59 ms   (+4.54%) |      21   →     100   (+376.19%) |      353.43 ms →        1.76 s  (+397.79%) | 
- │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      462.65 μs →      458.29 μs   (-0.94%) |      21   →     100   (+376.19%) |        9.72 ms →       45.83 ms (+371.70%) | 
- │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        7.52 ms →        7.96 ms   (+5.83%) |      42   →     200   (+376.19%) |      315.86 ms →        1.59 s  (+403.97%) | 
- │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.53 s  →        9.03 s  (+489.36%) |      21   →     100   (+376.19%) |       32.18 s  →      903.08 s  (+2706.47%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       51.35 ms →      259.20 ms (+404.76%) |     361   →    1.98 K (+449.31%) |       18.54 s  →      514.00 s  (+2672.69%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       29.54 ms →      191.34 ms (+547.70%) |     361   →    1.98 K (+449.31%) |       10.66 s  →      379.43 s  (+3457.84%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.95 μs →        2.27 μs  (+16.23%) |     361   →    1.98 K (+449.31%) |      704.21 μs →        4.50 ms (+538.44%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.57 μs →        1.92 μs  (+22.38%) |     361   →    1.98 K (+449.31%) |      567.18 μs →        3.81 ms (+572.23%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      386.68 ns →      416.56 ns   (+7.73%) |     361   →    1.98 K (+449.31%) |      139.59 μs →      826.05 μs (+491.75%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      427.08 ns →      584.83 ns  (+36.94%) |     361   →    1.98 K (+449.31%) |      154.18 μs →        1.16 ms (+652.20%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.87 ms →        4.24 ms  (+47.64%) |     361   →    1.98 K (+449.31%) |        1.04 s  →        8.42 s  (+711.01%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.23 ms →       11.58 ms (+258.94%) |     361   →    1.98 K (+449.31%) |        1.16 s  →       22.97 s  (+1871.68%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.85 ms →       26.01 ms (+231.45%) |     722   →    3.97 K (+449.31%) |        5.67 s  →      103.16 s  (+1720.68%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |        6.80 ms →       27.05 ms (+297.69%) |     361   →    1.98 K (+449.31%) |        2.46 s  →       53.64 s  (+2084.53%) | 
- │ │ │ │   │ ├ sddk::wf_inner                                          |        1.10 ms →        3.38 ms (+208.03%) |     701   →    3.87 K (+451.50%) |      770.05 ms →       13.08 s  (+1598.76%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       49.87 ns →       44.65 ns  (-10.47%) |     701   →    3.87 K (+451.50%) |       34.96 μs →      172.61 μs (+393.75%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |      936.28 μs →        3.21 ms (+242.48%) |     701   →    3.87 K (+451.50%) |      656.33 ms →       12.40 s  (+1788.78%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       49.96 ns →       47.75 ns   (-4.43%) |     701   →    3.87 K (+451.50%) |       35.02 μs →      184.60 μs (+427.09%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      140.74 μs →      651.00 μs (+362.55%) |     361   →    1.98 K (+449.31%) |       50.81 ms →        1.29 s  (+2440.85%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        2.16 ms →       10.59 ms (+389.40%) |     361   →    1.98 K (+449.31%) |      781.49 ms →       21.01 s  (+2588.30%) | 
- │ │ │ │   │ └ sddk::wf_trans                                          |        2.50 ms →        9.69 ms (+286.97%) |     340   →    1.88 K (+453.82%) |      851.44 ms →       18.25 s  (+2043.13%) | 
- │ │ │ │   │   └ sddk::wf_trans|pw                                     |      833.95 μs →        3.23 ms (+287.23%) |    1.02 K →    5.65 K (+453.82%) |      850.63 ms →       18.24 s  (+2044.57%) | 
- │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.42 ms →        4.89 ms (+244.32%) |     361   →    1.98 K (+449.31%) |      513.09 ms →        9.70 s  (+1791.36%) | 
- │ │ │ │   │ └ sddk::wf_inner                                          |        1.35 ms →        4.70 ms (+248.68%) |     361   →    1.98 K (+449.31%) |      486.25 ms →        9.31 s  (+1815.30%) | 
- │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       43.81 ns →       52.07 ns  (+18.86%) |     361   →    1.98 K (+449.31%) |       15.82 μs →      103.26 μs (+552.90%) | 
- │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        1.18 ms →        4.52 ms (+281.67%) |     361   →    1.98 K (+449.31%) |      427.75 ms →        8.97 s  (+1996.53%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       46.54 ns →       65.69 ns  (+41.13%) |     361   →    1.98 K (+449.31%) |       16.80 μs →      130.26 μs (+675.24%) | 
- │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       25.75 ms →      140.27 ms (+444.72%) |     361   →    1.98 K (+449.31%) |        9.30 s  →      278.15 s  (+2892.21%) | 
- │ │ │ │   ├ sirius::residuals                                         |        2.66 ms →       13.44 ms (+405.44%) |     346   →    1.88 K (+444.51%) |      919.94 ms →       25.32 s  (+2652.16%) | 
- │ │ │ │   │ ├ sddk::wf_trans                                          |        1.19 ms →        7.85 ms (+560.62%) |     342   →    1.88 K (+450.58%) |      406.64 ms →       14.79 s  (+3537.25%) | 
- │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      593.10 μs →        3.93 ms (+561.90%) |     684   →    3.77 K (+450.58%) |      405.68 ms →       14.78 s  (+3544.34%) | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.37 ms →        5.35 ms (+291.84%) |     342   →    1.88 K (+450.58%) |      467.21 ms →       10.08 s  (+2057.39%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        4.99 ms →       12.10 ms (+142.48%) |      90   →    1.84 K (+1940.00%) |      448.97 ms →       22.21 s  (+4846.64%) | 
- │ │ │ │     └ sddk::wf_trans                                          |        2.77 ms →        6.16 ms (+122.06%) |     159   →    3.57 K (+2146.54%) |      440.77 ms →       21.99 s  (+4888.66%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |        1.93 ms →        4.14 ms (+114.36%) |     228   →    5.31 K (+2228.07%) |      440.48 ms →       21.98 s  (+4890.42%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      515.52 ns →      424.25 ns  (-17.71%) |      21   →     100   (+376.19%) |       10.83 μs →       42.43 μs (+291.88%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       20.18 μs →       19.90 μs   (-1.43%) |      21   →     100   (+376.19%) |      423.86 μs →        1.99 ms (+369.40%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.54 ms →        1.04 ms  (-32.35%) |      21   →     100   (+376.19%) |       32.37 ms →      104.26 ms (+222.14%) | 
- │ │ ├ sirius::Density::generate                                       |      568.38 ms →      565.91 ms   (-0.43%) |      21   →     100   (+376.19%) |       11.94 s  →       56.59 s  (+374.12%) | 
- │ │ │ ├ sirius::Density::generate_valence                             |      400.38 ms →      395.72 ms   (-1.16%) |      21   →     100   (+376.19%) |        8.41 s  →       39.57 s  (+370.65%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        7.41 μs →        7.75 μs   (+4.58%) |      21   →     100   (+376.19%) |      155.55 μs →      774.68 μs (+398.01%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        6.72 μs →        7.07 μs   (+5.33%) |      21   →     100   (+376.19%) |      141.03 μs →      707.38 μs (+401.57%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       42.11 ms →       34.68 ms  (-17.65%) |      21   →     100   (+376.19%) |      884.30 ms →        3.47 s  (+292.17%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       12.20 μs →       10.68 μs  (-12.45%) |      21   →     100   (+376.19%) |      256.18 μs →        1.07 ms (+316.90%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.02 ms →        5.55 ms  (-20.88%) |      21   →     100   (+376.19%) |      147.40 ms →      555.37 ms (+276.78%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       33.93 ms →       28.07 ms  (-17.26%) |      21   →     100   (+376.19%) |      712.49 ms →        2.81 s  (+294.00%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      910.29 ns →      608.80 ns  (-33.12%) |      21   →     100   (+376.19%) |       19.12 μs →       60.88 μs (+218.48%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      104.08 ms →      109.32 ms   (+5.03%) |      21   →     100   (+376.19%) |        2.19 s  →       10.93 s  (+400.12%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.17 ms →        2.10 ms   (-3.12%) |      21   →     100   (+376.19%) |       45.58 ms →      210.28 ms (+361.35%) | 
- │ │ │ │ └ sirius::Density::augment                                    |      209.35 ms →      211.25 ms   (+0.90%) |      21   →     100   (+376.19%) |        4.40 s  →       21.12 s  (+380.50%) | 
- │ │ │ │   └ sirius::Density::generate_rho_aug                         |      209.14 ms →      211.03 ms   (+0.90%) |      21   →     100   (+376.19%) |        4.39 s  →       21.10 s  (+380.49%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      140.00 ms →      142.02 ms   (+1.44%) |      21   →     100   (+376.19%) |        2.94 s  →       14.20 s  (+383.05%) | 
- │ │ │ │ └ sirius::symmetrize_function|fpw                             |      140.00 ms →      142.02 ms   (+1.44%) |      21   →     100   (+376.19%) |        2.94 s  →       14.20 s  (+383.06%) | 
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       59.42 ms →       59.04 ms   (-0.64%) |      21   →     100   (+376.19%) |        1.25 s  →        5.90 s  (+373.16%) | 
- │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       67.29 ms →       69.72 ms   (+3.62%) |      21   →     100   (+376.19%) |        1.41 s  →        6.97 s  (+393.43%) | 
- │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.64 ms →       12.62 ms   (-0.21%) |      21   →     100   (+376.19%) |      265.49 ms →        1.26 s  (+375.17%) | 
- │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.63 ms →       23.58 ms   (-0.21%) |      21   →     100   (+376.19%) |      496.15 ms →        2.36 s  (+375.19%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        4.38 ms →        4.59 ms   (+4.99%) |      21   →     100   (+376.19%) |       91.88 ms →      459.35 ms (+399.94%) | 
- │ │ ├ sirius::Density::mix                                            |      137.35 ms →       85.62 ms  (-37.66%) |      21   →     100   (+376.19%) |        2.88 s  →        8.56 s  (+196.84%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      293.04 μs →      312.13 μs   (+6.52%) |      21   →     100   (+376.19%) |        6.15 ms →       31.21 ms (+407.22%) | 
- │ │ │ ├ sirius::Periodic_function|inner                               |        5.01 ms →        4.85 ms   (-3.20%) |     259   →     818   (+215.83%) |        1.30 s  →        3.97 s  (+205.72%) | 
- │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.83 ms →        4.64 ms   (-4.06%) |     259   →     818   (+215.83%) |        1.25 s  →        3.79 s  (+202.99%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.83 ms →        4.64 ms   (-4.06%) |     259   →     818   (+215.83%) |        1.25 s  →        3.79 s  (+203.00%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        6.58 ms →        5.88 ms  (-10.61%) |      21   →     100   (+376.19%) |      138.08 ms →      587.77 ms (+325.68%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.79 ms →        5.09 ms  (-12.02%) |      21   →     100   (+376.19%) |      121.50 ms →      509.02 ms (+318.93%) | 
- │ │ ├ sirius::Potential::generate                                     |      362.19 ms →      364.30 ms   (+0.58%) |      21   →     100   (+376.19%) |        7.61 s  →       36.43 s  (+378.96%) | 
- │ │ │ ├ sirius::Potential::poisson                                    |       42.07 ms →       44.37 ms   (+5.45%) |      21   →     100   (+376.19%) |      883.53 ms →        4.44 s  (+402.16%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       11.43 ms →        3.26 ms  (-71.50%) |      21   →     100   (+376.19%) |      239.97 ms →      325.68 ms  (+35.72%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |        4.85 ms →        5.06 ms   (+4.43%) |      21   →     100   (+376.19%) |      101.78 ms →      506.13 ms (+397.27%) | 
- │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.84 ms →        4.63 ms   (-4.34%) |      21   →     100   (+376.19%) |      101.68 ms →      463.15 ms (+355.51%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.84 ms →        4.63 ms   (-4.34%) |      21   →     100   (+376.19%) |      101.65 ms →      463.05 ms (+355.54%) | 
- │ │ │ ├ sirius::Periodic_function::add                                |      754.12 μs →      770.10 μs   (+2.12%) |      42   →     200   (+376.19%) |       31.67 ms →      154.02 ms (+386.28%) | 
- │ │ │ ├ sirius::Potential::xc                                         |       45.23 ms →       44.80 ms   (-0.97%) |      21   →     100   (+376.19%) |      949.90 ms →        4.48 s  (+371.58%) | 
- │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       44.04 ms →       43.61 ms   (-0.99%) |      21   →     100   (+376.19%) |      924.86 ms →        4.36 s  (+371.48%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function                          |      683.98 μs →      651.47 μs   (-4.75%) |      42   →     200   (+376.19%) |       28.73 ms →      130.29 ms (+353.56%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.81 ms →        4.94 ms   (+2.62%) |      21   →     100   (+376.19%) |      101.00 ms →      493.52 ms (+388.65%) | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.22 ms →        3.61 ms  (+11.98%) |      21   →     100   (+376.19%) |       67.72 ms →      361.10 ms (+433.23%) | 
- │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.76 ms →      268.56 ms   (-0.07%) |      21   →     100   (+376.19%) |        5.64 s  →       26.86 s  (+375.83%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      165.14 ns →      214.29 ns  (+29.76%) |      21   →     100   (+376.19%) |        3.47 μs →       21.43 μs (+517.91%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |       95.35 ms →       96.84 ms   (+1.57%) |      21   →     100   (+376.19%) |        2.00 s  →        9.68 s  (+383.67%) | 
- │ │ │ └ sirius::symmetrize_function|fpw                               |       95.34 ms →       96.84 ms   (+1.57%) |      21   →     100   (+376.19%) |        2.00 s  →        9.68 s  (+383.67%) | 
- │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       14.60 ms →       14.56 ms   (-0.24%) |      21   →     100   (+376.19%) |      306.59 ms →        1.46 s  (+375.06%) | 
- │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       66.90 ms →       69.10 ms   (+3.29%) |      21   →     100   (+376.19%) |        1.40 s  →        6.91 s  (+391.86%) | 
- │ │ │   └ sddk::Gvec_shells::remap_backward                           |       13.22 ms →       12.55 ms   (-5.05%) |      21   →     100   (+376.19%) |      277.64 ms →        1.26 s  (+352.16%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        4.37 ms →        4.40 ms   (+0.73%) |      21   →     100   (+376.19%) |       91.80 ms →      440.32 ms (+379.67%) | 
- │ │ ├ sirius::Periodic_function|inner                                 |        4.81 ms →        4.93 ms   (+2.59%) |     147   →     700   (+376.19%) |      706.74 ms →        3.45 s  (+388.54%) | 
- │ │ │ └ sirius::Periodic_function|inner_local                         |        4.58 ms →        4.75 ms   (+3.75%) |     147   →     700   (+376.19%) |      672.79 ms →        3.32 s  (+394.04%) | 
- │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.58 ms →        4.75 ms   (+3.75%) |     147   →     700   (+376.19%) |      672.68 ms →        3.32 s  (+394.05%) | 
- │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.76 ms →        4.53 ms   (-4.85%) |      63   →     300   (+376.19%) |      300.16 ms →        1.36 s  (+353.11%) | 
- │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.75 ms →        4.52 ms   (-4.69%) |      63   →     300   (+376.19%) |      299.06 ms →        1.36 s  (+353.88%) | 
- │ │ ├ sirius::Periodic_function::integrate                            |        4.57 ms →        4.54 ms   (-0.67%) |      21   →     100   (+376.19%) |       95.90 ms →      453.59 ms (+373.00%) | 
- │ │ └ sirius::Density::get_magnetisation                              |       73.75 μs →       75.90 μs   (+2.93%) |      21   →     100   (+376.19%) |        1.55 ms →        7.59 ms (+390.13%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |       69.10 μs →       70.68 μs   (+2.28%) |      21   →     100   (+376.19%) |        1.45 ms →        7.07 ms (+387.05%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.15 ms →        5.54 ms   (+7.70%) |       2   →       2              |       10.29 ms →       11.09 ms   (+7.70%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.90 ms →        4.74 ms   (-3.23%) |       6   →       6              |       29.42 ms →       28.47 ms   (-3.23%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.83 ms →        4.74 ms   (-1.96%) |       6   →       6              |       28.99 ms →       28.43 ms   (-1.96%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.83 ms →        4.74 ms   (-1.96%) |       6   →       6              |       28.99 ms →       28.42 ms   (-1.96%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.99 ms →        4.52 ms   (-9.36%) |       3   →       3              |       14.96 ms →       13.56 ms   (-9.36%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.98 ms →        4.52 ms   (-9.34%) |       3   →       3              |       14.94 ms →       13.55 ms   (-9.34%) | 
  ├ sirius::Periodic_function|inner                                     |        4.78 ms →        4.75 ms   (-0.48%) |       2   →       2              |        9.55 ms →        9.51 ms   (-0.48%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.77 ms →        4.73 ms   (-0.86%) |       2   →       2              |        9.54 ms →        9.46 ms   (-0.86%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.77 ms →        4.73 ms   (-0.86%) |       2   →       2              |        9.54 ms →        9.46 ms   (-0.86%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        5.00 ms →        4.53 ms   (-9.33%) |       1   →       1              |        5.00 ms →        4.53 ms   (-9.33%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.99 ms →        4.52 ms   (-9.37%) |       1   →       1              |        4.99 ms →        4.52 ms   (-9.37%) | 
+ └ sirius::finalize                                                    |      278.76 ms →      152.58 ms  (-45.27%) |       1   →       1              |      278.76 ms →      152.58 ms  (-45.27%) | 
  ====================================================================================================================================================================================================
```
