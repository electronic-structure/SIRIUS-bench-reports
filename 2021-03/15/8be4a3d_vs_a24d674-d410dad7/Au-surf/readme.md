# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs 8be4a3d847d7cac2fa4e252581562d3d44ebcb3a
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      152.06 s  →      124.43 s   (-18.17%) |       1   →       1              |      152.06 s  →      124.43 s   (-18.17%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |                       115.89 s             |                   1              |                       115.89 s             | 
  ├ sirius::Band::solve                                                 |                         1.87 s             |                  45              |                        84.11 s             | 
  ├ sirius::Band::diag_pseudo_potential_davidson                        |                         1.84 s             |                  45              |                        82.79 s             | 
  ├ sddk::orthogonalize                                                 |                        75.71 ms            |                 209              |                        15.82 s             | 
  ├ sirius::Density::generate                                           |                       299.16 ms            |                  45              |                        13.46 s             | 
  ├ sirius::Density::generate_valence                                   |                       295.21 ms            |                  45              |                        13.28 s             | 
  ├ Eigensolver_cuda|zheevdx                                            |                        38.57 ms            |                 209              |                         8.06 s             | 
  ├ sddk::orthogonalize|tmtrx                                           |                        27.21 ms            |                 209              |                         5.69 s             | 
  ├ sirius::Density::mix                                                |                       105.78 ms            |                  45              |                         4.76 s             | 
  ├ sirius::Density::add_k_point_contribution_rg                        |                       104.93 ms            |                  45              |                         4.72 s             | 
  ├ sirius::Band::diag_pseudo_potential_davidson|update_phi             |                        50.65 ms            |                  86              |                         4.36 s             | 
  ├ sddk::orthogonalize|transform                                       |                        15.89 ms            |                 209              |                         3.32 s             | 
  ├ sirius::residuals                                                   |                        15.11 ms            |                 204              |                         3.08 s             | 
  ├ sirius::Density::add_k_point_contribution_dm                        |                        61.17 ms            |                  45              |                         2.75 s             | 
  ├ sirius::initialize                                                  |        2.71 s  →        2.72 s    (+0.19%) |       1   →       1              |        2.71 s  →        2.72 s    (+0.19%) | 
  ├ sirius::Band::initialize_subspace                                   |                         2.25 s             |                   1              |                         2.25 s             | 
  ├ sirius::Band::initialize_subspace|kp                                |                         2.24 s             |                   1              |                         2.24 s             | 
+ ├ sirius::Simulation_context::initialize                              |        3.05 s  →        2.11 s   (-30.90%) |       1   →       1              |        3.05 s  →        2.11 s   (-30.90%) | 
  │ ├ sirius::Simulation_context::init_comm                             |       23.35 ms                             |       1                          |       23.35 ms                             | 
  │ ├ sirius::Unit_cell::initialize                                     |        1.07 s                              |       1                          |        1.07 s                              | 
  │ │ ├ sirius::Atom_type::init                                         |        1.06 s                              |       1                          |        1.06 s                              | 
  │ │ └ sirius::Unit_cell::update                                       |       15.99 ms                             |       1                          |       15.99 ms                             | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |       10.03 ms                             |       1                          |       10.03 ms                             | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |        5.94 ms                             |       1                          |        5.94 ms                             | 
  │ │     └ sirius::Unit_cell_symmetry                                  |        5.63 ms                             |       1                          |        5.63 ms                             | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        5.41 ms                             |       1                          |        5.41 ms                             | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      202.75 μs                             |       1                          |      202.75 μs                             | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |        2.58 μs                             |       1                          |        2.58 μs                             | 
  │ └ sirius::Simulation_context::update                                |        1.91 s                              |       1                          |        1.91 s                              | 
  │   ├ sirius::Unit_cell::update                                       |       11.34 ms                             |       1                          |       11.34 ms                             | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        8.31 ms                             |       1                          |        8.31 ms                             | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.02 ms                             |       1                          |        3.02 ms                             | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        2.72 ms                             |       1                          |        2.72 ms                             | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.52 ms                             |       1                          |        2.52 ms                             | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      198.18 μs                             |       1                          |      198.18 μs                             | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |        1.02 μs                             |       1                          |        1.02 μs                             | 
  │   ├ sirius::Radial_integrals|aug                                    |       21.25 ms                             |       2                          |       42.50 ms                             | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        1.10 ms                             |       2                          |        2.20 ms                             | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |      972.55 μs                             |       1                          |      972.55 μs                             | 
  │   ├ sirius::Radial_integrals|vloc                                   |        4.72 ms                             |       2                          |        9.44 ms                             | 
  │   ├ sirius::Radial_integrals|beta                                   |        4.09 ms                             |       2                          |        8.18 ms                             | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       15.23 ms                             |       4                          |       60.94 ms                             | 
  │   ├ sddk::Gvec::init                                                |      162.08 ms                             |       2                          |      324.15 ms                             | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      128.89 ms                             |       2                          |      257.77 ms                             | 
  │   ├ sddk::Gvec_shells                                               |      124.03 ms                             |       1                          |      124.03 ms                             | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.05 ms                             |       1                          |        1.05 ms                             | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      225.46 ms                             |       1                          |      225.46 ms                             | 
  ├ sirius::K_point_set::create_k_mesh                                  |       26.46 ms                             |       1                          |       26.46 ms                             | 
  │ ├ sirius::K_point::K_point                                          |        1.93 μs                             |       2                          |        3.86 μs                             | 
  │ └ sirius::K_point_set::initialize                                   |       26.43 ms                             |       1                          |       26.43 ms                             | 
  │   └ sirius::K_point::initialize                                     |       26.37 ms                             |       1                          |       26.37 ms                             | 
  │     ├ sirius::K_point::generate_gkvec                               |       19.80 ms                             |       1                          |       19.80 ms                             | 
  │     │ └ sddk::Gvec::init                                            |        5.19 ms                             |       1                          |        5.19 ms                             | 
  │     ├ sddk::matrix_storage::matrix_storage                          |       11.69 μs                             |       1                          |       11.69 μs                             | 
  │     └ sirius::K_point::update                                       |        4.22 ms                             |       1                          |        4.22 ms                             | 
  │       └ sirius::Beta_projectors                                     |        1.71 ms                             |       1                          |        1.71 ms                             | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      897.90 μs                             |       1                          |      897.90 μs                             | 
  ├ sirius::Smooth_periodic_function                                    |        2.21 ms                             |       2                          |        4.42 ms                             | 
  ├ sirius::Simulation_context::update                                  |                         1.90 s             |                   1              |                         1.90 s             | 
  ├ sirius::Hamiltonian_k::apply_h_s                                    |                       211.10 ms            |                 210              |                        44.33 s             | 
  ├ sirius::Local_operator::apply_h                                     |                       150.05 ms            |                 210              |                        31.51 s             | 
  ├ sirius::Density::augment                                            |                        20.36 ms            |                  45              |                       916.22 ms            | 
  ├ sirius::Density::generate_rho_aug                                   |                        20.15 ms            |                  45              |                       906.65 ms            | 
  ├ sirius::Density::get_magnetisation                                  |                        12.79 ms            |                  45              |                       575.34 ms            | 
  ├ sirius::Density::compute_atomic_mag_mom                             |                        12.78 ms            |                  45              |                       575.03 ms            | 
  ├ sirius::finalize                                                    |                       316.17 ms            |                   1              |                       316.17 ms            | 
  ├ sddk::Gvec::init                                                    |                       106.89 ms            |                   3              |                       320.67 ms            | 
  ├ sddk::matrix_storage::remap_forward                                 |                        35.08 ms            |                 255              |                         8.94 s             | 
  ├ sirius::normalized_preconditioned_residuals                         |                         1.40 ms            |                 184              |                       257.14 ms            | 
  ├ sddk::Gvec::find_gvec_shells                                        |                       124.23 ms            |                   2              |                       248.46 ms            | 
  ├ sirius::Potential::generate                                         |                       212.24 ms            |                  46              |                         9.76 s             | 
  ├ sirius::Augmentation_operator::generate_pw_coeffs                   |                       218.16 ms            |                   1              |                       218.16 ms            | 
  ├ sirius::Band::set_subspace_mtrx                                     |                        22.67 ms            |                 211              |                         4.78 s             | 
  ├ sddk::wf_inner                                                      |                        15.65 ms            |                 584              |                         9.14 s             | 
  ├ sddk::wf_inner|pw                                                   |                        11.13 ms            |                 584              |                         6.50 s             | 
  ├ sddk::matrix_storage::remap_backward                                |                        33.87 ms            |                 210              |                         7.11 s             | 
  ├ sirius::Non_local_operator::apply                                   |                        18.12 ms            |                 420              |                         7.61 s             | 
  ├ sirius::Potential::xc                                               |                       121.31 ms            |                  46              |                         5.58 s             | 
  ├ sirius::Potential::xc_rg_nonmagnetic                                |                       120.27 ms            |                  46              |                         5.53 s             | 
  ├ sddk::Gvec_shells                                                   |                       125.78 ms            |                   1              |                       125.78 ms            | 
  ├ Eigensolver_cuda|zhegvdx                                            |                       116.21 ms            |                   1              |                       116.21 ms            | 
  ├ sddk::matrix_storage::remap_forward|mpi                             |                        28.26 ms            |                 255              |                         7.21 s             | 
  ├ sirius::Density::mixer_output                                       |                         2.54 ms            |                  45              |                       114.21 ms            | 
  ├ sddk::matrix_storage::remap_backward|mpi                            |                        21.54 ms            |                 210              |                         4.52 s             | 
  ├ sirius::Potential                                                   |       93.13 ms →       92.61 ms   (-0.55%) |       1   →       1              |       93.13 ms →       92.61 ms   (-0.55%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.45 ms                             |       6                          |       14.72 ms                             | 
  │ └ sirius::Potential::update                                         |       78.09 ms                             |       1                          |       78.09 ms                             | 
  │   └ sirius::Potential::generate_local_potential                     |       77.91 ms                             |       1                          |       77.91 ms                             | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       53.43 ms                             |       1                          |       53.43 ms                             | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |       24.28 ms                             |       1                          |       24.28 ms                             | 
  ├ sirius::Density                                                     |       72.11 ms                             |       1                          |       72.11 ms                             | 
  │ ├ sirius::Smooth_periodic_function                                  |        4.72 ms                             |       2                          |        9.44 ms                             | 
  │ └ sirius::Density::update                                           |       62.56 ms                             |       1                          |       62.56 ms                             | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       62.39 ms                             |       1                          |       62.39 ms                             | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       52.95 ms                             |       1                          |       52.95 ms                             | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        9.23 ms                             |       1                          |        9.23 ms                             | 
  ├ sirius::Simulation_context::init_comm                               |                        90.18 ms            |                   1              |                        90.18 ms            | 
  ├ sirius::Beta_projectors_base::inner                                 |                        28.52 ms            |                 255              |                         7.27 s             | 
  ├ sirius::Density::initial_density                                    |       79.16 ms →       80.89 ms   (+2.18%) |       1   →       1              |       79.16 ms →       80.89 ms   (+2.18%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       52.23 ms                             |       1                          |       52.23 ms                             | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.33 ms                             |       2                          |       10.66 ms                             | 
  │ └ sirius::Periodic_function::integrate                              |        4.39 ms                             |       1                          |        4.39 ms                             | 
  ├ sirius::Potential::generate                                         |      191.05 ms                             |       1                          |      191.05 ms                             | 
  │ ├ sirius::Potential::poisson                                        |       64.08 ms                             |       1                          |       64.08 ms                             | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        9.45 ms                             |       1                          |        9.45 ms                             | 
  │ │ └ sirius::Periodic_function|inner                                 |        4.56 ms                             |       1                          |        4.56 ms                             | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.13 ms                             |       1                          |        4.13 ms                             | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.13 ms                             |       1                          |        4.13 ms                             | 
  │ ├ sirius::Periodic_function::add                                    |      237.48 μs                             |       2                          |      474.96 μs                             | 
  │ ├ sirius::Potential::xc                                             |      100.52 ms                             |       1                          |      100.52 ms                             | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |      100.52 ms                             |       1                          |      100.52 ms                             | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.28 ms                             |       5                          |       11.41 ms                             | 
  │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        2.46 ms                             |       9                          |       22.17 ms                             | 
  │ │   ├ sirius::gradient                                              |        7.58 ms                             |       1                          |        7.58 ms                             | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.44 ms                             |       3                          |        7.31 ms                             | 
  │ │   ├ sirius::dot                                                   |        2.88 ms                             |       1                          |        2.88 ms                             | 
  │ │   │ └ sirius::Smooth_periodic_function                            |        2.64 ms                             |       1                          |        2.64 ms                             | 
  │ │   └ sirius::divergence                                            |       19.85 ms                             |       1                          |       19.85 ms                             | 
  │ │     └ sirius::Smooth_periodic_function                            |        2.45 ms                             |       1                          |        2.45 ms                             | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.18 ms                             |       1                          |        3.18 ms                             | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       22.25 ms                             |       1                          |       22.25 ms                             | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      143.00 ns                             |       1                          |      143.00 ns                             | 
  ├ sirius::Potential::update                                           |                        77.70 ms            |                   1              |                        77.70 ms            | 
  ├ sirius::Potential::generate_local_potential                         |                        77.54 ms            |                   1              |                        77.54 ms            | 
  ├ sirius::Density                                                     |                        85.85 ms            |                   2              |                       171.70 ms            | 
  ├ sirius::Hamiltonian_k::get_h_o_diag                                 |                         1.62 ms            |                  45              |                        72.84 ms            | 
  ├ sirius::Unit_cell::initialize                                       |                        69.87 ms            |                   1              |                        69.87 ms            | 
  ├ sirius::Density::update                                             |                        76.32 ms            |                   2              |                       152.65 ms            | 
  ├ sirius::Density::generate_pseudo_core_charge_density                |                        76.15 ms            |                   2              |                       152.29 ms            | 
  ├ sirius::Potential::poisson                                          |                        64.37 ms            |                  46              |                         2.96 s             | 
  ├ sirius::Radial_integrals|atomic_wfs                                 |                        15.70 ms            |                   4              |                        62.80 ms            | 
  ├ sirius::Density::symmetrize_density_matrix                          |                         1.26 ms            |                  45              |                        56.57 ms            | 
  ├ sirius::Simulation_context::make_periodic_function                  |                        51.51 ms            |                   4              |                       206.06 ms            | 
  ├ sirius::Atom_type::init                                             |                        44.96 ms            |                   1              |                        44.96 ms            | 
  ├ sirius::K_point_set::find_band_occupancies                          |                       940.08 μs            |                  45              |                        42.30 ms            | 
  ├ sirius::divergence                                                  |                        19.77 ms            |                  92              |                         1.82 s             | 
  ├ sirius::Radial_integrals|aug                                        |                        18.39 ms            |                   2              |                        36.78 ms            | 
  ├ sddk::wf_trans                                                      |                        19.19 ms            |                 476              |                         9.13 s             | 
  ├ sddk::wf_trans|pw                                                   |                         8.76 ms            |                1.03 K            |                         9.02 s             | 
  ├ sirius::K_point_set::create_k_mesh                                  |                        26.29 ms            |                   1              |                        26.29 ms            | 
  ├ sirius::K_point_set::initialize                                     |                        26.23 ms            |                   1              |                        26.23 ms            | 
  ├ sirius::K_point::initialize                                         |                        26.18 ms            |                   1              |                        26.18 ms            | 
  ├ sirius::K_point::generate_atomic_wave_functions                     |                        25.14 ms            |                   1              |                        25.14 ms            | 
  ├ sirius::Unit_cell::update                                           |                        18.20 ms            |                   2              |                        36.39 ms            | 
  ├ sirius::Potential::generate_D_operator_matrix                       |                        20.96 ms            |                  46              |                       964.01 ms            | 
  ├ sirius::Potential::xc_rg_nonmagnetic|libxc                          |                        11.28 ms            |                  92              |                         1.04 s             | 
  ├ sirius::K_point::generate_gkvec                                     |                        19.78 ms            |                   1              |                        19.78 ms            | 
- ├ sirius::Hamiltonian0                                                |       13.99 ms →        8.63 ms  (-38.30%) |       1   →      46   (+4500.00%) |       13.99 ms →      397.17 ms (+2738.02%) | 
  │ ├ sirius::Local_operator                                            |       13.66 ms                             |       1                          |       13.66 ms                             | 
  │ │ ├ sirius::Smooth_periodic_function                                |        7.09 ms                             |       1                          |        7.09 ms                             | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        5.12 ms                             |       1                          |        5.12 ms                             | 
  │ ├ sirius::Non_local_operator                                        |       59.61 μs                             |       2                          |      119.22 μs                             | 
  │ ├ sirius::D_operator::initialize                                    |       82.96 μs                             |       1                          |       82.96 μs                             | 
  │ └ sirius::Q_operator::initialize                                    |       70.18 μs                             |       1                          |       70.18 μs                             | 
  ├ sirius::Band::initialize_subspace                                   |        2.21 s                              |       1                          |        2.21 s                              | 
  │ ├ sirius::Hamiltonian_k                                             |        8.40 ms                             |       1                          |        8.40 ms                             | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      237.18 μs                             |       1                          |      237.18 μs                             | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        8.16 ms                             |       1                          |        8.16 ms                             | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        2.20 s                              |       1                          |        2.20 s                              | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       86.35 ms                             |       4                          |      345.39 ms                             | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       25.13 ms                             |       1                          |       25.13 ms                             | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       14.35 ms                             |       1                          |       14.35 ms                             | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |        1.23 s                              |       1                          |        1.23 s                              | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |        1.01 s                              |       1                          |        1.01 s                              | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |      331.82 ms                             |       1                          |      331.82 ms                             | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |      174.60 ms                             |       1                          |      174.60 ms                             | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |      174.60 ms                             |       1                          |      174.60 ms                             | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |      138.75 ms                             |       1                          |      138.75 ms                             | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      171.27 ms                             |       1                          |      171.27 ms                             | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |      171.27 ms                             |       1                          |      171.27 ms                             | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      172.62 ms                             |       1                          |      172.62 ms                             | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |      122.09 ms                             |       1                          |      122.09 ms                             | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.76 ms                             |       1                          |        3.76 ms                             | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       90.24 ms                             |       1                          |       90.24 ms                             | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |       12.61 ms                             |       1                          |       12.61 ms                             | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       64.24 ms                             |       2                          |      128.47 ms                             | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       59.54 ms                             |       2                          |      119.07 ms                             | 
  │ │ │ └ sddk::inner                                                   |       59.42 ms                             |       2                          |      118.85 ms                             | 
  │ │ │   ├ sddk::inner|local                                           |       19.86 μs                             |       2                          |       39.73 μs                             | 
  │ │ │   ├ sddk::inner|device_copy                                     |       25.55 ms                             |       4                          |      102.20 ms                             | 
  │ │ │   ├ sddk::inner|store                                           |      692.05 μs                             |       4                          |        2.77 ms                             | 
  │ │ │   └ sddk::inner|mpi                                             |        6.91 ms                             |       2                          |       13.82 ms                             | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      116.17 ms                             |       1                          |      116.17 ms                             | 
  │ │ └ sddk::transform                                                 |       36.03 ms                             |       1                          |       36.03 ms                             | 
  │ │   ├ sddk::transform|init                                          |       13.45 μs                             |       1                          |       13.45 μs                             | 
  │ │   └ sddk::transform|local                                         |       18.08 μs                             |       1                          |       18.08 μs                             | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      470.00 ns                             |       1                          |      470.00 ns                             | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      142.29 s                              |       1                          |      142.29 s                              | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.16 ms                             |      31                          |       66.92 ms                             | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.30 s                              |      43                          |      142.04 s                              | 
  │ │ ├ sirius::Hamiltonian0                                            |        7.60 ms                             |      43                          |      326.86 ms                             | 
  │ │ │ ├ sirius::Local_operator                                        |        7.26 ms                             |      43                          |      312.37 ms                             | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |        1.50 ms                             |      43                          |       64.46 ms                             | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        4.31 ms                             |      43                          |      185.31 ms                             | 
  │ │ │ ├ sirius::Non_local_operator                                    |       61.02 μs                             |      86                          |        5.25 ms                             | 
  │ │ │ ├ sirius::D_operator::initialize                                |       84.28 μs                             |      43                          |        3.62 ms                             | 
  │ │ │ └ sirius::Q_operator::initialize                                |       70.64 μs                             |      43                          |        3.04 ms                             | 
  │ │ ├ sirius::Band::solve                                             |        2.63 s                              |      43                          |      112.95 s                              | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      212.23 μs                             |      43                          |        9.13 ms                             | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      204.95 μs                             |      43                          |        8.81 ms                             | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.39 μs                             |      43                          |      231.60 μs                             | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.62 s                              |      43                          |      112.52 s                              | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       69.13 ms                             |      43                          |        2.97 s                              | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        5.47 ms                             |     258                          |        1.41 s                              | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        2.31 ms                             |      43                          |       99.35 ms                             | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      421.47 μs                             |      43                          |       18.12 ms                             | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        1.18 ms                             |      43                          |       50.55 ms                             | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.52 s                              |      43                          |      108.40 s                              | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      217.51 ms                             |     208                          |       45.24 s                              | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |      154.45 ms                             |     208                          |       32.13 s                              | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |       28.73 ms                             |     208                          |        5.98 s                              | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      677.53 μs                             |     208                          |      140.93 ms                             | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        3.27 ms                             |      43                          |      140.49 ms                             | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |       23.58 ms                             |     208                          |        4.90 s                              | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      674.18 μs                             |     208                          |      140.23 ms                             | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |        3.25 ms                             |      43                          |      139.70 ms                             | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |       35.42 ms                             |     208                          |        7.37 s                              | 
  │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |       22.64 ms                             |     208                          |        4.71 s                              | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.65 ms                             |     208                          |      552.07 ms                             | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       22.97 ms                             |     208                          |        4.78 s                              | 
  │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        2.75 ms                             |     208                          |      571.85 ms                             | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       18.70 ms                             |     416                          |        7.78 s                              | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       82.83 ms                             |     208                          |       17.23 s                              | 
  │ │ │ │   │ ├ sddk::inner                                             |       10.69 ms                             |     373                          |        3.99 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|local                                     |       18.62 μs                             |     373                          |        6.95 ms                             | 
  │ │ │ │   │ │ ├ sddk::inner|device_copy                               |        4.47 ms                             |     746                          |        3.34 s                              | 
  │ │ │ │   │ │ ├ sddk::inner|store                                     |      102.52 μs                             |     746                          |       76.48 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|mpi                                       |        1.51 ms                             |     373                          |      563.57 ms                             | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |       30.35 ms                             |     208                          |        6.31 s                              | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       16.23 ms                             |     208                          |        3.38 s                              | 
  │ │ │ │   │ └ sddk::transform                                         |       21.52 ms                             |     165                          |        3.55 s                              | 
  │ │ │ │   │   ├ sddk::transform|init                                  |       19.34 μs                             |     165                          |        3.19 ms                             | 
  │ │ │ │   │   └ sddk::transform|local                                 |       51.05 μs                             |     495                          |       25.27 ms                             | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       25.46 ms                             |     208                          |        5.29 s                              | 
  │ │ │ │   │ └ sddk::inner                                             |       21.31 ms                             |     208                          |        4.43 s                              | 
  │ │ │ │   │   ├ sddk::inner|local                                     |       42.31 μs                             |     208                          |        8.80 ms                             | 
  │ │ │ │   │   ├ sddk::inner|device_copy                               |        7.92 ms                             |     416                          |        3.30 s                              | 
  │ │ │ │   │   ├ sddk::inner|store                                     |      230.91 μs                             |     416                          |       96.06 ms                             | 
  │ │ │ │   │   └ sddk::inner|mpi                                       |        4.95 ms                             |     208                          |        1.03 s                              | 
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |      165.37 ms                             |     208                          |       34.40 s                              | 
  │ │ │ │   ├ sirius::residuals                                         |       19.22 ms                             |     207                          |        3.98 s                              | 
  │ │ │ │   │ ├ sddk::transform                                         |       20.07 ms                             |     171                          |        3.43 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       15.88 μs                             |     171                          |        2.72 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       55.67 μs                             |     342                          |       19.04 ms                             | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        2.46 ms                             |     171                          |      420.33 ms                             | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       51.17 ms                             |      44                          |        2.25 s                              | 
  │ │ │ │     └ sddk::transform                                         |       49.76 ms                             |      45                          |        2.24 s                              | 
  │ │ │ │       ├ sddk::transform|init                                  |       12.68 μs                             |      45                          |      570.56 μs                             | 
  │ │ │ │       └ sddk::transform|local                                 |       16.71 μs                             |      46                          |      768.87 μs                             | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      591.86 ns                             |      43                          |       25.45 μs                             | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       34.23 μs                             |      43                          |        1.47 ms                             | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |        3.44 ms                             |      43                          |      147.91 ms                             | 
  │ │ ├ sirius::Density::generate                                       |      298.59 ms                             |      43                          |       12.84 s                              | 
  │ │ │ ├ sirius::Density::generate_valence                             |      294.66 ms                             |      43                          |       12.67 s                              | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       69.31 ms                             |      43                          |        2.98 s                              | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       62.40 μs                             |      43                          |        2.68 ms                             | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |        1.18 ms                             |       2                          |        2.36 ms                             | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       58.09 ms                             |      43                          |        2.50 s                              | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       61.28 ms                             |      43                          |        2.64 s                              | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.50 μs                             |      43                          |      408.48 μs                             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        2.31 ms                             |      43                          |       99.28 ms                             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       58.42 ms                             |      43                          |        2.51 s                              | 
  │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        7.01 ms                             |      43                          |      301.40 ms                             | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      574.09 ns                             |      43                          |       24.69 μs                             | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      104.17 ms                             |      43                          |        4.48 s                              | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.40 ms                             |      43                          |      103.38 ms                             | 
  │ │ │ │ └ sirius::Density::augment                                    |       20.06 ms                             |      43                          |      862.39 ms                             | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       19.89 ms                             |      43                          |      855.32 ms                             | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      280.79 ns                             |      43                          |       12.07 μs                             | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |        1.25 ms                             |      43                          |       53.92 ms                             | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        2.68 ms                             |      43                          |      115.16 ms                             | 
  │ │ ├ sirius::Density::mix                                            |      131.91 ms                             |      43                          |        5.67 s                              | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      255.79 μs                             |      43                          |       11.00 ms                             | 
  │ │ │ └ sirius::Density::mixer_output                                 |        3.80 ms                             |      43                          |      163.28 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        3.61 ms                             |      43                          |      155.02 ms                             | 
  │ │ ├ sirius::Potential::generate                                     |      186.63 ms                             |      43                          |        8.02 s                              | 
  │ │ │ ├ sirius::Potential::poisson                                    |       64.02 ms                             |      43                          |        2.75 s                              | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        9.68 ms                             |      43                          |      416.07 ms                             | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |        4.22 ms                             |      43                          |      181.56 ms                             | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.08 ms                             |      43                          |      175.25 ms                             | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.07 ms                             |      43                          |      175.19 ms                             | 
  │ │ │ ├ sirius::Periodic_function::add                                |      235.19 μs                             |      86                          |       20.23 ms                             | 
  │ │ │ ├ sirius::Potential::xc                                         |       97.33 ms                             |      43                          |        4.19 s                              | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       97.33 ms                             |      43                          |        4.19 s                              | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        1.61 ms                             |     215                          |      346.53 ms                             | 
  │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |        2.51 ms                             |     387                          |      972.12 ms                             | 
  │ │ │ │   ├ sirius::gradient                                          |        5.45 ms                             |      43                          |      234.43 ms                             | 
  │ │ │ │   │ └ sirius::Smooth_periodic_function                        |        1.73 ms                             |     129                          |      222.59 ms                             | 
  │ │ │ │   ├ sirius::dot                                               |        2.80 ms                             |      43                          |      120.53 ms                             | 
  │ │ │ │   │ └ sirius::Smooth_periodic_function                        |        2.57 ms                             |      43                          |      110.38 ms                             | 
  │ │ │ │   └ sirius::divergence                                        |       19.70 ms                             |      43                          |      847.16 ms                             | 
  │ │ │ │     └ sirius::Smooth_periodic_function                        |        2.42 ms                             |      43                          |      104.10 ms                             | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.29 ms                             |      43                          |      141.37 ms                             | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       20.96 ms                             |      43                          |      901.18 ms                             | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      230.14 ns                             |      43                          |        9.90 μs                             | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      296.53 ns                             |      43                          |       12.75 μs                             | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.28 ms                             |      43                          |       98.21 ms                             | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.14 ms                             |     301                          |        1.25 s                              | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        3.99 ms                             |     301                          |        1.20 s                              | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        3.99 ms                             |     301                          |        1.20 s                              | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.22 ms                             |     129                          |      543.81 ms                             | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.08 ms                             |     129                          |      525.85 ms                             | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.03 ms                             |      43                          |      173.19 ms                             | 
  │ │ └ sirius::Density::get_magnetisation                              |      186.78 μs                             |      43                          |        8.03 ms                             | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |      183.22 μs                             |      43                          |        7.88 ms                             | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.36 ms                             |       2                          |       10.71 ms                             | 
  │ ├ sirius::Periodic_function|inner                                   |        4.34 ms                             |       6                          |       26.03 ms                             | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.03 ms                             |       6                          |       24.18 ms                             | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.03 ms                             |       6                          |       24.18 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.61 ms                             |       3                          |       13.82 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.17 ms                             |       3                          |       12.51 ms                             | 
  ├ sirius::Periodic_function|inner                                     |        4.34 ms                             |       2                          |        8.69 ms                             | 
  │ └ sirius::Periodic_function|inner_local                             |        3.96 ms                             |       2                          |        7.92 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        3.96 ms                             |       2                          |        7.92 ms                             | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.53 ms                             |       1                          |        4.53 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.08 ms                             |       1                          |        4.08 ms                             | 
  ├ sirius::finalize                                                    |      420.04 ms                             |       1                          |      420.04 ms                             | 
  ├ sirius::Band::initialize_subspace|kp|wf                             |                        14.31 ms            |                   1              |                        14.31 ms            | 
  ├ sirius::Unit_cell::get_symmetry                                     |                         8.63 ms            |                   2              |                        17.26 ms            | 
  ├ sirius::Local_operator                                              |                         6.75 ms            |                  46              |                       310.71 ms            | 
  ├ sirius::Unit_cell_symmetry                                          |                         7.93 ms            |                   2              |                        15.86 ms            | 
  ├ sirius::Unit_cell_symmetry|spg                                      |                         7.70 ms            |                   2              |                        15.40 ms            | 
  ├ sirius::inner                                                       |                         4.28 ms            |                 598              |                         2.56 s             | 
  ├ sirius::Beta_projectors_base::inner|comm                            |                         3.26 ms            |                 255              |                       832.23 ms            | 
  ├ sirius::Unit_cell::find_nearest_neighbours                          |                         9.54 ms            |                   2              |                        19.08 ms            | 
  ├ sirius::Smooth_periodic_function::gather_f_pw                       |                         5.33 ms            |                   2              |                        10.65 ms            | 
  ├ sirius::Radial_integrals|vloc                                       |                         5.08 ms            |                   2              |                        10.17 ms            | 
  ├ sirius::Smooth_periodic_function::fft_transform                     |                         2.99 ms            |                 875              |                         2.62 s             | 
  ├ sirius::Density::mixer_input                                        |                       214.05 μs            |                  45              |                         9.63 ms            | 
  ├ sirius::Hamiltonian_k                                               |                       393.52 μs            |                  46              |                        18.10 ms            | 
  ├ sirius::Beta_projectors_base::prepare                               |                        96.86 μs            |                  91              |                         8.81 ms            | 
  ├ sirius::gradient                                                    |                         1.94 ms            |                  46              |                        89.31 ms            | 
  ├ sirius::Radial_integrals|beta                                       |                         3.63 ms            |                   2              |                         7.26 ms            | 
  ├ sirius::Periodic_function::integrate                                |                         4.14 ms            |                  46              |                       190.64 ms            | 
  ├ sirius::K_point_set::sync_band                                      |                        58.74 μs            |                  90              |                         5.29 ms            | 
  ├ sirius::K_point::update                                             |                         4.11 ms            |                   1              |                         4.11 ms            | 
  ├ sirius::Beta_projectors_base::generate                              |                         2.58 ms            |                 255              |                       658.60 ms            | 
  ├ sirius::dot                                                         |                       751.10 μs            |                  46              |                        34.55 ms            | 
  ├ sirius::Radial_integrals|rho_core_pseudo                            |                         1.09 ms            |                   2              |                         2.18 ms            | 
  ├ sirius::Beta_projectors                                             |                         1.71 ms            |                   1              |                         1.71 ms            | 
  ├ sirius::Q_operator::initialize                                      |                         1.10 ms            |                  46              |                        50.57 ms            | 
  ├ sirius::Simulation_context::init_atoms_to_grid_idx                  |                         1.03 ms            |                   1              |                         1.03 ms            | 
  ├ sirius::Radial_integrals|rho_pseudo                                 |                       963.61 μs            |                   1              |                       963.61 μs            | 
  ├ sirius::Beta_projectors::generate_pw_coefs_t                        |                       901.68 μs            |                   1              |                       901.68 μs            | 
  ├ sirius::D_operator::initialize                                      |                       596.46 μs            |                  46              |                        27.44 ms            | 
  ├ sirius::Periodic_function::add                                      |                       201.27 μs            |                  92              |                        18.52 ms            | 
  ├ sirius::Local_operator::prepare_k                                   |                       206.28 μs            |                  46              |                         9.49 ms            | 
  ├ sirius::Unit_cell_symmetry|equiv                                    |                       219.40 μs            |                   2              |                       438.80 μs            | 
  ├ sirius::Non_local_operator                                          |                        61.77 μs            |                  92              |                         5.68 ms            | 
  ├ sirius::K_point::K_point                                            |                         9.41 μs            |                   2              |                        18.83 μs            | 
  ├ sirius::Field4D::symmetrize                                         |                       380.96 ns            |                  90              |                        34.29 μs            | 
  ├ sirius::Unit_cell_symmetry|mag                                      |                         2.11 μs            |                   2              |                         4.23 μs            | 
  ├ sddk::wf_inner|scale_back                                           |                       381.21 ns            |                 584              |                       222.62 μs            | 
  ├ sirius::Beta_projectors_base::dismiss                               |                       556.05 ns            |                  91              |                        50.60 μs            | 
  ├ sddk::wf_inner|scale                                                |                       210.40 ns            |                 584              |                       122.87 μs            | 
  └ sirius::Potential::generate_PAW_effective_potential                 |                       265.41 ns            |                  46              |                        12.21 μs            | 
  ====================================================================================================================================================================================================
```
