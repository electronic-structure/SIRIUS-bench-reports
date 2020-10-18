# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      125.11 s  →      128.88 s    (+3.01%) |       1   →       1              |      125.11 s  →      128.88 s    (+3.01%) | 
  ├ sirius::initialize                                                  |        2.71 s  →        2.71 s    (+0.20%) |       1   →       1              |        2.71 s  →        2.71 s    (+0.20%) | 
  ├ sirius::Simulation_context::initialize                              |        2.95 s  →        2.99 s    (+1.27%) |       1   →       1              |        2.95 s  →        2.99 s    (+1.27%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       74.44 ms →       46.80 ms  (-37.13%) |       1   →       1              |       74.44 ms →       46.80 ms  (-37.13%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      150.92 ms →      169.18 ms  (+12.10%) |       1   →       1              |      150.92 ms →      169.18 ms  (+12.10%) | 
- │ │ ├ sirius::Atom_type::init                                         |       63.22 ms →       72.65 ms  (+14.91%) |       2   →       2              |      126.45 ms →      145.30 ms  (+14.91%) | 
  │ │ └ sirius::Unit_cell::update                                       |       24.40 ms →       23.77 ms   (-2.58%) |       1   →       1              |       24.40 ms →       23.77 ms   (-2.58%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.30 ms →        6.33 ms   (+0.40%) |       1   →       1              |        6.30 ms →        6.33 ms   (+0.40%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       18.06 ms →       17.40 ms   (-3.65%) |       1   →       1              |       18.06 ms →       17.40 ms   (-3.65%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       18.03 ms →       17.38 ms   (-3.65%) |       1   →       1              |       18.03 ms →       17.38 ms   (-3.65%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.13 ms →        4.15 ms   (+0.52%) |       1   →       1              |        4.13 ms →        4.15 ms   (+0.52%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.34 ms →        2.33 ms   (-0.47%) |       1   →       1              |        2.34 ms →        2.33 ms   (-0.47%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      105.52 μs →      102.60 μs   (-2.77%) |       1   →       1              |      105.52 μs →      102.60 μs   (-2.77%) | 
  │ └ sirius::Simulation_context::update                                |        2.68 s  →        2.73 s    (+1.69%) |       1   →       1              |        2.68 s  →        2.73 s    (+1.69%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.66 ms →       10.88 ms   (+2.07%) |       1   →       1              |       10.66 ms →       10.88 ms   (+2.07%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.24 ms →        4.45 ms   (+5.01%) |       1   →       1              |        4.24 ms →        4.45 ms   (+5.01%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.39 ms →        6.39 ms   (+0.10%) |       1   →       1              |        6.39 ms →        6.39 ms   (+0.10%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.37 ms →        6.37 ms   (+0.08%) |       1   →       1              |        6.37 ms →        6.37 ms   (+0.08%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.88 ms →        3.87 ms   (-0.46%) |       1   →       1              |        3.88 ms →        3.87 ms   (-0.46%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.31 ms →        2.34 ms   (+1.11%) |       1   →       1              |        2.31 ms →        2.34 ms   (+1.11%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      103.44 μs →      100.05 μs   (-3.28%) |       1   →       1              |      103.44 μs →      100.05 μs   (-3.28%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       62.96 ms →       62.63 ms   (-0.53%) |       2   →       2              |      125.92 ms →      125.25 ms   (-0.53%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.14 ms →        5.14 ms   (+0.06%) |       2   →       2              |       10.28 ms →       10.28 ms   (+0.06%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.49 ms →        4.49 ms   (-0.07%) |       1   →       1              |        4.49 ms →        4.49 ms   (-0.07%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.76 ms →       21.74 ms   (-0.10%) |       2   →       2              |       43.52 ms →       43.48 ms   (-0.10%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.92 ms →       14.81 ms   (-0.76%) |       2   →       2              |       29.84 ms →       29.62 ms   (-0.76%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.70 ms →       19.82 ms   (+0.64%) |       4   →       4              |       78.79 ms →       79.29 ms   (+0.64%) | 
  │   ├ sddk::Gvec::init                                                |      174.70 ms →      171.85 ms   (-1.63%) |       2   →       2              |      349.41 ms →      343.70 ms   (-1.63%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      131.91 ms →      129.63 ms   (-1.73%) |       2   →       2              |      263.82 ms →      259.27 ms   (-1.73%) | 
  │   ├ sddk::Gvec_shells                                               |      176.93 ms →      184.39 ms   (+4.22%) |       1   →       1              |      176.93 ms →      184.39 ms   (+4.22%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.31 ms →        1.34 ms   (+2.00%) |       1   →       1              |        1.31 ms →        1.34 ms   (+2.00%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      293.93 ms →      295.48 ms   (+0.53%) |       2   →       2              |      587.85 ms →      590.97 ms   (+0.53%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       35.51 ms →       35.48 ms   (-0.09%) |       1   →       1              |       35.51 ms →       35.48 ms   (-0.09%) | 
  │ ├ sirius::K_point::K_point                                          |        2.20 μs →        2.18 μs   (-0.95%) |       4   →       4              |        8.82 μs →        8.73 μs   (-0.95%) | 
  │ └ sirius::K_point_set::initialize                                   |       35.41 ms →       35.37 ms   (-0.11%) |       1   →       1              |       35.41 ms →       35.37 ms   (-0.11%) | 
  │   └ sirius::K_point::initialize                                     |       35.31 ms →       35.28 ms   (-0.09%) |       1   →       1              |       35.31 ms →       35.28 ms   (-0.09%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       18.02 ms →       18.03 ms   (+0.07%) |       1   →       1              |       18.02 ms →       18.03 ms   (+0.07%) | 
  │     │ └ sddk::Gvec::init                                            |        8.07 ms →        8.12 ms   (+0.64%) |       1   →       1              |        8.07 ms →        8.12 ms   (+0.64%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        8.75 μs →        9.29 μs   (+6.13%) |       1   →       1              |        8.75 μs →        9.29 μs   (+6.13%) | 
  │     └ sirius::K_point::update                                       |       12.40 ms →       12.45 ms   (+0.36%) |       1   →       1              |       12.40 ms →       12.45 ms   (+0.36%) | 
  │       └ sirius::Beta_projectors                                     |        6.18 ms →        6.23 ms   (+0.82%) |       1   →       1              |        6.18 ms →        6.23 ms   (+0.82%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.58 ms →        3.63 ms   (+1.57%) |       1   →       1              |        3.58 ms →        3.63 ms   (+1.57%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.17 ms →        5.50 ms   (+6.33%) |       2   →       2              |       10.34 ms →       11.00 ms   (+6.33%) | 
  ├ sirius::Potential                                                   |      159.91 ms →      157.97 ms   (-1.21%) |       1   →       1              |      159.91 ms →      157.97 ms   (-1.21%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.83 ms →        5.77 ms   (-1.00%) |       6   →       6              |       34.96 ms →       34.61 ms   (-1.00%) | 
  │ └ sirius::Potential::update                                         |      124.18 ms →      122.66 ms   (-1.22%) |       1   →       1              |      124.18 ms →      122.66 ms   (-1.22%) | 
  │   └ sirius::Potential::generate_local_potential                     |      123.41 ms →      121.96 ms   (-1.17%) |       1   →       1              |      123.41 ms →      121.96 ms   (-1.17%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      110.05 ms →      114.55 ms   (+4.09%) |       1   →       1              |      110.05 ms →      114.55 ms   (+4.09%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       12.45 ms →        6.52 ms  (-47.65%) |       1   →       1              |       12.45 ms →        6.52 ms  (-47.65%) | 
  ├ sirius::Density                                                     |      135.72 ms →      135.41 ms   (-0.23%) |       1   →       1              |      135.72 ms →      135.41 ms   (-0.23%) | 
- │ ├ sirius::Smooth_periodic_function                                  |        5.12 ms →        5.66 ms  (+10.38%) |       2   →       2              |       10.25 ms →       11.31 ms  (+10.38%) | 
  │ └ sirius::Density::update                                           |      125.20 ms →      123.80 ms   (-1.11%) |       1   →       1              |      125.20 ms →      123.80 ms   (-1.11%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      124.77 ms →      123.36 ms   (-1.14%) |       1   →       1              |      124.77 ms →      123.36 ms   (-1.14%) | 
- │     ├ sirius::rho_core_ri_pseudo|values                             |      103.67 μs →      115.47 μs  (+11.38%) |       1   →       1              |      103.67 μs →      115.47 μs  (+11.38%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      111.70 ms →      117.61 ms   (+5.29%) |       1   →       1              |      111.70 ms →      117.61 ms   (+5.29%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       12.51 ms →        5.18 ms  (-58.60%) |       1   →       1              |       12.51 ms →        5.18 ms  (-58.60%) | 
  ├ sirius::Density::initial_density                                    |      175.20 ms →      176.15 ms   (+0.55%) |       1   →       1              |      175.20 ms →      176.15 ms   (+0.55%) | 
- │ ├ sirius::Simulation_context::make_periodic_function                |      110.17 ms →      121.67 ms  (+10.44%) |       1   →       1              |      110.17 ms →      121.67 ms  (+10.44%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |       11.21 ms →        5.98 ms  (-46.68%) |       2   →       2              |       22.42 ms →       11.95 ms  (-46.68%) | 
  │ └ sirius::Periodic_function::integrate                              |       10.14 ms →       10.25 ms   (+1.00%) |       1   →       1              |       10.14 ms →       10.25 ms   (+1.00%) | 
  ├ sirius::Potential::generate                                         |      592.47 ms →      595.69 ms   (+0.54%) |       1   →       1              |      592.47 ms →      595.69 ms   (+0.54%) | 
  │ ├ sirius::Potential::poisson                                        |      137.87 ms →      137.05 ms   (-0.60%) |       1   →       1              |      137.87 ms →      137.05 ms   (-0.60%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       17.59 ms →        6.22 ms  (-64.64%) |       1   →       1              |       17.59 ms →        6.22 ms  (-64.64%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.59 ms →        9.91 ms   (-6.49%) |       1   →       1              |       10.59 ms →        9.91 ms   (-6.49%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |       10.57 ms →        9.89 ms   (-6.49%) |       1   →       1              |       10.57 ms →        9.89 ms   (-6.49%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |       10.56 ms →        9.88 ms   (-6.40%) |       1   →       1              |       10.56 ms →        9.88 ms   (-6.40%) | 
  │ ├ sirius::Periodic_function::add                                    |      549.37 μs →      551.90 μs   (+0.46%) |       2   →       2              |        1.10 ms →        1.10 ms   (+0.46%) | 
  │ ├ sirius::Potential::xc                                             |       53.86 ms →       57.61 ms   (+6.97%) |       1   →       1              |       53.86 ms →       57.61 ms   (+6.97%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.50 ms →       55.32 ms   (+7.41%) |       1   →       1              |       51.50 ms →       55.32 ms   (+7.41%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.70 ms →        6.20 ms   (+8.87%) |       2   →       2              |       11.39 ms →       12.40 ms   (+8.87%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.45 ms →        5.24 ms   (-3.87%) |       1   →       1              |        5.45 ms →        5.24 ms   (-3.87%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.87 ms →        5.76 ms   (-1.76%) |       1   →       1              |        5.87 ms →        5.76 ms   (-1.76%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.77 ms →       93.50 ms   (+0.78%) |       1   →       1              |       92.77 ms →       93.50 ms   (+0.78%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      299.62 ms →      299.31 ms   (-0.10%) |       1   →       1              |      299.62 ms →      299.31 ms   (-0.10%) | 
  ├ sirius::Hamiltonian0                                                |        8.36 ms →        8.41 ms   (+0.55%) |       1   →       1              |        8.36 ms →        8.41 ms   (+0.55%) | 
  │ ├ sirius::Local_operator                                            |        8.02 ms →        8.06 ms   (+0.60%) |       1   →       1              |        8.02 ms →        8.06 ms   (+0.60%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.71 ms →        4.74 ms   (+0.84%) |       1   →       1              |        4.71 ms →        4.74 ms   (+0.84%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.38 ms →        2.40 ms   (+0.77%) |       1   →       1              |        2.38 ms →        2.40 ms   (+0.77%) | 
  │ ├ sirius::Non_local_operator                                        |       62.46 μs →       63.05 μs   (+0.95%) |       2   →       2              |      124.91 μs →      126.10 μs   (+0.95%) | 
  │ ├ sirius::D_operator::initialize                                    |       91.40 μs →       93.70 μs   (+2.52%) |       1   →       1              |       91.40 μs →       93.70 μs   (+2.52%) | 
  │ └ sirius::Q_operator::initialize                                    |       77.09 μs →       74.26 μs   (-3.68%) |       1   →       1              |       77.09 μs →       74.26 μs   (-3.68%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.87 s  →        1.87 s    (+0.07%) |       1   →       1              |        1.87 s  →        1.87 s    (+0.07%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.70 ms →       18.70 ms   (+0.04%) |       1   →       1              |       18.70 ms →       18.70 ms   (+0.04%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      190.54 μs →      182.59 μs   (-4.17%) |       1   →       1              |      190.54 μs →      182.59 μs   (-4.17%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       18.50 ms →       18.52 ms   (+0.08%) |       1   →       1              |       18.50 ms →       18.52 ms   (+0.08%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.85 s  →        1.85 s    (+0.07%) |       1   →       1              |        1.85 s  →        1.85 s    (+0.07%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      128.20 ms →      130.80 ms   (+2.02%) |       4   →       4              |      512.82 ms →      523.19 ms   (+2.02%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       52.35 ms →       52.48 ms   (+0.26%) |       1   →       1              |       52.35 ms →       52.48 ms   (+0.26%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.08 ms →       21.67 ms   (+2.80%) |       1   →       1              |       21.08 ms →       21.67 ms   (+2.80%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      634.94 ms →      639.66 ms   (+0.74%) |       1   →       1              |      634.94 ms →      639.66 ms   (+0.74%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      298.05 ms →      297.45 ms   (-0.20%) |       1   →       1              |      298.05 ms →      297.45 ms   (-0.20%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.56 μs →        2.81 μs  (-21.23%) |       1   →       1              |        3.56 μs →        2.81 μs  (-21.23%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.43 μs →        1.91 μs  (-21.23%) |       1   →       1              |        2.43 μs →        1.91 μs  (-21.23%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      398.00 ns →      428.00 ns   (+7.54%) |       1   →       1              |      398.00 ns →      428.00 ns   (+7.54%) | 
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      622.00 ns →      460.00 ns  (-26.05%) |       1   →       1              |      622.00 ns →      460.00 ns  (-26.05%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.24 ms →        9.21 ms   (-0.33%) |       1   →       1              |        9.24 ms →        9.21 ms   (-0.33%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      120.66 ms →      122.33 ms   (+1.39%) |       1   →       1              |      120.66 ms →      122.33 ms   (+1.39%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      103.47 ms →      105.31 ms   (+1.78%) |       2   →       2              |      206.95 ms →      210.63 ms   (+1.78%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       40.64 ms →       40.29 ms   (-0.84%) |       2   →       2              |       81.27 ms →       80.59 ms   (-0.84%) | 
  │ │ │ └ sddk::wf_inner                                                |       40.07 ms →       39.71 ms   (-0.90%) |       2   →       2              |       80.15 ms →       79.43 ms   (-0.90%) | 
  │ │ │   ├ sddk::wf_inner|scale                                        |       26.00 ns →       28.50 ns   (+9.62%) |       2   →       2              |       52.00 ns →       57.00 ns   (+9.62%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       39.60 ms →       39.24 ms   (-0.91%) |       2   →       2              |       79.20 ms →       78.47 ms   (-0.91%) | 
+ │ │ │   └ sddk::wf_inner|scale_back                                   |       23.00 ns →       20.00 ns  (-13.04%) |       2   →       2              |       46.00 ns →       40.00 ns  (-13.04%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       56.34 ms →       57.46 ms   (+1.99%) |       1   →       1              |       56.34 ms →       57.46 ms   (+1.99%) | 
  │ │ └ sddk::wf_trans                                                  |       30.73 ms →       31.22 ms   (+1.59%) |       1   →       1              |       30.73 ms →       31.22 ms   (+1.59%) | 
  │ │   └ sddk::wf_trans|pw                                             |       30.73 ms →       31.22 ms   (+1.59%) |       1   →       1              |       30.73 ms →       31.22 ms   (+1.59%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      590.00 ns →      507.00 ns  (-14.07%) |       1   →       1              |      590.00 ns →      507.00 ns  (-14.07%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      115.46 s  →      118.80 s    (+2.90%) |       1   →       1              |      115.46 s  →      118.80 s    (+2.90%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.87 ms →        5.77 ms   (-1.68%) |      19   →      19              |      111.47 ms →      109.60 ms   (-1.68%) | 
! │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        5.00 s  →        4.56 s    (-8.98%) |      23   →      26    (+13.04%) |      115.11 s  →      118.45 s    (+2.90%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        4.48 ms →        4.61 ms   (+2.89%) |      23   →      26    (+13.04%) |      103.01 ms →      119.80 ms  (+16.31%) | 
- │ │ │ ├ sirius::Local_operator                                        |        4.11 ms →        4.25 ms   (+3.48%) |      23   →      26    (+13.04%) |       94.51 ms →      110.55 ms  (+16.98%) | 
! │ │ │ │ ├ sirius::Smooth_periodic_function                            |      962.57 μs →      934.81 μs   (-2.88%) |      23   →      26    (+13.04%) |       22.14 ms →       24.31 ms   (+9.78%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.25 ms →        2.25 ms   (+0.05%) |      23   →      26    (+13.04%) |       51.82 ms →       58.61 ms  (+13.10%) | 
- │ │ │ ├ sirius::Non_local_operator                                    |       64.71 μs →       64.20 μs   (-0.78%) |      46   →      52    (+13.04%) |        2.98 ms →        3.34 ms  (+12.16%) | 
! │ │ │ ├ sirius::D_operator::initialize                                |       88.52 μs →       85.96 μs   (-2.90%) |      23   →      26    (+13.04%) |        2.04 ms →        2.23 ms   (+9.77%) | 
! │ │ │ └ sirius::Q_operator::initialize                                |       79.79 μs →       75.82 μs   (-4.97%) |      23   →      26    (+13.04%) |        1.84 ms →        1.97 ms   (+7.42%) | 
+ │ │ ├ sirius::Band::solve                                             |        3.03 s  →        2.60 s   (-14.32%) |      23   →      26    (+13.04%) |       69.67 s  →       67.47 s    (-3.15%) | 
! │ │ │ ├ sirius::Hamiltonian_k                                         |      155.16 μs →      150.26 μs   (-3.16%) |      23   →      26    (+13.04%) |        3.57 ms →        3.91 ms   (+9.47%) | 
! │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      148.31 μs →      143.59 μs   (-3.18%) |      23   →      26    (+13.04%) |        3.41 ms →        3.73 ms   (+9.45%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.86 μs →        4.80 μs   (-1.10%) |      23   →      26    (+13.04%) |      111.74 μs →      124.93 μs  (+11.81%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.85 s  →        2.47 s   (-13.16%) |      23   →      26    (+13.04%) |       65.53 s  →       64.33 s    (-1.83%) | 
! │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |      103.70 ms →       95.97 ms   (-7.45%) |      23   →      26    (+13.04%) |        2.39 s  →        2.50 s    (+4.62%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        8.68 ms →        7.81 ms  (-10.02%) |     138   →     156    (+13.04%) |        1.20 s  →        1.22 s    (+1.71%) | 
- │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        5.95 ms →        5.97 ms   (+0.27%) |      23   →      26    (+13.04%) |      136.87 ms →      155.14 ms  (+13.35%) | 
- │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      354.34 μs →      357.76 μs   (+0.97%) |      23   →      26    (+13.04%) |        8.15 ms →        9.30 ms  (+14.14%) | 
- │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.31 ms →        2.30 ms   (-0.78%) |      46   →      52    (+13.04%) |      106.46 ms →      119.41 ms  (+12.17%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.70 s  →        2.34 s   (-13.58%) |      23   →      26    (+13.04%) |       62.18 s  →       60.75 s    (-2.31%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      125.24 ms →      137.56 ms   (+9.84%) |     268   →     262     (-2.24%) |       33.57 s  →       36.04 s    (+7.38%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       50.05 ms →       55.34 ms  (+10.58%) |     268   →     262     (-2.24%) |       13.41 s  →       14.50 s    (+8.11%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.98 μs →        1.93 μs   (-2.83%) |     268   →     262     (-2.24%) |      531.86 μs →      505.26 μs   (-5.00%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.71 μs →        1.65 μs   (-3.16%) |     268   →     262     (-2.24%) |      457.30 μs →      432.94 μs   (-5.33%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      384.77 ns →      358.09 ns   (-6.93%) |     268   →     262     (-2.24%) |      103.12 μs →       93.82 μs   (-9.02%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      437.93 ns →      421.83 ns   (-3.68%) |     268   →     262     (-2.24%) |      117.37 μs →      110.52 μs   (-5.83%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.44 ms →        7.45 ms   (+0.14%) |     268   →     262     (-2.24%) |        1.99 s  →        1.95 s    (-2.10%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       22.54 ms →       25.52 ms  (+13.21%) |     268   →     262     (-2.24%) |        6.04 s  →        6.69 s   (+10.67%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       22.60 ms →       24.62 ms   (+8.93%) |     536   →     524     (-2.24%) |       12.11 s  →       12.90 s    (+6.49%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       34.40 ms →       35.99 ms   (+4.63%) |     268   →     262     (-2.24%) |        9.22 s  →        9.43 s    (+2.28%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        5.94 ms →        6.25 ms   (+5.21%) |     513   →     498     (-2.92%) |        3.05 s  →        3.11 s    (+2.13%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       66.20 ns →       73.19 ns  (+10.56%) |     513   →     498     (-2.92%) |       33.96 μs →       36.45 μs   (+7.33%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        4.83 ms →        5.13 ms   (+6.32%) |     513   →     498     (-2.92%) |        2.48 s  →        2.56 s    (+3.21%) | 
+ │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       51.78 ns →       26.59 ns  (-48.65%) |     513   →     498     (-2.92%) |       26.56 μs →       13.24 μs  (-50.15%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      594.59 μs →      674.04 μs  (+13.36%) |     268   →     262     (-2.24%) |      159.35 ms →      176.60 ms  (+10.82%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        9.30 ms →       10.34 ms  (+11.21%) |     268   →     262     (-2.24%) |        2.49 s  →        2.71 s    (+8.72%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |       14.37 ms →       14.54 ms   (+1.20%) |     245   →     236     (-3.67%) |        3.52 s  →        3.43 s    (-2.52%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        4.79 ms →        4.85 ms   (+1.20%) |     735   →     708     (-3.67%) |        3.52 s  →        3.43 s    (-2.52%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       10.31 ms →       10.43 ms   (+1.16%) |     268   →     262     (-2.24%) |        2.76 s  →        2.73 s    (-1.11%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |       10.04 ms →       10.23 ms   (+1.84%) |     268   →     262     (-2.24%) |        2.69 s  →        2.68 s    (-0.44%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       46.20 ns →       26.13 ns  (-43.44%) |     268   →     262     (-2.24%) |       12.38 μs →        6.85 μs  (-44.70%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        8.93 ms →        9.11 ms   (+2.03%) |     268   →     262     (-2.24%) |        2.39 s  →        2.39 s    (-0.26%) | 
+ │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       70.23 ns →       49.39 ns  (-29.68%) |     268   →     262     (-2.24%) |       18.82 μs →       12.94 μs  (-31.25%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       34.45 ms →       17.65 ms  (-48.77%) |     268   →     262     (-2.24%) |        9.23 s  →        4.62 s   (-49.91%) | 
  │ │ │ │   ├ sirius::residuals                                         |       13.50 ms →       13.22 ms   (-2.13%) |     259   →     252     (-2.70%) |        3.50 s  →        3.33 s    (-4.77%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       12.15 ms →       11.75 ms   (-3.29%) |     250   →     242     (-3.20%) |        3.04 s  →        2.84 s    (-6.39%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        6.07 ms →        5.87 ms   (-3.29%) |     500   →     484     (-3.20%) |        3.04 s  →        2.84 s    (-6.39%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.60 ms →        1.72 ms   (+7.60%) |     250   →     242     (-3.20%) |      399.80 ms →      416.41 ms   (+4.16%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       77.93 ms →       53.92 ms  (-30.81%) |      50   →      85    (+70.00%) |        3.90 s  →        4.58 s   (+17.62%) | 
- │ │ │ │     └ sddk::wf_trans                                          |       50.36 ms →       31.57 ms  (-37.31%) |      77   →     144    (+87.01%) |        3.88 s  →        4.55 s   (+17.23%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |       37.29 ms →       22.39 ms  (-39.94%) |     104   →     203    (+95.19%) |        3.88 s  →        4.55 s   (+17.23%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      638.39 ns →      441.42 ns  (-30.85%) |      23   →      26    (+13.04%) |       14.68 μs →       11.48 μs  (-21.83%) | 
+ │ │ │ └ sirius::K_point_set::sync_band_energies                       |       49.08 μs →       29.60 μs  (-39.69%) |      23   →      26    (+13.04%) |        1.13 ms →      769.55 μs  (-31.83%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |      597.05 μs →      610.79 μs   (+2.30%) |      23   →      26    (+13.04%) |       13.73 ms →       15.88 ms  (+15.65%) | 
- │ │ ├ sirius::Density::generate                                       |      773.43 ms →      766.79 ms   (-0.86%) |      23   →      26    (+13.04%) |       17.79 s  →       19.94 s   (+12.07%) | 
- │ │ │ ├ sirius::Density::generate_valence                             |      403.43 ms →      401.04 ms   (-0.59%) |      23   →      26    (+13.04%) |        9.28 s  →       10.43 s   (+12.38%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.56 μs →        8.38 μs   (-2.11%) |      23   →      26    (+13.04%) |      196.95 μs →      217.95 μs  (+10.66%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        8.05 μs →        7.92 μs   (-1.71%) |      23   →      26    (+13.04%) |      185.22 μs →      205.80 μs  (+11.11%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |      100.30 ms →      100.98 ms   (+0.68%) |      23   →      26    (+13.04%) |        2.31 s  →        2.63 s   (+13.81%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.38 μs →        7.53 μs   (+2.11%) |      23   →      26    (+13.04%) |      169.68 μs →      195.86 μs  (+15.43%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.15 ms →        7.12 ms   (-0.45%) |      23   →      26    (+13.04%) |      164.49 ms →      185.11 ms  (+12.54%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       91.21 ms →       91.96 ms   (+0.82%) |      23   →      26    (+13.04%) |        2.10 s  →        2.39 s   (+13.97%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      723.57 ns →      579.50 ns  (-19.91%) |      23   →      26    (+13.04%) |       16.64 μs →       15.07 μs   (-9.46%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      164.29 ms →      162.27 ms   (-1.23%) |      23   →      26    (+13.04%) |        3.78 s  →        4.22 s   (+11.65%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.64 ms   (+0.22%) |      23   →      26    (+13.04%) |       37.65 ms →       42.66 ms  (+13.29%) | 
- │ │ │ │ └ sirius::Density::augment                                    |       88.27 ms →       88.35 ms   (+0.10%) |      23   →      26    (+13.04%) |        2.03 s  →        2.30 s   (+13.15%) | 
- │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.04 ms →       88.11 ms   (+0.08%) |      23   →      26    (+13.04%) |        2.02 s  →        2.29 s   (+13.13%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      276.13 ms →      274.28 ms   (-0.67%) |      23   →      26    (+13.04%) |        6.35 s  →        7.13 s   (+12.29%) | 
- │ │ │ │ └ sirius::symmetrize_function|fpw                             |      276.13 ms →      274.28 ms   (-0.67%) |      23   →      26    (+13.04%) |        6.35 s  →        7.13 s   (+12.29%) | 
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.15 ms →       24.15 ms   (+0.02%) |      23   →      26    (+13.04%) |      555.48 ms →      628.03 ms  (+13.06%) | 
- │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      227.77 ms →      225.11 ms   (-1.17%) |      23   →      26    (+13.04%) |        5.24 s  →        5.85 s   (+11.72%) | 
- │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       23.00 ms →       23.85 ms   (+3.69%) |      23   →      26    (+13.04%) |      529.05 ms →      620.13 ms  (+17.22%) | 
- │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       81.85 ms →       80.52 ms   (-1.62%) |      23   →      26    (+13.04%) |        1.88 s  →        2.09 s   (+11.21%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        8.44 ms →        7.34 ms  (-12.94%) |      23   →      26    (+13.04%) |      194.03 ms →      190.95 ms   (-1.59%) | 
! │ │ ├ sirius::Density::mix                                            |      214.70 ms →      205.90 ms   (-4.10%) |      23   →      26    (+13.04%) |        4.94 s  →        5.35 s    (+8.41%) | 
! │ │ │ ├ sirius::Density::mixer_input                                  |      953.31 μs →      923.94 μs   (-3.08%) |      23   →      26    (+13.04%) |       21.93 ms →       24.02 ms   (+9.56%) | 
! │ │ │ ├ sirius::Periodic_function|inner                               |       10.76 ms →       10.45 ms   (-2.87%) |     289   →     320    (+10.73%) |        3.11 s  →        3.34 s    (+7.55%) | 
! │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.37 ms →       10.01 ms   (-3.49%) |     289   →     320    (+10.73%) |        3.00 s  →        3.20 s    (+6.86%) | 
! │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.37 ms →       10.01 ms   (-3.49%) |     289   →     320    (+10.73%) |        3.00 s  →        3.20 s    (+6.86%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        6.80 ms →        7.16 ms   (+5.23%) |      23   →      26    (+13.04%) |      156.47 ms →      186.14 ms  (+18.96%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.95 ms →        6.35 ms   (+6.56%) |      23   →      26    (+13.04%) |      136.96 ms →      164.99 ms  (+20.46%) | 
- │ │ ├ sirius::Potential::generate                                     |      578.54 ms →      579.57 ms   (+0.18%) |      23   →      26    (+13.04%) |       13.31 s  →       15.07 s   (+13.24%) | 
- │ │ │ ├ sirius::Potential::poisson                                    |      137.21 ms →      137.97 ms   (+0.56%) |      23   →      26    (+13.04%) |        3.16 s  →        3.59 s   (+13.67%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       17.42 ms →        5.88 ms  (-66.23%) |      23   →      26    (+13.04%) |      400.56 ms →      152.91 ms  (-61.83%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |       10.31 ms →       11.01 ms   (+6.81%) |      23   →      26    (+13.04%) |      237.06 ms →      286.22 ms  (+20.74%) | 
- │ │ │ │   └ sirius::Periodic_function|inner_local                     |        9.88 ms →       10.13 ms   (+2.47%) |      23   →      26    (+13.04%) |      227.31 ms →      263.30 ms  (+15.83%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        9.88 ms →       10.13 ms   (+2.47%) |      23   →      26    (+13.04%) |      227.30 ms →      263.29 ms  (+15.83%) | 
- │ │ │ ├ sirius::Periodic_function::add                                |      553.49 μs →      559.55 μs   (+1.09%) |      46   →      52    (+13.04%) |       25.46 ms →       29.10 ms  (+14.28%) | 
- │ │ │ ├ sirius::Potential::xc                                         |       49.26 ms →       49.11 ms   (-0.29%) |      23   →      26    (+13.04%) |        1.13 s  →        1.28 s   (+12.72%) | 
- │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.90 ms →       46.83 ms   (-0.13%) |      23   →      26    (+13.04%) |        1.08 s  →        1.22 s   (+12.89%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.01 ms →        2.96 ms   (-1.44%) |      46   →      52    (+13.04%) |      138.38 ms →      154.18 ms  (+11.42%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.55 ms →        5.45 ms   (-1.76%) |      23   →      26    (+13.04%) |      127.57 ms →      141.67 ms  (+11.05%) | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.57 ms →        6.46 ms   (-1.67%) |      23   →      26    (+13.04%) |      151.01 ms →      167.86 ms  (+11.15%) | 
- │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.92 ms →       90.89 ms   (-0.03%) |      23   →      26    (+13.04%) |        2.09 s  →        2.36 s   (+13.01%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      292.18 ms →      292.73 ms   (+0.19%) |      23   →      26    (+13.04%) |        6.72 s  →        7.61 s   (+13.26%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |      282.80 ms →      281.49 ms   (-0.46%) |      23   →      26    (+13.04%) |        6.50 s  →        7.32 s   (+12.52%) | 
- │ │ │ └ sirius::symmetrize_function|fpw                               |      282.80 ms →      281.49 ms   (-0.46%) |      23   →      26    (+13.04%) |        6.50 s  →        7.32 s   (+12.52%) | 
- │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.15 ms →       27.24 ms   (+0.31%) |      23   →      26    (+13.04%) |      624.51 ms →      708.13 ms  (+13.39%) | 
- │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      228.04 ms →      226.34 ms   (-0.74%) |      23   →      26    (+13.04%) |        5.24 s  →        5.88 s   (+12.20%) | 
- │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.80 ms →       24.13 ms   (+1.35%) |      23   →      26    (+13.04%) |      547.51 ms →      627.26 ms  (+14.57%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.49 ms →        5.86 ms   (+6.77%) |      23   →      26    (+13.04%) |      126.29 ms →      152.43 ms  (+20.70%) | 
- │ │ ├ sirius::Periodic_function|inner                                 |       10.34 ms →       10.44 ms   (+0.94%) |     161   →     182    (+13.04%) |        1.67 s  →        1.90 s   (+14.11%) | 
- │ │ │ └ sirius::Periodic_function|inner_local                         |        9.80 ms →       10.07 ms   (+2.74%) |     161   →     182    (+13.04%) |        1.58 s  →        1.83 s   (+16.14%) | 
- │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.80 ms →       10.07 ms   (+2.74%) |     161   →     182    (+13.04%) |        1.58 s  →        1.83 s   (+16.14%) | 
! │ │ ├ sirius::Smooth_periodic_function|inner                          |       11.03 ms →       10.68 ms   (-3.19%) |      69   →      78    (+13.04%) |      761.20 ms →      833.05 ms   (+9.44%) | 
- │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.60 ms →       10.42 ms   (-1.65%) |      69   →      78    (+13.04%) |      731.38 ms →      813.13 ms  (+11.18%) | 
- │ │ ├ sirius::Periodic_function::integrate                            |       10.08 ms →       10.13 ms   (+0.45%) |      23   →      26    (+13.04%) |      231.87 ms →      263.29 ms  (+13.55%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      121.08 μs →      164.29 μs  (+35.70%) |      23   →      26    (+13.04%) |        2.78 ms →        4.27 ms  (+53.39%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      115.99 μs →      159.19 μs  (+37.24%) |      23   →      26    (+13.04%) |        2.67 ms →        4.14 ms  (+55.15%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.07 ms →        5.08 ms   (+0.09%) |       2   →       2              |       10.14 ms →       10.15 ms   (+0.09%) | 
  │ ├ sirius::Periodic_function|inner                                   |        9.69 ms →       10.20 ms   (+5.29%) |       6   →       6              |       58.12 ms →       61.20 ms   (+5.29%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        9.65 ms →       10.19 ms   (+5.65%) |       6   →       6              |       57.88 ms →       61.15 ms   (+5.65%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        9.65 ms →       10.19 ms   (+5.65%) |       6   →       6              |       57.88 ms →       61.15 ms   (+5.65%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.58 ms →       10.78 ms   (+1.90%) |       3   →       3              |       31.73 ms →       32.33 ms   (+1.90%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.56 ms →       10.77 ms   (+1.97%) |       3   →       3              |       31.69 ms →       32.31 ms   (+1.97%) | 
  ├ sirius::Periodic_function|inner                                     |       10.05 ms →       10.38 ms   (+3.27%) |       2   →       2              |       20.11 ms →       20.76 ms   (+3.27%) | 
  │ └ sirius::Periodic_function|inner_local                             |        9.66 ms →       10.37 ms   (+7.44%) |       2   →       2              |       19.31 ms →       20.75 ms   (+7.44%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.66 ms →       10.37 ms   (+7.44%) |       2   →       2              |       19.31 ms →       20.75 ms   (+7.44%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.47 ms →       10.86 ms   (+3.69%) |       1   →       1              |       10.47 ms →       10.86 ms   (+3.69%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.47 ms →       10.85 ms   (+3.69%) |       1   →       1              |       10.47 ms →       10.85 ms   (+3.69%) | 
  └ sirius::finalize                                                    |      196.18 ms →      202.35 ms   (+3.14%) |       1   →       1              |      196.18 ms →      202.35 ms   (+3.14%) | 
  ====================================================================================================================================================================================================
```
