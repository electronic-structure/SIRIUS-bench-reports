# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      133.86 s  →      134.46 s    (+0.45%) |       1   →       1              |      133.86 s  →      134.46 s    (+0.45%) | 
  ├ sirius::initialize                                                  |        2.72 s  →        2.82 s    (+3.80%) |       1   →       1              |        2.72 s  →        2.82 s    (+3.80%) | 
  ├ sirius::Simulation_context::initialize                              |        3.03 s  →        2.93 s    (-3.35%) |       1   →       1              |        3.03 s  →        2.93 s    (-3.35%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       44.97 ms →      257.86 μs  (-99.43%) |       1   →       1              |       44.97 ms →      257.86 μs  (-99.43%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      189.71 ms →      154.03 ms  (-18.81%) |       1   →       1              |      189.71 ms →      154.03 ms  (-18.81%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       82.75 ms →       64.69 ms  (-21.82%) |       2   →       2              |      165.50 ms →      129.39 ms  (-21.82%) | 
  │ │ └ sirius::Unit_cell::update                                       |       24.14 ms →       24.56 ms   (+1.77%) |       1   →       1              |       24.14 ms →       24.56 ms   (+1.77%) | 
- │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        5.57 ms →        6.37 ms  (+14.26%) |       1   →       1              |        5.57 ms →        6.37 ms  (+14.26%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       18.52 ms →       18.15 ms   (-2.03%) |       1   →       1              |       18.52 ms →       18.15 ms   (-2.03%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       18.50 ms →       18.13 ms   (-2.02%) |       1   →       1              |       18.50 ms →       18.13 ms   (-2.02%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.16 ms →        4.14 ms   (-0.36%) |       1   →       1              |        4.16 ms →        4.14 ms   (-0.36%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.34 ms   (+0.77%) |       1   →       1              |        2.33 ms →        2.34 ms   (+0.77%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      101.69 μs →      100.45 μs   (-1.22%) |       1   →       1              |      101.69 μs →      100.45 μs   (-1.22%) | 
  │ └ sirius::Simulation_context::update                                |        2.75 s  →        2.73 s    (-0.72%) |       1   →       1              |        2.75 s  →        2.73 s    (-0.72%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.89 ms →       10.80 ms   (-0.78%) |       1   →       1              |       10.89 ms →       10.80 ms   (-0.78%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.43 ms →        4.44 ms   (+0.28%) |       1   →       1              |        4.43 ms →        4.44 ms   (+0.28%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.42 ms →        6.32 ms   (-1.50%) |       1   →       1              |        6.42 ms →        6.32 ms   (-1.50%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.40 ms →        6.31 ms   (-1.49%) |       1   →       1              |        6.40 ms →        6.31 ms   (-1.49%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.90 ms →        3.81 ms   (-2.14%) |       1   →       1              |        3.90 ms →        3.81 ms   (-2.14%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.34 ms →        2.33 ms   (-0.41%) |       1   →       1              |        2.34 ms →        2.33 ms   (-0.41%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      100.99 μs →       99.45 μs   (-1.53%) |       1   →       1              |      100.99 μs →       99.45 μs   (-1.53%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       72.37 ms →       66.85 ms   (-7.62%) |       2   →       2              |      144.74 ms →      133.70 ms   (-7.62%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        6.51 ms →        5.94 ms   (-8.75%) |       2   →       2              |       13.03 ms →       11.89 ms   (-8.75%) | 
- │   ├ sirius::Radial_integrals|rho_pseudo                             |        5.41 ms →        6.03 ms  (+11.54%) |       1   →       1              |        5.41 ms →        6.03 ms  (+11.54%) | 
+ │   ├ sirius::Radial_integrals|vloc                                   |       25.45 ms →       22.73 ms  (-10.66%) |       2   →       2              |       50.89 ms →       45.47 ms  (-10.66%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       15.34 ms →       14.84 ms   (-3.26%) |       2   →       2              |       30.68 ms →       29.68 ms   (-3.26%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.67 ms →       19.80 ms   (+0.66%) |       4   →       4              |       78.67 ms →       79.19 ms   (+0.66%) | 
  │   ├ sddk::Gvec::init                                                |      173.62 ms →      171.90 ms   (-0.99%) |       2   →       2              |      347.25 ms →      343.80 ms   (-0.99%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      131.04 ms →      129.55 ms   (-1.14%) |       2   →       2              |      262.08 ms →      259.10 ms   (-1.14%) | 
- │   ├ sddk::Gvec_shells                                               |      162.25 ms →      181.27 ms  (+11.72%) |       1   →       1              |      162.25 ms →      181.27 ms  (+11.72%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.32 ms →        1.32 ms   (-0.38%) |       1   →       1              |        1.32 ms →        1.32 ms   (-0.38%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      291.18 ms →      295.69 ms   (+1.55%) |       2   →       2              |      582.36 ms →      591.38 ms   (+1.55%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       36.05 ms →       35.46 ms   (-1.66%) |       1   →       1              |       36.05 ms →       35.46 ms   (-1.66%) | 
- │ ├ sirius::K_point::K_point                                          |        2.24 μs →        2.56 μs  (+14.07%) |       4   →       4              |        8.98 μs →       10.24 μs  (+14.07%) | 
  │ └ sirius::K_point_set::initialize                                   |       35.95 ms →       35.36 ms   (-1.66%) |       1   →       1              |       35.95 ms →       35.36 ms   (-1.66%) | 
  │   └ sirius::K_point::initialize                                     |       35.86 ms →       35.26 ms   (-1.69%) |       1   →       1              |       35.86 ms →       35.26 ms   (-1.69%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       18.12 ms →       18.01 ms   (-0.63%) |       1   →       1              |       18.12 ms →       18.01 ms   (-0.63%) | 
  │     │ └ sddk::Gvec::init                                            |        8.10 ms →        8.09 ms   (-0.09%) |       1   →       1              |        8.10 ms →        8.09 ms   (-0.09%) | 
+ │     ├ sddk::matrix_storage::matrix_storage                          |       10.88 μs →        9.21 μs  (-15.32%) |       1   →       1              |       10.88 μs →        9.21 μs  (-15.32%) | 
  │     └ sirius::K_point::update                                       |       12.70 ms →       12.46 ms   (-1.85%) |       1   →       1              |       12.70 ms →       12.46 ms   (-1.85%) | 
  │       └ sirius::Beta_projectors                                     |        6.29 ms →        6.19 ms   (-1.57%) |       1   →       1              |        6.29 ms →        6.19 ms   (-1.57%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.69 ms →        3.61 ms   (-2.28%) |       1   →       1              |        3.69 ms →        3.61 ms   (-2.28%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.23 ms →        5.42 ms   (+3.56%) |       2   →       2              |       10.46 ms →       10.83 ms   (+3.56%) | 
  ├ sirius::Potential                                                   |      159.74 ms →      157.98 ms   (-1.10%) |       1   →       1              |      159.74 ms →      157.98 ms   (-1.10%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.92 ms →        5.83 ms   (-1.53%) |       6   →       6              |       35.52 ms →       34.97 ms   (-1.53%) | 
  │ └ sirius::Potential::update                                         |      123.48 ms →      122.28 ms   (-0.98%) |       1   →       1              |      123.48 ms →      122.28 ms   (-0.98%) | 
  │   └ sirius::Potential::generate_local_potential                     |      122.71 ms →      121.56 ms   (-0.93%) |       1   →       1              |      122.71 ms →      121.56 ms   (-0.93%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      115.35 ms →      114.37 ms   (-0.85%) |       1   →       1              |      115.35 ms →      114.37 ms   (-0.85%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        6.47 ms →        6.31 ms   (-2.49%) |       1   →       1              |        6.47 ms →        6.31 ms   (-2.49%) | 
  ├ sirius::Density                                                     |      135.34 ms →      135.11 ms   (-0.17%) |       1   →       1              |      135.34 ms →      135.11 ms   (-0.17%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.17 ms →        5.18 ms   (+0.24%) |       2   →       2              |       10.33 ms →       10.36 ms   (+0.24%) | 
  │ └ sirius::Density::update                                           |      124.73 ms →      124.48 ms   (-0.20%) |       1   →       1              |      124.73 ms →      124.48 ms   (-0.20%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      124.27 ms →      124.05 ms   (-0.18%) |       1   →       1              |      124.27 ms →      124.05 ms   (-0.18%) | 
+ │     ├ sirius::rho_core_ri_pseudo|values                             |      118.60 μs →      103.89 μs  (-12.41%) |       1   →       1              |      118.60 μs →      103.89 μs  (-12.41%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      118.48 ms →      118.52 ms   (+0.03%) |       1   →       1              |      118.48 ms →      118.52 ms   (+0.03%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        5.20 ms →        4.98 ms   (-4.32%) |       1   →       1              |        5.20 ms →        4.98 ms   (-4.32%) | 
  ├ sirius::Density::initial_density                                    |      174.79 ms →      177.69 ms   (+1.66%) |       1   →       1              |      174.79 ms →      177.69 ms   (+1.66%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      122.36 ms →      122.00 ms   (-0.29%) |       1   →       1              |      122.36 ms →      122.00 ms   (-0.29%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.11 ms →        6.68 ms  (+30.56%) |       2   →       2              |       10.23 ms →       13.35 ms  (+30.56%) | 
  │ └ sirius::Periodic_function::integrate                              |        9.79 ms →        9.79 ms   (-0.05%) |       1   →       1              |        9.79 ms →        9.79 ms   (-0.05%) | 
  ├ sirius::Potential::generate                                         |      591.77 ms →      593.21 ms   (+0.24%) |       1   →       1              |      591.77 ms →      593.21 ms   (+0.24%) | 
  │ ├ sirius::Potential::poisson                                        |      136.58 ms →      136.97 ms   (+0.28%) |       1   →       1              |      136.58 ms →      136.97 ms   (+0.28%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.35 ms →        5.20 ms   (-2.91%) |       1   →       1              |        5.35 ms →        5.20 ms   (-2.91%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        9.94 ms →       10.31 ms   (+3.70%) |       1   →       1              |        9.94 ms →       10.31 ms   (+3.70%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        9.92 ms →        9.89 ms   (-0.28%) |       1   →       1              |        9.92 ms →        9.89 ms   (-0.28%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.91 ms →        9.88 ms   (-0.28%) |       1   →       1              |        9.91 ms →        9.88 ms   (-0.28%) | 
  │ ├ sirius::Periodic_function::add                                    |      570.58 μs →      550.32 μs   (-3.55%) |       2   →       2              |        1.14 ms →        1.10 ms   (-3.55%) | 
  │ ├ sirius::Potential::xc                                             |       53.81 ms →       54.92 ms   (+2.07%) |       1   →       1              |       53.81 ms →       54.92 ms   (+2.07%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.38 ms →       52.58 ms   (+2.34%) |       1   →       1              |       51.38 ms →       52.58 ms   (+2.34%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.74 ms →        5.76 ms   (+0.34%) |       2   →       2              |       11.48 ms →       11.52 ms   (+0.34%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.37 ms →        5.50 ms   (+2.50%) |       1   →       1              |        5.37 ms →        5.50 ms   (+2.50%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.81 ms →        5.80 ms   (-0.18%) |       1   →       1              |        5.81 ms →        5.80 ms   (-0.18%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.73 ms →       93.03 ms   (+0.33%) |       1   →       1              |       92.73 ms →       93.03 ms   (+0.33%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      300.30 ms →      300.02 ms   (-0.09%) |       1   →       1              |      300.30 ms →      300.02 ms   (-0.09%) | 
- ├ sirius::Hamiltonian0                                                |        8.43 ms →        9.55 ms  (+13.37%) |       1   →       1              |        8.43 ms →        9.55 ms  (+13.37%) | 
- │ ├ sirius::Local_operator                                            |        8.07 ms →        9.20 ms  (+14.03%) |       1   →       1              |        8.07 ms →        9.20 ms  (+14.03%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.77 ms →        4.80 ms   (+0.62%) |       1   →       1              |        4.77 ms →        4.80 ms   (+0.62%) | 
- │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.38 ms →        3.48 ms  (+46.51%) |       1   →       1              |        2.38 ms →        3.48 ms  (+46.51%) | 
  │ ├ sirius::Non_local_operator                                        |       63.43 μs →       63.37 μs   (-0.10%) |       2   →       2              |      126.86 μs →      126.73 μs   (-0.10%) | 
  │ ├ sirius::D_operator::initialize                                    |       93.06 μs →       97.74 μs   (+5.03%) |       1   →       1              |       93.06 μs →       97.74 μs   (+5.03%) | 
  │ └ sirius::Q_operator::initialize                                    |       75.80 μs →       75.69 μs   (-0.15%) |       1   →       1              |       75.80 μs →       75.69 μs   (-0.15%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.85 s  →        1.85 s    (-0.33%) |       1   →       1              |        1.85 s  →        1.85 s    (-0.33%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.73 ms →       18.68 ms   (-0.27%) |       1   →       1              |       18.73 ms →       18.68 ms   (-0.27%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      180.41 μs →      183.76 μs   (+1.86%) |       1   →       1              |      180.41 μs →      183.76 μs   (+1.86%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       18.55 ms →       18.49 ms   (-0.29%) |       1   →       1              |       18.55 ms →       18.49 ms   (-0.29%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.83 s  →        1.83 s    (-0.33%) |       1   →       1              |        1.83 s  →        1.83 s    (-0.33%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      126.67 ms →      126.28 ms   (-0.31%) |       4   →       4              |      506.68 ms →      505.11 ms   (-0.31%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       52.88 ms →       52.67 ms   (-0.40%) |       1   →       1              |       52.88 ms →       52.67 ms   (-0.40%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.66 ms →       21.38 ms   (-1.29%) |       1   →       1              |       21.66 ms →       21.38 ms   (-1.29%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      635.75 ms →      634.30 ms   (-0.23%) |       1   →       1              |      635.75 ms →      634.30 ms   (-0.23%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      297.79 ms →      297.36 ms   (-0.14%) |       1   →       1              |      297.79 ms →      297.36 ms   (-0.14%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.44 μs →        3.54 μs   (+2.82%) |       1   →       1              |        3.44 μs →        3.54 μs   (+2.82%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.54 μs →        2.44 μs   (-3.86%) |       1   →       1              |        2.54 μs →        2.44 μs   (-3.86%) | 
+ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      440.00 ns →      336.00 ns  (-23.64%) |       1   →       1              |      440.00 ns →      336.00 ns  (-23.64%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      527.00 ns →      544.00 ns   (+3.23%) |       1   →       1              |      527.00 ns →      544.00 ns   (+3.23%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.22 ms →        9.23 ms   (+0.06%) |       1   →       1              |        9.22 ms →        9.23 ms   (+0.06%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      120.55 ms →      120.69 ms   (+0.12%) |       1   →       1              |      120.55 ms →      120.69 ms   (+0.12%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      104.08 ms →      103.49 ms   (-0.56%) |       2   →       2              |      208.15 ms →      206.99 ms   (-0.56%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       40.26 ms →       40.11 ms   (-0.35%) |       2   →       2              |       80.51 ms →       80.23 ms   (-0.35%) | 
  │ │ │ └ sddk::wf_inner                                                |       39.72 ms →       39.56 ms   (-0.40%) |       2   →       2              |       79.43 ms →       79.12 ms   (-0.40%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       12.50 ns →       60.00 ns (+380.00%) |       2   →       2              |       25.00 ns →      120.00 ns (+380.00%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       39.23 ms →       39.09 ms   (-0.36%) |       2   →       2              |       78.47 ms →       78.18 ms   (-0.36%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       19.00 ns →       23.50 ns  (+23.68%) |       2   →       2              |       38.00 ns →       47.00 ns  (+23.68%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       56.93 ms →       56.30 ms   (-1.10%) |       1   →       1              |       56.93 ms →       56.30 ms   (-1.10%) | 
  │ │ └ sddk::wf_trans                                                  |       30.75 ms →       30.72 ms   (-0.10%) |       1   →       1              |       30.75 ms →       30.72 ms   (-0.10%) | 
  │ │   └ sddk::wf_trans|pw                                             |       30.74 ms →       30.71 ms   (-0.10%) |       1   →       1              |       30.74 ms →       30.71 ms   (-0.10%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      830.00 ns →      517.00 ns  (-37.71%) |       1   →       1              |      830.00 ns →      517.00 ns  (-37.71%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      124.10 s  →      124.47 s    (+0.30%) |       1   →       1              |      124.10 s  →      124.47 s    (+0.30%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.89 ms →        5.79 ms   (-1.63%) |      19   →      19              |      111.88 ms →      110.05 ms   (-1.63%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.76 s  →        4.59 s    (-3.48%) |      26   →      27     (+3.85%) |      123.75 s  →      124.04 s    (+0.24%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        5.23 ms →        6.14 ms  (+17.49%) |      26   →      27     (+3.85%) |      135.91 ms →      165.82 ms  (+22.01%) | 
- │ │ │ ├ sirius::Local_operator                                        |        4.87 ms →        5.78 ms  (+18.73%) |      26   →      27     (+3.85%) |      126.49 ms →      155.96 ms  (+23.30%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      990.85 μs →      979.59 μs   (-1.14%) |      26   →      27     (+3.85%) |       25.76 ms →       26.45 ms   (+2.67%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.98 ms →        3.90 ms  (+30.85%) |      26   →      27     (+3.85%) |       77.58 ms →      105.41 ms  (+35.88%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.30 μs →       64.60 μs   (+0.47%) |      52   →      54     (+3.85%) |        3.34 ms →        3.49 ms   (+4.34%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       86.85 μs →       88.21 μs   (+1.57%) |      26   →      27     (+3.85%) |        2.26 ms →        2.38 ms   (+5.48%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       77.26 μs →       79.09 μs   (+2.36%) |      26   →      27     (+3.85%) |        2.01 ms →        2.14 ms   (+6.30%) | 
  │ │ ├ sirius::Band::solve                                             |        2.77 s  →        2.60 s    (-6.16%) |      26   →      27     (+3.85%) |       71.96 s  →       70.12 s    (-2.55%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      155.10 μs →      154.76 μs   (-0.22%) |      26   →      27     (+3.85%) |        4.03 ms →        4.18 ms   (+3.62%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      148.68 μs →      147.42 μs   (-0.84%) |      26   →      27     (+3.85%) |        3.87 ms →        3.98 ms   (+2.97%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.53 μs →        5.44 μs  (+20.09%) |      26   →      27     (+3.85%) |      117.88 μs →      147.01 μs  (+24.71%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.62 s  →        2.47 s    (-5.58%) |      26   →      27     (+3.85%) |       68.14 s  →       66.81 s    (-1.95%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       95.41 ms →       93.72 ms   (-1.77%) |      26   →      27     (+3.85%) |        2.48 s  →        2.53 s    (+2.01%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.72 ms →        7.30 ms   (-5.44%) |     156   →     162     (+3.85%) |        1.20 s  →        1.18 s    (-1.81%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        6.00 ms →        5.92 ms   (-1.41%) |      26   →      27     (+3.85%) |      156.08 ms →      159.80 ms   (+2.38%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      349.66 μs →      351.41 μs   (+0.50%) |      26   →      27     (+3.85%) |        9.09 ms →        9.49 ms   (+4.37%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.31 ms →        2.29 ms   (-0.86%) |      52   →      54     (+3.85%) |      120.00 ms →      123.55 ms   (+2.96%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.48 s  →        2.34 s    (-5.82%) |      26   →      27     (+3.85%) |       64.57 s  →       63.15 s    (-2.20%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      126.39 ms →      122.99 ms   (-2.69%) |     279   →     299     (+7.17%) |       35.26 s  →       36.77 s    (+4.29%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       50.42 ms →       49.16 ms   (-2.50%) |     279   →     299     (+7.17%) |       14.07 s  →       14.70 s    (+4.49%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.87 μs →        1.96 μs   (+4.71%) |     279   →     299     (+7.17%) |      521.35 μs →      585.03 μs  (+12.22%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.60 μs →        1.60 μs   (+0.04%) |     279   →     299     (+7.17%) |      446.98 μs →      479.20 μs   (+7.21%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      351.93 ns →      416.29 ns  (+18.29%) |     279   →     299     (+7.17%) |       98.19 μs →      124.47 μs  (+26.77%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      424.62 ns →      446.22 ns   (+5.09%) |     279   →     299     (+7.17%) |      118.47 μs →      133.42 μs  (+12.62%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.42 ms →        7.41 ms   (-0.19%) |     279   →     299     (+7.17%) |        2.07 s  →        2.21 s    (+6.96%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       22.88 ms →       21.87 ms   (-4.43%) |     279   →     299     (+7.17%) |        6.38 s  →        6.54 s    (+2.42%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       22.82 ms →       22.27 ms   (-2.42%) |     558   →     598     (+7.17%) |       12.74 s  →       13.32 s    (+4.57%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       34.14 ms →       32.69 ms   (-4.25%) |     279   →     299     (+7.17%) |        9.53 s  →        9.77 s    (+2.61%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        5.93 ms →        5.68 ms   (-4.15%) |     532   →     571     (+7.33%) |        3.15 s  →        3.24 s    (+2.87%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       80.14 ns →       47.17 ns  (-41.14%) |     532   →     571     (+7.33%) |       42.63 μs →       26.94 μs  (-36.82%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        4.81 ms →        4.57 ms   (-5.05%) |     532   →     571     (+7.33%) |        2.56 s  →        2.61 s    (+1.91%) | 
+ │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       55.28 ns →       32.13 ns  (-41.87%) |     532   →     571     (+7.33%) |       29.41 μs →       18.35 μs  (-37.61%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      614.77 μs →      589.62 μs   (-4.09%) |     279   →     299     (+7.17%) |      171.52 ms →      176.30 ms   (+2.79%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        9.49 ms →        9.12 ms   (-3.85%) |     279   →     299     (+7.17%) |        2.65 s  →        2.73 s    (+3.04%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |       14.04 ms →       13.32 ms   (-5.07%) |     253   →     272     (+7.51%) |        3.55 s  →        3.62 s    (+2.05%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        4.68 ms →        4.44 ms   (-5.08%) |     759   →     816     (+7.51%) |        3.55 s  →        3.62 s    (+2.05%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       10.28 ms →        9.49 ms   (-7.69%) |     279   →     299     (+7.17%) |        2.87 s  →        2.84 s    (-1.07%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |       10.01 ms →        9.29 ms   (-7.20%) |     279   →     299     (+7.17%) |        2.79 s  →        2.78 s    (-0.55%) | 
- │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       53.94 ns →       59.12 ns   (+9.61%) |     279   →     299     (+7.17%) |       15.05 μs →       17.68 μs  (+17.46%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        8.90 ms →        8.18 ms   (-8.08%) |     279   →     299     (+7.17%) |        2.48 s  →        2.45 s    (-1.49%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       71.16 ns →       92.47 ns  (+29.94%) |     279   →     299     (+7.17%) |       19.85 μs →       27.65 μs  (+39.26%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       33.39 ms →       18.88 ms  (-43.45%) |     279   →     299     (+7.17%) |        9.32 s  →        5.65 s   (-39.39%) | 
  │ │ │ │   ├ sirius::residuals                                         |       13.42 ms →       12.13 ms   (-9.62%) |     270   →     287     (+6.30%) |        3.62 s  →        3.48 s    (-3.93%) | 
+ │ │ │ │   │ ├ sddk::wf_trans                                          |       12.10 ms →       10.65 ms  (-12.05%) |     260   →     280     (+7.69%) |        3.15 s  →        2.98 s    (-5.29%) | 
+ │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        6.05 ms →        5.32 ms  (-12.06%) |     520   →     560     (+7.69%) |        3.15 s  →        2.98 s    (-5.29%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.58 ms →        1.55 ms   (-2.14%) |     260   →     280     (+7.69%) |      411.56 ms →      433.74 ms   (+5.39%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       74.92 ms →       59.39 ms  (-20.73%) |      53   →      78    (+47.17%) |        3.97 s  →        4.63 s   (+16.66%) | 
- │ │ │ │     └ sddk::wf_trans                                          |       49.40 ms →       35.65 ms  (-27.84%) |      80   →     129    (+61.25%) |        3.95 s  →        4.60 s   (+16.36%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |       36.93 ms →       25.54 ms  (-30.83%) |     107   →     180    (+68.22%) |        3.95 s  →        4.60 s   (+16.36%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      647.65 ns →      421.81 ns  (-34.87%) |      26   →      27     (+3.85%) |       16.84 μs →       11.39 μs  (-32.37%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       29.61 μs →       35.95 μs  (+21.42%) |      26   →      27     (+3.85%) |      769.85 μs →      970.74 μs  (+26.10%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      589.55 μs →      582.40 μs   (-1.21%) |      26   →      27     (+3.85%) |       15.33 ms →       15.72 ms   (+2.59%) | 
  │ │ ├ sirius::Density::generate                                       |      784.67 ms →      781.84 ms   (-0.36%) |      26   →      27     (+3.85%) |       20.40 s  →       21.11 s    (+3.47%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      401.49 ms →      402.65 ms   (+0.29%) |      26   →      27     (+3.85%) |       10.44 s  →       10.87 s    (+4.15%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.06 μs →        8.32 μs   (+3.15%) |      26   →      27     (+3.85%) |      209.62 μs →      224.55 μs   (+7.12%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.53 μs →        7.78 μs   (+3.32%) |      26   →      27     (+3.85%) |      195.75 μs →      210.02 μs   (+7.29%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |      100.21 ms →      100.13 ms   (-0.08%) |      26   →      27     (+3.85%) |        2.61 s  →        2.70 s    (+3.77%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.24 μs →        7.66 μs   (+5.79%) |      26   →      27     (+3.85%) |      188.18 μs →      206.73 μs   (+9.86%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.12 ms →        7.12 ms   (-0.01%) |      26   →      27     (+3.85%) |      185.10 ms →      192.21 ms   (+3.84%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       91.19 ms →       91.12 ms   (-0.08%) |      26   →      27     (+3.85%) |        2.37 s  →        2.46 s    (+3.77%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      744.88 ns →      558.26 ns  (-25.05%) |      26   →      27     (+3.85%) |       19.37 μs →       15.07 μs  (-22.17%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      162.56 ms →      163.87 ms   (+0.80%) |      26   →      27     (+3.85%) |        4.23 s  →        4.42 s    (+4.68%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.65 ms   (+0.31%) |      26   →      27     (+3.85%) |       42.70 ms →       44.48 ms   (+4.17%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.34 ms →       88.24 ms   (-0.11%) |      26   →      27     (+3.85%) |        2.30 s  →        2.38 s    (+3.73%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.10 ms →       88.01 ms   (-0.11%) |      26   →      27     (+3.85%) |        2.29 s  →        2.38 s    (+3.73%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      282.38 ms →      281.17 ms   (-0.43%) |      26   →      27     (+3.85%) |        7.34 s  →        7.59 s    (+3.40%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      282.38 ms →      281.17 ms   (-0.43%) |      26   →      27     (+3.85%) |        7.34 s  →        7.59 s    (+3.40%) | 
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.27 ms →       29.68 ms  (+22.28%) |      26   →      27     (+3.85%) |      631.08 ms →      801.38 ms  (+26.99%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      233.33 ms →      227.16 ms   (-2.65%) |      26   →      27     (+3.85%) |        6.07 s  →        6.13 s    (+1.10%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       23.58 ms →       23.14 ms   (-1.86%) |      26   →      27     (+3.85%) |      613.04 ms →      624.79 ms   (+1.92%) | 
+ │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       91.38 ms →       81.95 ms  (-10.32%) |      26   →      27     (+3.85%) |        2.38 s  →        2.21 s    (-6.87%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        5.83 ms →       12.48 ms (+114.11%) |      26   →      27     (+3.85%) |      151.52 ms →      336.90 ms (+122.35%) | 
  │ │ ├ sirius::Density::mix                                            |      218.36 ms →      216.48 ms   (-0.86%) |      26   →      27     (+3.85%) |        5.68 s  →        5.84 s    (+2.95%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      969.90 μs →      970.67 μs   (+0.08%) |      26   →      27     (+3.85%) |       25.22 ms →       26.21 ms   (+3.93%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.70 ms →       10.36 ms   (-3.21%) |     334   →     349     (+4.49%) |        3.58 s  →        3.62 s    (+1.14%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.34 ms →        9.97 ms   (-3.53%) |     334   →     349     (+4.49%) |        3.45 s  →        3.48 s    (+0.80%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.34 ms →        9.97 ms   (-3.53%) |     334   →     349     (+4.49%) |        3.45 s  →        3.48 s    (+0.80%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        6.91 ms →        6.60 ms   (-4.50%) |      26   →      27     (+3.85%) |      179.69 ms →      178.21 ms   (-0.83%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        6.06 ms →        5.78 ms   (-4.58%) |      26   →      27     (+3.85%) |      157.63 ms →      156.19 ms   (-0.91%) | 
  │ │ ├ sirius::Potential::generate                                     |      577.85 ms →      578.30 ms   (+0.08%) |      26   →      27     (+3.85%) |       15.02 s  →       15.61 s    (+3.93%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      137.06 ms →      136.77 ms   (-0.21%) |      26   →      27     (+3.85%) |        3.56 s  →        3.69 s    (+3.63%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        5.24 ms →        5.15 ms   (-1.79%) |      26   →      27     (+3.85%) |      136.31 ms →      139.01 ms   (+1.98%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.34 ms →       10.09 ms   (-2.39%) |      26   →      27     (+3.85%) |      268.86 ms →      272.53 ms   (+1.37%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        9.99 ms →        9.88 ms   (-1.07%) |      26   →      27     (+3.85%) |      259.64 ms →      266.75 ms   (+2.74%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        9.99 ms →        9.88 ms   (-1.06%) |      26   →      27     (+3.85%) |      259.62 ms →      266.73 ms   (+2.74%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      566.04 μs →      550.36 μs   (-2.77%) |      52   →      54     (+3.85%) |       29.43 ms →       29.72 ms   (+0.97%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       48.71 ms →       48.88 ms   (+0.36%) |      26   →      27     (+3.85%) |        1.27 s  →        1.32 s    (+4.22%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.32 ms →       46.54 ms   (+0.47%) |      26   →      27     (+3.85%) |        1.20 s  →        1.26 s    (+4.34%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.04 ms →        3.03 ms   (-0.33%) |      52   →      54     (+3.85%) |      158.14 ms →      163.67 ms   (+3.50%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.40 ms →        5.38 ms   (-0.30%) |      26   →      27     (+3.85%) |      140.40 ms →      145.37 ms   (+3.54%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.53 ms →        6.53 ms   (-0.00%) |      26   →      27     (+3.85%) |      169.68 ms →      176.20 ms   (+3.84%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.99 ms →       90.95 ms   (-0.04%) |      26   →      27     (+3.85%) |        2.37 s  →        2.46 s    (+3.80%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      292.11 ms →      292.79 ms   (+0.23%) |      26   →      27     (+3.85%) |        7.59 s  →        7.91 s    (+4.09%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      283.52 ms →      287.79 ms   (+1.51%) |      26   →      27     (+3.85%) |        7.37 s  →        7.77 s    (+5.41%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      283.52 ms →      287.79 ms   (+1.51%) |      26   →      27     (+3.85%) |        7.37 s  →        7.77 s    (+5.41%) | 
- │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.17 ms →       32.70 ms  (+20.34%) |      26   →      27     (+3.85%) |      706.42 ms →      882.80 ms  (+24.97%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      227.50 ms →      227.51 ms   (+0.01%) |      26   →      27     (+3.85%) |        5.91 s  →        6.14 s    (+3.85%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       25.05 ms →       23.79 ms   (-5.04%) |      26   →      27     (+3.85%) |      651.31 ms →      642.27 ms   (-1.39%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.80 ms →       12.28 ms (+111.71%) |      26   →      27     (+3.85%) |      150.84 ms →      331.62 ms (+119.85%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.32 ms →       10.24 ms   (-0.80%) |     182   →     189     (+3.85%) |        1.88 s  →        1.94 s    (+3.02%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.80 ms →        9.79 ms   (-0.09%) |     182   →     189     (+3.85%) |        1.78 s  →        1.85 s    (+3.76%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.80 ms →        9.79 ms   (-0.09%) |     182   →     189     (+3.85%) |        1.78 s  →        1.85 s    (+3.76%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       11.10 ms →       10.53 ms   (-5.18%) |      78   →      81     (+3.85%) |      866.05 ms →      852.79 ms   (-1.53%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.60 ms →       10.07 ms   (-4.99%) |      78   →      81     (+3.85%) |      827.10 ms →      816.05 ms   (-1.34%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |       10.06 ms →        9.97 ms   (-0.95%) |      26   →      27     (+3.85%) |      261.61 ms →      269.08 ms   (+2.85%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      109.67 μs →      129.17 μs  (+17.78%) |      26   →      27     (+3.85%) |        2.85 ms →        3.49 ms  (+22.31%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      104.71 μs →      124.52 μs  (+18.92%) |      26   →      27     (+3.85%) |        2.72 ms →        3.36 ms  (+23.49%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.07 ms →        5.34 ms   (+5.43%) |       2   →       2              |       10.14 ms →       10.69 ms   (+5.43%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.10 ms →       10.13 ms   (+0.30%) |       6   →       6              |       60.58 ms →       60.77 ms   (+0.30%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        9.76 ms →        9.72 ms   (-0.43%) |       6   →       6              |       58.54 ms →       58.29 ms   (-0.43%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        9.76 ms →        9.71 ms   (-0.43%) |       6   →       6              |       58.54 ms →       58.29 ms   (-0.43%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.91 ms →       10.48 ms   (-3.96%) |       3   →       3              |       32.74 ms →       31.44 ms   (-3.96%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.60 ms →       10.15 ms   (-4.30%) |       3   →       3              |       31.81 ms →       30.44 ms   (-4.30%) | 
  ├ sirius::Periodic_function|inner                                     |       10.05 ms →       10.06 ms   (+0.10%) |       2   →       2              |       20.09 ms →       20.11 ms   (+0.10%) | 
  │ └ sirius::Periodic_function|inner_local                             |        9.62 ms →        9.77 ms   (+1.55%) |       2   →       2              |       19.25 ms →       19.54 ms   (+1.55%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.62 ms →        9.77 ms   (+1.54%) |       2   →       2              |       19.25 ms →       19.54 ms   (+1.54%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.93 ms →       10.65 ms   (-2.53%) |       1   →       1              |       10.93 ms →       10.65 ms   (-2.53%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.47 ms →       10.09 ms   (-3.58%) |       1   →       1              |       10.47 ms →       10.09 ms   (-3.58%) | 
+ └ sirius::finalize                                                    |      217.34 ms →      185.23 ms  (-14.78%) |       1   →       1              |      217.34 ms →      185.23 ms  (-14.78%) | 
  ====================================================================================================================================================================================================
```
