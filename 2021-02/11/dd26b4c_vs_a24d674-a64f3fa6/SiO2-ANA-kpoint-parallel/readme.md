# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs dd26b4c3a8b510264c2723458c0ccaf5eeca6037
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      170.21 s  →      114.60 s   (-32.67%) |       1   →       1              |      170.21 s  →      114.60 s   (-32.67%) | 
  ├ sirius::initialize                                                  |        2.70 s  →        2.75 s    (+2.01%) |       1   →       1              |        2.70 s  →        2.75 s    (+2.01%) | 
  ├ sirius::Simulation_context::initialize                              |        2.96 s  →        2.94 s    (-0.50%) |       1   →       1              |        2.96 s  →        2.94 s    (-0.50%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       44.80 ms →       14.35 ms  (-67.97%) |       1   →       1              |       44.80 ms →       14.35 ms  (-67.97%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      144.77 ms →      164.77 ms  (+13.81%) |       1   →       1              |      144.77 ms →      164.77 ms  (+13.81%) | 
- │ │ ├ sirius::Atom_type::init                                         |       60.78 ms →       70.97 ms  (+16.76%) |       2   →       2              |      121.57 ms →      141.93 ms  (+16.76%) | 
  │ │ └ sirius::Unit_cell::update                                       |       23.13 ms →       22.63 ms   (-2.16%) |       1   →       1              |       23.13 ms →       22.63 ms   (-2.16%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.31 ms →        6.29 ms   (-0.32%) |       1   →       1              |        6.31 ms →        6.29 ms   (-0.32%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       16.77 ms →       16.30 ms   (-2.85%) |       1   →       1              |       16.77 ms →       16.30 ms   (-2.85%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       16.75 ms →       16.27 ms   (-2.89%) |       1   →       1              |       16.75 ms →       16.27 ms   (-2.89%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.16 ms →        4.16 ms   (+0.17%) |       1   →       1              |        4.16 ms →        4.16 ms   (+0.17%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.32 ms   (+0.12%) |       1   →       1              |        2.32 ms →        2.32 ms   (+0.12%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      102.34 μs →      105.92 μs   (+3.50%) |       1   →       1              |      102.34 μs →      105.92 μs   (+3.50%) | 
  │ └ sirius::Simulation_context::update                                |        2.72 s  →        2.72 s    (-0.21%) |       1   →       1              |        2.72 s  →        2.72 s    (-0.21%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.88 ms →       10.67 ms   (-1.96%) |       1   →       1              |       10.88 ms →       10.67 ms   (-1.96%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.45 ms →        4.22 ms   (-5.14%) |       1   →       1              |        4.45 ms →        4.22 ms   (-5.14%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.40 ms →        6.41 ms   (+0.28%) |       1   →       1              |        6.40 ms →        6.41 ms   (+0.28%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.38 ms →        6.39 ms   (+0.25%) |       1   →       1              |        6.38 ms →        6.39 ms   (+0.25%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.89 ms →        3.87 ms   (-0.37%) |       1   →       1              |        3.89 ms →        3.87 ms   (-0.37%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.34 ms   (+0.67%) |       1   →       1              |        2.32 ms →        2.34 ms   (+0.67%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       99.82 μs →      108.27 μs   (+8.47%) |       1   →       1              |       99.82 μs →      108.27 μs   (+8.47%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       64.78 ms →       65.96 ms   (+1.82%) |       2   →       2              |      129.56 ms →      131.92 ms   (+1.82%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.13 ms →        5.16 ms   (+0.56%) |       2   →       2              |       10.26 ms →       10.32 ms   (+0.56%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.51 ms →        4.49 ms   (-0.59%) |       1   →       1              |        4.51 ms →        4.49 ms   (-0.59%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.81 ms →       21.78 ms   (-0.17%) |       2   →       2              |       43.63 ms →       43.55 ms   (-0.17%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.76 ms →       14.79 ms   (+0.19%) |       2   →       2              |       29.53 ms →       29.58 ms   (+0.19%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.51 ms →       19.63 ms   (+0.61%) |       4   →       4              |       78.05 ms →       78.53 ms   (+0.61%) | 
  │   ├ sddk::Gvec::init                                                |      180.28 ms →      181.75 ms   (+0.82%) |       2   →       2              |      360.56 ms →      363.51 ms   (+0.82%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      134.11 ms →      138.92 ms   (+3.59%) |       2   →       2              |      268.21 ms →      277.84 ms   (+3.59%) | 
  │   ├ sddk::Gvec_shells                                               |      182.70 ms →      171.18 ms   (-6.31%) |       1   →       1              |      182.70 ms →      171.18 ms   (-6.31%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.31 ms →        1.32 ms   (+0.77%) |       1   →       1              |        1.31 ms →        1.32 ms   (+0.77%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      294.19 ms →      290.14 ms   (-1.38%) |       2   →       2              |      588.39 ms →      580.28 ms   (-1.38%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       40.40 ms →       36.98 ms   (-8.45%) |       1   →       1              |       40.40 ms →       36.98 ms   (-8.45%) | 
- │ ├ sirius::K_point::K_point                                          |        2.93 μs →        4.61 μs  (+57.73%) |       4   →       4              |       11.70 μs →       18.46 μs  (+57.73%) | 
  │ └ sirius::K_point_set::initialize                                   |       40.31 ms →       36.87 ms   (-8.52%) |       1   →       1              |       40.31 ms →       36.87 ms   (-8.52%) | 
  │   └ sirius::K_point::initialize                                     |       40.22 ms →       36.74 ms   (-8.65%) |       1   →       1              |       40.22 ms →       36.74 ms   (-8.65%) | 
+ │     ├ sirius::K_point::generate_gkvec                               |       20.49 ms →       18.25 ms  (-10.94%) |       1   →       1              |       20.49 ms →       18.25 ms  (-10.94%) | 
+ │     │ └ sddk::Gvec::init                                            |        9.12 ms →        8.11 ms  (-11.06%) |       1   →       1              |        9.12 ms →        8.11 ms  (-11.06%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        9.06 μs →        9.07 μs   (+0.21%) |       1   →       1              |        9.06 μs →        9.07 μs   (+0.21%) | 
  │     └ sirius::K_point::update                                       |       14.11 ms →       13.69 ms   (-2.97%) |       1   →       1              |       14.11 ms →       13.69 ms   (-2.97%) | 
  │       └ sirius::Beta_projectors                                     |        6.12 ms →        6.40 ms   (+4.69%) |       1   →       1              |        6.12 ms →        6.40 ms   (+4.69%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.52 ms →        3.81 ms   (+8.52%) |       1   →       1              |        3.52 ms →        3.81 ms   (+8.52%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.29 ms →        5.14 ms   (-2.88%) |       2   →       2              |       10.59 ms →       10.28 ms   (-2.88%) | 
  ├ sirius::Potential                                                   |      169.16 ms →      157.50 ms   (-6.89%) |       1   →       1              |      169.16 ms →      157.50 ms   (-6.89%) | 
+ │ ├ sirius::Smooth_periodic_function                                  |        5.81 ms →        5.75 ms   (-1.14%) |       6   →       5    (-16.67%) |       34.87 ms →       28.73 ms  (-17.61%) | 
  │ └ sirius::Potential::update                                         |      133.56 ms →      128.00 ms   (-4.16%) |       1   →       1              |      133.56 ms →      128.00 ms   (-4.16%) | 
  │   └ sirius::Potential::generate_local_potential                     |      132.82 ms →      127.28 ms   (-4.17%) |       1   →       1              |      132.82 ms →      127.28 ms   (-4.17%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      125.83 ms →      115.41 ms   (-8.28%) |       1   →       1              |      125.83 ms →      115.41 ms   (-8.28%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        6.44 ms →        7.62 ms  (+18.30%) |       1   →       1              |        6.44 ms →        7.62 ms  (+18.30%) | 
  ├ sirius::Density                                                     |      141.25 ms →      138.14 ms   (-2.20%) |       1   →       1              |      141.25 ms →      138.14 ms   (-2.20%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.21 ms →        5.11 ms   (-2.02%) |       2   →       2              |       10.42 ms →       10.21 ms   (-2.02%) | 
  │ └ sirius::Density::update                                           |      130.55 ms →      127.65 ms   (-2.22%) |       1   →       1              |      130.55 ms →      127.65 ms   (-2.22%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      130.10 ms →      127.23 ms   (-2.21%) |       1   →       1              |      130.10 ms →      127.23 ms   (-2.21%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |                       106.85 μs            |                   1              |                       106.85 μs            | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      124.57 ms →      120.43 ms   (-3.32%) |       1   →       1              |      124.57 ms →      120.43 ms   (-3.32%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        5.07 ms →        6.25 ms  (+23.32%) |       1   →       1              |        5.07 ms →        6.25 ms  (+23.32%) | 
  ├ sirius::Density::initial_density                                    |      176.21 ms →      177.76 ms   (+0.88%) |       1   →       1              |      176.21 ms →      177.76 ms   (+0.88%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      123.55 ms →      124.43 ms   (+0.71%) |       1   →       1              |      123.55 ms →      124.43 ms   (+0.71%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.91 ms →        4.98 ms   (+1.28%) |       2   →       2              |        9.82 ms →        9.95 ms   (+1.28%) | 
  │ └ sirius::Periodic_function::integrate                              |       10.29 ms →       10.07 ms   (-2.17%) |       1   →       1              |       10.29 ms →       10.07 ms   (-2.17%) | 
  ├ sirius::Potential::generate                                         |      586.52 ms →      573.83 ms   (-2.16%) |       1   →       1              |      586.52 ms →      573.83 ms   (-2.16%) | 
  │ ├ sirius::Potential::poisson                                        |      138.07 ms →      140.03 ms   (+1.42%) |       1   →       1              |      138.07 ms →      140.03 ms   (+1.42%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.22 ms →        5.98 ms  (+14.61%) |       1   →       1              |        5.22 ms →        5.98 ms  (+14.61%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.66 ms →       11.30 ms   (+6.08%) |       1   →       1              |       10.66 ms →       11.30 ms   (+6.08%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |       10.29 ms →       10.85 ms   (+5.36%) |       1   →       1              |       10.29 ms →       10.85 ms   (+5.36%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |       10.29 ms →       10.85 ms   (+5.36%) |       1   →       1              |       10.29 ms →       10.85 ms   (+5.36%) | 
+ │ ├ sirius::Periodic_function::add                                    |      557.58 μs →      465.00 μs  (-16.60%) |       2   →       2              |        1.12 ms →      929.99 μs  (-16.60%) | 
+ │ ├ sirius::Potential::xc                                             |       53.82 ms →       32.33 ms  (-39.94%) |       1   →       1              |       53.82 ms →       32.33 ms  (-39.94%) | 
+ │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       53.82 ms →       30.05 ms  (-44.17%) |       1   →       1              |       53.82 ms →       30.05 ms  (-44.17%) | 
+ │ │   ├ sirius::Smooth_periodic_function                              |        5.71 ms →        5.51 ms   (-3.63%) |       2   →       1    (-50.00%) |       11.43 ms →        5.51 ms  (-51.81%) | 
  │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        5.24 ms                             |       1                          |        5.24 ms                             | 
  │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                    |                         8.52 ms            |                   2              |                        17.03 ms            | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.73 ms →        6.14 ms   (+7.14%) |       1   →       1              |        5.73 ms →        6.14 ms   (+7.14%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.77 ms →       93.77 ms   (+1.08%) |       1   →       1              |       92.77 ms →       93.77 ms   (+1.08%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      293.65 ms →      299.30 ms   (+1.92%) |       1   →       1              |      293.65 ms →      299.30 ms   (+1.92%) | 
- ├ sirius::Hamiltonian0                                                |        8.41 ms →       11.98 ms  (+42.43%) |       1   →       1              |        8.41 ms →       11.98 ms  (+42.43%) | 
  │ ├ sirius::Local_operator                                            |        8.06 ms →        8.05 ms   (-0.20%) |       1   →       1              |        8.06 ms →        8.05 ms   (-0.20%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.75 ms →        4.70 ms   (-1.05%) |       1   →       1              |        4.75 ms →        4.70 ms   (-1.05%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.39 ms →        2.43 ms   (+2.02%) |       1   →       1              |        2.39 ms →        2.43 ms   (+2.02%) | 
  │ ├ sirius::Non_local_operator                                        |       63.02 μs →       63.47 μs   (+0.71%) |       2   →       2              |      126.03 μs →      126.93 μs   (+0.71%) | 
- │ ├ sirius::D_operator::initialize                                    |       97.00 μs →        1.31 ms (+1248.50%) |       1   →       1              |       97.00 μs →        1.31 ms (+1248.50%) | 
- │ └ sirius::Q_operator::initialize                                    |       75.92 μs →        2.45 ms (+3124.07%) |       1   →       1              |       75.92 μs →        2.45 ms (+3124.07%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.87 s  →        1.85 s    (-1.28%) |       1   →       1              |        1.87 s  →        1.85 s    (-1.28%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.71 ms →       18.68 ms   (-0.18%) |       1   →       1              |       18.71 ms →       18.68 ms   (-0.18%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      204.89 μs →      184.57 μs   (-9.92%) |       1   →       1              |      204.89 μs →      184.57 μs   (-9.92%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       18.51 ms →       18.49 ms   (-0.08%) |       1   →       1              |       18.51 ms →       18.49 ms   (-0.08%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.85 s  →        1.82 s    (-1.44%) |       1   →       1              |        1.85 s  →        1.82 s    (-1.44%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      130.51 ms →      126.34 ms   (-3.19%) |       4   →       4              |      522.03 ms →      505.38 ms   (-3.19%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       52.36 ms →       52.04 ms   (-0.61%) |       1   →       1              |       52.36 ms →       52.04 ms   (-0.61%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       20.98 ms →       21.08 ms   (+0.48%) |       1   →       1              |       20.98 ms →       21.08 ms   (+0.48%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      636.53 ms →      634.69 ms   (-0.29%) |       1   →       1              |      636.53 ms →      634.69 ms   (-0.29%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      297.76 ms →      297.56 ms   (-0.07%) |       1   →       1              |      297.76 ms →      297.56 ms   (-0.07%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        2.97 μs →        3.21 μs   (+8.04%) |       1   →       1              |        2.97 μs →        3.21 μs   (+8.04%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.09 μs →        2.19 μs   (+4.65%) |       1   →       1              |        2.09 μs →        2.19 μs   (+4.65%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      380.00 ns →      382.00 ns   (+0.53%) |       1   →       1              |      380.00 ns →      382.00 ns   (+0.53%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      582.00 ns →      565.00 ns   (-2.92%) |       1   →       1              |      582.00 ns →      565.00 ns   (-2.92%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.22 ms →        9.21 ms   (-0.10%) |       1   →       1              |        9.22 ms →        9.21 ms   (-0.10%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      121.57 ms →      120.76 ms   (-0.66%) |       1   →       1              |      121.57 ms →      120.76 ms   (-0.66%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      103.97 ms →      103.56 ms   (-0.40%) |       2   →       2              |      207.95 ms →      207.11 ms   (-0.40%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       38.53 ms →       40.09 ms   (+4.06%) |       2   →       2              |       77.05 ms →       80.18 ms   (+4.06%) | 
  │ │ │ ├ sddk::inner                                                   |       37.93 ms                             |       2                          |       75.86 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       23.52 μs                             |       2                          |       47.03 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        39.52 ms            |                   2              |                        79.04 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        73.00 ns            |                   2              |                       146.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        39.05 ms            |                   2              |                        78.11 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                       350.00 ns            |                   2              |                       700.00 ns            | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       56.41 ms →       56.46 ms   (+0.09%) |       1   →       1              |       56.41 ms →       56.46 ms   (+0.09%) | 
  │ │ ├ sddk::transform                                                 |       31.57 ms                             |       1                          |       31.57 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       11.97 μs                             |       1                          |       11.97 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       11.85 μs                             |       1                          |       11.85 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                        30.74 ms            |                   1              |                        30.74 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                        30.74 ms            |                   1              |                        30.74 ms            | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      849.00 ns →      413.00 ns  (-51.35%) |       1   →       1              |      849.00 ns →      413.00 ns  (-51.35%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      160.16 s  →      104.97 s   (-34.46%) |       1   →       1              |      160.16 s  →      104.97 s   (-34.46%) | 
+ │ ├ sirius::Smooth_periodic_function                                  |        5.80 ms →        5.14 ms  (-11.38%) |      19   →      18     (-5.26%) |      110.24 ms →       92.56 ms  (-16.04%) | 
  │ ├ sirius::Density                                                   |                       170.86 ms            |                   1              |                       170.86 ms            | 
  │ │ ├ sirius::Smooth_periodic_function                                |                         5.15 ms            |                   2              |                        10.30 ms            | 
  │ │ └ sirius::Density::update                                         |                       160.28 ms            |                   1              |                       160.28 ms            | 
  │ │   └ sirius::Density::generate_pseudo_core_charge_density          |                       159.87 ms            |                   1              |                       159.87 ms            | 
  │ │     ├ sirius::rho_core_ri_pseudo|values                           |                       135.12 μs            |                   1              |                       135.12 μs            | 
  │ │     ├ sirius::Simulation_context::make_periodic_function          |                       119.67 ms            |                   1              |                       119.67 ms            | 
  │ │     └ sirius::Smooth_periodic_function::fft_transform             |                        39.63 ms            |                   1              |                        39.63 ms            | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.70 s  →        4.74 s    (+0.96%) |      34   →      22    (-35.29%) |      159.76 s  →      104.37 s   (-34.67%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        4.77 ms →        8.06 ms  (+69.01%) |      34   →      22    (-35.29%) |      162.13 ms →      177.30 ms   (+9.36%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        4.40 ms →        4.12 ms   (-6.31%) |      34   →      22    (-35.29%) |      149.48 ms →       90.61 ms  (-39.38%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function                            |      971.99 μs →      951.85 μs   (-2.07%) |      34   →      22    (-35.29%) |       33.05 ms →       20.94 ms  (-36.63%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.53 ms →        2.24 ms  (-11.59%) |      34   →      22    (-35.29%) |       86.18 ms →       49.30 ms  (-42.79%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |       64.95 μs →       64.73 μs   (-0.34%) |      68   →      44    (-35.29%) |        4.42 ms →        2.85 ms  (-35.52%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |       96.70 μs →        1.29 ms (+1232.03%) |      34   →      22    (-35.29%) |        3.29 ms →       28.34 ms (+761.90%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       76.45 μs →        2.46 ms (+3117.53%) |      34   →      22    (-35.29%) |        2.60 ms →       54.11 ms (+1981.93%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.68 s  →        2.72 s    (+1.25%) |      34   →      22    (-35.29%) |       91.26 s  →       59.79 s   (-34.48%) | 
+ │ │ │ ├ sirius::Hamiltonian_k                                         |      175.30 μs →      161.74 μs   (-7.74%) |      34   →      22    (-35.29%) |        5.96 ms →        3.56 ms  (-40.30%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      168.74 μs →      153.45 μs   (-9.06%) |      34   →      22    (-35.29%) |        5.74 ms →        3.38 ms  (-41.16%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.78 μs →        4.13 μs  (-13.64%) |      34   →      22    (-35.29%) |      162.45 μs →       90.78 μs  (-44.12%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.63 s  →        2.54 s    (-3.31%) |      34   →      22    (-35.29%) |       89.27 s  →       55.85 s   (-37.43%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |      103.52 ms →      104.39 ms   (+0.84%) |      34   →      22    (-35.29%) |        3.52 s  →        2.30 s   (-34.75%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        8.92 ms →        8.94 ms   (+0.26%) |     204   →     132    (-35.29%) |        1.82 s  →        1.18 s   (-35.13%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        6.00 ms →        5.96 ms   (-0.66%) |      34   →      22    (-35.29%) |      204.02 ms →      131.14 ms  (-35.72%) | 
+ │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      355.71 μs →      351.41 μs   (-1.21%) |      34   →      22    (-35.29%) |       12.09 ms →        7.73 ms  (-36.08%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.32 ms →        2.31 ms   (-0.18%) |      68   →      44    (-35.29%) |      157.66 ms →      101.83 ms  (-35.41%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.48 s  →        2.39 s    (-3.53%) |      34   →      22    (-35.29%) |       84.32 s  →       52.63 s   (-37.58%) | 
+ │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      106.90 ms →      104.08 ms   (-2.63%) |     359   →     299    (-16.71%) |       38.38 s  →       31.12 s   (-18.91%) | 
+ │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       40.89 ms →       39.87 ms   (-2.51%) |     359   →     299    (-16.71%) |       14.68 s  →       11.92 s   (-18.80%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.84 μs →        1.62 μs  (-11.66%) |     359   →     299    (-16.71%) |      659.80 μs →      485.45 μs  (-26.43%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.56 μs →        1.39 μs  (-10.62%) |     359   →     299    (-16.71%) |      559.60 μs →      416.59 μs  (-25.56%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      337.36 ns →      338.39 ns   (+0.30%) |     359   →     299    (-16.71%) |      121.11 μs →      101.18 μs  (-16.46%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      439.21 ns →      529.99 ns  (+20.67%) |     359   →     299    (-16.71%) |      157.68 μs →      158.47 μs   (+0.50%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.35 ms →        7.34 ms   (-0.16%) |     359   →     299    (-16.71%) |        2.64 s  →        2.19 s   (-16.84%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       19.59 ms →       18.72 ms   (-4.43%) |     359   →     299    (-16.71%) |        7.03 s  →        5.60 s   (-20.41%) | 
+ │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       19.52 ms →       19.07 ms   (-2.35%) |     718   →     598    (-16.71%) |       14.02 s  →       11.40 s   (-18.67%) | 
+ │ │ │ │   ├ sddk::orthogonalize                                       |       35.58 ms →       31.76 ms  (-10.76%) |     359   →     299    (-16.71%) |       12.77 s  →        9.50 s   (-25.67%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        4.40 ms                             |     684                          |        3.01 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       21.39 μs                             |     684                          |       14.63 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                         4.88 ms            |                 576              |                         2.81 s             | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                       108.57 ns            |                 576              |                        62.54 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                         3.77 ms            |                 576              |                         2.17 s             | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                       204.78 ns            |                 576              |                       117.96 μs            | 
+ │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |        6.43 ms →        4.99 ms  (-22.42%) |     359   →     299    (-16.71%) |        2.31 s  →        1.49 s   (-35.39%) | 
+ │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        8.07 ms →        7.68 ms   (-4.82%) |     359   →     299    (-16.71%) |        2.90 s  →        2.30 s   (-20.73%) | 
  │ │ │ │   │ ├ sddk::transform                                         |       14.03 ms                             |     325                          |        4.56 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       17.46 μs                             |     325                          |        5.68 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       41.05 μs                             |     975                          |       40.02 ms                             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                        10.45 ms            |                 277              |                         2.89 s             | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                         3.48 ms            |                 831              |                         2.89 s             | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        9.49 ms →        8.33 ms  (-12.30%) |     359   →     299    (-16.71%) |        3.41 s  →        2.49 s   (-26.96%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        8.50 ms                             |     359                          |        3.05 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       28.86 μs                             |     359                          |       10.36 ms                             | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                         7.93 ms            |                 299              |                         2.37 s             | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                        93.87 ns            |                 299              |                        28.07 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                         6.82 ms            |                 299              |                         2.04 s             | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                       189.21 ns            |                 299              |                        56.57 μs            | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       64.15 ms →       12.26 ms  (-80.89%) |     359   →     299    (-16.71%) |       23.03 s  →        3.67 s   (-84.09%) | 
+ │ │ │ │   ├ sirius::residuals                                         |       13.62 ms →        7.48 ms  (-45.09%) |     348   →     288    (-17.24%) |        4.74 s  →        2.15 s   (-54.56%) | 
  │ │ │ │   │ ├ sddk::transform                                         |       12.62 ms                             |     334                          |        4.21 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       14.52 μs                             |     334                          |        4.85 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       39.10 μs                             |     668                          |       26.12 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                         6.24 ms            |                 277              |                         1.73 s             | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                         3.12 ms            |                 554              |                         1.73 s             | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.36 ms →        1.13 ms  (-17.45%) |     334   →     277    (-17.07%) |      455.60 ms →      311.90 ms  (-31.54%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       54.92 ms →       44.87 ms  (-18.29%) |      36   →      82   (+127.78%) |        1.98 s  →        3.68 s   (+86.11%) | 
  │ │ │ │     ├ sddk::transform                                         |       51.80 ms                             |      38                          |        1.97 s                              | 
  │ │ │ │     │ ├ sddk::transform|init                                  |       11.61 μs                             |      38                          |      441.28 μs                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       13.77 μs                             |      40                          |      550.93 μs                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                        25.62 ms            |                 142              |                         3.64 s             | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                        18.01 ms            |                 202              |                         3.64 s             | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      496.29 ns →      447.68 ns   (-9.80%) |      34   →      22    (-35.29%) |       16.87 μs →        9.85 μs  (-41.63%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       36.89 μs →        2.27 ms (+6050.93%) |      34   →      22    (-35.29%) |        1.25 ms →       49.92 ms (+3880.01%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |      605.72 μs →       59.30 ms (+9690.30%) |      34   →      22    (-35.29%) |       20.59 ms →        1.30 s  (+6234.90%) | 
+ │ │ ├ sirius::Density::generate                                       |      778.37 ms →      787.12 ms   (+1.13%) |      34   →      22    (-35.29%) |       26.46 s  →       17.32 s   (-34.57%) | 
+ │ │ │ ├ sirius::Density::generate_valence                             |      402.54 ms →      436.31 ms   (+8.39%) |      34   →      22    (-35.29%) |       13.69 s  →        9.60 s   (-29.87%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        7.53 μs →        2.54 μs  (-66.28%) |      34   →      22    (-35.29%) |      255.87 μs →       55.82 μs  (-78.18%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        6.90 μs →        2.24 μs  (-67.52%) |      34   →      22    (-35.29%) |      234.53 μs →       49.29 μs  (-78.98%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |      100.25 ms →      127.29 ms  (+26.97%) |      34   →      22    (-35.29%) |        3.41 s  →        2.80 s   (-17.84%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.11 μs →        8.92 μs  (+25.42%) |      34   →      22    (-35.29%) |      241.72 μs →      196.17 μs  (-18.85%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.12 ms →        7.12 ms   (+0.06%) |      34   →      22    (-35.29%) |      241.95 ms →      156.65 ms  (-35.25%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       91.22 ms →       91.18 ms   (-0.05%) |      34   →      22    (-35.29%) |        3.10 s  →        2.01 s   (-35.32%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      615.50 ns →      507.86 ns  (-17.49%) |      34   →      22    (-35.29%) |       20.93 μs →       11.17 μs  (-46.61%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      163.18 ms →      163.01 ms   (-0.10%) |      34   →      22    (-35.29%) |        5.55 s  →        3.59 s   (-35.36%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.64 ms   (+0.24%) |      34   →      22    (-35.29%) |       55.72 ms →       36.14 ms  (-35.14%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |       88.31 ms →       88.41 ms   (+0.11%) |      34   →      22    (-35.29%) |        3.00 s  →        1.94 s   (-35.22%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.09 ms →       88.18 ms   (+0.10%) |      34   →      22    (-35.29%) |        2.99 s  →        1.94 s   (-35.23%) | 
+ │ │ │ ├ sirius::Field4D::symmetrize                                   |      283.40 ms →      257.27 ms   (-9.22%) |      34   →      22    (-35.29%) |        9.64 s  →        5.66 s   (-41.26%) | 
+ │ │ │ │ └ sirius::symmetrize_function|fpw                             |      283.40 ms →      257.26 ms   (-9.22%) |      34   →      22    (-35.29%) |        9.64 s  →        5.66 s   (-41.26%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       29.24 ms →       25.77 ms  (-11.87%) |      34   →      22    (-35.29%) |      994.29 ms →      567.00 ms  (-42.97%) | 
+ │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      226.65 ms →      204.86 ms   (-9.61%) |      34   →      22    (-35.29%) |        7.71 s  →        4.51 s   (-41.51%) | 
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       26.32 ms →       25.49 ms   (-3.16%) |      34   →      22    (-35.29%) |      894.90 ms →      560.77 ms  (-37.34%) | 
+ │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       80.59 ms →       81.35 ms   (+0.94%) |      34   →      22    (-35.29%) |        2.74 s  →        1.79 s   (-34.69%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        8.27 ms →        8.52 ms   (+3.02%) |      34   →      22    (-35.29%) |      281.24 ms →      187.47 ms  (-33.34%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |                        10.83 ms            |                 198              |                         2.14 s             | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |                        10.40 ms            |                 198              |                         2.06 s             | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |                        10.40 ms            |                 198              |                         2.06 s             | 
+ │ │ ├ sirius::Density::mix                                            |      234.72 ms →      153.08 ms  (-34.78%) |      34   →      22    (-35.29%) |        7.98 s  →        3.37 s   (-57.80%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      956.59 μs →        1.07 ms  (+12.18%) |      34   →      22    (-35.29%) |       32.52 ms →       23.61 ms  (-27.42%) | 
+ │ │ │ ├ sirius::Periodic_function|inner                               |       11.22 ms →       10.14 ms   (-9.65%) |     454   →     274    (-39.65%) |        5.09 s  →        2.78 s   (-45.47%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.87 ms →        9.82 ms   (-9.67%) |     454   →     274    (-39.65%) |        4.93 s  →        2.69 s   (-45.48%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.87 ms →        9.82 ms   (-9.67%) |     454   →     274    (-39.65%) |        4.93 s  →        2.69 s   (-45.48%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        7.34 ms →        8.38 ms  (+14.20%) |      34   →      22    (-35.29%) |      249.57 ms →      184.41 ms  (-26.11%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        6.49 ms →        7.29 ms  (+12.24%) |      34   →      22    (-35.29%) |      220.81 ms →      160.37 ms  (-27.37%) | 
+ │ │ ├ sirius::Potential::generate                                     |      587.01 ms →      574.87 ms   (-2.07%) |      34   →      22    (-35.29%) |       19.96 s  →       12.65 s   (-36.63%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |      138.33 ms →      139.64 ms   (+0.95%) |      34   →      22    (-35.29%) |        4.70 s  →        3.07 s   (-34.68%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        5.09 ms →        5.90 ms  (+15.99%) |      34   →      22    (-35.29%) |      173.07 ms →      129.89 ms  (-24.95%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner                             |       10.79 ms →       10.97 ms   (+1.71%) |      34   →      22    (-35.29%) |      366.84 ms →      241.43 ms  (-34.19%) | 
+ │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.53 ms →       10.60 ms   (+0.58%) |      34   →      22    (-35.29%) |      358.15 ms →      233.10 ms  (-34.92%) | 
+ │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.53 ms →       10.59 ms   (+0.58%) |      34   →      22    (-35.29%) |      358.13 ms →      233.09 ms  (-34.92%) | 
+ │ │ │ ├ sirius::Periodic_function::add                                |      548.03 μs →      463.59 μs  (-15.41%) |      68   →      44    (-35.29%) |       37.27 ms →       20.40 ms  (-45.26%) | 
+ │ │ │ ├ sirius::Potential::xc                                         |       45.86 ms →       27.27 ms  (-40.54%) |      34   →      22    (-35.29%) |        1.56 s  →      599.94 ms  (-61.53%) | 
+ │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       45.86 ms →       24.91 ms  (-45.68%) |      34   →      22    (-35.29%) |        1.56 s  →      548.12 ms  (-64.85%) | 
+ │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.01 ms →        1.20 ms  (-60.11%) |      68   →      22    (-67.65%) |      204.91 ms →       26.45 ms  (-87.09%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |        5.33 ms                             |      34                          |      181.24 ms                             | 
  │ │ │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                |                         8.20 ms            |                  44              |                       360.69 ms            | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.30 ms →        6.76 ms   (+7.33%) |      34   →      22    (-35.29%) |      214.10 ms →      148.68 ms  (-30.55%) | 
+ │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.98 ms →       91.07 ms   (+0.10%) |      34   →      22    (-35.29%) |        3.09 s  →        2.00 s   (-35.23%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      303.15 ms →      307.89 ms   (+1.56%) |      34   →      22    (-35.29%) |       10.31 s  →        6.77 s   (-34.28%) | 
+ │ │ ├ sirius::Field4D::symmetrize                                     |      287.77 ms →      253.92 ms  (-11.76%) |      34   →      22    (-35.29%) |        9.78 s  →        5.59 s   (-42.90%) | 
+ │ │ │ └ sirius::symmetrize_function|fpw                               |      287.77 ms →      253.92 ms  (-11.76%) |      34   →      22    (-35.29%) |        9.78 s  →        5.59 s   (-42.91%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       30.61 ms →       24.53 ms  (-19.87%) |      34   →      22    (-35.29%) |        1.04 s  →      539.65 ms  (-48.15%) | 
+ │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      226.11 ms →      204.49 ms   (-9.56%) |      34   →      22    (-35.29%) |        7.69 s  →        4.50 s   (-41.48%) | 
+ │ │ │   └ sddk::Gvec_shells::remap_backward                           |       27.22 ms →       23.75 ms  (-12.77%) |      34   →      22    (-35.29%) |      925.59 ms →      522.45 ms  (-43.55%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.75 ms →        5.54 ms   (-3.55%) |      34   →      22    (-35.29%) |      195.45 ms →      121.98 ms  (-37.59%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.73 ms                             |     238                          |        2.55 s                              | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |       10.40 ms                             |     238                          |        2.47 s                              | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |       10.40 ms                             |     238                          |        2.47 s                              | 
+ │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.13 ms →       10.58 ms   (+4.43%) |     102   →      66    (-35.29%) |        1.03 s  →      698.16 ms  (-32.43%) | 
+ │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        9.90 ms →       10.29 ms   (+3.92%) |     102   →      66    (-35.29%) |        1.01 s  →      678.98 ms  (-32.76%) | 
+ │ │ ├ sirius::Periodic_function::integrate                            |        9.95 ms →       10.15 ms   (+2.06%) |      34   →      22    (-35.29%) |      338.27 ms →      223.39 ms  (-33.96%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      188.77 μs →       15.50 ms (+8111.43%) |      34   →      22    (-35.29%) |        6.42 ms →      341.02 ms (+5213.28%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      183.66 μs →       15.49 ms (+8336.55%) |      34   →      22    (-35.29%) |        6.24 ms →      340.88 ms (+5358.95%) | 
+ │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        6.86 ms →        4.73 ms  (-31.03%) |       2   →       2              |       13.71 ms →        9.46 ms  (-31.03%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.51 ms →       11.44 ms   (+8.90%) |       6   →       6              |       63.05 ms →       68.66 ms   (+8.90%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.45 ms →       10.22 ms   (-2.27%) |       6   →       6              |       62.71 ms →       61.29 ms   (-2.27%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.45 ms →       10.21 ms   (-2.27%) |       6   →       6              |       62.71 ms →       61.29 ms   (-2.27%) | 
- │ └ sirius::Smooth_periodic_function|inner                            |       10.08 ms →       11.32 ms  (+12.29%) |       3   →       3              |       30.24 ms →       33.95 ms  (+12.29%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.95 ms →       10.07 ms   (+1.19%) |       3   →       3              |       29.86 ms →       30.21 ms   (+1.19%) | 
  ├ sirius::Periodic_function|inner                                     |       10.45 ms →       11.18 ms   (+7.01%) |       2   →       2              |       20.89 ms →       22.36 ms   (+7.01%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.40 ms →       10.51 ms   (+1.11%) |       2   →       2              |       20.80 ms →       21.03 ms   (+1.11%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.40 ms →       10.51 ms   (+1.11%) |       2   →       2              |       20.80 ms →       21.03 ms   (+1.11%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.15 ms →       10.37 ms   (+2.19%) |       1   →       1              |       10.15 ms →       10.37 ms   (+2.19%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        9.96 ms →       10.37 ms   (+4.07%) |       1   →       1              |        9.96 ms →       10.37 ms   (+4.07%) | 
+ └ sirius::finalize                                                    |      219.94 ms →      178.62 ms  (-18.79%) |       1   →       1              |      219.94 ms →      178.62 ms  (-18.79%) | 
  ====================================================================================================================================================================================================
```
