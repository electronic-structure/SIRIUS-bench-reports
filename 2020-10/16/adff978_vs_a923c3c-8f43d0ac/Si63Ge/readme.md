# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |       71.30 s  →       72.55 s    (+1.76%) |       1   →       1              |       71.30 s  →       72.55 s    (+1.76%) | 
  ├ sirius::initialize                                                  |        2.91 s  →        2.97 s    (+1.93%) |       1   →       1              |        2.91 s  →        2.97 s    (+1.93%) | 
  ├ sirius::Simulation_context::initialize                              |        3.66 s  →        3.59 s    (-1.98%) |       1   →       1              |        3.66 s  →        3.59 s    (-1.98%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       35.28 ms →       28.19 ms  (-20.10%) |       1   →       1              |       35.28 ms →       28.19 ms  (-20.10%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      226.29 ms →      123.98 ms  (-45.21%) |       1   →       1              |      226.29 ms →      123.98 ms  (-45.21%) | 
+ │ │ ├ sirius::Atom_type::init                                         |      104.80 ms →       52.61 ms  (-49.80%) |       2   →       2              |      209.60 ms →      105.21 ms  (-49.80%) | 
- │ │ └ sirius::Unit_cell::update                                       |       16.59 ms →       18.66 ms  (+12.48%) |       1   →       1              |       16.59 ms →       18.66 ms  (+12.48%) | 
- │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.60 ms →        5.18 ms  (+44.05%) |       1   →       1              |        3.60 ms →        5.18 ms  (+44.05%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       12.95 ms →       13.43 ms   (+3.76%) |       1   →       1              |       12.95 ms →       13.43 ms   (+3.76%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       12.88 ms →       13.37 ms   (+3.78%) |       1   →       1              |       12.88 ms →       13.37 ms   (+3.78%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.75 ms →        2.73 ms   (-0.71%) |       1   →       1              |        2.75 ms →        2.73 ms   (-0.71%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      512.61 μs →      525.58 μs   (+2.53%) |       1   →       1              |      512.61 μs →      525.58 μs   (+2.53%) | 
+ │ │       └ sirius::Unit_cell_symmetry|mag                            |       17.22 μs →       15.31 μs  (-11.10%) |       1   →       1              |       17.22 μs →       15.31 μs  (-11.10%) | 
  │ └ sirius::Simulation_context::update                                |        3.30 s  →        3.22 s    (-2.42%) |       1   →       1              |        3.30 s  →        3.22 s    (-2.42%) | 
  │   ├ sirius::Unit_cell::update                                       |        6.86 ms →        7.02 ms   (+2.38%) |       1   →       1              |        6.86 ms →        7.02 ms   (+2.38%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.47 ms →        3.65 ms   (+5.19%) |       1   →       1              |        3.47 ms →        3.65 ms   (+5.19%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.33 ms →        3.33 ms   (-0.03%) |       1   →       1              |        3.33 ms →        3.33 ms   (-0.03%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.26 ms →        3.26 ms   (-0.07%) |       1   →       1              |        3.26 ms →        3.26 ms   (-0.07%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.73 ms →        2.72 ms   (-0.30%) |       1   →       1              |        2.73 ms →        2.72 ms   (-0.30%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      496.88 μs →      502.74 μs   (+1.18%) |       1   →       1              |      496.88 μs →      502.74 μs   (+1.18%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       14.29 μs →       14.34 μs   (+0.34%) |       1   →       1              |       14.29 μs →       14.34 μs   (+0.34%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      212.00 ms →      212.99 ms   (+0.47%) |       2   →       2              |      424.00 ms →      425.98 ms   (+0.47%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.15 ms →       15.19 ms   (+0.24%) |       2   →       2              |       30.30 ms →       30.37 ms   (+0.24%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.26 ms →       13.27 ms   (+0.10%) |       1   →       1              |       13.26 ms →       13.27 ms   (+0.10%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.28 ms →       56.38 ms   (+0.17%) |       2   →       2              |      112.57 ms →      112.76 ms   (+0.17%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.06 ms →       45.11 ms   (+0.09%) |       2   →       2              |       90.13 ms →       90.21 ms   (+0.09%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.27 ms →       60.17 ms   (-0.18%) |       4   →       4              |      241.10 ms →      240.67 ms   (-0.18%) | 
  │   ├ sddk::Gvec::init                                                |       94.27 ms →       93.41 ms   (-0.91%) |       2   →       2              |      188.53 ms →      186.82 ms   (-0.91%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       70.06 ms →       70.05 ms   (-0.01%) |       2   →       2              |      140.11 ms →      140.10 ms   (-0.01%) | 
  │   ├ sddk::Gvec_shells                                               |       93.18 ms →       98.30 ms   (+5.50%) |       1   →       1              |       93.18 ms →       98.30 ms   (+5.50%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.99 ms →        1.96 ms   (-1.73%) |       1   →       1              |        1.99 ms →        1.96 ms   (-1.73%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      514.15 ms →      464.33 ms   (-9.69%) |       2   →       2              |        1.03 s  →      928.65 ms   (-9.69%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |      147.47 ms →      133.16 ms   (-9.70%) |       1   →       1              |      147.47 ms →      133.16 ms   (-9.70%) | 
+ │ ├ sirius::K_point::K_point                                          |        1.90 μs →        1.28 μs  (-32.72%) |       4   →       4              |        7.60 μs →        5.12 μs  (-32.72%) | 
  │ └ sirius::K_point_set::initialize                                   |      147.38 ms →      133.07 ms   (-9.71%) |       1   →       1              |      147.38 ms →      133.07 ms   (-9.71%) | 
  │   └ sirius::K_point::initialize                                     |       28.18 ms →       28.66 ms   (+1.73%) |       1   →       1              |       28.18 ms →       28.66 ms   (+1.73%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       11.13 ms →       11.01 ms   (-1.06%) |       1   →       1              |       11.13 ms →       11.01 ms   (-1.06%) | 
  │     │ └ sddk::Gvec::init                                            |        4.98 ms →        5.02 ms   (+0.91%) |       1   →       1              |        4.98 ms →        5.02 ms   (+0.91%) | 
+ │     ├ sddk::matrix_storage::matrix_storage                          |       11.91 μs →        7.37 μs  (-38.09%) |       1   →       1              |       11.91 μs →        7.37 μs  (-38.09%) | 
  │     └ sirius::K_point::update                                       |       14.25 ms →       14.76 ms   (+3.61%) |       1   →       1              |       14.25 ms →       14.76 ms   (+3.61%) | 
  │       └ sirius::Beta_projectors                                     |       10.27 ms →       10.78 ms   (+5.00%) |       1   →       1              |       10.27 ms →       10.78 ms   (+5.00%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.31 ms →        8.22 ms   (-1.10%) |       1   →       1              |        8.31 ms →        8.22 ms   (-1.10%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.53 ms →        2.57 ms   (+1.69%) |       2   →       2              |        5.06 ms →        5.14 ms   (+1.69%) | 
  ├ sirius::Potential                                                   |       49.82 ms →       52.76 ms   (+5.90%) |       1   →       1              |       49.82 ms →       52.76 ms   (+5.90%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.95 ms →        2.92 ms   (-1.21%) |       6   →       6              |       17.73 ms →       17.51 ms   (-1.21%) | 
- │ └ sirius::Potential::update                                         |       31.49 ms →       34.68 ms  (+10.15%) |       1   →       1              |       31.49 ms →       34.68 ms  (+10.15%) | 
- │   └ sirius::Potential::generate_local_potential                     |       31.07 ms →       34.28 ms  (+10.32%) |       1   →       1              |       31.07 ms →       34.28 ms  (+10.32%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       26.36 ms →       26.42 ms   (+0.21%) |       1   →       1              |       26.36 ms →       26.42 ms   (+0.21%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        4.17 ms →        7.34 ms  (+75.90%) |       1   →       1              |        4.17 ms →        7.34 ms  (+75.90%) | 
  ├ sirius::Density                                                     |       36.73 ms →       38.77 ms   (+5.55%) |       1   →       1              |       36.73 ms →       38.77 ms   (+5.55%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.84 ms →        2.83 ms   (-0.42%) |       2   →       2              |        5.67 ms →        5.65 ms   (-0.42%) | 
  │ └ sirius::Density::update                                           |       30.92 ms →       32.98 ms   (+6.67%) |       1   →       1              |       30.92 ms →       32.98 ms   (+6.67%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       30.68 ms →       32.67 ms   (+6.49%) |       1   →       1              |       30.68 ms →       32.67 ms   (+6.49%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |       77.35 μs →       77.80 μs   (+0.58%) |       1   →       1              |       77.35 μs →       77.80 μs   (+0.58%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       26.67 ms →       27.28 ms   (+2.31%) |       1   →       1              |       26.67 ms →       27.28 ms   (+2.31%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        3.60 ms →        4.99 ms  (+38.82%) |       1   →       1              |        3.60 ms →        4.99 ms  (+38.82%) | 
  ├ sirius::Density::initial_density                                    |       56.29 ms →       60.78 ms   (+7.99%) |       1   →       1              |       56.29 ms →       60.78 ms   (+7.99%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       27.44 ms →       27.58 ms   (+0.50%) |       1   →       1              |       27.44 ms →       27.58 ms   (+0.50%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.71 ms →        7.07 ms  (+50.13%) |       2   →       2              |        9.42 ms →       14.14 ms  (+50.13%) | 
  │ └ sirius::Periodic_function::integrate                              |        5.79 ms →        5.32 ms   (-8.13%) |       1   →       1              |        5.79 ms →        5.32 ms   (-8.13%) | 
  ├ sirius::Potential::generate                                         |      361.43 ms →      367.29 ms   (+1.62%) |       1   →       1              |      361.43 ms →      367.29 ms   (+1.62%) | 
- │ ├ sirius::Potential::poisson                                        |       34.57 ms →       40.16 ms  (+16.16%) |       1   →       1              |       34.57 ms →       40.16 ms  (+16.16%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.85 ms →        8.70 ms (+205.83%) |       1   →       1              |        2.85 ms →        8.70 ms (+205.83%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        5.90 ms →        5.40 ms   (-8.38%) |       1   →       1              |        5.90 ms →        5.40 ms   (-8.38%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.66 ms →        4.64 ms   (-0.36%) |       1   →       1              |        4.66 ms →        4.64 ms   (-0.36%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.65 ms →        4.63 ms   (-0.32%) |       1   →       1              |        4.65 ms →        4.63 ms   (-0.32%) | 
  │ ├ sirius::Periodic_function::add                                    |      793.50 μs →      739.33 μs   (-6.83%) |       2   →       2              |        1.59 ms →        1.48 ms   (-6.83%) | 
  │ ├ sirius::Potential::xc                                             |       51.40 ms →       51.75 ms   (+0.68%) |       1   →       1              |       51.40 ms →       51.75 ms   (+0.68%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       50.23 ms →       50.60 ms   (+0.73%) |       1   →       1              |       50.23 ms →       50.60 ms   (+0.73%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.56 ms →        2.55 ms   (-0.12%) |       2   →       2              |        5.11 ms →        5.11 ms   (-0.12%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.42 ms →        4.42 ms   (-0.11%) |       1   →       1              |        4.42 ms →        4.42 ms   (-0.11%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.62 ms →        2.83 ms  (-21.87%) |       1   →       1              |        3.62 ms →        2.83 ms  (-21.87%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      268.91 ms →      269.68 ms   (+0.29%) |       1   →       1              |      268.91 ms →      269.68 ms   (+0.29%) | 
+ │ └ sirius::Potential::generate_PAW_effective_potential               |      332.00 ns →      228.00 ns  (-31.33%) |       1   →       1              |      332.00 ns →      228.00 ns  (-31.33%) | 
+ ├ sirius::Hamiltonian0                                                |        8.79 ms →        6.26 ms  (-28.72%) |       1   →       1              |        8.79 ms →        6.26 ms  (-28.72%) | 
+ │ ├ sirius::Local_operator                                            |        7.81 ms →        5.79 ms  (-25.84%) |       1   →       1              |        7.81 ms →        5.79 ms  (-25.84%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.74 ms →        2.75 ms   (+0.32%) |       1   →       1              |        2.74 ms →        2.75 ms   (+0.32%) | 
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        3.84 ms →        2.29 ms  (-40.24%) |       1   →       1              |        3.84 ms →        2.29 ms  (-40.24%) | 
+ │ ├ sirius::Non_local_operator                                        |      346.81 μs →       71.80 μs  (-79.30%) |       2   →       2              |      693.63 μs →      143.59 μs  (-79.30%) | 
  │ ├ sirius::D_operator::initialize                                    |      121.21 μs →      117.58 μs   (-3.00%) |       1   →       1              |      121.21 μs →      117.58 μs   (-3.00%) | 
- │ └ sirius::Q_operator::initialize                                    |       92.07 μs →      128.46 μs  (+39.53%) |       1   →       1              |       92.07 μs →      128.46 μs  (+39.53%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.30 s  →        1.26 s    (-2.94%) |       1   →       1              |        1.30 s  →        1.26 s    (-2.94%) | 
+ │ ├ sirius::Hamiltonian_k                                             |       81.84 ms →       34.28 ms  (-58.11%) |       1   →       1              |       81.84 ms →       34.28 ms  (-58.11%) | 
- │ │ ├ sirius::Local_operator::prepare_k                               |      256.92 μs →      370.59 μs  (+44.24%) |       1   →       1              |      256.92 μs →      370.59 μs  (+44.24%) | 
+ │ │ └ sirius::Beta_projectors_base::prepare                           |       81.58 ms →       33.90 ms  (-58.44%) |       1   →       1              |       81.58 ms →       33.90 ms  (-58.44%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.22 s  →        1.23 s    (+0.77%) |       1   →       1              |        1.22 s  →        1.23 s    (+0.77%) | 
+ │ │ ├ sddk::matrix_storage::matrix_storage                            |      112.37 ms →       81.51 ms  (-27.46%) |       4   →       4              |      449.48 ms →      326.04 ms  (-27.46%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       37.32 ms →       36.65 ms   (-1.80%) |       1   →       1              |       37.32 ms →       36.65 ms   (-1.80%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        6.59 ms →        6.60 ms   (+0.19%) |       1   →       1              |        6.59 ms →        6.60 ms   (+0.19%) | 
+ │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      512.47 ms →      310.88 ms  (-39.34%) |       1   →       1              |      512.47 ms →      310.88 ms  (-39.34%) | 
+ │ │ │ ├ sirius::Local_operator::apply_h                               |      421.88 ms →      243.36 ms  (-42.32%) |       1   →       1              |      421.88 ms →      243.36 ms  (-42.32%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.48 μs →        4.02 μs  (+15.33%) |       1   →       1              |        3.48 μs →        4.02 μs  (+15.33%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.58 μs →        3.07 μs  (+18.65%) |       1   →       1              |        2.58 μs →        3.07 μs  (+18.65%) | 
- │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      335.00 ns →      503.00 ns  (+50.15%) |       1   →       1              |      335.00 ns →      503.00 ns  (+50.15%) | 
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      808.00 ns →      632.00 ns  (-21.78%) |       1   →       1              |      808.00 ns →      632.00 ns  (-21.78%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.02 ms →        3.27 ms   (+8.37%) |       1   →       1              |        3.02 ms →        3.27 ms   (+8.37%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::inner                           |       39.04 ms →       21.30 ms  (-45.43%) |       1   →       1              |       39.04 ms →       21.30 ms  (-45.43%) | 
+ │ │ │ └ sirius::Non_local_operator::apply                             |       24.24 ms →       21.45 ms  (-11.53%) |       2   →       2              |       48.49 ms →       42.90 ms  (-11.53%) | 
- │ │ ├ sirius::Band::set_subspace_mtrx                                 |        6.68 ms →       16.91 ms (+153.00%) |       2   →       2              |       13.37 ms →       33.82 ms (+153.00%) | 
- │ │ │ └ sddk::wf_inner                                                |        6.47 ms →       16.70 ms (+158.03%) |       2   →       2              |       12.94 ms →       33.40 ms (+158.03%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       20.00 ns →       37.00 ns  (+85.00%) |       2   →       2              |       40.00 ns →       74.00 ns  (+85.00%) | 
- │ │ │   ├ sddk::wf_inner|pw                                           |        6.35 ms →       16.57 ms (+160.91%) |       2   →       2              |       12.70 ms →       33.14 ms (+160.91%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       21.00 ns →       23.50 ns  (+11.90%) |       2   →       2              |       42.00 ns →       47.00 ns  (+11.90%) | 
- │ │ ├ Eigensolver_cuda|zhegvdx                                        |       63.74 ms →      251.24 ms (+294.14%) |       1   →       1              |       63.74 ms →      251.24 ms (+294.14%) | 
  │ │ └ sddk::wf_trans                                                  |        2.59 ms →        2.61 ms   (+0.58%) |       1   →       1              |        2.59 ms →        2.61 ms   (+0.58%) | 
  │ │   └ sddk::wf_trans|pw                                             |        2.59 ms →        2.60 ms   (+0.57%) |       1   →       1              |        2.59 ms →        2.60 ms   (+0.57%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      549.00 ns →      451.00 ns  (-17.85%) |       1   →       1              |      549.00 ns →      451.00 ns  (-17.85%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |       61.67 s  →       62.96 s    (+2.10%) |       1   →       1              |       61.67 s  →       62.96 s    (+2.10%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.47 ms →        2.45 ms   (-1.08%) |      19   →      19              |       46.97 ms →       46.46 ms   (-1.08%) | 
! │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.24 s  →        2.98 s    (-7.86%) |      19   →      21    (+10.53%) |       61.50 s  →       62.63 s    (+1.84%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        5.23 ms →        5.56 ms   (+6.21%) |      19   →      21    (+10.53%) |       99.41 ms →      116.70 ms  (+17.39%) | 
- │ │ │ ├ sirius::Local_operator                                        |        4.45 ms →        4.75 ms   (+6.82%) |      19   →      21    (+10.53%) |       84.57 ms →       99.84 ms  (+18.07%) | 
! │ │ │ │ ├ sirius::Smooth_periodic_function                            |      556.77 μs →      549.19 μs   (-1.36%) |      19   →      21    (+10.53%) |       10.58 ms →       11.53 ms   (+9.02%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.68 ms →        3.04 ms  (+13.49%) |      19   →      21    (+10.53%) |       50.95 ms →       63.91 ms  (+25.43%) | 
- │ │ │ ├ sirius::Non_local_operator                                    |      243.88 μs →      262.92 μs   (+7.80%) |      38   →      42    (+10.53%) |        9.27 ms →       11.04 ms  (+19.15%) | 
! │ │ │ ├ sirius::D_operator::initialize                                |      121.40 μs →      111.31 μs   (-8.31%) |      19   →      21    (+10.53%) |        2.31 ms →        2.34 ms   (+1.34%) | 
! │ │ │ └ sirius::Q_operator::initialize                                |       90.92 μs →       89.45 μs   (-1.61%) |      19   →      21    (+10.53%) |        1.73 ms →        1.88 ms   (+8.74%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.02 s  →        1.76 s   (-13.03%) |      19   →      21    (+10.53%) |       38.43 s  →       36.95 s    (-3.87%) | 
! │ │ │ ├ sirius::Hamiltonian_k                                         |      209.25 μs →      201.40 μs   (-3.76%) |      19   →      21    (+10.53%) |        3.98 ms →        4.23 ms   (+6.38%) | 
! │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      198.46 μs →      192.56 μs   (-2.97%) |      19   →      21    (+10.53%) |        3.77 ms →        4.04 ms   (+7.24%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        7.80 μs →        6.46 μs  (-17.17%) |      19   →      21    (+10.53%) |      148.16 μs →      135.64 μs   (-8.45%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.97 s  →        1.63 s   (-16.89%) |      19   →      21    (+10.53%) |       37.37 s  →       34.33 s    (-8.14%) | 
! │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       79.22 ms →       72.01 ms   (-9.11%) |      19   →      21    (+10.53%) |        1.51 s  →        1.51 s    (+0.46%) | 
! │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.98 ms →        7.32 ms   (-8.30%) |     114   →     126    (+10.53%) |      909.70 ms →      922.01 ms   (+1.35%) | 
- │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       15.63 ms →       17.47 ms  (+11.76%) |      19   →      21    (+10.53%) |      297.02 ms →      366.90 ms  (+23.53%) | 
! │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      492.81 μs →      467.96 μs   (-5.04%) |      19   →      21    (+10.53%) |        9.36 ms →        9.83 ms   (+4.95%) | 
- │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        7.17 ms →        7.85 ms   (+9.54%) |      38   →      42    (+10.53%) |      272.35 ms →      329.74 ms  (+21.07%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.86 s  →        1.54 s   (-17.53%) |      19   →      21    (+10.53%) |       35.41 s  →       32.27 s    (-8.85%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       56.01 ms →       53.74 ms   (-4.04%) |     356   →     361     (+1.40%) |       19.94 s  →       19.40 s    (-2.69%) | 
+ │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       36.26 ms →       30.08 ms  (-17.05%) |     356   →     361     (+1.40%) |       12.91 s  →       10.86 s   (-15.89%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.00 μs →        2.23 μs  (+11.04%) |     356   →     361     (+1.40%) |      713.75 μs →      803.71 μs  (+12.60%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.71 μs →        1.88 μs   (+9.43%) |     356   →     361     (+1.40%) |      610.36 μs →      677.27 μs  (+10.96%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      459.47 ns →      458.28 ns   (-0.26%) |     356   →     361     (+1.40%) |      163.57 μs →      165.44 μs   (+1.14%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      556.09 ns →      637.27 ns  (+14.60%) |     356   →     361     (+1.40%) |      197.97 μs →      230.06 μs  (+16.21%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        3.14 ms →        2.90 ms   (-7.67%) |     356   →     361     (+1.40%) |        1.12 s  →        1.05 s    (-6.38%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.18 ms →        3.20 ms   (+0.61%) |     356   →     361     (+1.40%) |        1.13 s  →        1.16 s    (+2.03%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        6.70 ms →        8.77 ms  (+30.90%) |     712   →     722     (+1.40%) |        4.77 s  →        6.33 s   (+32.74%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |        5.51 ms →        7.25 ms  (+31.55%) |     356   →     361     (+1.40%) |        1.96 s  →        2.62 s   (+33.40%) | 
- │ │ │ │   │ ├ sddk::wf_inner                                          |      977.73 μs →        1.17 ms  (+19.84%) |     693   →     701     (+1.15%) |      677.56 ms →      821.35 ms  (+21.22%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       53.53 ns →       48.57 ns   (-9.27%) |     693   →     701     (+1.15%) |       37.10 μs →       34.05 μs   (-8.23%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |      816.49 μs →        1.01 ms  (+23.59%) |     693   →     701     (+1.15%) |      565.82 ms →      707.38 ms  (+25.02%) | 
+ │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       49.29 ns →       44.28 ns  (-10.17%) |     693   →     701     (+1.15%) |       34.16 μs →       31.04 μs   (-9.13%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      132.38 μs →      136.79 μs   (+3.33%) |     356   →     361     (+1.40%) |       47.13 ms →       49.38 ms   (+4.78%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        1.43 ms →        2.47 ms  (+72.97%) |     356   →     361     (+1.40%) |      508.18 ms →      891.35 ms  (+75.40%) | 
- │ │ │ │   │ └ sddk::wf_trans                                          |        2.16 ms →        2.51 ms  (+16.28%) |     337   →     340     (+0.89%) |      726.54 ms →      852.31 ms  (+17.31%) | 
- │ │ │ │   │   └ sddk::wf_trans|pw                                     |      717.78 μs →      834.75 μs  (+16.30%) |    1.01 K →    1.02 K   (+0.89%) |      725.67 ms →      851.44 ms  (+17.33%) | 
- │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.17 ms →        1.39 ms  (+18.45%) |     356   →     361     (+1.40%) |      417.63 ms →      501.62 ms  (+20.11%) | 
- │ │ │ │   │ └ sddk::wf_inner                                          |        1.10 ms →        1.34 ms  (+22.06%) |     356   →     361     (+1.40%) |      392.22 ms →      485.46 ms  (+23.77%) | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       40.50 ns →       41.20 ns   (+1.73%) |     356   →     361     (+1.40%) |       14.42 μs →       14.87 μs   (+3.16%) | 
- │ │ │ │   │   ├ sddk::wf_inner|pw                                     |      940.61 μs →        1.18 ms  (+25.31%) |     356   →     361     (+1.40%) |      334.86 ms →      425.52 ms  (+27.07%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       37.98 ns →       54.88 ns  (+44.48%) |     356   →     361     (+1.40%) |       13.52 μs →       19.81 μs  (+46.51%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       33.43 ms →       23.02 ms  (-31.12%) |     356   →     361     (+1.40%) |       11.90 s  →        8.31 s   (-30.16%) | 
- │ │ │ │   ├ sirius::residuals                                         |        2.46 ms →        2.89 ms  (+17.35%) |     340   →     346     (+1.76%) |      836.84 ms →      999.39 ms  (+19.42%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |        1.35 ms →        1.32 ms   (-2.23%) |     337   →     342     (+1.48%) |      455.70 ms →      452.14 ms   (-0.78%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      674.67 μs →      659.58 μs   (-2.24%) |     674   →     684     (+1.48%) |      454.73 ms →      451.15 ms   (-0.79%) | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.02 ms →        1.48 ms  (+45.00%) |     337   →     342     (+1.48%) |      343.85 ms →      505.99 ms  (+47.15%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        6.42 ms →        4.86 ms  (-24.36%) |      54   →      90    (+66.67%) |      346.80 ms →      437.21 ms  (+26.07%) | 
- │ │ │ │     └ sddk::wf_trans                                          |        3.85 ms →        2.70 ms  (-29.88%) |      89   →     159    (+78.65%) |      342.28 ms →      428.75 ms  (+25.26%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |        2.76 ms →        1.88 ms  (-31.89%) |     124   →     228    (+83.87%) |      342.09 ms →      428.43 ms  (+25.24%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      389.89 ns →      565.67 ns  (+45.08%) |      19   →      21    (+10.53%) |        7.41 μs →       11.88 μs  (+60.35%) | 
! │ │ │ └ sirius::K_point_set::sync_band_energies                       |       19.43 μs →       19.34 μs   (-0.49%) |      19   →      21    (+10.53%) |      369.23 μs →      406.11 μs   (+9.99%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.52 ms →        1.52 ms   (-0.27%) |      19   →      21    (+10.53%) |       28.93 ms →       31.89 ms  (+10.23%) | 
- │ │ ├ sirius::Density::generate                                       |      565.14 ms →      568.42 ms   (+0.58%) |      19   →      21    (+10.53%) |       10.74 s  →       11.94 s   (+11.17%) | 
- │ │ │ ├ sirius::Density::generate_valence                             |      383.77 ms →      418.93 ms   (+9.16%) |      19   →      21    (+10.53%) |        7.29 s  →        8.80 s   (+20.65%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.09 μs →        8.14 μs   (+0.68%) |      19   →      21    (+10.53%) |      153.65 μs →      170.98 μs  (+11.28%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.48 μs →        7.62 μs   (+1.89%) |      19   →      21    (+10.53%) |      142.18 μs →      160.12 μs  (+12.62%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       45.56 ms →       32.49 ms  (-28.70%) |      19   →      21    (+10.53%) |      865.68 ms →      682.24 ms  (-21.19%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.56 μs →        8.11 μs   (+7.38%) |      19   →      21    (+10.53%) |      143.57 μs →      170.40 μs  (+18.68%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |       24.05 ms →        5.05 ms  (-79.00%) |      19   →      21    (+10.53%) |      456.92 ms →      106.08 ms  (-76.78%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       20.45 ms →       26.39 ms  (+29.09%) |      19   →      21    (+10.53%) |      388.47 ms →      554.28 ms  (+42.68%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      625.74 ns →      813.52 ns  (+30.01%) |      19   →      21    (+10.53%) |       11.89 μs →       17.08 μs  (+43.70%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       94.00 ms →      113.56 ms  (+20.81%) |      19   →      21    (+10.53%) |        1.79 s  →        2.38 s   (+33.53%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.89 ms →        2.19 ms  (+16.13%) |      19   →      21    (+10.53%) |       35.89 ms →       46.06 ms  (+28.35%) | 
- │ │ │ │ └ sirius::Density::augment                                    |      196.52 ms →      231.18 ms  (+17.64%) |      19   →      21    (+10.53%) |        3.73 s  →        4.85 s   (+30.02%) | 
- │ │ │ │   └ sirius::Density::generate_rho_aug                         |      196.30 ms →      230.96 ms  (+17.66%) |      19   →      21    (+10.53%) |        3.73 s  →        4.85 s   (+30.05%) | 
+ │ │ │ ├ sirius::Field4D::symmetrize                                   |      152.72 ms →      122.54 ms  (-19.76%) |      19   →      21    (+10.53%) |        2.90 s  →        2.57 s   (-11.31%) | 
+ │ │ │ │ └ sirius::symmetrize_function|fpw                             |      152.72 ms →      122.54 ms  (-19.76%) |      19   →      21    (+10.53%) |        2.90 s  →        2.57 s   (-11.31%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       68.83 ms →       39.44 ms  (-42.70%) |      19   →      21    (+10.53%) |        1.31 s  →      828.27 ms  (-36.66%) | 
! │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       70.39 ms →       69.84 ms   (-0.78%) |      19   →      21    (+10.53%) |        1.34 s  →        1.47 s    (+9.67%) | 
! │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.84 ms →       12.60 ms   (-1.90%) |      19   →      21    (+10.53%) |      244.05 ms →      264.61 ms   (+8.42%) | 
! │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.64 ms →       23.50 ms   (-0.60%) |      19   →      21    (+10.53%) |      449.23 ms →      493.54 ms   (+9.86%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        5.00 ms →        3.45 ms  (-31.13%) |      19   →      21    (+10.53%) |       95.04 ms →       72.35 ms  (-23.88%) | 
- │ │ ├ sirius::Density::mix                                            |      132.62 ms →      134.74 ms   (+1.59%) |      19   →      21    (+10.53%) |        2.52 s  →        2.83 s   (+12.29%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      873.88 μs →      292.62 μs  (-66.52%) |      19   →      21    (+10.53%) |       16.60 ms →        6.14 ms  (-62.99%) | 
- │ │ │ ├ sirius::Periodic_function|inner                               |        4.85 ms →        4.78 ms   (-1.33%) |     229   →     259    (+13.10%) |        1.11 s  →        1.24 s   (+11.59%) | 
! │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.81 ms →        4.63 ms   (-3.82%) |     229   →     259    (+13.10%) |        1.10 s  →        1.20 s    (+8.78%) | 
! │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.81 ms →        4.63 ms   (-3.83%) |     229   →     259    (+13.10%) |        1.10 s  →        1.20 s    (+8.77%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        5.51 ms →        5.90 ms   (+7.22%) |      19   →      21    (+10.53%) |      104.60 ms →      123.96 ms  (+18.50%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        4.86 ms →        5.19 ms   (+6.78%) |      19   →      21    (+10.53%) |       92.26 ms →      108.89 ms  (+18.02%) | 
- │ │ ├ sirius::Potential::generate                                     |      355.26 ms →      360.88 ms   (+1.58%) |      19   →      21    (+10.53%) |        6.75 s  →        7.58 s   (+12.27%) | 
- │ │ │ ├ sirius::Potential::poisson                                    |       35.03 ms →       40.62 ms  (+15.98%) |      19   →      21    (+10.53%) |      665.50 ms →      853.07 ms  (+28.19%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        3.32 ms →        9.72 ms (+193.00%) |      19   →      21    (+10.53%) |       63.03 ms →      204.13 ms (+223.84%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner                             |        5.84 ms →        4.90 ms  (-16.07%) |      19   →      21    (+10.53%) |      110.93 ms →      102.91 ms   (-7.23%) | 
- │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.65 ms →        4.65 ms   (-0.10%) |      19   →      21    (+10.53%) |       88.38 ms →       97.59 ms  (+10.42%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.65 ms →        4.65 ms   (-0.11%) |      19   →      21    (+10.53%) |       88.36 ms →       97.56 ms  (+10.41%) | 
! │ │ │ ├ sirius::Periodic_function::add                                |      782.48 μs →      765.66 μs   (-2.15%) |      38   →      42    (+10.53%) |       29.73 ms →       32.16 ms   (+8.15%) | 
- │ │ │ ├ sirius::Potential::xc                                         |       45.26 ms →       45.22 ms   (-0.10%) |      19   →      21    (+10.53%) |      860.00 ms →      949.55 ms  (+10.41%) | 
- │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       44.09 ms →       44.04 ms   (-0.11%) |      19   →      21    (+10.53%) |      837.72 ms →      924.89 ms  (+10.41%) | 
! │ │ │ │   ├ sirius::Smooth_periodic_function                          |      690.79 μs →      662.31 μs   (-4.12%) |      38   →      42    (+10.53%) |       26.25 ms →       27.82 ms   (+5.97%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.43 ms →        4.67 ms   (+5.42%) |      19   →      21    (+10.53%) |       84.14 ms →       98.04 ms  (+16.52%) | 
! │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.67 ms →        3.33 ms   (-9.45%) |      19   →      21    (+10.53%) |       69.80 ms →       69.86 ms   (+0.08%) | 
- │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.31 ms →      268.77 ms   (+0.17%) |      19   →      21    (+10.53%) |        5.10 s  →        5.64 s   (+10.72%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      311.68 ns →      240.38 ns  (-22.88%) |      19   →      21    (+10.53%) |        5.92 μs →        5.05 μs  (-14.76%) | 
! │ │ ├ sirius::Field4D::symmetrize                                     |       98.17 ms →       96.18 ms   (-2.02%) |      19   →      21    (+10.53%) |        1.87 s  →        2.02 s    (+8.29%) | 
! │ │ │ └ sirius::symmetrize_function|fpw                               |       98.17 ms →       96.18 ms   (-2.02%) |      19   →      21    (+10.53%) |        1.87 s  →        2.02 s    (+8.29%) | 
- │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.35 ms →       13.30 ms   (-0.38%) |      19   →      21    (+10.53%) |      253.61 ms →      279.24 ms  (+10.11%) | 
! │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       71.31 ms →       69.71 ms   (-2.25%) |      19   →      21    (+10.53%) |        1.35 s  →        1.46 s    (+8.04%) | 
! │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.88 ms →       12.55 ms   (-2.61%) |      19   →      21    (+10.53%) |      244.75 ms →      263.46 ms   (+7.64%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        4.30 ms →        3.54 ms  (-17.73%) |      19   →      21    (+10.53%) |       81.76 ms →       74.35 ms   (-9.07%) | 
- │ │ ├ sirius::Periodic_function|inner                                 |        4.59 ms →        4.76 ms   (+3.59%) |     133   →     147    (+10.53%) |      610.95 ms →      699.52 ms  (+14.50%) | 
! │ │ │ └ sirius::Periodic_function|inner_local                         |        4.57 ms →        4.55 ms   (-0.54%) |     133   →     147    (+10.53%) |      608.02 ms →      668.38 ms   (+9.93%) | 
! │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.57 ms →        4.55 ms   (-0.54%) |     133   →     147    (+10.53%) |      607.94 ms →      668.30 ms   (+9.93%) | 
! │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.96 ms →        4.73 ms   (-4.57%) |      57   →      63    (+10.53%) |      282.78 ms →      298.26 ms   (+5.47%) | 
! │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.94 ms →        4.72 ms   (-4.54%) |      57   →      63    (+10.53%) |      281.62 ms →      297.11 ms   (+5.50%) | 
- │ │ ├ sirius::Periodic_function::integrate                            |        4.54 ms →        4.53 ms   (-0.09%) |      19   →      21    (+10.53%) |       86.23 ms →       95.22 ms  (+10.43%) | 
! │ │ └ sirius::Density::get_magnetisation                              |       77.18 μs →       75.49 μs   (-2.19%) |      19   →      21    (+10.53%) |        1.47 ms →        1.59 ms   (+8.11%) | 
! │ │   └ sirius::Density::compute_atomic_mag_mom                       |       72.34 μs →       70.53 μs   (-2.50%) |      19   →      21    (+10.53%) |        1.37 ms →        1.48 ms   (+7.76%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.12 ms →        5.12 ms   (-0.01%) |       2   →       2              |       10.24 ms →       10.24 ms   (-0.01%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.60 ms →        4.64 ms   (+0.75%) |       6   →       6              |       27.62 ms →       27.83 ms   (+0.75%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.56 ms →        4.53 ms   (-0.72%) |       6   →       6              |       27.39 ms →       27.19 ms   (-0.72%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.56 ms →        4.53 ms   (-0.69%) |       6   →       6              |       27.38 ms →       27.19 ms   (-0.69%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.95 ms →        4.74 ms   (-4.31%) |       3   →       3              |       14.85 ms →       14.21 ms   (-4.31%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.95 ms →        4.70 ms   (-4.91%) |       3   →       3              |       14.84 ms →       14.11 ms   (-4.91%) | 
  ├ sirius::Periodic_function|inner                                     |        4.68 ms →        4.53 ms   (-3.15%) |       2   →       2              |        9.36 ms →        9.07 ms   (-3.15%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.55 ms →        4.53 ms   (-0.45%) |       2   →       2              |        9.09 ms →        9.05 ms   (-0.45%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.55 ms →        4.53 ms   (-0.45%) |       2   →       2              |        9.09 ms →        9.05 ms   (-0.45%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.92 ms →        4.71 ms   (-4.16%) |       1   →       1              |        4.92 ms →        4.71 ms   (-4.16%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.91 ms →        4.71 ms   (-4.12%) |       1   →       1              |        4.91 ms →        4.71 ms   (-4.12%) | 
  └ sirius::finalize                                                    |      167.16 ms →      161.80 ms   (-3.21%) |       1   →       1              |      167.16 ms →      161.80 ms   (-3.21%) | 
  ====================================================================================================================================================================================================
```
