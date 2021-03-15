# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs 8be4a3d847d7cac2fa4e252581562d3d44ebcb3a
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |       78.33 s  →       47.38 s   (-39.51%) |       1   →       1              |       78.33 s  →       47.38 s   (-39.51%) | 
  ├ sirius::initialize                                                  |        2.91 s                              |       1                          |        2.91 s                              | 
  ├ sirius::DFT_ground_state::scf_loop                                  |                        37.76 s             |                   1              |                        37.76 s             | 
  ├ sirius::Band::solve                                                 |                         1.30 s             |                  15              |                        19.43 s             | 
  ├ sirius::Band::diag_pseudo_potential_davidson                        |                         1.13 s             |                  15              |                        17.02 s             | 
  ├ sirius::Density::generate                                           |                       566.53 ms            |                  15              |                         8.50 s             | 
  ├ sirius::Density::generate_valence                                   |                       420.00 ms            |                  15              |                         6.30 s             | 
+ ├ sirius::Simulation_context::initialize                              |        4.78 s  →        3.65 s   (-23.63%) |       1   →       1              |        4.78 s  →        3.65 s   (-23.63%) | 
  │ ├ sirius::Simulation_context::init_comm                             |       13.42 ms                             |       1                          |       13.42 ms                             | 
  │ ├ sirius::Unit_cell::initialize                                     |        1.22 s                              |       1                          |        1.22 s                              | 
  │ │ ├ sirius::Atom_type::init                                         |      603.03 ms                             |       2                          |        1.21 s                              | 
  │ │ └ sirius::Unit_cell::update                                       |       10.34 ms                             |       1                          |       10.34 ms                             | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.92 ms                             |       1                          |        3.92 ms                             | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |        6.35 ms                             |       1                          |        6.35 ms                             | 
  │ │     └ sirius::Unit_cell_symmetry                                  |        6.30 ms                             |       1                          |        6.30 ms                             | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.70 ms                             |       1                          |        2.70 ms                             | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      500.70 μs                             |       1                          |      500.70 μs                             | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       15.63 μs                             |       1                          |       15.63 μs                             | 
  │ └ sirius::Simulation_context::update                                |        3.44 s                              |       1                          |        3.44 s                              | 
  │   ├ sirius::Unit_cell::update                                       |        7.01 ms                             |       1                          |        7.01 ms                             | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.76 ms                             |       1                          |        3.76 ms                             | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.20 ms                             |       1                          |        3.20 ms                             | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.16 ms                             |       1                          |        3.16 ms                             | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.63 ms                             |       1                          |        2.63 ms                             | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      496.27 μs                             |       1                          |      496.27 μs                             | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       13.43 μs                             |       1                          |       13.43 μs                             | 
  │   ├ sirius::Radial_integrals|aug                                    |      212.84 ms                             |       2                          |      425.67 ms                             | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.19 ms                             |       2                          |       30.39 ms                             | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.25 ms                             |       1                          |       13.25 ms                             | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.43 ms                             |       2                          |      112.85 ms                             | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.04 ms                             |       2                          |       90.08 ms                             | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.33 ms                             |       4                          |      241.33 ms                             | 
  │   ├ sddk::Gvec::init                                                |       95.03 ms                             |       2                          |      190.07 ms                             | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       70.49 ms                             |       2                          |      140.98 ms                             | 
  │   ├ sddk::Gvec_shells                                               |      112.97 ms                             |       1                          |      112.97 ms                             | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.68 ms                             |       1                          |        1.68 ms                             | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      575.22 ms                             |       2                          |        1.15 s                              | 
  ├ sirius::Density::augment                                            |                       237.52 ms            |                  15              |                         3.56 s             | 
  ├ sirius::Density::generate_rho_aug                                   |                       237.30 ms            |                  15              |                         3.56 s             | 
  ├ sirius::Simulation_context::update                                  |                         3.24 s             |                   1              |                         3.24 s             | 
  ├ Eigensolver_cuda|zheevdx                                            |                        27.51 ms            |                 116              |                         3.19 s             | 
  ├ sirius::initialize                                                  |                         2.87 s             |                   1              |                         2.87 s             | 
  ├ sirius::Field4D::symmetrize                                         |                       105.37 ms            |                  30              |                         3.16 s             | 
  ├ sirius::symmetrize_function|fpw                                     |                       105.36 ms            |                  30              |                         3.16 s             | 
  ├ sirius::Density::add_k_point_contribution_rg                        |                       114.28 ms            |                  15              |                         1.71 s             | 
  ├ sirius::Band::initialize_subspace                                   |                         1.28 s             |                   1              |                         1.28 s             | 
  ├ sddk::orthogonalize                                                 |                        10.85 ms            |                 116              |                         1.26 s             | 
  ├ sirius::Band::initialize_subspace|kp                                |                         1.23 s             |                   1              |                         1.23 s             | 
  ├ sirius::Density::mix                                                |                        77.35 ms            |                  15              |                         1.16 s             | 
  ├ sirius::symmetrize_function|fpw|local                               |                        65.20 ms            |                  30              |                         1.96 s             | 
  ├ sirius::Augmentation_operator::generate_pw_coeffs                   |                       460.46 ms            |                   2              |                       920.92 ms            | 
  ├ sirius::finalize                                                    |                       759.49 ms            |                   1              |                       759.49 ms            | 
  ├ sddk::Gvec_shells::remap_forward                                    |                        26.62 ms            |                  30              |                       798.61 ms            | 
  ├ sddk::orthogonalize|transform                                       |                         4.61 ms            |                 116              |                       534.84 ms            | 
  ├ sirius::Density::add_k_point_contribution_dm                        |                        30.95 ms            |                  15              |                       464.28 ms            | 
  ├ sirius::Radial_integrals|aug                                        |                       214.18 ms            |                   2              |                       428.37 ms            | 
  ├ sirius::residuals                                                   |                         3.66 ms            |                 114              |                       416.91 ms            | 
  ├ sirius::Potential::generate                                         |                       362.79 ms            |                  16              |                         5.80 s             | 
  ├ sirius::Density::get_magnetisation                                  |                        24.30 ms            |                  15              |                       364.52 ms            | 
  ├ sirius::Density::compute_atomic_mag_mom                             |                        24.29 ms            |                  15              |                       364.41 ms            | 
  ├ sirius::Density::symmetrize_density_matrix                          |                        23.65 ms            |                  15              |                       354.77 ms            | 
  ├ sirius::Hamiltonian_k::apply_h_s                                    |                        87.35 ms            |                 117              |                        10.22 s             | 
  ├ sirius::Hamiltonian_k::get_h_o_diag                                 |                        18.81 ms            |                  15              |                       282.21 ms            | 
  ├ sirius::Potential::generate_D_operator_matrix                       |                       268.31 ms            |                  16              |                         4.29 s             | 
  ├ sirius::Local_operator::apply_h                                     |                        50.49 ms            |                 117              |                         5.91 s             | 
  ├ sirius::Band::diag_pseudo_potential_davidson|update_phi             |                         5.22 ms            |                  47              |                       245.18 ms            | 
  ├ sirius::Radial_integrals|atomic_wfs                                 |                        60.13 ms            |                   4              |                       240.51 ms            | 
  ├ Eigensolver_cuda|zhegvdx                                            |                       230.20 ms            |                   1              |                       230.20 ms            | 
  ├ sirius::Unit_cell::initialize                                       |                       221.06 ms            |                   1              |                       221.06 ms            | 
  ├ sirius::normalized_preconditioned_residuals                         |                         2.14 ms            |                 101              |                       215.72 ms            | 
  ├ sirius::Atom_type::init                                             |                       102.13 ms            |                   2              |                       204.26 ms            | 
  ├ sddk::Gvec_shells::remap_backward                                   |                        12.89 ms            |                  30              |                       386.81 ms            | 
  ├ sddk::Gvec::init                                                    |                        64.83 ms            |                   3              |                       194.48 ms            | 
