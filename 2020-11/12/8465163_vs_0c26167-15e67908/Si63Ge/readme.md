# Benchmark 0c261670dec9b96a58dd74a9134f19b00042d6d1 vs 8465163e5150bf9c73ec5dac4bf03576202704b3
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |       72.29 s  →       71.09 s    (-1.66%) |       1   →       1              |       72.29 s  →       71.09 s    (-1.66%) | 
  ├ sirius::initialize                                                  |        2.83 s  →        2.82 s    (-0.41%) |       1   →       1              |        2.83 s  →        2.82 s    (-0.41%) | 
  ├ sirius::Simulation_context::initialize                              |        3.70 s  →        3.69 s    (-0.45%) |       1   →       1              |        3.70 s  →        3.69 s    (-0.45%) | 
- │ ├ sirius::Simulation_context::init_comm                             |       33.36 ms →       37.51 ms  (+12.44%) |       1   →       1              |       33.36 ms →       37.51 ms  (+12.44%) | 
  │ ├ sirius::Unit_cell::initialize                                     |      167.25 ms →      162.66 ms   (-2.74%) |       1   →       1              |      167.25 ms →      162.66 ms   (-2.74%) | 
  │ │ ├ sirius::Atom_type::init                                         |       74.32 ms →       71.99 ms   (-3.13%) |       2   →       2              |      148.64 ms →      143.98 ms   (-3.13%) | 
  │ │ └ sirius::Unit_cell::update                                       |       18.53 ms →       18.59 ms   (+0.34%) |       1   →       1              |       18.53 ms →       18.59 ms   (+0.34%) | 
