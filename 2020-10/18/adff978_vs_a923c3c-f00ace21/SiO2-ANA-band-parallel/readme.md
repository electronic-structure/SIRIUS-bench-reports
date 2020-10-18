# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      243.96 s  →      224.21 s    (-8.10%) |       1   →       1              |      243.96 s  →      224.21 s    (-8.10%) | 
  ├ sirius::initialize                                                  |        2.70 s  →        2.70 s    (+0.15%) |       1   →       1              |        2.70 s  →        2.70 s    (+0.15%) | 
  ├ sirius::Simulation_context::initialize                              |        3.03 s  →        2.94 s    (-3.09%) |       1   →       1              |        3.03 s  →        2.94 s    (-3.09%) | 
- │ ├ sirius::Simulation_context::init_comm                             |       27.27 ms →       34.28 ms  (+25.70%) |       1   →       1              |       27.27 ms →       34.28 ms  (+25.70%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      246.97 ms →      170.00 ms  (-31.17%) |       1   →       1              |      246.97 ms →      170.00 ms  (-31.17%) | 
+ │ │ ├ sirius::Atom_type::init                                         |      111.26 ms →       72.54 ms  (-34.80%) |       2   →       2              |      222.52 ms →      145.07 ms  (-34.80%) | 
  │ │ └ sirius::Unit_cell::update                                       |       24.37 ms →       24.84 ms   (+1.93%) |       1   →       1              |       24.37 ms →       24.84 ms   (+1.93%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.25 ms →        6.43 ms   (+2.91%) |       1   →       1              |        6.25 ms →        6.43 ms   (+2.91%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       18.07 ms →       18.36 ms   (+1.60%) |       1   →       1              |       18.07 ms →       18.36 ms   (+1.60%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       18.05 ms →       18.34 ms   (+1.60%) |       1   →       1              |       18.05 ms →       18.34 ms   (+1.60%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.15 ms →        4.14 ms   (-0.05%) |       1   →       1              |        4.15 ms →        4.14 ms   (-0.05%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.34 ms →        2.35 ms   (+0.63%) |       1   →       1              |        2.34 ms →        2.35 ms   (+0.63%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      105.44 μs →      102.67 μs   (-2.63%) |       1   →       1              |      105.44 μs →      102.67 μs   (-2.63%) | 
  │ └ sirius::Simulation_context::update                                |        2.71 s  →        2.69 s    (-0.59%) |       1   →       1              |        2.71 s  →        2.69 s    (-0.59%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.96 ms →       11.16 ms   (+1.78%) |       1   →       1              |       10.96 ms →       11.16 ms   (+1.78%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.48 ms →        4.51 ms   (+0.77%) |       1   →       1              |        4.48 ms →        4.51 ms   (+0.77%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.45 ms →        6.61 ms   (+2.44%) |       1   →       1              |        6.45 ms →        6.61 ms   (+2.44%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.43 ms →        6.59 ms   (+2.46%) |       1   →       1              |        6.43 ms →        6.59 ms   (+2.46%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.92 ms →        4.09 ms   (+4.28%) |       1   →       1              |        3.92 ms →        4.09 ms   (+4.28%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.32 ms   (-0.24%) |       1   →       1              |        2.33 ms →        2.32 ms   (-0.24%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      100.71 μs →       99.61 μs   (-1.09%) |       1   →       1              |      100.71 μs →       99.61 μs   (-1.09%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       63.70 ms →       63.14 ms   (-0.87%) |       2   →       2              |      127.40 ms →      126.29 ms   (-0.87%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.18 ms →        5.15 ms   (-0.67%) |       2   →       2              |       10.37 ms →       10.30 ms   (-0.67%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.47 ms →        4.47 ms   (-0.03%) |       1   →       1              |        4.47 ms →        4.47 ms   (-0.03%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.95 ms →       21.72 ms   (-1.04%) |       2   →       2              |       43.90 ms →       43.44 ms   (-1.04%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.82 ms →       14.84 ms   (+0.10%) |       2   →       2              |       29.64 ms →       29.67 ms   (+0.10%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.67 ms →       19.85 ms   (+0.89%) |       4   →       4              |       78.69 ms →       79.39 ms   (+0.89%) | 
  │   ├ sddk::Gvec::init                                                |      170.40 ms →      171.26 ms   (+0.50%) |       2   →       2              |      340.81 ms →      342.52 ms   (+0.50%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      128.26 ms →      128.58 ms   (+0.25%) |       2   →       2              |      256.52 ms →      257.16 ms   (+0.25%) | 
  │   ├ sddk::Gvec_shells                                               |      163.52 ms →      163.43 ms   (-0.06%) |       1   →       1              |      163.52 ms →      163.43 ms   (-0.06%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.31 ms →        1.34 ms   (+2.07%) |       1   →       1              |        1.31 ms →        1.34 ms   (+2.07%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      294.63 ms →      294.55 ms   (-0.03%) |       2   →       2              |      589.27 ms →      589.10 ms   (-0.03%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       79.55 ms →       76.46 ms   (-3.88%) |       1   →       1              |       79.55 ms →       76.46 ms   (-3.88%) | 
- │ ├ sirius::K_point::K_point                                          |        2.19 μs →        2.46 μs  (+12.36%) |       4   →       4              |        8.75 μs →        9.84 μs  (+12.36%) | 
  │ └ sirius::K_point_set::initialize                                   |       79.45 ms →       76.36 ms   (-3.88%) |       1   →       1              |       79.45 ms →       76.36 ms   (-3.88%) | 
  │   └ sirius::K_point::initialize                                     |       19.85 ms →       19.07 ms   (-3.93%) |       4   →       4              |       79.40 ms →       76.28 ms   (-3.93%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       15.26 ms →       14.48 ms   (-5.11%) |       4   →       4              |       61.05 ms →       57.93 ms   (-5.11%) | 
  │     │ └ sddk::Gvec::init                                            |        3.82 ms →        3.86 ms   (+0.99%) |       4   →       4              |       15.29 ms →       15.44 ms   (+0.99%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        9.18 μs →        8.91 μs   (-2.91%) |       4   →       4              |       36.72 μs →       35.66 μs   (-2.91%) | 
  │     └ sirius::K_point::update                                       |        3.27 ms →        3.29 ms   (+0.56%) |       4   →       4              |       13.10 ms →       13.17 ms   (+0.56%) | 
  │       └ sirius::Beta_projectors                                     |        1.75 ms →        1.77 ms   (+1.31%) |       4   →       4              |        6.98 ms →        7.07 ms   (+1.31%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      926.25 μs →      941.91 μs   (+1.69%) |       4   →       4              |        3.70 ms →        3.77 ms   (+1.69%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.16 ms →        5.32 ms   (+3.01%) |       2   →       2              |       10.32 ms →       10.64 ms   (+3.01%) | 
  ├ sirius::Potential                                                   |      158.63 ms →      159.42 ms   (+0.50%) |       1   →       1              |      158.63 ms →      159.42 ms   (+0.50%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.75 ms →        5.75 ms   (+0.07%) |       6   →       6              |       34.48 ms →       34.51 ms   (+0.07%) | 
  │ └ sirius::Potential::update                                         |      123.43 ms →      124.21 ms   (+0.63%) |       1   →       1              |      123.43 ms →      124.21 ms   (+0.63%) | 
  │   └ sirius::Potential::generate_local_potential                     |      122.71 ms →      123.51 ms   (+0.65%) |       1   →       1              |      122.71 ms →      123.51 ms   (+0.65%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      114.53 ms →      115.19 ms   (+0.57%) |       1   →       1              |      114.53 ms →      115.19 ms   (+0.57%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        7.32 ms →        7.46 ms   (+1.90%) |       1   →       1              |        7.32 ms →        7.46 ms   (+1.90%) | 
  ├ sirius::Density                                                     |      134.79 ms →      134.73 ms   (-0.04%) |       1   →       1              |      134.79 ms →      134.73 ms   (-0.04%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.08 ms →        5.09 ms   (+0.21%) |       2   →       2              |       10.17 ms →       10.19 ms   (+0.21%) | 
  │ └ sirius::Density::update                                           |      124.36 ms →      124.28 ms   (-0.06%) |       1   →       1              |      124.36 ms →      124.28 ms   (-0.06%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      123.95 ms →      123.87 ms   (-0.07%) |       1   →       1              |      123.95 ms →      123.87 ms   (-0.07%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |      103.13 μs →      101.84 μs   (-1.25%) |       1   →       1              |      103.13 μs →      101.84 μs   (-1.25%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      118.27 ms →      118.25 ms   (-0.01%) |       1   →       1              |      118.27 ms →      118.25 ms   (-0.01%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        5.14 ms →        5.07 ms   (-1.42%) |       1   →       1              |        5.14 ms →        5.07 ms   (-1.42%) | 
  ├ sirius::Density::initial_density                                    |      177.14 ms →      174.43 ms   (-1.53%) |       1   →       1              |      177.14 ms →      174.43 ms   (-1.53%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      122.98 ms →      122.21 ms   (-0.62%) |       1   →       1              |      122.98 ms →      122.21 ms   (-0.62%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.07 ms →        5.00 ms   (-1.32%) |       2   →       2              |       10.14 ms →       10.01 ms   (-1.32%) | 
+ │ └ sirius::Periodic_function::integrate                              |       11.54 ms →        9.77 ms  (-15.35%) |       1   →       1              |       11.54 ms →        9.77 ms  (-15.35%) | 
  ├ sirius::Potential::generate                                         |      593.88 ms →      591.93 ms   (-0.33%) |       1   →       1              |      593.88 ms →      591.93 ms   (-0.33%) | 
  │ ├ sirius::Potential::poisson                                        |      137.01 ms →      137.42 ms   (+0.30%) |       1   →       1              |      137.01 ms →      137.42 ms   (+0.30%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.23 ms →        5.31 ms   (+1.60%) |       1   →       1              |        5.23 ms →        5.31 ms   (+1.60%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        9.98 ms →       10.79 ms   (+8.11%) |       1   →       1              |        9.98 ms →       10.79 ms   (+8.11%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        9.89 ms →        9.88 ms   (-0.09%) |       1   →       1              |        9.89 ms →        9.88 ms   (-0.09%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.89 ms →        9.88 ms   (-0.09%) |       1   →       1              |        9.89 ms →        9.88 ms   (-0.09%) | 
  │ ├ sirius::Periodic_function::add                                    |      546.56 μs →      559.68 μs   (+2.40%) |       2   →       2              |        1.09 ms →        1.12 ms   (+2.40%) | 
  │ ├ sirius::Potential::xc                                             |       56.04 ms →       54.31 ms   (-3.10%) |       1   →       1              |       56.04 ms →       54.31 ms   (-3.10%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       53.75 ms →       52.02 ms   (-3.21%) |       1   →       1              |       53.75 ms →       52.02 ms   (-3.21%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.61 ms →        5.65 ms   (+0.73%) |       2   →       2              |       11.22 ms →       11.30 ms   (+0.73%) | 
+ │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.97 ms →        5.30 ms  (-11.13%) |       1   →       1              |        5.97 ms →        5.30 ms  (-11.13%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.77 ms →        5.62 ms   (-2.63%) |       1   →       1              |        5.77 ms →        5.62 ms   (-2.63%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       93.44 ms →       92.72 ms   (-0.78%) |       1   →       1              |       93.44 ms →       92.72 ms   (-0.78%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      299.18 ms →      299.42 ms   (+0.08%) |       1   →       1              |      299.18 ms →      299.42 ms   (+0.08%) | 
  ├ sirius::Hamiltonian0                                                |        8.38 ms →        8.36 ms   (-0.27%) |       1   →       1              |        8.38 ms →        8.36 ms   (-0.27%) | 
  │ ├ sirius::Local_operator                                            |        8.03 ms →        8.03 ms   (-0.03%) |       1   →       1              |        8.03 ms →        8.03 ms   (-0.03%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.70 ms →        4.80 ms   (+2.16%) |       1   →       1              |        4.70 ms →        4.80 ms   (+2.16%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.41 ms →        2.31 ms   (-4.06%) |       1   →       1              |        2.41 ms →        2.31 ms   (-4.06%) | 
  │ ├ sirius::Non_local_operator                                        |       64.34 μs →       63.06 μs   (-1.99%) |       2   →       2              |      128.68 μs →      126.11 μs   (-1.99%) | 
  │ ├ sirius::D_operator::initialize                                    |       98.26 μs →       90.41 μs   (-7.99%) |       1   →       1              |       98.26 μs →       90.41 μs   (-7.99%) | 
  │ └ sirius::Q_operator::initialize                                    |       72.39 μs →       68.56 μs   (-5.30%) |       1   →       1              |       72.39 μs →       68.56 μs   (-5.30%) | 
  ├ sirius::Band::initialize_subspace                                   |        3.14 s  →        3.15 s    (+0.37%) |       1   →       1              |        3.14 s  →        3.15 s    (+0.37%) | 
  │ ├ sirius::Hamiltonian_k                                             |      379.12 μs →      374.50 μs   (-1.22%) |       4   →       4              |        1.52 ms →        1.50 ms   (-1.22%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      370.01 μs →      369.16 μs   (-0.23%) |       4   →       4              |        1.48 ms →        1.48 ms   (-0.23%) | 
+ │ │ └ sirius::Beta_projectors_base::prepare                           |        7.03 μs →        3.46 μs  (-50.78%) |       4   →       4              |       28.13 μs →       13.85 μs  (-50.78%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |      783.49 ms →      786.42 ms   (+0.37%) |       4   →       4              |        3.13 s  →        3.15 s    (+0.37%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       32.29 ms →       32.86 ms   (+1.76%) |      16   →      16              |      516.64 ms →      525.73 ms   (+1.76%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       14.56 ms →       14.68 ms   (+0.83%) |       4   →       4              |       58.25 ms →       58.74 ms   (+0.83%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        5.40 ms →        5.52 ms   (+2.38%) |       4   →       4              |       21.58 ms →       22.09 ms   (+2.38%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      357.54 ms →      356.82 ms   (-0.20%) |       4   →       4              |        1.43 s  →        1.43 s    (-0.20%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      259.62 ms →      258.98 ms   (-0.25%) |       4   →       4              |        1.04 s  →        1.04 s    (-0.25%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       63.79 ms →       63.40 ms   (-0.61%) |       4   →       4              |      255.15 ms →      253.59 ms   (-0.61%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       15.98 ms →       16.52 ms   (+3.43%) |       4   →       4              |       63.90 ms →       66.09 ms   (+3.43%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       15.97 ms →       16.52 ms   (+3.43%) |       4   →       4              |       63.89 ms →       66.08 ms   (+3.43%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       41.42 ms →       40.46 ms   (-2.33%) |       4   →       4              |      165.68 ms →      161.82 ms   (-2.33%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |       16.00 ms →       16.56 ms   (+3.53%) |       4   →       4              |       63.99 ms →       66.25 ms   (+3.53%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |       15.99 ms →       16.56 ms   (+3.54%) |       4   →       4              |       63.97 ms →       66.24 ms   (+3.54%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |       54.39 ms →       53.98 ms   (-0.77%) |       4   →       4              |      217.58 ms →      215.90 ms   (-0.77%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |       36.38 ms →       35.95 ms   (-1.17%) |       4   →       4              |      145.50 ms →      143.80 ms   (-1.17%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        1.93 ms →        1.94 ms   (+0.53%) |       4   →       4              |        7.70 ms →        7.74 ms   (+0.53%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       41.79 ms →       41.58 ms   (-0.52%) |       4   →       4              |      167.18 ms →      166.31 ms   (-0.52%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |        8.67 ms →        8.42 ms   (-2.87%) |       4   →       4              |       34.70 ms →       33.70 ms   (-2.87%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       27.08 ms →       27.15 ms   (+0.24%) |       8   →       8              |      216.65 ms →      217.17 ms   (+0.24%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       15.51 ms →       15.36 ms   (-1.02%) |       8   →       8              |      124.11 ms →      122.84 ms   (-1.02%) | 
  │ │ │ └ sddk::wf_inner                                                |       15.47 ms →       15.31 ms   (-1.03%) |       8   →       8              |      123.77 ms →      122.49 ms   (-1.03%) | 
  │ │ │   ├ sddk::wf_inner|scale                                        |       26.88 ns →       28.50 ns   (+6.05%) |       8   →       8              |      215.00 ns →      228.00 ns   (+6.05%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       15.30 ms →       15.13 ms   (-1.07%) |       8   →       8              |      122.37 ms →      121.07 ms   (-1.07%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       24.62 ns →       37.00 ns  (+50.25%) |       8   →       8              |      197.00 ns →      296.00 ns  (+50.25%) | 
  │ │ ├ Eigensolver_scalapack|pzhegvx                                   |      126.35 ms →      125.49 ms   (-0.68%) |       4   →       4              |      505.40 ms →      501.95 ms   (-0.68%) | 
  │ │ └ sddk::wf_trans                                                  |       23.62 ms →       23.65 ms   (+0.12%) |       4   →       4              |       94.49 ms →       94.60 ms   (+0.12%) | 
  │ │   └ sddk::wf_trans|pw                                             |       23.40 ms →       23.44 ms   (+0.18%) |       4   →       4              |       93.60 ms →       93.76 ms   (+0.18%) | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      386.00 ns →      438.75 ns  (+13.67%) |       4   →       4              |        1.54 μs →        1.75 μs  (+13.67%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      233.11 s  →      212.99 s    (-8.63%) |       1   →       1              |      233.11 s  →      212.99 s    (-8.63%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.67 ms →        5.68 ms   (+0.15%) |      19   →      19              |      107.74 ms →      107.90 ms   (+0.15%) | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        8.95 s  →        7.88 s   (-12.00%) |      26   →      27     (+3.85%) |      232.70 s  →      212.65 s    (-8.61%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        4.66 ms →        4.56 ms   (-2.22%) |      26   →      27     (+3.85%) |      121.26 ms →      123.14 ms   (+1.55%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.30 ms →        4.21 ms   (-2.25%) |      26   →      27     (+3.85%) |      111.88 ms →      113.58 ms   (+1.51%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      982.76 μs →      961.47 μs   (-2.17%) |      26   →      27     (+3.85%) |       25.55 ms →       25.96 ms   (+1.60%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.43 ms →        2.35 ms   (-3.18%) |      26   →      27     (+3.85%) |       63.22 ms →       63.57 ms   (+0.55%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.64 μs →       64.70 μs   (+0.10%) |      52   →      54     (+3.85%) |        3.36 ms →        3.49 ms   (+3.95%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       94.40 μs →       92.12 μs   (-2.41%) |      26   →      27     (+3.85%) |        2.45 ms →        2.49 ms   (+1.34%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       66.97 μs →       65.56 μs   (-2.11%) |      26   →      27     (+3.85%) |        1.74 ms →        1.77 ms   (+1.66%) | 
+ │ │ ├ sirius::Band::solve                                             |        6.84 s  →        5.78 s   (-15.56%) |      26   →      27     (+3.85%) |      177.89 s  →      155.99 s   (-12.31%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      334.86 μs →      326.64 μs   (-2.45%) |     104   →     108     (+3.85%) |       34.82 ms →       35.28 ms   (+1.30%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      328.85 μs →      321.41 μs   (-2.26%) |     104   →     108     (+3.85%) |       34.20 ms →       34.71 ms   (+1.49%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.19 μs →        3.86 μs   (-7.97%) |     104   →     108     (+3.85%) |      436.10 μs →      416.77 μs   (-4.43%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.71 s  →        1.44 s   (-15.56%) |     104   →     108     (+3.85%) |      177.86 s  →      155.95 s   (-12.32%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       11.98 ms →       11.89 ms   (-0.74%) |     104   →     108     (+3.85%) |        1.25 s  →        1.28 s    (+3.08%) | 
- │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |      630.27 ns →      726.33 ns  (+15.24%) |     624   →     648     (+3.85%) |      393.29 μs →      470.67 μs  (+19.67%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.84 ms →        1.82 ms   (-0.77%) |     104   →     108     (+3.85%) |      191.08 ms →      196.90 ms   (+3.04%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      354.16 μs →      349.89 μs   (-1.20%) |     104   →     108     (+3.85%) |       36.83 ms →       37.79 ms   (+2.60%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      551.94 μs →      549.25 μs   (-0.49%) |     208   →     216     (+3.85%) |      114.80 ms →      118.64 ms   (+3.34%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.69 s  →        1.42 s   (-15.77%) |     104   →     108     (+3.85%) |      175.48 s  →      153.49 s   (-12.53%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       70.59 ms →       69.83 ms   (-1.07%) |     899   →     953     (+6.01%) |       63.46 s  →       66.55 s    (+4.87%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       45.16 ms →       44.57 ms   (-1.30%) |     899   →     953     (+6.01%) |       40.60 s  →       42.47 s    (+4.62%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        8.81 ms →        8.85 ms   (+0.45%) |     899   →     953     (+6.01%) |        7.92 s  →        8.43 s    (+6.49%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      231.39 μs →      216.27 μs   (-6.54%) |     899   →     953     (+6.01%) |      208.02 ms →      206.10 ms   (-0.92%) | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        1.98 ms →        1.89 ms   (-4.59%) |     104   →     108     (+3.85%) |      206.20 ms →      204.30 ms   (-0.92%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |        7.03 ms →        6.90 ms   (-1.81%) |     899   →     953     (+6.01%) |        6.32 s  →        6.57 s    (+4.09%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |       88.88 μs →       83.32 μs   (-6.26%) |     899   →     953     (+6.01%) |       79.91 ms →       79.40 ms   (-0.63%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |      745.00 μs →      712.22 μs   (-4.40%) |     104   →     108     (+3.85%) |       77.48 ms →       76.92 ms   (-0.72%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       10.01 ms →        9.82 ms   (-1.86%) |     899   →     953     (+6.01%) |        9.00 s  →        9.36 s    (+4.03%) | 
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |        6.34 ms →        6.21 ms   (-2.03%) |     899   →     953     (+6.01%) |        5.70 s  →        5.92 s    (+3.85%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        1.52 ms →        1.52 ms   (+0.05%) |     899   →     953     (+6.01%) |        1.37 s  →        1.45 s    (+6.06%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        8.95 ms →        8.78 ms   (-1.87%) |     899   →     953     (+6.01%) |        8.05 s  →        8.37 s    (+4.02%) | 
  │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        1.56 ms →        1.53 ms   (-1.87%) |     899   →     953     (+6.01%) |        1.40 s  →        1.46 s    (+4.03%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.47 ms →        7.47 ms   (-0.01%) |    1.80 K →    1.91 K   (+6.01%) |       13.43 s  →       14.23 s    (+5.99%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       28.45 ms →       27.17 ms   (-4.53%) |     899   →     953     (+6.01%) |       25.58 s  →       25.89 s    (+1.20%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        2.13 ms →        1.98 ms   (-6.84%) |    1.69 K →    1.80 K   (+6.14%) |        3.61 s  →        3.57 s    (-1.12%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       67.62 ns →       71.39 ns   (+5.56%) |    1.69 K →    1.80 K   (+6.14%) |      114.55 μs →      128.35 μs  (+12.04%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        2.12 ms →        1.98 ms   (-6.66%) |    1.69 K →    1.80 K   (+6.14%) |        3.59 s  →        3.55 s    (-0.93%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       57.76 ns →       66.43 ns  (+15.01%) |    1.69 K →    1.80 K   (+6.14%) |       97.84 μs →      119.43 μs  (+22.07%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|potrf                               |      854.46 μs →      821.73 μs   (-3.83%) |     899   →     953     (+6.01%) |      768.16 ms →      783.11 ms   (+1.95%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|trtri                               |      784.87 μs →      805.48 μs   (+2.63%) |     899   →     953     (+6.01%) |      705.59 ms →      767.63 ms   (+8.79%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |        5.46 ms →        5.21 ms   (-4.64%) |    3.49 K →    3.70 K   (+6.07%) |       19.08 s  →       19.30 s    (+1.15%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        3.71 ms →        3.55 ms   (-4.48%) |    5.08 K →    5.39 K   (+6.14%) |       18.86 s  →       19.12 s    (+1.38%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        5.58 ms →        5.28 ms   (-5.47%) |     899   →     953     (+6.01%) |        5.02 s  →        5.03 s    (+0.21%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |        3.86 ms →        3.55 ms   (-7.96%) |     899   →     953     (+6.01%) |        3.47 s  →        3.39 s    (-2.44%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       55.01 ns →       49.29 ns  (-10.40%) |     899   →     953     (+6.01%) |       49.45 μs →       46.97 μs   (-5.02%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        3.84 ms →        3.54 ms   (-7.89%) |     899   →     953     (+6.01%) |        3.45 s  →        3.37 s    (-2.35%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       49.62 ns →       51.85 ns   (+4.50%) |     899   →     953     (+6.01%) |       44.61 μs →       49.42 μs  (+10.77%) | 
+ │ │ │ │   ├ Eigensolver_scalapack|pzheevx                             |       67.93 ms →       35.78 ms  (-47.33%) |     899   →     953     (+6.01%) |       61.07 s  →       34.10 s   (-44.16%) | 
  │ │ │ │   ├ sirius::residuals                                         |       10.85 ms →       10.01 ms   (-7.69%) |     880   →     925     (+5.11%) |        9.55 s  →        9.26 s    (-2.97%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       10.50 ms →        9.55 ms   (-9.00%) |     833   →     883     (+6.00%) |        8.74 s  →        8.43 s    (-3.54%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        5.21 ms →        4.75 ms   (-8.79%) |    1.67 K →    1.77 K   (+6.00%) |        8.67 s  →        8.38 s    (-3.31%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      654.44 μs →      645.75 μs   (-1.33%) |     833   →     883     (+6.00%) |      545.15 ms →      570.20 ms   (+4.60%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       51.55 ms →       37.04 ms  (-28.15%) |     209   →     341    (+63.16%) |       10.77 s  →       12.63 s   (+17.23%) | 
- │ │ │ │     └ sddk::wf_trans                                          |       34.20 ms →       21.88 ms  (-36.03%) |     314   →     574    (+82.80%) |       10.74 s  →       12.56 s   (+16.94%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |       25.44 ms →       15.46 ms  (-39.24%) |     419   →     807    (+92.60%) |       10.66 s  →       12.48 s   (+17.03%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      557.45 ns →      474.01 ns  (-14.97%) |     104   →     108     (+3.85%) |       57.98 μs →       51.19 μs  (-11.70%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       21.22 μs →       21.02 μs   (-0.91%) |      26   →      27     (+3.85%) |      551.64 μs →      567.67 μs   (+2.91%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      593.05 μs →      589.62 μs   (-0.58%) |      26   →      27     (+3.85%) |       15.42 ms →       15.92 ms   (+3.25%) | 
  │ │ ├ sirius::Density::generate                                       |      899.91 ms →      895.31 ms   (-0.51%) |      26   →      27     (+3.85%) |       23.40 s  →       24.17 s    (+3.31%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      529.82 ms →      529.54 ms   (-0.05%) |      26   →      27     (+3.85%) |       13.78 s  →       14.30 s    (+3.79%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       24.85 ms →       25.08 ms   (+0.90%) |     104   →     108     (+3.85%) |        2.58 s  →        2.71 s    (+4.78%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |        8.73 μs →        8.90 μs   (+1.89%) |     104   →     108     (+3.85%) |      908.03 μs →      960.78 μs   (+5.81%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       15.34 μs →       15.92 μs   (+3.75%) |       8   →       8              |      122.75 μs →      127.35 μs   (+3.75%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       20.75 ms →       20.89 ms   (+0.71%) |     104   →     108     (+3.85%) |        2.16 s  →        2.26 s    (+4.58%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       30.44 ms →       30.56 ms   (+0.39%) |     104   →     108     (+3.85%) |        3.17 s  →        3.30 s    (+4.25%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.37 μs →        9.46 μs   (+0.99%) |     104   →     108     (+3.85%) |      974.62 μs →        1.02 ms   (+4.88%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        1.45 ms →        1.45 ms   (+0.08%) |     104   →     108     (+3.85%) |      151.13 ms →      157.06 ms   (+3.93%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       28.51 ms →       28.64 ms   (+0.44%) |     104   →     108     (+3.85%) |        2.97 s  →        3.09 s    (+4.30%) | 
  │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        4.38 ms →        4.51 ms   (+2.89%) |     104   →     108     (+3.85%) |      455.80 ms →      487.00 ms   (+6.85%) | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      558.12 ns →      545.95 ns   (-2.18%) |     104   →     108     (+3.85%) |       58.04 μs →       58.96 μs   (+1.58%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       42.79 ms →       42.36 ms   (-1.01%) |     104   →     108     (+3.85%) |        4.45 s  →        4.57 s    (+2.80%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.64 ms   (-0.39%) |      26   →      27     (+3.85%) |       42.69 ms →       44.16 ms   (+3.44%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.93 ms →       88.84 ms   (-0.11%) |      26   →      27     (+3.85%) |        2.31 s  →        2.40 s    (+3.74%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.69 ms →       88.60 ms   (-0.11%) |      26   →      27     (+3.85%) |        2.31 s  →        2.39 s    (+3.74%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      276.85 ms →      275.50 ms   (-0.49%) |      26   →      27     (+3.85%) |        7.20 s  →        7.44 s    (+3.34%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      276.85 ms →      275.50 ms   (-0.49%) |      26   →      27     (+3.85%) |        7.20 s  →        7.44 s    (+3.34%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.53 ms →       24.27 ms   (-1.07%) |      26   →      27     (+3.85%) |      637.81 ms →      655.28 ms   (+2.74%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      226.12 ms →      224.81 ms   (-0.58%) |      26   →      27     (+3.85%) |        5.88 s  →        6.07 s    (+3.25%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       24.42 ms →       24.64 ms   (+0.89%) |      26   →      27     (+3.85%) |      635.00 ms →      665.30 ms   (+4.77%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       81.19 ms →       80.32 ms   (-1.07%) |      26   →      27     (+3.85%) |        2.11 s  →        2.17 s    (+2.73%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        8.46 ms →        6.36 ms  (-24.82%) |      26   →      27     (+3.85%) |      220.00 ms →      171.76 ms  (-21.93%) | 
  │ │ ├ sirius::Density::mix                                            |      219.99 ms →      216.24 ms   (-1.71%) |      26   →      27     (+3.85%) |        5.72 s  →        5.84 s    (+2.07%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      931.28 μs →      970.57 μs   (+4.22%) |      26   →      27     (+3.85%) |       24.21 ms →       26.21 ms   (+8.23%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.80 ms →       10.27 ms   (-4.89%) |     334   →     349     (+4.49%) |        3.61 s  →        3.59 s    (-0.62%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.37 ms →        9.94 ms   (-4.21%) |     334   →     349     (+4.49%) |        3.46 s  →        3.47 s    (+0.09%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.37 ms →        9.94 ms   (-4.21%) |     334   →     349     (+4.49%) |        3.46 s  →        3.47 s    (+0.09%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        7.44 ms →        6.06 ms  (-18.52%) |      26   →      27     (+3.85%) |      193.33 ms →      163.59 ms  (-15.38%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        6.58 ms →        5.23 ms  (-20.43%) |      26   →      27     (+3.85%) |      170.99 ms →      141.29 ms  (-17.37%) | 
  │ │ ├ sirius::Potential::generate                                     |      579.45 ms →      579.08 ms   (-0.06%) |      26   →      27     (+3.85%) |       15.07 s  →       15.64 s    (+3.78%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      137.48 ms →      136.99 ms   (-0.36%) |      26   →      27     (+3.85%) |        3.57 s  →        3.70 s    (+3.47%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        5.18 ms →        5.23 ms   (+0.87%) |      26   →      27     (+3.85%) |      134.70 ms →      141.10 ms   (+4.75%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.31 ms →       10.66 ms   (+3.42%) |      26   →      27     (+3.85%) |      268.06 ms →      287.88 ms   (+7.39%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.15 ms →       10.63 ms   (+4.72%) |      26   →      27     (+3.85%) |      263.97 ms →      287.06 ms   (+8.74%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.15 ms →       10.63 ms   (+4.72%) |      26   →      27     (+3.85%) |      263.96 ms →      287.04 ms   (+8.74%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      553.84 μs →      564.32 μs   (+1.89%) |      52   →      54     (+3.85%) |       28.80 ms →       30.47 ms   (+5.81%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       49.31 ms →       49.09 ms   (-0.45%) |      26   →      27     (+3.85%) |        1.28 s  →        1.33 s    (+3.38%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.94 ms →       46.78 ms   (-0.34%) |      26   →      27     (+3.85%) |        1.22 s  →        1.26 s    (+3.49%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.06 ms →        3.01 ms   (-1.67%) |      52   →      54     (+3.85%) |      159.35 ms →      162.71 ms   (+2.11%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.46 ms →        5.38 ms   (-1.48%) |      26   →      27     (+3.85%) |      141.88 ms →      145.17 ms   (+2.31%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.63 ms →        6.67 ms   (+0.51%) |      26   →      27     (+3.85%) |      172.50 ms →      180.04 ms   (+4.38%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.96 ms →       90.91 ms   (-0.05%) |      26   →      27     (+3.85%) |        2.36 s  →        2.45 s    (+3.79%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      292.66 ms →      293.03 ms   (+0.13%) |      26   →      27     (+3.85%) |        7.61 s  →        7.91 s    (+3.98%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      280.95 ms →      279.93 ms   (-0.37%) |      26   →      27     (+3.85%) |        7.30 s  →        7.56 s    (+3.47%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      280.95 ms →      279.93 ms   (-0.37%) |      26   →      27     (+3.85%) |        7.30 s  →        7.56 s    (+3.47%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.29 ms →       27.17 ms   (-0.46%) |      26   →      27     (+3.85%) |      709.60 ms →      733.49 ms   (+3.37%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      226.04 ms →      225.20 ms   (-0.37%) |      26   →      27     (+3.85%) |        5.88 s  →        6.08 s    (+3.46%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.81 ms →       23.77 ms   (-0.19%) |      26   →      27     (+3.85%) |      619.17 ms →      641.80 ms   (+3.65%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.72 ms →        5.51 ms   (-3.62%) |      26   →      27     (+3.85%) |      148.76 ms →      148.89 ms   (+0.09%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.42 ms →       10.67 ms   (+2.39%) |     182   →     189     (+3.85%) |        1.90 s  →        2.02 s    (+6.32%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.79 ms →        9.85 ms   (+0.59%) |     182   →     189     (+3.85%) |        1.78 s  →        1.86 s    (+4.46%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.79 ms →        9.85 ms   (+0.59%) |     182   →     189     (+3.85%) |        1.78 s  →        1.86 s    (+4.46%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       11.11 ms →       10.83 ms   (-2.57%) |      78   →      81     (+3.85%) |      866.97 ms →      877.16 ms   (+1.18%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.59 ms →       10.12 ms   (-4.41%) |      78   →      81     (+3.85%) |      825.99 ms →      819.90 ms   (-0.74%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        9.90 ms →       10.02 ms   (+1.25%) |      26   →      27     (+3.85%) |      257.29 ms →      270.52 ms   (+5.14%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      118.34 μs →      131.13 μs  (+10.80%) |      26   →      27     (+3.85%) |        3.08 ms →        3.54 ms  (+15.06%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      113.33 μs →      125.77 μs  (+10.97%) |      26   →      27     (+3.85%) |        2.95 ms →        3.40 ms  (+15.24%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.12 ms →        5.18 ms   (+1.21%) |       2   →       2              |       10.24 ms →       10.37 ms   (+1.21%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.09 ms →        9.84 ms   (-2.44%) |       6   →       6              |       60.53 ms →       59.05 ms   (-2.44%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.08 ms →        9.70 ms   (-3.72%) |       6   →       6              |       60.46 ms →       58.21 ms   (-3.72%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.08 ms →        9.70 ms   (-3.72%) |       6   →       6              |       60.46 ms →       58.21 ms   (-3.72%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.84 ms →       10.21 ms   (-5.84%) |       3   →       3              |       32.53 ms →       30.63 ms   (-5.84%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.83 ms →       10.10 ms   (-6.79%) |       3   →       3              |       32.50 ms →       30.30 ms   (-6.79%) | 
  ├ sirius::Periodic_function|inner                                     |       10.17 ms →        9.80 ms   (-3.61%) |       2   →       2              |       20.33 ms →       19.60 ms   (-3.61%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.16 ms →        9.78 ms   (-3.78%) |       2   →       2              |       20.32 ms →       19.55 ms   (-3.78%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.16 ms →        9.78 ms   (-3.78%) |       2   →       2              |       20.32 ms →       19.55 ms   (-3.78%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.86 ms →       10.13 ms   (-6.73%) |       1   →       1              |       10.86 ms →       10.13 ms   (-6.73%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.86 ms →       10.12 ms   (-6.75%) |       1   →       1              |       10.86 ms →       10.12 ms   (-6.75%) | 
  └ sirius::finalize                                                    |      305.86 ms →      291.23 ms   (-4.78%) |       1   →       1              |      305.86 ms →      291.23 ms   (-4.78%) | 
  ====================================================================================================================================================================================================
```
