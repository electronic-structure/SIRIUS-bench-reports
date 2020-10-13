# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs a923c3c8853d846138a8b9a9c096494004b8d208
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      163.33 s  →      133.76 s   (-18.11%) |       1   →       1              |      163.33 s  →      133.76 s   (-18.11%) | 
  ├ sirius::initialize                                                  |        2.86 s  →        2.69 s    (-5.98%) |       1   →       1              |        2.86 s  →        2.69 s    (-5.98%) | 
+ ├ sirius::Simulation_context::initialize                              |        4.05 s  →        2.98 s   (-26.58%) |       1   →       1              |        4.05 s  →        2.98 s   (-26.58%) | 
- │ ├ sirius::Simulation_context::init_comm                             |      196.40 μs →       59.13 ms (+30008.73%) |       1   →       1              |      196.40 μs →       59.13 ms (+30008.73%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      143.09 ms →      168.00 ms  (+17.41%) |       1   →       1              |      143.09 ms →      168.00 ms  (+17.41%) | 
- │ │ ├ sirius::Atom_type::init                                         |       58.91 ms →       72.58 ms  (+23.20%) |       2   →       2              |      117.82 ms →      145.15 ms  (+23.20%) | 
  │ │ └ sirius::Unit_cell::update                                       |       25.16 ms →       22.77 ms   (-9.48%) |       1   →       1              |       25.16 ms →       22.77 ms   (-9.48%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.55 ms →        6.46 ms   (-1.42%) |       1   →       1              |        6.55 ms →        6.46 ms   (-1.42%) | 
+ │ │   └ sirius::Unit_cell::get_symmetry                               |       18.56 ms →       16.27 ms  (-12.30%) |       1   →       1              |       18.56 ms →       16.27 ms  (-12.30%) | 
+ │ │     └ sirius::Unit_cell_symmetry                                  |       18.53 ms →       16.25 ms  (-12.29%) |       1   →       1              |       18.53 ms →       16.25 ms  (-12.29%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.15 ms →        4.16 ms   (+0.22%) |       1   →       1              |        4.15 ms →        4.16 ms   (+0.22%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.35 ms →        2.34 ms   (-0.35%) |       1   →       1              |        2.35 ms →        2.34 ms   (-0.35%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      103.12 μs →      101.13 μs   (-1.93%) |       1   →       1              |      103.12 μs →      101.13 μs   (-1.93%) | 
+ │ └ sirius::Simulation_context::update                                |        3.87 s  →        2.70 s   (-30.08%) |       1   →       1              |        3.87 s  →        2.70 s   (-30.08%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.99 ms →       10.66 ms   (-2.99%) |       1   →       1              |       10.99 ms →       10.66 ms   (-2.99%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.61 ms →        4.23 ms   (-8.19%) |       1   →       1              |        4.61 ms →        4.23 ms   (-8.19%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.35 ms →        6.40 ms   (+0.80%) |       1   →       1              |        6.35 ms →        6.40 ms   (+0.80%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.33 ms →        6.38 ms   (+0.86%) |       1   →       1              |        6.33 ms →        6.38 ms   (+0.86%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.83 ms →        3.90 ms   (+1.87%) |       1   →       1              |        3.83 ms →        3.90 ms   (+1.87%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.31 ms   (-0.77%) |       1   →       1              |        2.33 ms →        2.31 ms   (-0.77%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       99.76 μs →      100.45 μs   (+0.69%) |       1   →       1              |       99.76 μs →      100.45 μs   (+0.69%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       63.25 ms →       62.53 ms   (-1.15%) |       2   →       2              |      126.51 ms →      125.06 ms   (-1.15%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.30 ms →        5.14 ms   (-3.09%) |       2   →       2              |       10.60 ms →       10.28 ms   (-3.09%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.50 ms →        4.49 ms   (-0.14%) |       1   →       1              |        4.50 ms →        4.49 ms   (-0.14%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.76 ms →       21.78 ms   (+0.08%) |       2   →       2              |       43.52 ms →       43.56 ms   (+0.08%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.80 ms →       14.83 ms   (+0.20%) |       2   →       2              |       29.60 ms →       29.66 ms   (+0.20%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.75 ms →       19.79 ms   (+0.19%) |       4   →       4              |       79.00 ms →       79.15 ms   (+0.19%) | 
  │   ├ sddk::Gvec::init                                                |      182.29 ms →      172.72 ms   (-5.25%) |       2   →       2              |      364.59 ms →      345.45 ms   (-5.25%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      134.95 ms →      130.02 ms   (-3.65%) |       2   →       2              |      269.90 ms →      260.05 ms   (-3.65%) | 
  │   ├ sddk::Gvec_shells                                               |      190.34 ms →      173.64 ms   (-8.78%) |       1   →       1              |      190.34 ms →      173.64 ms   (-8.78%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.36 ms →        1.32 ms   (-3.38%) |       1   →       1              |        1.36 ms →        1.32 ms   (-3.38%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      295.40 ms →      291.21 ms   (-1.42%) |       2   →       2              |      590.81 ms →      582.42 ms   (-1.42%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       39.23 ms →       35.67 ms   (-9.08%) |       1   →       1              |       39.23 ms →       35.67 ms   (-9.08%) | 
+ │ ├ sirius::K_point::K_point                                          |        2.88 μs →        1.98 μs  (-31.23%) |       4   →       4              |       11.51 μs →        7.92 μs  (-31.23%) | 
  │ └ sirius::K_point_set::initialize                                   |       39.14 ms →       35.57 ms   (-9.11%) |       1   →       1              |       39.14 ms →       35.57 ms   (-9.11%) | 
  │   └ sirius::K_point::initialize                                     |       39.05 ms →       35.48 ms   (-9.15%) |       1   →       1              |       39.05 ms →       35.48 ms   (-9.15%) | 
+ │     ├ sirius::K_point::generate_gkvec                               |       20.26 ms →       18.11 ms  (-10.59%) |       1   →       1              |       20.26 ms →       18.11 ms  (-10.59%) | 
  │     │ └ sddk::Gvec::init                                            |        9.00 ms →        8.19 ms   (-9.02%) |       1   →       1              |        9.00 ms →        8.19 ms   (-9.02%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        9.92 μs →        9.70 μs   (-2.22%) |       1   →       1              |        9.92 μs →        9.70 μs   (-2.22%) | 
  │     └ sirius::K_point::update                                       |       13.18 ms →       12.57 ms   (-4.65%) |       1   →       1              |       13.18 ms →       12.57 ms   (-4.65%) | 
  │       └ sirius::Beta_projectors                                     |        6.09 ms →        6.38 ms   (+4.81%) |       1   →       1              |        6.09 ms →        6.38 ms   (+4.81%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.50 ms →        3.83 ms   (+9.61%) |       1   →       1              |        3.50 ms →        3.83 ms   (+9.61%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.26 ms →        5.10 ms   (-3.12%) |       2   →       2              |       10.53 ms →       10.20 ms   (-3.12%) | 
  ├ sirius::Potential                                                   |      169.56 ms →      159.60 ms   (-5.87%) |       1   →       1              |      169.56 ms →      159.60 ms   (-5.87%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.87 ms →        5.73 ms   (-2.36%) |       6   →       6              |       35.23 ms →       34.40 ms   (-2.36%) | 
  │ └ sirius::Potential::update                                         |      133.60 ms →      124.46 ms   (-6.84%) |       1   →       1              |      133.60 ms →      124.46 ms   (-6.84%) | 
  │   └ sirius::Potential::generate_local_potential                     |      132.89 ms →      123.75 ms   (-6.88%) |       1   →       1              |      132.89 ms →      123.75 ms   (-6.88%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |      125.98 ms →      109.92 ms  (-12.75%) |       1   →       1              |      125.98 ms →      109.92 ms  (-12.75%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        6.36 ms →       12.90 ms (+103.02%) |       1   →       1              |        6.36 ms →       12.90 ms (+103.02%) | 
  ├ sirius::Density                                                     |      140.87 ms →      134.98 ms   (-4.18%) |       1   →       1              |      140.87 ms →      134.98 ms   (-4.18%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.24 ms →        5.06 ms   (-3.43%) |       2   →       2              |       10.47 ms →       10.11 ms   (-3.43%) | 
  │ └ sirius::Density::update                                           |      130.13 ms →      124.60 ms   (-4.25%) |       1   →       1              |      130.13 ms →      124.60 ms   (-4.25%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      129.69 ms →      124.19 ms   (-4.24%) |       1   →       1              |      129.69 ms →      124.19 ms   (-4.24%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |                       101.80 μs            |                   1              |                       101.80 μs            | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      124.09 ms →      111.71 ms   (-9.97%) |       1   →       1              |      124.09 ms →      111.71 ms   (-9.97%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        5.15 ms →       11.94 ms (+131.75%) |       1   →       1              |        5.15 ms →       11.94 ms (+131.75%) | 
  ├ sirius::Density::initial_density                                    |      175.98 ms →      174.84 ms   (-0.65%) |       1   →       1              |      175.98 ms →      174.84 ms   (-0.65%) | 
+ │ ├ sirius::Simulation_context::make_periodic_function                |      123.09 ms →      110.48 ms  (-10.24%) |       1   →       1              |      123.09 ms →      110.48 ms  (-10.24%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.96 ms →       11.05 ms (+122.81%) |       2   →       2              |        9.92 ms →       22.09 ms (+122.81%) | 
  │ └ sirius::Periodic_function::integrate                              |       10.78 ms →       10.09 ms   (-6.43%) |       1   →       1              |       10.78 ms →       10.09 ms   (-6.43%) | 
  ├ sirius::Potential::generate                                         |      587.07 ms →      598.94 ms   (+2.02%) |       1   →       1              |      587.07 ms →      598.94 ms   (+2.02%) | 
  │ ├ sirius::Potential::poisson                                        |      137.26 ms →      136.55 ms   (-0.51%) |       1   →       1              |      137.26 ms →      136.55 ms   (-0.51%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.33 ms →       16.38 ms (+207.41%) |       1   →       1              |        5.33 ms →       16.38 ms (+207.41%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.34 ms →        9.91 ms   (-4.10%) |       1   →       1              |       10.34 ms →        9.91 ms   (-4.10%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        9.88 ms →        9.85 ms   (-0.36%) |       1   →       1              |        9.88 ms →        9.85 ms   (-0.36%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.88 ms →        9.84 ms   (-0.42%) |       1   →       1              |        9.88 ms →        9.84 ms   (-0.42%) | 
  │ ├ sirius::Periodic_function::add                                    |      553.33 μs →      550.39 μs   (-0.53%) |       2   →       2              |        1.11 ms →        1.10 ms   (-0.53%) | 
  │ ├ sirius::Potential::xc                                             |       53.93 ms →       53.86 ms   (-0.14%) |       1   →       1              |       53.93 ms →       53.86 ms   (-0.14%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       53.93 ms →       51.57 ms   (-4.37%) |       1   →       1              |       53.93 ms →       51.57 ms   (-4.37%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.72 ms →        5.62 ms   (-1.83%) |       2   →       2              |       11.44 ms →       11.23 ms   (-1.83%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.96 ms →        5.58 ms   (-6.36%) |       1   →       1              |        5.96 ms →        5.58 ms   (-6.36%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.89 ms →        5.97 ms   (+1.49%) |       1   →       1              |        5.89 ms →        5.97 ms   (+1.49%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.74 ms →       96.21 ms   (+3.73%) |       1   →       1              |       92.74 ms →       96.21 ms   (+3.73%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      294.75 ms →      303.91 ms   (+3.11%) |       1   →       1              |      294.75 ms →      303.91 ms   (+3.11%) | 
  ├ sirius::Hamiltonian0                                                |        8.42 ms →        8.44 ms   (+0.26%) |       1   →       1              |        8.42 ms →        8.44 ms   (+0.26%) | 
  │ ├ sirius::Local_operator                                            |        8.06 ms →        8.08 ms   (+0.34%) |       1   →       1              |        8.06 ms →        8.08 ms   (+0.34%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.80 ms →        4.69 ms   (-2.19%) |       1   →       1              |        4.80 ms →        4.69 ms   (-2.19%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.32 ms →        2.47 ms   (+6.58%) |       1   →       1              |        2.32 ms →        2.47 ms   (+6.58%) | 
  │ ├ sirius::Non_local_operator                                        |       62.62 μs →       64.23 μs   (+2.58%) |       2   →       2              |      125.24 μs →      128.47 μs   (+2.58%) | 
  │ ├ sirius::D_operator::initialize                                    |      105.80 μs →       95.80 μs   (-9.45%) |       1   →       1              |      105.80 μs →       95.80 μs   (-9.45%) | 
  │ └ sirius::Q_operator::initialize                                    |       79.34 μs →       77.07 μs   (-2.86%) |       1   →       1              |       79.34 μs →       77.07 μs   (-2.86%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.86 s  →        1.85 s    (-0.54%) |       1   →       1              |        1.86 s  →        1.85 s    (-0.54%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.74 ms →       18.05 ms   (-3.68%) |       1   →       1              |       18.74 ms →       18.05 ms   (-3.68%) | 
+ │ │ ├ sirius::Local_operator::prepare_k                               |      207.80 μs →      175.27 μs  (-15.65%) |       1   →       1              |      207.80 μs →      175.27 μs  (-15.65%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       18.53 ms →       17.87 ms   (-3.55%) |       1   →       1              |       18.53 ms →       17.87 ms   (-3.55%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.84 s  →        1.83 s    (-0.50%) |       1   →       1              |        1.84 s  →        1.83 s    (-0.50%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      129.22 ms →      126.75 ms   (-1.91%) |       4   →       4              |      516.87 ms →      506.99 ms   (-1.91%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       53.89 ms →       52.82 ms   (-1.99%) |       1   →       1              |       53.89 ms →       52.82 ms   (-1.99%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.61 ms →       21.50 ms   (-0.51%) |       1   →       1              |       21.61 ms →       21.50 ms   (-0.51%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      635.06 ms →      639.59 ms   (+0.71%) |       1   →       1              |      635.06 ms →      639.59 ms   (+0.71%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      297.87 ms →      301.31 ms   (+1.16%) |       1   →       1              |      297.87 ms →      301.31 ms   (+1.16%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.76 μs →        3.76 μs   (-0.03%) |       1   →       1              |        3.76 μs →        3.76 μs   (-0.03%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.40 μs →        2.74 μs  (+14.03%) |       1   →       1              |        2.40 μs →        2.74 μs  (+14.03%) | 
- │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      429.00 ns →      481.00 ns  (+12.12%) |       1   →       1              |      429.00 ns →      481.00 ns  (+12.12%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      562.00 ns →      527.00 ns   (-6.23%) |       1   →       1              |      562.00 ns →      527.00 ns   (-6.23%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.23 ms →        9.22 ms   (-0.11%) |       1   →       1              |        9.23 ms →        9.22 ms   (-0.11%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      120.76 ms →      120.58 ms   (-0.14%) |       1   →       1              |      120.76 ms →      120.58 ms   (-0.14%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      103.58 ms →      104.22 ms   (+0.62%) |       2   →       2              |      207.17 ms →      208.44 ms   (+0.62%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       38.35 ms →       40.12 ms   (+4.64%) |       2   →       2              |       76.69 ms →       80.25 ms   (+4.64%) | 
  │ │ │ ├ sddk::inner                                                   |       37.78 ms                             |       2                          |       75.55 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       22.48 μs                             |       2                          |       44.96 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        39.59 ms            |                   2              |                        79.18 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        19.50 ns            |                   2              |                        39.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        39.13 ms            |                   2              |                        78.27 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                        19.50 ns            |                   2              |                        39.00 ns            | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       56.42 ms →       61.75 ms   (+9.45%) |       1   →       1              |       56.42 ms →       61.75 ms   (+9.45%) | 
  │ │ ├ sddk::transform                                                 |       31.58 ms                             |       1                          |       31.58 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       11.75 μs                             |       1                          |       11.75 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       11.57 μs                             |       1                          |       11.57 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                        30.75 ms            |                   1              |                        30.75 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                        30.75 ms            |                   1              |                        30.75 ms            | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      612.00 ns →      555.00 ns   (-9.31%) |       1   →       1              |      612.00 ns →      555.00 ns   (-9.31%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      152.04 s  →      124.11 s   (-18.37%) |       1   →       1              |      152.04 s  →      124.11 s   (-18.37%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.82 ms →        5.68 ms   (-2.49%) |      19   →      19              |      110.64 ms →      107.89 ms   (-2.49%) | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.74 s  →        4.76 s    (+0.37%) |      32   →      26    (-18.75%) |      151.70 s  →      123.71 s   (-18.45%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        4.45 ms →        6.01 ms  (+35.07%) |      32   →      26    (-18.75%) |      142.48 ms →      156.37 ms   (+9.75%) | 
- │ │ │ ├ sirius::Local_operator                                        |        4.08 ms →        5.65 ms  (+38.63%) |      32   →      26    (-18.75%) |      130.44 ms →      146.92 ms  (+12.64%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function                            |      963.59 μs →      968.19 μs   (+0.48%) |      32   →      26    (-18.75%) |       30.83 ms →       25.17 ms  (-18.36%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.22 ms →        3.79 ms  (+71.01%) |      32   →      26    (-18.75%) |       70.93 ms →       98.56 ms  (+38.95%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |       65.11 μs →       64.26 μs   (-1.30%) |      64   →      52    (-18.75%) |        4.17 ms →        3.34 ms  (-19.81%) | 
+ │ │ │ ├ sirius::D_operator::initialize                                |      101.18 μs →       86.66 μs  (-14.36%) |      32   →      26    (-18.75%) |        3.24 ms →        2.25 ms  (-30.41%) | 
+ │ │ │ └ sirius::Q_operator::initialize                                |       76.30 μs →       78.92 μs   (+3.43%) |      32   →      26    (-18.75%) |        2.44 ms →        2.05 ms  (-15.96%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.75 s  →        2.78 s    (+1.10%) |      32   →      26    (-18.75%) |       88.03 s  →       72.31 s   (-17.86%) | 
+ │ │ │ ├ sirius::Hamiltonian_k                                         |      160.31 μs →      155.55 μs   (-2.97%) |      32   →      26    (-18.75%) |        5.13 ms →        4.04 ms  (-21.16%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      154.55 μs →      148.43 μs   (-3.96%) |      32   →      26    (-18.75%) |        4.95 ms →        3.86 ms  (-21.97%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.09 μs →        4.81 μs  (+17.69%) |      32   →      26    (-18.75%) |      130.91 μs →      125.18 μs   (-4.37%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.67 s  →        2.61 s    (-2.33%) |      32   →      26    (-18.75%) |       85.55 s  →       67.89 s   (-20.64%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |      106.70 ms →       94.39 ms  (-11.54%) |      32   →      26    (-18.75%) |        3.41 s  →        2.45 s   (-28.13%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        9.49 ms →        7.58 ms  (-20.17%) |     192   →     156    (-18.75%) |        1.82 s  →        1.18 s   (-35.14%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        5.95 ms →        5.96 ms   (+0.16%) |      32   →      26    (-18.75%) |      190.49 ms →      155.01 ms  (-18.62%) | 
+ │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      349.15 μs →      348.86 μs   (-0.08%) |      32   →      26    (-18.75%) |       11.17 ms →        9.07 ms  (-18.82%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.30 ms →        2.32 ms   (+0.80%) |      64   →      52    (-18.75%) |      147.08 ms →      120.46 ms  (-18.10%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.53 s  →        2.48 s    (-1.98%) |      32   →      26    (-18.75%) |       80.81 s  →       64.36 s   (-20.36%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      103.09 ms →      129.66 ms  (+25.78%) |     361   →     270    (-25.21%) |       37.21 s  →       35.01 s    (-5.92%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       39.38 ms →       52.21 ms  (+32.59%) |     361   →     270    (-25.21%) |       14.22 s  →       14.10 s    (-0.84%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.94 μs →        2.06 μs   (+6.24%) |     361   →     270    (-25.21%) |      699.92 μs →      556.17 μs  (-20.54%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.58 μs →        1.73 μs   (+9.73%) |     361   →     270    (-25.21%) |      569.11 μs →      467.07 μs  (-17.93%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      328.45 ns →      380.89 ns  (+15.97%) |     361   →     270    (-25.21%) |      118.57 μs →      102.84 μs  (-13.27%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      384.92 ns →      455.84 ns  (+18.43%) |     361   →     270    (-25.21%) |      138.96 μs →      123.08 μs  (-11.43%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.34 ms →        7.43 ms   (+1.18%) |     361   →     270    (-25.21%) |        2.65 s  →        2.01 s   (-24.32%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       18.68 ms →       23.46 ms  (+25.62%) |     361   →     270    (-25.21%) |        6.74 s  →        6.33 s    (-6.05%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       18.84 ms →       23.27 ms  (+23.55%) |     722   →     540    (-25.21%) |       13.60 s  →       12.57 s    (-7.59%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |       29.17 ms →       35.08 ms  (+20.25%) |     361   →     270    (-25.21%) |       10.53 s  →        9.47 s   (-10.06%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        4.30 ms                             |     690                          |        2.97 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       22.32 μs                             |     690                          |       15.40 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                         6.08 ms            |                 514              |                         3.12 s             | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                        67.44 ns            |                 514              |                        34.67 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                         4.96 ms            |                 514              |                         2.55 s             | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                        54.17 ns            |                 514              |                        27.84 μs            | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      488.06 μs →      633.76 μs  (+29.85%) |     361   →     270    (-25.21%) |      176.19 ms →      171.11 ms   (-2.88%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        7.77 ms →        9.80 ms  (+26.17%) |     361   →     270    (-25.21%) |        2.80 s  →        2.65 s    (-5.63%) | 
  │ │ │ │   │ ├ sddk::transform                                         |       13.92 ms                             |     329                          |        4.58 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       19.31 μs                             |     329                          |        6.35 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       46.95 μs                             |     987                          |       46.34 ms                             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                        14.47 ms            |                 244              |                         3.53 s             | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                         4.82 ms            |                 732              |                         3.53 s             | 
- │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        9.13 ms →       10.55 ms  (+15.59%) |     361   →     270    (-25.21%) |        3.29 s  →        2.85 s   (-13.55%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        8.32 ms                             |     361                          |        3.00 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       27.64 μs                             |     361                          |        9.98 ms                             | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                        10.28 ms            |                 270              |                         2.77 s             | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                        48.43 ns            |                 270              |                        13.08 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                         9.16 ms            |                 270              |                         2.47 s             | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                        73.23 ns            |                 270              |                        19.77 μs            | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       64.28 ms →       34.88 ms  (-45.73%) |     361   →     270    (-25.21%) |       23.21 s  →        9.42 s   (-59.41%) | 
+ │ │ │ │   ├ sirius::residuals                                         |       13.24 ms →       13.90 ms   (+4.96%) |     349   →     261    (-25.21%) |        4.62 s  →        3.63 s   (-21.50%) | 
  │ │ │ │   │ ├ sddk::transform                                         |       12.28 ms                             |     335                          |        4.11 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       14.51 μs                             |     335                          |        4.86 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       39.21 μs                             |     670                          |       26.27 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                        12.51 ms            |                 252              |                         3.15 s             | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                         6.25 ms            |                 504              |                         3.15 s             | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.31 ms →        1.65 ms  (+25.41%) |     335   →     252    (-24.78%) |      439.90 ms →      415.00 ms   (-5.66%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       56.55 ms →       74.93 ms  (+32.51%) |      34   →      53    (+55.88%) |        1.92 s  →        3.97 s  (+106.56%) | 
  │ │ │ │     ├ sddk::transform                                         |       53.18 ms                             |      36                          |        1.91 s                              | 
  │ │ │ │     │ ├ sddk::transform|init                                  |       12.46 μs                             |      36                          |      448.39 μs                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       13.86 μs                             |      38                          |      526.72 μs                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                        49.41 ms            |                  80              |                         3.95 s             | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                        36.94 ms            |                 107              |                         3.95 s             | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      468.44 ns →      661.42 ns  (+41.20%) |      32   →      26    (-18.75%) |       14.99 μs →       17.20 μs  (+14.72%) | 
+ │ │ │ └ sirius::K_point_set::sync_band_energies                       |       32.53 μs →       29.35 μs   (-9.79%) |      32   →      26    (-18.75%) |        1.04 ms →      763.03 μs  (-26.70%) | 
+ │ │ ├ sirius::K_point_set::find_band_occupancies                      |      620.63 μs →      592.89 μs   (-4.47%) |      32   →      26    (-18.75%) |       19.86 ms →       15.42 ms  (-22.38%) | 
+ │ │ ├ sirius::Density::generate                                       |      780.88 ms →      766.54 ms   (-1.84%) |      32   →      26    (-18.75%) |       24.99 s  →       19.93 s   (-20.24%) | 
+ │ │ │ ├ sirius::Density::generate_valence                             |      402.85 ms →      401.85 ms   (-0.25%) |      32   →      26    (-18.75%) |       12.89 s  →       10.45 s   (-18.95%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.13 μs →        8.22 μs   (+1.19%) |      32   →      26    (-18.75%) |      260.01 μs →      213.78 μs  (-17.78%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.24 μs →        7.71 μs   (+6.53%) |      32   →      26    (-18.75%) |      231.53 μs →      200.41 μs  (-13.44%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |      100.00 ms →      100.19 ms   (+0.19%) |      32   →      26    (-18.75%) |        3.20 s  →        2.60 s   (-18.60%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.34 μs →        7.59 μs   (+3.46%) |      32   →      26    (-18.75%) |      234.86 μs →      197.44 μs  (-15.94%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.12 ms →        7.12 ms   (-0.04%) |      32   →      26    (-18.75%) |      227.88 ms →      185.07 ms  (-18.79%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       90.99 ms →       91.16 ms   (+0.18%) |      32   →      26    (-18.75%) |        2.91 s  →        2.37 s   (-18.60%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      579.22 ns →      722.62 ns  (+24.76%) |      32   →      26    (-18.75%) |       18.54 μs →       18.79 μs   (+1.36%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      161.80 ms →      162.35 ms   (+0.34%) |      32   →      26    (-18.75%) |        5.18 s  →        4.22 s   (-18.47%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.65 ms →        1.64 ms   (-0.49%) |      32   →      26    (-18.75%) |       52.83 ms →       42.72 ms  (-19.15%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |       88.30 ms →       88.30 ms   (+0.00%) |      32   →      26    (-18.75%) |        2.83 s  →        2.30 s   (-18.75%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.06 ms →       88.06 ms   (+0.00%) |      32   →      26    (-18.75%) |        2.82 s  →        2.29 s   (-18.75%) | 
+ │ │ │ ├ sirius::Field4D::symmetrize                                   |      285.44 ms →      272.65 ms   (-4.48%) |      32   →      26    (-18.75%) |        9.13 s  →        7.09 s   (-22.39%) | 
+ │ │ │ │ └ sirius::symmetrize_function|fpw                             |      285.44 ms →      272.64 ms   (-4.48%) |      32   →      26    (-18.75%) |        9.13 s  →        7.09 s   (-22.39%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       28.77 ms →       23.95 ms  (-16.76%) |      32   →      26    (-18.75%) |      920.70 ms →      622.68 ms  (-32.37%) | 
+ │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      228.60 ms →      224.40 ms   (-1.84%) |      32   →      26    (-18.75%) |        7.32 s  →        5.83 s   (-20.25%) | 
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       26.86 ms →       23.11 ms  (-13.96%) |      32   →      26    (-18.75%) |      859.46 ms →      600.83 ms  (-30.09%) | 
+ │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       81.29 ms →       81.52 ms   (+0.29%) |      32   →      26    (-18.75%) |        2.60 s  →        2.12 s   (-18.52%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        7.72 ms →        6.93 ms  (-10.19%) |      32   →      26    (-18.75%) |      246.93 ms →      180.19 ms  (-27.03%) | 
+ │ │ ├ sirius::Density::mix                                            |      225.22 ms →      216.43 ms   (-3.91%) |      32   →      26    (-18.75%) |        7.21 s  →        5.63 s   (-21.92%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      961.84 μs →      960.60 μs   (-0.13%) |      32   →      26    (-18.75%) |       30.78 ms →       24.98 ms  (-18.86%) | 
+ │ │ │ ├ sirius::Periodic_function|inner                               |       10.69 ms →       10.57 ms   (-1.20%) |     424   →     334    (-21.23%) |        4.53 s  →        3.53 s   (-22.17%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.36 ms →       10.35 ms   (-0.11%) |     424   →     334    (-21.23%) |        4.39 s  →        3.46 s   (-21.31%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.36 ms →       10.35 ms   (-0.11%) |     424   →     334    (-21.23%) |        4.39 s  →        3.46 s   (-21.31%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        6.20 ms →        6.74 ms   (+8.74%) |      32   →      26    (-18.75%) |      198.49 ms →      175.37 ms  (-11.65%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.39 ms →        5.90 ms   (+9.36%) |      32   →      26    (-18.75%) |      172.57 ms →      153.35 ms  (-11.14%) | 
+ │ │ ├ sirius::Potential::generate                                     |      570.12 ms →      585.56 ms   (+2.71%) |      32   →      26    (-18.75%) |       18.24 s  →       15.22 s   (-16.55%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |      137.25 ms →      136.95 ms   (-0.21%) |      32   →      26    (-18.75%) |        4.39 s  →        3.56 s   (-18.92%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        5.16 ms →       17.05 ms (+230.13%) |      32   →      26    (-18.75%) |      165.22 ms →      443.17 ms (+168.23%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner                             |       10.33 ms →       10.21 ms   (-1.11%) |      32   →      26    (-18.75%) |      330.47 ms →      265.53 ms  (-19.65%) | 
+ │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.09 ms →        9.96 ms   (-1.35%) |      32   →      26    (-18.75%) |      322.93 ms →      258.84 ms  (-19.85%) | 
+ │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.09 ms →        9.95 ms   (-1.35%) |      32   →      26    (-18.75%) |      322.91 ms →      258.83 ms  (-19.85%) | 
+ │ │ │ ├ sirius::Periodic_function::add                                |      554.95 μs →      557.23 μs   (+0.41%) |      64   →      52    (-18.75%) |       35.52 ms →       28.98 ms  (-18.42%) | 
+ │ │ │ ├ sirius::Potential::xc                                         |       44.98 ms →       49.02 ms   (+8.98%) |      32   →      26    (-18.75%) |        1.44 s  →        1.27 s   (-11.46%) | 
+ │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       44.98 ms →       46.66 ms   (+3.74%) |      32   →      26    (-18.75%) |        1.44 s  →        1.21 s   (-15.71%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function                          |        1.22 ms →        3.01 ms (+147.00%) |      64   →      52    (-18.75%) |       77.91 ms →      156.36 ms (+100.68%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |       11.77 ms →        5.55 ms  (-52.87%) |      32   →      26    (-18.75%) |      376.73 ms →      144.26 ms  (-61.71%) | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        7.72 ms →        6.50 ms  (-15.82%) |      32   →      26    (-18.75%) |      246.97 ms →      168.93 ms  (-31.60%) | 
+ │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.89 ms →       90.87 ms   (-0.03%) |      32   →      26    (-18.75%) |        2.91 s  →        2.36 s   (-18.77%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      286.88 ms →      299.80 ms   (+4.51%) |      32   →      26    (-18.75%) |        9.18 s  →        7.79 s   (-15.09%) | 
+ │ │ ├ sirius::Field4D::symmetrize                                     |      287.52 ms →      280.11 ms   (-2.58%) |      32   →      26    (-18.75%) |        9.20 s  →        7.28 s   (-20.85%) | 
+ │ │ │ └ sirius::symmetrize_function|fpw                               |      287.52 ms →      280.10 ms   (-2.58%) |      32   →      26    (-18.75%) |        9.20 s  →        7.28 s   (-20.85%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       30.77 ms →       27.37 ms  (-11.06%) |      32   →      26    (-18.75%) |      984.75 ms →      711.65 ms  (-27.73%) | 
+ │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      228.00 ms →      224.69 ms   (-1.45%) |      32   →      26    (-18.75%) |        7.30 s  →        5.84 s   (-19.93%) | 
+ │ │ │   └ sddk::Gvec_shells::remap_backward                           |       27.61 ms →       24.21 ms  (-12.32%) |      32   →      26    (-18.75%) |      883.47 ms →      629.37 ms  (-28.76%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.46 ms →        5.66 ms   (+3.55%) |      32   →      26    (-18.75%) |      174.87 ms →      147.13 ms  (-15.86%) | 
+ │ │ ├ sirius::Periodic_function|inner                                 |       10.37 ms →       10.35 ms   (-0.18%) |     224   →     182    (-18.75%) |        2.32 s  →        1.88 s   (-18.89%) | 
+ │ │ │ └ sirius::Periodic_function|inner_local                         |        9.82 ms →        9.98 ms   (+1.57%) |     224   →     182    (-18.75%) |        2.20 s  →        1.82 s   (-17.47%) | 
+ │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.82 ms →        9.98 ms   (+1.57%) |     224   →     182    (-18.75%) |        2.20 s  →        1.82 s   (-17.48%) | 
+ │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.60 ms →       11.16 ms   (+5.31%) |      96   →      78    (-18.75%) |        1.02 s  →      870.43 ms  (-14.44%) | 
+ │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.16 ms →       10.75 ms   (+5.73%) |      96   →      78    (-18.75%) |      975.75 ms →      838.21 ms  (-14.10%) | 
+ │ │ ├ sirius::Periodic_function::integrate                            |       10.75 ms →       10.14 ms   (-5.65%) |      32   →      26    (-18.75%) |      344.01 ms →      263.72 ms  (-23.34%) | 
+ │ │ └ sirius::Density::get_magnetisation                              |      113.99 μs →      109.93 μs   (-3.56%) |      32   →      26    (-18.75%) |        3.65 ms →        2.86 ms  (-21.65%) | 
+ │ │   └ sirius::Density::compute_atomic_mag_mom                       |      108.76 μs →      104.59 μs   (-3.83%) |      32   →      26    (-18.75%) |        3.48 ms →        2.72 ms  (-21.86%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.05 ms →        5.03 ms   (-0.39%) |       2   →       2              |       10.11 ms →       10.07 ms   (-0.39%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.11 ms →        9.95 ms   (-1.65%) |       6   →       6              |       60.69 ms →       59.69 ms   (-1.65%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        9.65 ms →        9.85 ms   (+2.09%) |       6   →       6              |       57.88 ms →       59.08 ms   (+2.09%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        9.65 ms →        9.85 ms   (+2.09%) |       6   →       6              |       57.87 ms →       59.08 ms   (+2.09%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.48 ms →       10.65 ms   (+1.63%) |       3   →       3              |       31.44 ms →       31.95 ms   (+1.63%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.01 ms →       10.47 ms   (+4.57%) |       3   →       3              |       30.04 ms →       31.41 ms   (+4.57%) | 
  ├ sirius::Periodic_function|inner                                     |       10.06 ms →        9.68 ms   (-3.82%) |       2   →       2              |       20.12 ms →       19.35 ms   (-3.82%) | 
  │ └ sirius::Periodic_function|inner_local                             |        9.63 ms →        9.63 ms   (+0.02%) |       2   →       2              |       19.26 ms →       19.26 ms   (+0.02%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.63 ms →        9.63 ms   (+0.02%) |       2   →       2              |       19.26 ms →       19.26 ms   (+0.02%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.52 ms →       10.48 ms   (-0.42%) |       1   →       1              |       10.52 ms →       10.48 ms   (-0.42%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.02 ms →       10.46 ms   (+4.47%) |       1   →       1              |       10.02 ms →       10.46 ms   (+4.47%) | 
+ └ sirius::finalize                                                    |      218.21 ms →      191.57 ms  (-12.21%) |       1   →       1              |      218.21 ms →      191.57 ms  (-12.21%) | 
  ====================================================================================================================================================================================================
```
