# Benchmark 58f31ed08f2b4e9e6d289f9ed116027f00413e03 vs 8cf25a48a521cee28df94fe46e001c67fed20f54
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |       71.73 s  →       71.17 s    (-0.77%) |       1   →       1              |       71.73 s  →       71.17 s    (-0.77%) | 
  ├ sirius::initialize                                                  |        2.77 s  →        2.81 s    (+1.15%) |       1   →       1              |        2.77 s  →        2.81 s    (+1.15%) | 
  ├ sirius::Simulation_context::initialize                              |        3.60 s  →        3.53 s    (-1.93%) |       1   →       1              |        3.60 s  →        3.53 s    (-1.93%) | 
- │ ├ sirius::Simulation_context::init_comm                             |        7.59 ms →       33.26 ms (+338.22%) |       1   →       1              |        7.59 ms →       33.26 ms (+338.22%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      167.06 ms →       68.05 ms  (-59.26%) |       1   →       1              |      167.06 ms →       68.05 ms  (-59.26%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       75.58 ms →       26.50 ms  (-64.94%) |       2   →       2              |      151.17 ms →       52.99 ms  (-64.94%) | 
  │ │ └ sirius::Unit_cell::update                                       |       15.81 ms →       14.97 ms   (-5.27%) |       1   →       1              |       15.81 ms →       14.97 ms   (-5.27%) | 
+ │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.99 ms →        3.73 ms  (-25.19%) |       1   →       1              |        4.99 ms →        3.73 ms  (-25.19%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       10.73 ms →       11.15 ms   (+3.90%) |       1   →       1              |       10.73 ms →       11.15 ms   (+3.90%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       10.67 ms →       11.09 ms   (+3.89%) |       1   →       1              |       10.67 ms →       11.09 ms   (+3.89%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.76 ms →        2.78 ms   (+0.84%) |       1   →       1              |        2.76 ms →        2.78 ms   (+0.84%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      494.88 μs →      491.41 μs   (-0.70%) |       1   →       1              |      494.88 μs →      491.41 μs   (-0.70%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       16.45 μs →       16.39 μs   (-0.40%) |       1   →       1              |       16.45 μs →       16.39 μs   (-0.40%) | 
  │ └ sirius::Simulation_context::update                                |        3.24 s  →        3.22 s    (-0.51%) |       1   →       1              |        3.24 s  →        3.22 s    (-0.51%) | 
  │   ├ sirius::Unit_cell::update                                       |        7.03 ms →        6.93 ms   (-1.37%) |       1   →       1              |        7.03 ms →        6.93 ms   (-1.37%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.65 ms →        3.56 ms   (-2.37%) |       1   →       1              |        3.65 ms →        3.56 ms   (-2.37%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.32 ms →        3.32 ms   (+0.06%) |       1   →       1              |        3.32 ms →        3.32 ms   (+0.06%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.27 ms →        3.27 ms   (+0.01%) |       1   →       1              |        3.27 ms →        3.27 ms   (+0.01%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.72 ms →        2.73 ms   (+0.21%) |       1   →       1              |        2.72 ms →        2.73 ms   (+0.21%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      510.03 μs →      505.02 μs   (-0.98%) |       1   →       1              |      510.03 μs →      505.02 μs   (-0.98%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       14.17 μs →       14.76 μs   (+4.14%) |       1   →       1              |       14.17 μs →       14.76 μs   (+4.14%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      212.95 ms →      213.07 ms   (+0.06%) |       2   →       2              |      425.89 ms →      426.14 ms   (+0.06%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.19 ms →       15.16 ms   (-0.23%) |       2   →       2              |       30.38 ms →       30.32 ms   (-0.23%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.29 ms →       13.24 ms   (-0.41%) |       1   →       1              |       13.29 ms →       13.24 ms   (-0.41%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.80 ms →       56.87 ms   (+0.12%) |       2   →       2              |      113.61 ms →      113.74 ms   (+0.12%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.13 ms →       45.17 ms   (+0.08%) |       2   →       2              |       90.26 ms →       90.33 ms   (+0.08%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.18 ms →       60.50 ms   (+0.52%) |       4   →       4              |      240.72 ms →      241.98 ms   (+0.52%) | 
  │   ├ sddk::Gvec::init                                                |       93.81 ms →       92.74 ms   (-1.14%) |       2   →       2              |      187.62 ms →      185.48 ms   (-1.14%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       70.02 ms →       69.09 ms   (-1.32%) |       2   →       2              |      140.03 ms →      138.19 ms   (-1.32%) | 
  │   ├ sddk::Gvec_shells                                               |       99.67 ms →      101.07 ms   (+1.40%) |       1   →       1              |       99.67 ms →      101.07 ms   (+1.40%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.96 ms →        1.99 ms   (+1.37%) |       1   →       1              |        1.96 ms →        1.99 ms   (+1.37%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      462.41 ms →      459.39 ms   (-0.65%) |       2   →       2              |      924.82 ms →      918.78 ms   (-0.65%) | 
+ ├ sirius::K_point_set::create_k_mesh                                  |      167.40 ms →      149.79 ms  (-10.52%) |       1   →       1              |      167.40 ms →      149.79 ms  (-10.52%) | 
- │ ├ sirius::K_point::K_point                                          |      981.00 ns →        1.80 μs  (+83.56%) |       4   →       4              |        3.92 μs →        7.20 μs  (+83.56%) | 
+ │ └ sirius::K_point_set::initialize                                   |      167.32 ms →      149.71 ms  (-10.52%) |       1   →       1              |      167.32 ms →      149.71 ms  (-10.52%) | 
  │   └ sirius::K_point::initialize                                     |       28.53 ms →       28.00 ms   (-1.85%) |       1   →       1              |       28.53 ms →       28.00 ms   (-1.85%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       10.80 ms →       10.91 ms   (+0.96%) |       1   →       1              |       10.80 ms →       10.91 ms   (+0.96%) | 
  │     │ └ sddk::Gvec::init                                            |        4.82 ms →        4.92 ms   (+1.92%) |       1   →       1              |        4.82 ms →        4.92 ms   (+1.92%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        7.57 μs →        7.54 μs   (-0.34%) |       1   →       1              |        7.57 μs →        7.54 μs   (-0.34%) | 
  │     └ sirius::K_point::update                                       |       14.86 ms →       14.28 ms   (-3.90%) |       1   →       1              |       14.86 ms →       14.28 ms   (-3.90%) | 
  │       └ sirius::Beta_projectors                                     |       10.93 ms →       10.30 ms   (-5.84%) |       1   →       1              |       10.93 ms →       10.30 ms   (-5.84%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.74 ms →        8.32 ms   (-4.84%) |       1   →       1              |        8.74 ms →        8.32 ms   (-4.84%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.57 ms →        2.59 ms   (+0.55%) |       2   →       2              |        5.14 ms →        5.17 ms   (+0.55%) | 
  ├ sirius::Potential                                                   |       51.55 ms →       51.10 ms   (-0.87%) |       1   →       1              |       51.55 ms →       51.10 ms   (-0.87%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.92 ms →        2.90 ms   (-0.48%) |       6   →       6              |       17.51 ms →       17.42 ms   (-0.48%) | 
  │ └ sirius::Potential::update                                         |       33.50 ms →       33.07 ms   (-1.31%) |       1   →       1              |       33.50 ms →       33.07 ms   (-1.31%) | 
  │   └ sirius::Potential::generate_local_potential                     |       33.09 ms →       32.67 ms   (-1.29%) |       1   →       1              |       33.09 ms →       32.67 ms   (-1.29%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       26.59 ms →       24.26 ms   (-8.77%) |       1   →       1              |       26.59 ms →       24.26 ms   (-8.77%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        5.98 ms →        7.90 ms  (+32.08%) |       1   →       1              |        5.98 ms →        7.90 ms  (+32.08%) | 
  ├ sirius::Density                                                     |       41.36 ms →       40.37 ms   (-2.40%) |       1   →       1              |       41.36 ms →       40.37 ms   (-2.40%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.81 ms →        2.81 ms   (+0.17%) |       2   →       2              |        5.61 ms →        5.62 ms   (+0.17%) | 
  │ └ sirius::Density::update                                           |       35.61 ms →       34.61 ms   (-2.81%) |       1   →       1              |       35.61 ms →       34.61 ms   (-2.81%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       35.39 ms →       34.38 ms   (-2.86%) |       1   →       1              |       35.39 ms →       34.38 ms   (-2.86%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |       76.49 μs →       80.15 μs   (+4.78%) |       1   →       1              |       76.49 μs →       80.15 μs   (+4.78%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       26.39 ms →       24.17 ms   (-8.43%) |       1   →       1              |       26.39 ms →       24.17 ms   (-8.43%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        8.61 ms →        9.83 ms  (+14.16%) |       1   →       1              |        8.61 ms →        9.83 ms  (+14.16%) | 
  ├ sirius::Density::initial_density                                    |       60.60 ms →       58.87 ms   (-2.86%) |       1   →       1              |       60.60 ms →       58.87 ms   (-2.86%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       26.76 ms →       25.22 ms   (-5.77%) |       1   →       1              |       26.76 ms →       25.22 ms   (-5.77%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        7.47 ms →        7.88 ms   (+5.48%) |       2   →       2              |       14.93 ms →       15.75 ms   (+5.48%) | 
+ │ └ sirius::Periodic_function::integrate                              |        5.33 ms →        4.51 ms  (-15.31%) |       1   →       1              |        5.33 ms →        4.51 ms  (-15.31%) | 
  ├ sirius::Potential::generate                                         |      369.43 ms →      365.70 ms   (-1.01%) |       1   →       1              |      369.43 ms →      365.70 ms   (-1.01%) | 
  │ ├ sirius::Potential::poisson                                        |       41.77 ms →       38.64 ms   (-7.51%) |       1   →       1              |       41.77 ms →       38.64 ms   (-7.51%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        9.97 ms →        9.93 ms   (-0.44%) |       1   →       1              |        9.97 ms →        9.93 ms   (-0.44%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        5.73 ms →        5.16 ms   (-9.83%) |       1   →       1              |        5.73 ms →        5.16 ms   (-9.83%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.65 ms →        4.84 ms   (+4.08%) |       1   →       1              |        4.65 ms →        4.84 ms   (+4.08%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.64 ms →        4.83 ms   (+4.12%) |       1   →       1              |        4.64 ms →        4.83 ms   (+4.12%) | 
  │ ├ sirius::Periodic_function::add                                    |      828.88 μs →      761.00 μs   (-8.19%) |       2   →       2              |        1.66 ms →        1.52 ms   (-8.19%) | 
  │ ├ sirius::Potential::xc                                             |       50.94 ms →       50.84 ms   (-0.18%) |       1   →       1              |       50.94 ms →       50.84 ms   (-0.18%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       49.73 ms →       49.64 ms   (-0.17%) |       1   →       1              |       49.73 ms →       49.64 ms   (-0.17%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.57 ms →        2.55 ms   (-0.95%) |       2   →       2              |        5.15 ms →        5.10 ms   (-0.95%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        3.88 ms →        3.94 ms   (+1.50%) |       1   →       1              |        3.88 ms →        3.94 ms   (+1.50%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.89 ms →        3.87 ms   (-0.46%) |       1   →       1              |        3.89 ms →        3.87 ms   (-0.46%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      269.79 ms →      269.37 ms   (-0.15%) |       1   →       1              |      269.79 ms →      269.37 ms   (-0.15%) | 
- │ └ sirius::Potential::generate_PAW_effective_potential               |      329.00 ns →      459.00 ns  (+39.51%) |       1   →       1              |      329.00 ns →      459.00 ns  (+39.51%) | 
  ├ sirius::Hamiltonian0                                                |        8.52 ms →        8.11 ms   (-4.76%) |       1   →       1              |        8.52 ms →        8.11 ms   (-4.76%) | 
  │ ├ sirius::Local_operator                                            |        7.40 ms →        7.52 ms   (+1.68%) |       1   →       1              |        7.40 ms →        7.52 ms   (+1.68%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.74 ms →        2.73 ms   (-0.24%) |       1   →       1              |        2.74 ms →        2.73 ms   (-0.24%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        3.84 ms →        3.57 ms   (-6.80%) |       1   →       1              |        3.84 ms →        3.57 ms   (-6.80%) | 
+ │ ├ sirius::Non_local_operator                                        |      426.78 μs →      162.67 μs  (-61.88%) |       2   →       2              |      853.56 μs →      325.34 μs  (-61.88%) | 
  │ ├ sirius::D_operator::initialize                                    |      110.77 μs →      106.20 μs   (-4.12%) |       1   →       1              |      110.77 μs →      106.20 μs   (-4.12%) | 
  │ └ sirius::Q_operator::initialize                                    |       90.29 μs →       90.84 μs   (+0.61%) |       1   →       1              |       90.29 μs →       90.84 μs   (+0.61%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.28 s  →        1.29 s    (+1.22%) |       1   →       1              |        1.28 s  →        1.29 s    (+1.22%) | 
  │ ├ sirius::Hamiltonian_k                                             |       61.94 ms →       61.99 ms   (+0.08%) |       1   →       1              |       61.94 ms →       61.99 ms   (+0.08%) | 
- │ │ ├ sirius::Local_operator::prepare_k                               |      216.09 μs →      252.93 μs  (+17.05%) |       1   →       1              |      216.09 μs →      252.93 μs  (+17.05%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       61.72 ms →       61.73 ms   (+0.02%) |       1   →       1              |       61.72 ms →       61.73 ms   (+0.02%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.22 s  →        1.23 s    (+1.28%) |       1   →       1              |        1.22 s  →        1.23 s    (+1.28%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       75.81 ms →       79.68 ms   (+5.11%) |       4   →       4              |      303.24 ms →      318.73 ms   (+5.11%) | 
- │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       36.91 ms →       47.45 ms  (+28.55%) |       1   →       1              |       36.91 ms →       47.45 ms  (+28.55%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        7.18 ms →        7.42 ms   (+3.34%) |       1   →       1              |        7.18 ms →        7.42 ms   (+3.34%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      335.63 ms →      313.00 ms   (-6.74%) |       1   →       1              |      335.63 ms →      313.00 ms   (-6.74%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      248.28 ms →      245.02 ms   (-1.31%) |       1   →       1              |      248.28 ms →      245.02 ms   (-1.31%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        4.50 μs →        4.04 μs  (-10.24%) |       1   →       1              |        4.50 μs →        4.04 μs  (-10.24%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.33 μs →        3.15 μs   (-5.43%) |       1   →       1              |        3.33 μs →        3.15 μs   (-5.43%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      397.00 ns →      376.00 ns   (-5.29%) |       1   →       1              |      397.00 ns →      376.00 ns   (-5.29%) | 
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      849.00 ns →      708.00 ns  (-16.61%) |       1   →       1              |      849.00 ns →      708.00 ns  (-16.61%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.14 ms →        3.24 ms   (+3.01%) |       1   →       1              |        3.14 ms →        3.24 ms   (+3.01%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.27 ms →       21.28 ms   (+0.05%) |       1   →       1              |       21.27 ms →       21.28 ms   (+0.05%) | 
+ │ │ │ └ sirius::Non_local_operator::apply                             |       31.45 ms →       21.71 ms  (-30.96%) |       2   →       2              |       62.90 ms →       43.43 ms  (-30.96%) | 
- │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.77 ms →       16.28 ms  (+10.23%) |       2   →       2              |       29.54 ms →       32.56 ms  (+10.23%) | 
- │ │ │ └ sddk::wf_inner                                                |       14.56 ms →       16.07 ms  (+10.42%) |       2   →       2              |       29.11 ms →       32.15 ms  (+10.42%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       25.50 ns →       39.00 ns  (+52.94%) |       2   →       2              |       51.00 ns →       78.00 ns  (+52.94%) | 
- │ │ │   ├ sddk::wf_inner|pw                                           |       14.43 ms →       15.95 ms  (+10.50%) |       2   →       2              |       28.86 ms →       31.89 ms  (+10.50%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       27.00 ns →       39.50 ns  (+46.30%) |       2   →       2              |       54.00 ns →       79.00 ns  (+46.30%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      235.66 ms →      250.74 ms   (+6.40%) |       1   →       1              |      235.66 ms →      250.74 ms   (+6.40%) | 
  │ │ └ sddk::wf_trans                                                  |        2.66 ms →        2.61 ms   (-1.98%) |       1   →       1              |        2.66 ms →        2.61 ms   (-1.98%) | 
  │ │   └ sddk::wf_trans|pw                                             |        2.65 ms →        2.60 ms   (-2.03%) |       1   →       1              |        2.65 ms →        2.60 ms   (-2.03%) | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      344.00 ns →      443.00 ns  (+28.78%) |       1   →       1              |      344.00 ns →      443.00 ns  (+28.78%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |       62.24 s  →       61.78 s    (-0.75%) |       1   →       1              |       62.24 s  →       61.78 s    (-0.75%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.45 ms →        2.46 ms   (+0.55%) |      19   →      19              |       46.54 ms →       46.79 ms   (+0.55%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.26 s  →        3.24 s    (-0.73%) |      19   →      19              |       61.99 s  →       61.53 s    (-0.73%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        4.82 ms →        5.05 ms   (+4.59%) |      19   →      19              |       91.67 ms →       95.88 ms   (+4.59%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.15 ms →        4.43 ms   (+6.75%) |      19   →      19              |       78.79 ms →       84.11 ms   (+6.75%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      564.96 μs →      533.82 μs   (-5.51%) |      19   →      19              |       10.73 ms →       10.14 ms   (-5.51%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.55 ms →        2.91 ms  (+13.71%) |      19   →      19              |       48.54 ms →       55.20 ms  (+13.71%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |      186.29 μs →      158.31 μs  (-15.02%) |      38   →      38              |        7.08 ms →        6.02 ms  (-15.02%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |      128.59 μs →      125.77 μs   (-2.19%) |      19   →      19              |        2.44 ms →        2.39 ms   (-2.19%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       95.05 μs →       94.72 μs   (-0.35%) |      19   →      19              |        1.81 ms →        1.80 ms   (-0.35%) | 
  │ │ ├ sirius::Band::solve                                             |        2.04 s  →        2.02 s    (-0.58%) |      19   →      19              |       38.68 s  →       38.46 s    (-0.58%) | 
+ │ │ │ ├ sirius::Hamiltonian_k                                         |      254.63 μs →      202.15 μs  (-20.61%) |      19   →      19              |        4.84 ms →        3.84 ms  (-20.61%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      244.49 μs →      192.28 μs  (-21.35%) |      19   →      19              |        4.65 ms →        3.65 ms  (-21.35%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        7.18 μs →        7.17 μs   (-0.17%) |      19   →      19              |      136.43 μs →      136.20 μs   (-0.17%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.97 s  →        1.94 s    (-1.52%) |      19   →      19              |       37.47 s  →       36.90 s    (-1.52%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       76.32 ms →       70.59 ms   (-7.51%) |      19   →      19              |        1.45 s  →        1.34 s    (-7.51%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.90 ms →        7.90 ms   (+0.03%) |     114   →     114              |      900.44 ms →      900.73 ms   (+0.03%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       18.37 ms →       17.76 ms   (-3.31%) |      19   →      19              |      349.05 ms →      337.51 ms   (-3.31%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      463.75 μs →      454.06 μs   (-2.09%) |      19   →      19              |        8.81 ms →        8.63 ms   (-2.09%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        8.33 ms →        8.02 ms   (-3.71%) |      38   →      38              |      316.51 ms →      304.78 ms   (-3.71%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.87 s  →        1.85 s    (-1.22%) |      19   →      19              |       35.51 s  →       35.08 s    (-1.22%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       50.71 ms →       45.91 ms   (-9.46%) |     356   →     356              |       18.05 s  →       16.35 s    (-9.46%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       28.56 ms →       27.81 ms   (-2.64%) |     356   →     356              |       10.17 s  →        9.90 s    (-2.64%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.04 μs →        1.95 μs   (-4.28%) |     356   →     356              |      726.53 μs →      695.44 μs   (-4.28%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.74 μs →        1.65 μs   (-5.34%) |     356   →     356              |      620.17 μs →      587.08 μs   (-5.34%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      432.73 ns →      411.35 ns   (-4.94%) |     356   →     356              |      154.05 μs →      146.44 μs   (-4.94%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      484.73 ns →      497.45 ns   (+2.62%) |     356   →     356              |      172.56 μs →      177.09 μs   (+2.62%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.83 ms →        2.71 ms   (-3.93%) |     356   →     356              |        1.01 s  →      966.46 ms   (-3.93%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.25 ms →        3.17 ms   (-2.44%) |     356   →     356              |        1.16 s  →        1.13 s    (-2.44%) | 
+ │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        8.03 ms →        6.10 ms  (-23.99%) |     712   →     712              |        5.72 s  →        4.34 s   (-23.99%) | 
+ │ │ │ │   ├ sddk::orthogonalize                                       |        6.65 ms →        5.82 ms  (-12.44%) |     356   →     356              |        2.37 s  →        2.07 s   (-12.44%) | 
+ │ │ │ │   │ ├ sddk::wf_inner                                          |        1.05 ms →      875.51 μs  (-16.67%) |     693   →     693              |      728.09 ms →      606.73 ms  (-16.67%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       72.09 ns →       52.42 ns  (-27.29%) |     693   →     693              |       49.96 μs →       36.32 μs  (-27.29%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |      890.65 μs →      715.68 μs  (-19.65%) |     693   →     693              |      617.22 ms →      495.96 ms  (-19.65%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       43.89 ns →       55.40 ns  (+26.22%) |     693   →     693              |       30.41 μs →       38.39 μs  (+26.22%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      131.57 μs →      139.27 μs   (+5.85%) |     356   →     356              |       46.84 ms →       49.58 ms   (+5.85%) | 
+ │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        2.24 ms →        1.92 ms  (-14.12%) |     356   →     356              |      797.72 ms →      685.09 ms  (-14.12%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |        2.35 ms →        2.16 ms   (-7.95%) |     337   →     337              |      791.42 ms →      728.47 ms   (-7.95%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |      782.01 μs →      719.73 μs   (-7.96%) |    1.01 K →    1.01 K            |      790.61 ms →      727.65 ms   (-7.96%) | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.57 ms →        1.21 ms  (-23.01%) |     356   →     356              |      558.25 ms →      429.81 ms  (-23.01%) | 
+ │ │ │ │   │ └ sddk::wf_inner                                          |        1.49 ms →        1.14 ms  (-23.91%) |     356   →     356              |      531.48 ms →      404.41 ms  (-23.91%) | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       45.58 ns →       42.20 ns   (-7.42%) |     356   →     356              |       16.23 μs →       15.02 μs   (-7.42%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        1.33 ms →      974.88 μs  (-26.75%) |     356   →     356              |      473.82 ms →      347.06 ms  (-26.75%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       38.27 ns →       45.50 ns  (+18.90%) |     356   →     356              |       13.62 μs →       16.20 μs  (+18.90%) | 
- │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       37.23 ms →       42.18 ms  (+13.27%) |     356   →     356              |       13.26 s  →       15.01 s   (+13.27%) | 
  │ │ │ │   ├ sirius::residuals                                         |        2.62 ms →        2.56 ms   (-2.27%) |     340   →     340              |      889.51 ms →      869.30 ms   (-2.27%) | 
- │ │ │ │   │ ├ sddk::wf_trans                                          |        1.28 ms →        1.43 ms  (+11.25%) |     337   →     337              |      431.97 ms →      480.56 ms  (+11.25%) | 
- │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      639.44 μs →      711.52 μs  (+11.27%) |     674   →     674              |      430.98 ms →      479.57 ms  (+11.27%) | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.22 ms →        1.06 ms  (-12.77%) |     337   →     337              |      411.39 ms →      358.84 ms  (-12.77%) | 
+ │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        7.02 ms →        6.28 ms  (-10.58%) |      54   →      54              |      379.15 ms →      339.04 ms  (-10.58%) | 
+ │ │ │ │     └ sddk::wf_trans                                          |        4.21 ms →        3.76 ms  (-10.66%) |      89   →      89              |      374.74 ms →      334.78 ms  (-10.66%) | 
+ │ │ │ │       └ sddk::wf_trans|pw                                     |        3.02 ms →        2.70 ms  (-10.67%) |     124   →     124              |      374.56 ms →      334.60 ms  (-10.67%) | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      333.89 ns →      312.63 ns   (-6.37%) |      19   →      19              |        6.34 μs →        5.94 μs   (-6.37%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       20.12 μs →       20.33 μs   (+1.06%) |      19   →      19              |      382.29 μs →      386.34 μs   (+1.06%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.51 ms →        1.51 ms   (-0.12%) |      19   →      19              |       28.65 ms →       28.62 ms   (-0.12%) | 
  │ │ ├ sirius::Density::generate                                       |      570.66 ms →      563.17 ms   (-1.31%) |      19   →      19              |       10.84 s  →       10.70 s    (-1.31%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      401.80 ms →      401.44 ms   (-0.09%) |      19   →      19              |        7.63 s  →        7.63 s    (-0.09%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        7.72 μs →        7.01 μs   (-9.13%) |      19   →      19              |      146.60 μs →      133.22 μs   (-9.13%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.14 μs →        6.36 μs  (-10.89%) |      19   →      19              |      135.69 μs →      120.92 μs  (-10.89%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       24.03 ms →       21.86 ms   (-9.06%) |      19   →      19              |      456.63 ms →      415.28 ms   (-9.06%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.62 μs →       10.69 μs  (+40.30%) |      19   →      19              |      144.81 μs →      203.17 μs  (+40.30%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        3.18 ms →        3.82 ms  (+20.00%) |      19   →      19              |       60.50 ms →       72.60 ms  (+20.00%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       19.80 ms →       16.96 ms  (-14.34%) |      19   →      19              |      376.19 ms →      322.25 ms  (-14.34%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      538.68 ns →      769.21 ns  (+42.79%) |      19   →      19              |       10.24 μs →       14.62 μs  (+42.79%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      121.97 ms →      123.89 ms   (+1.57%) |      19   →      19              |        2.32 s  →        2.35 s    (+1.57%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.98 ms →        1.93 ms   (-2.27%) |      19   →      19              |       37.56 ms →       36.71 ms   (-2.27%) | 
  │ │ │ │ └ sirius::Density::augment                                    |      213.05 ms →      224.53 ms   (+5.39%) |      19   →      19              |        4.05 s  →        4.27 s    (+5.39%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |      212.83 ms →      224.31 ms   (+5.40%) |      19   →      19              |        4.04 s  →        4.26 s    (+5.40%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      141.15 ms →      132.98 ms   (-5.79%) |      19   →      19              |        2.68 s  →        2.53 s    (-5.79%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      141.15 ms →      132.98 ms   (-5.79%) |      19   →      19              |        2.68 s  →        2.53 s    (-5.79%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       57.19 ms →       51.46 ms  (-10.02%) |      19   →      19              |        1.09 s  →      977.76 ms  (-10.02%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       70.68 ms →       68.25 ms   (-3.45%) |      19   →      19              |        1.34 s  →        1.30 s    (-3.45%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.62 ms →       12.61 ms   (-0.06%) |      19   →      19              |      239.81 ms →      239.67 ms   (-0.06%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.77 ms →       23.56 ms   (-0.91%) |      19   →      19              |      451.71 ms →      447.60 ms   (-0.91%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        3.93 ms →        5.19 ms  (+31.94%) |      19   →      19              |       74.73 ms →       98.60 ms  (+31.94%) | 
  │ │ ├ sirius::Density::mix                                            |      133.74 ms →      131.05 ms   (-2.01%) |      19   →      19              |        2.54 s  →        2.49 s    (-2.01%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      980.28 μs →      743.03 μs  (-24.20%) |      19   →      19              |       18.63 ms →       14.12 ms  (-24.20%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |        4.88 ms →        4.67 ms   (-4.44%) |     229   →     229              |        1.12 s  →        1.07 s    (-4.44%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.82 ms →        4.60 ms   (-4.48%) |     229   →     229              |        1.10 s  →        1.05 s    (-4.48%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.82 ms →        4.60 ms   (-4.47%) |     229   →     229              |        1.10 s  →        1.05 s    (-4.47%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        4.96 ms →        5.32 ms   (+7.28%) |      19   →      19              |       94.17 ms →      101.03 ms   (+7.28%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        4.22 ms →        4.52 ms   (+7.27%) |      19   →      19              |       80.09 ms →       85.91 ms   (+7.27%) | 
  │ │ ├ sirius::Potential::generate                                     |      362.79 ms →      359.22 ms   (-0.98%) |      19   →      19              |        6.89 s  →        6.83 s    (-0.98%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |       42.39 ms →       38.95 ms   (-8.14%) |      19   →      19              |      805.50 ms →      739.96 ms   (-8.14%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       10.90 ms →       11.08 ms   (+1.59%) |      19   →      19              |      207.14 ms →      210.43 ms   (+1.59%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner                             |        5.69 ms →        4.84 ms  (-14.91%) |      19   →      19              |      108.17 ms →       92.04 ms  (-14.91%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.63 ms →        4.82 ms   (+4.10%) |      19   →      19              |       88.01 ms →       91.62 ms   (+4.10%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.63 ms →        4.82 ms   (+4.10%) |      19   →      19              |       87.99 ms →       91.60 ms   (+4.10%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      814.92 μs →      746.14 μs   (-8.44%) |      38   →      38              |       30.97 ms →       28.35 ms   (-8.44%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       44.60 ms →       44.67 ms   (+0.16%) |      19   →      19              |      847.32 ms →      848.64 ms   (+0.16%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       43.41 ms →       43.49 ms   (+0.17%) |      19   →      19              |      824.87 ms →      826.27 ms   (+0.17%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |      689.27 μs →      687.36 μs   (-0.28%) |      38   →      38              |       26.19 ms →       26.12 ms   (-0.28%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.04 ms →        4.17 ms   (+3.23%) |      19   →      19              |       76.69 ms →       79.17 ms   (+3.23%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.85 ms →        3.87 ms   (+0.45%) |      19   →      19              |       73.15 ms →       73.47 ms   (+0.45%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.92 ms →      268.83 ms   (-0.03%) |      19   →      19              |        5.11 s  →        5.11 s    (-0.03%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      303.32 ns →      231.16 ns  (-23.79%) |      19   →      19              |        5.76 μs →        4.39 μs  (-23.79%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |       96.80 ms →       94.33 ms   (-2.55%) |      19   →      19              |        1.84 s  →        1.79 s    (-2.55%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |       96.80 ms →       94.33 ms   (-2.55%) |      19   →      19              |        1.84 s  →        1.79 s    (-2.55%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.57 ms →       13.25 ms   (-2.40%) |      19   →      19              |      257.88 ms →      251.69 ms   (-2.40%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       70.02 ms →       67.87 ms   (-3.07%) |      19   →      19              |        1.33 s  →        1.29 s    (-3.07%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.58 ms →       12.59 ms   (+0.03%) |      19   →      19              |      239.06 ms →      239.12 ms   (+0.03%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.35 ms →        4.14 ms  (+23.47%) |      19   →      19              |       63.65 ms →       78.59 ms  (+23.47%) | 
- │ │ ├ sirius::Periodic_function|inner                                 |        4.73 ms →        5.33 ms  (+12.76%) |     133   →     133              |      628.45 ms →      708.64 ms  (+12.76%) | 
- │ │ │ └ sirius::Periodic_function|inner_local                         |        4.57 ms →        5.14 ms  (+12.58%) |     133   →     133              |      607.35 ms →      683.76 ms  (+12.58%) | 
- │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.57 ms →        5.14 ms  (+12.58%) |     133   →     133              |      607.26 ms →      683.68 ms  (+12.58%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.94 ms →        4.55 ms   (-7.94%) |      57   →      57              |      281.73 ms →      259.36 ms   (-7.94%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.93 ms →        4.54 ms   (-7.99%) |      57   →      57              |      281.24 ms →      258.78 ms   (-7.99%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.54 ms →        4.54 ms   (+0.03%) |      19   →      19              |       86.20 ms →       86.22 ms   (+0.03%) | 
  │ │ └ sirius::Density::get_magnetisation                              |       77.02 μs →       75.82 μs   (-1.55%) |      19   →      19              |        1.46 ms →        1.44 ms   (-1.55%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |       72.11 μs →       70.75 μs   (-1.89%) |      19   →      19              |        1.37 ms →        1.34 ms   (-1.89%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.25 ms →        5.47 ms   (+4.23%) |       2   →       2              |       10.49 ms →       10.94 ms   (+4.23%) | 
- │ ├ sirius::Periodic_function|inner                                   |        4.59 ms →        5.35 ms  (+16.52%) |       6   →       6              |       27.54 ms →       32.09 ms  (+16.52%) | 
- │ │ └ sirius::Periodic_function|inner_local                           |        4.58 ms →        5.34 ms  (+16.58%) |       6   →       6              |       27.48 ms →       32.03 ms  (+16.58%) | 
- │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.58 ms →        5.34 ms  (+16.59%) |       6   →       6              |       27.47 ms →       32.02 ms  (+16.59%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.94 ms →        4.69 ms   (-5.08%) |       3   →       3              |       14.82 ms →       14.06 ms   (-5.08%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.93 ms →        4.68 ms   (-5.22%) |       3   →       3              |       14.80 ms →       14.03 ms   (-5.22%) | 
- ├ sirius::Periodic_function|inner                                     |        4.98 ms →        5.51 ms  (+10.61%) |       2   →       2              |        9.96 ms →       11.02 ms  (+10.61%) | 
- │ └ sirius::Periodic_function|inner_local                             |        4.79 ms →        5.51 ms  (+14.94%) |       2   →       2              |        9.58 ms →       11.02 ms  (+14.94%) | 
- │   └ sirius::Smooth_periodic_function|inner_local                    |        4.79 ms →        5.51 ms  (+14.94%) |       2   →       2              |        9.58 ms →       11.02 ms  (+14.94%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        5.22 ms →        4.92 ms   (-5.79%) |       1   →       1              |        5.22 ms →        4.92 ms   (-5.79%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        5.21 ms →        4.91 ms   (-5.77%) |       1   →       1              |        5.21 ms →        4.91 ms   (-5.77%) | 
  └ sirius::finalize                                                    |      142.38 ms →      139.16 ms   (-2.26%) |       1   →       1              |      142.38 ms →      139.16 ms   (-2.26%) | 
  ====================================================================================================================================================================================================
```
