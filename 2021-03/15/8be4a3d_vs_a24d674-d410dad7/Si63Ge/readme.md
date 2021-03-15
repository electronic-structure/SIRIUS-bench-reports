# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs 8be4a3d847d7cac2fa4e252581562d3d44ebcb3a
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |       78.77 s  →       47.18 s   (-40.11%) |       1   →       1              |       78.77 s  →       47.18 s   (-40.11%) | 
  ├ sirius::initialize                                                  |        2.87 s                              |       1                          |        2.87 s                              | 
  ├ sirius::DFT_ground_state::scf_loop                                  |                        37.57 s             |                   1              |                        37.57 s             | 
  ├ sirius::Band::solve                                                 |                         1.29 s             |                  15              |                        19.33 s             | 
  ├ sirius::Band::diag_pseudo_potential_davidson                        |                         1.12 s             |                  15              |                        16.81 s             | 
  ├ sirius::Density::generate                                           |                       560.70 ms            |                  15              |                         8.41 s             | 
  ├ sirius::Density::generate_valence                                   |                       420.38 ms            |                  15              |                         6.31 s             | 
  ├ Eigensolver_cuda|zheevdx                                            |                        39.66 ms            |                 116              |                         4.60 s             | 
  ├ sirius::Density::augment                                            |                       246.85 ms            |                  15              |                         3.70 s             | 
  ├ sirius::Density::generate_rho_aug                                   |                       246.64 ms            |                  15              |                         3.70 s             | 
