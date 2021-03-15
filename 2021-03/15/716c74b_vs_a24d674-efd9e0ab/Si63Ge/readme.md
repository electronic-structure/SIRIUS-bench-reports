# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs 716c74b9e40f2dc514547b13861ce8c977f50e6c
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |       77.01 s  →       47.40 s   (-38.45%) |       1   →       1              |       77.01 s  →       47.40 s   (-38.45%) | 
  ├ sirius::initialize                                                  |        2.85 s  →        2.85 s    (-0.02%) |       1   →       1              |        2.85 s  →        2.85 s    (-0.02%) | 
  ├ sirius::Simulation_context::initialize                              |        3.60 s  →        3.73 s    (+3.68%) |       1   →       1              |        3.60 s  →        3.73 s    (+3.68%) | 
- │ ├ sirius::Simulation_context::init_comm                             |       40.45 ms →       47.02 ms  (+16.25%) |       1   →       1              |       40.45 ms →       47.02 ms  (+16.25%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      121.94 ms →      159.68 ms  (+30.94%) |       1   →       1              |      121.94 ms →      159.68 ms  (+30.94%) | 
- │ │ ├ sirius::Atom_type::init                                         |       50.53 ms →       71.28 ms  (+41.08%) |       2   →       2              |      101.05 ms →      142.57 ms  (+41.08%) | 
+ │ │ └ sirius::Unit_cell::update                                       |       20.80 ms →       16.96 ms  (-18.48%) |       1   →       1              |       20.80 ms →       16.96 ms  (-18.48%) | 
+ │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        7.39 ms →        4.97 ms  (-32.70%) |       1   →       1              |        7.39 ms →        4.97 ms  (-32.70%) | 
+ │ │   └ sirius::Unit_cell::get_symmetry                               |       13.34 ms →       11.93 ms  (-10.60%) |       1   →       1              |       13.34 ms →       11.93 ms  (-10.60%) | 
+ │ │     └ sirius::Unit_cell_symmetry                                  |       13.26 ms →       11.85 ms  (-10.64%) |       1   →       1              |       13.26 ms →       11.85 ms  (-10.64%) | 
+ │ │       ├ sirius::Unit_cell_symmetry|spg                            |        3.82 ms →        2.75 ms  (-28.04%) |       1   →       1              |        3.82 ms →        2.75 ms  (-28.04%) | 
+ │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.38 ms →      501.63 μs  (-78.93%) |       1   →       1              |        2.38 ms →      501.63 μs  (-78.93%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       17.81 μs →       16.69 μs   (-6.30%) |       1   →       1              |       17.81 μs →       16.69 μs   (-6.30%) | 
  │ └ sirius::Simulation_context::update                                |        3.26 s  →        3.43 s    (+5.24%) |       1   →       1              |        3.26 s  →        3.43 s    (+5.24%) | 
  │   ├ sirius::Unit_cell::update                                       |        7.04 ms →        6.78 ms   (-3.73%) |       1   →       1              |        7.04 ms →        6.78 ms   (-3.73%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.64 ms →        3.49 ms   (-4.08%) |       1   →       1              |        3.64 ms →        3.49 ms   (-4.08%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.36 ms →        3.22 ms   (-3.91%) |       1   →       1              |        3.36 ms →        3.22 ms   (-3.91%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.29 ms →        3.17 ms   (-3.77%) |       1   →       1              |        3.29 ms →        3.17 ms   (-3.77%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.73 ms →        2.64 ms   (-3.40%) |       1   →       1              |        2.73 ms →        2.64 ms   (-3.40%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      504.26 μs →      487.93 μs   (-3.24%) |       1   →       1              |      504.26 μs →      487.93 μs   (-3.24%) | 
+ │   │     └ sirius::Unit_cell_symmetry|mag                            |       26.74 μs →       13.96 μs  (-47.82%) |       1   →       1              |       26.74 μs →       13.96 μs  (-47.82%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      212.60 ms →      213.36 ms   (+0.36%) |       2   →       2              |      425.20 ms →      426.72 ms   (+0.36%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.11 ms →       15.19 ms   (+0.57%) |       2   →       2              |       30.21 ms →       30.38 ms   (+0.57%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.28 ms →       13.27 ms   (-0.05%) |       1   →       1              |       13.28 ms →       13.27 ms   (-0.05%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.35 ms →       56.28 ms   (-0.13%) |       2   →       2              |      112.71 ms →      112.56 ms   (-0.13%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.16 ms →       44.93 ms   (-0.53%) |       2   →       2              |       90.33 ms →       89.85 ms   (-0.53%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.28 ms →       60.11 ms   (-0.28%) |       4   →       4              |      241.10 ms →      240.43 ms   (-0.28%) | 
  │   ├ sddk::Gvec::init                                                |       94.21 ms →       92.99 ms   (-1.30%) |       2   →       2              |      188.42 ms →      185.97 ms   (-1.30%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       70.46 ms →       69.56 ms   (-1.27%) |       2   →       2              |      140.91 ms →      139.13 ms   (-1.27%) | 
  │   ├ sddk::Gvec_shells                                               |      101.94 ms →       95.73 ms   (-6.09%) |       1   →       1              |      101.94 ms →       95.73 ms   (-6.09%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.70 ms →        1.72 ms   (+1.28%) |       1   →       1              |        1.70 ms →        1.72 ms   (+1.28%) | 
- │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      463.70 ms →      550.28 ms  (+18.67%) |       2   →       2              |      927.39 ms →        1.10 s   (+18.67%) | 
+ ├ sirius::K_point_set::create_k_mesh                                  |      167.17 ms →      147.52 ms  (-11.76%) |       1   →       1              |      167.17 ms →      147.52 ms  (-11.76%) | 
- │ ├ sirius::K_point::K_point                                          |        1.29 μs →        4.96 μs (+284.49%) |       4   →       4              |        5.16 μs →       19.83 μs (+284.49%) | 
+ │ └ sirius::K_point_set::initialize                                   |      167.11 ms →      147.43 ms  (-11.78%) |       1   →       1              |      167.11 ms →      147.43 ms  (-11.78%) | 
  │   └ sirius::K_point::initialize                                     |       28.78 ms →       28.63 ms   (-0.49%) |       1   →       1              |       28.78 ms →       28.63 ms   (-0.49%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       11.07 ms →       11.31 ms   (+2.23%) |       1   →       1              |       11.07 ms →       11.31 ms   (+2.23%) | 
  │     │ └ sddk::Gvec::init                                            |        4.77 ms →        4.94 ms   (+3.65%) |       1   →       1              |        4.77 ms →        4.94 ms   (+3.65%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        7.30 μs                             |       1                          |        7.30 μs                             | 
  │     └ sirius::K_point::update                                       |       14.92 ms →       14.42 ms   (-3.32%) |       1   →       1              |       14.92 ms →       14.42 ms   (-3.32%) | 
  │       └ sirius::Beta_projectors                                     |       11.00 ms →       10.41 ms   (-5.44%) |       1   →       1              |       11.00 ms →       10.41 ms   (-5.44%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.75 ms →        8.38 ms   (-4.30%) |       1   →       1              |        8.75 ms →        8.38 ms   (-4.30%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.60 ms                             |       2                          |        5.20 ms                             | 
  ├ sirius::Potential                                                   |       55.18 ms →       51.97 ms   (-5.82%) |       1   →       1              |       55.18 ms →       51.97 ms   (-5.82%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.91 ms                             |       6                          |       17.43 ms                             | 
  │ └ sirius::Potential::update                                         |       37.32 ms →       37.01 ms   (-0.83%) |       1   →       1              |       37.32 ms →       37.01 ms   (-0.83%) | 
  │   └ sirius::Potential::generate_local_potential                     |       36.93 ms →       36.62 ms   (-0.82%) |       1   →       1              |       36.93 ms →       36.62 ms   (-0.82%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       26.71 ms →       29.04 ms   (+8.72%) |       1   →       1              |       26.71 ms →       29.04 ms   (+8.72%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        9.91 ms →        4.42 ms  (-55.37%) |       1   →       1              |        9.91 ms →        4.42 ms  (-55.37%) | 
  ├ sirius::Density                                                     |       43.94 ms →       39.75 ms   (-9.54%) |       1   →       1              |       43.94 ms →       39.75 ms   (-9.54%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.82 ms                             |       2                          |        5.64 ms                             | 
+ │ └ sirius::Density::update                                           |       38.16 ms →       33.97 ms  (-10.96%) |       1   →       1              |       38.16 ms →       33.97 ms  (-10.96%) | 
+ │   └ sirius::Density::generate_pseudo_core_charge_density            |       37.94 ms →       33.73 ms  (-11.09%) |       1   →       1              |       37.94 ms →       33.73 ms  (-11.09%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       28.85 ms →       29.22 ms   (+1.29%) |       1   →       1              |       28.85 ms →       29.22 ms   (+1.29%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        8.78 ms →        3.72 ms  (-57.63%) |       1   →       1              |        8.78 ms →        3.72 ms  (-57.63%) | 
  ├ sirius::Density::initial_density                                    |       62.19 ms →       57.41 ms   (-7.68%) |       1   →       1              |       62.19 ms →       57.41 ms   (-7.68%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       28.05 ms →       28.72 ms   (+2.38%) |       1   →       1              |       28.05 ms →       28.72 ms   (+2.38%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        7.38 ms →        4.50 ms  (-39.06%) |       2   →       2              |       14.76 ms →        9.00 ms  (-39.06%) | 
  │ └ sirius::Periodic_function::integrate                              |        5.70 ms →        5.75 ms   (+0.99%) |       1   →       1              |        5.70 ms →        5.75 ms   (+0.99%) | 
  ├ sirius::Potential::generate                                         |      380.18 ms →      365.25 ms   (-3.93%) |       1   →       1              |      380.18 ms →      365.25 ms   (-3.93%) | 
  │ ├ sirius::Potential::poisson                                        |       43.01 ms →       39.50 ms   (-8.18%) |       1   →       1              |       43.01 ms →       39.50 ms   (-8.18%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       10.83 ms →        3.81 ms  (-64.79%) |       1   →       1              |       10.83 ms →        3.81 ms  (-64.79%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        6.12 ms                             |       1                          |        6.12 ms                             | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.84 ms                             |       1                          |        4.84 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.84 ms                             |       1                          |        4.84 ms                             | 
  │ │ └ sirius::inner                                                   |                         4.83 ms            |                   1              |                         4.83 ms            | 
  │ ├ sirius::Periodic_function::add                                    |      766.57 μs →      702.67 μs   (-8.34%) |       2   →       2              |        1.53 ms →        1.41 ms   (-8.34%) | 
+ │ ├ sirius::Potential::xc                                             |       61.34 ms →       49.42 ms  (-19.43%) |       1   →       1              |       61.34 ms →       49.42 ms  (-19.43%) | 
+ │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       61.34 ms →       48.22 ms  (-21.38%) |       1   →       1              |       61.34 ms →       48.22 ms  (-21.38%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.54 ms                             |       2                          |        5.08 ms                             | 
  │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        3.91 ms                             |       1                          |        3.91 ms                             | 
  │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                    |                        20.12 ms            |                   2              |                        40.23 ms            | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.76 ms →        4.25 ms  (+13.04%) |       1   →       1              |        3.76 ms →        4.25 ms  (+13.04%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      269.13 ms →      267.74 ms   (-0.52%) |       1   →       1              |      269.13 ms →      267.74 ms   (-0.52%) | 
+ │ └ sirius::Potential::generate_PAW_effective_potential               |      481.00 ns →      149.00 ns  (-69.02%) |       1   →       1              |      481.00 ns →      149.00 ns  (-69.02%) | 
- ├ sirius::Hamiltonian0                                                |        6.30 ms →       12.81 ms (+103.27%) |       1   →       1              |        6.30 ms →       12.81 ms (+103.27%) | 
  │ ├ sirius::Local_operator                                            |        5.83 ms →        6.05 ms   (+3.72%) |       1   →       1              |        5.83 ms →        6.05 ms   (+3.72%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.76 ms                             |       1                          |        2.76 ms                             | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.32 ms →        2.54 ms   (+9.54%) |       1   →       1              |        2.32 ms →        2.54 ms   (+9.54%) | 
  │ ├ sirius::Non_local_operator                                        |       73.60 μs →       67.88 μs   (-7.77%) |       2   →       2              |      147.19 μs →      135.75 μs   (-7.77%) | 
- │ ├ sirius::D_operator::initialize                                    |      140.76 μs →        2.21 ms (+1471.74%) |       1   →       1              |      140.76 μs →        2.21 ms (+1471.74%) | 
- │ └ sirius::Q_operator::initialize                                    |      108.43 μs →        4.34 ms (+3899.86%) |       1   →       1              |      108.43 μs →        4.34 ms (+3899.86%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.28 s  →        1.29 s    (+0.95%) |       1   →       1              |        1.28 s  →        1.29 s    (+0.95%) | 
- │ ├ sirius::Hamiltonian_k                                             |       33.17 ms →       44.21 ms  (+33.27%) |       1   →       1              |       33.17 ms →       44.21 ms  (+33.27%) | 
+ │ │ ├ sirius::Local_operator::prepare_k                               |      305.19 μs →      218.37 μs  (-28.45%) |       1   →       1              |      305.19 μs →      218.37 μs  (-28.45%) | 
- │ │ └ sirius::Beta_projectors_base::prepare                           |       32.86 ms →       43.99 ms  (+33.85%) |       1   →       1              |       32.86 ms →       43.99 ms  (+33.85%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.25 s  →        1.25 s    (+0.04%) |       1   →       1              |        1.25 s  →        1.25 s    (+0.04%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       81.40 ms                             |       4                          |      325.58 ms                             | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       48.56 ms →       50.23 ms   (+3.43%) |       1   →       1              |       48.56 ms →       50.23 ms   (+3.43%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        7.69 ms →        6.96 ms   (-9.39%) |       1   →       1              |        7.69 ms →        6.96 ms   (-9.39%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      315.08 ms →      336.72 ms   (+6.87%) |       1   →       1              |      315.08 ms →      336.72 ms   (+6.87%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      244.90 ms →      248.30 ms   (+1.39%) |       1   →       1              |      244.90 ms →      248.30 ms   (+1.39%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.92 μs →        3.42 μs  (-12.63%) |       1   →       1              |        3.92 μs →        3.42 μs  (-12.63%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.02 μs                             |       1                          |        3.02 μs                             | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      483.00 ns                             |       1                          |      483.00 ns                             | 
- │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      619.00 ns →      897.00 ns  (+44.91%) |       1   →       1              |      619.00 ns →      897.00 ns  (+44.91%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.18 ms →        3.14 ms   (-1.24%) |       1   →       1              |        3.18 ms →        3.14 ms   (-1.24%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.27 ms →       21.32 ms   (+0.27%) |       1   →       1              |       21.27 ms →       21.32 ms   (+0.27%) | 
- │ │ │ └ sirius::Non_local_operator::apply                             |       22.84 ms →       31.95 ms  (+39.89%) |       2   →       2              |       45.68 ms →       63.90 ms  (+39.89%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.70 ms →       14.68 ms   (-0.11%) |       2   →       2              |       29.39 ms →       29.36 ms   (-0.11%) | 
  │ │ │ ├ sddk::inner                                                   |       14.49 ms                             |       2                          |       28.97 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       25.48 μs                             |       2                          |       50.97 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        14.47 ms            |                   2              |                        28.93 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        86.50 ns            |                   2              |                       173.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        14.33 ms            |                   2              |                        28.66 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                       377.50 ns            |                   2              |                       755.00 ns            | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      249.45 ms →      230.45 ms   (-7.61%) |       1   →       1              |      249.45 ms →      230.45 ms   (-7.61%) | 
  │ │ ├ sddk::transform                                                 |        2.82 ms                             |       1                          |        2.82 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       14.32 μs                             |       1                          |       14.32 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       17.26 μs                             |       1                          |       17.26 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                         2.61 ms            |                   1              |                         2.61 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                         2.60 ms            |                   1              |                         2.60 ms            | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      434.00 ns →      443.00 ns   (+2.07%) |       1   →       1              |      434.00 ns →      443.00 ns   (+2.07%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |       67.23 s  →       37.76 s   (-43.83%) |       1   →       1              |       67.23 s  →       37.76 s   (-43.83%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.44 ms                             |      19                          |       46.31 ms                             | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.35 s                              |      20                          |       66.99 s                              | 
  │ │ ├ sirius::Hamiltonian0                                            |        5.63 ms                             |      20                          |      112.60 ms                             | 
  │ │ │ ├ sirius::Local_operator                                        |        4.89 ms                             |      20                          |       97.78 ms                             | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      551.13 μs                             |      20                          |       11.02 ms                             | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.30 ms                             |      20                          |       66.01 ms                             | 
  │ │ │ ├ sirius::Non_local_operator                                    |      226.78 μs                             |      40                          |        9.07 ms                             | 
  │ │ │ ├ sirius::D_operator::initialize                                |      109.13 μs                             |      20                          |        2.18 ms                             | 
  │ │ │ └ sirius::Q_operator::initialize                                |       97.05 μs                             |      20                          |        1.94 ms                             | 
  │ │ ├ sirius::Band::solve                                             |        2.11 s                              |      20                          |       42.15 s                              | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      210.21 μs                             |      20                          |        4.20 ms                             | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      201.80 μs                             |      20                          |        4.04 ms                             | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        6.47 μs                             |      20                          |      129.46 μs                             | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.95 s                              |      20                          |       39.00 s                              | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       90.67 ms                             |      20                          |        1.81 s                              | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |       11.62 ms                             |     120                          |        1.39 s                              | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       15.52 ms                             |      20                          |      310.44 ms                             | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      451.66 μs                             |      20                          |        9.03 ms                             | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        7.31 ms                             |      40                          |      292.43 ms                             | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.84 s                              |      20                          |       36.73 s                              | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       52.57 ms                             |     250                          |       13.14 s                              | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       33.50 ms                             |     250                          |        8.37 s                              | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.21 μs                             |     250                          |      552.08 μs                             | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.90 μs                             |     250                          |      474.66 μs                             | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      472.98 ns                             |     250                          |      118.24 μs                             | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      557.34 ns                             |     250                          |      139.34 μs                             | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.71 ms                             |     250                          |      677.98 ms                             | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.42 ms                             |     250                          |      856.09 ms                             | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        6.46 ms                             |     500                          |        3.23 s                              | 
  │ │ │ │   ├ sddk::orthogonalize                                       |        6.64 ms                             |     250                          |        1.66 s                              | 
  │ │ │ │   │ ├ sddk::inner                                             |      810.25 μs                             |     480                          |      388.92 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       24.29 μs                             |     480                          |       11.66 ms                             | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      302.75 μs                             |     250                          |       75.69 ms                             | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        2.13 ms                             |     250                          |      533.49 ms                             | 
  │ │ │ │   │ └ sddk::transform                                         |        2.88 ms                             |     230                          |      661.55 ms                             | 
  │ │ │ │   │   ├ sddk::transform|init                                  |       18.93 μs                             |     230                          |        4.35 ms                             | 
  │ │ │ │   │   └ sddk::transform|local                                 |        7.92 μs                             |     690                          |        5.46 ms                             | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.72 ms                             |     250                          |      429.36 ms                             | 
  │ │ │ │   │ └ sddk::inner                                             |        1.52 ms                             |     250                          |      380.02 ms                             | 
  │ │ │ │   │   └ sddk::inner|local                                     |       24.93 μs                             |     250                          |        6.23 ms                             | 
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       82.72 ms                             |     250                          |       20.68 s                              | 
  │ │ │ │   ├ sirius::residuals                                         |        2.60 ms                             |     245                          |      636.48 ms                             | 
  │ │ │ │   │ ├ sddk::transform                                         |        1.75 ms                             |     231                          |      403.36 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       16.38 μs                             |     231                          |        3.78 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       10.72 μs                             |     462                          |        4.95 ms                             | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      931.43 μs                             |     231                          |      215.16 ms                             | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        7.17 ms                             |      25                          |      179.20 ms                             | 
  │ │ │ │     └ sddk::transform                                         |        5.89 ms                             |      30                          |      176.65 ms                             | 
  │ │ │ │       ├ sddk::transform|init                                  |       11.57 μs                             |      30                          |      347.15 μs                             | 
  │ │ │ │       └ sddk::transform|local                                 |       12.06 μs                             |      35                          |      422.02 μs                             | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      452.40 ns                             |      20                          |        9.05 μs                             | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       21.75 μs                             |      20                          |      434.91 μs                             | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.49 ms                             |      20                          |       29.73 ms                             | 
  │ │ ├ sirius::Density::generate                                       |      568.77 ms                             |      20                          |       11.38 s                              | 
  │ │ │ ├ sirius::Density::generate_valence                             |      408.56 ms                             |      20                          |        8.17 s                              | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        7.32 μs                             |      20                          |      146.43 μs                             | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        6.86 μs                             |      20                          |      137.15 μs                             | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       18.77 ms                             |      20                          |      375.36 ms                             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.92 μs                             |      20                          |      158.47 μs                             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        3.10 ms                             |      20                          |       61.95 ms                             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       14.65 ms                             |      20                          |      293.01 ms                             | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      852.35 ns                             |      20                          |       17.05 μs                             | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      126.39 ms                             |      20                          |        2.53 s                              | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.97 ms                             |      20                          |       39.49 ms                             | 
  │ │ │ │ └ sirius::Density::augment                                    |      227.50 ms                             |      20                          |        4.55 s                              | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |      227.28 ms                             |      20                          |        4.55 s                              | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      131.77 ms                             |      20                          |        2.64 s                              | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      131.76 ms                             |      20                          |        2.64 s                              | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       46.17 ms                             |      20                          |      923.31 ms                             | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       72.33 ms                             |      20                          |        1.45 s                              | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.63 ms                             |      20                          |      252.63 ms                             | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.64 ms                             |      20                          |      472.73 ms                             | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        4.80 ms                             |      20                          |       95.97 ms                             | 
  │ │ ├ sirius::Density::mix                                            |      136.72 ms                             |      20                          |        2.73 s                              | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      838.56 μs                             |      20                          |       16.77 ms                             | 
  │ │ │ ├ sirius::Periodic_function|inner                               |        5.10 ms                             |     244                          |        1.24 s                              | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |        5.01 ms                             |     244                          |        1.22 s                              | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        5.01 ms                             |     244                          |        1.22 s                              | 
  │ │ │ └ sirius::Density::mixer_output                                 |        6.42 ms                             |      20                          |      128.34 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.64 ms                             |      20                          |      112.77 ms                             | 
  │ │ ├ sirius::Potential::generate                                     |      374.42 ms                             |      20                          |        7.49 s                              | 
  │ │ │ ├ sirius::Potential::poisson                                    |       43.95 ms                             |      20                          |      879.00 ms                             | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       11.24 ms                             |      20                          |      224.85 ms                             | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |        6.61 ms                             |      20                          |      132.10 ms                             | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.83 ms                             |      20                          |       96.67 ms                             | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.83 ms                             |      20                          |       96.65 ms                             | 
  │ │ │ ├ sirius::Periodic_function::add                                |      745.83 μs                             |      40                          |       29.83 ms                             | 
  │ │ │ ├ sirius::Potential::xc                                         |       54.96 ms                             |      20                          |        1.10 s                              | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       54.96 ms                             |      20                          |        1.10 s                              | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |      645.64 μs                             |      40                          |       25.83 ms                             | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.18 ms                             |      20                          |       83.69 ms                             | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.78 ms                             |      20                          |       75.53 ms                             | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.84 ms                             |      20                          |        5.38 s                              | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      199.50 ns                             |      20                          |        3.99 μs                             | 
  │ │ ├ sirius::Field4D::symmetrize                                     |       98.45 ms                             |      20                          |        1.97 s                              | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |       98.45 ms                             |      20                          |        1.97 s                              | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.31 ms                             |      20                          |      266.25 ms                             | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       71.90 ms                             |      20                          |        1.44 s                              | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.61 ms                             |      20                          |      252.10 ms                             | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        4.52 ms                             |      20                          |       90.31 ms                             | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.77 ms                             |     140                          |      668.11 ms                             | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.76 ms                             |     140                          |      665.71 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.75 ms                             |     140                          |      665.59 ms                             | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.55 ms                             |      60                          |      272.74 ms                             | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.53 ms                             |      60                          |      272.04 ms                             | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.55 ms                             |      20                          |       90.93 ms                             | 
  │ │ └ sirius::Density::get_magnetisation                              |       76.74 μs                             |      20                          |        1.53 ms                             | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |       71.41 μs                             |      20                          |        1.43 ms                             | 
  │ ├ sirius::Density                                                   |                        51.18 ms            |                   1              |                        51.18 ms            | 
  │ │ └ sirius::Density::update                                         |                        45.39 ms            |                   1              |                        45.39 ms            | 
  │ │   └ sirius::Density::generate_pseudo_core_charge_density          |                        45.09 ms            |                   1              |                        45.09 ms            | 
  │ │     ├ sirius::Simulation_context::make_periodic_function          |                        29.11 ms            |                   1              |                        29.11 ms            | 
  │ │     └ sirius::Smooth_periodic_function::fft_transform             |                         4.33 ms            |                   1              |                         4.33 ms            | 
  │ ├ sirius::Hamiltonian0                                              |                        11.02 ms            |                  15              |                       165.24 ms            | 
  │ │ ├ sirius::Local_operator                                          |                         4.30 ms            |                  15              |                        64.45 ms            | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |                         2.64 ms            |                  15              |                        39.61 ms            | 
  │ │ ├ sirius::Non_local_operator                                      |                       141.06 μs            |                  30              |                         4.23 ms            | 
  │ │ ├ sirius::D_operator::initialize                                  |                         2.15 ms            |                  15              |                        32.22 ms            | 
  │ │ └ sirius::Q_operator::initialize                                  |                         4.22 ms            |                  15              |                        63.31 ms            | 
  │ ├ sirius::Band::solve                                               |                         1.30 s             |                  15              |                        19.45 s             | 
  │ │ ├ sirius::Hamiltonian_k                                           |                       191.99 μs            |                  15              |                         2.88 ms            | 
  │ │ │ ├ sirius::Local_operator::prepare_k                             |                       180.88 μs            |                  15              |                         2.71 ms            | 
  │ │ │ └ sirius::Beta_projectors_base::prepare                         |                         6.23 μs            |                  15              |                        93.48 μs            | 
  │ │ ├ sirius::Band::diag_pseudo_potential_davidson                    |                         1.13 s             |                  15              |                        16.99 s             | 
  │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                           |                        17.98 ms            |                  15              |                       269.66 ms            | 
  │ │ │ ├ sirius::Hamiltonian_k::apply_h_s                              |                        83.14 ms            |                 116              |                         9.64 s             | 
  │ │ │ │ ├ sirius::Local_operator::apply_h                             |                        48.71 ms            |                 116              |                         5.65 s             | 
  │ │ │ │ │ ├ sddk::matrix_storage::remap_forward                       |                         1.86 μs            |                 116              |                       216.03 μs            | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_backward                      |                       699.12 ns            |                 116              |                        81.10 μs            | 
  │ │ │ │ ├ sirius::Beta_projectors_base::generate                      |                         3.57 ms            |                 116              |                       413.67 ms            | 
  │ │ │ │ ├ sirius::Beta_projectors_base::inner                         |                         4.38 ms            |                 116              |                       508.02 ms            | 
  │ │ │ │ └ sirius::Non_local_operator::apply                           |                        13.23 ms            |                 232              |                         3.07 s             | 
  │ │ │ ├ sddk::orthogonalize                                           |                        10.72 ms            |                 116              |                         1.24 s             | 
  │ │ │ │ ├ sddk::wf_inner                                              |                         1.58 ms            |                 217              |                       341.88 ms            | 
  │ │ │ │ │ ├ sddk::wf_inner|scale                                      |                       101.28 ns            |                 217              |                        21.98 μs            | 
  │ │ │ │ │ ├ sddk::wf_inner|pw                                         |                         1.41 ms            |                 217              |                       305.46 ms            | 
  │ │ │ │ │ └ sddk::wf_inner|scale_back                                 |                       321.01 ns            |                 217              |                        69.66 μs            | 
  │ │ │ │ ├ sddk::orthogonalize|tmtrx                                   |                       491.41 μs            |                 116              |                        57.00 ms            | 
  │ │ │ │ ├ sddk::orthogonalize|transform                               |                         4.17 ms            |                 116              |                       483.39 ms            | 
  │ │ │ │ └ sddk::wf_trans                                              |                         3.57 ms            |                 101              |                       360.31 ms            | 
  │ │ │ │   └ sddk::wf_trans|pw                                         |                         1.19 ms            |                 303              |                       360.08 ms            | 
  │ │ │ ├ sirius::Band::set_subspace_mtrx                               |                         2.25 ms            |                 116              |                       260.44 ms            | 
  │ │ │ │ └ sddk::wf_inner                                              |                         2.18 ms            |                 116              |                       253.07 ms            | 
  │ │ │ │   ├ sddk::wf_inner|scale                                      |                       110.37 ns            |                 116              |                        12.80 μs            | 
  │ │ │ │   ├ sddk::wf_inner|pw                                         |                         2.01 ms            |                 116              |                       233.34 ms            | 
  │ │ │ │   └ sddk::wf_inner|scale_back                                 |                       272.46 ns            |                 116              |                        31.61 μs            | 
  │ │ │ ├ Eigensolver_cuda|zheevdx                                      |                        30.16 ms            |                 116              |                         3.50 s             | 
  │ │ │ ├ sirius::residuals                                             |                         3.30 ms            |                 114              |                       376.10 ms            | 
  │ │ │ │ ├ sddk::wf_trans                                              |                         1.65 ms            |                 101              |                       166.42 ms            | 
  │ │ │ │ │ └ sddk::wf_trans|pw                                         |                       822.49 μs            |                 202              |                       166.14 ms            | 
  │ │ │ │ └ sirius::normalized_preconditioned_residuals                 |                         1.87 ms            |                 101              |                       188.38 ms            | 
  │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|update_phi       |                         4.11 ms            |                  47              |                       193.08 ms            | 
  │ │ │   └ sddk::wf_trans                                              |                         2.39 ms            |                  79              |                       189.09 ms            | 
  │ │ │     └ sddk::wf_trans|pw                                         |                         1.70 ms            |                 111              |                       188.94 ms            | 
  │ │ ├ sirius::Beta_projectors_base::dismiss                           |                       424.87 ns            |                  15              |                         6.37 μs            | 
  │ │ └ sirius::K_point_set::sync_band                                  |                        64.40 μs            |                  15              |                       965.99 μs            | 
  │ ├ sirius::K_point_set::find_band_occupancies                        |                         1.00 ms            |                  15              |                        15.01 ms            | 
  │ │ └ sirius::K_point_set::sync_band                                  |                        13.17 μs            |                  15              |                       197.55 μs            | 
  │ ├ sirius::Density::generate                                         |                       568.01 ms            |                  15              |                         8.52 s             | 
  │ │ ├ sirius::Density::generate_valence                               |                       392.43 ms            |                  15              |                         5.89 s             | 
  │ │ │ ├ sddk::matrix_storage::remap_forward                           |                         5.59 μs            |                  15              |                        83.79 μs            | 
  │ │ │ ├ sirius::Density::add_k_point_contribution_dm                  |                        41.67 ms            |                  15              |                       625.05 ms            | 
  │ │ │ │ ├ sirius::Beta_projectors_base::prepare                       |                         9.45 μs            |                  15              |                       141.79 μs            | 
  │ │ │ │ ├ sirius::Beta_projectors_base::generate                      |                         7.01 ms            |                  15              |                       105.09 ms            | 
  │ │ │ │ ├ sirius::Beta_projectors_base::inner                         |                        33.61 ms            |                  15              |                       504.13 ms            | 
  │ │ │ │ └ sirius::Beta_projectors_base::dismiss                       |                       584.67 ns            |                  15              |                         8.77 μs            | 
  │ │ │ ├ sirius::Density::add_k_point_contribution_rg                  |                       104.68 ms            |                  15              |                         1.57 s             | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |                         2.39 ms            |                  15              |                        35.78 ms            | 
  │ │ │ └ sirius::Density::augment                                      |                       208.32 ms            |                  15              |                         3.12 s             | 
  │ │ │   └ sirius::Density::generate_rho_aug                           |                       208.10 ms            |                  15              |                         3.12 s             | 
  │ │ ├ sirius::Field4D::symmetrize                                     |                       147.51 ms            |                  15              |                         2.21 s             | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |                       147.50 ms            |                  15              |                         2.21 s             | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |                        68.02 ms            |                  15              |                         1.02 s             | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |                        65.91 ms            |                  15              |                       988.72 ms            | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |                        12.91 ms            |                  15              |                       193.71 ms            | 
  │ │ ├ sirius::Density::symmetrize_density_matrix                      |                        24.06 ms            |                  15              |                       360.93 ms            | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |                         4.00 ms            |                  15              |                        60.05 ms            | 
  │ ├ sirius::inner                                                     |                         4.69 ms            |                 189              |                       887.22 ms            | 
  │ ├ sirius::Density::mix                                              |                        77.20 ms            |                  15              |                         1.16 s             | 
  │ │ ├ sirius::Density::mixer_input                                    |                         1.03 ms            |                  15              |                        15.50 ms            | 
  │ │ ├ sirius::inner                                                   |                         4.75 ms            |                 169              |                       803.14 ms            | 
  │ │ └ sirius::Density::mixer_output                                   |                         5.63 ms            |                  15              |                        84.50 ms            | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |                         4.65 ms            |                  15              |                        69.69 ms            | 
  │ ├ sirius::Potential::generate                                       |                       362.97 ms            |                  15              |                         5.44 s             | 
  │ │ ├ sirius::Potential::poisson                                      |                        39.76 ms            |                  15              |                       596.41 ms            | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |                         3.62 ms            |                  15              |                        54.33 ms            | 
  │ │ │ └ sirius::inner                                                 |                         5.25 ms            |                  15              |                        78.74 ms            | 
  │ │ ├ sirius::Periodic_function::add                                  |                       695.37 μs            |                  30              |                        20.86 ms            | 
  │ │ ├ sirius::Potential::xc                                           |                        47.01 ms            |                  15              |                       705.22 ms            | 
  │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                          |                        45.82 ms            |                  15              |                       687.33 ms            | 
  │ │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                  |                        19.59 ms            |                  30              |                       587.78 ms            | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |                         4.13 ms            |                  15              |                        61.89 ms            | 
  │ │ ├ sirius::Potential::generate_D_operator_matrix                   |                       267.67 ms            |                  15              |                         4.02 s             | 
  │ │ └ sirius::Potential::generate_PAW_effective_potential             |                       121.93 ns            |                  15              |                         1.83 μs            | 
  │ ├ sirius::Field4D::symmetrize                                       |                        92.45 ms            |                  15              |                         1.39 s             | 
  │ │ └ sirius::symmetrize_function|fpw                                 |                        92.44 ms            |                  15              |                         1.39 s             | 
  │ │   ├ sddk::Gvec_shells::remap_forward                              |                        13.32 ms            |                  15              |                       199.77 ms            | 
  │ │   ├ sirius::symmetrize_function|fpw|local                         |                        65.65 ms            |                  15              |                       984.80 ms            | 
  │ │   └ sddk::Gvec_shells::remap_backward                             |                        12.84 ms            |                  15              |                       192.59 ms            | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |                         4.41 ms            |                  15              |                        66.19 ms            | 
  │ ├ sirius::Periodic_function::integrate                              |                         4.59 ms            |                  15              |                        68.82 ms            | 
  │ ├ sirius::Density::get_magnetisation                                |                        23.58 ms            |                  15              |                       353.70 ms            | 
  │ │ └ sirius::Density::compute_atomic_mag_mom                         |                        23.57 ms            |                  15              |                       353.59 ms            | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.52 ms →        5.73 ms   (+3.84%) |       2   →       2              |       11.04 ms →       11.46 ms   (+3.84%) | 
  │ ├ sirius::Periodic_function|inner                                   |        5.01 ms                             |       6                          |       30.06 ms                             | 
  │ │ └ sirius::Periodic_function|inner_local                           |        5.01 ms                             |       6                          |       30.04 ms                             | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        5.01 ms                             |       6                          |       30.03 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.77 ms                             |       3                          |       14.32 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.77 ms                             |       3                          |       14.30 ms                             | 
  ├ sirius::Periodic_function|inner                                     |        4.95 ms                             |       2                          |        9.90 ms                             | 
  │ └ sirius::Periodic_function|inner_local                             |        4.95 ms                             |       2                          |        9.90 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.95 ms                             |       2                          |        9.90 ms                             | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.83 ms                             |       1                          |        4.83 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.83 ms                             |       1                          |        4.83 ms                             | 
  ├ sirius::inner                                                       |                         4.88 ms            |                   3              |                        14.64 ms            | 
+ └ sirius::finalize                                                    |      941.62 ms →      198.46 ms  (-78.92%) |       1   →       1              |      941.62 ms →      198.46 ms  (-78.92%) | 
  ====================================================================================================================================================================================================
```
