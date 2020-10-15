# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |       71.41 s  →       70.99 s    (-0.59%) |       1   →       1              |       71.41 s  →       70.99 s    (-0.59%) | 
  ├ sirius::initialize                                                  |        2.60 s  →        2.57 s    (-1.32%) |       1   →       1              |        2.60 s  →        2.57 s    (-1.32%) | 
  ├ sirius::Simulation_context::initialize                              |        3.92 s  →        3.90 s    (-0.68%) |       1   →       1              |        3.92 s  →        3.90 s    (-0.68%) | 
  │ ├ sirius::Simulation_context::init_comm                             |      180.17 ms →      184.31 ms   (+2.30%) |       1   →       1              |      180.17 ms →      184.31 ms   (+2.30%) | 
  │ ├ sirius::Unit_cell::initialize                                     |      171.20 ms →      166.71 ms   (-2.62%) |       1   →       1              |      171.20 ms →      166.71 ms   (-2.62%) | 
  │ │ ├ sirius::Atom_type::init                                         |       76.05 ms →       74.17 ms   (-2.47%) |       2   →       2              |      152.09 ms →      148.34 ms   (-2.47%) | 
  │ │ └ sirius::Unit_cell::update                                       |       19.00 ms →       18.27 ms   (-3.85%) |       1   →       1              |       19.00 ms →       18.27 ms   (-3.85%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.90 ms →        3.69 ms   (-5.51%) |       1   →       1              |        3.90 ms →        3.69 ms   (-5.51%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       15.00 ms →       14.52 ms   (-3.21%) |       1   →       1              |       15.00 ms →       14.52 ms   (-3.21%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       14.94 ms →       14.46 ms   (-3.24%) |       1   →       1              |       14.94 ms →       14.46 ms   (-3.24%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.73 ms →        2.74 ms   (+0.33%) |       1   →       1              |        2.73 ms →        2.74 ms   (+0.33%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      497.01 μs →      502.51 μs   (+1.11%) |       1   →       1              |      497.01 μs →      502.51 μs   (+1.11%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       15.02 μs →       14.51 μs   (-3.45%) |       1   →       1              |       15.02 μs →       14.51 μs   (-3.45%) | 
  │ └ sirius::Simulation_context::update                                |        3.47 s  →        3.49 s    (+0.69%) |       1   →       1              |        3.47 s  →        3.49 s    (+0.69%) | 
  │   ├ sirius::Unit_cell::update                                       |        6.74 ms →        6.94 ms   (+2.96%) |       1   →       1              |        6.74 ms →        6.94 ms   (+2.96%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.42 ms →        3.61 ms   (+5.61%) |       1   →       1              |        3.42 ms →        3.61 ms   (+5.61%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.28 ms →        3.28 ms   (-0.00%) |       1   →       1              |        3.28 ms →        3.28 ms   (-0.00%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.24 ms →        3.24 ms   (-0.00%) |       1   →       1              |        3.24 ms →        3.24 ms   (-0.00%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.70 ms →        2.70 ms   (-0.05%) |       1   →       1              |        2.70 ms →        2.70 ms   (-0.05%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      503.34 μs →      504.48 μs   (+0.23%) |       1   →       1              |      503.34 μs →      504.48 μs   (+0.23%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       13.47 μs →       13.69 μs   (+1.56%) |       1   →       1              |       13.47 μs →       13.69 μs   (+1.56%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      213.76 ms →      212.48 ms   (-0.60%) |       2   →       2              |      427.51 ms →      424.96 ms   (-0.60%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.14 ms →       15.21 ms   (+0.44%) |       2   →       2              |       30.28 ms →       30.41 ms   (+0.44%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.24 ms →       13.28 ms   (+0.25%) |       1   →       1              |       13.24 ms →       13.28 ms   (+0.25%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.30 ms →       56.34 ms   (+0.07%) |       2   →       2              |      112.61 ms →      112.69 ms   (+0.07%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.08 ms →       45.09 ms   (+0.03%) |       2   →       2              |       90.16 ms →       90.18 ms   (+0.03%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.42 ms →       60.17 ms   (-0.40%) |       4   →       4              |      241.67 ms →      240.69 ms   (-0.40%) | 
  │   ├ sddk::Gvec::init                                                |       93.12 ms →       92.60 ms   (-0.56%) |       2   →       2              |      186.23 ms →      185.19 ms   (-0.56%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       69.54 ms →       69.16 ms   (-0.56%) |       2   →       2              |      139.09 ms →      138.31 ms   (-0.56%) | 
  │   ├ sddk::Gvec_shells                                               |       94.39 ms →       91.58 ms   (-2.98%) |       1   →       1              |       94.39 ms →       91.58 ms   (-2.98%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.96 ms →        1.93 ms   (-1.23%) |       1   →       1              |        1.96 ms →        1.93 ms   (-1.23%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      611.92 ms →      616.78 ms   (+0.79%) |       2   →       2              |        1.22 s  →        1.23 s    (+0.79%) | 
+ ├ sirius::K_point_set::create_k_mesh                                  |      143.59 ms →       89.05 ms  (-37.98%) |       1   →       1              |      143.59 ms →       89.05 ms  (-37.98%) | 
- │ ├ sirius::K_point::K_point                                          |        1.20 μs →        2.55 μs (+113.07%) |       4   →       4              |        4.79 μs →       10.20 μs (+113.07%) | 
+ │ └ sirius::K_point_set::initialize                                   |      143.50 ms →       88.97 ms  (-38.00%) |       1   →       1              |      143.50 ms →       88.97 ms  (-38.00%) | 
  │   └ sirius::K_point::initialize                                     |       28.76 ms →       28.36 ms   (-1.41%) |       1   →       1              |       28.76 ms →       28.36 ms   (-1.41%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       11.24 ms →       11.17 ms   (-0.65%) |       1   →       1              |       11.24 ms →       11.17 ms   (-0.65%) | 
  │     │ └ sddk::Gvec::init                                            |        5.01 ms →        5.05 ms   (+0.82%) |       1   →       1              |        5.01 ms →        5.05 ms   (+0.82%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |       10.61 μs →       10.46 μs   (-1.37%) |       1   →       1              |       10.61 μs →       10.46 μs   (-1.37%) | 
  │     └ sirius::K_point::update                                       |       14.75 ms →       14.32 ms   (-2.92%) |       1   →       1              |       14.75 ms →       14.32 ms   (-2.92%) | 
  │       └ sirius::Beta_projectors                                     |       10.75 ms →       10.29 ms   (-4.28%) |       1   →       1              |       10.75 ms →       10.29 ms   (-4.28%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.79 ms →        8.27 ms   (-5.97%) |       1   →       1              |        8.79 ms →        8.27 ms   (-5.97%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.55 ms →        2.56 ms   (+0.64%) |       2   →       2              |        5.09 ms →        5.13 ms   (+0.64%) | 
  ├ sirius::Potential                                                   |       50.25 ms →       54.58 ms   (+8.61%) |       1   →       1              |       50.25 ms →       54.58 ms   (+8.61%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.89 ms →        2.96 ms   (+2.48%) |       6   →       6              |       17.34 ms →       17.77 ms   (+2.48%) | 
- │ └ sirius::Potential::update                                         |       32.28 ms →       36.18 ms  (+12.10%) |       1   →       1              |       32.28 ms →       36.18 ms  (+12.10%) | 
- │   └ sirius::Potential::generate_local_potential                     |       31.89 ms →       35.79 ms  (+12.23%) |       1   →       1              |       31.89 ms →       35.79 ms  (+12.23%) | 
- │     ├ sirius::Simulation_context::make_periodic_function            |       27.16 ms →       31.41 ms  (+15.66%) |       1   →       1              |       27.16 ms →       31.41 ms  (+15.66%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        4.20 ms →        3.78 ms  (-10.02%) |       1   →       1              |        4.20 ms →        3.78 ms  (-10.02%) | 
  ├ sirius::Density                                                     |       39.55 ms →       41.64 ms   (+5.28%) |       1   →       1              |       39.55 ms →       41.64 ms   (+5.28%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.80 ms →        2.84 ms   (+1.69%) |       2   →       2              |        5.59 ms →        5.69 ms   (+1.69%) | 
  │ └ sirius::Density::update                                           |       33.82 ms →       35.81 ms   (+5.89%) |       1   →       1              |       33.82 ms →       35.81 ms   (+5.89%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       33.58 ms →       35.54 ms   (+5.83%) |       1   →       1              |       33.58 ms →       35.54 ms   (+5.83%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |       76.90 μs →       78.18 μs   (+1.66%) |       1   →       1              |       76.90 μs →       78.18 μs   (+1.66%) | 
- │     ├ sirius::Simulation_context::make_periodic_function            |       27.36 ms →       32.21 ms  (+17.73%) |       1   →       1              |       27.36 ms →       32.21 ms  (+17.73%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        5.82 ms →        2.89 ms  (-50.29%) |       1   →       1              |        5.82 ms →        2.89 ms  (-50.29%) | 
- ├ sirius::Density::initial_density                                    |       57.27 ms →       63.28 ms  (+10.51%) |       1   →       1              |       57.27 ms →       63.28 ms  (+10.51%) | 
- │ ├ sirius::Simulation_context::make_periodic_function                |       28.10 ms →       35.77 ms  (+27.30%) |       1   →       1              |       28.10 ms →       35.77 ms  (+27.30%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.56 ms →        4.49 ms  (-19.29%) |       2   →       2              |       11.12 ms →        8.98 ms  (-19.29%) | 
  │ └ sirius::Periodic_function::integrate                              |        4.50 ms →        4.85 ms   (+7.85%) |       1   →       1              |        4.50 ms →        4.85 ms   (+7.85%) | 
  ├ sirius::Potential::generate                                         |      364.20 ms →      370.74 ms   (+1.80%) |       1   →       1              |      364.20 ms →      370.74 ms   (+1.80%) | 
- │ ├ sirius::Potential::poisson                                        |       35.90 ms →       43.66 ms  (+21.61%) |       1   →       1              |       35.90 ms →       43.66 ms  (+21.61%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        4.98 ms →        2.92 ms  (-41.27%) |       1   →       1              |        4.98 ms →        2.92 ms  (-41.27%) | 
- │ │ └ sirius::Periodic_function|inner                                 |        4.63 ms →        5.43 ms  (+17.19%) |       1   →       1              |        4.63 ms →        5.43 ms  (+17.19%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.63 ms →        4.87 ms   (+5.29%) |       1   →       1              |        4.63 ms →        4.87 ms   (+5.29%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.62 ms →        4.86 ms   (+5.26%) |       1   →       1              |        4.62 ms →        4.86 ms   (+5.26%) | 
  │ ├ sirius::Periodic_function::add                                    |      775.42 μs →      803.29 μs   (+3.59%) |       2   →       2              |        1.55 ms →        1.61 ms   (+3.59%) | 
  │ ├ sirius::Potential::xc                                             |       52.89 ms →       51.16 ms   (-3.28%) |       1   →       1              |       52.89 ms →       51.16 ms   (-3.28%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.72 ms →       49.98 ms   (-3.35%) |       1   →       1              |       51.72 ms →       49.98 ms   (-3.35%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.53 ms →        2.57 ms   (+1.34%) |       2   →       2              |        5.06 ms →        5.13 ms   (+1.34%) | 
+ │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.55 ms →        3.91 ms  (-14.10%) |       1   →       1              |        4.55 ms →        3.91 ms  (-14.10%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.75 ms →        3.78 ms   (+0.61%) |       1   →       1              |        3.75 ms →        3.78 ms   (+0.61%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      268.69 ms →      269.16 ms   (+0.17%) |       1   →       1              |      268.69 ms →      269.16 ms   (+0.17%) | 
+ │ └ sirius::Potential::generate_PAW_effective_potential               |      236.00 ns →      118.00 ns  (-50.00%) |       1   →       1              |      236.00 ns →      118.00 ns  (-50.00%) | 
  ├ sirius::Hamiltonian0                                                |        6.43 ms →        6.86 ms   (+6.71%) |       1   →       1              |        6.43 ms →        6.86 ms   (+6.71%) | 
  │ ├ sirius::Local_operator                                            |        5.84 ms →        6.40 ms   (+9.62%) |       1   →       1              |        5.84 ms →        6.40 ms   (+9.62%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.75 ms →        2.78 ms   (+1.07%) |       1   →       1              |        2.75 ms →        2.78 ms   (+1.07%) | 
- │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.34 ms →        2.84 ms  (+21.34%) |       1   →       1              |        2.34 ms →        2.84 ms  (+21.34%) | 
+ │ ├ sirius::Non_local_operator                                        |      132.12 μs →       73.94 μs  (-44.04%) |       2   →       2              |      264.23 μs →      147.87 μs  (-44.04%) | 
- │ ├ sirius::D_operator::initialize                                    |      117.89 μs →      142.72 μs  (+21.05%) |       1   →       1              |      117.89 μs →      142.72 μs  (+21.05%) | 
+ │ └ sirius::Q_operator::initialize                                    |      129.91 μs →      100.98 μs  (-22.27%) |       1   →       1              |      129.91 μs →      100.98 μs  (-22.27%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.28 s  →        1.28 s    (-0.14%) |       1   →       1              |        1.28 s  →        1.28 s    (-0.14%) | 
- │ ├ sirius::Hamiltonian_k                                             |       48.88 ms →       59.79 ms  (+22.30%) |       1   →       1              |       48.88 ms →       59.79 ms  (+22.30%) | 
- │ │ ├ sirius::Local_operator::prepare_k                               |      261.20 μs →      292.07 μs  (+11.82%) |       1   →       1              |      261.20 μs →      292.07 μs  (+11.82%) | 
- │ │ └ sirius::Beta_projectors_base::prepare                           |       48.62 ms →       59.49 ms  (+22.36%) |       1   →       1              |       48.62 ms →       59.49 ms  (+22.36%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.23 s  →        1.22 s    (-1.03%) |       1   →       1              |        1.23 s  →        1.22 s    (-1.03%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       78.58 ms →       76.60 ms   (-2.52%) |       4   →       4              |      314.33 ms →      306.41 ms   (-2.52%) | 
+ │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       43.01 ms →       37.67 ms  (-12.40%) |       1   →       1              |       43.01 ms →       37.67 ms  (-12.40%) | 
+ │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        8.78 ms →        7.20 ms  (-17.98%) |       1   →       1              |        8.78 ms →        7.20 ms  (-17.98%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      315.74 ms →      336.39 ms   (+6.54%) |       1   →       1              |      315.74 ms →      336.39 ms   (+6.54%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      246.15 ms →      248.39 ms   (+0.91%) |       1   →       1              |      246.15 ms →      248.39 ms   (+0.91%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        4.60 μs →        4.02 μs  (-12.59%) |       1   →       1              |        4.60 μs →        4.02 μs  (-12.59%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.64 μs →        3.00 μs  (-17.55%) |       1   →       1              |        3.64 μs →        3.00 μs  (-17.55%) | 
- │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      449.00 ns →      535.00 ns  (+19.15%) |       1   →       1              |      449.00 ns →      535.00 ns  (+19.15%) | 
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      735.00 ns →      660.00 ns  (-10.20%) |       1   →       1              |      735.00 ns →      660.00 ns  (-10.20%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.19 ms →        3.19 ms   (-0.21%) |       1   →       1              |        3.19 ms →        3.19 ms   (-0.21%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.33 ms →       21.34 ms   (+0.04%) |       1   →       1              |       21.33 ms →       21.34 ms   (+0.04%) | 
- │ │ │ └ sirius::Non_local_operator::apply                             |       22.51 ms →       31.71 ms  (+40.90%) |       2   →       2              |       45.02 ms →       63.43 ms  (+40.90%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.91 ms →       14.70 ms   (-1.38%) |       2   →       2              |       29.81 ms →       29.40 ms   (-1.38%) | 
  │ │ │ └ sddk::wf_inner                                                |       14.69 ms →       14.48 ms   (-1.43%) |       2   →       2              |       29.39 ms →       28.97 ms   (-1.43%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       19.50 ns →       30.50 ns  (+56.41%) |       2   →       2              |       39.00 ns →       61.00 ns  (+56.41%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       14.57 ms →       14.36 ms   (-1.43%) |       2   →       2              |       29.13 ms →       28.72 ms   (-1.43%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       20.50 ns →       26.00 ns  (+26.83%) |       2   →       2              |       41.00 ns →       52.00 ns  (+26.83%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      254.59 ms →      231.25 ms   (-9.17%) |       1   →       1              |      254.59 ms →      231.25 ms   (-9.17%) | 
- │ │ └ sddk::wf_trans                                                  |        2.60 ms →        4.91 ms  (+88.73%) |       1   →       1              |        2.60 ms →        4.91 ms  (+88.73%) | 
- │ │   └ sddk::wf_trans|pw                                             |        2.60 ms →        4.90 ms  (+88.87%) |       1   →       1              |        2.60 ms →        4.90 ms  (+88.87%) | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      534.00 ns →      539.00 ns   (+0.94%) |       1   →       1              |      534.00 ns →      539.00 ns   (+0.94%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |       61.83 s  →       61.52 s    (-0.51%) |       1   →       1              |       61.83 s  →       61.52 s    (-0.51%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.45 ms →        2.46 ms   (+0.58%) |      19   →      19              |       46.51 ms →       46.78 ms   (+0.58%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.24 s  →        3.06 s    (-5.65%) |      19   →      20     (+5.26%) |       61.64 s  →       61.22 s    (-0.69%) | 
+ │ │ ├ sirius::Hamiltonian0                                            |        5.78 ms →        5.16 ms  (-10.77%) |      19   →      20     (+5.26%) |      109.81 ms →      103.14 ms   (-6.07%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.87 ms →        4.44 ms   (-8.94%) |      19   →      20     (+5.26%) |       92.55 ms →       88.70 ms   (-4.15%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      548.94 μs →      526.24 μs   (-4.13%) |      19   →      20     (+5.26%) |       10.43 ms →       10.52 ms   (+0.91%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.12 ms →        2.76 ms  (-11.39%) |      19   →      20     (+5.26%) |       59.19 ms →       55.21 ms   (-6.72%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |      313.65 μs →      219.46 μs  (-30.03%) |      38   →      40     (+5.26%) |       11.92 ms →        8.78 ms  (-26.35%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |      114.69 μs →      115.49 μs   (+0.70%) |      19   →      20     (+5.26%) |        2.18 ms →        2.31 ms   (+6.00%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       89.74 μs →       89.87 μs   (+0.14%) |      19   →      20     (+5.26%) |        1.71 ms →        1.80 ms   (+5.41%) | 
  │ │ ├ sirius::Band::solve                                             |        2.03 s  →        1.84 s    (-9.12%) |      19   →      20     (+5.26%) |       38.49 s  →       36.82 s    (-4.34%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      205.88 μs →      243.41 μs  (+18.22%) |      19   →      20     (+5.26%) |        3.91 ms →        4.87 ms  (+24.45%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      198.90 μs →      236.38 μs  (+18.84%) |      19   →      20     (+5.26%) |        3.78 ms →        4.73 ms  (+25.09%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.98 μs →        5.06 μs   (+1.73%) |      19   →      20     (+5.26%) |       94.57 μs →      101.27 μs   (+7.09%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.96 s  →        1.70 s   (-13.64%) |      19   →      20     (+5.26%) |       37.30 s  →       33.91 s    (-9.09%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       78.62 ms →       69.05 ms  (-12.17%) |      19   →      20     (+5.26%) |        1.49 s  →        1.38 s    (-7.55%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        8.23 ms →        7.79 ms   (-5.38%) |     114   →     120     (+5.26%) |      938.18 ms →      934.44 ms   (-0.40%) | 
- │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       16.02 ms →       18.34 ms  (+14.51%) |      19   →      20     (+5.26%) |      304.36 ms →      366.87 ms  (+20.54%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      486.40 μs →      456.60 μs   (-6.13%) |      19   →      20     (+5.26%) |        9.24 ms →        9.13 ms   (-1.19%) | 
- │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        7.35 ms →        8.38 ms  (+13.95%) |      38   →      40     (+5.26%) |      279.45 ms →      335.20 ms  (+19.95%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.86 s  →        1.60 s   (-14.10%) |      19   →      20     (+5.26%) |       35.36 s  →       31.97 s    (-9.58%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       55.18 ms →       50.65 ms   (-8.21%) |     356   →     351     (-1.40%) |       19.64 s  →       17.78 s    (-9.50%) | 
+ │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       34.29 ms →       29.22 ms  (-14.81%) |     356   →     351     (-1.40%) |       12.21 s  →       10.26 s   (-16.00%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.09 μs →        2.10 μs   (+0.59%) |     356   →     351     (-1.40%) |      743.41 μs →      737.28 μs   (-0.82%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.77 μs →        1.79 μs   (+0.86%) |     356   →     351     (-1.40%) |      631.37 μs →      627.82 μs   (-0.56%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      499.86 ns →      484.47 ns   (-3.08%) |     356   →     351     (-1.40%) |      177.95 μs →      170.05 μs   (-4.44%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      675.64 ns →      673.13 ns   (-0.37%) |     356   →     351     (-1.40%) |      240.53 μs →      236.27 μs   (-1.77%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.97 ms →        3.01 ms   (+1.13%) |     356   →     351     (-1.40%) |        1.06 s  →        1.06 s    (-0.29%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.48 ms →        3.40 ms   (-2.20%) |     356   →     351     (-1.40%) |        1.24 s  →        1.19 s    (-3.57%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.21 ms →        7.50 ms   (+4.09%) |     712   →     702     (-1.40%) |        5.13 s  →        5.27 s    (+2.63%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |        6.03 ms →        6.86 ms  (+13.80%) |     356   →     351     (-1.40%) |        2.15 s  →        2.41 s   (+12.20%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        1.02 ms →        1.11 ms   (+9.49%) |     693   →     682     (-1.59%) |      705.42 ms →      760.13 ms   (+7.76%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       51.25 ns →       34.28 ns  (-33.11%) |     693   →     682     (-1.59%) |       35.52 μs →       23.38 μs  (-34.17%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |      856.04 μs →      952.76 μs  (+11.30%) |     693   →     682     (-1.59%) |      593.23 ms →      649.78 ms   (+9.53%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       45.51 ns →       53.95 ns  (+18.55%) |     693   →     682     (-1.59%) |       31.54 μs →       36.79 μs  (+16.67%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      116.94 μs →      150.62 μs  (+28.80%) |     356   →     351     (-1.40%) |       41.63 ms →       52.87 ms  (+26.99%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        1.80 ms →        2.20 ms  (+22.43%) |     356   →     351     (-1.40%) |      639.43 ms →      771.86 ms  (+20.71%) | 
- │ │ │ │   │ └ sddk::wf_trans                                          |        2.25 ms →        2.48 ms  (+10.35%) |     337   →     331     (-1.78%) |      757.74 ms →      821.25 ms   (+8.38%) | 
- │ │ │ │   │   └ sddk::wf_trans|pw                                     |      748.65 μs →      826.21 μs  (+10.36%) |    1.01 K →     993     (-1.78%) |      756.88 ms →      820.43 ms   (+8.40%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.24 ms →        1.29 ms   (+4.55%) |     356   →     351     (-1.40%) |      440.14 ms →      453.69 ms   (+3.08%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |        1.16 ms →        1.24 ms   (+6.81%) |     356   →     351     (-1.40%) |      414.01 ms →      435.99 ms   (+5.31%) | 
- │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       40.11 ns →       63.63 ns  (+58.65%) |     356   →     351     (-1.40%) |       14.28 μs →       22.34 μs  (+56.42%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |      999.70 μs →        1.08 ms   (+7.93%) |     356   →     351     (-1.40%) |      355.89 ms →      378.71 ms   (+6.41%) | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       40.14 ns →       43.69 ns   (+8.86%) |     356   →     351     (-1.40%) |       14.29 μs →       15.34 μs   (+7.33%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       33.34 ms →       28.44 ms  (-14.69%) |     356   →     351     (-1.40%) |       11.87 s  →        9.98 s   (-15.89%) | 
  │ │ │ │   ├ sirius::residuals                                         |        2.62 ms →        2.70 ms   (+2.79%) |     340   →     335     (-1.47%) |      891.82 ms →      903.24 ms   (+1.28%) | 
+ │ │ │ │   │ ├ sddk::wf_trans                                          |        1.35 ms →        1.21 ms  (-10.67%) |     337   →     331     (-1.78%) |      454.92 ms →      399.13 ms  (-12.26%) | 
+ │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      673.47 μs →      601.44 μs  (-10.70%) |     674   →     662     (-1.78%) |      453.92 ms →      398.15 ms  (-12.29%) | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.18 ms →        1.43 ms  (+21.02%) |     337   →     331     (-1.78%) |      397.15 ms →      472.05 ms  (+18.86%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        6.68 ms →        5.49 ms  (-17.80%) |      54   →      80    (+48.15%) |      360.80 ms →      439.39 ms  (+21.78%) | 
- │ │ │ │     └ sddk::wf_trans                                          |        4.00 ms →        3.08 ms  (-22.93%) |      89   →     140    (+57.30%) |      356.22 ms →      431.87 ms  (+21.24%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |        2.87 ms →        2.16 ms  (-24.84%) |     124   →     200    (+61.29%) |      356.03 ms →      431.59 ms  (+21.22%) | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      378.79 ns →      354.15 ns   (-6.50%) |      19   →      20     (+5.26%) |        7.20 μs →        7.08 μs   (-1.58%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       19.16 μs →       18.64 μs   (-2.67%) |      19   →      20     (+5.26%) |      363.95 μs →      372.86 μs   (+2.45%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.51 ms →        1.59 ms   (+5.69%) |      19   →      20     (+5.26%) |       28.62 ms →       31.84 ms  (+11.25%) | 
  │ │ ├ sirius::Density::generate                                       |      564.44 ms →      563.66 ms   (-0.14%) |      19   →      20     (+5.26%) |       10.72 s  →       11.27 s    (+5.12%) | 
- │ │ │ ├ sirius::Density::generate_valence                             |      391.46 ms →      414.14 ms   (+5.79%) |      19   →      20     (+5.26%) |        7.44 s  →        8.28 s   (+11.36%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        7.36 μs →        7.18 μs   (-2.57%) |      19   →      20     (+5.26%) |      139.92 μs →      143.50 μs   (+2.56%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        6.88 μs →        6.79 μs   (-1.38%) |      19   →      20     (+5.26%) |      130.72 μs →      135.70 μs   (+3.81%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       38.51 ms →       27.25 ms  (-29.24%) |      19   →      20     (+5.26%) |      731.60 ms →      544.94 ms  (-25.51%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        6.79 μs →        5.79 μs  (-14.68%) |      19   →      20     (+5.26%) |      129.04 μs →      115.89 μs  (-10.19%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |       22.35 ms →        4.74 ms  (-78.79%) |      19   →      20     (+5.26%) |      424.69 ms →       94.80 ms  (-77.68%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       15.13 ms →       21.46 ms  (+41.81%) |      19   →      20     (+5.26%) |      287.56 ms →      429.26 ms  (+49.27%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      499.89 ns →      696.55 ns  (+39.34%) |      19   →      20     (+5.26%) |        9.50 μs →       13.93 μs  (+46.67%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      100.56 ms →      118.51 ms  (+17.86%) |      19   →      20     (+5.26%) |        1.91 s  →        2.37 s   (+24.06%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.14 ms →        2.25 ms   (+4.70%) |      19   →      20     (+5.26%) |       40.74 ms →       44.90 ms  (+10.21%) | 
- │ │ │ │ └ sirius::Density::augment                                    |      205.80 ms →      235.52 ms  (+14.44%) |      19   →      20     (+5.26%) |        3.91 s  →        4.71 s   (+20.47%) | 
- │ │ │ │   └ sirius::Density::generate_rho_aug                         |      205.57 ms →      235.29 ms  (+14.46%) |      19   →      20     (+5.26%) |        3.91 s  →        4.71 s   (+20.48%) | 
+ │ │ │ ├ sirius::Field4D::symmetrize                                   |      144.77 ms →      122.11 ms  (-15.66%) |      19   →      20     (+5.26%) |        2.75 s  →        2.44 s   (-11.22%) | 
+ │ │ │ │ └ sirius::symmetrize_function|fpw                             |      144.77 ms →      122.10 ms  (-15.66%) |      19   →      20     (+5.26%) |        2.75 s  →        2.44 s   (-11.22%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       61.03 ms →       38.40 ms  (-37.07%) |      19   →      20     (+5.26%) |        1.16 s  →      768.04 ms  (-33.76%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       70.43 ms →       70.24 ms   (-0.27%) |      19   →      20     (+5.26%) |        1.34 s  →        1.40 s    (+4.98%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.67 ms →       12.81 ms   (+1.12%) |      19   →      20     (+5.26%) |      240.67 ms →      256.19 ms   (+6.45%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.83 ms →       23.54 ms   (-1.24%) |      19   →      20     (+5.26%) |      452.77 ms →      470.71 ms   (+3.96%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        4.37 ms →        3.87 ms  (-11.42%) |      19   →      20     (+5.26%) |       83.05 ms →       77.44 ms   (-6.75%) | 
  │ │ ├ sirius::Density::mix                                            |      137.01 ms →      133.13 ms   (-2.84%) |      19   →      20     (+5.26%) |        2.60 s  →        2.66 s    (+2.28%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      307.38 μs →      300.05 μs   (-2.38%) |      19   →      20     (+5.26%) |        5.84 ms →        6.00 ms   (+2.75%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |        5.16 ms →        4.76 ms   (-7.66%) |     229   →     244     (+6.55%) |        1.18 s  →        1.16 s    (-1.61%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.82 ms →        4.62 ms   (-4.19%) |     229   →     244     (+6.55%) |        1.10 s  →        1.13 s    (+2.09%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.82 ms →        4.62 ms   (-4.19%) |     229   →     244     (+6.55%) |        1.10 s  →        1.13 s    (+2.09%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        5.37 ms →        4.44 ms  (-17.37%) |      19   →      20     (+5.26%) |      102.00 ms →       88.72 ms  (-13.02%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        4.61 ms →        3.79 ms  (-17.80%) |      19   →      20     (+5.26%) |       87.65 ms →       75.84 ms  (-13.47%) | 
  │ │ ├ sirius::Potential::generate                                     |      356.98 ms →      363.91 ms   (+1.94%) |      19   →      20     (+5.26%) |        6.78 s  →        7.28 s    (+7.31%) | 
- │ │ │ ├ sirius::Potential::poisson                                    |       36.76 ms →       43.73 ms  (+18.94%) |      19   →      20     (+5.26%) |      698.49 ms →      874.52 ms  (+25.20%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        5.48 ms →        2.90 ms  (-47.05%) |      19   →      20     (+5.26%) |      104.07 ms →       58.01 ms  (-44.26%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |        4.97 ms →        5.42 ms   (+9.16%) |      19   →      20     (+5.26%) |       94.39 ms →      108.46 ms  (+14.91%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.63 ms →        4.66 ms   (+0.67%) |      19   →      20     (+5.26%) |       87.94 ms →       93.19 ms   (+5.97%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.63 ms →        4.66 ms   (+0.66%) |      19   →      20     (+5.26%) |       87.92 ms →       93.17 ms   (+5.96%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      772.30 μs →      802.08 μs   (+3.86%) |      38   →      40     (+5.26%) |       29.35 ms →       32.08 ms   (+9.32%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       45.43 ms →       44.48 ms   (-2.11%) |      19   →      20     (+5.26%) |      863.24 ms →      889.51 ms   (+3.04%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       44.25 ms →       43.29 ms   (-2.17%) |      19   →      20     (+5.26%) |      840.83 ms →      865.88 ms   (+2.98%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |      674.40 μs →      675.63 μs   (+0.18%) |      38   →      40     (+5.26%) |       25.63 ms →       27.03 ms   (+5.46%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.96 ms →        4.04 ms  (-18.65%) |      19   →      20     (+5.26%) |       94.29 ms →       80.74 ms  (-14.37%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.73 ms →        3.83 ms   (+2.79%) |      19   →      20     (+5.26%) |       70.79 ms →       76.60 ms   (+8.21%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.09 ms →      268.83 ms   (+0.28%) |      19   →      20     (+5.26%) |        5.09 s  →        5.38 s    (+5.55%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      196.63 ns →      180.60 ns   (-8.15%) |      19   →      20     (+5.26%) |        3.74 μs →        3.61 μs   (-3.32%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |       96.43 ms →       96.81 ms   (+0.40%) |      19   →      20     (+5.26%) |        1.83 s  →        1.94 s    (+5.69%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |       96.43 ms →       96.81 ms   (+0.40%) |      19   →      20     (+5.26%) |        1.83 s  →        1.94 s    (+5.69%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.28 ms →       13.40 ms   (+0.92%) |      19   →      20     (+5.26%) |      252.23 ms →      267.95 ms   (+6.23%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       69.94 ms →       70.21 ms   (+0.38%) |      19   →      20     (+5.26%) |        1.33 s  →        1.40 s    (+5.66%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.58 ms →       12.58 ms   (+0.01%) |      19   →      20     (+5.26%) |      239.04 ms →      251.66 ms   (+5.28%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        4.52 ms →        3.39 ms  (-25.09%) |      19   →      20     (+5.26%) |       85.86 ms →       67.70 ms  (-21.15%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.58 ms →        4.73 ms   (+3.20%) |     133   →     140     (+5.26%) |      609.32 ms →      661.90 ms   (+8.63%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.56 ms →        4.55 ms   (-0.22%) |     133   →     140     (+5.26%) |      606.10 ms →      636.57 ms   (+5.03%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.56 ms →        4.55 ms   (-0.22%) |     133   →     140     (+5.26%) |      606.02 ms →      636.49 ms   (+5.03%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.94 ms →        4.72 ms   (-4.44%) |      57   →      60     (+5.26%) |      281.63 ms →      283.28 ms   (+0.59%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.93 ms →        4.71 ms   (-4.42%) |      57   →      60     (+5.26%) |      281.19 ms →      282.89 ms   (+0.61%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.53 ms →        4.52 ms   (-0.24%) |      19   →      20     (+5.26%) |       86.02 ms →       90.32 ms   (+5.01%) | 
  │ │ └ sirius::Density::get_magnetisation                              |       75.59 μs →       74.57 μs   (-1.34%) |      19   →      20     (+5.26%) |        1.44 ms →        1.49 ms   (+3.85%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |       71.68 μs →       70.59 μs   (-1.52%) |      19   →      20     (+5.26%) |        1.36 ms →        1.41 ms   (+3.67%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.48 ms →        5.27 ms   (-3.76%) |       2   →       2              |       10.96 ms →       10.54 ms   (-3.76%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.56 ms →        4.52 ms   (-0.84%) |       6   →       6              |       27.37 ms →       27.14 ms   (-0.84%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.54 ms →        4.52 ms   (-0.48%) |       6   →       6              |       27.23 ms →       27.10 ms   (-0.48%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.54 ms →        4.52 ms   (-0.44%) |       6   →       6              |       27.22 ms →       27.10 ms   (-0.44%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.97 ms →        4.72 ms   (-5.03%) |       3   →       3              |       14.91 ms →       14.16 ms   (-5.03%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.96 ms →        4.72 ms   (-4.99%) |       3   →       3              |       14.89 ms →       14.15 ms   (-4.99%) | 
  ├ sirius::Periodic_function|inner                                     |        4.81 ms →        4.79 ms   (-0.39%) |       2   →       2              |        9.62 ms →        9.58 ms   (-0.39%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.80 ms →        4.79 ms   (-0.38%) |       2   →       2              |        9.61 ms →        9.57 ms   (-0.38%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.80 ms →        4.79 ms   (-0.37%) |       2   →       2              |        9.61 ms →        9.57 ms   (-0.37%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        5.17 ms →        5.00 ms   (-3.16%) |       1   →       1              |        5.17 ms →        5.00 ms   (-3.16%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        5.16 ms →        5.00 ms   (-3.14%) |       1   →       1              |        5.16 ms →        5.00 ms   (-3.14%) | 
- └ sirius::finalize                                                    |      141.21 ms →      156.94 ms  (+11.14%) |       1   →       1              |      141.21 ms →      156.94 ms  (+11.14%) | 
  ====================================================================================================================================================================================================
```
