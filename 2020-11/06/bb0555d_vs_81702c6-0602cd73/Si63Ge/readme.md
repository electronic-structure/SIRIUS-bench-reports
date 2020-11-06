# Benchmark 81702c64a8be67a2936e3e8bb8ca2c9083dee03b vs bb0555d843e651e25debb001ebfae513375d5936
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |       73.56 s  →       75.22 s    (+2.26%) |       1   →       1              |       73.56 s  →       75.22 s    (+2.26%) | 
  ├ sirius::initialize                                                  |        3.24 s  →        2.92 s    (-9.96%) |       1   →       1              |        3.24 s  →        2.92 s    (-9.96%) | 
  ├ sirius::Simulation_context::initialize                              |        4.35 s  →        4.22 s    (-3.11%) |       1   →       1              |        4.35 s  →        4.22 s    (-3.11%) | 
- │ ├ sirius::Simulation_context::init_comm                             |        4.92 ms →      238.68 ms (+4746.34%) |       1   →       1              |        4.92 ms →      238.68 ms (+4746.34%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      656.21 ms →      376.68 ms  (-42.60%) |       1   →       1              |      656.21 ms →      376.68 ms  (-42.60%) | 
+ │ │ ├ sirius::Atom_type::init                                         |      314.67 ms →      179.09 ms  (-43.09%) |       2   →       2              |      629.34 ms →      358.18 ms  (-43.09%) | 
+ │ │ └ sirius::Unit_cell::update                                       |       26.78 ms →       18.41 ms  (-31.23%) |       1   →       1              |       26.78 ms →       18.41 ms  (-31.23%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.95 ms →        3.73 ms   (-5.57%) |       1   →       1              |        3.95 ms →        3.73 ms   (-5.57%) | 
+ │ │   └ sirius::Unit_cell::get_symmetry                               |       22.78 ms →       14.62 ms  (-35.81%) |       1   →       1              |       22.78 ms →       14.62 ms  (-35.81%) | 
+ │ │     └ sirius::Unit_cell_symmetry                                  |       22.70 ms →       14.55 ms  (-35.89%) |       1   →       1              |       22.70 ms →       14.55 ms  (-35.89%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.76 ms →        2.76 ms   (+0.32%) |       1   →       1              |        2.76 ms →        2.76 ms   (+0.32%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      524.09 μs →      508.71 μs   (-2.93%) |       1   →       1              |      524.09 μs →      508.71 μs   (-2.93%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       18.03 μs →       17.16 μs   (-4.84%) |       1   →       1              |       18.03 μs →       17.16 μs   (-4.84%) | 
  │ └ sirius::Simulation_context::update                                |        3.64 s  →        3.50 s    (-3.69%) |       1   →       1              |        3.64 s  →        3.50 s    (-3.69%) | 
  │   ├ sirius::Unit_cell::update                                       |        6.80 ms →        6.99 ms   (+2.68%) |       1   →       1              |        6.80 ms →        6.99 ms   (+2.68%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.45 ms →        3.64 ms   (+5.46%) |       1   →       1              |        3.45 ms →        3.64 ms   (+5.46%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.29 ms →        3.31 ms   (+0.47%) |       1   →       1              |        3.29 ms →        3.31 ms   (+0.47%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.25 ms →        3.27 ms   (+0.47%) |       1   →       1              |        3.25 ms →        3.27 ms   (+0.47%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.71 ms →        2.72 ms   (+0.24%) |       1   →       1              |        2.71 ms →        2.72 ms   (+0.24%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      498.48 μs →      507.24 μs   (+1.76%) |       1   →       1              |      498.48 μs →      507.24 μs   (+1.76%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       13.73 μs →       14.18 μs   (+3.31%) |       1   →       1              |       13.73 μs →       14.18 μs   (+3.31%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      217.91 ms →      212.23 ms   (-2.61%) |       2   →       2              |      435.82 ms →      424.46 ms   (-2.61%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.70 ms →       15.14 ms   (-3.60%) |       2   →       2              |       31.41 ms →       30.27 ms   (-3.60%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.40 ms →       13.24 ms   (-1.14%) |       1   →       1              |       13.40 ms →       13.24 ms   (-1.14%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.37 ms →       56.36 ms   (-0.02%) |       2   →       2              |      112.74 ms →      112.72 ms   (-0.02%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.24 ms →       45.29 ms   (+0.12%) |       2   →       2              |       90.47 ms →       90.58 ms   (+0.12%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.65 ms →       60.46 ms   (-0.32%) |       4   →       4              |      242.60 ms →      241.84 ms   (-0.32%) | 
  │   ├ sddk::Gvec::init                                                |       93.64 ms →       92.77 ms   (-0.94%) |       2   →       2              |      187.29 ms →      185.53 ms   (-0.94%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       70.08 ms →       69.26 ms   (-1.17%) |       2   →       2              |      140.17 ms →      138.53 ms   (-1.17%) | 
  │   ├ sddk::Gvec_shells                                               |       94.03 ms →       96.46 ms   (+2.59%) |       1   →       1              |       94.03 ms →       96.46 ms   (+2.59%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.97 ms →        1.97 ms   (+0.23%) |       1   →       1              |        1.97 ms →        1.97 ms   (+0.23%) | 
+ │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      682.04 ms →      609.47 ms  (-10.64%) |       2   →       2              |        1.36 s  →        1.22 s   (-10.64%) | 
- ├ sirius::K_point_set::create_k_mesh                                  |       28.98 ms →      147.01 ms (+407.29%) |       1   →       1              |       28.98 ms →      147.01 ms (+407.29%) | 
- │ ├ sirius::K_point::K_point                                          |        1.19 μs →        1.70 μs  (+42.89%) |       4   →       4              |        4.76 μs →        6.80 μs  (+42.89%) | 
- │ └ sirius::K_point_set::initialize                                   |       28.90 ms →      146.93 ms (+408.41%) |       1   →       1              |       28.90 ms →      146.93 ms (+408.41%) | 
  │   └ sirius::K_point::initialize                                     |       28.64 ms →       28.73 ms   (+0.33%) |       1   →       1              |       28.64 ms →       28.73 ms   (+0.33%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       10.97 ms →       11.15 ms   (+1.58%) |       1   →       1              |       10.97 ms →       11.15 ms   (+1.58%) | 
  │     │ └ sddk::Gvec::init                                            |        4.97 ms →        5.05 ms   (+1.73%) |       1   →       1              |        4.97 ms →        5.05 ms   (+1.73%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |       10.87 μs →       10.91 μs   (+0.35%) |       1   →       1              |       10.87 μs →       10.91 μs   (+0.35%) | 
  │     └ sirius::K_point::update                                       |       14.77 ms →       14.71 ms   (-0.46%) |       1   →       1              |       14.77 ms →       14.71 ms   (-0.46%) | 
  │       └ sirius::Beta_projectors                                     |       10.77 ms →       10.65 ms   (-1.06%) |       1   →       1              |       10.77 ms →       10.65 ms   (-1.06%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.83 ms →        8.69 ms   (-1.62%) |       1   →       1              |        8.83 ms →        8.69 ms   (-1.62%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.57 ms →        2.54 ms   (-0.86%) |       2   →       2              |        5.13 ms →        5.09 ms   (-0.86%) | 
- ├ sirius::Potential                                                   |       49.77 ms →       55.50 ms  (+11.50%) |       1   →       1              |       49.77 ms →       55.50 ms  (+11.50%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.93 ms →        2.93 ms   (-0.13%) |       6   →       6              |       17.59 ms →       17.57 ms   (-0.13%) | 
- │ └ sirius::Potential::update                                         |       31.71 ms →       37.40 ms  (+17.92%) |       1   →       1              |       31.71 ms →       37.40 ms  (+17.92%) | 
- │   └ sirius::Potential::generate_local_potential                     |       31.30 ms →       36.99 ms  (+18.18%) |       1   →       1              |       31.30 ms →       36.99 ms  (+18.18%) | 
- │     ├ sirius::Simulation_context::make_periodic_function            |       26.70 ms →       32.61 ms  (+22.14%) |       1   →       1              |       26.70 ms →       32.61 ms  (+22.14%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        4.08 ms →        3.82 ms   (-6.21%) |       1   →       1              |        4.08 ms →        3.82 ms   (-6.21%) | 
- ├ sirius::Density                                                     |       38.18 ms →       42.95 ms  (+12.49%) |       1   →       1              |       38.18 ms →       42.95 ms  (+12.49%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.83 ms →        2.83 ms   (+0.14%) |       2   →       2              |        5.65 ms →        5.66 ms   (+0.14%) | 
- │ └ sirius::Density::update                                           |       32.39 ms →       37.15 ms  (+14.69%) |       1   →       1              |       32.39 ms →       37.15 ms  (+14.69%) | 
- │   └ sirius::Density::generate_pseudo_core_charge_density            |       32.17 ms →       36.86 ms  (+14.57%) |       1   →       1              |       32.17 ms →       36.86 ms  (+14.57%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |       77.92 μs →       76.61 μs   (-1.69%) |       1   →       1              |       77.92 μs →       76.61 μs   (-1.69%) | 
- │     ├ sirius::Simulation_context::make_periodic_function            |       26.70 ms →       33.13 ms  (+24.11%) |       1   →       1              |       26.70 ms →       33.13 ms  (+24.11%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        5.09 ms →        3.30 ms  (-35.16%) |       1   →       1              |        5.09 ms →        3.30 ms  (-35.16%) | 
- ├ sirius::Density::initial_density                                    |       55.95 ms →       65.98 ms  (+17.92%) |       1   →       1              |       55.95 ms →       65.98 ms  (+17.92%) | 
- │ ├ sirius::Simulation_context::make_periodic_function                |       27.07 ms →       37.70 ms  (+39.26%) |       1   →       1              |       27.07 ms →       37.70 ms  (+39.26%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.84 ms →        4.98 ms   (+2.83%) |       2   →       2              |        9.68 ms →        9.95 ms   (+2.83%) | 
+ │ └ sirius::Periodic_function::integrate                              |        5.77 ms →        4.94 ms  (-14.28%) |       1   →       1              |        5.77 ms →        4.94 ms  (-14.28%) | 
  ├ sirius::Potential::generate                                         |      362.14 ms →      372.10 ms   (+2.75%) |       1   →       1              |      362.14 ms →      372.10 ms   (+2.75%) | 
- │ ├ sirius::Potential::poisson                                        |       35.02 ms →       45.47 ms  (+29.86%) |       1   →       1              |       35.02 ms →       45.47 ms  (+29.86%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.14 ms →        3.26 ms   (+3.61%) |       1   →       1              |        3.14 ms →        3.26 ms   (+3.61%) | 
+ │ │ └ sirius::Periodic_function|inner                                 |        6.04 ms →        5.24 ms  (-13.26%) |       1   →       1              |        6.04 ms →        5.24 ms  (-13.26%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.65 ms →        4.84 ms   (+4.11%) |       1   →       1              |        4.65 ms →        4.84 ms   (+4.11%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.64 ms →        4.83 ms   (+4.16%) |       1   →       1              |        4.64 ms →        4.83 ms   (+4.16%) | 
  │ ├ sirius::Periodic_function::add                                    |      834.99 μs →      771.90 μs   (-7.56%) |       2   →       2              |        1.67 ms →        1.54 ms   (-7.56%) | 
  │ ├ sirius::Potential::xc                                             |       51.48 ms →       51.25 ms   (-0.46%) |       1   →       1              |       51.48 ms →       51.25 ms   (-0.46%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       50.27 ms →       50.07 ms   (-0.40%) |       1   →       1              |       50.27 ms →       50.07 ms   (-0.40%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.56 ms →        2.54 ms   (-0.58%) |       2   →       2              |        5.11 ms →        5.08 ms   (-0.58%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.75 ms →        4.36 ms   (-8.33%) |       1   →       1              |        4.75 ms →        4.36 ms   (-8.33%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.61 ms →        3.94 ms   (+9.16%) |       1   →       1              |        3.61 ms →        3.94 ms   (+9.16%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      268.99 ms →      268.50 ms   (-0.19%) |       1   →       1              |      268.99 ms →      268.50 ms   (-0.19%) | 
+ │ └ sirius::Potential::generate_PAW_effective_potential               |      178.00 ns →      107.00 ns  (-39.89%) |       1   →       1              |      178.00 ns →      107.00 ns  (-39.89%) | 
  ├ sirius::Hamiltonian0                                                |        8.89 ms →        8.79 ms   (-1.09%) |       1   →       1              |        8.89 ms →        8.79 ms   (-1.09%) | 
  │ ├ sirius::Local_operator                                            |        8.35 ms →        8.17 ms   (-2.26%) |       1   →       1              |        8.35 ms →        8.17 ms   (-2.26%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.74 ms →        2.75 ms   (+0.07%) |       1   →       1              |        2.74 ms →        2.75 ms   (+0.07%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        4.06 ms →        4.00 ms   (-1.35%) |       1   →       1              |        4.06 ms →        4.00 ms   (-1.35%) | 
- │ ├ sirius::Non_local_operator                                        |      134.89 μs →      180.98 μs  (+34.17%) |       2   →       2              |      269.78 μs →      361.96 μs  (+34.17%) | 
  │ ├ sirius::D_operator::initialize                                    |      112.50 μs →      109.25 μs   (-2.89%) |       1   →       1              |      112.50 μs →      109.25 μs   (-2.89%) | 
  │ └ sirius::Q_operator::initialize                                    |       90.45 μs →       93.05 μs   (+2.88%) |       1   →       1              |       90.45 μs →       93.05 μs   (+2.88%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.29 s  →        1.30 s    (+0.15%) |       1   →       1              |        1.29 s  →        1.30 s    (+0.15%) | 
+ │ ├ sirius::Hamiltonian_k                                             |       69.45 ms →       54.62 ms  (-21.35%) |       1   →       1              |       69.45 ms →       54.62 ms  (-21.35%) | 
+ │ │ ├ sirius::Local_operator::prepare_k                               |      255.76 μs →      210.57 μs  (-17.67%) |       1   →       1              |      255.76 μs →      210.57 μs  (-17.67%) | 
+ │ │ └ sirius::Beta_projectors_base::prepare                           |       69.19 ms →       54.41 ms  (-21.36%) |       1   →       1              |       69.19 ms →       54.41 ms  (-21.36%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.22 s  →        1.24 s    (+1.37%) |       1   →       1              |        1.22 s  →        1.24 s    (+1.37%) | 
+ │ │ ├ sddk::matrix_storage::matrix_storage                            |      107.48 ms →       77.43 ms  (-27.96%) |       4   →       4              |      429.92 ms →      309.74 ms  (-27.96%) | 
- │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       38.09 ms →       48.05 ms  (+26.17%) |       1   →       1              |       38.09 ms →       48.05 ms  (+26.17%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        7.73 ms →        7.84 ms   (+1.47%) |       1   →       1              |        7.73 ms →        7.84 ms   (+1.47%) | 
+ │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      452.24 ms →      335.81 ms  (-25.75%) |       1   →       1              |      452.24 ms →      335.81 ms  (-25.75%) | 
+ │ │ │ ├ sirius::Local_operator::apply_h                               |      380.87 ms →      247.75 ms  (-34.95%) |       1   →       1              |      380.87 ms →      247.75 ms  (-34.95%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        2.80 μs →        3.67 μs  (+31.06%) |       1   →       1              |        2.80 μs →        3.67 μs  (+31.06%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.16 μs →        2.73 μs  (+26.62%) |       1   →       1              |        2.16 μs →        2.73 μs  (+26.62%) | 
- │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      415.00 ns →      565.00 ns  (+36.14%) |       1   →       1              |      415.00 ns →      565.00 ns  (+36.14%) | 
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      847.00 ns →      597.00 ns  (-29.52%) |       1   →       1              |      847.00 ns →      597.00 ns  (-29.52%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::generate                        |        7.81 ms →        3.18 ms  (-59.31%) |       1   →       1              |        7.81 ms →        3.18 ms  (-59.31%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.22 ms →       21.24 ms   (+0.08%) |       1   →       1              |       21.22 ms →       21.24 ms   (+0.08%) | 
- │ │ │ └ sirius::Non_local_operator::apply                             |       21.15 ms →       31.80 ms  (+50.34%) |       2   →       2              |       42.31 ms →       63.60 ms  (+50.34%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.79 ms →       14.68 ms   (-0.75%) |       2   →       2              |       29.58 ms →       29.36 ms   (-0.75%) | 
  │ │ │ └ sddk::wf_inner                                                |       14.58 ms →       14.47 ms   (-0.76%) |       2   →       2              |       29.16 ms →       28.94 ms   (-0.76%) | 
+ │ │ │   ├ sddk::wf_inner|scale                                        |       31.00 ns →       21.50 ns  (-30.65%) |       2   →       2              |       62.00 ns →       43.00 ns  (-30.65%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       14.46 ms →       14.34 ms   (-0.85%) |       2   →       2              |       28.92 ms →       28.68 ms   (-0.85%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       33.50 ns →       39.50 ns  (+17.91%) |       2   →       2              |       67.00 ns →       79.00 ns  (+17.91%) | 
- │ │ ├ Eigensolver_cuda|zhegvdx                                        |      108.30 ms →      242.13 ms (+123.58%) |       1   →       1              |      108.30 ms →      242.13 ms (+123.58%) | 
  │ │ └ sddk::wf_trans                                                  |        2.59 ms →        2.60 ms   (+0.32%) |       1   →       1              |        2.59 ms →        2.60 ms   (+0.32%) | 
  │ │   └ sddk::wf_trans|pw                                             |        2.59 ms →        2.60 ms   (+0.29%) |       1   →       1              |        2.59 ms →        2.60 ms   (+0.29%) | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      450.00 ns →      477.00 ns   (+6.00%) |       1   →       1              |      450.00 ns →      477.00 ns   (+6.00%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |       62.71 s  →       64.90 s    (+3.49%) |       1   →       1              |       62.71 s  →       64.90 s    (+3.49%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.46 ms →        2.45 ms   (-0.39%) |      19   →      19              |       46.74 ms →       46.56 ms   (-0.39%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        2.97 s  →        2.93 s    (-1.33%) |      21   →      22     (+4.76%) |       62.44 s  →       64.54 s    (+3.36%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        5.75 ms →        5.39 ms   (-6.33%) |      21   →      22     (+4.76%) |      120.77 ms →      118.51 ms   (-1.87%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.87 ms →        4.54 ms   (-6.88%) |      21   →      22     (+4.76%) |      102.28 ms →       99.77 ms   (-2.45%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      546.93 μs →      532.12 μs   (-2.71%) |      21   →      22     (+4.76%) |       11.49 ms →       11.71 ms   (+1.92%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.14 ms →        2.84 ms   (-9.60%) |      21   →      22     (+4.76%) |       65.98 ms →       62.49 ms   (-5.29%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |      300.66 μs →      289.83 μs   (-3.60%) |      42   →      44     (+4.76%) |       12.63 ms →       12.75 ms   (+0.99%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |      111.31 μs →      106.32 μs   (-4.48%) |      21   →      22     (+4.76%) |        2.34 ms →        2.34 ms   (+0.07%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       90.95 μs →       90.10 μs   (-0.94%) |      21   →      22     (+4.76%) |        1.91 ms →        1.98 ms   (+3.78%) | 
  │ │ ├ sirius::Band::solve                                             |        1.76 s  →        1.71 s    (-2.81%) |      21   →      22     (+4.76%) |       36.87 s  →       37.54 s    (+1.82%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      195.76 μs →      187.71 μs   (-4.11%) |      21   →      22     (+4.76%) |        4.11 ms →        4.13 ms   (+0.46%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      188.80 μs →      180.78 μs   (-4.25%) |      21   →      22     (+4.76%) |        3.96 ms →        3.98 ms   (+0.31%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.12 μs →        4.75 μs   (-7.20%) |      21   →      22     (+4.76%) |      107.45 μs →      104.46 μs   (-2.78%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.64 s  →        1.57 s    (-4.25%) |      21   →      22     (+4.76%) |       34.41 s  →       34.52 s    (+0.31%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       75.16 ms →       78.32 ms   (+4.21%) |      21   →      22     (+4.76%) |        1.58 s  →        1.72 s    (+9.17%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.71 ms →        6.27 ms  (-18.70%) |     126   →     154    (+22.22%) |      972.03 ms →      965.82 ms   (-0.64%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       15.30 ms →       12.81 ms  (-16.25%) |      21   →      22     (+4.76%) |      321.28 ms →      281.90 ms  (-12.26%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      473.48 μs →      461.66 μs   (-2.50%) |      21   →      22     (+4.76%) |        9.94 ms →       10.16 ms   (+2.15%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        7.01 ms →        5.56 ms  (-20.69%) |      42   →      44     (+4.76%) |      294.42 ms →      244.62 ms  (-16.92%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.54 s  →        1.46 s    (-5.33%) |      21   →      22     (+4.76%) |       32.30 s  →       32.04 s    (-0.82%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       59.61 ms →      102.45 ms  (+71.87%) |     361   →     180    (-50.14%) |       21.52 s  →       18.44 s   (-14.30%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       36.33 ms →       77.01 ms (+111.95%) |     361   →     180    (-50.14%) |       13.12 s  →       13.86 s    (+5.68%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.97 μs →        2.25 μs  (+14.15%) |     361   →     180    (-50.14%) |      712.64 μs →      405.62 μs  (-43.08%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.59 μs →        1.87 μs  (+17.54%) |     361   →     180    (-50.14%) |      573.10 μs →      335.88 μs  (-41.39%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      474.32 ns →      446.95 ns   (-5.77%) |     361   →     180    (-50.14%) |      171.23 μs →       80.45 μs  (-53.02%) | 
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      651.32 ns →      703.46 ns   (+8.00%) |     361   →     180    (-50.14%) |      235.13 μs →      126.62 μs  (-46.15%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        3.20 ms →        3.04 ms   (-4.86%) |     361   →     180    (-50.14%) |        1.15 s  →      547.34 ms  (-52.56%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.38 ms →        5.41 ms  (+60.16%) |     361   →     180    (-50.14%) |        1.22 s  →      972.95 ms  (-20.14%) | 
+ │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        8.34 ms →        8.49 ms   (+1.72%) |     722   →     360    (-50.14%) |        6.02 s  →        3.06 s   (-49.28%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |        6.09 ms →        7.72 ms  (+26.66%) |     361   →     180    (-50.14%) |        2.20 s  →        1.39 s   (-36.84%) | 
+ │ │ │ │   │ ├ sddk::wf_inner                                          |        1.15 ms →        1.19 ms   (+3.87%) |     701   →     338    (-51.78%) |      804.39 ms →      402.86 ms  (-49.92%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       56.13 ns →       47.20 ns  (-15.92%) |     701   →     338    (-51.78%) |       39.35 μs →       15.95 μs  (-59.46%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |      984.13 μs →        1.01 ms   (+2.92%) |     701   →     338    (-51.78%) |      689.88 ms →      342.34 ms  (-50.38%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       48.23 ns →       71.91 ns  (+49.10%) |     701   →     338    (-51.78%) |       33.81 μs →       24.31 μs  (-28.11%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      122.96 μs →      248.12 μs (+101.79%) |     361   →     180    (-50.14%) |       44.39 ms →       44.66 ms   (+0.62%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        1.67 ms →        2.49 ms  (+49.70%) |     361   →     180    (-50.14%) |      601.19 ms →      448.76 ms  (-25.36%) | 
- │ │ │ │   │ └ sddk::wf_trans                                          |        2.20 ms →        3.11 ms  (+41.51%) |     340   →     158    (-53.53%) |      747.58 ms →      491.63 ms  (-34.24%) | 
- │ │ │ │   │   └ sddk::wf_trans|pw                                     |      732.08 μs →        1.04 ms  (+41.57%) |    1.02 K →     474    (-53.53%) |      746.72 ms →      491.24 ms  (-34.21%) | 
- │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.21 ms →        1.67 ms  (+38.01%) |     361   →     180    (-50.14%) |      437.88 ms →      301.32 ms  (-31.19%) | 
- │ │ │ │   │ └ sddk::wf_inner                                          |        1.17 ms →        1.60 ms  (+37.52%) |     361   →     180    (-50.14%) |      421.14 ms →      288.77 ms  (-31.43%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       54.90 ns →       41.92 ns  (-23.65%) |     361   →     180    (-50.14%) |       19.82 μs →        7.54 μs  (-61.93%) | 
- │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        1.00 ms →        1.43 ms  (+42.56%) |     361   →     180    (-50.14%) |      361.11 ms →      256.69 ms  (-28.92%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       43.85 ns →       56.49 ns  (+28.84%) |     361   →     180    (-50.14%) |       15.83 μs →       10.17 μs  (-35.76%) | 
- │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       18.74 ms →       60.18 ms (+221.21%) |     361   →     180    (-50.14%) |        6.76 s  →       10.83 s   (+60.16%) | 
- │ │ │ │   ├ sirius::residuals                                         |        2.79 ms →        3.61 ms  (+29.46%) |     346   →     179    (-48.27%) |      964.21 ms →      645.77 ms  (-33.03%) | 
- │ │ │ │   │ ├ sddk::wf_trans                                          |        1.30 ms →        2.04 ms  (+56.28%) |     342   →     179    (-47.66%) |      445.46 ms →      364.37 ms  (-18.20%) | 
- │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      649.80 μs →        1.02 ms  (+56.39%) |     684   →     358    (-47.66%) |      444.47 ms →      363.80 ms  (-18.15%) | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.40 ms →        1.45 ms   (+3.55%) |     342   →     179    (-47.66%) |      479.75 ms →      260.01 ms  (-45.80%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        4.58 ms →        6.07 ms  (+32.42%) |      90   →      70    (-22.22%) |      412.54 ms →      424.89 ms   (+2.99%) | 
- │ │ │ │     └ sddk::wf_trans                                          |        2.54 ms →        3.54 ms  (+39.49%) |     159   →     118    (-25.79%) |      404.04 ms →      418.25 ms   (+3.52%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |        1.77 ms →        2.52 ms  (+42.21%) |     228   →     166    (-27.19%) |      403.71 ms →      418.00 ms   (+3.54%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      523.62 ns →      412.23 ns  (-21.27%) |      21   →      22     (+4.76%) |       11.00 μs →        9.07 μs  (-17.52%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       19.30 μs →       28.80 μs  (+49.22%) |      21   →      22     (+4.76%) |      405.23 μs →      633.50 μs  (+56.33%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.58 ms →        1.53 ms   (-3.27%) |      21   →      22     (+4.76%) |       33.14 ms →       33.58 ms   (+1.34%) | 
  │ │ ├ sirius::Density::generate                                       |      568.13 ms →      568.99 ms   (+0.15%) |      21   →      22     (+4.76%) |       11.93 s  →       12.52 s    (+4.92%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      399.54 ms →      394.00 ms   (-1.39%) |      21   →      22     (+4.76%) |        8.39 s  →        8.67 s    (+3.31%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        7.79 μs →        7.92 μs   (+1.72%) |      21   →      22     (+4.76%) |      163.55 μs →      174.29 μs   (+6.57%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.12 μs →        7.29 μs   (+2.37%) |      21   →      22     (+4.76%) |      149.48 μs →      160.31 μs   (+7.24%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       45.60 ms →       34.15 ms  (-25.10%) |      21   →      22     (+4.76%) |      957.59 ms →      751.35 ms  (-21.54%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.88 μs →        8.88 μs  (-10.07%) |      21   →      22     (+4.76%) |      207.47 μs →      195.46 μs   (-5.79%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |       23.96 ms →        5.20 ms  (-78.30%) |      21   →      22     (+4.76%) |      503.16 ms →      114.38 ms  (-77.27%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       20.57 ms →       27.91 ms  (+35.70%) |      21   →      22     (+4.76%) |      431.95 ms →      614.05 ms  (+42.16%) | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      829.52 ns →      811.82 ns   (-2.13%) |      21   →      22     (+4.76%) |       17.42 μs →       17.86 μs   (+2.53%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       93.94 ms →      111.37 ms  (+18.55%) |      21   →      22     (+4.76%) |        1.97 s  →        2.45 s   (+24.19%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.09 ms →        2.19 ms   (+4.54%) |      21   →      22     (+4.76%) |       43.99 ms →       48.17 ms   (+9.52%) | 
  │ │ │ │ └ sirius::Density::augment                                    |      213.58 ms →      201.38 ms   (-5.71%) |      21   →      22     (+4.76%) |        4.49 s  →        4.43 s    (-1.22%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |      213.35 ms →      201.16 ms   (-5.72%) |      21   →      22     (+4.76%) |        4.48 s  →        4.43 s    (-1.23%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      136.37 ms →      146.04 ms   (+7.09%) |      21   →      22     (+4.76%) |        2.86 s  →        3.21 s   (+12.19%) | 
- │ │ │ │ └ sirius::symmetrize_function|fpw                             |      136.37 ms →      146.04 ms   (+7.09%) |      21   →      22     (+4.76%) |        2.86 s  →        3.21 s   (+12.19%) | 
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       52.95 ms →       63.79 ms  (+20.48%) |      21   →      22     (+4.76%) |        1.11 s  →        1.40 s   (+26.22%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       70.03 ms →       68.92 ms   (-1.58%) |      21   →      22     (+4.76%) |        1.47 s  →        1.52 s    (+3.11%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.75 ms →       12.67 ms   (-0.59%) |      21   →      22     (+4.76%) |      267.68 ms →      278.79 ms   (+4.15%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.61 ms →       23.55 ms   (-0.25%) |      21   →      22     (+4.76%) |      495.72 ms →      518.01 ms   (+4.50%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        8.60 ms →        5.40 ms  (-37.26%) |      21   →      22     (+4.76%) |      180.66 ms →      118.75 ms  (-34.27%) | 
  │ │ ├ sirius::Density::mix                                            |      133.58 ms →      133.96 ms   (+0.29%) |      21   →      22     (+4.76%) |        2.81 s  →        2.95 s    (+5.06%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      897.46 μs →      801.16 μs  (-10.73%) |      21   →      22     (+4.76%) |       18.85 ms →       17.63 ms   (-6.48%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |        4.68 ms →        4.68 ms   (+0.01%) |     259   →     274     (+5.79%) |        1.21 s  →        1.28 s    (+5.81%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.63 ms →        4.61 ms   (-0.25%) |     259   →     274     (+5.79%) |        1.20 s  →        1.26 s    (+5.52%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.63 ms →        4.61 ms   (-0.25%) |     259   →     274     (+5.79%) |        1.20 s  →        1.26 s    (+5.53%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        5.34 ms →        6.68 ms  (+25.01%) |      21   →      22     (+4.76%) |      112.13 ms →      146.86 ms  (+30.97%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        4.73 ms →        5.90 ms  (+24.78%) |      21   →      22     (+4.76%) |       99.31 ms →      129.82 ms  (+30.72%) | 
  │ │ ├ sirius::Potential::generate                                     |      355.85 ms →      365.67 ms   (+2.76%) |      21   →      22     (+4.76%) |        7.47 s  →        8.04 s    (+7.65%) | 
- │ │ │ ├ sirius::Potential::poisson                                    |       35.50 ms →       45.41 ms  (+27.92%) |      21   →      22     (+4.76%) |      745.52 ms →      999.06 ms  (+34.01%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        3.69 ms →        3.22 ms  (-12.95%) |      21   →      22     (+4.76%) |       77.59 ms →       70.76 ms   (-8.80%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner                             |        5.91 ms →        5.29 ms  (-10.61%) |      21   →      22     (+4.76%) |      124.18 ms →      116.28 ms   (-6.36%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.64 ms →        4.83 ms   (+4.09%) |      21   →      22     (+4.76%) |       97.37 ms →      106.18 ms   (+9.05%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.64 ms →        4.83 ms   (+4.10%) |      21   →      22     (+4.76%) |       97.35 ms →      106.16 ms   (+9.05%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      817.24 μs →      777.12 μs   (-4.91%) |      42   →      44     (+4.76%) |       34.32 ms →       34.19 ms   (-0.38%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       45.05 ms →       45.28 ms   (+0.50%) |      21   →      22     (+4.76%) |      946.07 ms →      996.07 ms   (+5.28%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       43.86 ms →       44.10 ms   (+0.53%) |      21   →      22     (+4.76%) |      921.15 ms →      970.09 ms   (+5.31%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |      674.67 μs →      671.39 μs   (-0.49%) |      42   →      44     (+4.76%) |       28.34 ms →       29.54 ms   (+4.25%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.51 ms →        5.01 ms  (+11.02%) |      21   →      22     (+4.76%) |       94.80 ms →      110.26 ms  (+16.31%) | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.74 ms →        3.23 ms  (-13.54%) |      21   →      22     (+4.76%) |       78.55 ms →       71.15 ms   (-9.42%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.50 ms →      268.81 ms   (+0.11%) |      21   →      22     (+4.76%) |        5.64 s  →        5.91 s    (+4.88%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      170.90 ns →      183.55 ns   (+7.40%) |      21   →      22     (+4.76%) |        3.59 μs →        4.04 μs  (+12.51%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |       96.31 ms →       95.18 ms   (-1.18%) |      21   →      22     (+4.76%) |        2.02 s  →        2.09 s    (+3.53%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |       96.31 ms →       95.18 ms   (-1.18%) |      21   →      22     (+4.76%) |        2.02 s  →        2.09 s    (+3.53%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.27 ms →       13.32 ms   (+0.41%) |      21   →      22     (+4.76%) |      278.64 ms →      293.10 ms   (+5.19%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       69.87 ms →       68.54 ms   (-1.90%) |      21   →      22     (+4.76%) |        1.47 s  →        1.51 s    (+2.78%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.54 ms →       12.68 ms   (+1.10%) |      21   →      22     (+4.76%) |      263.42 ms →      279.00 ms   (+5.91%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        4.52 ms →        4.25 ms   (-6.13%) |      21   →      22     (+4.76%) |       94.98 ms →       93.41 ms   (-1.66%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.79 ms →        4.69 ms   (-1.97%) |     147   →     154     (+4.76%) |      703.61 ms →      722.59 ms   (+2.70%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.76 ms →        4.56 ms   (-4.19%) |     147   →     154     (+4.76%) |      700.06 ms →      702.68 ms   (+0.37%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.76 ms →        4.56 ms   (-4.19%) |     147   →     154     (+4.76%) |      699.98 ms →      702.58 ms   (+0.37%) | 
- │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.56 ms →        4.90 ms   (+7.47%) |      63   →      66     (+4.76%) |      287.32 ms →      323.49 ms  (+12.59%) | 
- │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.54 ms →        4.87 ms   (+7.32%) |      63   →      66     (+4.76%) |      285.73 ms →      321.25 ms  (+12.43%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.54 ms →        4.54 ms   (+0.02%) |      21   →      22     (+4.76%) |       95.39 ms →       99.96 ms   (+4.79%) | 
  │ │ └ sirius::Density::get_magnetisation                              |       73.13 μs →       74.06 μs   (+1.27%) |      21   →      22     (+4.76%) |        1.54 ms →        1.63 ms   (+6.10%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |       68.59 μs →       69.81 μs   (+1.78%) |      21   →      22     (+4.76%) |        1.44 ms →        1.54 ms   (+6.62%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.14 ms →        5.07 ms   (-1.38%) |       2   →       2              |       10.28 ms →       10.14 ms   (-1.38%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.99 ms →        4.63 ms   (-7.10%) |       6   →       6              |       29.93 ms →       27.80 ms   (-7.10%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.98 ms →        4.62 ms   (-7.28%) |       6   →       6              |       29.91 ms →       27.73 ms   (-7.28%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.98 ms →        4.62 ms   (-7.30%) |       6   →       6              |       29.90 ms →       27.72 ms   (-7.30%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.79 ms →        4.97 ms   (+3.57%) |       3   →       3              |       14.38 ms →       14.90 ms   (+3.57%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.79 ms →        4.96 ms   (+3.61%) |       3   →       3              |       14.36 ms →       14.88 ms   (+3.61%) | 
  ├ sirius::Periodic_function|inner                                     |        4.97 ms →        4.63 ms   (-6.91%) |       2   →       2              |        9.94 ms →        9.25 ms   (-6.91%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.97 ms →        4.62 ms   (-6.91%) |       2   →       2              |        9.93 ms →        9.25 ms   (-6.91%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.97 ms →        4.62 ms   (-6.91%) |       2   →       2              |        9.93 ms →        9.25 ms   (-6.91%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.77 ms →        4.84 ms   (+1.42%) |       1   →       1              |        4.77 ms →        4.84 ms   (+1.42%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.77 ms →        4.82 ms   (+1.02%) |       1   →       1              |        4.77 ms →        4.82 ms   (+1.02%) | 
  └ sirius::finalize                                                    |      150.73 ms →      151.36 ms   (+0.42%) |       1   →       1              |      150.73 ms →      151.36 ms   (+0.42%) | 
  ====================================================================================================================================================================================================
```
