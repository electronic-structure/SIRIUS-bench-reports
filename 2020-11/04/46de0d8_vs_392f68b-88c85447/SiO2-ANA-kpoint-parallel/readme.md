# Benchmark 392f68b5626168134a99cd6d4a3cc40b87322cb7 vs 46de0d896d343d7768c9da756627e739ed0717b7
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      129.20 s  →      128.50 s    (-0.54%) |       1   →       1              |      129.20 s  →      128.50 s    (-0.54%) | 
  ├ sirius::initialize                                                  |        2.68 s  →        2.85 s    (+6.21%) |       1   →       1              |        2.68 s  →        2.85 s    (+6.21%) | 
  ├ sirius::Simulation_context::initialize                              |        2.96 s  →        2.90 s    (-2.07%) |       1   →       1              |        2.96 s  →        2.90 s    (-2.07%) | 
- │ ├ sirius::Simulation_context::init_comm                             |        4.45 ms →       40.17 ms (+802.47%) |       1   →       1              |        4.45 ms →       40.17 ms (+802.47%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      181.08 ms →      129.91 ms  (-28.26%) |       1   →       1              |      181.08 ms →      129.91 ms  (-28.26%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       79.31 ms →       53.60 ms  (-32.41%) |       2   →       2              |      158.62 ms →      107.20 ms  (-32.41%) | 
  │ │ └ sirius::Unit_cell::update                                       |       22.39 ms →       22.62 ms   (+1.06%) |       1   →       1              |       22.39 ms →       22.62 ms   (+1.06%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.03 ms →        6.32 ms   (+4.89%) |       1   →       1              |        6.03 ms →        6.32 ms   (+4.89%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       16.32 ms →       16.26 ms   (-0.36%) |       1   →       1              |       16.32 ms →       16.26 ms   (-0.36%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       16.29 ms →       16.24 ms   (-0.36%) |       1   →       1              |       16.29 ms →       16.24 ms   (-0.36%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.13 ms →        4.14 ms   (+0.24%) |       1   →       1              |        4.13 ms →        4.14 ms   (+0.24%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.35 ms   (+0.48%) |       1   →       1              |        2.33 ms →        2.35 ms   (+0.48%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      106.18 μs →      110.76 μs   (+4.32%) |       1   →       1              |      106.18 μs →      110.76 μs   (+4.32%) | 
  │ └ sirius::Simulation_context::update                                |        2.73 s  →        2.69 s    (-1.68%) |       1   →       1              |        2.73 s  →        2.69 s    (-1.68%) | 
  │   ├ sirius::Unit_cell::update                                       |       11.10 ms →       10.78 ms   (-2.90%) |       1   →       1              |       11.10 ms →       10.78 ms   (-2.90%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.71 ms →        4.35 ms   (-7.55%) |       1   →       1              |        4.71 ms →        4.35 ms   (-7.55%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.36 ms →        6.40 ms   (+0.57%) |       1   →       1              |        6.36 ms →        6.40 ms   (+0.57%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.34 ms →        6.38 ms   (+0.58%) |       1   →       1              |        6.34 ms →        6.38 ms   (+0.58%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.83 ms →        3.86 ms   (+0.69%) |       1   →       1              |        3.83 ms →        3.86 ms   (+0.69%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.34 ms   (+0.44%) |       1   →       1              |        2.33 ms →        2.34 ms   (+0.44%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      106.45 μs →      103.27 μs   (-2.99%) |       1   →       1              |      106.45 μs →      103.27 μs   (-2.99%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       62.76 ms →       62.37 ms   (-0.61%) |       2   →       2              |      125.51 ms →      124.75 ms   (-0.61%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.16 ms →        5.13 ms   (-0.74%) |       2   →       2              |       10.33 ms →       10.25 ms   (-0.74%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.53 ms →        4.47 ms   (-1.32%) |       1   →       1              |        4.53 ms →        4.47 ms   (-1.32%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.76 ms →       21.77 ms   (+0.05%) |       2   →       2              |       43.53 ms →       43.55 ms   (+0.05%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.81 ms →       14.80 ms   (-0.06%) |       2   →       2              |       29.62 ms →       29.60 ms   (-0.06%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.80 ms →       19.79 ms   (-0.05%) |       4   →       4              |       79.20 ms →       79.16 ms   (-0.05%) | 
  │   ├ sddk::Gvec::init                                                |      174.24 ms →      171.88 ms   (-1.35%) |       2   →       2              |      348.49 ms →      343.77 ms   (-1.35%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      130.87 ms →      128.56 ms   (-1.77%) |       2   →       2              |      261.74 ms →      257.12 ms   (-1.77%) | 
  │   ├ sddk::Gvec_shells                                               |      191.51 ms →      175.01 ms   (-8.62%) |       1   →       1              |      191.51 ms →      175.01 ms   (-8.62%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.32 ms →        1.32 ms   (+0.20%) |       1   →       1              |        1.32 ms →        1.32 ms   (+0.20%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      292.64 ms →      292.22 ms   (-0.14%) |       2   →       2              |      585.28 ms →      584.44 ms   (-0.14%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       35.44 ms →       35.48 ms   (+0.10%) |       1   →       1              |       35.44 ms →       35.48 ms   (+0.10%) | 
- │ ├ sirius::K_point::K_point                                          |        2.31 μs →        2.63 μs  (+13.96%) |       4   →       4              |        9.23 μs →       10.52 μs  (+13.96%) | 
  │ └ sirius::K_point_set::initialize                                   |       35.33 ms →       35.38 ms   (+0.14%) |       1   →       1              |       35.33 ms →       35.38 ms   (+0.14%) | 
  │   └ sirius::K_point::initialize                                     |       35.23 ms →       35.27 ms   (+0.12%) |       1   →       1              |       35.23 ms →       35.27 ms   (+0.12%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       17.84 ms →       17.96 ms   (+0.65%) |       1   →       1              |       17.84 ms →       17.96 ms   (+0.65%) | 
  │     │ └ sddk::Gvec::init                                            |        8.02 ms →        8.05 ms   (+0.38%) |       1   →       1              |        8.02 ms →        8.05 ms   (+0.38%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        9.24 μs →        9.78 μs   (+5.82%) |       1   →       1              |        9.24 μs →        9.78 μs   (+5.82%) | 
  │     └ sirius::K_point::update                                       |       12.54 ms →       12.52 ms   (-0.20%) |       1   →       1              |       12.54 ms →       12.52 ms   (-0.20%) | 
  │       └ sirius::Beta_projectors                                     |        6.27 ms →        6.22 ms   (-0.71%) |       1   →       1              |        6.27 ms →        6.22 ms   (-0.71%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.66 ms →        3.66 ms   (-0.10%) |       1   →       1              |        3.66 ms →        3.66 ms   (-0.10%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.17 ms →        5.32 ms   (+2.83%) |       2   →       2              |       10.35 ms →       10.64 ms   (+2.83%) | 
  ├ sirius::Potential                                                   |      163.43 ms →      158.56 ms   (-2.98%) |       1   →       1              |      163.43 ms →      158.56 ms   (-2.98%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        6.13 ms →        5.79 ms   (-5.53%) |       6   →       6              |       36.75 ms →       34.72 ms   (-5.53%) | 
  │ └ sirius::Potential::update                                         |      125.97 ms →      123.09 ms   (-2.28%) |       1   →       1              |      125.97 ms →      123.09 ms   (-2.28%) | 
  │   └ sirius::Potential::generate_local_potential                     |      125.24 ms →      122.36 ms   (-2.30%) |       1   →       1              |      125.24 ms →      122.36 ms   (-2.30%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      106.44 ms →      111.27 ms   (+4.53%) |       1   →       1              |      106.44 ms →      111.27 ms   (+4.53%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       17.92 ms →       10.21 ms  (-43.03%) |       1   →       1              |       17.92 ms →       10.21 ms  (-43.03%) | 
  ├ sirius::Density                                                     |      136.03 ms →      134.13 ms   (-1.39%) |       1   →       1              |      136.03 ms →      134.13 ms   (-1.39%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.08 ms →        5.25 ms   (+3.48%) |       2   →       2              |       10.15 ms →       10.50 ms   (+3.48%) | 
  │ └ sirius::Density::update                                           |      125.61 ms →      123.35 ms   (-1.79%) |       1   →       1              |      125.61 ms →      123.35 ms   (-1.79%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      125.20 ms →      122.92 ms   (-1.82%) |       1   →       1              |      125.20 ms →      122.92 ms   (-1.82%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |      105.71 μs →      105.20 μs   (-0.48%) |       1   →       1              |      105.71 μs →      105.20 μs   (-0.48%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      109.30 ms →      112.75 ms   (+3.16%) |       1   →       1              |      109.30 ms →      112.75 ms   (+3.16%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       15.36 ms →        9.63 ms  (-37.29%) |       1   →       1              |       15.36 ms →        9.63 ms  (-37.29%) | 
  ├ sirius::Density::initial_density                                    |      179.35 ms →      179.08 ms   (-0.15%) |       1   →       1              |      179.35 ms →      179.08 ms   (-0.15%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      108.69 ms →      111.29 ms   (+2.39%) |       1   →       1              |      108.69 ms →      111.29 ms   (+2.39%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |       12.43 ms →       11.59 ms   (-6.81%) |       2   →       2              |       24.86 ms →       23.17 ms   (-6.81%) | 
- │ └ sirius::Periodic_function::integrate                              |       10.85 ms →       12.79 ms  (+17.90%) |       1   →       1              |       10.85 ms →       12.79 ms  (+17.90%) | 
  ├ sirius::Potential::generate                                         |      594.30 ms →      591.77 ms   (-0.42%) |       1   →       1              |      594.30 ms →      591.77 ms   (-0.42%) | 
  │ ├ sirius::Potential::poisson                                        |      138.90 ms →      137.37 ms   (-1.11%) |       1   →       1              |      138.90 ms →      137.37 ms   (-1.11%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       21.36 ms →       17.14 ms  (-19.76%) |       1   →       1              |       21.36 ms →       17.14 ms  (-19.76%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.55 ms →        9.88 ms   (-6.35%) |       1   →       1              |       10.55 ms →        9.88 ms   (-6.35%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |       10.23 ms →        9.82 ms   (-4.05%) |       1   →       1              |       10.23 ms →        9.82 ms   (-4.05%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |       10.23 ms →        9.81 ms   (-4.05%) |       1   →       1              |       10.23 ms →        9.81 ms   (-4.05%) | 
  │ ├ sirius::Periodic_function::add                                    |      551.77 μs →      546.41 μs   (-0.97%) |       2   →       2              |        1.10 ms →        1.09 ms   (-0.97%) | 
  │ ├ sirius::Potential::xc                                             |       55.29 ms →       54.59 ms   (-1.27%) |       1   →       1              |       55.29 ms →       54.59 ms   (-1.27%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       53.01 ms →       52.27 ms   (-1.39%) |       1   →       1              |       53.01 ms →       52.27 ms   (-1.39%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.58 ms →        5.64 ms   (+1.09%) |       2   →       2              |       11.17 ms →       11.29 ms   (+1.09%) | 
+ │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.96 ms →        5.26 ms  (-11.74%) |       1   →       1              |        5.96 ms →        5.26 ms  (-11.74%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.81 ms →        5.65 ms   (-2.71%) |       1   →       1              |        5.81 ms →        5.65 ms   (-2.71%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.72 ms →       92.66 ms   (-0.07%) |       1   →       1              |       92.72 ms →       92.66 ms   (-0.07%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      299.10 ms →      299.06 ms   (-0.01%) |       1   →       1              |      299.10 ms →      299.06 ms   (-0.01%) | 
  ├ sirius::Hamiltonian0                                                |        8.35 ms →        8.37 ms   (+0.24%) |       1   →       1              |        8.35 ms →        8.37 ms   (+0.24%) | 
  │ ├ sirius::Local_operator                                            |        8.00 ms →        8.02 ms   (+0.23%) |       1   →       1              |        8.00 ms →        8.02 ms   (+0.23%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.73 ms →        4.72 ms   (-0.06%) |       1   →       1              |        4.73 ms →        4.72 ms   (-0.06%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.36 ms →        2.37 ms   (+0.60%) |       1   →       1              |        2.36 ms →        2.37 ms   (+0.60%) | 
  │ ├ sirius::Non_local_operator                                        |       62.72 μs →       62.28 μs   (-0.69%) |       2   →       2              |      125.44 μs →      124.57 μs   (-0.69%) | 
  │ ├ sirius::D_operator::initialize                                    |       96.69 μs →       98.08 μs   (+1.43%) |       1   →       1              |       96.69 μs →       98.08 μs   (+1.43%) | 
  │ └ sirius::Q_operator::initialize                                    |       72.64 μs →       74.18 μs   (+2.11%) |       1   →       1              |       72.64 μs →       74.18 μs   (+2.11%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.85 s  →        1.89 s    (+2.05%) |       1   →       1              |        1.85 s  →        1.89 s    (+2.05%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.62 ms →       19.69 ms   (+5.80%) |       1   →       1              |       18.62 ms →       19.69 ms   (+5.80%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      185.22 μs →      188.29 μs   (+1.66%) |       1   →       1              |      185.22 μs →      188.29 μs   (+1.66%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       18.43 ms →       19.50 ms   (+5.84%) |       1   →       1              |       18.43 ms →       19.50 ms   (+5.84%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.83 s  →        1.87 s    (+2.01%) |       1   →       1              |        1.83 s  →        1.87 s    (+2.01%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      127.54 ms →      128.92 ms   (+1.08%) |       4   →       4              |      510.17 ms →      515.70 ms   (+1.08%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       52.27 ms →       52.10 ms   (-0.33%) |       1   →       1              |       52.27 ms →       52.10 ms   (-0.33%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.11 ms →       20.98 ms   (-0.62%) |       1   →       1              |       21.11 ms →       20.98 ms   (-0.62%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      638.09 ms →      635.92 ms   (-0.34%) |       1   →       1              |      638.09 ms →      635.92 ms   (-0.34%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      297.42 ms →      297.33 ms   (-0.03%) |       1   →       1              |      297.42 ms →      297.33 ms   (-0.03%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.09 μs →        3.19 μs   (+3.40%) |       1   →       1              |        3.09 μs →        3.19 μs   (+3.40%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.13 μs →        2.14 μs   (+0.52%) |       1   →       1              |        2.13 μs →        2.14 μs   (+0.52%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      358.00 ns →      364.00 ns   (+1.68%) |       1   →       1              |      358.00 ns →      364.00 ns   (+1.68%) | 
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      565.00 ns →      489.00 ns  (-13.45%) |       1   →       1              |      565.00 ns →      489.00 ns  (-13.45%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.23 ms →        9.23 ms   (-0.01%) |       1   →       1              |        9.23 ms →        9.23 ms   (-0.01%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      121.71 ms →      121.39 ms   (-0.26%) |       1   →       1              |      121.71 ms →      121.39 ms   (-0.26%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      104.85 ms →      103.97 ms   (-0.84%) |       2   →       2              |      209.70 ms →      207.95 ms   (-0.84%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       40.36 ms →       40.48 ms   (+0.29%) |       2   →       2              |       80.72 ms →       80.96 ms   (+0.29%) | 
  │ │ │ └ sddk::wf_inner                                                |       39.83 ms →       39.94 ms   (+0.29%) |       2   →       2              |       79.65 ms →       79.88 ms   (+0.29%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       29.50 ns →       58.00 ns  (+96.61%) |       2   →       2              |       59.00 ns →      116.00 ns  (+96.61%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       39.35 ms →       39.46 ms   (+0.29%) |       2   →       2              |       78.70 ms →       78.93 ms   (+0.29%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       13.00 ns →       22.50 ns  (+73.08%) |       2   →       2              |       26.00 ns →       45.00 ns  (+73.08%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       56.49 ms →       57.31 ms   (+1.45%) |       1   →       1              |       56.49 ms →       57.31 ms   (+1.45%) | 
  │ │ └ sddk::wf_trans                                                  |       30.76 ms →       30.88 ms   (+0.41%) |       1   →       1              |       30.76 ms →       30.88 ms   (+0.41%) | 
  │ │   └ sddk::wf_trans|pw                                             |       30.75 ms →       30.88 ms   (+0.41%) |       1   →       1              |       30.75 ms →       30.88 ms   (+0.41%) | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      394.00 ns →      460.00 ns  (+16.75%) |       1   →       1              |      394.00 ns →      460.00 ns  (+16.75%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      119.60 s  →      118.73 s    (-0.73%) |       1   →       1              |      119.60 s  →      118.73 s    (-0.73%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.73 ms →        6.30 ms   (+9.93%) |      19   →      19              |      108.85 ms →      119.65 ms   (+9.93%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.59 s  →        4.55 s    (-0.70%) |      26   →      26              |      119.23 s  →      118.40 s    (-0.70%) | 
+ │ │ ├ sirius::Hamiltonian0                                            |        5.14 ms →        4.44 ms  (-13.71%) |      26   →      26              |      133.65 ms →      115.33 ms  (-13.71%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        4.78 ms →        4.07 ms  (-14.84%) |      26   →      26              |      124.21 ms →      105.78 ms  (-14.84%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      958.70 μs →      971.60 μs   (+1.34%) |      26   →      26              |       24.93 ms →       25.26 ms   (+1.34%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.93 ms →        2.20 ms  (-24.85%) |      26   →      26              |       76.11 ms →       57.19 ms  (-24.85%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       63.91 μs →       64.04 μs   (+0.21%) |      52   →      52              |        3.32 ms →        3.33 ms   (+0.21%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       86.61 μs →       88.65 μs   (+2.35%) |      26   →      26              |        2.25 ms →        2.30 ms   (+2.35%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       77.22 μs →       78.76 μs   (+1.99%) |      26   →      26              |        2.01 ms →        2.05 ms   (+1.99%) | 
  │ │ ├ sirius::Band::solve                                             |        2.60 s  →        2.60 s    (-0.06%) |      26   →      26              |       67.65 s  →       67.60 s    (-0.06%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      153.15 μs →      164.83 μs   (+7.62%) |      26   →      26              |        3.98 ms →        4.29 ms   (+7.62%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      145.79 μs →      157.11 μs   (+7.77%) |      26   →      26              |        3.79 ms →        4.08 ms   (+7.77%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.60 μs →        5.96 μs   (+6.43%) |      26   →      26              |      145.72 μs →      155.09 μs   (+6.43%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.48 s  →        2.48 s    (+0.19%) |      26   →      26              |       64.41 s  →       64.53 s    (+0.19%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       94.98 ms →       95.49 ms   (+0.53%) |      26   →      26              |        2.47 s  →        2.48 s    (+0.53%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.63 ms →        7.68 ms   (+0.59%) |     156   →     156              |        1.19 s  →        1.20 s    (+0.59%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        5.96 ms →        5.91 ms   (-0.87%) |      26   →      26              |      154.90 ms →      153.55 ms   (-0.87%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      348.16 μs →      350.16 μs   (+0.57%) |      26   →      26              |        9.05 ms →        9.10 ms   (+0.57%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.32 ms →        2.30 ms   (-0.85%) |      52   →      52              |      120.51 ms →      119.49 ms   (-0.85%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.34 s  →        2.34 s    (+0.18%) |      26   →      26              |       60.86 s  →       60.96 s    (+0.18%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      137.57 ms →      137.77 ms   (+0.14%) |     262   →     262              |       36.04 s  →       36.10 s    (+0.14%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       55.67 ms →       55.78 ms   (+0.20%) |     262   →     262              |       14.59 s  →       14.61 s    (+0.20%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.98 μs →        2.19 μs  (+10.28%) |     262   →     262              |      519.61 μs →      573.04 μs  (+10.28%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.66 μs →        1.85 μs  (+11.66%) |     262   →     262              |      434.87 μs →      485.56 μs  (+11.66%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      430.26 ns →      448.25 ns   (+4.18%) |     262   →     262              |      112.73 μs →      117.44 μs   (+4.18%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      464.68 ns →      518.71 ns  (+11.63%) |     262   →     262              |      121.75 μs →      135.90 μs  (+11.63%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.46 ms →        7.46 ms   (+0.00%) |     262   →     262              |        1.95 s  →        1.95 s    (+0.00%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       25.30 ms →       25.37 ms   (+0.27%) |     262   →     262              |        6.63 s  →        6.65 s    (+0.27%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       24.56 ms →       24.57 ms   (+0.04%) |     524   →     524              |       12.87 s  →       12.88 s    (+0.04%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       35.94 ms →       35.95 ms   (+0.04%) |     262   →     262              |        9.42 s  →        9.42 s    (+0.04%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        6.23 ms →        6.23 ms   (-0.01%) |     498   →     498              |        3.10 s  →        3.10 s    (-0.01%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       66.90 ns →       77.51 ns  (+15.85%) |     498   →     498              |       33.32 μs →       38.60 μs  (+15.85%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        5.12 ms →        5.12 ms   (-0.01%) |     498   →     498              |        2.55 s  →        2.55 s    (-0.01%) | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       32.15 ns →       33.86 ns   (+5.34%) |     498   →     498              |       16.01 μs →       16.86 μs   (+5.34%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      662.61 μs →      685.58 μs   (+3.47%) |     262   →     262              |      173.60 ms →      179.62 ms   (+3.47%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       10.32 ms →       10.33 ms   (+0.01%) |     262   →     262              |        2.71 s  →        2.71 s    (+0.01%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |       14.54 ms →       14.52 ms   (-0.08%) |     236   →     236              |        3.43 s  →        3.43 s    (-0.08%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        4.84 ms →        4.84 ms   (-0.08%) |     708   →     708              |        3.43 s  →        3.43 s    (-0.08%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       10.40 ms →       10.39 ms   (-0.13%) |     262   →     262              |        2.73 s  →        2.72 s    (-0.13%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |       10.19 ms →       10.19 ms   (+0.01%) |     262   →     262              |        2.67 s  →        2.67 s    (+0.01%) | 
- │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       44.22 ns →       51.57 ns  (+16.62%) |     262   →     262              |       11.59 μs →       13.51 μs  (+16.62%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        9.07 ms →        9.07 ms   (+0.01%) |     262   →     262              |        2.38 s  →        2.38 s    (+0.01%) | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       50.82 ns →       53.31 ns   (+4.90%) |     262   →     262              |       13.31 μs →       13.97 μs   (+4.90%) | 
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       18.27 ms →       18.46 ms   (+1.05%) |     262   →     262              |        4.79 s  →        4.84 s    (+1.05%) | 
  │ │ │ │   ├ sirius::residuals                                         |       13.14 ms →       13.15 ms   (+0.09%) |     252   →     252              |        3.31 s  →        3.31 s    (+0.09%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       11.71 ms →       11.72 ms   (+0.02%) |     242   →     242              |        2.83 s  →        2.84 s    (+0.02%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        5.85 ms →        5.86 ms   (+0.01%) |     484   →     484              |        2.83 s  →        2.83 s    (+0.01%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.72 ms →        1.73 ms   (+0.59%) |     242   →     242              |      415.54 ms →      417.99 ms   (+0.59%) | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       53.74 ms →       53.75 ms   (+0.02%) |      85   →      85              |        4.57 s  →        4.57 s    (+0.02%) | 
  │ │ │ │     └ sddk::wf_trans                                          |       31.46 ms →       31.46 ms   (+0.01%) |     144   →     144              |        4.53 s  →        4.53 s    (+0.01%) | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |       22.31 ms →       22.32 ms   (+0.01%) |     203   →     203              |        4.53 s  →        4.53 s    (+0.01%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      441.58 ns →      502.62 ns  (+13.82%) |      26   →      26              |       11.48 μs →       13.07 μs  (+13.82%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       28.66 μs →       29.62 μs   (+3.33%) |      26   →      26              |      745.24 μs →      770.08 μs   (+3.33%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      598.43 μs →      610.71 μs   (+2.05%) |      26   →      26              |       15.56 ms →       15.88 ms   (+2.05%) | 
  │ │ ├ sirius::Density::generate                                       |      777.80 ms →      766.62 ms   (-1.44%) |      26   →      26              |       20.22 s  →       19.93 s    (-1.44%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      402.05 ms →      401.44 ms   (-0.15%) |      26   →      26              |       10.45 s  →       10.44 s    (-0.15%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.64 μs →        3.64 μs   (-0.05%) |      26   →      26              |       94.71 μs →       94.67 μs   (-0.05%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.34 μs →        3.31 μs   (-1.01%) |      26   →      26              |       86.94 μs →       86.06 μs   (-1.01%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |      100.59 ms →      100.57 ms   (-0.02%) |      26   →      26              |        2.62 s  →        2.61 s    (-0.02%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       11.20 μs →       10.78 μs   (-3.76%) |      26   →      26              |      291.30 μs →      280.33 μs   (-3.76%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.13 ms →        7.13 ms   (+0.02%) |      26   →      26              |      185.38 ms →      185.41 ms   (+0.02%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       91.54 ms →       91.49 ms   (-0.06%) |      26   →      26              |        2.38 s  →        2.38 s    (-0.06%) | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      606.23 ns →      606.23 ns            |      26   →      26              |       15.76 μs →       15.76 μs            | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      163.43 ms →      163.58 ms   (+0.10%) |      26   →      26              |        4.25 s  →        4.25 s    (+0.10%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.65 ms →        1.65 ms   (+0.30%) |      26   →      26              |       42.77 ms →       42.90 ms   (+0.30%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.32 ms →       88.29 ms   (-0.03%) |      26   →      26              |        2.30 s  →        2.30 s    (-0.03%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.09 ms →       88.07 ms   (-0.03%) |      26   →      26              |        2.29 s  →        2.29 s    (-0.03%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      275.13 ms →      271.36 ms   (-1.37%) |      26   →      26              |        7.15 s  →        7.06 s    (-1.37%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      275.13 ms →      271.36 ms   (-1.37%) |      26   →      26              |        7.15 s  →        7.06 s    (-1.37%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.34 ms →       24.47 ms   (+0.53%) |      26   →      26              |      632.93 ms →      636.28 ms   (+0.53%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      226.74 ms →      222.49 ms   (-1.87%) |      26   →      26              |        5.90 s  →        5.78 s    (-1.87%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       22.86 ms →       23.20 ms   (+1.47%) |      26   →      26              |      594.31 ms →      603.07 ms   (+1.47%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       81.11 ms →       81.15 ms   (+0.04%) |      26   →      26              |        2.11 s  →        2.11 s    (+0.04%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |       15.91 ms →        8.88 ms  (-44.20%) |      26   →      26              |      413.75 ms →      230.88 ms  (-44.20%) | 
  │ │ ├ sirius::Density::mix                                            |      220.23 ms →      204.72 ms   (-7.05%) |      26   →      26              |        5.73 s  →        5.32 s    (-7.05%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      930.75 μs →      965.00 μs   (+3.68%) |      26   →      26              |       24.20 ms →       25.09 ms   (+3.68%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.82 ms →       10.48 ms   (-3.11%) |     334   →     334              |        3.61 s  →        3.50 s    (-3.11%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.38 ms →       10.09 ms   (-2.83%) |     334   →     334              |        3.47 s  →        3.37 s    (-2.83%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.38 ms →       10.08 ms   (-2.83%) |     334   →     334              |        3.47 s  →        3.37 s    (-2.83%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        6.01 ms →        5.95 ms   (-0.91%) |      26   →      26              |      156.16 ms →      154.73 ms   (-0.91%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.15 ms →        5.14 ms   (-0.19%) |      26   →      26              |      133.98 ms →      133.72 ms   (-0.19%) | 
  │ │ ├ sirius::Potential::generate                                     |      581.00 ms →      579.18 ms   (-0.31%) |      26   →      26              |       15.11 s  →       15.06 s    (-0.31%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      139.02 ms →      138.54 ms   (-0.34%) |      26   →      26              |        3.61 s  →        3.60 s    (-0.34%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       21.27 ms →       16.94 ms  (-20.37%) |      26   →      26              |      553.07 ms →      440.39 ms  (-20.37%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.78 ms →       11.26 ms   (+4.43%) |      26   →      26              |      280.24 ms →      292.66 ms   (+4.43%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.30 ms →        9.87 ms   (-4.17%) |      26   →      26              |      267.71 ms →      256.54 ms   (-4.17%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.30 ms →        9.87 ms   (-4.17%) |      26   →      26              |      267.70 ms →      256.52 ms   (-4.17%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      547.22 μs →      548.56 μs   (+0.25%) |      52   →      52              |       28.46 ms →       28.53 ms   (+0.25%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       49.36 ms →       48.63 ms   (-1.48%) |      26   →      26              |        1.28 s  →        1.26 s    (-1.48%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       47.01 ms →       46.30 ms   (-1.50%) |      26   →      26              |        1.22 s  →        1.20 s    (-1.50%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.01 ms →        3.03 ms   (+0.62%) |      52   →      52              |      156.42 ms →      157.38 ms   (+0.62%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.40 ms →        5.19 ms   (-3.85%) |      26   →      26              |      140.38 ms →      134.98 ms   (-3.85%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.48 ms →        6.51 ms   (+0.36%) |      26   →      26              |      168.59 ms →      169.20 ms   (+0.36%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.89 ms →       90.87 ms   (-0.02%) |      26   →      26              |        2.36 s  →        2.36 s    (-0.02%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      292.89 ms →      292.26 ms   (-0.21%) |      26   →      26              |        7.62 s  →        7.60 s    (-0.21%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      279.52 ms →      276.92 ms   (-0.93%) |      26   →      26              |        7.27 s  →        7.20 s    (-0.93%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      279.52 ms →      276.91 ms   (-0.93%) |      26   →      26              |        7.27 s  →        7.20 s    (-0.93%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.21 ms →       27.22 ms   (+0.01%) |      26   →      26              |      707.58 ms →      707.65 ms   (+0.01%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      224.69 ms →      222.09 ms   (-1.16%) |      26   →      26              |        5.84 s  →        5.77 s    (-1.16%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.81 ms →       23.78 ms   (-0.14%) |      26   →      26              |      619.13 ms →      618.26 ms   (-0.14%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.56 ms →        5.54 ms   (-0.34%) |      26   →      26              |      144.55 ms →      144.06 ms   (-0.34%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.31 ms →       10.67 ms   (+3.51%) |     182   →     182              |        1.88 s  →        1.94 s    (+3.51%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.83 ms →       10.21 ms   (+3.86%) |     182   →     182              |        1.79 s  →        1.86 s    (+3.86%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.83 ms →       10.21 ms   (+3.86%) |     182   →     182              |        1.79 s  →        1.86 s    (+3.86%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.61 ms →       10.22 ms   (-3.63%) |      78   →      78              |      827.48 ms →      797.47 ms   (-3.63%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.23 ms →        9.76 ms   (-4.59%) |      78   →      78              |      797.56 ms →      760.99 ms   (-4.59%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |       10.04 ms →       10.03 ms   (-0.12%) |      26   →      26              |      261.01 ms →      260.70 ms   (-0.12%) | 
  │ │ └ sirius::Density::get_magnetisation                              |      111.15 μs →      111.98 μs   (+0.75%) |      26   →      26              |        2.89 ms →        2.91 ms   (+0.75%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |      106.15 μs →      106.72 μs   (+0.54%) |      26   →      26              |        2.76 ms →        2.77 ms   (+0.54%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.06 ms →        5.15 ms   (+1.93%) |       2   →       2              |       10.11 ms →       10.31 ms   (+1.93%) | 
  │ ├ sirius::Periodic_function|inner                                   |        9.71 ms →       10.59 ms   (+9.08%) |       6   →       6              |       58.27 ms →       63.56 ms   (+9.08%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        9.66 ms →       10.06 ms   (+4.19%) |       6   →       6              |       57.96 ms →       60.39 ms   (+4.19%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        9.66 ms →       10.06 ms   (+4.20%) |       6   →       6              |       57.96 ms →       60.39 ms   (+4.20%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.06 ms →       10.02 ms   (-0.39%) |       3   →       3              |       30.18 ms →       30.07 ms   (-0.39%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.04 ms →        9.61 ms   (-4.26%) |       3   →       3              |       30.12 ms →       28.84 ms   (-4.26%) | 
  ├ sirius::Periodic_function|inner                                     |       10.03 ms →       10.49 ms   (+4.61%) |       2   →       2              |       20.05 ms →       20.98 ms   (+4.61%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.02 ms →       10.45 ms   (+4.28%) |       2   →       2              |       20.04 ms →       20.89 ms   (+4.28%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.02 ms →       10.45 ms   (+4.28%) |       2   →       2              |       20.04 ms →       20.89 ms   (+4.28%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.41 ms →       10.88 ms   (+4.48%) |       1   →       1              |       10.41 ms →       10.88 ms   (+4.48%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.41 ms →       10.00 ms   (-3.86%) |       1   →       1              |       10.41 ms →       10.00 ms   (-3.86%) | 
- └ sirius::finalize                                                    |      177.59 ms →      210.00 ms  (+18.25%) |       1   →       1              |      177.59 ms →      210.00 ms  (+18.25%) | 
  ====================================================================================================================================================================================================
```
