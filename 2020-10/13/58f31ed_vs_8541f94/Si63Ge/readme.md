# Benchmark 8541f94e2e0e288633941ac63ad4d565828afb1d vs 58f31ed08f2b4e9e6d289f9ed116027f00413e03
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |       92.39 s  →       71.49 s   (-22.62%) |       1   →       1              |       92.39 s  →       71.49 s   (-22.62%) | 
  ├ sirius::initialize                                                  |        2.89 s  →        2.97 s    (+2.71%) |       1   →       1              |        2.89 s  →        2.97 s    (+2.71%) | 
  ├ sirius::Simulation_context::initialize                              |        3.88 s  →        3.67 s    (-5.54%) |       1   →       1              |        3.88 s  →        3.67 s    (-5.54%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       50.30 ms →      246.22 μs  (-99.51%) |       1   →       1              |       50.30 ms →      246.22 μs  (-99.51%) | 
  │ ├ sirius::Unit_cell::initialize                                     |      129.04 ms →      117.04 ms   (-9.30%) |       1   →       1              |      129.04 ms →      117.04 ms   (-9.30%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       56.13 ms →       49.17 ms  (-12.41%) |       2   →       2              |      112.26 ms →       98.33 ms  (-12.41%) | 
- │ │ └ sirius::Unit_cell::update                                       |       16.69 ms →       18.62 ms  (+11.54%) |       1   →       1              |       16.69 ms →       18.62 ms  (+11.54%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.98 ms →        3.82 ms   (-4.09%) |       1   →       1              |        3.98 ms →        3.82 ms   (-4.09%) | 
- │ │   └ sirius::Unit_cell::get_symmetry                               |       12.64 ms →       14.73 ms  (+16.56%) |       1   →       1              |       12.64 ms →       14.73 ms  (+16.56%) | 
- │ │     └ sirius::Unit_cell_symmetry                                  |       12.56 ms →       14.67 ms  (+16.74%) |       1   →       1              |       12.56 ms →       14.67 ms  (+16.74%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.76 ms →        2.74 ms   (-0.77%) |       1   →       1              |        2.76 ms →        2.74 ms   (-0.77%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      493.45 μs →      502.33 μs   (+1.80%) |       1   →       1              |      493.45 μs →      502.33 μs   (+1.80%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       15.39 μs →       15.45 μs   (+0.36%) |       1   →       1              |       15.39 μs →       15.45 μs   (+0.36%) | 
  │ └ sirius::Simulation_context::update                                |        3.66 s  →        3.50 s    (-4.29%) |       1   →       1              |        3.66 s  →        3.50 s    (-4.29%) | 
  │   ├ sirius::Unit_cell::update                                       |        7.14 ms →        6.85 ms   (-3.98%) |       1   →       1              |        7.14 ms →        6.85 ms   (-3.98%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.78 ms →        3.48 ms   (-7.96%) |       1   →       1              |        3.78 ms →        3.48 ms   (-7.96%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.32 ms →        3.31 ms   (-0.18%) |       1   →       1              |        3.32 ms →        3.31 ms   (-0.18%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.27 ms →        3.26 ms   (-0.36%) |       1   →       1              |        3.27 ms →        3.26 ms   (-0.36%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.71 ms →        2.71 ms   (-0.14%) |       1   →       1              |        2.71 ms →        2.71 ms   (-0.14%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      515.69 μs →      509.31 μs   (-1.24%) |       1   →       1              |      515.69 μs →      509.31 μs   (-1.24%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       15.26 μs →       15.01 μs   (-1.62%) |       1   →       1              |       15.26 μs →       15.01 μs   (-1.62%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      213.21 ms →      212.72 ms   (-0.23%) |       2   →       2              |      426.41 ms →      425.45 ms   (-0.23%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       16.18 ms →       15.29 ms   (-5.55%) |       2   →       2              |       32.37 ms →       30.57 ms   (-5.55%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.25 ms →       13.24 ms   (-0.08%) |       1   →       1              |       13.25 ms →       13.24 ms   (-0.08%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.56 ms →       56.34 ms   (-0.40%) |       2   →       2              |      113.13 ms →      112.67 ms   (-0.40%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.12 ms →       45.08 ms   (-0.08%) |       2   →       2              |       90.24 ms →       90.17 ms   (-0.08%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.36 ms →       60.11 ms   (-0.42%) |       4   →       4              |      241.44 ms →      240.42 ms   (-0.42%) | 
  │   ├ sddk::Gvec::init                                                |       95.56 ms →       93.57 ms   (-2.08%) |       2   →       2              |      191.11 ms →      187.15 ms   (-2.08%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       70.60 ms →       70.03 ms   (-0.81%) |       2   →       2              |      141.20 ms →      140.06 ms   (-0.81%) | 
+ │   ├ sddk::Gvec_shells                                               |      107.62 ms →       94.66 ms  (-12.04%) |       1   →       1              |      107.62 ms →       94.66 ms  (-12.04%) | 
- │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.69 ms →        1.95 ms  (+15.64%) |       1   →       1              |        1.69 ms →        1.95 ms  (+15.64%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      656.00 ms →      601.49 ms   (-8.31%) |       2   →       2              |        1.31 s  →        1.20 s    (-8.31%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       92.94 ms →       88.90 ms   (-4.35%) |       1   →       1              |       92.94 ms →       88.90 ms   (-4.35%) | 
  │ ├ sirius::K_point::K_point                                          |        1.45 μs →        1.53 μs   (+6.09%) |       4   →       4              |        5.78 μs →        6.13 μs   (+6.09%) | 
  │ └ sirius::K_point_set::initialize                                   |       92.88 ms →       88.82 ms   (-4.37%) |       1   →       1              |       92.88 ms →       88.82 ms   (-4.37%) | 
  │   └ sirius::K_point::initialize                                     |       29.19 ms →       27.51 ms   (-5.75%) |       1   →       1              |       29.19 ms →       27.51 ms   (-5.75%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       11.92 ms →       10.94 ms   (-8.22%) |       1   →       1              |       11.92 ms →       10.94 ms   (-8.22%) | 
  │     │ └ sddk::Gvec::init                                            |        5.15 ms →        4.92 ms   (-4.55%) |       1   →       1              |        5.15 ms →        4.92 ms   (-4.55%) | 
- │     ├ sddk::matrix_storage::matrix_storage                          |        6.32 μs →       10.49 μs  (+65.87%) |       1   →       1              |        6.32 μs →       10.49 μs  (+65.87%) | 
  │     └ sirius::K_point::update                                       |       14.06 ms →       13.75 ms   (-2.21%) |       1   →       1              |       14.06 ms →       13.75 ms   (-2.21%) | 
  │       └ sirius::Beta_projectors                                     |        9.96 ms →        9.98 ms   (+0.22%) |       1   →       1              |        9.96 ms →        9.98 ms   (+0.22%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.22 ms →        8.19 ms   (-0.33%) |       1   →       1              |        8.22 ms →        8.19 ms   (-0.33%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.53 ms →        2.59 ms   (+2.62%) |       2   →       2              |        5.05 ms →        5.19 ms   (+2.62%) | 
  ├ sirius::Potential                                                   |       49.57 ms →       52.33 ms   (+5.57%) |       1   →       1              |       49.57 ms →       52.33 ms   (+5.57%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.89 ms →        2.91 ms   (+0.57%) |       6   →       6              |       17.35 ms →       17.44 ms   (+0.57%) | 
  │ └ sirius::Potential::update                                         |       31.62 ms →       34.27 ms   (+8.38%) |       1   →       1              |       31.62 ms →       34.27 ms   (+8.38%) | 
  │   └ sirius::Potential::generate_local_potential                     |       31.24 ms →       33.87 ms   (+8.43%) |       1   →       1              |       31.24 ms →       33.87 ms   (+8.43%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       26.67 ms →       29.11 ms   (+9.16%) |       1   →       1              |       26.67 ms →       29.11 ms   (+9.16%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        4.22 ms →        4.17 ms   (-1.31%) |       1   →       1              |        4.22 ms →        4.17 ms   (-1.31%) | 
  ├ sirius::Density                                                     |       43.41 ms →       41.35 ms   (-4.76%) |       1   →       1              |       43.41 ms →       41.35 ms   (-4.76%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.82 ms →        2.83 ms   (+0.12%) |       2   →       2              |        5.64 ms →        5.65 ms   (+0.12%) | 
  │ └ sirius::Density::update                                           |       37.63 ms →       35.56 ms   (-5.51%) |       1   →       1              |       37.63 ms →       35.56 ms   (-5.51%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       37.31 ms →       35.32 ms   (-5.34%) |       1   →       1              |       37.31 ms →       35.32 ms   (-5.34%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |                        78.94 μs            |                   1              |                        78.94 μs            | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       33.64 ms →       29.66 ms  (-11.81%) |       1   →       1              |       33.64 ms →       29.66 ms  (-11.81%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        3.34 ms →        5.25 ms  (+57.34%) |       1   →       1              |        3.34 ms →        5.25 ms  (+57.34%) | 
  ├ sirius::Density::initial_density                                    |       61.56 ms →       61.26 ms   (-0.49%) |       1   →       1              |       61.56 ms →       61.26 ms   (-0.49%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       33.20 ms →       32.92 ms   (-0.86%) |       1   →       1              |       33.20 ms →       32.92 ms   (-0.86%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.65 ms →        4.91 ms   (+5.59%) |       2   →       2              |        9.29 ms →        9.81 ms   (+5.59%) | 
  │ └ sirius::Periodic_function::integrate                              |        5.30 ms →        4.86 ms   (-8.29%) |       1   →       1              |        5.30 ms →        4.86 ms   (-8.29%) | 
  ├ sirius::Potential::generate                                         |      365.98 ms →      369.09 ms   (+0.85%) |       1   →       1              |      365.98 ms →      369.09 ms   (+0.85%) | 
  │ ├ sirius::Potential::poisson                                        |       40.62 ms →       42.38 ms   (+4.35%) |       1   →       1              |       40.62 ms →       42.38 ms   (+4.35%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.28 ms →        5.62 ms  (+71.37%) |       1   →       1              |        3.28 ms →        5.62 ms  (+71.37%) | 
- │ │ └ sirius::Periodic_function|inner                                 |        5.09 ms →        5.74 ms  (+12.76%) |       1   →       1              |        5.09 ms →        5.74 ms  (+12.76%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.85 ms →        4.65 ms   (-4.23%) |       1   →       1              |        4.85 ms →        4.65 ms   (-4.23%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.85 ms →        4.64 ms   (-4.38%) |       1   →       1              |        4.85 ms →        4.64 ms   (-4.38%) | 
  │ ├ sirius::Periodic_function::add                                    |      778.48 μs →      814.73 μs   (+4.66%) |       2   →       2              |        1.56 ms →        1.63 ms   (+4.66%) | 
  │ ├ sirius::Potential::xc                                             |       50.16 ms →       51.43 ms   (+2.53%) |       1   →       1              |       50.16 ms →       51.43 ms   (+2.53%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       50.16 ms →       50.25 ms   (+0.19%) |       1   →       1              |       50.16 ms →       50.25 ms   (+0.19%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.54 ms →        2.54 ms   (-0.02%) |       2   →       2              |        5.07 ms →        5.07 ms   (-0.02%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.58 ms →        4.57 ms   (-0.17%) |       1   →       1              |        4.58 ms →        4.57 ms   (-0.17%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        2.87 ms →        3.66 ms  (+27.83%) |       1   →       1              |        2.87 ms →        3.66 ms  (+27.83%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      269.37 ms →      268.62 ms   (-0.28%) |       1   →       1              |      269.37 ms →      268.62 ms   (-0.28%) | 
- │ └ sirius::Potential::generate_PAW_effective_potential               |      238.00 ns →      320.00 ns  (+34.45%) |       1   →       1              |      238.00 ns →      320.00 ns  (+34.45%) | 
+ ├ sirius::Hamiltonian0                                                |        7.61 ms →        6.40 ms  (-15.89%) |       1   →       1              |        7.61 ms →        6.40 ms  (-15.89%) | 
+ │ ├ sirius::Local_operator                                            |        7.08 ms →        5.88 ms  (-16.97%) |       1   →       1              |        7.08 ms →        5.88 ms  (-16.97%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.73 ms →        2.75 ms   (+0.58%) |       1   →       1              |        2.73 ms →        2.75 ms   (+0.58%) | 
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        3.29 ms →        2.37 ms  (-28.04%) |       1   →       1              |        3.29 ms →        2.37 ms  (-28.04%) | 
+ │ ├ sirius::Non_local_operator                                        |      125.36 μs →       85.57 μs  (-31.74%) |       2   →       2              |      250.72 μs →      171.14 μs  (-31.74%) | 
- │ ├ sirius::D_operator::initialize                                    |      112.57 μs →      142.05 μs  (+26.20%) |       1   →       1              |      112.57 μs →      142.05 μs  (+26.20%) | 
- │ └ sirius::Q_operator::initialize                                    |       93.25 μs →      115.06 μs  (+23.39%) |       1   →       1              |       93.25 μs →      115.06 μs  (+23.39%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.28 s  →        1.29 s    (+0.80%) |       1   →       1              |        1.28 s  →        1.29 s    (+0.80%) | 
+ │ ├ sirius::Hamiltonian_k                                             |       68.58 ms →       37.18 ms  (-45.79%) |       1   →       1              |       68.58 ms →       37.18 ms  (-45.79%) | 
+ │ │ ├ sirius::Local_operator::prepare_k                               |      308.66 μs →      276.11 μs  (-10.55%) |       1   →       1              |      308.66 μs →      276.11 μs  (-10.55%) | 
+ │ │ └ sirius::Beta_projectors_base::prepare                           |       68.26 ms →       36.89 ms  (-45.96%) |       1   →       1              |       68.26 ms →       36.89 ms  (-45.96%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.21 s  →        1.25 s    (+3.44%) |       1   →       1              |        1.21 s  →        1.25 s    (+3.44%) | 
+ │ │ ├ sddk::matrix_storage::matrix_storage                            |      103.54 ms →       82.55 ms  (-20.27%) |       4   →       4              |      414.16 ms →      330.19 ms  (-20.27%) | 
- │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       38.58 ms →       50.68 ms  (+31.38%) |       1   →       1              |       38.58 ms →       50.68 ms  (+31.38%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        6.77 ms →        6.71 ms   (-0.99%) |       1   →       1              |        6.77 ms →        6.71 ms   (-0.99%) | 
+ │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      450.71 ms →      314.64 ms  (-30.19%) |       1   →       1              |      450.71 ms →      314.64 ms  (-30.19%) | 
+ │ │ │ ├ sirius::Local_operator::apply_h                               |      383.88 ms →      245.82 ms  (-35.96%) |       1   →       1              |      383.88 ms →      245.82 ms  (-35.96%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        4.05 μs →        3.76 μs   (-7.02%) |       1   →       1              |        4.05 μs →        3.76 μs   (-7.02%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.06 μs →        2.87 μs   (-6.40%) |       1   →       1              |        3.06 μs →        2.87 μs   (-6.40%) | 
- │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      460.00 ns →      793.00 ns  (+72.39%) |       1   →       1              |      460.00 ns →      793.00 ns  (+72.39%) | 
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                        |        1.16 μs →      547.00 ns  (-52.72%) |       1   →       1              |        1.16 μs →      547.00 ns  (-52.72%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        2.99 ms →        3.11 ms   (+4.07%) |       1   →       1              |        2.99 ms →        3.11 ms   (+4.07%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.22 ms →       21.32 ms   (+0.46%) |       1   →       1              |       21.22 ms →       21.32 ms   (+0.46%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       21.29 ms →       22.18 ms   (+4.17%) |       2   →       2              |       42.58 ms →       44.35 ms   (+4.17%) | 
- │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.66 ms →       16.56 ms  (+12.98%) |       2   →       2              |       29.31 ms →       33.12 ms  (+12.98%) | 
  │ │ │ ├ sddk::inner                                                   |       14.44 ms                             |       2                          |       28.89 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       25.33 μs                             |       2                          |       50.67 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        16.34 ms            |                   2              |                        32.68 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        22.50 ns            |                   2              |                        45.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        16.22 ms            |                   2              |                        32.44 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                        28.50 ns            |                   2              |                        57.00 ns            | 
- │ │ ├ Eigensolver_cuda|zhegvdx                                        |      111.48 ms →      249.78 ms (+124.05%) |       1   →       1              |      111.48 ms →      249.78 ms (+124.05%) | 
  │ │ ├ sddk::transform                                                 |        2.80 ms                             |       1                          |        2.80 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       13.30 μs                             |       1                          |       13.30 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       16.27 μs                             |       1                          |       16.27 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                         2.61 ms            |                   1              |                         2.61 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                         2.61 ms            |                   1              |                         2.61 ms            | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      367.00 ns →      503.00 ns  (+37.06%) |       1   →       1              |      367.00 ns →      503.00 ns  (+37.06%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |       82.61 s  →       61.83 s   (-25.15%) |       1   →       1              |       82.61 s  →       61.83 s   (-25.15%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.43 ms →        2.45 ms   (+1.17%) |      19   →      19              |       46.09 ms →       46.63 ms   (+1.17%) | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.85 s  →        3.24 s   (-33.10%) |      17   →      19    (+11.76%) |       82.43 s  →       61.63 s   (-25.23%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        4.64 ms →        5.44 ms  (+17.30%) |      17   →      19    (+11.76%) |       78.87 ms →      103.40 ms  (+31.10%) | 
- │ │ │ ├ sirius::Local_operator                                        |        4.06 ms →        4.88 ms  (+20.32%) |      17   →      19    (+11.76%) |       68.97 ms →       92.75 ms  (+34.48%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function                            |      562.86 μs →      563.20 μs   (+0.06%) |      17   →      19    (+11.76%) |        9.57 ms →       10.70 ms  (+11.83%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.30 ms →        3.07 ms  (+33.49%) |      17   →      19    (+11.76%) |       39.10 ms →       58.33 ms  (+49.19%) | 
- │ │ │ ├ sirius::Non_local_operator                                    |      134.47 μs →      141.37 μs   (+5.13%) |      34   →      38    (+11.76%) |        4.57 ms →        5.37 ms  (+17.50%) | 
+ │ │ │ ├ sirius::D_operator::initialize                                |      129.03 μs →      110.84 μs  (-14.10%) |      17   →      19    (+11.76%) |        2.19 ms →        2.11 ms   (-3.99%) | 
+ │ │ │ └ sirius::Q_operator::initialize                                |      101.81 μs →       90.31 μs  (-11.30%) |      17   →      19    (+11.76%) |        1.73 ms →        1.72 ms   (-0.86%) | 
+ │ │ ├ sirius::Band::solve                                             |        3.61 s  →        2.03 s   (-43.94%) |      17   →      19    (+11.76%) |       61.44 s  →       38.49 s   (-37.35%) | 
+ │ │ │ ├ sirius::Hamiltonian_k                                         |      249.69 μs →      215.89 μs  (-13.53%) |      17   →      19    (+11.76%) |        4.24 ms →        4.10 ms   (-3.36%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      240.73 μs →      205.77 μs  (-14.52%) |      17   →      19    (+11.76%) |        4.09 ms →        3.91 ms   (-4.46%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        6.86 μs →        7.13 μs   (+3.93%) |      17   →      19    (+11.76%) |      116.68 μs →      135.54 μs  (+16.16%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        3.36 s  →        1.96 s   (-41.59%) |      17   →      19    (+11.76%) |       57.06 s  →       37.25 s   (-34.72%) | 
! │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       83.36 ms →       78.87 ms   (-5.39%) |      17   →      19    (+11.76%) |        1.42 s  →        1.50 s    (+5.74%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        9.00 ms →        7.96 ms  (-11.49%) |     102   →     114    (+11.76%) |      917.59 ms →      907.74 ms   (-1.07%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       18.40 ms →       15.19 ms  (-17.45%) |      17   →      19    (+11.76%) |      312.88 ms →      288.68 ms   (-7.73%) | 
- │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      461.09 μs →      490.40 μs   (+6.36%) |      17   →      19    (+11.76%) |        7.84 ms →        9.32 ms  (+18.87%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        8.78 ms →        7.01 ms  (-20.14%) |      34   →      38    (+11.76%) |      298.45 ms →      266.38 ms  (-10.75%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        3.25 s  →        1.86 s   (-42.79%) |      17   →      19    (+11.76%) |       55.21 s  →       35.30 s   (-36.06%) | 
+ │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       86.56 ms →       55.09 ms  (-36.36%) |     287   →     356    (+24.04%) |       24.84 s  →       19.61 s   (-21.06%) | 
+ │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       55.28 ms →       33.17 ms  (-40.00%) |     287   →     356    (+24.04%) |       15.87 s  →       11.81 s   (-25.58%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.72 μs →        1.78 μs   (+3.79%) |     287   →     356    (+24.04%) |      492.49 μs →      634.06 μs  (+28.75%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.45 μs →        1.52 μs   (+5.15%) |     287   →     356    (+24.04%) |      414.90 μs →      541.17 μs  (+30.43%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      337.61 ns →      339.35 ns   (+0.52%) |     287   →     356    (+24.04%) |       96.89 μs →      120.81 μs  (+24.68%) | 
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      475.26 ns →      410.31 ns  (-13.67%) |     287   →     356    (+24.04%) |      136.40 μs →      146.07 μs   (+7.09%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        3.04 ms →        3.03 ms   (-0.37%) |     287   →     356    (+24.04%) |      872.65 ms →        1.08 s   (+23.58%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        5.29 ms →        3.28 ms  (-37.92%) |     287   →     356    (+24.04%) |        1.52 s  →        1.17 s   (-23.00%) | 
+ │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       11.46 ms →        7.80 ms  (-31.99%) |     574   →     712    (+24.04%) |        6.58 s  →        5.55 s   (-15.64%) | 
+ │ │ │ │   ├ sddk::orthogonalize                                       |        9.72 ms →        6.15 ms  (-36.71%) |     287   →     356    (+24.04%) |        2.79 s  →        2.19 s   (-21.50%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        1.51 ms                             |     557                          |      842.96 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       19.19 μs                             |     557                          |       10.69 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                         1.05 ms            |                 693              |                       728.91 ms            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                        62.75 ns            |                 693              |                        43.49 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                       891.54 μs            |                 693              |                       617.84 ms            | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                        45.69 ns            |                 693              |                        31.66 μs            | 
+ │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      215.33 μs →      129.36 μs  (-39.92%) |     287   →     356    (+24.04%) |       61.80 ms →       46.05 ms  (-25.48%) | 
+ │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        2.51 ms →        1.79 ms  (-28.63%) |     287   →     356    (+24.04%) |      720.40 ms →      637.77 ms  (-11.47%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        4.30 ms                             |     270                          |        1.16 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       16.57 μs                             |     270                          |        4.47 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |        6.93 μs                             |     810                          |        5.61 ms                             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                         2.30 ms            |                 337              |                       774.80 ms            | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                       765.64 μs            |                1.01 K            |                       774.07 ms            | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        2.03 ms →        1.21 ms  (-40.55%) |     287   →     356    (+24.04%) |      583.93 ms →      430.62 ms  (-26.25%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        1.93 ms                             |     287                          |      552.84 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       21.15 μs                             |     287                          |        6.07 ms                             | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                         1.14 ms            |                 356              |                       406.62 ms            | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                        41.74 ns            |                 356              |                        14.86 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                       979.93 μs            |                 356              |                       348.86 ms            | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                        43.28 ns            |                 356              |                        15.41 μs            | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       84.60 ms →       32.96 ms  (-61.04%) |     287   →     356    (+24.04%) |       24.28 s  →       11.73 s   (-51.67%) | 
+ │ │ │ │   ├ sirius::residuals                                         |        8.91 ms →        2.74 ms  (-69.21%) |     273   →     340    (+24.54%) |        2.43 s  →      932.55 ms  (-61.66%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        4.20 ms                             |     273                          |        1.15 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       13.76 μs                             |     273                          |        3.76 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |        8.99 μs                             |     546                          |        4.91 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                         1.36 ms            |                 337              |                       457.07 ms            | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                       676.84 μs            |                 674              |                       456.19 ms            | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        4.67 ms →        1.30 ms  (-72.23%) |     273   →     337    (+23.44%) |        1.28 s  →      437.45 ms  (-65.71%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        2.85 ms →        7.35 ms (+157.44%) |      97   →      54    (-44.33%) |      276.84 ms →      396.75 ms  (+43.32%) | 
  │ │ │ │     ├ sddk::transform                                         |        2.75 ms                             |      97                          |      267.20 ms                             | 
  │ │ │ │     │ ├ sddk::transform|init                                  |        8.60 μs                             |      97                          |      833.86 μs                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       10.19 μs                             |      97                          |      988.90 μs                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                         4.41 ms            |                  89              |                       392.66 ms            | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                         3.17 ms            |                 124              |                       392.50 ms            | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      348.65 ns →      370.00 ns   (+6.12%) |      17   →      19    (+11.76%) |        5.93 μs →        7.03 μs  (+18.61%) | 
! │ │ │ └ sirius::K_point_set::sync_band_energies                       |       21.73 μs →       19.64 μs   (-9.62%) |      17   →      19    (+11.76%) |      369.49 μs →      373.25 μs   (+1.02%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.47 ms →        1.51 ms   (+3.24%) |      17   →      19    (+11.76%) |       24.93 ms →       28.76 ms  (+15.38%) | 
! │ │ ├ sirius::Density::generate                                       |      579.31 ms →      563.92 ms   (-2.66%) |      17   →      19    (+11.76%) |        9.85 s  →       10.71 s    (+8.80%) | 
! │ │ │ ├ sirius::Density::generate_valence                             |      412.76 ms →      404.73 ms   (-1.95%) |      17   →      19    (+11.76%) |        7.02 s  →        7.69 s    (+9.59%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        7.82 μs →        8.21 μs   (+5.05%) |      17   →      19    (+11.76%) |      132.92 μs →      156.06 μs  (+17.41%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        6.82 μs →        7.64 μs  (+12.02%) |      17   →      19    (+11.76%) |      115.92 μs →      145.14 μs  (+25.20%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       46.85 ms →       40.87 ms  (-12.76%) |      17   →      19    (+11.76%) |      796.45 ms →      776.60 ms   (-2.49%) | 
! │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.62 μs →        7.46 μs   (-2.07%) |      17   →      19    (+11.76%) |      129.53 μs →      141.76 μs   (+9.45%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        8.09 ms →       22.89 ms (+182.91%) |      17   →      19    (+11.76%) |      137.53 ms →      434.86 ms (+216.20%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       37.68 ms →       16.93 ms  (-55.07%) |      17   →      19    (+11.76%) |      640.58 ms →      321.68 ms  (-49.78%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      613.59 ns →      544.47 ns  (-11.26%) |      17   →      19    (+11.76%) |       10.43 μs →       10.35 μs   (-0.82%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       99.31 ms →       98.38 ms   (-0.94%) |      17   →      19    (+11.76%) |        1.69 s  →        1.87 s   (+10.71%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.01 ms →        2.16 ms   (+7.16%) |      17   →      19    (+11.76%) |       34.22 ms →       40.99 ms  (+19.76%) | 
- │ │ │ │ └ sirius::Density::augment                                    |      221.01 ms →      227.01 ms   (+2.71%) |      17   →      19    (+11.76%) |        3.76 s  →        4.31 s   (+14.80%) | 
- │ │ │ │   └ sirius::Density::generate_rho_aug                         |      220.79 ms →      226.80 ms   (+2.72%) |      17   →      19    (+11.76%) |        3.75 s  →        4.31 s   (+14.81%) | 
! │ │ │ ├ sirius::Field4D::symmetrize                                   |      135.91 ms →      131.04 ms   (-3.59%) |      17   →      19    (+11.76%) |        2.31 s  →        2.49 s    (+7.75%) | 
! │ │ │ │ └ sirius::symmetrize_function|fpw                             |      135.91 ms →      131.04 ms   (-3.59%) |      17   →      19    (+11.76%) |        2.31 s  →        2.49 s    (+7.75%) | 
! │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       50.70 ms →       47.67 ms   (-5.99%) |      17   →      19    (+11.76%) |      861.95 ms →      905.67 ms   (+5.07%) | 
- │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       69.76 ms →       70.10 ms   (+0.48%) |      17   →      19    (+11.76%) |        1.19 s  →        1.33 s   (+12.31%) | 
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       14.80 ms →       12.61 ms  (-14.79%) |      17   →      19    (+11.76%) |      251.66 ms →      239.65 ms   (-4.77%) | 
- │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.65 ms →       23.56 ms   (-0.37%) |      17   →      19    (+11.76%) |      402.07 ms →      447.73 ms  (+11.36%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        6.98 ms →        4.58 ms  (-34.36%) |      17   →      19    (+11.76%) |      118.65 ms →       87.05 ms  (-26.64%) | 
- │ │ ├ sirius::Density::mix                                            |      128.48 ms →      132.67 ms   (+3.26%) |      17   →      19    (+11.76%) |        2.18 s  →        2.52 s   (+15.41%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      949.20 μs →      701.09 μs  (-26.14%) |      17   →      19    (+11.76%) |       16.14 ms →       13.32 ms  (-17.45%) | 
- │ │ │ ├ sirius::Periodic_function|inner                               |        4.78 ms →        4.91 ms   (+2.56%) |     199   →     229    (+15.08%) |      951.75 ms →        1.12 s   (+18.02%) | 
- │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.61 ms →        4.82 ms   (+4.43%) |     199   →     229    (+15.08%) |      918.33 ms →        1.10 s   (+20.18%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.61 ms →        4.82 ms   (+4.43%) |     199   →     229    (+15.08%) |      918.20 ms →        1.10 s   (+20.18%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        4.72 ms →        5.72 ms  (+21.22%) |      17   →      19    (+11.76%) |       80.16 ms →      108.60 ms  (+35.49%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        4.07 ms →        5.01 ms  (+23.12%) |      17   →      19    (+11.76%) |       69.20 ms →       95.22 ms  (+37.60%) | 
- │ │ ├ sirius::Potential::generate                                     |      359.39 ms →      362.05 ms   (+0.74%) |      17   →      19    (+11.76%) |        6.11 s  →        6.88 s   (+12.59%) | 
- │ │ │ ├ sirius::Potential::poisson                                    |       40.59 ms →       42.07 ms   (+3.63%) |      17   →      19    (+11.76%) |      690.10 ms →      799.32 ms  (+15.83%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        3.31 ms →        5.40 ms  (+63.32%) |      17   →      19    (+11.76%) |       56.19 ms →      102.56 ms  (+82.53%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |        5.08 ms →        5.77 ms  (+13.63%) |      17   →      19    (+11.76%) |       86.29 ms →      109.59 ms  (+27.00%) | 
! │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.83 ms →        4.64 ms   (-4.04%) |      17   →      19    (+11.76%) |       82.13 ms →       88.08 ms   (+7.25%) | 
! │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.83 ms →        4.63 ms   (-4.04%) |      17   →      19    (+11.76%) |       82.11 ms →       88.06 ms   (+7.25%) | 
- │ │ │ ├ sirius::Periodic_function::add                                |      774.83 μs →      791.81 μs   (+2.19%) |      34   →      38    (+11.76%) |       26.34 ms →       30.09 ms  (+14.21%) | 
- │ │ │ ├ sirius::Potential::xc                                         |       43.59 ms →       44.84 ms   (+2.88%) |      17   →      19    (+11.76%) |      740.96 ms →      851.98 ms  (+14.98%) | 
- │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       43.58 ms →       43.67 ms   (+0.20%) |      17   →      19    (+11.76%) |      740.90 ms →      829.72 ms  (+11.99%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function                          |      652.36 μs →      684.68 μs   (+4.95%) |      34   →      38    (+11.76%) |       22.18 ms →       26.02 ms  (+17.30%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.51 ms →        4.49 ms   (-0.54%) |      17   →      19    (+11.76%) |       76.75 ms →       85.32 ms  (+11.16%) | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.00 ms →        3.56 ms  (+18.68%) |      17   →      19    (+11.76%) |       50.95 ms →       67.59 ms  (+32.64%) | 
- │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      269.20 ms →      268.57 ms   (-0.23%) |      17   →      19    (+11.76%) |        4.58 s  →        5.10 s   (+11.50%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      319.47 ns →      331.63 ns   (+3.81%) |      17   →      19    (+11.76%) |        5.43 μs →        6.30 μs  (+16.02%) | 
! │ │ ├ sirius::Field4D::symmetrize                                     |      103.02 ms →       95.95 ms   (-6.86%) |      17   →      19    (+11.76%) |        1.75 s  →        1.82 s    (+4.09%) | 
! │ │ │ └ sirius::symmetrize_function|fpw                               |      103.02 ms →       95.95 ms   (-6.86%) |      17   →      19    (+11.76%) |        1.75 s  →        1.82 s    (+4.09%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       18.12 ms →       13.24 ms  (-26.90%) |      17   →      19    (+11.76%) |      307.99 ms →      251.61 ms  (-18.30%) | 
- │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       69.55 ms →       69.49 ms   (-0.09%) |      17   →      19    (+11.76%) |        1.18 s  →        1.32 s   (+11.67%) | 
+ │ │ │   └ sddk::Gvec_shells::remap_backward                           |       14.72 ms →       12.58 ms  (-14.49%) |      17   →      19    (+11.76%) |      250.18 ms →      239.10 ms   (-4.43%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        6.46 ms →        3.88 ms  (-39.98%) |      17   →      19    (+11.76%) |      109.89 ms →       73.71 ms  (-32.92%) | 
! │ │ ├ sirius::Periodic_function|inner                                 |        4.80 ms →        4.69 ms   (-2.24%) |     119   →     133    (+11.76%) |      570.98 ms →      623.85 ms   (+9.26%) | 
! │ │ │ └ sirius::Periodic_function|inner_local                         |        4.75 ms →        4.58 ms   (-3.68%) |     119   →     133    (+11.76%) |      565.37 ms →      608.64 ms   (+7.66%) | 
! │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.75 ms →        4.58 ms   (-3.68%) |     119   →     133    (+11.76%) |      565.28 ms →      608.55 ms   (+7.66%) | 
- │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.59 ms →        4.96 ms   (+8.04%) |      51   →      57    (+11.76%) |      234.33 ms →      282.96 ms  (+20.75%) | 
- │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.53 ms →        4.95 ms   (+9.36%) |      51   →      57    (+11.76%) |      230.91 ms →      282.23 ms  (+22.23%) | 
- │ │ ├ sirius::Periodic_function::integrate                            |        4.52 ms →        4.55 ms   (+0.52%) |      17   →      19    (+11.76%) |       76.87 ms →       86.36 ms  (+12.35%) | 
- │ │ └ sirius::Density::get_magnetisation                              |       76.40 μs →       77.88 μs   (+1.95%) |      17   →      19    (+11.76%) |        1.30 ms →        1.48 ms  (+13.94%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |       71.49 μs →       72.30 μs   (+1.14%) |      17   →      19    (+11.76%) |        1.22 ms →        1.37 ms  (+13.03%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.67 ms →        5.14 ms   (-9.24%) |       2   →       2              |       11.34 ms →       10.29 ms   (-9.24%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.75 ms →        4.57 ms   (-3.83%) |       6   →       6              |       28.51 ms →       27.42 ms   (-3.83%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.73 ms →        4.54 ms   (-3.88%) |       6   →       6              |       28.37 ms →       27.27 ms   (-3.88%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.73 ms →        4.54 ms   (-3.92%) |       6   →       6              |       28.37 ms →       27.25 ms   (-3.92%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.58 ms →        4.94 ms   (+7.89%) |       3   →       3              |       13.73 ms →       14.81 ms   (+7.89%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.54 ms →        4.93 ms   (+8.69%) |       3   →       3              |       13.61 ms →       14.79 ms   (+8.69%) | 
  ├ sirius::Periodic_function|inner                                     |        4.76 ms →        4.56 ms   (-4.10%) |       2   →       2              |        9.52 ms →        9.13 ms   (-4.10%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.71 ms →        4.55 ms   (-3.28%) |       2   →       2              |        9.42 ms →        9.11 ms   (-3.28%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.71 ms →        4.55 ms   (-3.28%) |       2   →       2              |        9.42 ms →        9.11 ms   (-3.28%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.53 ms →        4.94 ms   (+9.09%) |       1   →       1              |        4.53 ms →        4.94 ms   (+9.09%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.51 ms →        4.93 ms   (+9.31%) |       1   →       1              |        4.51 ms →        4.93 ms   (+9.31%) | 
+ └ sirius::finalize                                                    |      765.59 ms →      168.50 ms  (-77.99%) |       1   →       1              |      765.59 ms →      168.50 ms  (-77.99%) | 
  ====================================================================================================================================================================================================
```