- ├ sirius::K_point_set::create_k_mesh                                  |      133.14 ms →      169.04 ms  (+26.97%) |       1   →       1              |      133.14 ms →      169.04 ms  (+26.97%) | 
  │ ├ sirius::K_point::K_point                                          |        1.26 μs                             |       4                          |        5.05 μs                             | 
  │ └ sirius::K_point_set::initialize                                   |      133.07 ms                             |       1                          |      133.07 ms                             | 
  │   └ sirius::K_point::initialize                                     |       29.50 ms                             |       1                          |       29.50 ms                             | 
  │     ├ sirius::K_point::generate_gkvec                               |       11.08 ms                             |       1                          |       11.08 ms                             | 
  │     │ └ sddk::Gvec::init                                            |        4.88 ms                             |       1                          |        4.88 ms                             | 
  │     ├ sddk::matrix_storage::matrix_storage                          |       11.23 μs                             |       1                          |       11.23 μs                             | 
  │     └ sirius::K_point::update                                       |       15.53 ms                             |       1                          |       15.53 ms                             | 
  │       └ sirius::Beta_projectors                                     |       11.54 ms                             |       1                          |       11.54 ms                             | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.41 ms                             |       1                          |        8.41 ms                             | 
  ├ sirius::Smooth_periodic_function                                    |        2.62 ms                             |       2                          |        5.23 ms                             | 
  ├ sirius::K_point_set::initialize                                     |                       168.93 ms            |                   1              |                       168.93 ms            | 
  ├ sddk::Gvec::find_gvec_shells                                        |                        70.86 ms            |                   2              |                       141.72 ms            | 
  ├ sirius::Radial_integrals|vloc                                       |                        56.33 ms            |                   2              |                       112.66 ms            | 
  ├ sddk::Gvec_shells                                                   |                        96.39 ms            |                   1              |                        96.39 ms            | 
  ├ sirius::Radial_integrals|beta                                       |                        45.10 ms            |                   2              |                        90.20 ms            | 
  ├ sirius::Density::mixer_output                                       |                         5.25 ms            |                  15              |                        78.75 ms            | 
  ├ sirius::Non_local_operator::apply                                   |                        14.28 ms            |                 234              |                         3.34 s             | 
  ├ sirius::Density::initial_density                                    |                        57.18 ms            |                   1              |                        57.18 ms            | 
  ├ sddk::orthogonalize|tmtrx                                           |                       490.74 μs            |                 116              |                        56.93 ms            | 
  ├ sirius::Potential                                                   |       51.83 ms →       51.94 ms   (+0.21%) |       1   →       1              |       51.83 ms →       51.94 ms   (+0.21%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.88 ms                             |       6                          |       17.31 ms                             | 
  │ └ sirius::Potential::update                                         |       34.09 ms                             |       1                          |       34.09 ms                             | 
  │   └ sirius::Potential::generate_local_potential                     |       33.70 ms                             |       1                          |       33.70 ms                             | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       25.99 ms                             |       1                          |       25.99 ms                             | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        7.40 ms                             |       1                          |        7.40 ms                             | 
  ├ sirius::Potential::xc                                               |                        47.05 ms            |                  16              |                       752.80 ms            | 
  ├ sirius::Potential::xc_rg_nonmagnetic                                |                        45.86 ms            |                  16              |                       733.68 ms            | 
  ├ sirius::Hamiltonian_k                                               |                         3.16 ms            |                  16              |                        50.61 ms            | 
  ├ sirius::Beta_projectors_base::prepare                               |                         1.54 ms            |                  31              |                        47.71 ms            | 
- ├ sirius::Density                                                     |       43.29 ms →       47.28 ms   (+9.23%) |       1   →       2   (+100.00%) |       43.29 ms →       94.56 ms (+118.45%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.82 ms                             |       2                          |        5.63 ms                             | 
  │ └ sirius::Density::update                                           |       37.52 ms                             |       1                          |       37.52 ms                             | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       37.30 ms                             |       1                          |       37.30 ms                             | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       27.19 ms                             |       1                          |       27.19 ms                             | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        9.82 ms                             |       1                          |        9.82 ms                             | 
  ├ sirius::Density::initial_density                                    |       59.48 ms                             |       1                          |       59.48 ms                             | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       26.55 ms                             |       1                          |       26.55 ms                             | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        6.83 ms                             |       2                          |       13.65 ms                             | 
  │ └ sirius::Periodic_function::integrate                              |        5.78 ms                             |       1                          |        5.78 ms                             | 
  ├ sirius::Potential::generate                                         |      380.20 ms                             |       1                          |      380.20 ms                             | 
  │ ├ sirius::Potential::poisson                                        |       42.32 ms                             |       1                          |       42.32 ms                             | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       11.05 ms                             |       1                          |       11.05 ms                             | 
  │ │ └ sirius::Periodic_function|inner                                 |        6.05 ms                             |       1                          |        6.05 ms                             | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.61 ms                             |       1                          |        4.61 ms                             | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.60 ms                             |       1                          |        4.60 ms                             | 
  │ ├ sirius::Periodic_function::add                                    |      811.20 μs                             |       2                          |        1.62 ms                             | 
  │ ├ sirius::Potential::xc                                             |       61.50 ms                             |       1                          |       61.50 ms                             | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       61.50 ms                             |       1                          |       61.50 ms                             | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.56 ms                             |       2                          |        5.11 ms                             | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        3.87 ms                             |       1                          |        3.87 ms                             | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.48 ms                             |       1                          |        3.48 ms                             | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      269.90 ms                             |       1                          |      269.90 ms                             | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      487.00 ns                             |       1                          |      487.00 ns                             | 
  ├ sirius::Potential::xc_rg_nonmagnetic|libxc                          |                        19.62 ms            |                  32              |                       627.87 ms            | 
  ├ sirius::Potential::poisson                                          |                        39.28 ms            |                  16              |                       628.45 ms            | 
  ├ sirius::Potential::update                                           |                        37.05 ms            |                   1              |                        37.05 ms            | 
  ├ sirius::K_point::generate_atomic_wave_functions                     |                        36.93 ms            |                   1              |                        36.93 ms            | 
  ├ sirius::Potential::generate_local_potential                         |                        36.67 ms            |                   1              |                        36.67 ms            | 
  ├ sirius::Density::update                                             |                        41.52 ms            |                   2              |                        83.04 ms            | 
  ├ sirius::Density::generate_pseudo_core_charge_density                |                        41.31 ms            |                   2              |                        82.62 ms            | 
  ├ sirius::Radial_integrals|rho_core_pseudo                            |                        15.17 ms            |                   2              |                        30.33 ms            | 
  ├ sirius::Band::set_subspace_mtrx                                     |                         2.23 ms            |                 118              |                       263.12 ms            | 
  ├ sddk::wf_inner                                                      |                         1.83 ms            |                 335              |                       613.91 ms            | 
  ├ sirius::K_point::initialize                                         |                        28.64 ms            |                   1              |                        28.64 ms            | 
  ├ sddk::wf_inner|pw                                                   |                         1.66 ms            |                 335              |                       557.71 ms            | 
  ├ sirius::Simulation_context::make_periodic_function                  |                        28.07 ms            |                   4              |                       112.27 ms            | 
  ├ sirius::Beta_projectors_base::inner                                 |                         7.23 ms            |                 132              |                       954.55 ms            | 
  ├ sirius::Unit_cell::update                                           |                        11.72 ms            |                   2              |                        23.43 ms            | 
  ├ sirius::Density::mixer_input                                        |                         1.03 ms            |                  15              |                        15.51 ms            | 
  ├ sirius::K_point_set::find_band_occupancies                          |                         1.02 ms            |                  15              |                        15.30 ms            | 
  ├ sirius::inner                                                       |                         4.80 ms            |                 377              |                         1.81 s             | 
  ├ sirius::K_point::update                                             |                        14.50 ms            |                   1              |                        14.50 ms            | 
  ├ sirius::Radial_integrals|rho_pseudo                                 |                        13.29 ms            |                   1              |                        13.29 ms            | 
- ├ sirius::Hamiltonian0                                                |        8.76 ms →       11.08 ms  (+26.43%) |       1   →      16   (+1500.00%) |        8.76 ms →      177.26 ms (+1922.86%) | 
  │ ├ sirius::Local_operator                                            |        8.13 ms                             |       1                          |        8.13 ms                             | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.74 ms                             |       1                          |        2.74 ms                             | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        3.97 ms                             |       1                          |        3.97 ms                             | 
  │ ├ sirius::Non_local_operator                                        |      178.78 μs                             |       2                          |      357.55 μs                             | 
  │ ├ sirius::D_operator::initialize                                    |      112.45 μs                             |       1                          |      112.45 μs                             | 
  │ └ sirius::Q_operator::initialize                                    |       93.86 μs                             |       1                          |       93.86 μs                             | 
  ├ sirius::Band::initialize_subspace                                   |        1.29 s                              |       1                          |        1.29 s                              | 
  │ ├ sirius::Hamiltonian_k                                             |       67.33 ms                             |       1                          |       67.33 ms                             | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      290.48 μs                             |       1                          |      290.48 μs                             | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       67.04 ms                             |       1                          |       67.04 ms                             | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.22 s                              |       1                          |        1.22 s                              | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       87.93 ms                             |       4                          |      351.71 ms                             | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       46.74 ms                             |       1                          |       46.74 ms                             | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        8.56 ms                             |       1                          |        8.56 ms                             | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      383.77 ms                             |       1                          |      383.77 ms                             | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      272.34 ms                             |       1                          |      272.34 ms                             | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        4.43 μs                             |       1                          |        4.43 μs                             | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.35 μs                             |       1                          |        3.35 μs                             | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      506.00 ns                             |       1                          |      506.00 ns                             | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |        1.01 μs                             |       1                          |        1.01 μs                             | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.08 ms                             |       1                          |        3.08 ms                             | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.24 ms                             |       1                          |       21.24 ms                             | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       43.53 ms                             |       2                          |       87.05 ms                             | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |        5.35 ms                             |       2                          |       10.69 ms                             | 
  │ │ │ └ sddk::inner                                                   |        5.11 ms                             |       2                          |       10.22 ms                             | 
  │ │ │   └ sddk::inner|local                                           |       23.06 μs                             |       2                          |       46.12 μs                             | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      205.15 ms                             |       1                          |      205.15 ms                             | 
  │ │ └ sddk::transform                                                 |        2.82 ms                             |       1                          |        2.82 ms                             | 
  │ │   ├ sddk::transform|init                                          |       13.73 μs                             |       1                          |       13.73 μs                             | 
  │ │   └ sddk::transform|local                                         |       18.15 μs                             |       1                          |       18.15 μs                             | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      662.00 ns                             |       1                          |      662.00 ns                             | 
  ├ sirius::DFT_ground_state::scf_loop                                  |       67.35 s                              |       1                          |       67.35 s                              | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.44 ms                             |      19                          |       46.28 ms                             | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.35 s                              |      20                          |       67.10 s                              | 
  │ │ ├ sirius::Hamiltonian0                                            |        4.70 ms                             |      20                          |       94.09 ms                             | 
  │ │ │ ├ sirius::Local_operator                                        |        4.06 ms                             |      20                          |       81.13 ms                             | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      548.58 μs                             |      20                          |       10.97 ms                             | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.58 ms                             |      20                          |       51.65 ms                             | 
  │ │ │ ├ sirius::Non_local_operator                                    |      163.41 μs                             |      40                          |        6.54 ms                             | 
  │ │ │ ├ sirius::D_operator::initialize                                |      140.25 μs                             |      20                          |        2.80 ms                             | 
  │ │ │ └ sirius::Q_operator::initialize                                |       96.46 μs                             |      20                          |        1.93 ms                             | 
  │ │ ├ sirius::Band::solve                                             |        2.11 s                              |      20                          |       42.29 s                              | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      254.15 μs                             |      20                          |        5.08 ms                             | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      245.41 μs                             |      20                          |        4.91 ms                             | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        6.85 μs                             |      20                          |      137.07 μs                             | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.96 s                              |      20                          |       39.10 s                              | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       89.59 ms                             |      20                          |        1.79 s                              | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |       11.62 ms                             |     120                          |        1.39 s                              | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       17.63 ms                             |      20                          |      352.56 ms                             | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      455.08 μs                             |      20                          |        9.10 ms                             | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        8.38 ms                             |      40                          |      335.17 ms                             | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.84 s                              |      20                          |       36.82 s                              | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       57.24 ms                             |     250                          |       14.31 s                              | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       35.64 ms                             |     250                          |        8.91 s                              | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.05 μs                             |     250                          |      512.32 μs                             | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.65 μs                             |     250                          |      411.50 μs                             | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      443.40 ns                             |     250                          |      110.85 μs                             | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      517.47 ns                             |     250                          |      129.37 μs                             | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.77 ms                             |     250                          |      692.99 ms                             | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.52 ms                             |     250                          |      878.80 ms                             | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.65 ms                             |     500                          |        3.82 s                              | 
  │ │ │ │   ├ sddk::orthogonalize                                       |        8.10 ms                             |     250                          |        2.03 s                              | 
  │ │ │ │   │ ├ sddk::inner                                             |      993.80 μs                             |     480                          |      477.02 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       21.30 μs                             |     480                          |       10.22 ms                             | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      318.03 μs                             |     250                          |       79.51 ms                             | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        2.94 ms                             |     250                          |      735.51 ms                             | 
  │ │ │ │   │ └ sddk::transform                                         |        3.18 ms                             |     230                          |      732.16 ms                             | 
  │ │ │ │   │   ├ sddk::transform|init                                  |       17.49 μs                             |     230                          |        4.02 ms                             | 
  │ │ │ │   │   └ sddk::transform|local                                 |        7.24 μs                             |     690                          |        5.00 ms                             | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.78 ms                             |     250                          |      444.32 ms                             | 
  │ │ │ │   │ └ sddk::inner                                             |        1.58 ms                             |     250                          |      394.26 ms                             | 
  │ │ │ │   │   └ sddk::inner|local                                     |       22.40 μs                             |     250                          |        5.60 ms                             | 
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       76.40 ms                             |     250                          |       19.10 s                              | 
  │ │ │ │   ├ sirius::residuals                                         |        3.02 ms                             |     245                          |      740.09 ms                             | 
  │ │ │ │   │ ├ sddk::transform                                         |        1.95 ms                             |     231                          |      451.34 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       14.76 μs                             |     231                          |        3.41 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       10.03 μs                             |     462                          |        4.64 ms                             | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.17 ms                             |     231                          |      270.84 ms                             | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        7.99 ms                             |      25                          |      199.78 ms                             | 
  │ │ │ │     └ sddk::transform                                         |        6.57 ms                             |      30                          |      197.22 ms                             | 
  │ │ │ │       ├ sddk::transform|init                                  |       11.03 μs                             |      30                          |      330.95 μs                             | 
  │ │ │ │       └ sddk::transform|local                                 |       11.69 μs                             |      35                          |      408.98 μs                             | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      382.35 ns                             |      20                          |        7.65 μs                             | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       22.75 μs                             |      20                          |      455.08 μs                             | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.50 ms                             |      20                          |       29.91 ms                             | 
  │ │ ├ sirius::Density::generate                                       |      568.78 ms                             |      20                          |       11.38 s                              | 
  │ │ │ ├ sirius::Density::generate_valence                             |      417.85 ms                             |      20                          |        8.36 s                              | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        7.92 μs                             |      20                          |      158.41 μs                             | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.27 μs                             |      20                          |      145.40 μs                             | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       27.45 ms                             |      20                          |      549.01 ms                             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.59 μs                             |      20                          |      151.76 μs                             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        5.00 ms                             |      20                          |       99.99 ms                             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       21.43 ms                             |      20                          |      428.59 ms                             | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      884.25 ns                             |      20                          |       17.69 μs                             | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      118.66 ms                             |      20                          |        2.37 s                              | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.22 ms                             |      20                          |       44.42 ms                             | 
  │ │ │ │ └ sirius::Density::augment                                    |      238.97 ms                             |      20                          |        4.78 s                              | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |      238.75 ms                             |      20                          |        4.77 s                              | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      121.77 ms                             |      20                          |        2.44 s                              | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      121.77 ms                             |      20                          |        2.44 s                              | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       40.00 ms                             |      20                          |      800.01 ms                             | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       68.45 ms                             |      20                          |        1.37 s                              | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.68 ms                             |      20                          |      253.53 ms                             | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.50 ms                             |      20                          |      470.03 ms                             | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        5.65 ms                             |      20                          |      112.97 ms                             | 
  │ │ ├ sirius::Density::mix                                            |      135.89 ms                             |      20                          |        2.72 s                              | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      295.15 μs                             |      20                          |        5.90 ms                             | 
  │ │ │ ├ sirius::Periodic_function|inner                               |        4.94 ms                             |     244                          |        1.21 s                              | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.81 ms                             |     244                          |        1.17 s                              | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.81 ms                             |     244                          |        1.17 s                              | 
  │ │ │ └ sirius::Density::mixer_output                                 |        4.70 ms                             |      20                          |       93.94 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        3.97 ms                             |      20                          |       79.43 ms                             | 
  │ │ ├ sirius::Potential::generate                                     |      373.85 ms                             |      20                          |        7.48 s                              | 
  │ │ │ ├ sirius::Potential::poisson                                    |       43.13 ms                             |      20                          |      862.66 ms                             | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       11.91 ms                             |      20                          |      238.19 ms                             | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |        5.89 ms                             |      20                          |      117.89 ms                             | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.63 ms                             |      20                          |       92.62 ms                             | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.63 ms                             |      20                          |       92.61 ms                             | 
  │ │ │ ├ sirius::Periodic_function::add                                |      781.27 μs                             |      40                          |       31.25 ms                             | 
  │ │ │ ├ sirius::Potential::xc                                         |       54.95 ms                             |      20                          |        1.10 s                              | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       54.94 ms                             |      20                          |        1.10 s                              | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |      654.51 μs                             |      40                          |       26.18 ms                             | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.09 ms                             |      20                          |       81.77 ms                             | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.57 ms                             |      20                          |       71.48 ms                             | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      269.24 ms                             |      20                          |        5.38 s                              | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      245.30 ns                             |      20                          |        4.91 μs                             | 
  │ │ ├ sirius::Field4D::symmetrize                                     |       97.49 ms                             |      20                          |        1.95 s                              | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |       97.49 ms                             |      20                          |        1.95 s                              | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       15.87 ms                             |      20                          |      317.50 ms                             | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       68.33 ms                             |      20                          |        1.37 s                              | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.65 ms                             |      20                          |      253.05 ms                             | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.68 ms                             |      20                          |      113.53 ms                             | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.74 ms                             |     140                          |      664.11 ms                             | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.56 ms                             |     140                          |      638.21 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.56 ms                             |     140                          |      638.09 ms                             | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.79 ms                             |      60                          |      287.30 ms                             | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.75 ms                             |      60                          |      284.83 ms                             | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.54 ms                             |      20                          |       90.86 ms                             | 
  │ │ └ sirius::Density::get_magnetisation                              |       75.03 μs                             |      20                          |        1.50 ms                             | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |       69.34 μs                             |      20                          |        1.39 ms                             | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.71 ms                             |       2                          |       11.42 ms                             | 
  │ ├ sirius::Periodic_function|inner                                   |        4.53 ms                             |       6                          |       27.18 ms                             | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.52 ms                             |       6                          |       27.14 ms                             | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.52 ms                             |       6                          |       27.14 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.75 ms                             |       3                          |       14.24 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.74 ms                             |       3                          |       14.22 ms                             | 
  ├ sirius::Periodic_function|inner                                     |        4.56 ms                             |       2                          |        9.12 ms                             | 
  │ └ sirius::Periodic_function|inner_local                             |        4.56 ms                             |       2                          |        9.11 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.56 ms                             |       2                          |        9.11 ms                             | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.76 ms                             |       1                          |        4.76 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.75 ms                             |       1                          |        4.75 ms                             | 
  ├ sirius::finalize                                                    |      918.37 ms                             |       1                          |      918.37 ms                             | 
  ├ sirius::Unit_cell::get_symmetry                                     |                         8.11 ms            |                   2              |                        16.21 ms            | 
  ├ sirius::Unit_cell_symmetry                                          |                         8.04 ms            |                   2              |                        16.09 ms            | 
  ├ sirius::Smooth_periodic_function::gather_f_pw                       |                         5.66 ms            |                   2              |                        11.32 ms            | 
  ├ sirius::K_point::generate_gkvec                                     |                        11.25 ms            |                   1              |                        11.25 ms            | 
  ├ sirius::Beta_projectors                                             |                        10.49 ms            |                   1              |                        10.49 ms            | 
  ├ sirius::Simulation_context::init_comm                               |                         8.63 ms            |                   1              |                         8.63 ms            | 
  ├ sirius::Beta_projectors::generate_pw_coefs_t                        |                         8.32 ms            |                   1              |                         8.32 ms            | 
  ├ sirius::Band::initialize_subspace|kp|wf                             |                         6.68 ms            |                   1              |                         6.68 ms            | 
  ├ sirius::Smooth_periodic_function::fft_transform                     |                         3.66 ms            |                 113              |                       413.89 ms            | 
  ├ sirius::Local_operator                                              |                         4.18 ms            |                  16              |                        66.85 ms            | 
  ├ sirius::Periodic_function::integrate                                |                         4.65 ms            |                  16              |                        74.48 ms            | 
  ├ sirius::Q_operator::initialize                                      |                         4.41 ms            |                  16              |                        70.55 ms            | 
  ├ sirius::Unit_cell::find_nearest_neighbours                          |                         3.54 ms            |                   2              |                         7.08 ms            | 
  ├ sirius::Beta_projectors_base::generate                              |                         3.49 ms            |                 132              |                       460.91 ms            | 
  ├ sirius::Unit_cell_symmetry|spg                                      |                         2.67 ms            |                   2              |                         5.34 ms            | 
  ├ sddk::wf_trans                                                      |                         2.59 ms            |                 282              |                       731.10 ms            | 
  ├ sddk::wf_trans|pw                                                   |                         1.18 ms            |                 617              |                       730.39 ms            | 
  ├ sirius::D_operator::initialize                                      |                         2.23 ms            |                  16              |                        35.66 ms            | 
  ├ sirius::Simulation_context::init_atoms_to_grid_idx                  |                         1.94 ms            |                   1              |                         1.94 ms            | 
  ├ sirius::Periodic_function::add                                      |                       713.10 μs            |                  32              |                        22.82 ms            | 
  ├ sirius::K_point_set::sync_band                                      |                        38.68 μs            |                  30              |                         1.16 ms            | 
  ├ sirius::Unit_cell_symmetry|equiv                                    |                       506.95 μs            |                   2              |                         1.01 ms            | 
  ├ sirius::Local_operator::prepare_k                                   |                       185.02 μs            |                  16              |                         2.96 ms            | 
  ├ sirius::Non_local_operator                                          |                        96.73 μs            |                  32              |                         3.10 ms            | 
  ├ sirius::K_point::K_point                                            |                         8.61 μs            |                   4              |                        34.42 μs            | 
  ├ sirius::Unit_cell_symmetry|mag                                      |                        14.71 μs            |                   2              |                        29.43 μs            | 
  ├ sddk::matrix_storage::remap_forward                                 |                         2.28 μs            |                 132              |                       300.56 μs            | 
  ├ sddk::wf_inner|scale_back                                           |                       252.47 ns            |                 335              |                        84.58 μs            | 
  ├ sddk::matrix_storage::remap_backward                                |                       642.51 ns            |                 117              |                        75.17 μs            | 
  ├ sirius::Beta_projectors_base::dismiss                               |                       452.26 ns            |                  31              |                        14.02 μs            | 
  ├ sirius::Potential::generate_PAW_effective_potential                 |                       136.19 ns            |                  16              |                         2.18 μs            | 
  └ sddk::wf_inner|scale                                                |                        93.82 ns            |                 335              |                        31.43 μs            | 
  ====================================================================================================================================================================================================
```
