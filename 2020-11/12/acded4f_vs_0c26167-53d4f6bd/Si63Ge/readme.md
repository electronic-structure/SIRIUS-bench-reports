# Benchmark 0c261670dec9b96a58dd74a9134f19b00042d6d1 vs acded4f8dc8bf829fcf788e7dbd08a23ea769390
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |       72.81 s  →       70.95 s    (-2.56%) |       1   →       1              |       72.81 s  →       70.95 s    (-2.56%) | 
  ├ sirius::initialize                                                  |        2.86 s  →        2.87 s    (+0.34%) |       1   →       1              |        2.86 s  →        2.87 s    (+0.34%) | 
  ├ sirius::Simulation_context::initialize                              |        3.78 s  →        3.60 s    (-4.84%) |       1   →       1              |        3.78 s  →        3.60 s    (-4.84%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       70.28 ms →       43.18 ms  (-38.56%) |       1   →       1              |       70.28 ms →       43.18 ms  (-38.56%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      217.66 ms →      154.78 ms  (-28.89%) |       1   →       1              |      217.66 ms →      154.78 ms  (-28.89%) | 
+ │ │ ├ sirius::Atom_type::init                                         |      100.40 ms →       67.41 ms  (-32.86%) |       2   →       2              |      200.80 ms →      134.82 ms  (-32.86%) | 
- │ │ └ sirius::Unit_cell::update                                       |       16.76 ms →       19.87 ms  (+18.54%) |       1   →       1              |       16.76 ms →       19.87 ms  (+18.54%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.71 ms →        3.89 ms   (+4.94%) |       1   →       1              |        3.71 ms →        3.89 ms   (+4.94%) | 
- │ │   └ sirius::Unit_cell::get_symmetry                               |       12.97 ms →       15.92 ms  (+22.79%) |       1   →       1              |       12.97 ms →       15.92 ms  (+22.79%) | 
- │ │     └ sirius::Unit_cell_symmetry                                  |       12.89 ms →       15.85 ms  (+22.90%) |       1   →       1              |       12.89 ms →       15.85 ms  (+22.90%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.75 ms →        2.74 ms   (-0.59%) |       1   →       1              |        2.75 ms →        2.74 ms   (-0.59%) | 
+ │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      569.72 μs →      495.69 μs  (-13.00%) |       1   →       1              |      569.72 μs →      495.69 μs  (-13.00%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       16.49 μs →       16.37 μs   (-0.75%) |       1   →       1              |       16.49 μs →       16.37 μs   (-0.75%) | 
  │ └ sirius::Simulation_context::update                                |        3.40 s  →        3.21 s    (-5.40%) |       1   →       1              |        3.40 s  →        3.21 s    (-5.40%) | 
  │   ├ sirius::Unit_cell::update                                       |        7.13 ms →        7.01 ms   (-1.68%) |       1   →       1              |        7.13 ms →        7.01 ms   (-1.68%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.77 ms →        3.65 ms   (-3.14%) |       1   →       1              |        3.77 ms →        3.65 ms   (-3.14%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.31 ms →        3.33 ms   (+0.38%) |       1   →       1              |        3.31 ms →        3.33 ms   (+0.38%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.27 ms →        3.28 ms   (+0.40%) |       1   →       1              |        3.27 ms →        3.28 ms   (+0.40%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.72 ms →        2.73 ms   (+0.15%) |       1   →       1              |        2.72 ms →        2.73 ms   (+0.15%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      506.97 μs →      516.67 μs   (+1.91%) |       1   →       1              |      506.97 μs →      516.67 μs   (+1.91%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       14.02 μs →       14.25 μs   (+1.68%) |       1   →       1              |       14.02 μs →       14.25 μs   (+1.68%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      212.60 ms →      213.76 ms   (+0.54%) |       2   →       2              |      425.21 ms →      427.52 ms   (+0.54%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.17 ms →       15.16 ms   (-0.07%) |       2   →       2              |       30.33 ms →       30.31 ms   (-0.07%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.26 ms →       13.27 ms   (+0.06%) |       1   →       1              |       13.26 ms →       13.27 ms   (+0.06%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.34 ms →       56.33 ms   (-0.01%) |       2   →       2              |      112.68 ms →      112.66 ms   (-0.01%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.06 ms →       45.11 ms   (+0.12%) |       2   →       2              |       90.12 ms →       90.23 ms   (+0.12%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.11 ms →       60.29 ms   (+0.30%) |       4   →       4              |      240.42 ms →      241.14 ms   (+0.30%) | 
  │   ├ sddk::Gvec::init                                                |       92.71 ms →       92.69 ms   (-0.02%) |       2   →       2              |      185.43 ms →      185.39 ms   (-0.02%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       69.48 ms →       69.36 ms   (-0.17%) |       2   →       2              |      138.95 ms →      138.72 ms   (-0.17%) | 
  │   ├ sddk::Gvec_shells                                               |       93.01 ms →       93.40 ms   (+0.42%) |       1   →       1              |       93.01 ms →       93.40 ms   (+0.42%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        2.02 ms →        1.94 ms   (-3.81%) |       1   →       1              |        2.02 ms →        1.94 ms   (-3.81%) | 
+ │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      546.70 ms →      461.68 ms  (-15.55%) |       2   →       2              |        1.09 s  →      923.36 ms  (-15.55%) | 
- ├ sirius::K_point_set::create_k_mesh                                  |      149.02 ms →      164.69 ms  (+10.51%) |       1   →       1              |      149.02 ms →      164.69 ms  (+10.51%) | 
  │ ├ sirius::K_point::K_point                                          |        1.27 μs →        1.23 μs   (-3.12%) |       4   →       4              |        5.09 μs →        4.93 μs   (-3.12%) | 
- │ └ sirius::K_point_set::initialize                                   |      148.94 ms →      164.60 ms  (+10.52%) |       1   →       1              |      148.94 ms →      164.60 ms  (+10.52%) | 
  │   └ sirius::K_point::initialize                                     |       27.64 ms →       29.85 ms   (+8.01%) |       1   →       1              |       27.64 ms →       29.85 ms   (+8.01%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       11.07 ms →       11.61 ms   (+4.88%) |       1   →       1              |       11.07 ms →       11.61 ms   (+4.88%) | 
  │     │ └ sddk::Gvec::init                                            |        4.98 ms →        5.30 ms   (+6.52%) |       1   →       1              |        4.98 ms →        5.30 ms   (+6.52%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |       10.57 μs →       10.62 μs   (+0.48%) |       1   →       1              |       10.57 μs →       10.62 μs   (+0.48%) | 
- │     └ sirius::K_point::update                                       |       13.74 ms →       15.25 ms  (+11.01%) |       1   →       1              |       13.74 ms →       15.25 ms  (+11.01%) | 
  │       └ sirius::Beta_projectors                                     |        9.97 ms →       10.96 ms   (+9.90%) |       1   →       1              |        9.97 ms →       10.96 ms   (+9.90%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.20 ms →        8.78 ms   (+7.05%) |       1   →       1              |        8.20 ms →        8.78 ms   (+7.05%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.54 ms →        2.60 ms   (+2.51%) |       2   →       2              |        5.08 ms →        5.21 ms   (+2.51%) | 
  ├ sirius::Potential                                                   |       54.69 ms →       50.14 ms   (-8.33%) |       1   →       1              |       54.69 ms →       50.14 ms   (-8.33%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.93 ms →        2.93 ms   (-0.04%) |       6   →       6              |       17.59 ms →       17.58 ms   (-0.04%) | 
+ │ └ sirius::Potential::update                                         |       36.60 ms →       32.01 ms  (-12.56%) |       1   →       1              |       36.60 ms →       32.01 ms  (-12.56%) | 
+ │   └ sirius::Potential::generate_local_potential                     |       36.17 ms →       31.59 ms  (-12.66%) |       1   →       1              |       36.17 ms →       31.59 ms  (-12.66%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       31.39 ms →       26.55 ms  (-15.42%) |       1   →       1              |       31.39 ms →       26.55 ms  (-15.42%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        4.22 ms →        4.49 ms   (+6.47%) |       1   →       1              |        4.22 ms →        4.49 ms   (+6.47%) | 
+ ├ sirius::Density                                                     |       42.37 ms →       37.21 ms  (-12.18%) |       1   →       1              |       42.37 ms →       37.21 ms  (-12.18%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.85 ms →        2.83 ms   (-0.81%) |       2   →       2              |        5.71 ms →        5.66 ms   (-0.81%) | 
+ │ └ sirius::Density::update                                           |       36.51 ms →       31.41 ms  (-13.97%) |       1   →       1              |       36.51 ms →       31.41 ms  (-13.97%) | 
+ │   └ sirius::Density::generate_pseudo_core_charge_density            |       36.19 ms →       31.18 ms  (-13.84%) |       1   →       1              |       36.19 ms →       31.18 ms  (-13.84%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |       79.22 μs →       76.60 μs   (-3.31%) |       1   →       1              |       79.22 μs →       76.60 μs   (-3.31%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       32.15 ms →       26.67 ms  (-17.04%) |       1   →       1              |       32.15 ms →       26.67 ms  (-17.04%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        3.62 ms →        4.12 ms  (+13.74%) |       1   →       1              |        3.62 ms →        4.12 ms  (+13.74%) | 
+ ├ sirius::Density::initial_density                                    |       63.39 ms →       56.05 ms  (-11.58%) |       1   →       1              |       63.39 ms →       56.05 ms  (-11.58%) | 
+ │ ├ sirius::Simulation_context::make_periodic_function                |       35.86 ms →       27.48 ms  (-23.37%) |       1   →       1              |       35.86 ms →       27.48 ms  (-23.37%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.77 ms →        4.51 ms   (-5.52%) |       2   →       2              |        9.54 ms →        9.02 ms   (-5.52%) | 
- │ └ sirius::Periodic_function::integrate                              |        4.56 ms →        5.71 ms  (+25.02%) |       1   →       1              |        4.56 ms →        5.71 ms  (+25.02%) | 
  ├ sirius::Potential::generate                                         |      371.00 ms →      363.16 ms   (-2.11%) |       1   →       1              |      371.00 ms →      363.16 ms   (-2.11%) | 
+ │ ├ sirius::Potential::poisson                                        |       43.65 ms →       35.65 ms  (-18.34%) |       1   →       1              |       43.65 ms →       35.65 ms  (-18.34%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.64 ms →        3.82 ms   (+4.92%) |       1   →       1              |        3.64 ms →        3.82 ms   (+4.92%) | 
- │ │ └ sirius::Periodic_function|inner                                 |        4.64 ms →        5.90 ms  (+26.97%) |       1   →       1              |        4.64 ms →        5.90 ms  (+26.97%) | 
- │ │   └ sirius::Periodic_function|inner_local                         |        4.63 ms →        5.16 ms  (+11.26%) |       1   →       1              |        4.63 ms →        5.16 ms  (+11.26%) | 
- │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.63 ms →        5.15 ms  (+11.27%) |       1   →       1              |        4.63 ms →        5.15 ms  (+11.27%) | 
  │ ├ sirius::Periodic_function::add                                    |      766.94 μs →      825.15 μs   (+7.59%) |       2   →       2              |        1.53 ms →        1.65 ms   (+7.59%) | 
  │ ├ sirius::Potential::xc                                             |       52.42 ms →       51.44 ms   (-1.87%) |       1   →       1              |       52.42 ms →       51.44 ms   (-1.87%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.22 ms →       50.27 ms   (-1.85%) |       1   →       1              |       51.22 ms →       50.27 ms   (-1.85%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.57 ms →        2.56 ms   (-0.60%) |       2   →       2              |        5.14 ms →        5.11 ms   (-0.60%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.87 ms →        4.72 ms   (-3.11%) |       1   →       1              |        4.87 ms →        4.72 ms   (-3.11%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.80 ms →        3.61 ms   (-5.03%) |       1   →       1              |        3.80 ms →        3.61 ms   (-5.03%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      268.31 ms →      269.38 ms   (+0.40%) |       1   →       1              |      268.31 ms →      269.38 ms   (+0.40%) | 
+ │ └ sirius::Potential::generate_PAW_effective_potential               |      232.00 ns →       75.00 ns  (-67.67%) |       1   →       1              |      232.00 ns →       75.00 ns  (-67.67%) | 
+ ├ sirius::Hamiltonian0                                                |        8.84 ms →        6.35 ms  (-28.12%) |       1   →       1              |        8.84 ms →        6.35 ms  (-28.12%) | 
+ │ ├ sirius::Local_operator                                            |        7.76 ms →        5.88 ms  (-24.29%) |       1   →       1              |        7.76 ms →        5.88 ms  (-24.29%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.73 ms →        2.75 ms   (+0.54%) |       1   →       1              |        2.73 ms →        2.75 ms   (+0.54%) | 
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        4.10 ms →        2.36 ms  (-42.37%) |       1   →       1              |        4.10 ms →        2.36 ms  (-42.37%) | 
+ │ ├ sirius::Non_local_operator                                        |      407.92 μs →       71.55 μs  (-82.46%) |       2   →       2              |      815.85 μs →      143.10 μs  (-82.46%) | 
- │ ├ sirius::D_operator::initialize                                    |       98.42 μs →      132.40 μs  (+34.53%) |       1   →       1              |       98.42 μs →      132.40 μs  (+34.53%) | 
- │ └ sirius::Q_operator::initialize                                    |       92.79 μs →      119.29 μs  (+28.56%) |       1   →       1              |       92.79 μs →      119.29 μs  (+28.56%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.28 s  →        1.29 s    (+0.47%) |       1   →       1              |        1.28 s  →        1.29 s    (+0.47%) | 
+ │ ├ sirius::Hamiltonian_k                                             |       57.77 ms →       51.10 ms  (-11.55%) |       1   →       1              |       57.77 ms →       51.10 ms  (-11.55%) | 
- │ │ ├ sirius::Local_operator::prepare_k                               |      213.68 μs →      283.87 μs  (+32.85%) |       1   →       1              |      213.68 μs →      283.87 μs  (+32.85%) | 
+ │ │ └ sirius::Beta_projectors_base::prepare                           |       57.55 ms →       50.81 ms  (-11.72%) |       1   →       1              |       57.55 ms →       50.81 ms  (-11.72%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.23 s  →        1.24 s    (+1.04%) |       1   →       1              |        1.23 s  →        1.24 s    (+1.04%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       76.92 ms →       78.61 ms   (+2.20%) |       4   →       4              |      307.68 ms →      314.45 ms   (+2.20%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       44.89 ms →       44.82 ms   (-0.15%) |       1   →       1              |       44.89 ms →       44.82 ms   (-0.15%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        8.72 ms →        8.85 ms   (+1.50%) |       1   →       1              |        8.72 ms →        8.85 ms   (+1.50%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      311.39 ms →      334.59 ms   (+7.45%) |       1   →       1              |      311.39 ms →      334.59 ms   (+7.45%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      244.05 ms →      246.76 ms   (+1.11%) |       1   →       1              |      244.05 ms →      246.76 ms   (+1.11%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.89 μs →        3.79 μs   (-2.65%) |       1   →       1              |        3.89 μs →        3.79 μs   (-2.65%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.97 μs →        2.91 μs   (-2.15%) |       1   →       1              |        2.97 μs →        2.91 μs   (-2.15%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      549.00 ns →      496.00 ns   (-9.65%) |       1   →       1              |      549.00 ns →      496.00 ns   (-9.65%) | 
- │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      568.00 ns →      728.00 ns  (+28.17%) |       1   →       1              |      568.00 ns →      728.00 ns  (+28.17%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.20 ms →        3.17 ms   (-0.86%) |       1   →       1              |        3.20 ms →        3.17 ms   (-0.86%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.26 ms →       21.34 ms   (+0.41%) |       1   →       1              |       21.26 ms →       21.34 ms   (+0.41%) | 
- │ │ │ └ sirius::Non_local_operator::apply                             |       21.42 ms →       31.63 ms  (+47.68%) |       2   →       2              |       42.84 ms →       63.26 ms  (+47.68%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       16.21 ms →       14.92 ms   (-7.94%) |       2   →       2              |       32.42 ms →       29.85 ms   (-7.94%) | 
  │ │ │ └ sddk::wf_inner                                                |       16.00 ms →       14.72 ms   (-8.04%) |       2   →       2              |       32.00 ms →       29.43 ms   (-8.04%) | 
+ │ │ │   ├ sddk::wf_inner|scale                                        |       37.50 ns →       23.50 ns  (-37.33%) |       2   →       2              |       75.00 ns →       47.00 ns  (-37.33%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       15.87 ms →       14.59 ms   (-8.06%) |       2   →       2              |       31.73 ms →       29.17 ms   (-8.06%) | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |       38.50 ns →       38.50 ns            |       2   →       2              |       77.00 ns →       77.00 ns            | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      251.56 ms →      232.30 ms   (-7.66%) |       1   →       1              |      251.56 ms →      232.30 ms   (-7.66%) | 
  │ │ └ sddk::wf_trans                                                  |        2.61 ms →        2.60 ms   (-0.64%) |       1   →       1              |        2.61 ms →        2.60 ms   (-0.64%) | 
  │ │   └ sddk::wf_trans|pw                                             |        2.61 ms →        2.59 ms   (-0.62%) |       1   →       1              |        2.61 ms →        2.59 ms   (-0.62%) | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      397.00 ns →      622.00 ns  (+56.68%) |       1   →       1              |      397.00 ns →      622.00 ns  (+56.68%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |       63.11 s  →       61.40 s    (-2.70%) |       1   →       1              |       63.11 s  →       61.40 s    (-2.70%) | 
- │ ├ sirius::Smooth_periodic_function                                  |        2.48 ms →        2.79 ms  (+12.67%) |      19   →      83   (+336.84%) |       47.11 ms →      231.87 ms (+392.18%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        2.99 s  →        3.05 s    (+2.10%) |      21   →      20     (-4.76%) |       62.76 s  →       61.03 s    (-2.76%) | 
+ │ │ ├ sirius::Hamiltonian0                                            |        5.94 ms →        5.09 ms  (-14.21%) |      21   →      20     (-4.76%) |      124.67 ms →      101.86 ms  (-18.30%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        5.09 ms →        4.46 ms  (-12.41%) |      21   →      20     (-4.76%) |      106.97 ms →       89.23 ms  (-16.58%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      559.53 μs →      553.47 μs   (-1.08%) |      21   →      20     (-4.76%) |       11.75 ms →       11.07 ms   (-5.79%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.31 ms →        2.73 ms  (-17.62%) |      21   →      20     (-4.76%) |       69.59 ms →       54.60 ms  (-21.54%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |      283.23 μs →      164.38 μs  (-41.96%) |      42   →      40     (-4.76%) |       11.90 ms →        6.58 ms  (-44.73%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |      110.56 μs →      129.91 μs  (+17.51%) |      21   →      20     (-4.76%) |        2.32 ms →        2.60 ms  (+11.91%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       89.82 μs →       91.49 μs   (+1.86%) |      21   →      20     (-4.76%) |        1.89 ms →        1.83 ms   (-3.00%) | 
  │ │ ├ sirius::Band::solve                                             |        1.76 s  →        1.80 s    (+2.08%) |      21   →      20     (-4.76%) |       36.96 s  →       35.93 s    (-2.78%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      203.17 μs →      221.26 μs   (+8.90%) |      21   →      20     (-4.76%) |        4.27 ms →        4.43 ms   (+3.72%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      193.93 μs →      212.10 μs   (+9.37%) |      21   →      20     (-4.76%) |        4.07 ms →        4.24 ms   (+4.16%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        6.62 μs →        7.01 μs   (+5.87%) |      21   →      20     (-4.76%) |      139.07 μs →      140.22 μs   (+0.83%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.64 s  →        1.67 s    (+1.86%) |      21   →      20     (-4.76%) |       34.35 s  →       33.32 s    (-2.99%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       72.64 ms →       68.60 ms   (-5.56%) |      21   →      20     (-4.76%) |        1.53 s  →        1.37 s   (-10.06%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.37 ms →        7.57 ms   (+2.71%) |     126   →     120     (-4.76%) |      928.34 ms →      908.05 ms   (-2.19%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       18.42 ms →       17.75 ms   (-3.60%) |      21   →      20     (-4.76%) |      386.72 ms →      355.04 ms   (-8.19%) | 
+ │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      484.44 μs →      454.12 μs   (-6.26%) |      21   →      20     (-4.76%) |       10.17 ms →        9.08 ms  (-10.72%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        8.64 ms →        8.00 ms   (-7.46%) |      42   →      40     (-4.76%) |      362.97 ms →      319.92 ms  (-11.86%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.54 s  →        1.57 s    (+2.25%) |      21   →      20     (-4.76%) |       32.27 s  →       31.42 s    (-2.62%) | 
+ │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       55.05 ms →       47.82 ms  (-13.13%) |     361   →     363     (+0.55%) |       19.87 s  →       17.36 s   (-12.65%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       30.31 ms →       28.07 ms   (-7.39%) |     361   →     363     (+0.55%) |       10.94 s  →       10.19 s    (-6.87%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.94 μs →        1.88 μs   (-3.36%) |     361   →     363     (+0.55%) |      701.19 μs →      681.40 μs   (-2.82%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.59 μs →        1.62 μs   (+1.44%) |     361   →     363     (+0.55%) |      574.94 μs →      586.46 μs   (+2.00%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      434.51 ns →      348.61 ns  (-19.77%) |     361   →     363     (+0.55%) |      156.86 μs →      126.54 μs  (-19.33%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      534.52 ns →      516.06 ns   (-3.45%) |     361   →     363     (+0.55%) |      192.96 μs →      187.33 μs   (-2.92%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.95 ms →        2.71 ms   (-8.24%) |     361   →     363     (+0.55%) |        1.07 s  →      983.05 ms   (-7.74%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.31 ms →        3.22 ms   (-2.91%) |     361   →     363     (+0.55%) |        1.20 s  →        1.17 s    (-2.37%) | 
+ │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        9.23 ms →        6.90 ms  (-25.18%) |     722   →     726     (+0.55%) |        6.66 s  →        5.01 s   (-24.77%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |        7.05 ms →        7.08 ms   (+0.36%) |     361   →     363     (+0.55%) |        2.55 s  →        2.57 s    (+0.92%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        1.13 ms →        1.05 ms   (-7.51%) |     701   →     706     (+0.71%) |      793.75 ms →      739.38 ms   (-6.85%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       54.38 ns →       32.45 ns  (-40.33%) |     701   →     706     (+0.71%) |       38.12 μs →       22.91 μs  (-39.90%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |      968.38 μs →      883.89 μs   (-8.72%) |     701   →     706     (+0.71%) |      678.84 ms →      624.03 ms   (-8.07%) | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       52.74 ns →       56.39 ns   (+6.92%) |     701   →     706     (+0.71%) |       36.97 μs →       39.81 μs   (+7.68%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      257.55 μs →      269.43 μs   (+4.62%) |     361   →     363     (+0.55%) |       92.97 ms →       97.80 ms   (+5.20%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        2.38 ms →        2.38 ms   (-0.11%) |     361   →     363     (+0.55%) |      858.53 ms →      862.33 ms   (+0.44%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |        2.35 ms →        2.53 ms   (+7.70%) |     340   →     343     (+0.88%) |      798.78 ms →      867.89 ms   (+8.65%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |      782.30 μs →      842.69 μs   (+7.72%) |    1.02 K →    1.03 K   (+0.88%) |      797.94 ms →      867.12 ms   (+8.67%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.44 ms →        1.34 ms   (-7.04%) |     361   →     363     (+0.55%) |      521.48 ms →      487.46 ms   (-6.53%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |        1.40 ms →        1.30 ms   (-7.16%) |     361   →     363     (+0.55%) |      504.56 ms →      471.04 ms   (-6.64%) | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       50.60 ns →       53.39 ns   (+5.51%) |     361   →     363     (+0.55%) |       18.27 μs →       19.38 μs   (+6.09%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        1.23 ms →        1.13 ms   (-7.95%) |     361   →     363     (+0.55%) |      444.95 ms →      411.84 ms   (-7.44%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       48.32 ns →       54.21 ns  (+12.18%) |     361   →     363     (+0.55%) |       17.44 μs →       19.68 μs  (+12.80%) | 
- │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       21.68 ms →       26.89 ms  (+24.02%) |     361   →     363     (+0.55%) |        7.83 s  →        9.76 s   (+24.71%) | 
+ │ │ │ │   ├ sirius::residuals                                         |        2.92 ms →        2.39 ms  (-18.14%) |     346   →     347     (+0.29%) |        1.01 s  →      828.98 ms  (-17.90%) | 
+ │ │ │ │   │ ├ sddk::wf_trans                                          |        1.22 ms →        1.08 ms  (-11.54%) |     342   →     343     (+0.29%) |      418.92 ms →      371.65 ms  (-11.28%) | 
+ │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      611.04 μs →      540.43 μs  (-11.56%) |     684   →     686     (+0.29%) |      417.95 ms →      370.74 ms  (-11.30%) | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.59 ms →        1.24 ms  (-22.33%) |     342   →     343     (+0.29%) |      544.91 ms →      424.46 ms  (-22.10%) | 
+ │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        5.41 ms →        4.80 ms  (-11.26%) |      90   →      86     (-4.44%) |      486.62 ms →      412.65 ms  (-15.20%) | 
+ │ │ │ │     └ sddk::wf_trans                                          |        3.01 ms →        2.66 ms  (-11.43%) |     159   →     152     (-4.40%) |      478.36 ms →      405.03 ms  (-15.33%) | 
+ │ │ │ │       └ sddk::wf_trans|pw                                     |        2.10 ms →        1.86 ms  (-11.45%) |     228   →     218     (-4.39%) |      478.04 ms →      404.76 ms  (-15.33%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      531.62 ns →      345.20 ns  (-35.07%) |      21   →      20     (-4.76%) |       11.16 μs →        6.90 μs  (-38.16%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       20.22 μs →       19.98 μs   (-1.19%) |      21   →      20     (-4.76%) |      424.72 μs →      399.70 μs   (-5.89%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.60 ms →        1.56 ms   (-2.30%) |      21   →      20     (-4.76%) |       33.59 ms →       31.26 ms   (-6.95%) | 
  │ │ ├ sirius::Density::generate                                       |      570.21 ms →      564.01 ms   (-1.09%) |      21   →      20     (-4.76%) |       11.97 s  →       11.28 s    (-5.80%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      390.04 ms →      395.53 ms   (+1.41%) |      21   →      20     (-4.76%) |        8.19 s  →        7.91 s    (-3.42%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       10.89 μs →        8.35 μs  (-23.32%) |      21   →      20     (-4.76%) |      228.64 μs →      166.97 μs  (-26.97%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |       10.03 μs →        7.22 μs  (-28.08%) |      21   →      20     (-4.76%) |      210.66 μs →      144.30 μs  (-31.50%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       50.79 ms →       22.66 ms  (-55.39%) |      21   →      20     (-4.76%) |        1.07 s  →      453.12 ms  (-57.52%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       11.16 μs →       10.80 μs   (-3.20%) |      21   →      20     (-4.76%) |      234.32 μs →      216.02 μs   (-7.81%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        8.63 ms →        3.95 ms  (-54.24%) |      21   →      20     (-4.76%) |      181.26 ms →       78.99 ms  (-56.42%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       41.09 ms →       17.63 ms  (-57.09%) |      21   →      20     (-4.76%) |      862.79 ms →      352.59 ms  (-59.13%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |        1.14 μs →      817.05 ns  (-28.13%) |      21   →      20     (-4.76%) |       23.88 μs →       16.34 μs  (-31.56%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       94.93 ms →      122.64 ms  (+29.18%) |      21   →      20     (-4.76%) |        1.99 s  →        2.45 s   (+23.03%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.92 ms →        2.26 ms  (+17.82%) |      21   →      20     (-4.76%) |       40.32 ms →       45.24 ms  (+12.21%) | 
- │ │ │ │ └ sirius::Density::augment                                    |      198.41 ms →      222.64 ms  (+12.21%) |      21   →      20     (-4.76%) |        4.17 s  →        4.45 s    (+6.87%) | 
- │ │ │ │   └ sirius::Density::generate_rho_aug                         |      198.19 ms →      222.43 ms  (+12.23%) |      21   →      20     (-4.76%) |        4.16 s  →        4.45 s    (+6.89%) | 
+ │ │ │ ├ sirius::Field4D::symmetrize                                   |      151.50 ms →      141.14 ms   (-6.84%) |      21   →      20     (-4.76%) |        3.18 s  →        2.82 s   (-11.28%) | 
+ │ │ │ │ └ sirius::symmetrize_function|fpw                             |      151.50 ms →      141.13 ms   (-6.84%) |      21   →      20     (-4.76%) |        3.18 s  →        2.82 s   (-11.28%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       67.85 ms →       56.86 ms  (-16.20%) |      21   →      20     (-4.76%) |        1.42 s  →        1.14 s   (-20.19%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       70.37 ms →       71.01 ms   (+0.90%) |      21   →      20     (-4.76%) |        1.48 s  →        1.42 s    (-3.90%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.62 ms →       12.61 ms   (-0.06%) |      21   →      20     (-4.76%) |      264.99 ms →      252.23 ms   (-4.82%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.50 ms →       23.53 ms   (+0.11%) |      21   →      20     (-4.76%) |      493.49 ms →      470.50 ms   (-4.66%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        5.17 ms →        3.82 ms  (-26.07%) |      21   →      20     (-4.76%) |      108.48 ms →       76.37 ms  (-29.59%) | 
- │ │ ├ sirius::Density::mix                                            |      133.39 ms →      174.04 ms  (+30.47%) |      21   →      20     (-4.76%) |        2.80 s  →        3.48 s   (+24.26%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      783.87 μs →      425.70 μs  (-45.69%) |      21   →      20     (-4.76%) |       16.46 ms →        8.51 ms  (-48.28%) | 
- │ │ │ ├ sirius::Periodic_function|inner                               |        4.66 ms →        4.65 ms   (-0.19%) |     259   →     571   (+120.46%) |        1.21 s  →        2.65 s  (+120.04%) | 
- │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.61 ms →        4.59 ms   (-0.44%) |     259   →     571   (+120.46%) |        1.19 s  →        2.62 s  (+119.48%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.61 ms →        4.59 ms   (-0.44%) |     259   →     571   (+120.46%) |        1.19 s  →        2.62 s  (+119.49%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        5.60 ms →        5.19 ms   (-7.31%) |      21   →      20     (-4.76%) |      117.66 ms →      103.87 ms  (-11.72%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        4.89 ms →        4.34 ms  (-11.37%) |      21   →      20     (-4.76%) |      102.75 ms →       86.72 ms  (-15.59%) | 
  │ │ ├ sirius::Potential::generate                                     |      364.19 ms →      356.14 ms   (-2.21%) |      21   →      20     (-4.76%) |        7.65 s  →        7.12 s    (-6.87%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |       43.85 ms →       35.55 ms  (-18.92%) |      21   →      20     (-4.76%) |      920.79 ms →      711.06 ms  (-22.78%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        3.62 ms →        3.71 ms   (+2.49%) |      21   →      20     (-4.76%) |       76.07 ms →       74.26 ms   (-2.39%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |        4.64 ms →        5.90 ms  (+27.31%) |      21   →      20     (-4.76%) |       97.40 ms →      118.10 ms  (+21.25%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.62 ms →        4.64 ms   (+0.31%) |      21   →      20     (-4.76%) |       97.07 ms →       92.73 ms   (-4.47%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.62 ms →        4.64 ms   (+0.31%) |      21   →      20     (-4.76%) |       97.04 ms →       92.71 ms   (-4.46%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      775.17 μs →      805.22 μs   (+3.88%) |      42   →      40     (-4.76%) |       32.56 ms →       32.21 ms   (-1.07%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       45.32 ms →       45.13 ms   (-0.42%) |      21   →      20     (-4.76%) |      951.77 ms →      902.60 ms   (-5.17%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       44.13 ms →       43.95 ms   (-0.41%) |      21   →      20     (-4.76%) |      926.83 ms →      879.07 ms   (-5.15%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |      682.07 μs →      680.57 μs   (-0.22%) |      42   →      40     (-4.76%) |       28.65 ms →       27.22 ms   (-4.97%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.62 ms →        4.63 ms   (+0.25%) |      21   →      20     (-4.76%) |       97.01 ms →       92.62 ms   (-4.52%) | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.66 ms →        3.31 ms   (-9.71%) |      21   →      20     (-4.76%) |       76.90 ms →       66.13 ms  (-14.01%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.40 ms →      269.08 ms   (+0.25%) |      21   →      20     (-4.76%) |        5.64 s  →        5.38 s    (-4.52%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      192.57 ns →      137.40 ns  (-28.65%) |      21   →      20     (-4.76%) |        4.04 μs →        2.75 μs  (-32.05%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |       96.69 ms →       97.37 ms   (+0.71%) |      21   →      20     (-4.76%) |        2.03 s  →        1.95 s    (-4.09%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |       96.68 ms →       97.37 ms   (+0.71%) |      21   →      20     (-4.76%) |        2.03 s  →        1.95 s    (-4.09%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.29 ms →       13.28 ms   (-0.05%) |      21   →      20     (-4.76%) |      279.08 ms →      265.67 ms   (-4.81%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       70.16 ms →       70.88 ms   (+1.03%) |      21   →      20     (-4.76%) |        1.47 s  →        1.42 s    (-3.79%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.60 ms →       12.57 ms   (-0.21%) |      21   →      20     (-4.76%) |      264.62 ms →      251.49 ms   (-4.96%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        4.62 ms →        3.71 ms  (-19.58%) |      21   →      20     (-4.76%) |       96.98 ms →       74.28 ms  (-23.41%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.79 ms →        4.89 ms   (+2.25%) |     147   →     140     (-4.76%) |      703.64 ms →      685.20 ms   (-2.62%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.76 ms →        4.81 ms   (+1.03%) |     147   →     140     (-4.76%) |      699.74 ms →      673.31 ms   (-3.78%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.76 ms →        4.81 ms   (+1.03%) |     147   →     140     (-4.76%) |      699.64 ms →      673.19 ms   (-3.78%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.56 ms →        4.54 ms   (-0.37%) |      63   →      60     (-4.76%) |      287.02 ms →      272.36 ms   (-5.11%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.55 ms →        4.53 ms   (-0.31%) |      63   →      60     (-4.76%) |      286.34 ms →      271.85 ms   (-5.06%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.53 ms →        4.55 ms   (+0.33%) |      21   →      20     (-4.76%) |       95.15 ms →       90.92 ms   (-4.45%) | 
  │ │ └ sirius::Density::get_magnetisation                              |       76.12 μs →       75.78 μs   (-0.45%) |      21   →      20     (-4.76%) |        1.60 ms →        1.52 ms   (-5.19%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |       71.39 μs →       70.71 μs   (-0.96%) |      21   →      20     (-4.76%) |        1.50 ms →        1.41 ms   (-5.67%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.14 ms →        5.16 ms   (+0.43%) |       2   →       2              |       10.28 ms →       10.32 ms   (+0.43%) | 
  │ ├ sirius::Periodic_function|inner                                   |        5.08 ms →        5.00 ms   (-1.64%) |       6   →       6              |       30.50 ms →       30.00 ms   (-1.64%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        5.08 ms →        5.00 ms   (-1.66%) |       6   →       6              |       30.48 ms →       29.97 ms   (-1.66%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        5.08 ms →        4.99 ms   (-1.66%) |       6   →       6              |       30.48 ms →       29.97 ms   (-1.66%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.81 ms →        4.79 ms   (-0.40%) |       3   →       3              |       14.44 ms →       14.38 ms   (-0.40%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.80 ms →        4.79 ms   (-0.34%) |       3   →       3              |       14.41 ms →       14.37 ms   (-0.34%) | 
  ├ sirius::Periodic_function|inner                                     |        4.97 ms →        5.01 ms   (+0.66%) |       2   →       2              |        9.95 ms →       10.01 ms   (+0.66%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.97 ms →        5.00 ms   (+0.66%) |       2   →       2              |        9.94 ms →       10.01 ms   (+0.66%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.97 ms →        5.00 ms   (+0.65%) |       2   →       2              |        9.94 ms →       10.00 ms   (+0.65%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.79 ms →        4.80 ms   (+0.22%) |       1   →       1              |        4.79 ms →        4.80 ms   (+0.22%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.79 ms →        4.80 ms   (+0.22%) |       1   →       1              |        4.79 ms →        4.80 ms   (+0.22%) | 
  └ sirius::finalize                                                    |      171.57 ms →      165.44 ms   (-3.57%) |       1   →       1              |      171.57 ms →      165.44 ms   (-3.57%) | 
  ====================================================================================================================================================================================================
```
