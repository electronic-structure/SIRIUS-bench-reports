# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs 8be4a3d847d7cac2fa4e252581562d3d44ebcb3a
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      180.47 s  →      134.11 s   (-25.69%) |       1   →       1              |      180.47 s  →      134.11 s   (-25.69%) | 
  ├ sirius::initialize                                                  |        2.78 s                              |       1                          |        2.78 s                              | 
  ├ sirius::DFT_ground_state::scf_loop                                  |                       124.42 s             |                   1              |                       124.42 s             | 
  ├ sirius::Band::solve                                                 |                         2.57 s             |                  27              |                        69.39 s             | 
  ├ sirius::Band::diag_pseudo_potential_davidson                        |                         2.35 s             |                  27              |                        63.39 s             | 
  ├ sirius::Density::generate                                           |                       761.14 ms            |                  27              |                        20.55 s             | 
  ├ sirius::Density::generate_valence                                   |                       404.92 ms            |                  27              |                        10.93 s             | 
  ├ sddk::orthogonalize                                                 |                        31.26 ms            |                 339              |                        10.60 s             | 
  ├ sirius::Field4D::symmetrize                                         |                       263.76 ms            |                  54              |                        14.24 s             | 
  ├ sirius::symmetrize_function|fpw                                     |                       263.75 ms            |                  54              |                        14.24 s             | 
  ├ sirius::symmetrize_function|fpw|local                               |                       214.38 ms            |                  54              |                        11.58 s             | 
  ├ sirius::Density::add_k_point_contribution_rg                        |                       163.95 ms            |                  27              |                         4.43 s             | 
  ├ sirius::Density::mix                                                |                       163.69 ms            |                  27              |                         4.42 s             | 
  ├ Eigensolver_cuda|zheevdx                                            |                        12.50 ms            |                 339              |                         4.24 s             | 
  ├ sirius::Band::diag_pseudo_potential_davidson|update_phi             |                        41.81 ms            |                  99              |                         4.14 s             | 
