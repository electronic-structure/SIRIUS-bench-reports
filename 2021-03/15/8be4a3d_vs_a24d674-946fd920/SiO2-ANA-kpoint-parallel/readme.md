# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs 8be4a3d847d7cac2fa4e252581562d3d44ebcb3a
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      175.75 s  →      118.34 s   (-32.67%) |       1   →       1              |      175.75 s  →      118.34 s   (-32.67%) | 
  ├ sirius::initialize                                                  |        2.74 s                              |       1                          |        2.74 s                              | 
  ├ sirius::DFT_ground_state::scf_loop                                  |                       108.67 s             |                   1              |                       108.67 s             | 
  ├ sirius::Band::solve                                                 |                         2.70 s             |                  23              |                        62.04 s             | 
  ├ sirius::Band::diag_pseudo_potential_davidson                        |                         2.50 s             |                  23              |                        57.49 s             | 
  ├ sirius::Density::generate                                           |                       755.83 ms            |                  23              |                        17.38 s             | 
  ├ sddk::orthogonalize                                                 |                        32.40 ms            |                 301              |                         9.75 s             | 
  ├ sirius::Density::generate_valence                                   |                       404.56 ms            |                  23              |                         9.30 s             | 
  ├ sirius::Field4D::symmetrize                                         |                       258.23 ms            |                  46              |                        11.88 s             | 
  ├ sirius::symmetrize_function|fpw                                     |                       258.22 ms            |                  46              |                        11.88 s             | 
  ├ sirius::symmetrize_function|fpw|local                               |                       208.56 ms            |                  46              |                         9.59 s             | 
  ├ Eigensolver_cuda|zheevdx                                            |                        12.78 ms            |                 301              |                         3.85 s             | 
  ├ sirius::Band::diag_pseudo_potential_davidson|update_phi             |                        43.84 ms            |                  86              |                         3.77 s             | 
  ├ sirius::Density::add_k_point_contribution_rg                        |                       162.00 ms            |                  23              |                         3.73 s             | 
  ├ sirius::Density::mix                                                |                       159.68 ms            |                  23              |                         3.67 s             | 
