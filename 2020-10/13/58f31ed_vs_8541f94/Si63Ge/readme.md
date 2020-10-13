# Benchmark 8541f94e2e0e288633941ac63ad4d565828afb1d vs 58f31ed08f2b4e9e6d289f9ed116027f00413e03
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |       91.71 s  →       71.56 s   (-21.97%) |       1   →       1              |       91.71 s  →       71.56 s   (-21.97%) | 
  ├ sirius::initialize                                                  |        2.84 s  →        2.92 s    (+2.60%) |       1   →       1              |        2.84 s  →        2.92 s    (+2.60%) | 
  ├ sirius::Simulation_context::initialize                              |        3.71 s  →        3.60 s    (-3.18%) |       1   →       1              |        3.71 s  →        3.60 s    (-3.18%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       32.40 ms →      690.70 μs  (-97.87%) |       1   →       1              |       32.40 ms →      690.70 μs  (-97.87%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      137.28 ms →      115.08 ms  (-16.17%) |       1   →       1              |      137.28 ms →      115.08 ms  (-16.17%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       59.85 ms →       47.44 ms  (-20.73%) |       2   →       2              |      119.69 ms →       94.88 ms  (-20.73%) | 
- │ │ └ sirius::Unit_cell::update                                       |       17.50 ms →       20.12 ms  (+14.96%) |       1   →       1              |       17.50 ms →       20.12 ms  (+14.96%) | 
+ │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        5.34 ms →        3.82 ms  (-28.42%) |       1   →       1              |        5.34 ms →        3.82 ms  (-28.42%) | 
- │ │   └ sirius::Unit_cell::get_symmetry                               |       12.08 ms →       16.24 ms  (+34.50%) |       1   →       1              |       12.08 ms →       16.24 ms  (+34.50%) | 
- │ │     └ sirius::Unit_cell_symmetry                                  |       12.00 ms →       16.17 ms  (+34.74%) |       1   →       1              |       12.00 ms →       16.17 ms  (+34.74%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.75 ms →        2.74 ms   (-0.21%) |       1   →       1              |        2.75 ms →        2.74 ms   (-0.21%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      510.17 μs →      504.81 μs   (-1.05%) |       1   →       1              |      510.17 μs →      504.81 μs   (-1.05%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       15.65 μs →       15.83 μs   (+1.16%) |       1   →       1              |       15.65 μs →       15.83 μs   (+1.16%) | 
  │ └ sirius::Simulation_context::update                                |        3.35 s  →        3.43 s    (+2.41%) |       1   →       1              |        3.35 s  →        3.43 s    (+2.41%) | 
  │   ├ sirius::Unit_cell::update                                       |        7.19 ms →        7.19 ms   (-0.12%) |       1   →       1              |        7.19 ms →        7.19 ms   (-0.12%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.86 ms →        3.68 ms   (-4.78%) |       1   →       1              |        3.86 ms →        3.68 ms   (-4.78%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.30 ms →        3.47 ms   (+5.14%) |       1   →       1              |        3.30 ms →        3.47 ms   (+5.14%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.26 ms →        3.42 ms   (+4.89%) |       1   →       1              |        3.26 ms →        3.42 ms   (+4.89%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.70 ms →        2.78 ms   (+2.96%) |       1   →       1              |        2.70 ms →        2.78 ms   (+2.96%) | 
- │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      521.47 μs →      600.10 μs  (+15.08%) |       1   →       1              |      521.47 μs →      600.10 μs  (+15.08%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       14.22 μs →       13.95 μs   (-1.93%) |       1   →       1              |       14.22 μs →       13.95 μs   (-1.93%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      212.41 ms →      212.27 ms   (-0.06%) |       2   →       2              |      424.82 ms →      424.55 ms   (-0.06%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.28 ms →       15.19 ms   (-0.60%) |       2   →       2              |       30.55 ms →       30.37 ms   (-0.60%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.24 ms →       13.26 ms   (+0.16%) |       1   →       1              |       13.24 ms →       13.26 ms   (+0.16%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.30 ms →       56.36 ms   (+0.10%) |       2   →       2              |      112.61 ms →      112.72 ms   (+0.10%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.21 ms →       45.03 ms   (-0.40%) |       2   →       2              |       90.42 ms →       90.06 ms   (-0.40%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.54 ms →       60.23 ms   (-0.51%) |       4   →       4              |      242.16 ms →      240.92 ms   (-0.51%) | 
  │   ├ sddk::Gvec::init                                                |       93.81 ms →       92.78 ms   (-1.09%) |       2   →       2              |      187.61 ms →      185.57 ms   (-1.09%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       70.44 ms →       69.25 ms   (-1.70%) |       2   →       2              |      140.89 ms →      138.49 ms   (-1.70%) | 
- │   ├ sddk::Gvec_shells                                               |       95.28 ms →      105.77 ms  (+11.02%) |       1   →       1              |       95.28 ms →      105.77 ms  (+11.02%) | 
- │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.70 ms →        2.04 ms  (+19.84%) |       1   →       1              |        1.70 ms →        2.04 ms  (+19.84%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      514.40 ms →      563.52 ms   (+9.55%) |       2   →       2              |        1.03 s  →        1.13 s    (+9.55%) | 
+ ├ sirius::K_point_set::create_k_mesh                                  |      150.00 ms →       88.68 ms  (-40.88%) |       1   →       1              |      150.00 ms →       88.68 ms  (-40.88%) | 
- │ ├ sirius::K_point::K_point                                          |        1.27 μs →        1.44 μs  (+13.87%) |       4   →       4              |        5.06 μs →        5.76 μs  (+13.87%) | 
+ │ └ sirius::K_point_set::initialize                                   |      149.94 ms →       88.60 ms  (-40.91%) |       1   →       1              |      149.94 ms →       88.60 ms  (-40.91%) | 
  │   └ sirius::K_point::initialize                                     |       28.04 ms →       27.77 ms   (-0.95%) |       1   →       1              |       28.04 ms →       27.77 ms   (-0.95%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       11.13 ms →       10.78 ms   (-3.16%) |       1   →       1              |       11.13 ms →       10.78 ms   (-3.16%) | 
  │     │ └ sddk::Gvec::init                                            |        4.84 ms →        4.88 ms   (+0.72%) |       1   →       1              |        4.84 ms →        4.88 ms   (+0.72%) | 
- │     ├ sddk::matrix_storage::matrix_storage                          |        7.79 μs →       10.87 μs  (+39.61%) |       1   →       1              |        7.79 μs →       10.87 μs  (+39.61%) | 
  │     └ sirius::K_point::update                                       |       14.01 ms →       14.15 ms   (+1.00%) |       1   →       1              |       14.01 ms →       14.15 ms   (+1.00%) | 
  │       └ sirius::Beta_projectors                                     |       10.04 ms →       10.27 ms   (+2.23%) |       1   →       1              |       10.04 ms →       10.27 ms   (+2.23%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.15 ms →        8.31 ms   (+1.97%) |       1   →       1              |        8.15 ms →        8.31 ms   (+1.97%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.52 ms →        2.54 ms   (+0.94%) |       2   →       2              |        5.04 ms →        5.08 ms   (+0.94%) | 
  ├ sirius::Potential                                                   |       55.77 ms →       52.04 ms   (-6.69%) |       1   →       1              |       55.77 ms →       52.04 ms   (-6.69%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.94 ms →        2.92 ms   (-0.77%) |       6   →       6              |       17.65 ms →       17.52 ms   (-0.77%) | 
  │ └ sirius::Potential::update                                         |       37.51 ms →       33.90 ms   (-9.61%) |       1   →       1              |       37.51 ms →       33.90 ms   (-9.61%) | 
  │   └ sirius::Potential::generate_local_potential                     |       37.12 ms →       33.52 ms   (-9.70%) |       1   →       1              |       37.12 ms →       33.52 ms   (-9.70%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       32.92 ms →       25.96 ms  (-21.15%) |       1   →       1              |       32.92 ms →       25.96 ms  (-21.15%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        3.87 ms →        7.03 ms  (+81.75%) |       1   →       1              |        3.87 ms →        7.03 ms  (+81.75%) | 
  ├ sirius::Density                                                     |       46.89 ms →       43.27 ms   (-7.72%) |       1   →       1              |       46.89 ms →       43.27 ms   (-7.72%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.83 ms →        2.81 ms   (-0.46%) |       2   →       2              |        5.65 ms →        5.62 ms   (-0.46%) | 
  │ └ sirius::Density::update                                           |       41.10 ms →       37.51 ms   (-8.74%) |       1   →       1              |       41.10 ms →       37.51 ms   (-8.74%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       40.82 ms →       37.29 ms   (-8.64%) |       1   →       1              |       40.82 ms →       37.29 ms   (-8.64%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |                        76.41 μs            |                   1              |                        76.41 μs            | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       37.59 ms →       25.82 ms  (-31.32%) |       1   →       1              |       37.59 ms →       25.82 ms  (-31.32%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        2.90 ms →       11.11 ms (+283.24%) |       1   →       1              |        2.90 ms →       11.11 ms (+283.24%) | 
  ├ sirius::Density::initial_density                                    |       64.97 ms →       59.92 ms   (-7.78%) |       1   →       1              |       64.97 ms →       59.92 ms   (-7.78%) | 
+ │ ├ sirius::Simulation_context::make_periodic_function                |       37.28 ms →       26.00 ms  (-30.25%) |       1   →       1              |       37.28 ms →       26.00 ms  (-30.25%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.16 ms →        7.29 ms  (+75.44%) |       2   →       2              |        8.32 ms →       14.59 ms  (+75.44%) | 
  │ └ sirius::Periodic_function::integrate                              |        5.76 ms →        5.73 ms   (-0.46%) |       1   →       1              |        5.76 ms →        5.73 ms   (-0.46%) | 
  ├ sirius::Potential::generate                                         |      371.64 ms →      370.20 ms   (-0.39%) |       1   →       1              |      371.64 ms →      370.20 ms   (-0.39%) | 
  │ ├ sirius::Potential::poisson                                        |       45.49 ms →       42.75 ms   (-6.02%) |       1   →       1              |       45.49 ms →       42.75 ms   (-6.02%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.61 ms →       11.59 ms (+220.57%) |       1   →       1              |        3.61 ms →       11.59 ms (+220.57%) | 
- │ │ └ sirius::Periodic_function|inner                                 |        4.83 ms →        5.92 ms  (+22.58%) |       1   →       1              |        4.83 ms →        5.92 ms  (+22.58%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.82 ms →        4.64 ms   (-3.68%) |       1   →       1              |        4.82 ms →        4.64 ms   (-3.68%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.82 ms →        4.63 ms   (-3.87%) |       1   →       1              |        4.82 ms →        4.63 ms   (-3.87%) | 
  │ ├ sirius::Periodic_function::add                                    |      804.65 μs →      814.80 μs   (+1.26%) |       2   →       2              |        1.61 ms →        1.63 ms   (+1.26%) | 
  │ ├ sirius::Potential::xc                                             |       50.89 ms →       51.71 ms   (+1.60%) |       1   →       1              |       50.89 ms →       51.71 ms   (+1.60%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       50.89 ms →       50.51 ms   (-0.75%) |       1   →       1              |       50.89 ms →       50.51 ms   (-0.75%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.55 ms →        2.55 ms   (+0.03%) |       2   →       2              |        5.10 ms →        5.10 ms   (+0.03%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.95 ms →        4.70 ms   (-4.93%) |       1   →       1              |        4.95 ms →        4.70 ms   (-4.93%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.02 ms →        3.87 ms  (+28.06%) |       1   →       1              |        3.02 ms →        3.87 ms  (+28.06%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      269.25 ms →      268.85 ms   (-0.15%) |       1   →       1              |      269.25 ms →      268.85 ms   (-0.15%) | 
- │ └ sirius::Potential::generate_PAW_effective_potential               |      122.00 ns →      142.00 ns  (+16.39%) |       1   →       1              |      122.00 ns →      142.00 ns  (+16.39%) | 
+ ├ sirius::Hamiltonian0                                                |        8.40 ms →        6.48 ms  (-22.91%) |       1   →       1              |        8.40 ms →        6.48 ms  (-22.91%) | 
+ │ ├ sirius::Local_operator                                            |        7.35 ms →        5.88 ms  (-19.95%) |       1   →       1              |        7.35 ms →        5.88 ms  (-19.95%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.73 ms →        2.75 ms   (+0.51%) |       1   →       1              |        2.73 ms →        2.75 ms   (+0.51%) | 
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        3.58 ms →        2.36 ms  (-34.16%) |       1   →       1              |        3.58 ms →        2.36 ms  (-34.16%) | 
+ │ ├ sirius::Non_local_operator                                        |      395.61 μs →      117.19 μs  (-70.38%) |       2   →       2              |      791.21 μs →      234.39 μs  (-70.38%) | 
- │ ├ sirius::D_operator::initialize                                    |      106.44 μs →      168.04 μs  (+57.87%) |       1   →       1              |      106.44 μs →      168.04 μs  (+57.87%) | 
- │ └ sirius::Q_operator::initialize                                    |       88.36 μs →      106.34 μs  (+20.35%) |       1   →       1              |       88.36 μs →      106.34 μs  (+20.35%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.30 s  →        1.28 s    (-1.52%) |       1   →       1              |        1.30 s  →        1.28 s    (-1.52%) | 
+ │ ├ sirius::Hamiltonian_k                                             |       66.44 ms →       48.83 ms  (-26.50%) |       1   →       1              |       66.44 ms →       48.83 ms  (-26.50%) | 
- │ │ ├ sirius::Local_operator::prepare_k                               |      218.38 μs →      273.92 μs  (+25.43%) |       1   →       1              |      218.38 μs →      273.92 μs  (+25.43%) | 
+ │ │ └ sirius::Beta_projectors_base::prepare                           |       66.21 ms →       48.55 ms  (-26.67%) |       1   →       1              |       66.21 ms →       48.55 ms  (-26.67%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.23 s  →        1.23 s    (-0.17%) |       1   →       1              |        1.23 s  →        1.23 s    (-0.17%) | 
+ │ │ ├ sddk::matrix_storage::matrix_storage                            |       92.53 ms →       77.20 ms  (-16.57%) |       4   →       4              |      370.12 ms →      308.81 ms  (-16.57%) | 
- │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       38.40 ms →       43.90 ms  (+14.33%) |       1   →       1              |       38.40 ms →       43.90 ms  (+14.33%) | 
- │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        6.57 ms →        8.75 ms  (+33.21%) |       1   →       1              |        6.57 ms →        8.75 ms  (+33.21%) | 
+ │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      383.39 ms →      312.83 ms  (-18.40%) |       1   →       1              |      383.39 ms →      312.83 ms  (-18.40%) | 
+ │ │ │ ├ sirius::Local_operator::apply_h                               |      289.98 ms →      245.34 ms  (-15.39%) |       1   →       1              |      289.98 ms →      245.34 ms  (-15.39%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        4.20 μs →        3.68 μs  (-12.45%) |       1   →       1              |        4.20 μs →        3.68 μs  (-12.45%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.27 μs →        2.63 μs  (-19.61%) |       1   →       1              |        3.27 μs →        2.63 μs  (-19.61%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      500.00 ns →      455.00 ns   (-9.00%) |       1   →       1              |      500.00 ns →      455.00 ns   (-9.00%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      624.00 ns →      680.00 ns   (+8.97%) |       1   →       1              |      624.00 ns →      680.00 ns   (+8.97%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.16 ms →        3.09 ms   (-2.35%) |       1   →       1              |        3.16 ms →        3.09 ms   (-2.35%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.37 ms →       21.27 ms   (-0.49%) |       1   →       1              |       21.37 ms →       21.27 ms   (-0.49%) | 
+ │ │ │ └ sirius::Non_local_operator::apply                             |       34.42 ms →       21.55 ms  (-37.40%) |       2   →       2              |       68.83 ms →       43.09 ms  (-37.40%) | 
- │ │ ├ sirius::Band::set_subspace_mtrx                                 |        5.27 ms →       16.52 ms (+213.79%) |       2   →       2              |       10.53 ms →       33.05 ms (+213.79%) | 
  │ │ │ ├ sddk::inner                                                   |        5.06 ms                             |       2                          |       10.12 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       29.02 μs                             |       2                          |       58.03 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        16.31 ms            |                   2              |                        32.63 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        36.50 ns            |                   2              |                        73.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        16.18 ms            |                   2              |                        32.36 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                        21.50 ns            |                   2              |                        43.00 ns            | 
- │ │ ├ Eigensolver_cuda|zhegvdx                                        |      200.93 ms →      251.70 ms  (+25.27%) |       1   →       1              |      200.93 ms →      251.70 ms  (+25.27%) | 
  │ │ ├ sddk::transform                                                 |        5.23 ms                             |       1                          |        5.23 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       15.46 μs                             |       1                          |       15.46 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       20.40 μs                             |       1                          |       20.40 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                         2.62 ms            |                   1              |                         2.62 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                         2.61 ms            |                   1              |                         2.61 ms            | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      392.00 ns →      507.00 ns  (+29.34%) |       1   →       1              |      392.00 ns →      507.00 ns  (+29.34%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |       82.05 s  →       62.04 s   (-24.39%) |       1   →       1              |       82.05 s  →       62.04 s   (-24.39%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.42 ms →        2.45 ms   (+1.21%) |      19   →      19              |       46.05 ms →       46.61 ms   (+1.21%) | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.81 s  →        3.25 s   (-32.41%) |      17   →      19    (+11.76%) |       81.81 s  →       61.79 s   (-24.46%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        5.15 ms →        5.76 ms  (+11.80%) |      17   →      19    (+11.76%) |       87.55 ms →      109.40 ms  (+24.95%) | 
- │ │ │ ├ sirius::Local_operator                                        |        4.47 ms →        4.97 ms  (+10.98%) |      17   →      19    (+11.76%) |       76.05 ms →       94.34 ms  (+24.04%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function                            |      558.06 μs →      560.35 μs   (+0.41%) |      17   →      19    (+11.76%) |        9.49 ms →       10.65 ms  (+12.22%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.75 ms →        3.27 ms  (+19.04%) |      17   →      19    (+11.76%) |       46.67 ms →       62.09 ms  (+33.04%) | 
- │ │ │ ├ sirius::Non_local_operator                                    |      188.28 μs →      258.66 μs  (+37.38%) |      34   →      38    (+11.76%) |        6.40 ms →        9.83 ms  (+53.55%) | 
! │ │ │ ├ sirius::D_operator::initialize                                |      122.11 μs →      110.70 μs   (-9.34%) |      17   →      19    (+11.76%) |        2.08 ms →        2.10 ms   (+1.33%) | 
! │ │ │ └ sirius::Q_operator::initialize                                |       95.41 μs →       89.26 μs   (-6.44%) |      17   →      19    (+11.76%) |        1.62 ms →        1.70 ms   (+4.57%) | 
+ │ │ ├ sirius::Band::solve                                             |        3.59 s  →        2.03 s   (-43.45%) |      17   →      19    (+11.76%) |       61.09 s  →       38.61 s   (-36.80%) | 
+ │ │ │ ├ sirius::Hamiltonian_k                                         |      227.72 μs →      195.93 μs  (-13.96%) |      17   →      19    (+11.76%) |        3.87 ms →        3.72 ms   (-3.84%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      218.74 μs →      187.45 μs  (-14.31%) |      17   →      19    (+11.76%) |        3.72 ms →        3.56 ms   (-4.22%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        6.95 μs →        6.21 μs  (-10.59%) |      17   →      19    (+11.76%) |      118.08 μs →      118.00 μs   (-0.07%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        3.34 s  →        1.97 s   (-40.98%) |      17   →      19    (+11.76%) |       56.70 s  →       37.40 s   (-34.04%) | 
- │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       77.38 ms →       77.09 ms   (-0.37%) |      17   →      19    (+11.76%) |        1.32 s  →        1.46 s   (+11.35%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        9.11 ms →        8.12 ms  (-10.95%) |     102   →     114    (+11.76%) |      929.68 ms →      925.31 ms   (-0.47%) | 
- │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       17.45 ms →       18.38 ms   (+5.36%) |      17   →      19    (+11.76%) |      296.57 ms →      349.23 ms  (+17.75%) | 
- │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      454.73 μs →      476.26 μs   (+4.73%) |      17   →      19    (+11.76%) |        7.73 ms →        9.05 ms  (+17.06%) | 
- │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        8.29 ms →        8.34 ms   (+0.52%) |      34   →      38    (+11.76%) |      281.93 ms →      316.73 ms  (+12.34%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        3.23 s  →        1.86 s   (-42.33%) |      17   →      19    (+11.76%) |       54.97 s  →       35.43 s   (-35.55%) | 
+ │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       87.09 ms →       50.31 ms  (-42.23%) |     287   →     356    (+24.04%) |       25.00 s  →       17.91 s   (-28.34%) | 
+ │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       57.56 ms →       28.27 ms  (-50.88%) |     287   →     356    (+24.04%) |       16.52 s  →       10.06 s   (-39.07%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.94 μs →        1.74 μs  (-10.24%) |     287   →     356    (+24.04%) |      556.06 μs →      619.13 μs  (+11.34%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.61 μs →        1.46 μs   (-9.16%) |     287   →     356    (+24.04%) |      462.73 μs →      521.41 μs  (+12.68%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      413.54 ns →      345.03 ns  (-16.57%) |     287   →     356    (+24.04%) |      118.69 μs →      122.83 μs   (+3.49%) | 
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      632.67 ns →      413.39 ns  (-34.66%) |     287   →     356    (+24.04%) |      181.58 μs →      147.17 μs  (-18.95%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.83 ms →        2.86 ms   (+1.05%) |     287   →     356    (+24.04%) |      812.45 ms →        1.02 s   (+25.35%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        5.26 ms →        3.15 ms  (-40.00%) |     287   →     356    (+24.04%) |        1.51 s  →        1.12 s   (-25.57%) | 
+ │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       10.71 ms →        8.01 ms  (-25.27%) |     574   →     712    (+24.04%) |        6.15 s  →        5.70 s    (-7.30%) | 
+ │ │ │ │   ├ sddk::orthogonalize                                       |        9.27 ms →        6.83 ms  (-26.26%) |     287   →     356    (+24.04%) |        2.66 s  →        2.43 s    (-8.53%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        1.38 ms                             |     557                          |      767.17 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       22.57 μs                             |     557                          |       12.57 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                         1.20 ms            |                 693              |                       830.26 ms            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                        62.47 ns            |                 693              |                        43.29 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                         1.03 ms            |                 693              |                       716.80 ms            | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                        55.03 ns            |                 693              |                        38.14 μs            | 
+ │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      215.74 μs →      132.25 μs  (-38.70%) |     287   →     356    (+24.04%) |       61.92 ms →       47.08 ms  (-23.96%) | 
+ │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        2.49 ms →        2.09 ms  (-15.80%) |     287   →     356    (+24.04%) |      713.22 ms →      744.91 ms   (+4.44%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        4.13 ms                             |     270                          |        1.12 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       18.78 μs                             |     270                          |        5.07 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |        8.49 μs                             |     810                          |        6.87 ms                             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                         2.40 ms            |                 337              |                       808.98 ms            | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                       799.45 μs            |                1.01 K            |                       808.25 ms            | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.86 ms →        1.49 ms  (-19.97%) |     287   →     356    (+24.04%) |      535.20 ms →      531.33 ms   (-0.72%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        1.76 ms                             |     287                          |      504.86 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       24.31 μs                             |     287                          |        6.98 ms                             | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                         1.42 ms            |                 356              |                       507.02 ms            | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                        45.99 ns            |                 356              |                        16.37 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                         1.26 ms            |                 356              |                       449.13 ms            | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                        40.88 ns            |                 356              |                        14.55 μs            | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       84.17 ms →       37.17 ms  (-55.84%) |     287   →     356    (+24.04%) |       24.16 s  →       13.23 s   (-45.23%) | 
+ │ │ │ │   ├ sirius::residuals                                         |        8.61 ms →        2.69 ms  (-68.73%) |     273   →     340    (+24.54%) |        2.35 s  →      915.35 ms  (-61.06%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        4.36 ms                             |     273                          |        1.19 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       16.61 μs                             |     273                          |        4.53 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       10.18 μs                             |     546                          |        5.56 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                         1.37 ms            |                 337              |                       460.77 ms            | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                       682.36 μs            |                 674              |                       459.91 ms            | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        4.22 ms →        1.22 ms  (-71.08%) |     273   →     337    (+23.44%) |        1.15 s  →      411.01 ms  (-64.31%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        2.69 ms →        7.33 ms (+172.27%) |      97   →      54    (-44.33%) |      261.21 ms →      395.93 ms  (+51.57%) | 
  │ │ │ │     ├ sddk::transform                                         |        2.59 ms                             |      97                          |      251.05 ms                             | 
  │ │ │ │     │ ├ sddk::transform|init                                  |        9.46 μs                             |      97                          |      918.05 μs                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       11.04 μs                             |      97                          |        1.07 ms                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                         4.40 ms            |                  89              |                       391.66 ms            | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                         3.16 ms            |                 124              |                       391.49 ms            | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      359.00 ns →      382.32 ns   (+6.49%) |      17   →      19    (+11.76%) |        6.10 μs →        7.26 μs  (+19.02%) | 
! │ │ │ └ sirius::K_point_set::sync_band_energies                       |       21.09 μs →       19.24 μs   (-8.77%) |      17   →      19    (+11.76%) |      358.58 μs →      365.61 μs   (+1.96%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.50 ms →        1.52 ms   (+1.05%) |      17   →      19    (+11.76%) |       25.52 ms →       28.82 ms  (+12.94%) | 
- │ │ ├ sirius::Density::generate                                       |      564.27 ms →      568.72 ms   (+0.79%) |      17   →      19    (+11.76%) |        9.59 s  →       10.81 s   (+12.65%) | 
! │ │ │ ├ sirius::Density::generate_valence                             |      418.77 ms →      385.96 ms   (-7.83%) |      17   →      19    (+11.76%) |        7.12 s  →        7.33 s    (+3.01%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        9.68 μs →       10.19 μs   (+5.28%) |      17   →      19    (+11.76%) |      164.52 μs →      193.57 μs  (+17.66%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        8.67 μs →        9.72 μs  (+12.17%) |      17   →      19    (+11.76%) |      147.38 μs →      184.76 μs  (+25.36%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       17.72 ms →       47.27 ms (+166.83%) |      17   →      19    (+11.76%) |      301.17 ms →      898.17 ms (+198.22%) | 
! │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.37 μs →        7.23 μs   (-1.87%) |      17   →      19    (+11.76%) |      125.25 μs →      137.36 μs   (+9.67%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        2.81 ms →        7.98 ms (+184.38%) |      17   →      19    (+11.76%) |       47.72 ms →      151.68 ms (+217.83%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       13.89 ms →       38.23 ms (+175.21%) |      17   →      19    (+11.76%) |      236.17 ms →      726.44 ms (+207.59%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      937.47 ns →      636.74 ns  (-32.08%) |      17   →      19    (+11.76%) |       15.94 μs →       12.10 μs  (-24.09%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      127.49 ms →       98.88 ms  (-22.44%) |      17   →      19    (+11.76%) |        2.17 s  →        1.88 s   (-13.31%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.96 ms →        2.07 ms   (+5.36%) |      17   →      19    (+11.76%) |       33.40 ms →       39.33 ms  (+17.75%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |      233.83 ms →      195.49 ms  (-16.40%) |      17   →      19    (+11.76%) |        3.98 s  →        3.71 s    (-6.56%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |      233.61 ms →      195.26 ms  (-16.41%) |      17   →      19    (+11.76%) |        3.97 s  →        3.71 s    (-6.58%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      117.47 ms →      154.32 ms  (+31.36%) |      17   →      19    (+11.76%) |        2.00 s  →        2.93 s   (+46.82%) | 
- │ │ │ │ └ sirius::symmetrize_function|fpw                             |      117.47 ms →      154.31 ms  (+31.36%) |      17   →      19    (+11.76%) |        2.00 s  →        2.93 s   (+46.82%) | 
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       33.98 ms →       72.93 ms (+114.62%) |      17   →      19    (+11.76%) |      577.65 ms →        1.39 s  (+139.87%) | 
! │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       70.07 ms →       68.07 ms   (-2.85%) |      17   →      19    (+11.76%) |        1.19 s  →        1.29 s    (+8.58%) | 
- │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.78 ms →       12.66 ms   (-0.92%) |      17   →      19    (+11.76%) |      217.23 ms →      240.55 ms  (+10.74%) | 
- │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.98 ms →       23.66 ms   (-1.35%) |      17   →      19    (+11.76%) |      407.67 ms →      449.47 ms  (+10.25%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        4.04 ms →        4.79 ms  (+18.47%) |      17   →      19    (+11.76%) |       68.73 ms →       91.00 ms  (+32.41%) | 
- │ │ ├ sirius::Density::mix                                            |      130.11 ms →      130.63 ms   (+0.40%) |      17   →      19    (+11.76%) |        2.21 s  →        2.48 s   (+12.22%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      875.36 μs →      897.22 μs   (+2.50%) |      17   →      19    (+11.76%) |       14.88 ms →       17.05 ms  (+14.56%) | 
- │ │ │ ├ sirius::Periodic_function|inner                               |        4.88 ms →        4.68 ms   (-4.13%) |     199   →     229    (+15.08%) |      971.77 ms →        1.07 s   (+10.33%) | 
- │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.81 ms →        4.62 ms   (-3.99%) |     199   →     229    (+15.08%) |      957.28 ms →        1.06 s   (+10.48%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.81 ms →        4.62 ms   (-3.99%) |     199   →     229    (+15.08%) |      957.17 ms →        1.06 s   (+10.48%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        5.17 ms →        6.36 ms  (+22.87%) |      17   →      19    (+11.76%) |       87.95 ms →      120.78 ms  (+37.33%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        4.44 ms →        5.60 ms  (+26.02%) |      17   →      19    (+11.76%) |       75.53 ms →      106.38 ms  (+40.84%) | 
- │ │ ├ sirius::Potential::generate                                     |      364.58 ms →      363.52 ms   (-0.29%) |      17   →      19    (+11.76%) |        6.20 s  →        6.91 s   (+11.44%) | 
! │ │ │ ├ sirius::Potential::poisson                                    |       45.45 ms →       43.03 ms   (-5.34%) |      17   →      19    (+11.76%) |      772.71 ms →      817.50 ms   (+5.80%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.88 ms →       11.96 ms (+315.56%) |      17   →      19    (+11.76%) |       48.94 ms →      227.28 ms (+364.44%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |        5.62 ms →        5.90 ms   (+4.88%) |      17   →      19    (+11.76%) |       95.62 ms →      112.09 ms  (+17.22%) | 
! │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.83 ms →        4.64 ms   (-4.08%) |      17   →      19    (+11.76%) |       82.16 ms →       88.09 ms   (+7.21%) | 
! │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.83 ms →        4.64 ms   (-4.08%) |      17   →      19    (+11.76%) |       82.15 ms →       88.07 ms   (+7.20%) | 
- │ │ │ ├ sirius::Periodic_function::add                                |      779.17 μs →      793.77 μs   (+1.87%) |      34   →      38    (+11.76%) |       26.49 ms →       30.16 ms  (+13.86%) | 
- │ │ │ ├ sirius::Potential::xc                                         |       44.21 ms →       45.55 ms   (+3.03%) |      17   →      19    (+11.76%) |      751.54 ms →      865.43 ms  (+15.15%) | 
- │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       44.20 ms →       44.37 ms   (+0.37%) |      17   →      19    (+11.76%) |      751.48 ms →      843.00 ms  (+12.18%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function                          |      654.75 μs →      684.54 μs   (+4.55%) |      34   →      38    (+11.76%) |       22.26 ms →       26.01 ms  (+16.85%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.00 ms →        5.03 ms   (+0.59%) |      17   →      19    (+11.76%) |       85.07 ms →       95.64 ms  (+12.42%) | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        2.97 ms →        3.40 ms  (+14.16%) |      17   →      19    (+11.76%) |       50.56 ms →       64.51 ms  (+27.59%) | 
- │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.95 ms →      268.53 ms   (-0.16%) |      17   →      19    (+11.76%) |        4.57 s  →        5.10 s   (+11.59%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      152.35 ns →      239.53 ns  (+57.22%) |      17   →      19    (+11.76%) |        2.59 μs →        4.55 μs  (+75.71%) | 
! │ │ ├ sirius::Field4D::symmetrize                                     |       96.26 ms →       94.04 ms   (-2.31%) |      17   →      19    (+11.76%) |        1.64 s  →        1.79 s    (+9.18%) | 
! │ │ │ └ sirius::symmetrize_function|fpw                               |       96.26 ms →       94.03 ms   (-2.32%) |      17   →      19    (+11.76%) |        1.64 s  →        1.79 s    (+9.18%) | 
- │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.19 ms →       13.28 ms   (+0.71%) |      17   →      19    (+11.76%) |      224.19 ms →      252.33 ms  (+12.55%) | 
! │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       69.75 ms →       67.54 ms   (-3.17%) |      17   →      19    (+11.76%) |        1.19 s  →        1.28 s    (+8.22%) | 
- │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.70 ms →       12.59 ms   (-0.88%) |      17   →      19    (+11.76%) |      215.86 ms →      239.12 ms  (+10.78%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.71 ms →        4.41 ms  (+18.86%) |      17   →      19    (+11.76%) |       63.05 ms →       83.76 ms  (+32.84%) | 
! │ │ ├ sirius::Periodic_function|inner                                 |        4.92 ms →        4.61 ms   (-6.28%) |     119   →     133    (+11.76%) |      585.97 ms →      613.76 ms   (+4.74%) | 
! │ │ │ └ sirius::Periodic_function|inner_local                         |        4.76 ms →        4.56 ms   (-4.15%) |     119   →     133    (+11.76%) |      566.67 ms →      607.05 ms   (+7.13%) | 
! │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.76 ms →        4.56 ms   (-4.15%) |     119   →     133    (+11.76%) |      566.57 ms →      606.98 ms   (+7.13%) | 
- │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.53 ms →        4.83 ms   (+6.49%) |      51   →      57    (+11.76%) |      231.19 ms →      275.16 ms  (+19.02%) | 
- │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.52 ms →        4.73 ms   (+4.61%) |      51   →      57    (+11.76%) |      230.77 ms →      269.81 ms  (+16.92%) | 
- │ │ ├ sirius::Periodic_function::integrate                            |        4.52 ms →        4.53 ms   (+0.10%) |      17   →      19    (+11.76%) |       76.87 ms →       86.00 ms  (+11.88%) | 
! │ │ └ sirius::Density::get_magnetisation                              |       79.44 μs →       77.18 μs   (-2.85%) |      17   →      19    (+11.76%) |        1.35 ms →        1.47 ms   (+8.58%) | 
! │ │   └ sirius::Density::compute_atomic_mag_mom                       |       74.03 μs →       72.40 μs   (-2.19%) |      17   →      19    (+11.76%) |        1.26 ms →        1.38 ms   (+9.32%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.55 ms →        5.14 ms   (-7.34%) |       2   →       2              |       11.10 ms →       10.28 ms   (-7.34%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.78 ms →        4.96 ms   (+3.78%) |       6   →       6              |       28.66 ms →       29.75 ms   (+3.78%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.74 ms →        4.59 ms   (-3.32%) |       6   →       6              |       28.47 ms →       27.52 ms   (-3.32%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.74 ms →        4.58 ms   (-3.41%) |       6   →       6              |       28.46 ms →       27.49 ms   (-3.41%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.53 ms →        4.72 ms   (+4.22%) |       3   →       3              |       13.60 ms →       14.17 ms   (+4.22%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.53 ms →        4.72 ms   (+4.20%) |       3   →       3              |       13.58 ms →       14.15 ms   (+4.20%) | 
  ├ sirius::Periodic_function|inner                                     |        4.76 ms →        4.53 ms   (-4.66%) |       2   →       2              |        9.51 ms →        9.07 ms   (-4.66%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.75 ms →        4.53 ms   (-4.66%) |       2   →       2              |        9.50 ms →        9.06 ms   (-4.66%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.75 ms →        4.53 ms   (-4.67%) |       2   →       2              |        9.50 ms →        9.06 ms   (-4.67%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.56 ms →        4.73 ms   (+3.90%) |       1   →       1              |        4.56 ms →        4.73 ms   (+3.90%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.55 ms →        4.73 ms   (+3.94%) |       1   →       1              |        4.55 ms →        4.73 ms   (+3.94%) | 
  └ sirius::finalize                                                    |      770.93 ms →      750.68 ms   (-2.63%) |       1   →       1              |      770.93 ms →      750.68 ms   (-2.63%) | 
  ====================================================================================================================================================================================================
```
