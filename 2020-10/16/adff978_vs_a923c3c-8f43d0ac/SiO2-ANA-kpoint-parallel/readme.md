# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      132.89 s  →      128.88 s    (-3.02%) |       1   →       1              |      132.89 s  →      128.88 s    (-3.02%) | 
  ├ sirius::initialize                                                  |        2.73 s  →        2.71 s    (-0.91%) |       1   →       1              |        2.73 s  →        2.71 s    (-0.91%) | 
  ├ sirius::Simulation_context::initialize                              |        2.93 s  →        2.91 s    (-0.47%) |       1   →       1              |        2.93 s  →        2.91 s    (-0.47%) | 
- │ ├ sirius::Simulation_context::init_comm                             |       10.90 ms →       17.61 ms  (+61.62%) |       1   →       1              |       10.90 ms →       17.61 ms  (+61.62%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      179.28 ms →      130.71 ms  (-27.09%) |       1   →       1              |      179.28 ms →      130.71 ms  (-27.09%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       77.43 ms →       53.83 ms  (-30.48%) |       2   →       2              |      154.86 ms →      107.66 ms  (-30.48%) | 
  │ │ └ sirius::Unit_cell::update                                       |       24.34 ms →       22.98 ms   (-5.59%) |       1   →       1              |       24.34 ms →       22.98 ms   (-5.59%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.25 ms →        6.37 ms   (+1.91%) |       1   →       1              |        6.25 ms →        6.37 ms   (+1.91%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       18.05 ms →       16.57 ms   (-8.23%) |       1   →       1              |       18.05 ms →       16.57 ms   (-8.23%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       18.03 ms →       16.55 ms   (-8.25%) |       1   →       1              |       18.03 ms →       16.55 ms   (-8.25%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.17 ms →        4.16 ms   (-0.24%) |       1   →       1              |        4.17 ms →        4.16 ms   (-0.24%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.29 ms →        2.35 ms   (+2.44%) |       1   →       1              |        2.29 ms →        2.35 ms   (+2.44%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      101.17 μs →      106.73 μs   (+5.49%) |       1   →       1              |      101.17 μs →      106.73 μs   (+5.49%) | 
  │ └ sirius::Simulation_context::update                                |        2.69 s  →        2.72 s    (+0.93%) |       1   →       1              |        2.69 s  →        2.72 s    (+0.93%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.67 ms →       10.73 ms   (+0.57%) |       1   →       1              |       10.67 ms →       10.73 ms   (+0.57%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.25 ms →        4.36 ms   (+2.51%) |       1   →       1              |        4.25 ms →        4.36 ms   (+2.51%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.38 ms →        6.34 ms   (-0.73%) |       1   →       1              |        6.38 ms →        6.34 ms   (-0.73%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.37 ms →        6.32 ms   (-0.73%) |       1   →       1              |        6.37 ms →        6.32 ms   (-0.73%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.88 ms →        3.83 ms   (-1.51%) |       1   →       1              |        3.88 ms →        3.83 ms   (-1.51%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.31 ms →        2.33 ms   (+0.59%) |       1   →       1              |        2.31 ms →        2.33 ms   (+0.59%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      100.78 μs →       99.32 μs   (-1.45%) |       1   →       1              |      100.78 μs →       99.32 μs   (-1.45%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       62.57 ms →       62.94 ms   (+0.58%) |       2   →       2              |      125.15 ms →      125.88 ms   (+0.58%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.15 ms →        5.25 ms   (+1.93%) |       2   →       2              |       10.30 ms →       10.49 ms   (+1.93%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.47 ms →        4.48 ms   (+0.28%) |       1   →       1              |        4.47 ms →        4.48 ms   (+0.28%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.75 ms →       21.86 ms   (+0.49%) |       2   →       2              |       43.50 ms →       43.72 ms   (+0.49%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.82 ms →       14.92 ms   (+0.65%) |       2   →       2              |       29.65 ms →       29.84 ms   (+0.65%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.67 ms →       19.76 ms   (+0.49%) |       4   →       4              |       78.67 ms →       79.06 ms   (+0.49%) | 
  │   ├ sddk::Gvec::init                                                |      177.59 ms →      175.36 ms   (-1.26%) |       2   →       2              |      355.19 ms →      350.71 ms   (-1.26%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      134.62 ms →      131.45 ms   (-2.36%) |       2   →       2              |      269.24 ms →      262.89 ms   (-2.36%) | 
  │   ├ sddk::Gvec_shells                                               |      164.37 ms →      180.40 ms   (+9.75%) |       1   →       1              |      164.37 ms →      180.40 ms   (+9.75%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.33 ms →        1.33 ms   (+0.40%) |       1   →       1              |        1.33 ms →        1.33 ms   (+0.40%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      295.68 ms →      293.00 ms   (-0.91%) |       2   →       2              |      591.36 ms →      586.00 ms   (-0.91%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       35.89 ms →       37.72 ms   (+5.11%) |       1   →       1              |       35.89 ms →       37.72 ms   (+5.11%) | 
  │ ├ sirius::K_point::K_point                                          |        2.42 μs →        2.54 μs   (+5.02%) |       4   →       4              |        9.69 μs →       10.18 μs   (+5.02%) | 
  │ └ sirius::K_point_set::initialize                                   |       35.78 ms →       37.62 ms   (+5.13%) |       1   →       1              |       35.78 ms →       37.62 ms   (+5.13%) | 
  │   └ sirius::K_point::initialize                                     |       35.69 ms →       37.52 ms   (+5.12%) |       1   →       1              |       35.69 ms →       37.52 ms   (+5.12%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       18.15 ms →       19.20 ms   (+5.79%) |       1   →       1              |       18.15 ms →       19.20 ms   (+5.79%) | 
  │     │ └ sddk::Gvec::init                                            |        8.16 ms →        8.62 ms   (+5.69%) |       1   →       1              |        8.16 ms →        8.62 ms   (+5.69%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |       10.08 μs →       10.31 μs   (+2.26%) |       1   →       1              |       10.08 μs →       10.31 μs   (+2.26%) | 
  │     └ sirius::K_point::update                                       |       12.74 ms →       13.16 ms   (+3.27%) |       1   →       1              |       12.74 ms →       13.16 ms   (+3.27%) | 
  │       └ sirius::Beta_projectors                                     |        6.45 ms →        6.45 ms   (-0.03%) |       1   →       1              |        6.45 ms →        6.45 ms   (-0.03%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.79 ms →        3.83 ms   (+1.10%) |       1   →       1              |        3.79 ms →        3.83 ms   (+1.10%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.38 ms →        5.45 ms   (+1.31%) |       2   →       2              |       10.76 ms →       10.90 ms   (+1.31%) | 
  ├ sirius::Potential                                                   |      155.40 ms →      162.43 ms   (+4.53%) |       1   →       1              |      155.40 ms →      162.43 ms   (+4.53%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.92 ms →        5.89 ms   (-0.58%) |       6   →       6              |       35.54 ms →       35.34 ms   (-0.58%) | 
  │ └ sirius::Potential::update                                         |      119.10 ms →      126.35 ms   (+6.08%) |       1   →       1              |      119.10 ms →      126.35 ms   (+6.08%) | 
  │   └ sirius::Potential::generate_local_potential                     |      118.38 ms →      125.55 ms   (+6.06%) |       1   →       1              |      118.38 ms →      125.55 ms   (+6.06%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      108.72 ms →      115.39 ms   (+6.14%) |       1   →       1              |      108.72 ms →      115.39 ms   (+6.14%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        8.66 ms →        9.20 ms   (+6.31%) |       1   →       1              |        8.66 ms →        9.20 ms   (+6.31%) | 
  ├ sirius::Density                                                     |      129.82 ms →      136.18 ms   (+4.90%) |       1   →       1              |      129.82 ms →      136.18 ms   (+4.90%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.24 ms →        5.19 ms   (-0.96%) |       2   →       2              |       10.48 ms →       10.38 ms   (-0.96%) | 
  │ └ sirius::Density::update                                           |      119.07 ms →      125.53 ms   (+5.43%) |       1   →       1              |      119.07 ms →      125.53 ms   (+5.43%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      118.64 ms →      125.11 ms   (+5.45%) |       1   →       1              |      118.64 ms →      125.11 ms   (+5.45%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |      102.93 μs →      102.91 μs   (-0.03%) |       1   →       1              |      102.93 μs →      102.91 μs   (-0.03%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      110.46 ms →      119.48 ms   (+8.17%) |       1   →       1              |      110.46 ms →      119.48 ms   (+8.17%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        7.61 ms →        5.07 ms  (-33.40%) |       1   →       1              |        7.61 ms →        5.07 ms  (-33.40%) | 
  ├ sirius::Density::initial_density                                    |      165.90 ms →      175.35 ms   (+5.70%) |       1   →       1              |      165.90 ms →      175.35 ms   (+5.70%) | 
- │ ├ sirius::Simulation_context::make_periodic_function                |      109.42 ms →      122.83 ms  (+12.26%) |       1   →       1              |      109.42 ms →      122.83 ms  (+12.26%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        6.12 ms →        4.89 ms  (-20.11%) |       2   →       2              |       12.23 ms →        9.77 ms  (-20.11%) | 
+ │ └ sirius::Periodic_function::integrate                              |       11.68 ms →        9.85 ms  (-15.71%) |       1   →       1              |       11.68 ms →        9.85 ms  (-15.71%) | 
  ├ sirius::Potential::generate                                         |      582.36 ms →      597.97 ms   (+2.68%) |       1   →       1              |      582.36 ms →      597.97 ms   (+2.68%) | 
  │ ├ sirius::Potential::poisson                                        |      127.05 ms →      138.41 ms   (+8.94%) |       1   →       1              |      127.05 ms →      138.41 ms   (+8.94%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        8.13 ms →        5.70 ms  (-29.94%) |       1   →       1              |        8.13 ms →        5.70 ms  (-29.94%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.01 ms →       10.35 ms   (+3.47%) |       1   →       1              |       10.01 ms →       10.35 ms   (+3.47%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        9.89 ms →        9.89 ms   (+0.03%) |       1   →       1              |        9.89 ms →        9.89 ms   (+0.03%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.88 ms →        9.89 ms   (+0.06%) |       1   →       1              |        9.88 ms →        9.89 ms   (+0.06%) | 
  │ ├ sirius::Periodic_function::add                                    |      557.29 μs →      550.66 μs   (-1.19%) |       2   →       2              |        1.11 ms →        1.10 ms   (-1.19%) | 
  │ ├ sirius::Potential::xc                                             |       54.12 ms →       53.85 ms   (-0.49%) |       1   →       1              |       54.12 ms →       53.85 ms   (-0.49%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.75 ms →       51.43 ms   (-0.63%) |       1   →       1              |       51.75 ms →       51.43 ms   (-0.63%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.71 ms →        5.77 ms   (+0.93%) |       2   →       2              |       11.43 ms →       11.53 ms   (+0.93%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.29 ms →        5.16 ms   (-2.41%) |       1   →       1              |        5.29 ms →        5.16 ms   (-2.41%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.84 ms →        5.83 ms   (-0.18%) |       1   →       1              |        5.84 ms →        5.83 ms   (-0.18%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.84 ms →       92.99 ms   (+0.15%) |       1   →       1              |       92.84 ms →       92.99 ms   (+0.15%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      300.01 ms →      304.39 ms   (+1.46%) |       1   →       1              |      300.01 ms →      304.39 ms   (+1.46%) | 
  ├ sirius::Hamiltonian0                                                |        8.46 ms →        8.84 ms   (+4.48%) |       1   →       1              |        8.46 ms →        8.84 ms   (+4.48%) | 
  │ ├ sirius::Local_operator                                            |        8.11 ms →        8.49 ms   (+4.70%) |       1   →       1              |        8.11 ms →        8.49 ms   (+4.70%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.84 ms →        4.62 ms   (-4.48%) |       1   →       1              |        4.84 ms →        4.62 ms   (-4.48%) | 
- │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.34 ms →        2.95 ms  (+25.86%) |       1   →       1              |        2.34 ms →        2.95 ms  (+25.86%) | 
  │ ├ sirius::Non_local_operator                                        |       63.21 μs →       62.51 μs   (-1.11%) |       2   →       2              |      126.43 μs →      125.02 μs   (-1.11%) | 
  │ ├ sirius::D_operator::initialize                                    |       92.81 μs →       90.55 μs   (-2.43%) |       1   →       1              |       92.81 μs →       90.55 μs   (-2.43%) | 
  │ └ sirius::Q_operator::initialize                                    |       74.79 μs →       76.26 μs   (+1.97%) |       1   →       1              |       74.79 μs →       76.26 μs   (+1.97%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.87 s  →        1.86 s    (-0.35%) |       1   →       1              |        1.87 s  →        1.86 s    (-0.35%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.68 ms →       18.70 ms   (+0.10%) |       1   →       1              |       18.68 ms →       18.70 ms   (+0.10%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      187.87 μs →      187.22 μs   (-0.35%) |       1   →       1              |      187.87 μs →      187.22 μs   (-0.35%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       18.49 ms →       18.51 ms   (+0.11%) |       1   →       1              |       18.49 ms →       18.51 ms   (+0.11%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.85 s  →        1.85 s    (-0.35%) |       1   →       1              |        1.85 s  →        1.85 s    (-0.35%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      129.97 ms →      126.83 ms   (-2.42%) |       4   →       4              |      519.90 ms →      507.32 ms   (-2.42%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       53.23 ms →       53.98 ms   (+1.40%) |       1   →       1              |       53.23 ms →       53.98 ms   (+1.40%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.48 ms →       21.69 ms   (+0.99%) |       1   →       1              |       21.48 ms →       21.69 ms   (+0.99%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      635.26 ms →      637.58 ms   (+0.36%) |       1   →       1              |      635.26 ms →      637.58 ms   (+0.36%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      298.11 ms →      297.78 ms   (-0.11%) |       1   →       1              |      298.11 ms →      297.78 ms   (-0.11%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.36 μs →        3.67 μs   (+9.19%) |       1   →       1              |        3.36 μs →        3.67 μs   (+9.19%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.41 μs →        2.62 μs   (+8.59%) |       1   →       1              |        2.41 μs →        2.62 μs   (+8.59%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      360.00 ns →      375.00 ns   (+4.17%) |       1   →       1              |      360.00 ns →      375.00 ns   (+4.17%) | 
- │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      481.00 ns →      549.00 ns  (+14.14%) |       1   →       1              |      481.00 ns →      549.00 ns  (+14.14%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.22 ms →        9.22 ms   (-0.02%) |       1   →       1              |        9.22 ms →        9.22 ms   (-0.02%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      120.88 ms →      121.81 ms   (+0.77%) |       1   →       1              |      120.88 ms →      121.81 ms   (+0.77%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      103.50 ms →      104.36 ms   (+0.83%) |       2   →       2              |      207.00 ms →      208.72 ms   (+0.83%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       40.14 ms →       40.22 ms   (+0.21%) |       2   →       2              |       80.27 ms →       80.44 ms   (+0.21%) | 
  │ │ │ └ sddk::wf_inner                                                |       39.57 ms →       39.66 ms   (+0.22%) |       2   →       2              |       79.15 ms →       79.32 ms   (+0.22%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       19.50 ns →       36.50 ns  (+87.18%) |       2   →       2              |       39.00 ns →       73.00 ns  (+87.18%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       39.10 ms →       39.19 ms   (+0.22%) |       2   →       2              |       78.20 ms →       78.37 ms   (+0.22%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       19.00 ns →       26.00 ns  (+36.84%) |       2   →       2              |       38.00 ns →       52.00 ns  (+36.84%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       56.82 ms →       57.01 ms   (+0.33%) |       1   →       1              |       56.82 ms →       57.01 ms   (+0.33%) | 
  │ │ └ sddk::wf_trans                                                  |       30.73 ms →       30.75 ms   (+0.05%) |       1   →       1              |       30.73 ms →       30.75 ms   (+0.05%) | 
  │ │   └ sddk::wf_trans|pw                                             |       30.73 ms →       30.75 ms   (+0.05%) |       1   →       1              |       30.73 ms →       30.75 ms   (+0.05%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      568.00 ns →      432.00 ns  (-23.94%) |       1   →       1              |      568.00 ns →      432.00 ns  (-23.94%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      123.25 s  →      119.23 s    (-3.26%) |       1   →       1              |      123.25 s  →      119.23 s    (-3.26%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.85 ms →        5.90 ms   (+0.87%) |      19   →      19              |      111.17 ms →      112.14 ms   (+0.87%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.72 s  →        4.57 s    (-3.19%) |      26   →      26              |      122.75 s  →      118.83 s    (-3.19%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        5.14 ms →        4.67 ms   (-9.07%) |      26   →      26              |      133.65 ms →      121.53 ms   (-9.07%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.77 ms →        4.31 ms   (-9.52%) |      26   →      26              |      123.93 ms →      112.14 ms   (-9.52%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      964.45 μs →      985.24 μs   (+2.16%) |      26   →      26              |       25.08 ms →       25.62 ms   (+2.16%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.91 ms →        2.44 ms  (-16.18%) |      26   →      26              |       75.75 ms →       63.49 ms  (-16.18%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.65 μs →       64.10 μs   (-0.86%) |      52   →      52              |        3.36 ms →        3.33 ms   (-0.86%) | 
+ │ │ │ ├ sirius::D_operator::initialize                                |       96.17 μs →       86.08 μs  (-10.50%) |      26   →      26              |        2.50 ms →        2.24 ms  (-10.50%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       78.26 μs →       77.55 μs   (-0.90%) |      26   →      26              |        2.03 ms →        2.02 ms   (-0.90%) | 
  │ │ ├ sirius::Band::solve                                             |        2.75 s  →        2.60 s    (-5.73%) |      26   →      26              |       71.59 s  →       67.49 s    (-5.73%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      151.46 μs →      151.67 μs   (+0.14%) |      26   →      26              |        3.94 ms →        3.94 ms   (+0.14%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      144.92 μs →      145.00 μs   (+0.05%) |      26   →      26              |        3.77 ms →        3.77 ms   (+0.05%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.67 μs →        4.73 μs   (+1.38%) |      26   →      26              |      121.34 μs →      123.01 μs   (+1.38%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.59 s  →        2.47 s    (-4.77%) |      26   →      26              |       67.40 s  →       64.18 s    (-4.77%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       95.90 ms →       94.42 ms   (-1.55%) |      26   →      26              |        2.49 s  →        2.45 s    (-1.55%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.75 ms →        7.62 ms   (-1.72%) |     156   →     156              |        1.21 s  →        1.19 s    (-1.72%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        6.00 ms →        5.97 ms   (-0.54%) |      26   →      26              |      155.97 ms →      155.14 ms   (-0.54%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      349.79 μs →      350.26 μs   (+0.14%) |      26   →      26              |        9.09 ms →        9.11 ms   (+0.14%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.33 ms →        2.31 ms   (-0.83%) |      52   →      52              |      120.92 ms →      119.91 ms   (-0.83%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.45 s  →        2.33 s    (-4.97%) |      26   →      26              |       63.82 s  →       60.64 s    (-4.97%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      129.05 ms →      137.21 ms   (+6.32%) |     271   →     262     (-3.32%) |       34.97 s  →       35.95 s    (+2.79%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       51.89 ms →       55.41 ms   (+6.78%) |     271   →     262     (-3.32%) |       14.06 s  →       14.52 s    (+3.23%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.87 μs →        1.96 μs   (+4.86%) |     271   →     262     (-3.32%) |      506.21 μs →      513.18 μs   (+1.38%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.56 μs →        1.67 μs   (+7.23%) |     271   →     262     (-3.32%) |      422.48 μs →      437.97 μs   (+3.67%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      324.57 ns →      369.38 ns  (+13.81%) |     271   →     262     (-3.32%) |       87.96 μs →       96.78 μs  (+10.03%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      390.75 ns →      440.00 ns  (+12.61%) |     271   →     262     (-3.32%) |      105.89 μs →      115.28 μs   (+8.87%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.43 ms →        7.46 ms   (+0.38%) |     271   →     262     (-3.32%) |        2.01 s  →        1.95 s    (-2.95%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       23.21 ms →       25.29 ms   (+8.96%) |     271   →     262     (-3.32%) |        6.29 s  →        6.63 s    (+5.34%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       23.26 ms →       24.52 ms   (+5.45%) |     542   →     524     (-3.32%) |       12.60 s  →       12.85 s    (+1.95%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       34.88 ms →       35.90 ms   (+2.91%) |     271   →     262     (-3.32%) |        9.45 s  →        9.40 s    (-0.51%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        6.05 ms →        6.23 ms   (+2.95%) |     516   →     498     (-3.49%) |        3.12 s  →        3.10 s    (-0.64%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       74.71 ns →       59.93 ns  (-19.78%) |     516   →     498     (-3.49%) |       38.55 μs →       29.85 μs  (-22.58%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        4.94 ms →        5.11 ms   (+3.59%) |     516   →     498     (-3.49%) |        2.55 s  →        2.55 s    (-0.02%) | 
+ │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       51.49 ns →       28.00 ns  (-45.62%) |     516   →     498     (-3.49%) |       26.57 μs →       13.94 μs  (-47.52%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      628.47 μs →      666.73 μs   (+6.09%) |     271   →     262     (-3.32%) |      170.32 ms →      174.68 ms   (+2.56%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        9.76 ms →       10.31 ms   (+5.63%) |     271   →     262     (-3.32%) |        2.64 s  →        2.70 s    (+2.12%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |       14.35 ms →       14.52 ms   (+1.20%) |     245   →     236     (-3.67%) |        3.51 s  →        3.43 s    (-2.52%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        4.78 ms →        4.84 ms   (+1.20%) |     735   →     708     (-3.67%) |        3.51 s  →        3.43 s    (-2.52%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       10.50 ms →       10.40 ms   (-0.97%) |     271   →     262     (-3.32%) |        2.85 s  →        2.72 s    (-4.26%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |       10.23 ms →       10.19 ms   (-0.36%) |     271   →     262     (-3.32%) |        2.77 s  →        2.67 s    (-3.67%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       47.27 ns →       28.49 ns  (-39.72%) |     271   →     262     (-3.32%) |       12.81 μs →        7.47 μs  (-41.72%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        9.11 ms →        9.08 ms   (-0.40%) |     271   →     262     (-3.32%) |        2.47 s  →        2.38 s    (-3.71%) | 
+ │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       71.30 ns →       48.73 ns  (-31.66%) |     271   →     262     (-3.32%) |       19.32 μs →       12.77 μs  (-33.93%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       33.07 ms →       17.83 ms  (-46.07%) |     271   →     262     (-3.32%) |        8.96 s  →        4.67 s   (-47.86%) | 
  │ │ │ │   ├ sirius::residuals                                         |       13.76 ms →       13.16 ms   (-4.37%) |     262   →     252     (-3.82%) |        3.61 s  →        3.32 s    (-8.02%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       12.42 ms →       11.72 ms   (-5.64%) |     252   →     242     (-3.97%) |        3.13 s  →        2.84 s    (-9.38%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        6.21 ms →        5.86 ms   (-5.64%) |     504   →     484     (-3.97%) |        3.13 s  →        2.84 s    (-9.38%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.63 ms →        1.72 ms   (+5.45%) |     252   →     242     (-3.97%) |      410.37 ms →      415.55 ms   (+1.26%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       74.93 ms →       53.75 ms  (-28.26%) |      53   →      85    (+60.38%) |        3.97 s  →        4.57 s   (+15.06%) | 
- │ │ │ │     └ sddk::wf_trans                                          |       49.40 ms →       31.46 ms  (-36.31%) |      80   →     144    (+80.00%) |        3.95 s  →        4.53 s   (+14.64%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |       36.93 ms →       22.32 ms  (-39.58%) |     107   →     203    (+89.72%) |        3.95 s  →        4.53 s   (+14.63%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      652.46 ns →      426.73 ns  (-34.60%) |      26   →      26              |       16.96 μs →       11.10 μs  (-34.60%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       29.39 μs →       78.56 μs (+167.33%) |      26   →      26              |      764.06 μs →        2.04 ms (+167.33%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      594.62 μs →      612.78 μs   (+3.05%) |      26   →      26              |       15.46 ms →       15.93 ms   (+3.05%) | 
  │ │ ├ sirius::Density::generate                                       |      778.15 ms →      773.84 ms   (-0.55%) |      26   →      26              |       20.23 s  →       20.12 s    (-0.55%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      401.49 ms →      402.38 ms   (+0.22%) |      26   →      26              |       10.44 s  →       10.46 s    (+0.22%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        7.98 μs →        9.08 μs  (+13.74%) |      26   →      26              |      207.60 μs →      236.12 μs  (+13.74%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.45 μs →        8.59 μs  (+15.29%) |      26   →      26              |      193.66 μs →      223.28 μs  (+15.29%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |      100.18 ms →      100.49 ms   (+0.31%) |      26   →      26              |        2.60 s  →        2.61 s    (+0.31%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.28 μs →        7.81 μs   (+7.29%) |      26   →      26              |      189.27 μs →      203.07 μs   (+7.29%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.12 ms →        7.12 ms   (-0.01%) |      26   →      26              |      185.14 ms →      185.12 ms   (-0.01%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       91.14 ms →       91.39 ms   (+0.27%) |      26   →      26              |        2.37 s  →        2.38 s    (+0.27%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      763.38 ns →      551.46 ns  (-27.76%) |      26   →      26              |       19.85 μs →       14.34 μs  (-27.76%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      161.67 ms →      162.75 ms   (+0.67%) |      26   →      26              |        4.20 s  →        4.23 s    (+0.67%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.65 ms →        1.64 ms   (-0.66%) |      26   →      26              |       42.94 ms →       42.66 ms   (-0.66%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.29 ms →       88.30 ms   (+0.01%) |      26   →      26              |        2.30 s  →        2.30 s    (+0.01%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.04 ms →       88.07 ms   (+0.03%) |      26   →      26              |        2.29 s  →        2.29 s    (+0.03%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      274.61 ms →      279.76 ms   (+1.87%) |      26   →      26              |        7.14 s  →        7.27 s    (+1.87%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      274.61 ms →      279.76 ms   (+1.87%) |      26   →      26              |        7.14 s  →        7.27 s    (+1.87%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.35 ms →       26.18 ms   (+7.52%) |      26   →      26              |      633.04 ms →      680.62 ms   (+7.52%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      226.15 ms →      226.04 ms   (-0.05%) |      26   →      26              |        5.88 s  →        5.88 s    (-0.05%) | 
- │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       22.92 ms →       26.34 ms  (+14.95%) |      26   →      26              |      595.83 ms →      684.89 ms  (+14.95%) | 
+ │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       92.95 ms →       81.60 ms  (-12.21%) |      26   →      26              |        2.42 s  →        2.12 s   (-12.21%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        5.51 ms →        6.51 ms  (+18.24%) |      26   →      26              |      143.22 ms →      169.34 ms  (+18.24%) | 
  │ │ ├ sirius::Density::mix                                            |      217.13 ms →      211.68 ms   (-2.51%) |      26   →      26              |        5.65 s  →        5.50 s    (-2.51%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      978.23 μs →      923.76 μs   (-5.57%) |      26   →      26              |       25.43 ms →       24.02 ms   (-5.57%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.59 ms →       10.18 ms   (-3.86%) |     334   →     334              |        3.54 s  →        3.40 s    (-3.86%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.39 ms →        9.96 ms   (-4.14%) |     334   →     334              |        3.47 s  →        3.33 s    (-4.14%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.39 ms →        9.96 ms   (-4.14%) |     334   →     334              |        3.47 s  →        3.33 s    (-4.14%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        6.22 ms →        6.27 ms   (+0.82%) |      26   →      26              |      161.73 ms →      163.05 ms   (+0.82%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.37 ms →        5.41 ms   (+0.79%) |      26   →      26              |      139.66 ms →      140.76 ms   (+0.79%) | 
  │ │ ├ sirius::Potential::generate                                     |      567.43 ms →      579.58 ms   (+2.14%) |      26   →      26              |       14.75 s  →       15.07 s    (+2.14%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      126.30 ms →      137.74 ms   (+9.05%) |      26   →      26              |        3.28 s  →        3.58 s    (+9.05%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        7.48 ms →        5.23 ms  (-30.08%) |      26   →      26              |      194.58 ms →      136.04 ms  (-30.08%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.22 ms →       10.27 ms   (+0.44%) |      26   →      26              |      265.84 ms →      267.02 ms   (+0.44%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        9.92 ms →        9.98 ms   (+0.62%) |      26   →      26              |      257.95 ms →      259.54 ms   (+0.62%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        9.92 ms →        9.98 ms   (+0.62%) |      26   →      26              |      257.93 ms →      259.53 ms   (+0.62%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      557.87 μs →      587.19 μs   (+5.26%) |      52   →      52              |       29.01 ms →       30.53 ms   (+5.26%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       49.10 ms →       48.72 ms   (-0.77%) |      26   →      26              |        1.28 s  →        1.27 s    (-0.77%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.74 ms →       46.35 ms   (-0.83%) |      26   →      26              |        1.22 s  →        1.21 s    (-0.83%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.00 ms →        3.05 ms   (+1.67%) |      52   →      52              |      156.15 ms →      158.76 ms   (+1.67%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.41 ms →        5.23 ms   (-3.40%) |      26   →      26              |      140.75 ms →      135.96 ms   (-3.40%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.54 ms →        6.55 ms   (+0.18%) |      26   →      26              |      170.01 ms →      170.31 ms   (+0.18%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.93 ms →       91.07 ms   (+0.16%) |      26   →      26              |        2.36 s  →        2.37 s    (+0.16%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      292.16 ms →      293.03 ms   (+0.30%) |      26   →      26              |        7.60 s  →        7.62 s    (+0.30%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      279.74 ms →      287.15 ms   (+2.65%) |      26   →      26              |        7.27 s  →        7.47 s    (+2.65%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      279.73 ms →      287.15 ms   (+2.65%) |      26   →      26              |        7.27 s  →        7.47 s    (+2.65%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.57 ms →       29.61 ms   (+7.41%) |      26   →      26              |      716.75 ms →      769.84 ms   (+7.41%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      224.24 ms →      227.19 ms   (+1.31%) |      26   →      26              |        5.83 s  →        5.91 s    (+1.31%) | 
- │ │ │   └ sddk::Gvec_shells::remap_backward                           |       24.11 ms →       26.56 ms  (+10.14%) |      26   →      26              |      626.97 ms →      690.53 ms  (+10.14%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.76 ms →        5.18 ms  (-10.10%) |      26   →      26              |      149.68 ms →      134.56 ms  (-10.10%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.12 ms →       10.03 ms   (-0.86%) |     182   →     182              |        1.84 s  →        1.83 s    (-0.86%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.83 ms →        9.77 ms   (-0.62%) |     182   →     182              |        1.79 s  →        1.78 s    (-0.62%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.83 ms →        9.77 ms   (-0.62%) |     182   →     182              |        1.79 s  →        1.78 s    (-0.62%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.87 ms →       10.42 ms   (-4.12%) |      78   →      78              |      847.76 ms →      812.84 ms   (-4.12%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.63 ms →       10.16 ms   (-4.41%) |      78   →      78              |      829.25 ms →      792.71 ms   (-4.41%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        9.91 ms →        9.95 ms   (+0.39%) |      26   →      26              |      257.77 ms →      258.78 ms   (+0.39%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      110.62 μs →      135.26 μs  (+22.28%) |      26   →      26              |        2.88 ms →        3.52 ms  (+22.28%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      105.59 μs →      130.56 μs  (+23.65%) |      26   →      26              |        2.75 ms →        3.39 ms  (+23.65%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.06 ms →        5.33 ms   (+5.31%) |       2   →       2              |       10.13 ms →       10.67 ms   (+5.31%) | 
  │ ├ sirius::Periodic_function|inner                                   |        9.71 ms →       10.09 ms   (+3.98%) |       6   →       6              |       58.23 ms →       60.55 ms   (+3.98%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        9.69 ms →        9.70 ms   (+0.06%) |       6   →       6              |       58.15 ms →       58.18 ms   (+0.06%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        9.69 ms →        9.70 ms   (+0.06%) |       6   →       6              |       58.15 ms →       58.18 ms   (+0.06%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.62 ms →       10.45 ms   (-1.55%) |       3   →       3              |       31.86 ms →       31.36 ms   (-1.55%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.56 ms →       10.11 ms   (-4.29%) |       3   →       3              |       31.68 ms →       30.32 ms   (-4.29%) | 
  ├ sirius::Periodic_function|inner                                     |        9.73 ms →       10.03 ms   (+3.12%) |       2   →       2              |       19.46 ms →       20.07 ms   (+3.12%) | 
  │ └ sirius::Periodic_function|inner_local                             |        9.64 ms →        9.65 ms   (+0.12%) |       2   →       2              |       19.28 ms →       19.30 ms   (+0.12%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.64 ms →        9.65 ms   (+0.12%) |       2   →       2              |       19.28 ms →       19.30 ms   (+0.12%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.52 ms →       10.47 ms   (-0.48%) |       1   →       1              |       10.52 ms →       10.47 ms   (-0.48%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.46 ms →       10.08 ms   (-3.64%) |       1   →       1              |       10.46 ms →       10.08 ms   (-3.64%) | 
  └ sirius::finalize                                                    |      221.22 ms →      222.26 ms   (+0.47%) |       1   →       1              |      221.22 ms →      222.26 ms   (+0.47%) | 
  ====================================================================================================================================================================================================
```
