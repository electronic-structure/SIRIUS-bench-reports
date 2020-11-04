# Benchmark 392f68b5626168134a99cd6d4a3cc40b87322cb7 vs 4abe991ed1b67a61e2f44af0d6336c92b3f43afd
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
- sirius                                                                |       72.49 s  →     1035.23 s  (+1328.04%) |       1   →       1              |       72.49 s  →     1035.23 s  (+1328.04%) | 
  ├ sirius::initialize                                                  |        2.75 s  →        2.75 s    (+0.02%) |       1   →       1              |        2.75 s  →        2.75 s    (+0.02%) | 
  ├ sirius::Simulation_context::initialize                              |        3.93 s  →        3.89 s    (-1.08%) |       1   →       1              |        3.93 s  →        3.89 s    (-1.08%) | 
- │ ├ sirius::Simulation_context::init_comm                             |       43.43 ms →       63.13 ms  (+45.38%) |       1   →       1              |       43.43 ms →       63.13 ms  (+45.38%) | 
  │ ├ sirius::Unit_cell::initialize                                     |      128.13 ms →      119.61 ms   (-6.65%) |       1   →       1              |      128.13 ms →      119.61 ms   (-6.65%) | 
  │ │ ├ sirius::Atom_type::init                                         |       54.93 ms →       51.60 ms   (-6.05%) |       2   →       2              |      109.85 ms →      103.21 ms   (-6.05%) | 
