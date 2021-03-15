# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs 8be4a3d847d7cac2fa4e252581562d3d44ebcb3a
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      150.96 s  →      124.13 s   (-17.78%) |       1   →       1              |      150.96 s  →      124.13 s   (-17.78%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |                       115.50 s             |                   1              |                       115.50 s             | 
  ├ sirius::Band::solve                                                 |                         1.87 s             |                  45              |                        83.96 s             | 
  ├ sirius::Band::diag_pseudo_potential_davidson                        |                         1.83 s             |                  45              |                        82.39 s             | 
  ├ sddk::orthogonalize                                                 |                        75.20 ms            |                 209              |                        15.72 s             | 
  ├ sirius::Density::generate                                           |                       294.94 ms            |                  45              |                        13.27 s             | 
  ├ sirius::Density::generate_valence                                   |                       290.96 ms            |                  45              |                        13.09 s             | 
  ├ Eigensolver_cuda|zheevdx                                            |                        38.56 ms            |                 209              |                         8.06 s             | 
  ├ sddk::orthogonalize|tmtrx                                           |                        26.80 ms            |                 209              |                         5.60 s             | 
  ├ sirius::Density::mix                                                |                       104.72 ms            |                  45              |                         4.71 s             | 
  ├ sirius::Density::add_k_point_contribution_rg                        |                       104.58 ms            |                  45              |                         4.71 s             | 
  ├ sirius::Band::diag_pseudo_potential_davidson|update_phi             |                        50.63 ms            |                  86              |                         4.35 s             | 
  ├ sddk::orthogonalize|transform                                       |                        15.90 ms            |                 209              |                         3.32 s             | 
  ├ sirius::residuals                                                   |                        15.19 ms            |                 204              |                         3.10 s             | 
  ├ sirius::initialize                                                  |        2.80 s  →        2.75 s    (-2.03%) |       1   →       1              |        2.80 s  →        2.75 s    (-2.03%) | 
  ├ sirius::Density::add_k_point_contribution_dm                        |                        60.41 ms            |                  45              |                         2.72 s             | 
  ├ sirius::Band::initialize_subspace                                   |                         2.24 s             |                   1              |                         2.24 s             | 
  ├ sirius::Band::initialize_subspace|kp                                |                         2.23 s             |                   1              |                         2.23 s             | 
+ ├ sirius::Simulation_context::initialize                              |        2.96 s  →        2.08 s   (-29.62%) |       1   →       1              |        2.96 s  →        2.08 s   (-29.62%) | 
  │ ├ sirius::Simulation_context::init_comm                             |      258.27 μs                             |       1                          |      258.27 μs                             | 
  │ ├ sirius::Unit_cell::initialize                                     |        1.05 s                              |       1                          |        1.05 s                              | 
  │ │ ├ sirius::Atom_type::init                                         |        1.04 s                              |       1                          |        1.04 s                              | 
  │ │ └ sirius::Unit_cell::update                                       |       15.49 ms                             |       1                          |       15.49 ms                             | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        9.53 ms                             |       1                          |        9.53 ms                             | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |        5.93 ms                             |       1                          |        5.93 ms                             | 
  │ │     └ sirius::Unit_cell_symmetry                                  |        5.62 ms                             |       1                          |        5.62 ms                             | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        5.40 ms                             |       1                          |        5.40 ms                             | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      203.97 μs                             |       1                          |      203.97 μs                             | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |        2.64 μs                             |       1                          |        2.64 μs                             | 
  │ └ sirius::Simulation_context::update                                |        1.86 s                              |       1                          |        1.86 s                              | 
  │   ├ sirius::Unit_cell::update                                       |       10.86 ms                             |       1                          |       10.86 ms                             | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        7.84 ms                             |       1                          |        7.84 ms                             | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.01 ms                             |       1                          |        3.01 ms                             | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        2.71 ms                             |       1                          |        2.71 ms                             | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.50 ms                             |       1                          |        2.50 ms                             | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      199.17 μs                             |       1                          |      199.17 μs                             | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |        1.18 μs                             |       1                          |        1.18 μs                             | 
  │   ├ sirius::Radial_integrals|aug                                    |       20.14 ms                             |       2                          |       40.27 ms                             | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        1.09 ms                             |       2                          |        2.19 ms                             | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |      954.50 μs                             |       1                          |      954.50 μs                             | 
  │   ├ sirius::Radial_integrals|vloc                                   |        4.57 ms                             |       2                          |        9.14 ms                             | 
  │   ├ sirius::Radial_integrals|beta                                   |        3.62 ms                             |       2                          |        7.25 ms                             | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       15.37 ms                             |       4                          |       61.48 ms                             | 
  │   ├ sddk::Gvec::init                                                |      158.91 ms                             |       2                          |      317.81 ms                             | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      125.81 ms                             |       2                          |      251.62 ms                             | 
  │   ├ sddk::Gvec_shells                                               |      130.49 ms                             |       1                          |      130.49 ms                             | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.04 ms                             |       1                          |        1.04 ms                             | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      217.31 ms                             |       1                          |      217.31 ms                             | 
  ├ sirius::K_point_set::create_k_mesh                                  |       26.43 ms                             |       1                          |       26.43 ms                             | 
  │ ├ sirius::K_point::K_point                                          |        1.91 μs                             |       2                          |        3.83 μs                             | 
  │ └ sirius::K_point_set::initialize                                   |       26.40 ms                             |       1                          |       26.40 ms                             | 
  │   └ sirius::K_point::initialize                                     |       26.34 ms                             |       1                          |       26.34 ms                             | 
  │     ├ sirius::K_point::generate_gkvec                               |       19.74 ms                             |       1                          |       19.74 ms                             | 
  │     │ └ sddk::Gvec::init                                            |        5.20 ms                             |       1                          |        5.20 ms                             | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        9.60 μs                             |       1                          |        9.60 μs                             | 
  │     └ sirius::K_point::update                                       |        4.28 ms                             |       1                          |        4.28 ms                             | 
  │       └ sirius::Beta_projectors                                     |        1.72 ms                             |       1                          |        1.72 ms                             | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      908.50 μs                             |       1                          |      908.50 μs                             | 
  ├ sirius::Smooth_periodic_function                                    |        2.25 ms                             |       2                          |        4.49 ms                             | 
  ├ sirius::Simulation_context::update                                  |                         1.88 s             |                   1              |                         1.88 s             | 
  ├ sirius::Hamiltonian_k::apply_h_s                                    |                       209.66 ms            |                 210              |                        44.03 s             | 
  ├ sirius::Local_operator::apply_h                                     |                       148.71 ms            |                 210              |                        31.23 s             | 
  ├ sirius::Density::augment                                            |                        20.34 ms            |                  45              |                       915.19 ms            | 
  ├ sirius::Density::generate_rho_aug                                   |                        20.17 ms            |                  45              |                       907.46 ms            | 
  ├ sirius::Density::get_magnetisation                                  |                        12.77 ms            |                  45              |                       574.63 ms            | 
  ├ sirius::Density::compute_atomic_mag_mom                             |                        12.76 ms            |                  45              |                       574.33 ms            | 
  ├ sirius::finalize                                                    |                       410.94 ms            |                   1              |                       410.94 ms            | 
  ├ sddk::matrix_storage::remap_forward                                 |                        34.21 ms            |                 255              |                         8.72 s             | 
  ├ sddk::Gvec::init                                                    |                       106.29 ms            |                   3              |                       318.86 ms            | 
  ├ sirius::normalized_preconditioned_residuals                         |                         1.40 ms            |                 184              |                       256.76 ms            | 
  ├ sddk::Gvec::find_gvec_shells                                        |                       124.83 ms            |                   2              |                       249.67 ms            | 
  ├ sirius::Potential::generate                                         |                       212.37 ms            |                  46              |                         9.77 s             | 
  ├ sirius::Augmentation_operator::generate_pw_coeffs                   |                       217.88 ms            |                   1              |                       217.88 ms            | 
  ├ sirius::Band::set_subspace_mtrx                                     |                        22.81 ms            |                 211              |                         4.81 s             | 
  ├ sddk::wf_inner                                                      |                        15.68 ms            |                 584              |                         9.15 s             | 
  ├ sddk::wf_inner|pw                                                   |                        11.01 ms            |                 584              |                         6.43 s             | 
  ├ sddk::matrix_storage::remap_backward                                |                        32.97 ms            |                 210              |                         6.92 s             | 
  ├ sddk::matrix_storage::remap_forward|mpi                             |                        27.45 ms            |                 255              |                         7.00 s             | 
  ├ sirius::Potential::xc                                               |                       121.57 ms            |                  46              |                         5.59 s             | 
  ├ sirius::Potential::xc_rg_nonmagnetic                                |                       120.53 ms            |                  46              |                         5.54 s             | 
  ├ sirius::Non_local_operator::apply                                   |                        18.22 ms            |                 420              |                         7.65 s             | 
  ├ sddk::Gvec_shells                                                   |                       126.25 ms            |                   1              |                       126.25 ms            | 
  ├ Eigensolver_cuda|zhegvdx                                            |                       117.83 ms            |                   1              |                       117.83 ms            | 
  ├ sirius::Density::mixer_output                                       |                         2.55 ms            |                  45              |                       114.56 ms            | 
  ├ sddk::matrix_storage::remap_backward|mpi                            |                        20.63 ms            |                 210              |                         4.33 s             | 
  ├ sirius::Potential                                                   |       91.58 ms →       92.62 ms   (+1.14%) |       1   →       1              |       91.58 ms →       92.62 ms   (+1.14%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.48 ms                             |       6                          |       14.87 ms                             | 
  │ └ sirius::Potential::update                                         |       76.35 ms                             |       1                          |       76.35 ms                             | 
  │   └ sirius::Potential::generate_local_potential                     |       76.17 ms                             |       1                          |       76.17 ms                             | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       53.92 ms                             |       1                          |       53.92 ms                             | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |       22.05 ms                             |       1                          |       22.05 ms                             | 
  ├ sirius::Density                                                     |       71.27 ms                             |       1                          |       71.27 ms                             | 
  │ ├ sirius::Smooth_periodic_function                                  |        4.96 ms                             |       2                          |        9.91 ms                             | 
  │ └ sirius::Density::update                                           |       61.24 ms                             |       1                          |       61.24 ms                             | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       61.07 ms                             |       1                          |       61.07 ms                             | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       53.68 ms                             |       1                          |       53.68 ms                             | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        7.17 ms                             |       1                          |        7.17 ms                             | 
  ├ sirius::Beta_projectors_base::inner                                 |                        28.13 ms            |                 255              |                         7.17 s             | 
  ├ sirius::Unit_cell::initialize                                       |                        86.20 ms            |                   1              |                        86.20 ms            | 
  ├ sirius::Density::initial_density                                    |       78.52 ms →       80.06 ms   (+1.96%) |       1   →       1              |       78.52 ms →       80.06 ms   (+1.96%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       52.82 ms                             |       1                          |       52.82 ms                             | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.01 ms                             |       2                          |       10.01 ms                             | 
  │ └ sirius::Periodic_function::integrate                              |        4.03 ms                             |       1                          |        4.03 ms                             | 
  ├ sirius::Potential::generate                                         |      190.43 ms                             |       1                          |      190.43 ms                             | 
  │ ├ sirius::Potential::poisson                                        |       64.09 ms                             |       1                          |       64.09 ms                             | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        8.25 ms                             |       1                          |        8.25 ms                             | 
  │ │ └ sirius::Periodic_function|inner                                 |        4.19 ms                             |       1                          |        4.19 ms                             | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.04 ms                             |       1                          |        4.04 ms                             | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.04 ms                             |       1                          |        4.04 ms                             | 
  │ ├ sirius::Periodic_function::add                                    |      247.07 μs                             |       2                          |      494.14 μs                             | 
  │ ├ sirius::Potential::xc                                             |      100.21 ms                             |       1                          |      100.21 ms                             | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |      100.21 ms                             |       1                          |      100.21 ms                             | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.27 ms                             |       5                          |       11.37 ms                             | 
  │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        2.49 ms                             |       9                          |       22.41 ms                             | 
  │ │   ├ sirius::gradient                                              |        7.61 ms                             |       1                          |        7.61 ms                             | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.45 ms                             |       3                          |        7.34 ms                             | 
  │ │   ├ sirius::dot                                                   |        2.79 ms                             |       1                          |        2.79 ms                             | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.57 ms                             |       1                          |        2.57 ms                             | 
  │ │   └ sirius::divergence                                            |       19.75 ms                             |       1                          |       19.75 ms                             | 
  │ │     └ sirius::Smooth_periodic_function                            |        2.44 ms                             |       1                          |        2.44 ms                             | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.18 ms                             |       1                          |        3.18 ms                             | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       21.89 ms                             |       1                          |       21.89 ms                             | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      213.00 ns                             |       1                          |      213.00 ns                             | 
  ├ sirius::Potential::update                                           |                        77.93 ms            |                   1              |                        77.93 ms            | 
  ├ sirius::Potential::generate_local_potential                         |                        77.76 ms            |                   1              |                        77.76 ms            | 
  ├ sirius::Density                                                     |                        77.83 ms            |                   2              |                       155.66 ms            | 
  ├ sirius::Hamiltonian_k::get_h_o_diag                                 |                         1.62 ms            |                  45              |                        72.81 ms            | 
  ├ sirius::Density::update                                             |                        68.42 ms            |                   2              |                       136.84 ms            | 
  ├ sirius::Density::generate_pseudo_core_charge_density                |                        68.25 ms            |                   2              |                       136.50 ms            | 
  ├ sirius::Potential::poisson                                          |                        64.20 ms            |                  46              |                         2.95 s             | 
  ├ sirius::Radial_integrals|atomic_wfs                                 |                        15.63 ms            |                   4              |                        62.52 ms            | 
  ├ sirius::Atom_type::init                                             |                        62.19 ms            |                   1              |                        62.19 ms            | 
  ├ sirius::Simulation_context::init_comm                               |                        60.86 ms            |                   1              |                        60.86 ms            | 
  ├ sirius::Density::symmetrize_density_matrix                          |                         1.26 ms            |                  45              |                        56.60 ms            | 
  ├ sirius::Simulation_context::make_periodic_function                  |                        51.16 ms            |                   4              |                       204.64 ms            | 
  ├ sirius::K_point_set::find_band_occupancies                          |                       969.55 μs            |                  45              |                        43.63 ms            | 
  ├ sirius::divergence                                                  |                        19.80 ms            |                  92              |                         1.82 s             | 
  ├ sirius::Radial_integrals|aug                                        |                        18.64 ms            |                   2              |                        37.28 ms            | 
  ├ sddk::wf_trans                                                      |                        19.22 ms            |                 476              |                         9.15 s             | 
  ├ sddk::wf_trans|pw                                                   |                         8.77 ms            |                1.03 K            |                         9.02 s             | 
  ├ sirius::K_point_set::create_k_mesh                                  |                        25.72 ms            |                   1              |                        25.72 ms            | 
  ├ sirius::K_point_set::initialize                                     |                        25.67 ms            |                   1              |                        25.67 ms            | 
  ├ sirius::K_point::initialize                                         |                        25.61 ms            |                   1              |                        25.61 ms            | 
  ├ sirius::K_point::generate_atomic_wave_functions                     |                        25.02 ms            |                   1              |                        25.02 ms            | 
  ├ sirius::Unit_cell::update                                           |                        17.63 ms            |                   2              |                        35.26 ms            | 
  ├ sirius::Potential::generate_D_operator_matrix                       |                        20.96 ms            |                  46              |                       964.30 ms            | 
  ├ sirius::Potential::xc_rg_nonmagnetic|libxc                          |                        11.27 ms            |                  92              |                         1.04 s             | 
  ├ sirius::K_point::generate_gkvec                                     |                        19.31 ms            |                   1              |                        19.31 ms            | 
- ├ sirius::Hamiltonian0                                                |       14.05 ms →        8.71 ms  (-38.01%) |       1   →      46   (+4500.00%) |       14.05 ms →      400.73 ms (+2751.33%) | 
  │ ├ sirius::Local_operator                                            |       13.72 ms                             |       1                          |       13.72 ms                             | 
  │ │ ├ sirius::Smooth_periodic_function                                |        7.17 ms                             |       1                          |        7.17 ms                             | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        5.10 ms                             |       1                          |        5.10 ms                             | 
  │ ├ sirius::Non_local_operator                                        |       59.98 μs                             |       2                          |      119.96 μs                             | 
  │ ├ sirius::D_operator::initialize                                    |       87.43 μs                             |       1                          |       87.43 μs                             | 
  │ └ sirius::Q_operator::initialize                                    |       70.52 μs                             |       1                          |       70.52 μs                             | 
  ├ sirius::Band::initialize_subspace                                   |        2.19 s                              |       1                          |        2.19 s                              | 
  │ ├ sirius::Hamiltonian_k                                             |        8.43 ms                             |       1                          |        8.43 ms                             | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      260.20 μs                             |       1                          |      260.20 μs                             | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        8.16 ms                             |       1                          |        8.16 ms                             | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        2.18 s                              |       1                          |        2.18 s                              | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       86.27 ms                             |       4                          |      345.08 ms                             | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       25.30 ms                             |       1                          |       25.30 ms                             | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       14.35 ms                             |       1                          |       14.35 ms                             | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |        1.21 s                              |       1                          |        1.21 s                              | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      987.72 ms                             |       1                          |      987.72 ms                             | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |      313.06 ms                             |       1                          |      313.06 ms                             | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |      173.77 ms                             |       1                          |      173.77 ms                             | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |      173.77 ms                             |       1                          |      173.77 ms                             | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |      120.85 ms                             |       1                          |      120.85 ms                             | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      183.14 ms                             |       1                          |      183.14 ms                             | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |      183.14 ms                             |       1                          |      183.14 ms                             | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      160.02 ms                             |       1                          |      160.02 ms                             | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |      109.54 ms                             |       1                          |      109.54 ms                             | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.74 ms                             |       1                          |        3.74 ms                             | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       88.95 ms                             |       1                          |       88.95 ms                             | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |       11.27 ms                             |       1                          |       11.27 ms                             | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       64.22 ms                             |       2                          |      128.44 ms                             | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       58.35 ms                             |       2                          |      116.70 ms                             | 
  │ │ │ └ sddk::inner                                                   |       58.24 ms                             |       2                          |      116.47 ms                             | 
  │ │ │   ├ sddk::inner|local                                           |       20.03 μs                             |       2                          |       40.06 μs                             | 
  │ │ │   ├ sddk::inner|device_copy                                     |       25.56 ms                             |       4                          |      102.25 ms                             | 
  │ │ │   ├ sddk::inner|store                                           |      689.63 μs                             |       4                          |        2.76 ms                             | 
  │ │ │   └ sddk::inner|mpi                                             |        5.70 ms                             |       2                          |       11.40 ms                             | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      116.18 ms                             |       1                          |      116.18 ms                             | 
  │ │ └ sddk::transform                                                 |       36.03 ms                             |       1                          |       36.03 ms                             | 
  │ │   ├ sddk::transform|init                                          |       13.83 μs                             |       1                          |       13.83 μs                             | 
  │ │   └ sddk::transform|local                                         |       18.58 μs                             |       1                          |       18.58 μs                             | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      437.00 ns                             |       1                          |      437.00 ns                             | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      141.26 s                              |       1                          |      141.26 s                              | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.17 ms                             |      31                          |       67.39 ms                             | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.28 s                              |      43                          |      140.98 s                              | 
  │ │ ├ sirius::Hamiltonian0                                            |        7.00 ms                             |      43                          |      300.79 ms                             | 
  │ │ │ ├ sirius::Local_operator                                        |        6.66 ms                             |      43                          |      286.36 ms                             | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |        1.50 ms                             |      43                          |       64.39 ms                             | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.72 ms                             |      43                          |      159.97 ms                             | 
  │ │ │ ├ sirius::Non_local_operator                                    |       60.56 μs                             |      86                          |        5.21 ms                             | 
  │ │ │ ├ sirius::D_operator::initialize                                |       83.98 μs                             |      43                          |        3.61 ms                             | 
  │ │ │ └ sirius::Q_operator::initialize                                |       70.52 μs                             |      43                          |        3.03 ms                             | 
  │ │ ├ sirius::Band::solve                                             |        2.61 s                              |      43                          |      112.35 s                              | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      210.65 μs                             |      43                          |        9.06 ms                             | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      203.80 μs                             |      43                          |        8.76 ms                             | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.19 μs                             |      43                          |      223.27 μs                             | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.59 s                              |      43                          |      111.57 s                              | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       69.12 ms                             |      43                          |        2.97 s                              | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        5.38 ms                             |     258                          |        1.39 s                              | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        2.05 ms                             |      43                          |       88.14 ms                             | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      418.63 μs                             |      43                          |       18.00 ms                             | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      952.89 μs                             |      43                          |       40.97 ms                             | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.50 s                              |      43                          |      107.46 s                              | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      214.25 ms                             |     208                          |       44.56 s                              | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |      151.49 ms                             |     208                          |       31.51 s                              | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |       27.48 ms                             |     208                          |        5.72 s                              | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      662.14 μs                             |     208                          |      137.73 ms                             | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        3.19 ms                             |      43                          |      137.30 ms                             | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |       22.36 ms                             |     208                          |        4.65 s                              | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      658.20 μs                             |     208                          |      136.91 ms                             | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |        3.17 ms                             |      43                          |      136.36 ms                             | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       33.79 ms                             |     208                          |        7.03 s                              | 
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |       21.02 ms                             |     208                          |        4.37 s                              | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.66 ms                             |     208                          |      552.41 ms                             | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       22.43 ms                             |     208                          |        4.67 s                              | 
  │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        2.21 ms                             |     208                          |      459.40 ms                             | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       18.82 ms                             |     416                          |        7.83 s                              | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       82.24 ms                             |     208                          |       17.11 s                              | 
  │ │ │ │   │ ├ sddk::inner                                             |       10.42 ms                             |     373                          |        3.89 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|local                                     |       18.59 μs                             |     373                          |        6.93 ms                             | 
  │ │ │ │   │ │ ├ sddk::inner|device_copy                               |        4.49 ms                             |     746                          |        3.35 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|store                                     |      105.84 μs                             |     746                          |       78.96 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|mpi                                       |        1.21 ms                             |     373                          |      449.64 ms                             | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |       30.26 ms                             |     208                          |        6.29 s                              | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       16.22 ms                             |     208                          |        3.37 s                              | 
  │ │ │ │   │ └ sddk::transform                                         |       21.51 ms                             |     165                          |        3.55 s                              | 
  │ │ │ │   │   ├ sddk::transform|init                                  |       19.76 μs                             |     165                          |        3.26 ms                             | 
  │ │ │ │   │   └ sddk::transform|local                                 |       51.56 μs                             |     495                          |       25.52 ms                             | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       24.99 ms                             |     208                          |        5.20 s                              | 
  │ │ │ │   │ └ sddk::inner                                             |       20.83 ms                             |     208                          |        4.33 s                              | 
  │ │ │ │   │   ├ sddk::inner|local                                     |       42.40 μs                             |     208                          |        8.82 ms                             | 
  │ │ │ │   │   ├ sddk::inner|device_copy                               |        7.93 ms                             |     416                          |        3.30 s                              | 
  │ │ │ │   │   ├ sddk::inner|store                                     |      228.67 μs                             |     416                          |       95.13 ms                             | 
  │ │ │ │   │   └ sddk::inner|mpi                                       |        4.46 ms                             |     208                          |      927.19 ms                             | 
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |      165.18 ms                             |     208                          |       34.36 s                              | 
  │ │ │ │   ├ sirius::residuals                                         |       19.18 ms                             |     207                          |        3.97 s                              | 
  │ │ │ │   │ ├ sddk::transform                                         |       20.07 ms                             |     171                          |        3.43 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       16.29 μs                             |     171                          |        2.78 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       56.32 μs                             |     342                          |       19.26 ms                             | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        2.41 ms                             |     171                          |      412.58 ms                             | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       51.27 ms                             |      44                          |        2.26 s                              | 
  │ │ │ │     └ sddk::transform                                         |       49.83 ms                             |      45                          |        2.24 s                              | 
  │ │ │ │       ├ sddk::transform|init                                  |       12.38 μs                             |      45                          |      556.88 μs                             | 
  │ │ │ │       └ sddk::transform|local                                 |       16.36 μs                             |      46                          |      752.69 μs                             | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      579.70 ns                             |      43                          |       24.93 μs                             | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       22.71 μs                             |      43                          |      976.52 μs                             | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |        3.40 ms                             |      43                          |      146.19 ms                             | 
  │ │ ├ sirius::Density::generate                                       |      293.27 ms                             |      43                          |       12.61 s                              | 
  │ │ │ ├ sirius::Density::generate_valence                             |      289.34 ms                             |      43                          |       12.44 s                              | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       66.69 ms                             |      43                          |        2.87 s                              | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       62.20 μs                             |      43                          |        2.67 ms                             | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |        1.18 ms                             |       2                          |        2.37 ms                             | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       55.46 ms                             |      43                          |        2.38 s                              | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       59.85 ms                             |      43                          |        2.57 s                              | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.66 μs                             |      43                          |      415.22 μs                             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        2.30 ms                             |      43                          |       99.04 ms                             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       57.00 ms                             |      43                          |        2.45 s                              | 
  │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        5.55 ms                             |      43                          |      238.77 ms                             | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      586.09 ns                             |      43                          |       25.20 μs                             | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      104.23 ms                             |      43                          |        4.48 s                              | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.40 ms                             |      43                          |      103.18 ms                             | 
  │ │ │ │ └ sirius::Density::augment                                    |       20.08 ms                             |      43                          |      863.33 ms                             | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       19.91 ms                             |      43                          |      856.15 ms                             | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      271.98 ns                             |      43                          |       11.70 μs                             | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |        1.25 ms                             |      43                          |       53.86 ms                             | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        2.68 ms                             |      43                          |      115.17 ms                             | 
  │ │ ├ sirius::Density::mix                                            |      131.76 ms                             |      43                          |        5.67 s                              | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      256.69 μs                             |      43                          |       11.04 ms                             | 
  │ │ │ └ sirius::Density::mixer_output                                 |        3.84 ms                             |      43                          |      164.98 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        3.65 ms                             |      43                          |      156.76 ms                             | 
  │ │ ├ sirius::Potential::generate                                     |      182.71 ms                             |      43                          |        7.86 s                              | 
  │ │ │ ├ sirius::Potential::poisson                                    |       64.98 ms                             |      43                          |        2.79 s                              | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        8.32 ms                             |      43                          |      357.97 ms                             | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |        4.99 ms                             |      43                          |      214.62 ms                             | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.09 ms                             |      43                          |      175.84 ms                             | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.09 ms                             |      43                          |      175.80 ms                             | 
  │ │ │ ├ sirius::Periodic_function::add                                |      230.45 μs                             |      86                          |       19.82 ms                             | 
  │ │ │ ├ sirius::Potential::xc                                         |       92.51 ms                             |      43                          |        3.98 s                              | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       92.51 ms                             |      43                          |        3.98 s                              | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        1.64 ms                             |     215                          |      351.96 ms                             | 
  │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |        2.39 ms                             |     387                          |      926.00 ms                             | 
  │ │ │ │   ├ sirius::gradient                                          |        2.42 ms                             |      43                          |      104.18 ms                             | 
  │ │ │ │   │ └ sirius::Smooth_periodic_function                        |      714.16 μs                             |     129                          |       92.13 ms                             | 
  │ │ │ │   ├ sirius::dot                                               |        2.82 ms                             |      43                          |      121.07 ms                             | 
  │ │ │ │   │ └ sirius::Smooth_periodic_function                        |        2.58 ms                             |      43                          |      110.90 ms                             | 
  │ │ │ │   └ sirius::divergence                                        |       19.72 ms                             |      43                          |      848.06 ms                             | 
  │ │ │ │     └ sirius::Smooth_periodic_function                        |        2.43 ms                             |      43                          |      104.45 ms                             | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.30 ms                             |      43                          |      141.81 ms                             | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       20.91 ms                             |      43                          |      899.09 ms                             | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      202.93 ns                             |      43                          |        8.73 μs                             | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      311.30 ns                             |      43                          |       13.39 μs                             | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.22 ms                             |      43                          |       95.61 ms                             | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.08 ms                             |     301                          |        1.23 s                              | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        3.92 ms                             |     301                          |        1.18 s                              | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        3.92 ms                             |     301                          |        1.18 s                              | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.23 ms                             |     129                          |      546.09 ms                             | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.08 ms                             |     129                          |      525.80 ms                             | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.04 ms                             |      43                          |      173.59 ms                             | 
  │ │ └ sirius::Density::get_magnetisation                              |       99.56 μs                             |      43                          |        4.28 ms                             | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |       95.99 μs                             |      43                          |        4.13 ms                             | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.28 ms                             |       2                          |       10.57 ms                             | 
  │ ├ sirius::Periodic_function|inner                                   |        4.09 ms                             |       6                          |       24.57 ms                             | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.02 ms                             |       6                          |       24.12 ms                             | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.02 ms                             |       6                          |       24.11 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.11 ms                             |       3                          |       12.32 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.08 ms                             |       3                          |       12.25 ms                             | 
  ├ sirius::Periodic_function|inner                                     |        3.98 ms                             |       2                          |        7.95 ms                             | 
  │ └ sirius::Periodic_function|inner_local                             |        3.94 ms                             |       2                          |        7.89 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        3.94 ms                             |       2                          |        7.88 ms                             | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.08 ms                             |       1                          |        4.08 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.05 ms                             |       1                          |        4.05 ms                             | 
  ├ sirius::finalize                                                    |      372.09 ms                             |       1                          |      372.09 ms                             | 
  ├ sirius::Band::initialize_subspace|kp|wf                             |                        14.36 ms            |                   1              |                        14.36 ms            | 
  ├ sirius::Local_operator                                              |                         6.83 ms            |                  46              |                       314.31 ms            | 
  ├ sirius::Unit_cell::get_symmetry                                     |                         8.44 ms            |                   2              |                        16.88 ms            | 
  ├ sirius::inner                                                       |                         4.23 ms            |                 598              |                         2.53 s             | 
  ├ sirius::Unit_cell_symmetry                                          |                         7.84 ms            |                   2              |                        15.68 ms            | 
  ├ sirius::Unit_cell_symmetry|spg                                      |                         7.62 ms            |                   2              |                        15.24 ms            | 
  ├ sirius::Beta_projectors_base::inner|comm                            |                         2.87 ms            |                 255              |                       732.33 ms            | 
  ├ sirius::Smooth_periodic_function::fft_transform                     |                         2.99 ms            |                 875              |                         2.62 s             | 
  ├ sirius::Smooth_periodic_function::gather_f_pw                       |                         5.19 ms            |                   2              |                        10.38 ms            | 
  ├ sirius::Radial_integrals|vloc                                       |                         5.06 ms            |                   2              |                        10.13 ms            | 
  ├ sirius::Unit_cell::find_nearest_neighbours                          |                         9.16 ms            |                   2              |                        18.32 ms            | 
  ├ sirius::Density::mixer_input                                        |                       212.99 μs            |                  45              |                         9.58 ms            | 
  ├ sirius::gradient                                                    |                         1.99 ms            |                  46              |                        91.67 ms            | 
  ├ sirius::Radial_integrals|beta                                       |                         3.65 ms            |                   2              |                         7.29 ms            | 
  ├ sirius::Hamiltonian_k                                               |                       365.07 μs            |                  46              |                        16.79 ms            | 
  ├ sirius::Beta_projectors_base::prepare                               |                        82.89 μs            |                  91              |                         7.54 ms            | 
  ├ sirius::Periodic_function::integrate                                |                         4.22 ms            |                  46              |                       194.18 ms            | 
  ├ sirius::K_point_set::sync_band                                      |                        57.66 μs            |                  90              |                         5.19 ms            | 
  ├ sirius::K_point::update                                             |                         3.95 ms            |                   1              |                         3.95 ms            | 
  ├ sirius::Beta_projectors_base::generate                              |                         2.58 ms            |                 255              |                       658.41 ms            | 
  ├ sirius::dot                                                         |                       748.68 μs            |                  46              |                        34.44 ms            | 
  ├ sirius::Radial_integrals|rho_core_pseudo                            |                         1.09 ms            |                   2              |                         2.18 ms            | 
  ├ sirius::Beta_projectors                                             |                         1.67 ms            |                   1              |                         1.67 ms            | 
  ├ sirius::Q_operator::initialize                                      |                         1.10 ms            |                  46              |                        50.66 ms            | 
  ├ sirius::Simulation_context::init_atoms_to_grid_idx                  |                         1.02 ms            |                   1              |                         1.02 ms            | 
  ├ sirius::Radial_integrals|rho_pseudo                                 |                       954.26 μs            |                   1              |                       954.26 μs            | 
  ├ sirius::Beta_projectors::generate_pw_coefs_t                        |                       926.79 μs            |                   1              |                       926.79 μs            | 
  ├ sirius::D_operator::initialize                                      |                       593.80 μs            |                  46              |                        27.31 ms            | 
  ├ sirius::Periodic_function::add                                      |                       198.57 μs            |                  92              |                        18.27 ms            | 
  ├ sirius::Local_operator::prepare_k                                   |                       205.65 μs            |                  46              |                         9.46 ms            | 
  ├ sirius::Unit_cell_symmetry|equiv                                    |                       211.75 μs            |                   2              |                       423.49 μs            | 
  ├ sirius::Non_local_operator                                          |                        61.09 μs            |                  92              |                         5.62 ms            | 
  ├ sirius::Field4D::symmetrize                                         |                       349.31 ns            |                  90              |                        31.44 μs            | 
  ├ sirius::K_point::K_point                                            |                         5.29 μs            |                   2              |                        10.58 μs            | 
  ├ sirius::Unit_cell_symmetry|mag                                      |                         1.89 μs            |                   2              |                         3.77 μs            | 
  ├ sddk::wf_inner|scale_back                                           |                       385.53 ns            |                 584              |                       225.15 μs            | 
  ├ sirius::Beta_projectors_base::dismiss                               |                       571.71 ns            |                  91              |                        52.03 μs            | 
  ├ sddk::wf_inner|scale                                                |                       207.03 ns            |                 584              |                       120.91 μs            | 
  └ sirius::Potential::generate_PAW_effective_potential                 |                       288.11 ns            |                  46              |                        13.25 μs            | 
  ====================================================================================================================================================================================================
```
