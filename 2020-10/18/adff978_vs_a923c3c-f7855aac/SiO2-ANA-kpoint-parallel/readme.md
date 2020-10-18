# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      133.09 s  →      128.52 s    (-3.43%) |       1   →       1              |      133.09 s  →      128.52 s    (-3.43%) | 
  ├ sirius::initialize                                                  |        2.73 s  →        2.67 s    (-1.96%) |       1   →       1              |        2.73 s  →        2.67 s    (-1.96%) | 
  ├ sirius::Simulation_context::initialize                              |        2.93 s  →        2.97 s    (+1.34%) |       1   →       1              |        2.93 s  →        2.97 s    (+1.34%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       48.83 ms →       15.10 ms  (-69.09%) |       1   →       1              |       48.83 ms →       15.10 ms  (-69.09%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      144.55 ms →      163.73 ms  (+13.27%) |       1   →       1              |      144.55 ms →      163.73 ms  (+13.27%) | 
- │ │ ├ sirius::Atom_type::init                                         |       60.78 ms →       70.67 ms  (+16.27%) |       2   →       2              |      121.57 ms →      141.35 ms  (+16.27%) | 
  │ │ └ sirius::Unit_cell::update                                       |       22.88 ms →       22.30 ms   (-2.56%) |       1   →       1              |       22.88 ms →       22.30 ms   (-2.56%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.37 ms →        6.38 ms   (+0.11%) |       1   →       1              |        6.37 ms →        6.38 ms   (+0.11%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       16.47 ms →       15.87 ms   (-3.64%) |       1   →       1              |       16.47 ms →       15.87 ms   (-3.64%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       16.45 ms →       15.85 ms   (-3.64%) |       1   →       1              |       16.45 ms →       15.85 ms   (-3.64%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.14 ms →        4.14 ms   (-0.06%) |       1   →       1              |        4.14 ms →        4.14 ms   (-0.06%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.33 ms   (+0.06%) |       1   →       1              |        2.33 ms →        2.33 ms   (+0.06%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      104.74 μs →      102.36 μs   (-2.27%) |       1   →       1              |      104.74 μs →      102.36 μs   (-2.27%) | 
  │ └ sirius::Simulation_context::update                                |        2.69 s  →        2.74 s    (+1.99%) |       1   →       1              |        2.69 s  →        2.74 s    (+1.99%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.87 ms →       10.90 ms   (+0.22%) |       1   →       1              |       10.87 ms →       10.90 ms   (+0.22%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.44 ms →        4.46 ms   (+0.65%) |       1   →       1              |        4.44 ms →        4.46 ms   (+0.65%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.40 ms →        6.40 ms   (-0.11%) |       1   →       1              |        6.40 ms →        6.40 ms   (-0.11%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.38 ms →        6.38 ms   (-0.10%) |       1   →       1              |        6.38 ms →        6.38 ms   (-0.10%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.90 ms →        3.89 ms   (-0.11%) |       1   →       1              |        3.90 ms →        3.89 ms   (-0.11%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.32 ms   (-0.05%) |       1   →       1              |        2.32 ms →        2.32 ms   (-0.05%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       99.24 μs →       98.96 μs   (-0.29%) |       1   →       1              |       99.24 μs →       98.96 μs   (-0.29%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       63.10 ms →       64.44 ms   (+2.12%) |       2   →       2              |      126.21 ms →      128.89 ms   (+2.12%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.14 ms →        5.13 ms   (-0.13%) |       2   →       2              |       10.28 ms →       10.26 ms   (-0.13%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.55 ms →        4.48 ms   (-1.56%) |       1   →       1              |        4.55 ms →        4.48 ms   (-1.56%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.73 ms →       21.76 ms   (+0.13%) |       2   →       2              |       43.47 ms →       43.52 ms   (+0.13%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.83 ms →       14.83 ms   (+0.01%) |       2   →       2              |       29.67 ms →       29.67 ms   (+0.01%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.85 ms →       19.81 ms   (-0.21%) |       4   →       4              |       79.39 ms →       79.22 ms   (-0.21%) | 
  │   ├ sddk::Gvec::init                                                |      172.51 ms →      172.30 ms   (-0.12%) |       2   →       2              |      345.02 ms →      344.60 ms   (-0.12%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      129.83 ms →      129.26 ms   (-0.44%) |       2   →       2              |      259.66 ms →      258.52 ms   (-0.44%) | 
  │   ├ sddk::Gvec_shells                                               |      176.98 ms →      180.81 ms   (+2.17%) |       1   →       1              |      176.98 ms →      180.81 ms   (+2.17%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.33 ms →        1.34 ms   (+0.82%) |       1   →       1              |        1.33 ms →        1.34 ms   (+0.82%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      293.11 ms →      292.78 ms   (-0.11%) |       2   →       2              |      586.22 ms →      585.55 ms   (-0.11%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       40.18 ms →       38.85 ms   (-3.33%) |       1   →       1              |       40.18 ms →       38.85 ms   (-3.33%) | 
+ │ ├ sirius::K_point::K_point                                          |        2.86 μs →        2.15 μs  (-24.73%) |       4   →       4              |       11.42 μs →        8.60 μs  (-24.73%) | 
  │ └ sirius::K_point_set::initialize                                   |       40.08 ms →       38.72 ms   (-3.39%) |       1   →       1              |       40.08 ms →       38.72 ms   (-3.39%) | 
  │   └ sirius::K_point::initialize                                     |       38.09 ms →       38.62 ms   (+1.38%) |       1   →       1              |       38.09 ms →       38.62 ms   (+1.38%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       19.89 ms →       20.12 ms   (+1.16%) |       1   →       1              |       19.89 ms →       20.12 ms   (+1.16%) | 
  │     │ └ sddk::Gvec::init                                            |        8.52 ms →        9.04 ms   (+6.08%) |       1   →       1              |        8.52 ms →        9.04 ms   (+6.08%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |       10.82 μs →       10.31 μs   (-4.77%) |       1   →       1              |       10.82 μs →       10.31 μs   (-4.77%) | 
  │     └ sirius::K_point::update                                       |       12.90 ms →       13.13 ms   (+1.83%) |       1   →       1              |       12.90 ms →       13.13 ms   (+1.83%) | 
  │       └ sirius::Beta_projectors                                     |        6.23 ms →        6.20 ms   (-0.51%) |       1   →       1              |        6.23 ms →        6.20 ms   (-0.51%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.58 ms →        3.61 ms   (+0.83%) |       1   →       1              |        3.58 ms →        3.61 ms   (+0.83%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.24 ms →        5.42 ms   (+3.46%) |       2   →       2              |       10.48 ms →       10.84 ms   (+3.46%) | 
  ├ sirius::Potential                                                   |      159.49 ms →      158.90 ms   (-0.37%) |       1   →       1              |      159.49 ms →      158.90 ms   (-0.37%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.91 ms →        5.88 ms   (-0.57%) |       6   →       6              |       35.47 ms →       35.27 ms   (-0.57%) | 
  │ └ sirius::Potential::update                                         |      123.28 ms →      122.89 ms   (-0.31%) |       1   →       1              |      123.28 ms →      122.89 ms   (-0.31%) | 
  │   └ sirius::Potential::generate_local_potential                     |      122.55 ms →      122.11 ms   (-0.36%) |       1   →       1              |      122.55 ms →      122.11 ms   (-0.36%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      108.72 ms →      107.14 ms   (-1.45%) |       1   →       1              |      108.72 ms →      107.14 ms   (-1.45%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |       12.93 ms →       14.06 ms   (+8.69%) |       1   →       1              |       12.93 ms →       14.06 ms   (+8.69%) | 
  ├ sirius::Density                                                     |      136.49 ms →      136.08 ms   (-0.30%) |       1   →       1              |      136.49 ms →      136.08 ms   (-0.30%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.25 ms →        5.22 ms   (-0.53%) |       2   →       2              |       10.49 ms →       10.44 ms   (-0.53%) | 
  │ └ sirius::Density::update                                           |      125.70 ms →      125.37 ms   (-0.26%) |       1   →       1              |      125.70 ms →      125.37 ms   (-0.26%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      125.24 ms →      124.93 ms   (-0.25%) |       1   →       1              |      125.24 ms →      124.93 ms   (-0.25%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |      102.94 μs →      103.64 μs   (+0.68%) |       1   →       1              |      102.94 μs →      103.64 μs   (+0.68%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      111.14 ms →      109.19 ms   (-1.76%) |       1   →       1              |      111.14 ms →      109.19 ms   (-1.76%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |       13.51 ms →       15.18 ms  (+12.35%) |       1   →       1              |       13.51 ms →       15.18 ms  (+12.35%) | 
  ├ sirius::Density::initial_density                                    |      176.50 ms →      178.62 ms   (+1.20%) |       1   →       1              |      176.50 ms →      178.62 ms   (+1.20%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      110.39 ms →      108.69 ms   (-1.54%) |       1   →       1              |      110.39 ms →      108.69 ms   (-1.54%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |       11.75 ms →       11.77 ms   (+0.16%) |       2   →       2              |       23.50 ms →       23.54 ms   (+0.16%) | 
  │ └ sirius::Periodic_function::integrate                              |       10.29 ms →       10.89 ms   (+5.83%) |       1   →       1              |       10.29 ms →       10.89 ms   (+5.83%) | 
  ├ sirius::Potential::generate                                         |      595.09 ms →      595.71 ms   (+0.10%) |       1   →       1              |      595.09 ms →      595.71 ms   (+0.10%) | 
  │ ├ sirius::Potential::poisson                                        |      138.36 ms →      137.30 ms   (-0.77%) |       1   →       1              |      138.36 ms →      137.30 ms   (-0.77%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       19.47 ms →       19.52 ms   (+0.24%) |       1   →       1              |       19.47 ms →       19.52 ms   (+0.24%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        9.94 ms →       10.22 ms   (+2.80%) |       1   →       1              |        9.94 ms →       10.22 ms   (+2.80%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        9.83 ms →        9.94 ms   (+1.05%) |       1   →       1              |        9.83 ms →        9.94 ms   (+1.05%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.82 ms →        9.93 ms   (+1.05%) |       1   →       1              |        9.82 ms →        9.93 ms   (+1.05%) | 
  │ ├ sirius::Periodic_function::add                                    |      560.54 μs →      557.38 μs   (-0.56%) |       2   →       2              |        1.12 ms →        1.11 ms   (-0.56%) | 
  │ ├ sirius::Potential::xc                                             |       55.50 ms →       56.39 ms   (+1.61%) |       1   →       1              |       55.50 ms →       56.39 ms   (+1.61%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       53.09 ms →       54.00 ms   (+1.70%) |       1   →       1              |       53.09 ms →       54.00 ms   (+1.70%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.77 ms →        5.71 ms   (-1.15%) |       2   →       2              |       11.55 ms →       11.41 ms   (-1.15%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.70 ms →        6.01 ms   (+5.33%) |       1   →       1              |        5.70 ms →        6.01 ms   (+5.33%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.87 ms →        5.91 ms   (+0.61%) |       1   →       1              |        5.87 ms →        5.91 ms   (+0.61%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.76 ms →       93.56 ms   (+0.86%) |       1   →       1              |       92.76 ms →       93.56 ms   (+0.86%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      300.05 ms →      300.06 ms   (+0.00%) |       1   →       1              |      300.05 ms →      300.06 ms   (+0.00%) | 
  ├ sirius::Hamiltonian0                                                |        8.76 ms →        8.41 ms   (-4.00%) |       1   →       1              |        8.76 ms →        8.41 ms   (-4.00%) | 
  │ ├ sirius::Local_operator                                            |        8.40 ms →        8.06 ms   (-4.00%) |       1   →       1              |        8.40 ms →        8.06 ms   (-4.00%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        5.12 ms →        4.83 ms   (-5.75%) |       1   →       1              |        5.12 ms →        4.83 ms   (-5.75%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.35 ms →        2.31 ms   (-1.60%) |       1   →       1              |        2.35 ms →        2.31 ms   (-1.60%) | 
  │ ├ sirius::Non_local_operator                                        |       62.21 μs →       62.21 μs   (+0.01%) |       2   →       2              |      124.41 μs →      124.43 μs   (+0.01%) | 
  │ ├ sirius::D_operator::initialize                                    |       98.94 μs →       96.12 μs   (-2.85%) |       1   →       1              |       98.94 μs →       96.12 μs   (-2.85%) | 
  │ └ sirius::Q_operator::initialize                                    |       81.48 μs →       74.64 μs   (-8.40%) |       1   →       1              |       81.48 μs →       74.64 μs   (-8.40%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.90 s  →        1.86 s    (-1.87%) |       1   →       1              |        1.90 s  →        1.86 s    (-1.87%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.09 ms →       18.67 ms   (+3.19%) |       1   →       1              |       18.09 ms →       18.67 ms   (+3.19%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      193.02 μs →      196.21 μs   (+1.66%) |       1   →       1              |      193.02 μs →      196.21 μs   (+1.66%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       17.89 ms →       18.47 ms   (+3.21%) |       1   →       1              |       17.89 ms →       18.47 ms   (+3.21%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.88 s  →        1.84 s    (-1.92%) |       1   →       1              |        1.88 s  →        1.84 s    (-1.92%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      131.87 ms →      125.91 ms   (-4.52%) |       4   →       4              |      527.49 ms →      503.65 ms   (-4.52%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       53.33 ms →       52.53 ms   (-1.50%) |       1   →       1              |       53.33 ms →       52.53 ms   (-1.50%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.58 ms →       21.09 ms   (-2.24%) |       1   →       1              |       21.58 ms →       21.09 ms   (-2.24%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      640.95 ms →      634.52 ms   (-1.00%) |       1   →       1              |      640.95 ms →      634.52 ms   (-1.00%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      303.26 ms →      297.45 ms   (-1.92%) |       1   →       1              |      303.26 ms →      297.45 ms   (-1.92%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.62 μs →        3.25 μs  (-10.41%) |       1   →       1              |        3.62 μs →        3.25 μs  (-10.41%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.79 μs →        2.35 μs  (-15.63%) |       1   →       1              |        2.79 μs →        2.35 μs  (-15.63%) | 
- │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      386.00 ns →      434.00 ns  (+12.44%) |       1   →       1              |      386.00 ns →      434.00 ns  (+12.44%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      607.00 ns →      656.00 ns   (+8.07%) |       1   →       1              |      607.00 ns →      656.00 ns   (+8.07%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.22 ms →        9.22 ms   (+0.01%) |       1   →       1              |        9.22 ms →        9.22 ms   (+0.01%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      120.77 ms →      120.64 ms   (-0.11%) |       1   →       1              |      120.77 ms →      120.64 ms   (-0.11%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      103.83 ms →      103.59 ms   (-0.23%) |       2   →       2              |      207.66 ms →      207.18 ms   (-0.23%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       40.20 ms →       40.16 ms   (-0.09%) |       2   →       2              |       80.40 ms →       80.33 ms   (-0.09%) | 
  │ │ │ └ sddk::wf_inner                                                |       39.63 ms →       39.63 ms   (-0.01%) |       2   →       2              |       79.27 ms →       79.26 ms   (-0.01%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       25.00 ns →       37.00 ns  (+48.00%) |       2   →       2              |       50.00 ns →       74.00 ns  (+48.00%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       39.18 ms →       39.15 ms   (-0.07%) |       2   →       2              |       78.36 ms →       78.30 ms   (-0.07%) | 
+ │ │ │   └ sddk::wf_inner|scale_back                                   |       22.50 ns →       19.00 ns  (-15.56%) |       2   →       2              |       45.00 ns →       38.00 ns  (-15.56%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       61.66 ms →       57.10 ms   (-7.39%) |       1   →       1              |       61.66 ms →       57.10 ms   (-7.39%) | 
  │ │ └ sddk::wf_trans                                                  |       30.76 ms →       30.74 ms   (-0.06%) |       1   →       1              |       30.76 ms →       30.74 ms   (-0.06%) | 
  │ │   └ sddk::wf_trans|pw                                             |       30.76 ms →       30.74 ms   (-0.06%) |       1   →       1              |       30.76 ms →       30.74 ms   (-0.06%) | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      565.00 ns →      550.00 ns   (-2.65%) |       1   →       1              |      565.00 ns →      550.00 ns   (-2.65%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      123.37 s  →      118.80 s    (-3.70%) |       1   →       1              |      123.37 s  →      118.80 s    (-3.70%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.90 ms →        5.88 ms   (-0.21%) |      19   →      19              |      112.03 ms →      111.80 ms   (-0.21%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.73 s  →        4.56 s    (-3.73%) |      26   →      26              |      123.04 s  →      118.45 s    (-3.73%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        4.47 ms →        6.24 ms  (+39.49%) |      26   →      26              |      116.29 ms →      162.20 ms  (+39.49%) | 
- │ │ │ ├ sirius::Local_operator                                        |        4.11 ms →        5.87 ms  (+43.07%) |      26   →      26              |      106.75 ms →      152.72 ms  (+43.07%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      955.37 μs →      981.62 μs   (+2.75%) |      26   →      26              |       24.84 ms →       25.52 ms   (+2.75%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.25 ms →        4.00 ms  (+77.62%) |      26   →      26              |       58.57 ms →      104.04 ms  (+77.62%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.61 μs →       64.46 μs   (-0.24%) |      52   →      52              |        3.36 ms →        3.35 ms   (-0.24%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       88.87 μs →       88.15 μs   (-0.81%) |      26   →      26              |        2.31 ms →        2.29 ms   (-0.81%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       79.68 μs →       78.09 μs   (-2.00%) |      26   →      26              |        2.07 ms →        2.03 ms   (-2.00%) | 
  │ │ ├ sirius::Band::solve                                             |        2.76 s  →        2.59 s    (-5.98%) |      26   →      26              |       71.75 s  →       67.46 s    (-5.98%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      153.46 μs →      150.84 μs   (-1.71%) |      26   →      26              |        3.99 ms →        3.92 ms   (-1.71%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      146.24 μs →      143.85 μs   (-1.64%) |      26   →      26              |        3.80 ms →        3.74 ms   (-1.64%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.29 μs →        5.11 μs   (-3.39%) |      26   →      26              |      137.57 μs →      132.91 μs   (-3.39%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.62 s  →        2.47 s    (-5.86%) |      26   →      26              |       68.12 s  →       64.13 s    (-5.86%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       96.58 ms →       95.95 ms   (-0.65%) |      26   →      26              |        2.51 s  →        2.49 s    (-0.65%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.85 ms →        7.83 ms   (-0.26%) |     156   →     156              |        1.22 s  →        1.22 s    (-0.26%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        5.94 ms →        5.93 ms   (-0.13%) |      26   →      26              |      154.50 ms →      154.30 ms   (-0.13%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      351.65 μs →      348.80 μs   (-0.81%) |      26   →      26              |        9.14 ms →        9.07 ms   (-0.81%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.31 ms →        2.30 ms   (-0.45%) |      52   →      52              |      119.92 ms →      119.38 ms   (-0.45%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.48 s  →        2.33 s    (-6.16%) |      26   →      26              |       64.52 s  →       60.55 s    (-6.16%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      126.79 ms →      136.47 ms   (+7.63%) |     278   →     262     (-5.76%) |       35.25 s  →       35.75 s    (+1.44%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       50.79 ms →       55.64 ms   (+9.55%) |     278   →     262     (-5.76%) |       14.12 s  →       14.58 s    (+3.25%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.89 μs →        1.90 μs   (+0.70%) |     278   →     262     (-5.76%) |      525.05 μs →      498.28 μs   (-5.10%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.62 μs →        1.62 μs   (-0.32%) |     278   →     262     (-5.76%) |      451.31 μs →      423.97 μs   (-6.06%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      351.16 ns →      379.99 ns   (+8.21%) |     278   →     262     (-5.76%) |       97.62 μs →       99.56 μs   (+1.98%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      405.88 ns →      439.24 ns   (+8.22%) |     278   →     262     (-5.76%) |      112.83 μs →      115.08 μs   (+1.99%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.42 ms →        7.45 ms   (+0.48%) |     278   →     262     (-5.76%) |        2.06 s  →        1.95 s    (-5.30%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       22.83 ms →       24.55 ms   (+7.52%) |     278   →     262     (-5.76%) |        6.35 s  →        6.43 s    (+1.33%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       22.87 ms →       24.41 ms   (+6.72%) |     556   →     524     (-5.76%) |       12.71 s  →       12.79 s    (+0.58%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       34.20 ms →       35.84 ms   (+4.81%) |     278   →     262     (-5.76%) |        9.51 s  →        9.39 s    (-1.22%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        5.94 ms →        6.21 ms   (+4.69%) |     530   →     498     (-6.04%) |        3.15 s  →        3.09 s    (-1.63%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       79.54 ns →       52.75 ns  (-33.69%) |     530   →     498     (-6.04%) |       42.16 μs →       26.27 μs  (-37.69%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        4.82 ms →        5.10 ms   (+5.80%) |     530   →     498     (-6.04%) |        2.56 s  →        2.54 s    (-0.59%) | 
+ │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       52.53 ns →       27.78 ns  (-47.13%) |     530   →     498     (-6.04%) |       27.84 μs →       13.83 μs  (-50.32%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      609.89 μs →      660.54 μs   (+8.30%) |     278   →     262     (-5.76%) |      169.55 ms →      173.06 ms   (+2.07%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        9.51 ms →       10.31 ms   (+8.33%) |     278   →     262     (-5.76%) |        2.65 s  →        2.70 s    (+2.10%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |       14.06 ms →       14.49 ms   (+3.05%) |     252   →     236     (-6.35%) |        3.54 s  →        3.42 s    (-3.49%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        4.69 ms →        4.83 ms   (+3.05%) |     756   →     708     (-6.35%) |        3.54 s  →        3.42 s    (-3.49%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       10.29 ms →       10.38 ms   (+0.87%) |     278   →     262     (-5.76%) |        2.86 s  →        2.72 s    (-4.93%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |       10.03 ms →       10.18 ms   (+1.52%) |     278   →     262     (-5.76%) |        2.79 s  →        2.67 s    (-4.32%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       48.82 ns →       26.45 ns  (-45.82%) |     278   →     262     (-5.76%) |       13.57 μs →        6.93 μs  (-48.94%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        8.91 ms →        9.07 ms   (+1.73%) |     278   →     262     (-5.76%) |        2.48 s  →        2.38 s    (-4.12%) | 
+ │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       68.92 ns →       47.97 ns  (-30.39%) |     278   →     262     (-5.76%) |       19.16 μs →       12.57 μs  (-34.40%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       33.53 ms →       18.30 ms  (-45.43%) |     278   →     262     (-5.76%) |        9.32 s  →        4.79 s   (-48.57%) | 
  │ │ │ │   ├ sirius::residuals                                         |       13.41 ms →       13.15 ms   (-1.92%) |     269   →     252     (-6.32%) |        3.61 s  →        3.31 s    (-8.12%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       12.10 ms →       11.73 ms   (-3.11%) |     259   →     242     (-6.56%) |        3.13 s  →        2.84 s    (-9.47%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        6.05 ms →        5.86 ms   (-3.11%) |     518   →     484     (-6.56%) |        3.13 s  →        2.84 s    (-9.47%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.58 ms →        1.71 ms   (+8.23%) |     259   →     242     (-6.56%) |      410.08 ms →      414.70 ms   (+1.13%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       74.90 ms →       53.74 ms  (-28.26%) |      53   →      85    (+60.38%) |        3.97 s  →        4.57 s   (+15.06%) | 
- │ │ │ │     └ sddk::wf_trans                                          |       49.39 ms →       31.46 ms  (-36.32%) |      80   →     144    (+80.00%) |        3.95 s  →        4.53 s   (+14.63%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |       36.93 ms →       22.31 ms  (-39.58%) |     107   →     203    (+89.72%) |        3.95 s  →        4.53 s   (+14.63%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      663.50 ns →      405.92 ns  (-38.82%) |      26   →      26              |       17.25 μs →       10.55 μs  (-38.82%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       28.98 μs →       30.15 μs   (+4.04%) |      26   →      26              |      753.40 μs →      783.80 μs   (+4.04%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      589.08 μs →      610.37 μs   (+3.61%) |      26   →      26              |       15.32 ms →       15.87 ms   (+3.61%) | 
  │ │ ├ sirius::Density::generate                                       |      770.10 ms →      768.64 ms   (-0.19%) |      26   →      26              |       20.02 s  →       19.98 s    (-0.19%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      402.26 ms →      400.98 ms   (-0.32%) |      26   →      26              |       10.46 s  →       10.43 s    (-0.32%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.44 μs →        8.31 μs   (-1.57%) |      26   →      26              |      219.44 μs →      215.99 μs   (-1.57%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.87 μs →        7.83 μs   (-0.61%) |      26   →      26              |      204.71 μs →      203.47 μs   (-0.61%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |      100.15 ms →      100.20 ms   (+0.05%) |      26   →      26              |        2.60 s  →        2.61 s    (+0.05%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.48 μs →        7.79 μs   (+4.16%) |      26   →      26              |      194.54 μs →      202.64 μs   (+4.16%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.12 ms →        7.12 ms   (+0.02%) |      26   →      26              |      185.02 ms →      185.06 ms   (+0.02%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       91.13 ms →       91.17 ms   (+0.04%) |      26   →      26              |        2.37 s  →        2.37 s    (+0.04%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      797.77 ns →      574.46 ns  (-27.99%) |      26   →      26              |       20.74 μs →       14.94 μs  (-27.99%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      163.28 ms →      162.07 ms   (-0.74%) |      26   →      26              |        4.25 s  →        4.21 s    (-0.74%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.64 ms   (+0.19%) |      26   →      26              |       42.68 ms →       42.76 ms   (+0.19%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.32 ms →       88.28 ms   (-0.05%) |      26   →      26              |        2.30 s  →        2.30 s    (-0.05%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.09 ms →       88.05 ms   (-0.05%) |      26   →      26              |        2.29 s  →        2.29 s    (-0.05%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      275.46 ms →      274.16 ms   (-0.47%) |      26   →      26              |        7.16 s  →        7.13 s    (-0.47%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      275.46 ms →      274.15 ms   (-0.47%) |      26   →      26              |        7.16 s  →        7.13 s    (-0.47%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.08 ms →       24.33 ms   (+1.00%) |      26   →      26              |      626.18 ms →      632.46 ms   (+1.00%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      227.46 ms →      225.52 ms   (-0.86%) |      26   →      26              |        5.91 s  →        5.86 s    (-0.86%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       22.72 ms →       23.12 ms   (+1.77%) |      26   →      26              |      590.75 ms →      601.18 ms   (+1.77%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       81.04 ms →       81.18 ms   (+0.18%) |      26   →      26              |        2.11 s  →        2.11 s    (+0.18%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        7.75 ms →        8.73 ms  (+12.54%) |      26   →      26              |      201.60 ms →      226.89 ms  (+12.54%) | 
  │ │ ├ sirius::Density::mix                                            |      217.14 ms →      205.11 ms   (-5.54%) |      26   →      26              |        5.65 s  →        5.33 s    (-5.54%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      933.86 μs →      929.81 μs   (-0.43%) |      26   →      26              |       24.28 ms →       24.18 ms   (-0.43%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.63 ms →       10.37 ms   (-2.45%) |     334   →     320     (-4.19%) |        3.55 s  →        3.32 s    (-6.54%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.39 ms →        9.97 ms   (-4.08%) |     334   →     320     (-4.19%) |        3.47 s  →        3.19 s    (-8.10%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.39 ms →        9.97 ms   (-4.08%) |     334   →     320     (-4.19%) |        3.47 s  →        3.19 s    (-8.10%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        6.95 ms →        6.56 ms   (-5.65%) |      26   →      26              |      180.79 ms →      170.58 ms   (-5.65%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        6.14 ms →        5.73 ms   (-6.66%) |      26   →      26              |      159.74 ms →      149.10 ms   (-6.66%) | 
  │ │ ├ sirius::Potential::generate                                     |      579.38 ms →      579.15 ms   (-0.04%) |      26   →      26              |       15.06 s  →       15.06 s    (-0.04%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      138.58 ms →      137.45 ms   (-0.81%) |      26   →      26              |        3.60 s  →        3.57 s    (-0.81%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       18.85 ms →       19.08 ms   (+1.20%) |      26   →      26              |      490.10 ms →      495.99 ms   (+1.20%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.22 ms →       10.60 ms   (+3.66%) |      26   →      26              |      265.77 ms →      275.49 ms   (+3.66%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        9.96 ms →        9.88 ms   (-0.85%) |      26   →      26              |      259.04 ms →      256.83 ms   (-0.85%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        9.96 ms →        9.88 ms   (-0.85%) |      26   →      26              |      259.03 ms →      256.82 ms   (-0.85%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      561.99 μs →      547.24 μs   (-2.62%) |      52   →      52              |       29.22 ms →       28.46 ms   (-2.62%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       48.95 ms →       49.18 ms   (+0.47%) |      26   →      26              |        1.27 s  →        1.28 s    (+0.47%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.63 ms →       46.85 ms   (+0.47%) |      26   →      26              |        1.21 s  →        1.22 s    (+0.47%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.02 ms →        3.02 ms   (-0.09%) |      52   →      52              |      156.95 ms →      156.82 ms   (-0.09%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.37 ms →        5.41 ms   (+0.78%) |      26   →      26              |      139.55 ms →      140.64 ms   (+0.78%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.43 ms →        6.55 ms   (+1.93%) |      26   →      26              |      167.12 ms →      170.34 ms   (+1.93%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.93 ms →       91.02 ms   (+0.10%) |      26   →      26              |        2.36 s  →        2.37 s    (+0.10%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      292.08 ms →      292.59 ms   (+0.17%) |      26   →      26              |        7.59 s  →        7.61 s    (+0.17%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      280.51 ms →      280.11 ms   (-0.14%) |      26   →      26              |        7.29 s  →        7.28 s    (-0.14%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      280.51 ms →      280.11 ms   (-0.14%) |      26   →      26              |        7.29 s  →        7.28 s    (-0.14%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.34 ms →       27.43 ms   (+0.33%) |      26   →      26              |      710.89 ms →      713.24 ms   (+0.33%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      225.60 ms →      225.11 ms   (-0.21%) |      26   →      26              |        5.87 s  →        5.85 s    (-0.21%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.77 ms →       23.74 ms   (-0.14%) |      26   →      26              |      618.07 ms →      617.19 ms   (-0.14%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        6.06 ms →        5.45 ms  (-10.07%) |      26   →      26              |      157.45 ms →      141.60 ms  (-10.07%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.18 ms →       10.50 ms   (+3.14%) |     182   →     182              |        1.85 s  →        1.91 s    (+3.14%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.91 ms →        9.71 ms   (-2.05%) |     182   →     182              |        1.80 s  →        1.77 s    (-2.05%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.91 ms →        9.71 ms   (-2.05%) |     182   →     182              |        1.80 s  →        1.77 s    (-2.05%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.96 ms →       10.70 ms   (-2.34%) |      78   →      78              |      854.95 ms →      834.94 ms   (-2.34%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.70 ms →       10.09 ms   (-5.69%) |      78   →      78              |      834.93 ms →      787.39 ms   (-5.69%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        9.99 ms →        9.99 ms   (-0.01%) |      26   →      26              |      259.81 ms →      259.78 ms   (-0.01%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      108.70 μs →      129.90 μs  (+19.50%) |      26   →      26              |        2.83 ms →        3.38 ms  (+19.50%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      103.68 μs →      125.02 μs  (+20.58%) |      26   →      26              |        2.70 ms →        3.25 ms  (+20.58%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.08 ms →        5.02 ms   (-1.17%) |       2   →       2              |       10.16 ms →       10.04 ms   (-1.17%) | 
  │ ├ sirius::Periodic_function|inner                                   |        9.84 ms →       10.26 ms   (+4.28%) |       6   →       6              |       59.06 ms →       61.59 ms   (+4.28%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        9.83 ms →        9.84 ms   (+0.13%) |       6   →       6              |       58.97 ms →       59.05 ms   (+0.13%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        9.83 ms →        9.84 ms   (+0.13%) |       6   →       6              |       58.97 ms →       59.05 ms   (+0.13%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.55 ms →       10.64 ms   (+0.88%) |       3   →       3              |       31.65 ms →       31.93 ms   (+0.88%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.54 ms →       10.13 ms   (-3.91%) |       3   →       3              |       31.62 ms →       30.39 ms   (-3.91%) | 
  ├ sirius::Periodic_function|inner                                     |        9.69 ms →        9.95 ms   (+2.70%) |       2   →       2              |       19.37 ms →       19.89 ms   (+2.70%) | 
  │ └ sirius::Periodic_function|inner_local                             |        9.68 ms →        9.77 ms   (+0.94%) |       2   →       2              |       19.36 ms →       19.54 ms   (+0.94%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.68 ms →        9.77 ms   (+0.94%) |       2   →       2              |       19.36 ms →       19.54 ms   (+0.94%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.48 ms →       10.41 ms   (-0.62%) |       1   →       1              |       10.48 ms →       10.41 ms   (-0.62%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.45 ms →       10.13 ms   (-3.11%) |       1   →       1              |       10.45 ms →       10.13 ms   (-3.11%) | 
  └ sirius::finalize                                                    |      227.62 ms →      245.93 ms   (+8.05%) |       1   →       1              |      227.62 ms →      245.93 ms   (+8.05%) | 
  ====================================================================================================================================================================================================
```