+ ├ sirius::Simulation_context::initialize                              |        4.95 s  →        3.60 s   (-27.31%) |       1   →       1              |        4.95 s  →        3.60 s   (-27.31%) | 
  │ ├ sirius::Simulation_context::init_comm                             |       18.59 ms                             |       1                          |       18.59 ms                             | 
  │ ├ sirius::Unit_cell::initialize                                     |        1.26 s                              |       1                          |        1.26 s                              | 
  │ │ ├ sirius::Atom_type::init                                         |      623.67 ms                             |       2                          |        1.25 s                              | 
  │ │ └ sirius::Unit_cell::update                                       |       10.25 ms                             |       1                          |       10.25 ms                             | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.77 ms                             |       1                          |        3.77 ms                             | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |        6.40 ms                             |       1                          |        6.40 ms                             | 
  │ │     └ sirius::Unit_cell_symmetry                                  |        6.35 ms                             |       1                          |        6.35 ms                             | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.72 ms                             |       1                          |        2.72 ms                             | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      567.84 μs                             |       1                          |      567.84 μs                             | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       15.73 μs                             |       1                          |       15.73 μs                             | 
  │ └ sirius::Simulation_context::update                                |        3.63 s                              |       1                          |        3.63 s                              | 
  │   ├ sirius::Unit_cell::update                                       |        6.80 ms                             |       1                          |        6.80 ms                             | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.53 ms                             |       1                          |        3.53 ms                             | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.23 ms                             |       1                          |        3.23 ms                             | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.19 ms                             |       1                          |        3.19 ms                             | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.66 ms                             |       1                          |        2.66 ms                             | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      496.86 μs                             |       1                          |      496.86 μs                             | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       13.41 μs                             |       1                          |       13.41 μs                             | 
  │   ├ sirius::Radial_integrals|aug                                    |      212.80 ms                             |       2                          |      425.61 ms                             | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.34 ms                             |       2                          |       30.69 ms                             | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.43 ms                             |       1                          |       13.43 ms                             | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.38 ms                             |       2                          |      112.76 ms                             | 
  │   ├ sirius::Radial_integrals|beta                                   |       44.92 ms                             |       2                          |       89.84 ms                             | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.14 ms                             |       4                          |      240.56 ms                             | 
  │   ├ sddk::Gvec::init                                                |       96.38 ms                             |       2                          |      192.75 ms                             | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       71.72 ms                             |       2                          |      143.44 ms                             | 
  │   ├ sddk::Gvec_shells                                               |      104.14 ms                             |       1                          |      104.14 ms                             | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.68 ms                             |       1                          |        1.68 ms                             | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      657.71 ms                             |       2                          |        1.32 s                              | 
  ├ sirius::Simulation_context::update                                  |                         3.24 s             |                   1              |                         3.24 s             | 
  ├ sirius::initialize                                                  |                         2.88 s             |                   1              |                         2.88 s             | 
  ├ sirius::Density::add_k_point_contribution_rg                        |                       119.28 ms            |                  15              |                         1.79 s             | 
  ├ sirius::Field4D::symmetrize                                         |                       102.84 ms            |                  30              |                         3.09 s             | 
  ├ sirius::symmetrize_function|fpw                                     |                       102.83 ms            |                  30              |                         3.08 s             | 
  ├ sirius::Band::initialize_subspace                                   |                         1.29 s             |                   1              |                         1.29 s             | 
  ├ sirius::Band::initialize_subspace|kp                                |                         1.24 s             |                   1              |                         1.24 s             | 
  ├ sddk::orthogonalize                                                 |                        10.59 ms            |                 116              |                         1.23 s             | 
  ├ sirius::Density::mix                                                |                        76.72 ms            |                  15              |                         1.15 s             | 
  ├ sirius::symmetrize_function|fpw|local                               |                        65.64 ms            |                  30              |                         1.97 s             | 
  ├ sirius::Augmentation_operator::generate_pw_coeffs                   |                       457.30 ms            |                   2              |                       914.60 ms            | 
  ├ sirius::finalize                                                    |                       791.33 ms            |                   1              |                       791.33 ms            | 
  ├ sddk::orthogonalize|transform                                       |                         4.68 ms            |                 116              |                       543.40 ms            | 
  ├ sddk::Gvec_shells::remap_forward                                    |                        23.64 ms            |                  30              |                       709.06 ms            | 
  ├ sirius::Radial_integrals|aug                                        |                       213.83 ms            |                   2              |                       427.67 ms            | 
  ├ sirius::Density::add_k_point_contribution_dm                        |                        26.54 ms            |                  15              |                       398.09 ms            | 
  ├ sirius::Density::get_magnetisation                                  |                        24.30 ms            |                  15              |                       364.51 ms            | 
  ├ sirius::Density::compute_atomic_mag_mom                             |                        24.29 ms            |                  15              |                       364.39 ms            | 
  ├ sirius::Potential::generate                                         |                       361.66 ms            |                  16              |                         5.79 s             | 
  ├ sirius::Density::symmetrize_density_matrix                          |                        23.59 ms            |                  15              |                       353.86 ms            | 
  ├ sirius::Hamiltonian_k::apply_h_s                                    |                        75.76 ms            |                 117              |                         8.86 s             | 
  ├ sirius::residuals                                                   |                         2.66 ms            |                 114              |                       303.03 ms            | 
  ├ sirius::Potential::generate_D_operator_matrix                       |                       268.22 ms            |                  16              |                         4.29 s             | 
  ├ sirius::Hamiltonian_k::get_h_o_diag                                 |                        17.66 ms            |                  15              |                       264.97 ms            | 
  ├ Eigensolver_cuda|zhegvdx                                            |                       250.12 ms            |                   1              |                       250.12 ms            | 
  ├ sirius::Local_operator::apply_h                                     |                        48.42 ms            |                 117              |                         5.66 s             | 
  ├ sirius::Radial_integrals|atomic_wfs                                 |                        60.28 ms            |                   4              |                       241.12 ms            | 
  ├ sirius::Band::diag_pseudo_potential_davidson|update_phi             |                         4.68 ms            |                  47              |                       220.18 ms            | 
  ├ sddk::Gvec_shells::remap_backward                                   |                        12.91 ms            |                  30              |                       387.37 ms            | 
  ├ sddk::Gvec::init                                                    |                        63.92 ms            |                   3              |                       191.77 ms            | 
