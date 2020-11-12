# Benchmark 0c261670dec9b96a58dd74a9134f19b00042d6d1 vs 8465163e5150bf9c73ec5dac4bf03576202704b3
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      130.79 s  →      129.34 s    (-1.11%) |       1   →       1              |      130.79 s  →      129.34 s    (-1.11%) | 
  ├ sirius::initialize                                                  |        2.69 s  →        2.69 s    (+0.07%) |       1   →       1              |        2.69 s  →        2.69 s    (+0.07%) | 
  ├ sirius::Simulation_context::initialize                              |        2.92 s  →        2.96 s    (+1.22%) |       1   →       1              |        2.92 s  →        2.96 s    (+1.22%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       99.09 ms →       65.59 ms  (-33.81%) |       1   →       1              |       99.09 ms →       65.59 ms  (-33.81%) | 
- │ ├ sirius::Unit_cell::initialize                                     |       80.21 ms →      134.63 ms  (+67.84%) |       1   →       1              |       80.21 ms →      134.63 ms  (+67.84%) | 
- │ │ ├ sirius::Atom_type::init                                         |       28.33 ms →       55.33 ms  (+95.34%) |       2   →       2              |       56.65 ms →      110.67 ms  (+95.34%) | 
  │ │ └ sirius::Unit_cell::update                                       |       23.49 ms →       23.89 ms   (+1.70%) |       1   →       1              |       23.49 ms →       23.89 ms   (+1.70%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.32 ms →        6.25 ms   (-1.07%) |       1   →       1              |        6.32 ms →        6.25 ms   (-1.07%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       17.13 ms →       17.59 ms   (+2.68%) |       1   →       1              |       17.13 ms →       17.59 ms   (+2.68%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       17.11 ms →       17.56 ms   (+2.68%) |       1   →       1              |       17.11 ms →       17.56 ms   (+2.68%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.14 ms →        4.16 ms   (+0.60%) |       1   →       1              |        4.14 ms →        4.16 ms   (+0.60%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.34 ms   (+0.65%) |       1   →       1              |        2.32 ms →        2.34 ms   (+0.65%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      104.27 μs →      105.48 μs   (+1.16%) |       1   →       1              |      104.27 μs →      105.48 μs   (+1.16%) | 
  │ └ sirius::Simulation_context::update                                |        2.70 s  →        2.71 s    (+0.52%) |       1   →       1              |        2.70 s  →        2.71 s    (+0.52%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.74 ms →       10.76 ms   (+0.17%) |       1   →       1              |       10.74 ms →       10.76 ms   (+0.17%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.32 ms →        4.37 ms   (+1.29%) |       1   →       1              |        4.32 ms →        4.37 ms   (+1.29%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.39 ms →        6.35 ms   (-0.60%) |       1   →       1              |        6.39 ms →        6.35 ms   (-0.60%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.37 ms →        6.33 ms   (-0.61%) |       1   →       1              |        6.37 ms →        6.33 ms   (-0.61%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.88 ms →        3.84 ms   (-1.00%) |       1   →       1              |        3.88 ms →        3.84 ms   (-1.00%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.32 ms   (+0.33%) |       1   →       1              |        2.32 ms →        2.32 ms   (+0.33%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      109.27 μs →      101.45 μs   (-7.16%) |       1   →       1              |      109.27 μs →      101.45 μs   (-7.16%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       64.14 ms →       62.76 ms   (-2.15%) |       2   →       2              |      128.28 ms →      125.53 ms   (-2.15%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.18 ms →        5.22 ms   (+0.73%) |       2   →       2              |       10.37 ms →       10.45 ms   (+0.73%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.47 ms →        4.48 ms   (+0.37%) |       1   →       1              |        4.47 ms →        4.48 ms   (+0.37%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       22.47 ms →       21.81 ms   (-2.93%) |       2   →       2              |       44.93 ms →       43.62 ms   (-2.93%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.85 ms →       14.87 ms   (+0.13%) |       2   →       2              |       29.70 ms →       29.73 ms   (+0.13%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.68 ms →       19.61 ms   (-0.36%) |       4   →       4              |       78.73 ms →       78.45 ms   (-0.36%) | 
  │   ├ sddk::Gvec::init                                                |      170.59 ms →      174.08 ms   (+2.05%) |       2   →       2              |      341.18 ms →      348.17 ms   (+2.05%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      128.15 ms →      130.85 ms   (+2.11%) |       2   →       2              |      256.30 ms →      261.70 ms   (+2.11%) | 
  │   ├ sddk::Gvec_shells                                               |      161.99 ms →      174.63 ms   (+7.81%) |       1   →       1              |      161.99 ms →      174.63 ms   (+7.81%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.32 ms →        1.31 ms   (-0.58%) |       1   →       1              |        1.32 ms →        1.31 ms   (-0.58%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      294.13 ms →      291.60 ms   (-0.86%) |       2   →       2              |      588.26 ms →      583.21 ms   (-0.86%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       35.36 ms →       36.26 ms   (+2.54%) |       1   →       1              |       35.36 ms →       36.26 ms   (+2.54%) | 
  │ ├ sirius::K_point::K_point                                          |        2.57 μs →        2.59 μs   (+1.01%) |       4   →       4              |       10.27 μs →       10.37 μs   (+1.01%) | 
  │ └ sirius::K_point_set::initialize                                   |       35.24 ms →       36.13 ms   (+2.52%) |       1   →       1              |       35.24 ms →       36.13 ms   (+2.52%) | 
  │   └ sirius::K_point::initialize                                     |       35.15 ms →       36.04 ms   (+2.53%) |       1   →       1              |       35.15 ms →       36.04 ms   (+2.53%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       17.95 ms →       18.56 ms   (+3.39%) |       1   →       1              |       17.95 ms →       18.56 ms   (+3.39%) | 
  │     │ └ sddk::Gvec::init                                            |        8.06 ms →        8.06 ms   (+0.09%) |       1   →       1              |        8.06 ms →        8.06 ms   (+0.09%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        8.92 μs →        9.42 μs   (+5.66%) |       1   →       1              |        8.92 μs →        9.42 μs   (+5.66%) | 
  │     └ sirius::K_point::update                                       |       12.25 ms →       12.62 ms   (+2.99%) |       1   →       1              |       12.25 ms →       12.62 ms   (+2.99%) | 
  │       └ sirius::Beta_projectors                                     |        6.06 ms →        6.36 ms   (+4.90%) |       1   →       1              |        6.06 ms →        6.36 ms   (+4.90%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.61 ms →        3.72 ms   (+3.06%) |       1   →       1              |        3.61 ms →        3.72 ms   (+3.06%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.35 ms →        5.43 ms   (+1.47%) |       2   →       2              |       10.71 ms →       10.86 ms   (+1.47%) | 
  ├ sirius::Potential                                                   |      163.04 ms →      159.30 ms   (-2.30%) |       1   →       1              |      163.04 ms →      159.30 ms   (-2.30%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.92 ms →        5.75 ms   (-2.91%) |       6   →       6              |       35.53 ms →       34.49 ms   (-2.91%) | 
  │ └ sirius::Potential::update                                         |      126.77 ms →      124.08 ms   (-2.13%) |       1   →       1              |      126.77 ms →      124.08 ms   (-2.13%) | 
  │   └ sirius::Potential::generate_local_potential                     |      125.98 ms →      123.34 ms   (-2.09%) |       1   →       1              |      125.98 ms →      123.34 ms   (-2.09%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      116.37 ms →      116.11 ms   (-0.22%) |       1   →       1              |      116.37 ms →      116.11 ms   (-0.22%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        8.70 ms →        6.33 ms  (-27.22%) |       1   →       1              |        8.70 ms →        6.33 ms  (-27.22%) | 
  ├ sirius::Density                                                     |      136.98 ms →      136.78 ms   (-0.14%) |       1   →       1              |      136.98 ms →      136.78 ms   (-0.14%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.20 ms →        5.20 ms   (-0.12%) |       2   →       2              |       10.41 ms →       10.39 ms   (-0.12%) | 
  │ └ sirius::Density::update                                           |      126.29 ms →      126.12 ms   (-0.14%) |       1   →       1              |      126.29 ms →      126.12 ms   (-0.14%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      125.86 ms →      125.71 ms   (-0.12%) |       1   →       1              |      125.86 ms →      125.71 ms   (-0.12%) | 
- │     ├ sirius::rho_core_ri_pseudo|values                             |      105.84 μs →      140.47 μs  (+32.72%) |       1   →       1              |      105.84 μs →      140.47 μs  (+32.72%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      119.25 ms →      120.04 ms   (+0.67%) |       1   →       1              |      119.25 ms →      120.04 ms   (+0.67%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        6.04 ms →        5.10 ms  (-15.63%) |       1   →       1              |        6.04 ms →        5.10 ms  (-15.63%) | 
  ├ sirius::Density::initial_density                                    |      176.49 ms →      176.26 ms   (-0.13%) |       1   →       1              |      176.49 ms →      176.26 ms   (-0.13%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      124.19 ms →      124.29 ms   (+0.07%) |       1   →       1              |      124.19 ms →      124.29 ms   (+0.07%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.13 ms →        4.92 ms   (-4.07%) |       2   →       2              |       10.26 ms →        9.84 ms   (-4.07%) | 
  │ └ sirius::Periodic_function::integrate                              |       10.04 ms →        9.90 ms   (-1.43%) |       1   →       1              |       10.04 ms →        9.90 ms   (-1.43%) | 
  ├ sirius::Potential::generate                                         |      594.09 ms →      594.70 ms   (+0.10%) |       1   →       1              |      594.09 ms →      594.70 ms   (+0.10%) | 
  │ ├ sirius::Potential::poisson                                        |      138.75 ms →      138.92 ms   (+0.12%) |       1   →       1              |      138.75 ms →      138.92 ms   (+0.12%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.98 ms →        5.20 ms  (-12.96%) |       1   →       1              |        5.98 ms →        5.20 ms  (-12.96%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.31 ms →       10.29 ms   (-0.12%) |       1   →       1              |       10.31 ms →       10.29 ms   (-0.12%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        9.89 ms →       10.28 ms   (+3.92%) |       1   →       1              |        9.89 ms →       10.28 ms   (+3.92%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.88 ms →       10.27 ms   (+3.93%) |       1   →       1              |        9.88 ms →       10.27 ms   (+3.93%) | 
  │ ├ sirius::Periodic_function::add                                    |      549.13 μs →      543.37 μs   (-1.05%) |       2   →       2              |        1.10 ms →        1.09 ms   (-1.05%) | 
  │ ├ sirius::Potential::xc                                             |       54.23 ms →       55.54 ms   (+2.42%) |       1   →       1              |       54.23 ms →       55.54 ms   (+2.42%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.81 ms →       53.23 ms   (+2.75%) |       1   →       1              |       51.81 ms →       53.23 ms   (+2.75%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.78 ms →        5.63 ms   (-2.64%) |       2   →       2              |       11.56 ms →       11.26 ms   (-2.64%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.36 ms →        5.70 ms   (+6.29%) |       1   →       1              |        5.36 ms →        5.70 ms   (+6.29%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.93 ms →        5.74 ms   (-3.27%) |       1   →       1              |        5.93 ms →        5.74 ms   (-3.27%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.68 ms →       92.61 ms   (-0.07%) |       1   →       1              |       92.68 ms →       92.61 ms   (-0.07%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      300.02 ms →      299.47 ms   (-0.18%) |       1   →       1              |      300.02 ms →      299.47 ms   (-0.18%) | 
  ├ sirius::Hamiltonian0                                                |        8.45 ms →        8.45 ms   (-0.04%) |       1   →       1              |        8.45 ms →        8.45 ms   (-0.04%) | 
  │ ├ sirius::Local_operator                                            |        8.10 ms →        8.10 ms   (+0.05%) |       1   →       1              |        8.10 ms →        8.10 ms   (+0.05%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.83 ms →        4.69 ms   (-2.93%) |       1   →       1              |        4.83 ms →        4.69 ms   (-2.93%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.35 ms →        2.50 ms   (+6.46%) |       1   →       1              |        2.35 ms →        2.50 ms   (+6.46%) | 
  │ ├ sirius::Non_local_operator                                        |       62.41 μs →       62.82 μs   (+0.65%) |       2   →       2              |      124.82 μs →      125.63 μs   (+0.65%) | 
  │ ├ sirius::D_operator::initialize                                    |       98.39 μs →       94.14 μs   (-4.32%) |       1   →       1              |       98.39 μs →       94.14 μs   (-4.32%) | 
  │ └ sirius::Q_operator::initialize                                    |       75.59 μs →       74.23 μs   (-1.81%) |       1   →       1              |       75.59 μs →       74.23 μs   (-1.81%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.88 s  →        1.86 s    (-1.11%) |       1   →       1              |        1.88 s  →        1.86 s    (-1.11%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.70 ms →       18.69 ms   (-0.08%) |       1   →       1              |       18.70 ms →       18.69 ms   (-0.08%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      186.71 μs →      185.59 μs   (-0.60%) |       1   →       1              |      186.71 μs →      185.59 μs   (-0.60%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       18.52 ms →       18.50 ms   (-0.08%) |       1   →       1              |       18.52 ms →       18.50 ms   (-0.08%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.86 s  →        1.84 s    (-1.12%) |       1   →       1              |        1.86 s  →        1.84 s    (-1.12%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      128.50 ms →      127.73 ms   (-0.61%) |       4   →       4              |      514.01 ms →      510.90 ms   (-0.61%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       52.61 ms →       52.23 ms   (-0.72%) |       1   →       1              |       52.61 ms →       52.23 ms   (-0.72%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.05 ms →       20.99 ms   (-0.29%) |       1   →       1              |       21.05 ms →       20.99 ms   (-0.29%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      635.14 ms →      636.37 ms   (+0.19%) |       1   →       1              |      635.14 ms →      636.37 ms   (+0.19%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      298.25 ms →      297.83 ms   (-0.14%) |       1   →       1              |      298.25 ms →      297.83 ms   (-0.14%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        2.66 μs →        3.00 μs  (+12.75%) |       1   →       1              |        2.66 μs →        3.00 μs  (+12.75%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        1.70 μs →        2.12 μs  (+24.50%) |       1   →       1              |        1.70 μs →        2.12 μs  (+24.50%) | 
+ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      407.00 ns →      321.00 ns  (-21.13%) |       1   →       1              |      407.00 ns →      321.00 ns  (-21.13%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      500.00 ns →      513.00 ns   (+2.60%) |       1   →       1              |      500.00 ns →      513.00 ns   (+2.60%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.22 ms →        9.23 ms   (+0.09%) |       1   →       1              |        9.22 ms →        9.23 ms   (+0.09%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      120.60 ms →      120.98 ms   (+0.31%) |       1   →       1              |      120.60 ms →      120.98 ms   (+0.31%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      103.51 ms →      104.14 ms   (+0.61%) |       2   →       2              |      207.03 ms →      208.29 ms   (+0.61%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       40.08 ms →       40.16 ms   (+0.20%) |       2   →       2              |       80.16 ms →       80.31 ms   (+0.20%) | 
  │ │ │ └ sddk::wf_inner                                                |       39.52 ms →       39.58 ms   (+0.14%) |       2   →       2              |       79.04 ms →       79.16 ms   (+0.14%) | 
+ │ │ │   ├ sddk::wf_inner|scale                                        |       40.00 ns →       24.50 ns  (-38.75%) |       2   →       2              |       80.00 ns →       49.00 ns  (-38.75%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       39.05 ms →       39.10 ms   (+0.14%) |       2   →       2              |       78.09 ms →       78.21 ms   (+0.14%) | 
+ │ │ │   └ sddk::wf_inner|scale_back                                   |       25.50 ns →       22.50 ns  (-11.76%) |       2   →       2              |       51.00 ns →       45.00 ns  (-11.76%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       56.43 ms →       57.65 ms   (+2.15%) |       1   →       1              |       56.43 ms →       57.65 ms   (+2.15%) | 
  │ │ └ sddk::wf_trans                                                  |       30.70 ms →       30.77 ms   (+0.24%) |       1   →       1              |       30.70 ms →       30.77 ms   (+0.24%) | 
  │ │   └ sddk::wf_trans|pw                                             |       30.69 ms →       30.77 ms   (+0.23%) |       1   →       1              |       30.69 ms →       30.77 ms   (+0.23%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      918.00 ns →      421.00 ns  (-54.14%) |       1   →       1              |      918.00 ns →      421.00 ns  (-54.14%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      121.16 s  →      119.68 s    (-1.22%) |       1   →       1              |      121.16 s  →      119.68 s    (-1.22%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        6.28 ms →        5.70 ms   (-9.19%) |      19   →      19              |      119.25 ms →      108.29 ms   (-9.19%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.64 s  →        4.58 s    (-1.46%) |      26   →      26              |      120.75 s  →      118.98 s    (-1.46%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        4.61 ms →        6.19 ms  (+34.19%) |      26   →      26              |      119.92 ms →      160.91 ms  (+34.19%) | 
- │ │ │ ├ sirius::Local_operator                                        |        4.25 ms →        5.82 ms  (+36.94%) |      26   →      26              |      110.49 ms →      151.31 ms  (+36.94%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      971.30 μs →      973.09 μs   (+0.18%) |      26   →      26              |       25.25 ms →       25.30 ms   (+0.18%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.39 ms →        3.96 ms  (+65.58%) |      26   →      26              |       62.10 ms →      102.83 ms  (+65.58%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.42 μs →       64.23 μs   (-0.29%) |      52   →      52              |        3.35 ms →        3.34 ms   (-0.29%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       87.76 μs →       89.85 μs   (+2.39%) |      26   →      26              |        2.28 ms →        2.34 ms   (+2.39%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       77.55 μs →       80.43 μs   (+3.71%) |      26   →      26              |        2.02 ms →        2.09 ms   (+3.71%) | 
  │ │ ├ sirius::Band::solve                                             |        2.66 s  →        2.66 s    (-0.03%) |      26   →      26              |       69.15 s  →       69.13 s    (-0.03%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      150.49 μs →      158.91 μs   (+5.60%) |      26   →      26              |        3.91 ms →        4.13 ms   (+5.60%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      143.75 μs →      151.53 μs   (+5.41%) |      26   →      26              |        3.74 ms →        3.94 ms   (+5.41%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.01 μs →        5.48 μs   (+9.45%) |      26   →      26              |      130.18 μs →      142.48 μs   (+9.45%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.53 s  →        2.54 s    (+0.19%) |      26   →      26              |       65.86 s  →       65.98 s    (+0.19%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       94.89 ms →       94.52 ms   (-0.39%) |      26   →      26              |        2.47 s  →        2.46 s    (-0.39%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.69 ms →        7.56 ms   (-1.68%) |     156   →     156              |        1.20 s  →        1.18 s    (-1.68%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        5.85 ms →        5.99 ms   (+2.38%) |      26   →      26              |      152.08 ms →      155.71 ms   (+2.38%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      351.15 μs →      353.04 μs   (+0.54%) |      26   →      26              |        9.13 ms →        9.18 ms   (+0.54%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.33 ms →        2.32 ms   (-0.37%) |      52   →      52              |      120.96 ms →      120.51 ms   (-0.37%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.40 s  →        2.40 s    (+0.21%) |      26   →      26              |       62.31 s  →       62.44 s    (+0.21%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      136.62 ms →      137.00 ms   (+0.28%) |     262   →     262              |       35.79 s  →       35.90 s    (+0.28%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       55.53 ms →       55.58 ms   (+0.10%) |     262   →     262              |       14.55 s  →       14.56 s    (+0.10%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.92 μs →        2.07 μs   (+7.82%) |     262   →     262              |      502.21 μs →      541.50 μs   (+7.82%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.62 μs →        1.76 μs   (+8.67%) |     262   →     262              |      425.26 μs →      462.14 μs   (+8.67%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      364.79 ns →      407.92 ns  (+11.82%) |     262   →     262              |       95.58 μs →      106.88 μs  (+11.82%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      436.16 ns →      454.02 ns   (+4.09%) |     262   →     262              |      114.27 μs →      118.95 μs   (+4.09%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.45 ms →        7.45 ms   (+0.00%) |     262   →     262              |        1.95 s  →        1.95 s    (+0.00%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       24.76 ms →       25.10 ms   (+1.39%) |     262   →     262              |        6.49 s  →        6.58 s    (+1.39%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       24.43 ms →       24.43 ms   (-0.03%) |     524   →     524              |       12.80 s  →       12.80 s    (-0.03%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       42.71 ms →       42.67 ms   (-0.09%) |     262   →     262              |       11.19 s  →       11.18 s    (-0.09%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        6.23 ms →        6.22 ms   (-0.15%) |     498   →     498              |        3.10 s  →        3.10 s    (-0.15%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       52.69 ns →       44.44 ns  (-15.65%) |     498   →     498              |       26.24 μs →       22.13 μs  (-15.65%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        5.11 ms →        5.11 ms   (-0.17%) |     498   →     498              |        2.55 s  →        2.54 s    (-0.17%) | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       28.71 ns →       29.01 ns   (+1.01%) |     498   →     498              |       14.30 μs →       14.45 μs   (+1.01%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |        7.47 ms →        7.48 ms   (+0.02%) |     262   →     262              |        1.96 s  →        1.96 s    (+0.02%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       10.31 ms →       10.31 ms   (-0.08%) |     262   →     262              |        2.70 s  →        2.70 s    (-0.08%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |       14.52 ms →       14.50 ms   (-0.12%) |     236   →     236              |        3.43 s  →        3.42 s    (-0.12%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        4.84 ms →        4.83 ms   (-0.12%) |     708   →     708              |        3.43 s  →        3.42 s    (-0.12%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       10.57 ms →       10.58 ms   (+0.06%) |     262   →     262              |        2.77 s  →        2.77 s    (+0.06%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |       10.18 ms →       10.17 ms   (-0.07%) |     262   →     262              |        2.67 s  →        2.67 s    (-0.07%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       26.71 ns →       23.94 ns  (-10.39%) |     262   →     262              |        7.00 μs →        6.27 μs  (-10.39%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        9.07 ms →        9.06 ms   (-0.05%) |     262   →     262              |        2.38 s  →        2.37 s    (-0.05%) | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       42.66 ns →       42.71 ns   (+0.13%) |     262   →     262              |       11.18 μs →       11.19 μs   (+0.13%) | 
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       17.80 ms →       17.95 ms   (+0.81%) |     262   →     262              |        4.66 s  →        4.70 s    (+0.81%) | 
  │ │ │ │   ├ sirius::residuals                                         |       13.14 ms →       13.17 ms   (+0.19%) |     252   →     252              |        3.31 s  →        3.32 s    (+0.19%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       11.71 ms →       11.72 ms   (+0.08%) |     242   →     242              |        2.83 s  →        2.84 s    (+0.08%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        5.86 ms →        5.86 ms   (+0.08%) |     484   →     484              |        2.83 s  →        2.84 s    (+0.08%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.72 ms →        1.72 ms   (+0.45%) |     242   →     242              |      415.22 ms →      417.07 ms   (+0.45%) | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       53.79 ms →       53.75 ms   (-0.07%) |      85   →      85              |        4.57 s  →        4.57 s    (-0.07%) | 
  │ │ │ │     └ sddk::wf_trans                                          |       31.48 ms →       31.46 ms   (-0.07%) |     144   →     144              |        4.53 s  →        4.53 s    (-0.07%) | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |       22.33 ms →       22.31 ms   (-0.07%) |     203   →     203              |        4.53 s  →        4.53 s    (-0.07%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      401.88 ns →      458.35 ns  (+14.05%) |      26   →      26              |       10.45 μs →       11.92 μs  (+14.05%) | 
+ │ │ │ └ sirius::K_point_set::sync_band_energies                       |       80.73 μs →       40.76 μs  (-49.51%) |      26   →      26              |        2.10 ms →        1.06 ms  (-49.51%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      612.78 μs →      608.03 μs   (-0.78%) |      26   →      26              |       15.93 ms →       15.81 ms   (-0.78%) | 
  │ │ ├ sirius::Density::generate                                       |      776.95 ms →      770.42 ms   (-0.84%) |      26   →      26              |       20.20 s  →       20.03 s    (-0.84%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      402.83 ms →      402.40 ms   (-0.11%) |      26   →      26              |       10.47 s  →       10.46 s    (-0.11%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.40 μs →        3.54 μs   (+3.98%) |      26   →      26              |       88.47 μs →       91.99 μs   (+3.98%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.10 μs →        3.29 μs   (+6.09%) |      26   →      26              |       80.55 μs →       85.46 μs   (+6.09%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |      100.37 ms →      100.26 ms   (-0.11%) |      26   →      26              |        2.61 s  →        2.61 s    (-0.11%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       10.53 μs →       10.85 μs   (+3.03%) |      26   →      26              |      273.83 μs →      282.11 μs   (+3.03%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.13 ms →        7.12 ms   (-0.02%) |      26   →      26              |      185.26 ms →      185.23 ms   (-0.02%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       91.24 ms →       91.24 ms   (-0.00%) |      26   →      26              |        2.37 s  →        2.37 s    (-0.00%) | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      555.04 ns →      564.42 ns   (+1.69%) |      26   →      26              |       14.43 μs →       14.68 μs   (+1.69%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      163.25 ms →      162.03 ms   (-0.75%) |      26   →      26              |        4.24 s  →        4.21 s    (-0.75%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.64 ms   (-0.06%) |      26   →      26              |       42.61 ms →       42.59 ms   (-0.06%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.27 ms →       88.25 ms   (-0.02%) |      26   →      26              |        2.30 s  →        2.29 s    (-0.02%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.05 ms →       88.03 ms   (-0.02%) |      26   →      26              |        2.29 s  →        2.29 s    (-0.02%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      280.78 ms →      275.05 ms   (-2.04%) |      26   →      26              |        7.30 s  →        7.15 s    (-2.04%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      280.78 ms →      275.05 ms   (-2.04%) |      26   →      26              |        7.30 s  →        7.15 s    (-2.04%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.65 ms →       24.86 ms   (+0.83%) |      26   →      26              |      641.00 ms →      646.29 ms   (+0.83%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      232.24 ms →      225.71 ms   (-2.81%) |      26   →      26              |        6.04 s  →        5.87 s    (-2.81%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       22.73 ms →       23.32 ms   (+2.62%) |      26   →      26              |      590.92 ms →      606.42 ms   (+2.62%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       80.82 ms →       81.37 ms   (+0.68%) |      26   →      26              |        2.10 s  →        2.12 s    (+0.68%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        8.92 ms →        8.00 ms  (-10.31%) |      26   →      26              |      232.04 ms →      208.13 ms  (-10.31%) | 
+ │ │ ├ sirius::Density::mix                                            |      215.07 ms →      157.96 ms  (-26.55%) |      26   →      26              |        5.59 s  →        4.11 s   (-26.55%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      910.04 μs →      944.40 μs   (+3.78%) |      26   →      26              |       23.66 ms →       24.55 ms   (+3.78%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.35 ms →       10.38 ms   (+0.33%) |     334   →     334              |        3.46 s  →        3.47 s    (+0.33%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |        9.98 ms →        9.81 ms   (-1.75%) |     334   →     334              |        3.33 s  →        3.28 s    (-1.75%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        9.98 ms →        9.81 ms   (-1.75%) |     334   →     334              |        3.33 s  →        3.28 s    (-1.75%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        8.01 ms →        6.43 ms  (-19.74%) |      26   →      26              |      208.27 ms →      167.15 ms  (-19.74%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        7.16 ms →        5.34 ms  (-25.45%) |      26   →      26              |      186.16 ms →      138.78 ms  (-25.45%) | 
  │ │ ├ sirius::Potential::generate                                     |      580.18 ms →      580.61 ms   (+0.07%) |      26   →      26              |       15.08 s  →       15.10 s    (+0.07%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      138.38 ms →      138.78 ms   (+0.29%) |      26   →      26              |        3.60 s  →        3.61 s    (+0.29%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        5.36 ms →        5.17 ms   (-3.52%) |      26   →      26              |      139.29 ms →      134.39 ms   (-3.52%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.39 ms →       10.29 ms   (-0.96%) |      26   →      26              |      270.19 ms →      267.60 ms   (-0.96%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.14 ms →       10.00 ms   (-1.34%) |      26   →      26              |      263.54 ms →      260.00 ms   (-1.34%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.14 ms →       10.00 ms   (-1.34%) |      26   →      26              |      263.53 ms →      259.99 ms   (-1.34%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      555.48 μs →      549.49 μs   (-1.08%) |      52   →      52              |       28.88 ms →       28.57 ms   (-1.08%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       49.15 ms →       49.16 ms   (+0.02%) |      26   →      26              |        1.28 s  →        1.28 s    (+0.02%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.79 ms →       46.78 ms   (-0.00%) |      26   →      26              |        1.22 s  →        1.22 s    (-0.00%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.04 ms →        3.03 ms   (-0.43%) |      52   →      52              |      158.33 ms →      157.65 ms   (-0.43%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.58 ms →        5.37 ms   (-3.88%) |      26   →      26              |      145.19 ms →      139.55 ms   (-3.88%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.58 ms →        6.49 ms   (-1.36%) |      26   →      26              |      171.17 ms →      168.84 ms   (-1.36%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       91.07 ms →       91.04 ms   (-0.03%) |      26   →      26              |        2.37 s  →        2.37 s    (-0.03%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      292.57 ms →      292.72 ms   (+0.05%) |      26   →      26              |        7.61 s  →        7.61 s    (+0.05%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      285.11 ms →      280.42 ms   (-1.64%) |      26   →      26              |        7.41 s  →        7.29 s    (-1.64%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      285.11 ms →      280.42 ms   (-1.64%) |      26   →      26              |        7.41 s  →        7.29 s    (-1.64%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.21 ms →       27.33 ms   (+0.44%) |      26   →      26              |      707.41 ms →      710.53 ms   (+0.44%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      230.11 ms →      225.13 ms   (-2.16%) |      26   →      26              |        5.98 s  →        5.85 s    (-2.16%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.97 ms →       24.13 ms   (+0.66%) |      26   →      26              |      623.19 ms →      627.32 ms   (+0.66%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.93 ms →        5.38 ms   (-9.20%) |      26   →      26              |      154.18 ms →      140.00 ms   (-9.20%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.74 ms →       10.71 ms   (-0.28%) |     182   →     182              |        1.96 s  →        1.95 s    (-0.28%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |       10.38 ms →       10.28 ms   (-0.92%) |     182   →     182              |        1.89 s  →        1.87 s    (-0.92%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |       10.38 ms →       10.28 ms   (-0.92%) |     182   →     182              |        1.89 s  →        1.87 s    (-0.92%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.22 ms →       10.14 ms   (-0.78%) |      78   →      78              |      797.42 ms →      791.23 ms   (-0.78%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        9.90 ms →        9.79 ms   (-1.04%) |      78   →      78              |      771.85 ms →      763.84 ms   (-1.04%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |       10.08 ms →       10.03 ms   (-0.55%) |      26   →      26              |      262.12 ms →      260.69 ms   (-0.55%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      118.43 μs →      146.19 μs  (+23.44%) |      26   →      26              |        3.08 ms →        3.80 ms  (+23.44%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      113.81 μs →      141.23 μs  (+24.09%) |      26   →      26              |        2.96 ms →        3.67 ms  (+24.09%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        7.21 ms →        7.37 ms   (+2.19%) |       2   →       2              |       14.43 ms →       14.74 ms   (+2.19%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.51 ms →       10.22 ms   (-2.75%) |       6   →       6              |       63.08 ms →       61.35 ms   (-2.75%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.49 ms →       10.09 ms   (-3.75%) |       6   →       6              |       62.91 ms →       60.55 ms   (-3.75%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.49 ms →       10.09 ms   (-3.75%) |       6   →       6              |       62.91 ms →       60.55 ms   (-3.75%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        9.93 ms →       10.19 ms   (+2.61%) |       3   →       3              |       29.80 ms →       30.58 ms   (+2.61%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.86 ms →        9.65 ms   (-2.16%) |       3   →       3              |       29.58 ms →       28.94 ms   (-2.16%) | 
  ├ sirius::Periodic_function|inner                                     |       10.18 ms →       10.25 ms   (+0.63%) |       2   →       2              |       20.37 ms →       20.50 ms   (+0.63%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.18 ms →       10.17 ms   (-0.03%) |       2   →       2              |       20.35 ms →       20.34 ms   (-0.03%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.17 ms →       10.17 ms   (-0.03%) |       2   →       2              |       20.35 ms →       20.34 ms   (-0.03%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        9.69 ms →        9.61 ms   (-0.80%) |       1   →       1              |        9.69 ms →        9.61 ms   (-0.80%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        9.62 ms →        9.61 ms   (-0.10%) |       1   →       1              |        9.62 ms →        9.61 ms   (-0.10%) | 
  └ sirius::finalize                                                    |      223.38 ms →      226.96 ms   (+1.60%) |       1   →       1              |      223.38 ms →      226.96 ms   (+1.60%) | 
  ====================================================================================================================================================================================================
```
