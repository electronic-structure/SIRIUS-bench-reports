# Benchmark 392f68b5626168134a99cd6d4a3cc40b87322cb7 vs 4abe991ed1b67a61e2f44af0d6336c92b3f43afd
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      224.71 s  →      219.09 s    (-2.50%) |       1   →       1              |      224.71 s  →      219.09 s    (-2.50%) | 
  ├ sirius::initialize                                                  |        2.64 s  →        2.63 s    (-0.46%) |       1   →       1              |        2.64 s  →        2.63 s    (-0.46%) | 
  ├ sirius::Simulation_context::initialize                              |        2.98 s  →        2.94 s    (-1.31%) |       1   →       1              |        2.98 s  →        2.94 s    (-1.31%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       34.87 ms →      386.33 μs  (-98.89%) |       1   →       1              |       34.87 ms →      386.33 μs  (-98.89%) | 
  │ ├ sirius::Unit_cell::initialize                                     |      172.04 ms →      168.83 ms   (-1.87%) |       1   →       1              |      172.04 ms →      168.83 ms   (-1.87%) | 
  │ │ ├ sirius::Atom_type::init                                         |       74.63 ms →       73.12 ms   (-2.02%) |       2   →       2              |      149.26 ms →      146.25 ms   (-2.02%) | 
  │ │ └ sirius::Unit_cell::update                                       |       22.70 ms →       22.51 ms   (-0.85%) |       1   →       1              |       22.70 ms →       22.51 ms   (-0.85%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.34 ms →        6.33 ms   (-0.15%) |       1   →       1              |        6.34 ms →        6.33 ms   (-0.15%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       16.32 ms →       16.14 ms   (-1.11%) |       1   →       1              |       16.32 ms →       16.14 ms   (-1.11%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       16.29 ms →       16.11 ms   (-1.11%) |       1   →       1              |       16.29 ms →       16.11 ms   (-1.11%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.14 ms →        4.14 ms   (+0.04%) |       1   →       1              |        4.14 ms →        4.14 ms   (+0.04%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.30 ms →        2.34 ms   (+1.71%) |       1   →       1              |        2.30 ms →        2.34 ms   (+1.71%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      107.48 μs →      110.75 μs   (+3.03%) |       1   →       1              |      107.48 μs →      110.75 μs   (+3.03%) | 
  │ └ sirius::Simulation_context::update                                |        2.72 s  →        2.72 s    (-0.02%) |       1   →       1              |        2.72 s  →        2.72 s    (-0.02%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.76 ms →       10.71 ms   (-0.47%) |       1   →       1              |       10.76 ms →       10.71 ms   (-0.47%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.38 ms →        4.28 ms   (-2.39%) |       1   →       1              |        4.38 ms →        4.28 ms   (-2.39%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.34 ms →        6.40 ms   (+0.85%) |       1   →       1              |        6.34 ms →        6.40 ms   (+0.85%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.32 ms →        6.38 ms   (+0.85%) |       1   →       1              |        6.32 ms →        6.38 ms   (+0.85%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.82 ms →        3.88 ms   (+1.66%) |       1   →       1              |        3.82 ms →        3.88 ms   (+1.66%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.32 ms   (-0.38%) |       1   →       1              |        2.33 ms →        2.32 ms   (-0.38%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      111.23 μs →      110.17 μs   (-0.96%) |       1   →       1              |      111.23 μs →      110.17 μs   (-0.96%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       62.66 ms →       62.60 ms   (-0.10%) |       2   →       2              |      125.33 ms →      125.21 ms   (-0.10%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.16 ms →        5.13 ms   (-0.51%) |       2   →       2              |       10.32 ms →       10.27 ms   (-0.51%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.46 ms →        4.48 ms   (+0.30%) |       1   →       1              |        4.46 ms →        4.48 ms   (+0.30%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.77 ms →       21.77 ms   (-0.00%) |       2   →       2              |       43.53 ms →       43.53 ms   (-0.00%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.80 ms →       14.80 ms   (+0.00%) |       2   →       2              |       29.61 ms →       29.61 ms   (+0.00%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.84 ms →       19.72 ms   (-0.63%) |       4   →       4              |       79.36 ms →       78.86 ms   (-0.63%) | 
  │   ├ sddk::Gvec::init                                                |      171.37 ms →      175.58 ms   (+2.45%) |       2   →       2              |      342.74 ms →      351.15 ms   (+2.45%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      128.59 ms →      132.32 ms   (+2.90%) |       2   →       2              |      257.18 ms →      264.64 ms   (+2.90%) | 
  │   ├ sddk::Gvec_shells                                               |      177.27 ms →      189.57 ms   (+6.93%) |       1   →       1              |      177.27 ms →      189.57 ms   (+6.93%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.33 ms →        1.32 ms   (-0.97%) |       1   →       1              |        1.33 ms →        1.32 ms   (-0.97%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      294.67 ms →      293.80 ms   (-0.29%) |       2   →       2              |      589.34 ms →      587.60 ms   (-0.29%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       76.77 ms →       75.55 ms   (-1.58%) |       1   →       1              |       76.77 ms →       75.55 ms   (-1.58%) | 
- │ ├ sirius::K_point::K_point                                          |        2.00 μs →        2.59 μs  (+29.31%) |       4   →       4              |        8.01 μs →       10.35 μs  (+29.31%) | 
  │ └ sirius::K_point_set::initialize                                   |       76.67 ms →       75.45 ms   (-1.59%) |       1   →       1              |       76.67 ms →       75.45 ms   (-1.59%) | 
  │   └ sirius::K_point::initialize                                     |       19.15 ms →       18.84 ms   (-1.59%) |       4   →       4              |       76.58 ms →       75.37 ms   (-1.59%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       14.52 ms →       14.22 ms   (-2.04%) |       4   →       4              |       58.08 ms →       56.90 ms   (-2.04%) | 
  │     │ └ sddk::Gvec::init                                            |        3.90 ms →        3.85 ms   (-1.22%) |       4   →       4              |       15.60 ms →       15.41 ms   (-1.22%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        9.13 μs →        8.94 μs   (-2.13%) |       4   →       4              |       36.54 μs →       35.76 μs   (-2.13%) | 
  │     └ sirius::K_point::update                                       |        3.30 ms →        3.33 ms   (+0.84%) |       4   →       4              |       13.20 ms →       13.32 ms   (+0.84%) | 
  │       └ sirius::Beta_projectors                                     |        1.76 ms →        1.80 ms   (+2.49%) |       4   →       4              |        7.03 ms →        7.21 ms   (+2.49%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      924.94 μs →      936.43 μs   (+1.24%) |       4   →       4              |        3.70 ms →        3.75 ms   (+1.24%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.22 ms →        5.17 ms   (-0.93%) |       2   →       2              |       10.44 ms →       10.35 ms   (-0.93%) | 
  ├ sirius::Potential                                                   |      156.33 ms →      159.77 ms   (+2.20%) |       1   →       1              |      156.33 ms →      159.77 ms   (+2.20%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.84 ms →        5.74 ms   (-1.78%) |       6   →       6              |       35.07 ms →       34.45 ms   (-1.78%) | 
  │ └ sirius::Potential::update                                         |      120.54 ms →      124.62 ms   (+3.39%) |       1   →       1              |      120.54 ms →      124.62 ms   (+3.39%) | 
  │   └ sirius::Potential::generate_local_potential                     |      119.74 ms →      123.90 ms   (+3.47%) |       1   →       1              |      119.74 ms →      123.90 ms   (+3.47%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      111.64 ms →      106.84 ms   (-4.30%) |       1   →       1              |      111.64 ms →      106.84 ms   (-4.30%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        7.22 ms →       16.17 ms (+123.85%) |       1   →       1              |        7.22 ms →       16.17 ms (+123.85%) | 
  ├ sirius::Density                                                     |      129.73 ms →      134.48 ms   (+3.67%) |       1   →       1              |      129.73 ms →      134.48 ms   (+3.67%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.13 ms →        5.04 ms   (-1.71%) |       2   →       2              |       10.27 ms →       10.09 ms   (-1.71%) | 
  │ └ sirius::Density::update                                           |      119.12 ms →      124.13 ms   (+4.21%) |       1   →       1              |      119.12 ms →      124.13 ms   (+4.21%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      118.69 ms →      123.72 ms   (+4.24%) |       1   →       1              |      118.69 ms →      123.72 ms   (+4.24%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |      104.00 μs →      105.48 μs   (+1.42%) |       1   →       1              |      104.00 μs →      105.48 μs   (+1.42%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      112.32 ms →      109.89 ms   (-2.16%) |       1   →       1              |      112.32 ms →      109.89 ms   (-2.16%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        5.81 ms →       13.29 ms (+128.60%) |       1   →       1              |        5.81 ms →       13.29 ms (+128.60%) | 
  ├ sirius::Density::initial_density                                    |      167.33 ms →      173.93 ms   (+3.94%) |       1   →       1              |      167.33 ms →      173.93 ms   (+3.94%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      111.59 ms →      109.17 ms   (-2.16%) |       1   →       1              |      111.59 ms →      109.17 ms   (-2.16%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.86 ms →       11.54 ms (+137.68%) |       2   →       2              |        9.71 ms →       23.09 ms (+137.68%) | 
  │ └ sirius::Periodic_function::integrate                              |       10.86 ms →        9.87 ms   (-9.05%) |       1   →       1              |       10.86 ms →        9.87 ms   (-9.05%) | 
  ├ sirius::Potential::generate                                         |      580.41 ms →      590.86 ms   (+1.80%) |       1   →       1              |      580.41 ms →      590.86 ms   (+1.80%) | 
  │ ├ sirius::Potential::poisson                                        |      126.94 ms →      136.78 ms   (+7.74%) |       1   →       1              |      126.94 ms →      136.78 ms   (+7.74%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        7.01 ms →       18.87 ms (+169.11%) |       1   →       1              |        7.01 ms →       18.87 ms (+169.11%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.71 ms →       10.26 ms   (-4.15%) |       1   →       1              |       10.71 ms →       10.26 ms   (-4.15%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |       10.22 ms →       10.01 ms   (-2.13%) |       1   →       1              |       10.22 ms →       10.01 ms   (-2.13%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |       10.22 ms →       10.01 ms   (-2.13%) |       1   →       1              |       10.22 ms →       10.01 ms   (-2.13%) | 
  │ ├ sirius::Periodic_function::add                                    |      548.35 μs →      546.97 μs   (-0.25%) |       2   →       2              |        1.10 ms →        1.09 ms   (-0.25%) | 
  │ ├ sirius::Potential::xc                                             |       53.49 ms →       53.46 ms   (-0.06%) |       1   →       1              |       53.49 ms →       53.46 ms   (-0.06%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.14 ms →       51.18 ms   (+0.07%) |       1   →       1              |       51.14 ms →       51.18 ms   (+0.07%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.70 ms →        5.66 ms   (-0.61%) |       2   →       2              |       11.39 ms →       11.32 ms   (-0.61%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.14 ms →        5.22 ms   (+1.60%) |       1   →       1              |        5.14 ms →        5.22 ms   (+1.60%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.79 ms →        5.69 ms   (-1.71%) |       1   →       1              |        5.79 ms →        5.69 ms   (-1.71%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.54 ms →       92.60 ms   (+0.07%) |       1   →       1              |       92.54 ms →       92.60 ms   (+0.07%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      299.16 ms →      299.90 ms   (+0.25%) |       1   →       1              |      299.16 ms →      299.90 ms   (+0.25%) | 
  ├ sirius::Hamiltonian0                                                |        8.65 ms →        8.36 ms   (-3.31%) |       1   →       1              |        8.65 ms →        8.36 ms   (-3.31%) | 
  │ ├ sirius::Local_operator                                            |        8.29 ms →        8.03 ms   (-3.20%) |       1   →       1              |        8.29 ms →        8.03 ms   (-3.20%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.77 ms →        4.69 ms   (-1.70%) |       1   →       1              |        4.77 ms →        4.69 ms   (-1.70%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.59 ms →        2.43 ms   (-6.20%) |       1   →       1              |        2.59 ms →        2.43 ms   (-6.20%) | 
  │ ├ sirius::Non_local_operator                                        |       64.13 μs →       62.97 μs   (-1.82%) |       2   →       2              |      128.27 μs →      125.94 μs   (-1.82%) | 
  │ ├ sirius::D_operator::initialize                                    |       97.83 μs →       90.43 μs   (-7.56%) |       1   →       1              |       97.83 μs →       90.43 μs   (-7.56%) | 
  │ └ sirius::Q_operator::initialize                                    |       73.09 μs →       68.19 μs   (-6.70%) |       1   →       1              |       73.09 μs →       68.19 μs   (-6.70%) | 
  ├ sirius::Band::initialize_subspace                                   |        3.11 s  →        3.09 s    (-0.57%) |       1   →       1              |        3.11 s  →        3.09 s    (-0.57%) | 
  │ ├ sirius::Hamiltonian_k                                             |      384.72 μs →      402.73 μs   (+4.68%) |       4   →       4              |        1.54 ms →        1.61 ms   (+4.68%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      378.57 μs →      397.63 μs   (+5.03%) |       4   →       4              |        1.51 ms →        1.59 ms   (+5.03%) | 
+ │ │ └ sirius::Beta_projectors_base::prepare                           |        4.25 μs →        3.36 μs  (-20.87%) |       4   →       4              |       16.98 μs →       13.44 μs  (-20.87%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |      777.08 ms →      772.61 ms   (-0.58%) |       4   →       4              |        3.11 s  →        3.09 s    (-0.58%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       32.49 ms →       32.89 ms   (+1.25%) |      16   →      16              |      519.77 ms →      526.28 ms   (+1.25%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       14.47 ms →       14.48 ms   (+0.03%) |       4   →       4              |       57.90 ms →       57.91 ms   (+0.03%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        5.31 ms →        5.27 ms   (-0.76%) |       4   →       4              |       21.24 ms →       21.08 ms   (-0.76%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      356.21 ms →      354.36 ms   (-0.52%) |       4   →       4              |        1.42 s  →        1.42 s    (-0.52%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      259.68 ms →      257.89 ms   (-0.69%) |       4   →       4              |        1.04 s  →        1.03 s    (-0.69%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       64.60 ms →       63.32 ms   (-1.98%) |       4   →       4              |      258.40 ms →      253.28 ms   (-1.98%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       16.36 ms →       16.66 ms   (+1.79%) |       4   →       4              |       65.46 ms →       66.63 ms   (+1.79%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       16.36 ms →       16.65 ms   (+1.78%) |       4   →       4              |       65.45 ms →       66.62 ms   (+1.78%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       41.72 ms →       40.18 ms   (-3.69%) |       4   →       4              |      166.88 ms →      160.73 ms   (-3.69%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |       16.34 ms →       16.54 ms   (+1.22%) |       4   →       4              |       65.36 ms →       66.16 ms   (+1.22%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |       16.34 ms →       16.54 ms   (+1.22%) |       4   →       4              |       65.35 ms →       66.15 ms   (+1.22%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |       53.37 ms →       54.36 ms   (+1.86%) |       4   →       4              |      213.48 ms →      217.45 ms   (+1.86%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |       35.35 ms →       36.31 ms   (+2.71%) |       4   →       4              |      141.41 ms →      145.24 ms   (+2.71%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        1.94 ms →        1.97 ms   (+1.44%) |       4   →       4              |        7.76 ms →        7.87 ms   (+1.44%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       40.16 ms →       40.13 ms   (-0.09%) |       4   →       4              |      160.65 ms →      160.50 ms   (-0.09%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |        7.01 ms →        6.96 ms   (-0.71%) |       4   →       4              |       28.03 ms →       27.83 ms   (-0.71%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       27.19 ms →       27.17 ms   (-0.09%) |       8   →       8              |      217.55 ms →      217.35 ms   (-0.09%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.78 ms →       14.80 ms   (+0.14%) |       8   →       8              |      118.28 ms →      118.44 ms   (+0.14%) | 
  │ │ │ └ sddk::wf_inner                                                |       14.74 ms →       14.76 ms   (+0.10%) |       8   →       8              |      117.94 ms →      118.06 ms   (+0.10%) | 
+ │ │ │   ├ sddk::wf_inner|scale                                        |       50.63 ns →       25.38 ns  (-49.88%) |       8   →       8              |      405.00 ns →      203.00 ns  (-49.88%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       14.57 ms →       14.57 ms   (-0.01%) |       8   →       8              |      116.54 ms →      116.52 ms   (-0.01%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       22.50 ns →       54.13 ns (+140.56%) |       8   →       8              |      180.00 ns →      433.00 ns (+140.56%) | 
  │ │ ├ Eigensolver_scalapack|pzhegvx                                   |      119.43 ms →      117.42 ms   (-1.68%) |       4   →       4              |      477.71 ms →      469.68 ms   (-1.68%) | 
  │ │ └ sddk::wf_trans                                                  |       26.76 ms →       26.64 ms   (-0.45%) |       4   →       4              |      107.03 ms →      106.55 ms   (-0.45%) | 
  │ │   └ sddk::wf_trans|pw                                             |       26.57 ms →       26.42 ms   (-0.57%) |       4   →       4              |      106.28 ms →      105.68 ms   (-0.57%) | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      368.00 ns →      370.50 ns   (+0.68%) |       4   →       4              |        1.47 μs →        1.48 μs   (+0.68%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      214.02 s  →      208.46 s    (-2.60%) |       1   →       1              |      214.02 s  →      208.46 s    (-2.60%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.78 ms →        5.72 ms   (-1.16%) |      19   →      19              |      109.90 ms →      108.63 ms   (-1.16%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        7.91 s  →        8.00 s    (+1.14%) |      27   →      26     (-3.70%) |      213.65 s  →      208.09 s    (-2.60%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        4.45 ms →        4.48 ms   (+0.47%) |      27   →      26     (-3.70%) |      120.27 ms →      116.36 ms   (-3.25%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.10 ms →        4.12 ms   (+0.60%) |      27   →      26     (-3.70%) |      110.68 ms →      107.22 ms   (-3.13%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      981.50 μs →      954.58 μs   (-2.74%) |      27   →      26     (-3.70%) |       26.50 ms →       24.82 ms   (-6.34%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.23 ms →        2.28 ms   (+2.48%) |      27   →      26     (-3.70%) |       60.19 ms →       59.39 ms   (-1.32%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       63.97 μs →       64.24 μs   (+0.41%) |      54   →      52     (-3.70%) |        3.45 ms →        3.34 ms   (-3.30%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       90.84 μs →       89.78 μs   (-1.17%) |      27   →      26     (-3.70%) |        2.45 ms →        2.33 ms   (-4.83%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       66.51 μs →       66.18 μs   (-0.50%) |      27   →      26     (-3.70%) |        1.80 ms →        1.72 ms   (-4.18%) | 
  │ │ ├ sirius::Band::solve                                             |        5.83 s  →        5.91 s    (+1.38%) |      27   →      26     (-3.70%) |      157.39 s  →      153.65 s    (-2.37%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      325.66 μs →      341.09 μs   (+4.74%) |     108   →     104     (-3.70%) |       35.17 ms →       35.47 ms   (+0.86%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      320.26 μs →      335.82 μs   (+4.86%) |     108   →     104     (-3.70%) |       34.59 ms →       34.93 ms   (+0.98%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        3.98 μs →        4.02 μs   (+1.03%) |     108   →     104     (-3.70%) |      429.71 μs →      418.08 μs   (-2.71%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.46 s  →        1.48 s    (+1.38%) |     108   →     104     (-3.70%) |      157.35 s  →      153.62 s    (-2.37%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       11.97 ms →       12.02 ms   (+0.42%) |     108   →     104     (-3.70%) |        1.29 s  →        1.25 s    (-3.29%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |      712.80 ns →      640.67 ns  (-10.12%) |     648   →     624     (-3.70%) |      461.90 μs →      399.78 μs  (-13.45%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.84 ms →        1.84 ms   (+0.16%) |     108   →     104     (-3.70%) |      198.59 ms →      191.53 ms   (-3.55%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      356.11 μs →      357.31 μs   (+0.34%) |     108   →     104     (-3.70%) |       38.46 ms →       37.16 ms   (-3.38%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      552.13 μs →      555.89 μs   (+0.68%) |     216   →     208     (-3.70%) |      119.26 ms →      115.62 ms   (-3.05%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.43 s  →        1.45 s    (+1.40%) |     108   →     104     (-3.70%) |      154.88 s  →      151.23 s    (-2.36%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       69.01 ms →       70.16 ms   (+1.67%) |     958   →     925     (-3.44%) |       66.11 s  →       64.90 s    (-1.83%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       44.11 ms →       44.88 ms   (+1.73%) |     958   →     925     (-3.44%) |       42.26 s  →       41.51 s    (-1.77%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        8.76 ms →        8.88 ms   (+1.28%) |     958   →     925     (-3.44%) |        8.39 s  →        8.21 s    (-2.21%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      224.27 μs →      231.64 μs   (+3.28%) |     958   →     925     (-3.44%) |      214.85 ms →      214.27 ms   (-0.27%) | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        1.97 ms →        2.04 ms   (+3.50%) |     108   →     104     (-3.70%) |      213.05 ms →      212.33 ms   (-0.34%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |        6.76 ms →        6.86 ms   (+1.53%) |     958   →     925     (-3.44%) |        6.47 s  →        6.35 s    (-1.97%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |       84.90 μs →       87.87 μs   (+3.50%) |     958   →     925     (-3.44%) |       81.33 ms →       81.28 ms   (-0.06%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |      731.36 μs →      759.48 μs   (+3.84%) |     108   →     104     (-3.70%) |       78.99 ms →       78.99 ms   (-0.00%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |        9.58 ms →        9.83 ms   (+2.62%) |     958   →     925     (-3.44%) |        9.17 s  →        9.09 s    (-0.92%) | 
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |        5.99 ms →        6.18 ms   (+3.20%) |     958   →     925     (-3.44%) |        5.74 s  →        5.72 s    (-0.36%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        1.52 ms →        1.52 ms   (+0.07%) |     958   →     925     (-3.44%) |        1.46 s  →        1.41 s    (-3.38%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        8.49 ms →        8.63 ms   (+1.64%) |     958   →     925     (-3.44%) |        8.13 s  →        7.98 s    (-1.86%) | 
  │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        1.23 ms →        1.27 ms   (+3.65%) |     958   →     925     (-3.44%) |        1.18 s  →        1.18 s    (+0.08%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.43 ms →        7.55 ms   (+1.67%) |    1.92 K →    1.85 K   (-3.44%) |       14.24 s  →       13.97 s    (-1.83%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       28.82 ms →       29.26 ms   (+1.53%) |     958   →     925     (-3.44%) |       27.61 s  →       27.07 s    (-1.97%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        1.94 ms →        1.95 ms   (+0.90%) |    1.81 K →    1.75 K   (-3.43%) |        3.50 s  →        3.41 s    (-2.56%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       80.91 ns →       55.82 ns  (-31.01%) |    1.81 K →    1.75 K   (-3.43%) |      146.28 μs →       97.46 μs  (-33.38%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        1.93 ms →        1.95 ms   (+0.93%) |    1.81 K →    1.75 K   (-3.43%) |        3.48 s  →        3.40 s    (-2.53%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       83.11 ns →       93.87 ns  (+12.94%) |    1.81 K →    1.75 K   (-3.43%) |      150.27 μs →      163.90 μs   (+9.07%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|potrf                               |      852.63 μs →      838.85 μs   (-1.62%) |     958   →     925     (-3.44%) |      816.82 ms →      775.94 ms   (-5.01%) | 
+ │ │ │ │   │ ├ sddk::orthogonalize|trtri                               |      838.25 μs →      765.29 μs   (-8.70%) |     958   →     925     (-3.44%) |      803.04 ms →      707.89 ms  (-11.85%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |        5.64 ms →        5.76 ms   (+2.11%) |    3.72 K →    3.60 K   (-3.44%) |       20.99 s  →       20.70 s    (-1.40%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        3.84 ms →        3.92 ms   (+2.05%) |    5.42 K →    5.24 K   (-3.43%) |       20.81 s  →       20.51 s    (-1.45%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        5.23 ms →        5.24 ms   (+0.18%) |     958   →     925     (-3.44%) |        5.01 s  →        4.85 s    (-3.27%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |        3.49 ms →        3.53 ms   (+1.24%) |     958   →     925     (-3.44%) |        3.34 s  →        3.26 s    (-2.25%) | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       72.34 ns →       70.83 ns   (-2.08%) |     958   →     925     (-3.44%) |       69.30 μs →       65.52 μs   (-5.45%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        3.47 ms →        3.52 ms   (+1.27%) |     958   →     925     (-3.44%) |        3.33 s  →        3.25 s    (-2.22%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       53.30 ns →       75.81 ns  (+42.23%) |     958   →     925     (-3.44%) |       51.06 μs →       70.12 μs  (+37.33%) | 
  │ │ │ │   ├ Eigensolver_scalapack|pzheevx                             |       33.60 ms →       33.19 ms   (-1.23%) |     958   →     925     (-3.44%) |       32.19 s  →       30.70 s    (-4.63%) | 
  │ │ │ │   ├ sirius::residuals                                         |       10.72 ms →       10.80 ms   (+0.77%) |     932   →     899     (-3.54%) |        9.99 s  →        9.71 s    (-2.80%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       10.33 ms →       10.46 ms   (+1.27%) |     890   →     855     (-3.93%) |        9.19 s  →        8.94 s    (-2.71%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        5.14 ms →        5.20 ms   (+1.14%) |    1.78 K →    1.71 K   (-3.93%) |        9.15 s  →        8.89 s    (-2.84%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      624.58 μs →      632.43 μs   (+1.26%) |     890   →     855     (-3.93%) |      555.88 ms →      540.72 ms   (-2.73%) | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       40.65 ms →       40.65 ms   (-0.01%) |     343   →     344     (+0.29%) |       13.94 s  →       13.98 s    (+0.28%) | 
  │ │ │ │     └ sddk::wf_trans                                          |       24.00 ms →       23.82 ms   (-0.76%) |     578   →     584     (+1.04%) |       13.87 s  →       13.91 s    (+0.27%) | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |       16.98 ms →       16.78 ms   (-1.15%) |     813   →     824     (+1.35%) |       13.81 s  →       13.83 s    (+0.18%) | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      496.81 ns →      468.76 ns   (-5.65%) |     108   →     104     (-3.70%) |       53.66 μs →       48.75 μs   (-9.14%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       21.69 μs →       23.06 μs   (+6.35%) |      27   →      26     (-3.70%) |      585.56 μs →      599.68 μs   (+2.41%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      601.29 μs →      600.63 μs   (-0.11%) |      27   →      26     (-3.70%) |       16.23 ms →       15.62 ms   (-3.81%) | 
  │ │ ├ sirius::Density::generate                                       |      897.49 ms →      895.98 ms   (-0.17%) |      27   →      26     (-3.70%) |       24.23 s  →       23.30 s    (-3.87%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      526.38 ms →      524.66 ms   (-0.33%) |      27   →      26     (-3.70%) |       14.21 s  →       13.64 s    (-4.02%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       24.87 ms →       24.57 ms   (-1.23%) |     108   →     104     (-3.70%) |        2.69 s  →        2.55 s    (-4.89%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |        5.80 μs →        6.04 μs   (+4.01%) |     108   →     104     (-3.70%) |      626.86 μs →      627.82 μs   (+0.15%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       13.23 μs →       12.43 μs   (-6.04%) |       8   →       8              |      105.81 μs →       99.42 μs   (-6.04%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       20.77 ms →       20.45 ms   (-1.52%) |     108   →     104     (-3.70%) |        2.24 s  →        2.13 s    (-5.17%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       29.89 ms →       29.76 ms   (-0.42%) |     108   →     104     (-3.70%) |        3.23 s  →        3.10 s    (-4.11%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       10.95 μs →       11.15 μs   (+1.81%) |     108   →     104     (-3.70%) |        1.18 ms →        1.16 ms   (-1.96%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        1.46 ms →        1.46 ms   (+0.06%) |     108   →     104     (-3.70%) |      157.76 ms →      152.01 ms   (-3.65%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       27.94 ms →       27.82 ms   (-0.45%) |     108   →     104     (-3.70%) |        3.02 s  →        2.89 s    (-4.13%) | 
  │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        3.80 ms →        3.68 ms   (-3.33%) |     108   →     104     (-3.70%) |      410.93 ms →      382.52 ms   (-6.91%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      564.64 ns →      499.95 ns  (-11.46%) |     108   →     104     (-3.70%) |       60.98 μs →       51.99 μs  (-14.74%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       42.57 ms →       42.55 ms   (-0.05%) |     108   →     104     (-3.70%) |        4.60 s  →        4.42 s    (-3.75%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.63 ms   (-0.84%) |      27   →      26     (-3.70%) |       44.38 ms →       42.38 ms   (-4.52%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.93 ms →       88.93 ms   (+0.00%) |      27   →      26     (-3.70%) |        2.40 s  →        2.31 s    (-3.70%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.70 ms →       88.70 ms   (-0.00%) |      27   →      26     (-3.70%) |        2.40 s  →        2.31 s    (-3.71%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      278.56 ms →      277.85 ms   (-0.26%) |      27   →      26     (-3.70%) |        7.52 s  →        7.22 s    (-3.95%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      278.56 ms →      277.85 ms   (-0.26%) |      27   →      26     (-3.70%) |        7.52 s  →        7.22 s    (-3.95%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.70 ms →       25.93 ms   (+4.95%) |      27   →      26     (-3.70%) |      666.98 ms →      674.08 ms   (+1.06%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      228.15 ms →      226.24 ms   (-0.83%) |      27   →      26     (-3.70%) |        6.16 s  →        5.88 s    (-4.51%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       23.94 ms →       23.89 ms   (-0.20%) |      27   →      26     (-3.70%) |      646.29 ms →      621.10 ms   (-3.90%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       81.15 ms →       80.71 ms   (-0.54%) |      27   →      26     (-3.70%) |        2.19 s  →        2.10 s    (-4.22%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        7.80 ms →        9.17 ms  (+17.57%) |      27   →      26     (-3.70%) |      210.61 ms →      238.45 ms  (+13.22%) | 
  │ │ ├ sirius::Density::mix                                            |      211.29 ms →      206.95 ms   (-2.05%) |      27   →      26     (-3.70%) |        5.70 s  →        5.38 s    (-5.68%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      962.15 μs →      941.80 μs   (-2.12%) |      27   →      26     (-3.70%) |       25.98 ms →       24.49 ms   (-5.74%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.70 ms →       10.73 ms   (+0.32%) |     335   →     334     (-0.30%) |        3.58 s  →        3.58 s    (+0.02%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.41 ms →       10.59 ms   (+1.70%) |     335   →     334     (-0.30%) |        3.49 s  →        3.54 s    (+1.40%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.41 ms →       10.58 ms   (+1.71%) |     335   →     334     (-0.30%) |        3.49 s  →        3.54 s    (+1.40%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        6.12 ms →        6.01 ms   (-1.73%) |      27   →      26     (-3.70%) |      165.13 ms →      156.27 ms   (-5.37%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.26 ms →        5.17 ms   (-1.64%) |      27   →      26     (-3.70%) |      141.93 ms →      134.43 ms   (-5.28%) | 
  │ │ ├ sirius::Potential::generate                                     |      568.63 ms →      579.29 ms   (+1.88%) |      27   →      26     (-3.70%) |       15.35 s  →       15.06 s    (-1.90%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      126.90 ms →      137.56 ms   (+8.40%) |      27   →      26     (-3.70%) |        3.43 s  →        3.58 s    (+4.39%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        6.60 ms →       18.69 ms (+183.28%) |      27   →      26     (-3.70%) |      178.14 ms →      485.94 ms (+172.78%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.74 ms →       11.04 ms   (+2.81%) |      27   →      26     (-3.70%) |      289.88 ms →      286.98 ms   (-1.00%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.59 ms →        9.93 ms   (-6.30%) |      27   →      26     (-3.70%) |      286.03 ms →      258.09 ms   (-9.77%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.59 ms →        9.93 ms   (-6.30%) |      27   →      26     (-3.70%) |      286.01 ms →      258.08 ms   (-9.77%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      550.69 μs →      548.18 μs   (-0.46%) |      54   →      52     (-3.70%) |       29.74 ms →       28.51 ms   (-4.14%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       49.19 ms →       49.37 ms   (+0.35%) |      27   →      26     (-3.70%) |        1.33 s  →        1.28 s    (-3.36%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.85 ms →       47.04 ms   (+0.40%) |      27   →      26     (-3.70%) |        1.27 s  →        1.22 s    (-3.31%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.06 ms →        3.00 ms   (-2.13%) |      54   →      52     (-3.70%) |      165.26 ms →      155.76 ms   (-5.75%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.26 ms →        5.30 ms   (+0.91%) |      27   →      26     (-3.70%) |      141.89 ms →      137.88 ms   (-2.82%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.63 ms →        6.62 ms   (-0.15%) |      27   →      26     (-3.70%) |      179.10 ms →      172.21 ms   (-3.85%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.93 ms →       90.91 ms   (-0.02%) |      27   →      26     (-3.70%) |        2.46 s  →        2.36 s    (-3.72%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      292.57 ms →      292.45 ms   (-0.04%) |      27   →      26     (-3.70%) |        7.90 s  →        7.60 s    (-3.74%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      281.77 ms →      281.13 ms   (-0.23%) |      27   →      26     (-3.70%) |        7.61 s  →        7.31 s    (-3.92%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      281.77 ms →      281.13 ms   (-0.23%) |      27   →      26     (-3.70%) |        7.61 s  →        7.31 s    (-3.92%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.15 ms →       28.60 ms   (+5.33%) |      27   →      26     (-3.70%) |      733.08 ms →      743.54 ms   (+1.43%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      227.05 ms →      224.94 ms   (-0.93%) |      27   →      26     (-3.70%) |        6.13 s  →        5.85 s    (-4.60%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.78 ms →       23.80 ms   (+0.07%) |      27   →      26     (-3.70%) |      642.12 ms →      618.79 ms   (-3.63%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.51 ms →        7.52 ms  (+36.38%) |      27   →      26     (-3.70%) |      148.88 ms →      195.52 ms  (+31.33%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.29 ms →       10.78 ms   (+4.72%) |     189   →     182     (-3.70%) |        1.94 s  →        1.96 s    (+0.84%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.88 ms →       10.47 ms   (+5.94%) |     189   →     182     (-3.70%) |        1.87 s  →        1.91 s    (+2.02%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.88 ms →       10.47 ms   (+5.94%) |     189   →     182     (-3.70%) |        1.87 s  →        1.91 s    (+2.02%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.57 ms →       10.60 ms   (+0.25%) |      81   →      78     (-3.70%) |      856.13 ms →      826.45 ms   (-3.47%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.23 ms →       10.37 ms   (+1.36%) |      81   →      78     (-3.70%) |      828.88 ms →      809.05 ms   (-2.39%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |       10.11 ms →       10.06 ms   (-0.53%) |      27   →      26     (-3.70%) |      272.98 ms →      261.49 ms   (-4.21%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      109.87 μs →      185.17 μs  (+68.54%) |      27   →      26     (-3.70%) |        2.97 ms →        4.81 ms  (+62.30%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      104.64 μs →      179.27 μs  (+71.32%) |      27   →      26     (-3.70%) |        2.83 ms →        4.66 ms  (+64.98%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.07 ms →        5.01 ms   (-1.26%) |       2   →       2              |       10.15 ms →       10.02 ms   (-1.26%) | 
  │ ├ sirius::Periodic_function|inner                                   |        9.94 ms →       10.60 ms   (+6.66%) |       6   →       6              |       59.62 ms →       63.59 ms   (+6.66%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        9.78 ms →       10.58 ms   (+8.22%) |       6   →       6              |       58.68 ms →       63.51 ms   (+8.22%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        9.78 ms →       10.58 ms   (+8.22%) |       6   →       6              |       58.68 ms →       63.51 ms   (+8.22%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.21 ms →       10.04 ms   (-1.63%) |       3   →       3              |       30.62 ms →       30.13 ms   (-1.63%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.13 ms →       10.03 ms   (-0.95%) |       3   →       3              |       30.38 ms →       30.10 ms   (-0.95%) | 
  ├ sirius::Periodic_function|inner                                     |       10.06 ms →       10.50 ms   (+4.41%) |       2   →       2              |       20.11 ms →       21.00 ms   (+4.41%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.05 ms →       10.49 ms   (+4.43%) |       2   →       2              |       20.10 ms →       20.99 ms   (+4.43%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.05 ms →       10.49 ms   (+4.43%) |       2   →       2              |       20.10 ms →       20.99 ms   (+4.43%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.42 ms →       10.06 ms   (-3.54%) |       1   →       1              |       10.42 ms →       10.06 ms   (-3.54%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.42 ms →       10.05 ms   (-3.55%) |       1   →       1              |       10.42 ms →       10.05 ms   (-3.55%) | 
  └ sirius::finalize                                                    |      349.31 ms →      333.86 ms   (-4.42%) |       1   →       1              |      349.31 ms →      333.86 ms   (-4.42%) | 
  ====================================================================================================================================================================================================
```
