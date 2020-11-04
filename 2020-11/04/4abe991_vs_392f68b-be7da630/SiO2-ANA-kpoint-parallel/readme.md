# Benchmark 392f68b5626168134a99cd6d4a3cc40b87322cb7 vs 4abe991ed1b67a61e2f44af0d6336c92b3f43afd
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      129.21 s  →      122.95 s    (-4.84%) |       1   →       1              |      129.21 s  →      122.95 s    (-4.84%) | 
  ├ sirius::initialize                                                  |        2.64 s  →        2.64 s    (+0.36%) |       1   →       1              |        2.64 s  →        2.64 s    (+0.36%) | 
  ├ sirius::Simulation_context::initialize                              |        2.90 s  →        2.91 s    (+0.32%) |       1   →       1              |        2.90 s  →        2.91 s    (+0.32%) | 
- │ ├ sirius::Simulation_context::init_comm                             |       13.62 ms →       23.78 ms  (+74.60%) |       1   →       1              |       13.62 ms →       23.78 ms  (+74.60%) | 
  │ ├ sirius::Unit_cell::initialize                                     |      139.05 ms →      138.30 ms   (-0.54%) |       1   →       1              |      139.05 ms →      138.30 ms   (-0.54%) | 
  │ │ ├ sirius::Atom_type::init                                         |       58.25 ms →       57.74 ms   (-0.89%) |       2   →       2              |      116.51 ms →      115.48 ms   (-0.89%) | 
  │ │ └ sirius::Unit_cell::update                                       |       22.47 ms →       22.74 ms   (+1.23%) |       1   →       1              |       22.47 ms →       22.74 ms   (+1.23%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.40 ms →        6.41 ms   (+0.08%) |       1   →       1              |        6.40 ms →        6.41 ms   (+0.08%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       16.03 ms →       16.29 ms   (+1.66%) |       1   →       1              |       16.03 ms →       16.29 ms   (+1.66%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       16.00 ms →       16.27 ms   (+1.65%) |       1   →       1              |       16.00 ms →       16.27 ms   (+1.65%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.13 ms →        4.13 ms   (+0.02%) |       1   →       1              |        4.13 ms →        4.13 ms   (+0.02%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.34 ms →        2.35 ms   (+0.18%) |       1   →       1              |        2.34 ms →        2.35 ms   (+0.18%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      106.56 μs →      111.90 μs   (+5.01%) |       1   →       1              |      106.56 μs →      111.90 μs   (+5.01%) | 
  │ └ sirius::Simulation_context::update                                |        2.71 s  →        2.70 s    (-0.03%) |       1   →       1              |        2.71 s  →        2.70 s    (-0.03%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.87 ms →       10.85 ms   (-0.17%) |       1   →       1              |       10.87 ms →       10.85 ms   (-0.17%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.44 ms →        4.44 ms   (-0.19%) |       1   →       1              |        4.44 ms →        4.44 ms   (-0.19%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.39 ms →        6.38 ms   (-0.15%) |       1   →       1              |        6.39 ms →        6.38 ms   (-0.15%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.37 ms →        6.36 ms   (-0.15%) |       1   →       1              |        6.37 ms →        6.36 ms   (-0.15%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.87 ms →        3.84 ms   (-0.76%) |       1   →       1              |        3.87 ms →        3.84 ms   (-0.76%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.34 ms   (+0.90%) |       1   →       1              |        2.32 ms →        2.34 ms   (+0.90%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      107.39 μs →      103.12 μs   (-3.98%) |       1   →       1              |      107.39 μs →      103.12 μs   (-3.98%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       62.74 ms →       62.37 ms   (-0.58%) |       2   →       2              |      125.48 ms →      124.75 ms   (-0.58%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.14 ms →        5.14 ms   (+0.05%) |       2   →       2              |       10.28 ms →       10.28 ms   (+0.05%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.46 ms →        4.47 ms   (+0.13%) |       1   →       1              |        4.46 ms →        4.47 ms   (+0.13%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.81 ms →       21.79 ms   (-0.07%) |       2   →       2              |       43.62 ms →       43.58 ms   (-0.07%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.81 ms →       14.80 ms   (-0.05%) |       2   →       2              |       29.62 ms →       29.60 ms   (-0.05%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.70 ms →       19.85 ms   (+0.75%) |       4   →       4              |       78.80 ms →       79.39 ms   (+0.75%) | 
  │   ├ sddk::Gvec::init                                                |      175.03 ms →      178.39 ms   (+1.92%) |       2   →       2              |      350.06 ms →      356.77 ms   (+1.92%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      131.56 ms →      135.15 ms   (+2.73%) |       2   →       2              |      263.12 ms →      270.30 ms   (+2.73%) | 
  │   ├ sddk::Gvec_shells                                               |      181.13 ms →      163.96 ms   (-9.48%) |       1   →       1              |      181.13 ms →      163.96 ms   (-9.48%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.32 ms →        1.31 ms   (-0.24%) |       1   →       1              |        1.32 ms →        1.31 ms   (-0.24%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      289.14 ms →      292.69 ms   (+1.23%) |       2   →       2              |      578.27 ms →      585.39 ms   (+1.23%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       35.52 ms →       35.54 ms   (+0.06%) |       1   →       1              |       35.52 ms →       35.54 ms   (+0.06%) | 
  │ ├ sirius::K_point::K_point                                          |        2.52 μs →        2.34 μs   (-7.05%) |       4   →       4              |       10.08 μs →        9.37 μs   (-7.05%) | 
  │ └ sirius::K_point_set::initialize                                   |       35.40 ms →       35.44 ms   (+0.10%) |       1   →       1              |       35.40 ms →       35.44 ms   (+0.10%) | 
  │   └ sirius::K_point::initialize                                     |       35.31 ms →       35.34 ms   (+0.08%) |       1   →       1              |       35.31 ms →       35.34 ms   (+0.08%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       18.03 ms →       17.84 ms   (-1.06%) |       1   →       1              |       18.03 ms →       17.84 ms   (-1.06%) | 
  │     │ └ sddk::Gvec::init                                            |        8.06 ms →        8.03 ms   (-0.38%) |       1   →       1              |        8.06 ms →        8.03 ms   (-0.38%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |       10.18 μs →       10.40 μs   (+2.17%) |       1   →       1              |       10.18 μs →       10.40 μs   (+2.17%) | 
  │     └ sirius::K_point::update                                       |       12.51 ms →       12.66 ms   (+1.27%) |       1   →       1              |       12.51 ms →       12.66 ms   (+1.27%) | 
  │       └ sirius::Beta_projectors                                     |        6.30 ms →        6.41 ms   (+1.65%) |       1   →       1              |        6.30 ms →        6.41 ms   (+1.65%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.78 ms →        3.83 ms   (+1.20%) |       1   →       1              |        3.78 ms →        3.83 ms   (+1.20%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.16 ms →        5.41 ms   (+4.85%) |       2   →       2              |       10.33 ms →       10.83 ms   (+4.85%) | 
  ├ sirius::Potential                                                   |      159.49 ms →      160.23 ms   (+0.47%) |       1   →       1              |      159.49 ms →      160.23 ms   (+0.47%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.71 ms →        6.11 ms   (+7.04%) |       6   →       6              |       34.26 ms →       36.67 ms   (+7.04%) | 
  │ └ sirius::Potential::update                                         |      124.50 ms →      122.80 ms   (-1.37%) |       1   →       1              |      124.50 ms →      122.80 ms   (-1.37%) | 
  │   └ sirius::Potential::generate_local_potential                     |      123.79 ms →      122.05 ms   (-1.41%) |       1   →       1              |      123.79 ms →      122.05 ms   (-1.41%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      110.89 ms →      114.74 ms   (+3.48%) |       1   →       1              |      110.89 ms →      114.74 ms   (+3.48%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       11.97 ms →        6.39 ms  (-46.60%) |       1   →       1              |       11.97 ms →        6.39 ms  (-46.60%) | 
  ├ sirius::Density                                                     |      134.59 ms →      133.62 ms   (-0.72%) |       1   →       1              |      134.59 ms →      133.62 ms   (-0.72%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.10 ms →        5.13 ms   (+0.61%) |       2   →       2              |       10.20 ms →       10.26 ms   (+0.61%) | 
  │ └ sirius::Density::update                                           |      124.12 ms →      123.08 ms   (-0.84%) |       1   →       1              |      124.12 ms →      123.08 ms   (-0.84%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      123.71 ms →      122.66 ms   (-0.85%) |       1   →       1              |      123.71 ms →      122.66 ms   (-0.85%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |      105.05 μs →      105.54 μs   (+0.47%) |       1   →       1              |      105.05 μs →      105.54 μs   (+0.47%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      112.44 ms →      116.87 ms   (+3.94%) |       1   →       1              |      112.44 ms →      116.87 ms   (+3.94%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       10.73 ms →        5.11 ms  (-52.36%) |       1   →       1              |       10.73 ms →        5.11 ms  (-52.36%) | 
  ├ sirius::Density::initial_density                                    |      178.02 ms →      174.03 ms   (-2.24%) |       1   →       1              |      178.02 ms →      174.03 ms   (-2.24%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      111.06 ms →      121.83 ms   (+9.69%) |       1   →       1              |      111.06 ms →      121.83 ms   (+9.69%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |       11.33 ms →        4.96 ms  (-56.24%) |       2   →       2              |       22.66 ms →        9.91 ms  (-56.24%) | 
+ │ └ sirius::Periodic_function::integrate                              |       12.54 ms →        9.72 ms  (-22.48%) |       1   →       1              |       12.54 ms →        9.72 ms  (-22.48%) | 
  ├ sirius::Potential::generate                                         |      595.08 ms →      590.83 ms   (-0.71%) |       1   →       1              |      595.08 ms →      590.83 ms   (-0.71%) | 
  │ ├ sirius::Potential::poisson                                        |      138.34 ms →      135.93 ms   (-1.74%) |       1   →       1              |      138.34 ms →      135.93 ms   (-1.74%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       16.47 ms →        5.31 ms  (-67.75%) |       1   →       1              |       16.47 ms →        5.31 ms  (-67.75%) | 
+ │ │ └ sirius::Periodic_function|inner                                 |       11.39 ms →        9.91 ms  (-13.00%) |       1   →       1              |       11.39 ms →        9.91 ms  (-13.00%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |       10.24 ms →        9.89 ms   (-3.33%) |       1   →       1              |       10.24 ms →        9.89 ms   (-3.33%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |       10.23 ms →        9.89 ms   (-3.33%) |       1   →       1              |       10.23 ms →        9.89 ms   (-3.33%) | 
  │ ├ sirius::Periodic_function::add                                    |      544.84 μs →      543.66 μs   (-0.22%) |       2   →       2              |        1.09 ms →        1.09 ms   (-0.22%) | 
  │ ├ sirius::Potential::xc                                             |       55.70 ms →       55.13 ms   (-1.02%) |       1   →       1              |       55.70 ms →       55.13 ms   (-1.02%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       53.39 ms →       52.76 ms   (-1.18%) |       1   →       1              |       53.39 ms →       52.76 ms   (-1.18%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.60 ms →        5.67 ms   (+1.41%) |       2   →       2              |       11.19 ms →       11.35 ms   (+1.41%) | 
+ │ │   └ sirius::Smooth_periodic_function::fft_transform               |        6.00 ms →        5.24 ms  (-12.64%) |       1   →       1              |        6.00 ms →        5.24 ms  (-12.64%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.62 ms →        5.71 ms   (+1.57%) |       1   →       1              |        5.62 ms →        5.71 ms   (+1.57%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       93.53 ms →       92.66 ms   (-0.93%) |       1   →       1              |       93.53 ms →       92.66 ms   (-0.93%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      299.48 ms →      298.96 ms   (-0.17%) |       1   →       1              |      299.48 ms →      298.96 ms   (-0.17%) | 
  ├ sirius::Hamiltonian0                                                |        8.58 ms →        8.38 ms   (-2.31%) |       1   →       1              |        8.58 ms →        8.38 ms   (-2.31%) | 
  │ ├ sirius::Local_operator                                            |        8.20 ms →        8.03 ms   (-2.13%) |       1   →       1              |        8.20 ms →        8.03 ms   (-2.13%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.74 ms →        4.72 ms   (-0.30%) |       1   →       1              |        4.74 ms →        4.72 ms   (-0.30%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.54 ms →        2.39 ms   (-6.09%) |       1   →       1              |        2.54 ms →        2.39 ms   (-6.09%) | 
  │ ├ sirius::Non_local_operator                                        |       63.46 μs →       62.24 μs   (-1.92%) |       2   →       2              |      126.92 μs →      124.49 μs   (-1.92%) | 
  │ ├ sirius::D_operator::initialize                                    |      100.26 μs →       97.97 μs   (-2.29%) |       1   →       1              |      100.26 μs →       97.97 μs   (-2.29%) | 
  │ └ sirius::Q_operator::initialize                                    |       78.47 μs →       72.96 μs   (-7.02%) |       1   →       1              |       78.47 μs →       72.96 μs   (-7.02%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.85 s  →        1.86 s    (+0.75%) |       1   →       1              |        1.85 s  →        1.86 s    (+0.75%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.06 ms →       18.62 ms   (+3.12%) |       1   →       1              |       18.06 ms →       18.62 ms   (+3.12%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      185.62 μs →      188.68 μs   (+1.65%) |       1   →       1              |      185.62 μs →      188.68 μs   (+1.65%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       17.87 ms →       18.43 ms   (+3.13%) |       1   →       1              |       17.87 ms →       18.43 ms   (+3.13%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.83 s  →        1.84 s    (+0.72%) |       1   →       1              |        1.83 s  →        1.84 s    (+0.72%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      124.91 ms →      127.24 ms   (+1.86%) |       4   →       4              |      499.63 ms →      508.95 ms   (+1.86%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       51.99 ms →       52.96 ms   (+1.87%) |       1   →       1              |       51.99 ms →       52.96 ms   (+1.87%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       20.99 ms →       21.01 ms   (+0.10%) |       1   →       1              |       20.99 ms →       21.01 ms   (+0.10%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      641.51 ms →      638.88 ms   (-0.41%) |       1   →       1              |      641.51 ms →      638.88 ms   (-0.41%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      301.53 ms →      297.31 ms   (-1.40%) |       1   →       1              |      301.53 ms →      297.31 ms   (-1.40%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.24 μs →        3.43 μs   (+5.83%) |       1   →       1              |        3.24 μs →        3.43 μs   (+5.83%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.43 μs →        2.46 μs   (+1.19%) |       1   →       1              |        2.43 μs →        2.46 μs   (+1.19%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      360.00 ns →      355.00 ns   (-1.39%) |       1   →       1              |      360.00 ns →      355.00 ns   (-1.39%) | 
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      570.00 ns →      502.00 ns  (-11.93%) |       1   →       1              |      570.00 ns →      502.00 ns  (-11.93%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.22 ms →        9.23 ms   (+0.02%) |       1   →       1              |        9.22 ms →        9.23 ms   (+0.02%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      121.24 ms →      121.44 ms   (+0.17%) |       1   →       1              |      121.24 ms →      121.44 ms   (+0.17%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      104.74 ms →      105.44 ms   (+0.67%) |       2   →       2              |      209.48 ms →      210.88 ms   (+0.67%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       40.57 ms →       40.53 ms   (-0.08%) |       2   →       2              |       81.13 ms →       81.06 ms   (-0.08%) | 
  │ │ │ └ sddk::wf_inner                                                |       40.03 ms →       40.00 ms   (-0.09%) |       2   →       2              |       80.06 ms →       79.99 ms   (-0.09%) | 
+ │ │ │   ├ sddk::wf_inner|scale                                        |       45.50 ns →       18.50 ns  (-59.34%) |       2   →       2              |       91.00 ns →       37.00 ns  (-59.34%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       39.58 ms →       39.52 ms   (-0.14%) |       2   →       2              |       79.15 ms →       79.04 ms   (-0.14%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       20.50 ns →       46.50 ns (+126.83%) |       2   →       2              |       41.00 ns →       93.00 ns (+126.83%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       61.47 ms →       56.33 ms   (-8.36%) |       1   →       1              |       61.47 ms →       56.33 ms   (-8.36%) | 
  │ │ └ sddk::wf_trans                                                  |       30.77 ms →       30.76 ms   (-0.05%) |       1   →       1              |       30.77 ms →       30.76 ms   (-0.05%) | 
  │ │   └ sddk::wf_trans|pw                                             |       30.77 ms →       30.75 ms   (-0.05%) |       1   →       1              |       30.77 ms →       30.75 ms   (-0.05%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      720.00 ns →      484.00 ns  (-32.78%) |       1   →       1              |      720.00 ns →      484.00 ns  (-32.78%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      119.68 s  →      113.43 s    (-5.22%) |       1   →       1              |      119.68 s  →      113.43 s    (-5.22%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.76 ms →        5.84 ms   (+1.42%) |      19   →      19              |      109.37 ms →      110.93 ms   (+1.42%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.59 s  →        4.71 s    (+2.64%) |      26   →      24     (-7.69%) |      119.28 s  →      113.01 s    (-5.25%) | 
+ │ │ ├ sirius::Hamiltonian0                                            |        5.19 ms →        4.38 ms  (-15.61%) |      26   →      24     (-7.69%) |      134.89 ms →      105.07 ms  (-22.10%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        4.83 ms →        4.01 ms  (-16.88%) |      26   →      24     (-7.69%) |      125.51 ms →       96.30 ms  (-23.27%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function                            |      961.43 μs →      925.16 μs   (-3.77%) |      26   →      24     (-7.69%) |       25.00 ms →       22.20 ms  (-11.17%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.97 ms →        2.20 ms  (-26.10%) |      26   →      24     (-7.69%) |       77.31 ms →       52.74 ms  (-31.78%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       63.77 μs →       64.56 μs   (+1.24%) |      52   →      48     (-7.69%) |        3.32 ms →        3.10 ms   (-6.55%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       85.85 μs →       86.80 μs   (+1.12%) |      26   →      24     (-7.69%) |        2.23 ms →        2.08 ms   (-6.66%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       76.34 μs →       78.00 μs   (+2.18%) |      26   →      24     (-7.69%) |        1.98 ms →        1.87 ms   (-5.68%) | 
  │ │ ├ sirius::Band::solve                                             |        2.60 s  →        2.75 s    (+5.88%) |      26   →      24     (-7.69%) |       67.52 s  →       65.99 s    (-2.26%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      154.15 μs →      155.96 μs   (+1.17%) |      26   →      24     (-7.69%) |        4.01 ms →        3.74 ms   (-6.61%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      146.69 μs →      148.03 μs   (+0.92%) |      26   →      24     (-7.69%) |        3.81 ms →        3.55 ms   (-6.85%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.69 μs →        5.98 μs   (+5.18%) |      26   →      24     (-7.69%) |      147.82 μs →      143.52 μs   (-2.91%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.48 s  →        2.63 s    (+5.86%) |      26   →      24     (-7.69%) |       64.47 s  →       63.00 s    (-2.28%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       95.28 ms →       98.71 ms   (+3.59%) |      26   →      24     (-7.69%) |        2.48 s  →        2.37 s    (-4.38%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.73 ms →        8.25 ms   (+6.73%) |     156   →     144     (-7.69%) |        1.21 s  →        1.19 s    (-1.48%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        5.95 ms →        5.91 ms   (-0.80%) |      26   →      24     (-7.69%) |      154.78 ms →      141.73 ms   (-8.43%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      346.84 μs →      348.82 μs   (+0.57%) |      26   →      24     (-7.69%) |        9.02 ms →        8.37 ms   (-7.16%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.31 ms →        2.31 ms   (+0.31%) |      52   →      48     (-7.69%) |      119.94 ms →      111.06 ms   (-7.41%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.34 s  →        2.48 s    (+6.06%) |      26   →      24     (-7.69%) |       60.91 s  →       59.63 s    (-2.09%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      137.74 ms →      135.03 ms   (-1.97%) |     262   →     260     (-0.76%) |       36.09 s  →       35.11 s    (-2.71%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       55.73 ms →       54.51 ms   (-2.18%) |     262   →     260     (-0.76%) |       14.60 s  →       14.17 s    (-2.93%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.01 μs →        2.23 μs  (+11.12%) |     262   →     260     (-0.76%) |      525.33 μs →      579.30 μs  (+10.27%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.69 μs →        1.90 μs  (+12.08%) |     262   →     260     (-0.76%) |      443.90 μs →      493.72 μs  (+11.22%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      439.86 ns →      476.12 ns   (+8.24%) |     262   →     260     (-0.76%) |      115.24 μs →      123.79 μs   (+7.42%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      465.83 ns →      550.37 ns  (+18.15%) |     262   →     260     (-0.76%) |      122.05 μs →      143.09 μs  (+17.25%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.46 ms →        7.45 ms   (-0.14%) |     262   →     260     (-0.76%) |        1.95 s  →        1.94 s    (-0.90%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       25.41 ms →       24.80 ms   (-2.40%) |     262   →     260     (-0.76%) |        6.66 s  →        6.45 s    (-3.15%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       24.56 ms →       24.13 ms   (-1.78%) |     524   →     520     (-0.76%) |       12.87 s  →       12.55 s    (-2.53%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       35.92 ms →       35.54 ms   (-1.04%) |     262   →     260     (-0.76%) |        9.41 s  →        9.24 s    (-1.79%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        6.23 ms →        6.14 ms   (-1.42%) |     498   →     496     (-0.40%) |        3.10 s  →        3.05 s    (-1.82%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       62.47 ns →       43.92 ns  (-29.69%) |     498   →     496     (-0.40%) |       31.11 μs →       21.78 μs  (-29.98%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        5.12 ms →        5.03 ms   (-1.70%) |     498   →     496     (-0.40%) |        2.55 s  →        2.50 s    (-2.10%) | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       31.04 ns →       33.27 ns   (+7.16%) |     498   →     496     (-0.40%) |       15.46 μs →       16.50 μs   (+6.73%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      659.87 μs →      633.97 μs   (-3.92%) |     262   →     260     (-0.76%) |      172.89 ms →      164.83 ms   (-4.66%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       10.32 ms →       10.01 ms   (-3.02%) |     262   →     260     (-0.76%) |        2.70 s  →        2.60 s    (-3.76%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |       14.52 ms →       14.51 ms   (-0.08%) |     236   →     236              |        3.43 s  →        3.42 s    (-0.08%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        4.84 ms →        4.84 ms   (-0.08%) |     708   →     708              |        3.43 s  →        3.42 s    (-0.08%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       10.38 ms →       10.26 ms   (-1.17%) |     262   →     260     (-0.76%) |        2.72 s  →        2.67 s    (-1.92%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |       10.18 ms →       10.05 ms   (-1.24%) |     262   →     260     (-0.76%) |        2.67 s  →        2.61 s    (-2.00%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       47.05 ns →       23.23 ns  (-50.62%) |     262   →     260     (-0.76%) |       12.33 μs →        6.04 μs  (-51.00%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        9.07 ms →        8.94 ms   (-1.38%) |     262   →     260     (-0.76%) |        2.38 s  →        2.32 s    (-2.13%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       49.44 ns →       54.88 ns  (+10.99%) |     262   →     260     (-0.76%) |       12.95 μs →       14.27 μs  (+10.14%) | 
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       18.33 ms →       18.61 ms   (+1.54%) |     262   →     260     (-0.76%) |        4.80 s  →        4.84 s    (+0.77%) | 
  │ │ │ │   ├ sirius::residuals                                         |       13.15 ms →       13.01 ms   (-1.00%) |     252   →     250     (-0.79%) |        3.31 s  →        3.25 s    (-1.79%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       11.72 ms →       11.55 ms   (-1.46%) |     242   →     241     (-0.41%) |        2.84 s  →        2.78 s    (-1.86%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        5.86 ms →        5.78 ms   (-1.46%) |     484   →     482     (-0.41%) |        2.84 s  →        2.78 s    (-1.86%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.71 ms →        1.70 ms   (-0.61%) |     242   →     241     (-0.41%) |      413.01 ms →      408.81 ms   (-1.02%) | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       53.75 ms →       54.41 ms   (+1.23%) |      85   →      83     (-2.35%) |        4.57 s  →        4.52 s    (-1.15%) | 
  │ │ │ │     └ sddk::wf_trans                                          |       31.47 ms →       31.54 ms   (+0.23%) |     144   →     142     (-1.39%) |        4.53 s  →        4.48 s    (-1.16%) | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |       22.32 ms →       22.28 ms   (-0.17%) |     203   →     201     (-0.99%) |        4.53 s  →        4.48 s    (-1.16%) | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      410.77 ns →      430.08 ns   (+4.70%) |      26   →      24     (-7.69%) |       10.68 μs →       10.32 μs   (-3.35%) | 
+ │ │ │ └ sirius::K_point_set::sync_band_energies                       |       30.30 μs →       29.47 μs   (-2.71%) |      26   →      24     (-7.69%) |      787.69 μs →      707.36 μs  (-10.20%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      623.75 μs →      613.19 μs   (-1.69%) |      26   →      24     (-7.69%) |       16.22 ms →       14.72 ms   (-9.26%) | 
  │ │ ├ sirius::Density::generate                                       |      778.87 ms →      771.07 ms   (-1.00%) |      26   →      24     (-7.69%) |       20.25 s  →       18.51 s    (-8.62%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      401.37 ms →      401.69 ms   (+0.08%) |      26   →      24     (-7.69%) |       10.44 s  →        9.64 s    (-7.62%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.77 μs →        3.57 μs   (-5.26%) |      26   →      24     (-7.69%) |       98.10 μs →       85.79 μs  (-12.55%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.45 μs →        3.26 μs   (-5.47%) |      26   →      24     (-7.69%) |       89.79 μs →       78.35 μs  (-12.74%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |      100.53 ms →      100.62 ms   (+0.09%) |      26   →      24     (-7.69%) |        2.61 s  →        2.41 s    (-7.61%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       10.25 μs →       10.76 μs   (+4.95%) |      26   →      24     (-7.69%) |      266.54 μs →      258.20 μs   (-3.13%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.13 ms →        7.13 ms   (-0.00%) |      26   →      24     (-7.69%) |      185.40 ms →      171.13 ms   (-7.70%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       91.51 ms →       91.57 ms   (+0.07%) |      26   →      24     (-7.69%) |        2.38 s  →        2.20 s    (-7.63%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      627.15 ns →      569.29 ns   (-9.23%) |      26   →      24     (-7.69%) |       16.31 μs →       13.66 μs  (-16.21%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      162.37 ms →      164.45 ms   (+1.28%) |      26   →      24     (-7.69%) |        4.22 s  →        3.95 s    (-6.51%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.63 ms   (-0.35%) |      26   →      24     (-7.69%) |       42.65 ms →       39.24 ms   (-8.01%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.32 ms →       88.26 ms   (-0.07%) |      26   →      24     (-7.69%) |        2.30 s  →        2.12 s    (-7.76%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.10 ms →       88.04 ms   (-0.07%) |      26   →      24     (-7.69%) |        2.29 s  →        2.11 s    (-7.76%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      277.77 ms →      276.08 ms   (-0.61%) |      26   →      24     (-7.69%) |        7.22 s  →        6.63 s    (-8.25%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      277.77 ms →      276.08 ms   (-0.61%) |      26   →      24     (-7.69%) |        7.22 s  →        6.63 s    (-8.25%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.32 ms →       24.23 ms   (-0.38%) |      26   →      24     (-7.69%) |      632.34 ms →      581.49 ms   (-8.04%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      228.87 ms →      227.69 ms   (-0.52%) |      26   →      24     (-7.69%) |        5.95 s  →        5.46 s    (-8.17%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       23.38 ms →       22.99 ms   (-1.70%) |      26   →      24     (-7.69%) |      607.99 ms →      551.69 ms   (-9.26%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       81.74 ms →       80.19 ms   (-1.90%) |      26   →      24     (-7.69%) |        2.13 s  →        1.92 s    (-9.44%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |       14.40 ms →        9.39 ms  (-34.82%) |      26   →      24     (-7.69%) |      374.46 ms →      225.30 ms  (-39.83%) | 
+ │ │ ├ sirius::Density::mix                                            |      223.26 ms →      201.89 ms   (-9.57%) |      26   →      24     (-7.69%) |        5.80 s  →        4.85 s   (-16.53%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      971.04 μs →      941.51 μs   (-3.04%) |      26   →      24     (-7.69%) |       25.25 ms →       22.60 ms  (-10.50%) | 
+ │ │ │ ├ sirius::Periodic_function|inner                               |       11.06 ms →       10.54 ms   (-4.73%) |     334   →     304     (-8.98%) |        3.69 s  →        3.20 s   (-13.28%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.86 ms →        9.98 ms   (-8.18%) |     334   →     304     (-8.98%) |        3.63 s  →        3.03 s   (-16.42%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.86 ms →        9.97 ms   (-8.18%) |     334   →     304     (-8.98%) |        3.63 s  →        3.03 s   (-16.42%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        6.11 ms →        6.74 ms  (+10.39%) |      26   →      24     (-7.69%) |      158.80 ms →      161.81 ms   (+1.90%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.26 ms →        5.90 ms  (+12.16%) |      26   →      24     (-7.69%) |      136.88 ms →      141.71 ms   (+3.53%) | 
  │ │ ├ sirius::Potential::generate                                     |      580.84 ms →      577.46 ms   (-0.58%) |      26   →      24     (-7.69%) |       15.10 s  →       13.86 s    (-8.23%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      137.48 ms →      136.49 ms   (-0.72%) |      26   →      24     (-7.69%) |        3.57 s  →        3.28 s    (-8.36%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       16.04 ms →        5.21 ms  (-67.53%) |      26   →      24     (-7.69%) |      416.98 ms →      124.96 ms  (-70.03%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner                             |       10.71 ms →       10.30 ms   (-3.77%) |      26   →      24     (-7.69%) |      278.35 ms →      247.26 ms  (-11.17%) | 
+ │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.33 ms →        9.93 ms   (-3.87%) |      26   →      24     (-7.69%) |      268.52 ms →      238.28 ms  (-11.26%) | 
+ │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.33 ms →        9.93 ms   (-3.87%) |      26   →      24     (-7.69%) |      268.50 ms →      238.27 ms  (-11.26%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      543.12 μs →      540.57 μs   (-0.47%) |      52   →      48     (-7.69%) |       28.24 ms →       25.95 ms   (-8.13%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       48.97 ms →       48.83 ms   (-0.29%) |      26   →      24     (-7.69%) |        1.27 s  →        1.17 s    (-7.96%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.63 ms →       46.54 ms   (-0.20%) |      26   →      24     (-7.69%) |        1.21 s  →        1.12 s    (-7.88%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.02 ms →        2.97 ms   (-1.69%) |      52   →      48     (-7.69%) |      156.88 ms →      142.37 ms   (-9.25%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.25 ms →        5.38 ms   (+2.44%) |      26   →      24     (-7.69%) |      136.43 ms →      129.00 ms   (-5.44%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.41 ms →        6.64 ms   (+3.53%) |      26   →      24     (-7.69%) |      166.68 ms →      159.30 ms   (-4.43%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.89 ms →       90.89 ms   (-0.00%) |      26   →      24     (-7.69%) |        2.36 s  →        2.18 s    (-7.70%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      294.72 ms →      292.28 ms   (-0.83%) |      26   →      24     (-7.69%) |        7.66 s  →        7.01 s    (-8.46%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      281.33 ms →      282.58 ms   (+0.44%) |      26   →      24     (-7.69%) |        7.31 s  →        6.78 s    (-7.28%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      281.33 ms →      282.57 ms   (+0.44%) |      26   →      24     (-7.69%) |        7.31 s  →        6.78 s    (-7.28%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.02 ms →       27.19 ms   (+0.60%) |      26   →      24     (-7.69%) |      702.64 ms →      652.51 ms   (-7.14%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      226.51 ms →      227.63 ms   (+0.50%) |      26   →      24     (-7.69%) |        5.89 s  →        5.46 s    (-7.23%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       24.00 ms →       24.00 ms   (+0.01%) |      26   →      24     (-7.69%) |      623.96 ms →      576.02 ms   (-7.68%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.46 ms →        5.45 ms   (-0.28%) |      26   →      24     (-7.69%) |      142.06 ms →      130.76 ms   (-7.95%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.37 ms →       10.65 ms   (+2.73%) |     182   →     168     (-7.69%) |        1.89 s  →        1.79 s    (-5.18%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.90 ms →       10.19 ms   (+2.97%) |     182   →     168     (-7.69%) |        1.80 s  →        1.71 s    (-4.95%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.90 ms →       10.19 ms   (+2.97%) |     182   →     168     (-7.69%) |        1.80 s  →        1.71 s    (-4.95%) | 
+ │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.74 ms →       10.33 ms   (-3.88%) |      78   →      72     (-7.69%) |      838.04 ms →      743.57 ms  (-11.27%) | 
+ │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.31 ms →        9.76 ms   (-5.26%) |      78   →      72     (-7.69%) |      803.88 ms →      702.99 ms  (-12.55%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |       10.06 ms →        9.95 ms   (-1.13%) |      26   →      24     (-7.69%) |      261.57 ms →      238.71 ms   (-8.74%) | 
  │ │ └ sirius::Density::get_magnetisation                              |      108.59 μs →      111.59 μs   (+2.76%) |      26   →      24     (-7.69%) |        2.82 ms →        2.68 ms   (-5.14%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |      103.67 μs →      106.52 μs   (+2.76%) |      26   →      24     (-7.69%) |        2.70 ms →        2.56 ms   (-5.15%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.16 ms →        5.29 ms   (+2.36%) |       2   →       2              |       10.33 ms →       10.57 ms   (+2.36%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.66 ms →       10.66 ms   (-0.01%) |       6   →       6              |       63.95 ms →       63.94 ms   (-0.01%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        9.80 ms →       10.48 ms   (+6.95%) |       6   →       6              |       58.79 ms →       62.87 ms   (+6.95%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        9.80 ms →       10.48 ms   (+6.95%) |       6   →       6              |       58.79 ms →       62.87 ms   (+6.95%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.34 ms →        9.98 ms   (-3.44%) |       3   →       3              |       31.01 ms →       29.94 ms   (-3.44%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.06 ms →        9.96 ms   (-1.00%) |       3   →       3              |       30.17 ms →       29.87 ms   (-1.00%) | 
  ├ sirius::Periodic_function|inner                                     |       10.03 ms →       10.37 ms   (+3.34%) |       2   →       2              |       20.06 ms →       20.73 ms   (+3.34%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.02 ms →       10.14 ms   (+1.14%) |       2   →       2              |       20.05 ms →       20.28 ms   (+1.14%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.02 ms →       10.14 ms   (+1.14%) |       2   →       2              |       20.05 ms →       20.28 ms   (+1.14%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.44 ms →       11.32 ms   (+8.46%) |       1   →       1              |       10.44 ms →       11.32 ms   (+8.46%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.43 ms →        9.62 ms   (-7.76%) |       1   →       1              |       10.43 ms →        9.62 ms   (-7.76%) | 
+ └ sirius::finalize                                                    |      220.62 ms →      185.06 ms  (-16.12%) |       1   →       1              |      220.62 ms →      185.06 ms  (-16.12%) | 
  ====================================================================================================================================================================================================
```
