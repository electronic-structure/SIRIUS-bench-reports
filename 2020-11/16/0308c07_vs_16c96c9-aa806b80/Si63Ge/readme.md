# Benchmark 16c96c9521ba11c164891eb65cdeac5a4e0e34b3 vs 0308c074b92841e183b2aa72e055c15d8e0ec6ab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
- sirius                                                                |       71.66 s  →       90.42 s   (+26.18%) |       1   →       1              |       71.66 s  →       90.42 s   (+26.18%) | 
+ ├ sirius::initialize                                                  |        2.92 s  →        2.45 s   (-16.18%) |       1   →       1              |        2.92 s  →        2.45 s   (-16.18%) | 
  ├ sirius::Simulation_context::initialize                              |        3.81 s  →        3.80 s    (-0.29%) |       1   →       1              |        3.81 s  →        3.80 s    (-0.29%) | 
- │ ├ sirius::Simulation_context::init_comm                             |       58.40 ms →      231.35 ms (+296.12%) |       1   →       1              |       58.40 ms →      231.35 ms (+296.12%) | 
  │ ├ sirius::Unit_cell::initialize                                     |      141.19 ms →      127.21 ms   (-9.90%) |       1   →       1              |      141.19 ms →      127.21 ms   (-9.90%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       60.80 ms →       53.56 ms  (-11.91%) |       2   →       2              |      121.60 ms →      107.11 ms  (-11.91%) | 
  │ │ └ sirius::Unit_cell::update                                       |       19.50 ms →       20.02 ms   (+2.62%) |       1   →       1              |       19.50 ms →       20.02 ms   (+2.62%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.88 ms →        3.90 ms   (+0.44%) |       1   →       1              |        3.88 ms →        3.90 ms   (+0.44%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       15.57 ms →       16.04 ms   (+3.03%) |       1   →       1              |       15.57 ms →       16.04 ms   (+3.03%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       15.49 ms →       15.98 ms   (+3.13%) |       1   →       1              |       15.49 ms →       15.98 ms   (+3.13%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.73 ms →        2.74 ms   (+0.32%) |       1   →       1              |        2.73 ms →        2.74 ms   (+0.32%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      513.07 μs →      509.67 μs   (-0.66%) |       1   →       1              |      513.07 μs →      509.67 μs   (-0.66%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       16.38 μs →       15.46 μs   (-5.57%) |       1   →       1              |       16.38 μs →       15.46 μs   (-5.57%) | 
  │ └ sirius::Simulation_context::update                                |        3.41 s  →        3.39 s    (-0.66%) |       1   →       1              |        3.41 s  →        3.39 s    (-0.66%) | 
  │   ├ sirius::Unit_cell::update                                       |        7.01 ms →        6.99 ms   (-0.18%) |       1   →       1              |        7.01 ms →        6.99 ms   (-0.18%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.63 ms →        3.65 ms   (+0.43%) |       1   →       1              |        3.63 ms →        3.65 ms   (+0.43%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.33 ms →        3.31 ms   (-0.64%) |       1   →       1              |        3.33 ms →        3.31 ms   (-0.64%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.29 ms →        3.27 ms   (-0.58%) |       1   →       1              |        3.29 ms →        3.27 ms   (-0.58%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.73 ms →        2.71 ms   (-0.53%) |       1   →       1              |        2.73 ms →        2.71 ms   (-0.53%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      520.45 μs →      517.40 μs   (-0.59%) |       1   →       1              |      520.45 μs →      517.40 μs   (-0.59%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       14.18 μs →       14.15 μs   (-0.18%) |       1   →       1              |       14.18 μs →       14.15 μs   (-0.18%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      212.97 ms →      211.61 ms   (-0.63%) |       2   →       2              |      425.93 ms →      423.23 ms   (-0.63%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.17 ms →       15.18 ms   (+0.07%) |       2   →       2              |       30.33 ms →       30.35 ms   (+0.07%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.25 ms →       13.28 ms   (+0.20%) |       1   →       1              |       13.25 ms →       13.28 ms   (+0.20%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.37 ms →       56.50 ms   (+0.22%) |       2   →       2              |      112.74 ms →      112.99 ms   (+0.22%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.07 ms →       45.16 ms   (+0.20%) |       2   →       2              |       90.13 ms →       90.31 ms   (+0.20%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.23 ms →       60.37 ms   (+0.22%) |       4   →       4              |      240.94 ms →      241.47 ms   (+0.22%) | 
  │   ├ sddk::Gvec::init                                                |       93.24 ms →       92.79 ms   (-0.48%) |       2   →       2              |      186.48 ms →      185.58 ms   (-0.48%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       69.73 ms →       69.31 ms   (-0.59%) |       2   →       2              |      139.45 ms →      138.63 ms   (-0.59%) | 
  │   ├ sddk::Gvec_shells                                               |       94.91 ms →       98.47 ms   (+3.75%) |       1   →       1              |       94.91 ms →       98.47 ms   (+3.75%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.98 ms →        1.93 ms   (-2.74%) |       1   →       1              |        1.98 ms →        1.93 ms   (-2.74%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      548.38 ms →      566.77 ms   (+3.35%) |       2   →       2              |        1.10 s  →        1.13 s    (+3.35%) | 
+ ├ sirius::K_point_set::create_k_mesh                                  |      147.06 ms →       87.98 ms  (-40.18%) |       1   →       1              |      147.06 ms →       87.98 ms  (-40.18%) | 
+ │ ├ sirius::K_point::K_point                                          |        2.61 μs →        1.63 μs  (-37.42%) |       4   →       4              |       10.44 μs →        6.53 μs  (-37.42%) | 
+ │ └ sirius::K_point_set::initialize                                   |      146.97 ms →       87.88 ms  (-40.20%) |       1   →       1              |      146.97 ms →       87.88 ms  (-40.20%) | 
  │   └ sirius::K_point::initialize                                     |       28.32 ms →       28.30 ms   (-0.08%) |       1   →       1              |       28.32 ms →       28.30 ms   (-0.08%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       11.14 ms →       10.88 ms   (-2.35%) |       1   →       1              |       11.14 ms →       10.88 ms   (-2.35%) | 
  │     │ └ sddk::Gvec::init                                            |        5.06 ms →        4.93 ms   (-2.45%) |       1   →       1              |        5.06 ms →        4.93 ms   (-2.45%) | 
- │     ├ sddk::matrix_storage::matrix_storage                          |        7.90 μs →        9.98 μs  (+26.28%) |       1   →       1              |        7.90 μs →        9.98 μs  (+26.28%) | 
  │     └ sirius::K_point::update                                       |       14.34 ms →       14.58 ms   (+1.70%) |       1   →       1              |       14.34 ms →       14.58 ms   (+1.70%) | 
  │       └ sirius::Beta_projectors                                     |       10.36 ms →       10.66 ms   (+2.87%) |       1   →       1              |       10.36 ms →       10.66 ms   (+2.87%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.38 ms →        8.79 ms   (+5.00%) |       1   →       1              |        8.38 ms →        8.79 ms   (+5.00%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.53 ms →        2.59 ms   (+2.47%) |       2   →       2              |        5.06 ms →        5.18 ms   (+2.47%) | 
  ├ sirius::Potential                                                   |       55.48 ms →       51.95 ms   (-6.37%) |       1   →       1              |       55.48 ms →       51.95 ms   (-6.37%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.94 ms →        2.91 ms   (-0.98%) |       6   →       6              |       17.62 ms →       17.45 ms   (-0.98%) | 
  │ └ sirius::Potential::update                                         |       37.29 ms →       33.93 ms   (-9.00%) |       1   →       1              |       37.29 ms →       33.93 ms   (-9.00%) | 
  │   └ sirius::Potential::generate_local_potential                     |       36.87 ms →       33.55 ms   (-9.00%) |       1   →       1              |       36.87 ms →       33.55 ms   (-9.00%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       32.10 ms →       26.63 ms  (-17.04%) |       1   →       1              |       32.10 ms →       26.63 ms  (-17.04%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        4.22 ms →        6.40 ms  (+51.74%) |       1   →       1              |        4.22 ms →        6.40 ms  (+51.74%) | 
  ├ sirius::Density                                                     |       42.41 ms →       39.10 ms   (-7.79%) |       1   →       1              |       42.41 ms →       39.10 ms   (-7.79%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.83 ms →        2.81 ms   (-0.84%) |       2   →       2              |        5.67 ms →        5.62 ms   (-0.84%) | 
  │ └ sirius::Density::update                                           |       36.60 ms →       33.34 ms   (-8.89%) |       1   →       1              |       36.60 ms →       33.34 ms   (-8.89%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       36.28 ms →       33.07 ms   (-8.84%) |       1   →       1              |       36.28 ms →       33.07 ms   (-8.84%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |       54.01 μs →       53.97 μs   (-0.08%) |       1   →       1              |       54.01 μs →       53.97 μs   (-0.08%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       32.24 ms →       26.63 ms  (-17.41%) |       1   →       1              |       32.24 ms →       26.63 ms  (-17.41%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        3.64 ms →        6.06 ms  (+66.35%) |       1   →       1              |        3.64 ms →        6.06 ms  (+66.35%) | 
  ├ sirius::Density::initial_density                                    |       64.98 ms →       59.99 ms   (-7.68%) |       1   →       1              |       64.98 ms →       59.99 ms   (-7.68%) | 
+ │ ├ sirius::Simulation_context::make_periodic_function                |       37.24 ms →       27.60 ms  (-25.89%) |       1   →       1              |       37.24 ms →       27.60 ms  (-25.89%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.30 ms →        7.16 ms  (+66.31%) |       2   →       2              |        8.61 ms →       14.31 ms  (+66.31%) | 
+ │ └ sirius::Periodic_function::integrate                              |        5.71 ms →        4.51 ms  (-20.95%) |       1   →       1              |        5.71 ms →        4.51 ms  (-20.95%) | 
  ├ sirius::Potential::generate                                         |      372.39 ms →      367.92 ms   (-1.20%) |       1   →       1              |      372.39 ms →      367.92 ms   (-1.20%) | 
+ │ ├ sirius::Potential::poisson                                        |       45.33 ms →       40.26 ms  (-11.18%) |       1   →       1              |       45.33 ms →       40.26 ms  (-11.18%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.64 ms →       10.03 ms (+175.47%) |       1   →       1              |        3.64 ms →       10.03 ms (+175.47%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        4.84 ms →        4.64 ms   (-4.20%) |       1   →       1              |        4.84 ms →        4.64 ms   (-4.20%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.83 ms →        4.63 ms   (-4.20%) |       1   →       1              |        4.83 ms →        4.63 ms   (-4.20%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.83 ms →        4.62 ms   (-4.20%) |       1   →       1              |        4.83 ms →        4.62 ms   (-4.20%) | 
  │ ├ sirius::Periodic_function::add                                    |      778.23 μs →      768.14 μs   (-1.30%) |       2   →       2              |        1.56 ms →        1.54 ms   (-1.30%) | 
  │ ├ sirius::Potential::xc                                             |       51.00 ms →       51.24 ms   (+0.47%) |       1   →       1              |       51.00 ms →       51.24 ms   (+0.47%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       49.79 ms →       50.06 ms   (+0.53%) |       1   →       1              |       49.79 ms →       50.06 ms   (+0.53%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.58 ms →        2.56 ms   (-1.03%) |       2   →       2              |        5.16 ms →        5.11 ms   (-1.03%) | 
+ │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.15 ms →        3.74 ms  (-10.00%) |       1   →       1              |        4.15 ms →        3.74 ms  (-10.00%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.87 ms →        3.91 ms   (+1.10%) |       1   →       1              |        3.87 ms →        3.91 ms   (+1.10%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      269.26 ms →      269.57 ms   (+0.12%) |       1   →       1              |      269.26 ms →      269.57 ms   (+0.12%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      159.00 ns →      162.00 ns   (+1.89%) |       1   →       1              |      159.00 ns →      162.00 ns   (+1.89%) | 
- ├ sirius::Hamiltonian0                                                |        6.92 ms →        8.50 ms  (+22.74%) |       1   →       1              |        6.92 ms →        8.50 ms  (+22.74%) | 
- │ ├ sirius::Local_operator                                            |        6.41 ms →        7.43 ms  (+15.94%) |       1   →       1              |        6.41 ms →        7.43 ms  (+15.94%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.74 ms →        2.75 ms   (+0.19%) |       1   →       1              |        2.74 ms →        2.75 ms   (+0.19%) | 
- │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.91 ms →        3.61 ms  (+24.25%) |       1   →       1              |        2.91 ms →        3.61 ms  (+24.25%) | 
- │ ├ sirius::Non_local_operator                                        |       72.96 μs →      398.14 μs (+445.72%) |       2   →       2              |      145.91 μs →      796.28 μs (+445.72%) | 
+ │ ├ sirius::D_operator::initialize                                    |      171.77 μs →      111.24 μs  (-35.24%) |       1   →       1              |      171.77 μs →      111.24 μs  (-35.24%) | 
+ │ └ sirius::Q_operator::initialize                                    |      110.88 μs →       94.54 μs  (-14.74%) |       1   →       1              |      110.88 μs →       94.54 μs  (-14.74%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.28 s  →        1.29 s    (+0.71%) |       1   →       1              |        1.28 s  →        1.29 s    (+0.71%) | 
- │ ├ sirius::Hamiltonian_k                                             |       44.81 ms →       83.06 ms  (+85.37%) |       1   →       1              |       44.81 ms →       83.06 ms  (+85.37%) | 
+ │ │ ├ sirius::Local_operator::prepare_k                               |      336.18 μs →      223.73 μs  (-33.45%) |       1   →       1              |      336.18 μs →      223.73 μs  (-33.45%) | 
- │ │ └ sirius::Beta_projectors_base::prepare                           |       44.46 ms →       82.83 ms  (+86.28%) |       1   →       1              |       44.46 ms →       82.83 ms  (+86.28%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.23 s  →        1.20 s    (-2.36%) |       1   →       1              |        1.23 s  →        1.20 s    (-2.36%) | 
- │ │ ├ sddk::matrix_storage::matrix_storage                            |       79.04 ms →      110.60 ms  (+39.93%) |       4   →       4              |      316.16 ms →      442.41 ms  (+39.93%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       41.02 ms →       38.68 ms   (-5.69%) |       1   →       1              |       41.02 ms →       38.68 ms   (-5.69%) | 
+ │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        7.97 ms →        6.58 ms  (-17.47%) |       1   →       1              |        7.97 ms →        6.58 ms  (-17.47%) | 
- │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      336.13 ms →      510.92 ms  (+52.00%) |       1   →       1              |      336.13 ms →      510.92 ms  (+52.00%) | 
- │ │ │ ├ sirius::Local_operator::apply_h                               |      247.51 ms →      420.68 ms  (+69.96%) |       1   →       1              |      247.51 ms →      420.68 ms  (+69.96%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        4.23 μs →        2.43 μs  (-42.46%) |       1   →       1              |        4.23 μs →        2.43 μs  (-42.46%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.04 μs →        1.83 μs  (-39.78%) |       1   →       1              |        3.04 μs →        1.83 μs  (-39.78%) | 
- │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      427.00 ns →      523.00 ns  (+22.48%) |       1   →       1              |      427.00 ns →      523.00 ns  (+22.48%) | 
- │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      573.00 ns →        1.13 μs  (+97.21%) |       1   →       1              |      573.00 ns →        1.13 μs  (+97.21%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.11 ms →        3.02 ms   (-2.98%) |       1   →       1              |        3.11 ms →        3.02 ms   (-2.98%) | 
- │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.29 ms →       38.58 ms  (+81.22%) |       1   →       1              |       21.29 ms →       38.58 ms  (+81.22%) | 
+ │ │ │ └ sirius::Non_local_operator::apply                             |       32.09 ms →       24.30 ms  (-24.27%) |       2   →       2              |       64.18 ms →       48.60 ms  (-24.27%) | 
+ │ │ ├ sirius::Band::set_subspace_mtrx                                 |       15.33 ms →        6.54 ms  (-57.31%) |       2   →       2              |       30.65 ms →       13.09 ms  (-57.31%) | 
+ │ │ │ └ sddk::wf_inner                                                |       15.11 ms →        6.33 ms  (-58.10%) |       2   →       2              |       30.23 ms →       12.67 ms  (-58.10%) | 
  │ │ │   ├ sddk::wf_inner|scale                                        |       21.00 ns →       19.00 ns   (-9.52%) |       2   →       2              |       42.00 ns →       38.00 ns   (-9.52%) | 
+ │ │ │   ├ sddk::wf_inner|pw                                           |       14.98 ms →        6.21 ms  (-58.56%) |       2   →       2              |       29.96 ms →       12.42 ms  (-58.56%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       22.00 ns →       34.00 ns  (+54.55%) |       2   →       2              |       44.00 ns →       68.00 ns  (+54.55%) | 
+ │ │ ├ Eigensolver_cuda|zhegvdx                                        |      233.36 ms →       54.40 ms  (-76.69%) |       1   →       1              |      233.36 ms →       54.40 ms  (-76.69%) | 
  │ │ └ sddk::wf_trans                                                  |        2.62 ms →        2.59 ms   (-1.15%) |       1   →       1              |        2.62 ms →        2.59 ms   (-1.15%) | 
  │ │   └ sddk::wf_trans|pw                                             |        2.61 ms →        2.58 ms   (-1.09%) |       1   →       1              |        2.61 ms →        2.58 ms   (-1.09%) | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      385.00 ns →      363.00 ns   (-5.71%) |       1   →       1              |      385.00 ns →      363.00 ns   (-5.71%) | 
- ├ sirius::DFT_ground_state::scf_loop                                  |       61.84 s  →       81.16 s   (+31.24%) |       1   →       1              |       61.84 s  →       81.16 s   (+31.24%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.42 ms →        2.39 ms   (-1.01%) |      17   →      17              |       41.07 ms →       40.65 ms   (-1.01%) | 
- │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        2.93 s  →        3.00 s    (+2.22%) |      21   →      27    (+28.57%) |       61.58 s  →       80.93 s   (+31.43%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        4.64 ms →        4.68 ms   (+0.89%) |      21   →      27    (+28.57%) |       97.40 ms →      126.35 ms  (+29.72%) | 
- │ │ │ ├ sirius::Local_operator                                        |        4.04 ms →        4.04 ms   (+0.06%) |      21   →      27    (+28.57%) |       84.89 ms →      109.21 ms  (+28.65%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function                            |      553.38 μs →      534.45 μs   (-3.42%) |      21   →      27    (+28.57%) |       11.62 ms →       14.43 ms  (+24.18%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.57 ms →        2.52 ms   (-2.23%) |      21   →      27    (+28.57%) |       54.06 ms →       67.96 ms  (+25.71%) | 
- │ │ │ ├ sirius::Non_local_operator                                    |      137.49 μs →      164.26 μs  (+19.47%) |      42   →      54    (+28.57%) |        5.77 ms →        8.87 ms  (+53.61%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |      139.43 μs →      129.57 μs   (-7.07%) |      21   →      27    (+28.57%) |        2.93 ms →        3.50 ms  (+19.48%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       96.97 μs →       93.16 μs   (-3.93%) |      21   →      27    (+28.57%) |        2.04 ms →        2.52 ms  (+23.52%) | 
- │ │ ├ sirius::Band::solve                                             |        1.76 s  →        1.85 s    (+5.34%) |      21   →      27    (+28.57%) |       36.97 s  →       50.08 s   (+35.44%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      227.96 μs →      221.47 μs   (-2.85%) |      21   →      27    (+28.57%) |        4.79 ms →        5.98 ms  (+24.91%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      218.93 μs →      213.04 μs   (-2.69%) |      21   →      27    (+28.57%) |        4.60 ms →        5.75 ms  (+25.11%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        6.93 μs →        6.29 μs   (-9.35%) |      21   →      27    (+28.57%) |      145.63 μs →      169.74 μs  (+16.56%) | 
- │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.63 s  →        1.67 s    (+2.48%) |      21   →      27    (+28.57%) |       34.27 s  →       45.16 s   (+31.77%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       71.82 ms →       55.58 ms  (-22.61%) |      21   →      27    (+28.57%) |        1.51 s  →        1.50 s    (-0.50%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.24 ms →        5.56 ms  (-23.26%) |     126   →     162    (+28.57%) |      912.26 ms →      900.12 ms   (-1.33%) | 
- │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       17.34 ms →       17.17 ms   (-0.96%) |      21   →      27    (+28.57%) |      364.06 ms →      463.60 ms  (+27.34%) | 
- │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      455.18 μs →      452.93 μs   (-0.50%) |      21   →      27    (+28.57%) |        9.56 ms →       12.23 ms  (+27.93%) | 
- │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        7.82 ms →        7.79 ms   (-0.32%) |      42   →      54    (+28.57%) |      328.28 ms →      420.73 ms  (+28.16%) | 
- │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.53 s  →        1.59 s    (+3.63%) |      21   →      27    (+28.57%) |       32.22 s  →       42.93 s   (+33.23%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       50.63 ms →       67.37 ms  (+33.07%) |     361   →     349     (-3.32%) |       18.28 s  →       23.51 s   (+28.64%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       29.14 ms →       42.24 ms  (+44.99%) |     361   →     349     (-3.32%) |       10.52 s  →       14.74 s   (+40.17%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.19 μs →        2.13 μs   (-2.78%) |     361   →     349     (-3.32%) |      791.74 μs →      744.15 μs   (-6.01%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.87 μs →        1.75 μs   (-6.47%) |     361   →     349     (-3.32%) |      674.01 μs →      609.43 μs   (-9.58%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      418.58 ns →      462.88 ns  (+10.58%) |     361   →     349     (-3.32%) |      151.11 μs →      161.54 μs   (+6.91%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      681.15 ns →      664.10 ns   (-2.50%) |     361   →     349     (-3.32%) |      245.90 μs →      231.77 μs   (-5.74%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.73 ms →        2.97 ms   (+8.96%) |     361   →     349     (-3.32%) |      984.33 ms →        1.04 s    (+5.33%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.29 ms →        4.06 ms  (+23.48%) |     361   →     349     (-3.32%) |        1.19 s  →        1.42 s   (+19.38%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.73 ms →        9.04 ms  (+16.93%) |     722   →     698     (-3.32%) |        5.58 s  →        6.31 s   (+13.04%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |        7.12 ms →        8.46 ms  (+18.73%) |     361   →     349     (-3.32%) |        2.57 s  →        2.95 s   (+14.79%) | 
- │ │ │ │   │ ├ sddk::wf_inner                                          |        1.10 ms →        1.37 ms  (+24.35%) |     701   →     671     (-4.28%) |      770.02 ms →      916.57 ms  (+19.03%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       55.11 ns →       46.54 ns  (-15.56%) |     701   →     671     (-4.28%) |       38.63 μs →       31.23 μs  (-19.17%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |      936.05 μs →        1.20 ms  (+28.10%) |     701   →     671     (-4.28%) |      656.17 ms →      804.59 ms  (+22.62%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       38.05 ns →       51.25 ns  (+34.68%) |     701   →     671     (-4.28%) |       26.67 μs →       34.39 μs  (+28.92%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      286.58 μs →      369.19 μs  (+28.82%) |     361   →     349     (-3.32%) |      103.46 ms →      128.85 ms  (+24.54%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        2.48 ms →        2.64 ms   (+6.28%) |     361   →     349     (-3.32%) |      897.07 ms →      921.75 ms   (+2.75%) | 
- │ │ │ │   │ └ sddk::wf_trans                                          |        2.35 ms →        3.05 ms  (+29.87%) |     340   →     322     (-5.29%) |      798.66 ms →      982.29 ms  (+22.99%) | 
- │ │ │ │   │   └ sddk::wf_trans|pw                                     |      782.21 μs →        1.02 ms  (+29.89%) |    1.02 K →     966     (-5.29%) |      797.85 ms →      981.50 ms  (+23.02%) | 
- │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.27 ms →        1.62 ms  (+27.43%) |     361   →     349     (-3.32%) |      460.02 ms →      566.73 ms  (+23.20%) | 
- │ │ │ │   │ └ sddk::wf_inner                                          |        1.23 ms →        1.57 ms  (+27.66%) |     361   →     349     (-3.32%) |      443.50 ms →      547.34 ms  (+23.41%) | 
- │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       29.80 ns →       56.18 ns  (+88.55%) |     361   →     349     (-3.32%) |       10.76 μs →       19.61 μs  (+82.28%) | 
- │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        1.06 ms →        1.40 ms  (+31.53%) |     361   →     349     (-3.32%) |      383.96 ms →      488.24 ms  (+27.16%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       41.14 ns →       58.77 ns  (+42.87%) |     361   →     349     (-3.32%) |       14.85 μs →       20.51 μs  (+38.12%) | 
- │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       26.21 ms →       40.59 ms  (+54.84%) |     361   →     349     (-3.32%) |        9.46 s  →       14.17 s   (+49.69%) | 
- │ │ │ │   ├ sirius::residuals                                         |        2.78 ms →        3.34 ms  (+20.08%) |     346   →     336     (-2.89%) |      961.11 ms →        1.12 s   (+16.61%) | 
- │ │ │ │   │ ├ sddk::wf_trans                                          |        1.27 ms →        1.70 ms  (+34.20%) |     342   →     326     (-4.68%) |      433.73 ms →      554.86 ms  (+27.93%) | 
- │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      632.71 μs →      849.47 μs  (+34.26%) |     684   →     652     (-4.68%) |      432.77 ms →      553.86 ms  (+27.98%) | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.44 ms →        1.63 ms  (+13.14%) |     342   →     326     (-4.68%) |      492.24 ms →      530.85 ms   (+7.84%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        5.32 ms →        5.52 ms   (+3.76%) |      90   →     109    (+21.11%) |      479.17 ms →      602.14 ms  (+25.66%) | 
- │ │ │ │     └ sddk::wf_trans                                          |        2.96 ms →        3.10 ms   (+4.71%) |     159   →     191    (+20.13%) |      470.73 ms →      592.08 ms  (+25.78%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |        2.06 ms →        2.17 ms   (+5.05%) |     228   →     273    (+19.74%) |      470.43 ms →      591.70 ms  (+25.78%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      379.67 ns →      529.44 ns  (+39.45%) |      21   →      27    (+28.57%) |        7.97 μs →       14.29 μs  (+79.29%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       20.26 μs →       20.16 μs   (-0.49%) |      21   →      27    (+28.57%) |      425.51 μs →      544.39 μs  (+27.94%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.58 ms →        1.49 ms   (-5.84%) |      21   →      27    (+28.57%) |       33.28 ms →       40.28 ms  (+21.06%) | 
- │ │ ├ sirius::Density::generate                                       |      567.76 ms →      562.71 ms   (-0.89%) |      21   →      27    (+28.57%) |       11.92 s  →       15.19 s   (+27.43%) | 
- │ │ │ ├ sirius::Density::generate_valence                             |      429.80 ms →      392.09 ms   (-8.78%) |      21   →      27    (+28.57%) |        9.03 s  →       10.59 s   (+17.29%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        9.48 μs →        7.78 μs  (-17.94%) |      21   →      27    (+28.57%) |      199.12 μs →      210.08 μs   (+5.50%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        8.75 μs →        6.99 μs  (-20.09%) |      21   →      27    (+28.57%) |      183.81 μs →      188.84 μs   (+2.74%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       32.04 ms →       20.39 ms  (-36.36%) |      21   →      27    (+28.57%) |      672.75 ms →      550.49 ms  (-18.17%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       12.32 μs →       10.94 μs  (-11.17%) |      21   →      27    (+28.57%) |      258.67 μs →      295.42 μs  (+14.21%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        4.98 ms →        3.43 ms  (-31.05%) |      21   →      27    (+28.57%) |      104.59 ms →       92.73 ms  (-11.35%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       26.00 ms →       15.91 ms  (-38.81%) |      21   →      27    (+28.57%) |      545.95 ms →      429.51 ms  (-21.33%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      527.10 ns →      772.15 ns  (+46.49%) |      21   →      27    (+28.57%) |       11.07 μs →       20.85 μs  (+88.35%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      113.74 ms →      125.01 ms   (+9.90%) |      21   →      27    (+28.57%) |        2.39 s  →        3.38 s   (+41.30%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.22 ms →        1.95 ms  (-12.18%) |      21   →      27    (+28.57%) |       46.53 ms →       52.54 ms  (+12.92%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |      250.87 ms →      214.31 ms  (-14.57%) |      21   →      27    (+28.57%) |        5.27 s  →        5.79 s    (+9.83%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |      250.66 ms →      214.09 ms  (-14.59%) |      21   →      27    (+28.57%) |        5.26 s  →        5.78 s    (+9.81%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      110.24 ms →      143.10 ms  (+29.81%) |      21   →      27    (+28.57%) |        2.31 s  →        3.86 s   (+66.90%) | 
- │ │ │ │ └ sirius::symmetrize_function|fpw                             |      110.23 ms →      143.10 ms  (+29.81%) |      21   →      27    (+28.57%) |        2.31 s  →        3.86 s   (+66.90%) | 
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       28.35 ms →       59.25 ms (+108.97%) |      21   →      27    (+28.57%) |      595.39 ms →        1.60 s  (+168.68%) | 
- │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       68.59 ms →       70.54 ms   (+2.84%) |      21   →      27    (+28.57%) |        1.44 s  →        1.90 s   (+32.23%) | 
- │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.64 ms →       12.68 ms   (+0.29%) |      21   →      27    (+28.57%) |      265.45 ms →      342.27 ms  (+28.94%) | 
- │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.61 ms →       23.67 ms   (+0.27%) |      21   →      27    (+28.57%) |      495.71 ms →      639.04 ms  (+28.91%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        4.11 ms →        3.85 ms   (-6.42%) |      21   →      27    (+28.57%) |       86.41 ms →      103.96 ms  (+20.31%) | 
+ │ │ ├ sirius::Density::mix                                            |       81.53 ms →       59.61 ms  (-26.88%) |      21   →      27    (+28.57%) |        1.71 s  →        1.61 s    (-5.99%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |        1.06 ms →      737.40 μs  (-30.31%) |      21   →      27    (+28.57%) |       22.22 ms →       19.91 ms  (-10.40%) | 
+ │ │ │ ├ sirius::Periodic_function|inner                               |        4.73 ms →        4.87 ms   (+3.03%) |     259   →     215    (-16.99%) |        1.22 s  →        1.05 s   (-14.47%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.55 ms →        4.77 ms   (+4.73%) |     259   →     215    (-16.99%) |        1.18 s  →        1.02 s   (-13.06%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.55 ms →        4.77 ms   (+4.73%) |     259   →     215    (-16.99%) |        1.18 s  →        1.02 s   (-13.06%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        5.50 ms →        5.79 ms   (+5.41%) |      21   →      27    (+28.57%) |      115.42 ms →      156.42 ms  (+35.52%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        4.57 ms →        4.94 ms   (+7.99%) |      21   →      27    (+28.57%) |       96.01 ms →      133.30 ms  (+38.84%) | 
- │ │ ├ sirius::Potential::generate                                     |      365.48 ms →      361.04 ms   (-1.21%) |      21   →      27    (+28.57%) |        7.68 s  →        9.75 s   (+27.01%) | 
- │ │ │ ├ sirius::Potential::poisson                                    |       45.20 ms →       40.41 ms  (-10.59%) |      21   →      27    (+28.57%) |      949.11 ms →        1.09 s   (+14.96%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        3.22 ms →        9.67 ms (+200.28%) |      21   →      27    (+28.57%) |       67.63 ms →      261.10 ms (+286.07%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |        5.19 ms →        5.18 ms   (-0.13%) |      21   →      27    (+28.57%) |      108.92 ms →      139.86 ms  (+28.41%) | 
- │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.82 ms →        4.63 ms   (-4.07%) |      21   →      27    (+28.57%) |      101.26 ms →      124.89 ms  (+23.34%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.82 ms →        4.62 ms   (-4.07%) |      21   →      27    (+28.57%) |      101.24 ms →      124.87 ms  (+23.34%) | 
- │ │ │ ├ sirius::Periodic_function::add                                |      804.22 μs →      768.98 μs   (-4.38%) |      42   →      54    (+28.57%) |       33.78 ms →       41.52 ms  (+22.94%) | 
- │ │ │ ├ sirius::Potential::xc                                         |       44.47 ms →       44.75 ms   (+0.64%) |      21   →      27    (+28.57%) |      933.88 ms →        1.21 s   (+29.39%) | 
- │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       43.30 ms →       43.57 ms   (+0.64%) |      21   →      27    (+28.57%) |      909.21 ms →        1.18 s   (+29.39%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function                          |      683.92 μs →      661.25 μs   (-3.32%) |      42   →      54    (+28.57%) |       28.72 ms →       35.71 ms  (+24.31%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.23 ms →        4.32 ms   (+2.06%) |      21   →      27    (+28.57%) |       88.84 ms →      116.58 ms  (+31.23%) | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.88 ms →        3.84 ms   (-0.83%) |      21   →      27    (+28.57%) |       81.41 ms →      103.80 ms  (+27.51%) | 
- │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.95 ms →      269.09 ms   (+0.05%) |      21   →      27    (+28.57%) |        5.65 s  →        7.27 s   (+28.64%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      132.71 ns →      194.15 ns  (+46.29%) |      21   →      27    (+28.57%) |        2.79 μs →        5.24 μs  (+88.09%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |       94.91 ms →       96.81 ms   (+2.00%) |      21   →      27    (+28.57%) |        1.99 s  →        2.61 s   (+31.14%) | 
- │ │ │ └ sirius::symmetrize_function|fpw                               |       94.91 ms →       96.81 ms   (+2.00%) |      21   →      27    (+28.57%) |        1.99 s  →        2.61 s   (+31.14%) | 
- │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.29 ms →       13.30 ms   (+0.08%) |      21   →      27    (+28.57%) |      279.10 ms →      359.14 ms  (+28.68%) | 
- │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       68.38 ms →       70.26 ms   (+2.75%) |      21   →      27    (+28.57%) |        1.44 s  →        1.90 s   (+32.11%) | 
- │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.62 ms →       12.61 ms   (-0.01%) |      21   →      27    (+28.57%) |      264.92 ms →      340.59 ms  (+28.56%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.68 ms →        3.99 ms   (+8.35%) |      21   →      27    (+28.57%) |       77.27 ms →      107.64 ms  (+39.30%) | 
- │ │ ├ sirius::Periodic_function|inner                                 |        4.72 ms →        4.85 ms   (+2.87%) |     147   →     189    (+28.57%) |      693.35 ms →      916.99 ms  (+32.26%) | 
- │ │ │ └ sirius::Periodic_function|inner_local                         |        4.56 ms →        4.75 ms   (+4.31%) |     147   →     189    (+28.57%) |      670.07 ms →      898.69 ms  (+34.12%) | 
- │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.56 ms →        4.75 ms   (+4.32%) |     147   →     189    (+28.57%) |      669.98 ms →      898.59 ms  (+34.12%) | 
- │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.73 ms →        4.53 ms   (-4.19%) |      63   →      81    (+28.57%) |      298.13 ms →      367.24 ms  (+23.18%) | 
- │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.73 ms →        4.53 ms   (-4.22%) |      63   →      81    (+28.57%) |      297.70 ms →      366.62 ms  (+23.15%) | 
- │ │ ├ sirius::Periodic_function::integrate                            |        4.54 ms →        4.54 ms   (+0.11%) |      21   →      27    (+28.57%) |       95.27 ms →      122.63 ms  (+28.72%) | 
- │ │ └ sirius::Density::get_magnetisation                              |       76.21 μs →       74.33 μs   (-2.46%) |      21   →      27    (+28.57%) |        1.60 ms →        2.01 ms  (+25.40%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |       71.58 μs →       69.69 μs   (-2.65%) |      21   →      27    (+28.57%) |        1.50 ms →        1.88 ms  (+25.17%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.13 ms →        5.48 ms   (+6.80%) |       2   →       2              |       10.26 ms →       10.95 ms   (+6.80%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.84 ms →        4.79 ms   (-1.08%) |       6   →       6              |       29.03 ms →       28.71 ms   (-1.08%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.80 ms →        4.77 ms   (-0.82%) |       6   →       6              |       28.83 ms →       28.59 ms   (-0.82%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.80 ms →        4.76 ms   (-0.81%) |       6   →       6              |       28.82 ms →       28.59 ms   (-0.81%) | 
+ │ └ sirius::Smooth_periodic_function|inner                            |        5.03 ms →        4.53 ms  (-10.08%) |       3   →       3              |       15.10 ms →       13.58 ms  (-10.08%) | 
+ │   └ sirius::Smooth_periodic_function|inner_local                    |        5.03 ms →        4.52 ms  (-10.18%) |       3   →       3              |       15.09 ms →       13.55 ms  (-10.18%) | 
  ├ sirius::Periodic_function|inner                                     |        4.76 ms →        4.79 ms   (+0.54%) |       2   →       2              |        9.53 ms →        9.58 ms   (+0.54%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.76 ms →        4.79 ms   (+0.50%) |       2   →       2              |        9.52 ms →        9.57 ms   (+0.50%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.76 ms →        4.78 ms   (+0.50%) |       2   →       2              |        9.52 ms →        9.57 ms   (+0.50%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.97 ms →        4.56 ms   (-8.34%) |       1   →       1              |        4.97 ms →        4.56 ms   (-8.34%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.97 ms →        4.55 ms   (-8.44%) |       1   →       1              |        4.97 ms →        4.55 ms   (-8.44%) | 
- └ sirius::finalize                                                    |      182.72 ms →      275.18 ms  (+50.60%) |       1   →       1              |      182.72 ms →      275.18 ms  (+50.60%) | 
  ====================================================================================================================================================================================================
```
