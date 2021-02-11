# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs dd26b4c3a8b510264c2723458c0ccaf5eeca6037
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      242.64 s  →      197.38 s   (-18.65%) |       1   →       1              |      242.64 s  →      197.38 s   (-18.65%) | 
  ├ sirius::initialize                                                  |        2.71 s  →        2.76 s    (+1.69%) |       1   →       1              |        2.71 s  →        2.76 s    (+1.69%) | 
  ├ sirius::Simulation_context::initialize                              |        6.01 s  →        5.81 s    (-3.33%) |       1   →       1              |        6.01 s  →        5.81 s    (-3.33%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |      150.08 ms →        3.35 ms  (-97.77%) |       1   →       1              |      150.08 ms →        3.35 ms  (-97.77%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |        1.13 s  →      243.03 ms  (-78.44%) |       1   →       1              |        1.13 s  →      243.03 ms  (-78.44%) | 
+ │ │ ├ sirius::Atom_type::init                                         |      547.09 ms →      105.17 ms  (-80.78%) |       2   →       2              |        1.09 s  →      210.35 ms  (-80.78%) | 
  │ │ └ sirius::Unit_cell::update                                       |       32.77 ms →       32.49 ms   (-0.86%) |       1   →       1              |       32.77 ms →       32.49 ms   (-0.86%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |       11.94 ms →       11.84 ms   (-0.86%) |       1   →       1              |       11.94 ms →       11.84 ms   (-0.86%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       20.76 ms →       20.60 ms   (-0.78%) |       1   →       1              |       20.76 ms →       20.60 ms   (-0.78%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       20.74 ms →       20.57 ms   (-0.81%) |       1   →       1              |       20.74 ms →       20.57 ms   (-0.81%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.16 ms →        4.19 ms   (+0.59%) |       1   →       1              |        4.16 ms →        4.19 ms   (+0.59%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        6.79 ms →        6.77 ms   (-0.23%) |       1   →       1              |        6.79 ms →        6.77 ms   (-0.23%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      127.10 μs →      129.86 μs   (+2.18%) |       1   →       1              |      127.10 μs →      129.86 μs   (+2.18%) | 
- │ └ sirius::Simulation_context::update                                |        4.69 s  →        5.52 s   (+17.68%) |       1   →       1              |        4.69 s  →        5.52 s   (+17.68%) | 
  │   ├ sirius::Unit_cell::update                                       |       16.94 ms →       16.94 ms   (-0.04%) |       1   →       1              |       16.94 ms →       16.94 ms   (-0.04%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        8.39 ms →        8.29 ms   (-1.11%) |       1   →       1              |        8.39 ms →        8.29 ms   (-1.11%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        8.50 ms →        8.60 ms   (+1.07%) |       1   →       1              |        8.50 ms →        8.60 ms   (+1.07%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        8.48 ms →        8.57 ms   (+1.01%) |       1   →       1              |        8.48 ms →        8.57 ms   (+1.01%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.72 ms →        3.77 ms   (+1.51%) |       1   →       1              |        3.72 ms →        3.77 ms   (+1.51%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        4.60 ms →        4.61 ms   (+0.30%) |       1   →       1              |        4.60 ms →        4.61 ms   (+0.30%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      100.58 μs →      109.28 μs   (+8.65%) |       1   →       1              |      100.58 μs →      109.28 μs   (+8.65%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      136.98 ms →      136.09 ms   (-0.65%) |       2   →       2              |      273.96 ms →      272.17 ms   (-0.65%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       12.79 ms →       13.37 ms   (+4.52%) |       2   →       2              |       25.58 ms →       26.74 ms   (+4.52%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       10.86 ms →       10.41 ms   (-4.18%) |       1   →       1              |       10.86 ms →       10.41 ms   (-4.18%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       49.78 ms →       51.00 ms   (+2.46%) |       2   →       2              |       99.56 ms →      102.01 ms   (+2.46%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       34.34 ms →       33.24 ms   (-3.19%) |       2   →       2              |       68.68 ms →       66.49 ms   (-3.19%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       47.59 ms →       47.57 ms   (-0.05%) |       4   →       4              |      190.38 ms →      190.29 ms   (-0.05%) | 
  │   ├ sddk::Gvec::init                                                |      180.37 ms →      173.84 ms   (-3.62%) |       2   →       2              |      360.74 ms →      347.68 ms   (-3.62%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      134.52 ms →      131.77 ms   (-2.04%) |       2   →       2              |      269.03 ms →      263.55 ms   (-2.04%) | 
+ │   ├ sddk::Gvec_shells                                               |      511.11 ms →      269.98 ms  (-47.18%) |       1   →       1              |      511.11 ms →      269.98 ms  (-47.18%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        2.37 ms →        2.42 ms   (+2.10%) |       1   →       1              |        2.37 ms →        2.42 ms   (+2.10%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      293.70 ms →      296.00 ms   (+0.78%) |       2   →       2              |      587.40 ms →      591.99 ms   (+0.78%) | 
+ ├ sirius::K_point_set::create_k_mesh                                  |      405.65 ms →       38.84 ms  (-90.42%) |       1   →       1              |      405.65 ms →       38.84 ms  (-90.42%) | 
- │ ├ sirius::K_point::K_point                                          |        3.14 μs →        4.82 μs  (+53.48%) |       4   →       4              |       12.57 μs →       19.29 μs  (+53.48%) | 
+ │ └ sirius::K_point_set::initialize                                   |      405.56 ms →       38.73 ms  (-90.45%) |       1   →       1              |      405.56 ms →       38.73 ms  (-90.45%) | 
+ │   └ sirius::K_point::initialize                                     |       46.69 ms →       38.62 ms  (-17.29%) |       1   →       1              |       46.69 ms →       38.62 ms  (-17.29%) | 
+ │     ├ sirius::K_point::generate_gkvec                               |       21.51 ms →       18.15 ms  (-15.65%) |       1   →       1              |       21.51 ms →       18.15 ms  (-15.65%) | 
+ │     │ └ sddk::Gvec::init                                            |        9.31 ms →        8.06 ms  (-13.41%) |       1   →       1              |        9.31 ms →        8.06 ms  (-13.41%) | 
- │     ├ sddk::matrix_storage::matrix_storage                          |        7.15 μs →        9.22 μs  (+28.99%) |       1   →       1              |        7.15 μs →        9.22 μs  (+28.99%) | 
+ │     └ sirius::K_point::update                                       |       19.50 ms →       15.66 ms  (-19.69%) |       1   →       1              |       19.50 ms →       15.66 ms  (-19.69%) | 
+ │       └ sirius::Beta_projectors                                     |       11.86 ms →        9.36 ms  (-21.06%) |       1   →       1              |       11.86 ms →        9.36 ms  (-21.06%) | 
+ │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        9.31 ms →        6.82 ms  (-26.80%) |       1   →       1              |        9.31 ms →        6.82 ms  (-26.80%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.08 ms →        5.10 ms   (+0.44%) |       2   →       2              |       10.16 ms →       10.21 ms   (+0.44%) | 
  ├ sirius::Potential                                                   |        1.02 s  →        1.02 s    (+0.13%) |       1   →       1              |        1.02 s  →        1.02 s    (+0.13%) | 
+ │ ├ sirius::Smooth_periodic_function                                  |        5.74 ms →        5.87 ms   (+2.34%) |       6   →       5    (-16.67%) |       34.43 ms →       29.36 ms  (-14.72%) | 
  │ └ sirius::Potential::update                                         |      985.21 ms →      991.55 ms   (+0.64%) |       1   →       1              |      985.21 ms →      991.55 ms   (+0.64%) | 
  │   └ sirius::Potential::generate_local_potential                     |      984.47 ms →      990.79 ms   (+0.64%) |       1   →       1              |      984.47 ms →      990.79 ms   (+0.64%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      951.63 ms →      882.82 ms   (-7.23%) |       1   →       1              |      951.63 ms →      882.82 ms   (-7.23%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |       32.29 ms →      103.62 ms (+220.95%) |       1   →       1              |       32.29 ms →      103.62 ms (+220.95%) | 
  ├ sirius::Density                                                     |      898.14 ms →      817.69 ms   (-8.96%) |       1   →       1              |      898.14 ms →      817.69 ms   (-8.96%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.11 ms →        5.05 ms   (-1.18%) |       2   →       2              |       10.21 ms →       10.09 ms   (-1.18%) | 
  │ └ sirius::Density::update                                           |      887.67 ms →      807.31 ms   (-9.05%) |       1   →       1              |      887.67 ms →      807.31 ms   (-9.05%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      887.24 ms →      806.88 ms   (-9.06%) |       1   →       1              |      887.24 ms →      806.88 ms   (-9.06%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |                       103.84 μs            |                   1              |                       103.84 μs            | 
- │     ├ sirius::Simulation_context::make_periodic_function            |      628.51 ms →      695.27 ms  (+10.62%) |       1   →       1              |      628.51 ms →      695.27 ms  (+10.62%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |      258.24 ms →      111.00 ms  (-57.01%) |       1   →       1              |      258.24 ms →      111.00 ms  (-57.01%) | 
  ├ sirius::Density::initial_density                                    |        1.30 s  →        1.28 s    (-1.79%) |       1   →       1              |        1.30 s  →        1.28 s    (-1.79%) | 
- │ ├ sirius::Simulation_context::make_periodic_function                |      656.35 ms →      836.09 ms  (+27.38%) |       1   →       1              |      656.35 ms →      836.09 ms  (+27.38%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |      296.99 ms →      198.23 ms  (-33.26%) |       2   →       2              |      593.99 ms →      396.45 ms  (-33.26%) | 
+ │ └ sirius::Periodic_function::integrate                              |       12.35 ms →        9.74 ms  (-21.16%) |       1   →       1              |       12.35 ms →        9.74 ms  (-21.16%) | 
  ├ sirius::Potential::generate                                         |        1.43 s  →        1.44 s    (+1.01%) |       1   →       1              |        1.43 s  →        1.44 s    (+1.01%) | 
  │ ├ sirius::Potential::poisson                                        |      861.23 ms →      888.84 ms   (+3.21%) |       1   →       1              |      861.23 ms →      888.84 ms   (+3.21%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |      303.45 ms →      128.98 ms  (-57.49%) |       1   →       1              |      303.45 ms →      128.98 ms  (-57.49%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.67 ms →       10.98 ms   (+2.96%) |       1   →       1              |       10.67 ms →       10.98 ms   (+2.96%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |       10.54 ms →       10.29 ms   (-2.34%) |       1   →       1              |       10.54 ms →       10.29 ms   (-2.34%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |       10.54 ms →       10.29 ms   (-2.34%) |       1   →       1              |       10.54 ms →       10.29 ms   (-2.34%) | 
  │ ├ sirius::Periodic_function::add                                    |      576.24 μs →      562.26 μs   (-2.43%) |       2   →       2              |        1.15 ms →        1.12 ms   (-2.43%) | 
+ │ ├ sirius::Potential::xc                                             |       76.47 ms →       48.78 ms  (-36.22%) |       1   →       1              |       76.47 ms →       48.78 ms  (-36.22%) | 
+ │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       76.47 ms →       46.51 ms  (-39.18%) |       1   →       1              |       76.47 ms →       46.51 ms  (-39.18%) | 
+ │ │   ├ sirius::Smooth_periodic_function                              |        5.67 ms →        5.71 ms   (+0.63%) |       2   →       1    (-50.00%) |       11.34 ms →        5.71 ms  (-49.68%) | 
  │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        5.32 ms                             |       1                          |        5.32 ms                             | 
  │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                    |                        16.45 ms            |                   2              |                        32.91 ms            | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        6.09 ms →       12.45 ms (+104.42%) |       1   →       1              |        6.09 ms →       12.45 ms (+104.42%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.85 ms →       93.68 ms   (+0.90%) |       1   →       1              |       92.85 ms →       93.68 ms   (+0.90%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      390.37 ms →      397.86 ms   (+1.92%) |       1   →       1              |      390.37 ms →      397.86 ms   (+1.92%) | 
- ├ sirius::Hamiltonian0                                                |        8.88 ms →       14.64 ms  (+64.96%) |       1   →       1              |        8.88 ms →       14.64 ms  (+64.96%) | 
  │ ├ sirius::Local_operator                                            |        8.37 ms →        8.08 ms   (-3.43%) |       1   →       1              |        8.37 ms →        8.08 ms   (-3.43%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.56 ms →        4.58 ms   (+0.43%) |       1   →       1              |        4.56 ms →        4.58 ms   (+0.43%) | 
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.83 ms →        2.52 ms  (-11.00%) |       1   →       1              |        2.83 ms →        2.52 ms  (-11.00%) | 
  │ ├ sirius::Non_local_operator                                        |       63.87 μs →       63.05 μs   (-1.27%) |       2   →       2              |      127.74 μs →      126.11 μs   (-1.27%) | 
- │ ├ sirius::D_operator::initialize                                    |      178.50 μs →        1.64 ms (+819.93%) |       1   →       1              |      178.50 μs →        1.64 ms (+819.93%) | 
- │ └ sirius::Q_operator::initialize                                    |      140.21 μs →        4.73 ms (+3273.98%) |       1   →       1              |      140.21 μs →        4.73 ms (+3273.98%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.92 s  →        1.93 s    (+0.48%) |       1   →       1              |        1.92 s  →        1.93 s    (+0.48%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.23 ms →       18.15 ms   (-0.45%) |       1   →       1              |       18.23 ms →       18.15 ms   (-0.45%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      305.60 μs →      290.28 μs   (-5.01%) |       1   →       1              |      305.60 μs →      290.28 μs   (-5.01%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       17.92 ms →       17.86 ms   (-0.39%) |       1   →       1              |       17.92 ms →       17.86 ms   (-0.39%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.90 s  →        1.90 s    (+0.34%) |       1   →       1              |        1.90 s  →        1.90 s    (+0.34%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      129.10 ms →      132.30 ms   (+2.48%) |       4   →       4              |      516.39 ms →      529.21 ms   (+2.48%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |      108.15 ms →      100.99 ms   (-6.62%) |       1   →       1              |      108.15 ms →      100.99 ms   (-6.62%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       22.00 ms →       21.69 ms   (-1.41%) |       1   →       1              |       22.00 ms →       21.69 ms   (-1.41%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      634.44 ms →      635.46 ms   (+0.16%) |       1   →       1              |      634.44 ms →      635.46 ms   (+0.16%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      297.57 ms →      297.83 ms   (+0.09%) |       1   →       1              |      297.57 ms →      297.83 ms   (+0.09%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.27 μs →        3.05 μs   (-6.73%) |       1   →       1              |        3.27 μs →        3.05 μs   (-6.73%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.42 μs →        2.11 μs  (-12.94%) |       1   →       1              |        2.42 μs →        2.11 μs  (-12.94%) | 
+ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      524.00 ns →      427.00 ns  (-18.51%) |       1   →       1              |      524.00 ns →      427.00 ns  (-18.51%) | 
- │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      529.00 ns →      604.00 ns  (+14.18%) |       1   →       1              |      529.00 ns →      604.00 ns  (+14.18%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.23 ms →        9.23 ms   (-0.03%) |       1   →       1              |        9.23 ms →        9.23 ms   (-0.03%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      120.69 ms →      120.80 ms   (+0.08%) |       1   →       1              |      120.69 ms →      120.80 ms   (+0.08%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      103.45 ms →      103.78 ms   (+0.31%) |       2   →       2              |      206.91 ms →      207.56 ms   (+0.31%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       38.48 ms →       39.97 ms   (+3.88%) |       2   →       2              |       76.95 ms →       79.94 ms   (+3.88%) | 
  │ │ │ ├ sddk::inner                                                   |       37.89 ms                             |       2                          |       75.77 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       29.42 μs                             |       2                          |       58.84 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        39.40 ms            |                   2              |                        78.81 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        74.00 ns            |                   2              |                       148.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        38.92 ms            |                   2              |                        77.85 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                       569.00 ns            |                   2              |                         1.14 μs            | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       56.08 ms →       56.85 ms   (+1.38%) |       1   →       1              |       56.08 ms →       56.85 ms   (+1.38%) | 
  │ │ ├ sddk::transform                                                 |       31.55 ms                             |       1                          |       31.55 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       11.83 μs                             |       1                          |       11.83 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       12.09 μs                             |       1                          |       12.09 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                        30.74 ms            |                   1              |                        30.74 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                        30.74 ms            |                   1              |                        30.74 ms            | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      695.00 ns →      434.00 ns  (-37.55%) |       1   →       1              |      695.00 ns →      434.00 ns  (-37.55%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      224.80 s  →      180.51 s   (-19.70%) |       1   →       1              |      224.80 s  →      180.51 s   (-19.70%) | 
+ │ ├ sirius::Smooth_periodic_function                                  |        5.85 ms →        5.16 ms  (-11.87%) |      19   →      18     (-5.26%) |      111.17 ms →       92.82 ms  (-16.51%) | 
  │ ├ sirius::Density                                                   |                       879.33 ms            |                   1              |                       879.33 ms            | 
  │ │ ├ sirius::Smooth_periodic_function                                |                         5.17 ms            |                   2              |                        10.34 ms            | 
  │ │ └ sirius::Density::update                                         |                       868.71 ms            |                   1              |                       868.71 ms            | 
  │ │   └ sirius::Density::generate_pseudo_core_charge_density          |                       868.29 ms            |                   1              |                       868.29 ms            | 
  │ │     ├ sirius::rho_core_ri_pseudo|values                           |                       130.42 μs            |                   1              |                       130.42 μs            | 
  │ │     ├ sirius::Simulation_context::make_periodic_function          |                       831.31 ms            |                   1              |                       831.31 ms            | 
  │ │     └ sirius::Smooth_periodic_function::fft_transform             |                        36.41 ms            |                   1              |                        36.41 ms            | 
- │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        5.58 s  →        8.13 s   (+45.76%) |      40   →      22    (-45.00%) |      223.02 s  →      178.78 s   (-19.83%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        5.11 ms →        9.48 ms  (+85.47%) |      40   →      22    (-45.00%) |      204.39 ms →      208.50 ms   (+2.01%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        4.62 ms →        4.13 ms  (-10.60%) |      40   →      22    (-45.00%) |      184.79 ms →       90.86 ms  (-50.83%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function                            |      935.22 μs →      839.90 μs  (-10.19%) |      40   →      22    (-45.00%) |       37.41 ms →       18.48 ms  (-50.61%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.64 ms →        2.28 ms  (-13.78%) |      40   →      22    (-45.00%) |      105.78 ms →       50.16 ms  (-52.58%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |       65.61 μs →       65.89 μs   (+0.43%) |      80   →      44    (-45.00%) |        5.25 ms →        2.90 ms  (-44.76%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |      173.71 μs →        1.77 ms (+920.32%) |      40   →      22    (-45.00%) |        6.95 ms →       38.99 ms (+461.18%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |      120.76 μs →        3.38 ms (+2699.95%) |      40   →      22    (-45.00%) |        4.83 ms →       74.39 ms (+1439.97%) | 
- │ │ ├ sirius::Band::solve                                             |        2.51 s  →        5.11 s  (+103.45%) |      40   →      22    (-45.00%) |      100.39 s  →      112.33 s   (+11.90%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      278.52 μs →      307.60 μs  (+10.44%) |      40   →      22    (-45.00%) |       11.14 ms →        6.77 ms  (-39.26%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      272.51 μs →      297.26 μs   (+9.08%) |      40   →      22    (-45.00%) |       10.90 ms →        6.54 ms  (-40.00%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.35 μs →        5.21 μs  (+19.90%) |      40   →      22    (-45.00%) |      173.93 μs →      114.70 μs  (-34.05%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.44 s  →        2.67 s    (+9.22%) |      40   →      22    (-45.00%) |       97.67 s  →       58.67 s   (-39.93%) | 
- │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       94.71 ms →      105.54 ms  (+11.43%) |      40   →      22    (-45.00%) |        3.79 s  →        2.32 s   (-38.71%) | 
- │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.46 ms →        9.24 ms  (+23.87%) |     240   →     132    (-45.00%) |        1.79 s  →        1.22 s   (-31.87%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       24.00 ms →       18.09 ms  (-24.65%) |      40   →      22    (-45.00%) |      960.17 ms →      397.90 ms  (-58.56%) | 
+ │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      368.07 μs →      363.78 μs   (-1.17%) |      40   →      22    (-45.00%) |       14.72 ms →        8.00 ms  (-45.64%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |       11.32 ms →        8.38 ms  (-25.98%) |      80   →      44    (-45.00%) |      905.95 ms →      368.81 ms  (-59.29%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.29 s  →        2.51 s    (+9.62%) |      40   →      22    (-45.00%) |       91.49 s  →       55.16 s   (-39.71%) | 
+ │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      111.96 ms →      104.05 ms   (-7.06%) |     367   →     299    (-18.53%) |       41.09 s  →       31.11 s   (-24.28%) | 
+ │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       43.81 ms →       39.95 ms   (-8.81%) |     367   →     299    (-18.53%) |       16.08 s  →       11.94 s   (-25.71%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.95 μs →        1.77 μs   (-9.34%) |     367   →     299    (-18.53%) |      715.91 μs →      528.76 μs  (-26.14%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.67 μs →        1.52 μs   (-9.38%) |     367   →     299    (-18.53%) |      613.95 μs →      453.27 μs  (-26.17%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      406.46 ns →      388.26 ns   (-4.48%) |     367   →     299    (-18.53%) |      149.17 μs →      116.09 μs  (-22.17%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      459.21 ns →      524.94 ns  (+14.31%) |     367   →     299    (-18.53%) |      168.53 μs →      156.96 μs   (-6.87%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.37 ms →        7.34 ms   (-0.38%) |     367   →     299    (-18.53%) |        2.71 s  →        2.20 s   (-18.84%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       20.23 ms →       18.43 ms   (-8.91%) |     367   →     299    (-18.53%) |        7.43 s  →        5.51 s   (-25.79%) | 
+ │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       20.26 ms →       19.15 ms   (-5.49%) |     734   →     598    (-18.53%) |       14.87 s  →       11.45 s   (-23.00%) | 
+ │ │ │ │   ├ sddk::orthogonalize                                       |       44.83 ms →       40.08 ms  (-10.60%) |     367   →     299    (-18.53%) |       16.45 s  →       11.98 s   (-27.17%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        4.56 ms                             |     694                          |        3.16 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       21.42 μs                             |     694                          |       14.87 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                         4.88 ms            |                 576              |                         2.81 s             | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                       103.76 ns            |                 576              |                        59.77 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                         3.77 ms            |                 576              |                         2.17 s             | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                       235.57 ns            |                 576              |                       135.69 μs            | 
+ │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |       15.04 ms →       13.31 ms  (-11.49%) |     367   →     299    (-18.53%) |        5.52 s  →        3.98 s   (-27.89%) | 
+ │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        8.73 ms →        7.68 ms  (-12.08%) |     367   →     299    (-18.53%) |        3.20 s  →        2.30 s   (-28.37%) | 
  │ │ │ │   │ ├ sddk::transform                                         |       13.96 ms                             |     327                          |        4.57 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       19.18 μs                             |     327                          |        6.27 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       32.20 μs                             |     981                          |       31.59 ms                             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                        10.46 ms            |                 277              |                         2.90 s             | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                         3.48 ms            |                 831              |                         2.90 s             | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        9.88 ms →        8.35 ms  (-15.49%) |     367   →     299    (-18.53%) |        3.63 s  →        2.50 s   (-31.15%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        8.74 ms                             |     367                          |        3.21 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       32.03 μs                             |     367                          |       11.76 ms                             | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                         7.94 ms            |                 299              |                         2.37 s             | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                       113.57 ns            |                 299              |                        33.96 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                         6.82 ms            |                 299              |                         2.04 s             | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                       240.88 ns            |                 299              |                        72.02 μs            | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       62.91 ms →       12.36 ms  (-80.35%) |     367   →     299    (-18.53%) |       23.09 s  →        3.70 s   (-83.99%) | 
+ │ │ │ │   ├ sirius::residuals                                         |       14.34 ms →        7.50 ms  (-47.70%) |     355   →     288    (-18.87%) |        5.09 s  →        2.16 s   (-57.57%) | 
  │ │ │ │   │ ├ sddk::transform                                         |       13.23 ms                             |     341                          |        4.51 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       14.58 μs                             |     341                          |        4.97 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       35.31 μs                             |     682                          |       24.08 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                         6.24 ms            |                 277              |                         1.73 s             | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                         3.12 ms            |                 554              |                         1.73 s             | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.47 ms →        1.14 ms  (-22.57%) |     341   →     277    (-18.77%) |      500.82 ms →      315.03 ms  (-37.10%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       50.71 ms →       44.93 ms  (-11.40%) |      42   →      82    (+95.24%) |        2.13 s  →        3.68 s   (+72.97%) | 
  │ │ │ │     ├ sddk::transform                                         |       48.22 ms                             |      44                          |        2.12 s                              | 
  │ │ │ │     │ ├ sddk::transform|init                                  |       10.93 μs                             |      44                          |      481.11 μs                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       12.82 μs                             |      46                          |      589.91 μs                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                        25.62 ms            |                 142              |                         3.64 s             | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                        18.01 ms            |                 202              |                         3.64 s             | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      478.38 ns →      446.00 ns   (-6.77%) |      40   →      22    (-45.00%) |       19.14 μs →        9.81 μs  (-48.72%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       34.69 μs →        2.25 ms (+6388.87%) |      40   →      22    (-45.00%) |        1.39 ms →       49.52 ms (+3468.88%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |      609.22 μs →       59.12 ms (+9604.10%) |      40   →      22    (-45.00%) |       24.37 ms →        1.30 s  (+5237.25%) | 
+ │ │ ├ sirius::Density::generate                                       |      791.57 ms →      810.35 ms   (+2.37%) |      40   →      22    (-45.00%) |       31.66 s  →       17.83 s   (-43.70%) | 
- │ │ │ ├ sirius::Density::generate_valence                             |      405.56 ms →      452.70 ms  (+11.62%) |      40   →      22    (-45.00%) |       16.22 s  →        9.96 s   (-38.61%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        7.98 μs →        2.63 μs  (-67.01%) |      40   →      22    (-45.00%) |      319.22 μs →       57.93 μs  (-81.85%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.38 μs →        2.32 μs  (-68.52%) |      40   →      22    (-45.00%) |      295.36 μs →       51.14 μs  (-82.69%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |      101.08 ms →      144.10 ms  (+42.56%) |      40   →      22    (-45.00%) |        4.04 s  →        3.17 s   (-21.59%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.42 μs →        9.21 μs  (+24.18%) |      40   →      22    (-45.00%) |      296.70 μs →      202.65 μs  (-31.70%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.12 ms →        7.12 ms   (-0.02%) |      40   →      22    (-45.00%) |      284.83 ms →      156.63 ms  (-45.01%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       90.90 ms →       91.50 ms   (+0.66%) |      40   →      22    (-45.00%) |        3.64 s  →        2.01 s   (-44.64%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      679.00 ns →      630.09 ns   (-7.20%) |      40   →      22    (-45.00%) |       27.16 μs →       13.86 μs  (-48.96%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      162.93 ms →      164.55 ms   (+0.99%) |      40   →      22    (-45.00%) |        6.52 s  →        3.62 s   (-44.45%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.73 ms →        1.71 ms   (-1.29%) |      40   →      22    (-45.00%) |       69.25 ms →       37.60 ms  (-45.71%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |       88.37 ms →       88.59 ms   (+0.26%) |      40   →      22    (-45.00%) |        3.53 s  →        1.95 s   (-44.86%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.08 ms →       88.34 ms   (+0.29%) |      40   →      22    (-45.00%) |        3.52 s  →        1.94 s   (-44.84%) | 
+ │ │ │ ├ sirius::Field4D::symmetrize                                   |      287.13 ms →      257.72 ms  (-10.24%) |      40   →      22    (-45.00%) |       11.49 s  →        5.67 s   (-50.63%) | 
+ │ │ │ │ └ sirius::symmetrize_function|fpw                             |      287.13 ms →      257.72 ms  (-10.24%) |      40   →      22    (-45.00%) |       11.49 s  →        5.67 s   (-50.63%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       30.91 ms →       26.74 ms  (-13.50%) |      40   →      22    (-45.00%) |        1.24 s  →      588.19 ms  (-52.42%) | 
+ │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      228.21 ms →      206.42 ms   (-9.55%) |      40   →      22    (-45.00%) |        9.13 s  →        4.54 s   (-50.25%) | 
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       26.84 ms →       23.39 ms  (-12.83%) |      40   →      22    (-45.00%) |        1.07 s  →      514.66 ms  (-52.06%) | 
+ │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       81.89 ms →       82.17 ms   (+0.35%) |      40   →      22    (-45.00%) |        3.28 s  →        1.81 s   (-44.81%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        8.38 ms →        7.68 ms   (-8.29%) |      40   →      22    (-45.00%) |      335.00 ms →      168.98 ms  (-49.56%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |                        11.23 ms            |                 198              |                         2.22 s             | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |                        10.60 ms            |                 198              |                         2.10 s             | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |                        10.60 ms            |                 198              |                         2.10 s             | 
+ │ │ ├ sirius::Density::mix                                            |      413.63 ms →      215.99 ms  (-47.78%) |      40   →      22    (-45.00%) |       16.55 s  →        4.75 s   (-71.28%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |        1.16 ms →        1.24 ms   (+6.82%) |      40   →      22    (-45.00%) |       46.41 ms →       27.27 ms  (-41.25%) | 
+ │ │ │ ├ sirius::Periodic_function|inner                               |       11.82 ms →       10.72 ms   (-9.27%) |     530   →     274    (-48.30%) |        6.26 s  →        2.94 s   (-53.10%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner_local                       |       11.57 ms →       10.03 ms  (-13.25%) |     530   →     274    (-48.30%) |        6.13 s  →        2.75 s   (-55.15%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       11.57 ms →       10.03 ms  (-13.25%) |     530   →     274    (-48.30%) |        6.13 s  →        2.75 s   (-55.15%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        7.60 ms →        6.90 ms   (-9.19%) |      40   →      22    (-45.00%) |      304.14 ms →      151.91 ms  (-50.05%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        6.54 ms →        5.61 ms  (-14.30%) |      40   →      22    (-45.00%) |      261.71 ms →      123.36 ms  (-52.86%) | 
+ │ │ ├ sirius::Potential::generate                                     |        1.44 s  →        1.45 s    (+0.90%) |      40   →      22    (-45.00%) |       57.54 s  →       31.93 s   (-44.51%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |      894.55 ms →      914.53 ms   (+2.23%) |      40   →      22    (-45.00%) |       35.78 s  →       20.12 s   (-43.77%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |      128.04 ms →      123.80 ms   (-3.31%) |      40   →      22    (-45.00%) |        5.12 s  →        2.72 s   (-46.82%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner                             |       11.03 ms →       10.91 ms   (-1.03%) |      40   →      22    (-45.00%) |      441.06 ms →      240.09 ms  (-45.57%) | 
+ │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.52 ms →       10.56 ms   (+0.38%) |      40   →      22    (-45.00%) |      420.77 ms →      232.30 ms  (-44.79%) | 
+ │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.52 ms →       10.56 ms   (+0.38%) |      40   →      22    (-45.00%) |      420.75 ms →      232.29 ms  (-44.79%) | 
+ │ │ │ ├ sirius::Periodic_function::add                                |      607.07 μs →      540.04 μs  (-11.04%) |      80   →      44    (-45.00%) |       48.57 ms →       23.76 ms  (-51.07%) | 
+ │ │ │ ├ sirius::Potential::xc                                         |       67.33 ms →       45.73 ms  (-32.08%) |      40   →      22    (-45.00%) |        2.69 s  →        1.01 s   (-62.64%) | 
+ │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       67.33 ms →       43.52 ms  (-35.35%) |      40   →      22    (-45.00%) |        2.69 s  →      957.51 ms  (-64.44%) | 
+ │ │ │ │   ├ sirius::Smooth_periodic_function                          |        2.98 ms →        1.22 ms  (-59.24%) |      80   →      22    (-72.50%) |      238.58 ms →       26.74 ms  (-88.79%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |        6.41 ms                             |      40                          |      256.59 ms                             | 
  │ │ │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                |                        17.21 ms            |                  44              |                       757.28 ms            | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.51 ms →       10.45 ms  (+60.57%) |      40   →      22    (-45.00%) |      260.33 ms →      229.91 ms  (-11.69%) | 
+ │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.96 ms →       90.95 ms   (-0.01%) |      40   →      22    (-45.00%) |        3.64 s  →        2.00 s   (-45.00%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      376.54 ms →      387.23 ms   (+2.84%) |      40   →      22    (-45.00%) |       15.06 s  →        8.52 s   (-43.44%) | 
+ │ │ ├ sirius::Field4D::symmetrize                                     |      290.15 ms →      256.96 ms  (-11.44%) |      40   →      22    (-45.00%) |       11.61 s  →        5.65 s   (-51.29%) | 
+ │ │ │ └ sirius::symmetrize_function|fpw                               |      290.15 ms →      256.95 ms  (-11.44%) |      40   →      22    (-45.00%) |       11.61 s  →        5.65 s   (-51.29%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       31.10 ms →       25.04 ms  (-19.50%) |      40   →      22    (-45.00%) |        1.24 s  →      550.77 ms  (-55.73%) | 
+ │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      227.78 ms →      207.26 ms   (-9.01%) |      40   →      22    (-45.00%) |        9.11 s  →        4.56 s   (-49.96%) | 
+ │ │ │   └ sddk::Gvec_shells::remap_backward                           |       27.56 ms →       23.52 ms  (-14.69%) |      40   →      22    (-45.00%) |        1.10 s  →      517.33 ms  (-53.08%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        6.32 ms →        5.67 ms  (-10.30%) |      40   →      22    (-45.00%) |      252.97 ms →      124.81 ms  (-50.66%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.94 ms                             |     280                          |        3.06 s                              | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |       10.37 ms                             |     280                          |        2.90 s                              | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |       10.37 ms                             |     280                          |        2.90 s                              | 
+ │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.92 ms →       11.20 ms   (+2.49%) |     120   →      66    (-45.00%) |        1.31 s  →      738.98 ms  (-43.63%) | 
+ │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        9.90 ms →       10.57 ms   (+6.79%) |     120   →      66    (-45.00%) |        1.19 s  →      697.53 ms  (-41.27%) | 
+ │ │ ├ sirius::Periodic_function::integrate                            |       10.17 ms →       10.66 ms   (+4.78%) |      40   →      22    (-45.00%) |      406.88 ms →      234.49 ms  (-42.37%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      122.55 μs →       35.11 ms (+28548.22%) |      40   →      22    (-45.00%) |        4.90 ms →      772.37 ms (+15656.52%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      117.54 μs →       35.10 ms (+29762.83%) |      40   →      22    (-45.00%) |        4.70 ms →      772.19 ms (+16324.55%) | 
+ │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        6.87 ms →        4.92 ms  (-28.46%) |       2   →       2              |       13.74 ms →        9.83 ms  (-28.46%) | 
- │ ├ sirius::Periodic_function|inner                                   |       10.12 ms →       11.70 ms  (+15.60%) |       6   →       6              |       60.71 ms →       70.18 ms  (+15.60%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.07 ms →       10.13 ms   (+0.57%) |       6   →       6              |       60.42 ms →       60.77 ms   (+0.57%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.07 ms →       10.13 ms   (+0.57%) |       6   →       6              |       60.42 ms →       60.76 ms   (+0.57%) | 
- │ └ sirius::Smooth_periodic_function|inner                            |        9.92 ms →       11.57 ms  (+16.59%) |       3   →       3              |       29.77 ms →       34.71 ms  (+16.59%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.62 ms →       10.14 ms   (+5.36%) |       3   →       3              |       28.87 ms →       30.42 ms   (+5.36%) | 
- ├ sirius::Periodic_function|inner                                     |       10.27 ms →       11.36 ms  (+10.51%) |       2   →       2              |       20.55 ms →       22.71 ms  (+10.51%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.26 ms →       10.12 ms   (-1.39%) |       2   →       2              |       20.52 ms →       20.23 ms   (-1.39%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.26 ms →       10.11 ms   (-1.39%) |       2   →       2              |       20.51 ms →       20.23 ms   (-1.39%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        9.72 ms →       10.45 ms   (+7.43%) |       1   →       1              |        9.72 ms →       10.45 ms   (+7.43%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        9.72 ms →       10.13 ms   (+4.23%) |       1   →       1              |        9.72 ms →       10.13 ms   (+4.23%) | 
+ └ sirius::finalize                                                    |      227.07 ms →      181.87 ms  (-19.91%) |       1   →       1              |      227.07 ms →      181.87 ms  (-19.91%) | 
  ====================================================================================================================================================================================================
```
