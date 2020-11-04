# Benchmark 392f68b5626168134a99cd6d4a3cc40b87322cb7 vs 4abe991ed1b67a61e2f44af0d6336c92b3f43afd
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      128.74 s  →      128.50 s    (-0.19%) |       1   →       1              |      128.74 s  →      128.50 s    (-0.19%) | 
  ├ sirius::initialize                                                  |        2.65 s  →        2.63 s    (-0.94%) |       1   →       1              |        2.65 s  →        2.63 s    (-0.94%) | 
  ├ sirius::Simulation_context::initialize                              |        2.91 s  →        2.88 s    (-0.85%) |       1   →       1              |        2.91 s  →        2.88 s    (-0.85%) | 
- │ ├ sirius::Simulation_context::init_comm                             |        2.34 ms →       26.19 ms (+1020.30%) |       1   →       1              |        2.34 ms →       26.19 ms (+1020.30%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      143.27 ms →      113.63 ms  (-20.68%) |       1   →       1              |      143.27 ms →      113.63 ms  (-20.68%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       60.31 ms →       45.52 ms  (-24.53%) |       2   →       2              |      120.62 ms →       91.03 ms  (-24.53%) | 
  │ │ └ sirius::Unit_cell::update                                       |       22.58 ms →       22.53 ms   (-0.20%) |       1   →       1              |       22.58 ms →       22.53 ms   (-0.20%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.28 ms →        6.47 ms   (+3.08%) |       1   →       1              |        6.28 ms →        6.47 ms   (+3.08%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       16.26 ms →       16.02 ms   (-1.47%) |       1   →       1              |       16.26 ms →       16.02 ms   (-1.47%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       16.24 ms →       16.00 ms   (-1.47%) |       1   →       1              |       16.24 ms →       16.00 ms   (-1.47%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.13 ms →        4.14 ms   (+0.12%) |       1   →       1              |        4.13 ms →        4.14 ms   (+0.12%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.34 ms   (+0.89%) |       1   →       1              |        2.32 ms →        2.34 ms   (+0.89%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      108.37 μs →      105.36 μs   (-2.78%) |       1   →       1              |      108.37 μs →      105.36 μs   (-2.78%) | 
  │ └ sirius::Simulation_context::update                                |        2.72 s  →        2.70 s    (-0.75%) |       1   →       1              |        2.72 s  →        2.70 s    (-0.75%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.77 ms →       10.86 ms   (+0.78%) |       1   →       1              |       10.77 ms →       10.86 ms   (+0.78%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.29 ms →        4.45 ms   (+3.73%) |       1   →       1              |        4.29 ms →        4.45 ms   (+3.73%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.45 ms →        6.37 ms   (-1.20%) |       1   →       1              |        6.45 ms →        6.37 ms   (-1.20%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.43 ms →        6.35 ms   (-1.21%) |       1   →       1              |        6.43 ms →        6.35 ms   (-1.21%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.92 ms →        3.85 ms   (-1.71%) |       1   →       1              |        3.92 ms →        3.85 ms   (-1.71%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.32 ms   (-0.28%) |       1   →       1              |        2.33 ms →        2.32 ms   (-0.28%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      113.76 μs →      106.14 μs   (-6.70%) |       1   →       1              |      113.76 μs →      106.14 μs   (-6.70%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       62.83 ms →       62.25 ms   (-0.92%) |       2   →       2              |      125.67 ms →      124.51 ms   (-0.92%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.20 ms →        5.16 ms   (-0.72%) |       2   →       2              |       10.39 ms →       10.32 ms   (-0.72%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.47 ms →        4.46 ms   (-0.11%) |       1   →       1              |        4.47 ms →        4.46 ms   (-0.11%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.88 ms →       21.74 ms   (-0.61%) |       2   →       2              |       43.75 ms →       43.48 ms   (-0.61%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.82 ms →       14.80 ms   (-0.14%) |       2   →       2              |       29.64 ms →       29.60 ms   (-0.14%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.73 ms →       19.77 ms   (+0.21%) |       4   →       4              |       78.93 ms →       79.09 ms   (+0.21%) | 
  │   ├ sddk::Gvec::init                                                |      181.43 ms →      171.43 ms   (-5.51%) |       2   →       2              |      362.86 ms →      342.86 ms   (-5.51%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      137.25 ms →      128.56 ms   (-6.33%) |       2   →       2              |      274.49 ms →      257.13 ms   (-6.33%) | 
  │   ├ sddk::Gvec_shells                                               |      197.58 ms →      184.11 ms   (-6.82%) |       1   →       1              |      197.58 ms →      184.11 ms   (-6.82%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.34 ms →        1.31 ms   (-2.58%) |       1   →       1              |        1.34 ms →        1.31 ms   (-2.58%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      295.30 ms →      290.13 ms   (-1.75%) |       2   →       2              |      590.60 ms →      580.25 ms   (-1.75%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       35.43 ms →       36.27 ms   (+2.37%) |       1   →       1              |       35.43 ms →       36.27 ms   (+2.37%) | 
  │ ├ sirius::K_point::K_point                                          |        2.31 μs →        2.32 μs   (+0.41%) |       4   →       4              |        9.26 μs →        9.29 μs   (+0.41%) | 
  │ └ sirius::K_point_set::initialize                                   |       35.32 ms →       36.17 ms   (+2.41%) |       1   →       1              |       35.32 ms →       36.17 ms   (+2.41%) | 
  │   └ sirius::K_point::initialize                                     |       35.22 ms →       36.07 ms   (+2.42%) |       1   →       1              |       35.22 ms →       36.07 ms   (+2.42%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       18.01 ms →       18.74 ms   (+4.09%) |       1   →       1              |       18.01 ms →       18.74 ms   (+4.09%) | 
  │     │ └ sddk::Gvec::init                                            |        8.15 ms →        8.72 ms   (+7.03%) |       1   →       1              |        8.15 ms →        8.72 ms   (+7.03%) | 
- │     ├ sddk::matrix_storage::matrix_storage                          |        8.40 μs →        9.97 μs  (+18.66%) |       1   →       1              |        8.40 μs →        9.97 μs  (+18.66%) | 
  │     └ sirius::K_point::update                                       |       12.41 ms →       12.48 ms   (+0.49%) |       1   →       1              |       12.41 ms →       12.48 ms   (+0.49%) | 
  │       └ sirius::Beta_projectors                                     |        6.11 ms →        6.02 ms   (-1.54%) |       1   →       1              |        6.11 ms →        6.02 ms   (-1.54%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.53 ms →        3.42 ms   (-3.10%) |       1   →       1              |        3.53 ms →        3.42 ms   (-3.10%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.44 ms →        5.22 ms   (-4.06%) |       2   →       2              |       10.89 ms →       10.44 ms   (-4.06%) | 
  ├ sirius::Potential                                                   |      153.58 ms →      159.13 ms   (+3.62%) |       1   →       1              |      153.58 ms →      159.13 ms   (+3.62%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.82 ms →        5.72 ms   (-1.82%) |       6   →       6              |       34.95 ms →       34.31 ms   (-1.82%) | 
  │ └ sirius::Potential::update                                         |      117.91 ms →      124.11 ms   (+5.26%) |       1   →       1              |      117.91 ms →      124.11 ms   (+5.26%) | 
  │   └ sirius::Potential::generate_local_potential                     |      117.16 ms →      123.36 ms   (+5.29%) |       1   →       1              |      117.16 ms →      123.36 ms   (+5.29%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      106.55 ms →      109.95 ms   (+3.18%) |       1   →       1              |      106.55 ms →      109.95 ms   (+3.18%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        9.70 ms →       12.53 ms  (+29.17%) |       1   →       1              |        9.70 ms →       12.53 ms  (+29.17%) | 
  ├ sirius::Density                                                     |      127.91 ms →      129.44 ms   (+1.19%) |       1   →       1              |      127.91 ms →      129.44 ms   (+1.19%) | 
+ │ ├ sirius::Smooth_periodic_function                                  |        5.66 ms →        5.08 ms  (-10.32%) |       2   →       2              |       11.32 ms →       10.15 ms  (-10.32%) | 
  │ └ sirius::Density::update                                           |      116.29 ms →      119.02 ms   (+2.34%) |       1   →       1              |      116.29 ms →      119.02 ms   (+2.34%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      115.82 ms →      118.61 ms   (+2.40%) |       1   →       1              |      115.82 ms →      118.61 ms   (+2.40%) | 
+ │     ├ sirius::rho_core_ri_pseudo|values                             |      118.90 μs →      104.59 μs  (-12.03%) |       1   →       1              |      118.90 μs →      104.59 μs  (-12.03%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      109.26 ms →      111.77 ms   (+2.30%) |       1   →       1              |      109.26 ms →      111.77 ms   (+2.30%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        6.00 ms →        6.29 ms   (+4.79%) |       1   →       1              |        6.00 ms →        6.29 ms   (+4.79%) | 
  ├ sirius::Density::initial_density                                    |      162.64 ms →      165.25 ms   (+1.60%) |       1   →       1              |      162.64 ms →      165.25 ms   (+1.60%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      108.91 ms →      111.43 ms   (+2.31%) |       1   →       1              |      108.91 ms →      111.43 ms   (+2.31%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.78 ms →        5.27 ms   (-8.83%) |       2   →       2              |       11.56 ms →       10.54 ms   (-8.83%) | 
  │ └ sirius::Periodic_function::integrate                              |       10.17 ms →        9.70 ms   (-4.59%) |       1   →       1              |       10.17 ms →        9.70 ms   (-4.59%) | 
  ├ sirius::Potential::generate                                         |      582.63 ms →      580.18 ms   (-0.42%) |       1   →       1              |      582.63 ms →      580.18 ms   (-0.42%) | 
  │ ├ sirius::Potential::poisson                                        |      127.84 ms →      126.03 ms   (-1.42%) |       1   →       1              |      127.84 ms →      126.03 ms   (-1.42%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        8.44 ms →        5.34 ms  (-36.68%) |       1   →       1              |        8.44 ms →        5.34 ms  (-36.68%) | 
+ │ │ └ sirius::Periodic_function|inner                                 |       11.05 ms →        9.91 ms  (-10.32%) |       1   →       1              |       11.05 ms →        9.91 ms  (-10.32%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |       10.31 ms →        9.89 ms   (-4.03%) |       1   →       1              |       10.31 ms →        9.89 ms   (-4.03%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |       10.30 ms →        9.88 ms   (-4.03%) |       1   →       1              |       10.30 ms →        9.88 ms   (-4.03%) | 
  │ ├ sirius::Periodic_function::add                                    |      534.20 μs →      543.65 μs   (+1.77%) |       2   →       2              |        1.07 ms →        1.09 ms   (+1.77%) | 
  │ ├ sirius::Potential::xc                                             |       54.06 ms →       53.77 ms   (-0.52%) |       1   →       1              |       54.06 ms →       53.77 ms   (-0.52%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.75 ms →       51.51 ms   (-0.46%) |       1   →       1              |       51.75 ms →       51.51 ms   (-0.46%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.73 ms →        5.64 ms   (-1.54%) |       2   →       2              |       11.46 ms →       11.28 ms   (-1.54%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.32 ms →        5.38 ms   (+1.11%) |       1   →       1              |        5.32 ms →        5.38 ms   (+1.11%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.95 ms →        5.87 ms   (-1.26%) |       1   →       1              |        5.95 ms →        5.87 ms   (-1.26%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.70 ms →       92.56 ms   (-0.15%) |       1   →       1              |       92.70 ms →       92.56 ms   (-0.15%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      299.62 ms →      299.49 ms   (-0.04%) |       1   →       1              |      299.62 ms →      299.49 ms   (-0.04%) | 
  ├ sirius::Hamiltonian0                                                |        8.36 ms →        8.33 ms   (-0.39%) |       1   →       1              |        8.36 ms →        8.33 ms   (-0.39%) | 
  │ ├ sirius::Local_operator                                            |        8.02 ms →        7.98 ms   (-0.44%) |       1   →       1              |        8.02 ms →        7.98 ms   (-0.44%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.74 ms →        4.68 ms   (-1.24%) |       1   →       1              |        4.74 ms →        4.68 ms   (-1.24%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.36 ms →        2.40 ms   (+1.68%) |       1   →       1              |        2.36 ms →        2.40 ms   (+1.68%) | 
  │ ├ sirius::Non_local_operator                                        |       62.35 μs →       63.86 μs   (+2.41%) |       2   →       2              |      124.70 μs →      127.71 μs   (+2.41%) | 
  │ ├ sirius::D_operator::initialize                                    |       92.68 μs →       93.22 μs   (+0.58%) |       1   →       1              |       92.68 μs →       93.22 μs   (+0.58%) | 
  │ └ sirius::Q_operator::initialize                                    |       74.09 μs →       73.27 μs   (-1.11%) |       1   →       1              |       74.09 μs →       73.27 μs   (-1.11%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.85 s  →        1.84 s    (-0.55%) |       1   →       1              |        1.85 s  →        1.84 s    (-0.55%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.63 ms →       19.70 ms   (+5.73%) |       1   →       1              |       18.63 ms →       19.70 ms   (+5.73%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      187.61 μs →      187.68 μs   (+0.04%) |       1   →       1              |      187.61 μs →      187.68 μs   (+0.04%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       18.44 ms →       19.51 ms   (+5.79%) |       1   →       1              |       18.44 ms →       19.51 ms   (+5.79%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.84 s  →        1.83 s    (-0.61%) |       1   →       1              |        1.84 s  →        1.83 s    (-0.61%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      127.22 ms →      125.00 ms   (-1.75%) |       4   →       4              |      508.89 ms →      500.00 ms   (-1.75%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       52.45 ms →       52.63 ms   (+0.34%) |       1   →       1              |       52.45 ms →       52.63 ms   (+0.34%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.04 ms →       20.99 ms   (-0.26%) |       1   →       1              |       21.04 ms →       20.99 ms   (-0.26%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      634.85 ms →      636.52 ms   (+0.26%) |       1   →       1              |      634.85 ms →      636.52 ms   (+0.26%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      297.62 ms →      297.40 ms   (-0.08%) |       1   →       1              |      297.62 ms →      297.40 ms   (-0.08%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.25 μs →        2.83 μs  (-13.02%) |       1   →       1              |        3.25 μs →        2.83 μs  (-13.02%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.31 μs →        1.87 μs  (-19.02%) |       1   →       1              |        2.31 μs →        1.87 μs  (-19.02%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      344.00 ns →      358.00 ns   (+4.07%) |       1   →       1              |      344.00 ns →      358.00 ns   (+4.07%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      559.00 ns →      543.00 ns   (-2.86%) |       1   →       1              |      559.00 ns →      543.00 ns   (-2.86%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.23 ms →        9.22 ms   (-0.07%) |       1   →       1              |        9.23 ms →        9.22 ms   (-0.07%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      120.78 ms →      121.02 ms   (+0.20%) |       1   →       1              |      120.78 ms →      121.02 ms   (+0.20%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      103.59 ms →      104.42 ms   (+0.80%) |       2   →       2              |      207.19 ms →      208.85 ms   (+0.80%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       40.24 ms →       40.20 ms   (-0.11%) |       2   →       2              |       80.48 ms →       80.39 ms   (-0.11%) | 
  │ │ │ └ sddk::wf_inner                                                |       39.68 ms →       39.62 ms   (-0.16%) |       2   →       2              |       79.36 ms →       79.24 ms   (-0.16%) | 
+ │ │ │   ├ sddk::wf_inner|scale                                        |       64.50 ns →       19.00 ns  (-70.54%) |       2   →       2              |      129.00 ns →       38.00 ns  (-70.54%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       39.21 ms →       39.14 ms   (-0.16%) |       2   →       2              |       78.41 ms →       78.29 ms   (-0.16%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       33.00 ns →       38.00 ns  (+15.15%) |       2   →       2              |       66.00 ns →       76.00 ns  (+15.15%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       56.39 ms →       55.47 ms   (-1.63%) |       1   →       1              |       56.39 ms →       55.47 ms   (-1.63%) | 
  │ │ └ sddk::wf_trans                                                  |       30.77 ms →       30.78 ms   (+0.02%) |       1   →       1              |       30.77 ms →       30.78 ms   (+0.02%) | 
  │ │   └ sddk::wf_trans|pw                                             |       30.77 ms →       30.77 ms   (+0.02%) |       1   →       1              |       30.77 ms →       30.77 ms   (+0.02%) | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      382.00 ns →      423.00 ns  (+10.73%) |       1   →       1              |      382.00 ns →      423.00 ns  (+10.73%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      119.24 s  →      119.06 s    (-0.15%) |       1   →       1              |      119.24 s  →      119.06 s    (-0.15%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.81 ms →        5.77 ms   (-0.78%) |      19   →      19              |      110.40 ms →      109.54 ms   (-0.78%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.57 s  →        4.57 s    (-0.11%) |      26   →      26              |      118.86 s  →      118.73 s    (-0.11%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        4.42 ms →        5.62 ms  (+27.07%) |      26   →      26              |      115.00 ms →      146.13 ms  (+27.07%) | 
- │ │ │ ├ sirius::Local_operator                                        |        4.06 ms →        5.25 ms  (+29.54%) |      26   →      26              |      105.43 ms →      136.58 ms  (+29.54%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      941.77 μs →      926.18 μs   (-1.65%) |      26   →      26              |       24.49 ms →       24.08 ms   (-1.65%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.23 ms →        3.44 ms  (+54.41%) |      26   →      26              |       57.87 ms →       89.35 ms  (+54.41%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.21 μs →       64.62 μs   (+0.64%) |      52   →      52              |        3.34 ms →        3.36 ms   (+0.64%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       88.04 μs →       87.90 μs   (-0.16%) |      26   →      26              |        2.29 ms →        2.29 ms   (-0.16%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       78.93 μs →       78.16 μs   (-0.98%) |      26   →      26              |        2.05 ms →        2.03 ms   (-0.98%) | 
  │ │ ├ sirius::Band::solve                                             |        2.60 s  →        2.63 s    (+1.10%) |      26   →      26              |       67.55 s  →       68.29 s    (+1.10%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      153.27 μs →      159.55 μs   (+4.09%) |      26   →      26              |        3.99 ms →        4.15 ms   (+4.09%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      145.63 μs →      151.77 μs   (+4.22%) |      26   →      26              |        3.79 ms →        3.95 ms   (+4.22%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.94 μs →        6.20 μs   (+4.34%) |      26   →      26              |      154.46 μs →      161.16 μs   (+4.34%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.47 s  →        2.48 s    (+0.56%) |      26   →      26              |       64.14 s  →       64.50 s    (+0.56%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       95.56 ms →       94.09 ms   (-1.54%) |      26   →      26              |        2.48 s  →        2.45 s    (-1.54%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.62 ms →        7.53 ms   (-1.27%) |     156   →     156              |        1.19 s  →        1.17 s    (-1.27%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        5.87 ms →        5.90 ms   (+0.45%) |      26   →      26              |      152.62 ms →      153.30 ms   (+0.45%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      347.74 μs →      347.15 μs   (-0.17%) |      26   →      26              |        9.04 ms →        9.03 ms   (-0.17%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.28 ms →        2.31 ms   (+0.99%) |      52   →      52              |      118.81 ms →      119.98 ms   (+0.99%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.33 s  →        2.34 s    (+0.65%) |      26   →      26              |       60.57 s  →       60.97 s    (+0.65%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      136.45 ms →      137.72 ms   (+0.92%) |     262   →     262              |       35.75 s  →       36.08 s    (+0.92%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       55.82 ms →       55.96 ms   (+0.24%) |     262   →     262              |       14.62 s  →       14.66 s    (+0.24%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.19 μs →        2.22 μs   (+1.15%) |     262   →     262              |      573.84 μs →      580.44 μs   (+1.15%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.84 μs →        1.89 μs   (+2.73%) |     262   →     262              |      481.97 μs →      495.12 μs   (+2.73%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      435.74 ns →      446.19 ns   (+2.40%) |     262   →     262              |      114.17 μs →      116.90 μs   (+2.40%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      526.83 ns →      541.68 ns   (+2.82%) |     262   →     262              |      138.03 μs →      141.92 μs   (+2.82%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.45 ms →        7.45 ms   (-0.01%) |     262   →     262              |        1.95 s  →        1.95 s    (-0.01%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       24.32 ms →       25.26 ms   (+3.83%) |     262   →     262              |        6.37 s  →        6.62 s    (+3.83%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       24.42 ms →       24.52 ms   (+0.40%) |     524   →     524              |       12.80 s  →       12.85 s    (+0.40%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       35.84 ms →       35.84 ms   (-0.01%) |     262   →     262              |        9.39 s  →        9.39 s    (-0.01%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        6.22 ms →        6.22 ms   (+0.03%) |     498   →     498              |        3.10 s  →        3.10 s    (+0.03%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       62.58 ns →       50.28 ns  (-19.66%) |     498   →     498              |       31.16 μs →       25.04 μs  (-19.66%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        5.10 ms →        5.11 ms   (+0.09%) |     498   →     498              |        2.54 s  →        2.54 s    (+0.09%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       30.70 ns →       34.00 ns  (+10.75%) |     498   →     498              |       15.29 μs →       16.93 μs  (+10.75%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      650.86 μs →      653.46 μs   (+0.40%) |     262   →     262              |      170.53 ms →      171.21 ms   (+0.40%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       10.31 ms →       10.30 ms   (-0.04%) |     262   →     262              |        2.70 s  →        2.70 s    (-0.04%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |       14.50 ms →       14.50 ms   (-0.05%) |     236   →     236              |        3.42 s  →        3.42 s    (-0.05%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        4.83 ms →        4.83 ms   (-0.05%) |     708   →     708              |        3.42 s  →        3.42 s    (-0.05%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       10.38 ms →       10.40 ms   (+0.18%) |     262   →     262              |        2.72 s  →        2.73 s    (+0.18%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |       10.18 ms →       10.17 ms   (-0.11%) |     262   →     262              |        2.67 s  →        2.66 s    (-0.11%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       40.97 ns →       23.52 ns  (-42.58%) |     262   →     262              |       10.73 μs →        6.16 μs  (-42.58%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        9.07 ms →        9.06 ms   (-0.09%) |     262   →     262              |        2.38 s  →        2.37 s    (-0.09%) | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       47.85 ns →       51.37 ns   (+7.34%) |     262   →     262              |       12.54 μs →       13.46 μs   (+7.34%) | 
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       18.39 ms →       18.63 ms   (+1.31%) |     262   →     262              |        4.82 s  →        4.88 s    (+1.31%) | 
  │ │ │ │   ├ sirius::residuals                                         |       13.16 ms →       13.15 ms   (-0.04%) |     252   →     252              |        3.32 s  →        3.31 s    (-0.04%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       11.72 ms →       11.73 ms   (+0.09%) |     242   →     242              |        2.84 s  →        2.84 s    (+0.09%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        5.86 ms →        5.86 ms   (+0.09%) |     484   →     484              |        2.83 s  →        2.84 s    (+0.09%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.73 ms →        1.72 ms   (-0.68%) |     242   →     242              |      419.08 ms →      416.25 ms   (-0.68%) | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       53.73 ms →       53.72 ms   (-0.02%) |      85   →      85              |        4.57 s  →        4.57 s    (-0.02%) | 
  │ │ │ │     └ sddk::wf_trans                                          |       31.45 ms →       31.45 ms   (-0.02%) |     144   →     144              |        4.53 s  →        4.53 s    (-0.02%) | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |       22.31 ms →       22.31 ms   (-0.02%) |     203   →     203              |        4.53 s  →        4.53 s    (-0.02%) | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      454.35 ns →      419.69 ns   (-7.63%) |      26   →      26              |       11.81 μs →       10.91 μs   (-7.63%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       30.83 μs →       30.39 μs   (-1.43%) |      26   →      26              |      801.64 μs →      790.16 μs   (-1.43%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      605.40 μs →      612.09 μs   (+1.11%) |      26   →      26              |       15.74 ms →       15.91 ms   (+1.11%) | 
  │ │ ├ sirius::Density::generate                                       |      772.97 ms →      766.09 ms   (-0.89%) |      26   →      26              |       20.10 s  →       19.92 s    (-0.89%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      401.97 ms →      402.73 ms   (+0.19%) |      26   →      26              |       10.45 s  →       10.47 s    (+0.19%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.63 μs →        3.64 μs   (+0.37%) |      26   →      26              |       94.27 μs →       94.62 μs   (+0.37%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.33 μs →        3.30 μs   (-1.04%) |      26   →      26              |       86.70 μs →       85.80 μs   (-1.04%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |      100.13 ms →      100.35 ms   (+0.21%) |      26   →      26              |        2.60 s  →        2.61 s    (+0.21%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       10.92 μs →       10.64 μs   (-2.62%) |      26   →      26              |      283.98 μs →      276.55 μs   (-2.62%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.13 ms →        7.13 ms   (+0.00%) |      26   →      26              |      185.28 ms →      185.28 ms   (+0.00%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       91.09 ms →       91.29 ms   (+0.22%) |      26   →      26              |        2.37 s  →        2.37 s    (+0.22%) | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      552.73 ns →      598.65 ns   (+8.31%) |      26   →      26              |       14.37 μs →       15.56 μs   (+8.31%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      163.52 ms →      164.09 ms   (+0.35%) |      26   →      26              |        4.25 s  →        4.27 s    (+0.35%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.65 ms →        1.64 ms   (-0.33%) |      26   →      26              |       42.84 ms →       42.70 ms   (-0.33%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.31 ms →       88.26 ms   (-0.06%) |      26   →      26              |        2.30 s  →        2.29 s    (-0.06%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.08 ms →       88.03 ms   (-0.06%) |      26   →      26              |        2.29 s  →        2.29 s    (-0.06%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      273.80 ms →      271.68 ms   (-0.77%) |      26   →      26              |        7.12 s  →        7.06 s    (-0.77%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      273.80 ms →      271.68 ms   (-0.77%) |      26   →      26              |        7.12 s  →        7.06 s    (-0.77%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       28.74 ms →       24.15 ms  (-15.97%) |      26   →      26              |      747.22 ms →      627.86 ms  (-15.97%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      220.73 ms →      223.63 ms   (+1.31%) |      26   →      26              |        5.74 s  →        5.81 s    (+1.31%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       23.16 ms →       22.73 ms   (-1.85%) |      26   →      26              |      602.09 ms →      590.96 ms   (-1.85%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       82.02 ms →       80.51 ms   (-1.85%) |      26   →      26              |        2.13 s  →        2.09 s    (-1.85%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |       11.58 ms →        7.59 ms  (-34.48%) |      26   →      26              |      301.07 ms →      197.25 ms  (-34.48%) | 
  │ │ ├ sirius::Density::mix                                            |      219.00 ms →      201.68 ms   (-7.91%) |      26   →      26              |        5.69 s  →        5.24 s    (-7.91%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      949.70 μs →      904.00 μs   (-4.81%) |      26   →      26              |       24.69 ms →       23.50 ms   (-4.81%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.74 ms →       10.34 ms   (-3.72%) |     334   →     334              |        3.59 s  →        3.45 s    (-3.72%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.33 ms →        9.95 ms   (-3.69%) |     334   →     334              |        3.45 s  →        3.32 s    (-3.69%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.33 ms →        9.95 ms   (-3.69%) |     334   →     334              |        3.45 s  →        3.32 s    (-3.69%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        6.15 ms →        6.61 ms   (+7.51%) |      26   →      26              |      159.97 ms →      171.99 ms   (+7.51%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.35 ms →        5.78 ms   (+7.92%) |      26   →      26              |      139.22 ms →      150.24 ms   (+7.92%) | 
  │ │ ├ sirius::Potential::generate                                     |      569.80 ms →      568.29 ms   (-0.27%) |      26   →      26              |       14.81 s  →       14.78 s    (-0.27%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      127.59 ms →      126.55 ms   (-0.82%) |      26   →      26              |        3.32 s  →        3.29 s    (-0.82%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        8.93 ms →        5.26 ms  (-41.09%) |      26   →      26              |      232.24 ms →      136.82 ms  (-41.09%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.60 ms →       10.37 ms   (-2.13%) |      26   →      26              |      275.48 ms →      269.62 ms   (-2.13%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.30 ms →        9.98 ms   (-3.04%) |      26   →      26              |      267.70 ms →      259.57 ms   (-3.04%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.30 ms →        9.98 ms   (-3.04%) |      26   →      26              |      267.69 ms →      259.55 ms   (-3.04%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      543.08 μs →      542.99 μs   (-0.02%) |      52   →      52              |       28.24 ms →       28.24 ms   (-0.02%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       49.16 ms →       49.59 ms   (+0.88%) |      26   →      26              |        1.28 s  →        1.29 s    (+0.88%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.86 ms →       47.29 ms   (+0.92%) |      26   →      26              |        1.22 s  →        1.23 s    (+0.92%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        2.98 ms →        2.96 ms   (-0.75%) |      52   →      52              |      154.85 ms →      153.69 ms   (-0.75%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.45 ms →        5.46 ms   (+0.08%) |      26   →      26              |      141.82 ms →      141.93 ms   (+0.08%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.65 ms →        6.58 ms   (-1.03%) |      26   →      26              |      172.96 ms →      171.18 ms   (-1.03%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.91 ms →       90.87 ms   (-0.05%) |      26   →      26              |        2.36 s  →        2.36 s    (-0.05%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      293.14 ms →      292.32 ms   (-0.28%) |      26   →      26              |        7.62 s  →        7.60 s    (-0.28%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      281.45 ms →      277.71 ms   (-1.33%) |      26   →      26              |        7.32 s  →        7.22 s    (-1.33%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      281.45 ms →      277.71 ms   (-1.33%) |      26   →      26              |        7.32 s  →        7.22 s    (-1.33%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       32.17 ms →       27.01 ms  (-16.04%) |      26   →      26              |      836.37 ms →      702.20 ms  (-16.04%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      221.60 ms →      223.25 ms   (+0.75%) |      26   →      26              |        5.76 s  →        5.80 s    (+0.75%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.89 ms →       23.69 ms   (-0.85%) |      26   →      26              |      621.25 ms →      615.95 ms   (-0.85%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       11.12 ms →        5.57 ms  (-49.94%) |      26   →      26              |      289.22 ms →      144.77 ms  (-49.94%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.30 ms →       10.58 ms   (+2.72%) |     182   →     182              |        1.88 s  →        1.93 s    (+2.72%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.82 ms →       10.16 ms   (+3.43%) |     182   →     182              |        1.79 s  →        1.85 s    (+3.43%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.82 ms →       10.16 ms   (+3.43%) |     182   →     182              |        1.79 s  →        1.85 s    (+3.43%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.62 ms →       10.09 ms   (-5.03%) |      78   →      78              |      828.65 ms →      786.99 ms   (-5.03%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.21 ms →        9.71 ms   (-4.94%) |      78   →      78              |      796.64 ms →      757.28 ms   (-4.94%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |       10.06 ms →        9.89 ms   (-1.75%) |      26   →      26              |      261.69 ms →      257.10 ms   (-1.75%) | 
  │ │ └ sirius::Density::get_magnetisation                              |      112.65 μs →      114.42 μs   (+1.57%) |      26   →      26              |        2.93 ms →        2.97 ms   (+1.57%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |      107.84 μs →      109.57 μs   (+1.60%) |      26   →      26              |        2.80 ms →        2.85 ms   (+1.60%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.20 ms →        5.11 ms   (-1.68%) |       2   →       2              |       10.40 ms →       10.23 ms   (-1.68%) | 
  │ ├ sirius::Periodic_function|inner                                   |        9.71 ms →       10.45 ms   (+7.70%) |       6   →       6              |       58.23 ms →       62.71 ms   (+7.70%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        9.68 ms →       10.23 ms   (+5.62%) |       6   →       6              |       58.09 ms →       61.36 ms   (+5.62%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        9.68 ms →       10.23 ms   (+5.62%) |       6   →       6              |       58.09 ms →       61.36 ms   (+5.62%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.13 ms →        9.95 ms   (-1.79%) |       3   →       3              |       30.40 ms →       29.86 ms   (-1.79%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.06 ms →        9.76 ms   (-2.99%) |       3   →       3              |       30.19 ms →       29.28 ms   (-2.99%) | 
  ├ sirius::Periodic_function|inner                                     |       10.02 ms →       10.52 ms   (+4.96%) |       2   →       2              |       20.04 ms →       21.04 ms   (+4.96%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.01 ms →       10.51 ms   (+4.96%) |       2   →       2              |       20.03 ms →       21.02 ms   (+4.96%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.01 ms →       10.51 ms   (+4.96%) |       2   →       2              |       20.03 ms →       21.02 ms   (+4.96%) | 
+ ├ sirius::Smooth_periodic_function|inner                              |       11.27 ms →       10.06 ms  (-10.70%) |       1   →       1              |       11.27 ms →       10.06 ms  (-10.70%) | 
+ │ └ sirius::Smooth_periodic_function|inner_local                      |       11.26 ms →       10.06 ms  (-10.70%) |       1   →       1              |       11.26 ms →       10.06 ms  (-10.70%) | 
+ └ sirius::finalize                                                    |      205.58 ms →      184.48 ms  (-10.27%) |       1   →       1              |      205.58 ms →      184.48 ms  (-10.27%) | 
  ====================================================================================================================================================================================================
```
