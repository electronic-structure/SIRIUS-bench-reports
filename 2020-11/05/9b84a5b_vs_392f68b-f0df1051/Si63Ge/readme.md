# Benchmark 392f68b5626168134a99cd6d4a3cc40b87322cb7 vs 9b84a5bea034e7aac2565a82a15a8dc1c2516588
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |       72.44 s  →       74.37 s    (+2.66%) |       1   →       1              |       72.44 s  →       74.37 s    (+2.66%) | 
  ├ sirius::initialize                                                  |        2.80 s  →        2.77 s    (-0.97%) |       1   →       1              |        2.80 s  →        2.77 s    (-0.97%) | 
  ├ sirius::Simulation_context::initialize                              |        3.91 s  →        3.67 s    (-6.05%) |       1   →       1              |        3.91 s  →        3.67 s    (-6.05%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       71.63 ms →       36.76 ms  (-48.68%) |       1   →       1              |       71.63 ms →       36.76 ms  (-48.68%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      127.08 ms →      160.55 ms  (+26.33%) |       1   →       1              |      127.08 ms →      160.55 ms  (+26.33%) | 
- │ │ ├ sirius::Atom_type::init                                         |       54.21 ms →       70.18 ms  (+29.47%) |       2   →       2              |      108.42 ms →      140.37 ms  (+29.47%) | 
  │ │ └ sirius::Unit_cell::update                                       |       18.57 ms →       20.09 ms   (+8.22%) |       1   →       1              |       18.57 ms →       20.09 ms   (+8.22%) | 
- │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.61 ms →        5.00 ms  (+38.76%) |       1   →       1              |        3.61 ms →        5.00 ms  (+38.76%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       14.91 ms →       15.00 ms   (+0.64%) |       1   →       1              |       14.91 ms →       15.00 ms   (+0.64%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       14.84 ms →       14.91 ms   (+0.50%) |       1   →       1              |       14.84 ms →       14.91 ms   (+0.50%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.75 ms →        2.76 ms   (+0.44%) |       1   →       1              |        2.75 ms →        2.76 ms   (+0.44%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      572.45 μs →      565.01 μs   (-1.30%) |       1   →       1              |      572.45 μs →      565.01 μs   (-1.30%) | 
- │ │       └ sirius::Unit_cell_symmetry|mag                            |       16.18 μs →       28.73 μs  (+77.62%) |       1   →       1              |       16.18 μs →       28.73 μs  (+77.62%) | 
  │ └ sirius::Simulation_context::update                                |        3.51 s  →        3.39 s    (-3.29%) |       1   →       1              |        3.51 s  →        3.39 s    (-3.29%) | 
  │   ├ sirius::Unit_cell::update                                       |        6.98 ms →        6.96 ms   (-0.16%) |       1   →       1              |        6.98 ms →        6.96 ms   (-0.16%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.64 ms →        3.64 ms   (-0.14%) |       1   →       1              |        3.64 ms →        3.64 ms   (-0.14%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.30 ms →        3.29 ms   (-0.26%) |       1   →       1              |        3.30 ms →        3.29 ms   (-0.26%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.25 ms →        3.23 ms   (-0.73%) |       1   →       1              |        3.25 ms →        3.23 ms   (-0.73%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.69 ms →        2.69 ms   (-0.15%) |       1   →       1              |        2.69 ms →        2.69 ms   (-0.15%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      522.69 μs →      492.54 μs   (-5.77%) |       1   →       1              |      522.69 μs →      492.54 μs   (-5.77%) | 
- │   │     └ sirius::Unit_cell_symmetry|mag                            |       13.99 μs →       20.04 μs  (+43.19%) |       1   →       1              |       13.99 μs →       20.04 μs  (+43.19%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      212.67 ms →      214.95 ms   (+1.07%) |       2   →       2              |      425.35 ms →      429.90 ms   (+1.07%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.60 ms →       15.17 ms   (-2.80%) |       2   →       2              |       31.21 ms →       30.33 ms   (-2.80%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.33 ms →       13.29 ms   (-0.33%) |       1   →       1              |       13.33 ms →       13.29 ms   (-0.33%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.56 ms →       61.20 ms   (+8.21%) |       2   →       2              |      113.12 ms →      122.40 ms   (+8.21%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.05 ms →       45.08 ms   (+0.07%) |       2   →       2              |       90.10 ms →       90.16 ms   (+0.07%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.22 ms →       60.09 ms   (-0.22%) |       4   →       4              |      240.89 ms →      240.36 ms   (-0.22%) | 
  │   ├ sddk::Gvec::init                                                |       93.65 ms →       93.36 ms   (-0.31%) |       2   →       2              |      187.31 ms →      186.72 ms   (-0.31%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       69.61 ms →       69.25 ms   (-0.52%) |       2   →       2              |      139.23 ms →      138.50 ms   (-0.52%) | 
  │   ├ sddk::Gvec_shells                                               |       95.46 ms →       97.16 ms   (+1.78%) |       1   →       1              |       95.46 ms →       97.16 ms   (+1.78%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.98 ms →        1.98 ms   (-0.20%) |       1   →       1              |        1.98 ms →        1.98 ms   (-0.20%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      547.97 ms →      516.06 ms   (-5.82%) |       2   →       2              |        1.10 s  →        1.03 s    (-5.82%) | 
- ├ sirius::K_point_set::create_k_mesh                                  |      149.20 ms →      165.41 ms  (+10.86%) |       1   →       1              |      149.20 ms →      165.41 ms  (+10.86%) | 
- │ ├ sirius::K_point::K_point                                          |      808.75 ns →        1.41 μs  (+74.13%) |       4   →       4              |        3.23 μs →        5.63 μs  (+74.13%) | 
- │ └ sirius::K_point_set::initialize                                   |      149.12 ms →      165.32 ms  (+10.86%) |       1   →       1              |      149.12 ms →      165.32 ms  (+10.86%) | 
  │   └ sirius::K_point::initialize                                     |       28.90 ms →       28.13 ms   (-2.65%) |       1   →       1              |       28.90 ms →       28.13 ms   (-2.65%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       11.59 ms →       10.82 ms   (-6.63%) |       1   →       1              |       11.59 ms →       10.82 ms   (-6.63%) | 
  │     │ └ sddk::Gvec::init                                            |        5.24 ms →        4.87 ms   (-7.15%) |       1   →       1              |        5.24 ms →        4.87 ms   (-7.15%) | 
+ │     ├ sddk::matrix_storage::matrix_storage                          |       11.12 μs →        8.88 μs  (-20.09%) |       1   →       1              |       11.12 μs →        8.88 μs  (-20.09%) | 
  │     └ sirius::K_point::update                                       |       14.50 ms →       14.47 ms   (-0.18%) |       1   →       1              |       14.50 ms →       14.47 ms   (-0.18%) | 
  │       └ sirius::Beta_projectors                                     |       10.16 ms →       10.46 ms   (+2.88%) |       1   →       1              |       10.16 ms →       10.46 ms   (+2.88%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.24 ms →        8.25 ms   (+0.06%) |       1   →       1              |        8.24 ms →        8.25 ms   (+0.06%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.56 ms →        2.56 ms   (+0.02%) |       2   →       2              |        5.11 ms →        5.11 ms   (+0.02%) | 
  ├ sirius::Potential                                                   |       55.20 ms →       52.27 ms   (-5.30%) |       1   →       1              |       55.20 ms →       52.27 ms   (-5.30%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.89 ms →        2.87 ms   (-0.57%) |       6   →       6              |       17.34 ms →       17.25 ms   (-0.57%) | 
  │ └ sirius::Potential::update                                         |       37.32 ms →       34.46 ms   (-7.67%) |       1   →       1              |       37.32 ms →       34.46 ms   (-7.67%) | 
  │   └ sirius::Potential::generate_local_potential                     |       36.92 ms →       34.05 ms   (-7.77%) |       1   →       1              |       36.92 ms →       34.05 ms   (-7.77%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       32.54 ms →       29.10 ms  (-10.55%) |       1   →       1              |       32.54 ms →       29.10 ms  (-10.55%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        3.83 ms →        4.42 ms  (+15.40%) |       1   →       1              |        3.83 ms →        4.42 ms  (+15.40%) | 
  ├ sirius::Density                                                     |       42.50 ms →       39.24 ms   (-7.67%) |       1   →       1              |       42.50 ms →       39.24 ms   (-7.67%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.84 ms →        2.81 ms   (-1.00%) |       2   →       2              |        5.68 ms →        5.62 ms   (-1.00%) | 
  │ └ sirius::Density::update                                           |       36.67 ms →       33.49 ms   (-8.69%) |       1   →       1              |       36.67 ms →       33.49 ms   (-8.69%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       36.40 ms →       33.26 ms   (-8.63%) |       1   →       1              |       36.40 ms →       33.26 ms   (-8.63%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |       78.88 μs →       75.99 μs   (-3.66%) |       1   →       1              |       78.88 μs →       75.99 μs   (-3.66%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       32.72 ms →       26.43 ms  (-19.21%) |       1   →       1              |       32.72 ms →       26.43 ms  (-19.21%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        3.26 ms →        6.44 ms  (+97.75%) |       1   →       1              |        3.26 ms →        6.44 ms  (+97.75%) | 
  ├ sirius::Density::initial_density                                    |       64.50 ms →       58.53 ms   (-9.25%) |       1   →       1              |       64.50 ms →       58.53 ms   (-9.25%) | 
+ │ ├ sirius::Simulation_context::make_periodic_function                |       37.40 ms →       26.70 ms  (-28.61%) |       1   →       1              |       37.40 ms →       26.70 ms  (-28.61%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.10 ms →        6.21 ms  (+51.53%) |       2   →       2              |        8.20 ms →       12.42 ms  (+51.53%) | 
  │ └ sirius::Periodic_function::integrate                              |        5.49 ms →        5.78 ms   (+5.17%) |       1   →       1              |        5.49 ms →        5.78 ms   (+5.17%) | 
  ├ sirius::Potential::generate                                         |      373.34 ms →      366.07 ms   (-1.95%) |       1   →       1              |      373.34 ms →      366.07 ms   (-1.95%) | 
+ │ ├ sirius::Potential::poisson                                        |       45.91 ms →       39.18 ms  (-14.67%) |       1   →       1              |       45.91 ms →       39.18 ms  (-14.67%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.28 ms →        7.08 ms (+115.97%) |       1   →       1              |        3.28 ms →        7.08 ms (+115.97%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        5.74 ms →        6.10 ms   (+6.21%) |       1   →       1              |        5.74 ms →        6.10 ms   (+6.21%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.83 ms →        4.64 ms   (-4.05%) |       1   →       1              |        4.83 ms →        4.64 ms   (-4.05%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.83 ms →        4.63 ms   (-4.14%) |       1   →       1              |        4.83 ms →        4.63 ms   (-4.14%) | 
  │ ├ sirius::Periodic_function::add                                    |      767.60 μs →      778.13 μs   (+1.37%) |       2   →       2              |        1.54 ms →        1.56 ms   (+1.37%) | 
  │ ├ sirius::Potential::xc                                             |       51.84 ms →       51.32 ms   (-1.01%) |       1   →       1              |       51.84 ms →       51.32 ms   (-1.01%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       50.65 ms →       50.13 ms   (-1.03%) |       1   →       1              |       50.65 ms →       50.13 ms   (-1.03%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.55 ms →        2.53 ms   (-0.64%) |       2   →       2              |        5.10 ms →        5.07 ms   (-0.64%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.53 ms →        4.65 ms   (+2.58%) |       1   →       1              |        4.53 ms →        4.65 ms   (+2.58%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.56 ms →        3.61 ms   (+1.34%) |       1   →       1              |        3.56 ms →        3.61 ms   (+1.34%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      269.09 ms →      269.08 ms   (-0.00%) |       1   →       1              |      269.09 ms →      269.08 ms   (-0.00%) | 
- │ └ sirius::Potential::generate_PAW_effective_potential               |      119.00 ns →      230.00 ns  (+93.28%) |       1   →       1              |      119.00 ns →      230.00 ns  (+93.28%) | 
- ├ sirius::Hamiltonian0                                                |        6.26 ms →        8.72 ms  (+39.22%) |       1   →       1              |        6.26 ms →        8.72 ms  (+39.22%) | 
- │ ├ sirius::Local_operator                                            |        5.83 ms →        7.65 ms  (+31.28%) |       1   →       1              |        5.83 ms →        7.65 ms  (+31.28%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.73 ms →        2.73 ms   (+0.02%) |       1   →       1              |        2.73 ms →        2.73 ms   (+0.02%) | 
- │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.35 ms →        3.98 ms  (+69.65%) |       1   →       1              |        2.35 ms →        3.98 ms  (+69.65%) | 
- │ ├ sirius::Non_local_operator                                        |       71.46 μs →      405.66 μs (+467.71%) |       2   →       2              |      142.91 μs →      811.32 μs (+467.71%) | 
+ │ ├ sirius::D_operator::initialize                                    |      124.59 μs →      101.04 μs  (-18.91%) |       1   →       1              |      124.59 μs →      101.04 μs  (-18.91%) | 
+ │ └ sirius::Q_operator::initialize                                    |      100.42 μs →       89.93 μs  (-10.45%) |       1   →       1              |      100.42 μs →       89.93 μs  (-10.45%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.28 s  →        1.28 s    (-0.23%) |       1   →       1              |        1.28 s  →        1.28 s    (-0.23%) | 
- │ ├ sirius::Hamiltonian_k                                             |       31.10 ms →       69.58 ms (+123.73%) |       1   →       1              |       31.10 ms →       69.58 ms (+123.73%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      229.78 μs →      207.80 μs   (-9.57%) |       1   →       1              |      229.78 μs →      207.80 μs   (-9.57%) | 
- │ │ └ sirius::Beta_projectors_base::prepare                           |       30.86 ms →       69.37 ms (+124.74%) |       1   →       1              |       30.86 ms →       69.37 ms (+124.74%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.25 s  →        1.21 s    (-3.31%) |       1   →       1              |        1.25 s  →        1.21 s    (-3.31%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       81.56 ms →       87.59 ms   (+7.39%) |       4   →       4              |      326.25 ms →      350.36 ms   (+7.39%) | 
+ │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       53.65 ms →       46.41 ms  (-13.49%) |       1   →       1              |       53.65 ms →       46.41 ms  (-13.49%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        7.60 ms →        7.72 ms   (+1.60%) |       1   →       1              |        7.60 ms →        7.72 ms   (+1.60%) | 
- │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      312.78 ms →      380.80 ms  (+21.75%) |       1   →       1              |      312.78 ms →      380.80 ms  (+21.75%) | 
- │ │ │ ├ sirius::Local_operator::apply_h                               |      244.89 ms →      307.24 ms  (+25.46%) |       1   →       1              |      244.89 ms →      307.24 ms  (+25.46%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.80 μs →        3.58 μs   (-5.71%) |       1   →       1              |        3.80 μs →        3.58 μs   (-5.71%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.90 μs →        2.70 μs   (-6.94%) |       1   →       1              |        2.90 μs →        2.70 μs   (-6.94%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      403.00 ns →      397.00 ns   (-1.49%) |       1   →       1              |      403.00 ns →      397.00 ns   (-1.49%) | 
- │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      625.00 ns →        1.25 μs  (+99.20%) |       1   →       1              |      625.00 ns →        1.25 μs  (+99.20%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.23 ms →        3.12 ms   (-3.61%) |       1   →       1              |        3.23 ms →        3.12 ms   (-3.61%) | 
- │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.30 ms →       24.57 ms  (+15.37%) |       1   →       1              |       21.30 ms →       24.57 ms  (+15.37%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       21.66 ms →       22.91 ms   (+5.80%) |       2   →       2              |       43.32 ms →       45.83 ms   (+5.80%) | 
+ │ │ ├ sirius::Band::set_subspace_mtrx                                 |       16.64 ms →        7.70 ms  (-53.74%) |       2   →       2              |       33.27 ms →       15.39 ms  (-53.74%) | 
+ │ │ │ └ sddk::wf_inner                                                |       16.42 ms →        7.49 ms  (-54.39%) |       2   →       2              |       32.85 ms →       14.98 ms  (-54.39%) | 
+ │ │ │   ├ sddk::wf_inner|scale                                        |       47.50 ns →       21.00 ns  (-55.79%) |       2   →       2              |       95.00 ns →       42.00 ns  (-55.79%) | 
+ │ │ │   ├ sddk::wf_inner|pw                                           |       16.30 ms →        7.36 ms  (-54.87%) |       2   →       2              |       32.59 ms →       14.71 ms  (-54.87%) | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |       28.50 ns →       26.50 ns   (-7.02%) |       2   →       2              |       57.00 ns →       53.00 ns   (-7.02%) | 
+ │ │ ├ Eigensolver_cuda|zhegvdx                                        |      252.33 ms →      197.86 ms  (-21.59%) |       1   →       1              |      252.33 ms →      197.86 ms  (-21.59%) | 
  │ │ └ sddk::wf_trans                                                  |        2.62 ms →        2.60 ms   (-0.65%) |       1   →       1              |        2.62 ms →        2.60 ms   (-0.65%) | 
  │ │   └ sddk::wf_trans|pw                                             |        2.61 ms →        2.60 ms   (-0.65%) |       1   →       1              |        2.61 ms →        2.60 ms   (-0.65%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      427.00 ns →      328.00 ns  (-23.19%) |       1   →       1              |      427.00 ns →      328.00 ns  (-23.19%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |       62.67 s  →       64.75 s    (+3.33%) |       1   →       1              |       62.67 s  →       64.75 s    (+3.33%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.45 ms →        2.44 ms   (-0.09%) |      19   →      19              |       46.49 ms →       46.45 ms   (-0.09%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        2.97 s  →        2.93 s    (-1.41%) |      21   →      22     (+4.76%) |       62.43 s  →       64.49 s    (+3.29%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        5.02 ms →        5.45 ms   (+8.77%) |      21   →      22     (+4.76%) |      105.32 ms →      120.01 ms  (+13.94%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.40 ms →        4.61 ms   (+4.80%) |      21   →      22     (+4.76%) |       92.38 ms →      101.42 ms   (+9.79%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      570.58 μs →      554.20 μs   (-2.87%) |      21   →      22     (+4.76%) |       11.98 ms →       12.19 ms   (+1.76%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.77 ms →        2.96 ms   (+6.87%) |      21   →      22     (+4.76%) |       58.21 ms →       65.18 ms  (+11.96%) | 
- │ │ │ ├ sirius::Non_local_operator                                    |      165.05 μs →      287.61 μs  (+74.26%) |      42   →      44     (+4.76%) |        6.93 ms →       12.65 ms  (+82.55%) | 
+ │ │ │ ├ sirius::D_operator::initialize                                |      120.00 μs →      106.05 μs  (-11.63%) |      21   →      22     (+4.76%) |        2.52 ms →        2.33 ms   (-7.42%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       90.65 μs →       87.68 μs   (-3.27%) |      21   →      22     (+4.76%) |        1.90 ms →        1.93 ms   (+1.34%) | 
  │ │ ├ sirius::Band::solve                                             |        1.75 s  →        1.71 s    (-2.80%) |      21   →      22     (+4.76%) |       36.85 s  →       37.53 s    (+1.83%) | 
+ │ │ │ ├ sirius::Hamiltonian_k                                         |      210.20 μs →      180.31 μs  (-14.22%) |      21   →      22     (+4.76%) |        4.41 ms →        3.97 ms  (-10.13%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      199.79 μs →      170.90 μs  (-14.46%) |      21   →      22     (+4.76%) |        4.20 ms →        3.76 ms  (-10.38%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        7.82 μs →        6.33 μs  (-19.09%) |      21   →      22     (+4.76%) |      164.22 μs →      139.19 μs  (-15.24%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.64 s  →        1.56 s    (-4.69%) |      21   →      22     (+4.76%) |       34.39 s  →       34.34 s    (-0.15%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       73.73 ms →       76.59 ms   (+3.89%) |      21   →      22     (+4.76%) |        1.55 s  →        1.69 s    (+8.84%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.14 ms →        5.92 ms  (-17.10%) |     126   →     154    (+22.22%) |      899.75 ms →      911.62 ms   (+1.32%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       16.17 ms →       13.03 ms  (-19.39%) |      21   →      22     (+4.76%) |      339.59 ms →      286.77 ms  (-15.55%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      509.97 μs →      466.15 μs   (-8.59%) |      21   →      22     (+4.76%) |       10.71 ms →       10.26 ms   (-4.24%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        7.39 ms →        5.57 ms  (-24.58%) |      42   →      44     (+4.76%) |      310.40 ms →      245.24 ms  (-20.99%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.54 s  →        1.45 s    (-5.86%) |      21   →      22     (+4.76%) |       32.34 s  →       31.89 s    (-1.38%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       59.21 ms →       96.91 ms  (+63.67%) |     361   →     180    (-50.14%) |       21.37 s  →       17.44 s   (-18.39%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       37.60 ms →       71.53 ms  (+90.25%) |     361   →     180    (-50.14%) |       13.57 s  →       12.88 s    (-5.14%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.95 μs →        2.20 μs  (+12.56%) |     361   →     180    (-50.14%) |      704.46 μs →      395.36 μs  (-43.88%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.58 μs →        1.84 μs  (+16.87%) |     361   →     180    (-50.14%) |      569.19 μs →      331.69 μs  (-41.73%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      394.93 ns →      419.42 ns   (+6.20%) |     361   →     180    (-50.14%) |      142.57 μs →       75.49 μs  (-47.05%) | 
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      483.35 ns →      530.02 ns   (+9.65%) |     361   →     180    (-50.14%) |      174.49 μs →       95.40 μs  (-45.32%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        3.01 ms →        2.85 ms   (-5.52%) |     361   →     180    (-50.14%) |        1.09 s  →      512.18 ms  (-52.89%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.44 ms →        5.58 ms  (+62.14%) |     361   →     180    (-50.14%) |        1.24 s  →        1.00 s   (-19.16%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.57 ms →        8.47 ms  (+11.84%) |     722   →     360    (-50.14%) |        5.47 s  →        3.05 s   (-44.23%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |        5.92 ms →        7.91 ms  (+33.58%) |     361   →     180    (-50.14%) |        2.14 s  →        1.42 s   (-33.39%) | 
- │ │ │ │   │ ├ sddk::wf_inner                                          |      994.46 μs →        1.30 ms  (+30.87%) |     701   →     338    (-51.78%) |      697.12 ms →      439.88 ms  (-36.90%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       45.07 ns →       47.03 ns   (+4.34%) |     701   →     338    (-51.78%) |       31.59 μs →       15.89 μs  (-49.69%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |      831.56 μs →        1.12 ms  (+34.50%) |     701   →     338    (-51.78%) |      582.92 ms →      378.03 ms  (-35.15%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       54.17 ns →       60.25 ns  (+11.22%) |     701   →     338    (-51.78%) |       37.98 μs →       20.36 μs  (-46.37%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      137.77 μs →      293.74 μs (+113.20%) |     361   →     180    (-50.14%) |       49.74 ms →       52.87 ms   (+6.31%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        1.86 ms →        2.46 ms  (+31.96%) |     361   →     180    (-50.14%) |      673.05 ms →      442.85 ms  (-34.20%) | 
- │ │ │ │   │ └ sddk::wf_trans                                          |        2.11 ms →        3.08 ms  (+46.40%) |     340   →     158    (-53.53%) |      716.03 ms →      487.12 ms  (-31.97%) | 
- │ │ │ │   │   └ sddk::wf_trans|pw                                     |      701.20 μs →        1.03 ms  (+46.44%) |    1.02 K →     474    (-53.53%) |      715.22 ms →      486.72 ms  (-31.95%) | 
- │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.21 ms →        1.67 ms  (+37.96%) |     361   →     180    (-50.14%) |      435.71 ms →      299.72 ms  (-31.21%) | 
- │ │ │ │   │ └ sddk::wf_inner                                          |        1.16 ms →        1.59 ms  (+37.09%) |     361   →     180    (-50.14%) |      419.32 ms →      286.62 ms  (-31.65%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       43.40 ns →       43.20 ns   (-0.46%) |     361   →     180    (-50.14%) |       15.67 μs →        7.78 μs  (-50.37%) | 
- │ │ │ │   │   ├ sddk::wf_inner|pw                                     |      999.01 μs →        1.41 ms  (+41.14%) |     361   →     180    (-50.14%) |      360.64 ms →      253.81 ms  (-29.62%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       46.80 ns →       54.07 ns  (+15.54%) |     361   →     180    (-50.14%) |       16.89 μs →        9.73 μs  (-42.39%) | 
- │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       19.75 ms →       64.95 ms (+228.90%) |     361   →     180    (-50.14%) |        7.13 s  →       11.69 s   (+63.99%) | 
- │ │ │ │   ├ sirius::residuals                                         |        2.47 ms →        3.32 ms  (+34.42%) |     346   →     179    (-48.27%) |      854.43 ms →      594.19 ms  (-30.46%) | 
- │ │ │ │   │ ├ sddk::wf_trans                                          |        1.21 ms →        1.85 ms  (+52.30%) |     342   →     179    (-47.66%) |      415.45 ms →      331.16 ms  (-20.29%) | 
- │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      605.97 μs →      923.47 μs  (+52.39%) |     684   →     358    (-47.66%) |      414.48 ms →      330.60 ms  (-20.24%) | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.17 ms →        1.34 ms  (+14.95%) |     342   →     179    (-47.66%) |      398.48 ms →      239.74 ms  (-39.84%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        4.42 ms →        6.18 ms  (+39.77%) |      90   →      70    (-22.22%) |      397.82 ms →      432.47 ms   (+8.71%) | 
- │ │ │ │     └ sddk::wf_trans                                          |        2.45 ms →        3.61 ms  (+47.33%) |     159   →     118    (-25.79%) |      389.70 ms →      426.11 ms   (+9.34%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |        1.71 ms →        2.57 ms  (+50.21%) |     228   →     166    (-27.19%) |      389.40 ms →      425.87 ms   (+9.37%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      476.67 ns →      402.95 ns  (-15.46%) |      21   →      22     (+4.76%) |       10.01 μs →        8.86 μs  (-11.44%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       20.87 μs →       30.16 μs  (+44.52%) |      21   →      22     (+4.76%) |      438.21 μs →      663.46 μs  (+51.40%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.58 ms →        1.53 ms   (-3.41%) |      21   →      22     (+4.76%) |       33.16 ms →       33.56 ms   (+1.19%) | 
  │ │ ├ sirius::Density::generate                                       |      560.22 ms →      570.26 ms   (+1.79%) |      21   →      22     (+4.76%) |       11.76 s  →       12.55 s    (+6.64%) | 
- │ │ │ ├ sirius::Density::generate_valence                             |      383.43 ms →      405.88 ms   (+5.85%) |      21   →      22     (+4.76%) |        8.05 s  →        8.93 s   (+10.90%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.28 μs →        9.56 μs  (+15.50%) |      21   →      22     (+4.76%) |      173.82 μs →      210.32 μs  (+21.00%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.56 μs →        8.69 μs  (+14.87%) |      21   →      22     (+4.76%) |      158.84 μs →      191.15 μs  (+20.34%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       45.58 ms →       43.30 ms   (-5.01%) |      21   →      22     (+4.76%) |      957.21 ms →      952.51 ms   (-0.49%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       11.02 μs →       10.73 μs   (-2.63%) |      21   →      22     (+4.76%) |      231.48 μs →      236.13 μs   (+2.01%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |       23.93 ms →        7.17 ms  (-70.05%) |      21   →      22     (+4.76%) |      502.61 ms →      157.72 ms  (-68.62%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       20.57 ms →       35.10 ms  (+70.65%) |      21   →      22     (+4.76%) |      431.91 ms →      772.14 ms  (+78.77%) | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      945.76 ns →      873.77 ns   (-7.61%) |      21   →      22     (+4.76%) |       19.86 μs →       19.22 μs   (-3.21%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       93.93 ms →      102.42 ms   (+9.04%) |      21   →      22     (+4.76%) |        1.97 s  →        2.25 s   (+14.23%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.93 ms →        2.14 ms  (+11.40%) |      21   →      22     (+4.76%) |       40.43 ms →       47.18 ms  (+16.70%) | 
- │ │ │ │ └ sirius::Density::augment                                    |      193.06 ms →      218.54 ms  (+13.20%) |      21   →      22     (+4.76%) |        4.05 s  →        4.81 s   (+18.59%) | 
- │ │ │ │   └ sirius::Density::generate_rho_aug                         |      192.85 ms →      218.33 ms  (+13.21%) |      21   →      22     (+4.76%) |        4.05 s  →        4.80 s   (+18.60%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      148.70 ms →      135.45 ms   (-8.91%) |      21   →      22     (+4.76%) |        3.12 s  →        2.98 s    (-4.58%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      148.70 ms →      135.44 ms   (-8.91%) |      21   →      22     (+4.76%) |        3.12 s  →        2.98 s    (-4.58%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       68.38 ms →       52.37 ms  (-23.41%) |      21   →      22     (+4.76%) |        1.44 s  →        1.15 s   (-19.76%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       67.06 ms →       69.78 ms   (+4.06%) |      21   →      22     (+4.76%) |        1.41 s  →        1.54 s    (+9.02%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.61 ms →       12.64 ms   (+0.22%) |      21   →      22     (+4.76%) |      264.81 ms →      278.02 ms   (+4.99%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.77 ms →       23.76 ms   (-0.04%) |      21   →      22     (+4.76%) |      499.07 ms →      522.64 ms   (+4.72%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        4.31 ms →        5.17 ms  (+19.90%) |      21   →      22     (+4.76%) |       90.60 ms →      113.81 ms  (+25.61%) | 
  │ │ ├ sirius::Density::mix                                            |      136.18 ms →      136.65 ms   (+0.35%) |      21   →      22     (+4.76%) |        2.86 s  →        3.01 s    (+5.12%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      783.72 μs →      770.18 μs   (-1.73%) |      21   →      22     (+4.76%) |       16.46 ms →       16.94 ms   (+2.95%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |        4.91 ms →        4.87 ms   (-0.77%) |     259   →     274     (+5.79%) |        1.27 s  →        1.33 s    (+4.97%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.82 ms →        4.81 ms   (-0.22%) |     259   →     274     (+5.79%) |        1.25 s  →        1.32 s    (+5.56%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.82 ms →        4.81 ms   (-0.22%) |     259   →     274     (+5.79%) |        1.25 s  →        1.32 s    (+5.56%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        5.90 ms →        6.44 ms   (+9.04%) |      21   →      22     (+4.76%) |      124.00 ms →      141.65 ms  (+14.24%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.16 ms →        5.68 ms  (+10.07%) |      21   →      22     (+4.76%) |      108.28 ms →      124.85 ms  (+15.31%) | 
  │ │ ├ sirius::Potential::generate                                     |      365.68 ms →      358.87 ms   (-1.86%) |      21   →      22     (+4.76%) |        7.68 s  →        7.90 s    (+2.81%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |       45.40 ms →       38.39 ms  (-15.45%) |      21   →      22     (+4.76%) |      953.42 ms →      844.51 ms  (-11.42%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        3.20 ms →        6.57 ms (+105.43%) |      21   →      22     (+4.76%) |       67.20 ms →      144.63 ms (+115.21%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |        5.32 ms →        5.90 ms  (+11.05%) |      21   →      22     (+4.76%) |      111.62 ms →      129.86 ms  (+16.33%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.83 ms →        4.64 ms   (-4.03%) |      21   →      22     (+4.76%) |      101.47 ms →      102.02 ms   (+0.54%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.83 ms →        4.64 ms   (-4.02%) |      21   →      22     (+4.76%) |      101.44 ms →      102.00 ms   (+0.55%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      773.97 μs →      807.37 μs   (+4.31%) |      42   →      44     (+4.76%) |       32.51 ms →       35.52 ms   (+9.28%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       45.14 ms →       45.37 ms   (+0.51%) |      21   →      22     (+4.76%) |      947.95 ms →      998.19 ms   (+5.30%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       43.96 ms →       44.19 ms   (+0.54%) |      21   →      22     (+4.76%) |      923.13 ms →      972.29 ms   (+5.33%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |      684.30 μs →      677.85 μs   (-0.94%) |      42   →      44     (+4.76%) |       28.74 ms →       29.83 ms   (+3.78%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.69 ms →        5.11 ms   (+8.78%) |      21   →      22     (+4.76%) |       98.56 ms →      112.32 ms  (+13.96%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.60 ms →        3.59 ms   (-0.36%) |      21   →      22     (+4.76%) |       75.56 ms →       78.87 ms   (+4.38%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.56 ms →      268.48 ms   (-0.03%) |      21   →      22     (+4.76%) |        5.64 s  →        5.91 s    (+4.73%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      137.52 ns →      151.95 ns  (+10.49%) |      21   →      22     (+4.76%) |        2.89 μs →        3.34 μs  (+15.75%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |       93.39 ms →       95.89 ms   (+2.68%) |      21   →      22     (+4.76%) |        1.96 s  →        2.11 s    (+7.57%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |       93.39 ms →       95.89 ms   (+2.68%) |      21   →      22     (+4.76%) |        1.96 s  →        2.11 s    (+7.57%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.28 ms →       13.43 ms   (+1.08%) |      21   →      22     (+4.76%) |      278.97 ms →      295.40 ms   (+5.89%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       66.87 ms →       69.27 ms   (+3.59%) |      21   →      22     (+4.76%) |        1.40 s  →        1.52 s    (+8.52%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.60 ms →       12.57 ms   (-0.29%) |      21   →      22     (+4.76%) |      264.66 ms →      276.47 ms   (+4.46%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.90 ms →        4.43 ms  (+13.64%) |      21   →      22     (+4.76%) |       81.83 ms →       97.42 ms  (+19.06%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.70 ms →        4.81 ms   (+2.32%) |     147   →     154     (+4.76%) |      691.19 ms →      740.93 ms   (+7.20%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.57 ms →        4.76 ms   (+4.09%) |     147   →     154     (+4.76%) |      672.19 ms →      733.02 ms   (+9.05%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.57 ms →        4.76 ms   (+4.09%) |     147   →     154     (+4.76%) |      672.10 ms →      732.91 ms   (+9.05%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.79 ms →        4.65 ms   (-2.96%) |      63   →      66     (+4.76%) |      301.73 ms →      306.75 ms   (+1.66%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.77 ms →        4.55 ms   (-4.68%) |      63   →      66     (+4.76%) |      300.41 ms →      300.00 ms   (-0.14%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.57 ms →        4.53 ms   (-0.71%) |      21   →      22     (+4.76%) |       95.92 ms →       99.77 ms   (+4.02%) | 
  │ │ └ sirius::Density::get_magnetisation                              |       75.54 μs →       75.45 μs   (-0.13%) |      21   →      22     (+4.76%) |        1.59 ms →        1.66 ms   (+4.63%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |       70.63 μs →       70.43 μs   (-0.29%) |      21   →      22     (+4.76%) |        1.48 ms →        1.55 ms   (+4.46%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.13 ms →        5.61 ms   (+9.27%) |       2   →       2              |       10.27 ms →       11.22 ms   (+9.27%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.56 ms →        4.81 ms   (+5.55%) |       6   →       6              |       27.36 ms →       28.88 ms   (+5.55%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.55 ms →        4.81 ms   (+5.64%) |       6   →       6              |       27.31 ms →       28.85 ms   (+5.64%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.55 ms →        4.81 ms   (+5.61%) |       6   →       6              |       27.31 ms →       28.84 ms   (+5.61%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.75 ms →        4.58 ms   (-3.51%) |       3   →       3              |       14.25 ms →       13.75 ms   (-3.51%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.74 ms →        4.54 ms   (-4.22%) |       3   →       3              |       14.23 ms →       13.63 ms   (-4.22%) | 
  ├ sirius::Periodic_function|inner                                     |        4.54 ms →        4.80 ms   (+5.74%) |       2   →       2              |        9.08 ms →        9.60 ms   (+5.74%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.53 ms →        4.79 ms   (+5.73%) |       2   →       2              |        9.07 ms →        9.59 ms   (+5.73%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.53 ms →        4.79 ms   (+5.73%) |       2   →       2              |        9.07 ms →        9.59 ms   (+5.73%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.73 ms →        4.52 ms   (-4.36%) |       1   →       1              |        4.73 ms →        4.52 ms   (-4.36%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.73 ms →        4.52 ms   (-4.37%) |       1   →       1              |        4.73 ms →        4.52 ms   (-4.37%) | 
+ └ sirius::finalize                                                    |      201.93 ms →      148.40 ms  (-26.51%) |       1   →       1              |      201.93 ms →      148.40 ms  (-26.51%) | 
  ====================================================================================================================================================================================================
```