- ├ sirius::K_point_set::create_k_mesh                                  |       93.08 ms →      162.57 ms  (+74.65%) |       1   →       1              |       93.08 ms →      162.57 ms  (+74.65%) | 
  │ ├ sirius::K_point::K_point                                          |        1.17 μs                             |       4                          |        4.66 μs                             | 
  │ └ sirius::K_point_set::initialize                                   |       93.02 ms                             |       1                          |       93.02 ms                             | 
  │   └ sirius::K_point::initialize                                     |       28.06 ms                             |       1                          |       28.06 ms                             | 
  │     ├ sirius::K_point::generate_gkvec                               |       11.01 ms                             |       1                          |       11.01 ms                             | 
  │     │ └ sddk::Gvec::init                                            |        4.79 ms                             |       1                          |        4.79 ms                             | 
  │     ├ sddk::matrix_storage::matrix_storage                          |       13.68 μs                             |       1                          |       13.68 μs                             | 
  │     └ sirius::K_point::update                                       |       14.18 ms                             |       1                          |       14.18 ms                             | 
  │       └ sirius::Beta_projectors                                     |       10.24 ms                             |       1                          |       10.24 ms                             | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.31 ms                             |       1                          |        8.31 ms                             | 
  ├ sirius::Smooth_periodic_function                                    |        2.60 ms                             |       2                          |        5.20 ms                             | 
  ├ sirius::K_point_set::initialize                                     |                       162.48 ms            |                   1              |                       162.48 ms            | 
  ├ sirius::Unit_cell::initialize                                       |                       155.72 ms            |                   1              |                       155.72 ms            | 
  ├ sddk::Gvec::find_gvec_shells                                        |                        70.02 ms            |                   2              |                       140.04 ms            | 
  ├ sirius::Atom_type::init                                             |                        67.89 ms            |                   2              |                       135.77 ms            | 
  ├ sirius::normalized_preconditioned_residuals                         |                         1.26 ms            |                 101              |                       126.82 ms            | 
  ├ sirius::Radial_integrals|vloc                                       |                        56.38 ms            |                   2              |                       112.76 ms            | 
  ├ sddk::Gvec_shells                                                   |                        99.54 ms            |                   1              |                        99.54 ms            | 
  ├ sirius::Radial_integrals|beta                                       |                        45.13 ms            |                   2              |                        90.25 ms            | 
  ├ sirius::Density::mixer_output                                       |                         5.20 ms            |                  15              |                        78.05 ms            | 
  ├ sirius::Density::initial_density                                    |                        57.37 ms            |                   1              |                        57.37 ms            | 
  ├ sirius::K_point::generate_atomic_wave_functions                     |                        55.08 ms            |                   1              |                        55.08 ms            | 
  ├ sddk::orthogonalize|tmtrx                                           |                       462.86 μs            |                 116              |                        53.69 ms            | 
  ├ sirius::Potential                                                   |       54.88 ms →       51.76 ms   (-5.68%) |       1   →       1              |       54.88 ms →       51.76 ms   (-5.68%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.91 ms                             |       6                          |       17.44 ms                             | 
  │ └ sirius::Potential::update                                         |       37.01 ms                             |       1                          |       37.01 ms                             | 
  │   └ sirius::Potential::generate_local_potential                     |       36.62 ms                             |       1                          |       36.62 ms                             | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       22.62 ms                             |       1                          |       22.62 ms                             | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |       13.70 ms                             |       1                          |       13.70 ms                             | 
  ├ sirius::Potential::xc                                               |                        46.41 ms            |                  16              |                       742.61 ms            | 
  ├ sirius::Potential::xc_rg_nonmagnetic                                |                        45.23 ms            |                  16              |                       723.74 ms            | 
  ├ sirius::Hamiltonian_k                                               |                         3.14 ms            |                  16              |                        50.29 ms            | 
  ├ sirius::Beta_projectors_base::prepare                               |                         1.53 ms            |                  31              |                        47.35 ms            | 
  ├ sirius::Non_local_operator::apply                                   |                         9.70 ms            |                 234              |                         2.27 s             | 
- ├ sirius::Density                                                     |       44.08 ms →       45.79 ms   (+3.88%) |       1   →       2   (+100.00%) |       44.08 ms →       91.58 ms (+107.77%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.83 ms                             |       2                          |        5.65 ms                             | 
  │ └ sirius::Density::update                                           |       38.29 ms                             |       1                          |       38.29 ms                             | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       38.07 ms                             |       1                          |       38.07 ms                             | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       27.40 ms                             |       1                          |       27.40 ms                             | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |       10.38 ms                             |       1                          |       10.38 ms                             | 
  ├ sirius::Density::initial_density                                    |       60.76 ms                             |       1                          |       60.76 ms                             | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       27.27 ms                             |       1                          |       27.27 ms                             | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        7.18 ms                             |       2                          |       14.37 ms                             | 
  │ └ sirius::Periodic_function::integrate                              |        5.71 ms                             |       1                          |        5.71 ms                             | 
  ├ sirius::Potential::generate                                         |      379.26 ms                             |       1                          |      379.26 ms                             | 
  │ ├ sirius::Potential::poisson                                        |       41.96 ms                             |       1                          |       41.96 ms                             | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        6.99 ms                             |       1                          |        6.99 ms                             | 
  │ │ └ sirius::Periodic_function|inner                                 |        5.88 ms                             |       1                          |        5.88 ms                             | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.64 ms                             |       1                          |        4.64 ms                             | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.64 ms                             |       1                          |        4.64 ms                             | 
  │ ├ sirius::Periodic_function::add                                    |      802.26 μs                             |       2                          |        1.60 ms                             | 
  │ ├ sirius::Potential::xc                                             |       61.82 ms                             |       1                          |       61.82 ms                             | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       61.81 ms                             |       1                          |       61.81 ms                             | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.57 ms                             |       2                          |        5.14 ms                             | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.28 ms                             |       1                          |        5.28 ms                             | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.70 ms                             |       1                          |        3.70 ms                             | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      268.82 ms                             |       1                          |      268.82 ms                             | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      322.00 ns                             |       1                          |      322.00 ns                             | 
  ├ sirius::Potential::xc_rg_nonmagnetic|libxc                          |                        19.65 ms            |                  32              |                       628.86 ms            | 
  ├ sirius::Potential::poisson                                          |                        39.07 ms            |                  16              |                       625.18 ms            | 
  ├ sirius::Potential::update                                           |                        36.79 ms            |                   1              |                        36.79 ms            | 
  ├ sirius::Potential::generate_local_potential                         |                        36.40 ms            |                   1              |                        36.40 ms            | 
  ├ sirius::Density::update                                             |                        40.03 ms            |                   2              |                        80.07 ms            | 
  ├ sirius::Density::generate_pseudo_core_charge_density                |                        39.80 ms            |                   2              |                        79.59 ms            | 
  ├ sirius::Band::set_subspace_mtrx                                     |                         2.18 ms            |                 118              |                       257.82 ms            | 
  ├ sddk::wf_inner                                                      |                         1.66 ms            |                 335              |                       554.96 ms            | 
  ├ sddk::wf_inner|pw                                                   |                         1.49 ms            |                 335              |                       499.37 ms            | 
  ├ sirius::Radial_integrals|rho_core_pseudo                            |                        15.18 ms            |                   2              |                        30.36 ms            | 
  ├ sirius::K_point::initialize                                         |                        29.24 ms            |                   1              |                        29.24 ms            | 
  ├ sirius::Simulation_context::make_periodic_function                  |                        26.11 ms            |                   4              |                       104.44 ms            | 
  ├ sirius::Beta_projectors_base::inner                                 |                         6.61 ms            |                 132              |                       872.07 ms            | 
  ├ sirius::Unit_cell::update                                           |                        13.42 ms            |                   2              |                        26.84 ms            | 
  ├ sirius::Radial_integrals|rho_pseudo                                 |                        15.97 ms            |                   1              |                        15.97 ms            | 
  ├ sirius::Unit_cell::get_symmetry                                     |                         9.56 ms            |                   2              |                        19.11 ms            | 
  ├ sirius::Density::mixer_input                                        |                         1.05 ms            |                  15              |                        15.82 ms            | 
  ├ sirius::Unit_cell_symmetry                                          |                         9.50 ms            |                   2              |                        18.99 ms            | 
  ├ sirius::K_point::update                                             |                        15.23 ms            |                   1              |                        15.23 ms            | 
  ├ sirius::K_point_set::find_band_occupancies                          |                         1.00 ms            |                  15              |                        15.04 ms            | 
  ├ sirius::inner                                                       |                         4.85 ms            |                 377              |                         1.83 s             | 
- ├ sirius::Hamiltonian0                                                |        6.41 ms →       11.11 ms  (+73.35%) |       1   →      16   (+1500.00%) |        6.41 ms →      177.84 ms (+2673.58%) | 
  │ ├ sirius::Local_operator                                            |        5.90 ms                             |       1                          |        5.90 ms                             | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.75 ms                             |       1                          |        2.75 ms                             | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.36 ms                             |       1                          |        2.36 ms                             | 
  │ ├ sirius::Non_local_operator                                        |       74.45 μs                             |       2                          |      148.90 μs                             | 
  │ ├ sirius::D_operator::initialize                                    |      159.68 μs                             |       1                          |      159.68 μs                             | 
  │ └ sirius::Q_operator::initialize                                    |      116.15 μs                             |       1                          |      116.15 μs                             | 
  ├ sirius::Band::initialize_subspace                                   |        1.27 s                              |       1                          |        1.27 s                              | 
  │ ├ sirius::Hamiltonian_k                                             |       32.99 ms                             |       1                          |       32.99 ms                             | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      278.67 μs                             |       1                          |      278.67 μs                             | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       32.70 ms                             |       1                          |       32.70 ms                             | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.24 s                              |       1                          |        1.24 s                              | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       82.34 ms                             |       4                          |      329.34 ms                             | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       37.00 ms                             |       1                          |       37.00 ms                             | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        6.52 ms                             |       1                          |        6.52 ms                             | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      315.60 ms                             |       1                          |      315.60 ms                             | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      245.36 ms                             |       1                          |      245.36 ms                             | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        4.48 μs                             |       1                          |        4.48 μs                             | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.35 μs                             |       1                          |        3.35 μs                             | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      463.00 ns                             |       1                          |      463.00 ns                             | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      634.00 ns                             |       1                          |      634.00 ns                             | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.24 ms                             |       1                          |        3.24 ms                             | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.27 ms                             |       1                          |       21.27 ms                             | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       22.84 ms                             |       2                          |       45.68 ms                             | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.74 ms                             |       2                          |       29.47 ms                             | 
  │ │ │ └ sddk::inner                                                   |       14.53 ms                             |       2                          |       29.05 ms                             | 
  │ │ │   └ sddk::inner|local                                           |       25.29 μs                             |       2                          |       50.58 μs                             | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      249.65 ms                             |       1                          |      249.65 ms                             | 
  │ │ └ sddk::transform                                                 |        2.82 ms                             |       1                          |        2.82 ms                             | 
  │ │   ├ sddk::transform|init                                          |       15.25 μs                             |       1                          |       15.25 μs                             | 
  │ │   └ sddk::transform|local                                         |       18.04 μs                             |       1                          |       18.04 μs                             | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      527.00 ns                             |       1                          |      527.00 ns                             | 
  ├ sirius::DFT_ground_state::scf_loop                                  |       67.70 s                              |       1                          |       67.70 s                              | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.44 ms                             |      19                          |       46.41 ms                             | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.37 s                              |      20                          |       67.48 s                              | 
  │ │ ├ sirius::Hamiltonian0                                            |        5.63 ms                             |      20                          |      112.55 ms                             | 
  │ │ │ ├ sirius::Local_operator                                        |        4.83 ms                             |      20                          |       96.64 ms                             | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      550.93 μs                             |      20                          |       11.02 ms                             | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.11 ms                             |      20                          |       62.19 ms                             | 
  │ │ │ ├ sirius::Non_local_operator                                    |      246.87 μs                             |      40                          |        9.87 ms                             | 
  │ │ │ ├ sirius::D_operator::initialize                                |      126.63 μs                             |      20                          |        2.53 ms                             | 
  │ │ │ └ sirius::Q_operator::initialize                                |       95.51 μs                             |      20                          |        1.91 ms                             | 
  │ │ ├ sirius::Band::solve                                             |        2.13 s                              |      20                          |       42.51 s                              | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      220.63 μs                             |      20                          |        4.41 ms                             | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      210.73 μs                             |      20                          |        4.21 ms                             | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        7.92 μs                             |      20                          |      158.31 μs                             | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.97 s                              |      20                          |       39.44 s                              | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       95.57 ms                             |      20                          |        1.91 s                              | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |       11.29 ms                             |     120                          |        1.36 s                              | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       17.81 ms                             |      20                          |      356.15 ms                             | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      485.09 μs                             |      20                          |        9.70 ms                             | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        8.47 ms                             |      40                          |      338.70 ms                             | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.85 s                              |      20                          |       37.03 s                              | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       68.39 ms                             |     250                          |       17.10 s                              | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       40.08 ms                             |     250                          |       10.02 s                              | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.24 μs                             |     250                          |      559.79 μs                             | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.84 μs                             |     250                          |      460.06 μs                             | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      466.16 ns                             |     250                          |      116.54 μs                             | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      581.26 ns                             |     250                          |      145.31 μs                             | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        3.09 ms                             |     250                          |      771.88 ms                             | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.82 ms                             |     250                          |      954.72 ms                             | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       10.69 ms                             |     500                          |        5.35 s                              | 
  │ │ │ │   ├ sddk::orthogonalize                                       |        7.72 ms                             |     250                          |        1.93 s                              | 
  │ │ │ │   │ ├ sddk::inner                                             |        1.12 ms                             |     480                          |      537.05 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       24.42 μs                             |     480                          |       11.72 ms                             | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      362.42 μs                             |     250                          |       90.61 ms                             | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        2.47 ms                             |     250                          |      617.00 ms                             | 
  │ │ │ │   │ └ sddk::transform                                         |        2.97 ms                             |     230                          |      682.89 ms                             | 
  │ │ │ │   │   ├ sddk::transform|init                                  |       19.99 μs                             |     230                          |        4.60 ms                             | 
  │ │ │ │   │   └ sddk::transform|local                                 |        8.23 μs                             |     690                          |        5.68 ms                             | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        2.03 ms                             |     250                          |      506.86 ms                             | 
  │ │ │ │   │ └ sddk::inner                                             |        1.82 ms                             |     250                          |      456.11 ms                             | 
  │ │ │ │   │   └ sddk::inner|local                                     |       25.05 μs                             |     250                          |        6.26 ms                             | 
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       65.93 ms                             |     250                          |       16.48 s                              | 
  │ │ │ │   ├ sirius::residuals                                         |        3.30 ms                             |     245                          |      809.63 ms                             | 
  │ │ │ │   │ ├ sddk::transform                                         |        2.04 ms                             |     231                          |      471.22 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       16.56 μs                             |     231                          |        3.83 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       11.03 μs                             |     462                          |        5.10 ms                             | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.39 ms                             |     231                          |      320.50 ms                             | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        7.87 ms                             |      25                          |      196.67 ms                             | 
  │ │ │ │     └ sddk::transform                                         |        6.47 ms                             |      30                          |      194.02 ms                             | 
  │ │ │ │       ├ sddk::transform|init                                  |       11.29 μs                             |      30                          |      338.56 μs                             | 
  │ │ │ │       └ sddk::transform|local                                 |       12.04 μs                             |      35                          |      421.33 μs                             | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      425.25 ns                             |      20                          |        8.50 μs                             | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       23.07 μs                             |      20                          |      461.46 μs                             | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.49 ms                             |      20                          |       29.78 ms                             | 
  │ │ ├ sirius::Density::generate                                       |      576.31 ms                             |      20                          |       11.53 s                              | 
  │ │ │ ├ sirius::Density::generate_valence                             |      407.45 ms                             |      20                          |        8.15 s                              | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.01 μs                             |      20                          |      160.26 μs                             | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.35 μs                             |      20                          |      146.98 μs                             | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       34.04 ms                             |      20                          |      680.72 ms                             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.58 μs                             |      20                          |      151.60 μs                             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        5.35 ms                             |      20                          |      107.05 ms                             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       27.63 ms                             |      20                          |      552.69 ms                             | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      538.30 ns                             |      20                          |       10.77 μs                             | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      111.89 ms                             |      20                          |        2.24 s                              | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.38 ms                             |      20                          |       47.59 ms                             | 
  │ │ │ │ └ sirius::Density::augment                                    |      219.28 ms                             |      20                          |        4.39 s                              | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |      219.06 ms                             |      20                          |        4.38 s                              | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      140.74 ms                             |      20                          |        2.81 s                              | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      140.74 ms                             |      20                          |        2.81 s                              | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       54.89 ms                             |      20                          |        1.10 s                              | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       69.11 ms                             |      20                          |        1.38 s                              | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       16.10 ms                             |      20                          |      321.93 ms                             | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.69 ms                             |      20                          |      473.72 ms                             | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        4.43 ms                             |      20                          |       88.66 ms                             | 
  │ │ ├ sirius::Density::mix                                            |      134.86 ms                             |      20                          |        2.70 s                              | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      768.72 μs                             |      20                          |       15.37 ms                             | 
  │ │ │ ├ sirius::Periodic_function|inner                               |        4.86 ms                             |     244                          |        1.18 s                              | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.81 ms                             |     244                          |        1.17 s                              | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.81 ms                             |     244                          |        1.17 s                              | 
  │ │ │ └ sirius::Density::mixer_output                                 |        4.77 ms                             |      20                          |       95.40 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        4.00 ms                             |      20                          |       79.91 ms                             | 
  │ │ ├ sirius::Potential::generate                                     |      373.01 ms                             |      20                          |        7.46 s                              | 
  │ │ │ ├ sirius::Potential::poisson                                    |       42.10 ms                             |      20                          |      841.95 ms                             | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        7.27 ms                             |      20                          |      145.39 ms                             | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |        5.83 ms                             |      20                          |      116.62 ms                             | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.63 ms                             |      20                          |       92.68 ms                             | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.63 ms                             |      20                          |       92.67 ms                             | 
  │ │ │ ├ sirius::Periodic_function::add                                |      781.78 μs                             |      40                          |       31.27 ms                             | 
  │ │ │ ├ sirius::Potential::xc                                         |       55.47 ms                             |      20                          |        1.11 s                              | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       55.47 ms                             |      20                          |        1.11 s                              | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |      653.06 μs                             |      40                          |       26.12 ms                             | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.92 ms                             |      20                          |       98.32 ms                             | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.62 ms                             |      20                          |       72.39 ms                             | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.85 ms                             |      20                          |        5.38 s                              | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      221.80 ns                             |      20                          |        4.44 μs                             | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      101.91 ms                             |      20                          |        2.04 s                              | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      101.91 ms                             |      20                          |        2.04 s                              | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       16.29 ms                             |      20                          |      325.84 ms                             | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       68.80 ms                             |      20                          |        1.38 s                              | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       16.19 ms                             |      20                          |      323.72 ms                             | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.65 ms                             |      20                          |       73.07 ms                             | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.58 ms                             |     140                          |      641.03 ms                             | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.57 ms                             |     140                          |      639.55 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.57 ms                             |     140                          |      639.44 ms                             | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.91 ms                             |      60                          |      294.63 ms                             | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.91 ms                             |      60                          |      294.30 ms                             | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.55 ms                             |      20                          |       90.92 ms                             | 
  │ │ └ sirius::Density::get_magnetisation                              |       75.95 μs                             |      20                          |        1.52 ms                             | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |       70.82 μs                             |      20                          |        1.42 ms                             | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.54 ms                             |       2                          |       11.08 ms                             | 
  │ ├ sirius::Periodic_function|inner                                   |        4.71 ms                             |       6                          |       28.28 ms                             | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.62 ms                             |       6                          |       27.73 ms                             | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.62 ms                             |       6                          |       27.73 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.90 ms                             |       3                          |       14.69 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.89 ms                             |       3                          |       14.68 ms                             | 
  ├ sirius::Periodic_function|inner                                     |        4.51 ms                             |       2                          |        9.02 ms                             | 
  │ └ sirius::Periodic_function|inner_local                             |        4.50 ms                             |       2                          |        9.01 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.50 ms                             |       2                          |        9.01 ms                             | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.79 ms                             |       1                          |        4.79 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.79 ms                             |       1                          |        4.79 ms                             | 
  ├ sirius::finalize                                                    |      929.29 ms                             |       1                          |      929.29 ms                             | 
  ├ sirius::Beta_projectors                                             |                        11.20 ms            |                   1              |                        11.20 ms            | 
  ├ sirius::K_point::generate_gkvec                                     |                        11.13 ms            |                   1              |                        11.13 ms            | 
  ├ sirius::Simulation_context::init_comm                               |                        11.05 ms            |                   1              |                        11.05 ms            | 
  ├ sirius::Smooth_periodic_function::gather_f_pw                       |                         5.29 ms            |                   2              |                        10.58 ms            | 
  ├ sirius::Beta_projectors::generate_pw_coefs_t                        |                         8.99 ms            |                   1              |                         8.99 ms            | 
  ├ sirius::Band::initialize_subspace|kp|wf                             |                         8.63 ms            |                   1              |                         8.63 ms            | 
  ├ sirius::Smooth_periodic_function::fft_transform                     |                         4.03 ms            |                 113              |                       455.75 ms            | 
  ├ sirius::Local_operator                                              |                         4.07 ms            |                  16              |                        65.19 ms            | 
  ├ sirius::Periodic_function::integrate                                |                         4.66 ms            |                  16              |                        74.53 ms            | 
  ├ sirius::Q_operator::initialize                                      |                         4.43 ms            |                  16              |                        70.85 ms            | 
  ├ sirius::Unit_cell::find_nearest_neighbours                          |                         3.82 ms            |                   2              |                         7.63 ms            | 
  ├ sirius::Beta_projectors_base::generate                              |                         3.31 ms            |                 132              |                       436.59 ms            | 
  ├ sirius::Unit_cell_symmetry|spg                                      |                         2.69 ms            |                   2              |                         5.38 ms            | 
  ├ sddk::wf_trans                                                      |                         2.48 ms            |                 282              |                       698.80 ms            | 
  ├ sddk::wf_trans|pw                                                   |                         1.13 ms            |                 617              |                       698.08 ms            | 
  ├ sirius::D_operator::initialize                                      |                         2.24 ms            |                  16              |                        35.80 ms            | 
  ├ sirius::Simulation_context::init_atoms_to_grid_idx                  |                         1.68 ms            |                   1              |                         1.68 ms            | 
  ├ sirius::Periodic_function::add                                      |                       599.54 μs            |                  32              |                        19.19 ms            | 
  ├ sirius::K_point_set::sync_band                                      |                        37.48 μs            |                  30              |                         1.12 ms            | 
  ├ sirius::Unit_cell_symmetry|equiv                                    |                       515.61 μs            |                   2              |                         1.03 ms            | 
  ├ sirius::Local_operator::prepare_k                                   |                       187.46 μs            |                  16              |                         3.00 ms            | 
  ├ sirius::Non_local_operator                                          |                       151.96 μs            |                  32              |                         4.86 ms            | 
  ├ sirius::K_point::K_point                                            |                         4.65 μs            |                   4              |                        18.59 μs            | 
  ├ sirius::Unit_cell_symmetry|mag                                      |                        15.76 μs            |                   2              |                        31.51 μs            | 
  ├ sddk::matrix_storage::remap_forward                                 |                         2.39 μs            |                 132              |                       315.08 μs            | 
  ├ sddk::wf_inner|scale_back                                           |                       255.62 ns            |                 335              |                        85.63 μs            | 
  ├ sddk::matrix_storage::remap_backward                                |                       789.57 ns            |                 117              |                        92.38 μs            | 
  ├ sirius::Beta_projectors_base::dismiss                               |                       535.16 ns            |                  31              |                        16.59 μs            | 
  ├ sirius::Potential::generate_PAW_effective_potential                 |                       140.81 ns            |                  16              |                         2.25 μs            | 
  └ sddk::wf_inner|scale                                                |                       103.64 ns            |                 335              |                        34.72 μs            | 
  ====================================================================================================================================================================================================
```
