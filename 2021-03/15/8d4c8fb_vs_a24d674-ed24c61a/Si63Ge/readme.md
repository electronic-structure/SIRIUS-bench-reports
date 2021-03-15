# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs 8d4c8fb637741d881d5cdc9faf167adefd93fb67
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |       77.52 s  →       47.50 s   (-38.72%) |       1   →       1              |       77.52 s  →       47.50 s   (-38.72%) | 
  ├ sirius::initialize                                                  |        2.83 s  →        2.85 s    (+0.70%) |       1   →       1              |        2.83 s  →        2.85 s    (+0.70%) | 
  ├ sirius::Simulation_context::initialize                              |        3.72 s  →        3.72 s    (+0.01%) |       1   →       1              |        3.72 s  →        3.72 s    (+0.01%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       46.46 ms →      479.44 μs  (-98.97%) |       1   →       1              |       46.46 ms →      479.44 μs  (-98.97%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      164.46 ms →      107.09 ms  (-34.88%) |       1   →       1              |      164.46 ms →      107.09 ms  (-34.88%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       72.81 ms →       41.57 ms  (-42.90%) |       2   →       2              |      145.62 ms →       83.15 ms  (-42.90%) | 
- │ │ └ sirius::Unit_cell::update                                       |       18.75 ms →       23.81 ms  (+26.99%) |       1   →       1              |       18.75 ms →       23.81 ms  (+26.99%) | 
+ │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        7.51 ms →        3.64 ms  (-51.50%) |       1   →       1              |        7.51 ms →        3.64 ms  (-51.50%) | 
- │ │   └ sirius::Unit_cell::get_symmetry                               |       11.16 ms →       20.08 ms  (+79.94%) |       1   →       1              |       11.16 ms →       20.08 ms  (+79.94%) | 
- │ │     └ sirius::Unit_cell_symmetry                                  |       11.08 ms →       20.01 ms  (+80.54%) |       1   →       1              |       11.08 ms →       20.01 ms  (+80.54%) | 
+ │ │       ├ sirius::Unit_cell_symmetry|spg                            |        3.44 ms →        2.77 ms  (-19.46%) |       1   →       1              |        3.44 ms →        2.77 ms  (-19.46%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      540.69 μs →      504.24 μs   (-6.74%) |       1   →       1              |      540.69 μs →      504.24 μs   (-6.74%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       16.88 μs →       16.07 μs   (-4.78%) |       1   →       1              |       16.88 μs →       16.07 μs   (-4.78%) | 
  │ └ sirius::Simulation_context::update                                |        3.42 s  →        3.52 s    (+2.89%) |       1   →       1              |        3.42 s  →        3.52 s    (+2.89%) | 
  │   ├ sirius::Unit_cell::update                                       |        6.96 ms →        6.97 ms   (+0.06%) |       1   →       1              |        6.96 ms →        6.97 ms   (+0.06%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.66 ms →        3.65 ms   (-0.21%) |       1   →       1              |        3.66 ms →        3.65 ms   (-0.21%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.26 ms →        3.26 ms   (+0.10%) |       1   →       1              |        3.26 ms →        3.26 ms   (+0.10%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.22 ms →        3.19 ms   (-0.71%) |       1   →       1              |        3.22 ms →        3.19 ms   (-0.71%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.67 ms →        2.64 ms   (-1.23%) |       1   →       1              |        2.67 ms →        2.64 ms   (-1.23%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      504.39 μs →      507.01 μs   (+0.52%) |       1   →       1              |      504.39 μs →      507.01 μs   (+0.52%) | 
- │   │     └ sirius::Unit_cell_symmetry|mag                            |       14.92 μs →       21.85 μs  (+46.46%) |       1   →       1              |       14.92 μs →       21.85 μs  (+46.46%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      213.11 ms →      218.45 ms   (+2.51%) |       2   →       2              |      426.22 ms →      436.90 ms   (+2.51%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.14 ms →       15.18 ms   (+0.28%) |       2   →       2              |       30.28 ms →       30.36 ms   (+0.28%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.28 ms →       13.27 ms   (-0.14%) |       1   →       1              |       13.28 ms →       13.27 ms   (-0.14%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.35 ms →       56.44 ms   (+0.14%) |       2   →       2              |      112.71 ms →      112.87 ms   (+0.14%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       44.98 ms →       45.02 ms   (+0.08%) |       2   →       2              |       89.96 ms →       90.03 ms   (+0.08%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.05 ms →       60.24 ms   (+0.32%) |       4   →       4              |      240.19 ms →      240.95 ms   (+0.32%) | 
  │   ├ sddk::Gvec::init                                                |       93.20 ms →       92.99 ms   (-0.22%) |       2   →       2              |      186.39 ms →      185.97 ms   (-0.22%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       69.65 ms →       69.48 ms   (-0.25%) |       2   →       2              |      139.31 ms →      138.97 ms   (-0.25%) | 
  │   ├ sddk::Gvec_shells                                               |      100.85 ms →       93.26 ms   (-7.53%) |       1   →       1              |      100.85 ms →       93.26 ms   (-7.53%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.68 ms →        1.70 ms   (+1.52%) |       1   →       1              |        1.68 ms →        1.70 ms   (+1.52%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      554.05 ms →      601.21 ms   (+8.51%) |       2   →       2              |        1.11 s  →        1.20 s    (+8.51%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |      147.80 ms →      148.03 ms   (+0.16%) |       1   →       1              |      147.80 ms →      148.03 ms   (+0.16%) | 
- │ ├ sirius::K_point::K_point                                          |        1.33 μs →        4.65 μs (+248.67%) |       4   →       4              |        5.33 μs →       18.59 μs (+248.67%) | 
  │ └ sirius::K_point_set::initialize                                   |      147.73 ms →      147.94 ms   (+0.14%) |       1   →       1              |      147.73 ms →      147.94 ms   (+0.14%) | 
  │   └ sirius::K_point::initialize                                     |       28.22 ms →       28.33 ms   (+0.39%) |       1   →       1              |       28.22 ms →       28.33 ms   (+0.39%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       11.15 ms →       11.26 ms   (+0.97%) |       1   →       1              |       11.15 ms →       11.26 ms   (+0.97%) | 
  │     │ └ sddk::Gvec::init                                            |        4.82 ms →        4.90 ms   (+1.77%) |       1   →       1              |        4.82 ms →        4.90 ms   (+1.77%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        8.53 μs                             |       1                          |        8.53 μs                             | 
  │     └ sirius::K_point::update                                       |       14.17 ms →       14.16 ms   (-0.06%) |       1   →       1              |       14.17 ms →       14.16 ms   (-0.06%) | 
  │       └ sirius::Beta_projectors                                     |       10.24 ms →       10.24 ms   (+0.02%) |       1   →       1              |       10.24 ms →       10.24 ms   (+0.02%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.25 ms →        8.36 ms   (+1.29%) |       1   →       1              |        8.25 ms →        8.36 ms   (+1.29%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.53 ms                             |       2                          |        5.05 ms                             | 
  ├ sirius::Potential                                                   |       54.90 ms →       49.56 ms   (-9.72%) |       1   →       1              |       54.90 ms →       49.56 ms   (-9.72%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.89 ms                             |       6                          |       17.32 ms                             | 
  │ └ sirius::Potential::update                                         |       37.15 ms →       34.60 ms   (-6.87%) |       1   →       1              |       37.15 ms →       34.60 ms   (-6.87%) | 
  │   └ sirius::Potential::generate_local_potential                     |       36.77 ms →       34.22 ms   (-6.95%) |       1   →       1              |       36.77 ms →       34.22 ms   (-6.95%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       25.89 ms →       26.10 ms   (+0.82%) |       1   →       1              |       25.89 ms →       26.10 ms   (+0.82%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       10.58 ms →        5.03 ms  (-52.45%) |       1   →       1              |       10.58 ms →        5.03 ms  (-52.45%) | 
+ ├ sirius::Density                                                     |       44.01 ms →       38.17 ms  (-13.27%) |       1   →       1              |       44.01 ms →       38.17 ms  (-13.27%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.80 ms                             |       2                          |        5.60 ms                             | 
+ │ └ sirius::Density::update                                           |       38.27 ms →       32.40 ms  (-15.35%) |       1   →       1              |       38.27 ms →       32.40 ms  (-15.35%) | 
+ │   └ sirius::Density::generate_pseudo_core_charge_density            |       38.05 ms →       32.16 ms  (-15.48%) |       1   →       1              |       38.05 ms →       32.16 ms  (-15.48%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       27.24 ms →       26.06 ms   (-4.33%) |       1   →       1              |       27.24 ms →       26.06 ms   (-4.33%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       10.52 ms →        4.91 ms  (-53.37%) |       1   →       1              |       10.52 ms →        4.91 ms  (-53.37%) | 
  ├ sirius::Density::initial_density                                    |       61.66 ms →       55.88 ms   (-9.37%) |       1   →       1              |       61.66 ms →       55.88 ms   (-9.37%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       26.62 ms →       25.44 ms   (-4.43%) |       1   →       1              |       26.62 ms →       25.44 ms   (-4.43%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        7.84 ms →        6.00 ms  (-23.41%) |       2   →       2              |       15.67 ms →       12.00 ms  (-23.41%) | 
+ │ └ sirius::Periodic_function::integrate                              |        5.73 ms →        4.53 ms  (-20.93%) |       1   →       1              |        5.73 ms →        4.53 ms  (-20.93%) | 
  ├ sirius::Potential::generate                                         |      381.08 ms →      361.09 ms   (-5.25%) |       1   →       1              |      381.08 ms →      361.09 ms   (-5.25%) | 
+ │ ├ sirius::Potential::poisson                                        |       43.25 ms →       34.95 ms  (-19.18%) |       1   →       1              |       43.25 ms →       34.95 ms  (-19.18%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       11.52 ms →        3.89 ms  (-66.22%) |       1   →       1              |       11.52 ms →        3.89 ms  (-66.22%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        6.13 ms                             |       1                          |        6.13 ms                             | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.85 ms                             |       1                          |        4.85 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.85 ms                             |       1                          |        4.85 ms                             | 
  │ │ └ sirius::inner                                                   |                         5.65 ms            |                   1              |                         5.65 ms            | 
  │ ├ sirius::Periodic_function::add                                    |      741.75 μs →      703.64 μs   (-5.14%) |       2   →       2              |        1.48 ms →        1.41 ms   (-5.14%) | 
+ │ ├ sirius::Potential::xc                                             |       62.25 ms →       49.26 ms  (-20.86%) |       1   →       1              |       62.25 ms →       49.26 ms  (-20.86%) | 
+ │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       62.23 ms →       48.09 ms  (-22.73%) |       1   →       1              |       62.23 ms →       48.09 ms  (-22.73%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.54 ms                             |       2                          |        5.09 ms                             | 
  │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        4.94 ms                             |       1                          |        4.94 ms                             | 
  │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                    |                        20.01 ms            |                   2              |                        40.03 ms            | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.72 ms →        4.27 ms  (+14.87%) |       1   →       1              |        3.72 ms →        4.27 ms  (+14.87%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      268.99 ms →      268.24 ms   (-0.28%) |       1   →       1              |      268.99 ms →      268.24 ms   (-0.28%) | 
+ │ └ sirius::Potential::generate_PAW_effective_potential               |      206.00 ns →      144.00 ns  (-30.10%) |       1   →       1              |      206.00 ns →      144.00 ns  (-30.10%) | 
- ├ sirius::Hamiltonian0                                                |        7.72 ms →       12.96 ms  (+67.87%) |       1   →       1              |        7.72 ms →       12.96 ms  (+67.87%) | 
+ │ ├ sirius::Local_operator                                            |        7.06 ms →        6.34 ms  (-10.21%) |       1   →       1              |        7.06 ms →        6.34 ms  (-10.21%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.74 ms                             |       1                          |        2.74 ms                             | 
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        3.29 ms →        2.85 ms  (-13.20%) |       1   →       1              |        3.29 ms →        2.85 ms  (-13.20%) | 
+ │ ├ sirius::Non_local_operator                                        |      192.12 μs →       68.05 μs  (-64.58%) |       2   →       2              |      384.25 μs →      136.11 μs  (-64.58%) | 
- │ ├ sirius::D_operator::initialize                                    |      106.23 μs →        2.20 ms (+1970.83%) |       1   →       1              |      106.23 μs →        2.20 ms (+1970.83%) | 
- │ └ sirius::Q_operator::initialize                                    |       96.38 μs →        4.22 ms (+4276.45%) |       1   →       1              |       96.38 μs →        4.22 ms (+4276.45%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.30 s  →        1.28 s    (-1.80%) |       1   →       1              |        1.30 s  →        1.28 s    (-1.80%) | 
+ │ ├ sirius::Hamiltonian_k                                             |       66.64 ms →       37.93 ms  (-43.08%) |       1   →       1              |       66.64 ms →       37.93 ms  (-43.08%) | 
+ │ │ ├ sirius::Local_operator::prepare_k                               |      342.64 μs →      221.27 μs  (-35.42%) |       1   →       1              |      342.64 μs →      221.27 μs  (-35.42%) | 
+ │ │ └ sirius::Beta_projectors_base::prepare                           |       66.29 ms →       37.71 ms  (-43.12%) |       1   →       1              |       66.29 ms →       37.71 ms  (-43.12%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.24 s  →        1.24 s    (+0.37%) |       1   →       1              |        1.24 s  →        1.24 s    (+0.37%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       90.92 ms                             |       4                          |      363.70 ms                             | 
+ │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       46.49 ms →       38.38 ms  (-17.46%) |       1   →       1              |       46.49 ms →       38.38 ms  (-17.46%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        8.96 ms →        8.08 ms   (-9.77%) |       1   →       1              |        8.96 ms →        8.08 ms   (-9.77%) | 
+ │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      384.03 ms →      312.82 ms  (-18.54%) |       1   →       1              |      384.03 ms →      312.82 ms  (-18.54%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      271.94 ms →      244.97 ms   (-9.92%) |       1   →       1              |      271.94 ms →      244.97 ms   (-9.92%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        4.19 μs →        3.81 μs   (-8.86%) |       1   →       1              |        4.19 μs →        3.81 μs   (-8.86%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.04 μs                             |       1                          |        3.04 μs                             | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      387.00 ns                             |       1                          |      387.00 ns                             | 
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                        |        1.01 μs →      791.00 ns  (-21.99%) |       1   →       1              |        1.01 μs →      791.00 ns  (-21.99%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.06 ms →        3.17 ms   (+3.85%) |       1   →       1              |        3.06 ms →        3.17 ms   (+3.85%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::inner                           |       38.33 ms →       21.28 ms  (-44.48%) |       1   →       1              |       38.33 ms →       21.28 ms  (-44.48%) | 
+ │ │ │ └ sirius::Non_local_operator::apply                             |       35.33 ms →       21.68 ms  (-38.65%) |       2   →       2              |       70.66 ms →       43.35 ms  (-38.65%) | 
- │ │ ├ sirius::Band::set_subspace_mtrx                                 |        5.36 ms →       16.20 ms (+202.23%) |       2   →       2              |       10.72 ms →       32.41 ms (+202.23%) | 
  │ │ │ ├ sddk::inner                                                   |        5.15 ms                             |       2                          |       10.30 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       26.44 μs                             |       2                          |       52.89 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        15.99 ms            |                   2              |                        31.98 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        84.00 ns            |                   2              |                       168.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        15.87 ms            |                   2              |                        31.73 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                       420.50 ns            |                   2              |                       841.00 ns            | 
- │ │ ├ Eigensolver_cuda|zhegvdx                                        |      205.75 ms →      249.94 ms  (+21.48%) |       1   →       1              |      205.75 ms →      249.94 ms  (+21.48%) | 
  │ │ ├ sddk::transform                                                 |        2.81 ms                             |       1                          |        2.81 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       14.61 μs                             |       1                          |       14.61 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       18.08 μs                             |       1                          |       18.08 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                         2.61 ms            |                   1              |                         2.61 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                         2.60 ms            |                   1              |                         2.60 ms            | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      527.00 ns →      478.00 ns   (-9.30%) |       1   →       1              |      527.00 ns →      478.00 ns   (-9.30%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |       67.64 s  →       37.83 s   (-44.07%) |       1   →       1              |       67.64 s  →       37.83 s   (-44.07%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.42 ms                             |      19                          |       46.04 ms                             | 
  │ ├ sirius::Density                                                   |                        49.46 ms            |                   1              |                        49.46 ms            | 
  │ │ └ sirius::Density::update                                         |                        43.64 ms            |                   1              |                        43.64 ms            | 
  │ │   └ sirius::Density::generate_pseudo_core_charge_density          |                        43.29 ms            |                   1              |                        43.29 ms            | 
  │ │     ├ sirius::Simulation_context::make_periodic_function          |                        25.99 ms            |                   1              |                        25.99 ms            | 
  │ │     └ sirius::Smooth_periodic_function::fft_transform             |                         5.03 ms            |                   1              |                         5.03 ms            | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.37 s  →        2.50 s   (-25.76%) |      20   →      15    (-25.00%) |       67.43 s  →       37.54 s   (-44.32%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        5.27 ms →       10.94 ms (+107.60%) |      20   →      15    (-25.00%) |      105.43 ms →      164.15 ms  (+55.70%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        4.55 ms →        4.33 ms   (-4.86%) |      20   →      15    (-25.00%) |       91.04 ms →       64.96 ms  (-28.65%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      547.17 μs                             |      20                          |       10.94 ms                             | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.85 ms →        2.62 ms   (-8.25%) |      20   →      15    (-25.00%) |       57.06 ms →       39.26 ms  (-31.19%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |      210.43 μs →       63.99 μs  (-69.59%) |      40   →      30    (-25.00%) |        8.42 ms →        1.92 ms  (-77.19%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |      119.39 μs →        2.16 ms (+1711.30%) |      20   →      15    (-25.00%) |        2.39 ms →       32.44 ms (+1258.48%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       98.51 μs →        4.25 ms (+4215.58%) |      20   →      15    (-25.00%) |        1.97 ms →       63.77 ms (+3136.69%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.13 s  →        1.30 s   (-38.94%) |      20   →      15    (-25.00%) |       42.50 s  →       19.46 s   (-54.21%) | 
+ │ │ │ ├ sirius::Hamiltonian_k                                         |      223.13 μs →      190.96 μs  (-14.41%) |      20   →      15    (-25.00%) |        4.46 ms →        2.86 ms  (-35.81%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      213.24 μs →      180.78 μs  (-15.22%) |      20   →      15    (-25.00%) |        4.26 ms →        2.71 ms  (-36.42%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        7.58 μs →        5.65 μs  (-25.48%) |      20   →      15    (-25.00%) |      151.51 μs →       84.68 μs  (-44.11%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.97 s  →        1.13 s   (-42.63%) |      20   →      15    (-25.00%) |       39.40 s  →       16.95 s   (-56.97%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       95.13 ms                             |      20                          |        1.90 s                              | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |       11.37 ms                             |     120                          |        1.36 s                              | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       17.90 ms →       18.44 ms   (+3.01%) |      20   →      15    (-25.00%) |      357.99 ms →      276.58 ms  (-22.74%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      477.27 μs                             |      20                          |        9.55 ms                             | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        8.52 ms                             |      40                          |      340.77 ms                             | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.85 s                              |      20                          |       37.00 s                              | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::apply_h_s                          |       62.22 ms                             |     250                          |       15.55 s                              | 
  │ │ │ │ │ │ ├ sirius::Local_operator::apply_h                         |       36.38 ms                             |     250                          |        9.10 s                              | 
  │ │ │ │ │ │ │ ├ sddk::matrix_storage::remap_forward                   |        2.06 μs                             |     250                          |      515.56 μs                             | 
  │ │ │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.76 μs                             |     250                          |      439.42 μs                             | 
  │ │ │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                   |      430.11 ns                             |     250                          |      107.53 μs                             | 
  │ │ │ │ │ │ │ └ sddk::matrix_storage::remap_backward                  |      528.92 ns                             |     250                          |      132.23 μs                             | 
  │ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                  |        2.91 ms                             |     250                          |      726.71 ms                             | 
  │ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                     |        3.57 ms                             |     250                          |      893.29 ms                             | 
  │ │ │ │ │ │ └ sirius::Non_local_operator::apply                       |        9.67 ms                             |     500                          |        4.83 s                              | 
  │ │ │ │ │ ├ sddk::orthogonalize                                       |        8.11 ms                             |     250                          |        2.03 s                              | 
  │ │ │ │ │ │ ├ sddk::inner                                             |        1.14 ms                             |     480                          |      546.18 ms                             | 
  │ │ │ │ │ │ │ └ sddk::inner|local                                     |       23.15 μs                             |     480                          |       11.11 ms                             | 
  │ │ │ │ │ │ ├ sddk::orthogonalize|tmtrx                               |      317.93 μs                             |     250                          |       79.48 ms                             | 
  │ │ │ │ │ │ ├ sddk::orthogonalize|transform                           |        2.71 ms                             |     250                          |      676.29 ms                             | 
  │ │ │ │ │ │ └ sddk::transform                                         |        3.15 ms                             |     230                          |      724.12 ms                             | 
  │ │ │ │ │ │   ├ sddk::transform|init                                  |       18.11 μs                             |     230                          |        4.17 ms                             | 
  │ │ │ │ │ │   └ sddk::transform|local                                 |        7.81 μs                             |     690                          |        5.39 ms                             | 
  │ │ │ │ │ ├ sirius::Band::set_subspace_mtrx                           |        1.99 ms                             |     250                          |      496.72 ms                             | 
  │ │ │ │ │ │ └ sddk::inner                                             |        1.78 ms                             |     250                          |      445.96 ms                             | 
  │ │ │ │ │ │   └ sddk::inner|local                                     |       24.43 μs                             |     250                          |        6.11 ms                             | 
  │ │ │ │ │ ├ Eigensolver_cuda|zheevdx                                  |       71.60 ms                             |     250                          |       17.90 s                              | 
  │ │ │ │ │ ├ sirius::residuals                                         |        3.40 ms                             |     245                          |      832.89 ms                             | 
  │ │ │ │ │ │ ├ sddk::transform                                         |        2.00 ms                             |     231                          |      461.47 ms                             | 
  │ │ │ │ │ │ │ ├ sddk::transform|init                                  |       16.15 μs                             |     231                          |        3.73 ms                             | 
  │ │ │ │ │ │ │ └ sddk::transform|local                                 |       10.56 μs                             |     462                          |        4.88 ms                             | 
  │ │ │ │ │ │ └ sirius::normalized_preconditioned_residuals             |        1.53 ms                             |     231                          |      353.40 ms                             | 
  │ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        7.41 ms                             |      25                          |      185.28 ms                             | 
  │ │ │ │ │   └ sddk::transform                                         |        6.09 ms                             |      30                          |      182.76 ms                             | 
  │ │ │ │ │     ├ sddk::transform|init                                  |       10.86 μs                             |      30                          |      325.75 μs                             | 
  │ │ │ │ │     └ sddk::transform|local                                 |       11.67 μs                             |      35                          |      408.45 μs                             | 
  │ │ │ │ ├ sirius::Hamiltonian_k::apply_h_s                            |                        83.82 ms            |                 116              |                         9.72 s             | 
  │ │ │ │ │ ├ sirius::Local_operator::apply_h                           |                        49.86 ms            |                 116              |                         5.78 s             | 
  │ │ │ │ │ │ ├ sddk::matrix_storage::remap_forward                     |                         1.80 μs            |                 116              |                       208.38 μs            | 
  │ │ │ │ │ │ └ sddk::matrix_storage::remap_backward                    |                       556.53 ns            |                 116              |                        64.56 μs            | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |                         3.23 ms            |                 116              |                       375.00 ms            | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |                         4.58 ms            |                 116              |                       531.48 ms            | 
  │ │ │ │ │ └ sirius::Non_local_operator::apply                         |                        13.06 ms            |                 232              |                         3.03 s             | 
  │ │ │ │ ├ sddk::orthogonalize                                         |                        10.25 ms            |                 116              |                         1.19 s             | 
  │ │ │ │ │ ├ sddk::wf_inner                                            |                         1.60 ms            |                 217              |                       347.98 ms            | 
  │ │ │ │ │ │ ├ sddk::wf_inner|scale                                    |                        95.10 ns            |                 217              |                        20.64 μs            | 
  │ │ │ │ │ │ ├ sddk::wf_inner|pw                                       |                         1.44 ms            |                 217              |                       311.79 ms            | 
  │ │ │ │ │ │ └ sddk::wf_inner|scale_back                               |                       235.59 ns            |                 217              |                        51.12 μs            | 
  │ │ │ │ │ ├ sddk::orthogonalize|tmtrx                                 |                       528.75 μs            |                 116              |                        61.34 ms            | 
  │ │ │ │ │ ├ sddk::orthogonalize|transform                             |                         3.99 ms            |                 116              |                       462.34 ms            | 
  │ │ │ │ │ └ sddk::wf_trans                                            |                         3.14 ms            |                 101              |                       317.08 ms            | 
  │ │ │ │ │   └ sddk::wf_trans|pw                                       |                         1.05 ms            |                 303              |                       316.85 ms            | 
  │ │ │ │ ├ sirius::Band::set_subspace_mtrx                             |                         1.77 ms            |                 116              |                       205.37 ms            | 
  │ │ │ │ │ └ sddk::wf_inner                                            |                         1.71 ms            |                 116              |                       198.47 ms            | 
  │ │ │ │ │   ├ sddk::wf_inner|scale                                    |                        77.65 ns            |                 116              |                         9.01 μs            | 
  │ │ │ │ │   ├ sddk::wf_inner|pw                                       |                         1.54 ms            |                 116              |                       178.78 ms            | 
  │ │ │ │ │   └ sddk::wf_inner|scale_back                               |                       223.91 ns            |                 116              |                        25.97 μs            | 
  │ │ │ │ ├ Eigensolver_cuda|zheevdx                                    |                        29.90 ms            |                 116              |                         3.47 s             | 
  │ │ │ │ ├ sirius::residuals                                           |                         3.23 ms            |                 114              |                       368.59 ms            | 
  │ │ │ │ │ ├ sddk::wf_trans                                            |                         1.76 ms            |                 101              |                       178.26 ms            | 
  │ │ │ │ │ │ └ sddk::wf_trans|pw                                       |                       881.03 μs            |                 202              |                       177.97 ms            | 
  │ │ │ │ │ └ sirius::normalized_preconditioned_residuals               |                         1.68 ms            |                 101              |                       169.30 ms            | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|update_phi     |                         4.83 ms            |                  47              |                       226.79 ms            | 
  │ │ │ │   └ sddk::wf_trans                                            |                         2.82 ms            |                  79              |                       222.97 ms            | 
  │ │ │ │     └ sddk::wf_trans|pw                                       |                         2.01 ms            |                 111              |                       222.81 ms            | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      373.60 ns →      424.33 ns  (+13.58%) |      20   →      15    (-25.00%) |        7.47 μs →        6.37 μs  (-14.82%) | 
  │ │ │ ├ sirius::K_point_set::sync_band_energies                       |       22.12 μs                             |      20                          |      442.31 μs                             | 
  │ │ │ └ sirius::K_point_set::sync_band                                |                        61.22 μs            |                  15              |                       918.34 μs            | 
+ │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.49 ms →      998.25 μs  (-33.08%) |      20   →      15    (-25.00%) |       29.84 ms →       14.97 ms  (-49.81%) | 
  │ │ │ └ sirius::K_point_set::sync_band                                |                        13.41 μs            |                  15              |                       201.19 μs            | 
+ │ │ ├ sirius::Density::generate                                       |      574.15 ms →      572.03 ms   (-0.37%) |      20   →      15    (-25.00%) |       11.48 s  →        8.58 s   (-25.28%) | 
+ │ │ │ ├ sirius::Density::generate_valence                             |      431.01 ms →      382.99 ms  (-11.14%) |      20   →      15    (-25.00%) |        8.62 s  →        5.74 s   (-33.36%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        7.56 μs →        5.62 μs  (-25.63%) |      20   →      15    (-25.00%) |      151.12 μs →       84.29 μs  (-44.22%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.12 μs                             |      20                          |      142.34 μs                             | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       43.12 ms →       45.91 ms   (+6.46%) |      20   →      15    (-25.00%) |      862.46 ms →      688.64 ms  (-20.15%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.53 μs →        9.09 μs  (+20.65%) |      20   →      15    (-25.00%) |      150.64 μs →      136.31 μs   (-9.51%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.35 ms →        7.91 ms   (+7.53%) |      20   →      15    (-25.00%) |      147.08 ms →      118.61 ms  (-19.35%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       34.73 ms →       36.94 ms   (+6.36%) |      20   →      15    (-25.00%) |      694.66 ms →      554.15 ms  (-20.23%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      702.20 ns →      647.67 ns   (-7.77%) |      20   →      15    (-25.00%) |       14.04 μs →        9.72 μs  (-30.82%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      103.04 ms →      100.42 ms   (-2.55%) |      20   →      15    (-25.00%) |        2.06 s  →        1.51 s   (-26.91%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.31 ms →        2.16 ms   (-6.77%) |      20   →      15    (-25.00%) |       46.24 ms →       32.33 ms  (-30.08%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |      239.38 ms →      201.47 ms  (-15.84%) |      20   →      15    (-25.00%) |        4.79 s  →        3.02 s   (-36.88%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |      239.17 ms →      201.26 ms  (-15.85%) |      20   →      15    (-25.00%) |        4.78 s  →        3.02 s   (-36.89%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      115.01 ms →      157.40 ms  (+36.86%) |      20   →      15    (-25.00%) |        2.30 s  →        2.36 s    (+2.65%) | 
- │ │ │ │ └ sirius::symmetrize_function|fpw                             |      115.01 ms →      157.40 ms  (+36.86%) |      20   →      15    (-25.00%) |        2.30 s  →        2.36 s    (+2.64%) | 
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       30.12 ms →       77.73 ms (+158.06%) |      20   →      15    (-25.00%) |      602.39 ms →        1.17 s   (+93.54%) | 
+ │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       71.71 ms →       66.14 ms   (-7.77%) |      20   →      15    (-25.00%) |        1.43 s  →      992.03 ms  (-30.83%) | 
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.54 ms →       12.88 ms   (+2.71%) |      20   →      15    (-25.00%) |      250.73 ms →      193.15 ms  (-22.97%) | 
+ │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.52 ms →       23.57 ms   (+0.18%) |      20   →      15    (-25.00%) |      470.46 ms →      353.48 ms  (-24.87%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        4.60 ms →        8.06 ms  (+75.30%) |      20   →      15    (-25.00%) |       91.95 ms →      120.89 ms  (+31.48%) | 
  │ │ ├ sirius::inner                                                   |                         4.85 ms            |                 180              |                       872.76 ms            | 
+ │ │ ├ sirius::Density::mix                                            |      137.60 ms →       75.68 ms  (-45.00%) |      20   →      15    (-25.00%) |        2.75 s  →        1.14 s   (-58.75%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      745.43 μs →        1.03 ms  (+38.06%) |      20   →      15    (-25.00%) |       14.91 ms →       15.44 ms   (+3.54%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |        5.06 ms                             |     244                          |        1.23 s                              | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |        5.01 ms                             |     244                          |        1.22 s                              | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        5.01 ms                             |     244                          |        1.22 s                              | 
  │ │ │ ├ sirius::inner                                                 |                         4.60 ms            |                 169              |                       777.36 ms            | 
- │ │ │ └ sirius::Density::mixer_output                                 |        4.93 ms →        5.73 ms  (+16.37%) |      20   →      15    (-25.00%) |       98.56 ms →       86.02 ms  (-12.72%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        4.28 ms →        4.77 ms  (+11.46%) |      20   →      15    (-25.00%) |       85.57 ms →       71.53 ms  (-16.41%) | 
+ │ │ ├ sirius::Potential::generate                                     |      373.46 ms →      359.64 ms   (-3.70%) |      20   →      15    (-25.00%) |        7.47 s  →        5.39 s   (-27.78%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |       42.94 ms →       36.04 ms  (-16.07%) |      20   →      15    (-25.00%) |      858.87 ms →      540.67 ms  (-37.05%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       11.33 ms →        5.04 ms  (-55.51%) |      20   →      15    (-25.00%) |      226.52 ms →       75.59 ms  (-66.63%) | 
  │ │ │ │ ├ sirius::Periodic_function|inner                             |        6.10 ms                             |      20                          |      122.03 ms                             | 
  │ │ │ │ │ └ sirius::Periodic_function|inner_local                     |        4.83 ms                             |      20                          |       96.68 ms                             | 
  │ │ │ │ │   └ sirius::Smooth_periodic_function|inner_local            |        4.83 ms                             |      20                          |       96.66 ms                             | 
  │ │ │ │ └ sirius::inner                                               |                         5.65 ms            |                  15              |                        84.75 ms            | 
+ │ │ │ ├ sirius::Periodic_function::add                                |      784.37 μs →      720.72 μs   (-8.11%) |      40   →      30    (-25.00%) |       31.37 ms →       21.62 ms  (-31.09%) | 
+ │ │ │ ├ sirius::Potential::xc                                         |       55.55 ms →       47.24 ms  (-14.96%) |      20   →      15    (-25.00%) |        1.11 s  →      708.64 ms  (-36.22%) | 
+ │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       55.55 ms →       46.05 ms  (-17.10%) |      20   →      15    (-25.00%) |        1.11 s  →      690.81 ms  (-37.82%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |      647.75 μs                             |      40                          |       25.91 ms                             | 
  │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |        4.70 ms                             |      20                          |       94.10 ms                             | 
  │ │ │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                |                        19.57 ms            |                  30              |                       587.01 ms            | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.74 ms →        4.19 ms  (+12.23%) |      20   →      15    (-25.00%) |       74.75 ms →       62.92 ms  (-15.83%) | 
+ │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.25 ms →      267.75 ms   (-0.18%) |      20   →      15    (-25.00%) |        5.36 s  →        4.02 s   (-25.14%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      249.80 ns →      150.27 ns  (-39.85%) |      20   →      15    (-25.00%) |        5.00 μs →        2.25 μs  (-54.88%) | 
+ │ │ ├ sirius::Field4D::symmetrize                                     |       97.96 ms →       92.53 ms   (-5.54%) |      20   →      15    (-25.00%) |        1.96 s  →        1.39 s   (-29.16%) | 
+ │ │ │ └ sirius::symmetrize_function|fpw                               |       97.96 ms →       92.52 ms   (-5.55%) |      20   →      15    (-25.00%) |        1.96 s  →        1.39 s   (-29.16%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.21 ms →       13.31 ms   (+0.71%) |      20   →      15    (-25.00%) |      264.27 ms →      199.60 ms  (-24.47%) | 
+ │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       71.64 ms →       65.78 ms   (-8.18%) |      20   →      15    (-25.00%) |        1.43 s  →      986.63 ms  (-31.14%) | 
+ │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.48 ms →       12.81 ms   (+2.68%) |      20   →      15    (-25.00%) |      249.57 ms →      192.18 ms  (-22.99%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        4.32 ms →        4.56 ms   (+5.55%) |      20   →      15    (-25.00%) |       86.33 ms →       68.34 ms  (-20.84%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.80 ms                             |     140                          |      672.07 ms                             | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.75 ms                             |     140                          |      665.13 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.75 ms                             |     140                          |      665.00 ms                             | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.54 ms                             |      60                          |      272.23 ms                             | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.53 ms                             |      60                          |      271.84 ms                             | 
+ │ │ ├ sirius::Periodic_function::integrate                            |        4.53 ms →        4.60 ms   (+1.45%) |      20   →      15    (-25.00%) |       90.65 ms →       68.97 ms  (-23.91%) | 
- │ │ └ sirius::Density::get_magnetisation                              |       77.25 μs →       23.58 ms (+30421.44%) |      20   →      15    (-25.00%) |        1.54 ms →      353.67 ms (+22791.08%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |       72.06 μs →       23.57 ms (+32609.35%) |      20   →      15    (-25.00%) |        1.44 ms →      353.55 ms (+24432.01%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.12 ms →        5.25 ms   (+2.54%) |       2   →       2              |       10.23 ms →       10.49 ms   (+2.54%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.72 ms                             |       6                          |       28.34 ms                             | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.72 ms                             |       6                          |       28.30 ms                             | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.72 ms                             |       6                          |       28.30 ms                             | 
  │ ├ sirius::Smooth_periodic_function|inner                            |        4.55 ms                             |       3                          |       13.66 ms                             | 
  │ │ └ sirius::Smooth_periodic_function|inner_local                    |        4.55 ms                             |       3                          |       13.65 ms                             | 
  │ └ sirius::inner                                                     |                         4.84 ms            |                   9              |                        43.57 ms            | 
  ├ sirius::Periodic_function|inner                                     |        4.83 ms                             |       2                          |        9.66 ms                             | 
  │ └ sirius::Periodic_function|inner_local                             |        4.82 ms                             |       2                          |        9.65 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.82 ms                             |       2                          |        9.65 ms                             | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.63 ms                             |       1                          |        4.63 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.62 ms                             |       1                          |        4.62 ms                             | 
  ├ sirius::inner                                                       |                         5.08 ms            |                   3              |                        15.25 ms            | 
+ └ sirius::finalize                                                    |      923.47 ms →      179.65 ms  (-80.55%) |       1   →       1              |      923.47 ms →      179.65 ms  (-80.55%) | 
  ====================================================================================================================================================================================================
```
