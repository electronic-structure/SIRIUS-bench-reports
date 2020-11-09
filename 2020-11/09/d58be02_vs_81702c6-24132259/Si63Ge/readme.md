# Benchmark 81702c64a8be67a2936e3e8bb8ca2c9083dee03b vs d58be0235bf025c49e07930fbe8483989a6b739c
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |       73.55 s  →       74.13 s    (+0.80%) |       1   →       1              |       73.55 s  →       74.13 s    (+0.80%) | 
+ ├ sirius::initialize                                                  |        3.50 s  →        2.83 s   (-19.24%) |       1   →       1              |        3.50 s  →        2.83 s   (-19.24%) | 
- ├ sirius::Simulation_context::initialize                              |        3.89 s  →        4.66 s   (+19.69%) |       1   →       1              |        3.89 s  →        4.66 s   (+19.69%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |      102.22 ms →        6.53 ms  (-93.61%) |       1   →       1              |      102.22 ms →        6.53 ms  (-93.61%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      190.43 ms →      941.15 ms (+394.22%) |       1   →       1              |      190.43 ms →      941.15 ms (+394.22%) | 
- │ │ ├ sirius::Atom_type::init                                         |       85.81 ms →      460.31 ms (+436.41%) |       2   →       2              |      171.63 ms →      920.63 ms (+436.41%) | 
  │ │ └ sirius::Unit_cell::update                                       |       18.70 ms →       20.43 ms   (+9.25%) |       1   →       1              |       18.70 ms →       20.43 ms   (+9.25%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.76 ms →        4.00 ms   (+6.21%) |       1   →       1              |        3.76 ms →        4.00 ms   (+6.21%) | 
- │ │   └ sirius::Unit_cell::get_symmetry                               |       14.86 ms →       16.36 ms  (+10.08%) |       1   →       1              |       14.86 ms →       16.36 ms  (+10.08%) | 
- │ │     └ sirius::Unit_cell_symmetry                                  |       14.78 ms →       16.28 ms  (+10.15%) |       1   →       1              |       14.78 ms →       16.28 ms  (+10.15%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.79 ms →        2.78 ms   (-0.24%) |       1   →       1              |        2.79 ms →        2.78 ms   (-0.24%) | 
- │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      530.40 μs →        2.28 ms (+329.14%) |       1   →       1              |      530.40 μs →        2.28 ms (+329.14%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       16.76 μs →       17.72 μs   (+5.74%) |       1   →       1              |       16.76 μs →       17.72 μs   (+5.74%) | 
  │ └ sirius::Simulation_context::update                                |        3.50 s  →        3.66 s    (+4.48%) |       1   →       1              |        3.50 s  →        3.66 s    (+4.48%) | 
- │   ├ sirius::Unit_cell::update                                       |        7.15 ms →        8.02 ms  (+12.14%) |       1   →       1              |        7.15 ms →        8.02 ms  (+12.14%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.77 ms →        3.60 ms   (-4.47%) |       1   →       1              |        3.77 ms →        3.60 ms   (-4.47%) | 
- │   │ └ sirius::Unit_cell::get_symmetry                               |        3.33 ms →        4.37 ms  (+31.20%) |       1   →       1              |        3.33 ms →        4.37 ms  (+31.20%) | 
- │   │   └ sirius::Unit_cell_symmetry                                  |        3.28 ms →        4.32 ms  (+31.70%) |       1   →       1              |        3.28 ms →        4.32 ms  (+31.70%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.73 ms →        2.80 ms   (+2.36%) |       1   →       1              |        2.73 ms →        2.80 ms   (+2.36%) | 
- │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      507.46 μs →        1.48 ms (+192.49%) |       1   →       1              |      507.46 μs →        1.48 ms (+192.49%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       14.56 μs →       14.65 μs   (+0.67%) |       1   →       1              |       14.56 μs →       14.65 μs   (+0.67%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      211.85 ms →      210.43 ms   (-0.67%) |       2   →       2              |      423.70 ms →      420.87 ms   (-0.67%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.17 ms →       15.15 ms   (-0.15%) |       2   →       2              |       30.35 ms →       30.31 ms   (-0.15%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.30 ms →       13.24 ms   (-0.47%) |       1   →       1              |       13.30 ms →       13.24 ms   (-0.47%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.43 ms →       56.56 ms   (+0.24%) |       2   →       2              |      112.86 ms →      113.13 ms   (+0.24%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.18 ms →       45.05 ms   (-0.28%) |       2   →       2              |       90.36 ms →       90.10 ms   (-0.28%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.19 ms →       60.06 ms   (-0.22%) |       4   →       4              |      240.78 ms →      240.25 ms   (-0.22%) | 
  │   ├ sddk::Gvec::init                                                |       92.97 ms →       92.84 ms   (-0.15%) |       2   →       2              |      185.95 ms →      185.68 ms   (-0.15%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       69.31 ms →       69.58 ms   (+0.39%) |       2   →       2              |      138.63 ms →      139.16 ms   (+0.39%) | 
- │   ├ sddk::Gvec_shells                                               |       97.15 ms →      140.56 ms  (+44.69%) |       1   →       1              |       97.15 ms →      140.56 ms  (+44.69%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.99 ms →        2.04 ms   (+2.47%) |       1   →       1              |        1.99 ms →        2.04 ms   (+2.47%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      603.98 ms →      652.55 ms   (+8.04%) |       2   →       2              |        1.21 s  →        1.31 s    (+8.04%) | 
+ ├ sirius::K_point_set::create_k_mesh                                  |      149.56 ms →       89.20 ms  (-40.36%) |       1   →       1              |      149.56 ms →       89.20 ms  (-40.36%) | 
+ │ ├ sirius::K_point::K_point                                          |        4.45 μs →        1.27 μs  (-71.54%) |       4   →       4              |       17.80 μs →        5.07 μs  (-71.54%) | 
+ │ └ sirius::K_point_set::initialize                                   |      149.47 ms →       89.12 ms  (-40.37%) |       1   →       1              |      149.47 ms →       89.12 ms  (-40.37%) | 
  │   └ sirius::K_point::initialize                                     |       28.54 ms →       27.60 ms   (-3.30%) |       1   →       1              |       28.54 ms →       27.60 ms   (-3.30%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       11.11 ms →       10.91 ms   (-1.77%) |       1   →       1              |       11.11 ms →       10.91 ms   (-1.77%) | 
  │     │ └ sddk::Gvec::init                                            |        5.03 ms →        4.94 ms   (-1.75%) |       1   →       1              |        5.03 ms →        4.94 ms   (-1.75%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |       10.85 μs →       10.10 μs   (-6.91%) |       1   →       1              |       10.85 μs →       10.10 μs   (-6.91%) | 
  │     └ sirius::K_point::update                                       |       14.55 ms →       13.77 ms   (-5.37%) |       1   →       1              |       14.55 ms →       13.77 ms   (-5.37%) | 
  │       └ sirius::Beta_projectors                                     |       10.54 ms →        9.97 ms   (-5.49%) |       1   →       1              |       10.54 ms →        9.97 ms   (-5.49%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.60 ms →        8.20 ms   (-4.74%) |       1   →       1              |        8.60 ms →        8.20 ms   (-4.74%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.56 ms →        2.54 ms   (-0.81%) |       2   →       2              |        5.13 ms →        5.09 ms   (-0.81%) | 
  ├ sirius::Potential                                                   |       52.15 ms →       54.10 ms   (+3.74%) |       1   →       1              |       52.15 ms →       54.10 ms   (+3.74%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.93 ms →        2.94 ms   (+0.44%) |       6   →       6              |       17.55 ms →       17.63 ms   (+0.44%) | 
  │ └ sirius::Potential::update                                         |       33.98 ms →       35.87 ms   (+5.57%) |       1   →       1              |       33.98 ms →       35.87 ms   (+5.57%) | 
  │   └ sirius::Potential::generate_local_potential                     |       33.58 ms →       35.47 ms   (+5.63%) |       1   →       1              |       33.58 ms →       35.47 ms   (+5.63%) | 
- │     ├ sirius::Simulation_context::make_periodic_function            |       26.71 ms →       31.08 ms  (+16.36%) |       1   →       1              |       26.71 ms →       31.08 ms  (+16.36%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        6.33 ms →        3.85 ms  (-39.17%) |       1   →       1              |        6.33 ms →        3.85 ms  (-39.17%) | 
  ├ sirius::Density                                                     |       38.59 ms →       41.94 ms   (+8.66%) |       1   →       1              |       38.59 ms →       41.94 ms   (+8.66%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.84 ms →        2.82 ms   (-0.67%) |       2   →       2              |        5.69 ms →        5.65 ms   (-0.67%) | 
- │ └ sirius::Density::update                                           |       32.77 ms →       36.15 ms  (+10.32%) |       1   →       1              |       32.77 ms →       36.15 ms  (+10.32%) | 
- │   └ sirius::Density::generate_pseudo_core_charge_density            |       32.45 ms →       35.86 ms  (+10.53%) |       1   →       1              |       32.45 ms →       35.86 ms  (+10.53%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |       77.88 μs →       78.84 μs   (+1.23%) |       1   →       1              |       77.88 μs →       78.84 μs   (+1.23%) | 
- │     ├ sirius::Simulation_context::make_periodic_function            |       26.96 ms →       31.45 ms  (+16.63%) |       1   →       1              |       26.96 ms →       31.45 ms  (+16.63%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        5.08 ms →        4.02 ms  (-20.94%) |       1   →       1              |        5.08 ms →        4.02 ms  (-20.94%) | 
- ├ sirius::Density::initial_density                                    |       59.05 ms →       65.61 ms  (+11.11%) |       1   →       1              |       59.05 ms →       65.61 ms  (+11.11%) | 
- │ ├ sirius::Simulation_context::make_periodic_function                |       27.79 ms →       37.15 ms  (+33.69%) |       1   →       1              |       27.79 ms →       37.15 ms  (+33.69%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        6.63 ms →        4.95 ms  (-25.35%) |       2   →       2              |       13.27 ms →        9.90 ms  (-25.35%) | 
  │ └ sirius::Periodic_function::integrate                              |        4.54 ms →        4.80 ms   (+5.70%) |       1   →       1              |        4.54 ms →        4.80 ms   (+5.70%) | 
  ├ sirius::Potential::generate                                         |      367.42 ms →      372.58 ms   (+1.41%) |       1   →       1              |      367.42 ms →      372.58 ms   (+1.41%) | 
- │ ├ sirius::Potential::poisson                                        |       40.24 ms →       44.62 ms  (+10.88%) |       1   →       1              |       40.24 ms →       44.62 ms  (+10.88%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        9.18 ms →        3.63 ms  (-60.48%) |       1   →       1              |        9.18 ms →        3.63 ms  (-60.48%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        4.64 ms →        4.84 ms   (+4.16%) |       1   →       1              |        4.64 ms →        4.84 ms   (+4.16%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.63 ms →        4.83 ms   (+4.14%) |       1   →       1              |        4.63 ms →        4.83 ms   (+4.14%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.63 ms →        4.82 ms   (+4.17%) |       1   →       1              |        4.63 ms →        4.82 ms   (+4.17%) | 
  │ ├ sirius::Periodic_function::add                                    |      785.02 μs →      776.38 μs   (-1.10%) |       2   →       2              |        1.57 ms →        1.55 ms   (-1.10%) | 
  │ ├ sirius::Potential::xc                                             |       51.80 ms →       52.29 ms   (+0.95%) |       1   →       1              |       51.80 ms →       52.29 ms   (+0.95%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       50.61 ms →       51.11 ms   (+1.00%) |       1   →       1              |       50.61 ms →       51.11 ms   (+1.00%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.55 ms →        2.55 ms   (-0.18%) |       2   →       2              |        5.10 ms →        5.09 ms   (-0.18%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.78 ms →        4.91 ms   (+2.74%) |       1   →       1              |        4.78 ms →        4.91 ms   (+2.74%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.62 ms →        3.69 ms   (+1.97%) |       1   →       1              |        3.62 ms →        3.69 ms   (+1.97%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      268.83 ms →      269.01 ms   (+0.07%) |       1   →       1              |      268.83 ms →      269.01 ms   (+0.07%) | 
- │ └ sirius::Potential::generate_PAW_effective_potential               |      242.00 ns →      335.00 ns  (+38.43%) |       1   →       1              |      242.00 ns →      335.00 ns  (+38.43%) | 
  ├ sirius::Hamiltonian0                                                |        8.49 ms →        8.38 ms   (-1.35%) |       1   →       1              |        8.49 ms →        8.38 ms   (-1.35%) | 
  │ ├ sirius::Local_operator                                            |        7.25 ms →        7.77 ms   (+7.09%) |       1   →       1              |        7.25 ms →        7.77 ms   (+7.09%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.74 ms →        2.72 ms   (-1.04%) |       1   →       1              |        2.74 ms →        2.72 ms   (-1.04%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        3.44 ms →        3.54 ms   (+2.99%) |       1   →       1              |        3.44 ms →        3.54 ms   (+2.99%) | 
+ │ ├ sirius::Non_local_operator                                        |      479.36 μs →      171.88 μs  (-64.14%) |       2   →       2              |      958.71 μs →      343.76 μs  (-64.14%) | 
  │ ├ sirius::D_operator::initialize                                    |      110.23 μs →      106.96 μs   (-2.96%) |       1   →       1              |      110.23 μs →      106.96 μs   (-2.96%) | 
  │ └ sirius::Q_operator::initialize                                    |      101.64 μs →       96.56 μs   (-5.00%) |       1   →       1              |      101.64 μs →       96.56 μs   (-5.00%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.29 s  →        1.30 s    (+1.16%) |       1   →       1              |        1.29 s  →        1.30 s    (+1.16%) | 
+ │ ├ sirius::Hamiltonian_k                                             |       77.64 ms →       65.20 ms  (-16.02%) |       1   →       1              |       77.64 ms →       65.20 ms  (-16.02%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      287.45 μs →      264.81 μs   (-7.87%) |       1   →       1              |      287.45 μs →      264.81 μs   (-7.87%) | 
+ │ │ └ sirius::Beta_projectors_base::prepare                           |       77.35 ms →       64.93 ms  (-16.05%) |       1   →       1              |       77.35 ms →       64.93 ms  (-16.05%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.21 s  →        1.24 s    (+2.26%) |       1   →       1              |        1.21 s  →        1.24 s    (+2.26%) | 
+ │ │ ├ sddk::matrix_storage::matrix_storage                            |      107.95 ms →       91.39 ms  (-15.34%) |       4   →       4              |      431.79 ms →      365.57 ms  (-15.34%) | 
- │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       45.96 ms →       52.96 ms  (+15.22%) |       1   →       1              |       45.96 ms →       52.96 ms  (+15.22%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        7.47 ms →        7.86 ms   (+5.17%) |       1   →       1              |        7.47 ms →        7.86 ms   (+5.17%) | 
+ │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      511.55 ms →      382.55 ms  (-25.22%) |       1   →       1              |      511.55 ms →      382.55 ms  (-25.22%) | 
+ │ │ │ ├ sirius::Local_operator::apply_h                               |      440.26 ms →      271.16 ms  (-38.41%) |       1   →       1              |      440.26 ms →      271.16 ms  (-38.41%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.62 μs →        4.35 μs  (+20.06%) |       1   →       1              |        3.62 μs →        4.35 μs  (+20.06%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.65 μs →        3.43 μs  (+29.34%) |       1   →       1              |        2.65 μs →        3.43 μs  (+29.34%) | 
- │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      446.00 ns →      533.00 ns  (+19.51%) |       1   →       1              |      446.00 ns →      533.00 ns  (+19.51%) | 
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      886.00 ns →      642.00 ns  (-27.54%) |       1   →       1              |      886.00 ns →      642.00 ns  (-27.54%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.00 ms →        3.06 ms   (+2.10%) |       1   →       1              |        3.00 ms →        3.06 ms   (+2.10%) | 
- │ │ │ ├ sirius::Beta_projectors_base::inner                           |       24.54 ms →       39.53 ms  (+61.09%) |       1   →       1              |       24.54 ms →       39.53 ms  (+61.09%) | 
- │ │ │ └ sirius::Non_local_operator::apply                             |       21.86 ms →       34.38 ms  (+57.29%) |       2   →       2              |       43.71 ms →       68.75 ms  (+57.29%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |        6.47 ms →        6.59 ms   (+1.89%) |       2   →       2              |       12.94 ms →       13.19 ms   (+1.89%) | 
  │ │ │ └ sddk::wf_inner                                                |        6.26 ms →        6.38 ms   (+1.97%) |       2   →       2              |       12.52 ms →       12.77 ms   (+1.97%) | 
  │ │ │   ├ sddk::wf_inner|scale                                        |       33.00 ns →       34.00 ns   (+3.03%) |       2   →       2              |       66.00 ns →       68.00 ns   (+3.03%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |        6.13 ms →        6.25 ms   (+1.86%) |       2   →       2              |       12.26 ms →       12.49 ms   (+1.86%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       22.00 ns →       36.00 ns  (+63.64%) |       2   →       2              |       44.00 ns →       72.00 ns  (+63.64%) | 
- │ │ ├ Eigensolver_cuda|zhegvdx                                        |       65.24 ms →      204.01 ms (+212.72%) |       1   →       1              |       65.24 ms →      204.01 ms (+212.72%) | 
  │ │ └ sddk::wf_trans                                                  |        2.59 ms →        2.60 ms   (+0.37%) |       1   →       1              |        2.59 ms →        2.60 ms   (+0.37%) | 
  │ │   └ sddk::wf_trans|pw                                             |        2.59 ms →        2.59 ms   (+0.34%) |       1   →       1              |        2.59 ms →        2.59 ms   (+0.34%) | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      371.00 ns →      427.00 ns  (+15.09%) |       1   →       1              |      371.00 ns →      427.00 ns  (+15.09%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |       63.09 s  →       63.50 s    (+0.64%) |       1   →       1              |       63.09 s  →       63.50 s    (+0.64%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.44 ms →        2.44 ms   (+0.14%) |      19   →      19              |       46.33 ms →       46.39 ms   (+0.14%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        2.98 s  →        3.11 s    (+4.40%) |      21   →      20     (-4.76%) |       62.50 s  →       62.14 s    (-0.57%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        4.87 ms →        4.94 ms   (+1.37%) |      21   →      20     (-4.76%) |      102.25 ms →       98.72 ms   (-3.46%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.19 ms →        4.31 ms   (+2.82%) |      21   →      20     (-4.76%) |       88.07 ms →       86.24 ms   (-2.08%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      548.80 μs →      549.83 μs   (+0.19%) |      21   →      20     (-4.76%) |       11.52 ms →       11.00 ms   (-4.58%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.35 ms →        2.47 ms   (+5.12%) |      21   →      20     (-4.76%) |       49.30 ms →       49.36 ms   (+0.11%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |      199.54 μs →      162.29 μs  (-18.67%) |      42   →      40     (-4.76%) |        8.38 ms →        6.49 ms  (-22.54%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |      105.11 μs →      119.18 μs  (+13.38%) |      21   →      20     (-4.76%) |        2.21 ms →        2.38 ms   (+7.98%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       93.65 μs →       95.67 μs   (+2.15%) |      21   →      20     (-4.76%) |        1.97 ms →        1.91 ms   (-2.71%) | 
  │ │ ├ sirius::Band::solve                                             |        1.76 s  →        1.88 s    (+6.87%) |      21   →      20     (-4.76%) |       36.90 s  →       37.56 s    (+1.78%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      199.05 μs →      209.36 μs   (+5.18%) |      21   →      20     (-4.76%) |        4.18 ms →        4.19 ms   (+0.17%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      189.93 μs →      200.44 μs   (+5.53%) |      21   →      20     (-4.76%) |        3.99 ms →        4.01 ms   (+0.51%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        6.68 μs →        6.45 μs   (-3.34%) |      21   →      20     (-4.76%) |      140.22 μs →      129.09 μs   (-7.94%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.64 s  →        1.75 s    (+7.02%) |      21   →      20     (-4.76%) |       34.38 s  →       35.05 s    (+1.93%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       74.01 ms →       78.34 ms   (+5.84%) |      21   →      20     (-4.76%) |        1.55 s  →        1.57 s    (+0.80%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.36 ms →        6.33 ms  (-13.91%) |     126   →     140    (+11.11%) |      927.08 ms →      886.83 ms   (-4.34%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       15.13 ms →       13.21 ms  (-12.64%) |      21   →      20     (-4.76%) |      317.64 ms →      264.29 ms  (-16.80%) | 
+ │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      485.77 μs →      458.28 μs   (-5.66%) |      21   →      20     (-4.76%) |       10.20 ms →        9.17 ms  (-10.15%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        6.89 ms →        5.70 ms  (-17.20%) |      42   →      40     (-4.76%) |      289.25 ms →      228.08 ms  (-21.15%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.54 s  →        1.64 s    (+6.54%) |      21   →      20     (-4.76%) |       32.35 s  →       32.82 s    (+1.46%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       58.01 ms →       67.71 ms  (+16.72%) |     361   →     258    (-28.53%) |       20.94 s  →       17.47 s   (-16.58%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       33.81 ms →       47.85 ms  (+41.51%) |     361   →     258    (-28.53%) |       12.21 s  →       12.34 s    (+1.14%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.95 μs →        1.86 μs   (-4.78%) |     361   →     258    (-28.53%) |      705.47 μs →      480.09 μs  (-31.95%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.59 μs →        1.58 μs   (-1.20%) |     361   →     258    (-28.53%) |      575.50 μs →      406.37 μs  (-29.39%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      428.63 ns →      308.32 ns  (-28.07%) |     361   →     258    (-28.53%) |      154.73 μs →       79.55 μs  (-48.59%) | 
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      580.87 ns →      580.92 ns   (+0.01%) |     361   →     258    (-28.53%) |      209.69 μs →      149.88 μs  (-28.53%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        3.01 ms →        2.71 ms  (-10.09%) |     361   →     258    (-28.53%) |        1.09 s  →      698.79 ms  (-35.74%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.43 ms →        4.04 ms  (+17.80%) |     361   →     258    (-28.53%) |        1.24 s  →        1.04 s   (-15.81%) | 
+ │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        8.87 ms →        6.55 ms  (-26.19%) |     722   →     516    (-28.53%) |        6.40 s  →        3.38 s   (-47.25%) | 
+ │ │ │ │   ├ sddk::orthogonalize                                       |        6.52 ms →        7.15 ms   (+9.74%) |     361   →     258    (-28.53%) |        2.35 s  →        1.85 s   (-21.57%) | 
+ │ │ │ │   │ ├ sddk::wf_inner                                          |        1.13 ms →        1.16 ms   (+2.51%) |     701   →     496    (-29.24%) |      792.07 ms →      574.51 ms  (-27.47%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       55.93 ns →       53.46 ns   (-4.41%) |     701   →     496    (-29.24%) |       39.21 μs →       26.52 μs  (-32.37%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |      962.30 μs →      981.56 μs   (+2.00%) |     701   →     496    (-29.24%) |      674.57 ms →      486.85 ms  (-27.83%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       49.66 ns →       66.56 ns  (+34.03%) |     701   →     496    (-29.24%) |       34.81 μs →       33.02 μs   (-5.16%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      144.94 μs →      197.85 μs  (+36.51%) |     361   →     258    (-28.53%) |       52.32 ms →       51.05 ms   (-2.44%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        2.01 ms →        2.22 ms  (+10.84%) |     361   →     258    (-28.53%) |      724.41 ms →      573.84 ms  (-20.79%) | 
- │ │ │ │   │ └ sddk::wf_trans                                          |        2.30 ms →        2.71 ms  (+17.68%) |     340   →     238    (-30.00%) |      783.11 ms →      645.09 ms  (-17.62%) | 
- │ │ │ │   │   └ sddk::wf_trans|pw                                     |      766.94 μs →      902.74 μs  (+17.71%) |    1.02 K →     714    (-30.00%) |      782.28 ms →      644.56 ms  (-17.61%) | 
- │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.25 ms →        1.53 ms  (+21.56%) |     361   →     258    (-28.53%) |      452.98 ms →      393.52 ms  (-13.13%) | 
- │ │ │ │   │ └ sddk::wf_inner                                          |        1.21 ms →        1.47 ms  (+21.34%) |     361   →     258    (-28.53%) |      437.43 ms →      379.33 ms  (-13.28%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       60.04 ns →       63.53 ns   (+5.80%) |     361   →     258    (-28.53%) |       21.68 μs →       16.39 μs  (-24.39%) | 
- │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        1.05 ms →        1.30 ms  (+23.99%) |     361   →     258    (-28.53%) |      377.94 ms →      334.89 ms  (-11.39%) | 
+ │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       47.86 ns →       37.76 ns  (-21.11%) |     361   →     258    (-28.53%) |       17.28 μs →        9.74 μs  (-43.62%) | 
- │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       19.73 ms →       46.61 ms (+136.25%) |     361   →     258    (-28.53%) |        7.12 s  →       12.03 s   (+68.85%) | 
+ │ │ │ │   ├ sirius::residuals                                         |        2.86 ms →        2.66 ms   (-6.95%) |     346   →     253    (-26.88%) |      990.45 ms →      673.93 ms  (-31.96%) | 
+ │ │ │ │   │ ├ sddk::wf_trans                                          |        1.35 ms →        1.42 ms   (+5.22%) |     342   →     253    (-26.02%) |      460.14 ms →      358.16 ms  (-22.16%) | 
+ │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      671.33 μs →      706.47 μs   (+5.23%) |     684   →     506    (-26.02%) |      459.19 ms →      357.47 ms  (-22.15%) | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.43 ms →        1.14 ms  (-20.29%) |     342   →     253    (-26.02%) |      490.68 ms →      289.34 ms  (-41.03%) | 
+ │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        5.32 ms →        5.21 ms   (-2.02%) |      90   →      78    (-13.33%) |      479.03 ms →      406.76 ms  (-15.09%) | 
+ │ │ │ │     └ sddk::wf_trans                                          |        2.96 ms →        2.94 ms   (-0.78%) |     159   →     136    (-14.47%) |      470.83 ms →      399.60 ms  (-15.13%) | 
+ │ │ │ │       └ sddk::wf_trans|pw                                     |        2.06 ms →        2.06 ms   (-0.25%) |     228   →     194    (-14.91%) |      470.52 ms →      399.35 ms  (-15.13%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      565.00 ns →      422.15 ns  (-25.28%) |      21   →      20     (-4.76%) |       11.86 μs →        8.44 μs  (-28.84%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       19.62 μs →       31.84 μs  (+62.24%) |      21   →      20     (-4.76%) |      412.07 μs →      636.71 μs  (+54.52%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.57 ms →        1.56 ms   (-0.84%) |      21   →      20     (-4.76%) |       32.99 ms →       31.15 ms   (-5.56%) | 
  │ │ ├ sirius::Density::generate                                       |      562.43 ms →      562.97 ms   (+0.10%) |      21   →      20     (-4.76%) |       11.81 s  →       11.26 s    (-4.67%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      385.92 ms →      387.97 ms   (+0.53%) |      21   →      20     (-4.76%) |        8.10 s  →        7.76 s    (-4.26%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       11.54 μs →       11.45 μs   (-0.82%) |      21   →      20     (-4.76%) |      242.37 μs →      228.92 μs   (-5.55%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |       10.52 μs →       10.59 μs   (+0.59%) |      21   →      20     (-4.76%) |      221.00 μs →      211.71 μs   (-4.20%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       46.04 ms →       44.97 ms   (-2.32%) |      21   →      20     (-4.76%) |      966.86 ms →      899.49 ms   (-6.97%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       10.73 μs →       10.70 μs   (-0.29%) |      21   →      20     (-4.76%) |      225.32 μs →      213.97 μs   (-5.04%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |       24.08 ms →       23.87 ms   (-0.87%) |      21   →      20     (-4.76%) |      505.67 ms →      477.42 ms   (-5.59%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       20.92 ms →       20.05 ms   (-4.17%) |      21   →      20     (-4.76%) |      439.29 ms →      400.92 ms   (-8.73%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      961.71 ns →      575.25 ns  (-40.18%) |      21   →      20     (-4.76%) |       20.20 μs →       11.51 μs  (-43.03%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       93.26 ms →       94.32 ms   (+1.13%) |      21   →      20     (-4.76%) |        1.96 s  →        1.89 s    (-3.68%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.98 ms →        2.06 ms   (+3.83%) |      21   →      20     (-4.76%) |       41.62 ms →       41.16 ms   (-1.11%) | 
  │ │ │ │ └ sirius::Density::augment                                    |      195.98 ms →      206.24 ms   (+5.23%) |      21   →      20     (-4.76%) |        4.12 s  →        4.12 s    (+0.22%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |      195.75 ms →      206.03 ms   (+5.25%) |      21   →      20     (-4.76%) |        4.11 s  →        4.12 s    (+0.24%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      149.37 ms →      146.36 ms   (-2.02%) |      21   →      20     (-4.76%) |        3.14 s  →        2.93 s    (-6.69%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      149.37 ms →      146.35 ms   (-2.02%) |      21   →      20     (-4.76%) |        3.14 s  →        2.93 s    (-6.69%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       65.95 ms →       64.13 ms   (-2.77%) |      21   →      20     (-4.76%) |        1.39 s  →        1.28 s    (-7.40%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       70.12 ms →       68.84 ms   (-1.82%) |      21   →      20     (-4.76%) |        1.47 s  →        1.38 s    (-6.49%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.65 ms →       12.74 ms   (+0.68%) |      21   →      20     (-4.76%) |      265.71 ms →      254.78 ms   (-4.11%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.55 ms →       23.80 ms   (+1.09%) |      21   →      20     (-4.76%) |      494.47 ms →      476.07 ms   (-3.72%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        3.58 ms →        4.84 ms  (+35.30%) |      21   →      20     (-4.76%) |       75.16 ms →       96.85 ms  (+28.85%) | 
  │ │ ├ sirius::Density::mix                                            |      136.77 ms →      132.61 ms   (-3.04%) |      21   →      20     (-4.76%) |        2.87 s  →        2.65 s    (-7.66%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      321.32 μs →      888.53 μs (+176.52%) |      21   →      20     (-4.76%) |        6.75 ms →       17.77 ms (+163.36%) | 
+ │ │ │ ├ sirius::Periodic_function|inner                               |        5.01 ms →        4.71 ms   (-5.96%) |     259   →     244     (-5.79%) |        1.30 s  →        1.15 s   (-11.41%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.83 ms →        4.62 ms   (-4.37%) |     259   →     244     (-5.79%) |        1.25 s  →        1.13 s    (-9.91%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.83 ms →        4.62 ms   (-4.37%) |     259   →     244     (-5.79%) |        1.25 s  →        1.13 s    (-9.91%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        6.36 ms →        5.46 ms  (-14.10%) |      21   →      20     (-4.76%) |      133.49 ms →      109.21 ms  (-18.19%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.63 ms →        4.71 ms  (-16.33%) |      21   →      20     (-4.76%) |      118.14 ms →       94.15 ms  (-20.31%) | 
  │ │ ├ sirius::Potential::generate                                     |      360.25 ms →      366.48 ms   (+1.73%) |      21   →      20     (-4.76%) |        7.57 s  →        7.33 s    (-3.12%) | 
- │ │ │ ├ sirius::Potential::poisson                                    |       40.00 ms →       44.56 ms  (+11.41%) |      21   →      20     (-4.76%) |      840.02 ms →      891.27 ms   (+6.10%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        8.86 ms →        3.60 ms  (-59.34%) |      21   →      20     (-4.76%) |      186.07 ms →       72.05 ms  (-61.28%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |        4.70 ms →        4.87 ms   (+3.67%) |      21   →      20     (-4.76%) |       98.61 ms →       97.36 ms   (-1.27%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.63 ms →        4.83 ms   (+4.29%) |      21   →      20     (-4.76%) |       97.16 ms →       96.50 ms   (-0.68%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.63 ms →        4.82 ms   (+4.30%) |      21   →      20     (-4.76%) |       97.13 ms →       96.49 ms   (-0.66%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      778.65 μs →      776.02 μs   (-0.34%) |      42   →      40     (-4.76%) |       32.70 ms →       31.04 ms   (-5.08%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       45.05 ms →       46.84 ms   (+3.98%) |      21   →      20     (-4.76%) |      945.99 ms →      936.83 ms   (-0.97%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       43.86 ms →       45.67 ms   (+4.12%) |      21   →      20     (-4.76%) |      921.03 ms →      913.32 ms   (-0.84%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |      682.65 μs →      688.29 μs   (+0.83%) |      42   →      40     (-4.76%) |       28.67 ms →       27.53 ms   (-3.98%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.81 ms →        4.79 ms   (-0.45%) |      21   →      20     (-4.76%) |      101.04 ms →       95.79 ms   (-5.19%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.63 ms →        3.68 ms   (+1.25%) |      21   →      20     (-4.76%) |       76.26 ms →       73.53 ms   (-3.57%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.61 ms →      268.42 ms   (-0.07%) |      21   →      20     (-4.76%) |        5.64 s  →        5.37 s    (-4.83%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      199.90 ns →      216.75 ns   (+8.43%) |      21   →      20     (-4.76%) |        4.20 μs →        4.34 μs   (+3.26%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |       96.06 ms →      104.18 ms   (+8.46%) |      21   →      20     (-4.76%) |        2.02 s  →        2.08 s    (+3.29%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |       96.05 ms →      104.18 ms   (+8.46%) |      21   →      20     (-4.76%) |        2.02 s  →        2.08 s    (+3.29%) | 
- │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.29 ms →       17.70 ms  (+33.17%) |      21   →      20     (-4.76%) |      279.13 ms →      354.01 ms  (+26.83%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       69.54 ms →       68.44 ms   (-1.59%) |      21   →      20     (-4.76%) |        1.46 s  →        1.37 s    (-6.28%) | 
- │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.59 ms →       17.42 ms  (+38.33%) |      21   →      20     (-4.76%) |      264.42 ms →      348.37 ms  (+31.75%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        4.25 ms →        4.42 ms   (+4.10%) |      21   →      20     (-4.76%) |       89.26 ms →       88.49 ms   (-0.85%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.87 ms →        4.66 ms   (-4.11%) |     147   →     140     (-4.76%) |      715.16 ms →      653.09 ms   (-8.68%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.76 ms →        4.58 ms   (-3.78%) |     147   →     140     (-4.76%) |      699.45 ms →      640.96 ms   (-8.36%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.76 ms →        4.58 ms   (-3.78%) |     147   →     140     (-4.76%) |      699.35 ms →      640.89 ms   (-8.36%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.65 ms →        4.81 ms   (+3.28%) |      63   →      60     (-4.76%) |      293.24 ms →      288.44 ms   (-1.64%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.54 ms →        4.74 ms   (+4.38%) |      63   →      60     (-4.76%) |      286.00 ms →      284.32 ms   (-0.59%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.53 ms →        4.55 ms   (+0.28%) |      21   →      20     (-4.76%) |       95.21 ms →       90.93 ms   (-4.49%) | 
  │ │ └ sirius::Density::get_magnetisation                              |       76.03 μs →       73.65 μs   (-3.13%) |      21   →      20     (-4.76%) |        1.60 ms →        1.47 ms   (-7.74%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |       70.64 μs →       68.51 μs   (-3.02%) |      21   →      20     (-4.76%) |        1.48 ms →        1.37 ms   (-7.64%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.66 ms →        5.26 ms   (-6.94%) |       2   →       2              |       11.31 ms →       10.53 ms   (-6.94%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.99 ms →        4.80 ms   (-3.75%) |       6   →       6              |       29.94 ms →       28.82 ms   (-3.75%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.99 ms →        4.54 ms   (-8.92%) |       6   →       6              |       29.92 ms →       27.25 ms   (-8.92%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.99 ms →        4.54 ms   (-8.95%) |       6   →       6              |       29.91 ms →       27.24 ms   (-8.95%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.81 ms →        4.71 ms   (-2.05%) |       3   →       3              |       14.43 ms →       14.14 ms   (-2.05%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.80 ms →        4.70 ms   (-2.26%) |       3   →       3              |       14.41 ms →       14.09 ms   (-2.26%) | 
  ├ sirius::Periodic_function|inner                                     |        4.96 ms →        4.54 ms   (-8.53%) |       2   →       2              |        9.92 ms →        9.07 ms   (-8.53%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.96 ms →        4.53 ms   (-8.67%) |       2   →       2              |        9.91 ms →        9.05 ms   (-8.67%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.96 ms →        4.53 ms   (-8.67%) |       2   →       2              |        9.91 ms →        9.05 ms   (-8.67%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.80 ms →        4.78 ms   (-0.37%) |       1   →       1              |        4.80 ms →        4.78 ms   (-0.37%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.80 ms →        4.73 ms   (-1.29%) |       1   →       1              |        4.80 ms →        4.73 ms   (-1.29%) | 
- └ sirius::finalize                                                    |      162.78 ms →      212.51 ms  (+30.54%) |       1   →       1              |      162.78 ms →      212.51 ms  (+30.54%) | 
  ====================================================================================================================================================================================================
```
