# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      246.82 s  →      224.03 s    (-9.24%) |       1   →       1              |      246.82 s  →      224.03 s    (-9.24%) | 
  ├ sirius::initialize                                                  |        2.74 s  →        2.71 s    (-1.13%) |       1   →       1              |        2.74 s  →        2.71 s    (-1.13%) | 
  ├ sirius::Simulation_context::initialize                              |        2.94 s  →        2.93 s    (-0.06%) |       1   →       1              |        2.94 s  →        2.93 s    (-0.06%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       25.60 ms →      225.65 μs  (-99.12%) |       1   →       1              |       25.60 ms →      225.65 μs  (-99.12%) | 
  │ ├ sirius::Unit_cell::initialize                                     |      162.44 ms →      173.30 ms   (+6.69%) |       1   →       1              |      162.44 ms →      173.30 ms   (+6.69%) | 
  │ │ ├ sirius::Atom_type::init                                         |       69.59 ms →       75.20 ms   (+8.06%) |       2   →       2              |      139.18 ms →      150.39 ms   (+8.06%) | 
  │ │ └ sirius::Unit_cell::update                                       |       23.18 ms →       22.84 ms   (-1.49%) |       1   →       1              |       23.18 ms →       22.84 ms   (-1.49%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.28 ms →        6.18 ms   (-1.61%) |       1   →       1              |        6.28 ms →        6.18 ms   (-1.61%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       16.86 ms →       16.62 ms   (-1.44%) |       1   →       1              |       16.86 ms →       16.62 ms   (-1.44%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       16.84 ms →       16.60 ms   (-1.43%) |       1   →       1              |       16.84 ms →       16.60 ms   (-1.43%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.15 ms →        4.15 ms   (-0.06%) |       1   →       1              |        4.15 ms →        4.15 ms   (-0.06%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.35 ms →        2.34 ms   (-0.39%) |       1   →       1              |        2.35 ms →        2.34 ms   (-0.39%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      104.89 μs →      101.90 μs   (-2.85%) |       1   →       1              |      104.89 μs →      101.90 μs   (-2.85%) | 
  │ └ sirius::Simulation_context::update                                |        2.70 s  →        2.71 s    (+0.50%) |       1   →       1              |        2.70 s  →        2.71 s    (+0.50%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.61 ms →       10.98 ms   (+3.54%) |       1   →       1              |       10.61 ms →       10.98 ms   (+3.54%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.18 ms →        4.35 ms   (+3.97%) |       1   →       1              |        4.18 ms →        4.35 ms   (+3.97%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.39 ms →        6.60 ms   (+3.28%) |       1   →       1              |        6.39 ms →        6.60 ms   (+3.28%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.37 ms →        6.58 ms   (+3.29%) |       1   →       1              |        6.37 ms →        6.58 ms   (+3.29%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.88 ms →        4.08 ms   (+5.15%) |       1   →       1              |        3.88 ms →        4.08 ms   (+5.15%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.32 ms   (+0.26%) |       1   →       1              |        2.32 ms →        2.32 ms   (+0.26%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      103.24 μs →       99.13 μs   (-3.98%) |       1   →       1              |      103.24 μs →       99.13 μs   (-3.98%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       62.47 ms →       62.75 ms   (+0.45%) |       2   →       2              |      124.94 ms →      125.51 ms   (+0.45%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.18 ms →        5.16 ms   (-0.34%) |       2   →       2              |       10.36 ms →       10.32 ms   (-0.34%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.56 ms →        4.49 ms   (-1.55%) |       1   →       1              |        4.56 ms →        4.49 ms   (-1.55%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.81 ms →       21.83 ms   (+0.10%) |       2   →       2              |       43.61 ms →       43.65 ms   (+0.10%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.83 ms →       14.81 ms   (-0.18%) |       2   →       2              |       29.66 ms →       29.61 ms   (-0.18%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.79 ms →       19.75 ms   (-0.17%) |       4   →       4              |       79.16 ms →       79.02 ms   (-0.17%) | 
  │   ├ sddk::Gvec::init                                                |      172.27 ms →      172.82 ms   (+0.32%) |       2   →       2              |      344.53 ms →      345.64 ms   (+0.32%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      129.99 ms →      130.07 ms   (+0.06%) |       2   →       2              |      259.97 ms →      260.14 ms   (+0.06%) | 
  │   ├ sddk::Gvec_shells                                               |      172.61 ms →      183.93 ms   (+6.56%) |       1   →       1              |      172.61 ms →      183.93 ms   (+6.56%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.31 ms →        1.36 ms   (+3.56%) |       1   →       1              |        1.31 ms →        1.36 ms   (+3.56%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      294.02 ms →      297.22 ms   (+1.09%) |       2   →       2              |      588.03 ms →      594.44 ms   (+1.09%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       74.52 ms →       75.76 ms   (+1.67%) |       1   →       1              |       74.52 ms →       75.76 ms   (+1.67%) | 
  │ ├ sirius::K_point::K_point                                          |        2.95 μs →        2.68 μs   (-9.36%) |       4   →       4              |       11.81 μs →       10.71 μs   (-9.36%) | 
  │ └ sirius::K_point_set::initialize                                   |       74.40 ms →       75.66 ms   (+1.69%) |       1   →       1              |       74.40 ms →       75.66 ms   (+1.69%) | 
  │   └ sirius::K_point::initialize                                     |       18.59 ms →       18.89 ms   (+1.64%) |       4   →       4              |       74.35 ms →       75.58 ms   (+1.64%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       14.02 ms →       14.33 ms   (+2.25%) |       4   →       4              |       56.08 ms →       57.34 ms   (+2.25%) | 
  │     │ └ sddk::Gvec::init                                            |        3.84 ms →        3.87 ms   (+1.03%) |       4   →       4              |       15.34 ms →       15.50 ms   (+1.03%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        9.04 μs →        9.07 μs   (+0.36%) |       4   →       4              |       36.16 μs →       36.29 μs   (+0.36%) | 
  │     └ sirius::K_point::update                                       |        3.26 ms →        3.27 ms   (+0.56%) |       4   →       4              |       13.02 ms →       13.09 ms   (+0.56%) | 
  │       └ sirius::Beta_projectors                                     |        1.75 ms →        1.74 ms   (-0.45%) |       4   →       4              |        7.01 ms →        6.98 ms   (-0.45%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      930.17 μs →      922.40 μs   (-0.84%) |       4   →       4              |        3.72 ms →        3.69 ms   (-0.84%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.18 ms →        5.30 ms   (+2.23%) |       2   →       2              |       10.36 ms →       10.59 ms   (+2.23%) | 
  ├ sirius::Potential                                                   |      159.69 ms →      158.94 ms   (-0.47%) |       1   →       1              |      159.69 ms →      158.94 ms   (-0.47%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.77 ms →        5.74 ms   (-0.62%) |       6   →       6              |       34.64 ms →       34.42 ms   (-0.62%) | 
  │ └ sirius::Potential::update                                         |      124.34 ms →      123.79 ms   (-0.44%) |       1   →       1              |      124.34 ms →      123.79 ms   (-0.44%) | 
  │   └ sirius::Potential::generate_local_potential                     |      123.60 ms →      123.05 ms   (-0.45%) |       1   →       1              |      123.60 ms →      123.05 ms   (-0.45%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      114.59 ms →      111.04 ms   (-3.10%) |       1   →       1              |      114.59 ms →      111.04 ms   (-3.10%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        8.11 ms →       11.11 ms  (+37.11%) |       1   →       1              |        8.11 ms →       11.11 ms  (+37.11%) | 
  ├ sirius::Density                                                     |      135.35 ms →      134.43 ms   (-0.68%) |       1   →       1              |      135.35 ms →      134.43 ms   (-0.68%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.11 ms →        5.11 ms   (+0.17%) |       2   →       2              |       10.21 ms →       10.23 ms   (+0.17%) | 
  │ └ sirius::Density::update                                           |      124.87 ms →      123.93 ms   (-0.75%) |       1   →       1              |      124.87 ms →      123.93 ms   (-0.75%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      124.46 ms →      123.52 ms   (-0.75%) |       1   →       1              |      124.46 ms →      123.52 ms   (-0.75%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |      105.41 μs →      103.00 μs   (-2.29%) |       1   →       1              |      105.41 μs →      103.00 μs   (-2.29%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      118.18 ms →      112.76 ms   (-4.59%) |       1   →       1              |      118.18 ms →      112.76 ms   (-4.59%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        5.73 ms →       10.22 ms  (+78.31%) |       1   →       1              |        5.73 ms →       10.22 ms  (+78.31%) | 
  ├ sirius::Density::initial_density                                    |      175.22 ms →      174.26 ms   (-0.55%) |       1   →       1              |      175.22 ms →      174.26 ms   (-0.55%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      122.90 ms →      110.97 ms   (-9.70%) |       1   →       1              |      122.90 ms →      110.97 ms   (-9.70%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.87 ms →       10.34 ms (+112.24%) |       2   →       2              |        9.75 ms →       20.68 ms (+112.24%) | 
  │ └ sirius::Periodic_function::integrate                              |        9.98 ms →       10.01 ms   (+0.29%) |       1   →       1              |        9.98 ms →       10.01 ms   (+0.29%) | 
  ├ sirius::Potential::generate                                         |      591.67 ms →      591.00 ms   (-0.11%) |       1   →       1              |      591.67 ms →      591.00 ms   (-0.11%) | 
  │ ├ sirius::Potential::poisson                                        |      137.98 ms →      136.11 ms   (-1.36%) |       1   →       1              |      137.98 ms →      136.11 ms   (-1.36%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.17 ms →       15.55 ms (+200.57%) |       1   →       1              |        5.17 ms →       15.55 ms (+200.57%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.92 ms →        9.95 ms   (-8.82%) |       1   →       1              |       10.92 ms →        9.95 ms   (-8.82%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        9.96 ms →        9.92 ms   (-0.44%) |       1   →       1              |        9.96 ms →        9.92 ms   (-0.44%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.96 ms →        9.92 ms   (-0.44%) |       1   →       1              |        9.96 ms →        9.92 ms   (-0.44%) | 
  │ ├ sirius::Periodic_function::add                                    |      563.29 μs →      547.05 μs   (-2.88%) |       2   →       2              |        1.13 ms →        1.09 ms   (-2.88%) | 
  │ ├ sirius::Potential::xc                                             |       53.62 ms →       54.51 ms   (+1.67%) |       1   →       1              |       53.62 ms →       54.51 ms   (+1.67%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.27 ms →       52.22 ms   (+1.85%) |       1   →       1              |       51.27 ms →       52.22 ms   (+1.85%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.61 ms →        5.67 ms   (+1.16%) |       2   →       2              |       11.21 ms →       11.34 ms   (+1.16%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.26 ms →        5.43 ms   (+3.25%) |       1   →       1              |        5.26 ms →        5.43 ms   (+3.25%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.73 ms →        5.88 ms   (+2.52%) |       1   →       1              |        5.73 ms →        5.88 ms   (+2.52%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.58 ms →       92.89 ms   (+0.33%) |       1   →       1              |       92.58 ms →       92.89 ms   (+0.33%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      299.28 ms →      299.18 ms   (-0.04%) |       1   →       1              |      299.28 ms →      299.18 ms   (-0.04%) | 
  ├ sirius::Hamiltonian0                                                |        8.53 ms →        8.33 ms   (-2.32%) |       1   →       1              |        8.53 ms →        8.33 ms   (-2.32%) | 
  │ ├ sirius::Local_operator                                            |        8.18 ms →        7.99 ms   (-2.35%) |       1   →       1              |        8.18 ms →        7.99 ms   (-2.35%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.67 ms →        4.68 ms   (+0.21%) |       1   →       1              |        4.67 ms →        4.68 ms   (+0.21%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.61 ms →        2.40 ms   (-8.10%) |       1   →       1              |        2.61 ms →        2.40 ms   (-8.10%) | 
  │ ├ sirius::Non_local_operator                                        |       63.28 μs →       63.38 μs   (+0.16%) |       2   →       2              |      126.56 μs →      126.76 μs   (+0.16%) | 
  │ ├ sirius::D_operator::initialize                                    |       94.19 μs →       90.64 μs   (-3.78%) |       1   →       1              |       94.19 μs →       90.64 μs   (-3.78%) | 
  │ └ sirius::Q_operator::initialize                                    |       69.47 μs →       68.15 μs   (-1.90%) |       1   →       1              |       69.47 μs →       68.15 μs   (-1.90%) | 
  ├ sirius::Band::initialize_subspace                                   |        3.09 s  →        3.10 s    (+0.28%) |       1   →       1              |        3.09 s  →        3.10 s    (+0.28%) | 
  │ ├ sirius::Hamiltonian_k                                             |      373.04 μs →      368.29 μs   (-1.27%) |       4   →       4              |        1.49 ms →        1.47 ms   (-1.27%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      368.28 μs →      363.63 μs   (-1.26%) |       4   →       4              |        1.47 ms →        1.45 ms   (-1.26%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        3.00 μs →        3.09 μs   (+2.82%) |       4   →       4              |       12.01 μs →       12.35 μs   (+2.82%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |      771.96 ms →      774.15 ms   (+0.28%) |       4   →       4              |        3.09 s  →        3.10 s    (+0.28%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       32.38 ms →       32.40 ms   (+0.07%) |      16   →      16              |      518.06 ms →      518.42 ms   (+0.07%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       14.45 ms →       14.49 ms   (+0.30%) |       4   →       4              |       57.80 ms →       57.97 ms   (+0.30%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        5.28 ms →        5.30 ms   (+0.34%) |       4   →       4              |       21.11 ms →       21.18 ms   (+0.34%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      351.63 ms →      355.57 ms   (+1.12%) |       4   →       4              |        1.41 s  →        1.42 s    (+1.12%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      255.35 ms →      258.16 ms   (+1.10%) |       4   →       4              |        1.02 s  →        1.03 s    (+1.10%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       61.83 ms →       62.91 ms   (+1.75%) |       4   →       4              |      247.32 ms →      251.65 ms   (+1.75%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       16.53 ms →       16.29 ms   (-1.41%) |       4   →       4              |       66.10 ms →       65.17 ms   (-1.41%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       16.52 ms →       16.29 ms   (-1.41%) |       4   →       4              |       66.09 ms →       65.16 ms   (-1.41%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       38.81 ms →       40.13 ms   (+3.42%) |       4   →       4              |      155.24 ms →      160.54 ms   (+3.42%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |       16.24 ms →       16.24 ms   (+0.01%) |       4   →       4              |       64.94 ms →       64.95 ms   (+0.01%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |       16.23 ms →       16.23 ms   (+0.01%) |       4   →       4              |       64.93 ms →       64.93 ms   (+0.01%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |       53.41 ms →       55.05 ms   (+3.07%) |       4   →       4              |      213.64 ms →      220.20 ms   (+3.07%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |       35.37 ms →       37.02 ms   (+4.68%) |       4   →       4              |      141.46 ms →      148.08 ms   (+4.68%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        1.95 ms →        1.94 ms   (-0.74%) |       4   →       4              |        7.81 ms →        7.75 ms   (-0.74%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       40.20 ms →       41.19 ms   (+2.46%) |       4   →       4              |      160.79 ms →      164.75 ms   (+2.46%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |        7.13 ms →        8.11 ms  (+13.74%) |       4   →       4              |       28.51 ms →       32.42 ms  (+13.74%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       27.05 ms →       27.13 ms   (+0.28%) |       8   →       8              |      216.39 ms →      217.00 ms   (+0.28%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       15.16 ms →       15.10 ms   (-0.38%) |       8   →       8              |      121.25 ms →      120.79 ms   (-0.38%) | 
  │ │ │ └ sddk::wf_inner                                                |       15.11 ms →       15.06 ms   (-0.37%) |       8   →       8              |      120.90 ms →      120.45 ms   (-0.37%) | 
  │ │ │   ├ sddk::wf_inner|scale                                        |       36.13 ns →       38.75 ns   (+7.27%) |       8   →       8              |      289.00 ns →      310.00 ns   (+7.27%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       14.94 ms →       14.89 ms   (-0.35%) |       8   →       8              |      119.52 ms →      119.10 ms   (-0.35%) | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |       26.37 ns →       24.13 ns   (-8.53%) |       8   →       8              |      211.00 ns →      193.00 ns   (-8.53%) | 
  │ │ ├ Eigensolver_scalapack|pzhegvx                                   |      122.75 ms →      121.81 ms   (-0.76%) |       4   →       4              |      491.00 ms →      487.25 ms   (-0.76%) | 
  │ │ └ sddk::wf_trans                                                  |       23.56 ms →       23.68 ms   (+0.50%) |       4   →       4              |       94.25 ms →       94.71 ms   (+0.50%) | 
  │ │   └ sddk::wf_trans|pw                                             |       23.34 ms →       23.42 ms   (+0.36%) |       4   →       4              |       93.36 ms →       93.69 ms   (+0.36%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      447.50 ns →      339.00 ns  (-24.25%) |       4   →       4              |        1.79 μs →        1.36 μs  (-24.25%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      236.07 s  →      213.35 s    (-9.62%) |       1   →       1              |      236.07 s  →      213.35 s    (-9.62%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.65 ms →        5.67 ms   (+0.37%) |      19   →      19              |      107.29 ms →      107.69 ms   (+0.37%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        8.73 s  →        7.89 s    (-9.63%) |      27   →      27              |      235.70 s  →      212.99 s    (-9.63%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        4.66 ms →        4.61 ms   (-1.07%) |      27   →      27              |      125.87 ms →      124.51 ms   (-1.07%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.31 ms →        4.26 ms   (-1.22%) |      27   →      27              |      116.32 ms →      114.91 ms   (-1.22%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      959.64 μs →      983.36 μs   (+2.47%) |      27   →      27              |       25.91 ms →       26.55 ms   (+2.47%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.46 ms →        2.39 ms   (-3.07%) |      27   →      27              |       66.52 ms →       64.48 ms   (-3.07%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.44 μs →       64.46 μs   (+0.04%) |      54   →      54              |        3.48 ms →        3.48 ms   (+0.04%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       91.43 μs →       93.38 μs   (+2.14%) |      27   →      27              |        2.47 ms →        2.52 ms   (+2.14%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       65.47 μs →       65.29 μs   (-0.28%) |      27   →      27              |        1.77 ms →        1.76 ms   (-0.28%) | 
+ │ │ ├ sirius::Band::solve                                             |        6.64 s  →        5.80 s   (-12.67%) |      27   →      27              |      179.19 s  →      156.48 s   (-12.67%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      331.59 μs →      324.28 μs   (-2.21%) |     108   →     108              |       35.81 ms →       35.02 ms   (-2.21%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      326.13 μs →      319.05 μs   (-2.17%) |     108   →     108              |       35.22 ms →       34.46 ms   (-2.17%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        3.94 μs →        3.79 μs   (-3.85%) |     108   →     108              |      425.39 μs →      409.03 μs   (-3.85%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.66 s  →        1.45 s   (-12.67%) |     108   →     108              |      179.15 s  →      156.45 s   (-12.67%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       12.01 ms →       12.09 ms   (+0.71%) |     108   →     108              |        1.30 s  →        1.31 s    (+0.71%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |      653.26 ns →      705.76 ns   (+8.04%) |     648   →     648              |      423.31 μs →      457.33 μs   (+8.04%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.82 ms →        1.83 ms   (+0.51%) |     108   →     108              |      196.81 ms →      197.81 ms   (+0.51%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      352.12 μs →      355.14 μs   (+0.86%) |     108   →     108              |       38.03 ms →       38.36 ms   (+0.86%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      547.07 μs →      549.81 μs   (+0.50%) |     216   →     216              |      118.17 ms →      118.76 ms   (+0.50%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.64 s  →        1.43 s   (-12.86%) |     108   →     108              |      176.68 s  →      153.96 s   (-12.86%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       68.86 ms →       68.21 ms   (-0.94%) |     926   →     979     (+5.72%) |       63.77 s  →       66.78 s    (+4.73%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       43.80 ms →       43.52 ms   (-0.65%) |     926   →     979     (+5.72%) |       40.56 s  →       42.61 s    (+5.04%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        8.33 ms →        8.65 ms   (+3.88%) |     926   →     979     (+5.72%) |        7.71 s  →        8.47 s    (+9.82%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      227.77 μs →      215.02 μs   (-5.60%) |     926   →     979     (+5.72%) |      210.91 ms →      210.50 ms   (-0.19%) | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        1.94 ms →        1.93 ms   (-0.19%) |     108   →     108              |      209.12 ms →      208.73 ms   (-0.19%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |        6.51 ms →        6.67 ms   (+2.47%) |     926   →     979     (+5.72%) |        6.03 s  →        6.53 s    (+8.34%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |       87.52 μs →       83.32 μs   (-4.81%) |     926   →     979     (+5.72%) |       81.05 ms →       81.57 ms   (+0.64%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |      727.98 μs →      732.48 μs   (+0.62%) |     108   →     108              |       78.62 ms →       79.11 ms   (+0.62%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |        9.45 ms →        9.61 ms   (+1.79%) |     926   →     979     (+5.72%) |        8.75 s  →        9.41 s    (+7.61%) | 
- │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |        5.82 ms →        6.10 ms   (+4.80%) |     926   →     979     (+5.72%) |        5.39 s  →        5.97 s   (+10.79%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        1.52 ms →        1.52 ms   (-0.18%) |     926   →     979     (+5.72%) |        1.41 s  →        1.49 s    (+5.54%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        8.66 ms →        8.51 ms   (-1.75%) |     926   →     979     (+5.72%) |        8.02 s  →        8.33 s    (+3.87%) | 
- │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        1.33 ms →        1.40 ms   (+4.74%) |     926   →     979     (+5.72%) |        1.24 s  →        1.37 s   (+10.74%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.42 ms →        7.32 ms   (-1.41%) |    1.85 K →    1.96 K   (+5.72%) |       13.75 s  →       14.33 s    (+4.23%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       27.81 ms →       26.58 ms   (-4.41%) |     926   →     979     (+5.72%) |       25.75 s  →       26.03 s    (+1.06%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        2.04 ms →        1.96 ms   (-3.91%) |    1.74 K →    1.85 K   (+6.08%) |        3.56 s  →        3.63 s    (+1.94%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       76.31 ns →       61.50 ns  (-19.41%) |    1.74 K →    1.85 K   (+6.08%) |      133.08 μs →      113.77 μs  (-14.51%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        2.03 ms →        1.95 ms   (-4.03%) |    1.74 K →    1.85 K   (+6.08%) |        3.55 s  →        3.61 s    (+1.80%) | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       61.66 ns →       60.95 ns   (-1.14%) |    1.74 K →    1.85 K   (+6.08%) |      107.53 μs →      112.76 μs   (+4.87%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|potrf                               |      796.90 μs →      804.79 μs   (+0.99%) |     926   →     979     (+5.72%) |      737.93 ms →      787.89 ms   (+6.77%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|trtri                               |      781.32 μs →      747.08 μs   (-4.38%) |     926   →     979     (+5.72%) |      723.50 ms →      731.39 ms   (+1.09%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |        5.37 ms →        5.09 ms   (-5.21%) |    3.60 K →    3.81 K   (+5.90%) |       19.29 s  →       19.37 s    (+0.38%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        3.65 ms →        3.45 ms   (-5.38%) |    5.23 K →    5.55 K   (+6.08%) |       19.09 s  →       19.16 s    (+0.38%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        5.36 ms →        5.23 ms   (-2.43%) |     926   →     979     (+5.72%) |        4.96 s  →        5.12 s    (+3.16%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |        3.67 ms →        3.50 ms   (-4.41%) |     926   →     979     (+5.72%) |        3.39 s  →        3.43 s    (+1.06%) | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       58.14 ns →       55.47 ns   (-4.59%) |     926   →     979     (+5.72%) |       53.84 μs →       54.31 μs   (+0.87%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        3.65 ms →        3.49 ms   (-4.39%) |     926   →     979     (+5.72%) |        3.38 s  →        3.42 s    (+1.08%) | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       57.13 ns →       54.90 ns   (-3.91%) |     926   →     979     (+5.72%) |       52.90 μs →       53.74 μs   (+1.59%) | 
+ │ │ │ │   ├ Eigensolver_scalapack|pzheevx                             |       66.41 ms →       34.98 ms  (-47.33%) |     926   →     979     (+5.72%) |       61.50 s  →       34.25 s   (-44.31%) | 
+ │ │ │ │   ├ sirius::residuals                                         |       10.88 ms →        9.59 ms  (-11.86%) |     905   →     951     (+5.08%) |        9.85 s  →        9.12 s    (-7.38%) | 
+ │ │ │ │   │ ├ sddk::wf_trans                                          |       10.51 ms →        9.15 ms  (-12.96%) |     859   →     908     (+5.70%) |        9.03 s  →        8.31 s    (-7.99%) | 
+ │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        5.22 ms →        4.54 ms  (-12.92%) |    1.72 K →    1.82 K   (+5.70%) |        8.96 s  →        8.25 s    (-7.95%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      645.04 μs →      616.19 μs   (-4.47%) |     859   →     908     (+5.70%) |      554.09 ms →      559.50 ms   (+0.98%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       50.80 ms →       36.65 ms  (-27.86%) |     213   →     345    (+61.97%) |       10.82 s  →       12.64 s   (+16.85%) | 
- │ │ │ │     └ sddk::wf_trans                                          |       33.92 ms →       21.60 ms  (-36.32%) |     318   →     582    (+83.02%) |       10.79 s  →       12.57 s   (+16.55%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |       25.35 ms →       15.24 ms  (-39.86%) |     423   →     819    (+93.62%) |       10.72 s  →       12.48 s   (+16.44%) | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      526.87 ns →      533.07 ns   (+1.18%) |     108   →     108              |       56.90 μs →       57.57 μs   (+1.18%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       21.00 μs →       21.54 μs   (+2.60%) |      27   →      27              |      566.89 μs →      581.61 μs   (+2.60%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      586.57 μs →      592.70 μs   (+1.05%) |      27   →      27              |       15.84 ms →       16.00 ms   (+1.05%) | 
  │ │ ├ sirius::Density::generate                                       |      887.71 ms →      893.43 ms   (+0.64%) |      27   →      27              |       23.97 s  →       24.12 s    (+0.64%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      520.61 ms →      527.13 ms   (+1.25%) |      27   →      27              |       14.06 s  →       14.23 s    (+1.25%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       23.34 ms →       24.32 ms   (+4.22%) |     108   →     108              |        2.52 s  →        2.63 s    (+4.22%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |        8.48 μs →        8.70 μs   (+2.59%) |     108   →     108              |      916.38 μs →      940.11 μs   (+2.59%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       14.97 μs →       15.88 μs   (+6.11%) |       8   →       8              |      119.75 μs →      127.07 μs   (+6.11%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       19.22 ms →       20.20 ms   (+5.10%) |     108   →     108              |        2.08 s  →        2.18 s    (+5.10%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       29.83 ms →       30.17 ms   (+1.13%) |     108   →     108              |        3.22 s  →        3.26 s    (+1.13%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.50 μs →        9.79 μs   (+3.11%) |     108   →     108              |        1.03 ms →        1.06 ms   (+3.11%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        1.46 ms →        1.45 ms   (-0.30%) |     108   →     108              |      157.44 ms →      156.96 ms   (-0.30%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       27.89 ms →       28.24 ms   (+1.24%) |     108   →     108              |        3.01 s  →        3.05 s    (+1.24%) | 
  │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        3.76 ms →        4.11 ms   (+9.24%) |     108   →     108              |      406.29 ms →      443.84 ms   (+9.24%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      586.78 ns →      681.23 ns  (+16.10%) |     108   →     108              |       63.37 μs →       73.57 μs  (+16.10%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       42.70 ms →       42.77 ms   (+0.17%) |     108   →     108              |        4.61 s  →        4.62 s    (+0.17%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.64 ms   (-0.02%) |      27   →      27              |       44.27 ms →       44.27 ms   (-0.02%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.84 ms →       88.85 ms   (+0.02%) |      27   →      27              |        2.40 s  →        2.40 s    (+0.02%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.60 ms →       88.62 ms   (+0.02%) |      27   →      27              |        2.39 s  →        2.39 s    (+0.02%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      275.27 ms →      274.94 ms   (-0.12%) |      27   →      27              |        7.43 s  →        7.42 s    (-0.12%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      275.27 ms →      274.94 ms   (-0.12%) |      27   →      27              |        7.43 s  →        7.42 s    (-0.12%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.35 ms →       24.68 ms   (+1.36%) |      27   →      27              |      657.53 ms →      666.48 ms   (+1.36%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      225.23 ms →      224.39 ms   (-0.37%) |      27   →      27              |        6.08 s  →        6.06 s    (-0.37%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       23.94 ms →       24.10 ms   (+0.66%) |      27   →      27              |      646.39 ms →      650.64 ms   (+0.66%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       81.35 ms →       80.69 ms   (-0.82%) |      27   →      27              |        2.20 s  →        2.18 s    (-0.82%) | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        6.86 ms →        7.07 ms   (+3.00%) |      27   →      27              |      185.33 ms →      190.90 ms   (+3.00%) | 
  │ │ ├ sirius::Density::mix                                            |      220.89 ms →      215.21 ms   (-2.57%) |      27   →      27              |        5.96 s  →        5.81 s    (-2.57%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      944.74 μs →      928.04 μs   (-1.77%) |      27   →      27              |       25.51 ms →       25.06 ms   (-1.77%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.77 ms →       10.33 ms   (-4.06%) |     349   →     349              |        3.76 s  →        3.60 s    (-4.06%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.39 ms →       10.01 ms   (-3.63%) |     349   →     349              |        3.63 s  →        3.49 s    (-3.63%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.39 ms →       10.01 ms   (-3.63%) |     349   →     349              |        3.63 s  →        3.49 s    (-3.63%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        6.42 ms →        6.31 ms   (-1.74%) |      27   →      27              |      173.28 ms →      170.26 ms   (-1.74%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.57 ms →        5.43 ms   (-2.49%) |      27   →      27              |      150.47 ms →      146.72 ms   (-2.49%) | 
  │ │ ├ sirius::Potential::generate                                     |      579.08 ms →      578.11 ms   (-0.17%) |      27   →      27              |       15.64 s  →       15.61 s    (-0.17%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      137.23 ms →      136.33 ms   (-0.66%) |      27   →      27              |        3.71 s  →        3.68 s    (-0.66%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        5.11 ms →       15.27 ms (+198.92%) |      27   →      27              |      137.96 ms →      412.40 ms (+198.92%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.33 ms →       10.31 ms   (-0.15%) |      27   →      27              |      278.85 ms →      278.42 ms   (-0.15%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.05 ms →       10.06 ms   (+0.12%) |      27   →      27              |      271.35 ms →      271.69 ms   (+0.12%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.05 ms →       10.06 ms   (+0.12%) |      27   →      27              |      271.34 ms →      271.67 ms   (+0.12%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      552.07 μs →      547.63 μs   (-0.80%) |      54   →      54              |       29.81 ms →       29.57 ms   (-0.80%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       49.25 ms →       48.94 ms   (-0.64%) |      27   →      27              |        1.33 s  →        1.32 s    (-0.64%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.91 ms →       46.57 ms   (-0.73%) |      27   →      27              |        1.27 s  →        1.26 s    (-0.73%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.02 ms →        3.05 ms   (+0.84%) |      54   →      54              |      163.10 ms →      164.47 ms   (+0.84%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.38 ms →        5.31 ms   (-1.31%) |      27   →      27              |      145.33 ms →      143.42 ms   (-1.31%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.57 ms →        6.60 ms   (+0.58%) |      27   →      27              |      177.30 ms →      178.33 ms   (+0.58%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.86 ms →       91.03 ms   (+0.19%) |      27   →      27              |        2.45 s  →        2.46 s    (+0.19%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      292.79 ms →      292.81 ms   (+0.01%) |      27   →      27              |        7.91 s  →        7.91 s    (+0.01%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      277.93 ms →      279.51 ms   (+0.57%) |      27   →      27              |        7.50 s  →        7.55 s    (+0.57%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      277.92 ms →      279.51 ms   (+0.57%) |      27   →      27              |        7.50 s  →        7.55 s    (+0.57%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.03 ms →       27.28 ms   (+0.93%) |      27   →      27              |      729.71 ms →      736.48 ms   (+0.93%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      223.30 ms →      224.77 ms   (+0.66%) |      27   →      27              |        6.03 s  →        6.07 s    (+0.66%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.82 ms →       23.67 ms   (-0.62%) |      27   →      27              |      643.13 ms →      639.15 ms   (-0.62%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.74 ms →        5.67 ms   (-1.32%) |      27   →      27              |      155.06 ms →      153.02 ms   (-1.32%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.36 ms →       10.43 ms   (+0.65%) |     189   →     189              |        1.96 s  →        1.97 s    (+0.65%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.88 ms →        9.90 ms   (+0.26%) |     189   →     189              |        1.87 s  →        1.87 s    (+0.26%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.88 ms →        9.90 ms   (+0.26%) |     189   →     189              |        1.87 s  →        1.87 s    (+0.26%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       11.11 ms →       10.77 ms   (-3.03%) |      81   →      81              |      899.76 ms →      872.53 ms   (-3.03%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.67 ms →       10.24 ms   (-3.95%) |      81   →      81              |      863.87 ms →      829.75 ms   (-3.95%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |       10.06 ms →       10.17 ms   (+1.01%) |      27   →      27              |      271.75 ms →      274.48 ms   (+1.01%) | 
  │ │ └ sirius::Density::get_magnetisation                              |      126.56 μs →      114.90 μs   (-9.21%) |      27   →      27              |        3.42 ms →        3.10 ms   (-9.21%) | 
+ │ │   └ sirius::Density::compute_atomic_mag_mom                       |      121.52 μs →      109.33 μs  (-10.03%) |      27   →      27              |        3.28 ms →        2.95 ms  (-10.03%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.23 ms →        5.04 ms   (-3.59%) |       2   →       2              |       10.46 ms →       10.09 ms   (-3.59%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.01 ms →       10.30 ms   (+2.90%) |       6   →       6              |       60.08 ms →       61.83 ms   (+2.90%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        9.72 ms →        9.93 ms   (+2.21%) |       6   →       6              |       58.30 ms →       59.58 ms   (+2.21%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        9.72 ms →        9.93 ms   (+2.21%) |       6   →       6              |       58.29 ms →       59.58 ms   (+2.21%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.78 ms →       10.46 ms   (-2.92%) |       3   →       3              |       32.33 ms →       31.38 ms   (-2.92%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.49 ms →       10.25 ms   (-2.23%) |       3   →       3              |       31.46 ms →       30.76 ms   (-2.23%) | 
  ├ sirius::Periodic_function|inner                                     |        9.96 ms →        9.94 ms   (-0.13%) |       2   →       2              |       19.91 ms →       19.88 ms   (-0.13%) | 
  │ └ sirius::Periodic_function|inner_local                             |        9.69 ms →        9.66 ms   (-0.29%) |       2   →       2              |       19.38 ms →       19.33 ms   (-0.29%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.69 ms →        9.66 ms   (-0.29%) |       2   →       2              |       19.38 ms →       19.32 ms   (-0.29%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.78 ms →       10.14 ms   (-5.98%) |       1   →       1              |       10.78 ms →       10.14 ms   (-5.98%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.46 ms →       10.10 ms   (-3.48%) |       1   →       1              |       10.46 ms →       10.10 ms   (-3.48%) | 
+ └ sirius::finalize                                                    |      326.59 ms →      274.24 ms  (-16.03%) |       1   →       1              |      326.59 ms →      274.24 ms  (-16.03%) | 
  ====================================================================================================================================================================================================
```