+ ├ sirius::Simulation_context::initialize                              |        3.76 s  →        2.90 s   (-22.89%) |       1   →       1              |        3.76 s  →        2.90 s   (-22.89%) | 
  │ ├ sirius::Simulation_context::init_comm                             |      345.91 μs                             |       1                          |      345.91 μs                             | 
  │ ├ sirius::Unit_cell::initialize                                     |        1.09 s                              |       1                          |        1.09 s                              | 
  │ │ ├ sirius::Atom_type::init                                         |      534.42 ms                             |       2                          |        1.07 s                              | 
  │ │ └ sirius::Unit_cell::update                                       |       16.91 ms                             |       1                          |       16.91 ms                             | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.24 ms                             |       1                          |        6.24 ms                             | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       10.63 ms                             |       1                          |       10.63 ms                             | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       10.61 ms                             |       1                          |       10.61 ms                             | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        5.19 ms                             |       1                          |        5.19 ms                             | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms                             |       1                          |        2.33 ms                             | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      101.04 μs                             |       1                          |      101.04 μs                             | 
  │ └ sirius::Simulation_context::update                                |        2.64 s                              |       1                          |        2.64 s                              | 
  │   ├ sirius::Unit_cell::update                                       |       11.81 ms                             |       1                          |       11.81 ms                             | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.45 ms                             |       1                          |        4.45 ms                             | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        7.33 ms                             |       1                          |        7.33 ms                             | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        7.31 ms                             |       1                          |        7.31 ms                             | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        4.82 ms                             |       1                          |        4.82 ms                             | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms                             |       1                          |        2.33 ms                             | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       98.91 μs                             |       1                          |       98.91 μs                             | 
  │   ├ sirius::Radial_integrals|aug                                    |       68.36 ms                             |       2                          |      136.73 ms                             | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.17 ms                             |       2                          |       10.33 ms                             | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.54 ms                             |       1                          |        4.54 ms                             | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.80 ms                             |       2                          |       43.60 ms                             | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.76 ms                             |       2                          |       29.53 ms                             | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.72 ms                             |       4                          |       78.88 ms                             | 
  │   ├ sddk::Gvec::init                                                |      173.29 ms                             |       2                          |      346.57 ms                             | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      130.98 ms                             |       2                          |      261.96 ms                             | 
  │   ├ sddk::Gvec_shells                                               |      164.04 ms                             |       1                          |      164.04 ms                             | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.32 ms                             |       1                          |        1.32 ms                             | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      294.14 ms                             |       2                          |      588.28 ms                             | 
  ├ sirius::K_point_set::create_k_mesh                                  |       35.81 ms                             |       1                          |       35.81 ms                             | 
  │ ├ sirius::K_point::K_point                                          |        3.17 μs                             |       4                          |       12.67 μs                             | 
  │ └ sirius::K_point_set::initialize                                   |       35.72 ms                             |       1                          |       35.72 ms                             | 
  │   └ sirius::K_point::initialize                                     |       35.63 ms                             |       1                          |       35.63 ms                             | 
  │     ├ sirius::K_point::generate_gkvec                               |       18.32 ms                             |       1                          |       18.32 ms                             | 
  │     │ └ sddk::Gvec::init                                            |        8.19 ms                             |       1                          |        8.19 ms                             | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        9.36 μs                             |       1                          |        9.36 μs                             | 
  │     └ sirius::K_point::update                                       |       12.54 ms                             |       1                          |       12.54 ms                             | 
  │       └ sirius::Beta_projectors                                     |        6.29 ms                             |       1                          |        6.29 ms                             | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.72 ms                             |       1                          |        3.72 ms                             | 
  ├ sirius::Smooth_periodic_function                                    |        5.20 ms                             |       2                          |       10.40 ms                             | 
  ├ sirius::initialize                                                  |                         2.71 s             |                   1              |                         2.71 s             | 
  ├ sirius::Simulation_context::update                                  |                         2.68 s             |                   1              |                         2.68 s             | 
  ├ sddk::orthogonalize|transform                                       |                         7.82 ms            |                 301              |                         2.35 s             | 
  ├ sirius::Density::add_k_point_contribution_dm                        |                       100.19 ms            |                  23              |                         2.30 s             | 
  ├ sirius::residuals                                                   |                         7.67 ms            |                 291              |                         2.23 s             | 
  ├ sirius::Density::augment                                            |                        88.40 ms            |                  23              |                         2.03 s             | 
  ├ sirius::Density::generate_rho_aug                                   |                        88.18 ms            |                  23              |                         2.03 s             | 
  ├ sirius::Density::symmetrize_density_matrix                          |                        81.25 ms            |                  23              |                         1.87 s             | 
  ├ sirius::Band::initialize_subspace                                   |                         1.87 s             |                   1              |                         1.87 s             | 
  ├ sirius::Band::initialize_subspace|kp                                |                         1.85 s             |                   1              |                         1.85 s             | 
  ├ sddk::orthogonalize|tmtrx                                           |                         5.10 ms            |                 301              |                         1.54 s             | 
  ├ sirius::Potential::generate                                         |                       663.80 ms            |                  24              |                        15.93 s             | 
  ├ sirius::Hamiltonian_k::apply_h_s                                    |                       108.12 ms            |                 302              |                        32.65 s             | 
  ├ sirius::Augmentation_operator::generate_pw_coeffs                   |                       294.35 ms            |                   2              |                       588.70 ms            | 
  ├ sddk::Gvec_shells::remap_forward                                    |                        24.56 ms            |                  46              |                         1.13 s             | 
  ├ sddk::Gvec_shells::remap_backward                                   |                        23.96 ms            |                  46              |                         1.10 s             | 
  ├ sirius::Potential::generate_PAW_effective_potential                 |                       401.31 ms            |                  24              |                         9.63 s             | 
  ├ sddk::Gvec::init                                                    |                       118.88 ms            |                   3              |                       356.63 ms            | 
  ├ sirius::normalized_preconditioned_residuals                         |                         1.17 ms            |                 278              |                       325.90 ms            | 
  ├ sirius::Density::get_magnetisation                                  |                        14.14 ms            |                  23              |                       325.11 ms            | 
  ├ sirius::Density::compute_atomic_mag_mom                             |                        14.13 ms            |                  23              |                       324.97 ms            | 
  ├ sirius::Local_operator::apply_h                                     |                        41.79 ms            |                 302              |                        12.62 s             | 
  ├ sddk::Gvec::find_gvec_shells                                        |                       131.36 ms            |                   2              |                       262.72 ms            | 
  ├ sirius::finalize                                                    |                       212.37 ms            |                   1              |                       212.37 ms            | 
  ├ sirius::Non_local_operator::apply                                   |                        19.74 ms            |                 604              |                        11.92 s             | 
  ├ sirius::Unit_cell::initialize                                       |                       175.74 ms            |                   1              |                       175.74 ms            | 
  ├ sddk::Gvec_shells                                                   |                       169.04 ms            |                   1              |                       169.04 ms            | 
  ├ sirius::Density::initial_density                                    |                       163.72 ms            |                   1              |                       163.72 ms            | 
  ├ sirius::Atom_type::init                                             |                        76.07 ms            |                   2              |                       152.14 ms            | 
  ├ sirius::Potential                                                   |      162.01 ms →      152.07 ms   (-6.14%) |       1   →       1              |      162.01 ms →      152.07 ms   (-6.14%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.85 ms                             |       6                          |       35.13 ms                             | 
  │ └ sirius::Potential::update                                         |      126.14 ms                             |       1                          |      126.14 ms                             | 
  │   └ sirius::Potential::generate_local_potential                     |      125.33 ms                             |       1                          |      125.33 ms                             | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      112.38 ms                             |       1                          |      112.38 ms                             | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |       12.40 ms                             |       1                          |       12.40 ms                             | 
  ├ sirius::Density::mixer_output                                       |                         6.39 ms            |                  23              |                       147.02 ms            | 
  ├ sirius::Hamiltonian_k::get_h_o_diag                                 |                         5.93 ms            |                  23              |                       136.42 ms            | 
- ├ sirius::Density                                                     |      130.24 ms →      132.92 ms   (+2.06%) |       1   →       2   (+100.00%) |      130.24 ms →      265.85 ms (+104.12%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.16 ms                             |       2                          |       10.31 ms                             | 
  │ └ sirius::Density::update                                           |      119.66 ms                             |       1                          |      119.66 ms                             | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      119.22 ms                             |       1                          |      119.22 ms                             | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      111.92 ms                             |       1                          |      111.92 ms                             | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        6.85 ms                             |       1                          |        6.85 ms                             | 
  ├ sirius::Density::initial_density                                    |      165.93 ms                             |       1                          |      165.93 ms                             | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      110.86 ms                             |       1                          |      110.86 ms                             | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        6.15 ms                             |       2                          |       12.29 ms                             | 
  │ └ sirius::Periodic_function::integrate                              |        9.74 ms                             |       1                          |        9.74 ms                             | 
  ├ sirius::Potential::generate                                         |      694.82 ms                             |       1                          |      694.82 ms                             | 
  │ ├ sirius::Potential::poisson                                        |      125.26 ms                             |       1                          |      125.26 ms                             | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.98 ms                             |       1                          |        5.98 ms                             | 
  │ │ └ sirius::Periodic_function|inner                                 |        9.97 ms                             |       1                          |        9.97 ms                             | 
  │ │   └ sirius::Periodic_function|inner_local                         |        9.81 ms                             |       1                          |        9.81 ms                             | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.81 ms                             |       1                          |        9.81 ms                             | 
  │ ├ sirius::Periodic_function::add                                    |      563.24 μs                             |       2                          |        1.13 ms                             | 
  │ ├ sirius::Potential::xc                                             |       59.27 ms                             |       1                          |       59.27 ms                             | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       59.27 ms                             |       1                          |       59.27 ms                             | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.71 ms                             |       2                          |       11.43 ms                             | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.54 ms                             |       1                          |        5.54 ms                             | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.92 ms                             |       1                          |        5.92 ms                             | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.95 ms                             |       1                          |       92.95 ms                             | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      408.93 ms                             |       1                          |      408.93 ms                             | 
  ├ sirius::Radial_integrals|aug                                        |                        64.90 ms            |                   2              |                       129.80 ms            | 
  ├ sirius::Potential::poisson                                          |                       126.84 ms            |                  24              |                         3.04 s             | 
  ├ sirius::Potential::update                                           |                       122.74 ms            |                   1              |                       122.74 ms            | 
  ├ sirius::Potential::generate_local_potential                         |                       122.04 ms            |                   1              |                       122.04 ms            | 
  ├ sirius::Beta_projectors_base::inner                                 |                        24.54 ms            |                 325              |                         7.98 s             | 
  ├ sirius::Density::update                                             |                       122.33 ms            |                   2              |                       244.67 ms            | 
  ├ sirius::Density::generate_pseudo_core_charge_density                |                       121.92 ms            |                   2              |                       243.84 ms            | 
  ├ sirius::Simulation_context::make_periodic_function                  |                       109.22 ms            |                   4              |                       436.89 ms            | 
  ├ sirius::Potential::generate_D_operator_matrix                       |                        91.07 ms            |                  24              |                         2.19 s             | 
  ├ sirius::Band::set_subspace_mtrx                                     |                         8.63 ms            |                 303              |                         2.62 s             | 
  ├ sddk::wf_inner                                                      |                         6.09 ms            |                 882              |                         5.37 s             | 
  ├ sirius::Radial_integrals|atomic_wfs                                 |                        19.68 ms            |                   4              |                        78.71 ms            | 
  ├ sddk::wf_inner|pw                                                   |                         4.98 ms            |                 882              |                         4.39 s             | 
  ├ Eigensolver_cuda|zhegvdx                                            |                        56.46 ms            |                   1              |                        56.46 ms            | 
  ├ sirius::K_point::generate_atomic_wave_functions                     |                        51.86 ms            |                   1              |                        51.86 ms            | 
  ├ sirius::Radial_integrals|vloc                                       |                        21.70 ms            |                   2              |                        43.40 ms            | 
  ├ sirius::Potential::xc                                               |                        34.64 ms            |                  24              |                       831.34 ms            | 
  ├ sirius::Potential::xc_rg_nonmagnetic                                |                        32.30 ms            |                  24              |                       775.26 ms            | 
  ├ sirius::K_point_set::create_k_mesh                                  |                        35.88 ms            |                   1              |                        35.88 ms            | 
  ├ sirius::K_point_set::initialize                                     |                        35.75 ms            |                   1              |                        35.75 ms            | 
  ├ sirius::K_point::initialize                                         |                        35.66 ms            |                   1              |                        35.66 ms            | 
  ├ sirius::inner                                                       |                        10.63 ms            |                 601              |                         6.39 s             | 
  ├ sddk::wf_trans                                                      |                        12.11 ms            |                 706              |                         8.55 s             | 
  ├ sddk::wf_trans|pw                                                   |                         5.33 ms            |                1.60 K            |                         8.55 s             | 
  ├ sirius::Radial_integrals|beta                                       |                        14.77 ms            |                   2              |                        29.53 ms            | 
  ├ sirius::Density::mixer_input                                        |                         1.10 ms            |                  23              |                        25.20 ms            | 
  ├ sirius::Potential::xc_rg_nonmagnetic|libxc                          |                        11.82 ms            |                  48              |                       567.60 ms            | 
  ├ sirius::Unit_cell::update                                           |                        17.69 ms            |                   2              |                        35.38 ms            | 
  ├ sirius::Band::initialize_subspace|kp|wf                             |                        21.02 ms            |                   1              |                        21.02 ms            | 
  ├ sirius::Hamiltonian_k                                               |                       935.42 μs            |                  24              |                        22.45 ms            | 
  ├ sirius::Beta_projectors_base::prepare                               |                       399.69 μs            |                  47              |                        18.79 ms            | 
  ├ sirius::K_point::generate_gkvec                                     |                        18.41 ms            |                   1              |                        18.41 ms            | 
  ├ sirius::Unit_cell::get_symmetry                                     |                        12.26 ms            |                   2              |                        24.52 ms            | 
  ├ sirius::Unit_cell_symmetry                                          |                        12.24 ms            |                   2              |                        24.47 ms            | 
  ├ sirius::K_point::update                                             |                        12.44 ms            |                   1              |                        12.44 ms            | 
- ├ sirius::Hamiltonian0                                                |        8.37 ms →        8.20 ms   (-2.11%) |       1   →      24   (+2300.00%) |        8.37 ms →      196.71 ms (+2249.34%) | 
  │ ├ sirius::Local_operator                                            |        8.02 ms                             |       1                          |        8.02 ms                             | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.76 ms                             |       1                          |        4.76 ms                             | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.33 ms                             |       1                          |        2.33 ms                             | 
  │ ├ sirius::Non_local_operator                                        |       62.94 μs                             |       2                          |      125.88 μs                             | 
  │ ├ sirius::D_operator::initialize                                    |      100.02 μs                             |       1                          |      100.02 μs                             | 
  │ └ sirius::Q_operator::initialize                                    |       75.88 μs                             |       1                          |       75.88 μs                             | 
  ├ sirius::Band::initialize_subspace                                   |        1.86 s                              |       1                          |        1.86 s                              | 
  │ ├ sirius::Hamiltonian_k                                             |       18.70 ms                             |       1                          |       18.70 ms                             | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      198.89 μs                             |       1                          |      198.89 μs                             | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       18.50 ms                             |       1                          |       18.50 ms                             | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.84 s                              |       1                          |        1.84 s                              | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      130.43 ms                             |       4                          |      521.73 ms                             | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       52.04 ms                             |       1                          |       52.04 ms                             | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.15 ms                             |       1                          |       21.15 ms                             | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      634.27 ms                             |       1                          |      634.27 ms                             | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      297.39 ms                             |       1                          |      297.39 ms                             | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.44 μs                             |       1                          |        3.44 μs                             | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.54 μs                             |       1                          |        2.54 μs                             | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      461.00 ns                             |       1                          |      461.00 ns                             | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      475.00 ns                             |       1                          |      475.00 ns                             | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.22 ms                             |       1                          |        9.22 ms                             | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      120.66 ms                             |       1                          |      120.66 ms                             | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      103.48 ms                             |       2                          |      206.96 ms                             | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       38.39 ms                             |       2                          |       76.78 ms                             | 
  │ │ │ └ sddk::inner                                                   |       37.85 ms                             |       2                          |       75.71 ms                             | 
  │ │ │   └ sddk::inner|local                                           |       25.49 μs                             |       2                          |       50.99 μs                             | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       56.12 ms                             |       1                          |       56.12 ms                             | 
  │ │ └ sddk::transform                                                 |       31.56 ms                             |       1                          |       31.56 ms                             | 
  │ │   ├ sddk::transform|init                                          |       12.12 μs                             |       1                          |       12.12 μs                             | 
  │ │   └ sddk::transform|local                                         |       10.99 μs                             |       1                          |       10.99 μs                             | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      543.00 ns                             |       1                          |      543.00 ns                             | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      164.80 s                              |       1                          |      164.80 s                              | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.81 ms                             |      19                          |      110.35 ms                             | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.70 s                              |      35                          |      164.46 s                              | 
  │ │ ├ sirius::Hamiltonian0                                            |        4.75 ms                             |      35                          |      166.31 ms                             | 
  │ │ │ ├ sirius::Local_operator                                        |        4.37 ms                             |      35                          |      153.02 ms                             | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      987.01 μs                             |      35                          |       34.55 ms                             | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.50 ms                             |      35                          |       87.43 ms                             | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.85 μs                             |      70                          |        4.54 ms                             | 
  │ │ │ ├ sirius::D_operator::initialize                                |      101.22 μs                             |      35                          |        3.54 ms                             | 
  │ │ │ └ sirius::Q_operator::initialize                                |       77.00 μs                             |      35                          |        2.70 ms                             | 
  │ │ ├ sirius::Band::solve                                             |        2.61 s                              |      35                          |       91.51 s                              | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      163.20 μs                             |      35                          |        5.71 ms                             | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      156.10 μs                             |      35                          |        5.46 ms                             | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.50 μs                             |      35                          |      192.61 μs                             | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.55 s                              |      35                          |       89.37 s                              | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |      103.28 ms                             |      35                          |        3.61 s                              | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        9.00 ms                             |     210                          |        1.89 s                              | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        5.96 ms                             |      35                          |      208.74 ms                             | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      350.33 μs                             |      35                          |       12.26 ms                             | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.31 ms                             |      70                          |      161.66 ms                             | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.41 s                              |      35                          |       84.29 s                              | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      107.65 ms                             |     358                          |       38.54 s                              | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       41.75 ms                             |     358                          |       14.95 s                              | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.06 μs                             |     358                          |      738.89 μs                             | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.71 μs                             |     358                          |      612.84 μs                             | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      355.29 ns                             |     358                          |      127.19 μs                             | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      417.10 ns                             |     358                          |      149.32 μs                             | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.36 ms                             |     358                          |        2.63 s                              | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       19.39 ms                             |     358                          |        6.94 s                              | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       19.57 ms                             |     716                          |       14.01 s                              | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       34.99 ms                             |     358                          |       12.53 s                              | 
  │ │ │ │   │ ├ sddk::inner                                             |        4.45 ms                             |     681                          |        3.03 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       21.65 μs                             |     681                          |       14.75 ms                             | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |        5.51 ms                             |     358                          |        1.97 s                              | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        8.24 ms                             |     358                          |        2.95 s                              | 
  │ │ │ │   │ └ sddk::transform                                         |       14.16 ms                             |     323                          |        4.57 s                              | 
  │ │ │ │   │   ├ sddk::transform|init                                  |       17.73 μs                             |     323                          |        5.73 ms                             | 
  │ │ │ │   │   └ sddk::transform|local                                 |       32.93 μs                             |     969                          |       31.91 ms                             | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        9.46 ms                             |     358                          |        3.39 s                              | 
  │ │ │ │   │ └ sddk::inner                                             |        8.59 ms                             |     358                          |        3.08 s                              | 
  │ │ │ │   │   └ sddk::inner|local                                     |       28.09 μs                             |     358                          |       10.05 ms                             | 
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       64.26 ms                             |     358                          |       23.01 s                              | 
  │ │ │ │   ├ sirius::residuals                                         |       13.87 ms                             |     347                          |        4.81 s                              | 
  │ │ │ │   │ ├ sddk::transform                                         |       12.84 ms                             |     333                          |        4.27 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       14.87 μs                             |     333                          |        4.95 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       34.99 μs                             |     666                          |       23.31 ms                             | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.40 ms                             |     333                          |      465.63 ms                             | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       54.17 ms                             |      37                          |        2.00 s                              | 
  │ │ │ │     └ sddk::transform                                         |       51.18 ms                             |      39                          |        2.00 s                              | 
  │ │ │ │       ├ sddk::transform|init                                  |       12.00 μs                             |      39                          |      467.83 μs                             | 
  │ │ │ │       └ sddk::transform|local                                 |       13.18 μs                             |      41                          |      540.55 μs                             | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      565.80 ns                             |      35                          |       19.80 μs                             | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       40.67 μs                             |      35                          |        1.42 ms                             | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      607.78 μs                             |      35                          |       21.27 ms                             | 
  │ │ ├ sirius::Density::generate                                       |      771.97 ms                             |      35                          |       27.02 s                              | 
  │ │ │ ├ sirius::Density::generate_valence                             |      402.05 ms                             |      35                          |       14.07 s                              | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.20 μs                             |      35                          |      286.93 μs                             | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.37 μs                             |      35                          |      257.96 μs                             | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       99.76 ms                             |      35                          |        3.49 s                              | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.86 μs                             |      35                          |      274.99 μs                             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.12 ms                             |      35                          |      249.11 ms                             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       90.75 ms                             |      35                          |        3.18 s                              | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      573.57 ns                             |      35                          |       20.07 μs                             | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      162.11 ms                             |      35                          |        5.67 s                              | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms                             |      35                          |       57.53 ms                             | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.38 ms                             |      35                          |        3.09 s                              | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.15 ms                             |      35                          |        3.09 s                              | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      278.03 ms                             |      35                          |        9.73 s                              | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      278.03 ms                             |      35                          |        9.73 s                              | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.86 ms                             |      35                          |      870.10 ms                             | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      229.35 ms                             |      35                          |        8.03 s                              | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       22.64 ms                             |      35                          |      792.42 ms                             | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       80.79 ms                             |      35                          |        2.83 s                              | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        7.55 ms                             |      35                          |      264.18 ms                             | 
  │ │ ├ sirius::Density::mix                                            |      229.10 ms                             |      35                          |        8.02 s                              | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      965.85 μs                             |      35                          |       33.80 ms                             | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.71 ms                             |     469                          |        5.02 s                              | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.40 ms                             |     469                          |        4.88 s                              | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.40 ms                             |     469                          |        4.88 s                              | 
  │ │ │ └ sirius::Density::mixer_output                                 |        7.63 ms                             |      35                          |      267.08 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        6.79 ms                             |      35                          |      237.60 ms                             | 
  │ │ ├ sirius::Potential::generate                                     |      674.69 ms                             |      35                          |       23.61 s                              | 
  │ │ │ ├ sirius::Potential::poisson                                    |      125.90 ms                             |      35                          |        4.41 s                              | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        5.74 ms                             |      35                          |      200.96 ms                             | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.45 ms                             |      35                          |      365.78 ms                             | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.08 ms                             |      35                          |      352.79 ms                             | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.08 ms                             |      35                          |      352.77 ms                             | 
  │ │ │ ├ sirius::Periodic_function::add                                |      550.23 μs                             |      70                          |       38.52 ms                             | 
  │ │ │ ├ sirius::Potential::xc                                         |       54.58 ms                             |      35                          |        1.91 s                              | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       54.58 ms                             |      35                          |        1.91 s                              | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.02 ms                             |      70                          |      211.50 ms                             | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.58 ms                             |      35                          |      195.24 ms                             | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.57 ms                             |      35                          |      229.87 ms                             | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.97 ms                             |      35                          |        3.18 s                              | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      394.26 ms                             |      35                          |       13.80 s                              | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      282.21 ms                             |      35                          |        9.88 s                              | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      282.21 ms                             |      35                          |        9.88 s                              | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.16 ms                             |      35                          |      950.66 ms                             | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      227.46 ms                             |      35                          |        7.96 s                              | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.79 ms                             |      35                          |      832.78 ms                             | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.61 ms                             |      35                          |      196.40 ms                             | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.49 ms                             |     245                          |        2.57 s                              | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |       10.22 ms                             |     245                          |        2.50 s                              | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |       10.22 ms                             |     245                          |        2.50 s                              | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.52 ms                             |     105                          |        1.10 s                              | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.23 ms                             |     105                          |        1.07 s                              | 
  │ │ ├ sirius::Periodic_function::integrate                            |        9.97 ms                             |      35                          |      348.99 ms                             | 
  │ │ └ sirius::Density::get_magnetisation                              |      167.05 μs                             |      35                          |        5.85 ms                             | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |      162.20 μs                             |      35                          |        5.68 ms                             | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        7.15 ms                             |       2                          |       14.29 ms                             | 
  │ ├ sirius::Periodic_function|inner                                   |        9.79 ms                             |       6                          |       58.71 ms                             | 
  │ │ └ sirius::Periodic_function|inner_local                           |        9.75 ms                             |       6                          |       58.51 ms                             | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        9.75 ms                             |       6                          |       58.51 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.18 ms                             |       3                          |       30.54 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.14 ms                             |       3                          |       30.41 ms                             | 
  ├ sirius::Periodic_function|inner                                     |        9.68 ms                             |       2                          |       19.36 ms                             | 
  │ └ sirius::Periodic_function|inner_local                             |        9.67 ms                             |       2                          |       19.34 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.67 ms                             |       2                          |       19.34 ms                             | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.57 ms                             |       1                          |       10.57 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.19 ms                             |       1                          |       10.19 ms                             | 
  ├ sirius::finalize                                                    |      219.99 ms                             |       1                          |      219.99 ms                             | 
  ├ sirius::K_point_set::find_band_occupancies                          |                       475.66 μs            |                  23              |                        10.94 ms            | 
  ├ sirius::Radial_integrals|rho_core_pseudo                            |                         5.18 ms            |                   2              |                        10.36 ms            | 
  ├ sirius::Periodic_function::integrate                                |                        10.12 ms            |                  24              |                       242.81 ms            | 
  ├ sirius::Smooth_periodic_function::gather_f_pw                       |                         4.76 ms            |                   2              |                         9.53 ms            | 
  ├ sirius::Beta_projectors_base::generate                              |                         7.34 ms            |                 325              |                         2.38 s             | 
  ├ sirius::Smooth_periodic_function::fft_transform                     |                         5.19 ms            |                 169              |                       877.62 ms            | 
  ├ sirius::Local_operator                                              |                         4.27 ms            |                  24              |                       102.46 ms            | 
  ├ sirius::Unit_cell::find_nearest_neighbours                          |                         5.39 ms            |                   2              |                        10.78 ms            | 
  ├ sirius::Beta_projectors                                             |                         6.23 ms            |                   1              |                         6.23 ms            | 
  ├ sirius::Unit_cell_symmetry|spg                                      |                         5.15 ms            |                   2              |                        10.30 ms            | 
  ├ sirius::Radial_integrals|rho_pseudo                                 |                         4.48 ms            |                   1              |                         4.48 ms            | 
  ├ sirius::Beta_projectors::generate_pw_coefs_t                        |                         3.66 ms            |                   1              |                         3.66 ms            | 
  ├ sirius::Q_operator::initialize                                      |                         2.46 ms            |                  24              |                        59.12 ms            | 
  ├ sirius::Unit_cell_symmetry|equiv                                    |                         2.33 ms            |                   2              |                         4.66 ms            | 
  ├ sirius::K_point_set::sync_band                                      |                        64.54 μs            |                  46              |                         2.97 ms            | 
  ├ sirius::Simulation_context::init_atoms_to_grid_idx                  |                         1.31 ms            |                   1              |                         1.31 ms            | 
  ├ sirius::D_operator::initialize                                      |                         1.27 ms            |                  24              |                        30.55 ms            | 
  ├ sirius::Periodic_function::add                                      |                       456.98 μs            |                  48              |                        21.94 ms            | 
  ├ sirius::Simulation_context::init_comm                               |                       311.29 μs            |                   1              |                       311.29 μs            | 
  ├ sirius::Local_operator::prepare_k                                   |                       156.48 μs            |                  24              |                         3.76 ms            | 
  ├ sirius::Non_local_operator                                          |                        64.20 μs            |                  48              |                         3.08 ms            | 
  ├ sirius::Unit_cell_symmetry|mag                                      |                       102.48 μs            |                   2              |                       204.95 μs            | 
  ├ sirius::K_point::K_point                                            |                         6.08 μs            |                   4              |                        24.30 μs            | 
  ├ sddk::matrix_storage::remap_forward                                 |                         1.71 μs            |                 325              |                       556.27 μs            | 
  ├ sddk::wf_inner|scale_back                                           |                       215.47 ns            |                 882              |                       190.04 μs            | 
  ├ sddk::matrix_storage::remap_backward                                |                       481.81 ns            |                 302              |                       145.51 μs            | 
  ├ sirius::Beta_projectors_base::dismiss                               |                       511.13 ns            |                  47              |                        24.02 μs            | 
  └ sddk::wf_inner|scale                                                |                       123.36 ns            |                 882              |                       108.80 μs            | 
  ====================================================================================================================================================================================================
```
