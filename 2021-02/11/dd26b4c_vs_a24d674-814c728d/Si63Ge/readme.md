# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs dd26b4c3a8b510264c2723458c0ccaf5eeca6037
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |       77.38 s  →       48.68 s   (-37.09%) |       1   →       1              |       77.38 s  →       48.68 s   (-37.09%) | 
  ├ sirius::initialize                                                  |        2.99 s  →        2.85 s    (-4.76%) |       1   →       1              |        2.99 s  →        2.85 s    (-4.76%) | 
  ├ sirius::Simulation_context::initialize                              |        3.82 s  →        4.00 s    (+4.79%) |       1   →       1              |        3.82 s  →        4.00 s    (+4.79%) | 
- │ ├ sirius::Simulation_context::init_comm                             |       21.75 ms →       80.09 ms (+268.26%) |       1   →       1              |       21.75 ms →       80.09 ms (+268.26%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      233.63 ms →      169.95 ms  (-27.25%) |       1   →       1              |      233.63 ms →      169.95 ms  (-27.25%) | 
+ │ │ ├ sirius::Atom_type::init                                         |      109.27 ms →       76.22 ms  (-30.25%) |       2   →       2              |      218.53 ms →      152.43 ms  (-30.25%) | 
- │ │ └ sirius::Unit_cell::update                                       |       15.01 ms →       17.37 ms  (+15.78%) |       1   →       1              |       15.01 ms →       17.37 ms  (+15.78%) | 
- │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.61 ms →        3.98 ms  (+10.29%) |       1   →       1              |        3.61 ms →        3.98 ms  (+10.29%) | 
- │ │   └ sirius::Unit_cell::get_symmetry                               |       11.32 ms →       13.33 ms  (+17.79%) |       1   →       1              |       11.32 ms →       13.33 ms  (+17.79%) | 
- │ │     └ sirius::Unit_cell_symmetry                                  |       11.25 ms →       13.25 ms  (+17.86%) |       1   →       1              |       11.25 ms →       13.25 ms  (+17.86%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.77 ms →        2.75 ms   (-1.00%) |       1   →       1              |        2.77 ms →        2.75 ms   (-1.00%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      491.89 μs →      494.74 μs   (+0.58%) |       1   →       1              |      491.89 μs →      494.74 μs   (+0.58%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       16.06 μs →       16.29 μs   (+1.44%) |       1   →       1              |       16.06 μs →       16.29 μs   (+1.44%) | 
- │ └ sirius::Simulation_context::update                                |        3.36 s  →        3.70 s   (+10.05%) |       1   →       1              |        3.36 s  →        3.70 s   (+10.05%) | 
  │   ├ sirius::Unit_cell::update                                       |        6.83 ms →        6.95 ms   (+1.72%) |       1   →       1              |        6.83 ms →        6.95 ms   (+1.72%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.48 ms →        3.61 ms   (+3.54%) |       1   →       1              |        3.48 ms →        3.61 ms   (+3.54%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.30 ms →        3.28 ms   (-0.72%) |       1   →       1              |        3.30 ms →        3.28 ms   (-0.72%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.24 ms →        3.23 ms   (-0.24%) |       1   →       1              |        3.24 ms →        3.23 ms   (-0.24%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.69 ms →        2.70 ms   (+0.11%) |       1   →       1              |        2.69 ms →        2.70 ms   (+0.11%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      505.65 μs →      498.39 μs   (-1.44%) |       1   →       1              |      505.65 μs →      498.39 μs   (-1.44%) | 
+ │   │     └ sirius::Unit_cell_symmetry|mag                            |       17.75 μs →       14.12 μs  (-20.47%) |       1   →       1              |       17.75 μs →       14.12 μs  (-20.47%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      221.04 ms →      214.04 ms   (-3.17%) |       2   →       2              |      442.09 ms →      428.09 ms   (-3.17%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.15 ms →       15.18 ms   (+0.25%) |       2   →       2              |       30.29 ms →       30.37 ms   (+0.25%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.28 ms →       13.57 ms   (+2.12%) |       1   →       1              |       13.28 ms →       13.57 ms   (+2.12%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.34 ms →       56.31 ms   (-0.06%) |       2   →       2              |      112.69 ms →      112.62 ms   (-0.06%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       44.95 ms →       44.95 ms   (+0.00%) |       2   →       2              |       89.90 ms →       89.90 ms   (+0.00%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.14 ms →       60.08 ms   (-0.09%) |       4   →       4              |      240.56 ms →      240.34 ms   (-0.09%) | 
  │   ├ sddk::Gvec::init                                                |       97.47 ms →       94.48 ms   (-3.06%) |       2   →       2              |      194.94 ms →      188.96 ms   (-3.06%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       71.32 ms →       70.96 ms   (-0.51%) |       2   →       2              |      142.64 ms →      141.91 ms   (-0.51%) | 
+ │   ├ sddk::Gvec_shells                                               |      104.81 ms →       92.16 ms  (-12.07%) |       1   →       1              |      104.81 ms →       92.16 ms  (-12.07%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.97 ms →        1.97 ms   (-0.25%) |       1   →       1              |        1.97 ms →        1.97 ms   (-0.25%) | 
- │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      511.38 ms →      712.45 ms  (+39.32%) |       2   →       2              |        1.02 s  →        1.42 s   (+39.32%) | 
+ ├ sirius::K_point_set::create_k_mesh                                  |      144.82 ms →       28.93 ms  (-80.03%) |       1   →       1              |      144.82 ms →       28.93 ms  (-80.03%) | 
- │ ├ sirius::K_point::K_point                                          |        1.06 μs →        4.82 μs (+354.64%) |       4   →       4              |        4.24 μs →       19.26 μs (+354.64%) | 
+ │ └ sirius::K_point_set::initialize                                   |      144.75 ms →       28.83 ms  (-80.08%) |       1   →       1              |      144.75 ms →       28.83 ms  (-80.08%) | 
  │   └ sirius::K_point::initialize                                     |       30.67 ms →       28.56 ms   (-6.88%) |       1   →       1              |       30.67 ms →       28.56 ms   (-6.88%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       12.22 ms →       11.00 ms   (-9.97%) |       1   →       1              |       12.22 ms →       11.00 ms   (-9.97%) | 
  │     │ └ sddk::Gvec::init                                            |        5.44 ms →        4.94 ms   (-9.13%) |       1   →       1              |        5.44 ms →        4.94 ms   (-9.13%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |       10.56 μs →        9.75 μs   (-7.70%) |       1   →       1              |       10.56 μs →        9.75 μs   (-7.70%) | 
  │     └ sirius::K_point::update                                       |       15.19 ms →       14.70 ms   (-3.21%) |       1   →       1              |       15.19 ms →       14.70 ms   (-3.21%) | 
  │       └ sirius::Beta_projectors                                     |       10.68 ms →       10.79 ms   (+1.03%) |       1   →       1              |       10.68 ms →       10.79 ms   (+1.03%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.70 ms →        8.93 ms   (+2.60%) |       1   →       1              |        8.70 ms →        8.93 ms   (+2.60%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.56 ms →        2.55 ms   (-0.24%) |       2   →       2              |        5.12 ms →        5.11 ms   (-0.24%) | 
  ├ sirius::Potential                                                   |       49.38 ms →       49.29 ms   (-0.17%) |       1   →       1              |       49.38 ms →       49.29 ms   (-0.17%) | 
+ │ ├ sirius::Smooth_periodic_function                                  |        2.90 ms →        2.89 ms   (-0.27%) |       6   →       5    (-16.67%) |       17.41 ms →       14.47 ms  (-16.89%) | 
  │ └ sirius::Potential::update                                         |       31.40 ms →       34.27 ms   (+9.14%) |       1   →       1              |       31.40 ms →       34.27 ms   (+9.14%) | 
  │   └ sirius::Potential::generate_local_potential                     |       31.00 ms →       33.86 ms   (+9.24%) |       1   →       1              |       31.00 ms →       33.86 ms   (+9.24%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       26.41 ms →       26.64 ms   (+0.89%) |       1   →       1              |       26.41 ms →       26.64 ms   (+0.89%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        4.25 ms →        4.23 ms   (-0.45%) |       1   →       1              |        4.25 ms →        4.23 ms   (-0.45%) | 
  ├ sirius::Density                                                     |       40.14 ms →       36.79 ms   (-8.35%) |       1   →       1              |       40.14 ms →       36.79 ms   (-8.35%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.82 ms →        2.83 ms   (+0.30%) |       2   →       2              |        5.64 ms →        5.66 ms   (+0.30%) | 
  │ └ sirius::Density::update                                           |       34.34 ms →       30.97 ms   (-9.81%) |       1   →       1              |       34.34 ms →       30.97 ms   (-9.81%) | 
+ │   └ sirius::Density::generate_pseudo_core_charge_density            |       34.13 ms →       30.68 ms  (-10.10%) |       1   →       1              |       34.13 ms →       30.68 ms  (-10.10%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |                        88.61 μs            |                   1              |                        88.61 μs            | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       30.21 ms →       26.91 ms  (-10.93%) |       1   →       1              |       30.21 ms →       26.91 ms  (-10.93%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        3.56 ms →        3.31 ms   (-7.14%) |       1   →       1              |        3.56 ms →        3.31 ms   (-7.14%) | 
  ├ sirius::Density::initial_density                                    |       58.04 ms →       55.19 ms   (-4.91%) |       1   →       1              |       58.04 ms →       55.19 ms   (-4.91%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       30.35 ms →       27.77 ms   (-8.51%) |       1   →       1              |       30.35 ms →       27.77 ms   (-8.51%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.34 ms →        4.63 ms   (+6.62%) |       2   →       2              |        8.68 ms →        9.25 ms   (+6.62%) | 
+ │ └ sirius::Periodic_function::integrate                              |        5.37 ms →        4.50 ms  (-16.18%) |       1   →       1              |        5.37 ms →        4.50 ms  (-16.18%) | 
  ├ sirius::Potential::generate                                         |      364.53 ms →      348.71 ms   (-4.34%) |       1   →       1              |      364.53 ms →      348.71 ms   (-4.34%) | 
  │ ├ sirius::Potential::poisson                                        |       38.73 ms →       35.29 ms   (-8.90%) |       1   →       1              |       38.73 ms →       35.29 ms   (-8.90%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.29 ms →        3.77 ms  (+14.50%) |       1   →       1              |        3.29 ms →        3.77 ms  (+14.50%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        5.12 ms →        5.13 ms   (+0.20%) |       1   →       1              |        5.12 ms →        5.13 ms   (+0.20%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.83 ms →        4.87 ms   (+0.86%) |       1   →       1              |        4.83 ms →        4.87 ms   (+0.86%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.82 ms →        4.87 ms   (+0.87%) |       1   →       1              |        4.82 ms →        4.87 ms   (+0.87%) | 
  │ ├ sirius::Periodic_function::add                                    |      783.73 μs →      749.16 μs   (-4.41%) |       2   →       2              |        1.57 ms →        1.50 ms   (-4.41%) | 
+ │ ├ sirius::Potential::xc                                             |       50.11 ms →       37.67 ms  (-24.82%) |       1   →       1              |       50.11 ms →       37.67 ms  (-24.82%) | 
+ │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       50.10 ms →       36.45 ms  (-27.24%) |       1   →       1              |       50.10 ms →       36.45 ms  (-27.24%) | 
+ │ │   ├ sirius::Smooth_periodic_function                              |        2.55 ms →        2.20 ms  (-13.80%) |       2   →       1    (-50.00%) |        5.11 ms →        2.20 ms  (-56.90%) | 
  │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        4.60 ms                             |       1                          |        4.60 ms                             | 
  │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                    |                        14.08 ms            |                   2              |                        28.17 ms            | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.80 ms →        3.85 ms   (+1.25%) |       1   →       1              |        3.80 ms →        3.85 ms   (+1.25%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      268.93 ms →      268.96 ms   (+0.01%) |       1   →       1              |      268.93 ms →      268.96 ms   (+0.01%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      134.00 ns →      147.00 ns   (+9.70%) |       1   →       1              |      134.00 ns →      147.00 ns   (+9.70%) | 
- ├ sirius::Hamiltonian0                                                |        8.49 ms →       12.86 ms  (+51.36%) |       1   →       1              |        8.49 ms →       12.86 ms  (+51.36%) | 
+ │ ├ sirius::Local_operator                                            |        7.35 ms →        5.87 ms  (-20.17%) |       1   →       1              |        7.35 ms →        5.87 ms  (-20.17%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.74 ms →        2.75 ms   (+0.46%) |       1   →       1              |        2.74 ms →        2.75 ms   (+0.46%) | 
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        3.63 ms →        2.35 ms  (-35.32%) |       1   →       1              |        3.63 ms →        2.35 ms  (-35.32%) | 
+ │ ├ sirius::Non_local_operator                                        |      435.15 μs →       66.91 μs  (-84.62%) |       2   →       2              |      870.30 μs →      133.82 μs  (-84.62%) | 
- │ ├ sirius::D_operator::initialize                                    |      109.27 μs →        2.30 ms (+2000.38%) |       1   →       1              |      109.27 μs →        2.30 ms (+2000.38%) | 
- │ └ sirius::Q_operator::initialize                                    |       93.93 μs →        4.48 ms (+4673.55%) |       1   →       1              |       93.93 μs →        4.48 ms (+4673.55%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.30 s  →        1.26 s    (-2.61%) |       1   →       1              |        1.30 s  →        1.26 s    (-2.61%) | 
+ │ ├ sirius::Hamiltonian_k                                             |       58.80 ms →       49.50 ms  (-15.82%) |       1   →       1              |       58.80 ms →       49.50 ms  (-15.82%) | 
- │ │ ├ sirius::Local_operator::prepare_k                               |      217.41 μs →      256.37 μs  (+17.92%) |       1   →       1              |      217.41 μs →      256.37 μs  (+17.92%) | 
+ │ │ └ sirius::Beta_projectors_base::prepare                           |       58.58 ms →       49.24 ms  (-15.95%) |       1   →       1              |       58.58 ms →       49.24 ms  (-15.95%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.24 s  →        1.21 s    (-2.08%) |       1   →       1              |        1.24 s  →        1.21 s    (-2.08%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       78.92 ms →       77.01 ms   (-2.41%) |       4   →       4              |      315.66 ms →      308.05 ms   (-2.41%) | 
+ │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       47.79 ms →       37.06 ms  (-22.46%) |       1   →       1              |       47.79 ms →       37.06 ms  (-22.46%) | 
+ │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        8.00 ms →        6.80 ms  (-15.01%) |       1   →       1              |        8.00 ms →        6.80 ms  (-15.01%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      315.14 ms →      334.88 ms   (+6.26%) |       1   →       1              |      315.14 ms →      334.88 ms   (+6.26%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      245.06 ms →      246.56 ms   (+0.61%) |       1   →       1              |      245.06 ms →      246.56 ms   (+0.61%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        4.17 μs →        3.21 μs  (-23.04%) |       1   →       1              |        4.17 μs →        3.21 μs  (-23.04%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.05 μs →        2.36 μs  (-22.82%) |       1   →       1              |        3.05 μs →        2.36 μs  (-22.82%) | 
- │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      406.00 ns →      484.00 ns  (+19.21%) |       1   →       1              |      406.00 ns →      484.00 ns  (+19.21%) | 
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      678.00 ns →      549.00 ns  (-19.03%) |       1   →       1              |      678.00 ns →      549.00 ns  (-19.03%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.15 ms →        3.20 ms   (+1.54%) |       1   →       1              |        3.15 ms →        3.20 ms   (+1.54%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.29 ms →       21.29 ms   (+0.02%) |       1   →       1              |       21.29 ms →       21.29 ms   (+0.02%) | 
- │ │ │ └ sirius::Non_local_operator::apply                             |       22.80 ms →       31.89 ms  (+39.89%) |       2   →       2              |       45.59 ms →       63.78 ms  (+39.89%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.71 ms →       14.85 ms   (+0.95%) |       2   →       2              |       29.42 ms →       29.69 ms   (+0.95%) | 
  │ │ │ ├ sddk::inner                                                   |       14.50 ms                             |       2                          |       28.99 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       25.52 μs                             |       2                          |       51.05 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        14.63 ms            |                   2              |                        29.27 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                       106.00 ns            |                   2              |                       212.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        14.51 ms            |                   2              |                        29.01 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                       427.50 ns            |                   2              |                       855.00 ns            | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      250.36 ms →      229.08 ms   (-8.50%) |       1   →       1              |      250.36 ms →      229.08 ms   (-8.50%) | 
  │ │ ├ sddk::transform                                                 |        5.23 ms                             |       1                          |        5.23 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       14.10 μs                             |       1                          |       14.10 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       18.18 μs                             |       1                          |       18.18 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                         2.60 ms            |                   1              |                         2.60 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                         2.60 ms            |                   1              |                         2.60 ms            | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      608.00 ns →      412.00 ns  (-32.24%) |       1   →       1              |      608.00 ns →      412.00 ns  (-32.24%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |       67.27 s  →       38.91 s   (-42.15%) |       1   →       1              |       67.27 s  →       38.91 s   (-42.15%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.43 ms →        2.63 ms   (+8.27%) |      19   →      18     (-5.26%) |       46.12 ms →       47.31 ms   (+2.57%) | 
  │ ├ sirius::Density                                                   |                        50.72 ms            |                   1              |                        50.72 ms            | 
  │ │ ├ sirius::Smooth_periodic_function                                |                         2.79 ms            |                   2              |                         5.58 ms            | 
  │ │ └ sirius::Density::update                                         |                        44.98 ms            |                   1              |                        44.98 ms            | 
  │ │   └ sirius::Density::generate_pseudo_core_charge_density          |                        44.75 ms            |                   1              |                        44.75 ms            | 
  │ │     ├ sirius::rho_core_ri_pseudo|values                           |                        91.85 μs            |                   1              |                        91.85 μs            | 
  │ │     ├ sirius::Simulation_context::make_periodic_function          |                        27.01 ms            |                   1              |                        27.01 ms            | 
  │ │     └ sirius::Smooth_periodic_function::fft_transform             |                        17.31 ms            |                   1              |                        17.31 ms            | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.35 s  →        2.56 s   (-23.44%) |      20   →      15    (-25.00%) |       66.96 s  →       38.45 s   (-42.58%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        5.80 ms →       11.30 ms  (+94.76%) |      20   →      15    (-25.00%) |      116.07 ms →      169.54 ms  (+46.07%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        5.05 ms →        4.37 ms  (-13.46%) |      20   →      15    (-25.00%) |      100.99 ms →       65.55 ms  (-35.09%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function                            |      529.10 μs →      512.14 μs   (-3.20%) |      20   →      15    (-25.00%) |       10.58 ms →        7.68 ms  (-27.40%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.17 ms →        2.80 ms  (-11.92%) |      20   →      15    (-25.00%) |       63.50 ms →       41.95 ms  (-33.94%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |      233.38 μs →       98.65 μs  (-57.73%) |      40   →      30    (-25.00%) |        9.34 ms →        2.96 ms  (-68.30%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |      115.52 μs →        2.28 ms (+1872.84%) |      20   →      15    (-25.00%) |        2.31 ms →       34.19 ms (+1379.63%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       95.25 μs →        4.39 ms (+4510.48%) |      20   →      15    (-25.00%) |        1.90 ms →       65.87 ms (+3357.86%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.12 s  →        1.30 s   (-38.78%) |      20   →      15    (-25.00%) |       42.38 s  →       19.46 s   (-54.08%) | 
+ │ │ │ ├ sirius::Hamiltonian_k                                         |      201.59 μs →      192.51 μs   (-4.50%) |      20   →      15    (-25.00%) |        4.03 ms →        2.89 ms  (-28.38%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      191.46 μs →      181.57 μs   (-5.17%) |      20   →      15    (-25.00%) |        3.83 ms →        2.72 ms  (-28.87%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        7.91 μs →        6.65 μs  (-15.95%) |      20   →      15    (-25.00%) |      158.28 μs →       99.78 μs  (-36.96%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.97 s  →        1.13 s   (-42.64%) |      20   →      15    (-25.00%) |       39.46 s  →       16.98 s   (-56.98%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       97.85 ms →       90.15 ms   (-7.86%) |      20   →      15    (-25.00%) |        1.96 s  →        1.35 s   (-30.90%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |       11.80 ms →       10.06 ms  (-14.71%) |     120   →      90    (-25.00%) |        1.42 s  →      905.46 ms  (-36.03%) | 
- │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       15.42 ms →       18.69 ms  (+21.26%) |      20   →      15    (-25.00%) |      308.32 ms →      280.40 ms   (-9.05%) | 
+ │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      489.55 μs →      462.36 μs   (-5.55%) |      20   →      15    (-25.00%) |        9.79 ms →        6.94 ms  (-29.17%) | 
- │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        7.28 ms →        8.42 ms  (+15.65%) |      40   →      30    (-25.00%) |      291.39 ms →      252.74 ms  (-13.26%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.85 s  →        1.01 s   (-45.29%) |      20   →      15    (-25.00%) |       37.05 s  →       15.20 s   (-58.97%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       72.42 ms →       84.30 ms  (+16.40%) |     250   →     116    (-53.60%) |       18.11 s  →        9.78 s   (-45.99%) | 
+ │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       50.25 ms →       49.58 ms   (-1.33%) |     250   →     116    (-53.60%) |       12.56 s  →        5.75 s   (-54.22%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.11 μs →        1.80 μs  (-14.50%) |     250   →     116    (-53.60%) |      527.38 μs →      209.21 μs  (-60.33%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.79 μs →        1.51 μs  (-15.71%) |     250   →     116    (-53.60%) |      446.83 μs →      174.76 μs  (-60.89%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      505.83 ns →      443.63 ns  (-12.30%) |     250   →     116    (-53.60%) |      126.46 μs →       51.46 μs  (-59.31%) | 
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      686.86 ns →      455.97 ns  (-33.61%) |     250   →     116    (-53.60%) |      171.72 μs →       52.89 μs  (-69.20%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        3.07 ms →        3.05 ms   (-0.93%) |     250   →     116    (-53.60%) |      768.56 ms →      353.31 ms  (-54.03%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.77 ms →        4.71 ms  (+25.18%) |     250   →     116    (-53.60%) |      941.26 ms →      546.70 ms  (-41.92%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.66 ms →       13.47 ms  (+75.88%) |     500   →     232    (-53.60%) |        3.83 s  →        3.12 s   (-18.39%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |        6.54 ms →       10.60 ms  (+62.14%) |     250   →     116    (-53.60%) |        1.64 s  →        1.23 s   (-24.77%) | 
  │ │ │ │   │ ├ sddk::inner                                             |      867.88 μs                             |     480                          |      416.58 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       26.26 μs                             |     480                          |       12.60 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                         1.68 ms            |                 217              |                       363.50 ms            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                        89.11 ns            |                 217              |                        19.34 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                         1.51 ms            |                 217              |                       327.82 ms            | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                       209.13 ns            |                 217              |                        45.38 μs            | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      321.17 μs →      494.31 μs  (+53.91%) |     250   →     116    (-53.60%) |       80.29 ms →       57.34 ms  (-28.59%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        2.04 ms →        4.07 ms  (+99.27%) |     250   →     116    (-53.60%) |      510.38 ms →      471.91 ms   (-7.54%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        2.72 ms                             |     230                          |      626.43 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       21.63 μs                             |     230                          |        4.98 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |        9.10 μs                             |     690                          |        6.28 ms                             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                         3.33 ms            |                 101              |                       336.74 ms            | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                         1.11 ms            |                 303              |                       336.52 ms            | 
- │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.66 ms →        2.01 ms  (+21.14%) |     250   →     116    (-53.60%) |      415.09 ms →      233.32 ms  (-43.79%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        1.45 ms                             |     250                          |      362.64 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       27.56 μs                             |     250                          |        6.89 ms                             | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                         1.95 ms            |                 116              |                       226.13 ms            | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                       114.44 ns            |                 116              |                        13.28 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                         1.79 ms            |                 116              |                       207.10 ms            | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                       157.27 ns            |                 116              |                        18.24 μs            | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       63.96 ms →       28.92 ms  (-54.78%) |     250   →     116    (-53.60%) |       15.99 s  →        3.35 s   (-79.02%) | 
- │ │ │ │   ├ sirius::residuals                                         |        2.95 ms →        3.37 ms  (+14.33%) |     245   →     114    (-53.47%) |      721.98 ms →      384.08 ms  (-46.80%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        1.93 ms                             |     231                          |      445.92 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       18.41 μs                             |     231                          |        4.25 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       12.04 μs                             |     462                          |        5.56 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                         1.73 ms            |                 101              |                       174.35 ms            | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                       861.77 μs            |                 202              |                       174.08 ms            | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.12 ms →        1.84 ms  (+63.95%) |     231   →     101    (-56.28%) |      258.64 ms →      185.40 ms  (-28.32%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        7.15 ms →        4.58 ms  (-35.90%) |      25   →      47    (+88.00%) |      178.81 ms →      215.47 ms  (+20.50%) | 
  │ │ │ │     ├ sddk::transform                                         |        5.87 ms                             |      30                          |      176.18 ms                             | 
  │ │ │ │     │ ├ sddk::transform|init                                  |       11.92 μs                             |      30                          |      357.59 μs                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       12.84 μs                             |      35                          |      449.28 μs                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                         2.66 ms            |                  79              |                       210.35 ms            | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                         1.89 ms            |                 111              |                       210.20 ms            | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      392.35 ns →      359.20 ns   (-8.45%) |      20   →      15    (-25.00%) |        7.85 μs →        5.39 μs  (-31.34%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       21.57 μs →      876.30 μs (+3962.94%) |      20   →      15    (-25.00%) |      431.36 μs →       13.14 ms (+2947.21%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.53 ms →       64.71 ms (+4139.19%) |      20   →      15    (-25.00%) |       30.53 ms →      970.60 ms (+3079.39%) | 
+ │ │ ├ sirius::Density::generate                                       |      569.87 ms →      571.65 ms   (+0.31%) |      20   →      15    (-25.00%) |       11.40 s  →        8.57 s   (-24.77%) | 
+ │ │ │ ├ sirius::Density::generate_valence                             |      423.22 ms →      419.78 ms   (-0.81%) |      20   →      15    (-25.00%) |        8.46 s  →        6.30 s   (-25.61%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        7.52 μs →        8.16 μs   (+8.46%) |      20   →      15    (-25.00%) |      150.48 μs →      122.40 μs  (-18.66%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        6.99 μs →        7.15 μs   (+2.29%) |      20   →      15    (-25.00%) |      139.73 μs →      107.20 μs  (-23.28%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       39.98 ms →       61.10 ms  (+52.84%) |      20   →      15    (-25.00%) |      799.58 ms →      916.57 ms  (+14.63%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.59 μs →        8.69 μs  (+14.51%) |      20   →      15    (-25.00%) |      151.79 μs →      130.36 μs  (-14.11%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |       22.64 ms →        6.35 ms  (-71.93%) |      20   →      15    (-25.00%) |      452.72 ms →       95.31 ms  (-78.95%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       16.32 ms →       33.04 ms (+102.47%) |      20   →      15    (-25.00%) |      326.34 ms →      495.54 ms  (+51.85%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      637.85 ns →      719.33 ns  (+12.77%) |      20   →      15    (-25.00%) |       12.76 μs →       10.79 μs  (-15.42%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       98.90 ms →       81.25 ms  (-17.85%) |      20   →      15    (-25.00%) |        1.98 s  →        1.22 s   (-38.39%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.33 ms →        2.11 ms   (-9.38%) |      20   →      15    (-25.00%) |       46.60 ms →       31.67 ms  (-32.03%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |      236.30 ms →      222.26 ms   (-5.94%) |      20   →      15    (-25.00%) |        4.73 s  →        3.33 s   (-29.46%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |      236.09 ms →      222.04 ms   (-5.95%) |      20   →      15    (-25.00%) |        4.72 s  →        3.33 s   (-29.46%) | 
+ │ │ │ ├ sirius::Field4D::symmetrize                                   |      118.31 ms →      123.91 ms   (+4.73%) |      20   →      15    (-25.00%) |        2.37 s  →        1.86 s   (-21.45%) | 
+ │ │ │ │ └ sirius::symmetrize_function|fpw                             |      118.31 ms →      123.90 ms   (+4.73%) |      20   →      15    (-25.00%) |        2.37 s  →        1.86 s   (-21.46%) | 
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       33.99 ms →       44.01 ms  (+29.46%) |      20   →      15    (-25.00%) |      679.88 ms →      660.14 ms   (-2.90%) | 
+ │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       68.90 ms →       66.33 ms   (-3.73%) |      20   →      15    (-25.00%) |        1.38 s  →      994.96 ms  (-27.80%) | 
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       14.77 ms →       12.90 ms  (-12.67%) |      20   →      15    (-25.00%) |      295.47 ms →      193.53 ms  (-34.50%) | 
+ │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.69 ms →       23.69 ms   (+0.01%) |      20   →      15    (-25.00%) |      473.72 ms →      355.31 ms  (-25.00%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        4.65 ms →        4.26 ms   (-8.38%) |      20   →      15    (-25.00%) |       93.02 ms →       63.92 ms  (-31.29%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |                         4.91 ms            |                 135              |                       662.59 ms            | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |                         4.76 ms            |                 135              |                       643.16 ms            | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |                         4.76 ms            |                 135              |                       643.07 ms            | 
+ │ │ ├ sirius::Density::mix                                            |      137.65 ms →       74.76 ms  (-45.69%) |      20   →      15    (-25.00%) |        2.75 s  →        1.12 s   (-59.27%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      904.27 μs →        1.02 ms  (+13.16%) |      20   →      15    (-25.00%) |       18.09 ms →       15.35 ms  (-15.13%) | 
+ │ │ │ ├ sirius::Periodic_function|inner                               |        5.04 ms →        4.55 ms   (-9.65%) |     244   →     169    (-30.74%) |        1.23 s  →      769.47 ms  (-37.42%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner_local                       |        5.00 ms →        4.54 ms   (-9.31%) |     244   →     169    (-30.74%) |        1.22 s  →      766.85 ms  (-37.19%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        5.00 ms →        4.54 ms   (-9.31%) |     244   →     169    (-30.74%) |        1.22 s  →      766.75 ms  (-37.19%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        5.51 ms →        5.38 ms   (-2.40%) |      20   →      15    (-25.00%) |      110.15 ms →       80.63 ms  (-26.80%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        4.65 ms →        4.40 ms   (-5.30%) |      20   →      15    (-25.00%) |       93.01 ms →       66.06 ms  (-28.97%) | 
+ │ │ ├ sirius::Potential::generate                                     |      358.37 ms →      345.89 ms   (-3.48%) |      20   →      15    (-25.00%) |        7.17 s  →        5.19 s   (-27.61%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |       38.71 ms →       34.94 ms   (-9.73%) |      20   →      15    (-25.00%) |      774.12 ms →      524.08 ms  (-32.30%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        3.31 ms →        3.55 ms   (+7.31%) |      20   →      15    (-25.00%) |       66.17 ms →       53.26 ms  (-19.52%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner                             |        5.06 ms →        4.99 ms   (-1.39%) |      20   →      15    (-25.00%) |      101.27 ms →       74.90 ms  (-26.04%) | 
+ │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.82 ms →        4.86 ms   (+0.84%) |      20   →      15    (-25.00%) |       96.49 ms →       72.97 ms  (-24.37%) | 
+ │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.82 ms →        4.86 ms   (+0.84%) |      20   →      15    (-25.00%) |       96.47 ms →       72.96 ms  (-24.37%) | 
+ │ │ │ ├ sirius::Periodic_function::add                                |      780.84 μs →      708.92 μs   (-9.21%) |      40   →      30    (-25.00%) |       31.23 ms →       21.27 ms  (-31.91%) | 
+ │ │ │ ├ sirius::Potential::xc                                         |       44.24 ms →       35.75 ms  (-19.19%) |      20   →      15    (-25.00%) |      884.87 ms →      536.29 ms  (-39.39%) | 
+ │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       44.24 ms →       34.56 ms  (-21.89%) |      20   →      15    (-25.00%) |      884.82 ms →      518.36 ms  (-41.42%) | 
+ │ │ │ │   ├ sirius::Smooth_periodic_function                          |      632.17 μs →      655.69 μs   (+3.72%) |      40   →      15    (-62.50%) |       25.29 ms →        9.84 ms  (-61.11%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |        4.58 ms                             |      20                          |       91.50 ms                             | 
  │ │ │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                |                        13.89 ms            |                  30              |                       416.68 ms            | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.37 ms →        3.91 ms  (+16.10%) |      20   →      15    (-25.00%) |       67.39 ms →       58.68 ms  (-12.93%) | 
+ │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      269.04 ms →      268.40 ms   (-0.24%) |      20   →      15    (-25.00%) |        5.38 s  →        4.03 s   (-25.18%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      140.30 ns →      148.60 ns   (+5.92%) |      20   →      15    (-25.00%) |        2.81 μs →        2.23 μs  (-20.56%) | 
+ │ │ ├ sirius::Field4D::symmetrize                                     |       99.41 ms →       92.79 ms   (-6.66%) |      20   →      15    (-25.00%) |        1.99 s  →        1.39 s   (-29.99%) | 
+ │ │ │ └ sirius::symmetrize_function|fpw                               |       99.40 ms →       92.78 ms   (-6.66%) |      20   →      15    (-25.00%) |        1.99 s  →        1.39 s   (-30.00%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       15.43 ms →       13.37 ms  (-13.35%) |      20   →      15    (-25.00%) |      308.57 ms →      200.54 ms  (-35.01%) | 
+ │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       68.78 ms →       65.90 ms   (-4.19%) |      20   →      15    (-25.00%) |        1.38 s  →      988.49 ms  (-28.14%) | 
+ │ │ │   └ sddk::Gvec_shells::remap_backward                           |       14.56 ms →       12.88 ms  (-11.57%) |      20   →      15    (-25.00%) |      291.26 ms →      193.16 ms  (-33.68%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        4.09 ms →        4.22 ms   (+3.29%) |      20   →      15    (-25.00%) |       81.74 ms →       63.32 ms  (-22.53%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.88 ms                             |     140                          |      682.71 ms                             | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.74 ms                             |     140                          |      664.23 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.74 ms                             |     140                          |      664.11 ms                             | 
+ │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.54 ms →        4.80 ms   (+5.54%) |      60   →      45    (-25.00%) |      272.63 ms →      215.80 ms  (-20.85%) | 
+ │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.52 ms →        4.73 ms   (+4.54%) |      60   →      45    (-25.00%) |      271.50 ms →      212.86 ms  (-21.60%) | 
+ │ │ ├ sirius::Periodic_function::integrate                            |        4.53 ms →        4.58 ms   (+0.99%) |      20   →      15    (-25.00%) |       90.61 ms →       68.63 ms  (-24.26%) | 
- │ │ └ sirius::Density::get_magnetisation                              |       76.24 μs →       25.55 ms (+33409.58%) |      20   →      15    (-25.00%) |        1.52 ms →      383.24 ms (+25032.18%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |       71.17 μs →       25.54 ms (+35785.57%) |      20   →      15    (-25.00%) |        1.42 ms →      383.10 ms (+26814.17%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.57 ms →        5.29 ms   (-4.94%) |       2   →       2              |       11.14 ms →       10.59 ms   (-4.94%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.99 ms →        4.73 ms   (-5.14%) |       6   →       6              |       29.94 ms →       28.41 ms   (-5.14%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.99 ms →        4.72 ms   (-5.32%) |       6   →       6              |       29.93 ms →       28.33 ms   (-5.32%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.99 ms →        4.72 ms   (-5.33%) |       6   →       6              |       29.92 ms →       28.33 ms   (-5.33%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.79 ms →        4.72 ms   (-1.48%) |       3   →       3              |       14.38 ms →       14.17 ms   (-1.48%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.79 ms →        4.72 ms   (-1.50%) |       3   →       3              |       14.37 ms →       14.15 ms   (-1.50%) | 
  ├ sirius::Periodic_function|inner                                     |        4.98 ms →        4.77 ms   (-4.18%) |       2   →       2              |        9.95 ms →        9.54 ms   (-4.18%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.97 ms →        4.76 ms   (-4.20%) |       2   →       2              |        9.94 ms →        9.53 ms   (-4.20%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.97 ms →        4.76 ms   (-4.20%) |       2   →       2              |        9.94 ms →        9.52 ms   (-4.20%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.77 ms →        4.71 ms   (-1.25%) |       1   →       1              |        4.77 ms →        4.71 ms   (-1.25%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.77 ms →        4.71 ms   (-1.27%) |       1   →       1              |        4.77 ms →        4.71 ms   (-1.27%) | 
+ └ sirius::finalize                                                    |      937.29 ms →      196.39 ms  (-79.05%) |       1   →       1              |      937.29 ms →      196.39 ms  (-79.05%) | 
  ====================================================================================================================================================================================================
```