+ ├ sirius::Simulation_context::initialize                              |        3.81 s  →        2.86 s   (-25.06%) |       1   →       1              |        3.81 s  →        2.86 s   (-25.06%) | 
  │ ├ sirius::Simulation_context::init_comm                             |      315.83 μs                             |       1                          |      315.83 μs                             | 
  │ ├ sirius::Unit_cell::initialize                                     |        1.08 s                              |       1                          |        1.08 s                              | 
  │ │ ├ sirius::Atom_type::init                                         |      533.59 ms                             |       2                          |        1.07 s                              | 
  │ │ └ sirius::Unit_cell::update                                       |       16.66 ms                             |       1                          |       16.66 ms                             | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.00 ms                             |       1                          |        6.00 ms                             | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       10.62 ms                             |       1                          |       10.62 ms                             | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       10.59 ms                             |       1                          |       10.59 ms                             | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        5.19 ms                             |       1                          |        5.19 ms                             | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms                             |       1                          |        2.32 ms                             | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       99.94 μs                             |       1                          |       99.94 μs                             | 
  │ └ sirius::Simulation_context::update                                |        2.69 s                              |       1                          |        2.69 s                              | 
  │   ├ sirius::Unit_cell::update                                       |       11.82 ms                             |       1                          |       11.82 ms                             | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.46 ms                             |       1                          |        4.46 ms                             | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        7.33 ms                             |       1                          |        7.33 ms                             | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        7.31 ms                             |       1                          |        7.31 ms                             | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        4.83 ms                             |       1                          |        4.83 ms                             | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms                             |       1                          |        2.32 ms                             | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       98.16 μs                             |       1                          |       98.16 μs                             | 
  │   ├ sirius::Radial_integrals|aug                                    |       63.58 ms                             |       2                          |      127.17 ms                             | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.16 ms                             |       2                          |       10.32 ms                             | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.48 ms                             |       1                          |        4.48 ms                             | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.79 ms                             |       2                          |       43.58 ms                             | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.77 ms                             |       2                          |       29.54 ms                             | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.56 ms                             |       4                          |       78.24 ms                             | 
  │   ├ sddk::Gvec::init                                                |      178.35 ms                             |       2                          |      356.71 ms                             | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      135.61 ms                             |       2                          |      271.23 ms                             | 
  │   ├ sddk::Gvec_shells                                               |      178.99 ms                             |       1                          |      178.99 ms                             | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.32 ms                             |       1                          |        1.32 ms                             | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      298.86 ms                             |       2                          |      597.72 ms                             | 
  ├ sirius::K_point_set::create_k_mesh                                  |       35.85 ms                             |       1                          |       35.85 ms                             | 
  │ ├ sirius::K_point::K_point                                          |        2.62 μs                             |       4                          |       10.48 μs                             | 
  │ └ sirius::K_point_set::initialize                                   |       35.76 ms                             |       1                          |       35.76 ms                             | 
  │   └ sirius::K_point::initialize                                     |       35.67 ms                             |       1                          |       35.67 ms                             | 
  │     ├ sirius::K_point::generate_gkvec                               |       18.33 ms                             |       1                          |       18.33 ms                             | 
  │     │ └ sddk::Gvec::init                                            |        8.18 ms                             |       1                          |        8.18 ms                             | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        9.64 μs                             |       1                          |        9.64 μs                             | 
  │     └ sirius::K_point::update                                       |       12.52 ms                             |       1                          |       12.52 ms                             | 
  │       └ sirius::Beta_projectors                                     |        6.18 ms                             |       1                          |        6.18 ms                             | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.59 ms                             |       1                          |        3.59 ms                             | 
  ├ sirius::Smooth_periodic_function                                    |        5.23 ms                             |       2                          |       10.46 ms                             | 
  ├ sirius::initialize                                                  |                         2.77 s             |                   1              |                         2.77 s             | 
  ├ sirius::Density::add_k_point_contribution_dm                        |                       100.60 ms            |                  27              |                         2.72 s             | 
  ├ sirius::Simulation_context::update                                  |                         2.70 s             |                   1              |                         2.70 s             | 
  ├ sddk::orthogonalize|transform                                       |                         7.61 ms            |                 339              |                         2.58 s             | 
  ├ sirius::residuals                                                   |                         7.67 ms            |                 328              |                         2.51 s             | 
  ├ sirius::Density::augment                                            |                        88.38 ms            |                  27              |                         2.39 s             | 
  ├ sirius::Density::generate_rho_aug                                   |                        88.16 ms            |                  27              |                         2.38 s             | 
  ├ sirius::Density::symmetrize_density_matrix                          |                        80.76 ms            |                  27              |                         2.18 s             | 
  ├ sirius::Band::initialize_subspace                                   |                         1.86 s             |                   1              |                         1.86 s             | 
  ├ sirius::Band::initialize_subspace|kp                                |                         1.84 s             |                   1              |                         1.84 s             | 
  ├ sddk::orthogonalize|tmtrx                                           |                         5.06 ms            |                 339              |                         1.72 s             | 
  ├ sddk::Gvec_shells::remap_forward                                    |                        24.90 ms            |                  54              |                         1.34 s             | 
  ├ sirius::Potential::generate                                         |                       662.47 ms            |                  28              |                        18.55 s             | 
  ├ sirius::Hamiltonian_k::apply_h_s                                    |                       106.30 ms            |                 340              |                        36.14 s             | 
  ├ sddk::Gvec_shells::remap_backward                                   |                        23.32 ms            |                  54              |                         1.26 s             | 
  ├ sirius::Augmentation_operator::generate_pw_coeffs                   |                       299.84 ms            |                   2              |                       599.68 ms            | 
  ├ sirius::Potential::generate_PAW_effective_potential                 |                       401.04 ms            |                  28              |                        11.23 s             | 
  ├ sirius::Density::get_magnetisation                                  |                        14.14 ms            |                  27              |                       381.84 ms            | 
  ├ sirius::Density::compute_atomic_mag_mom                             |                        14.14 ms            |                  27              |                       381.68 ms            | 
  ├ sirius::normalized_preconditioned_residuals                         |                         1.18 ms            |                 312              |                       368.75 ms            | 
  ├ sddk::Gvec::init                                                    |                       124.77 ms            |                   3              |                       374.31 ms            | 
  ├ sirius::Local_operator::apply_h                                     |                        40.79 ms            |                 340              |                        13.87 s             | 
  ├ sddk::Gvec::find_gvec_shells                                        |                       140.41 ms            |                   2              |                       280.81 ms            | 
  ├ sirius::finalize                                                    |                       225.15 ms            |                   1              |                       225.15 ms            | 
  ├ sirius::Non_local_operator::apply                                   |                        19.38 ms            |                 680              |                        13.18 s             | 
  ├ sirius::Density::mixer_output                                       |                         6.51 ms            |                  27              |                       175.78 ms            | 
  ├ sddk::Gvec_shells                                                   |                       170.48 ms            |                   1              |                       170.48 ms            | 
  ├ sirius::Density::initial_density                                    |                       161.38 ms            |                   1              |                       161.38 ms            | 
  ├ sirius::Hamiltonian_k::get_h_o_diag                                 |                         5.95 ms            |                  27              |                       160.64 ms            | 
