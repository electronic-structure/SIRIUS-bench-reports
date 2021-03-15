# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs 716c74b9e40f2dc514547b13861ce8c977f50e6c
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      182.83 s  →      164.79 s    (-9.87%) |       1   →       1              |      182.83 s  →      164.79 s    (-9.87%) | 
  ├ sirius::initialize                                                  |        2.70 s  →        2.73 s    (+1.04%) |       1   →       1              |        2.70 s  →        2.73 s    (+1.04%) | 
+ ├ sirius::Simulation_context::initialize                              |        4.21 s  →        2.90 s   (-31.13%) |       1   →       1              |        4.21 s  →        2.90 s   (-31.13%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       49.52 ms →       37.16 ms  (-24.97%) |       1   →       1              |       49.52 ms →       37.16 ms  (-24.97%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |        1.49 s  →      123.69 ms  (-91.67%) |       1   →       1              |        1.49 s  →      123.69 ms  (-91.67%) | 
+ │ │ ├ sirius::Atom_type::init                                         |      734.10 ms →       49.65 ms  (-93.24%) |       2   →       2              |        1.47 s  →       99.31 ms  (-93.24%) | 
- │ │ └ sirius::Unit_cell::update                                       |       16.98 ms →       24.20 ms  (+42.55%) |       1   →       1              |       16.98 ms →       24.20 ms  (+42.55%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.26 ms →        5.68 ms   (-9.23%) |       1   →       1              |        6.26 ms →        5.68 ms   (-9.23%) | 
- │ │   └ sirius::Unit_cell::get_symmetry                               |       10.68 ms →       18.47 ms  (+73.01%) |       1   →       1              |       10.68 ms →       18.47 ms  (+73.01%) | 
- │ │     └ sirius::Unit_cell_symmetry                                  |       10.65 ms →       18.45 ms  (+73.23%) |       1   →       1              |       10.65 ms →       18.45 ms  (+73.23%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        5.22 ms →        5.29 ms   (+1.42%) |       1   →       1              |        5.22 ms →        5.29 ms   (+1.42%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.34 ms   (+0.60%) |       1   →       1              |        2.32 ms →        2.34 ms   (+0.60%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      102.47 μs →      105.35 μs   (+2.81%) |       1   →       1              |      102.47 μs →      105.35 μs   (+2.81%) | 
  │ └ sirius::Simulation_context::update                                |        2.63 s  →        2.70 s    (+2.53%) |       1   →       1              |        2.63 s  →        2.70 s    (+2.53%) | 
  │   ├ sirius::Unit_cell::update                                       |       11.90 ms →       12.08 ms   (+1.47%) |       1   →       1              |       11.90 ms →       12.08 ms   (+1.47%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.50 ms →        4.47 ms   (-0.67%) |       1   →       1              |        4.50 ms →        4.47 ms   (-0.67%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        7.36 ms →        7.57 ms   (+2.78%) |       1   →       1              |        7.36 ms →        7.57 ms   (+2.78%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        7.34 ms →        7.55 ms   (+2.80%) |       1   →       1              |        7.34 ms →        7.55 ms   (+2.80%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        4.85 ms →        5.05 ms   (+4.04%) |       1   →       1              |        4.85 ms →        5.05 ms   (+4.04%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.33 ms   (+0.41%) |       1   →       1              |        2.32 ms →        2.33 ms   (+0.41%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       99.44 μs →       98.90 μs   (-0.54%) |       1   →       1              |       99.44 μs →       98.90 μs   (-0.54%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       63.77 ms →       64.51 ms   (+1.16%) |       2   →       2              |      127.54 ms →      129.03 ms   (+1.16%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.17 ms →        5.14 ms   (-0.58%) |       2   →       2              |       10.33 ms →       10.27 ms   (-0.58%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.48 ms →        4.48 ms   (+0.04%) |       1   →       1              |        4.48 ms →        4.48 ms   (+0.04%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.81 ms →       21.92 ms   (+0.50%) |       2   →       2              |       43.62 ms →       43.84 ms   (+0.50%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.77 ms →       14.78 ms   (+0.04%) |       2   →       2              |       29.54 ms →       29.55 ms   (+0.04%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.66 ms →       19.69 ms   (+0.14%) |       4   →       4              |       78.66 ms →       78.77 ms   (+0.14%) | 
  │   ├ sddk::Gvec::init                                                |      175.45 ms →      178.26 ms   (+1.60%) |       2   →       2              |      350.91 ms →      356.51 ms   (+1.60%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      132.94 ms →      133.78 ms   (+0.63%) |       2   →       2              |      265.89 ms →      267.56 ms   (+0.63%) | 
  │   ├ sddk::Gvec_shells                                               |      175.95 ms →      179.70 ms   (+2.13%) |       1   →       1              |      175.95 ms →      179.70 ms   (+2.13%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.32 ms →        1.31 ms   (-0.86%) |       1   →       1              |        1.32 ms →        1.31 ms   (-0.86%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      292.77 ms →      294.83 ms   (+0.70%) |       2   →       2              |      585.53 ms →      589.65 ms   (+0.70%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       38.29 ms →       35.90 ms   (-6.24%) |       1   →       1              |       38.29 ms →       35.90 ms   (-6.24%) | 
- │ ├ sirius::K_point::K_point                                          |        2.92 μs →        6.16 μs (+110.74%) |       4   →       4              |       11.70 μs →       24.66 μs (+110.74%) | 
  │ └ sirius::K_point_set::initialize                                   |       38.19 ms →       35.74 ms   (-6.41%) |       1   →       1              |       38.19 ms →       35.74 ms   (-6.41%) | 
  │   └ sirius::K_point::initialize                                     |       38.10 ms →       35.65 ms   (-6.43%) |       1   →       1              |       38.10 ms →       35.65 ms   (-6.43%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       19.96 ms →       18.22 ms   (-8.73%) |       1   →       1              |       19.96 ms →       18.22 ms   (-8.73%) | 
+ │     │ └ sddk::Gvec::init                                            |        9.11 ms →        8.13 ms  (-10.73%) |       1   →       1              |        9.11 ms →        8.13 ms  (-10.73%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |       10.43 μs                             |       1                          |       10.43 μs                             | 
  │     └ sirius::K_point::update                                       |       13.00 ms →       12.59 ms   (-3.13%) |       1   →       1              |       13.00 ms →       12.59 ms   (-3.13%) | 
  │       └ sirius::Beta_projectors                                     |        6.28 ms →        6.33 ms   (+0.78%) |       1   →       1              |        6.28 ms →        6.33 ms   (+0.78%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.66 ms →        3.76 ms   (+2.68%) |       1   →       1              |        3.66 ms →        3.76 ms   (+2.68%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.37 ms                             |       2                          |       10.74 ms                             | 
  ├ sirius::Potential                                                   |      172.17 ms →      156.23 ms   (-9.26%) |       1   →       1              |      172.17 ms →      156.23 ms   (-9.26%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.95 ms                             |       6                          |       35.68 ms                             | 
  │ └ sirius::Potential::update                                         |      135.75 ms →      126.79 ms   (-6.61%) |       1   →       1              |      135.75 ms →      126.79 ms   (-6.61%) | 
  │   └ sirius::Potential::generate_local_potential                     |      134.87 ms →      126.07 ms   (-6.52%) |       1   →       1              |      134.87 ms →      126.07 ms   (-6.52%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      113.12 ms →      109.09 ms   (-3.56%) |       1   →       1              |      113.12 ms →      109.09 ms   (-3.56%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       21.20 ms →       11.32 ms  (-46.58%) |       1   →       1              |       21.20 ms →       11.32 ms  (-46.58%) | 
  ├ sirius::Density                                                     |      141.03 ms →      135.61 ms   (-3.84%) |       1   →       1              |      141.03 ms →      135.61 ms   (-3.84%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.19 ms                             |       2                          |       10.39 ms                             | 
  │ └ sirius::Density::update                                           |      130.37 ms →      125.03 ms   (-4.10%) |       1   →       1              |      130.37 ms →      125.03 ms   (-4.10%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      129.93 ms →      124.62 ms   (-4.09%) |       1   →       1              |      129.93 ms →      124.62 ms   (-4.09%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      112.65 ms →      111.76 ms   (-0.79%) |       1   →       1              |      112.65 ms →      111.76 ms   (-0.79%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       16.83 ms →       11.03 ms  (-34.47%) |       1   →       1              |       16.83 ms →       11.03 ms  (-34.47%) | 
  ├ sirius::Density::initial_density                                    |      175.61 ms →      172.19 ms   (-1.95%) |       1   →       1              |      175.61 ms →      172.19 ms   (-1.95%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      111.19 ms →      109.69 ms   (-1.35%) |       1   →       1              |      111.19 ms →      109.69 ms   (-1.35%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |       11.06 ms →        9.03 ms  (-18.35%) |       2   →       2              |       22.12 ms →       18.06 ms  (-18.35%) | 
- │ └ sirius::Periodic_function::integrate                              |        9.61 ms →       12.00 ms  (+24.85%) |       1   →       1              |        9.61 ms →       12.00 ms  (+24.85%) | 
  ├ sirius::Potential::generate                                         |      707.68 ms →      684.30 ms   (-3.30%) |       1   →       1              |      707.68 ms →      684.30 ms   (-3.30%) | 
  │ ├ sirius::Potential::poisson                                        |      136.96 ms →      137.13 ms   (+0.12%) |       1   →       1              |      136.96 ms →      137.13 ms   (+0.12%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       16.47 ms →       18.11 ms   (+9.95%) |       1   →       1              |       16.47 ms →       18.11 ms   (+9.95%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.20 ms                             |       1                          |       10.20 ms                             | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.89 ms                             |       1                          |        9.89 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.89 ms                             |       1                          |        9.89 ms                             | 
  │ │ └ sirius::inner                                                   |                        10.36 ms            |                   1              |                        10.36 ms            | 
+ │ ├ sirius::Periodic_function::add                                    |      550.29 μs →      449.42 μs  (-18.33%) |       2   →       2              |        1.10 ms →      898.84 μs  (-18.33%) | 
+ │ ├ sirius::Potential::xc                                             |       58.47 ms →       38.98 ms  (-33.34%) |       1   →       1              |       58.47 ms →       38.98 ms  (-33.34%) | 
+ │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       58.47 ms →       36.67 ms  (-37.28%) |       1   →       1              |       58.47 ms →       36.67 ms  (-37.28%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.69 ms                             |       2                          |       11.38 ms                             | 
  │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        5.26 ms                             |       1                          |        5.26 ms                             | 
  │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                    |                        12.12 ms            |                   2              |                        24.24 ms            | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.81 ms →        5.90 ms   (+1.60%) |       1   →       1              |        5.81 ms →        5.90 ms   (+1.60%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       93.82 ms →       93.58 ms   (-0.26%) |       1   →       1              |       93.82 ms →       93.58 ms   (-0.26%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      410.15 ms →      403.77 ms   (-1.56%) |       1   →       1              |      410.15 ms →      403.77 ms   (-1.56%) | 
- ├ sirius::Hamiltonian0                                                |        8.40 ms →       11.91 ms  (+41.84%) |       1   →       1              |        8.40 ms →       11.91 ms  (+41.84%) | 
  │ ├ sirius::Local_operator                                            |        8.04 ms →        8.00 ms   (-0.47%) |       1   →       1              |        8.04 ms →        8.00 ms   (-0.47%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.75 ms                             |       1                          |        4.75 ms                             | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.36 ms →        2.42 ms   (+2.52%) |       1   →       1              |        2.36 ms →        2.42 ms   (+2.52%) | 
  │ ├ sirius::Non_local_operator                                        |       62.54 μs →       63.30 μs   (+1.21%) |       2   →       2              |      125.09 μs →      126.59 μs   (+1.21%) | 
- │ ├ sirius::D_operator::initialize                                    |       99.82 μs →        1.27 ms (+1175.32%) |       1   →       1              |       99.82 μs →        1.27 ms (+1175.32%) | 
- │ └ sirius::Q_operator::initialize                                    |       75.91 μs →        2.45 ms (+3125.48%) |       1   →       1              |       75.91 μs →        2.45 ms (+3125.48%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.86 s  →        1.87 s    (+0.64%) |       1   →       1              |        1.86 s  →        1.87 s    (+0.64%) | 
  │ ├ sirius::Hamiltonian_k                                             |       19.75 ms →       18.71 ms   (-5.26%) |       1   →       1              |       19.75 ms →       18.71 ms   (-5.26%) | 
+ │ │ ├ sirius::Local_operator::prepare_k                               |      201.76 μs →      180.68 μs  (-10.45%) |       1   →       1              |      201.76 μs →      180.68 μs  (-10.45%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       19.54 ms →       18.52 ms   (-5.22%) |       1   →       1              |       19.54 ms →       18.52 ms   (-5.22%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.84 s  →        1.85 s    (+0.61%) |       1   →       1              |        1.84 s  →        1.85 s    (+0.61%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      126.76 ms                             |       4                          |      507.03 ms                             | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       52.44 ms →       51.71 ms   (-1.40%) |       1   →       1              |       52.44 ms →       51.71 ms   (-1.40%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.09 ms →       21.10 ms   (+0.08%) |       1   →       1              |       21.09 ms →       21.10 ms   (+0.08%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      635.72 ms →      636.89 ms   (+0.18%) |       1   →       1              |      635.72 ms →      636.89 ms   (+0.18%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      297.45 ms →      298.05 ms   (+0.20%) |       1   →       1              |      297.45 ms →      298.05 ms   (+0.20%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.46 μs →        3.24 μs   (-6.30%) |       1   →       1              |        3.46 μs →        3.24 μs   (-6.30%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.53 μs                             |       1                          |        2.53 μs                             | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      395.00 ns                             |       1                          |      395.00 ns                             | 
- │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      447.00 ns →      557.00 ns  (+24.61%) |       1   →       1              |      447.00 ns →      557.00 ns  (+24.61%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.22 ms →        9.22 ms   (+0.01%) |       1   →       1              |        9.22 ms →        9.22 ms   (+0.01%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      120.72 ms →      121.01 ms   (+0.24%) |       1   →       1              |      120.72 ms →      121.01 ms   (+0.24%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      104.15 ms →      104.28 ms   (+0.12%) |       2   →       2              |      208.29 ms →      208.55 ms   (+0.12%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       38.60 ms →       40.49 ms   (+4.90%) |       2   →       2              |       77.19 ms →       80.98 ms   (+4.90%) | 
  │ │ │ ├ sddk::inner                                                   |       38.06 ms                             |       2                          |       76.12 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       28.21 μs                             |       2                          |       56.41 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        39.91 ms            |                   2              |                        79.82 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        91.00 ns            |                   2              |                       182.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        39.43 ms            |                   2              |                        78.86 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                       434.50 ns            |                   2              |                       869.00 ns            | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       57.13 ms →       57.27 ms   (+0.25%) |       1   →       1              |       57.13 ms →       57.27 ms   (+0.25%) | 
  │ │ ├ sddk::transform                                                 |       31.53 ms                             |       1                          |       31.53 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       12.66 μs                             |       1                          |       12.66 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       11.02 μs                             |       1                          |       11.02 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                        30.76 ms            |                   1              |                        30.76 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                        30.76 ms            |                   1              |                        30.76 ms            | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |        1.32 μs →      403.00 ns  (-69.40%) |       1   →       1              |        1.32 μs →      403.00 ns  (-69.40%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      171.42 s  →      155.06 s    (-9.55%) |       1   →       1              |      171.42 s  →      155.06 s    (-9.55%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.87 ms                             |      19                          |      111.53 ms                             | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.62 s                              |      37                          |      171.08 s                              | 
  │ │ ├ sirius::Hamiltonian0                                            |        4.83 ms                             |      37                          |      178.69 ms                             | 
  │ │ │ ├ sirius::Local_operator                                        |        4.45 ms                             |      37                          |      164.77 ms                             | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      966.78 μs                             |      37                          |       35.77 ms                             | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.60 ms                             |      37                          |       96.15 ms                             | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.69 μs                             |      74                          |        4.79 ms                             | 
  │ │ │ ├ sirius::D_operator::initialize                                |       99.51 μs                             |      37                          |        3.68 ms                             | 
  │ │ │ └ sirius::Q_operator::initialize                                |       77.36 μs                             |      37                          |        2.86 ms                             | 
  │ │ ├ sirius::Band::solve                                             |        2.53 s                              |      37                          |       93.55 s                              | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      168.22 μs                             |      37                          |        6.22 ms                             | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      160.95 μs                             |      37                          |        5.96 ms                             | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.57 μs                             |      37                          |      206.22 μs                             | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.47 s                              |      37                          |       91.32 s                              | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       97.32 ms                             |      37                          |        3.60 s                              | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        8.00 ms                             |     222                          |        1.78 s                              | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        5.92 ms                             |      37                          |      218.89 ms                             | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      355.40 μs                             |      37                          |       13.15 ms                             | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.29 ms                             |      74                          |      169.20 ms                             | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.33 s                              |      37                          |       86.17 s                              | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      111.86 ms                             |     354                          |       39.60 s                              | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       43.72 ms                             |     354                          |       15.48 s                              | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.15 μs                             |     354                          |      759.82 μs                             | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.75 μs                             |     354                          |      619.05 μs                             | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      404.95 ns                             |     354                          |      143.35 μs                             | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      495.10 ns                             |     354                          |      175.27 μs                             | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.37 ms                             |     354                          |        2.61 s                              | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       20.14 ms                             |     354                          |        7.13 s                              | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       20.31 ms                             |     708                          |       14.38 s                              | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       36.08 ms                             |     354                          |       12.77 s                              | 
  │ │ │ │   │ ├ sddk::inner                                             |        4.61 ms                             |     671                          |        3.09 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       23.05 μs                             |     671                          |       15.47 ms                             | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |        5.78 ms                             |     354                          |        2.05 s                              | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        8.63 ms                             |     354                          |        3.06 s                              | 
  │ │ │ │   │ └ sddk::transform                                         |       14.44 ms                             |     317                          |        4.58 s                              | 
  │ │ │ │   │   ├ sddk::transform|init                                  |       19.41 μs                             |     317                          |        6.15 ms                             | 
  │ │ │ │   │   └ sddk::transform|local                                 |       34.33 μs                             |     951                          |       32.65 ms                             | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        9.74 ms                             |     354                          |        3.45 s                              | 
  │ │ │ │   │ └ sddk::inner                                             |        8.84 ms                             |     354                          |        3.13 s                              | 
  │ │ │ │   │   └ sddk::inner|local                                     |       29.57 μs                             |     354                          |       10.47 ms                             | 
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       66.01 ms                             |     354                          |       23.37 s                              | 
  │ │ │ │   ├ sirius::residuals                                         |       14.34 ms                             |     343                          |        4.92 s                              | 
  │ │ │ │   │ ├ sddk::transform                                         |       13.26 ms                             |     329                          |        4.36 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       16.27 μs                             |     329                          |        5.35 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       36.16 μs                             |     658                          |       23.79 ms                             | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.46 ms                             |     329                          |      480.43 ms                             | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       52.76 ms                             |      39                          |        2.06 s                              | 
  │ │ │ │     └ sddk::transform                                         |       49.99 ms                             |      41                          |        2.05 s                              | 
  │ │ │ │       ├ sddk::transform|init                                  |       11.79 μs                             |      41                          |      483.43 μs                             | 
  │ │ │ │       └ sddk::transform|local                                 |       13.62 μs                             |      43                          |      585.48 μs                             | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      527.57 ns                             |      37                          |       19.52 μs                             | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       35.30 μs                             |      37                          |        1.31 ms                             | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      585.89 μs                             |      37                          |       21.68 ms                             | 
  │ │ ├ sirius::Density::generate                                       |      770.50 ms                             |      37                          |       28.51 s                              | 
  │ │ │ ├ sirius::Density::generate_valence                             |      401.85 ms                             |      37                          |       14.87 s                              | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.12 μs                             |      37                          |      300.33 μs                             | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.24 μs                             |      37                          |      267.91 μs                             | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       99.90 ms                             |      37                          |        3.70 s                              | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.45 μs                             |      37                          |      275.67 μs                             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.12 ms                             |      37                          |      263.41 ms                             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       90.92 ms                             |      37                          |        3.36 s                              | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      543.11 ns                             |      37                          |       20.09 μs                             | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      162.92 ms                             |      37                          |        6.03 s                              | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms                             |      37                          |       60.63 ms                             | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.32 ms                             |      37                          |        3.27 s                              | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.09 ms                             |      37                          |        3.26 s                              | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      276.43 ms                             |      37                          |       10.23 s                              | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      276.43 ms                             |      37                          |       10.23 s                              | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       25.32 ms                             |      37                          |      936.78 ms                             | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      227.02 ms                             |      37                          |        8.40 s                              | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       22.92 ms                             |      37                          |      848.11 ms                             | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       80.84 ms                             |      37                          |        2.99 s                              | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        7.81 ms                             |      37                          |      289.15 ms                             | 
  │ │ ├ sirius::Density::mix                                            |      231.50 ms                             |      37                          |        8.57 s                              | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      922.41 μs                             |      37                          |       34.13 ms                             | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.82 ms                             |     499                          |        5.40 s                              | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.37 ms                             |     499                          |        5.18 s                              | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.37 ms                             |     499                          |        5.18 s                              | 
  │ │ │ └ sirius::Density::mixer_output                                 |        7.96 ms                             |      37                          |      294.45 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        7.15 ms                             |      37                          |      264.55 ms                             | 
  │ │ ├ sirius::Potential::generate                                     |      687.65 ms                             |      37                          |       25.44 s                              | 
  │ │ │ ├ sirius::Potential::poisson                                    |      137.20 ms                             |      37                          |        5.08 s                              | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       16.54 ms                             |      37                          |      611.91 ms                             | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.45 ms                             |      37                          |      386.67 ms                             | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        9.88 ms                             |      37                          |      365.68 ms                             | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        9.88 ms                             |      37                          |      365.66 ms                             | 
  │ │ │ ├ sirius::Periodic_function::add                                |      546.38 μs                             |      74                          |       40.43 ms                             | 
  │ │ │ ├ sirius::Potential::xc                                         |       53.77 ms                             |      37                          |        1.99 s                              | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       53.77 ms                             |      37                          |        1.99 s                              | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        2.98 ms                             |      74                          |      220.34 ms                             | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.42 ms                             |      37                          |      200.63 ms                             | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.48 ms                             |      37                          |      239.68 ms                             | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.94 ms                             |      37                          |        3.36 s                              | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      396.91 ms                             |      37                          |       14.69 s                              | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      280.26 ms                             |      37                          |       10.37 s                              | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      280.26 ms                             |      37                          |       10.37 s                              | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.37 ms                             |      37                          |        1.01 s                              | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      225.34 ms                             |      37                          |        8.34 s                              | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.75 ms                             |      37                          |      878.61 ms                             | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.47 ms                             |      37                          |      202.43 ms                             | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.33 ms                             |     259                          |        2.68 s                              | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.86 ms                             |     259                          |        2.55 s                              | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.86 ms                             |     259                          |        2.55 s                              | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.65 ms                             |     111                          |        1.18 s                              | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.24 ms                             |     111                          |        1.14 s                              | 
  │ │ ├ sirius::Periodic_function::integrate                            |       10.04 ms                             |      37                          |      371.53 ms                             | 
  │ │ └ sirius::Density::get_magnetisation                              |      117.00 μs                             |      37                          |        4.33 ms                             | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |      111.74 μs                             |      37                          |        4.13 ms                             | 
  │ ├ sirius::Density                                                   |                       141.42 ms            |                   1              |                       141.42 ms            | 
  │ │ └ sirius::Density::update                                         |                       130.87 ms            |                   1              |                       130.87 ms            | 
  │ │   └ sirius::Density::generate_pseudo_core_charge_density          |                       130.45 ms            |                   1              |                       130.45 ms            | 
  │ │     ├ sirius::Simulation_context::make_periodic_function          |                       111.17 ms            |                   1              |                       111.17 ms            | 
  │ │     └ sirius::Smooth_periodic_function::fft_transform             |                        11.30 ms            |                   1              |                        11.30 ms            | 
  │ ├ sirius::Hamiltonian0                                              |                         7.95 ms            |                  35              |                       278.21 ms            | 
  │ │ ├ sirius::Local_operator                                          |                         4.09 ms            |                  35              |                       143.09 ms            | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |                         2.23 ms            |                  35              |                        78.08 ms            | 
  │ │ ├ sirius::Non_local_operator                                      |                        64.34 μs            |                  70              |                         4.50 ms            | 
  │ │ ├ sirius::D_operator::initialize                                  |                         1.25 ms            |                  35              |                        43.86 ms            | 
  │ │ └ sirius::Q_operator::initialize                                  |                         2.42 ms            |                  35              |                        84.53 ms            | 
  │ ├ sirius::Band::solve                                               |                         2.39 s             |                  35              |                        83.70 s             | 
  │ │ ├ sirius::Hamiltonian_k                                           |                       161.12 μs            |                  35              |                         5.64 ms            | 
  │ │ │ ├ sirius::Local_operator::prepare_k                             |                       152.65 μs            |                  35              |                         5.34 ms            | 
  │ │ │ └ sirius::Beta_projectors_base::prepare                         |                         4.18 μs            |                  35              |                       146.22 μs            | 
  │ │ ├ sirius::Band::diag_pseudo_potential_davidson                    |                         2.20 s             |                  35              |                        76.93 s             | 
  │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                           |                         5.89 ms            |                  35              |                       206.02 ms            | 
  │ │ │ ├ sirius::Hamiltonian_k::apply_h_s                              |                        88.77 ms            |                 490              |                        43.50 s             | 
  │ │ │ │ ├ sirius::Local_operator::apply_h                             |                        32.70 ms            |                 490              |                        16.02 s             | 
  │ │ │ │ │ ├ sddk::matrix_storage::remap_forward                       |                         1.43 μs            |                 490              |                       702.97 μs            | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_backward                      |                       436.21 ns            |                 490              |                       213.74 μs            | 
  │ │ │ │ ├ sirius::Beta_projectors_base::generate                      |                         7.29 ms            |                 490              |                         3.57 s             | 
  │ │ │ │ ├ sirius::Beta_projectors_base::inner                         |                        15.56 ms            |                 490              |                         7.63 s             | 
  │ │ │ │ └ sirius::Non_local_operator::apply                           |                        16.60 ms            |                 980              |                        16.27 s             | 
  │ │ │ ├ sddk::orthogonalize                                           |                        26.04 ms            |                 490              |                        12.76 s             | 
  │ │ │ │ ├ sddk::wf_inner                                              |                         4.12 ms            |                 945              |                         3.89 s             | 
  │ │ │ │ │ ├ sddk::wf_inner|scale                                      |                       126.16 ns            |                 945              |                       119.22 μs            | 
  │ │ │ │ │ ├ sddk::wf_inner|pw                                         |                         3.01 ms            |                 945              |                         2.84 s             | 
  │ │ │ │ │ └ sddk::wf_inner|scale_back                                 |                       201.54 ns            |                 945              |                       190.45 μs            | 
  │ │ │ │ ├ sddk::orthogonalize|tmtrx                                   |                         4.16 ms            |                 490              |                         2.04 s             | 
  │ │ │ │ ├ sddk::orthogonalize|transform                               |                         6.19 ms            |                 490              |                         3.03 s             | 
  │ │ │ │ └ sddk::wf_trans                                              |                         8.34 ms            |                 455              |                         3.80 s             | 
  │ │ │ │   └ sddk::wf_trans|pw                                         |                         2.78 ms            |                1.36 K            |                         3.79 s             | 
  │ │ │ ├ sirius::Band::set_subspace_mtrx                               |                         6.56 ms            |                 490              |                         3.22 s             | 
  │ │ │ │ └ sddk::wf_inner                                              |                         6.23 ms            |                 490              |                         3.05 s             | 
  │ │ │ │   ├ sddk::wf_inner|scale                                      |                       107.84 ns            |                 490              |                        52.84 μs            | 
  │ │ │ │   ├ sddk::wf_inner|pw                                         |                         5.12 ms            |                 490              |                         2.51 s             | 
  │ │ │ │   └ sddk::wf_inner|scale_back                                 |                       209.43 ns            |                 490              |                       102.62 μs            | 
  │ │ │ ├ Eigensolver_cuda|zheevdx                                      |                        10.42 ms            |                 490              |                         5.11 s             | 
  │ │ │ ├ sirius::residuals                                             |                         6.66 ms            |                 472              |                         3.14 s             | 
  │ │ │ │ ├ sddk::wf_trans                                              |                         5.51 ms            |                 455              |                         2.51 s             | 
  │ │ │ │ │ └ sddk::wf_trans|pw                                         |                         2.75 ms            |                 910              |                         2.51 s             | 
  │ │ │ │ └ sirius::normalized_preconditioned_residuals                 |                         1.06 ms            |                 455              |                       482.01 ms            | 
  │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|update_phi       |                        38.50 ms            |                 125              |                         4.81 s             | 
  │ │ │   └ sddk::wf_trans                                              |                        22.13 ms            |                 215              |                         4.76 s             | 
  │ │ │     └ sddk::wf_trans|pw                                         |                        15.60 ms            |                 305              |                         4.76 s             | 
  │ │ ├ sirius::Beta_projectors_base::dismiss                           |                       501.66 ns            |                  35              |                        17.56 μs            | 
  │ │ └ sirius::K_point_set::sync_band                                  |                        97.45 μs            |                  35              |                         3.41 ms            | 
  │ ├ sirius::K_point_set::find_band_occupancies                        |                       451.89 μs            |                  35              |                        15.82 ms            | 
  │ │ └ sirius::K_point_set::sync_band                                  |                        26.11 μs            |                  35              |                       913.86 μs            | 
  │ ├ sirius::Density::generate                                         |                       758.38 ms            |                  35              |                        26.54 s             | 
  │ │ ├ sirius::Density::generate_valence                               |                       404.23 ms            |                  35              |                        14.15 s             | 
  │ │ │ ├ sddk::matrix_storage::remap_forward                           |                         2.68 μs            |                  35              |                        93.75 μs            | 
  │ │ │ ├ sirius::Density::add_k_point_contribution_dm                  |                       100.36 ms            |                  35              |                         3.51 s             | 
  │ │ │ │ ├ sirius::Beta_projectors_base::prepare                       |                         9.02 μs            |                  35              |                       315.73 μs            | 
  │ │ │ │ ├ sirius::Beta_projectors_base::generate                      |                         7.12 ms            |                  35              |                       249.26 ms            | 
  │ │ │ │ ├ sirius::Beta_projectors_base::inner                         |                        91.35 ms            |                  35              |                         3.20 s             | 
  │ │ │ │ └ sirius::Beta_projectors_base::dismiss                       |                       508.91 ns            |                  35              |                        17.81 μs            | 
  │ │ │ ├ sirius::Density::add_k_point_contribution_rg                  |                       164.02 ms            |                  35              |                         5.74 s             | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |                         1.64 ms            |                  35              |                        57.41 ms            | 
  │ │ │ └ sirius::Density::augment                                      |                        88.43 ms            |                  35              |                         3.09 s             | 
  │ │ │   └ sirius::Density::generate_rho_aug                           |                        88.19 ms            |                  35              |                         3.09 s             | 
  │ │ ├ sirius::Field4D::symmetrize                                     |                       261.92 ms            |                  35              |                         9.17 s             | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |                       261.91 ms            |                  35              |                         9.17 s             | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |                        24.95 ms            |                  35              |                       873.38 ms            | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |                       210.96 ms            |                  35              |                         7.38 s             | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |                        24.85 ms            |                  35              |                       869.67 ms            | 
  │ │ ├ sirius::Density::symmetrize_density_matrix                      |                        80.87 ms            |                  35              |                         2.83 s             | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |                         7.70 ms            |                  35              |                       269.45 ms            | 
  │ ├ sirius::inner                                                     |                        10.36 ms            |                 429              |                         4.45 s             | 
  │ ├ sirius::Density::mix                                              |                       167.94 ms            |                  35              |                         5.88 s             | 
  │ │ ├ sirius::Density::mixer_input                                    |                         1.08 ms            |                  35              |                        37.85 ms            | 
  │ │ ├ sirius::inner                                                   |                        10.65 ms            |                 469              |                         4.99 s             | 
  │ │ └ sirius::Density::mixer_output                                   |                         6.64 ms            |                  35              |                       232.55 ms            | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |                         5.52 ms            |                  35              |                       193.22 ms            | 
  │ ├ sirius::Potential::generate                                       |                       673.90 ms            |                  35              |                        23.59 s             | 
  │ │ ├ sirius::Potential::poisson                                      |                       136.93 ms            |                  35              |                         4.79 s             | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |                        17.90 ms            |                  35              |                       626.47 ms            | 
  │ │ │ └ sirius::inner                                                 |                        10.71 ms            |                  35              |                       374.68 ms            | 
  │ │ ├ sirius::Periodic_function::add                                  |                       457.02 μs            |                  70              |                        31.99 ms            | 
  │ │ ├ sirius::Potential::xc                                           |                        34.38 ms            |                  35              |                         1.20 s             | 
  │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                          |                        32.01 ms            |                  35              |                         1.12 s             | 
  │ │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                  |                        11.82 ms            |                  70              |                       827.72 ms            | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |                         5.63 ms            |                  35              |                       197.07 ms            | 
  │ │ ├ sirius::Potential::generate_D_operator_matrix                   |                        90.91 ms            |                  35              |                         3.18 s             | 
  │ │ └ sirius::Potential::generate_PAW_effective_potential             |                       401.14 ms            |                  35              |                        14.04 s             | 
  │ ├ sirius::Field4D::symmetrize                                       |                       257.88 ms            |                  35              |                         9.03 s             | 
  │ │ └ sirius::symmetrize_function|fpw                                 |                       257.87 ms            |                  35              |                         9.03 s             | 
  │ │   ├ sddk::Gvec_shells::remap_forward                              |                        23.71 ms            |                  35              |                       829.71 ms            | 
  │ │   ├ sirius::symmetrize_function|fpw|local                         |                       209.87 ms            |                  35              |                         7.35 s             | 
  │ │   └ sddk::Gvec_shells::remap_backward                             |                        23.15 ms            |                  35              |                       810.35 ms            | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |                         5.59 ms            |                  35              |                       195.48 ms            | 
  │ ├ sirius::Periodic_function::integrate                              |                        10.16 ms            |                  35              |                       355.46 ms            | 
  │ ├ sirius::Density::get_magnetisation                                |                        13.68 ms            |                  35              |                       478.72 ms            | 
  │ │ └ sirius::Density::compute_atomic_mag_mom                         |                        13.67 ms            |                  35              |                       478.53 ms            | 
+ │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        7.14 ms →        4.70 ms  (-34.19%) |       2   →       2              |       14.29 ms →        9.40 ms  (-34.19%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.11 ms                             |       6                          |       60.65 ms                             | 
  │ │ └ sirius::Periodic_function|inner_local                           |        9.69 ms                             |       6                          |       58.13 ms                             | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        9.69 ms                             |       6                          |       58.13 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.46 ms                             |       3                          |       31.39 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.04 ms                             |       3                          |       30.12 ms                             | 
  ├ sirius::Periodic_function|inner                                     |       10.04 ms                             |       2                          |       20.08 ms                             | 
  │ └ sirius::Periodic_function|inner_local                             |       10.02 ms                             |       2                          |       20.05 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.02 ms                             |       2                          |       20.05 ms                             | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.53 ms                             |       1                          |       10.53 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.44 ms                             |       1                          |       10.44 ms                             | 
  ├ sirius::inner                                                       |                        10.53 ms            |                   3              |                        31.60 ms            | 
  └ sirius::finalize                                                    |      223.86 ms →      236.50 ms   (+5.64%) |       1   →       1              |      223.86 ms →      236.50 ms   (+5.64%) | 
  ====================================================================================================================================================================================================
```
