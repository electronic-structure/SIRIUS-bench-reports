# Benchmark 0c261670dec9b96a58dd74a9134f19b00042d6d1 vs 4e60b1847c4444fb88c162c63a530351544e3d41
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |       72.58 s  →       72.43 s    (-0.21%) |       1   →       1              |       72.58 s  →       72.43 s    (-0.21%) | 
  ├ sirius::initialize                                                  |        2.88 s  →        2.85 s    (-0.84%) |       1   →       1              |        2.88 s  →        2.85 s    (-0.84%) | 
  ├ sirius::Simulation_context::initialize                              |        3.65 s  →        3.93 s    (+7.88%) |       1   →       1              |        3.65 s  →        3.93 s    (+7.88%) | 
- │ ├ sirius::Simulation_context::init_comm                             |      358.24 μs →       37.28 ms (+10306.10%) |       1   →       1              |      358.24 μs →       37.28 ms (+10306.10%) | 
  │ ├ sirius::Unit_cell::initialize                                     |      231.42 ms →      233.74 ms   (+1.00%) |       1   →       1              |      231.42 ms →      233.74 ms   (+1.00%) | 
  │ │ ├ sirius::Atom_type::init                                         |      107.77 ms →      105.93 ms   (-1.71%) |       2   →       2              |      215.53 ms →      211.85 ms   (-1.71%) | 
