# Benchmark 58f31ed08f2b4e9e6d289f9ed116027f00413e03 vs eab7a5e09a790e571ffec2b67e8d778bf317b1b5
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
- sirius                                                                |       71.53 s  →       82.08 s   (+14.76%) |       1   →       1              |       71.53 s  →       82.08 s   (+14.76%) | 
  ├ sirius::initialize                                                  |        2.92 s  →        2.92 s    (-0.06%) |       1   →       1              |        2.92 s  →        2.92 s    (-0.06%) | 
  ├ sirius::Simulation_context::initialize                              |        3.63 s  →        3.71 s    (+2.09%) |       1   →       1              |        3.63 s  →        3.71 s    (+2.09%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       16.26 ms →      222.52 μs  (-98.63%) |       1   →       1              |       16.26 ms →      222.52 μs  (-98.63%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      141.44 ms →      201.75 ms  (+42.64%) |       1   →       1              |      141.44 ms →      201.75 ms  (+42.64%) | 
- │ │ ├ sirius::Atom_type::init                                         |       60.02 ms →       91.76 ms  (+52.89%) |       2   →       2              |      120.03 ms →      183.51 ms  (+52.89%) | 
+ │ │ └ sirius::Unit_cell::update                                       |       21.31 ms →       18.14 ms  (-14.86%) |       1   →       1              |       21.31 ms →       18.14 ms  (-14.86%) | 
+ │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        5.22 ms →        3.83 ms  (-26.58%) |       1   →       1              |        5.22 ms →        3.83 ms  (-26.58%) | 
+ │ │   └ sirius::Unit_cell::get_symmetry                               |       16.04 ms →       14.22 ms  (-11.32%) |       1   →       1              |       16.04 ms →       14.22 ms  (-11.32%) | 
+ │ │     └ sirius::Unit_cell_symmetry                                  |       15.96 ms →       14.15 ms  (-11.29%) |       1   →       1              |       15.96 ms →       14.15 ms  (-11.29%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.74 ms →        2.75 ms   (+0.21%) |       1   →       1              |        2.74 ms →        2.75 ms   (+0.21%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      506.00 μs →      503.87 μs   (-0.42%) |       1   →       1              |      506.00 μs →      503.87 μs   (-0.42%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       16.91 μs →       15.49 μs   (-8.36%) |       1   →       1              |       16.91 μs →       15.49 μs   (-8.36%) | 
  │ └ sirius::Simulation_context::update                                |        3.42 s  →        3.30 s    (-3.51%) |       1   →       1              |        3.42 s  →        3.30 s    (-3.51%) | 
  │   ├ sirius::Unit_cell::update                                       |        7.06 ms →        6.80 ms   (-3.74%) |       1   →       1              |        7.06 ms →        6.80 ms   (-3.74%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.65 ms →        3.45 ms   (-5.58%) |       1   →       1              |        3.65 ms →        3.45 ms   (-5.58%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.37 ms →        3.29 ms   (-2.49%) |       1   →       1              |        3.37 ms →        3.29 ms   (-2.49%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.32 ms →        3.24 ms   (-2.54%) |       1   →       1              |        3.32 ms →        3.24 ms   (-2.54%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.78 ms →        2.70 ms   (-2.73%) |       1   →       1              |        2.78 ms →        2.70 ms   (-2.73%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      504.28 μs →      498.24 μs   (-1.20%) |       1   →       1              |      504.28 μs →      498.24 μs   (-1.20%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       14.98 μs →       14.18 μs   (-5.37%) |       1   →       1              |       14.98 μs →       14.18 μs   (-5.37%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      213.03 ms →      213.95 ms   (+0.43%) |       2   →       2              |      426.06 ms →      427.91 ms   (+0.43%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.17 ms →       15.19 ms   (+0.14%) |       2   →       2              |       30.33 ms →       30.38 ms   (+0.14%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.26 ms →       13.25 ms   (-0.02%) |       1   →       1              |       13.26 ms →       13.25 ms   (-0.02%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.28 ms →       56.30 ms   (+0.02%) |       2   →       2              |      112.57 ms →      112.59 ms   (+0.02%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.20 ms →       45.23 ms   (+0.08%) |       2   →       2              |       90.39 ms →       90.46 ms   (+0.08%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.30 ms →       60.38 ms   (+0.13%) |       4   →       4              |      241.22 ms →      241.52 ms   (+0.13%) | 
  │   ├ sddk::Gvec::init                                                |       94.13 ms →       93.34 ms   (-0.85%) |       2   →       2              |      188.27 ms →      186.67 ms   (-0.85%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       70.71 ms →       69.04 ms   (-2.36%) |       2   →       2              |      141.43 ms →      138.09 ms   (-2.36%) | 
  │   ├ sddk::Gvec_shells                                               |       99.76 ms →       96.29 ms   (-3.48%) |       1   →       1              |       99.76 ms →       96.29 ms   (-3.48%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.93 ms →        1.95 ms   (+0.60%) |       1   →       1              |        1.93 ms →        1.95 ms   (+0.60%) | 
+ │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      564.51 ms →      504.55 ms  (-10.62%) |       2   →       2              |        1.13 s  →        1.01 s   (-10.62%) | 
- ├ sirius::K_point_set::create_k_mesh                                  |       87.88 ms →      149.60 ms  (+70.23%) |       1   →       1              |       87.88 ms →      149.60 ms  (+70.23%) | 
- │ ├ sirius::K_point::K_point                                          |        1.22 μs →        1.63 μs  (+33.08%) |       4   →       4              |        4.90 μs →        6.52 μs  (+33.08%) | 
- │ └ sirius::K_point_set::initialize                                   |       87.80 ms →      149.52 ms  (+70.29%) |       1   →       1              |       87.80 ms →      149.52 ms  (+70.29%) | 
  │   └ sirius::K_point::initialize                                     |       27.71 ms →       28.86 ms   (+4.13%) |       1   →       1              |       27.71 ms →       28.86 ms   (+4.13%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       10.92 ms →       11.22 ms   (+2.81%) |       1   →       1              |       10.92 ms →       11.22 ms   (+2.81%) | 
  │     │ └ sddk::Gvec::init                                            |        4.91 ms →        5.02 ms   (+2.13%) |       1   →       1              |        4.91 ms →        5.02 ms   (+2.13%) | 
- │     ├ sddk::matrix_storage::matrix_storage                          |        7.64 μs →       10.31 μs  (+34.92%) |       1   →       1              |        7.64 μs →       10.31 μs  (+34.92%) | 
  │     └ sirius::K_point::update                                       |       13.96 ms →       14.76 ms   (+5.74%) |       1   →       1              |       13.96 ms →       14.76 ms   (+5.74%) | 
  │       └ sirius::Beta_projectors                                     |       10.09 ms →       10.75 ms   (+6.63%) |       1   →       1              |       10.09 ms →       10.75 ms   (+6.63%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.25 ms →        8.75 ms   (+6.05%) |       1   →       1              |        8.25 ms →        8.75 ms   (+6.05%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.56 ms →        2.57 ms   (+0.19%) |       2   →       2              |        5.13 ms →        5.14 ms   (+0.19%) | 
  ├ sirius::Potential                                                   |       49.75 ms →       52.08 ms   (+4.68%) |       1   →       1              |       49.75 ms →       52.08 ms   (+4.68%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.89 ms →        2.91 ms   (+0.94%) |       6   →       6              |       17.31 ms →       17.48 ms   (+0.94%) | 
  │ └ sirius::Potential::update                                         |       31.81 ms →       33.99 ms   (+6.84%) |       1   →       1              |       31.81 ms →       33.99 ms   (+6.84%) | 
  │   └ sirius::Potential::generate_local_potential                     |       31.41 ms →       33.60 ms   (+6.95%) |       1   →       1              |       31.41 ms →       33.60 ms   (+6.95%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       26.42 ms →       26.70 ms   (+1.05%) |       1   →       1              |       26.42 ms →       26.70 ms   (+1.05%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        4.46 ms →        6.34 ms  (+42.18%) |       1   →       1              |        4.46 ms →        6.34 ms  (+42.18%) | 
- ├ sirius::Density                                                     |       37.24 ms →       41.65 ms  (+11.83%) |       1   →       1              |       37.24 ms →       41.65 ms  (+11.83%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.81 ms →        2.84 ms   (+1.29%) |       2   →       2              |        5.61 ms →        5.68 ms   (+1.29%) | 
- │ └ sirius::Density::update                                           |       31.49 ms →       35.82 ms  (+13.76%) |       1   →       1              |       31.49 ms →       35.82 ms  (+13.76%) | 
- │   └ sirius::Density::generate_pseudo_core_charge_density            |       31.26 ms →       35.58 ms  (+13.82%) |       1   →       1              |       31.26 ms →       35.58 ms  (+13.82%) | 
- │     ├ sirius::rho_core_ri_pseudo|values                             |       92.00 μs →      103.22 μs  (+12.19%) |       1   →       1              |       92.00 μs →      103.22 μs  (+12.19%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       26.74 ms →       26.92 ms   (+0.67%) |       1   →       1              |       26.74 ms →       26.92 ms   (+0.67%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        4.11 ms →        8.23 ms (+100.34%) |       1   →       1              |        4.11 ms →        8.23 ms (+100.34%) | 
  ├ sirius::Density::initial_density                                    |       55.78 ms →       58.42 ms   (+4.73%) |       1   →       1              |       55.78 ms →       58.42 ms   (+4.73%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       27.48 ms →       27.83 ms   (+1.26%) |       1   →       1              |       27.48 ms →       27.83 ms   (+1.26%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.41 ms →        6.13 ms  (+39.00%) |       2   →       2              |        8.82 ms →       12.27 ms  (+39.00%) | 
+ │ └ sirius::Periodic_function::integrate                              |        5.78 ms →        4.56 ms  (-21.01%) |       1   →       1              |        5.78 ms →        4.56 ms  (-21.01%) | 
  ├ sirius::Potential::generate                                         |      362.32 ms →      366.10 ms   (+1.04%) |       1   →       1              |      362.32 ms →      366.10 ms   (+1.04%) | 
- │ ├ sirius::Potential::poisson                                        |       35.14 ms →       39.05 ms  (+11.12%) |       1   →       1              |       35.14 ms →       39.05 ms  (+11.12%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.90 ms →        8.31 ms (+113.05%) |       1   →       1              |        3.90 ms →        8.31 ms (+113.05%) | 
+ │ │ └ sirius::Periodic_function|inner                                 |        5.41 ms →        4.64 ms  (-14.30%) |       1   →       1              |        5.41 ms →        4.64 ms  (-14.30%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.63 ms →        4.63 ms   (-0.07%) |       1   →       1              |        4.63 ms →        4.63 ms   (-0.07%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.63 ms →        4.62 ms   (-0.05%) |       1   →       1              |        4.63 ms →        4.62 ms   (-0.05%) | 
  │ ├ sirius::Periodic_function::add                                    |      824.48 μs →      745.21 μs   (-9.62%) |       2   →       2              |        1.65 ms →        1.49 ms   (-9.62%) | 
  │ ├ sirius::Potential::xc                                             |       50.85 ms →       51.49 ms   (+1.27%) |       1   →       1              |       50.85 ms →       51.49 ms   (+1.27%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       49.67 ms →       50.30 ms   (+1.28%) |       1   →       1              |       49.67 ms →       50.30 ms   (+1.28%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.53 ms →        2.56 ms   (+1.01%) |       2   →       2              |        5.06 ms →        5.11 ms   (+1.01%) | 
- │ │   └ sirius::Smooth_periodic_function::fft_transform               |        3.89 ms →        4.58 ms  (+17.78%) |       1   →       1              |        3.89 ms →        4.58 ms  (+17.78%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.87 ms →        3.63 ms   (-6.17%) |       1   →       1              |        3.87 ms →        3.63 ms   (-6.17%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      269.35 ms →      269.00 ms   (-0.13%) |       1   →       1              |      269.35 ms →      269.00 ms   (-0.13%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      345.00 ns →      322.00 ns   (-6.67%) |       1   →       1              |      345.00 ns →      322.00 ns   (-6.67%) | 
- ├ sirius::Hamiltonian0                                                |        7.20 ms →        8.93 ms  (+23.99%) |       1   →       1              |        7.20 ms →        8.93 ms  (+23.99%) | 
- │ ├ sirius::Local_operator                                            |        6.68 ms →        8.00 ms  (+19.68%) |       1   →       1              |        6.68 ms →        8.00 ms  (+19.68%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.74 ms →        2.75 ms   (+0.13%) |       1   →       1              |        2.74 ms →        2.75 ms   (+0.13%) | 
- │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        3.09 ms →        4.10 ms  (+32.63%) |       1   →       1              |        3.09 ms →        4.10 ms  (+32.63%) | 
- │ ├ sirius::Non_local_operator                                        |       88.78 μs →      328.69 μs (+270.22%) |       2   →       2              |      177.56 μs →      657.39 μs (+270.22%) | 
+ │ ├ sirius::D_operator::initialize                                    |      152.83 μs →      115.74 μs  (-24.27%) |       1   →       1              |      152.83 μs →      115.74 μs  (-24.27%) | 
  │ └ sirius::Q_operator::initialize                                    |      100.14 μs →       90.92 μs   (-9.21%) |       1   →       1              |      100.14 μs →       90.92 μs   (-9.21%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.29 s  →        1.30 s    (+0.43%) |       1   →       1              |        1.29 s  →        1.30 s    (+0.43%) | 
  │ ├ sirius::Hamiltonian_k                                             |       74.11 ms →       73.91 ms   (-0.27%) |       1   →       1              |       74.11 ms →       73.91 ms   (-0.27%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      264.30 μs →      283.72 μs   (+7.35%) |       1   →       1              |      264.30 μs →      283.72 μs   (+7.35%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       73.84 ms →       73.62 ms   (-0.29%) |       1   →       1              |       73.84 ms →       73.62 ms   (-0.29%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.22 s  →        1.22 s    (+0.47%) |       1   →       1              |        1.22 s  →        1.22 s    (+0.47%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      103.71 ms →      104.72 ms   (+0.98%) |       4   →       4              |      414.84 ms →      418.89 ms   (+0.98%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       41.09 ms →       43.68 ms   (+6.30%) |       1   →       1              |       41.09 ms →       43.68 ms   (+6.30%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        7.90 ms →        8.59 ms   (+8.75%) |       1   →       1              |        7.90 ms →        8.59 ms   (+8.75%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      472.51 ms →      449.68 ms   (-4.83%) |       1   →       1              |      472.51 ms →      449.68 ms   (-4.83%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      382.61 ms →      377.54 ms   (-1.33%) |       1   →       1              |      382.61 ms →      377.54 ms   (-1.33%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.89 μs →        3.90 μs   (+0.31%) |       1   →       1              |        3.89 μs →        3.90 μs   (+0.31%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.91 μs →        2.69 μs   (-7.60%) |       1   →       1              |        2.91 μs →        2.69 μs   (-7.60%) | 
+ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      552.00 ns →      400.00 ns  (-27.54%) |       1   →       1              |      552.00 ns →      400.00 ns  (-27.54%) | 
- │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      879.00 ns →        1.02 μs  (+15.70%) |       1   →       1              |      879.00 ns →        1.02 μs  (+15.70%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::generate                        |        7.89 ms →        3.03 ms  (-61.60%) |       1   →       1              |        7.89 ms →        3.03 ms  (-61.60%) | 
- │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.28 ms →       24.53 ms  (+15.27%) |       1   →       1              |       21.28 ms →       24.53 ms  (+15.27%) | 
+ │ │ │ └ sirius::Non_local_operator::apply                             |       30.34 ms →       22.27 ms  (-26.60%) |       2   →       2              |       60.68 ms →       44.54 ms  (-26.60%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.55 ms →       15.91 ms   (+9.35%) |       2   →       2              |       29.10 ms →       31.82 ms   (+9.35%) | 
  │ │ │ └ sddk::wf_inner                                                |       14.34 ms →       15.70 ms   (+9.49%) |       2   →       2              |       28.68 ms →       31.40 ms   (+9.49%) | 
  │ │ │   ├ sddk::wf_inner|scale                                        |       21.50 ns →       20.50 ns   (-4.65%) |       2   →       2              |       43.00 ns →       41.00 ns   (-4.65%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       14.22 ms →       15.57 ms   (+9.53%) |       2   →       2              |       28.43 ms →       31.14 ms   (+9.53%) | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |       21.00 ns →       20.50 ns   (-2.38%) |       2   →       2              |       42.00 ns →       41.00 ns   (-2.38%) | 
- │ │ ├ Eigensolver_cuda|zhegvdx                                        |       93.65 ms →      111.52 ms  (+19.08%) |       1   →       1              |       93.65 ms →      111.52 ms  (+19.08%) | 
- │ │ └ sddk::wf_trans                                                  |        2.60 ms →        4.75 ms  (+82.32%) |       1   →       1              |        2.60 ms →        4.75 ms  (+82.32%) | 
- │ │   └ sddk::wf_trans|pw                                             |        2.60 ms →        4.74 ms  (+82.43%) |       1   →       1              |        2.60 ms →        4.74 ms  (+82.43%) | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      448.00 ns →      634.00 ns  (+41.52%) |       1   →       1              |      448.00 ns →      634.00 ns  (+41.52%) | 
- ├ sirius::DFT_ground_state::scf_loop                                  |       61.97 s  →       71.60 s   (+15.53%) |       1   →       1              |       61.97 s  →       71.60 s   (+15.53%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.45 ms →        2.47 ms   (+0.59%) |      19   →      19              |       46.60 ms →       46.88 ms   (+0.59%) | 
- │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.25 s  →        3.10 s    (-4.52%) |      19   →      23    (+21.05%) |       61.73 s  →       71.35 s   (+15.58%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        4.78 ms →        4.91 ms   (+2.75%) |      19   →      23    (+21.05%) |       90.87 ms →      113.03 ms  (+24.39%) | 
- │ │ │ ├ sirius::Local_operator                                        |        4.10 ms →        4.16 ms   (+1.65%) |      19   →      23    (+21.05%) |       77.83 ms →       95.77 ms  (+23.05%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function                            |      554.31 μs →      548.92 μs   (-0.97%) |      19   →      23    (+21.05%) |       10.53 ms →       12.63 ms  (+19.88%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.53 ms →        2.49 ms   (-1.69%) |      19   →      23    (+21.05%) |       48.08 ms →       57.22 ms  (+19.00%) | 
- │ │ │ ├ sirius::Non_local_operator                                    |      198.71 μs →      226.02 μs  (+13.75%) |      38   →      46    (+21.05%) |        7.55 ms →       10.40 ms  (+37.69%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |      114.52 μs →      122.77 μs   (+7.21%) |      19   →      23    (+21.05%) |        2.18 ms →        2.82 ms  (+29.78%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       95.38 μs →       94.18 μs   (-1.25%) |      19   →      23    (+21.05%) |        1.81 ms →        2.17 ms  (+19.53%) | 
- │ │ ├ sirius::Band::solve                                             |        2.03 s  →        1.88 s    (-7.41%) |      19   →      23    (+21.05%) |       38.48 s  →       43.13 s   (+12.09%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      222.14 μs →      239.69 μs   (+7.90%) |      19   →      23    (+21.05%) |        4.22 ms →        5.51 ms  (+30.62%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      212.84 μs →      229.48 μs   (+7.82%) |      19   →      23    (+21.05%) |        4.04 ms →        5.28 ms  (+30.52%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        6.70 μs →        7.46 μs  (+11.34%) |      19   →      23    (+21.05%) |      127.22 μs →      171.47 μs  (+34.78%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.96 s  →        1.75 s   (-11.01%) |      19   →      23    (+21.05%) |       37.31 s  →       40.19 s    (+7.73%) | 
- │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       76.67 ms →       70.13 ms   (-8.53%) |      19   →      23    (+21.05%) |        1.46 s  →        1.61 s   (+10.73%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.96 ms →        6.59 ms  (-17.17%) |     114   →     138    (+21.05%) |      907.10 ms →      909.59 ms   (+0.27%) | 
- │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       17.67 ms →       16.23 ms   (-8.13%) |      19   →      23    (+21.05%) |      335.74 ms →      373.39 ms  (+11.21%) | 
- │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      456.20 μs →      484.45 μs   (+6.19%) |      19   →      23    (+21.05%) |        8.67 ms →       11.14 ms  (+28.55%) | 
- │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        8.00 ms →        7.44 ms   (-6.99%) |      38   →      46    (+21.05%) |      304.07 ms →      342.36 ms  (+12.59%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.86 s  →        1.65 s   (-11.35%) |      19   →      23    (+21.05%) |       35.36 s  →       37.94 s    (+7.31%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       51.01 ms →       67.96 ms  (+33.23%) |     356   →     298    (-16.29%) |       18.16 s  →       20.25 s   (+11.53%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       29.83 ms →       43.27 ms  (+45.03%) |     356   →     298    (-16.29%) |       10.62 s  →       12.89 s   (+21.40%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.15 μs →        2.10 μs   (-2.44%) |     356   →     298    (-16.29%) |      765.20 μs →      624.93 μs  (-18.33%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.83 μs →        1.76 μs   (-4.11%) |     356   →     298    (-16.29%) |      651.59 μs →      523.00 μs  (-19.73%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      453.45 ns →      392.15 ns  (-13.52%) |     356   →     298    (-16.29%) |      161.43 μs →      116.86 μs  (-27.61%) | 
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      611.04 ns →      519.66 ns  (-14.96%) |     356   →     298    (-16.29%) |      217.53 μs →      154.86 μs  (-28.81%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.96 ms →        3.12 ms   (+5.69%) |     356   →     298    (-16.29%) |        1.05 s  →      930.96 ms  (-11.53%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.22 ms →        3.85 ms  (+19.34%) |     356   →     298    (-16.29%) |        1.15 s  →        1.15 s    (-0.11%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.49 ms →        8.85 ms  (+18.20%) |     712   →     596    (-16.29%) |        5.33 s  →        5.28 s    (-1.06%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |        6.02 ms →        6.74 ms  (+11.90%) |     356   →     298    (-16.29%) |        2.14 s  →        2.01 s    (-6.33%) | 
- │ │ │ │   │ ├ sddk::wf_inner                                          |        1.01 ms →        1.22 ms  (+21.11%) |     693   →     573    (-17.32%) |      699.73 ms →      700.70 ms   (+0.14%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       51.78 ns →       40.51 ns  (-21.77%) |     693   →     573    (-17.32%) |       35.89 μs →       23.21 μs  (-35.31%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |      850.36 μs →        1.06 ms  (+24.70%) |     693   →     573    (-17.32%) |      589.30 ms →      607.62 ms   (+3.11%) | 
+ │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       45.78 ns →       38.22 ns  (-16.50%) |     693   →     573    (-17.32%) |       31.72 μs →       21.90 μs  (-30.96%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      134.85 μs →      163.34 μs  (+21.13%) |     356   →     298    (-16.29%) |       48.01 ms →       48.68 ms   (+1.40%) | 
! │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        1.77 ms →        1.90 ms   (+7.73%) |     356   →     298    (-16.29%) |      628.51 ms →      566.78 ms   (-9.82%) | 
- │ │ │ │   │ └ sddk::wf_trans                                          |        2.27 ms →        2.51 ms  (+10.47%) |     337   →     275    (-18.40%) |      766.66 ms →      691.13 ms   (-9.85%) | 
- │ │ │ │   │   └ sddk::wf_trans|pw                                     |      757.51 μs →      836.96 μs  (+10.49%) |    1.01 K →     825    (-18.40%) |      765.84 ms →      690.50 ms   (-9.84%) | 
! │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.31 ms →        1.41 ms   (+7.81%) |     356   →     298    (-16.29%) |      464.74 ms →      419.41 ms   (-9.75%) | 
+ │ │ │ │   │ └ sddk::wf_inner                                          |        1.23 ms →        1.30 ms   (+5.67%) |     356   →     298    (-16.29%) |      439.51 ms →      388.77 ms  (-11.55%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       41.08 ns →       32.37 ns  (-21.20%) |     356   →     298    (-16.29%) |       14.63 μs →        9.65 μs  (-34.04%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        1.07 ms →        1.14 ms   (+6.07%) |     356   →     298    (-16.29%) |      382.21 ms →      339.36 ms  (-11.21%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       39.91 ns →       67.86 ns  (+70.03%) |     356   →     298    (-16.29%) |       14.21 μs →       20.22 μs  (+42.33%) | 
- │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       37.53 ms →       46.80 ms  (+24.69%) |     356   →     298    (-16.29%) |       13.36 s  →       13.95 s    (+4.37%) | 
- │ │ │ │   ├ sirius::residuals                                         |        2.61 ms →        3.02 ms  (+15.83%) |     340   →     289    (-15.00%) |      886.23 ms →      872.57 ms   (-1.54%) | 
- │ │ │ │   │ ├ sddk::wf_trans                                          |        1.35 ms →        1.75 ms  (+29.69%) |     337   →     278    (-17.51%) |      454.47 ms →      486.21 ms   (+6.98%) | 
- │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      672.87 μs →      873.05 μs  (+29.75%) |     674   →     556    (-17.51%) |      453.52 ms →      485.42 ms   (+7.03%) | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.17 ms →        1.25 ms   (+6.85%) |     337   →     278    (-17.51%) |      393.64 ms →      346.96 ms  (-11.86%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        6.14 ms →        7.63 ms  (+24.21%) |      54   →      57     (+5.56%) |      331.80 ms →      435.04 ms  (+31.11%) | 
- │ │ │ │     └ sddk::wf_trans                                          |        3.68 ms →        4.73 ms  (+28.76%) |      89   →      91     (+2.25%) |      327.26 ms →      430.85 ms  (+31.65%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |        2.64 ms →        3.45 ms  (+30.62%) |     124   →     125     (+0.81%) |      327.09 ms →      430.68 ms  (+31.67%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      382.58 ns →      376.22 ns   (-1.66%) |      19   →      23    (+21.05%) |        7.27 μs →        8.65 μs  (+19.04%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       19.34 μs →       20.47 μs   (+5.84%) |      19   →      23    (+21.05%) |      367.49 μs →      470.85 μs  (+28.12%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.52 ms →        1.48 ms   (-2.42%) |      19   →      23    (+21.05%) |       28.85 ms →       34.07 ms  (+18.12%) | 
- │ │ ├ sirius::Density::generate                                       |      572.07 ms →      563.51 ms   (-1.50%) |      19   →      23    (+21.05%) |       10.87 s  →       12.96 s   (+19.24%) | 
+ │ │ │ ├ sirius::Density::generate_valence                             |      433.36 ms →      385.31 ms  (-11.09%) |      19   →      23    (+21.05%) |        8.23 s  →        8.86 s    (+7.63%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.68 μs →        8.19 μs   (-5.60%) |      19   →      23    (+21.05%) |      164.94 μs →      188.48 μs  (+14.27%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        8.06 μs →        7.62 μs   (-5.43%) |      19   →      23    (+21.05%) |      153.15 μs →      175.32 μs  (+14.48%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       35.40 ms →       43.35 ms  (+22.45%) |      19   →      23    (+21.05%) |      672.69 ms →      997.09 ms  (+48.22%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.67 μs →        7.50 μs   (-2.17%) |      19   →      23    (+21.05%) |      145.66 μs →      172.50 μs  (+18.43%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        5.82 ms →       23.44 ms (+302.75%) |      19   →      23    (+21.05%) |      110.56 ms →      539.03 ms (+387.54%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       28.55 ms →       18.84 ms  (-34.02%) |      19   →      23    (+21.05%) |      542.39 ms →      433.23 ms  (-20.12%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      484.37 ns →      674.70 ns  (+39.29%) |      19   →      23    (+21.05%) |        9.20 μs →       15.52 μs  (+68.62%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      110.72 ms →       96.06 ms  (-13.24%) |      19   →      23    (+21.05%) |        2.10 s  →        2.21 s    (+5.03%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.98 ms →        1.97 ms   (-0.34%) |      19   →      23    (+21.05%) |       37.53 ms →       45.27 ms  (+20.64%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |      252.89 ms →      197.92 ms  (-21.74%) |      19   →      23    (+21.05%) |        4.80 s  →        4.55 s    (-5.26%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |      252.67 ms →      197.69 ms  (-21.76%) |      19   →      23    (+21.05%) |        4.80 s  →        4.55 s    (-5.29%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      110.89 ms →      150.31 ms  (+35.55%) |      19   →      23    (+21.05%) |        2.11 s  →        3.46 s   (+64.08%) | 
- │ │ │ │ └ sirius::symmetrize_function|fpw                             |      110.89 ms →      150.31 ms  (+35.55%) |      19   →      23    (+21.05%) |        2.11 s  →        3.46 s   (+64.08%) | 
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       26.53 ms →       66.48 ms (+150.60%) |      19   →      23    (+21.05%) |      504.01 ms →        1.53 s  (+203.36%) | 
- │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       71.11 ms →       70.58 ms   (-0.75%) |      19   →      23    (+21.05%) |        1.35 s  →        1.62 s   (+20.14%) | 
- │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.61 ms →       12.61 ms   (+0.01%) |      19   →      23    (+21.05%) |      239.52 ms →      289.99 ms  (+21.07%) | 
- │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.58 ms →       23.61 ms   (+0.10%) |      19   →      23    (+21.05%) |      448.07 ms →      542.92 ms  (+21.17%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        4.23 ms →        4.28 ms   (+1.14%) |      19   →      23    (+21.05%) |       80.42 ms →       98.46 ms  (+22.44%) | 
- │ │ ├ sirius::Density::mix                                            |      133.57 ms →      143.35 ms   (+7.32%) |      19   →      23    (+21.05%) |        2.54 s  →        3.30 s   (+29.91%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      291.24 μs →      540.55 μs  (+85.61%) |      19   →      23    (+21.05%) |        5.53 ms →       12.43 ms (+124.68%) | 
- │ │ │ ├ sirius::Periodic_function|inner                               |        4.99 ms →        5.20 ms   (+4.29%) |     229   →     289    (+26.20%) |        1.14 s  →        1.50 s   (+31.61%) | 
- │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.82 ms →        4.82 ms   (-0.06%) |     229   →     289    (+26.20%) |        1.10 s  →        1.39 s   (+26.13%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.82 ms →        4.82 ms   (-0.05%) |     229   →     289    (+26.20%) |        1.10 s  →        1.39 s   (+26.14%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        5.87 ms →        5.41 ms   (-7.86%) |      19   →      23    (+21.05%) |      111.50 ms →      124.36 ms  (+11.54%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.12 ms →        4.66 ms   (-9.02%) |      19   →      23    (+21.05%) |       97.31 ms →      107.17 ms  (+10.13%) | 
- │ │ ├ sirius::Potential::generate                                     |      356.24 ms →      359.89 ms   (+1.02%) |      19   →      23    (+21.05%) |        6.77 s  →        8.28 s   (+22.29%) | 
- │ │ │ ├ sirius::Potential::poisson                                    |       35.79 ms →       39.68 ms  (+10.88%) |      19   →      23    (+21.05%) |      679.99 ms →      912.69 ms  (+34.22%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        4.05 ms →        8.79 ms (+117.11%) |      19   →      23    (+21.05%) |       76.89 ms →      202.09 ms (+162.82%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner                             |        5.87 ms →        4.85 ms  (-17.39%) |      19   →      23    (+21.05%) |      111.59 ms →      111.59 ms   (-0.00%) | 
- │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.64 ms →        4.63 ms   (-0.23%) |      19   →      23    (+21.05%) |       88.09 ms →      106.39 ms  (+20.77%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.64 ms →        4.62 ms   (-0.23%) |      19   →      23    (+21.05%) |       88.07 ms →      106.37 ms  (+20.78%) | 
- │ │ │ ├ sirius::Periodic_function::add                                |      807.59 μs →      753.26 μs   (-6.73%) |      38   →      46    (+21.05%) |       30.69 ms →       34.65 ms  (+12.91%) | 
- │ │ │ ├ sirius::Potential::xc                                         |       44.52 ms →       45.06 ms   (+1.21%) |      19   →      23    (+21.05%) |      845.94 ms →        1.04 s   (+22.52%) | 
- │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       43.34 ms →       43.88 ms   (+1.26%) |      19   →      23    (+21.05%) |      823.42 ms →        1.01 s   (+22.58%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function                          |      683.34 μs →      675.78 μs   (-1.11%) |      38   →      46    (+21.05%) |       25.97 ms →       31.09 ms  (+19.71%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.09 ms →        4.54 ms  (+10.98%) |      19   →      23    (+21.05%) |       77.77 ms →      104.47 ms  (+34.34%) | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.81 ms →        3.66 ms   (-3.93%) |      19   →      23    (+21.05%) |       72.33 ms →       84.11 ms  (+16.30%) | 
- │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      269.10 ms →      268.55 ms   (-0.21%) |      19   →      23    (+21.05%) |        5.11 s  →        6.18 s   (+20.80%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      313.32 ns →      325.74 ns   (+3.97%) |      19   →      23    (+21.05%) |        5.95 μs →        7.49 μs  (+25.85%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |       98.46 ms →       97.09 ms   (-1.40%) |      19   →      23    (+21.05%) |        1.87 s  →        2.23 s   (+19.36%) | 
- │ │ │ └ sirius::symmetrize_function|fpw                               |       98.46 ms →       97.09 ms   (-1.40%) |      19   →      23    (+21.05%) |        1.87 s  →        2.23 s   (+19.36%) | 
- │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       14.26 ms →       13.22 ms   (-7.30%) |      19   →      23    (+21.05%) |      270.97 ms →      304.07 ms  (+12.21%) | 
- │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       70.99 ms →       70.72 ms   (-0.38%) |      19   →      23    (+21.05%) |        1.35 s  →        1.63 s   (+20.59%) | 
- │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.59 ms →       12.51 ms   (-0.59%) |      19   →      23    (+21.05%) |      239.12 ms →      287.74 ms  (+20.34%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        4.13 ms →        4.41 ms   (+6.75%) |      19   →      23    (+21.05%) |       78.41 ms →      101.32 ms  (+29.22%) | 
- │ │ ├ sirius::Periodic_function|inner                                 |        4.80 ms →        4.69 ms   (-2.31%) |     133   →     161    (+21.05%) |      638.49 ms →      755.08 ms  (+18.26%) | 
- │ │ │ └ sirius::Periodic_function|inner_local                         |        4.61 ms →        4.56 ms   (-1.08%) |     133   →     161    (+21.05%) |      613.13 ms →      734.22 ms  (+19.75%) | 
- │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.61 ms →        4.56 ms   (-1.07%) |     133   →     161    (+21.05%) |      613.04 ms →      734.13 ms  (+19.75%) | 
- │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.94 ms →        4.95 ms   (+0.27%) |      57   →      69    (+21.05%) |      281.59 ms →      341.80 ms  (+21.38%) | 
- │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.93 ms →        4.93 ms   (+0.07%) |      57   →      69    (+21.05%) |      281.02 ms →      340.42 ms  (+21.13%) | 
- │ │ ├ sirius::Periodic_function::integrate                            |        4.54 ms →        4.54 ms   (+0.03%) |      19   →      23    (+21.05%) |       86.18 ms →      104.35 ms  (+21.09%) | 
- │ │ └ sirius::Density::get_magnetisation                              |       78.10 μs →       76.15 μs   (-2.50%) |      19   →      23    (+21.05%) |        1.48 ms →        1.75 ms  (+18.03%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |       73.14 μs →       71.40 μs   (-2.37%) |      19   →      23    (+21.05%) |        1.39 ms →        1.64 ms  (+18.18%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.12 ms →        5.17 ms   (+1.16%) |       2   →       2              |       10.23 ms →       10.35 ms   (+1.16%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.81 ms →        4.55 ms   (-5.24%) |       6   →       6              |       28.83 ms →       27.32 ms   (-5.24%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.80 ms →        4.55 ms   (-5.32%) |       6   →       6              |       28.81 ms →       27.28 ms   (-5.32%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.80 ms →        4.55 ms   (-5.30%) |       6   →       6              |       28.80 ms →       27.27 ms   (-5.30%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        5.20 ms →        4.92 ms   (-5.40%) |       3   →       3              |       15.61 ms →       14.77 ms   (-5.40%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        5.20 ms →        4.92 ms   (-5.42%) |       3   →       3              |       15.60 ms →       14.75 ms   (-5.42%) | 
  ├ sirius::Periodic_function|inner                                     |        4.80 ms →        4.54 ms   (-5.44%) |       2   →       2              |        9.59 ms →        9.07 ms   (-5.44%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.79 ms →        4.53 ms   (-5.51%) |       2   →       2              |        9.59 ms →        9.06 ms   (-5.51%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.79 ms →        4.53 ms   (-5.50%) |       2   →       2              |        9.59 ms →        9.06 ms   (-5.50%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        5.17 ms →        4.97 ms   (-3.81%) |       1   →       1              |        5.17 ms →        4.97 ms   (-3.81%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        5.16 ms →        4.96 ms   (-3.82%) |       1   →       1              |        5.16 ms →        4.96 ms   (-3.82%) | 
- └ sirius::finalize                                                    |      170.33 ms →      547.41 ms (+221.38%) |       1   →       1              |      170.33 ms →      547.41 ms (+221.38%) | 
  ====================================================================================================================================================================================================
```
