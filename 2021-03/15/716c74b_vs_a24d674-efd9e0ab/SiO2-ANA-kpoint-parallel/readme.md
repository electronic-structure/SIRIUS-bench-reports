# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs 716c74b9e40f2dc514547b13861ce8c977f50e6c
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      175.75 s  →      123.03 s   (-29.99%) |       1   →       1              |      175.75 s  →      123.03 s   (-29.99%) | 
  ├ sirius::initialize                                                  |        2.72 s  →        2.72 s    (-0.02%) |       1   →       1              |        2.72 s  →        2.72 s    (-0.02%) | 
  ├ sirius::Simulation_context::initialize                              |        2.98 s  →        3.06 s    (+2.52%) |       1   →       1              |        2.98 s  →        3.06 s    (+2.52%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       36.34 ms →      299.86 μs  (-99.17%) |       1   →       1              |       36.34 ms →      299.86 μs  (-99.17%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      198.74 ms →      295.05 ms  (+48.46%) |       1   →       1              |      198.74 ms →      295.05 ms  (+48.46%) | 
- │ │ ├ sirius::Atom_type::init                                         |       86.24 ms →      135.08 ms  (+56.64%) |       2   →       2              |      172.47 ms →      270.17 ms  (+56.64%) | 
  │ │ └ sirius::Unit_cell::update                                       |       26.20 ms →       24.70 ms   (-5.73%) |       1   →       1              |       26.20 ms →       24.70 ms   (-5.73%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.54 ms →        6.52 ms   (-0.33%) |       1   →       1              |        6.54 ms →        6.52 ms   (-0.33%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       19.61 ms →       18.13 ms   (-7.56%) |       1   →       1              |       19.61 ms →       18.13 ms   (-7.56%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       19.59 ms →       18.11 ms   (-7.58%) |       1   →       1              |       19.59 ms →       18.11 ms   (-7.58%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        5.30 ms →        5.20 ms   (-1.90%) |       1   →       1              |        5.30 ms →        5.20 ms   (-1.90%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.34 ms →        2.32 ms   (-0.63%) |       1   →       1              |        2.34 ms →        2.32 ms   (-0.63%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      104.57 μs →      104.47 μs   (-0.09%) |       1   →       1              |      104.57 μs →      104.47 μs   (-0.09%) | 
  │ └ sirius::Simulation_context::update                                |        2.70 s  →        2.71 s    (+0.47%) |       1   →       1              |        2.70 s  →        2.71 s    (+0.47%) | 
  │   ├ sirius::Unit_cell::update                                       |       12.42 ms →       11.81 ms   (-4.87%) |       1   →       1              |       12.42 ms →       11.81 ms   (-4.87%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.47 ms →        4.48 ms   (+0.09%) |       1   →       1              |        4.47 ms →        4.48 ms   (+0.09%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        7.92 ms →        7.30 ms   (-7.74%) |       1   →       1              |        7.92 ms →        7.30 ms   (-7.74%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        7.89 ms →        7.28 ms   (-7.82%) |       1   →       1              |        7.89 ms →        7.28 ms   (-7.82%) | 
+ │   │     ├ sirius::Unit_cell_symmetry|spg                            |        5.40 ms →        4.78 ms  (-11.51%) |       1   →       1              |        5.40 ms →        4.78 ms  (-11.51%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.31 ms →        2.33 ms   (+0.71%) |       1   →       1              |        2.31 ms →        2.33 ms   (+0.71%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      103.82 μs →       99.60 μs   (-4.07%) |       1   →       1              |      103.82 μs →       99.60 μs   (-4.07%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       64.89 ms →       64.62 ms   (-0.43%) |       2   →       2              |      129.79 ms →      129.23 ms   (-0.43%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.15 ms →        5.14 ms   (-0.22%) |       2   →       2              |       10.30 ms →       10.28 ms   (-0.22%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.47 ms →        4.47 ms   (-0.00%) |       1   →       1              |        4.47 ms →        4.47 ms   (-0.00%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.77 ms →       21.78 ms   (+0.03%) |       2   →       2              |       43.55 ms →       43.56 ms   (+0.03%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.75 ms →       14.76 ms   (+0.05%) |       2   →       2              |       29.50 ms →       29.52 ms   (+0.05%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.56 ms →       19.73 ms   (+0.84%) |       4   →       4              |       78.26 ms →       78.91 ms   (+0.84%) | 
  │   ├ sddk::Gvec::init                                                |      179.04 ms →      172.80 ms   (-3.49%) |       2   →       2              |      358.09 ms →      345.59 ms   (-3.49%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      136.08 ms →      130.21 ms   (-4.32%) |       2   →       2              |      272.17 ms →      260.42 ms   (-4.32%) | 
  │   ├ sddk::Gvec_shells                                               |      166.15 ms →      177.87 ms   (+7.06%) |       1   →       1              |      166.15 ms →      177.87 ms   (+7.06%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.31 ms →        1.32 ms   (+0.29%) |       1   →       1              |        1.31 ms →        1.32 ms   (+0.29%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      293.24 ms →      292.47 ms   (-0.26%) |       2   →       2              |      586.48 ms →      584.93 ms   (-0.26%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       36.16 ms →       39.35 ms   (+8.83%) |       1   →       1              |       36.16 ms →       39.35 ms   (+8.83%) | 
- │ ├ sirius::K_point::K_point                                          |        2.94 μs →        6.59 μs (+123.62%) |       4   →       4              |       11.78 μs →       26.34 μs (+123.62%) | 
  │ └ sirius::K_point_set::initialize                                   |       36.06 ms →       39.22 ms   (+8.75%) |       1   →       1              |       36.06 ms →       39.22 ms   (+8.75%) | 
  │   └ sirius::K_point::initialize                                     |       35.97 ms →       39.13 ms   (+8.77%) |       1   →       1              |       35.97 ms →       39.13 ms   (+8.77%) | 
- │     ├ sirius::K_point::generate_gkvec                               |       18.33 ms →       21.17 ms  (+15.50%) |       1   →       1              |       18.33 ms →       21.17 ms  (+15.50%) | 
  │     │ └ sddk::Gvec::init                                            |        8.14 ms →        8.65 ms   (+6.25%) |       1   →       1              |        8.14 ms →        8.65 ms   (+6.25%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |       10.27 μs                             |       1                          |       10.27 μs                             | 
  │     └ sirius::K_point::update                                       |       12.63 ms →       12.84 ms   (+1.65%) |       1   →       1              |       12.63 ms →       12.84 ms   (+1.65%) | 
  │       └ sirius::Beta_projectors                                     |        6.32 ms →        6.23 ms   (-1.41%) |       1   →       1              |        6.32 ms →        6.23 ms   (-1.41%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.71 ms →        3.71 ms   (-0.02%) |       1   →       1              |        3.71 ms →        3.71 ms   (-0.02%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.32 ms                             |       2                          |       10.64 ms                             | 
  ├ sirius::Potential                                                   |      171.34 ms →      158.86 ms   (-7.28%) |       1   →       1              |      171.34 ms →      158.86 ms   (-7.28%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.85 ms                             |       6                          |       35.11 ms                             | 
  │ └ sirius::Potential::update                                         |      135.47 ms →      129.42 ms   (-4.47%) |       1   →       1              |      135.47 ms →      129.42 ms   (-4.47%) | 
  │   └ sirius::Potential::generate_local_potential                     |      134.74 ms →      128.70 ms   (-4.48%) |       1   →       1              |      134.74 ms →      128.70 ms   (-4.48%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      125.46 ms →      115.17 ms   (-8.20%) |       1   →       1              |      125.46 ms →      115.17 ms   (-8.20%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        8.73 ms →        5.45 ms  (-37.60%) |       1   →       1              |        8.73 ms →        5.45 ms  (-37.60%) | 
  ├ sirius::Density                                                     |      140.89 ms →      136.68 ms   (-2.99%) |       1   →       1              |      140.89 ms →      136.68 ms   (-2.99%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.24 ms                             |       2                          |       10.49 ms                             | 
  │ └ sirius::Density::update                                           |      130.13 ms →      126.16 ms   (-3.05%) |       1   →       1              |      130.13 ms →      126.16 ms   (-3.05%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      129.69 ms →      125.75 ms   (-3.04%) |       1   →       1              |      129.69 ms →      125.75 ms   (-3.04%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      124.09 ms →      118.31 ms   (-4.66%) |       1   →       1              |      124.09 ms →      118.31 ms   (-4.66%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        5.15 ms →        5.24 ms   (+1.77%) |       1   →       1              |        5.15 ms →        5.24 ms   (+1.77%) | 
  ├ sirius::Density::initial_density                                    |      178.73 ms →      172.17 ms   (-3.67%) |       1   →       1              |      178.73 ms →      172.17 ms   (-3.67%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      122.50 ms →      117.11 ms   (-4.40%) |       1   →       1              |      122.50 ms →      117.11 ms   (-4.40%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.64 ms →        5.15 ms   (-8.73%) |       2   →       2              |       11.29 ms →       10.30 ms   (-8.73%) | 
  │ └ sirius::Periodic_function::integrate                              |       11.83 ms →       11.71 ms   (-1.01%) |       1   →       1              |       11.83 ms →       11.71 ms   (-1.01%) | 
  ├ sirius::Potential::generate                                         |      702.85 ms →      685.91 ms   (-2.41%) |       1   →       1              |      702.85 ms →      685.91 ms   (-2.41%) | 
  │ ├ sirius::Potential::poisson                                        |      137.32 ms →      138.44 ms   (+0.82%) |       1   →       1              |      137.32 ms →      138.44 ms   (+0.82%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.69 ms →        5.65 ms   (-0.65%) |       1   →       1              |        5.69 ms →        5.65 ms   (-0.65%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.34 ms                             |       1                          |       10.34 ms                             | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |       10.30 ms                             |       1                          |       10.30 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |       10.30 ms                             |       1                          |       10.30 ms                             | 
  │ │ └ sirius::inner                                                   |                        11.35 ms            |                   1              |                        11.35 ms            | 
+ │ ├ sirius::Periodic_function::add                                    |      536.76 μs →      471.92 μs  (-12.08%) |       2   →       2              |        1.07 ms →      943.84 μs  (-12.08%) | 
+ │ ├ sirius::Potential::xc                                             |       58.55 ms →       41.21 ms  (-29.62%) |       1   →       1              |       58.55 ms →       41.21 ms  (-29.62%) | 
+ │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       58.54 ms →       38.89 ms  (-33.56%) |       1   →       1              |       58.54 ms →       38.89 ms  (-33.56%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.76 ms                             |       2                          |       11.52 ms                             | 
  │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        5.37 ms                             |       1                          |        5.37 ms                             | 
  │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                    |                        12.72 ms            |                   2              |                        25.44 ms            | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.73 ms →        4.77 ms  (-16.75%) |       1   →       1              |        5.73 ms →        4.77 ms  (-16.75%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       93.66 ms →       93.61 ms   (-0.05%) |       1   →       1              |       93.66 ms →       93.61 ms   (-0.05%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      405.17 ms →      402.90 ms   (-0.56%) |       1   →       1              |      405.17 ms →      402.90 ms   (-0.56%) | 
- ├ sirius::Hamiltonian0                                                |        8.60 ms →       12.08 ms  (+40.52%) |       1   →       1              |        8.60 ms →       12.08 ms  (+40.52%) | 
  │ ├ sirius::Local_operator                                            |        8.25 ms →        8.27 ms   (+0.21%) |       1   →       1              |        8.25 ms →        8.27 ms   (+0.21%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.76 ms                             |       1                          |        4.76 ms                             | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.58 ms →        2.68 ms   (+3.82%) |       1   →       1              |        2.58 ms →        2.68 ms   (+3.82%) | 
  │ ├ sirius::Non_local_operator                                        |       62.04 μs →       62.44 μs   (+0.64%) |       2   →       2              |      124.09 μs →      124.87 μs   (+0.64%) | 
- │ ├ sirius::D_operator::initialize                                    |       94.37 μs →        1.25 ms (+1221.49%) |       1   →       1              |       94.37 μs →        1.25 ms (+1221.49%) | 
- │ └ sirius::Q_operator::initialize                                    |       75.27 μs →        2.38 ms (+3056.72%) |       1   →       1              |       75.27 μs →        2.38 ms (+3056.72%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.87 s  →        1.86 s    (-0.35%) |       1   →       1              |        1.87 s  →        1.86 s    (-0.35%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.71 ms →       18.12 ms   (-3.16%) |       1   →       1              |       18.71 ms →       18.12 ms   (-3.16%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      192.80 μs →      205.26 μs   (+6.46%) |       1   →       1              |      192.80 μs →      205.26 μs   (+6.46%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       18.52 ms →       17.91 ms   (-3.28%) |       1   →       1              |       18.52 ms →       17.91 ms   (-3.28%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.85 s  →        1.84 s    (-0.40%) |       1   →       1              |        1.85 s  →        1.84 s    (-0.40%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      128.24 ms                             |       4                          |      512.95 ms                             | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       52.79 ms →       52.63 ms   (-0.29%) |       1   →       1              |       52.79 ms →       52.63 ms   (-0.29%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.06 ms →       21.00 ms   (-0.30%) |       1   →       1              |       21.06 ms →       21.00 ms   (-0.30%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      636.75 ms →      645.12 ms   (+1.31%) |       1   →       1              |      636.75 ms →      645.12 ms   (+1.31%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      297.54 ms →      302.74 ms   (+1.75%) |       1   →       1              |      297.54 ms →      302.74 ms   (+1.75%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.38 μs →        3.08 μs   (-8.93%) |       1   →       1              |        3.38 μs →        3.08 μs   (-8.93%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.55 μs                             |       1                          |        2.55 μs                             | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      357.00 ns                             |       1                          |      357.00 ns                             | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      545.00 ns →      591.00 ns   (+8.44%) |       1   →       1              |      545.00 ns →      591.00 ns   (+8.44%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.23 ms →        9.23 ms   (-0.03%) |       1   →       1              |        9.23 ms →        9.23 ms   (-0.03%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      120.81 ms →      121.80 ms   (+0.82%) |       1   →       1              |      120.81 ms →      121.80 ms   (+0.82%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      104.56 ms →      105.65 ms   (+1.04%) |       2   →       2              |      209.13 ms →      211.31 ms   (+1.04%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       38.53 ms →       40.19 ms   (+4.31%) |       2   →       2              |       77.05 ms →       80.37 ms   (+4.31%) | 
  │ │ │ ├ sddk::inner                                                   |       37.97 ms                             |       2                          |       75.93 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       23.12 μs                             |       2                          |       46.23 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        39.64 ms            |                   2              |                        79.27 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        72.50 ns            |                   2              |                       145.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        39.18 ms            |                   2              |                        78.36 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                       488.50 ns            |                   2              |                       977.00 ns            | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       56.83 ms →       61.64 ms   (+8.47%) |       1   →       1              |       56.83 ms →       61.64 ms   (+8.47%) | 
  │ │ ├ sddk::transform                                                 |       31.80 ms                             |       1                          |       31.80 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       12.88 μs                             |       1                          |       12.88 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       13.06 μs                             |       1                          |       13.06 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                        30.87 ms            |                   1              |                        30.87 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                        30.86 ms            |                   1              |                        30.86 ms            | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      640.00 ns →      428.00 ns  (-33.12%) |       1   →       1              |      640.00 ns →      428.00 ns  (-33.12%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      165.58 s  →      113.15 s   (-31.67%) |       1   →       1              |      165.58 s  →      113.15 s   (-31.67%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.81 ms                             |      19                          |      110.47 ms                             | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.72 s                              |      35                          |      165.24 s                              | 
  │ │ ├ sirius::Hamiltonian0                                            |        4.70 ms                             |      35                          |      164.60 ms                             | 
  │ │ │ ├ sirius::Local_operator                                        |        4.34 ms                             |      35                          |      151.75 ms                             | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      975.94 μs                             |      35                          |       34.16 ms                             | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.47 ms                             |      35                          |       86.55 ms                             | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.64 μs                             |      70                          |        4.52 ms                             | 
  │ │ │ ├ sirius::D_operator::initialize                                |       93.28 μs                             |      35                          |        3.26 ms                             | 
  │ │ │ └ sirius::Q_operator::initialize                                |       75.82 μs                             |      35                          |        2.65 ms                             | 
  │ │ ├ sirius::Band::solve                                             |        2.62 s                              |      35                          |       91.79 s                              | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      162.61 μs                             |      35                          |        5.69 ms                             | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      156.38 μs                             |      35                          |        5.47 ms                             | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.68 μs                             |      35                          |      163.94 μs                             | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.56 s                              |      35                          |       89.58 s                              | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |      101.57 ms                             |      35                          |        3.56 s                              | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        8.64 ms                             |     210                          |        1.81 s                              | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        5.97 ms                             |      35                          |      208.85 ms                             | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      353.95 μs                             |      35                          |       12.39 ms                             | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.30 ms                             |      70                          |      160.78 ms                             | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.42 s                              |      35                          |       84.56 s                              | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      106.66 ms                             |     362                          |       38.61 s                              | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       41.24 ms                             |     362                          |       14.93 s                              | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.79 μs                             |     362                          |      648.88 μs                             | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.53 μs                             |     362                          |      552.29 μs                             | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      300.29 ns                             |     362                          |      108.71 μs                             | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      379.67 ns                             |     362                          |      137.44 μs                             | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.36 ms                             |     362                          |        2.66 s                              | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       19.12 ms                             |     362                          |        6.92 s                              | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       19.47 ms                             |     724                          |       14.09 s                              | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       34.73 ms                             |     362                          |       12.57 s                              | 
  │ │ │ │   │ ├ sddk::inner                                             |        4.42 ms                             |     689                          |        3.04 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       20.62 μs                             |     689                          |       14.21 ms                             | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |        5.47 ms                             |     362                          |        1.98 s                              | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        8.16 ms                             |     362                          |        2.95 s                              | 
  │ │ │ │   │ └ sddk::transform                                         |       14.04 ms                             |     327                          |        4.59 s                              | 
  │ │ │ │   │   ├ sddk::transform|init                                  |       17.40 μs                             |     327                          |        5.69 ms                             | 
  │ │ │ │   │   └ sddk::transform|local                                 |       33.10 μs                             |     981                          |       32.47 ms                             | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        9.41 ms                             |     362                          |        3.41 s                              | 
  │ │ │ │   │ └ sddk::inner                                             |        8.54 ms                             |     362                          |        3.09 s                              | 
  │ │ │ │   │   └ sddk::inner|local                                     |       27.29 μs                             |     362                          |        9.88 ms                             | 
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       63.90 ms                             |     362                          |       23.13 s                              | 
  │ │ │ │   ├ sirius::residuals                                         |       13.77 ms                             |     350                          |        4.82 s                              | 
  │ │ │ │   │ ├ sddk::transform                                         |       12.74 ms                             |     336                          |        4.28 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       14.14 μs                             |     336                          |        4.75 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       34.95 μs                             |     672                          |       23.49 ms                             | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.39 ms                             |     336                          |      465.68 ms                             | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       54.17 ms                             |      37                          |        2.00 s                              | 
  │ │ │ │     └ sddk::transform                                         |       51.19 ms                             |      39                          |        2.00 s                              | 
  │ │ │ │       ├ sddk::transform|init                                  |       11.97 μs                             |      39                          |      466.77 μs                             | 
  │ │ │ │       └ sddk::transform|local                                 |       13.36 μs                             |      41                          |      547.55 μs                             | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      477.29 ns                             |      35                          |       16.70 μs                             | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       30.48 μs                             |      35                          |        1.07 ms                             | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      605.51 μs                             |      35                          |       21.19 ms                             | 
  │ │ ├ sirius::Density::generate                                       |      772.66 ms                             |      35                          |       27.04 s                              | 
  │ │ │ ├ sirius::Density::generate_valence                             |      401.23 ms                             |      35                          |       14.04 s                              | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        7.59 μs                             |      35                          |      265.63 μs                             | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        6.96 μs                             |      35                          |      243.52 μs                             | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       99.94 ms                             |      35                          |        3.50 s                              | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.23 μs                             |      35                          |      252.90 μs                             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.12 ms                             |      35                          |      249.31 ms                             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       90.95 ms                             |      35                          |        3.18 s                              | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      572.11 ns                             |      35                          |       20.02 μs                             | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      162.12 ms                             |      35                          |        5.67 s                              | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.65 ms                             |      35                          |       57.64 ms                             | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.31 ms                             |      35                          |        3.09 s                              | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.08 ms                             |      35                          |        3.08 s                              | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      277.22 ms                             |      35                          |        9.70 s                              | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      277.22 ms                             |      35                          |        9.70 s                              | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.89 ms                             |      35                          |      871.23 ms                             | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      227.24 ms                             |      35                          |        7.95 s                              | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       23.91 ms                             |      35                          |      836.97 ms                             | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       81.44 ms                             |      35                          |        2.85 s                              | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        9.21 ms                             |      35                          |      322.20 ms                             | 
  │ │ ├ sirius::Density::mix                                            |      233.91 ms                             |      35                          |        8.19 s                              | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      927.14 μs                             |      35                          |       32.45 ms                             | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       11.14 ms                             |     469                          |        5.22 s                              | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.83 ms                             |     469                          |        5.08 s                              | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.83 ms                             |     469                          |        5.08 s                              | 
  │ │ │ └ sirius::Density::mixer_output                                 |        7.63 ms                             |      35                          |      266.97 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        6.82 ms                             |      35                          |      238.77 ms                             | 
  │ │ ├ sirius::Potential::generate                                     |      685.56 ms                             |      35                          |       23.99 s                              | 
  │ │ │ ├ sirius::Potential::poisson                                    |      137.21 ms                             |      35                          |        4.80 s                              | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        5.70 ms                             |      35                          |      199.53 ms                             | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.64 ms                             |      35                          |      372.44 ms                             | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.55 ms                             |      35                          |      369.26 ms                             | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.55 ms                             |      35                          |      369.24 ms                             | 
  │ │ │ ├ sirius::Periodic_function::add                                |      553.40 μs                             |      70                          |       38.74 ms                             | 
  │ │ │ ├ sirius::Potential::xc                                         |       53.41 ms                             |      35                          |        1.87 s                              | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       53.41 ms                             |      35                          |        1.87 s                              | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.02 ms                             |      70                          |      211.67 ms                             | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.34 ms                             |      35                          |      186.73 ms                             | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.44 ms                             |      35                          |      225.35 ms                             | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.90 ms                             |      35                          |        3.18 s                              | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      395.21 ms                             |      35                          |       13.83 s                              | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      280.34 ms                             |      35                          |        9.81 s                              | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      280.34 ms                             |      35                          |        9.81 s                              | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.42 ms                             |      35                          |      959.87 ms                             | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      225.02 ms                             |      35                          |        7.88 s                              | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       24.09 ms                             |      35                          |      843.27 ms                             | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.45 ms                             |      35                          |      190.64 ms                             | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.61 ms                             |     245                          |        2.60 s                              | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |       10.34 ms                             |     245                          |        2.53 s                              | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |       10.34 ms                             |     245                          |        2.53 s                              | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.27 ms                             |     105                          |        1.08 s                              | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        9.86 ms                             |     105                          |        1.04 s                              | 
  │ │ ├ sirius::Periodic_function::integrate                            |        9.95 ms                             |      35                          |      348.41 ms                             | 
  │ │ └ sirius::Density::get_magnetisation                              |      112.09 μs                             |      35                          |        3.92 ms                             | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |      106.77 μs                             |      35                          |        3.74 ms                             | 
  │ ├ sirius::Density                                                   |                       161.12 ms            |                   1              |                       161.12 ms            | 
  │ │ └ sirius::Density::update                                         |                       150.68 ms            |                   1              |                       150.68 ms            | 
  │ │   └ sirius::Density::generate_pseudo_core_charge_density          |                       150.27 ms            |                   1              |                       150.27 ms            | 
  │ │     ├ sirius::Simulation_context::make_periodic_function          |                       118.91 ms            |                   1              |                       118.91 ms            | 
  │ │     └ sirius::Smooth_periodic_function::fft_transform             |                         5.09 ms            |                   1              |                         5.09 ms            | 
  │ ├ sirius::Hamiltonian0                                              |                         8.05 ms            |                  24              |                       193.10 ms            | 
  │ │ ├ sirius::Local_operator                                          |                         4.23 ms            |                  24              |                       101.59 ms            | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |                         2.32 ms            |                  24              |                        55.59 ms            | 
  │ │ ├ sirius::Non_local_operator                                      |                        64.31 μs            |                  48              |                         3.09 ms            | 
  │ │ ├ sirius::D_operator::initialize                                  |                         1.23 ms            |                  24              |                        29.62 ms            | 
  │ │ └ sirius::Q_operator::initialize                                  |                         2.39 ms            |                  24              |                        57.26 ms            | 
  │ ├ sirius::Band::solve                                               |                         2.66 s             |                  24              |                        63.95 s             | 
  │ │ ├ sirius::Hamiltonian_k                                           |                       178.08 μs            |                  24              |                         4.27 ms            | 
  │ │ │ ├ sirius::Local_operator::prepare_k                             |                       168.60 μs            |                  24              |                         4.05 ms            | 
  │ │ │ └ sirius::Beta_projectors_base::prepare                         |                         5.11 μs            |                  24              |                       122.71 μs            | 
  │ │ ├ sirius::Band::diag_pseudo_potential_davidson                    |                         2.47 s             |                  24              |                        59.35 s             | 
  │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                           |                         5.92 ms            |                  24              |                       142.08 ms            | 
  │ │ │ ├ sirius::Hamiltonian_k::apply_h_s                              |                       105.13 ms            |                 316              |                        33.22 s             | 
  │ │ │ │ ├ sirius::Local_operator::apply_h                             |                        40.09 ms            |                 316              |                        12.67 s             | 
  │ │ │ │ │ ├ sddk::matrix_storage::remap_forward                       |                         1.67 μs            |                 316              |                       527.56 μs            | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_backward                      |                       500.73 ns            |                 316              |                       158.23 μs            | 
  │ │ │ │ ├ sirius::Beta_projectors_base::generate                      |                         7.34 ms            |                 316              |                         2.32 s             | 
  │ │ │ │ ├ sirius::Beta_projectors_base::inner                         |                        19.25 ms            |                 316              |                         6.08 s             | 
  │ │ │ │ └ sirius::Non_local_operator::apply                           |                        19.22 ms            |                 632              |                        12.14 s             | 
  │ │ │ ├ sddk::orthogonalize                                           |                        31.67 ms            |                 316              |                        10.01 s             | 
  │ │ │ │ ├ sddk::wf_inner                                              |                         4.86 ms            |                 608              |                         2.96 s             | 
  │ │ │ │ │ ├ sddk::wf_inner|scale                                      |                       136.02 ns            |                 608              |                        82.70 μs            | 
  │ │ │ │ │ ├ sddk::wf_inner|pw                                         |                         3.75 ms            |                 608              |                         2.28 s             | 
  │ │ │ │ │ └ sddk::wf_inner|scale_back                                 |                       247.60 ns            |                 608              |                       150.54 μs            | 
  │ │ │ │ ├ sddk::orthogonalize|tmtrx                                   |                         5.03 ms            |                 316              |                         1.59 s             | 
  │ │ │ │ ├ sddk::orthogonalize|transform                               |                         7.64 ms            |                 316              |                         2.41 s             | 
  │ │ │ │ └ sddk::wf_trans                                              |                        10.43 ms            |                 292              |                         3.04 s             | 
  │ │ │ │   └ sddk::wf_trans|pw                                         |                         3.47 ms            |                 876              |                         3.04 s             | 
  │ │ │ ├ sirius::Band::set_subspace_mtrx                               |                         8.23 ms            |                 316              |                         2.60 s             | 
  │ │ │ │ └ sddk::wf_inner                                              |                         7.82 ms            |                 316              |                         2.47 s             | 
  │ │ │ │   ├ sddk::wf_inner|scale                                      |                       116.94 ns            |                 316              |                        36.95 μs            | 
  │ │ │ │   ├ sddk::wf_inner|pw                                         |                         6.71 ms            |                 316              |                         2.12 s             | 
  │ │ │ │   └ sddk::wf_inner|scale_back                                 |                       246.80 ns            |                 316              |                        77.99 μs            | 
  │ │ │ ├ Eigensolver_cuda|zheevdx                                      |                        12.51 ms            |                 316              |                         3.95 s             | 
  │ │ │ ├ sirius::residuals                                             |                         7.55 ms            |                 305              |                         2.30 s             | 
  │ │ │ │ ├ sddk::wf_trans                                              |                         6.35 ms            |                 292              |                         1.85 s             | 
  │ │ │ │ │ └ sddk::wf_trans|pw                                         |                         3.17 ms            |                 584              |                         1.85 s             | 
  │ │ │ │ └ sirius::normalized_preconditioned_residuals                 |                         1.16 ms            |                 292              |                       338.67 ms            | 
  │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|update_phi       |                        42.98 ms            |                  90              |                         3.87 s             | 
  │ │ │   └ sddk::wf_trans                                              |                        24.54 ms            |                 156              |                         3.83 s             | 
  │ │ │     └ sddk::wf_trans|pw                                         |                        17.24 ms            |                 222              |                         3.83 s             | 
  │ │ ├ sirius::Beta_projectors_base::dismiss                           |                       418.92 ns            |                  24              |                        10.05 μs            | 
  │ │ └ sirius::K_point_set::sync_band                                  |                       118.55 μs            |                  24              |                         2.85 ms            | 
  │ ├ sirius::K_point_set::find_band_occupancies                        |                       532.98 μs            |                  24              |                        12.79 ms            | 
  │ │ └ sirius::K_point_set::sync_band                                  |                        44.62 μs            |                  24              |                         1.07 ms            | 
  │ ├ sirius::Density::generate                                         |                       764.08 ms            |                  24              |                        18.34 s             | 
  │ │ ├ sirius::Density::generate_valence                               |                       405.98 ms            |                  24              |                         9.74 s             | 
  │ │ │ ├ sddk::matrix_storage::remap_forward                           |                         2.89 μs            |                  24              |                        69.30 μs            | 
  │ │ │ ├ sirius::Density::add_k_point_contribution_dm                  |                       100.86 ms            |                  24              |                         2.42 s             | 
  │ │ │ │ ├ sirius::Beta_projectors_base::prepare                       |                         8.90 μs            |                  24              |                       213.66 μs            | 
  │ │ │ │ ├ sirius::Beta_projectors_base::generate                      |                         7.12 ms            |                  24              |                       170.99 ms            | 
  │ │ │ │ ├ sirius::Beta_projectors_base::inner                         |                        91.77 ms            |                  24              |                         2.20 s             | 
  │ │ │ │ └ sirius::Beta_projectors_base::dismiss                       |                       555.42 ns            |                  24              |                        13.33 μs            | 
  │ │ │ ├ sirius::Density::add_k_point_contribution_rg                  |                       165.09 ms            |                  24              |                         3.96 s             | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |                         1.65 ms            |                  24              |                        39.50 ms            | 
  │ │ │ └ sirius::Density::augment                                      |                        88.47 ms            |                  24              |                         2.12 s             | 
  │ │ │   └ sirius::Density::generate_rho_aug                           |                        88.24 ms            |                  24              |                         2.12 s             | 
  │ │ ├ sirius::Field4D::symmetrize                                     |                       264.78 ms            |                  24              |                         6.35 s             | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |                       264.77 ms            |                  24              |                         6.35 s             | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |                        24.83 ms            |                  24              |                       595.93 ms            | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |                       214.70 ms            |                  24              |                         5.15 s             | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |                        24.10 ms            |                  24              |                       578.35 ms            | 
  │ │ ├ sirius::Density::symmetrize_density_matrix                      |                        80.73 ms            |                  24              |                         1.94 s             | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |                         8.91 ms            |                  24              |                       213.90 ms            | 
  │ ├ sirius::inner                                                     |                        10.34 ms            |                 297              |                         3.07 s             | 
  │ ├ sirius::Density::mix                                              |                       158.93 ms            |                  24              |                         3.81 s             | 
  │ │ ├ sirius::Density::mixer_input                                    |                         1.11 ms            |                  24              |                        26.54 ms            | 
  │ │ ├ sirius::inner                                                   |                        10.54 ms            |                 304              |                         3.20 s             | 
  │ │ └ sirius::Density::mixer_output                                   |                         6.52 ms            |                  24              |                       156.51 ms            | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |                         5.39 ms            |                  24              |                       129.33 ms            | 
  │ ├ sirius::Potential::generate                                       |                       674.99 ms            |                  24              |                        16.20 s             | 
  │ │ ├ sirius::Potential::poisson                                      |                       137.99 ms            |                  24              |                         3.31 s             | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |                         5.69 ms            |                  24              |                       136.54 ms            | 
  │ │ │ └ sirius::inner                                                 |                        10.74 ms            |                  24              |                       257.82 ms            | 
  │ │ ├ sirius::Periodic_function::add                                  |                       460.14 μs            |                  48              |                        22.09 ms            | 
  │ │ ├ sirius::Potential::xc                                           |                        34.89 ms            |                  24              |                       837.36 ms            | 
  │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                          |                        32.52 ms            |                  24              |                       780.45 ms            | 
  │ │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                  |                        12.12 ms            |                  48              |                       581.79 ms            | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |                         4.95 ms            |                  24              |                       118.82 ms            | 
  │ │ ├ sirius::Potential::generate_D_operator_matrix                   |                        91.01 ms            |                  24              |                         2.18 s             | 
  │ │ └ sirius::Potential::generate_PAW_effective_potential             |                       401.22 ms            |                  24              |                         9.63 s             | 
  │ ├ sirius::Field4D::symmetrize                                       |                       262.64 ms            |                  24              |                         6.30 s             | 
  │ │ └ sirius::symmetrize_function|fpw                                 |                       262.63 ms            |                  24              |                         6.30 s             | 
  │ │   ├ sddk::Gvec_shells::remap_forward                              |                        23.66 ms            |                  24              |                       567.89 ms            | 
  │ │   ├ sirius::symmetrize_function|fpw|local                         |                       213.36 ms            |                  24              |                         5.12 s             | 
  │ │   └ sddk::Gvec_shells::remap_backward                             |                        24.47 ms            |                  24              |                       587.18 ms            | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |                         5.51 ms            |                  24              |                       132.28 ms            | 
  │ ├ sirius::Periodic_function::integrate                              |                        10.17 ms            |                  24              |                       244.01 ms            | 
  │ ├ sirius::Density::get_magnetisation                                |                        13.59 ms            |                  24              |                       326.06 ms            | 
  │ │ └ sirius::Density::compute_atomic_mag_mom                         |                        13.58 ms            |                  24              |                       325.92 ms            | 
+ │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        7.05 ms →        4.69 ms  (-33.50%) |       2   →       2              |       14.09 ms →        9.37 ms  (-33.50%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.63 ms                             |       6                          |       63.75 ms                             | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.35 ms                             |       6                          |       62.10 ms                             | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.35 ms                             |       6                          |       62.10 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.07 ms                             |       3                          |       30.20 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.82 ms                             |       3                          |       29.45 ms                             | 
  ├ sirius::Periodic_function|inner                                     |       10.45 ms                             |       2                          |       20.90 ms                             | 
  │ └ sirius::Periodic_function|inner_local                             |       10.17 ms                             |       2                          |       20.35 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.17 ms                             |       2                          |       20.34 ms                             | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.07 ms                             |       1                          |       10.07 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        9.67 ms                             |       1                          |        9.67 ms                             | 
  ├ sirius::inner                                                       |                        10.56 ms            |                   3              |                        31.68 ms            | 
- └ sirius::finalize                                                    |      174.48 ms →      223.11 ms  (+27.87%) |       1   →       1              |      174.48 ms →      223.11 ms  (+27.87%) | 
  ====================================================================================================================================================================================================
```
