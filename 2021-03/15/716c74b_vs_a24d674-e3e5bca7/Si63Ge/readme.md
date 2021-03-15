# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs 716c74b9e40f2dc514547b13861ce8c977f50e6c
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |       77.97 s  →       47.24 s   (-39.41%) |       1   →       1              |       77.97 s  →       47.24 s   (-39.41%) | 
  ├ sirius::initialize                                                  |        2.87 s  →        2.87 s    (+0.09%) |       1   →       1              |        2.87 s  →        2.87 s    (+0.09%) | 
+ ├ sirius::Simulation_context::initialize                              |        4.73 s  →        3.60 s   (-23.78%) |       1   →       1              |        4.73 s  →        3.60 s   (-23.78%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       21.37 ms →      560.60 μs  (-97.38%) |       1   →       1              |       21.37 ms →      560.60 μs  (-97.38%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |        1.22 s  →      142.64 ms  (-88.31%) |       1   →       1              |        1.22 s  →      142.64 ms  (-88.31%) | 
+ │ │ ├ sirius::Atom_type::init                                         |      604.91 ms →       61.81 ms  (-89.78%) |       2   →       2              |        1.21 s  →      123.63 ms  (-89.78%) | 
- │ │ └ sirius::Unit_cell::update                                       |       10.15 ms →       18.85 ms  (+85.78%) |       1   →       1              |       10.15 ms →       18.85 ms  (+85.78%) | 
- │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.71 ms →        5.04 ms  (+35.95%) |       1   →       1              |        3.71 ms →        5.04 ms  (+35.95%) | 
- │ │   └ sirius::Unit_cell::get_symmetry                               |        6.36 ms →       13.75 ms (+116.15%) |       1   →       1              |        6.36 ms →       13.75 ms (+116.15%) | 
- │ │     └ sirius::Unit_cell_symmetry                                  |        6.31 ms →       13.68 ms (+116.73%) |       1   →       1              |        6.31 ms →       13.68 ms (+116.73%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.70 ms →        2.70 ms   (+0.15%) |       1   →       1              |        2.70 ms →        2.70 ms   (+0.15%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      501.96 μs →      489.41 μs   (-2.50%) |       1   →       1              |      501.96 μs →      489.41 μs   (-2.50%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       15.98 μs →       16.89 μs   (+5.74%) |       1   →       1              |       15.98 μs →       16.89 μs   (+5.74%) | 
  │ └ sirius::Simulation_context::update                                |        3.44 s  →        3.36 s    (-2.20%) |       1   →       1              |        3.44 s  →        3.36 s    (-2.20%) | 
  │   ├ sirius::Unit_cell::update                                       |        6.78 ms →        7.14 ms   (+5.28%) |       1   →       1              |        6.78 ms →        7.14 ms   (+5.28%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.53 ms →        3.76 ms   (+6.72%) |       1   →       1              |        3.53 ms →        3.76 ms   (+6.72%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.21 ms →        3.33 ms   (+3.77%) |       1   →       1              |        3.21 ms →        3.33 ms   (+3.77%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.17 ms →        3.29 ms   (+3.66%) |       1   →       1              |        3.17 ms →        3.29 ms   (+3.66%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.63 ms →        2.74 ms   (+4.36%) |       1   →       1              |        2.63 ms →        2.74 ms   (+4.36%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      506.47 μs →      506.89 μs   (+0.08%) |       1   →       1              |      506.47 μs →      506.89 μs   (+0.08%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       13.32 μs →       13.94 μs   (+4.63%) |       1   →       1              |       13.32 μs →       13.94 μs   (+4.63%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      214.45 ms →      214.17 ms   (-0.13%) |       2   →       2              |      428.90 ms →      428.34 ms   (-0.13%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.50 ms →       15.19 ms   (-1.98%) |       2   →       2              |       30.99 ms →       30.38 ms   (-1.98%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.25 ms →       13.31 ms   (+0.41%) |       1   →       1              |       13.25 ms →       13.31 ms   (+0.41%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.39 ms →       56.42 ms   (+0.06%) |       2   →       2              |      112.77 ms →      112.84 ms   (+0.06%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       44.89 ms →       45.08 ms   (+0.42%) |       2   →       2              |       89.79 ms →       90.16 ms   (+0.42%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.04 ms →       60.41 ms   (+0.61%) |       4   →       4              |      240.17 ms →      241.64 ms   (+0.61%) | 
  │   ├ sddk::Gvec::init                                                |       94.21 ms →       94.45 ms   (+0.25%) |       2   →       2              |      188.42 ms →      188.89 ms   (+0.25%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       70.45 ms →       70.91 ms   (+0.66%) |       2   →       2              |      140.89 ms →      141.82 ms   (+0.66%) | 
  │   ├ sddk::Gvec_shells                                               |       96.67 ms →       94.99 ms   (-1.74%) |       1   →       1              |       96.67 ms →       94.99 ms   (-1.74%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.69 ms →        1.69 ms   (+0.46%) |       1   →       1              |        1.69 ms →        1.69 ms   (+0.46%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      568.17 ms →      514.87 ms   (-9.38%) |       2   →       2              |        1.14 s  →        1.03 s    (-9.38%) | 
- ├ sirius::K_point_set::create_k_mesh                                  |       86.47 ms →      144.35 ms  (+66.93%) |       1   →       1              |       86.47 ms →      144.35 ms  (+66.93%) | 
- │ ├ sirius::K_point::K_point                                          |        1.31 μs →        6.97 μs (+433.30%) |       4   →       4              |        5.23 μs →       27.89 μs (+433.30%) | 
- │ └ sirius::K_point_set::initialize                                   |       86.41 ms →      144.24 ms  (+66.92%) |       1   →       1              |       86.41 ms →      144.24 ms  (+66.92%) | 
  │   └ sirius::K_point::initialize                                     |       28.08 ms →       28.63 ms   (+1.98%) |       1   →       1              |       28.08 ms →       28.63 ms   (+1.98%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       11.17 ms →       11.47 ms   (+2.62%) |       1   →       1              |       11.17 ms →       11.47 ms   (+2.62%) | 
  │     │ └ sddk::Gvec::init                                            |        5.02 ms →        4.97 ms   (-0.90%) |       1   →       1              |        5.02 ms →        4.97 ms   (-0.90%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |       10.45 μs                             |       1                          |       10.45 μs                             | 
  │     └ sirius::K_point::update                                       |       14.07 ms →       14.28 ms   (+1.51%) |       1   →       1              |       14.07 ms →       14.28 ms   (+1.51%) | 
  │       └ sirius::Beta_projectors                                     |       10.18 ms →       10.22 ms   (+0.37%) |       1   →       1              |       10.18 ms →       10.22 ms   (+0.37%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.25 ms →        8.35 ms   (+1.28%) |       1   →       1              |        8.25 ms →        8.35 ms   (+1.28%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.58 ms                             |       2                          |        5.15 ms                             | 
  ├ sirius::Potential                                                   |       54.85 ms →       49.69 ms   (-9.41%) |       1   →       1              |       54.85 ms →       49.69 ms   (-9.41%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.89 ms                             |       6                          |       17.33 ms                             | 
  │ └ sirius::Potential::update                                         |       37.08 ms →       34.59 ms   (-6.72%) |       1   →       1              |       37.08 ms →       34.59 ms   (-6.72%) | 
  │   └ sirius::Potential::generate_local_potential                     |       36.68 ms →       34.20 ms   (-6.76%) |       1   →       1              |       36.68 ms →       34.20 ms   (-6.76%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       24.91 ms →       26.74 ms   (+7.34%) |       1   →       1              |       24.91 ms →       26.74 ms   (+7.34%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       11.47 ms →        4.41 ms  (-61.56%) |       1   →       1              |       11.47 ms →        4.41 ms  (-61.56%) | 
+ ├ sirius::Density                                                     |       44.26 ms →       36.95 ms  (-16.50%) |       1   →       1              |       44.26 ms →       36.95 ms  (-16.50%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.82 ms                             |       2                          |        5.64 ms                             | 
+ │ └ sirius::Density::update                                           |       38.48 ms →       31.16 ms  (-19.02%) |       1   →       1              |       38.48 ms →       31.16 ms  (-19.02%) | 
+ │   └ sirius::Density::generate_pseudo_core_charge_density            |       38.26 ms →       30.92 ms  (-19.17%) |       1   →       1              |       38.26 ms →       30.92 ms  (-19.17%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       30.72 ms →       27.25 ms  (-11.28%) |       1   →       1              |       30.72 ms →       27.25 ms  (-11.28%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        7.21 ms →        3.01 ms  (-58.33%) |       1   →       1              |        7.21 ms →        3.01 ms  (-58.33%) | 
+ ├ sirius::Density::initial_density                                    |       60.91 ms →       54.47 ms  (-10.59%) |       1   →       1              |       60.91 ms →       54.47 ms  (-10.59%) | 
+ │ ├ sirius::Simulation_context::make_periodic_function                |       30.17 ms →       26.58 ms  (-11.87%) |       1   →       1              |       30.17 ms →       26.58 ms  (-11.87%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.77 ms →        4.77 ms  (-17.26%) |       2   →       2              |       11.54 ms →        9.55 ms  (-17.26%) | 
+ │ └ sirius::Periodic_function::integrate                              |        5.72 ms →        4.94 ms  (-13.69%) |       1   →       1              |        5.72 ms →        4.94 ms  (-13.69%) | 
  ├ sirius::Potential::generate                                         |      380.77 ms →      360.83 ms   (-5.24%) |       1   →       1              |      380.77 ms →      360.83 ms   (-5.24%) | 
+ │ ├ sirius::Potential::poisson                                        |       42.75 ms →       34.74 ms  (-18.73%) |       1   →       1              |       42.75 ms →       34.74 ms  (-18.73%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        7.36 ms →        2.92 ms  (-60.32%) |       1   →       1              |        7.36 ms →        2.92 ms  (-60.32%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        5.90 ms                             |       1                          |        5.90 ms                             | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.63 ms                             |       1                          |        4.63 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.63 ms                             |       1                          |        4.63 ms                             | 
  │ │ └ sirius::inner                                                   |                         5.50 ms            |                   1              |                         5.50 ms            | 
+ │ ├ sirius::Periodic_function::add                                    |      804.89 μs →      718.09 μs  (-10.79%) |       2   →       2              |        1.61 ms →        1.44 ms  (-10.79%) | 
+ │ ├ sirius::Potential::xc                                             |       61.47 ms →       49.30 ms  (-19.80%) |       1   →       1              |       61.47 ms →       49.30 ms  (-19.80%) | 
+ │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       61.47 ms →       48.12 ms  (-21.72%) |       1   →       1              |       61.47 ms →       48.12 ms  (-21.72%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.53 ms                             |       2                          |        5.06 ms                             | 
  │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        4.12 ms                             |       1                          |        4.12 ms                             | 
  │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                    |                        20.06 ms            |                   2              |                        40.11 ms            | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.83 ms →        4.39 ms  (+14.51%) |       1   →       1              |        3.83 ms →        4.39 ms  (+14.51%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      269.75 ms →      267.99 ms   (-0.65%) |       1   →       1              |      269.75 ms →      267.99 ms   (-0.65%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      236.00 ns →      223.00 ns   (-5.51%) |       1   →       1              |      236.00 ns →      223.00 ns   (-5.51%) | 
- ├ sirius::Hamiltonian0                                                |        7.61 ms →       12.69 ms  (+66.70%) |       1   →       1              |        7.61 ms →       12.69 ms  (+66.70%) | 
+ │ ├ sirius::Local_operator                                            |        7.12 ms →        5.88 ms  (-17.31%) |       1   →       1              |        7.12 ms →        5.88 ms  (-17.31%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.74 ms                             |       1                          |        2.74 ms                             | 
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        3.27 ms →        2.36 ms  (-27.73%) |       1   →       1              |        3.27 ms →        2.36 ms  (-27.73%) | 
+ │ ├ sirius::Non_local_operator                                        |      107.44 μs →       68.20 μs  (-36.53%) |       2   →       2              |      214.88 μs →      136.39 μs  (-36.53%) | 
- │ ├ sirius::D_operator::initialize                                    |      117.24 μs →        2.28 ms (+1843.42%) |       1   →       1              |      117.24 μs →        2.28 ms (+1843.42%) | 
- │ └ sirius::Q_operator::initialize                                    |       90.60 μs →        4.32 ms (+4669.97%) |       1   →       1              |       90.60 μs →        4.32 ms (+4669.97%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.29 s  →        1.27 s    (-1.79%) |       1   →       1              |        1.29 s  →        1.27 s    (-1.79%) | 
+ │ ├ sirius::Hamiltonian_k                                             |       56.99 ms →       42.13 ms  (-26.07%) |       1   →       1              |       56.99 ms →       42.13 ms  (-26.07%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      226.47 μs →      217.49 μs   (-3.97%) |       1   →       1              |      226.47 μs →      217.49 μs   (-3.97%) | 
+ │ │ └ sirius::Beta_projectors_base::prepare                           |       56.77 ms →       41.91 ms  (-26.17%) |       1   →       1              |       56.77 ms →       41.91 ms  (-26.17%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.24 s  →        1.23 s    (-0.72%) |       1   →       1              |        1.24 s  →        1.23 s    (-0.72%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       77.24 ms                             |       4                          |      308.97 ms                             | 
+ │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       47.94 ms →       41.08 ms  (-14.30%) |       1   →       1              |       47.94 ms →       41.08 ms  (-14.30%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        7.72 ms →        7.88 ms   (+2.01%) |       1   →       1              |        7.72 ms →        7.88 ms   (+2.01%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      317.00 ms →      336.64 ms   (+6.20%) |       1   →       1              |      317.00 ms →      336.64 ms   (+6.20%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      247.03 ms →      248.06 ms   (+0.42%) |       1   →       1              |      247.03 ms →      248.06 ms   (+0.42%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.85 μs →        3.22 μs  (-16.43%) |       1   →       1              |        3.85 μs →        3.22 μs  (-16.43%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.88 μs                             |       1                          |        2.88 μs                             | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      490.00 ns                             |       1                          |      490.00 ns                             | 
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      666.00 ns →      545.00 ns  (-18.17%) |       1   →       1              |      666.00 ns →      545.00 ns  (-18.17%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.16 ms →        3.14 ms   (-0.54%) |       1   →       1              |        3.16 ms →        3.14 ms   (-0.54%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.27 ms →       21.30 ms   (+0.16%) |       1   →       1              |       21.27 ms →       21.30 ms   (+0.16%) | 
- │ │ │ └ sirius::Non_local_operator::apply                             |       22.74 ms →       32.04 ms  (+40.86%) |       2   →       2              |       45.49 ms →       64.08 ms  (+40.86%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.69 ms →       14.88 ms   (+1.27%) |       2   →       2              |       29.38 ms →       29.75 ms   (+1.27%) | 
  │ │ │ ├ sddk::inner                                                   |       14.48 ms                             |       2                          |       28.96 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       27.97 μs                             |       2                          |       55.94 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        14.65 ms            |                   2              |                        29.31 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        79.50 ns            |                   2              |                       159.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        14.51 ms            |                   2              |                        29.02 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                       306.50 ns            |                   2              |                       613.00 ns            | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      249.77 ms →      230.03 ms   (-7.90%) |       1   →       1              |      249.77 ms →      230.03 ms   (-7.90%) | 
  │ │ ├ sddk::transform                                                 |        2.83 ms                             |       1                          |        2.83 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       15.46 μs                             |       1                          |       15.46 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       18.24 μs                             |       1                          |       18.24 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                         2.62 ms            |                   1              |                         2.62 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                         2.61 ms            |                   1              |                         2.61 ms            | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      383.00 ns →      398.00 ns   (+3.92%) |       1   →       1              |      383.00 ns →      398.00 ns   (+3.92%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |       67.13 s  →       37.72 s   (-43.81%) |       1   →       1              |       67.13 s  →       37.72 s   (-43.81%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.43 ms                             |      19                          |       46.08 ms                             | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.34 s                              |      20                          |       66.89 s                              | 
  │ │ ├ sirius::Hamiltonian0                                            |        5.29 ms                             |      20                          |      105.88 ms                             | 
  │ │ │ ├ sirius::Local_operator                                        |        4.58 ms                             |      20                          |       91.57 ms                             | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      552.55 μs                             |      20                          |       11.05 ms                             | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.04 ms                             |      20                          |       60.78 ms                             | 
  │ │ │ ├ sirius::Non_local_operator                                    |      208.99 μs                             |      40                          |        8.36 ms                             | 
  │ │ │ ├ sirius::D_operator::initialize                                |      123.64 μs                             |      20                          |        2.47 ms                             | 
  │ │ │ └ sirius::Q_operator::initialize                                |       92.90 μs                             |      20                          |        1.86 ms                             | 
  │ │ ├ sirius::Band::solve                                             |        2.11 s                              |      20                          |       42.22 s                              | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      222.51 μs                             |      20                          |        4.45 ms                             | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      214.11 μs                             |      20                          |        4.28 ms                             | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        6.48 μs                             |      20                          |      129.56 μs                             | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.95 s                              |      20                          |       39.03 s                              | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       90.79 ms                             |      20                          |        1.82 s                              | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |       11.47 ms                             |     120                          |        1.38 s                              | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       17.49 ms                             |      20                          |      349.89 ms                             | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      454.58 μs                             |      20                          |        9.09 ms                             | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        8.32 ms                             |      40                          |      332.94 ms                             | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.84 s                              |      20                          |       36.73 s                              | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       55.05 ms                             |     250                          |       13.76 s                              | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       34.49 ms                             |     250                          |        8.62 s                              | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.98 μs                             |     250                          |      495.74 μs                             | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.61 μs                             |     250                          |      402.82 μs                             | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      406.10 ns                             |     250                          |      101.53 μs                             | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      507.24 ns                             |     250                          |      126.81 μs                             | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.74 ms                             |     250                          |      685.04 ms                             | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.43 ms                             |     250                          |      858.59 ms                             | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.19 ms                             |     500                          |        3.59 s                              | 
  │ │ │ │   ├ sddk::orthogonalize                                       |        7.59 ms                             |     250                          |        1.90 s                              | 
  │ │ │ │   │ ├ sddk::inner                                             |      964.67 μs                             |     480                          |      463.04 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       21.13 μs                             |     480                          |       10.14 ms                             | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      302.51 μs                             |     250                          |       75.63 ms                             | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        2.74 ms                             |     250                          |      685.01 ms                             | 
  │ │ │ │   │ └ sddk::transform                                         |        2.92 ms                             |     230                          |      671.74 ms                             | 
  │ │ │ │   │   ├ sddk::transform|init                                  |       17.55 μs                             |     230                          |        4.04 ms                             | 
  │ │ │ │   │   └ sddk::transform|local                                 |        7.22 μs                             |     690                          |        4.98 ms                             | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.99 ms                             |     250                          |      497.34 ms                             | 
  │ │ │ │   │ └ sddk::inner                                             |        1.79 ms                             |     250                          |      447.67 ms                             | 
  │ │ │ │   │   └ sddk::inner|local                                     |       22.36 μs                             |     250                          |        5.59 ms                             | 
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       79.19 ms                             |     250                          |       19.80 s                              | 
  │ │ │ │   ├ sirius::residuals                                         |        2.50 ms                             |     245                          |      613.28 ms                             | 
  │ │ │ │   │ ├ sddk::transform                                         |        1.81 ms                             |     231                          |      417.99 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       15.09 μs                             |     231                          |        3.49 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |        9.97 μs                             |     462                          |        4.61 ms                             | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      769.98 μs                             |     231                          |      177.86 ms                             | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        6.23 ms                             |      25                          |      155.72 ms                             | 
  │ │ │ │     └ sddk::transform                                         |        5.11 ms                             |      30                          |      153.26 ms                             | 
  │ │ │ │       ├ sddk::transform|init                                  |       10.89 μs                             |      30                          |      326.81 μs                             | 
  │ │ │ │       └ sddk::transform|local                                 |       11.16 μs                             |      35                          |      390.65 μs                             | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      449.15 ns                             |      20                          |        8.98 μs                             | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       22.61 μs                             |      20                          |      452.19 μs                             | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.49 ms                             |      20                          |       29.88 ms                             | 
  │ │ ├ sirius::Density::generate                                       |      566.47 ms                             |      20                          |       11.33 s                              | 
  │ │ │ ├ sirius::Density::generate_valence                             |      426.21 ms                             |      20                          |        8.52 s                              | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.20 μs                             |      20                          |      164.03 μs                             | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.54 μs                             |      20                          |      150.90 μs                             | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       26.27 ms                             |      20                          |      525.48 ms                             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.72 μs                             |      20                          |      154.43 μs                             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        4.62 ms                             |      20                          |       92.34 ms                             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       20.61 ms                             |      20                          |      412.16 ms                             | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      858.85 ns                             |      20                          |       17.18 μs                             | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      119.43 ms                             |      20                          |        2.39 s                              | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.23 ms                             |      20                          |       44.67 ms                             | 
  │ │ │ │ └ sirius::Density::augment                                    |      247.52 ms                             |      20                          |        4.95 s                              | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |      247.31 ms                             |      20                          |        4.95 s                              | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      112.41 ms                             |      20                          |        2.25 s                              | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      112.40 ms                             |      20                          |        2.25 s                              | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       28.92 ms                             |      20                          |      578.45 ms                             | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       70.18 ms                             |      20                          |        1.40 s                              | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.66 ms                             |      20                          |      253.20 ms                             | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.58 ms                             |      20                          |      471.64 ms                             | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        4.28 ms                             |      20                          |       85.50 ms                             | 
  │ │ ├ sirius::Density::mix                                            |      135.35 ms                             |      20                          |        2.71 s                              | 
  │ │ │ ├ sirius::Density::mixer_input                                  |        1.09 ms                             |      20                          |       21.87 ms                             | 
  │ │ │ ├ sirius::Periodic_function|inner                               |        4.89 ms                             |     244                          |        1.19 s                              | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.82 ms                             |     244                          |        1.18 s                              | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.82 ms                             |     244                          |        1.18 s                              | 
  │ │ │ └ sirius::Density::mixer_output                                 |        4.86 ms                             |      20                          |       97.27 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        4.20 ms                             |      20                          |       84.05 ms                             | 
  │ │ ├ sirius::Potential::generate                                     |      372.82 ms                             |      20                          |        7.46 s                              | 
  │ │ │ ├ sirius::Potential::poisson                                    |       42.41 ms                             |      20                          |      848.24 ms                             | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        7.06 ms                             |      20                          |      141.25 ms                             | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |        5.88 ms                             |      20                          |      117.68 ms                             | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.63 ms                             |      20                          |       92.64 ms                             | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.63 ms                             |      20                          |       92.62 ms                             | 
  │ │ │ ├ sirius::Periodic_function::add                                |      794.12 μs                             |      40                          |       31.76 ms                             | 
  │ │ │ ├ sirius::Potential::xc                                         |       54.86 ms                             |      20                          |        1.10 s                              | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       54.86 ms                             |      20                          |        1.10 s                              | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |      638.65 μs                             |      40                          |       25.55 ms                             | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        3.98 ms                             |      20                          |       79.51 ms                             | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.86 ms                             |      20                          |       77.26 ms                             | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.69 ms                             |      20                          |        5.37 s                              | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      204.00 ns                             |      20                          |        4.08 μs                             | 
  │ │ ├ sirius::Field4D::symmetrize                                     |       95.89 ms                             |      20                          |        1.92 s                              | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |       95.89 ms                             |      20                          |        1.92 s                              | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.28 ms                             |      20                          |      265.62 ms                             | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       69.36 ms                             |      20                          |        1.39 s                              | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.61 ms                             |      20                          |      252.27 ms                             | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.83 ms                             |      20                          |       76.64 ms                             | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.76 ms                             |     140                          |      665.93 ms                             | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.65 ms                             |     140                          |      650.87 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.65 ms                             |     140                          |      650.76 ms                             | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.76 ms                             |      60                          |      285.58 ms                             | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.75 ms                             |      60                          |      284.86 ms                             | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.55 ms                             |      20                          |       90.96 ms                             | 
  │ │ └ sirius::Density::get_magnetisation                              |       77.95 μs                             |      20                          |        1.56 ms                             | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |       72.05 μs                             |      20                          |        1.44 ms                             | 
  │ ├ sirius::Density                                                   |                        47.63 ms            |                   1              |                        47.63 ms            | 
  │ │ └ sirius::Density::update                                         |                        41.84 ms            |                   1              |                        41.84 ms            | 
  │ │   └ sirius::Density::generate_pseudo_core_charge_density          |                        41.50 ms            |                   1              |                        41.50 ms            | 
  │ │     ├ sirius::Simulation_context::make_periodic_function          |                        27.05 ms            |                   1              |                        27.05 ms            | 
  │ │     └ sirius::Smooth_periodic_function::fft_transform             |                         3.01 ms            |                   1              |                         3.01 ms            | 
  │ ├ sirius::Hamiltonian0                                              |                        11.07 ms            |                  15              |                       166.07 ms            | 
  │ │ ├ sirius::Local_operator                                          |                         4.22 ms            |                  15              |                        63.33 ms            | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |                         2.44 ms            |                  15              |                        36.64 ms            | 
  │ │ ├ sirius::Non_local_operator                                      |                       150.49 μs            |                  30              |                         4.51 ms            | 
  │ │ ├ sirius::D_operator::initialize                                  |                         2.21 ms            |                  15              |                        33.12 ms            | 
  │ │ └ sirius::Q_operator::initialize                                  |                         4.27 ms            |                  15              |                        64.08 ms            | 
  │ ├ sirius::Band::solve                                               |                         1.30 s             |                  15              |                        19.46 s             | 
  │ │ ├ sirius::Hamiltonian_k                                           |                       195.90 μs            |                  15              |                         2.94 ms            | 
  │ │ │ ├ sirius::Local_operator::prepare_k                             |                       184.99 μs            |                  15              |                         2.77 ms            | 
  │ │ │ └ sirius::Beta_projectors_base::prepare                         |                         6.05 μs            |                  15              |                        90.75 μs            | 
  │ │ ├ sirius::Band::diag_pseudo_potential_davidson                    |                         1.13 s             |                  15              |                        16.94 s             | 
  │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                           |                        18.69 ms            |                  15              |                       280.37 ms            | 
  │ │ │ ├ sirius::Hamiltonian_k::apply_h_s                              |                        85.06 ms            |                 116              |                         9.87 s             | 
  │ │ │ │ ├ sirius::Local_operator::apply_h                             |                        49.67 ms            |                 116              |                         5.76 s             | 
  │ │ │ │ │ ├ sddk::matrix_storage::remap_forward                       |                         1.66 μs            |                 116              |                       192.54 μs            | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_backward                      |                       506.87 ns            |                 116              |                        58.80 μs            | 
  │ │ │ │ ├ sirius::Beta_projectors_base::generate                      |                         3.48 ms            |                 116              |                       403.58 ms            | 
  │ │ │ │ ├ sirius::Beta_projectors_base::inner                         |                         4.54 ms            |                 116              |                       526.70 ms            | 
  │ │ │ │ └ sirius::Non_local_operator::apply                           |                        13.67 ms            |                 232              |                         3.17 s             | 
  │ │ │ ├ sddk::orthogonalize                                           |                        11.10 ms            |                 116              |                         1.29 s             | 
  │ │ │ │ ├ sddk::wf_inner                                              |                         1.49 ms            |                 217              |                       322.71 ms            | 
  │ │ │ │ │ ├ sddk::wf_inner|scale                                      |                        89.54 ns            |                 217              |                        19.43 μs            | 
  │ │ │ │ │ ├ sddk::wf_inner|pw                                         |                         1.32 ms            |                 217              |                       287.12 ms            | 
  │ │ │ │ │ └ sddk::wf_inner|scale_back                                 |                       242.31 ns            |                 217              |                        52.58 μs            | 
  │ │ │ │ ├ sddk::orthogonalize|tmtrx                                   |                       480.42 μs            |                 116              |                        55.73 ms            | 
  │ │ │ │ ├ sddk::orthogonalize|transform                               |                         4.63 ms            |                 116              |                       536.85 ms            | 
  │ │ │ │ └ sddk::wf_trans                                              |                         3.68 ms            |                 101              |                       371.80 ms            | 
  │ │ │ │   └ sddk::wf_trans|pw                                         |                         1.23 ms            |                 303              |                       371.58 ms            | 
  │ │ │ ├ sirius::Band::set_subspace_mtrx                               |                         2.35 ms            |                 116              |                       272.45 ms            | 
  │ │ │ │ └ sddk::wf_inner                                              |                         2.28 ms            |                 116              |                       264.93 ms            | 
  │ │ │ │   ├ sddk::wf_inner|scale                                      |                       101.53 ns            |                 116              |                        11.78 μs            | 
  │ │ │ │   ├ sddk::wf_inner|pw                                         |                         2.12 ms            |                 116              |                       245.76 ms            | 
  │ │ │ │   └ sddk::wf_inner|scale_back                                 |                       204.71 ns            |                 116              |                        23.75 μs            | 
  │ │ │ ├ Eigensolver_cuda|zheevdx                                      |                        27.02 ms            |                 116              |                         3.13 s             | 
  │ │ │ ├ sirius::residuals                                             |                         3.13 ms            |                 114              |                       356.69 ms            | 
  │ │ │ │ ├ sddk::wf_trans                                              |                         1.59 ms            |                 101              |                       160.85 ms            | 
  │ │ │ │ │ └ sddk::wf_trans|pw                                         |                       794.92 μs            |                 202              |                       160.57 ms            | 
  │ │ │ │ └ sirius::normalized_preconditioned_residuals                 |                         1.73 ms            |                 101              |                       174.98 ms            | 
  │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|update_phi       |                         4.86 ms            |                  47              |                       228.25 ms            | 
  │ │ │   └ sddk::wf_trans                                              |                         2.84 ms            |                  79              |                       224.41 ms            | 
  │ │ │     └ sddk::wf_trans|pw                                         |                         2.02 ms            |                 111              |                       224.26 ms            | 
  │ │ ├ sirius::Beta_projectors_base::dismiss                           |                       385.60 ns            |                  15              |                         5.78 μs            | 
  │ │ └ sirius::K_point_set::sync_band                                  |                        62.17 μs            |                  15              |                       932.58 μs            | 
  │ ├ sirius::K_point_set::find_band_occupancies                        |                       993.92 μs            |                  15              |                        14.91 ms            | 
  │ │ └ sirius::K_point_set::sync_band                                  |                        14.21 μs            |                  15              |                       213.18 μs            | 
  │ ├ sirius::Density::generate                                         |                       566.49 ms            |                  15              |                         8.50 s             | 
  │ │ ├ sirius::Density::generate_valence                               |                       410.90 ms            |                  15              |                         6.16 s             | 
  │ │ │ ├ sddk::matrix_storage::remap_forward                           |                         5.27 μs            |                  15              |                        79.07 μs            | 
  │ │ │ ├ sirius::Density::add_k_point_contribution_dm                  |                        30.19 ms            |                  15              |                       452.87 ms            | 
  │ │ │ │ ├ sirius::Beta_projectors_base::prepare                       |                         8.99 μs            |                  15              |                       134.90 μs            | 
  │ │ │ │ ├ sirius::Beta_projectors_base::generate                      |                         4.43 ms            |                  15              |                        66.45 ms            | 
  │ │ │ │ ├ sirius::Beta_projectors_base::inner                         |                        24.70 ms            |                  15              |                       370.50 ms            | 
  │ │ │ │ └ sirius::Beta_projectors_base::dismiss                       |                       472.67 ns            |                  15              |                         7.09 μs            | 
  │ │ │ ├ sirius::Density::add_k_point_contribution_rg                  |                       115.50 ms            |                  15              |                         1.73 s             | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |                         1.92 ms            |                  15              |                        28.79 ms            | 
  │ │ │ └ sirius::Density::augment                                      |                       231.38 ms            |                  15              |                         3.47 s             | 
  │ │ │   └ sirius::Density::generate_rho_aug                           |                       231.16 ms            |                  15              |                         3.47 s             | 
  │ │ ├ sirius::Field4D::symmetrize                                     |                       128.33 ms            |                  15              |                         1.92 s             | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |                       128.32 ms            |                  15              |                         1.92 s             | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |                        49.50 ms            |                  15              |                       742.56 ms            | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |                        65.23 ms            |                  15              |                       978.38 ms            | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |                        12.94 ms            |                  15              |                       194.15 ms            | 
  │ │ ├ sirius::Density::symmetrize_density_matrix                      |                        23.52 ms            |                  15              |                       352.73 ms            | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |                         3.73 ms            |                  15              |                        55.98 ms            | 
  │ ├ sirius::inner                                                     |                         4.79 ms            |                 189              |                       904.59 ms            | 
  │ ├ sirius::Density::mix                                              |                        77.48 ms            |                  15              |                         1.16 s             | 
  │ │ ├ sirius::Density::mixer_input                                    |                         1.02 ms            |                  15              |                        15.35 ms            | 
  │ │ ├ sirius::inner                                                   |                         4.79 ms            |                 169              |                       808.95 ms            | 
  │ │ └ sirius::Density::mixer_output                                   |                         5.38 ms            |                  15              |                        80.70 ms            | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |                         4.39 ms            |                  15              |                        65.79 ms            | 
  │ ├ sirius::Potential::generate                                       |                       358.59 ms            |                  15              |                         5.38 s             | 
  │ │ ├ sirius::Potential::poisson                                      |                        35.19 ms            |                  15              |                       527.86 ms            | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |                         3.59 ms            |                  15              |                        53.90 ms            | 
  │ │ │ └ sirius::inner                                                 |                         5.17 ms            |                  15              |                        77.54 ms            | 
  │ │ ├ sirius::Periodic_function::add                                  |                       714.67 μs            |                  30              |                        21.44 ms            | 
  │ │ ├ sirius::Potential::xc                                           |                        47.21 ms            |                  15              |                       708.20 ms            | 
  │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                          |                        46.02 ms            |                  15              |                       690.24 ms            | 
  │ │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                  |                        19.57 ms            |                  30              |                       587.11 ms            | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |                         3.73 ms            |                  15              |                        55.95 ms            | 
  │ │ ├ sirius::Potential::generate_D_operator_matrix                   |                       268.04 ms            |                  15              |                         4.02 s             | 
  │ │ └ sirius::Potential::generate_PAW_effective_potential             |                       154.60 ns            |                  15              |                         2.32 μs            | 
  │ ├ sirius::Field4D::symmetrize                                       |                        91.87 ms            |                  15              |                         1.38 s             | 
  │ │ └ sirius::symmetrize_function|fpw                                 |                        91.86 ms            |                  15              |                         1.38 s             | 
  │ │   ├ sddk::Gvec_shells::remap_forward                              |                        13.37 ms            |                  15              |                       200.54 ms            | 
  │ │   ├ sirius::symmetrize_function|fpw|local                         |                        64.94 ms            |                  15              |                       974.12 ms            | 
  │ │   └ sddk::Gvec_shells::remap_backward                             |                        12.91 ms            |                  15              |                       193.64 ms            | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |                         3.44 ms            |                  15              |                        51.64 ms            | 
  │ ├ sirius::Periodic_function::integrate                              |                         4.57 ms            |                  15              |                        68.59 ms            | 
  │ ├ sirius::Density::get_magnetisation                                |                        23.33 ms            |                  15              |                       349.95 ms            | 
  │ │ └ sirius::Density::compute_atomic_mag_mom                         |                        23.32 ms            |                  15              |                       349.85 ms            | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.18 ms →        5.24 ms   (+1.09%) |       2   →       2              |       10.36 ms →       10.47 ms   (+1.09%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.58 ms                             |       6                          |       27.49 ms                             | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.53 ms                             |       6                          |       27.21 ms                             | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.53 ms                             |       6                          |       27.20 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.91 ms                             |       3                          |       14.73 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.91 ms                             |       3                          |       14.72 ms                             | 
  ├ sirius::Periodic_function|inner                                     |        4.77 ms                             |       2                          |        9.54 ms                             | 
  │ └ sirius::Periodic_function|inner_local                             |        4.76 ms                             |       2                          |        9.53 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.76 ms                             |       2                          |        9.53 ms                             | 
  ├ sirius::Smooth_periodic_function|inner                              |        5.12 ms                             |       1                          |        5.12 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.94 ms                             |       1                          |        4.94 ms                             | 
  ├ sirius::inner                                                       |                         4.61 ms            |                   3              |                        13.82 ms            | 
+ └ sirius::finalize                                                    |      929.99 ms →      763.95 ms  (-17.85%) |       1   →       1              |      929.99 ms →      763.95 ms  (-17.85%) | 
  ====================================================================================================================================================================================================
```