+ │ │ └ sirius::Unit_cell::update                                       |       18.20 ms →       16.33 ms  (-10.26%) |       1   →       1              |       18.20 ms →       16.33 ms  (-10.26%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        5.22 ms →        5.19 ms   (-0.46%) |       1   →       1              |        5.22 ms →        5.19 ms   (-0.46%) | 
+ │ │   └ sirius::Unit_cell::get_symmetry                               |       12.91 ms →       11.07 ms  (-14.20%) |       1   →       1              |       12.91 ms →       11.07 ms  (-14.20%) | 
+ │ │     └ sirius::Unit_cell_symmetry                                  |       12.82 ms →       11.01 ms  (-14.12%) |       1   →       1              |       12.82 ms →       11.01 ms  (-14.12%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.76 ms →        2.76 ms   (-0.19%) |       1   →       1              |        2.76 ms →        2.76 ms   (-0.19%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      503.86 μs →      553.43 μs   (+9.84%) |       1   →       1              |      503.86 μs →      553.43 μs   (+9.84%) | 
+ │ │       └ sirius::Unit_cell_symmetry|mag                            |       27.30 μs →       15.76 μs  (-42.26%) |       1   →       1              |       27.30 μs →       15.76 μs  (-42.26%) | 
  │ └ sirius::Simulation_context::update                                |        3.71 s  →        3.58 s    (-3.40%) |       1   →       1              |        3.71 s  →        3.58 s    (-3.40%) | 
  │   ├ sirius::Unit_cell::update                                       |        6.84 ms →        6.90 ms   (+0.92%) |       1   →       1              |        6.84 ms →        6.90 ms   (+0.92%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.49 ms →        3.51 ms   (+0.53%) |       1   →       1              |        3.49 ms →        3.51 ms   (+0.53%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.30 ms →        3.35 ms   (+1.49%) |       1   →       1              |        3.30 ms →        3.35 ms   (+1.49%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.24 ms →        3.27 ms   (+1.14%) |       1   →       1              |        3.24 ms →        3.27 ms   (+1.14%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.70 ms →        2.73 ms   (+0.98%) |       1   →       1              |        2.70 ms →        2.73 ms   (+0.98%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      486.58 μs →      495.88 μs   (+1.91%) |       1   →       1              |      486.58 μs →      495.88 μs   (+1.91%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       21.24 μs →       22.99 μs   (+8.23%) |       1   →       1              |       21.24 μs →       22.99 μs   (+8.23%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      219.03 ms →      214.03 ms   (-2.28%) |       2   →       2              |      438.06 ms →      428.05 ms   (-2.28%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.15 ms →       15.14 ms   (-0.09%) |       2   →       2              |       30.31 ms →       30.28 ms   (-0.09%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.25 ms →       13.24 ms   (-0.11%) |       1   →       1              |       13.25 ms →       13.24 ms   (-0.11%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.40 ms →       56.94 ms   (+0.97%) |       2   →       2              |      112.79 ms →      113.89 ms   (+0.97%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.06 ms →       45.15 ms   (+0.20%) |       2   →       2              |       90.13 ms →       90.31 ms   (+0.20%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.12 ms →       60.26 ms   (+0.24%) |       4   →       4              |      240.47 ms →      241.06 ms   (+0.24%) | 
  │   ├ sddk::Gvec::init                                                |       93.56 ms →       94.00 ms   (+0.47%) |       2   →       2              |      187.12 ms →      187.99 ms   (+0.47%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       69.52 ms →       69.66 ms   (+0.20%) |       2   →       2              |      139.05 ms →      139.32 ms   (+0.20%) | 
  │   ├ sddk::Gvec_shells                                               |       95.18 ms →       94.71 ms   (-0.49%) |       1   →       1              |       95.18 ms →       94.71 ms   (-0.49%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.96 ms →        2.03 ms   (+3.39%) |       1   →       1              |        1.96 ms →        2.03 ms   (+3.39%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      653.17 ms →      605.96 ms   (-7.23%) |       2   →       2              |        1.31 s  →        1.21 s    (-7.23%) | 
- ├ sirius::K_point_set::create_k_mesh                                  |       89.81 ms →      120.21 ms  (+33.84%) |       1   →       1              |       89.81 ms →      120.21 ms  (+33.84%) | 
- │ ├ sirius::K_point::K_point                                          |        1.03 μs →        1.70 μs  (+65.13%) |       4   →       4              |        4.11 μs →        6.79 μs  (+65.13%) | 
- │ └ sirius::K_point_set::initialize                                   |       89.74 ms →      120.13 ms  (+33.87%) |       1   →       1              |       89.74 ms →      120.13 ms  (+33.87%) | 
  │   └ sirius::K_point::initialize                                     |       28.56 ms →       28.36 ms   (-0.71%) |       1   →       1              |       28.56 ms →       28.36 ms   (-0.71%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       10.96 ms →       10.79 ms   (-1.59%) |       1   →       1              |       10.96 ms →       10.79 ms   (-1.59%) | 
  │     │ └ sddk::Gvec::init                                            |        4.94 ms →        4.87 ms   (-1.52%) |       1   →       1              |        4.94 ms →        4.87 ms   (-1.52%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        7.27 μs →        7.27 μs   (+0.03%) |       1   →       1              |        7.27 μs →        7.27 μs   (+0.03%) | 
  │     └ sirius::K_point::update                                       |       14.71 ms →       14.74 ms   (+0.24%) |       1   →       1              |       14.71 ms →       14.74 ms   (+0.24%) | 
  │       └ sirius::Beta_projectors                                     |       10.73 ms →       10.83 ms   (+0.85%) |       1   →       1              |       10.73 ms →       10.83 ms   (+0.85%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.79 ms →        8.84 ms   (+0.51%) |       1   →       1              |        8.79 ms →        8.84 ms   (+0.51%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.55 ms →        2.57 ms   (+0.61%) |       2   →       2              |        5.11 ms →        5.14 ms   (+0.61%) | 
  ├ sirius::Potential                                                   |       56.28 ms →       51.83 ms   (-7.91%) |       1   →       1              |       56.28 ms →       51.83 ms   (-7.91%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.93 ms →        2.91 ms   (-0.83%) |       6   →       6              |       17.59 ms →       17.45 ms   (-0.83%) | 
+ │ └ sirius::Potential::update                                         |       38.07 ms →       33.85 ms  (-11.08%) |       1   →       1              |       38.07 ms →       33.85 ms  (-11.08%) | 
+ │   └ sirius::Potential::generate_local_potential                     |       37.68 ms →       33.41 ms  (-11.32%) |       1   →       1              |       37.68 ms →       33.41 ms  (-11.32%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       33.31 ms →       27.62 ms  (-17.06%) |       1   →       1              |       33.31 ms →       27.62 ms  (-17.06%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        3.81 ms →        5.23 ms  (+37.25%) |       1   →       1              |        3.81 ms →        5.23 ms  (+37.25%) | 
+ ├ sirius::Density                                                     |       43.45 ms →       38.86 ms  (-10.57%) |       1   →       1              |       43.45 ms →       38.86 ms  (-10.57%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.83 ms →        2.82 ms   (-0.44%) |       2   →       2              |        5.66 ms →        5.64 ms   (-0.44%) | 
+ │ └ sirius::Density::update                                           |       37.64 ms →       33.08 ms  (-12.11%) |       1   →       1              |       37.64 ms →       33.08 ms  (-12.11%) | 
+ │   └ sirius::Density::generate_pseudo_core_charge_density            |       37.33 ms →       32.84 ms  (-12.04%) |       1   →       1              |       37.33 ms →       32.84 ms  (-12.04%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |       78.63 μs →       78.83 μs   (+0.26%) |       1   →       1              |       78.63 μs →       78.83 μs   (+0.26%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       33.60 ms →       26.93 ms  (-19.86%) |       1   →       1              |       33.60 ms →       26.93 ms  (-19.86%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        3.31 ms →        5.50 ms  (+66.10%) |       1   →       1              |        3.31 ms →        5.50 ms  (+66.10%) | 
+ ├ sirius::Density::initial_density                                    |       66.10 ms →       56.18 ms  (-15.01%) |       1   →       1              |       66.10 ms →       56.18 ms  (-15.01%) | 
+ │ ├ sirius::Simulation_context::make_periodic_function                |       38.13 ms →       27.78 ms  (-27.15%) |       1   →       1              |       38.13 ms →       27.78 ms  (-27.15%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.88 ms →        5.11 ms   (+4.70%) |       2   →       2              |        9.76 ms →       10.22 ms   (+4.70%) | 
  │ └ sirius::Periodic_function::integrate                              |        4.65 ms →        4.61 ms   (-0.80%) |       1   →       1              |        4.65 ms →        4.61 ms   (-0.80%) | 
  ├ sirius::Potential::generate                                         |      372.69 ms →      363.12 ms   (-2.57%) |       1   →       1              |      372.69 ms →      363.12 ms   (-2.57%) | 
+ │ ├ sirius::Potential::poisson                                        |       45.66 ms →       36.09 ms  (-20.95%) |       1   →       1              |       45.66 ms →       36.09 ms  (-20.95%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.28 ms →        5.05 ms  (+53.80%) |       1   →       1              |        3.28 ms →        5.05 ms  (+53.80%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        5.11 ms →        4.64 ms   (-9.24%) |       1   →       1              |        5.11 ms →        4.64 ms   (-9.24%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.84 ms →        4.63 ms   (-4.28%) |       1   →       1              |        4.84 ms →        4.63 ms   (-4.28%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.83 ms →        4.63 ms   (-4.25%) |       1   →       1              |        4.83 ms →        4.63 ms   (-4.25%) | 
  │ ├ sirius::Periodic_function::add                                    |      750.43 μs →      777.84 μs   (+3.65%) |       2   →       2              |        1.50 ms →        1.56 ms   (+3.65%) | 
  │ ├ sirius::Potential::xc                                             |       51.37 ms →       51.84 ms   (+0.93%) |       1   →       1              |       51.37 ms →       51.84 ms   (+0.93%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       50.14 ms →       50.63 ms   (+0.98%) |       1   →       1              |       50.14 ms →       50.63 ms   (+0.98%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.55 ms →        2.55 ms   (+0.24%) |       2   →       2              |        5.09 ms →        5.11 ms   (+0.24%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.68 ms →        4.68 ms   (+0.10%) |       1   →       1              |        4.68 ms →        4.68 ms   (+0.10%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        2.88 ms →        3.58 ms  (+24.43%) |       1   →       1              |        2.88 ms →        3.58 ms  (+24.43%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      269.85 ms →      268.66 ms   (-0.44%) |       1   →       1              |      269.85 ms →      268.66 ms   (-0.44%) | 
- │ └ sirius::Potential::generate_PAW_effective_potential               |      124.00 ns →      198.00 ns  (+59.68%) |       1   →       1              |      124.00 ns →      198.00 ns  (+59.68%) | 
  ├ sirius::Hamiltonian0                                                |        7.75 ms →        7.93 ms   (+2.41%) |       1   →       1              |        7.75 ms →        7.93 ms   (+2.41%) | 
  │ ├ sirius::Local_operator                                            |        7.05 ms →        7.17 ms   (+1.68%) |       1   →       1              |        7.05 ms →        7.17 ms   (+1.68%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.75 ms →        2.73 ms   (-0.82%) |       1   →       1              |        2.75 ms →        2.73 ms   (-0.82%) | 
- │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        3.23 ms →        3.58 ms  (+10.73%) |       1   →       1              |        3.23 ms →        3.58 ms  (+10.73%) | 
- │ ├ sirius::Non_local_operator                                        |      213.96 μs →      248.87 μs  (+16.32%) |       2   →       2              |      427.92 μs →      497.74 μs  (+16.32%) | 
  │ ├ sirius::D_operator::initialize                                    |      103.16 μs →      102.42 μs   (-0.71%) |       1   →       1              |      103.16 μs →      102.42 μs   (-0.71%) | 
  │ └ sirius::Q_operator::initialize                                    |       91.72 μs →       92.86 μs   (+1.24%) |       1   →       1              |       91.72 μs →       92.86 μs   (+1.24%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.29 s  →        1.31 s    (+0.95%) |       1   →       1              |        1.29 s  →        1.31 s    (+0.95%) | 
+ │ ├ sirius::Hamiltonian_k                                             |       66.30 ms →       59.24 ms  (-10.66%) |       1   →       1              |       66.30 ms →       59.24 ms  (-10.66%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      321.06 μs →      318.28 μs   (-0.87%) |       1   →       1              |      321.06 μs →      318.28 μs   (-0.87%) | 
+ │ │ └ sirius::Beta_projectors_base::prepare                           |       65.98 ms →       58.92 ms  (-10.70%) |       1   →       1              |       65.98 ms →       58.92 ms  (-10.70%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.23 s  →        1.25 s    (+1.58%) |       1   →       1              |        1.23 s  →        1.25 s    (+1.58%) | 
+ │ │ ├ sddk::matrix_storage::matrix_storage                            |       87.36 ms →       78.21 ms  (-10.48%) |       4   →       4              |      349.45 ms →      312.84 ms  (-10.48%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       56.17 ms →       53.53 ms   (-4.70%) |       1   →       1              |       56.17 ms →       53.53 ms   (-4.70%) | 
+ │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        8.65 ms →        7.50 ms  (-13.29%) |       1   →       1              |        8.65 ms →        7.50 ms  (-13.29%) | 
+ │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      384.08 ms →      315.80 ms  (-17.78%) |       1   →       1              |      384.08 ms →      315.80 ms  (-17.78%) | 
+ │ │ │ ├ sirius::Local_operator::apply_h                               |      289.88 ms →      244.96 ms  (-15.50%) |       1   →       1              |      289.88 ms →      244.96 ms  (-15.50%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.87 μs →        4.86 μs  (+25.38%) |       1   →       1              |        3.87 μs →        4.86 μs  (+25.38%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.98 μs →        3.77 μs  (+26.63%) |       1   →       1              |        2.98 μs →        3.77 μs  (+26.63%) | 
- │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      460.00 ns →      665.00 ns  (+44.57%) |       1   →       1              |      460.00 ns →      665.00 ns  (+44.57%) | 
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      799.00 ns →      623.00 ns  (-22.03%) |       1   →       1              |      799.00 ns →      623.00 ns  (-22.03%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.09 ms →        3.17 ms   (+2.75%) |       1   →       1              |        3.09 ms →        3.17 ms   (+2.75%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::inner                           |       38.34 ms →       21.22 ms  (-44.66%) |       1   →       1              |       38.34 ms →       21.22 ms  (-44.66%) | 
+ │ │ │ └ sirius::Non_local_operator::apply                             |       26.37 ms →       23.20 ms  (-12.00%) |       2   →       2              |       52.74 ms →       46.41 ms  (-12.00%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       16.62 ms →       14.98 ms   (-9.88%) |       2   →       2              |       33.25 ms →       29.96 ms   (-9.88%) | 
  │ │ │ └ sddk::wf_inner                                                |       16.40 ms →       14.77 ms   (-9.94%) |       2   →       2              |       32.81 ms →       29.54 ms   (-9.94%) | 
  │ │ │   ├ sddk::wf_inner|scale                                        |       19.00 ns →       20.50 ns   (+7.89%) |       2   →       2              |       38.00 ns →       41.00 ns   (+7.89%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       16.25 ms →       14.63 ms   (-9.96%) |       2   →       2              |       32.50 ms →       29.26 ms   (-9.96%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       27.50 ns →       46.50 ns  (+69.09%) |       2   →       2              |       55.00 ns →       93.00 ns  (+69.09%) | 
- │ │ ├ Eigensolver_cuda|zhegvdx                                        |      180.65 ms →      248.94 ms  (+37.80%) |       1   →       1              |      180.65 ms →      248.94 ms  (+37.80%) | 
  │ │ └ sddk::wf_trans                                                  |        2.62 ms →        2.61 ms   (-0.20%) |       1   →       1              |        2.62 ms →        2.61 ms   (-0.20%) | 
  │ │   └ sddk::wf_trans|pw                                             |        2.61 ms →        2.61 ms   (-0.19%) |       1   →       1              |        2.61 ms →        2.61 ms   (-0.19%) | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      440.00 ns →      540.00 ns  (+22.73%) |       1   →       1              |      440.00 ns →      540.00 ns  (+22.73%) | 
- ├ sirius::DFT_ground_state::scf_loop                                  |       62.77 s  →     1025.54 s  (+1533.90%) |       1   →       1              |       62.77 s  →     1025.54 s  (+1533.90%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.47 ms →        2.45 ms   (-0.83%) |      19   →      19              |       46.97 ms →       46.58 ms   (-0.83%) | 
- │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        2.98 s  →       10.25 s  (+244.56%) |      21   →     100   (+376.19%) |       62.49 s  →     1025.30 s  (+1540.74%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        5.44 ms →        5.28 ms   (-2.92%) |      21   →     100   (+376.19%) |      114.31 ms →      528.48 ms (+362.31%) | 
- │ │ │ ├ sirius::Local_operator                                        |        4.67 ms →        4.42 ms   (-5.29%) |      21   →     100   (+376.19%) |       98.00 ms →      441.98 ms (+350.99%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function                            |      560.82 μs →      553.45 μs   (-1.31%) |      21   →     100   (+376.19%) |       11.78 ms →       55.35 ms (+369.93%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.84 ms →        2.72 ms   (-3.98%) |      21   →     100   (+376.19%) |       59.57 ms →      272.37 ms (+357.22%) | 
- │ │ │ ├ sirius::Non_local_operator                                    |      250.82 μs →      300.87 μs  (+19.95%) |      42   →     200   (+376.19%) |       10.53 ms →       60.17 ms (+471.21%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |      110.82 μs →      107.62 μs   (-2.88%) |      21   →     100   (+376.19%) |        2.33 ms →       10.76 ms (+362.46%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       87.58 μs →       88.24 μs   (+0.76%) |      21   →     100   (+376.19%) |        1.84 ms →        8.82 ms (+379.79%) | 
- │ │ ├ sirius::Band::solve                                             |        1.76 s  →        9.10 s  (+418.26%) |      21   →     100   (+376.19%) |       36.86 s  →      909.65 s  (+2367.88%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      187.79 μs →      192.77 μs   (+2.65%) |      21   →     100   (+376.19%) |        3.94 ms →       19.28 ms (+388.80%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      178.26 μs →      183.65 μs   (+3.02%) |      21   →     100   (+376.19%) |        3.74 ms →       18.36 ms (+390.59%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        7.35 μs →        6.88 μs   (-6.38%) |      21   →     100   (+376.19%) |      154.40 μs →      688.30 μs (+345.80%) | 
- │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.64 s  →        9.08 s  (+454.24%) |      21   →     100   (+376.19%) |       34.41 s  →      908.28 s  (+2539.24%) | 
- │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       73.59 ms →       37.61 ms  (-48.90%) |      21   →     100   (+376.19%) |        1.55 s  →        3.76 s  (+143.33%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.44 ms →        1.51 ms  (-79.76%) |     126   →     600   (+376.19%) |      937.90 ms →      903.88 ms   (-3.63%) | 
- │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       15.25 ms →       15.22 ms   (-0.16%) |      21   →     100   (+376.19%) |      320.18 ms →        1.52 s  (+375.41%) | 
- │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      484.75 μs →      486.65 μs   (+0.39%) |      21   →     100   (+376.19%) |       10.18 ms →       48.66 ms (+378.06%) | 
- │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        6.95 ms →        6.91 ms   (-0.55%) |      42   →     200   (+376.19%) |      291.91 ms →        1.38 s  (+373.55%) | 
- │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.54 s  →        9.02 s  (+485.05%) |      21   →     100   (+376.19%) |       32.38 s  →      902.02 s  (+2685.96%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       60.45 ms →      270.71 ms (+347.85%) |     361   →    1.98 K (+449.31%) |       21.82 s  →      536.82 s  (+2360.07%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       37.09 ms →      210.13 ms (+466.49%) |     361   →    1.98 K (+449.31%) |       13.39 s  →      416.69 s  (+3011.78%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.05 μs →        2.24 μs   (+9.16%) |     361   →    1.98 K (+449.31%) |      740.10 μs →        4.44 ms (+499.61%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.67 μs →        1.88 μs  (+12.51%) |     361   →    1.98 K (+449.31%) |      603.22 μs →        3.73 ms (+518.05%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      450.45 ns →      390.10 ns  (-13.40%) |     361   →    1.98 K (+449.31%) |      162.61 μs →      773.57 μs (+375.72%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      521.55 ns →      671.97 ns  (+28.84%) |     361   →    1.98 K (+449.31%) |      188.28 μs →        1.33 ms (+607.73%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        3.08 ms →        4.46 ms  (+45.02%) |     361   →    1.98 K (+449.31%) |        1.11 s  →        8.85 s  (+696.60%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.44 ms →       11.59 ms (+236.75%) |     361   →    1.98 K (+449.31%) |        1.24 s  →       22.97 s  (+1749.80%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        8.41 ms →       22.26 ms (+164.68%) |     722   →    3.97 K (+449.31%) |        6.07 s  →       88.26 s  (+1353.89%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |        5.75 ms →       21.61 ms (+275.61%) |     361   →    1.98 K (+449.31%) |        2.08 s  →       42.85 s  (+1963.27%) | 
- │ │ │ │   │ ├ sddk::wf_inner                                          |        1.03 ms →        2.91 ms (+182.79%) |     701   →    3.87 K (+451.50%) |      722.11 ms →       11.26 s  (+1459.60%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       40.34 ns →       47.36 ns  (+17.39%) |     701   →    3.87 K (+451.50%) |       28.28 μs →      183.08 μs (+547.42%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |      867.42 μs →        2.74 ms (+215.38%) |     701   →    3.87 K (+451.50%) |      608.06 ms →       10.58 s  (+1639.31%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       50.55 ns →       56.11 ns  (+10.98%) |     701   →    3.87 K (+451.50%) |       35.44 μs →      216.91 μs (+512.07%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      139.20 μs →      690.58 μs (+396.10%) |     361   →    1.98 K (+449.31%) |       50.25 ms →        1.37 s  (+2625.09%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        1.64 ms →        7.83 ms (+377.98%) |     361   →    1.98 K (+449.31%) |      591.63 ms →       15.53 s  (+2525.56%) | 
- │ │ │ │   │ └ sddk::wf_trans                                          |        2.09 ms →        7.79 ms (+272.54%) |     340   →    1.88 K (+453.82%) |      710.88 ms →       14.67 s  (+1963.19%) | 
- │ │ │ │   │   └ sddk::wf_trans|pw                                     |      696.07 μs →        2.60 ms (+272.87%) |    1.02 K →    5.65 K (+453.82%) |      710.00 ms →       14.66 s  (+1965.06%) | 
- │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.14 ms →        4.03 ms (+253.58%) |     361   →    1.98 K (+449.31%) |      411.37 ms →        7.99 s  (+1842.22%) | 
- │ │ │ │   │ └ sddk::wf_inner                                          |        1.09 ms →        3.85 ms (+251.65%) |     361   →    1.98 K (+449.31%) |      395.29 ms →        7.64 s  (+1831.65%) | 
- │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       41.62 ns →       51.11 ns  (+22.80%) |     361   →    1.98 K (+449.31%) |       15.02 μs →      101.35 μs (+574.56%) | 
- │ │ │ │   │   ├ sddk::wf_inner|pw                                     |      931.54 μs →        3.68 ms (+295.07%) |     361   →    1.98 K (+449.31%) |      336.29 ms →        7.30 s  (+2070.17%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       46.90 ns →       61.19 ns  (+30.45%) |     361   →    1.98 K (+449.31%) |       16.93 μs →      121.33 μs (+616.60%) | 
- │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       18.85 ms →      137.28 ms (+628.33%) |     361   →    1.98 K (+449.31%) |        6.80 s  →      272.22 s  (+3900.75%) | 
- │ │ │ │   ├ sirius::residuals                                         |        2.51 ms →       12.02 ms (+379.24%) |     346   →    1.88 K (+444.51%) |      868.14 ms →       22.65 s  (+2509.51%) | 
- │ │ │ │   │ ├ sddk::wf_trans                                          |        1.15 ms →        7.25 ms (+533.10%) |     342   →    1.88 K (+450.58%) |      391.66 ms →       13.65 s  (+3385.74%) | 
- │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      571.11 μs →        3.62 ms (+534.48%) |     684   →    3.77 K (+450.58%) |      390.64 ms →       13.65 s  (+3393.33%) | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.29 ms →        4.59 ms (+256.95%) |     342   →    1.88 K (+450.58%) |      440.13 ms →        8.65 s  (+1865.29%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        4.31 ms →       10.59 ms (+145.33%) |      90   →    1.84 K (+1940.00%) |      388.35 ms →       19.44 s  (+4904.75%) | 
- │ │ │ │     └ sddk::wf_trans                                          |        2.39 ms →        5.38 ms (+125.15%) |     159   →    3.57 K (+2146.54%) |      379.86 ms →       19.21 s  (+4958.15%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |        1.66 ms →        3.62 ms (+117.37%) |     228   →    5.31 K (+2228.07%) |      379.53 ms →       19.21 s  (+4960.59%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      525.05 ns →      477.57 ns   (-9.04%) |      21   →     100   (+376.19%) |       11.03 μs →       47.76 μs (+333.13%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       20.31 μs →       20.23 μs   (-0.41%) |      21   →     100   (+376.19%) |      426.54 μs →        2.02 ms (+374.26%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.52 ms →        1.06 ms  (-30.32%) |      21   →     100   (+376.19%) |       31.94 ms →      105.99 ms (+231.81%) | 
- │ │ ├ sirius::Density::generate                                       |      560.64 ms →      558.02 ms   (-0.47%) |      21   →     100   (+376.19%) |       11.77 s  →       55.80 s  (+373.97%) | 
- │ │ │ ├ sirius::Density::generate_valence                             |      409.50 ms →      381.70 ms   (-6.79%) |      21   →     100   (+376.19%) |        8.60 s  →       38.17 s  (+343.86%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.08 μs →        8.01 μs   (-0.95%) |      21   →     100   (+376.19%) |      169.76 μs →      800.69 μs (+371.65%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.45 μs →        7.31 μs   (-1.83%) |      21   →     100   (+376.19%) |      156.41 μs →      731.22 μs (+367.49%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       38.59 ms →       41.22 ms   (+6.80%) |      21   →     100   (+376.19%) |      810.43 ms →        4.12 s  (+408.58%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       11.09 μs →       10.70 μs   (-3.51%) |      21   →     100   (+376.19%) |      232.98 μs →        1.07 ms (+359.47%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |       22.63 ms →       23.12 ms   (+2.18%) |      21   →     100   (+376.19%) |      475.23 ms →        2.31 s  (+386.56%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       14.92 ms →       17.06 ms  (+14.33%) |      21   →     100   (+376.19%) |      313.26 ms →        1.71 s  (+444.44%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      974.67 ns →      671.04 ns  (-31.15%) |      21   →     100   (+376.19%) |       20.47 μs →       67.10 μs (+227.85%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      100.72 ms →       96.10 ms   (-4.59%) |      21   →     100   (+376.19%) |        2.12 s  →        9.61 s  (+354.33%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.18 ms →        2.24 ms   (+2.88%) |      21   →     100   (+376.19%) |       45.82 ms →      224.49 ms (+389.90%) | 
- │ │ │ │ └ sirius::Density::augment                                    |      229.25 ms →      199.62 ms  (-12.93%) |      21   →     100   (+376.19%) |        4.81 s  →       19.96 s  (+314.63%) | 
- │ │ │ │   └ sirius::Density::generate_rho_aug                         |      229.03 ms →      199.39 ms  (-12.94%) |      21   →     100   (+376.19%) |        4.81 s  →       19.94 s  (+314.57%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      123.62 ms →      148.21 ms  (+19.89%) |      21   →     100   (+376.19%) |        2.60 s  →       14.82 s  (+470.91%) | 
- │ │ │ │ └ sirius::symmetrize_function|fpw                             |      123.62 ms →      148.21 ms  (+19.89%) |      21   →     100   (+376.19%) |        2.60 s  →       14.82 s  (+470.91%) | 
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       42.85 ms →       65.49 ms  (+52.84%) |      21   →     100   (+376.19%) |      899.79 ms →        6.55 s  (+627.80%) | 
- │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       67.51 ms →       69.32 ms   (+2.68%) |      21   →     100   (+376.19%) |        1.42 s  →        6.93 s  (+388.94%) | 
- │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.61 ms →       12.77 ms   (+1.25%) |      21   →     100   (+376.19%) |      264.78 ms →        1.28 s  (+382.16%) | 
- │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.62 ms →       23.63 ms   (+0.05%) |      21   →     100   (+376.19%) |      496.06 ms →        2.36 s  (+376.42%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        3.89 ms →        4.47 ms  (+14.81%) |      21   →     100   (+376.19%) |       81.71 ms →      446.75 ms (+446.72%) | 
- │ │ ├ sirius::Density::mix                                            |      136.80 ms →       84.25 ms  (-38.41%) |      21   →     100   (+376.19%) |        2.87 s  →        8.42 s  (+193.27%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      500.20 μs →      671.26 μs  (+34.20%) |      21   →     100   (+376.19%) |       10.50 ms →       67.13 ms (+539.03%) | 
- │ │ │ ├ sirius::Periodic_function|inner                               |        4.98 ms →        4.71 ms   (-5.50%) |     259   →     818   (+215.83%) |        1.29 s  →        3.85 s  (+198.47%) | 
- │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.82 ms →        4.62 ms   (-4.13%) |     259   →     818   (+215.83%) |        1.25 s  →        3.78 s  (+202.79%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.82 ms →        4.62 ms   (-4.12%) |     259   →     818   (+215.83%) |        1.25 s  →        3.78 s  (+202.81%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        6.57 ms →        5.97 ms   (-9.05%) |      21   →     100   (+376.19%) |      137.89 ms →      597.20 ms (+333.10%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.77 ms →        5.16 ms  (-10.56%) |      21   →     100   (+376.19%) |      121.25 ms →      516.41 ms (+325.90%) | 
- │ │ ├ sirius::Potential::generate                                     |      366.04 ms →      355.45 ms   (-2.89%) |      21   →     100   (+376.19%) |        7.69 s  →       35.55 s  (+362.41%) | 
- │ │ │ ├ sirius::Potential::poisson                                    |       45.55 ms →       35.74 ms  (-21.53%) |      21   →     100   (+376.19%) |      956.45 ms →        3.57 s  (+273.67%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        3.29 ms →        4.53 ms  (+37.71%) |      21   →     100   (+376.19%) |       69.04 ms →      452.73 ms (+555.78%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |        5.10 ms →        4.78 ms   (-6.29%) |      21   →     100   (+376.19%) |      107.05 ms →      477.67 ms (+346.23%) | 
- │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.83 ms →        4.63 ms   (-4.21%) |      21   →     100   (+376.19%) |      101.51 ms →      463.04 ms (+356.16%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.83 ms →        4.63 ms   (-4.20%) |      21   →     100   (+376.19%) |      101.48 ms →      462.96 ms (+356.21%) | 
- │ │ │ ├ sirius::Periodic_function::add                                |      747.47 μs →      746.22 μs   (-0.17%) |      42   →     200   (+376.19%) |       31.39 ms →      149.24 ms (+375.39%) | 
- │ │ │ ├ sirius::Potential::xc                                         |       45.34 ms →       44.96 ms   (-0.84%) |      21   →     100   (+376.19%) |      952.21 ms →        4.50 s  (+372.20%) | 
- │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       44.15 ms →       43.77 ms   (-0.85%) |      21   →     100   (+376.19%) |      927.10 ms →        4.38 s  (+372.15%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function                          |      687.15 μs →      655.18 μs   (-4.65%) |      42   →     200   (+376.19%) |       28.86 ms →      131.04 ms (+354.04%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.66 ms →        4.93 ms   (+5.68%) |      21   →     100   (+376.19%) |       97.90 ms →      492.66 ms (+403.22%) | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        2.93 ms →        3.58 ms  (+22.08%) |      21   →     100   (+376.19%) |       61.54 ms →      357.72 ms (+481.32%) | 
- │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      269.30 ms →      268.27 ms   (-0.38%) |      21   →     100   (+376.19%) |        5.66 s  →       26.83 s  (+374.38%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      149.52 ns →      235.47 ns  (+57.48%) |      21   →     100   (+376.19%) |        3.14 μs →       23.55 μs (+649.90%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |       93.97 ms →       95.47 ms   (+1.59%) |      21   →     100   (+376.19%) |        1.97 s  →        9.55 s  (+383.77%) | 
- │ │ │ └ sirius::symmetrize_function|fpw                               |       93.97 ms →       95.47 ms   (+1.59%) |      21   →     100   (+376.19%) |        1.97 s  →        9.55 s  (+383.77%) | 
- │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.29 ms →       13.29 ms   (-0.00%) |      21   →     100   (+376.19%) |      279.09 ms →        1.33 s  (+376.17%) | 
- │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       67.51 ms →       68.78 ms   (+1.89%) |      21   →     100   (+376.19%) |        1.42 s  →        6.88 s  (+385.18%) | 
- │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.54 ms →       12.76 ms   (+1.79%) |      21   →     100   (+376.19%) |      263.25 ms →        1.28 s  (+384.72%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.70 ms →        4.24 ms  (+14.56%) |      21   →     100   (+376.19%) |       77.72 ms →      423.97 ms (+445.52%) | 
- │ │ ├ sirius::Periodic_function|inner                                 |        4.74 ms →        4.88 ms   (+2.84%) |     147   →     700   (+376.19%) |      697.51 ms →        3.42 s  (+389.72%) | 
- │ │ │ └ sirius::Periodic_function|inner_local                         |        4.58 ms →        4.77 ms   (+4.14%) |     147   →     700   (+376.19%) |      673.36 ms →        3.34 s  (+395.91%) | 
- │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.58 ms →        4.77 ms   (+4.14%) |     147   →     700   (+376.19%) |      673.27 ms →        3.34 s  (+395.90%) | 
- │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.77 ms →        4.58 ms   (-4.15%) |      63   →     300   (+376.19%) |      300.77 ms →        1.37 s  (+356.41%) | 
- │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.76 ms →        4.55 ms   (-4.41%) |      63   →     300   (+376.19%) |      300.11 ms →        1.37 s  (+355.18%) | 
- │ │ ├ sirius::Periodic_function::integrate                            |        4.55 ms →        4.55 ms   (-0.17%) |      21   →     100   (+376.19%) |       95.64 ms →      454.63 ms (+375.36%) | 
- │ │ └ sirius::Density::get_magnetisation                              |       73.94 μs →       74.76 μs   (+1.12%) |      21   →     100   (+376.19%) |        1.55 ms →        7.48 ms (+381.51%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |       69.32 μs →       69.69 μs   (+0.53%) |      21   →     100   (+376.19%) |        1.46 ms →        6.97 ms (+378.73%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.66 ms →        5.29 ms   (-6.62%) |       2   →       2              |       11.33 ms →       10.58 ms   (-6.62%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.80 ms →        4.73 ms   (-1.39%) |       6   →       6              |       28.80 ms →       28.40 ms   (-1.39%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.80 ms →        4.72 ms   (-1.51%) |       6   →       6              |       28.78 ms →       28.34 ms   (-1.51%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.80 ms →        4.72 ms   (-1.52%) |       6   →       6              |       28.77 ms →       28.34 ms   (-1.52%) | 
+ │ └ sirius::Smooth_periodic_function|inner                            |        5.05 ms →        4.54 ms  (-10.14%) |       3   →       3              |       15.14 ms →       13.61 ms  (-10.14%) | 
+ │   └ sirius::Smooth_periodic_function|inner_local                    |        5.04 ms →        4.53 ms  (-10.20%) |       3   →       3              |       15.12 ms →       13.58 ms  (-10.20%) | 
  ├ sirius::Periodic_function|inner                                     |        4.81 ms →        4.96 ms   (+3.12%) |       2   →       2              |        9.61 ms →        9.91 ms   (+3.12%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.80 ms →        4.95 ms   (+3.13%) |       2   →       2              |        9.60 ms →        9.90 ms   (+3.13%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.80 ms →        4.95 ms   (+3.13%) |       2   →       2              |        9.60 ms →        9.90 ms   (+3.13%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.97 ms →        4.81 ms   (-3.22%) |       1   →       1              |        4.97 ms →        4.81 ms   (-3.22%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.96 ms →        4.80 ms   (-3.22%) |       1   →       1              |        4.96 ms →        4.80 ms   (-3.22%) | 
- └ sirius::finalize                                                    |      238.58 ms →      345.12 ms  (+44.66%) |       1   →       1              |      238.58 ms →      345.12 ms  (+44.66%) | 
  ====================================================================================================================================================================================================
```
