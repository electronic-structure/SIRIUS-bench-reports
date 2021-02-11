# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs dd26b4c3a8b510264c2723458c0ccaf5eeca6037
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      169.28 s  →      122.85 s   (-27.43%) |       1   →       1              |      169.28 s  →      122.85 s   (-27.43%) | 
  ├ sirius::initialize                                                  |        2.70 s  →        2.75 s    (+1.90%) |       1   →       1              |        2.70 s  →        2.75 s    (+1.90%) | 
  ├ sirius::Simulation_context::initialize                              |        3.63 s  →        3.85 s    (+5.82%) |       1   →       1              |        3.63 s  →        3.85 s    (+5.82%) | 
- │ ├ sirius::Simulation_context::init_comm                             |       32.66 ms →       43.50 ms  (+33.19%) |       1   →       1              |       32.66 ms →       43.50 ms  (+33.19%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      820.04 ms →        1.06 s   (+29.82%) |       1   →       1              |      820.04 ms →        1.06 s   (+29.82%) | 
- │ │ ├ sirius::Atom_type::init                                         |      398.54 ms →      521.33 ms  (+30.81%) |       2   →       2              |      797.08 ms →        1.04 s   (+30.81%) | 
  │ │ └ sirius::Unit_cell::update                                       |       22.87 ms →       21.69 ms   (-5.16%) |       1   →       1              |       22.87 ms →       21.69 ms   (-5.16%) | 
+ │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.27 ms →        5.41 ms  (-13.71%) |       1   →       1              |        6.27 ms →        5.41 ms  (-13.71%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       16.56 ms →       16.25 ms   (-1.90%) |       1   →       1              |       16.56 ms →       16.25 ms   (-1.90%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       16.54 ms →       16.22 ms   (-1.94%) |       1   →       1              |       16.54 ms →       16.22 ms   (-1.94%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.15 ms →        4.16 ms   (+0.17%) |       1   →       1              |        4.15 ms →        4.16 ms   (+0.17%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.34 ms →        2.34 ms   (+0.15%) |       1   →       1              |        2.34 ms →        2.34 ms   (+0.15%) | 
- │ │       └ sirius::Unit_cell_symmetry|mag                            |      100.96 μs →      111.73 μs  (+10.67%) |       1   →       1              |      100.96 μs →      111.73 μs  (+10.67%) | 
  │ └ sirius::Simulation_context::update                                |        2.74 s  →        2.69 s    (-1.59%) |       1   →       1              |        2.74 s  →        2.69 s    (-1.59%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.81 ms →       10.84 ms   (+0.33%) |       1   →       1              |       10.81 ms →       10.84 ms   (+0.33%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.36 ms →        4.43 ms   (+1.66%) |       1   →       1              |        4.36 ms →        4.43 ms   (+1.66%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.41 ms →        6.38 ms   (-0.54%) |       1   →       1              |        6.41 ms →        6.38 ms   (-0.54%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.39 ms →        6.35 ms   (-0.61%) |       1   →       1              |        6.39 ms →        6.35 ms   (-0.61%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.89 ms →        3.83 ms   (-1.36%) |       1   →       1              |        3.89 ms →        3.83 ms   (-1.36%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.34 ms   (+0.36%) |       1   →       1              |        2.33 ms →        2.34 ms   (+0.36%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      104.50 μs →      103.94 μs   (-0.53%) |       1   →       1              |      104.50 μs →      103.94 μs   (-0.53%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       65.46 ms →       66.93 ms   (+2.25%) |       2   →       2              |      130.92 ms →      133.87 ms   (+2.25%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.15 ms →        5.15 ms   (+0.04%) |       2   →       2              |       10.29 ms →       10.30 ms   (+0.04%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.47 ms →        4.52 ms   (+1.13%) |       1   →       1              |        4.47 ms →        4.52 ms   (+1.13%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.74 ms →       21.73 ms   (-0.02%) |       2   →       2              |       43.47 ms →       43.46 ms   (-0.02%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.79 ms →       14.80 ms   (+0.06%) |       2   →       2              |       29.58 ms →       29.60 ms   (+0.06%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.71 ms →       19.70 ms   (-0.07%) |       4   →       4              |       78.84 ms →       78.79 ms   (-0.07%) | 
  │   ├ sddk::Gvec::init                                                |      179.51 ms →      173.14 ms   (-3.55%) |       2   →       2              |      359.03 ms →      346.29 ms   (-3.55%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      133.43 ms →      130.87 ms   (-1.92%) |       2   →       2              |      266.87 ms →      261.74 ms   (-1.92%) | 
  │   ├ sddk::Gvec_shells                                               |      183.53 ms →      184.12 ms   (+0.32%) |       1   →       1              |      183.53 ms →      184.12 ms   (+0.32%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.32 ms →        1.32 ms   (+0.33%) |       1   →       1              |        1.32 ms →        1.32 ms   (+0.33%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      294.00 ms →      293.77 ms   (-0.08%) |       2   →       2              |      588.00 ms →      587.54 ms   (-0.08%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       39.71 ms →       35.79 ms   (-9.86%) |       1   →       1              |       39.71 ms →       35.79 ms   (-9.86%) | 
- │ ├ sirius::K_point::K_point                                          |        3.19 μs →        4.43 μs  (+38.98%) |       4   →       4              |       12.75 μs →       17.72 μs  (+38.98%) | 
  │ └ sirius::K_point_set::initialize                                   |       39.61 ms →       35.68 ms   (-9.92%) |       1   →       1              |       39.61 ms →       35.68 ms   (-9.92%) | 
  │   └ sirius::K_point::initialize                                     |       39.52 ms →       35.57 ms   (-9.99%) |       1   →       1              |       39.52 ms →       35.57 ms   (-9.99%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       20.37 ms →       18.36 ms   (-9.83%) |       1   →       1              |       20.37 ms →       18.36 ms   (-9.83%) | 
+ │     │ └ sddk::Gvec::init                                            |        8.93 ms →        8.03 ms  (-10.09%) |       1   →       1              |        8.93 ms →        8.03 ms  (-10.09%) | 
+ │     ├ sddk::matrix_storage::matrix_storage                          |        9.90 μs →        8.36 μs  (-15.59%) |       1   →       1              |        9.90 μs →        8.36 μs  (-15.59%) | 
  │     └ sirius::K_point::update                                       |       13.29 ms →       12.37 ms   (-6.91%) |       1   →       1              |       13.29 ms →       12.37 ms   (-6.91%) | 
  │       └ sirius::Beta_projectors                                     |        6.11 ms →        6.15 ms   (+0.60%) |       1   →       1              |        6.11 ms →        6.15 ms   (+0.60%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.50 ms →        3.56 ms   (+1.73%) |       1   →       1              |        3.50 ms →        3.56 ms   (+1.73%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.31 ms →        5.29 ms   (-0.31%) |       2   →       2              |       10.61 ms →       10.58 ms   (-0.31%) | 
  ├ sirius::Potential                                                   |      168.99 ms →      153.01 ms   (-9.46%) |       1   →       1              |      168.99 ms →      153.01 ms   (-9.46%) | 
+ │ ├ sirius::Smooth_periodic_function                                  |        5.86 ms →        5.78 ms   (-1.42%) |       6   →       5    (-16.67%) |       35.18 ms →       28.90 ms  (-17.85%) | 
  │ └ sirius::Potential::update                                         |      133.06 ms →      123.34 ms   (-7.31%) |       1   →       1              |      133.06 ms →      123.34 ms   (-7.31%) | 
  │   └ sirius::Potential::generate_local_potential                     |      132.26 ms →      122.60 ms   (-7.31%) |       1   →       1              |      132.26 ms →      122.60 ms   (-7.31%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |      125.36 ms →      108.30 ms  (-13.61%) |       1   →       1              |      125.36 ms →      108.30 ms  (-13.61%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        6.35 ms →       10.04 ms  (+58.26%) |       1   →       1              |        6.35 ms →       10.04 ms  (+58.26%) | 
  ├ sirius::Density                                                     |      140.88 ms →      129.25 ms   (-8.25%) |       1   →       1              |      140.88 ms →      129.25 ms   (-8.25%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.30 ms →        5.19 ms   (-1.97%) |       2   →       2              |       10.59 ms →       10.38 ms   (-1.97%) | 
  │ └ sirius::Density::update                                           |      130.01 ms →      118.59 ms   (-8.78%) |       1   →       1              |      130.01 ms →      118.59 ms   (-8.78%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      129.57 ms →      118.13 ms   (-8.83%) |       1   →       1              |      129.57 ms →      118.13 ms   (-8.83%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |                       107.01 μs            |                   1              |                       107.01 μs            | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |      123.65 ms →      110.17 ms  (-10.91%) |       1   →       1              |      123.65 ms →      110.17 ms  (-10.91%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        5.47 ms →        7.39 ms  (+35.01%) |       1   →       1              |        5.47 ms →        7.39 ms  (+35.01%) | 
  ├ sirius::Density::initial_density                                    |      175.57 ms →      163.61 ms   (-6.81%) |       1   →       1              |      175.57 ms →      163.61 ms   (-6.81%) | 
+ │ ├ sirius::Simulation_context::make_periodic_function                |      122.29 ms →      109.52 ms  (-10.45%) |       1   →       1              |      122.29 ms →      109.52 ms  (-10.45%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.31 ms →        5.49 ms   (+3.38%) |       2   →       2              |       10.63 ms →       10.99 ms   (+3.38%) | 
  │ └ sirius::Periodic_function::integrate                              |        9.73 ms →        9.80 ms   (+0.66%) |       1   →       1              |        9.73 ms →        9.80 ms   (+0.66%) | 
  ├ sirius::Potential::generate                                         |      584.32 ms →      560.21 ms   (-4.13%) |       1   →       1              |      584.32 ms →      560.21 ms   (-4.13%) | 
  │ ├ sirius::Potential::poisson                                        |      137.60 ms →      127.95 ms   (-7.02%) |       1   →       1              |      137.60 ms →      127.95 ms   (-7.02%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.26 ms →        8.21 ms  (+56.21%) |       1   →       1              |        5.26 ms →        8.21 ms  (+56.21%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.81 ms →       10.70 ms   (-1.04%) |       1   →       1              |       10.81 ms →       10.70 ms   (-1.04%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |       10.71 ms →       10.38 ms   (-3.10%) |       1   →       1              |       10.71 ms →       10.38 ms   (-3.10%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |       10.71 ms →       10.38 ms   (-3.10%) |       1   →       1              |       10.71 ms →       10.38 ms   (-3.10%) | 
+ │ ├ sirius::Periodic_function::add                                    |      548.10 μs →      456.90 μs  (-16.64%) |       2   →       2              |        1.10 ms →      913.79 μs  (-16.64%) | 
+ │ ├ sirius::Potential::xc                                             |       51.96 ms →       31.77 ms  (-38.87%) |       1   →       1              |       51.96 ms →       31.77 ms  (-38.87%) | 
+ │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.96 ms →       29.44 ms  (-43.35%) |       1   →       1              |       51.96 ms →       29.44 ms  (-43.35%) | 
+ │ │   ├ sirius::Smooth_periodic_function                              |        5.72 ms →        5.59 ms   (-2.29%) |       2   →       1    (-50.00%) |       11.45 ms →        5.59 ms  (-51.14%) | 
  │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        5.55 ms                             |       1                          |        5.55 ms                             | 
  │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                    |                         8.49 ms            |                   2              |                        16.98 ms            | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.85 ms →        4.91 ms  (-16.02%) |       1   →       1              |        5.85 ms →        4.91 ms  (-16.02%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.64 ms →       93.60 ms   (+1.04%) |       1   →       1              |       92.64 ms →       93.60 ms   (+1.04%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      293.81 ms →      299.70 ms   (+2.01%) |       1   →       1              |      293.81 ms →      299.70 ms   (+2.01%) | 
- ├ sirius::Hamiltonian0                                                |        8.38 ms →       12.14 ms  (+44.75%) |       1   →       1              |        8.38 ms →       12.14 ms  (+44.75%) | 
  │ ├ sirius::Local_operator                                            |        8.03 ms →        8.15 ms   (+1.50%) |       1   →       1              |        8.03 ms →        8.15 ms   (+1.50%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.79 ms →        4.76 ms   (-0.67%) |       1   →       1              |        4.79 ms →        4.76 ms   (-0.67%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.31 ms →        2.47 ms   (+6.95%) |       1   →       1              |        2.31 ms →        2.47 ms   (+6.95%) | 
  │ ├ sirius::Non_local_operator                                        |       62.95 μs →       63.18 μs   (+0.36%) |       2   →       2              |      125.91 μs →      126.37 μs   (+0.36%) | 
- │ ├ sirius::D_operator::initialize                                    |      100.78 μs →        1.31 ms (+1197.56%) |       1   →       1              |      100.78 μs →        1.31 ms (+1197.56%) | 
- │ └ sirius::Q_operator::initialize                                    |       76.52 μs →        2.50 ms (+3163.32%) |       1   →       1              |       76.52 μs →        2.50 ms (+3163.32%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.85 s  →        1.87 s    (+0.73%) |       1   →       1              |        1.85 s  →        1.87 s    (+0.73%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.70 ms →       18.68 ms   (-0.11%) |       1   →       1              |       18.70 ms →       18.68 ms   (-0.11%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      205.31 μs →      185.19 μs   (-9.80%) |       1   →       1              |      205.31 μs →      185.19 μs   (-9.80%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       18.49 ms →       18.49 ms   (-0.01%) |       1   →       1              |       18.49 ms →       18.49 ms   (-0.01%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.84 s  →        1.85 s    (+0.58%) |       1   →       1              |        1.84 s  →        1.85 s    (+0.58%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      128.23 ms →      130.37 ms   (+1.67%) |       4   →       4              |      512.93 ms →      521.49 ms   (+1.67%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       52.26 ms →       51.98 ms   (-0.54%) |       1   →       1              |       52.26 ms →       51.98 ms   (-0.54%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.23 ms →       20.99 ms   (-1.13%) |       1   →       1              |       21.23 ms →       20.99 ms   (-1.13%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      634.52 ms →      634.60 ms   (+0.01%) |       1   →       1              |      634.52 ms →      634.60 ms   (+0.01%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      297.45 ms →      297.60 ms   (+0.05%) |       1   →       1              |      297.45 ms →      297.60 ms   (+0.05%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.46 μs →        3.11 μs  (-10.09%) |       1   →       1              |        3.46 μs →        3.11 μs  (-10.09%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.58 μs →        2.03 μs  (-21.41%) |       1   →       1              |        2.58 μs →        2.03 μs  (-21.41%) | 
+ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      514.00 ns →      385.00 ns  (-25.10%) |       1   →       1              |      514.00 ns →      385.00 ns  (-25.10%) | 
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      617.00 ns →      534.00 ns  (-13.45%) |       1   →       1              |      617.00 ns →      534.00 ns  (-13.45%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.21 ms →        9.23 ms   (+0.16%) |       1   →       1              |        9.21 ms →        9.23 ms   (+0.16%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      120.75 ms →      120.69 ms   (-0.05%) |       1   →       1              |      120.75 ms →      120.69 ms   (-0.05%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      103.54 ms →      103.52 ms   (-0.02%) |       2   →       2              |      207.07 ms →      207.04 ms   (-0.02%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       38.37 ms →       40.25 ms   (+4.89%) |       2   →       2              |       76.74 ms →       80.50 ms   (+4.89%) | 
  │ │ │ ├ sddk::inner                                                   |       37.83 ms                             |       2                          |       75.66 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       23.38 μs                             |       2                          |       46.76 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        39.67 ms            |                   2              |                        79.34 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        83.50 ns            |                   2              |                       167.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        39.19 ms            |                   2              |                        78.38 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                       335.00 ns            |                   2              |                       670.00 ns            | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       56.56 ms →       57.28 ms   (+1.26%) |       1   →       1              |       56.56 ms →       57.28 ms   (+1.26%) | 
  │ │ ├ sddk::transform                                                 |       31.53 ms                             |       1                          |       31.53 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       11.91 μs                             |       1                          |       11.91 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       12.00 μs                             |       1                          |       12.00 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                        30.76 ms            |                   1              |                        30.76 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                        30.75 ms            |                   1              |                        30.75 ms            | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      563.00 ns →      438.00 ns  (-22.20%) |       1   →       1              |      563.00 ns →      438.00 ns  (-22.20%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      158.59 s  →      112.32 s   (-29.18%) |       1   →       1              |      158.59 s  →      112.32 s   (-29.18%) | 
+ │ ├ sirius::Smooth_periodic_function                                  |        5.85 ms →        5.20 ms  (-11.03%) |      19   →      18     (-5.26%) |      111.14 ms →       93.68 ms  (-15.71%) | 
  │ ├ sirius::Density                                                   |                       128.16 ms            |                   1              |                       128.16 ms            | 
  │ │ ├ sirius::Smooth_periodic_function                                |                         5.21 ms            |                   2              |                        10.41 ms            | 
  │ │ └ sirius::Density::update                                         |                       117.47 ms            |                   1              |                       117.47 ms            | 
  │ │   └ sirius::Density::generate_pseudo_core_charge_density          |                       117.04 ms            |                   1              |                       117.04 ms            | 
  │ │     ├ sirius::rho_core_ri_pseudo|values                           |                       130.25 μs            |                   1              |                       130.25 μs            | 
  │ │     ├ sirius::Simulation_context::make_periodic_function          |                       110.42 ms            |                   1              |                       110.42 ms            | 
  │ │     └ sirius::Smooth_periodic_function::fft_transform             |                         6.04 ms            |                   1              |                         6.04 ms            | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.73 s  →        4.66 s    (-1.59%) |      33   →      24    (-27.27%) |      156.18 s  →      111.78 s   (-28.43%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        4.45 ms →        8.07 ms  (+81.24%) |      33   →      24    (-27.27%) |      146.89 ms →      193.62 ms  (+31.81%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        4.08 ms →        4.11 ms   (+0.68%) |      33   →      24    (-27.27%) |      134.58 ms →       98.55 ms  (-26.78%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function                            |      986.29 μs →      934.19 μs   (-5.28%) |      33   →      24    (-27.27%) |       32.55 ms →       22.42 ms  (-31.11%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.20 ms →        2.25 ms   (+2.04%) |      33   →      24    (-27.27%) |       72.75 ms →       53.99 ms  (-25.79%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |       65.00 μs →       64.56 μs   (-0.67%) |      66   →      48    (-27.27%) |        4.29 ms →        3.10 ms  (-27.76%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |       97.73 μs →        1.29 ms (+1216.28%) |      33   →      24    (-27.27%) |        3.23 ms →       30.87 ms (+857.29%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       76.32 μs →        2.48 ms (+3153.80%) |      33   →      24    (-27.27%) |        2.52 ms →       59.60 ms (+2266.40%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.72 s  →        2.65 s    (-2.64%) |      33   →      24    (-27.27%) |       89.91 s  →       63.66 s   (-29.19%) | 
+ │ │ │ ├ sirius::Hamiltonian_k                                         |      161.99 μs →      158.85 μs   (-1.94%) |      33   →      24    (-27.27%) |        5.35 ms →        3.81 ms  (-28.68%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      156.28 μs →      150.42 μs   (-3.75%) |      33   →      24    (-27.27%) |        5.16 ms →        3.61 ms  (-30.00%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.19 μs →        4.51 μs   (+7.42%) |      33   →      24    (-27.27%) |      138.42 μs →      108.14 μs  (-21.87%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.66 s  →        2.47 s    (-7.02%) |      33   →      24    (-27.27%) |       87.69 s  →       59.30 s   (-32.38%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |      105.89 ms →      100.73 ms   (-4.87%) |      33   →      24    (-27.27%) |        3.49 s  →        2.42 s   (-30.81%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        9.18 ms →        8.43 ms   (-8.18%) |     198   →     144    (-27.27%) |        1.82 s  →        1.21 s   (-33.22%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        5.96 ms →        5.91 ms   (-0.91%) |      33   →      24    (-27.27%) |      196.84 ms →      141.85 ms  (-27.94%) | 
+ │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      357.30 μs →      347.99 μs   (-2.61%) |      33   →      24    (-27.27%) |       11.79 ms →        8.35 ms  (-29.17%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.30 ms →        2.29 ms   (-0.32%) |      66   →      48    (-27.27%) |      151.64 ms →      109.94 ms  (-27.50%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.51 s  →        2.33 s    (-7.22%) |      33   →      24    (-27.27%) |       82.82 s  →       55.88 s   (-32.52%) | 
+ │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      103.26 ms →      102.37 ms   (-0.87%) |     362   →     323    (-10.77%) |       37.38 s  →       33.06 s   (-11.55%) | 
+ │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       39.85 ms →       39.16 ms   (-1.73%) |     362   →     323    (-10.77%) |       14.42 s  →       12.65 s   (-12.32%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.84 μs →        1.63 μs  (-11.60%) |     362   →     323    (-10.77%) |      666.02 μs →      525.32 μs  (-21.13%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.56 μs →        1.40 μs  (-10.51%) |     362   →     323    (-10.77%) |      565.46 μs →      451.51 μs  (-20.15%) | 
! │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      349.00 ns →      352.78 ns   (+1.08%) |     362   →     323    (-10.77%) |      126.34 μs →      113.95 μs   (-9.81%) | 
! │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      448.67 ns →      482.17 ns   (+7.47%) |     362   →     323    (-10.77%) |      162.42 μs →      155.74 μs   (-4.11%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.35 ms →        7.34 ms   (-0.14%) |     362   →     323    (-10.77%) |        2.66 s  →        2.37 s   (-10.90%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       18.31 ms →       18.29 ms   (-0.10%) |     362   →     323    (-10.77%) |        6.63 s  →        5.91 s   (-10.86%) | 
+ │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       18.87 ms →       18.78 ms   (-0.48%) |     724   →     646    (-10.77%) |       13.66 s  →       12.13 s   (-11.20%) | 
+ │ │ │ │   ├ sddk::orthogonalize                                       |       34.10 ms →       31.09 ms   (-8.83%) |     362   →     323    (-10.77%) |       12.34 s  →       10.04 s   (-18.65%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        4.30 ms                             |     691                          |        2.97 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       21.47 μs                             |     691                          |       14.84 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                         4.78 ms            |                 622              |                         2.98 s             | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                       115.20 ns            |                 622              |                        71.65 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                         3.67 ms            |                 622              |                         2.29 s             | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                       197.68 ns            |                 622              |                       122.96 μs            | 
+ │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |        5.40 ms →        4.97 ms   (-8.04%) |     362   →     323    (-10.77%) |        1.96 s  →        1.60 s   (-17.95%) | 
+ │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        7.86 ms →        7.49 ms   (-4.71%) |     362   →     323    (-10.77%) |        2.84 s  →        2.42 s   (-14.97%) | 
  │ │ │ │   │ ├ sddk::transform                                         |       13.89 ms                             |     329                          |        4.57 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       17.80 μs                             |     329                          |        5.86 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       33.28 μs                             |     987                          |       32.85 ms                             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                        10.17 ms            |                 299              |                         3.04 s             | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                         3.39 ms            |                 897              |                         3.04 s             | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        9.26 ms →        8.09 ms  (-12.56%) |     362   →     323    (-10.77%) |        3.35 s  →        2.61 s   (-21.98%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        8.35 ms                             |     362                          |        3.02 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       28.00 μs                             |     362                          |       10.13 ms                             | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                         7.67 ms            |                 323              |                         2.48 s             | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                        93.65 ns            |                 323              |                        30.25 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                         6.56 ms            |                 323              |                         2.12 s             | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                       177.98 ns            |                 323              |                        57.49 μs            | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       63.77 ms →       12.18 ms  (-80.90%) |     362   →     323    (-10.77%) |       23.09 s  →        3.93 s   (-82.96%) | 
+ │ │ │ │   ├ sirius::residuals                                         |       13.41 ms →        7.46 ms  (-44.32%) |     350   →     311    (-11.14%) |        4.69 s  →        2.32 s   (-50.53%) | 
  │ │ │ │   │ ├ sddk::transform                                         |       12.42 ms                             |     336                          |        4.17 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       14.46 μs                             |     336                          |        4.86 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       35.90 μs                             |     672                          |       24.13 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                         6.21 ms            |                 299              |                         1.86 s             | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                         3.11 ms            |                 598              |                         1.86 s             | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.34 ms →        1.13 ms  (-14.99%) |     336   →     299    (-11.01%) |      448.58 ms →      339.33 ms  (-24.35%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       55.69 ms →       43.03 ms  (-22.74%) |      35   →      90   (+157.14%) |        1.95 s  →        3.87 s   (+98.67%) | 
  │ │ │ │     ├ sddk::transform                                         |       52.45 ms                             |      37                          |        1.94 s                              | 
  │ │ │ │     │ ├ sddk::transform|init                                  |       12.18 μs                             |      37                          |      450.72 μs                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       14.01 μs                             |      39                          |      546.54 μs                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                        24.54 ms            |                 156              |                         3.83 s             | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                        17.24 ms            |                 222              |                         3.83 s             | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      460.91 ns →      396.37 ns  (-14.00%) |      33   →      24    (-27.27%) |       15.21 μs →        9.51 μs  (-37.46%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       31.68 μs →        2.30 ms (+7171.52%) |      33   →      24    (-27.27%) |        1.05 ms →       55.28 ms (+5188.38%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |      608.08 μs →       59.64 ms (+9707.78%) |      33   →      24    (-27.27%) |       20.07 ms →        1.43 s  (+7032.93%) | 
+ │ │ ├ sirius::Density::generate                                       |      786.74 ms →      787.30 ms   (+0.07%) |      33   →      24    (-27.27%) |       25.96 s  →       18.90 s   (-27.22%) | 
+ │ │ │ ├ sirius::Density::generate_valence                             |      401.36 ms →      436.14 ms   (+8.67%) |      33   →      24    (-27.27%) |       13.24 s  →       10.47 s   (-20.97%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        7.74 μs →        2.45 μs  (-68.30%) |      33   →      24    (-27.27%) |      255.48 μs →       58.90 μs  (-76.94%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.03 μs →        2.17 μs  (-69.17%) |      33   →      24    (-27.27%) |      232.10 μs →       52.05 μs  (-77.58%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       99.72 ms →      127.25 ms  (+27.61%) |      33   →      24    (-27.27%) |        3.29 s  →        3.05 s    (-7.19%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.07 μs →        8.81 μs  (+24.70%) |      33   →      24    (-27.27%) |      233.17 μs →      211.46 μs   (-9.31%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.12 ms →        7.12 ms   (-0.09%) |      33   →      24    (-27.27%) |      235.10 ms →      170.83 ms  (-27.34%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       90.71 ms →       91.17 ms   (+0.51%) |      33   →      24    (-27.27%) |        2.99 s  →        2.19 s   (-26.90%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      621.70 ns →      524.00 ns  (-15.71%) |      33   →      24    (-27.27%) |       20.52 μs →       12.58 μs  (-38.70%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      163.27 ms →      164.13 ms   (+0.53%) |      33   →      24    (-27.27%) |        5.39 s  →        3.94 s   (-26.89%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.65 ms →        1.64 ms   (-0.52%) |      33   →      24    (-27.27%) |       54.39 ms →       39.35 ms  (-27.65%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |       88.31 ms →       88.41 ms   (+0.11%) |      33   →      24    (-27.27%) |        2.91 s  →        2.12 s   (-27.19%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.08 ms →       88.18 ms   (+0.12%) |      33   →      24    (-27.27%) |        2.91 s  →        2.12 s   (-27.19%) | 
+ │ │ │ ├ sirius::Field4D::symmetrize                                   |      292.42 ms →      257.79 ms  (-11.84%) |      33   →      24    (-27.27%) |        9.65 s  →        6.19 s   (-35.89%) | 
+ │ │ │ │ └ sirius::symmetrize_function|fpw                             |      292.42 ms →      257.78 ms  (-11.85%) |      33   →      24    (-27.27%) |        9.65 s  →        6.19 s   (-35.89%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       29.06 ms →       25.21 ms  (-13.25%) |      33   →      24    (-27.27%) |      958.98 ms →      605.01 ms  (-36.91%) | 
+ │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      235.24 ms →      206.96 ms  (-12.02%) |      33   →      24    (-27.27%) |        7.76 s  →        4.97 s   (-36.02%) | 
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       26.91 ms →       24.47 ms   (-9.07%) |      33   →      24    (-27.27%) |      888.03 ms →      587.27 ms  (-33.87%) | 
+ │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       81.21 ms →       81.58 ms   (+0.46%) |      33   →      24    (-27.27%) |        2.68 s  →        1.96 s   (-26.94%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        8.19 ms →        8.12 ms   (-0.89%) |      33   →      24    (-27.27%) |      270.42 ms →      194.92 ms  (-27.92%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |                        10.84 ms            |                 216              |                         2.34 s             | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |                        10.32 ms            |                 216              |                         2.23 s             | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |                        10.32 ms            |                 216              |                         2.23 s             | 
+ │ │ ├ sirius::Density::mix                                            |      232.85 ms →      159.90 ms  (-31.33%) |      33   →      24    (-27.27%) |        7.68 s  →        3.84 s   (-50.06%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      931.77 μs →        1.11 ms  (+19.41%) |      33   →      24    (-27.27%) |       30.75 ms →       26.70 ms  (-13.16%) | 
+ │ │ │ ├ sirius::Periodic_function|inner                               |       11.19 ms →       10.64 ms   (-4.93%) |     439   →     304    (-30.75%) |        4.91 s  →        3.23 s   (-34.17%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.85 ms →        9.76 ms  (-10.02%) |     439   →     304    (-30.75%) |        4.76 s  →        2.97 s   (-37.69%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.85 ms →        9.76 ms  (-10.02%) |     439   →     304    (-30.75%) |        4.76 s  →        2.97 s   (-37.69%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        7.35 ms →        6.57 ms  (-10.73%) |      33   →      24    (-27.27%) |      242.70 ms →      157.58 ms  (-35.07%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        6.54 ms →        5.47 ms  (-16.35%) |      33   →      24    (-27.27%) |      215.83 ms →      131.30 ms  (-39.17%) | 
+ │ │ ├ sirius::Potential::generate                                     |      568.79 ms →      545.62 ms   (-4.07%) |      33   →      24    (-27.27%) |       18.77 s  →       13.09 s   (-30.24%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |      137.39 ms →      127.61 ms   (-7.11%) |      33   →      24    (-27.27%) |        4.53 s  →        3.06 s   (-32.45%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        5.34 ms →        8.28 ms  (+54.94%) |      33   →      24    (-27.27%) |      176.32 ms →      198.68 ms  (+12.68%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner                             |       10.85 ms →       10.90 ms   (+0.47%) |      33   →      24    (-27.27%) |      358.00 ms →      261.60 ms  (-26.93%) | 
+ │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.57 ms →       10.65 ms   (+0.71%) |      33   →      24    (-27.27%) |      348.91 ms →      255.55 ms  (-26.76%) | 
+ │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.57 ms →       10.65 ms   (+0.71%) |      33   →      24    (-27.27%) |      348.89 ms →      255.54 ms  (-26.76%) | 
+ │ │ │ ├ sirius::Periodic_function::add                                |      546.22 μs →      457.29 μs  (-16.28%) |      66   →      48    (-27.27%) |       36.05 ms →       21.95 ms  (-39.11%) | 
+ │ │ │ ├ sirius::Potential::xc                                         |       44.67 ms →       27.28 ms  (-38.93%) |      33   →      24    (-27.27%) |        1.47 s  →      654.69 ms  (-55.58%) | 
+ │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       44.67 ms →       24.96 ms  (-44.13%) |      33   →      24    (-27.27%) |        1.47 s  →      598.96 ms  (-59.36%) | 
+ │ │ │ │   ├ sirius::Smooth_periodic_function                          |        1.24 ms →        1.19 ms   (-3.76%) |      66   →      24    (-63.64%) |       81.81 ms →       28.63 ms  (-65.00%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |       11.66 ms                             |      33                          |      384.71 ms                             | 
  │ │ │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                |                         8.19 ms            |                  48              |                       393.00 ms            | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        7.62 ms →        4.90 ms  (-35.74%) |      33   →      24    (-27.27%) |      251.57 ms →      117.57 ms  (-53.26%) | 
+ │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.92 ms →       90.95 ms   (+0.03%) |      33   →      24    (-27.27%) |        3.00 s  →        2.18 s   (-27.25%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      285.82 ms →      292.65 ms   (+2.39%) |      33   →      24    (-27.27%) |        9.43 s  →        7.02 s   (-25.54%) | 
+ │ │ ├ sirius::Field4D::symmetrize                                     |      292.61 ms →      255.57 ms  (-12.66%) |      33   →      24    (-27.27%) |        9.66 s  →        6.13 s   (-36.48%) | 
+ │ │ │ └ sirius::symmetrize_function|fpw                               |      292.60 ms →      255.56 ms  (-12.66%) |      33   →      24    (-27.27%) |        9.66 s  →        6.13 s   (-36.48%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       30.51 ms →       23.92 ms  (-21.62%) |      33   →      24    (-27.27%) |        1.01 s  →      574.01 ms  (-43.00%) | 
+ │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      233.05 ms →      204.75 ms  (-12.14%) |      33   →      24    (-27.27%) |        7.69 s  →        4.91 s   (-36.10%) | 
+ │ │ │   └ sddk::Gvec_shells::remap_backward                           |       27.90 ms →       25.76 ms   (-7.65%) |      33   →      24    (-27.27%) |      920.54 ms →      618.28 ms  (-32.83%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.42 ms →        5.23 ms   (-3.48%) |      33   →      24    (-27.27%) |      178.76 ms →      125.48 ms  (-29.81%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.88 ms                             |     231                          |        2.51 s                              | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |       10.36 ms                             |     231                          |        2.39 s                              | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |       10.36 ms                             |     231                          |        2.39 s                              | 
+ │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.16 ms →       10.53 ms   (+3.72%) |      99   →      72    (-27.27%) |        1.01 s  →      758.40 ms  (-24.56%) | 
+ │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        9.85 ms →       10.19 ms   (+3.49%) |      99   →      72    (-27.27%) |      974.79 ms →      733.68 ms  (-24.73%) | 
+ │ │ ├ sirius::Periodic_function::integrate                            |       10.00 ms →       10.06 ms   (+0.65%) |      33   →      24    (-27.27%) |      329.86 ms →      241.46 ms  (-26.80%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      113.87 μs →       14.78 ms (+12876.59%) |      33   →      24    (-27.27%) |        3.76 ms →      354.62 ms (+9337.52%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      108.38 μs →       14.77 ms (+13527.26%) |      33   →      24    (-27.27%) |        3.58 ms →      354.47 ms (+9810.74%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        4.83 ms →        5.03 ms   (+4.19%) |       2   →       2              |        9.66 ms →       10.07 ms   (+4.19%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.20 ms →       10.71 ms   (+4.95%) |       6   →       6              |       61.21 ms →       64.24 ms   (+4.95%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.09 ms →       10.23 ms   (+1.40%) |       6   →       6              |       60.53 ms →       61.38 ms   (+1.40%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.09 ms →       10.23 ms   (+1.40%) |       6   →       6              |       60.53 ms →       61.37 ms   (+1.40%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        9.73 ms →       10.60 ms   (+8.98%) |       3   →       3              |       29.18 ms →       31.80 ms   (+8.98%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.61 ms →       10.15 ms   (+5.58%) |       3   →       3              |       28.84 ms →       30.45 ms   (+5.58%) | 
  ├ sirius::Periodic_function|inner                                     |       10.41 ms →       10.41 ms   (-0.01%) |       2   →       2              |       20.83 ms →       20.83 ms   (-0.01%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.41 ms →       10.22 ms   (-1.75%) |       2   →       2              |       20.81 ms →       20.45 ms   (-1.75%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.41 ms →       10.22 ms   (-1.75%) |       2   →       2              |       20.81 ms →       20.45 ms   (-1.75%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        9.68 ms →       10.35 ms   (+6.91%) |       1   →       1              |        9.68 ms →       10.35 ms   (+6.91%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        9.67 ms →       10.01 ms   (+3.55%) |       1   →       1              |        9.67 ms →       10.01 ms   (+3.55%) | 
  └ sirius::finalize                                                    |      173.29 ms →      177.34 ms   (+2.33%) |       1   →       1              |      173.29 ms →      177.34 ms   (+2.33%) | 
  ====================================================================================================================================================================================================
```