+ ├ sirius::Potential                                                   |      172.42 ms →      149.97 ms  (-13.02%) |       1   →       1              |      172.42 ms →      149.97 ms  (-13.02%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.86 ms                             |       6                          |       35.16 ms                             | 
  │ └ sirius::Potential::update                                         |      136.52 ms                             |       1                          |      136.52 ms                             | 
  │   └ sirius::Potential::generate_local_potential                     |      135.72 ms                             |       1                          |      135.72 ms                             | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      110.57 ms                             |       1                          |      110.57 ms                             | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |       24.60 ms                             |       1                          |       24.60 ms                             | 
  ├ sirius::Radial_integrals|aug                                        |                        66.46 ms            |                   2              |                       132.91 ms            | 
- ├ sirius::Density                                                     |      139.97 ms →      134.84 ms   (-3.66%) |       1   →       2   (+100.00%) |      139.97 ms →      269.69 ms  (+92.68%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.15 ms                             |       2                          |       10.29 ms                             | 
  │ └ sirius::Density::update                                           |      129.40 ms                             |       1                          |      129.40 ms                             | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      128.97 ms                             |       1                          |      128.97 ms                             | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      110.14 ms                             |       1                          |      110.14 ms                             | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |       18.37 ms                             |       1                          |       18.37 ms                             | 
  ├ sirius::Density::initial_density                                    |      174.40 ms                             |       1                          |      174.40 ms                             | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      108.98 ms                             |       1                          |      108.98 ms                             | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |       11.90 ms                             |       2                          |       23.80 ms                             | 
  │ └ sirius::Periodic_function::integrate                              |        9.85 ms                             |       1                          |        9.85 ms                             | 
  ├ sirius::Potential::generate                                         |      703.50 ms                             |       1                          |      703.50 ms                             | 
  │ ├ sirius::Potential::poisson                                        |      137.26 ms                             |       1                          |      137.26 ms                             | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       19.15 ms                             |       1                          |       19.15 ms                             | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.37 ms                             |       1                          |       10.37 ms                             | 
  │ │   └ sirius::Periodic_function|inner_local                         |        9.81 ms                             |       1                          |        9.81 ms                             | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.81 ms                             |       1                          |        9.81 ms                             | 
  │ ├ sirius::Periodic_function::add                                    |      550.94 μs                             |       2                          |        1.10 ms                             | 
  │ ├ sirius::Potential::xc                                             |       59.83 ms                             |       1                          |       59.83 ms                             | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       59.82 ms                             |       1                          |       59.82 ms                             | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.69 ms                             |       2                          |       11.38 ms                             | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.88 ms                             |       1                          |        5.88 ms                             | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.87 ms                             |       1                          |        5.87 ms                             | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       93.48 ms                             |       1                          |       93.48 ms                             | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      404.58 ms                             |       1                          |      404.58 ms                             | 
  ├ sirius::Potential::poisson                                          |                       124.71 ms            |                  28              |                         3.49 s             | 
  ├ sirius::Beta_projectors_base::inner                                 |                        24.69 ms            |                 367              |                         9.06 s             | 
  ├ sirius::Potential::update                                           |                       120.27 ms            |                   1              |                       120.27 ms            | 
  ├ sirius::Potential::generate_local_potential                         |                       119.54 ms            |                   1              |                       119.54 ms            | 
  ├ sirius::Density::update                                             |                       124.35 ms            |                   2              |                       248.69 ms            | 
  ├ sirius::Density::generate_pseudo_core_charge_density                |                       123.94 ms            |                   2              |                       247.88 ms            | 
  ├ sirius::Simulation_context::make_periodic_function                  |                       108.31 ms            |                   4              |                       433.25 ms            | 
  ├ sirius::Potential::generate_D_operator_matrix                       |                        91.04 ms            |                  28              |                         2.55 s             | 
  ├ sirius::Band::set_subspace_mtrx                                     |                         8.27 ms            |                 341              |                         2.82 s             | 
  ├ sddk::wf_inner                                                      |                         5.86 ms            |                 992              |                         5.81 s             | 
  ├ sddk::wf_inner|pw                                                   |                         4.75 ms            |                 992              |                         4.71 s             | 
  ├ sirius::Unit_cell::initialize                                       |                        78.65 ms            |                   1              |                        78.65 ms            | 
  ├ sirius::Radial_integrals|atomic_wfs                                 |                        19.63 ms            |                   4              |                        78.50 ms            | 
  ├ Eigensolver_cuda|zhegvdx                                            |                        62.11 ms            |                   1              |                        62.11 ms            | 
  ├ sirius::Atom_type::init                                             |                        27.16 ms            |                   2              |                        54.32 ms            | 
  ├ sirius::K_point::generate_atomic_wave_functions                     |                        51.82 ms            |                   1              |                        51.82 ms            | 
  ├ sirius::Radial_integrals|vloc                                       |                        21.73 ms            |                   2              |                        43.47 ms            | 
  ├ sirius::Potential::xc                                               |                        35.78 ms            |                  28              |                         1.00 s             | 
  ├ sirius::Potential::xc_rg_nonmagnetic                                |                        33.42 ms            |                  28              |                       935.80 ms            | 
  ├ sirius::Simulation_context::init_comm                               |                        35.91 ms            |                   1              |                        35.91 ms            | 
  ├ sirius::K_point_set::create_k_mesh                                  |                        35.90 ms            |                   1              |                        35.90 ms            | 
  ├ sirius::K_point_set::initialize                                     |                        35.74 ms            |                   1              |                        35.74 ms            | 
  ├ sirius::K_point::initialize                                         |                        35.65 ms            |                   1              |                        35.65 ms            | 
  ├ sirius::inner                                                       |                        10.58 ms            |                 713              |                         7.54 s             | 
  ├ sddk::wf_trans                                                      |                        11.71 ms            |                 796              |                         9.32 s             | 
  ├ sddk::wf_trans|pw                                                   |                         5.17 ms            |                1.80 K            |                         9.32 s             | 
  ├ sirius::Density::mixer_input                                        |                         1.10 ms            |                  27              |                        29.68 ms            | 
  ├ sirius::Radial_integrals|beta                                       |                        14.77 ms            |                   2              |                        29.54 ms            | 
  ├ sirius::Potential::xc_rg_nonmagnetic|libxc                          |                        12.37 ms            |                  56              |                       692.81 ms            | 
  ├ sirius::Unit_cell::update                                           |                        18.11 ms            |                   2              |                        36.21 ms            | 
  ├ sirius::Band::initialize_subspace|kp|wf                             |                        21.00 ms            |                   1              |                        21.00 ms            | 
  ├ sirius::Hamiltonian_k                                               |                       836.73 μs            |                  28              |                        23.43 ms            | 
  ├ sirius::Beta_projectors_base::prepare                               |                       342.88 μs            |                  55              |                        18.86 ms            | 
  ├ sirius::K_point::generate_gkvec                                     |                        18.26 ms            |                   1              |                        18.26 ms            | 
  ├ sirius::Unit_cell::get_symmetry                                     |                        12.71 ms            |                   2              |                        25.43 ms            | 
  ├ sirius::Unit_cell_symmetry                                          |                        12.69 ms            |                   2              |                        25.38 ms            | 
  ├ sirius::K_point::update                                             |                        12.59 ms            |                   1              |                        12.59 ms            | 
  ├ sirius::K_point_set::find_band_occupancies                          |                       464.34 μs            |                  27              |                        12.54 ms            | 
- ├ sirius::Hamiltonian0                                                |        8.38 ms →        8.16 ms   (-2.66%) |       1   →      28   (+2700.00%) |        8.38 ms →      228.43 ms (+2625.44%) | 
  │ ├ sirius::Local_operator                                            |        8.02 ms                             |       1                          |        8.02 ms                             | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.75 ms                             |       1                          |        4.75 ms                             | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.34 ms                             |       1                          |        2.34 ms                             | 
  │ ├ sirius::Non_local_operator                                        |       63.03 μs                             |       2                          |      126.05 μs                             | 
  │ ├ sirius::D_operator::initialize                                    |      106.68 μs                             |       1                          |      106.68 μs                             | 
  │ └ sirius::Q_operator::initialize                                    |       74.87 μs                             |       1                          |       74.87 μs                             | 
  ├ sirius::Band::initialize_subspace                                   |        1.85 s                              |       1                          |        1.85 s                              | 
  │ ├ sirius::Hamiltonian_k                                             |       18.65 ms                             |       1                          |       18.65 ms                             | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      172.81 μs                             |       1                          |      172.81 μs                             | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       18.47 ms                             |       1                          |       18.47 ms                             | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.83 s                              |       1                          |        1.83 s                              | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      126.00 ms                             |       4                          |      504.00 ms                             | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       52.29 ms                             |       1                          |       52.29 ms                             | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.00 ms                             |       1                          |       21.00 ms                             | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      637.27 ms                             |       1                          |      637.27 ms                             | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      297.12 ms                             |       1                          |      297.12 ms                             | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.83 μs                             |       1                          |        3.83 μs                             | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.99 μs                             |       1                          |        2.99 μs                             | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      436.00 ns                             |       1                          |      436.00 ns                             | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      466.00 ns                             |       1                          |      466.00 ns                             | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.22 ms                             |       1                          |        9.22 ms                             | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      121.69 ms                             |       1                          |      121.69 ms                             | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      104.60 ms                             |       2                          |      209.20 ms                             | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       38.37 ms                             |       2                          |       76.75 ms                             | 
  │ │ │ └ sddk::inner                                                   |       37.84 ms                             |       2                          |       75.68 ms                             | 
  │ │ │   └ sddk::inner|local                                           |       22.33 μs                             |       2                          |       44.66 μs                             | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       56.13 ms                             |       1                          |       56.13 ms                             | 
  │ │ └ sddk::transform                                                 |       31.54 ms                             |       1                          |       31.54 ms                             | 
  │ │   ├ sddk::transform|init                                          |       10.72 μs                             |       1                          |       10.72 μs                             | 
  │ │   └ sddk::transform|local                                         |       10.65 μs                             |       1                          |       10.65 μs                             | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      409.00 ns                             |       1                          |      409.00 ns                             | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      169.44 s                              |       1                          |      169.44 s                              | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.86 ms                             |      19                          |      111.28 ms                             | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.70 s                              |      36                          |      169.09 s                              | 
  │ │ ├ sirius::Hamiltonian0                                            |        4.89 ms                             |      36                          |      175.87 ms                             | 
  │ │ │ ├ sirius::Local_operator                                        |        4.51 ms                             |      36                          |      162.42 ms                             | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      988.12 μs                             |      36                          |       35.57 ms                             | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.64 ms                             |      36                          |       94.89 ms                             | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.28 μs                             |      72                          |        4.63 ms                             | 
  │ │ │ ├ sirius::D_operator::initialize                                |      101.31 μs                             |      36                          |        3.65 ms                             | 
  │ │ │ └ sirius::Q_operator::initialize                                |       75.72 μs                             |      36                          |        2.73 ms                             | 
  │ │ ├ sirius::Band::solve                                             |        2.57 s                              |      36                          |       92.42 s                              | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      161.78 μs                             |      36                          |        5.82 ms                             | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      155.12 μs                             |      36                          |        5.58 ms                             | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.06 μs                             |      36                          |      182.27 μs                             | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.50 s                              |      36                          |       90.13 s                              | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |      100.54 ms                             |      36                          |        3.62 s                              | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        8.34 ms                             |     216                          |        1.80 s                              | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        5.98 ms                             |      36                          |      215.31 ms                             | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      349.83 μs                             |      36                          |       12.59 ms                             | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.31 ms                             |      72                          |      166.00 ms                             | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.36 s                              |      36                          |       85.01 s                              | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      109.05 ms                             |     360                          |       39.26 s                              | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       42.04 ms                             |     360                          |       15.13 s                              | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.95 μs                             |     360                          |      700.91 μs                             | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.60 μs                             |     360                          |      577.28 μs                             | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      320.76 ns                             |     360                          |      115.47 μs                             | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      381.82 ns                             |     360                          |      137.45 μs                             | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.36 ms                             |     360                          |        2.65 s                              | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       20.11 ms                             |     360                          |        7.24 s                              | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       19.77 ms                             |     720                          |       14.23 s                              | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       35.27 ms                             |     360                          |       12.70 s                              | 
  │ │ │ │   │ ├ sddk::inner                                             |        4.48 ms                             |     684                          |        3.07 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       20.20 μs                             |     684                          |       13.82 ms                             | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |        5.69 ms                             |     360                          |        2.05 s                              | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        8.34 ms                             |     360                          |        3.00 s                              | 
  │ │ │ │   │ └ sddk::transform                                         |       14.12 ms                             |     324                          |        4.58 s                              | 
  │ │ │ │   │   ├ sddk::transform|init                                  |       17.01 μs                             |     324                          |        5.51 ms                             | 
  │ │ │ │   │   └ sddk::transform|local                                 |       32.16 μs                             |     972                          |       31.26 ms                             | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        9.50 ms                             |     360                          |        3.42 s                              | 
  │ │ │ │   │ └ sddk::inner                                             |        8.62 ms                             |     360                          |        3.10 s                              | 
  │ │ │ │   │   └ sddk::inner|local                                     |       26.37 μs                             |     360                          |        9.49 ms                             | 
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       63.10 ms                             |     360                          |       22.72 s                              | 
  │ │ │ │   ├ sirius::residuals                                         |       13.95 ms                             |     349                          |        4.87 s                              | 
  │ │ │ │   │ ├ sddk::transform                                         |       12.90 ms                             |     335                          |        4.32 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       14.02 μs                             |     335                          |        4.70 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       34.02 μs                             |     670                          |       22.79 ms                             | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.40 ms                             |     335                          |      470.47 ms                             | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       53.40 ms                             |      38                          |        2.03 s                              | 
  │ │ │ │     └ sddk::transform                                         |       50.53 ms                             |      40                          |        2.02 s                              | 
  │ │ │ │       ├ sddk::transform|init                                  |       11.87 μs                             |      40                          |      474.72 μs                             | 
  │ │ │ │       └ sddk::transform|local                                 |       12.90 μs                             |      42                          |      541.94 μs                             | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      549.19 ns                             |      36                          |       19.77 μs                             | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       30.12 μs                             |      36                          |        1.08 ms                             | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      598.36 μs                             |      36                          |       21.54 ms                             | 
  │ │ ├ sirius::Density::generate                                       |      773.37 ms                             |      36                          |       27.84 s                              | 
  │ │ │ ├ sirius::Density::generate_valence                             |      402.32 ms                             |      36                          |       14.48 s                              | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.07 μs                             |      36                          |      290.41 μs                             | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.21 μs                             |      36                          |      259.72 μs                             | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       99.92 ms                             |      36                          |        3.60 s                              | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.57 μs                             |      36                          |      272.63 μs                             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.12 ms                             |      36                          |      256.24 ms                             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       90.94 ms                             |      36                          |        3.27 s                              | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      587.42 ns                             |      36                          |       21.15 μs                             | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      162.55 ms                             |      36                          |        5.85 s                              | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms                             |      36                          |       58.96 ms                             | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.39 ms                             |      36                          |        3.18 s                              | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.17 ms                             |      36                          |        3.17 s                              | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      276.67 ms                             |      36                          |        9.96 s                              | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      276.67 ms                             |      36                          |        9.96 s                              | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.70 ms                             |      36                          |      889.27 ms                             | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      228.07 ms                             |      36                          |        8.21 s                              | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       22.71 ms                             |      36                          |      817.61 ms                             | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       81.05 ms                             |      36                          |        2.92 s                              | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        9.77 ms                             |      36                          |      351.88 ms                             | 
  │ │ ├ sirius::Density::mix                                            |      222.83 ms                             |      36                          |        8.02 s                              | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      966.94 μs                             |      36                          |       34.81 ms                             | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.66 ms                             |     470                          |        5.01 s                              | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.40 ms                             |     470                          |        4.89 s                              | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.40 ms                             |     470                          |        4.89 s                              | 
  │ │ │ └ sirius::Density::mixer_output                                 |        7.50 ms                             |      36                          |      270.06 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        6.65 ms                             |      36                          |      239.30 ms                             | 
  │ │ ├ sirius::Potential::generate                                     |      689.60 ms                             |      36                          |       24.83 s                              | 
  │ │ │ ├ sirius::Potential::poisson                                    |      136.83 ms                             |      36                          |        4.93 s                              | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       18.91 ms                             |      36                          |      680.89 ms                             | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.05 ms                             |      36                          |      361.79 ms                             | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        9.87 ms                             |      36                          |      355.18 ms                             | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        9.87 ms                             |      36                          |      355.16 ms                             | 
  │ │ │ ├ sirius::Periodic_function::add                                |      550.11 μs                             |      72                          |       39.61 ms                             | 
  │ │ │ ├ sirius::Potential::xc                                         |       53.87 ms                             |      36                          |        1.94 s                              | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       53.87 ms                             |      36                          |        1.94 s                              | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.02 ms                             |      72                          |      217.40 ms                             | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.57 ms                             |      36                          |      200.47 ms                             | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.54 ms                             |      36                          |      235.49 ms                             | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.87 ms                             |      36                          |        3.27 s                              | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      399.09 ms                             |      36                          |       14.37 s                              | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      301.61 ms                             |      36                          |       10.86 s                              | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      301.61 ms                             |      36                          |       10.86 s                              | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       46.34 ms                             |      36                          |        1.67 s                              | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      227.70 ms                             |      36                          |        8.20 s                              | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.75 ms                             |      36                          |      855.03 ms                             | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       24.54 ms                             |      36                          |      883.62 ms                             | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.11 ms                             |     252                          |        2.55 s                              | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.78 ms                             |     252                          |        2.47 s                              | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.78 ms                             |     252                          |        2.47 s                              | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.47 ms                             |     108                          |        1.13 s                              | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.18 ms                             |     108                          |        1.10 s                              | 
  │ │ ├ sirius::Periodic_function::integrate                            |        9.92 ms                             |      36                          |      357.02 ms                             | 
  │ │ └ sirius::Density::get_magnetisation                              |      111.89 μs                             |      36                          |        4.03 ms                             | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |      106.57 μs                             |      36                          |        3.84 ms                             | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        7.02 ms                             |       2                          |       14.04 ms                             | 
  │ ├ sirius::Periodic_function|inner                                   |        9.96 ms                             |       6                          |       59.79 ms                             | 
  │ │ └ sirius::Periodic_function|inner_local                           |        9.91 ms                             |       6                          |       59.43 ms                             | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        9.90 ms                             |       6                          |       59.43 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.26 ms                             |       3                          |       30.78 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.17 ms                             |       3                          |       30.51 ms                             | 
  ├ sirius::Periodic_function|inner                                     |        9.99 ms                             |       2                          |       19.97 ms                             | 
  │ └ sirius::Periodic_function|inner_local                             |        9.98 ms                             |       2                          |       19.95 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.98 ms                             |       2                          |       19.95 ms                             | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.41 ms                             |       1                          |       10.41 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.40 ms                             |       1                          |       10.40 ms                             | 
  ├ sirius::finalize                                                    |      195.20 ms                             |       1                          |      195.20 ms                             | 
  ├ sirius::Radial_integrals|rho_core_pseudo                            |                         5.15 ms            |                   2              |                        10.30 ms            | 
  ├ sirius::Periodic_function::integrate                                |                        10.14 ms            |                  28              |                       284.05 ms            | 
  ├ sirius::Smooth_periodic_function::gather_f_pw                       |                         4.79 ms            |                   2              |                         9.58 ms            | 
  ├ sirius::Beta_projectors_base::generate                              |                         7.33 ms            |                 367              |                         2.69 s             | 
  ├ sirius::Local_operator                                              |                         4.23 ms            |                  28              |                       118.43 ms            | 
  ├ sirius::Smooth_periodic_function::fft_transform                     |                         5.17 ms            |                 197              |                         1.02 s             | 
  ├ sirius::Unit_cell::find_nearest_neighbours                          |                         5.36 ms            |                   2              |                        10.72 ms            | 
  ├ sirius::Beta_projectors                                             |                         6.29 ms            |                   1              |                         6.29 ms            | 
  ├ sirius::Unit_cell_symmetry|spg                                      |                         5.17 ms            |                   2              |                        10.34 ms            | 
  ├ sirius::Radial_integrals|rho_pseudo                                 |                         4.48 ms            |                   1              |                         4.48 ms            | 
  ├ sirius::Beta_projectors::generate_pw_coefs_t                        |                         3.69 ms            |                   1              |                         3.69 ms            | 
  ├ sirius::K_point_set::sync_band                                      |                        61.62 μs            |                  54              |                         3.33 ms            | 
  ├ sirius::Q_operator::initialize                                      |                         2.47 ms            |                  28              |                        69.19 ms            | 
  ├ sirius::Unit_cell_symmetry|equiv                                    |                         2.34 ms            |                   2              |                         4.68 ms            | 
  ├ sirius::Simulation_context::init_atoms_to_grid_idx                  |                         1.31 ms            |                   1              |                         1.31 ms            | 
  ├ sirius::D_operator::initialize                                      |                         1.26 ms            |                  28              |                        35.39 ms            | 
  ├ sirius::Periodic_function::add                                      |                       456.34 μs            |                  56              |                        25.56 ms            | 
  ├ sirius::Local_operator::prepare_k                                   |                       167.00 μs            |                  28              |                         4.68 ms            | 
  ├ sirius::Non_local_operator                                          |                        64.52 μs            |                  56              |                         3.61 ms            | 
  ├ sirius::Unit_cell_symmetry|mag                                      |                       104.24 μs            |                   2              |                       208.49 μs            | 
  ├ sirius::K_point::K_point                                            |                         6.50 μs            |                   4              |                        26.02 μs            | 
  ├ sddk::matrix_storage::remap_forward                                 |                         1.67 μs            |                 367              |                       612.82 μs            | 
  ├ sddk::wf_inner|scale_back                                           |                       203.15 ns            |                 992              |                       201.53 μs            | 
  ├ sddk::matrix_storage::remap_backward                                |                       496.97 ns            |                 340              |                       168.97 μs            | 
  ├ sirius::Beta_projectors_base::dismiss                               |                       549.96 ns            |                  55              |                        30.25 μs            | 
  └ sddk::wf_inner|scale                                                |                       121.08 ns            |                 992              |                       120.11 μs            | 
  ====================================================================================================================================================================================================
```
