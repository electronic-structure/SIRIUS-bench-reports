# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs 6f4917d65584ba2b52ea522b0bd003886a7daddd
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      175.45 s  →      142.52 s   (-18.77%) |       1   →       1              |      175.45 s  →      142.52 s   (-18.77%) | 
  ├ sirius::initialize                                                  |        2.73 s  →        2.70 s    (-1.15%) |       1   →       1              |        2.73 s  →        2.70 s    (-1.15%) | 
+ ├ sirius::Simulation_context::initialize                              |        3.85 s  →        2.95 s   (-23.36%) |       1   →       1              |        3.85 s  →        2.95 s   (-23.36%) | 
- │ ├ sirius::Simulation_context::init_comm                             |      450.23 μs →       19.07 ms (+4135.46%) |       1   →       1              |      450.23 μs →       19.07 ms (+4135.46%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |        1.15 s  →      174.12 ms  (-84.92%) |       1   →       1              |        1.15 s  →      174.12 ms  (-84.92%) | 
+ │ │ ├ sirius::Atom_type::init                                         |      569.30 ms →       75.34 ms  (-86.77%) |       2   →       2              |        1.14 s  →      150.68 ms  (-86.77%) | 
- │ │ └ sirius::Unit_cell::update                                       |       16.07 ms →       23.27 ms  (+44.77%) |       1   →       1              |       16.07 ms →       23.27 ms  (+44.77%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        5.38 ms →        5.61 ms   (+4.38%) |       1   →       1              |        5.38 ms →        5.61 ms   (+4.38%) | 
- │ │   └ sirius::Unit_cell::get_symmetry                               |       10.65 ms →       17.61 ms  (+65.25%) |       1   →       1              |       10.65 ms →       17.61 ms  (+65.25%) | 
- │ │     └ sirius::Unit_cell_symmetry                                  |       10.63 ms →       17.58 ms  (+65.41%) |       1   →       1              |       10.63 ms →       17.58 ms  (+65.41%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        5.20 ms →        5.33 ms   (+2.55%) |       1   →       1              |        5.20 ms →        5.33 ms   (+2.55%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.31 ms →        2.34 ms   (+1.41%) |       1   →       1              |        2.31 ms →        2.34 ms   (+1.41%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       99.96 μs →      101.37 μs   (+1.42%) |       1   →       1              |       99.96 μs →      101.37 μs   (+1.42%) | 
  │ └ sirius::Simulation_context::update                                |        2.66 s  →        2.72 s    (+2.33%) |       1   →       1              |        2.66 s  →        2.72 s    (+2.33%) | 
  │   ├ sirius::Unit_cell::update                                       |       11.78 ms →       12.03 ms   (+2.10%) |       1   →       1              |       11.78 ms →       12.03 ms   (+2.10%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.45 ms →        4.46 ms   (+0.40%) |       1   →       1              |        4.45 ms →        4.46 ms   (+0.40%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        7.30 ms →        7.53 ms   (+3.15%) |       1   →       1              |        7.30 ms →        7.53 ms   (+3.15%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        7.28 ms →        7.51 ms   (+3.12%) |       1   →       1              |        7.28 ms →        7.51 ms   (+3.12%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        4.78 ms →        5.01 ms   (+4.72%) |       1   →       1              |        4.78 ms →        5.01 ms   (+4.72%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.33 ms   (-0.17%) |       1   →       1              |        2.33 ms →        2.33 ms   (-0.17%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       98.42 μs →       99.54 μs   (+1.13%) |       1   →       1              |       98.42 μs →       99.54 μs   (+1.13%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       63.40 ms →       65.03 ms   (+2.57%) |       2   →       2              |      126.80 ms →      130.06 ms   (+2.57%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.16 ms →        5.14 ms   (-0.33%) |       2   →       2              |       10.32 ms →       10.29 ms   (-0.33%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.50 ms →        4.49 ms   (-0.15%) |       1   →       1              |        4.50 ms →        4.49 ms   (-0.15%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.81 ms →       21.74 ms   (-0.31%) |       2   →       2              |       43.62 ms →       43.48 ms   (-0.31%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.75 ms →       14.76 ms   (+0.05%) |       2   →       2              |       29.50 ms →       29.52 ms   (+0.05%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.55 ms →       19.79 ms   (+1.24%) |       4   →       4              |       78.20 ms →       79.17 ms   (+1.24%) | 
  │   ├ sddk::Gvec::init                                                |      176.59 ms →      175.32 ms   (-0.72%) |       2   →       2              |      353.19 ms →      350.63 ms   (-0.72%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      134.08 ms →      132.67 ms   (-1.05%) |       2   →       2              |      268.16 ms →      265.34 ms   (-1.05%) | 
  │   ├ sddk::Gvec_shells                                               |      166.47 ms →      171.41 ms   (+2.97%) |       1   →       1              |      166.47 ms →      171.41 ms   (+2.97%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.33 ms →        1.31 ms   (-1.33%) |       1   →       1              |        1.33 ms →        1.31 ms   (-1.33%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      295.28 ms →      290.91 ms   (-1.48%) |       2   →       2              |      590.55 ms →      581.81 ms   (-1.48%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       35.91 ms →       36.47 ms   (+1.55%) |       1   →       1              |       35.91 ms →       36.47 ms   (+1.55%) | 
- │ ├ sirius::K_point::K_point                                          |        2.85 μs →        6.64 μs (+133.27%) |       4   →       4              |       11.39 μs →       26.56 μs (+133.27%) | 
  │ └ sirius::K_point_set::initialize                                   |       35.82 ms →       36.33 ms   (+1.42%) |       1   →       1              |       35.82 ms →       36.33 ms   (+1.42%) | 
  │   └ sirius::K_point::initialize                                     |       35.73 ms →       36.24 ms   (+1.42%) |       1   →       1              |       35.73 ms →       36.24 ms   (+1.42%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       18.35 ms →       18.56 ms   (+1.15%) |       1   →       1              |       18.35 ms →       18.56 ms   (+1.15%) | 
  │     │ └ sddk::Gvec::init                                            |        8.20 ms →        8.32 ms   (+1.51%) |       1   →       1              |        8.20 ms →        8.32 ms   (+1.51%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        6.82 μs                             |       1                          |        6.82 μs                             | 
  │     └ sirius::K_point::update                                       |       12.44 ms →       12.83 ms   (+3.14%) |       1   →       1              |       12.44 ms →       12.83 ms   (+3.14%) | 
  │       └ sirius::Beta_projectors                                     |        6.14 ms →        6.51 ms   (+6.13%) |       1   →       1              |        6.14 ms →        6.51 ms   (+6.13%) | 
- │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.50 ms →        3.90 ms  (+11.42%) |       1   →       1              |        3.50 ms →        3.90 ms  (+11.42%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.28 ms                             |       2                          |       10.57 ms                             | 
  ├ sirius::Potential                                                   |      160.08 ms →      157.03 ms   (-1.90%) |       1   →       1              |      160.08 ms →      157.03 ms   (-1.90%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.98 ms                             |       6                          |       35.90 ms                             | 
  │ └ sirius::Potential::update                                         |      123.44 ms →      127.10 ms   (+2.96%) |       1   →       1              |      123.44 ms →      127.10 ms   (+2.96%) | 
  │   └ sirius::Potential::generate_local_potential                     |      122.61 ms →      126.26 ms   (+2.98%) |       1   →       1              |      122.61 ms →      126.26 ms   (+2.98%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      113.37 ms →      115.67 ms   (+2.03%) |       1   →       1              |      113.37 ms →      115.67 ms   (+2.03%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        8.69 ms →        5.42 ms  (-37.63%) |       1   →       1              |        8.69 ms →        5.42 ms  (-37.63%) | 
  ├ sirius::Density                                                     |      129.68 ms →      138.09 ms   (+6.49%) |       1   →       1              |      129.68 ms →      138.09 ms   (+6.49%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.23 ms                             |       2                          |       10.47 ms                             | 
  │ └ sirius::Density::update                                           |      118.94 ms →      127.24 ms   (+6.98%) |       1   →       1              |      118.94 ms →      127.24 ms   (+6.98%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      118.48 ms →      126.82 ms   (+7.04%) |       1   →       1              |      118.48 ms →      126.82 ms   (+7.04%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      112.91 ms →      119.98 ms   (+6.25%) |       1   →       1              |      112.91 ms →      119.98 ms   (+6.25%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        5.11 ms →        5.15 ms   (+0.81%) |       1   →       1              |        5.11 ms →        5.15 ms   (+0.81%) | 
  ├ sirius::Density::initial_density                                    |      163.57 ms →      174.17 ms   (+6.48%) |       1   →       1              |      163.57 ms →      174.17 ms   (+6.48%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      111.21 ms →      118.83 ms   (+6.85%) |       1   →       1              |      111.21 ms →      118.83 ms   (+6.85%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.01 ms →        5.66 ms  (+12.89%) |       2   →       2              |       10.03 ms →       11.32 ms  (+12.89%) | 
- │ └ sirius::Periodic_function::integrate                              |        9.73 ms →       11.64 ms  (+19.63%) |       1   →       1              |        9.73 ms →       11.64 ms  (+19.63%) | 
  ├ sirius::Potential::generate                                         |      692.28 ms →      687.44 ms   (-0.70%) |       1   →       1              |      692.28 ms →      687.44 ms   (-0.70%) | 
- │ ├ sirius::Potential::poisson                                        |      126.81 ms →      139.63 ms  (+10.11%) |       1   →       1              |      126.81 ms →      139.63 ms  (+10.11%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        6.11 ms →        5.55 ms   (-9.11%) |       1   →       1              |        6.11 ms →        5.55 ms   (-9.11%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.59 ms                             |       1                          |       10.59 ms                             | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |       10.55 ms                             |       1                          |       10.55 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |       10.55 ms                             |       1                          |       10.55 ms                             | 
  │ │ └ sirius::inner                                                   |                        10.72 ms            |                   1              |                        10.72 ms            | 
+ │ ├ sirius::Periodic_function::add                                    |      553.35 μs →      452.88 μs  (-18.16%) |       2   →       2              |        1.11 ms →      905.76 μs  (-18.16%) | 
+ │ ├ sirius::Potential::xc                                             |       58.45 ms →       38.99 ms  (-33.29%) |       1   →       1              |       58.45 ms →       38.99 ms  (-33.29%) | 
+ │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       58.45 ms →       36.62 ms  (-37.34%) |       1   →       1              |       58.45 ms →       36.62 ms  (-37.34%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.75 ms                             |       2                          |       11.49 ms                             | 
  │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        5.14 ms                             |       1                          |        5.14 ms                             | 
  │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                    |                        12.12 ms            |                   2              |                        24.24 ms            | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.83 ms →        4.97 ms  (-14.78%) |       1   →       1              |        5.83 ms →        4.97 ms  (-14.78%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       93.49 ms →       93.61 ms   (+0.12%) |       1   →       1              |       93.49 ms →       93.61 ms   (+0.12%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      405.20 ms →      405.23 ms   (+0.01%) |       1   →       1              |      405.20 ms →      405.23 ms   (+0.01%) | 
- ├ sirius::Hamiltonian0                                                |        8.46 ms →       11.98 ms  (+41.67%) |       1   →       1              |        8.46 ms →       11.98 ms  (+41.67%) | 
  │ ├ sirius::Local_operator                                            |        8.10 ms →        8.13 ms   (+0.37%) |       1   →       1              |        8.10 ms →        8.13 ms   (+0.37%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.81 ms                             |       1                          |        4.81 ms                             | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.37 ms →        2.36 ms   (-0.41%) |       1   →       1              |        2.37 ms →        2.36 ms   (-0.41%) | 
  │ ├ sirius::Non_local_operator                                        |       63.00 μs →       62.51 μs   (-0.79%) |       2   →       2              |      126.01 μs →      125.01 μs   (-0.79%) | 
- │ ├ sirius::D_operator::initialize                                    |      102.23 μs →        1.29 ms (+1158.82%) |       1   →       1              |      102.23 μs →        1.29 ms (+1158.82%) | 
- │ └ sirius::Q_operator::initialize                                    |       77.10 μs →        2.38 ms (+2990.36%) |       1   →       1              |       77.10 μs →        2.38 ms (+2990.36%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.88 s  →        1.87 s    (-0.91%) |       1   →       1              |        1.88 s  →        1.87 s    (-0.91%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.68 ms →       18.68 ms   (+0.01%) |       1   →       1              |       18.68 ms →       18.68 ms   (+0.01%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      177.97 μs →      170.10 μs   (-4.42%) |       1   →       1              |      177.97 μs →      170.10 μs   (-4.42%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       18.50 ms →       18.51 ms   (+0.04%) |       1   →       1              |       18.50 ms →       18.51 ms   (+0.04%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.87 s  →        1.85 s    (-1.01%) |       1   →       1              |        1.87 s  →        1.85 s    (-1.01%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      130.73 ms                             |       4                          |      522.93 ms                             | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       52.59 ms →       52.04 ms   (-1.05%) |       1   →       1              |       52.59 ms →       52.04 ms   (-1.05%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       20.98 ms →       20.98 ms   (+0.01%) |       1   →       1              |       20.98 ms →       20.98 ms   (+0.01%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      636.37 ms →      634.59 ms   (-0.28%) |       1   →       1              |      636.37 ms →      634.59 ms   (-0.28%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      297.65 ms →      297.76 ms   (+0.04%) |       1   →       1              |      297.65 ms →      297.76 ms   (+0.04%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.56 μs →        3.73 μs   (+4.77%) |       1   →       1              |        3.56 μs →        3.73 μs   (+4.77%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.58 μs                             |       1                          |        2.58 μs                             | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      441.00 ns                             |       1                          |      441.00 ns                             | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      536.00 ns →      584.00 ns   (+8.96%) |       1   →       1              |      536.00 ns →      584.00 ns   (+8.96%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.23 ms →        9.22 ms   (-0.03%) |       1   →       1              |        9.23 ms →        9.22 ms   (-0.03%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      121.05 ms →      120.67 ms   (-0.31%) |       1   →       1              |      121.05 ms →      120.67 ms   (-0.31%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      104.20 ms →      103.44 ms   (-0.72%) |       2   →       2              |      208.40 ms →      206.89 ms   (-0.72%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       38.64 ms →       40.08 ms   (+3.74%) |       2   →       2              |       77.28 ms →       80.17 ms   (+3.74%) | 
  │ │ │ ├ sddk::inner                                                   |       38.05 ms                             |       2                          |       76.11 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       28.51 μs                             |       2                          |       57.02 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        39.52 ms            |                   2              |                        79.04 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                       199.50 ns            |                   2              |                       399.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        39.04 ms            |                   2              |                        78.08 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                       428.00 ns            |                   2              |                       856.00 ns            | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       57.13 ms →       56.84 ms   (-0.50%) |       1   →       1              |       57.13 ms →       56.84 ms   (-0.50%) | 
  │ │ ├ sddk::transform                                                 |       31.54 ms                             |       1                          |       31.54 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       11.28 μs                             |       1                          |       11.28 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       11.18 μs                             |       1                          |       11.18 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                        30.73 ms            |                   1              |                        30.73 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                        30.73 ms            |                   1              |                        30.73 ms            | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      479.00 ns →      670.00 ns  (+39.87%) |       1   →       1              |      479.00 ns →      670.00 ns  (+39.87%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      164.42 s  →      132.78 s   (-19.24%) |       1   →       1              |      164.42 s  →      132.78 s   (-19.24%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.92 ms                             |      19                          |      112.43 ms                             | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.69 s                              |      35                          |      164.03 s                              | 
  │ │ ├ sirius::Hamiltonian0                                            |        4.55 ms                             |      35                          |      159.42 ms                             | 
  │ │ │ ├ sirius::Local_operator                                        |        4.18 ms                             |      35                          |      146.32 ms                             | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |        1.01 ms                             |      35                          |       35.29 ms                             | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.28 ms                             |      35                          |       79.93 ms                             | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.15 μs                             |      70                          |        4.49 ms                             | 
  │ │ │ ├ sirius::D_operator::initialize                                |      100.30 μs                             |      35                          |        3.51 ms                             | 
  │ │ │ └ sirius::Q_operator::initialize                                |       75.91 μs                             |      35                          |        2.66 ms                             | 
  │ │ ├ sirius::Band::solve                                             |        2.60 s                              |      35                          |       91.03 s                              | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      178.69 μs                             |      35                          |        6.25 ms                             | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      172.03 μs                             |      35                          |        6.02 ms                             | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.97 μs                             |      35                          |      173.98 μs                             | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.52 s                              |      35                          |       88.14 s                              | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |      102.62 ms                             |      35                          |        3.59 s                              | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        8.79 ms                             |     210                          |        1.85 s                              | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        6.02 ms                             |      35                          |      210.69 ms                             | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      350.34 μs                             |      35                          |       12.26 ms                             | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.32 ms                             |      70                          |      162.08 ms                             | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.37 s                              |      35                          |       83.08 s                              | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      112.26 ms                             |     340                          |       38.17 s                              | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       43.85 ms                             |     340                          |       14.91 s                              | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.01 μs                             |     340                          |      682.75 μs                             | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.65 μs                             |     340                          |      562.08 μs                             | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      309.50 ns                             |     340                          |      105.23 μs                             | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      366.76 ns                             |     340                          |      124.70 μs                             | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.38 ms                             |     340                          |        2.51 s                              | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       20.19 ms                             |     340                          |        6.86 s                              | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       20.42 ms                             |     680                          |       13.88 s                              | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       36.78 ms                             |     340                          |       12.50 s                              | 
  │ │ │ │   │ ├ sddk::inner                                             |        4.68 ms                             |     645                          |        3.02 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       20.36 μs                             |     645                          |       13.13 ms                             | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |        5.91 ms                             |     340                          |        2.01 s                              | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        8.67 ms                             |     340                          |        2.95 s                              | 
  │ │ │ │   │ └ sddk::transform                                         |       14.84 ms                             |     305                          |        4.53 s                              | 
  │ │ │ │   │   ├ sddk::transform|init                                  |       17.07 μs                             |     305                          |        5.21 ms                             | 
  │ │ │ │   │   └ sddk::transform|local                                 |       36.47 μs                             |     915                          |       33.37 ms                             | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        9.91 ms                             |     340                          |        3.37 s                              | 
  │ │ │ │   │ └ sddk::inner                                             |        9.00 ms                             |     340                          |        3.06 s                              | 
  │ │ │ │   │   └ sddk::inner|local                                     |       27.53 μs                             |     340                          |        9.36 ms                             | 
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       65.44 ms                             |     340                          |       22.25 s                              | 
  │ │ │ │   ├ sirius::residuals                                         |       14.46 ms                             |     330                          |        4.77 s                              | 
  │ │ │ │   │ ├ sddk::transform                                         |       13.42 ms                             |     316                          |        4.24 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       13.87 μs                             |     316                          |        4.38 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       38.45 μs                             |     632                          |       24.30 ms                             | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.45 ms                             |     316                          |      459.30 ms                             | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       54.12 ms                             |      37                          |        2.00 s                              | 
  │ │ │ │     └ sddk::transform                                         |       51.14 ms                             |      39                          |        1.99 s                              | 
  │ │ │ │       ├ sddk::transform|init                                  |       11.52 μs                             |      39                          |      449.25 μs                             | 
  │ │ │ │       └ sddk::transform|local                                 |       13.77 μs                             |      41                          |      564.67 μs                             | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      545.51 ns                             |      35                          |       19.09 μs                             | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       31.96 μs                             |      35                          |        1.12 ms                             | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      600.86 μs                             |      35                          |       21.03 ms                             | 
  │ │ ├ sirius::Density::generate                                       |      770.97 ms                             |      35                          |       26.98 s                              | 
  │ │ │ ├ sirius::Density::generate_valence                             |      402.27 ms                             |      35                          |       14.08 s                              | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.03 μs                             |      35                          |      281.18 μs                             | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.20 μs                             |      35                          |      251.96 μs                             | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       99.94 ms                             |      35                          |        3.50 s                              | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.55 μs                             |      35                          |      264.27 μs                             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.12 ms                             |      35                          |      249.17 ms                             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       90.94 ms                             |      35                          |        3.18 s                              | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      563.43 ns                             |      35                          |       19.72 μs                             | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      162.99 ms                             |      35                          |        5.70 s                              | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms                             |      35                          |       57.39 ms                             | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.36 ms                             |      35                          |        3.09 s                              | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.13 ms                             |      35                          |        3.08 s                              | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      275.56 ms                             |      35                          |        9.64 s                              | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      275.56 ms                             |      35                          |        9.64 s                              | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.95 ms                             |      35                          |      873.30 ms                             | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      226.17 ms                             |      35                          |        7.92 s                              | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       23.25 ms                             |      35                          |      813.66 ms                             | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       80.98 ms                             |      35                          |        2.83 s                              | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        8.60 ms                             |      35                          |      301.13 ms                             | 
  │ │ ├ sirius::Density::mix                                            |      230.49 ms                             |      35                          |        8.07 s                              | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      987.93 μs                             |      35                          |       34.58 ms                             | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.81 ms                             |     469                          |        5.07 s                              | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.45 ms                             |     469                          |        4.90 s                              | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.45 ms                             |     469                          |        4.90 s                              | 
  │ │ │ └ sirius::Density::mixer_output                                 |        7.23 ms                             |      35                          |      253.00 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        6.38 ms                             |      35                          |      223.42 ms                             | 
  │ │ ├ sirius::Potential::generate                                     |      679.84 ms                             |      35                          |       23.79 s                              | 
  │ │ │ ├ sirius::Potential::poisson                                    |      126.17 ms                             |      35                          |        4.42 s                              | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        5.69 ms                             |      35                          |      199.24 ms                             | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.45 ms                             |      35                          |      365.61 ms                             | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.12 ms                             |      35                          |      354.22 ms                             | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.12 ms                             |      35                          |      354.20 ms                             | 
  │ │ │ ├ sirius::Periodic_function::add                                |      548.36 μs                             |      70                          |       38.39 ms                             | 
  │ │ │ ├ sirius::Potential::xc                                         |       54.02 ms                             |      35                          |        1.89 s                              | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       54.02 ms                             |      35                          |        1.89 s                              | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.04 ms                             |      70                          |      212.57 ms                             | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.40 ms                             |      35                          |      188.83 ms                             | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.42 ms                             |      35                          |      224.69 ms                             | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.91 ms                             |      35                          |        3.18 s                              | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      399.92 ms                             |      35                          |       14.00 s                              | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      278.92 ms                             |      35                          |        9.76 s                              | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      278.92 ms                             |      35                          |        9.76 s                              | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.50 ms                             |      35                          |      962.39 ms                             | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      223.73 ms                             |      35                          |        7.83 s                              | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.85 ms                             |      35                          |      834.90 ms                             | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.40 ms                             |      35                          |      189.14 ms                             | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.38 ms                             |     245                          |        2.54 s                              | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.97 ms                             |     245                          |        2.44 s                              | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.97 ms                             |     245                          |        2.44 s                              | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.61 ms                             |     105                          |        1.11 s                              | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.28 ms                             |     105                          |        1.08 s                              | 
  │ │ ├ sirius::Periodic_function::integrate                            |        9.96 ms                             |      35                          |      348.73 ms                             | 
  │ │ └ sirius::Density::get_magnetisation                              |      121.74 μs                             |      35                          |        4.26 ms                             | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |      116.81 μs                             |      35                          |        4.09 ms                             | 
  │ ├ sirius::Density                                                   |                       138.25 ms            |                   1              |                       138.25 ms            | 
  │ │ └ sirius::Density::update                                         |                       127.50 ms            |                   1              |                       127.50 ms            | 
  │ │   └ sirius::Density::generate_pseudo_core_charge_density          |                       127.07 ms            |                   1              |                       127.07 ms            | 
  │ │     ├ sirius::Simulation_context::make_periodic_function          |                       119.99 ms            |                   1              |                       119.99 ms            | 
  │ │     └ sirius::Smooth_periodic_function::fft_transform             |                         5.23 ms            |                   1              |                         5.23 ms            | 
  │ ├ sirius::Hamiltonian0                                              |                         7.97 ms            |                  29              |                       231.27 ms            | 
  │ │ ├ sirius::Local_operator                                          |                         4.10 ms            |                  29              |                       118.82 ms            | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |                         2.24 ms            |                  29              |                        65.05 ms            | 
  │ │ ├ sirius::Non_local_operator                                      |                        64.56 μs            |                  58              |                         3.74 ms            | 
  │ │ ├ sirius::D_operator::initialize                                  |                         1.26 ms            |                  29              |                        36.41 ms            | 
  │ │ └ sirius::Q_operator::initialize                                  |                         2.43 ms            |                  29              |                        70.38 ms            | 
  │ ├ sirius::Band::solve                                               |                         2.54 s             |                  29              |                        73.68 s             | 
  │ │ ├ sirius::Hamiltonian_k                                           |                       174.34 μs            |                  29              |                         5.06 ms            | 
  │ │ │ ├ sirius::Local_operator::prepare_k                             |                       164.72 μs            |                  29              |                         4.78 ms            | 
  │ │ │ └ sirius::Beta_projectors_base::prepare                         |                         4.95 μs            |                  29              |                       143.50 μs            | 
  │ │ ├ sirius::Band::diag_pseudo_potential_davidson                    |                         2.30 s             |                  29              |                        66.81 s             | 
  │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                           |                         5.88 ms            |                  29              |                       170.38 ms            | 
  │ │ │ ├ sirius::Hamiltonian_k::apply_h_s                              |                       101.36 ms            |                 370              |                        37.50 s             | 
  │ │ │ │ ├ sirius::Local_operator::apply_h                             |                        38.65 ms            |                 370              |                        14.30 s             | 
  │ │ │ │ │ ├ sddk::matrix_storage::remap_forward                       |                         1.66 μs            |                 370              |                       614.69 μs            | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_backward                      |                       510.24 ns            |                 370              |                       188.79 μs            | 
  │ │ │ │ ├ sirius::Beta_projectors_base::generate                      |                         7.33 ms            |                 370              |                         2.71 s             | 
  │ │ │ │ ├ sirius::Beta_projectors_base::inner                         |                        18.20 ms            |                 370              |                         6.73 s             | 
  │ │ │ │ └ sirius::Non_local_operator::apply                           |                        18.58 ms            |                 740              |                        13.75 s             | 
  │ │ │ ├ sddk::orthogonalize                                           |                        29.91 ms            |                 370              |                        11.07 s             | 
  │ │ │ │ ├ sddk::wf_inner                                              |                         4.65 ms            |                 711              |                         3.31 s             | 
  │ │ │ │ │ ├ sddk::wf_inner|scale                                      |                       128.00 ns            |                 711              |                        91.00 μs            | 
  │ │ │ │ │ ├ sddk::wf_inner|pw                                         |                         3.54 ms            |                 711              |                         2.52 s             | 
  │ │ │ │ │ └ sddk::wf_inner|scale_back                                 |                       228.69 ns            |                 711              |                       162.60 μs            | 
  │ │ │ │ ├ sddk::orthogonalize|tmtrx                                   |                         4.68 ms            |                 370              |                         1.73 s             | 
  │ │ │ │ ├ sddk::orthogonalize|transform                               |                         7.28 ms            |                 370              |                         2.70 s             | 
  │ │ │ │ └ sddk::wf_trans                                              |                         9.77 ms            |                 341              |                         3.33 s             | 
  │ │ │ │   └ sddk::wf_trans|pw                                         |                         3.26 ms            |                1.02 K            |                         3.33 s             | 
  │ │ │ ├ sirius::Band::set_subspace_mtrx                               |                         7.76 ms            |                 370              |                         2.87 s             | 
  │ │ │ │ └ sddk::wf_inner                                              |                         7.34 ms            |                 370              |                         2.71 s             | 
  │ │ │ │   ├ sddk::wf_inner|scale                                      |                       120.80 ns            |                 370              |                        44.70 μs            | 
  │ │ │ │   ├ sddk::wf_inner|pw                                         |                         6.23 ms            |                 370              |                         2.30 s             | 
  │ │ │ │   └ sddk::wf_inner|scale_back                                 |                       216.73 ns            |                 370              |                        80.19 μs            | 
  │ │ │ ├ Eigensolver_cuda|zheevdx                                      |                        12.29 ms            |                 370              |                         4.55 s             | 
  │ │ │ ├ sirius::residuals                                             |                         7.48 ms            |                 358              |                         2.68 s             | 
  │ │ │ │ ├ sddk::wf_trans                                              |                         6.31 ms            |                 341              |                         2.15 s             | 
  │ │ │ │ │ └ sddk::wf_trans|pw                                         |                         3.15 ms            |                 682              |                         2.15 s             | 
  │ │ │ │ └ sirius::normalized_preconditioned_residuals                 |                         1.17 ms            |                 341              |                       399.95 ms            | 
  │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|update_phi       |                        40.05 ms            |                 108              |                         4.33 s             | 
  │ │ │   └ sddk::wf_trans                                              |                        22.87 ms            |                 187              |                         4.28 s             | 
  │ │ │     └ sddk::wf_trans|pw                                         |                        16.08 ms            |                 266              |                         4.28 s             | 
  │ │ ├ sirius::Beta_projectors_base::dismiss                           |                       387.38 ns            |                  29              |                        11.23 μs            | 
  │ │ └ sirius::K_point_set::sync_band                                  |                       158.61 μs            |                  29              |                         4.60 ms            | 
  │ ├ sirius::K_point_set::find_band_occupancies                        |                         2.68 ms            |                  29              |                        77.67 ms            | 
  │ │ └ sirius::K_point_set::sync_band                                  |                        37.97 μs            |                  29              |                         1.10 ms            | 
  │ ├ sirius::Density::generate                                         |                       755.82 ms            |                  29              |                        21.92 s             | 
  │ │ ├ sirius::Density::generate_valence                               |                       405.60 ms            |                  29              |                        11.76 s             | 
  │ │ │ ├ sddk::matrix_storage::remap_forward                           |                         2.91 μs            |                  29              |                        84.29 μs            | 
  │ │ │ ├ sirius::Density::add_k_point_contribution_dm                  |                       100.16 ms            |                  29              |                         2.90 s             | 
  │ │ │ │ ├ sirius::Beta_projectors_base::prepare                       |                         8.72 μs            |                  29              |                       252.77 μs            | 
  │ │ │ │ ├ sirius::Beta_projectors_base::generate                      |                         7.12 ms            |                  29              |                       206.50 ms            | 
  │ │ │ │ ├ sirius::Beta_projectors_base::inner                         |                        91.14 ms            |                  29              |                         2.64 s             | 
  │ │ │ │ └ sirius::Beta_projectors_base::dismiss                       |                       548.83 ns            |                  29              |                        15.92 μs            | 
  │ │ │ ├ sirius::Density::add_k_point_contribution_rg                  |                       164.03 ms            |                  29              |                         4.76 s             | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |                         1.69 ms            |                  29              |                        49.11 ms            | 
  │ │ │ └ sirius::Density::augment                                      |                        88.37 ms            |                  29              |                         2.56 s             | 
  │ │ │   └ sirius::Density::generate_rho_aug                           |                        88.14 ms            |                  29              |                         2.56 s             | 
  │ │ ├ sirius::Field4D::symmetrize                                     |                       256.54 ms            |                  29              |                         7.44 s             | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |                       256.54 ms            |                  29              |                         7.44 s             | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |                        25.19 ms            |                  29              |                       730.43 ms            | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |                       206.55 ms            |                  29              |                         5.99 s             | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |                        23.65 ms            |                  29              |                       685.81 ms            | 
  │ │ ├ sirius::Density::symmetrize_density_matrix                      |                        80.67 ms            |                  29              |                         2.34 s             | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |                         9.35 ms            |                  29              |                       271.12 ms            | 
  │ ├ sirius::inner                                                     |                        10.38 ms            |                 357              |                         3.70 s             | 
  │ ├ sirius::Density::mix                                              |                       165.30 ms            |                  29              |                         4.79 s             | 
  │ │ ├ sirius::Density::mixer_input                                    |                         1.08 ms            |                  29              |                        31.30 ms            | 
  │ │ ├ sirius::inner                                                   |                        10.73 ms            |                 379              |                         4.07 s             | 
  │ │ └ sirius::Density::mixer_output                                   |                         6.55 ms            |                  29              |                       189.94 ms            | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |                         5.42 ms            |                  29              |                       157.18 ms            | 
  │ ├ sirius::Potential::generate                                       |                       676.03 ms            |                  29              |                        19.60 s             | 
  │ │ ├ sirius::Potential::poisson                                      |                       139.31 ms            |                  29              |                         4.04 s             | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |                         5.35 ms            |                  29              |                       155.16 ms            | 
  │ │ │ └ sirius::inner                                                 |                        10.75 ms            |                  29              |                       311.70 ms            | 
  │ │ ├ sirius::Periodic_function::add                                  |                       454.15 μs            |                  58              |                        26.34 ms            | 
  │ │ ├ sirius::Potential::xc                                           |                        34.39 ms            |                  29              |                       997.42 ms            | 
  │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                          |                        32.04 ms            |                  29              |                       929.04 ms            | 
  │ │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                  |                        11.82 ms            |                  58              |                       685.49 ms            | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |                         5.14 ms            |                  29              |                       149.15 ms            | 
  │ │ ├ sirius::Potential::generate_D_operator_matrix                   |                        90.97 ms            |                  29              |                         2.64 s             | 
  │ │ └ sirius::Potential::generate_PAW_effective_potential             |                       401.34 ms            |                  29              |                        11.64 s             | 
  │ ├ sirius::Field4D::symmetrize                                       |                       253.96 ms            |                  29              |                         7.36 s             | 
  │ │ └ sirius::symmetrize_function|fpw                                 |                       253.96 ms            |                  29              |                         7.36 s             | 
  │ │   ├ sddk::Gvec_shells::remap_forward                              |                        24.21 ms            |                  29              |                       702.15 ms            | 
  │ │   ├ sirius::symmetrize_function|fpw|local                         |                       205.14 ms            |                  29              |                         5.95 s             | 
  │ │   └ sddk::Gvec_shells::remap_backward                             |                        23.47 ms            |                  29              |                       680.68 ms            | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |                         5.68 ms            |                  29              |                       164.69 ms            | 
  │ ├ sirius::Periodic_function::integrate                              |                        10.13 ms            |                  29              |                       293.82 ms            | 
  │ ├ sirius::Density::get_magnetisation                                |                        13.67 ms            |                  29              |                       396.56 ms            | 
  │ │ └ sirius::Density::compute_atomic_mag_mom                         |                        13.67 ms            |                  29              |                       396.40 ms            | 
+ │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        7.42 ms →        4.82 ms  (-35.01%) |       2   →       2              |       14.84 ms →        9.65 ms  (-35.01%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.10 ms                             |       6                          |       60.60 ms                             | 
  │ │ └ sirius::Periodic_function|inner_local                           |        9.81 ms                             |       6                          |       58.87 ms                             | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        9.81 ms                             |       6                          |       58.87 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.52 ms                             |       3                          |       31.56 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.30 ms                             |       3                          |       30.91 ms                             | 
  ├ sirius::Periodic_function|inner                                     |       10.04 ms                             |       2                          |       20.08 ms                             | 
  │ └ sirius::Periodic_function|inner_local                             |        9.76 ms                             |       2                          |       19.52 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.76 ms                             |       2                          |       19.52 ms                             | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.48 ms                             |       1                          |       10.48 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.15 ms                             |       1                          |       10.15 ms                             | 
  ├ sirius::inner                                                       |                        10.29 ms            |                   3              |                        30.87 ms            | 
  └ sirius::finalize                                                    |      187.04 ms →      175.42 ms   (-6.21%) |       1   →       1              |      187.04 ms →      175.42 ms   (-6.21%) | 
  ====================================================================================================================================================================================================
```
