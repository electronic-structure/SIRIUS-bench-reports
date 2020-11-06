# Benchmark 81702c64a8be67a2936e3e8bb8ca2c9083dee03b vs 036306af487fc282c8f6df5ed9ab8eedf0369ac6
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |       72.69 s  →       74.65 s    (+2.70%) |       1   →       1              |       72.69 s  →       74.65 s    (+2.70%) | 
  ├ sirius::initialize                                                  |        2.87 s  →        2.91 s    (+1.23%) |       1   →       1              |        2.87 s  →        2.91 s    (+1.23%) | 
  ├ sirius::Simulation_context::initialize                              |        3.73 s  →        3.79 s    (+1.59%) |       1   →       1              |        3.73 s  →        3.79 s    (+1.59%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       62.83 ms →      232.91 μs  (-99.63%) |       1   →       1              |       62.83 ms →      232.91 μs  (-99.63%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      190.28 ms →      157.72 ms  (-17.11%) |       1   →       1              |      190.28 ms →      157.72 ms  (-17.11%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       87.22 ms →       69.72 ms  (-20.06%) |       2   →       2              |      174.44 ms →      139.44 ms  (-20.06%) | 
- │ │ └ sirius::Unit_cell::update                                       |       15.73 ms →       18.18 ms  (+15.54%) |       1   →       1              |       15.73 ms →       18.18 ms  (+15.54%) | 
- │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.67 ms →        4.99 ms  (+35.95%) |       1   →       1              |        3.67 ms →        4.99 ms  (+35.95%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       11.99 ms →       13.11 ms   (+9.33%) |       1   →       1              |       11.99 ms →       13.11 ms   (+9.33%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       11.92 ms →       13.04 ms   (+9.37%) |       1   →       1              |       11.92 ms →       13.04 ms   (+9.37%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.73 ms →        2.76 ms   (+0.96%) |       1   →       1              |        2.73 ms →        2.76 ms   (+0.96%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      474.27 μs →      494.56 μs   (+4.28%) |       1   →       1              |      474.27 μs →      494.56 μs   (+4.28%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       15.41 μs →       16.72 μs   (+8.47%) |       1   →       1              |       15.41 μs →       16.72 μs   (+8.47%) | 
  │ └ sirius::Simulation_context::update                                |        3.43 s  →        3.54 s    (+3.09%) |       1   →       1              |        3.43 s  →        3.54 s    (+3.09%) | 
  │   ├ sirius::Unit_cell::update                                       |        7.04 ms →        6.84 ms   (-2.89%) |       1   →       1              |        7.04 ms →        6.84 ms   (-2.89%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.74 ms →        3.53 ms   (-5.50%) |       1   →       1              |        3.74 ms →        3.53 ms   (-5.50%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.27 ms →        3.27 ms   (+0.13%) |       1   →       1              |        3.27 ms →        3.27 ms   (+0.13%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.23 ms →        3.23 ms   (+0.07%) |       1   →       1              |        3.23 ms →        3.23 ms   (+0.07%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.70 ms →        2.70 ms   (-0.06%) |       1   →       1              |        2.70 ms →        2.70 ms   (-0.06%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      494.16 μs →      498.80 μs   (+0.94%) |       1   →       1              |      494.16 μs →      498.80 μs   (+0.94%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       13.71 μs →       13.76 μs   (+0.33%) |       1   →       1              |       13.71 μs →       13.76 μs   (+0.33%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      213.13 ms →      213.11 ms   (-0.01%) |       2   →       2              |      426.26 ms →      426.21 ms   (-0.01%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.19 ms →       15.17 ms   (-0.14%) |       2   →       2              |       30.37 ms →       30.33 ms   (-0.14%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.26 ms →       13.26 ms   (+0.02%) |       1   →       1              |       13.26 ms →       13.26 ms   (+0.02%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.48 ms →       56.29 ms   (-0.33%) |       2   →       2              |      112.96 ms →      112.58 ms   (-0.33%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.09 ms →       45.11 ms   (+0.05%) |       2   →       2              |       90.18 ms →       90.22 ms   (+0.05%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.23 ms →       60.17 ms   (-0.10%) |       4   →       4              |      240.91 ms →      240.67 ms   (-0.10%) | 
  │   ├ sddk::Gvec::init                                                |       92.99 ms →       93.30 ms   (+0.34%) |       2   →       2              |      185.97 ms →      186.60 ms   (+0.34%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       69.49 ms →       69.96 ms   (+0.67%) |       2   →       2              |      138.99 ms →      139.92 ms   (+0.67%) | 
  │   ├ sddk::Gvec_shells                                               |       97.94 ms →       92.86 ms   (-5.19%) |       1   →       1              |       97.94 ms →       92.86 ms   (-5.19%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.95 ms →        1.96 ms   (+0.53%) |       1   →       1              |        1.95 ms →        1.96 ms   (+0.53%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      565.48 ms →      612.61 ms   (+8.33%) |       2   →       2              |        1.13 s  →        1.23 s    (+8.33%) | 
- ├ sirius::K_point_set::create_k_mesh                                  |       89.18 ms →      141.71 ms  (+58.90%) |       1   →       1              |       89.18 ms →      141.71 ms  (+58.90%) | 
- │ ├ sirius::K_point::K_point                                          |        1.03 μs →        1.66 μs  (+60.41%) |       4   →       4              |        4.13 μs →        6.62 μs  (+60.41%) | 
- │ └ sirius::K_point_set::initialize                                   |       89.10 ms →      141.65 ms  (+58.97%) |       1   →       1              |       89.10 ms →      141.65 ms  (+58.97%) | 
  │   └ sirius::K_point::initialize                                     |       27.79 ms →       27.86 ms   (+0.24%) |       1   →       1              |       27.79 ms →       27.86 ms   (+0.24%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       10.94 ms →       11.03 ms   (+0.85%) |       1   →       1              |       10.94 ms →       11.03 ms   (+0.85%) | 
  │     │ └ sddk::Gvec::init                                            |        4.90 ms →        4.96 ms   (+1.23%) |       1   →       1              |        4.90 ms →        4.96 ms   (+1.23%) | 
+ │     ├ sddk::matrix_storage::matrix_storage                          |       12.70 μs →        7.17 μs  (-43.51%) |       1   →       1              |       12.70 μs →        7.17 μs  (-43.51%) | 
  │     └ sirius::K_point::update                                       |       13.96 ms →       14.06 ms   (+0.77%) |       1   →       1              |       13.96 ms →       14.06 ms   (+0.77%) | 
  │       └ sirius::Beta_projectors                                     |       10.02 ms →       10.15 ms   (+1.33%) |       1   →       1              |       10.02 ms →       10.15 ms   (+1.33%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.13 ms →        8.28 ms   (+1.83%) |       1   →       1              |        8.13 ms →        8.28 ms   (+1.83%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.58 ms →        2.56 ms   (-0.48%) |       2   →       2              |        5.15 ms →        5.13 ms   (-0.48%) | 
  ├ sirius::Potential                                                   |       51.02 ms →       49.40 ms   (-3.16%) |       1   →       1              |       51.02 ms →       49.40 ms   (-3.16%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.93 ms →        2.91 ms   (-0.41%) |       6   →       6              |       17.56 ms →       17.49 ms   (-0.41%) | 
  │ └ sirius::Potential::update                                         |       32.92 ms →       31.36 ms   (-4.74%) |       1   →       1              |       32.92 ms →       31.36 ms   (-4.74%) | 
  │   └ sirius::Potential::generate_local_potential                     |       32.50 ms →       30.94 ms   (-4.79%) |       1   →       1              |       32.50 ms →       30.94 ms   (-4.79%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       26.61 ms →       26.49 ms   (-0.45%) |       1   →       1              |       26.61 ms →       26.49 ms   (-0.45%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        5.36 ms →        3.89 ms  (-27.47%) |       1   →       1              |        5.36 ms →        3.89 ms  (-27.47%) | 
  ├ sirius::Density                                                     |       39.80 ms →       36.33 ms   (-8.71%) |       1   →       1              |       39.80 ms →       36.33 ms   (-8.71%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.82 ms →        2.82 ms   (+0.05%) |       2   →       2              |        5.64 ms →        5.65 ms   (+0.05%) | 
+ │ └ sirius::Density::update                                           |       34.01 ms →       30.55 ms  (-10.19%) |       1   →       1              |       34.01 ms →       30.55 ms  (-10.19%) | 
+ │   └ sirius::Density::generate_pseudo_core_charge_density            |       33.80 ms →       30.27 ms  (-10.43%) |       1   →       1              |       33.80 ms →       30.27 ms  (-10.43%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |       78.37 μs →       76.27 μs   (-2.68%) |       1   →       1              |       78.37 μs →       76.27 μs   (-2.68%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       26.99 ms →       26.18 ms   (-3.02%) |       1   →       1              |       26.99 ms →       26.18 ms   (-3.02%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        6.42 ms →        3.67 ms  (-42.84%) |       1   →       1              |        6.42 ms →        3.67 ms  (-42.84%) | 
  ├ sirius::Density::initial_density                                    |       58.66 ms →       54.63 ms   (-6.87%) |       1   →       1              |       58.66 ms →       54.63 ms   (-6.87%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       27.68 ms →       26.74 ms   (-3.39%) |       1   →       1              |       27.68 ms →       26.74 ms   (-3.39%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.79 ms →        4.63 ms  (-19.98%) |       2   →       2              |       11.58 ms →        9.26 ms  (-19.98%) | 
  │ └ sirius::Periodic_function::integrate                              |        5.76 ms →        5.23 ms   (-9.24%) |       1   →       1              |        5.76 ms →        5.23 ms   (-9.24%) | 
  ├ sirius::Potential::generate                                         |      365.77 ms →      362.19 ms   (-0.98%) |       1   →       1              |      365.77 ms →      362.19 ms   (-0.98%) | 
+ │ ├ sirius::Potential::poisson                                        |       38.54 ms →       33.84 ms  (-12.20%) |       1   →       1              |       38.54 ms →       33.84 ms  (-12.20%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        6.17 ms →        3.66 ms  (-40.65%) |       1   →       1              |        6.17 ms →        3.66 ms  (-40.65%) | 
+ │ │ └ sirius::Periodic_function|inner                                 |        5.93 ms →        4.63 ms  (-21.91%) |       1   →       1              |        5.93 ms →        4.63 ms  (-21.91%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.85 ms →        4.62 ms   (-4.55%) |       1   →       1              |        4.85 ms →        4.62 ms   (-4.55%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.83 ms →        4.62 ms   (-4.44%) |       1   →       1              |        4.83 ms →        4.62 ms   (-4.44%) | 
  │ ├ sirius::Periodic_function::add                                    |      775.75 μs →      770.03 μs   (-0.74%) |       2   →       2              |        1.55 ms →        1.54 ms   (-0.74%) | 
  │ ├ sirius::Potential::xc                                             |       51.27 ms →       53.28 ms   (+3.92%) |       1   →       1              |       51.27 ms →       53.28 ms   (+3.92%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       50.11 ms →       52.09 ms   (+3.95%) |       1   →       1              |       50.11 ms →       52.09 ms   (+3.95%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.58 ms →        2.54 ms   (-1.35%) |       2   →       2              |        5.16 ms →        5.09 ms   (-1.35%) | 
- │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.09 ms →        4.85 ms  (+18.44%) |       1   →       1              |        4.09 ms →        4.85 ms  (+18.44%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.41 ms →        3.58 ms   (+5.00%) |       1   →       1              |        3.41 ms →        3.58 ms   (+5.00%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      269.62 ms →      268.51 ms   (-0.41%) |       1   →       1              |      269.62 ms →      268.51 ms   (-0.41%) | 
- │ └ sirius::Potential::generate_PAW_effective_potential               |      142.00 ns →      177.00 ns  (+24.65%) |       1   →       1              |      142.00 ns →      177.00 ns  (+24.65%) | 
+ ├ sirius::Hamiltonian0                                                |        8.50 ms →        6.31 ms  (-25.77%) |       1   →       1              |        8.50 ms →        6.31 ms  (-25.77%) | 
+ │ ├ sirius::Local_operator                                            |        7.90 ms →        5.84 ms  (-26.07%) |       1   →       1              |        7.90 ms →        5.84 ms  (-26.07%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.73 ms →        2.74 ms   (+0.64%) |       1   →       1              |        2.73 ms →        2.74 ms   (+0.64%) | 
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        3.92 ms →        2.35 ms  (-39.97%) |       1   →       1              |        3.92 ms →        2.35 ms  (-39.97%) | 
+ │ ├ sirius::Non_local_operator                                        |      165.45 μs →       75.39 μs  (-54.43%) |       2   →       2              |      330.89 μs →      150.78 μs  (-54.43%) | 
  │ ├ sirius::D_operator::initialize                                    |      107.48 μs →      109.11 μs   (+1.52%) |       1   →       1              |      107.48 μs →      109.11 μs   (+1.52%) | 
- │ └ sirius::Q_operator::initialize                                    |       89.31 μs →      125.43 μs  (+40.44%) |       1   →       1              |       89.31 μs →      125.43 μs  (+40.44%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.29 s  →        1.29 s    (-0.11%) |       1   →       1              |        1.29 s  →        1.29 s    (-0.11%) | 
+ │ ├ sirius::Hamiltonian_k                                             |       58.87 ms →       31.01 ms  (-47.33%) |       1   →       1              |       58.87 ms →       31.01 ms  (-47.33%) | 
- │ │ ├ sirius::Local_operator::prepare_k                               |      216.32 μs →      284.86 μs  (+31.69%) |       1   →       1              |      216.32 μs →      284.86 μs  (+31.69%) | 
+ │ │ └ sirius::Beta_projectors_base::prepare                           |       58.65 ms →       30.72 ms  (-47.62%) |       1   →       1              |       58.65 ms →       30.72 ms  (-47.62%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.23 s  →        1.26 s    (+2.15%) |       1   →       1              |        1.23 s  →        1.26 s    (+2.15%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       78.36 ms →       82.46 ms   (+5.23%) |       4   →       4              |      313.46 ms →      329.86 ms   (+5.23%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       45.45 ms →       48.35 ms   (+6.39%) |       1   →       1              |       45.45 ms →       48.35 ms   (+6.39%) | 
+ │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        8.95 ms →        7.62 ms  (-14.86%) |       1   →       1              |        8.95 ms →        7.62 ms  (-14.86%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      354.21 ms →      334.85 ms   (-5.47%) |       1   →       1              |      354.21 ms →      334.85 ms   (-5.47%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      248.33 ms →      246.18 ms   (-0.87%) |       1   →       1              |      248.33 ms →      246.18 ms   (-0.87%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.96 μs →        3.60 μs   (-9.24%) |       1   →       1              |        3.96 μs →        3.60 μs   (-9.24%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.94 μs →        2.61 μs  (-11.09%) |       1   →       1              |        2.94 μs →        2.61 μs  (-11.09%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      479.00 ns →      472.00 ns   (-1.46%) |       1   →       1              |      479.00 ns →      472.00 ns   (-1.46%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      601.00 ns →      594.00 ns   (-1.16%) |       1   →       1              |      601.00 ns →      594.00 ns   (-1.16%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.18 ms →        3.27 ms   (+2.65%) |       1   →       1              |        3.18 ms →        3.27 ms   (+2.65%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.26 ms →       21.23 ms   (-0.16%) |       1   →       1              |       21.26 ms →       21.23 ms   (-0.16%) | 
+ │ │ │ └ sirius::Non_local_operator::apply                             |       40.70 ms →       32.07 ms  (-21.21%) |       2   →       2              |       81.40 ms →       64.13 ms  (-21.21%) | 
+ │ │ ├ sirius::Band::set_subspace_mtrx                                 |       17.46 ms →       14.40 ms  (-17.50%) |       2   →       2              |       34.92 ms →       28.81 ms  (-17.50%) | 
  │ │ │ ├ sddk::wf_inner                                                |       17.25 ms                             |       2                          |       34.49 ms                             | 
  │ │ │ │ ├ sddk::wf_inner|scale                                        |       21.00 ns                             |       2                          |       42.00 ns                             | 
  │ │ │ │ ├ sddk::wf_inner|pw                                           |       17.10 ms                             |       2                          |       34.19 ms                             | 
  │ │ │ │ └ sddk::wf_inner|scale_back                                   |       20.00 ns                             |       2                          |       40.00 ns                             | 
  │ │ │ └ sddk::inner                                                   |                        14.19 ms            |                   2              |                        28.38 ms            | 
  │ │ │   └ sddk::inner|local                                           |                        23.76 μs            |                   2              |                        47.51 μs            | 
- │ │ ├ Eigensolver_cuda|zhegvdx                                        |      206.40 ms →      233.65 ms  (+13.20%) |       1   →       1              |      206.40 ms →      233.65 ms  (+13.20%) | 
  │ │ ├ sddk::wf_trans                                                  |        2.61 ms                             |       1                          |        2.61 ms                             | 
  │ │ │ └ sddk::wf_trans|pw                                             |        2.60 ms                             |       1                          |        2.60 ms                             | 
  │ │ └ sddk::transform                                                 |                         5.26 ms            |                   1              |                         5.26 ms            | 
  │ │   ├ sddk::transform|init                                          |                        18.56 μs            |                   1              |                        18.56 μs            | 
  │ │   └ sddk::transform|local                                         |                        17.48 μs            |                   1              |                        17.48 μs            | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      466.00 ns →      518.00 ns  (+11.16%) |       1   →       1              |      466.00 ns →      518.00 ns  (+11.16%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |       62.75 s  →       64.85 s    (+3.33%) |       1   →       1              |       62.75 s  →       64.85 s    (+3.33%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.46 ms →        2.44 ms   (-0.99%) |      19   →      19              |       46.74 ms →       46.28 ms   (-0.99%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        2.96 s  →        2.93 s    (-1.09%) |      21   →      22     (+4.76%) |       62.26 s  →       64.51 s    (+3.62%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        4.73 ms →        5.22 ms  (+10.27%) |      21   →      22     (+4.76%) |       99.38 ms →      114.81 ms  (+15.53%) | 
- │ │ │ ├ sirius::Local_operator                                        |        4.18 ms →        4.51 ms   (+7.82%) |      21   →      22     (+4.76%) |       87.78 ms →       99.15 ms  (+12.96%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      549.25 μs →      551.58 μs   (+0.42%) |      21   →      22     (+4.76%) |       11.53 ms →       12.13 ms   (+5.21%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.65 ms →        2.81 ms   (+5.97%) |      21   →      22     (+4.76%) |       55.63 ms →       61.76 ms  (+11.01%) | 
- │ │ │ ├ sirius::Non_local_operator                                    |      117.59 μs →      212.60 μs  (+80.79%) |      42   →      44     (+4.76%) |        4.94 ms →        9.35 ms  (+89.40%) | 
+ │ │ │ ├ sirius::D_operator::initialize                                |      133.77 μs →      110.34 μs  (-17.52%) |      21   →      22     (+4.76%) |        2.81 ms →        2.43 ms  (-13.59%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       95.00 μs →       97.66 μs   (+2.80%) |      21   →      22     (+4.76%) |        1.99 ms →        2.15 ms   (+7.70%) | 
  │ │ ├ sirius::Band::solve                                             |        1.75 s  →        1.71 s    (-2.26%) |      21   →      22     (+4.76%) |       36.77 s  →       37.65 s    (+2.39%) | 
+ │ │ │ ├ sirius::Hamiltonian_k                                         |      223.48 μs →      199.12 μs  (-10.90%) |      21   →      22     (+4.76%) |        4.69 ms →        4.38 ms   (-6.66%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      214.68 μs →      190.31 μs  (-11.35%) |      21   →      22     (+4.76%) |        4.51 ms →        4.19 ms   (-7.13%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        6.39 μs →        6.51 μs   (+1.80%) |      21   →      22     (+4.76%) |      134.29 μs →      143.22 μs   (+6.65%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.63 s  →        1.57 s    (-3.51%) |      21   →      22     (+4.76%) |       34.13 s  →       34.51 s    (+1.09%) | 
- │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       66.04 ms →       78.45 ms  (+18.80%) |      21   →      22     (+4.76%) |        1.39 s  →        1.73 s   (+24.45%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.18 ms →        5.85 ms  (-18.58%) |     126   →     154    (+22.22%) |      905.30 ms →      900.92 ms   (-0.48%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       18.29 ms →       12.60 ms  (-31.11%) |      21   →      22     (+4.76%) |      384.05 ms →      277.17 ms  (-27.83%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      458.24 μs →      464.09 μs   (+1.28%) |      21   →      22     (+4.76%) |        9.62 ms →       10.21 ms   (+6.10%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        8.28 ms →        5.59 ms  (-32.42%) |      42   →      44     (+4.76%) |      347.72 ms →      246.18 ms  (-29.20%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.53 s  →        1.46 s    (-4.82%) |      21   →      22     (+4.76%) |       32.18 s  →       32.09 s    (-0.28%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       49.84 ms →       99.56 ms  (+99.75%) |     361   →     180    (-50.14%) |       17.99 s  →       17.92 s    (-0.40%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       29.51 ms →       74.77 ms (+153.40%) |     361   →     180    (-50.14%) |       10.65 s  →       13.46 s   (+26.35%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.85 μs →        2.03 μs  (+10.16%) |     361   →     180    (-50.14%) |      666.72 μs →      366.22 μs  (-45.07%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.52 μs →        1.76 μs  (+15.70%) |     361   →     180    (-50.14%) |      548.25 μs →      316.28 μs  (-42.31%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      353.76 ns →      398.32 ns  (+12.60%) |     361   →     180    (-50.14%) |      127.71 μs →       71.70 μs  (-43.86%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      466.35 ns →      677.73 ns  (+45.33%) |     361   →     180    (-50.14%) |      168.35 μs →      121.99 μs  (-27.54%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.82 ms →        2.85 ms   (+1.02%) |     361   →     180    (-50.14%) |        1.02 s  →      512.43 ms  (-49.63%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.27 ms →        5.40 ms  (+65.00%) |     361   →     180    (-50.14%) |        1.18 s  →      971.13 ms  (-17.73%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.12 ms →        8.26 ms  (+16.14%) |     722   →     360    (-50.14%) |        5.14 s  →        2.98 s   (-42.09%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |        6.55 ms →        7.73 ms  (+18.05%) |     361   →     180    (-50.14%) |        2.36 s  →        1.39 s   (-41.14%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        1.02 ms                             |     701                          |      717.79 ms                             | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       40.20 ns                             |     701                          |       28.18 μs                             | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |      859.45 μs                             |     701                          |      602.47 ms                             | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       45.10 ns                             |     701                          |       31.61 μs                             | 
  │ │ │ │   │ ├ sddk::inner                                             |                         1.05 ms            |                 338              |                       355.99 ms            | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |                        22.04 μs            |                 338              |                         7.45 ms            | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      145.07 μs →      291.87 μs (+101.20%) |     361   →     180    (-50.14%) |       52.37 ms →       52.54 ms   (+0.32%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        2.35 ms →        2.77 ms  (+17.79%) |     361   →     180    (-50.14%) |      849.63 ms →      498.99 ms  (-41.27%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |        2.18 ms                             |     340                          |      742.19 ms                             | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      726.92 μs                             |    1.02 K                        |      741.46 ms                             | 
  │ │ │ │   │ └ sddk::transform                                         |                         3.06 ms            |                 158              |                       482.75 ms            | 
  │ │ │ │   │   ├ sddk::transform|init                                  |                        17.34 μs            |                 158              |                         2.74 ms            | 
  │ │ │ │   │   └ sddk::transform|local                                 |                         7.66 μs            |                 474              |                         3.63 ms            | 
- │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.29 ms →        1.51 ms  (+17.21%) |     361   →     180    (-50.14%) |      465.41 ms →      272.00 ms  (-41.56%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        1.25 ms                             |     361                          |      449.67 ms                             | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       42.06 ns                             |     361                          |       15.18 μs                             | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        1.08 ms                             |     361                          |      390.80 ms                             | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       46.13 ns                             |     361                          |       16.65 μs                             | 
  │ │ │ │   │ └ sddk::inner                                             |                         1.44 ms            |                 180              |                       259.41 ms            | 
  │ │ │ │   │   └ sddk::inner|local                                     |                        21.45 μs            |                 180              |                         3.86 ms            | 
- │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       27.81 ms →       63.72 ms (+129.14%) |     361   →     180    (-50.14%) |       10.04 s  →       11.47 s   (+14.25%) | 
- │ │ │ │   ├ sirius::residuals                                         |        2.53 ms →        3.38 ms  (+33.24%) |     346   →     179    (-48.27%) |      876.51 ms →      604.20 ms  (-31.07%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |        1.24 ms                             |     342                          |      423.59 ms                             | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      618.04 μs                             |     684                          |      422.74 ms                             | 
  │ │ │ │   │ ├ sddk::transform                                         |                         1.82 ms            |                 179              |                       325.54 ms            | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |                        14.64 μs            |                 179              |                         2.62 ms            | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |                        10.07 μs            |                 358              |                         3.61 ms            | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.20 ms →        1.42 ms  (+18.73%) |     342   →     179    (-47.66%) |      409.82 ms →      254.68 ms  (-37.86%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        4.89 ms →        6.16 ms  (+25.92%) |      90   →      70    (-22.22%) |      440.12 ms →      431.05 ms   (-2.06%) | 
  │ │ │ │     ├ sddk::wf_trans                                          |        2.72 ms                             |     159                          |      432.46 ms                             | 
  │ │ │ │     │ └ sddk::wf_trans|pw                                     |        1.90 ms                             |     228                          |      432.18 ms                             | 
  │ │ │ │     └ sddk::transform                                         |                         3.60 ms            |                 118              |                       425.02 ms            | 
  │ │ │ │       ├ sddk::transform|init                                  |                         9.96 μs            |                 118              |                         1.18 ms            | 
  │ │ │ │       └ sddk::transform|local                                 |                         8.22 μs            |                 166              |                         1.36 ms            | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      556.10 ns →      747.82 ns  (+34.48%) |      21   →      22     (+4.76%) |       11.68 μs →       16.45 μs  (+40.88%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       19.23 μs →       28.74 μs  (+49.45%) |      21   →      22     (+4.76%) |      403.86 μs →      632.30 μs  (+56.56%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.53 ms →        1.53 ms   (+0.06%) |      21   →      22     (+4.76%) |       32.11 ms →       33.66 ms   (+4.82%) | 
  │ │ ├ sirius::Density::generate                                       |      563.00 ms →      571.34 ms   (+1.48%) |      21   →      22     (+4.76%) |       11.82 s  →       12.57 s    (+6.31%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      414.56 ms →      405.20 ms   (-2.26%) |      21   →      22     (+4.76%) |        8.71 s  →        8.91 s    (+2.40%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        7.30 μs →        8.30 μs  (+13.65%) |      21   →      22     (+4.76%) |      153.37 μs →      182.60 μs  (+19.06%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        6.61 μs →        7.76 μs  (+17.35%) |      21   →      22     (+4.76%) |      138.88 μs →      170.74 μs  (+22.93%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       21.31 ms →       47.26 ms (+121.77%) |      21   →      22     (+4.76%) |      447.49 ms →        1.04 s  (+132.33%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.89 μs →        7.28 μs  (-26.45%) |      21   →      22     (+4.76%) |      207.71 μs →      160.05 μs  (-22.95%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        3.64 ms →        8.09 ms (+122.42%) |      21   →      22     (+4.76%) |       76.34 ms →      177.89 ms (+133.01%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       16.62 ms →       38.12 ms (+129.40%) |      21   →      22     (+4.76%) |      348.95 ms →      838.61 ms (+140.32%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |        1.04 μs →      540.32 ns  (-47.92%) |      21   →      22     (+4.76%) |       21.79 μs →       11.89 μs  (-45.44%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      123.63 ms →       98.73 ms  (-20.14%) |      21   →      22     (+4.76%) |        2.60 s  →        2.17 s   (-16.34%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.93 ms →        2.28 ms  (+17.91%) |      21   →      22     (+4.76%) |       40.56 ms →       50.11 ms  (+23.53%) | 
  │ │ │ │ └ sirius::Density::augment                                    |      234.14 ms →      220.95 ms   (-5.63%) |      21   →      22     (+4.76%) |        4.92 s  →        4.86 s    (-1.14%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |      233.92 ms →      220.73 ms   (-5.64%) |      21   →      22     (+4.76%) |        4.91 s  →        4.86 s    (-1.14%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      120.57 ms →      137.79 ms  (+14.28%) |      21   →      22     (+4.76%) |        2.53 s  →        3.03 s   (+19.73%) | 
- │ │ │ │ └ sirius::symmetrize_function|fpw                             |      120.57 ms →      137.79 ms  (+14.28%) |      21   →      22     (+4.76%) |        2.53 s  →        3.03 s   (+19.72%) | 
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       37.43 ms →       52.91 ms  (+41.38%) |      21   →      22     (+4.76%) |      785.93 ms →        1.16 s   (+48.12%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       69.75 ms →       71.65 ms   (+2.73%) |      21   →      22     (+4.76%) |        1.46 s  →        1.58 s    (+7.62%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.74 ms →       12.59 ms   (-1.22%) |      21   →      22     (+4.76%) |      267.57 ms →      276.89 ms   (+3.48%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.71 ms →       23.52 ms   (-0.80%) |      21   →      22     (+4.76%) |      497.97 ms →      517.52 ms   (+3.93%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        4.15 ms →        4.83 ms  (+16.18%) |      21   →      22     (+4.76%) |       87.23 ms →      106.17 ms  (+21.71%) | 
  │ │ ├ sirius::Density::mix                                            |      134.36 ms →      134.69 ms   (+0.24%) |      21   →      22     (+4.76%) |        2.82 s  →        2.96 s    (+5.02%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      768.25 μs →      685.09 μs  (-10.82%) |      21   →      22     (+4.76%) |       16.13 ms →       15.07 ms   (-6.58%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |        4.69 ms →        4.72 ms   (+0.76%) |     259   →     274     (+5.79%) |        1.21 s  →        1.29 s    (+6.59%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.62 ms →        4.62 ms   (-0.06%) |     259   →     274     (+5.79%) |        1.20 s  →        1.27 s    (+5.73%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.62 ms →        4.62 ms   (-0.06%) |     259   →     274     (+5.79%) |        1.20 s  →        1.27 s    (+5.73%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        5.10 ms →        6.62 ms  (+29.81%) |      21   →      22     (+4.76%) |      107.02 ms →      145.54 ms  (+35.99%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        4.47 ms →        5.85 ms  (+30.71%) |      21   →      22     (+4.76%) |       93.95 ms →      128.66 ms  (+36.94%) | 
  │ │ ├ sirius::Potential::generate                                     |      358.29 ms →      354.14 ms   (-1.16%) |      21   →      22     (+4.76%) |        7.52 s  →        7.79 s    (+3.55%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |       38.27 ms →       34.21 ms  (-10.63%) |      21   →      22     (+4.76%) |      803.76 ms →      752.54 ms   (-6.37%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        5.97 ms →        3.79 ms  (-36.56%) |      21   →      22     (+4.76%) |      125.46 ms →       83.39 ms  (-33.53%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner                             |        5.95 ms →        4.87 ms  (-18.15%) |      21   →      22     (+4.76%) |      124.96 ms →      107.14 ms  (-14.26%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.84 ms →        4.64 ms   (-3.95%) |      21   →      22     (+4.76%) |      101.54 ms →      102.17 ms   (+0.62%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.83 ms →        4.64 ms   (-3.95%) |      21   →      22     (+4.76%) |      101.51 ms →      102.15 ms   (+0.62%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      782.44 μs →      766.02 μs   (-2.10%) |      42   →      44     (+4.76%) |       32.86 ms →       33.70 ms   (+2.56%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       44.91 ms →       45.30 ms   (+0.86%) |      21   →      22     (+4.76%) |      943.17 ms →      996.54 ms   (+5.66%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       43.75 ms →       44.12 ms   (+0.84%) |      21   →      22     (+4.76%) |      918.76 ms →      970.64 ms   (+5.65%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |      678.00 μs →      683.48 μs   (+0.81%) |      42   →      44     (+4.76%) |       28.48 ms →       30.07 ms   (+5.61%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.40 ms →        5.04 ms  (+14.69%) |      21   →      22     (+4.76%) |       92.30 ms →      110.90 ms  (+20.15%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.59 ms →        3.63 ms   (+1.07%) |      21   →      22     (+4.76%) |       75.41 ms →       79.84 ms   (+5.88%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.55 ms →      268.04 ms   (-0.19%) |      21   →      22     (+4.76%) |        5.64 s  →        5.90 s    (+4.56%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      146.14 ns →      192.82 ns  (+31.94%) |      21   →      22     (+4.76%) |        3.07 μs →        4.24 μs  (+38.22%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |       96.03 ms →       97.75 ms   (+1.80%) |      21   →      22     (+4.76%) |        2.02 s  →        2.15 s    (+6.65%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |       96.02 ms →       97.75 ms   (+1.80%) |      21   →      22     (+4.76%) |        2.02 s  →        2.15 s    (+6.65%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.21 ms →       13.26 ms   (+0.43%) |      21   →      22     (+4.76%) |      277.36 ms →      291.81 ms   (+5.21%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       69.69 ms →       71.30 ms   (+2.32%) |      21   →      22     (+4.76%) |        1.46 s  →        1.57 s    (+7.19%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.49 ms →       12.56 ms   (+0.48%) |      21   →      22     (+4.76%) |      262.39 ms →      276.21 ms   (+5.27%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        4.30 ms →        4.52 ms   (+5.21%) |      21   →      22     (+4.76%) |       90.32 ms →       99.55 ms  (+10.22%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.63 ms →        4.78 ms   (+3.34%) |     147   →     154     (+4.76%) |      680.24 ms →      736.42 ms   (+8.26%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.55 ms →        4.76 ms   (+4.45%) |     147   →     154     (+4.76%) |      669.35 ms →      732.43 ms   (+9.42%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.55 ms →        4.76 ms   (+4.45%) |     147   →     154     (+4.76%) |      669.25 ms →      732.32 ms   (+9.42%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.79 ms →        4.54 ms   (-5.22%) |      63   →      66     (+4.76%) |      301.87 ms →      299.73 ms   (-0.71%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.72 ms →        4.54 ms   (-3.97%) |      63   →      66     (+4.76%) |      297.56 ms →      299.34 ms   (+0.60%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.54 ms →        4.56 ms   (+0.33%) |      21   →      22     (+4.76%) |       95.42 ms →      100.29 ms   (+5.10%) | 
  │ │ └ sirius::Density::get_magnetisation                              |       76.64 μs →       75.52 μs   (-1.46%) |      21   →      22     (+4.76%) |        1.61 ms →        1.66 ms   (+3.24%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |       71.57 μs →       70.35 μs   (-1.71%) |      21   →      22     (+4.76%) |        1.50 ms →        1.55 ms   (+2.97%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.60 ms →        5.16 ms   (-7.72%) |       2   →       2              |       11.19 ms →       10.33 ms   (-7.72%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.56 ms →        5.01 ms   (+9.88%) |       6   →       6              |       27.35 ms →       30.05 ms   (+9.88%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.55 ms →        5.01 ms   (+9.99%) |       6   →       6              |       27.30 ms →       30.03 ms   (+9.99%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.55 ms →        5.00 ms   (+9.99%) |       6   →       6              |       27.30 ms →       30.03 ms   (+9.99%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.89 ms →        4.83 ms   (-1.05%) |       3   →       3              |       14.66 ms →       14.50 ms   (-1.05%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.73 ms →        4.83 ms   (+2.03%) |       3   →       3              |       14.20 ms →       14.49 ms   (+2.03%) | 
  ├ sirius::Periodic_function|inner                                     |        4.56 ms →        4.96 ms   (+8.67%) |       2   →       2              |        9.13 ms →        9.92 ms   (+8.67%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.55 ms →        4.96 ms   (+8.86%) |       2   →       2              |        9.11 ms →        9.91 ms   (+8.86%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.55 ms →        4.96 ms   (+8.86%) |       2   →       2              |        9.10 ms →        9.91 ms   (+8.86%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.74 ms →        4.87 ms   (+2.72%) |       1   →       1              |        4.74 ms →        4.87 ms   (+2.72%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.74 ms →        4.86 ms   (+2.71%) |       1   →       1              |        4.74 ms →        4.86 ms   (+2.71%) | 
- └ sirius::finalize                                                    |      166.74 ms →      719.20 ms (+331.33%) |       1   →       1              |      166.74 ms →      719.20 ms (+331.33%) | 
  ====================================================================================================================================================================================================
```
