# Benchmark 440e4baa3b03646988c956603d0cb2cbea939e9f vs f641654ae8bc5cecb285c326c4cb5850ab38d32a
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
- sirius                                                                |      128.55 s  →      141.42 s   (+10.01%) |       1   →       1              |      128.55 s  →      141.42 s   (+10.01%) | 
  ├ sirius::initialize                                                  |        2.76 s  →        2.85 s    (+3.06%) |       1   →       1              |        2.76 s  →        2.85 s    (+3.06%) | 
  ├ sirius::Simulation_context::initialize                              |        2.89 s  →        2.91 s    (+0.58%) |       1   →       1              |        2.89 s  →        2.91 s    (+0.58%) | 
  │ ├ sirius::Simulation_context::init_comm                             |      210.80 μs →      199.26 μs   (-5.48%) |       1   →       1              |      210.80 μs →      199.26 μs   (-5.48%) | 
  │ ├ sirius::Unit_cell::initialize                                     |      165.30 ms →      151.24 ms   (-8.51%) |       1   →       1              |      165.30 ms →      151.24 ms   (-8.51%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       70.68 ms →       63.60 ms  (-10.02%) |       2   →       2              |      141.36 ms →      127.20 ms  (-10.02%) | 
  │ │ └ sirius::Unit_cell::update                                       |       23.86 ms →       23.97 ms   (+0.43%) |       1   →       1              |       23.86 ms →       23.97 ms   (+0.43%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        5.98 ms →        6.43 ms   (+7.63%) |       1   →       1              |        5.98 ms →        6.43 ms   (+7.63%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       17.85 ms →       17.49 ms   (-2.04%) |       1   →       1              |       17.85 ms →       17.49 ms   (-2.04%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       17.83 ms →       17.47 ms   (-2.04%) |       1   →       1              |       17.83 ms →       17.47 ms   (-2.04%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.15 ms →        4.14 ms   (-0.36%) |       1   →       1              |        4.15 ms →        4.14 ms   (-0.36%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.31 ms →        2.34 ms   (+1.34%) |       1   →       1              |        2.31 ms →        2.34 ms   (+1.34%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      101.18 μs →      104.18 μs   (+2.97%) |       1   →       1              |      101.18 μs →      104.18 μs   (+2.97%) | 
  │ └ sirius::Simulation_context::update                                |        2.69 s  →        2.72 s    (+1.19%) |       1   →       1              |        2.69 s  →        2.72 s    (+1.19%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.87 ms →       10.82 ms   (-0.47%) |       1   →       1              |       10.87 ms →       10.82 ms   (-0.47%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.47 ms →        4.44 ms   (-0.61%) |       1   →       1              |        4.47 ms →        4.44 ms   (-0.61%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.36 ms →        6.34 ms   (-0.40%) |       1   →       1              |        6.36 ms →        6.34 ms   (-0.40%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.35 ms →        6.32 ms   (-0.40%) |       1   →       1              |        6.35 ms →        6.32 ms   (-0.40%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.85 ms →        3.82 ms   (-0.70%) |       1   →       1              |        3.85 ms →        3.82 ms   (-0.70%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.33 ms   (+0.10%) |       1   →       1              |        2.33 ms →        2.33 ms   (+0.10%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       99.13 μs →       99.17 μs   (+0.04%) |       1   →       1              |       99.13 μs →       99.17 μs   (+0.04%) | 
- │   ├ sirius::Radial_integrals|aug                                    |       62.81 ms →       76.01 ms  (+21.03%) |       2   →       2              |      125.61 ms →      152.03 ms  (+21.03%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.13 ms →        5.30 ms   (+3.37%) |       2   →       2              |       10.26 ms →       10.60 ms   (+3.37%) | 
- │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.47 ms →        4.96 ms  (+10.97%) |       1   →       1              |        4.47 ms →        4.96 ms  (+10.97%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.69 ms →       21.70 ms   (+0.02%) |       2   →       2              |       43.38 ms →       43.39 ms   (+0.02%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.82 ms →       15.02 ms   (+1.37%) |       2   →       2              |       29.64 ms →       30.04 ms   (+1.37%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.69 ms →       19.57 ms   (-0.61%) |       4   →       4              |       78.76 ms →       78.28 ms   (-0.61%) | 
  │   ├ sddk::Gvec::init                                                |      174.48 ms →      172.57 ms   (-1.09%) |       2   →       2              |      348.95 ms →      345.15 ms   (-1.09%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      132.01 ms →      129.82 ms   (-1.66%) |       2   →       2              |      264.02 ms →      259.65 ms   (-1.66%) | 
  │   ├ sddk::Gvec_shells                                               |      180.47 ms →      169.49 ms   (-6.08%) |       1   →       1              |      180.47 ms →      169.49 ms   (-6.08%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.37 ms →        1.32 ms   (-3.95%) |       1   →       1              |        1.37 ms →        1.32 ms   (-3.95%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      293.59 ms →      291.69 ms   (-0.65%) |       2   →       2              |      587.17 ms →      583.37 ms   (-0.65%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       35.71 ms →       35.44 ms   (-0.73%) |       1   →       1              |       35.71 ms →       35.44 ms   (-0.73%) | 
  │ ├ sirius::K_point::K_point                                          |        2.49 μs →        2.72 μs   (+9.15%) |       4   →       4              |        9.96 μs →       10.88 μs   (+9.15%) | 
  │ └ sirius::K_point_set::initialize                                   |       35.60 ms →       35.34 ms   (-0.73%) |       1   →       1              |       35.60 ms →       35.34 ms   (-0.73%) | 
  │   └ sirius::K_point::initialize                                     |       35.49 ms →       35.25 ms   (-0.68%) |       1   →       1              |       35.49 ms →       35.25 ms   (-0.68%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       17.96 ms →       17.92 ms   (-0.25%) |       1   →       1              |       17.96 ms →       17.92 ms   (-0.25%) | 
  │     │ └ sddk::Gvec::init                                            |        8.04 ms →        8.03 ms   (-0.15%) |       1   →       1              |        8.04 ms →        8.03 ms   (-0.15%) | 
+ │     ├ sddk::matrix_storage::matrix_storage                          |        9.69 μs →        6.89 μs  (-28.90%) |       1   →       1              |        9.69 μs →        6.89 μs  (-28.90%) | 
  │     └ sirius::K_point::update                                       |       12.51 ms →       12.54 ms   (+0.27%) |       1   →       1              |       12.51 ms →       12.54 ms   (+0.27%) | 
  │       └ sirius::Beta_projectors                                     |        6.20 ms →        6.32 ms   (+1.84%) |       1   →       1              |        6.20 ms →        6.32 ms   (+1.84%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.60 ms →        3.70 ms   (+2.76%) |       1   →       1              |        3.60 ms →        3.70 ms   (+2.76%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.43 ms →        5.34 ms   (-1.73%) |       2   →       2              |       10.87 ms →       10.68 ms   (-1.73%) | 
  ├ sirius::Potential                                                   |      154.91 ms →      158.65 ms   (+2.41%) |       1   →       1              |      154.91 ms →      158.65 ms   (+2.41%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.84 ms →        5.73 ms   (-1.94%) |       6   →       6              |       35.05 ms →       34.37 ms   (-1.94%) | 
  │ └ sirius::Potential::update                                         |      119.12 ms →      123.56 ms   (+3.72%) |       1   →       1              |      119.12 ms →      123.56 ms   (+3.72%) | 
  │   └ sirius::Potential::generate_local_potential                     |      118.32 ms →      122.85 ms   (+3.83%) |       1   →       1              |      118.32 ms →      122.85 ms   (+3.83%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      106.33 ms →      114.40 ms   (+7.58%) |       1   →       1              |      106.33 ms →      114.40 ms   (+7.58%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       11.09 ms →        7.56 ms  (-31.81%) |       1   →       1              |       11.09 ms →        7.56 ms  (-31.81%) | 
  ├ sirius::Density                                                     |      127.50 ms →      132.02 ms   (+3.55%) |       1   →       1              |      127.50 ms →      132.02 ms   (+3.55%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.11 ms →        5.25 ms   (+2.80%) |       2   →       2              |       10.21 ms →       10.50 ms   (+2.80%) | 
  │ └ sirius::Density::update                                           |      117.01 ms →      121.25 ms   (+3.63%) |       1   →       1              |      117.01 ms →      121.25 ms   (+3.63%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      116.57 ms →      120.84 ms   (+3.67%) |       1   →       1              |      116.57 ms →      120.84 ms   (+3.67%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |       74.02 μs →       74.03 μs   (+0.00%) |       1   →       1              |       74.02 μs →       74.03 μs   (+0.00%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      105.95 ms →      113.80 ms   (+7.41%) |       1   →       1              |      105.95 ms →      113.80 ms   (+7.41%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       10.09 ms →        6.53 ms  (-35.33%) |       1   →       1              |       10.09 ms →        6.53 ms  (-35.33%) | 
  ├ sirius::Density::initial_density                                    |      165.15 ms →      178.98 ms   (+8.37%) |       1   →       1              |      165.15 ms →      178.98 ms   (+8.37%) | 
- │ ├ sirius::Simulation_context::make_periodic_function                |      108.59 ms →      122.21 ms  (+12.54%) |       1   →       1              |      108.59 ms →      122.21 ms  (+12.54%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        6.48 ms →        6.20 ms   (-4.36%) |       2   →       2              |       12.97 ms →       12.40 ms   (-4.36%) | 
- │ └ sirius::Periodic_function::integrate                              |       10.79 ms →       12.00 ms  (+11.20%) |       1   →       1              |       10.79 ms →       12.00 ms  (+11.20%) | 
  ├ sirius::Potential::generate                                         |      582.56 ms →      591.70 ms   (+1.57%) |       1   →       1              |      582.56 ms →      591.70 ms   (+1.57%) | 
  │ ├ sirius::Potential::poisson                                        |      126.28 ms →      136.40 ms   (+8.01%) |       1   →       1              |      126.28 ms →      136.40 ms   (+8.01%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        8.45 ms →        5.67 ms  (-32.92%) |       1   →       1              |        8.45 ms →        5.67 ms  (-32.92%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.93 ms →       10.25 ms   (-6.27%) |       1   →       1              |       10.93 ms →       10.25 ms   (-6.27%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |       10.15 ms →       10.23 ms   (+0.71%) |       1   →       1              |       10.15 ms →       10.23 ms   (+0.71%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |       10.15 ms →       10.22 ms   (+0.70%) |       1   →       1              |       10.15 ms →       10.22 ms   (+0.70%) | 
  │ ├ sirius::Periodic_function::add                                    |      560.72 μs →      548.84 μs   (-2.12%) |       2   →       2              |        1.12 ms →        1.10 ms   (-2.12%) | 
  │ ├ sirius::Potential::xc                                             |       55.08 ms →       53.96 ms   (-2.04%) |       1   →       1              |       55.08 ms →       53.96 ms   (-2.04%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       52.66 ms →       51.69 ms   (-1.84%) |       1   →       1              |       52.66 ms →       51.69 ms   (-1.84%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.70 ms →        5.64 ms   (-1.01%) |       2   →       2              |       11.40 ms →       11.29 ms   (-1.01%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.80 ms →        5.39 ms   (-7.09%) |       1   →       1              |        5.80 ms →        5.39 ms   (-7.09%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.87 ms →        5.72 ms   (-2.58%) |       1   →       1              |        5.87 ms →        5.72 ms   (-2.58%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.73 ms →       93.74 ms   (+1.10%) |       1   →       1              |       92.73 ms →       93.74 ms   (+1.10%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      300.10 ms →      299.46 ms   (-0.21%) |       1   →       1              |      300.10 ms →      299.46 ms   (-0.21%) | 
  ├ sirius::Hamiltonian0                                                |        8.44 ms →        8.54 ms   (+1.18%) |       1   →       1              |        8.44 ms →        8.54 ms   (+1.18%) | 
  │ ├ sirius::Local_operator                                            |        8.08 ms →        8.19 ms   (+1.30%) |       1   →       1              |        8.08 ms →        8.19 ms   (+1.30%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.74 ms →        4.75 ms   (+0.22%) |       1   →       1              |        4.74 ms →        4.75 ms   (+0.22%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.43 ms →        2.53 ms   (+4.21%) |       1   →       1              |        2.43 ms →        2.53 ms   (+4.21%) | 
  │ ├ sirius::Non_local_operator                                        |       62.77 μs →       62.77 μs   (+0.01%) |       2   →       2              |      125.54 μs →      125.55 μs   (+0.01%) | 
  │ ├ sirius::D_operator::initialize                                    |       94.49 μs →       94.49 μs   (-0.01%) |       1   →       1              |       94.49 μs →       94.49 μs   (-0.01%) | 
  │ └ sirius::Q_operator::initialize                                    |       76.94 μs →       74.01 μs   (-3.80%) |       1   →       1              |       76.94 μs →       74.01 μs   (-3.80%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.87 s  →        1.84 s    (-1.51%) |       1   →       1              |        1.87 s  →        1.84 s    (-1.51%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.70 ms →       18.74 ms   (+0.23%) |       1   →       1              |       18.70 ms →       18.74 ms   (+0.23%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      183.93 μs →      185.43 μs   (+0.81%) |       1   →       1              |      183.93 μs →      185.43 μs   (+0.81%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       18.51 ms →       18.55 ms   (+0.22%) |       1   →       1              |       18.51 ms →       18.55 ms   (+0.22%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.85 s  →        1.82 s    (-1.53%) |       1   →       1              |        1.85 s  →        1.82 s    (-1.53%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      128.07 ms →      126.15 ms   (-1.50%) |       4   →       4              |      512.27 ms →      504.60 ms   (-1.50%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       52.20 ms →       52.37 ms   (+0.32%) |       1   →       1              |       52.20 ms →       52.37 ms   (+0.32%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       20.99 ms →       21.19 ms   (+0.99%) |       1   →       1              |       20.99 ms →       21.19 ms   (+0.99%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      636.88 ms →      635.99 ms   (-0.14%) |       1   →       1              |      636.88 ms →      635.99 ms   (-0.14%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      297.98 ms →      297.65 ms   (-0.11%) |       1   →       1              |      297.98 ms →      297.65 ms   (-0.11%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.16 μs →        3.43 μs   (+8.38%) |       1   →       1              |        3.16 μs →        3.43 μs   (+8.38%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.18 μs →        2.41 μs  (+10.89%) |       1   →       1              |        2.18 μs →        2.41 μs  (+10.89%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      357.00 ns →      347.00 ns   (-2.80%) |       1   →       1              |      357.00 ns →      347.00 ns   (-2.80%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      524.00 ns →      546.00 ns   (+4.20%) |       1   →       1              |      524.00 ns →      546.00 ns   (+4.20%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.22 ms →        9.21 ms   (-0.10%) |       1   →       1              |        9.22 ms →        9.21 ms   (-0.10%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      120.83 ms →      121.11 ms   (+0.23%) |       1   →       1              |      120.83 ms →      121.11 ms   (+0.23%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      104.40 ms →      103.99 ms   (-0.40%) |       2   →       2              |      208.81 ms →      207.98 ms   (-0.40%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       40.31 ms →       40.28 ms   (-0.07%) |       2   →       2              |       80.62 ms →       80.56 ms   (-0.07%) | 
  │ │ │ └ sddk::wf_inner                                                |       39.74 ms →       39.71 ms   (-0.09%) |       2   →       2              |       79.49 ms →       79.42 ms   (-0.09%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       12.00 ns →       19.50 ns  (+62.50%) |       2   →       2              |       24.00 ns →       39.00 ns  (+62.50%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       39.26 ms →       39.23 ms   (-0.07%) |       2   →       2              |       78.52 ms →       78.47 ms   (-0.07%) | 
+ │ │ │   └ sddk::wf_inner|scale_back                                   |       25.50 ns →       16.50 ns  (-35.29%) |       2   →       2              |       51.00 ns →       33.00 ns  (-35.29%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       56.86 ms →       56.43 ms   (-0.75%) |       1   →       1              |       56.86 ms →       56.43 ms   (-0.75%) | 
  │ │ └ sddk::wf_trans                                                  |       30.76 ms →       30.74 ms   (-0.05%) |       1   →       1              |       30.76 ms →       30.74 ms   (-0.05%) | 
  │ │   └ sddk::wf_trans|pw                                             |       30.75 ms →       30.73 ms   (-0.06%) |       1   →       1              |       30.75 ms →       30.73 ms   (-0.06%) | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      396.00 ns →      468.00 ns  (+18.18%) |       1   →       1              |      396.00 ns →      468.00 ns  (+18.18%) | 
- ├ sirius::DFT_ground_state::scf_loop                                  |      118.90 s  →      131.72 s   (+10.78%) |       1   →       1              |      118.90 s  →      131.72 s   (+10.78%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.89 ms →        5.73 ms   (-2.73%) |      17   →      17              |      100.13 ms →       97.40 ms   (-2.73%) | 
- │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.56 s  →        6.91 s   (+51.66%) |      26   →      19    (-26.92%) |      118.46 s  →      131.29 s   (+10.83%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        4.59 ms →        5.78 ms  (+25.94%) |      26   →      19    (-26.92%) |      119.32 ms →      109.81 ms   (-7.97%) | 
- │ │ │ ├ sirius::Local_operator                                        |        4.22 ms →        5.41 ms  (+28.11%) |      26   →      19    (-26.92%) |      109.83 ms →      102.82 ms   (-6.38%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function                            |      970.92 μs →      978.54 μs   (+0.79%) |      26   →      19    (-26.92%) |       25.24 ms →       18.59 ms  (-26.35%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.30 ms →        3.54 ms  (+53.98%) |      26   →      19    (-26.92%) |       59.77 ms →       67.25 ms  (+12.53%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |       64.85 μs →       63.96 μs   (-1.37%) |      52   →      38    (-26.92%) |        3.37 ms →        2.43 ms  (-27.92%) | 
+ │ │ │ ├ sirius::D_operator::initialize                                |       88.87 μs →       88.77 μs   (-0.11%) |      26   →      19    (-26.92%) |        2.31 ms →        1.69 ms  (-27.01%) | 
+ │ │ │ └ sirius::Q_operator::initialize                                |       78.01 μs →       77.81 μs   (-0.25%) |      26   →      19    (-26.92%) |        2.03 ms →        1.48 ms  (-27.10%) | 
- │ │ ├ sirius::Band::solve                                             |        2.65 s  →        5.01 s   (+88.66%) |      26   →      19    (-26.92%) |       69.03 s  →       95.17 s   (+37.87%) | 
+ │ │ │ ├ sirius::Hamiltonian_k                                         |      156.11 μs →      154.21 μs   (-1.22%) |      26   →      19    (-26.92%) |        4.06 ms →        2.93 ms  (-27.81%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      149.79 μs →      147.43 μs   (-1.58%) |      26   →      19    (-26.92%) |        3.89 ms →        2.80 ms  (-28.07%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.53 μs →        4.70 μs   (+3.74%) |      26   →      19    (-26.92%) |      117.87 μs →       89.36 μs  (-24.19%) | 
- │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.53 s  →        4.97 s   (+96.08%) |      26   →      19    (-26.92%) |       65.84 s  →       94.34 s   (+43.29%) | 
- │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       94.72 ms →      112.41 ms  (+18.67%) |      26   →      19    (-26.92%) |        2.46 s  →        2.14 s   (-13.28%) | 
- │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.66 ms →       10.36 ms  (+35.30%) |     156   →     114    (-26.92%) |        1.19 s  →        1.18 s    (-1.13%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        6.10 ms →        6.03 ms   (-1.12%) |      26   →      19    (-26.92%) |      158.64 ms →      114.63 ms  (-27.74%) | 
+ │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      347.25 μs →      351.25 μs   (+1.15%) |      26   →      19    (-26.92%) |        9.03 ms →        6.67 ms  (-26.08%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.38 ms →        2.33 ms   (-1.90%) |      52   →      38    (-26.92%) |      123.60 ms →       88.61 ms  (-28.31%) | 
- │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.40 s  →        4.81 s  (+100.83%) |      26   →      19    (-26.92%) |       62.29 s  →       91.41 s   (+46.76%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      136.62 ms →      175.53 ms  (+28.48%) |     262   →     271     (+3.44%) |       35.79 s  →       47.57 s   (+32.89%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       55.54 ms →       74.12 ms  (+33.45%) |     262   →     271     (+3.44%) |       14.55 s  →       20.09 s   (+38.04%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.88 μs →        2.06 μs   (+9.63%) |     262   →     271     (+3.44%) |      493.37 μs →      559.45 μs  (+13.39%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.59 μs →        1.77 μs  (+10.84%) |     262   →     271     (+3.44%) |      417.81 μs →      479.00 μs  (+14.65%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      449.85 ns →      414.37 ns   (-7.89%) |     262   →     271     (+3.44%) |      117.86 μs →      112.29 μs   (-4.72%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      437.84 ns →      404.04 ns   (-7.72%) |     262   →     271     (+3.44%) |      114.71 μs →      109.50 μs   (-4.55%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.46 ms →        7.58 ms   (+1.73%) |     262   →     271     (+3.44%) |        1.95 s  →        2.06 s    (+5.22%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       24.83 ms →       32.35 ms  (+30.31%) |     262   →     271     (+3.44%) |        6.50 s  →        8.77 s   (+34.79%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       24.39 ms →       30.73 ms  (+25.98%) |     524   →     542     (+3.44%) |       12.78 s  →       16.66 s   (+30.31%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |       42.53 ms →       61.78 ms  (+45.25%) |     262   →     271     (+3.44%) |       11.14 s  →       16.74 s   (+50.24%) | 
- │ │ │ │   │ ├ sddk::wf_inner                                          |        6.22 ms →        8.50 ms  (+36.67%) |     498   →     523     (+5.02%) |        3.10 s  →        4.45 s   (+43.53%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       49.34 ns →       71.71 ns  (+45.34%) |     498   →     523     (+5.02%) |       24.57 μs →       37.50 μs  (+52.64%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        5.11 ms →        7.39 ms  (+44.63%) |     498   →     523     (+5.02%) |        2.54 s  →        3.86 s   (+51.89%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       49.04 ns →       53.61 ns   (+9.31%) |     498   →     523     (+5.02%) |       24.42 μs →       28.04 μs  (+14.80%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |        7.34 ms →       10.19 ms  (+38.86%) |     262   →     271     (+3.44%) |        1.92 s  →        2.76 s   (+43.63%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       10.30 ms →       13.60 ms  (+31.97%) |     262   →     271     (+3.44%) |        2.70 s  →        3.68 s   (+36.50%) | 
- │ │ │ │   │ └ sddk::wf_trans                                          |       14.50 ms →       23.21 ms  (+60.03%) |     236   →     252     (+6.78%) |        3.42 s  →        5.85 s   (+70.88%) | 
- │ │ │ │   │   └ sddk::wf_trans|pw                                     |        4.83 ms →        7.74 ms  (+60.04%) |     708   →     756     (+6.78%) |        3.42 s  →        5.85 s   (+70.89%) | 
- │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       10.57 ms →       15.50 ms  (+46.70%) |     262   →     271     (+3.44%) |        2.77 s  →        4.20 s   (+51.73%) | 
- │ │ │ │   │ └ sddk::wf_inner                                          |       10.18 ms →       15.12 ms  (+48.58%) |     262   →     271     (+3.44%) |        2.67 s  →        4.10 s   (+53.68%) | 
- │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       43.23 ns →       69.66 ns  (+61.13%) |     262   →     271     (+3.44%) |       11.33 μs →       18.88 μs  (+66.67%) | 
- │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        9.06 ms →       14.01 ms  (+54.51%) |     262   →     271     (+3.44%) |        2.37 s  →        3.80 s   (+59.81%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       21.18 ns →       74.39 ns (+251.31%) |     262   →     271     (+3.44%) |        5.55 μs →       20.16 μs (+263.37%) | 
- │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       17.91 ms →       27.64 ms  (+54.30%) |     262   →     271     (+3.44%) |        4.69 s  →        7.49 s   (+59.60%) | 
- │ │ │ │   ├ sirius::residuals                                         |       13.14 ms →       25.89 ms  (+96.95%) |     252   →     258     (+2.38%) |        3.31 s  →        6.68 s  (+101.64%) | 
- │ │ │ │   │ ├ sddk::wf_trans                                          |       11.71 ms →       23.02 ms  (+96.64%) |     242   →     256     (+5.79%) |        2.83 s  →        5.89 s  (+108.02%) | 
- │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        5.85 ms →       11.51 ms  (+96.67%) |     484   →     512     (+5.79%) |        2.83 s  →        5.89 s  (+108.04%) | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.72 ms →        2.61 ms  (+51.89%) |     242   →     256     (+5.79%) |      415.11 ms →      666.96 ms  (+60.67%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       53.74 ms →       89.92 ms  (+67.32%) |      85   →      97    (+14.12%) |        4.57 s  →        8.72 s   (+90.94%) | 
- │ │ │ │     └ sddk::wf_trans                                          |       31.46 ms →       49.51 ms  (+57.37%) |     144   →     175    (+21.53%) |        4.53 s  →        8.66 s   (+91.25%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |       22.32 ms →       34.25 ms  (+53.46%) |     203   →     253    (+24.63%) |        4.53 s  →        8.66 s   (+91.26%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      410.27 ns →      453.32 ns  (+10.49%) |      26   →      19    (-26.92%) |       10.67 μs →        8.61 μs  (-19.26%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       35.47 μs →       83.73 μs (+136.05%) |      26   →      19    (-26.92%) |      922.18 μs →        1.59 ms  (+72.50%) | 
+ │ │ ├ sirius::K_point_set::find_band_occupancies                      |      608.90 μs →      600.78 μs   (-1.33%) |      26   →      19    (-26.92%) |       15.83 ms →       11.41 ms  (-27.90%) | 
+ │ │ ├ sirius::Density::generate                                       |      768.88 ms →      767.07 ms   (-0.24%) |      26   →      19    (-26.92%) |       19.99 s  →       14.57 s   (-27.10%) | 
+ │ │ │ ├ sirius::Density::generate_valence                             |      402.25 ms →      403.22 ms   (+0.24%) |      26   →      19    (-26.92%) |       10.46 s  →        7.66 s   (-26.75%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.79 μs →        2.97 μs  (-21.57%) |      26   →      19    (-26.92%) |       98.47 μs →       56.44 μs  (-42.68%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.46 μs →        2.69 μs  (-22.43%) |      26   →      19    (-26.92%) |       90.02 μs →       51.03 μs  (-43.31%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |      100.33 ms →      100.44 ms   (+0.11%) |      26   →      19    (-26.92%) |        2.61 s  →        1.91 s   (-26.84%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       11.30 μs →        9.99 μs  (-11.54%) |      26   →      19    (-26.92%) |      293.70 μs →      189.85 μs  (-35.36%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.13 ms →        7.12 ms   (-0.04%) |      26   →      19    (-26.92%) |      185.30 ms →      135.36 ms  (-26.95%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       91.29 ms →       91.37 ms   (+0.09%) |      26   →      19    (-26.92%) |        2.37 s  →        1.74 s   (-26.86%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      551.69 ns →      551.58 ns   (-0.02%) |      26   →      19    (-26.92%) |       14.34 μs →       10.48 μs  (-26.94%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      162.44 ms →      162.53 ms   (+0.05%) |      26   →      19    (-26.92%) |        4.22 s  →        3.09 s   (-26.88%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.65 ms →        1.64 ms   (-0.27%) |      26   →      19    (-26.92%) |       42.79 ms →       31.18 ms  (-27.12%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |       88.25 ms →       88.27 ms   (+0.02%) |      26   →      19    (-26.92%) |        2.29 s  →        1.68 s   (-26.91%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.03 ms →       88.04 ms   (+0.02%) |      26   →      19    (-26.92%) |        2.29 s  →        1.67 s   (-26.91%) | 
+ │ │ │ ├ sirius::Field4D::symmetrize                                   |      273.06 ms →      270.46 ms   (-0.95%) |      26   →      19    (-26.92%) |        7.10 s  →        5.14 s   (-27.62%) | 
+ │ │ │ │ └ sirius::symmetrize_function|fpw                             |      273.05 ms →      270.46 ms   (-0.95%) |      26   →      19    (-26.92%) |        7.10 s  →        5.14 s   (-27.62%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       27.14 ms →       25.21 ms   (-7.11%) |      26   →      19    (-26.92%) |      705.66 ms →      479.01 ms  (-32.12%) | 
+ │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      221.55 ms →      220.67 ms   (-0.39%) |      26   →      19    (-26.92%) |        5.76 s  →        4.19 s   (-27.21%) | 
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       23.17 ms →       23.36 ms   (+0.79%) |      26   →      19    (-26.92%) |      602.50 ms →      443.76 ms  (-26.35%) | 
+ │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       81.10 ms →       81.35 ms   (+0.31%) |      26   →      19    (-26.92%) |        2.11 s  →        1.55 s   (-26.70%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        8.88 ms →        8.44 ms   (-5.00%) |      26   →      19    (-26.92%) |      230.93 ms →      160.31 ms  (-30.58%) | 
+ │ │ ├ sirius::Density::mix                                            |      154.94 ms →      154.60 ms   (-0.23%) |      26   →      19    (-26.92%) |        4.03 s  →        2.94 s   (-27.09%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      969.50 μs →      972.07 μs   (+0.26%) |      26   →      19    (-26.92%) |       25.21 ms →       18.47 ms  (-26.73%) | 
+ │ │ │ ├ sirius::Periodic_function|inner                               |       10.14 ms →       10.79 ms   (+6.42%) |     334   →     229    (-31.44%) |        3.39 s  →        2.47 s   (-27.03%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner_local                       |        9.82 ms →       10.41 ms   (+5.97%) |     334   →     229    (-31.44%) |        3.28 s  →        2.38 s   (-27.34%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        9.82 ms →       10.41 ms   (+5.97%) |     334   →     229    (-31.44%) |        3.28 s  →        2.38 s   (-27.34%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        6.43 ms →        6.34 ms   (-1.35%) |      26   →      19    (-26.92%) |      167.12 ms →      120.48 ms  (-27.91%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.38 ms →        5.30 ms   (-1.46%) |      26   →      19    (-26.92%) |      139.93 ms →      100.76 ms  (-27.99%) | 
+ │ │ ├ sirius::Potential::generate                                     |      567.10 ms →      578.46 ms   (+2.00%) |      26   →      19    (-26.92%) |       14.74 s  →       10.99 s   (-25.46%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |      125.84 ms →      136.98 ms   (+8.85%) |      26   →      19    (-26.92%) |        3.27 s  →        2.60 s   (-20.45%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        8.30 ms →        5.71 ms  (-31.26%) |      26   →      19    (-26.92%) |      215.77 ms →      108.40 ms  (-49.76%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner                             |       10.46 ms →       10.38 ms   (-0.82%) |      26   →      19    (-26.92%) |      272.06 ms →      197.18 ms  (-27.52%) | 
+ │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.25 ms →       10.21 ms   (-0.35%) |      26   →      19    (-26.92%) |      266.40 ms →      194.00 ms  (-27.18%) | 
+ │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.25 ms →       10.21 ms   (-0.35%) |      26   →      19    (-26.92%) |      266.38 ms →      193.98 ms  (-27.18%) | 
+ │ │ │ ├ sirius::Periodic_function::add                                |      546.35 μs →      547.96 μs   (+0.29%) |      52   →      38    (-26.92%) |       28.41 ms →       20.82 ms  (-26.71%) | 
+ │ │ │ ├ sirius::Potential::xc                                         |       49.02 ms →       49.35 ms   (+0.68%) |      26   →      19    (-26.92%) |        1.27 s  →      937.68 ms  (-26.43%) | 
+ │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.67 ms →       47.01 ms   (+0.71%) |      26   →      19    (-26.92%) |        1.21 s  →      893.11 ms  (-26.40%) | 
+ │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.07 ms →        3.04 ms   (-0.89%) |      52   →      38    (-26.92%) |      159.71 ms →      115.68 ms  (-27.57%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.30 ms →        5.72 ms   (+7.89%) |      26   →      19    (-26.92%) |      137.81 ms →      108.65 ms  (-21.16%) | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.50 ms →        6.46 ms   (-0.66%) |      26   →      19    (-26.92%) |      169.00 ms →      122.68 ms  (-27.41%) | 
+ │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.88 ms →       90.97 ms   (+0.10%) |      26   →      19    (-26.92%) |        2.36 s  →        1.73 s   (-26.85%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      292.47 ms →      292.29 ms   (-0.06%) |      26   →      19    (-26.92%) |        7.60 s  →        5.55 s   (-26.97%) | 
+ │ │ ├ sirius::Field4D::symmetrize                                     |      280.88 ms →      272.77 ms   (-2.89%) |      26   →      19    (-26.92%) |        7.30 s  →        5.18 s   (-29.03%) | 
+ │ │ │ └ sirius::symmetrize_function|fpw                               |      280.88 ms →      272.76 ms   (-2.89%) |      26   →      19    (-26.92%) |        7.30 s  →        5.18 s   (-29.03%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       29.39 ms →       27.23 ms   (-7.35%) |      26   →      19    (-26.92%) |      764.18 ms →      517.37 ms  (-32.30%) | 
+ │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      223.47 ms →      217.88 ms   (-2.50%) |      26   →      19    (-26.92%) |        5.81 s  →        4.14 s   (-28.75%) | 
+ │ │ │   └ sddk::Gvec_shells::remap_backward                           |       24.18 ms →       23.88 ms   (-1.27%) |      26   →      19    (-26.92%) |      628.81 ms →      453.66 ms  (-27.85%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        8.80 ms →        5.43 ms  (-38.36%) |      26   →      19    (-26.92%) |      228.92 ms →      103.11 ms  (-54.96%) | 
+ │ │ ├ sirius::Periodic_function|inner                                 |       10.70 ms →       10.78 ms   (+0.68%) |     182   →     133    (-26.92%) |        1.95 s  →        1.43 s   (-26.43%) | 
+ │ │ │ └ sirius::Periodic_function|inner_local                         |       10.25 ms →       10.42 ms   (+1.71%) |     182   →     133    (-26.92%) |        1.86 s  →        1.39 s   (-25.68%) | 
+ │ │ │   └ sirius::Smooth_periodic_function|inner_local                |       10.25 ms →       10.42 ms   (+1.71%) |     182   →     133    (-26.92%) |        1.86 s  →        1.39 s   (-25.67%) | 
+ │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.07 ms →       10.19 ms   (+1.22%) |      78   →      57    (-26.92%) |      785.43 ms →      580.99 ms  (-26.03%) | 
+ │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        9.80 ms →        9.81 ms   (+0.06%) |      78   →      57    (-26.92%) |      764.51 ms →      558.99 ms  (-26.88%) | 
+ │ │ ├ sirius::Periodic_function::integrate                            |        9.95 ms →        9.99 ms   (+0.40%) |      26   →      19    (-26.92%) |      258.66 ms →      189.78 ms  (-26.63%) | 
+ │ │ └ sirius::Density::get_magnetisation                              |      167.13 μs →      115.65 μs  (-30.80%) |      26   →      19    (-26.92%) |        4.35 ms →        2.20 ms  (-49.43%) | 
+ │ │   └ sirius::Density::compute_atomic_mag_mom                       |      162.38 μs →      111.12 μs  (-31.57%) |      26   →      19    (-26.92%) |        4.22 ms →        2.11 ms  (-49.99%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.17 ms →        5.30 ms   (+2.50%) |       2   →       2              |       10.33 ms →       10.59 ms   (+2.50%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.17 ms →       10.48 ms   (+3.05%) |       6   →       6              |       61.01 ms →       62.87 ms   (+3.05%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.10 ms →       10.45 ms   (+3.42%) |       6   →       6              |       60.62 ms →       62.69 ms   (+3.42%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.10 ms →       10.45 ms   (+3.42%) |       6   →       6              |       60.61 ms →       62.69 ms   (+3.42%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        9.72 ms →        9.88 ms   (+1.62%) |       3   →       3              |       29.16 ms →       29.64 ms   (+1.62%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.63 ms →        9.87 ms   (+2.50%) |       3   →       3              |       28.88 ms →       29.60 ms   (+2.50%) | 
  ├ sirius::Periodic_function|inner                                     |       10.18 ms →       10.45 ms   (+2.74%) |       2   →       2              |       20.35 ms →       20.91 ms   (+2.74%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.14 ms →       10.45 ms   (+2.99%) |       2   →       2              |       20.28 ms →       20.89 ms   (+2.99%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.14 ms →       10.45 ms   (+2.99%) |       2   →       2              |       20.28 ms →       20.89 ms   (+2.99%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        9.86 ms →       10.14 ms   (+2.81%) |       1   →       1              |        9.86 ms →       10.14 ms   (+2.81%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        9.68 ms →       10.13 ms   (+4.68%) |       1   →       1              |        9.68 ms →       10.13 ms   (+4.68%) | 
+ └ sirius::finalize                                                    |      236.16 ms →      185.90 ms  (-21.28%) |       1   →       1              |      236.16 ms →      185.90 ms  (-21.28%) | 
  ====================================================================================================================================================================================================
```
