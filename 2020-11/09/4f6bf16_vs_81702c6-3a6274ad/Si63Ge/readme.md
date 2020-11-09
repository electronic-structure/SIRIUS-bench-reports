# Benchmark 81702c64a8be67a2936e3e8bb8ca2c9083dee03b vs 4f6bf1684449bb549717c67734c215f779f51100
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |       73.68 s  →       74.68 s    (+1.36%) |       1   →       1              |       73.68 s  →       74.68 s    (+1.36%) | 
  ├ sirius::initialize                                                  |        2.87 s  →        3.10 s    (+8.01%) |       1   →       1              |        2.87 s  →        3.10 s    (+8.01%) | 
+ ├ sirius::Simulation_context::initialize                              |        4.57 s  →        3.88 s   (-15.06%) |       1   →       1              |        4.57 s  →        3.88 s   (-15.06%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       42.17 ms →       29.06 ms  (-31.09%) |       1   →       1              |       42.17 ms →       29.06 ms  (-31.09%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      821.19 ms →      236.61 ms  (-71.19%) |       1   →       1              |      821.19 ms →      236.61 ms  (-71.19%) | 
+ │ │ ├ sirius::Atom_type::init                                         |      400.96 ms →      110.28 ms  (-72.50%) |       2   →       2              |      801.92 ms →      220.55 ms  (-72.50%) | 
+ │ │ └ sirius::Unit_cell::update                                       |       19.17 ms →       15.96 ms  (-16.77%) |       1   →       1              |       19.17 ms →       15.96 ms  (-16.77%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.78 ms →        3.75 ms   (-0.77%) |       1   →       1              |        3.78 ms →        3.75 ms   (-0.77%) | 
+ │ │   └ sirius::Unit_cell::get_symmetry                               |       15.31 ms →       12.12 ms  (-20.85%) |       1   →       1              |       15.31 ms →       12.12 ms  (-20.85%) | 
+ │ │     └ sirius::Unit_cell_symmetry                                  |       15.21 ms →       12.04 ms  (-20.81%) |       1   →       1              |       15.21 ms →       12.04 ms  (-20.81%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.82 ms →        2.76 ms   (-1.94%) |       1   →       1              |        2.82 ms →        2.76 ms   (-1.94%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      477.65 μs →      493.82 μs   (+3.38%) |       1   →       1              |      477.65 μs →      493.82 μs   (+3.38%) | 
+ │ │       └ sirius::Unit_cell_symmetry|mag                            |       27.67 μs →       17.20 μs  (-37.83%) |       1   →       1              |       27.67 μs →       17.20 μs  (-37.83%) | 
  │ └ sirius::Simulation_context::update                                |        3.50 s  →        3.42 s    (-2.45%) |       1   →       1              |        3.50 s  →        3.42 s    (-2.45%) | 
  │   ├ sirius::Unit_cell::update                                       |        7.16 ms →        7.09 ms   (-1.05%) |       1   →       1              |        7.16 ms →        7.09 ms   (-1.05%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.77 ms →        3.77 ms   (+0.01%) |       1   →       1              |        3.77 ms →        3.77 ms   (+0.01%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.35 ms →        3.28 ms   (-2.02%) |       1   →       1              |        3.35 ms →        3.28 ms   (-2.02%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.30 ms →        3.23 ms   (-2.04%) |       1   →       1              |        3.30 ms →        3.23 ms   (-2.04%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.76 ms →        2.70 ms   (-2.20%) |       1   →       1              |        2.76 ms →        2.70 ms   (-2.20%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      506.05 μs →      500.06 μs   (-1.18%) |       1   →       1              |      506.05 μs →      500.06 μs   (-1.18%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       14.29 μs →       14.27 μs   (-0.20%) |       1   →       1              |       14.29 μs →       14.27 μs   (-0.20%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      213.35 ms →      212.54 ms   (-0.38%) |       2   →       2              |      426.70 ms →      425.07 ms   (-0.38%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.16 ms →       15.16 ms   (-0.03%) |       2   →       2              |       30.32 ms →       30.31 ms   (-0.03%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.29 ms →       13.23 ms   (-0.42%) |       1   →       1              |       13.29 ms →       13.23 ms   (-0.42%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.30 ms →       56.24 ms   (-0.11%) |       2   →       2              |      112.59 ms →      112.47 ms   (-0.11%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.26 ms →       45.11 ms   (-0.33%) |       2   →       2              |       90.52 ms →       90.23 ms   (-0.33%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.25 ms →       60.23 ms   (-0.03%) |       4   →       4              |      241.00 ms →      240.94 ms   (-0.03%) | 
  │   ├ sddk::Gvec::init                                                |       92.35 ms →       93.41 ms   (+1.15%) |       2   →       2              |      184.69 ms →      186.83 ms   (+1.15%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       69.07 ms →       70.10 ms   (+1.49%) |       2   →       2              |      138.14 ms →      140.20 ms   (+1.49%) | 
  │   ├ sddk::Gvec_shells                                               |       95.23 ms →       91.86 ms   (-3.54%) |       1   →       1              |       95.23 ms →       91.86 ms   (-3.54%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.99 ms →        2.15 ms   (+7.87%) |       1   →       1              |        1.99 ms →        2.15 ms   (+7.87%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      606.38 ms →      558.22 ms   (-7.94%) |       2   →       2              |        1.21 s  →        1.12 s    (-7.94%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |      144.25 ms →      150.45 ms   (+4.30%) |       1   →       1              |      144.25 ms →      150.45 ms   (+4.30%) | 
+ │ ├ sirius::K_point::K_point                                          |        2.11 μs →        1.36 μs  (-35.38%) |       4   →       4              |        8.44 μs →        5.45 μs  (-35.38%) | 
  │ └ sirius::K_point_set::initialize                                   |      144.16 ms →      150.37 ms   (+4.31%) |       1   →       1              |      144.16 ms →      150.37 ms   (+4.31%) | 
  │   └ sirius::K_point::initialize                                     |       29.16 ms →       28.43 ms   (-2.50%) |       1   →       1              |       29.16 ms →       28.43 ms   (-2.50%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       11.37 ms →       11.06 ms   (-2.72%) |       1   →       1              |       11.37 ms →       11.06 ms   (-2.72%) | 
  │     │ └ sddk::Gvec::init                                            |        5.15 ms →        4.96 ms   (-3.72%) |       1   →       1              |        5.15 ms →        4.96 ms   (-3.72%) | 
+ │     ├ sddk::matrix_storage::matrix_storage                          |       10.78 μs →        9.09 μs  (-15.64%) |       1   →       1              |       10.78 μs →        9.09 μs  (-15.64%) | 
  │     └ sirius::K_point::update                                       |       14.90 ms →       14.53 ms   (-2.47%) |       1   →       1              |       14.90 ms →       14.53 ms   (-2.47%) | 
  │       └ sirius::Beta_projectors                                     |       10.89 ms →       10.62 ms   (-2.45%) |       1   →       1              |       10.89 ms →       10.62 ms   (-2.45%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.86 ms →        8.71 ms   (-1.67%) |       1   →       1              |        8.86 ms →        8.71 ms   (-1.67%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.55 ms →        2.57 ms   (+0.63%) |       2   →       2              |        5.11 ms →        5.14 ms   (+0.63%) | 
  ├ sirius::Potential                                                   |       49.12 ms →       50.24 ms   (+2.28%) |       1   →       1              |       49.12 ms →       50.24 ms   (+2.28%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.91 ms →        2.92 ms   (+0.46%) |       6   →       6              |       17.45 ms →       17.54 ms   (+0.46%) | 
  │ └ sirius::Potential::update                                         |       31.07 ms →       32.17 ms   (+3.54%) |       1   →       1              |       31.07 ms →       32.17 ms   (+3.54%) | 
  │   └ sirius::Potential::generate_local_potential                     |       30.66 ms →       31.77 ms   (+3.62%) |       1   →       1              |       30.66 ms →       31.77 ms   (+3.62%) | 
- │     ├ sirius::Simulation_context::make_periodic_function            |       24.19 ms →       26.97 ms  (+11.50%) |       1   →       1              |       24.19 ms →       26.97 ms  (+11.50%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        5.95 ms →        4.27 ms  (-28.27%) |       1   →       1              |        5.95 ms →        4.27 ms  (-28.27%) | 
  ├ sirius::Density                                                     |       38.01 ms →       38.58 ms   (+1.50%) |       1   →       1              |       38.01 ms →       38.58 ms   (+1.50%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.82 ms →        2.81 ms   (-0.33%) |       2   →       2              |        5.63 ms →        5.62 ms   (-0.33%) | 
  │ └ sirius::Density::update                                           |       32.24 ms →       32.83 ms   (+1.83%) |       1   →       1              |       32.24 ms →       32.83 ms   (+1.83%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       31.99 ms →       32.62 ms   (+1.94%) |       1   →       1              |       31.99 ms →       32.62 ms   (+1.94%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |       78.16 μs →       77.17 μs   (-1.28%) |       1   →       1              |       78.16 μs →       77.17 μs   (-1.28%) | 
- │     ├ sirius::Simulation_context::make_periodic_function            |       24.13 ms →       28.17 ms  (+16.75%) |       1   →       1              |       24.13 ms →       28.17 ms  (+16.75%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        7.49 ms →        4.04 ms  (-46.11%) |       1   →       1              |        7.49 ms →        4.04 ms  (-46.11%) | 
  ├ sirius::Density::initial_density                                    |       55.72 ms →       56.66 ms   (+1.70%) |       1   →       1              |       55.72 ms →       56.66 ms   (+1.70%) | 
- │ ├ sirius::Simulation_context::make_periodic_function                |       25.11 ms →       28.76 ms  (+14.57%) |       1   →       1              |       25.11 ms →       28.76 ms  (+14.57%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        6.17 ms →        4.29 ms  (-30.56%) |       2   →       2              |       12.35 ms →        8.58 ms  (-30.56%) | 
- │ └ sirius::Periodic_function::integrate                              |        4.84 ms →        5.92 ms  (+22.32%) |       1   →       1              |        4.84 ms →        5.92 ms  (+22.32%) | 
  ├ sirius::Potential::generate                                         |      362.48 ms →      363.74 ms   (+0.35%) |       1   →       1              |      362.48 ms →      363.74 ms   (+0.35%) | 
  │ ├ sirius::Potential::poisson                                        |       35.27 ms →       36.92 ms   (+4.66%) |       1   →       1              |       35.27 ms →       36.92 ms   (+4.66%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        7.18 ms →        2.91 ms  (-59.43%) |       1   →       1              |        7.18 ms →        2.91 ms  (-59.43%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        5.01 ms →        5.32 ms   (+6.19%) |       1   →       1              |        5.01 ms →        5.32 ms   (+6.19%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.64 ms →        4.64 ms   (+0.04%) |       1   →       1              |        4.64 ms →        4.64 ms   (+0.04%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.63 ms →        4.63 ms   (+0.06%) |       1   →       1              |        4.63 ms →        4.63 ms   (+0.06%) | 
- │ ├ sirius::Periodic_function::add                                    |      741.61 μs →      819.21 μs  (+10.46%) |       2   →       2              |        1.48 ms →        1.64 ms  (+10.46%) | 
  │ ├ sirius::Potential::xc                                             |       51.41 ms →       50.83 ms   (-1.13%) |       1   →       1              |       51.41 ms →       50.83 ms   (-1.13%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       50.20 ms →       49.67 ms   (-1.07%) |       1   →       1              |       50.20 ms →       49.67 ms   (-1.07%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.53 ms →        2.53 ms   (+0.16%) |       2   →       2              |        5.06 ms →        5.06 ms   (+0.16%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.69 ms →        4.29 ms   (-8.46%) |       1   →       1              |        4.69 ms →        4.29 ms   (-8.46%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.69 ms →        3.96 ms   (+7.40%) |       1   →       1              |        3.69 ms →        3.96 ms   (+7.40%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      269.20 ms →      268.97 ms   (-0.08%) |       1   →       1              |      269.20 ms →      268.97 ms   (-0.08%) | 
+ │ └ sirius::Potential::generate_PAW_effective_potential               |      198.00 ns →      145.00 ns  (-26.77%) |       1   →       1              |      198.00 ns →      145.00 ns  (-26.77%) | 
  ├ sirius::Hamiltonian0                                                |        6.62 ms →        6.92 ms   (+4.48%) |       1   →       1              |        6.62 ms →        6.92 ms   (+4.48%) | 
  │ ├ sirius::Local_operator                                            |        6.06 ms →        6.41 ms   (+5.75%) |       1   →       1              |        6.06 ms →        6.41 ms   (+5.75%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.74 ms →        2.75 ms   (+0.28%) |       1   →       1              |        2.74 ms →        2.75 ms   (+0.28%) | 
- │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.57 ms →        2.87 ms  (+11.84%) |       1   →       1              |        2.57 ms →        2.87 ms  (+11.84%) | 
+ │ ├ sirius::Non_local_operator                                        |      109.16 μs →       75.86 μs  (-30.51%) |       2   →       2              |      218.33 μs →      151.71 μs  (-30.51%) | 
- │ ├ sirius::D_operator::initialize                                    |      131.84 μs →      167.02 μs  (+26.68%) |       1   →       1              |      131.84 μs →      167.02 μs  (+26.68%) | 
+ │ └ sirius::Q_operator::initialize                                    |      124.68 μs →      107.44 μs  (-13.83%) |       1   →       1              |      124.68 μs →      107.44 μs  (-13.83%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.29 s  →        1.28 s    (-1.46%) |       1   →       1              |        1.29 s  →        1.28 s    (-1.46%) | 
  │ ├ sirius::Hamiltonian_k                                             |       49.90 ms →       51.15 ms   (+2.49%) |       1   →       1              |       49.90 ms →       51.15 ms   (+2.49%) | 
- │ │ ├ sirius::Local_operator::prepare_k                               |      276.02 μs →      354.53 μs  (+28.44%) |       1   →       1              |      276.02 μs →      354.53 μs  (+28.44%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       49.62 ms →       50.79 ms   (+2.35%) |       1   →       1              |       49.62 ms →       50.79 ms   (+2.35%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.24 s  →        1.22 s    (-1.62%) |       1   →       1              |        1.24 s  →        1.22 s    (-1.62%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       81.13 ms →       78.31 ms   (-3.47%) |       4   →       4              |      324.53 ms →      313.25 ms   (-3.47%) | 
+ │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       48.86 ms →       37.70 ms  (-22.84%) |       1   →       1              |       48.86 ms →       37.70 ms  (-22.84%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        7.52 ms →        6.84 ms   (-9.05%) |       1   →       1              |        7.52 ms →        6.84 ms   (-9.05%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      312.98 ms →      335.09 ms   (+7.06%) |       1   →       1              |      312.98 ms →      335.09 ms   (+7.06%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      245.32 ms →      247.32 ms   (+0.82%) |       1   →       1              |      245.32 ms →      247.32 ms   (+0.82%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.62 μs →        3.77 μs   (+4.03%) |       1   →       1              |        3.62 μs →        3.77 μs   (+4.03%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.72 μs →        2.75 μs   (+1.07%) |       1   →       1              |        2.72 μs →        2.75 μs   (+1.07%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      440.00 ns →      470.00 ns   (+6.82%) |       1   →       1              |      440.00 ns →      470.00 ns   (+6.82%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      638.00 ns →      651.00 ns   (+2.04%) |       1   →       1              |      638.00 ns →      651.00 ns   (+2.04%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.21 ms →        3.04 ms   (-5.26%) |       1   →       1              |        3.21 ms →        3.04 ms   (-5.26%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.24 ms →       21.32 ms   (+0.39%) |       1   →       1              |       21.24 ms →       21.32 ms   (+0.39%) | 
- │ │ │ └ sirius::Non_local_operator::apply                             |       21.58 ms →       31.68 ms  (+46.79%) |       2   →       2              |       43.16 ms →       63.36 ms  (+46.79%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       16.35 ms →       14.84 ms   (-9.24%) |       2   →       2              |       32.70 ms →       29.68 ms   (-9.24%) | 
  │ │ │ └ sddk::wf_inner                                                |       16.14 ms →       14.63 ms   (-9.36%) |       2   →       2              |       32.29 ms →       29.26 ms   (-9.36%) | 
+ │ │ │   ├ sddk::wf_inner|scale                                        |       36.50 ns →       21.50 ns  (-41.10%) |       2   →       2              |       73.00 ns →       43.00 ns  (-41.10%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       16.02 ms →       14.50 ms   (-9.46%) |       2   →       2              |       32.03 ms →       29.00 ms   (-9.46%) | 
+ │ │ │   └ sddk::wf_inner|scale_back                                   |       31.00 ns →       21.50 ns  (-30.65%) |       2   →       2              |       62.00 ns →       43.00 ns  (-30.65%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      250.19 ms →      232.13 ms   (-7.22%) |       1   →       1              |      250.19 ms →      232.13 ms   (-7.22%) | 
- │ │ └ sddk::wf_trans                                                  |        2.61 ms →        4.80 ms  (+83.68%) |       1   →       1              |        2.61 ms →        4.80 ms  (+83.68%) | 
- │ │   └ sddk::wf_trans|pw                                             |        2.61 ms →        4.79 ms  (+83.84%) |       1   →       1              |        2.61 ms →        4.79 ms  (+83.84%) | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      326.00 ns →      311.00 ns   (-4.60%) |       1   →       1              |      326.00 ns →      311.00 ns   (-4.60%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |       63.18 s  →       64.50 s    (+2.09%) |       1   →       1              |       63.18 s  →       64.50 s    (+2.09%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.43 ms →        2.47 ms   (+1.61%) |      19   →      19              |       46.17 ms →       46.91 ms   (+1.61%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        2.98 s  →        2.92 s    (-2.11%) |      21   →      22     (+4.76%) |       62.64 s  →       64.23 s    (+2.55%) | 
+ │ │ ├ sirius::Hamiltonian0                                            |        5.73 ms →        4.94 ms  (-13.77%) |      21   →      22     (+4.76%) |      120.30 ms →      108.68 ms   (-9.66%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        4.88 ms →        4.31 ms  (-11.75%) |      21   →      22     (+4.76%) |      102.50 ms →       94.76 ms   (-7.55%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      549.63 μs →      538.34 μs   (-2.05%) |      21   →      22     (+4.76%) |       11.54 ms →       11.84 ms   (+2.61%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.22 ms →        2.78 ms  (-13.73%) |      21   →      22     (+4.76%) |       67.64 ms →       61.13 ms   (-9.63%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |      283.35 μs →      167.42 μs  (-40.91%) |      42   →      44     (+4.76%) |       11.90 ms →        7.37 ms  (-38.10%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |      112.49 μs →      119.62 μs   (+6.34%) |      21   →      22     (+4.76%) |        2.36 ms →        2.63 ms  (+11.41%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       90.98 μs →       95.71 μs   (+5.20%) |      21   →      22     (+4.76%) |        1.91 ms →        2.11 ms  (+10.21%) | 
  │ │ ├ sirius::Band::solve                                             |        1.76 s  →        1.70 s    (-3.33%) |      21   →      22     (+4.76%) |       36.99 s  →       37.46 s    (+1.28%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      201.55 μs →      225.75 μs  (+12.01%) |      21   →      22     (+4.76%) |        4.23 ms →        4.97 ms  (+17.34%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      193.50 μs →      216.16 μs  (+11.71%) |      21   →      22     (+4.76%) |        4.06 ms →        4.76 ms  (+17.03%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        6.06 μs →        6.78 μs  (+11.90%) |      21   →      22     (+4.76%) |      127.19 μs →      149.11 μs  (+17.23%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.64 s  →        1.55 s    (-5.16%) |      21   →      22     (+4.76%) |       34.38 s  →       34.16 s    (-0.64%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       72.48 ms →       71.20 ms   (-1.77%) |      21   →      22     (+4.76%) |        1.52 s  →        1.57 s    (+2.91%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.16 ms →        6.12 ms  (-14.59%) |     126   →     154    (+22.22%) |      902.50 ms →      942.13 ms   (+4.39%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       18.21 ms →       12.28 ms  (-32.54%) |      21   →      22     (+4.76%) |      382.34 ms →      270.20 ms  (-29.33%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      474.20 μs →      451.25 μs   (-4.84%) |      21   →      22     (+4.76%) |        9.96 ms →        9.93 ms   (-0.31%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        8.32 ms →        5.44 ms  (-34.56%) |      42   →      44     (+4.76%) |      349.30 ms →      239.48 ms  (-31.44%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.54 s  →        1.45 s    (-5.88%) |      21   →      22     (+4.76%) |       32.31 s  →       31.86 s    (-1.40%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       56.09 ms →       87.33 ms  (+55.69%) |     361   →     180    (-50.14%) |       20.25 s  →       15.72 s   (-22.37%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       31.00 ms →       63.16 ms (+103.77%) |     361   →     180    (-50.14%) |       11.19 s  →       11.37 s    (+1.60%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.07 μs →        2.33 μs  (+12.28%) |     361   →     180    (-50.14%) |      747.76 μs →      418.62 μs  (-44.02%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.70 μs →        1.93 μs  (+13.77%) |     361   →     180    (-50.14%) |      613.19 μs →      347.85 μs  (-43.27%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      444.33 ns →      434.11 ns   (-2.30%) |     361   →     180    (-50.14%) |      160.40 μs →       78.14 μs  (-51.29%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      612.72 ns →      732.48 ns  (+19.55%) |     361   →     180    (-50.14%) |      221.19 μs →      131.85 μs  (-40.39%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.98 ms →        2.81 ms   (-5.56%) |     361   →     180    (-50.14%) |        1.07 s  →      505.96 ms  (-52.91%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.34 ms →        5.39 ms  (+61.23%) |     361   →     180    (-50.14%) |        1.21 s  →      970.13 ms  (-19.61%) | 
+ │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        9.38 ms →        7.97 ms  (-15.01%) |     722   →     360    (-50.14%) |        6.77 s  →        2.87 s   (-57.62%) | 
+ │ │ │ │   ├ sddk::orthogonalize                                       |        6.58 ms →        7.06 ms   (+7.29%) |     361   →     180    (-50.14%) |        2.37 s  →        1.27 s   (-46.50%) | 
+ │ │ │ │   │ ├ sddk::wf_inner                                          |        1.18 ms →        1.19 ms   (+0.75%) |     701   →     338    (-51.78%) |      829.16 ms →      402.78 ms  (-51.42%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       61.24 ns →       51.58 ns  (-15.78%) |     701   →     338    (-51.78%) |       42.93 μs →       17.43 μs  (-59.39%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        1.02 ms →        1.01 ms   (-0.53%) |     701   →     338    (-51.78%) |      715.09 ms →      342.97 ms  (-52.04%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       49.71 ns →       70.29 ns  (+41.41%) |     701   →     338    (-51.78%) |       34.85 μs →       23.76 μs  (-31.82%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      137.38 μs →      272.97 μs  (+98.70%) |     361   →     180    (-50.14%) |       49.59 ms →       49.14 ms   (-0.93%) | 
+ │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        2.05 ms →        1.87 ms   (-8.75%) |     361   →     180    (-50.14%) |      740.99 ms →      337.14 ms  (-54.50%) | 
- │ │ │ │   │ └ sddk::wf_trans                                          |        2.21 ms →        3.04 ms  (+37.23%) |     340   →     158    (-53.53%) |      752.70 ms →      479.99 ms  (-36.23%) | 
- │ │ │ │   │   └ sddk::wf_trans|pw                                     |      737.14 μs →        1.01 ms  (+37.26%) |    1.02 K →     474    (-53.53%) |      751.89 ms →      479.59 ms  (-36.22%) | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.50 ms →        1.62 ms   (+8.44%) |     361   →     180    (-50.14%) |      539.87 ms →      291.92 ms  (-45.93%) | 
+ │ │ │ │   │ └ sddk::wf_inner                                          |        1.45 ms →        1.55 ms   (+7.20%) |     361   →     180    (-50.14%) |      522.87 ms →      279.48 ms  (-46.55%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       54.86 ns →       41.22 ns  (-24.86%) |     361   →     180    (-50.14%) |       19.80 μs →        7.42 μs  (-62.53%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        1.28 ms →        1.37 ms   (+7.20%) |     361   →     180    (-50.14%) |      462.93 ms →      247.45 ms  (-46.55%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       43.86 ns →       49.83 ns  (+13.61%) |     361   →     180    (-50.14%) |       15.83 μs →        8.97 μs  (-43.35%) | 
- │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       21.13 ms →       75.20 ms (+255.84%) |     361   →     180    (-50.14%) |        7.63 s  →       13.54 s   (+77.43%) | 
- │ │ │ │   ├ sirius::residuals                                         |        3.03 ms →        3.43 ms  (+13.41%) |     346   →     179    (-48.27%) |        1.05 s  →      614.12 ms  (-41.33%) | 
- │ │ │ │   │ ├ sddk::wf_trans                                          |        1.37 ms →        2.01 ms  (+46.15%) |     342   →     179    (-47.66%) |      469.91 ms →      359.44 ms  (-23.51%) | 
- │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      685.61 μs →        1.00 ms  (+46.21%) |     684   →     358    (-47.66%) |      468.96 ms →      358.88 ms  (-23.47%) | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.55 ms →        1.31 ms  (-15.57%) |     342   →     179    (-47.66%) |      528.59 ms →      233.60 ms  (-55.81%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        5.14 ms →        6.01 ms  (+17.00%) |      90   →      70    (-22.22%) |      462.52 ms →      420.89 ms   (-9.00%) | 
- │ │ │ │     └ sddk::wf_trans                                          |        2.86 ms →        3.51 ms  (+22.83%) |     159   →     118    (-25.79%) |      454.25 ms →      414.08 ms   (-8.84%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |        1.99 ms →        2.49 ms  (+25.22%) |     228   →     166    (-27.19%) |      453.93 ms →      413.83 ms   (-8.83%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      518.71 ns →      442.41 ns  (-14.71%) |      21   →      22     (+4.76%) |       10.89 μs →        9.73 μs  (-10.65%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       19.74 μs →       31.09 μs  (+57.54%) |      21   →      22     (+4.76%) |      414.44 μs →      684.01 μs  (+65.05%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.59 ms →        1.54 ms   (-3.45%) |      21   →      22     (+4.76%) |       33.42 ms →       33.81 ms   (+1.15%) | 
  │ │ ├ sirius::Density::generate                                       |      569.62 ms →      562.33 ms   (-1.28%) |      21   →      22     (+4.76%) |       11.96 s  →       12.37 s    (+3.42%) | 
- │ │ │ ├ sirius::Density::generate_valence                             |      395.03 ms →      425.32 ms   (+7.67%) |      21   →      22     (+4.76%) |        8.30 s  →        9.36 s   (+12.79%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       10.87 μs →       14.17 μs  (+30.36%) |      21   →      22     (+4.76%) |      228.28 μs →      311.74 μs  (+36.56%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        9.90 μs →       13.20 μs  (+33.30%) |      21   →      22     (+4.76%) |      208.00 μs →      290.46 μs  (+39.64%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       44.99 ms →       26.90 ms  (-40.20%) |      21   →      22     (+4.76%) |      944.79 ms →      591.88 ms  (-37.35%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       10.86 μs →       11.34 μs   (+4.46%) |      21   →      22     (+4.76%) |      227.98 μs →      249.48 μs   (+9.43%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.60 ms →        4.78 ms  (-37.09%) |      21   →      22     (+4.76%) |      159.52 ms →      105.13 ms  (-34.10%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       36.31 ms →       21.09 ms  (-41.92%) |      21   →      22     (+4.76%) |      762.61 ms →      464.03 ms  (-39.15%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |        1.08 μs →        1.18 μs   (+9.79%) |      21   →      22     (+4.76%) |       22.65 μs →       26.05 μs  (+15.01%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      100.92 ms →      118.82 ms  (+17.74%) |      21   →      22     (+4.76%) |        2.12 s  →        2.61 s   (+23.34%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.92 ms →        2.30 ms  (+19.88%) |      21   →      22     (+4.76%) |       40.32 ms →       50.64 ms  (+25.59%) | 
- │ │ │ │ └ sirius::Density::augment                                    |      204.92 ms →      251.34 ms  (+22.65%) |      21   →      22     (+4.76%) |        4.30 s  →        5.53 s   (+28.49%) | 
- │ │ │ │   └ sirius::Density::generate_rho_aug                         |      204.69 ms →      251.12 ms  (+22.68%) |      21   →      22     (+4.76%) |        4.30 s  →        5.52 s   (+28.52%) | 
+ │ │ │ ├ sirius::Field4D::symmetrize                                   |      145.98 ms →      109.38 ms  (-25.07%) |      21   →      22     (+4.76%) |        3.07 s  →        2.41 s   (-21.51%) | 
+ │ │ │ │ └ sirius::symmetrize_function|fpw                             |      145.98 ms →      109.38 ms  (-25.07%) |      21   →      22     (+4.76%) |        3.07 s  →        2.41 s   (-21.51%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       62.90 ms →       26.37 ms  (-58.08%) |      21   →      22     (+4.76%) |        1.32 s  →      580.06 ms  (-56.08%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       69.84 ms →       69.74 ms   (-0.14%) |      21   →      22     (+4.76%) |        1.47 s  →        1.53 s    (+4.62%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.60 ms →       12.62 ms   (+0.21%) |      21   →      22     (+4.76%) |      264.53 ms →      277.72 ms   (+4.99%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.57 ms →       23.77 ms   (+0.84%) |      21   →      22     (+4.76%) |      495.05 ms →      522.96 ms   (+5.64%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        5.03 ms →        3.85 ms  (-23.45%) |      21   →      22     (+4.76%) |      105.60 ms →       84.69 ms  (-19.80%) | 
  │ │ ├ sirius::Density::mix                                            |      135.41 ms →      137.75 ms   (+1.73%) |      21   →      22     (+4.76%) |        2.84 s  →        3.03 s    (+6.57%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      690.12 μs →      756.35 μs   (+9.60%) |      21   →      22     (+4.76%) |       14.49 ms →       16.64 ms  (+14.82%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |        4.88 ms →        4.94 ms   (+1.25%) |     259   →     274     (+5.79%) |        1.26 s  →        1.35 s    (+7.11%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.81 ms →        4.82 ms   (+0.16%) |     259   →     274     (+5.79%) |        1.25 s  →        1.32 s    (+5.96%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.81 ms →        4.82 ms   (+0.15%) |     259   →     274     (+5.79%) |        1.25 s  →        1.32 s    (+5.95%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        5.73 ms →        6.23 ms   (+8.60%) |      21   →      22     (+4.76%) |      120.41 ms →      136.99 ms  (+13.78%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.09 ms →        5.44 ms   (+6.91%) |      21   →      22     (+4.76%) |      106.83 ms →      119.65 ms  (+12.00%) | 
  │ │ ├ sirius::Potential::generate                                     |      355.15 ms →      357.17 ms   (+0.57%) |      21   →      22     (+4.76%) |        7.46 s  →        7.86 s    (+5.36%) | 
- │ │ │ ├ sirius::Potential::poisson                                    |       35.02 ms →       36.97 ms   (+5.56%) |      21   →      22     (+4.76%) |      735.38 ms →      813.25 ms  (+10.59%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        7.19 ms →        2.95 ms  (-59.02%) |      21   →      22     (+4.76%) |      151.03 ms →       64.83 ms  (-57.07%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |        4.79 ms →        5.26 ms   (+9.81%) |      21   →      22     (+4.76%) |      100.55 ms →      115.66 ms  (+15.04%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.63 ms →        4.63 ms   (+0.02%) |      21   →      22     (+4.76%) |       97.18 ms →      101.84 ms   (+4.79%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.63 ms →        4.63 ms   (+0.03%) |      21   →      22     (+4.76%) |       97.15 ms →      101.81 ms   (+4.80%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      773.79 μs →      810.99 μs   (+4.81%) |      42   →      44     (+4.76%) |       32.50 ms →       35.68 ms   (+9.80%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       45.10 ms →       44.55 ms   (-1.22%) |      21   →      22     (+4.76%) |      947.11 ms →      980.14 ms   (+3.49%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       43.92 ms →       43.38 ms   (-1.25%) |      21   →      22     (+4.76%) |      922.40 ms →      954.28 ms   (+3.46%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |      680.57 μs →      669.99 μs   (-1.55%) |      42   →      44     (+4.76%) |       28.58 ms →       29.48 ms   (+3.13%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.56 ms →        4.27 ms   (-6.50%) |      21   →      22     (+4.76%) |       95.86 ms →       93.90 ms   (-2.05%) | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.40 ms →        3.97 ms  (+16.95%) |      21   →      22     (+4.76%) |       71.31 ms →       87.37 ms  (+22.51%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.67 ms →      268.64 ms   (-0.01%) |      21   →      22     (+4.76%) |        5.64 s  →        5.91 s    (+4.75%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      211.38 ns →      130.50 ns  (-38.26%) |      21   →      22     (+4.76%) |        4.44 μs →        2.87 μs  (-35.32%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |       96.90 ms →       96.64 ms   (-0.27%) |      21   →      22     (+4.76%) |        2.03 s  →        2.13 s    (+4.48%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |       96.90 ms →       96.64 ms   (-0.27%) |      21   →      22     (+4.76%) |        2.03 s  →        2.13 s    (+4.48%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.47 ms →       13.64 ms   (+1.25%) |      21   →      22     (+4.76%) |      282.94 ms →      300.13 ms   (+6.07%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       69.79 ms →       69.42 ms   (-0.53%) |      21   →      22     (+4.76%) |        1.47 s  →        1.53 s    (+4.21%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       13.01 ms →       12.96 ms   (-0.41%) |      21   →      22     (+4.76%) |      273.28 ms →      285.13 ms   (+4.34%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        4.19 ms →        3.41 ms  (-18.80%) |      21   →      22     (+4.76%) |       88.07 ms →       74.92 ms  (-14.93%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.91 ms →        4.93 ms   (+0.54%) |     147   →     154     (+4.76%) |      721.18 ms →      759.56 ms   (+5.32%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.76 ms →        4.79 ms   (+0.48%) |     147   →     154     (+4.76%) |      700.28 ms →      737.16 ms   (+5.27%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.76 ms →        4.79 ms   (+0.48%) |     147   →     154     (+4.76%) |      700.18 ms →      737.07 ms   (+5.27%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.55 ms →        4.55 ms   (-0.07%) |      63   →      66     (+4.76%) |      286.71 ms →      300.15 ms   (+4.69%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.54 ms →        4.54 ms   (+0.08%) |      63   →      66     (+4.76%) |      285.99 ms →      299.85 ms   (+4.85%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.55 ms →        4.74 ms   (+4.25%) |      21   →      22     (+4.76%) |       95.47 ms →      104.27 ms   (+9.21%) | 
  │ │ └ sirius::Density::get_magnetisation                              |       75.51 μs →       74.86 μs   (-0.86%) |      21   →      22     (+4.76%) |        1.59 ms →        1.65 ms   (+3.86%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |       70.54 μs →       69.65 μs   (-1.26%) |      21   →      22     (+4.76%) |        1.48 ms →        1.53 ms   (+3.44%) | 
- │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.11 ms →        5.67 ms  (+10.88%) |       2   →       2              |       10.22 ms →       11.33 ms  (+10.88%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.98 ms →        4.75 ms   (-4.53%) |       6   →       6              |       29.86 ms →       28.50 ms   (-4.53%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.97 ms →        4.75 ms   (-4.56%) |       6   →       6              |       29.83 ms →       28.47 ms   (-4.56%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.97 ms →        4.74 ms   (-4.58%) |       6   →       6              |       29.83 ms →       28.46 ms   (-4.58%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.82 ms →        4.57 ms   (-5.28%) |       3   →       3              |       14.46 ms →       13.70 ms   (-5.28%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.81 ms →        4.56 ms   (-5.22%) |       3   →       3              |       14.44 ms →       13.68 ms   (-5.22%) | 
- ├ sirius::Periodic_function|inner                                     |        4.73 ms →        9.86 ms (+108.28%) |       2   →       2              |        9.47 ms →       19.72 ms (+108.28%) | 
- │ └ sirius::Periodic_function|inner_local                             |        4.73 ms →        9.86 ms (+108.47%) |       2   →       2              |        9.46 ms →       19.72 ms (+108.47%) | 
- │   └ sirius::Smooth_periodic_function|inner_local                    |        4.73 ms →        9.86 ms (+108.49%) |       2   →       2              |        9.46 ms →       19.72 ms (+108.49%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.86 ms →        4.51 ms   (-7.19%) |       1   →       1              |        4.86 ms →        4.51 ms   (-7.19%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.86 ms →        4.50 ms   (-7.36%) |       1   →       1              |        4.86 ms →        4.50 ms   (-7.36%) | 
  └ sirius::finalize                                                    |      166.67 ms →      163.04 ms   (-2.18%) |       1   →       1              |      166.67 ms →      163.04 ms   (-2.18%) | 
  ====================================================================================================================================================================================================
```