- │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.80 ms →        4.97 ms  (+30.84%) |       1   →       1              |        3.80 ms →        4.97 ms  (+30.84%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       14.66 ms →       13.56 ms   (-7.48%) |       1   →       1              |       14.66 ms →       13.56 ms   (-7.48%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       14.58 ms →       13.47 ms   (-7.65%) |       1   →       1              |       14.58 ms →       13.47 ms   (-7.65%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.73 ms →        2.75 ms   (+0.64%) |       1   →       1              |        2.73 ms →        2.75 ms   (+0.64%) | 
- │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      518.26 μs →      571.95 μs  (+10.36%) |       1   →       1              |      518.26 μs →      571.95 μs  (+10.36%) | 
- │ │       └ sirius::Unit_cell_symmetry|mag                            |       16.45 μs →       27.74 μs  (+68.68%) |       1   →       1              |       16.45 μs →       27.74 μs  (+68.68%) | 
  │ └ sirius::Simulation_context::update                                |        3.31 s  →        3.39 s    (+2.57%) |       1   →       1              |        3.31 s  →        3.39 s    (+2.57%) | 
  │   ├ sirius::Unit_cell::update                                       |        6.96 ms →        7.00 ms   (+0.57%) |       1   →       1              |        6.96 ms →        7.00 ms   (+0.57%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.65 ms →        3.66 ms   (+0.23%) |       1   →       1              |        3.65 ms →        3.66 ms   (+0.23%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.27 ms →        3.30 ms   (+0.72%) |       1   →       1              |        3.27 ms →        3.30 ms   (+0.72%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.23 ms →        3.25 ms   (+0.73%) |       1   →       1              |        3.23 ms →        3.25 ms   (+0.73%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.69 ms →        2.70 ms   (+0.17%) |       1   →       1              |        2.69 ms →        2.70 ms   (+0.17%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      498.67 μs →      517.60 μs   (+3.80%) |       1   →       1              |      498.67 μs →      517.60 μs   (+3.80%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       13.84 μs →       14.44 μs   (+4.37%) |       1   →       1              |       13.84 μs →       14.44 μs   (+4.37%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      213.05 ms →      213.50 ms   (+0.21%) |       2   →       2              |      426.11 ms →      427.00 ms   (+0.21%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.17 ms →       15.41 ms   (+1.58%) |       2   →       2              |       30.35 ms →       30.82 ms   (+1.58%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.26 ms →       13.24 ms   (-0.16%) |       1   →       1              |       13.26 ms →       13.24 ms   (-0.16%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.64 ms →       56.28 ms   (-0.65%) |       2   →       2              |      113.29 ms →      112.55 ms   (-0.65%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.15 ms →       45.25 ms   (+0.22%) |       2   →       2              |       90.30 ms →       90.50 ms   (+0.22%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.41 ms →       60.53 ms   (+0.20%) |       4   →       4              |      241.65 ms →      242.13 ms   (+0.20%) | 
  │   ├ sddk::Gvec::init                                                |       92.50 ms →       93.08 ms   (+0.63%) |       2   →       2              |      185.00 ms →      186.17 ms   (+0.63%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       69.27 ms →       69.58 ms   (+0.45%) |       2   →       2              |      138.54 ms →      139.16 ms   (+0.45%) | 
  │   ├ sddk::Gvec_shells                                               |       94.15 ms →      102.44 ms   (+8.80%) |       1   →       1              |       94.15 ms →      102.44 ms   (+8.80%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.95 ms →        1.98 ms   (+1.17%) |       1   →       1              |        1.95 ms →        1.98 ms   (+1.17%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      513.47 ms →      552.61 ms   (+7.62%) |       2   →       2              |        1.03 s  →        1.11 s    (+7.62%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |      153.18 ms →      149.02 ms   (-2.71%) |       1   →       1              |      153.18 ms →      149.02 ms   (-2.71%) | 
- │ ├ sirius::K_point::K_point                                          |        1.60 μs →        2.01 μs  (+26.14%) |       4   →       4              |        6.39 μs →        8.05 μs  (+26.14%) | 
  │ └ sirius::K_point_set::initialize                                   |      153.09 ms →      148.93 ms   (-2.72%) |       1   →       1              |      153.09 ms →      148.93 ms   (-2.72%) | 
  │   └ sirius::K_point::initialize                                     |       27.92 ms →       27.86 ms   (-0.22%) |       1   →       1              |       27.92 ms →       27.86 ms   (-0.22%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       10.95 ms →       10.93 ms   (-0.21%) |       1   →       1              |       10.95 ms →       10.93 ms   (-0.21%) | 
  │     │ └ sddk::Gvec::init                                            |        4.89 ms →        4.89 ms   (-0.11%) |       1   →       1              |        4.89 ms →        4.89 ms   (-0.11%) | 
+ │     ├ sddk::matrix_storage::matrix_storage                          |       12.22 μs →        7.80 μs  (-36.17%) |       1   →       1              |       12.22 μs →        7.80 μs  (-36.17%) | 
  │     └ sirius::K_point::update                                       |       14.19 ms →       14.14 ms   (-0.33%) |       1   →       1              |       14.19 ms →       14.14 ms   (-0.33%) | 
  │       └ sirius::Beta_projectors                                     |       10.21 ms →       10.17 ms   (-0.38%) |       1   →       1              |       10.21 ms →       10.17 ms   (-0.38%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.28 ms →        8.24 ms   (-0.40%) |       1   →       1              |        8.28 ms →        8.24 ms   (-0.40%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.53 ms →        2.57 ms   (+1.56%) |       2   →       2              |        5.06 ms →        5.14 ms   (+1.56%) | 
  ├ sirius::Potential                                                   |       50.16 ms →       53.03 ms   (+5.72%) |       1   →       1              |       50.16 ms →       53.03 ms   (+5.72%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.90 ms →        2.92 ms   (+0.88%) |       6   →       6              |       17.39 ms →       17.54 ms   (+0.88%) | 
  │ └ sirius::Potential::update                                         |       32.14 ms →       34.96 ms   (+8.80%) |       1   →       1              |       32.14 ms →       34.96 ms   (+8.80%) | 
  │   └ sirius::Potential::generate_local_potential                     |       31.75 ms →       34.55 ms   (+8.82%) |       1   →       1              |       31.75 ms →       34.55 ms   (+8.82%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       26.38 ms →       26.79 ms   (+1.53%) |       1   →       1              |       26.38 ms →       26.79 ms   (+1.53%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        4.82 ms →        7.24 ms  (+50.18%) |       1   →       1              |        4.82 ms →        7.24 ms  (+50.18%) | 
- ├ sirius::Density                                                     |       36.19 ms →       42.53 ms  (+17.53%) |       1   →       1              |       36.19 ms →       42.53 ms  (+17.53%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.82 ms →        2.82 ms   (-0.11%) |       2   →       2              |        5.64 ms →        5.64 ms   (-0.11%) | 
- │ └ sirius::Density::update                                           |       30.39 ms →       36.76 ms  (+20.95%) |       1   →       1              |       30.39 ms →       36.76 ms  (+20.95%) | 
- │   └ sirius::Density::generate_pseudo_core_charge_density            |       30.07 ms →       36.54 ms  (+21.50%) |       1   →       1              |       30.07 ms →       36.54 ms  (+21.50%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |       78.34 μs →       77.22 μs   (-1.43%) |       1   →       1              |       78.34 μs →       77.22 μs   (-1.43%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       26.33 ms →       26.31 ms   (-0.06%) |       1   →       1              |       26.33 ms →       26.31 ms   (-0.06%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        3.28 ms →        9.86 ms (+200.32%) |       1   →       1              |        3.28 ms →        9.86 ms (+200.32%) | 
- ├ sirius::Density::initial_density                                    |       54.33 ms →       62.48 ms  (+14.99%) |       1   →       1              |       54.33 ms →       62.48 ms  (+14.99%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       26.63 ms →       26.67 ms   (+0.17%) |       1   →       1              |       26.63 ms →       26.67 ms   (+0.17%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.50 ms →        8.25 ms  (+83.12%) |       2   →       2              |        9.01 ms →       16.49 ms  (+83.12%) | 
  │ └ sirius::Periodic_function::integrate                              |        5.33 ms →        5.72 ms   (+7.46%) |       1   →       1              |        5.33 ms →        5.72 ms   (+7.46%) | 
  ├ sirius::Potential::generate                                         |      360.89 ms →      370.45 ms   (+2.65%) |       1   →       1              |      360.89 ms →      370.45 ms   (+2.65%) | 
- │ ├ sirius::Potential::poisson                                        |       34.07 ms →       43.24 ms  (+26.90%) |       1   →       1              |       34.07 ms →       43.24 ms  (+26.90%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.42 ms →       11.62 ms (+240.34%) |       1   →       1              |        3.42 ms →       11.62 ms (+240.34%) | 
- │ │ └ sirius::Periodic_function|inner                                 |        5.08 ms →        5.91 ms  (+16.41%) |       1   →       1              |        5.08 ms →        5.91 ms  (+16.41%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.63 ms →        4.64 ms   (+0.21%) |       1   →       1              |        4.63 ms →        4.64 ms   (+0.21%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.63 ms →        4.63 ms   (+0.14%) |       1   →       1              |        4.63 ms →        4.63 ms   (+0.14%) | 
  │ ├ sirius::Periodic_function::add                                    |      782.31 μs →      856.27 μs   (+9.45%) |       2   →       2              |        1.56 ms →        1.71 ms   (+9.45%) | 
  │ ├ sirius::Potential::xc                                             |       51.43 ms →       50.99 ms   (-0.84%) |       1   →       1              |       51.43 ms →       50.99 ms   (-0.84%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       50.22 ms →       49.79 ms   (-0.86%) |       1   →       1              |       50.22 ms →       49.79 ms   (-0.86%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.53 ms →        2.55 ms   (+0.77%) |       2   →       2              |        5.06 ms →        5.10 ms   (+0.77%) | 
+ │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.03 ms →        4.12 ms  (-18.10%) |       1   →       1              |        5.03 ms →        4.12 ms  (-18.10%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.08 ms →        3.76 ms  (+22.31%) |       1   →       1              |        3.08 ms →        3.76 ms  (+22.31%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      269.33 ms →      269.34 ms   (+0.00%) |       1   →       1              |      269.33 ms →      269.34 ms   (+0.00%) | 
- │ └ sirius::Potential::generate_PAW_effective_potential               |      182.00 ns →      284.00 ns  (+56.04%) |       1   →       1              |      182.00 ns →      284.00 ns  (+56.04%) | 
  ├ sirius::Hamiltonian0                                                |        7.28 ms →        7.02 ms   (-3.64%) |       1   →       1              |        7.28 ms →        7.02 ms   (-3.64%) | 
  │ ├ sirius::Local_operator                                            |        6.76 ms →        6.57 ms   (-2.75%) |       1   →       1              |        6.76 ms →        6.57 ms   (-2.75%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.72 ms →        2.77 ms   (+2.06%) |       1   →       1              |        2.72 ms →        2.77 ms   (+2.06%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        3.19 ms →        3.02 ms   (-5.43%) |       1   →       1              |        3.19 ms →        3.02 ms   (-5.43%) | 
+ │ ├ sirius::Non_local_operator                                        |       89.20 μs →       70.57 μs  (-20.88%) |       2   →       2              |      178.39 μs →      141.14 μs  (-20.88%) | 
+ │ ├ sirius::D_operator::initialize                                    |      158.49 μs →      138.16 μs  (-12.83%) |       1   →       1              |      158.49 μs →      138.16 μs  (-12.83%) | 
  │ └ sirius::Q_operator::initialize                                    |      104.13 μs →       97.29 μs   (-6.57%) |       1   →       1              |      104.13 μs →       97.29 μs   (-6.57%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.27 s  →        1.29 s    (+1.85%) |       1   →       1              |        1.27 s  →        1.29 s    (+1.85%) | 
+ │ ├ sirius::Hamiltonian_k                                             |       54.16 ms →       37.36 ms  (-31.03%) |       1   →       1              |       54.16 ms →       37.36 ms  (-31.03%) | 
+ │ │ ├ sirius::Local_operator::prepare_k                               |      437.09 μs →      284.44 μs  (-34.93%) |       1   →       1              |      437.09 μs →      284.44 μs  (-34.93%) | 
+ │ │ └ sirius::Beta_projectors_base::prepare                           |       53.72 ms →       37.07 ms  (-31.00%) |       1   →       1              |       53.72 ms →       37.07 ms  (-31.00%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.21 s  →        1.25 s    (+3.31%) |       1   →       1              |        1.21 s  →        1.25 s    (+3.31%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       76.57 ms →       80.71 ms   (+5.40%) |       4   →       4              |      306.27 ms →      322.82 ms   (+5.40%) | 
- │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       37.27 ms →       54.29 ms  (+45.66%) |       1   →       1              |       37.27 ms →       54.29 ms  (+45.66%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        7.09 ms →        7.54 ms   (+6.23%) |       1   →       1              |        7.09 ms →        7.54 ms   (+6.23%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      335.54 ms →      316.15 ms   (-5.78%) |       1   →       1              |      335.54 ms →      316.15 ms   (-5.78%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      247.42 ms →      246.49 ms   (-0.37%) |       1   →       1              |      247.42 ms →      246.49 ms   (-0.37%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.73 μs →        4.10 μs   (+9.96%) |       1   →       1              |        3.73 μs →        4.10 μs   (+9.96%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.80 μs →        3.08 μs  (+10.10%) |       1   →       1              |        2.80 μs →        3.08 μs  (+10.10%) | 
+ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      690.00 ns →      474.00 ns  (-31.30%) |       1   →       1              |      690.00 ns →      474.00 ns  (-31.30%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      625.00 ns →      635.00 ns   (+1.60%) |       1   →       1              |      625.00 ns →      635.00 ns   (+1.60%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.12 ms →        3.07 ms   (-1.50%) |       1   →       1              |        3.12 ms →        3.07 ms   (-1.50%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.25 ms →       21.39 ms   (+0.63%) |       1   →       1              |       21.25 ms →       21.39 ms   (+0.63%) | 
+ │ │ │ └ sirius::Non_local_operator::apply                             |       31.85 ms →       22.58 ms  (-29.13%) |       2   →       2              |       63.71 ms →       45.15 ms  (-29.13%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.63 ms →       14.93 ms   (+2.08%) |       2   →       2              |       29.26 ms →       29.87 ms   (+2.08%) | 
  │ │ │ └ sddk::wf_inner                                                |       14.42 ms →       14.72 ms   (+2.12%) |       2   →       2              |       28.83 ms →       29.44 ms   (+2.12%) | 
+ │ │ │   ├ sddk::wf_inner|scale                                        |       43.50 ns →       19.00 ns  (-56.32%) |       2   →       2              |       87.00 ns →       38.00 ns  (-56.32%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       14.28 ms →       14.59 ms   (+2.15%) |       2   →       2              |       28.57 ms →       29.18 ms   (+2.15%) | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |       20.50 ns →       21.00 ns   (+2.44%) |       2   →       2              |       41.00 ns →       42.00 ns   (+2.44%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      235.04 ms →      251.63 ms   (+7.06%) |       1   →       1              |      235.04 ms →      251.63 ms   (+7.06%) | 
  │ │ └ sddk::wf_trans                                                  |        2.60 ms →        2.63 ms   (+1.13%) |       1   →       1              |        2.60 ms →        2.63 ms   (+1.13%) | 
  │ │   └ sddk::wf_trans|pw                                             |        2.60 ms →        2.63 ms   (+1.13%) |       1   →       1              |        2.60 ms →        2.63 ms   (+1.13%) | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      377.00 ns →      375.00 ns   (-0.53%) |       1   →       1              |      377.00 ns →      375.00 ns   (-0.53%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |       62.72 s  →       61.49 s    (-1.95%) |       1   →       1              |       62.72 s  →       61.49 s    (-1.95%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.42 ms →        2.45 ms   (+1.04%) |      19   →      19              |       46.07 ms →       46.54 ms   (+1.04%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        2.98 s  →        2.92 s    (-1.98%) |      21   →      21              |       62.51 s  →       61.27 s    (-1.98%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        5.20 ms →        5.21 ms   (+0.30%) |      21   →      21              |      109.12 ms →      109.45 ms   (+0.30%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.43 ms →        4.48 ms   (+1.22%) |      21   →      21              |       93.05 ms →       94.18 ms   (+1.22%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      531.14 μs →      570.74 μs   (+7.45%) |      21   →      21              |       11.15 ms →       11.99 ms   (+7.45%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.90 ms →        2.84 ms   (-2.15%) |      21   →      21              |       60.87 ms →       59.56 ms   (-2.15%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |      241.91 μs →      219.38 μs   (-9.31%) |      42   →      42              |       10.16 ms →        9.21 ms   (-9.31%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |      116.56 μs →      119.99 μs   (+2.95%) |      21   →      21              |        2.45 ms →        2.52 ms   (+2.95%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       87.23 μs →       89.06 μs   (+2.10%) |      21   →      21              |        1.83 ms →        1.87 ms   (+2.10%) | 
  │ │ ├ sirius::Band::solve                                             |        1.76 s  →        1.75 s    (-0.47%) |      21   →      21              |       36.94 s  →       36.76 s    (-0.47%) | 
+ │ │ │ ├ sirius::Hamiltonian_k                                         |      275.66 μs →      241.32 μs  (-12.46%) |      21   →      21              |        5.79 ms →        5.07 ms  (-12.46%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      267.29 μs →      232.85 μs  (-12.89%) |      21   →      21              |        5.61 ms →        4.89 ms  (-12.89%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        6.06 μs →        6.31 μs   (+4.21%) |      21   →      21              |      127.21 μs →      132.58 μs   (+4.21%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.63 s  →        1.63 s    (-0.18%) |      21   →      21              |       34.32 s  →       34.25 s    (-0.18%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       72.14 ms →       66.34 ms   (-8.04%) |      21   →      21              |        1.51 s  →        1.39 s    (-8.04%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.20 ms →        7.20 ms   (+0.04%) |     126   →     126              |      907.06 ms →      907.45 ms   (+0.04%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       17.97 ms →       16.68 ms   (-7.15%) |      21   →      21              |      377.29 ms →      350.31 ms   (-7.15%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      465.78 μs →      461.10 μs   (-1.00%) |      21   →      21              |        9.78 ms →        9.68 ms   (-1.00%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        8.17 ms →        7.42 ms   (-9.25%) |      42   →      42              |      343.23 ms →      311.47 ms   (-9.25%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.54 s  →        1.54 s    (+0.22%) |      21   →      21              |       32.26 s  →       32.33 s    (+0.22%) | 
+ │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       55.22 ms →       49.66 ms  (-10.05%) |     361   →     361              |       19.93 s  →       17.93 s   (-10.05%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       30.80 ms →       29.61 ms   (-3.87%) |     361   →     361              |       11.12 s  →       10.69 s    (-3.87%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.98 μs →        2.14 μs   (+8.21%) |     361   →     361              |      714.66 μs →      773.33 μs   (+8.21%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.62 μs →        1.77 μs   (+9.11%) |     361   →     361              |      584.83 μs →      638.08 μs   (+9.11%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      416.43 ns →      421.52 ns   (+1.22%) |     361   →     361              |      150.33 μs →      152.17 μs   (+1.22%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      571.62 ns →      560.95 ns   (-1.87%) |     361   →     361              |      206.36 μs →      202.50 μs   (-1.87%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.83 ms →        2.74 ms   (-3.18%) |     361   →     361              |        1.02 s  →      988.17 ms   (-3.18%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.39 ms →        3.20 ms   (-5.33%) |     361   →     361              |        1.22 s  →        1.16 s    (-5.33%) | 
+ │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        9.09 ms →        7.05 ms  (-22.50%) |     722   →     722              |        6.56 s  →        5.09 s   (-22.50%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |        7.12 ms →        7.17 ms   (+0.70%) |     361   →     361              |        2.57 s  →        2.59 s    (+0.70%) | 
+ │ │ │ │   │ ├ sddk::wf_inner                                          |        1.21 ms →        1.03 ms  (-14.67%) |     701   →     701              |      846.03 ms →      721.88 ms  (-14.67%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       51.47 ns →       44.77 ns  (-13.00%) |     701   →     701              |       36.08 μs →       31.39 μs  (-13.00%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        1.04 ms →      865.76 μs  (-16.96%) |     701   →     701              |      730.82 ms →      606.90 ms  (-16.96%) | 
+ │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       51.13 ns →       43.38 ns  (-15.16%) |     701   →     701              |       35.84 μs →       30.41 μs  (-15.16%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      271.18 μs →      248.99 μs   (-8.18%) |     361   →     361              |       97.90 ms →       89.89 ms   (-8.18%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        2.08 ms →        2.63 ms  (+26.40%) |     361   →     361              |      752.03 ms →      950.53 ms  (+26.40%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |        2.57 ms →        2.43 ms   (-5.54%) |     340   →     340              |      874.17 ms →      825.76 ms   (-5.54%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |      856.21 μs →      808.77 μs   (-5.54%) |    1.02 K →    1.02 K            |      873.33 ms →      824.95 ms   (-5.54%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.35 ms →        1.31 ms   (-3.08%) |     361   →     361              |      487.09 ms →      472.07 ms   (-3.08%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |        1.30 ms →        1.26 ms   (-3.08%) |     361   →     361              |      470.33 ms →      455.86 ms   (-3.08%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       53.71 ns →       38.42 ns  (-28.47%) |     361   →     361              |       19.39 μs →       13.87 μs  (-28.47%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        1.14 ms →        1.10 ms   (-3.65%) |     361   →     361              |      410.81 ms →      395.80 ms   (-3.65%) | 
+ │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       46.97 ns →       40.29 ns  (-14.23%) |     361   →     361              |       16.96 μs →       14.54 μs  (-14.23%) | 
- │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       21.39 ms →       27.97 ms  (+30.73%) |     361   →     361              |        7.72 s  →       10.10 s   (+30.73%) | 
+ │ │ │ │   ├ sirius::residuals                                         |        3.00 ms →        2.33 ms  (-22.33%) |     346   →     346              |        1.04 s  →      807.57 ms  (-22.33%) | 
+ │ │ │ │   │ ├ sddk::wf_trans                                          |        1.32 ms →        1.11 ms  (-15.57%) |     342   →     342              |      450.99 ms →      380.77 ms  (-15.57%) | 
+ │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      657.90 μs →      555.27 μs  (-15.60%) |     684   →     684              |      450.00 ms →      379.81 ms  (-15.60%) | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.59 ms →        1.16 ms  (-27.25%) |     342   →     342              |      543.45 ms →      395.34 ms  (-27.25%) | 
+ │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        5.50 ms →        4.71 ms  (-14.31%) |      90   →      90              |      494.63 ms →      423.83 ms  (-14.31%) | 
+ │ │ │ │     └ sddk::wf_trans                                          |        3.06 ms →        2.61 ms  (-14.57%) |     159   →     159              |      486.21 ms →      415.35 ms  (-14.57%) | 
+ │ │ │ │       └ sddk::wf_trans|pw                                     |        2.13 ms →        1.82 ms  (-14.58%) |     228   →     228              |      485.90 ms →      415.05 ms  (-14.58%) | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      531.86 ns →      499.05 ns   (-6.17%) |      21   →      21              |       11.17 μs →       10.48 μs   (-6.17%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       19.57 μs →       20.02 μs   (+2.31%) |      21   →      21              |      410.96 μs →      420.45 μs   (+2.31%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.52 ms →        1.58 ms   (+4.17%) |      21   →      21              |       31.90 ms →       33.23 ms   (+4.17%) | 
  │ │ ├ sirius::Density::generate                                       |      568.92 ms →      563.75 ms   (-0.91%) |      21   →      21              |       11.95 s  →       11.84 s    (-0.91%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      412.80 ms →      399.08 ms   (-3.32%) |      21   →      21              |        8.67 s  →        8.38 s    (-3.32%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        7.16 μs →       10.58 μs  (+47.72%) |      21   →      21              |      150.37 μs →      222.13 μs  (+47.72%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        6.51 μs →        9.60 μs  (+47.47%) |      21   →      21              |      136.67 μs →      201.54 μs  (+47.47%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       37.03 ms →       26.03 ms  (-29.72%) |      21   →      21              |      777.71 ms →      546.57 ms  (-29.72%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       10.83 μs →       10.78 μs   (-0.51%) |      21   →      21              |      227.51 μs →      226.35 μs   (-0.51%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        6.01 ms →        4.68 ms  (-22.04%) |      21   →      21              |      126.14 ms →       98.34 ms  (-22.04%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       29.96 ms →       20.29 ms  (-32.26%) |      21   →      21              |      629.17 ms →      426.18 ms  (-32.26%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      875.81 ns →        1.01 μs  (+15.63%) |      21   →      21              |       18.39 μs →       21.27 μs  (+15.63%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      108.58 ms →      119.55 ms  (+10.10%) |      21   →      21              |        2.28 s  →        2.51 s   (+10.10%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.22 ms →        1.96 ms  (-11.73%) |      21   →      21              |       46.70 ms →       41.22 ms  (-11.73%) | 
  │ │ │ │ └ sirius::Density::augment                                    |      229.81 ms →      216.25 ms   (-5.90%) |      21   →      21              |        4.83 s  →        4.54 s    (-5.90%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |      229.60 ms →      216.03 ms   (-5.91%) |      21   →      21              |        4.82 s  →        4.54 s    (-5.91%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      128.35 ms →      137.05 ms   (+6.78%) |      21   →      21              |        2.70 s  →        2.88 s    (+6.78%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      128.35 ms →      137.05 ms   (+6.78%) |      21   →      21              |        2.70 s  →        2.88 s    (+6.78%) | 
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       45.19 ms →       53.14 ms  (+17.61%) |      21   →      21              |      948.97 ms →        1.12 s   (+17.61%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       69.91 ms →       70.64 ms   (+1.04%) |      21   →      21              |        1.47 s  →        1.48 s    (+1.04%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.60 ms →       12.62 ms   (+0.17%) |      21   →      21              |      264.52 ms →      264.97 ms   (+0.17%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.53 ms →       23.93 ms   (+1.71%) |      21   →      21              |      494.13 ms →      502.57 ms   (+1.71%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        4.24 ms →        3.68 ms  (-13.25%) |      21   →      21              |       88.98 ms →       77.19 ms  (-13.25%) | 
+ │ │ ├ sirius::Density::mix                                            |      134.43 ms →       79.79 ms  (-40.64%) |      21   →      21              |        2.82 s  →        1.68 s   (-40.64%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      660.13 μs →        1.09 ms  (+65.01%) |      21   →      21              |       13.86 ms →       22.88 ms  (+65.01%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |        4.71 ms →        4.60 ms   (-2.20%) |     259   →     259              |        1.22 s  →        1.19 s    (-2.20%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.62 ms →        4.55 ms   (-1.51%) |     259   →     259              |        1.20 s  →        1.18 s    (-1.51%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.62 ms →        4.55 ms   (-1.51%) |     259   →     259              |        1.20 s  →        1.18 s    (-1.51%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        6.24 ms →        6.01 ms   (-3.69%) |      21   →      21              |      131.05 ms →      126.22 ms   (-3.69%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.48 ms →        5.16 ms   (-5.85%) |      21   →      21              |      115.06 ms →      108.33 ms   (-5.85%) | 
  │ │ ├ sirius::Potential::generate                                     |      354.94 ms →      363.66 ms   (+2.46%) |      21   →      21              |        7.45 s  →        7.64 s    (+2.46%) | 
- │ │ │ ├ sirius::Potential::poisson                                    |       34.31 ms →       43.46 ms  (+26.68%) |      21   →      21              |      720.47 ms →      912.70 ms  (+26.68%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        3.91 ms →       11.80 ms (+201.98%) |      21   →      21              |       82.07 ms →      247.84 ms (+201.98%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |        4.91 ms →        5.91 ms  (+20.33%) |      21   →      21              |      103.06 ms →      124.01 ms  (+20.33%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.63 ms →        4.64 ms   (+0.24%) |      21   →      21              |       97.13 ms →       97.37 ms   (+0.24%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.62 ms →        4.64 ms   (+0.24%) |      21   →      21              |       97.11 ms →       97.34 ms   (+0.24%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      790.90 μs →      818.41 μs   (+3.48%) |      42   →      42              |       33.22 ms →       34.37 ms   (+3.48%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       45.43 ms →       44.52 ms   (-2.02%) |      21   →      21              |      954.04 ms →      934.82 ms   (-2.02%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       44.25 ms →       43.33 ms   (-2.07%) |      21   →      21              |      929.16 ms →      909.91 ms   (-2.07%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |      671.31 μs →      691.23 μs   (+2.97%) |      42   →      42              |       28.19 ms →       29.03 ms   (+2.97%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.57 ms →        4.22 ms   (-7.78%) |      21   →      21              |       96.07 ms →       88.59 ms   (-7.78%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.60 ms →        3.80 ms   (+5.62%) |      21   →      21              |       75.59 ms →       79.84 ms   (+5.62%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.56 ms →      268.83 ms   (+0.10%) |      21   →      21              |        5.64 s  →        5.65 s    (+0.10%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      182.76 ns →      178.38 ns   (-2.40%) |      21   →      21              |        3.84 μs →        3.75 μs   (-2.40%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |       96.20 ms →       96.57 ms   (+0.38%) |      21   →      21              |        2.02 s  →        2.03 s    (+0.38%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |       96.20 ms →       96.57 ms   (+0.38%) |      21   →      21              |        2.02 s  →        2.03 s    (+0.38%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.31 ms →       13.32 ms   (+0.09%) |      21   →      21              |      279.41 ms →      279.66 ms   (+0.09%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       69.67 ms →       70.01 ms   (+0.50%) |      21   →      21              |        1.46 s  →        1.47 s    (+0.50%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.60 ms →       12.60 ms   (+0.05%) |      21   →      21              |      264.54 ms →      264.67 ms   (+0.05%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        4.08 ms →        3.75 ms   (-8.20%) |      21   →      21              |       85.69 ms →       78.67 ms   (-8.20%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.85 ms →        4.90 ms   (+1.20%) |     147   →     147              |      712.40 ms →      720.96 ms   (+1.20%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.76 ms →        4.75 ms   (-0.04%) |     147   →     147              |      699.21 ms →      698.93 ms   (-0.04%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.76 ms →        4.75 ms   (-0.04%) |     147   →     147              |      699.12 ms →      698.84 ms   (-0.04%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.60 ms →        4.56 ms   (-0.90%) |      63   →      63              |      289.80 ms →      287.20 ms   (-0.90%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.58 ms →        4.54 ms   (-0.95%) |      63   →      63              |      288.75 ms →      286.01 ms   (-0.95%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.53 ms →        4.54 ms   (+0.42%) |      21   →      21              |       95.04 ms →       95.44 ms   (+0.42%) | 
  │ │ └ sirius::Density::get_magnetisation                              |       74.87 μs →       76.46 μs   (+2.12%) |      21   →      21              |        1.57 ms →        1.61 ms   (+2.12%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |       70.22 μs →       71.19 μs   (+1.38%) |      21   →      21              |        1.47 ms →        1.49 ms   (+1.38%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.43 ms →        5.70 ms   (+4.96%) |       2   →       2              |       10.86 ms →       11.40 ms   (+4.96%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.80 ms →        4.74 ms   (-1.15%) |       6   →       6              |       28.78 ms →       28.44 ms   (-1.15%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.79 ms →        4.72 ms   (-1.35%) |       6   →       6              |       28.73 ms →       28.34 ms   (-1.35%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.79 ms →        4.72 ms   (-1.35%) |       6   →       6              |       28.73 ms →       28.34 ms   (-1.35%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.55 ms →        4.56 ms   (+0.33%) |       3   →       3              |       13.65 ms →       13.69 ms   (+0.33%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.54 ms →        4.53 ms   (-0.17%) |       3   →       3              |       13.62 ms →       13.60 ms   (-0.17%) | 
  ├ sirius::Periodic_function|inner                                     |        4.73 ms →        4.91 ms   (+3.90%) |       2   →       2              |        9.45 ms →        9.82 ms   (+3.90%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.72 ms →        4.72 ms   (-0.01%) |       2   →       2              |        9.44 ms →        9.44 ms   (-0.01%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.72 ms →        4.72 ms   (-0.02%) |       2   →       2              |        9.44 ms →        9.43 ms   (-0.02%) | 
- ├ sirius::Smooth_periodic_function|inner                              |        4.52 ms →        4.98 ms  (+10.12%) |       1   →       1              |        4.52 ms →        4.98 ms  (+10.12%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.51 ms →        4.59 ms   (+1.76%) |       1   →       1              |        4.51 ms →        4.59 ms   (+1.76%) | 
+ └ sirius::finalize                                                    |      328.15 ms →      175.93 ms  (-46.39%) |       1   →       1              |      328.15 ms →      175.93 ms  (-46.39%) | 
  ====================================================================================================================================================================================================
```