- │ │ └ sirius::Unit_cell::update                                       |       15.80 ms →       21.79 ms  (+37.90%) |       1   →       1              |       15.80 ms →       21.79 ms  (+37.90%) | 
- │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.61 ms →        9.78 ms (+170.75%) |       1   →       1              |        3.61 ms →        9.78 ms (+170.75%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       12.11 ms →       11.94 ms   (-1.39%) |       1   →       1              |       12.11 ms →       11.94 ms   (-1.39%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       12.04 ms →       11.87 ms   (-1.45%) |       1   →       1              |       12.04 ms →       11.87 ms   (-1.45%) | 
- │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.73 ms →        3.83 ms  (+40.29%) |       1   →       1              |        2.73 ms →        3.83 ms  (+40.29%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      505.12 μs →      475.59 μs   (-5.85%) |       1   →       1              |      505.12 μs →      475.59 μs   (-5.85%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       15.51 μs →       16.02 μs   (+3.28%) |       1   →       1              |       15.51 μs →       16.02 μs   (+3.28%) | 
- │ └ sirius::Simulation_context::update                                |        3.22 s  →        3.61 s   (+12.22%) |       1   →       1              |        3.22 s  →        3.61 s   (+12.22%) | 
  │   ├ sirius::Unit_cell::update                                       |        7.02 ms →        6.97 ms   (-0.72%) |       1   →       1              |        7.02 ms →        6.97 ms   (-0.72%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.65 ms →        3.50 ms   (-4.14%) |       1   →       1              |        3.65 ms →        3.50 ms   (-4.14%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.31 ms →        3.43 ms   (+3.53%) |       1   →       1              |        3.31 ms →        3.43 ms   (+3.53%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.27 ms →        3.38 ms   (+3.45%) |       1   →       1              |        3.27 ms →        3.38 ms   (+3.45%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.73 ms →        2.83 ms   (+3.78%) |       1   →       1              |        2.73 ms →        2.83 ms   (+3.78%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      503.61 μs →      506.11 μs   (+0.50%) |       1   →       1              |      503.61 μs →      506.11 μs   (+0.50%) | 
- │   │     └ sirius::Unit_cell_symmetry|mag                            |       13.97 μs →       20.44 μs  (+46.31%) |       1   →       1              |       13.97 μs →       20.44 μs  (+46.31%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      212.94 ms →      211.96 ms   (-0.46%) |       2   →       2              |      425.87 ms →      423.92 ms   (-0.46%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.17 ms →       15.15 ms   (-0.14%) |       2   →       2              |       30.34 ms →       30.30 ms   (-0.14%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.30 ms →       13.26 ms   (-0.28%) |       1   →       1              |       13.30 ms →       13.26 ms   (-0.28%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.24 ms →       56.37 ms   (+0.23%) |       2   →       2              |      112.49 ms →      112.75 ms   (+0.23%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.04 ms →       45.24 ms   (+0.45%) |       2   →       2              |       90.08 ms →       90.49 ms   (+0.45%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.20 ms →       60.47 ms   (+0.46%) |       4   →       4              |      240.80 ms →      241.89 ms   (+0.46%) | 
  │   ├ sddk::Gvec::init                                                |       92.27 ms →       93.42 ms   (+1.24%) |       2   →       2              |      184.55 ms →      186.83 ms   (+1.24%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       69.04 ms →       69.50 ms   (+0.66%) |       2   →       2              |      138.09 ms →      138.99 ms   (+0.66%) | 
+ │   ├ sddk::Gvec_shells                                               |      115.78 ms →       93.47 ms  (-19.27%) |       1   →       1              |      115.78 ms →       93.47 ms  (-19.27%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.95 ms →        1.98 ms   (+1.34%) |       1   →       1              |        1.95 ms →        1.98 ms   (+1.34%) | 
- │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      460.72 ms →      654.15 ms  (+41.99%) |       2   →       2              |      921.43 ms →        1.31 s   (+41.99%) | 
+ ├ sirius::K_point_set::create_k_mesh                                  |      157.22 ms →       89.48 ms  (-43.09%) |       1   →       1              |      157.22 ms →       89.48 ms  (-43.09%) | 
+ │ ├ sirius::K_point::K_point                                          |        2.66 μs →        1.17 μs  (-56.12%) |       4   →       4              |       10.63 μs →        4.66 μs  (-56.12%) | 
+ │ └ sirius::K_point_set::initialize                                   |      157.14 ms →       89.39 ms  (-43.11%) |       1   →       1              |      157.14 ms →       89.39 ms  (-43.11%) | 
  │   └ sirius::K_point::initialize                                     |       28.61 ms →       28.11 ms   (-1.75%) |       1   →       1              |       28.61 ms →       28.11 ms   (-1.75%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       10.87 ms →       10.76 ms   (-0.98%) |       1   →       1              |       10.87 ms →       10.76 ms   (-0.98%) | 
  │     │ └ sddk::Gvec::init                                            |        4.87 ms →        4.83 ms   (-0.73%) |       1   →       1              |        4.87 ms →        4.83 ms   (-0.73%) | 
+ │     ├ sddk::matrix_storage::matrix_storage                          |       11.07 μs →        7.10 μs  (-35.90%) |       1   →       1              |       11.07 μs →        7.10 μs  (-35.90%) | 
  │     └ sirius::K_point::update                                       |       14.88 ms →       14.48 ms   (-2.72%) |       1   →       1              |       14.88 ms →       14.48 ms   (-2.72%) | 
  │       └ sirius::Beta_projectors                                     |       10.88 ms →       10.50 ms   (-3.55%) |       1   →       1              |       10.88 ms →       10.50 ms   (-3.55%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.90 ms →        8.54 ms   (-4.10%) |       1   →       1              |        8.90 ms →        8.54 ms   (-4.10%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.59 ms →        2.56 ms   (-1.02%) |       2   →       2              |        5.17 ms →        5.12 ms   (-1.02%) | 
  ├ sirius::Potential                                                   |       51.89 ms →       53.29 ms   (+2.70%) |       1   →       1              |       51.89 ms →       53.29 ms   (+2.70%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.91 ms →        2.92 ms   (+0.38%) |       6   →       6              |       17.46 ms →       17.52 ms   (+0.38%) | 
  │ └ sirius::Potential::update                                         |       33.86 ms →       35.22 ms   (+4.04%) |       1   →       1              |       33.86 ms →       35.22 ms   (+4.04%) | 
  │   └ sirius::Potential::generate_local_potential                     |       33.46 ms →       34.79 ms   (+3.96%) |       1   →       1              |       33.46 ms →       34.79 ms   (+3.96%) | 
- │     ├ sirius::Simulation_context::make_periodic_function            |       26.65 ms →       30.41 ms  (+14.11%) |       1   →       1              |       26.65 ms →       30.41 ms  (+14.11%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        6.25 ms →        3.80 ms  (-39.21%) |       1   →       1              |        6.25 ms →        3.80 ms  (-39.21%) | 
  ├ sirius::Density                                                     |       40.92 ms →       40.69 ms   (-0.56%) |       1   →       1              |       40.92 ms →       40.69 ms   (-0.56%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.81 ms →        2.83 ms   (+0.86%) |       2   →       2              |        5.62 ms →        5.67 ms   (+0.86%) | 
  │ └ sirius::Density::update                                           |       35.16 ms →       34.88 ms   (-0.79%) |       1   →       1              |       35.16 ms →       34.88 ms   (-0.79%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       34.92 ms →       34.61 ms   (-0.89%) |       1   →       1              |       34.92 ms →       34.61 ms   (-0.89%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |       77.61 μs →       81.90 μs   (+5.52%) |       1   →       1              |       77.61 μs →       81.90 μs   (+5.52%) | 
- │     ├ sirius::Simulation_context::make_periodic_function            |       26.59 ms →       30.57 ms  (+14.97%) |       1   →       1              |       26.59 ms →       30.57 ms  (+14.97%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        7.95 ms →        3.61 ms  (-54.57%) |       1   →       1              |        7.95 ms →        3.61 ms  (-54.57%) | 
  ├ sirius::Density::initial_density                                    |       59.39 ms →       63.29 ms   (+6.58%) |       1   →       1              |       59.39 ms →       63.29 ms   (+6.58%) | 
- │ ├ sirius::Simulation_context::make_periodic_function                |       27.71 ms →       35.40 ms  (+27.75%) |       1   →       1              |       27.71 ms →       35.40 ms  (+27.75%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        6.16 ms →        4.96 ms  (-19.52%) |       2   →       2              |       12.33 ms →        9.92 ms  (-19.52%) | 
+ │ └ sirius::Periodic_function::integrate                              |        5.82 ms →        4.54 ms  (-21.96%) |       1   →       1              |        5.82 ms →        4.54 ms  (-21.96%) | 
  ├ sirius::Potential::generate                                         |      367.44 ms →      368.65 ms   (+0.33%) |       1   →       1              |      367.44 ms →      368.65 ms   (+0.33%) | 
  │ ├ sirius::Potential::poisson                                        |       40.39 ms →       41.47 ms   (+2.69%) |       1   →       1              |       40.39 ms →       41.47 ms   (+2.69%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        9.23 ms →        3.66 ms  (-60.34%) |       1   →       1              |        9.23 ms →        3.66 ms  (-60.34%) | 
+ │ │ └ sirius::Periodic_function|inner                                 |        5.41 ms →        4.63 ms  (-14.35%) |       1   →       1              |        5.41 ms →        4.63 ms  (-14.35%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.64 ms →        4.62 ms   (-0.43%) |       1   →       1              |        4.64 ms →        4.62 ms   (-0.43%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.64 ms →        4.62 ms   (-0.43%) |       1   →       1              |        4.64 ms →        4.62 ms   (-0.43%) | 
  │ ├ sirius::Periodic_function::add                                    |      808.30 μs →      787.15 μs   (-2.62%) |       2   →       2              |        1.62 ms →        1.57 ms   (-2.62%) | 
  │ ├ sirius::Potential::xc                                             |       50.83 ms →       51.70 ms   (+1.71%) |       1   →       1              |       50.83 ms →       51.70 ms   (+1.71%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       49.68 ms →       50.52 ms   (+1.69%) |       1   →       1              |       49.68 ms →       50.52 ms   (+1.69%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.54 ms →        2.58 ms   (+1.68%) |       2   →       2              |        5.08 ms →        5.17 ms   (+1.68%) | 
- │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.12 ms →        4.72 ms  (+14.61%) |       1   →       1              |        4.12 ms →        4.72 ms  (+14.61%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.79 ms →        3.74 ms   (-1.50%) |       1   →       1              |        3.79 ms →        3.74 ms   (-1.50%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      269.45 ms →      268.75 ms   (-0.26%) |       1   →       1              |      269.45 ms →      268.75 ms   (-0.26%) | 
- │ └ sirius::Potential::generate_PAW_effective_potential               |      149.00 ns →      328.00 ns (+120.13%) |       1   →       1              |      149.00 ns →      328.00 ns (+120.13%) | 
  ├ sirius::Hamiltonian0                                                |        6.82 ms →        6.39 ms   (-6.35%) |       1   →       1              |        6.82 ms →        6.39 ms   (-6.35%) | 
  │ ├ sirius::Local_operator                                            |        6.37 ms →        5.87 ms   (-7.73%) |       1   →       1              |        6.37 ms →        5.87 ms   (-7.73%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.73 ms →        2.75 ms   (+0.75%) |       1   →       1              |        2.73 ms →        2.75 ms   (+0.75%) | 
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.85 ms →        2.37 ms  (-16.80%) |       1   →       1              |        2.85 ms →        2.37 ms  (-16.80%) | 
  │ ├ sirius::Non_local_operator                                        |       72.78 μs →       76.01 μs   (+4.44%) |       2   →       2              |      145.55 μs →      152.02 μs   (+4.44%) | 
- │ ├ sirius::D_operator::initialize                                    |      135.34 μs →      151.27 μs  (+11.77%) |       1   →       1              |      135.34 μs →      151.27 μs  (+11.77%) | 
- │ └ sirius::Q_operator::initialize                                    |      100.52 μs →      122.02 μs  (+21.40%) |       1   →       1              |      100.52 μs →      122.02 μs  (+21.40%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.30 s  →        1.29 s    (-0.60%) |       1   →       1              |        1.30 s  →        1.29 s    (-0.60%) | 
  │ ├ sirius::Hamiltonian_k                                             |       47.99 ms →       46.80 ms   (-2.47%) |       1   →       1              |       47.99 ms →       46.80 ms   (-2.47%) | 
- │ │ ├ sirius::Local_operator::prepare_k                               |      304.72 μs →      345.04 μs  (+13.23%) |       1   →       1              |      304.72 μs →      345.04 μs  (+13.23%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       47.68 ms →       46.45 ms   (-2.57%) |       1   →       1              |       47.68 ms →       46.45 ms   (-2.57%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.25 s  →        1.25 s    (-0.53%) |       1   →       1              |        1.25 s  →        1.25 s    (-0.53%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       81.18 ms →       79.32 ms   (-2.28%) |       4   →       4              |      324.70 ms →      317.29 ms   (-2.28%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       48.24 ms →       44.71 ms   (-7.32%) |       1   →       1              |       48.24 ms →       44.71 ms   (-7.32%) | 
- │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        7.43 ms →        8.77 ms  (+18.06%) |       1   →       1              |        7.43 ms →        8.77 ms  (+18.06%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      335.65 ms →      336.41 ms   (+0.23%) |       1   →       1              |      335.65 ms →      336.41 ms   (+0.23%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      247.59 ms →      248.83 ms   (+0.50%) |       1   →       1              |      247.59 ms →      248.83 ms   (+0.50%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.76 μs →        3.77 μs   (+0.27%) |       1   →       1              |        3.76 μs →        3.77 μs   (+0.27%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.83 μs →        2.89 μs   (+2.19%) |       1   →       1              |        2.83 μs →        2.89 μs   (+2.19%) | 
+ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      643.00 ns →      437.00 ns  (-32.04%) |       1   →       1              |      643.00 ns →      437.00 ns  (-32.04%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      598.00 ns →      638.00 ns   (+6.69%) |       1   →       1              |      598.00 ns →      638.00 ns   (+6.69%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.17 ms →        3.15 ms   (-0.82%) |       1   →       1              |        3.17 ms →        3.15 ms   (-0.82%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.29 ms →       21.25 ms   (-0.18%) |       1   →       1              |       21.29 ms →       21.25 ms   (-0.18%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       31.78 ms →       31.57 ms   (-0.64%) |       2   →       2              |       63.55 ms →       63.14 ms   (-0.64%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.82 ms →       14.99 ms   (+1.14%) |       2   →       2              |       29.64 ms →       29.98 ms   (+1.14%) | 
  │ │ │ └ sddk::wf_inner                                                |       14.61 ms →       14.78 ms   (+1.17%) |       2   →       2              |       29.22 ms →       29.56 ms   (+1.17%) | 
+ │ │ │   ├ sddk::wf_inner|scale                                        |       38.00 ns →       23.50 ns  (-38.16%) |       2   →       2              |       76.00 ns →       47.00 ns  (-38.16%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       14.49 ms →       14.65 ms   (+1.12%) |       2   →       2              |       28.97 ms →       29.30 ms   (+1.12%) | 
+ │ │ │   └ sddk::wf_inner|scale_back                                   |       23.00 ns →       20.50 ns  (-10.87%) |       2   →       2              |       46.00 ns →       41.00 ns  (-10.87%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      237.89 ms →      238.81 ms   (+0.39%) |       1   →       1              |      237.89 ms →      238.81 ms   (+0.39%) | 
  │ │ └ sddk::wf_trans                                                  |        4.97 ms →        5.01 ms   (+0.73%) |       1   →       1              |        4.97 ms →        5.01 ms   (+0.73%) | 
  │ │   └ sddk::wf_trans|pw                                             |        4.97 ms →        5.00 ms   (+0.73%) |       1   →       1              |        4.97 ms →        5.00 ms   (+0.73%) | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      393.00 ns →      538.00 ns  (+36.90%) |       1   →       1              |      393.00 ns →      538.00 ns  (+36.90%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |       62.96 s  →       62.58 s    (-0.59%) |       1   →       1              |       62.96 s  →       62.58 s    (-0.59%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.44 ms →        2.46 ms   (+0.48%) |      19   →      19              |       46.44 ms →       46.66 ms   (+0.48%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        2.99 s  →        2.95 s    (-1.15%) |      21   →      21              |       62.70 s  →       61.98 s    (-1.15%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        5.28 ms →        5.23 ms   (-1.03%) |      21   →      21              |      110.97 ms →      109.83 ms   (-1.03%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.52 ms →        4.48 ms   (-0.85%) |      21   →      21              |       94.86 ms →       94.06 ms   (-0.85%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      533.50 μs →      550.51 μs   (+3.19%) |      21   →      21              |       11.20 ms →       11.56 ms   (+3.19%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.83 ms →        2.79 ms   (-1.45%) |      21   →      21              |       59.43 ms →       58.56 ms   (-1.45%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |      246.16 μs →      231.69 μs   (-5.88%) |      42   →      42              |       10.34 ms →        9.73 ms   (-5.88%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |      109.90 μs →      118.30 μs   (+7.64%) |      21   →      21              |        2.31 ms →        2.48 ms   (+7.64%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       87.32 μs →       89.04 μs   (+1.97%) |      21   →      21              |        1.83 ms →        1.87 ms   (+1.97%) | 
  │ │ ├ sirius::Band::solve                                             |        1.76 s  →        1.75 s    (-0.39%) |      21   →      21              |       36.92 s  →       36.78 s    (-0.39%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      197.30 μs →      194.90 μs   (-1.22%) |      21   →      21              |        4.14 ms →        4.09 ms   (-1.22%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      188.40 μs →      183.62 μs   (-2.54%) |      21   →      21              |        3.96 ms →        3.86 ms   (-2.54%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        6.55 μs →        8.51 μs  (+29.83%) |      21   →      21              |      137.60 μs →      178.65 μs  (+29.83%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.64 s  →        1.63 s    (-0.17%) |      21   →      21              |       34.35 s  →       34.29 s    (-0.17%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       72.33 ms →       74.14 ms   (+2.49%) |      21   →      21              |        1.52 s  →        1.56 s    (+2.49%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.24 ms →        7.51 ms   (+3.65%) |     126   →     126              |      912.37 ms →      945.72 ms   (+3.65%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       18.03 ms →       15.77 ms  (-12.55%) |      21   →      21              |      378.68 ms →      331.17 ms  (-12.55%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      455.02 μs →      478.44 μs   (+5.15%) |      21   →      21              |        9.56 ms →       10.05 ms   (+5.15%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        8.14 ms →        7.21 ms  (-11.38%) |      42   →      42              |      341.68 ms →      302.80 ms  (-11.38%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.54 s  →        1.53 s    (-0.21%) |      21   →      21              |       32.28 s  →       32.21 s    (-0.21%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       55.45 ms →       60.00 ms   (+8.20%) |     361   →     361              |       20.02 s  →       21.66 s    (+8.20%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       31.06 ms →       37.17 ms  (+19.67%) |     361   →     361              |       11.21 s  →       13.42 s   (+19.67%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.07 μs →        1.96 μs   (-5.02%) |     361   →     361              |      745.90 μs →      708.45 μs   (-5.02%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.69 μs →        1.67 μs   (-1.40%) |     361   →     361              |      610.04 μs →      601.52 μs   (-1.40%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      456.42 ns →      386.27 ns  (-15.37%) |     361   →     361              |      164.77 μs →      139.44 μs  (-15.37%) | 
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      650.36 ns →      551.81 ns  (-15.15%) |     361   →     361              |      234.78 μs →      199.20 μs  (-15.15%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.82 ms →        3.15 ms  (+11.59%) |     361   →     361              |        1.02 s  →        1.14 s   (+11.59%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.26 ms →        3.38 ms   (+3.82%) |     361   →     361              |        1.18 s  →        1.22 s    (+3.82%) | 
+ │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        9.15 ms →        8.15 ms  (-10.99%) |     722   →     722              |        6.61 s  →        5.88 s   (-10.99%) | 
+ │ │ │ │   ├ sddk::orthogonalize                                       |        7.31 ms →        6.19 ms  (-15.37%) |     361   →     361              |        2.64 s  →        2.23 s   (-15.37%) | 
+ │ │ │ │   │ ├ sddk::wf_inner                                          |        1.32 ms →        1.13 ms  (-14.54%) |     701   →     701              |      928.63 ms →      793.62 ms  (-14.54%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       49.98 ns →       40.41 ns  (-19.14%) |     701   →     701              |       35.03 μs →       28.33 μs  (-19.14%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        1.16 ms →      967.55 μs  (-16.78%) |     701   →     701              |      814.96 ms →      678.25 ms  (-16.78%) | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       50.71 ns →       47.44 ns   (-6.45%) |     701   →     701              |       35.55 μs →       33.26 μs   (-6.45%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      261.77 μs →      279.55 μs   (+6.79%) |     361   →     361              |       94.50 ms →      100.92 ms   (+6.79%) | 
+ │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        2.28 ms →        1.57 ms  (-31.44%) |     361   →     361              |      824.11 ms →      564.99 ms  (-31.44%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |        2.33 ms →        2.27 ms   (-2.27%) |     340   →     340              |      790.98 ms →      773.06 ms   (-2.27%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |      774.63 μs →      757.15 μs   (-2.26%) |    1.02 K →    1.02 K            |      790.12 ms →      772.29 ms   (-2.26%) | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.53 ms →        1.13 ms  (-26.16%) |     361   →     361              |      550.84 ms →      406.72 ms  (-26.16%) | 
+ │ │ │ │   │ └ sddk::wf_inner                                          |        1.48 ms →        1.08 ms  (-26.86%) |     361   →     361              |      534.33 ms →      390.81 ms  (-26.86%) | 
- │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       47.74 ns →       71.13 ns  (+48.98%) |     361   →     361              |       17.23 μs →       25.68 μs  (+48.98%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        1.31 ms →      918.00 μs  (-30.15%) |     361   →     361              |      474.43 ms →      331.40 ms  (-30.15%) | 
+ │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       54.38 ns →       22.12 ns  (-59.32%) |     361   →     361              |       19.63 μs →        7.98 μs  (-59.32%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       20.95 ms →       18.29 ms  (-12.72%) |     361   →     361              |        7.56 s  →        6.60 s   (-12.72%) | 
+ │ │ │ │   ├ sirius::residuals                                         |        2.97 ms →        2.58 ms  (-13.23%) |     346   →     346              |        1.03 s  →      891.48 ms  (-13.23%) | 
+ │ │ │ │   │ ├ sddk::wf_trans                                          |        1.42 ms →        1.18 ms  (-17.17%) |     342   →     342              |      485.84 ms →      402.41 ms  (-17.17%) | 
+ │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      708.82 μs →      586.94 μs  (-17.19%) |     684   →     684              |      484.83 ms →      401.47 ms  (-17.19%) | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.45 ms →        1.30 ms  (-10.16%) |     342   →     342              |      495.12 ms →      444.82 ms  (-10.16%) | 
+ │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        5.25 ms →        4.58 ms  (-12.84%) |      90   →      90              |      472.70 ms →      412.01 ms  (-12.84%) | 
+ │ │ │ │     └ sddk::wf_trans                                          |        2.92 ms →        2.54 ms  (-13.06%) |     159   →     159              |      464.37 ms →      403.73 ms  (-13.06%) | 
+ │ │ │ │       └ sddk::wf_trans|pw                                     |        2.04 ms →        1.77 ms  (-13.07%) |     228   →     228              |      464.05 ms →      403.41 ms  (-13.07%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      515.90 ns →      353.43 ns  (-31.49%) |      21   →      21              |       10.83 μs →        7.42 μs  (-31.49%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       20.06 μs →       19.73 μs   (-1.62%) |      21   →      21              |      421.22 μs →      414.40 μs   (-1.62%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.53 ms →        1.56 ms   (+2.22%) |      21   →      21              |       32.05 ms →       32.76 ms   (+2.22%) | 
  │ │ ├ sirius::Density::generate                                       |      570.82 ms →      563.35 ms   (-1.31%) |      21   →      21              |       11.99 s  →       11.83 s    (-1.31%) | 
+ │ │ │ ├ sirius::Density::generate_valence                             |      409.00 ms →      361.52 ms  (-11.61%) |      21   →      21              |        8.59 s  →        7.59 s   (-11.61%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        7.43 μs →       10.58 μs  (+42.43%) |      21   →      21              |      156.04 μs →      222.25 μs  (+42.43%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        6.79 μs →        9.71 μs  (+43.00%) |      21   →      21              |      142.63 μs →      203.96 μs  (+43.00%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       25.43 ms →       44.07 ms  (+73.28%) |      21   →      21              |      534.04 ms →      925.38 ms  (+73.28%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       11.22 μs →       10.74 μs   (-4.27%) |      21   →      21              |      235.64 μs →      225.58 μs   (-4.27%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        3.55 ms →       23.62 ms (+565.00%) |      21   →      21              |       74.59 ms →      496.05 ms (+565.00%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       20.82 ms →       19.36 ms   (-7.00%) |      21   →      21              |      437.26 ms →      406.63 ms   (-7.00%) | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      752.14 ns →      703.19 ns   (-6.51%) |      21   →      21              |       15.79 μs →       14.77 μs   (-6.51%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      120.67 ms →       95.33 ms  (-21.00%) |      21   →      21              |        2.53 s  →        2.00 s   (-21.00%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.90 ms →        1.74 ms   (-8.73%) |      21   →      21              |       39.94 ms →       36.45 ms   (-8.73%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |      224.86 ms →      180.43 ms  (-19.76%) |      21   →      21              |        4.72 s  →        3.79 s   (-19.76%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |      224.64 ms →      180.20 ms  (-19.78%) |      21   →      21              |        4.72 s  →        3.78 s   (-19.78%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      134.51 ms →      173.46 ms  (+28.96%) |      21   →      21              |        2.82 s  →        3.64 s   (+28.96%) | 
- │ │ │ │ └ sirius::symmetrize_function|fpw                             |      134.50 ms →      173.46 ms  (+28.96%) |      21   →      21              |        2.82 s  →        3.64 s   (+28.96%) | 
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       49.36 ms →       90.51 ms  (+83.38%) |      21   →      21              |        1.04 s  →        1.90 s   (+83.38%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       71.91 ms →       69.63 ms   (-3.17%) |      21   →      21              |        1.51 s  →        1.46 s    (-3.17%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.58 ms →       12.67 ms   (+0.68%) |      21   →      21              |      264.26 ms →      266.07 ms   (+0.68%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.52 ms →       23.60 ms   (+0.34%) |      21   →      21              |      493.99 ms →      495.66 ms   (+0.34%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        3.79 ms →        4.77 ms  (+25.89%) |      21   →      21              |       79.53 ms →      100.12 ms  (+25.89%) | 
+ │ │ ├ sirius::Density::mix                                            |      134.75 ms →      115.62 ms  (-14.20%) |      21   →      21              |        2.83 s  →        2.43 s   (-14.20%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      754.02 μs →      636.96 μs  (-15.52%) |      21   →      21              |       15.83 ms →       13.38 ms  (-15.52%) | 
- │ │ │ ├ sirius::Periodic_function|inner                               |        4.73 ms →        4.67 ms   (-1.26%) |     259   →     358    (+38.22%) |        1.22 s  →        1.67 s   (+36.48%) | 
- │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.62 ms →        4.61 ms   (-0.05%) |     259   →     358    (+38.22%) |        1.20 s  →        1.65 s   (+38.16%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.62 ms →        4.61 ms   (-0.04%) |     259   →     358    (+38.22%) |        1.20 s  →        1.65 s   (+38.16%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        5.00 ms →        5.95 ms  (+19.00%) |      21   →      21              |      104.93 ms →      124.86 ms  (+19.00%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        4.32 ms →        5.03 ms  (+16.54%) |      21   →      21              |       90.64 ms →      105.63 ms  (+16.54%) | 
  │ │ ├ sirius::Potential::generate                                     |      360.14 ms →      361.70 ms   (+0.43%) |      21   →      21              |        7.56 s  →        7.60 s    (+0.43%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |       39.58 ms →       41.44 ms   (+4.71%) |      21   →      21              |      831.12 ms →      870.25 ms   (+4.71%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        8.68 ms →        3.65 ms  (-57.99%) |      21   →      21              |      182.31 ms →       76.59 ms  (-57.99%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner                             |        5.39 ms →        4.63 ms  (-14.10%) |      21   →      21              |      113.16 ms →       97.20 ms  (-14.10%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.63 ms →        4.62 ms   (-0.21%) |      21   →      21              |       97.29 ms →       97.09 ms   (-0.21%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.63 ms →        4.62 ms   (-0.21%) |      21   →      21              |       97.27 ms →       97.07 ms   (-0.21%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      826.52 μs →      768.86 μs   (-6.98%) |      42   →      42              |       34.71 ms →       32.29 ms   (-6.98%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       44.63 ms →       45.01 ms   (+0.85%) |      21   →      21              |      937.24 ms →      945.20 ms   (+0.85%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       43.46 ms →       43.83 ms   (+0.84%) |      21   →      21              |      912.76 ms →      920.44 ms   (+0.84%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |      670.61 μs →      690.19 μs   (+2.92%) |      42   →      42              |       28.17 ms →       28.99 ms   (+2.92%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.08 ms →        4.60 ms  (+12.92%) |      21   →      21              |       85.59 ms →       96.66 ms  (+12.92%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.89 ms →        3.70 ms   (-4.92%) |      21   →      21              |       81.74 ms →       77.72 ms   (-4.92%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      269.00 ms →      268.57 ms   (-0.16%) |      21   →      21              |        5.65 s  →        5.64 s    (-0.16%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      202.81 ns →      316.62 ns  (+56.12%) |      21   →      21              |        4.26 μs →        6.65 μs  (+56.12%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |       98.24 ms →       96.00 ms   (-2.29%) |      21   →      21              |        2.06 s  →        2.02 s    (-2.29%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |       98.24 ms →       95.99 ms   (-2.29%) |      21   →      21              |        2.06 s  →        2.02 s    (-2.29%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.29 ms →       13.32 ms   (+0.18%) |      21   →      21              |      279.13 ms →      279.63 ms   (+0.18%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       71.75 ms →       69.47 ms   (-3.17%) |      21   →      21              |        1.51 s  →        1.46 s    (-3.17%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.57 ms →       12.58 ms   (+0.08%) |      21   →      21              |      263.92 ms →      264.13 ms   (+0.08%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.88 ms →        4.60 ms  (+18.61%) |      21   →      21              |       81.53 ms →       96.70 ms  (+18.61%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.93 ms →        4.77 ms   (-3.20%) |     147   →     147              |      724.33 ms →      701.17 ms   (-3.20%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.79 ms →        4.75 ms   (-0.75%) |     147   →     147              |      703.42 ms →      698.13 ms   (-0.75%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.78 ms →        4.75 ms   (-0.76%) |     147   →     147              |      703.35 ms →      698.03 ms   (-0.76%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.56 ms →        4.59 ms   (+0.85%) |      63   →      63              |      287.01 ms →      289.45 ms   (+0.85%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.54 ms →        4.58 ms   (+0.85%) |      63   →      63              |      286.01 ms →      288.44 ms   (+0.85%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.53 ms →        4.55 ms   (+0.53%) |      21   →      21              |       95.03 ms →       95.53 ms   (+0.53%) | 
  │ │ └ sirius::Density::get_magnetisation                              |       76.26 μs →       76.63 μs   (+0.48%) |      21   →      21              |        1.60 ms →        1.61 ms   (+0.48%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |       71.28 μs →       71.33 μs   (+0.07%) |      21   →      21              |        1.50 ms →        1.50 ms   (+0.07%) | 
+ │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.66 ms →        5.09 ms  (-10.08%) |       2   →       2              |       11.31 ms →       10.17 ms  (-10.08%) | 
  │ ├ sirius::Periodic_function|inner                                   |        5.01 ms →        5.00 ms   (-0.08%) |       6   →       6              |       30.04 ms →       30.02 ms   (-0.08%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        5.00 ms →        5.00 ms   (-0.08%) |       6   →       6              |       30.02 ms →       30.00 ms   (-0.08%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        5.00 ms →        5.00 ms   (-0.09%) |       6   →       6              |       30.02 ms →       29.99 ms   (-0.09%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.79 ms →        4.79 ms   (-0.01%) |       3   →       3              |       14.36 ms →       14.36 ms   (-0.01%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.78 ms →        4.78 ms   (+0.04%) |       3   →       3              |       14.34 ms →       14.35 ms   (+0.04%) | 
  ├ sirius::Periodic_function|inner                                     |        4.75 ms →        4.96 ms   (+4.41%) |       2   →       2              |        9.50 ms →        9.92 ms   (+4.41%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.74 ms →        4.96 ms   (+4.53%) |       2   →       2              |        9.48 ms →        9.91 ms   (+4.53%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.74 ms →        4.95 ms   (+4.53%) |       2   →       2              |        9.48 ms →        9.91 ms   (+4.53%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.54 ms →        4.78 ms   (+5.43%) |       1   →       1              |        4.54 ms →        4.78 ms   (+5.43%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.52 ms →        4.78 ms   (+5.77%) |       1   →       1              |        4.52 ms →        4.78 ms   (+5.77%) | 
+ └ sirius::finalize                                                    |      431.86 ms →      166.43 ms  (-61.46%) |       1   →       1              |      431.86 ms →      166.43 ms  (-61.46%) | 
  ====================================================================================================================================================================================================
```
