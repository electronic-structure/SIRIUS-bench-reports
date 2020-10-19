# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs a923c3c8853d846138a8b9a9c096494004b8d208
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |       77.21 s  →       71.41 s    (-7.51%) |       1   →       1              |       77.21 s  →       71.41 s    (-7.51%) | 
  ├ sirius::initialize                                                  |        2.85 s  →        2.91 s    (+2.06%) |       1   →       1              |        2.85 s  →        2.91 s    (+2.06%) | 
  ├ sirius::Simulation_context::initialize                              |        3.67 s  →        3.66 s    (-0.32%) |       1   →       1              |        3.67 s  →        3.66 s    (-0.32%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       30.35 ms →        2.13 ms  (-92.99%) |       1   →       1              |       30.35 ms →        2.13 ms  (-92.99%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      164.90 ms →      142.32 ms  (-13.69%) |       1   →       1              |      164.90 ms →      142.32 ms  (-13.69%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       73.21 ms →       62.40 ms  (-14.76%) |       2   →       2              |      146.41 ms →      124.80 ms  (-14.76%) | 
  │ │ └ sirius::Unit_cell::update                                       |       18.40 ms →       17.44 ms   (-5.24%) |       1   →       1              |       18.40 ms →       17.44 ms   (-5.24%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        5.17 ms →        5.19 ms   (+0.40%) |       1   →       1              |        5.17 ms →        5.19 ms   (+0.40%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       13.15 ms →       12.17 ms   (-7.48%) |       1   →       1              |       13.15 ms →       12.17 ms   (-7.48%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       13.07 ms →       12.10 ms   (-7.43%) |       1   →       1              |       13.07 ms →       12.10 ms   (-7.43%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.75 ms →        2.75 ms   (-0.09%) |       1   →       1              |        2.75 ms →        2.75 ms   (-0.09%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      523.17 μs →      497.44 μs   (-4.92%) |       1   →       1              |      523.17 μs →      497.44 μs   (-4.92%) | 
+ │ │       └ sirius::Unit_cell_symmetry|mag                            |       17.62 μs →       15.28 μs  (-13.27%) |       1   →       1              |       17.62 μs →       15.28 μs  (-13.27%) | 
  │ └ sirius::Simulation_context::update                                |        3.39 s  →        3.42 s    (+0.92%) |       1   →       1              |        3.39 s  →        3.42 s    (+0.92%) | 
  │   ├ sirius::Unit_cell::update                                       |        6.77 ms →        7.01 ms   (+3.61%) |       1   →       1              |        6.77 ms →        7.01 ms   (+3.61%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.43 ms →        3.65 ms   (+6.32%) |       1   →       1              |        3.43 ms →        3.65 ms   (+6.32%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.28 ms →        3.30 ms   (+0.49%) |       1   →       1              |        3.28 ms →        3.30 ms   (+0.49%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.24 ms →        3.26 ms   (+0.51%) |       1   →       1              |        3.24 ms →        3.26 ms   (+0.51%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.70 ms →        2.70 ms   (+0.04%) |       1   →       1              |        2.70 ms →        2.70 ms   (+0.04%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      504.80 μs →      521.37 μs   (+3.28%) |       1   →       1              |      504.80 μs →      521.37 μs   (+3.28%) | 
+ │   │     └ sirius::Unit_cell_symmetry|mag                            |       14.90 μs →       13.41 μs  (-10.01%) |       1   →       1              |       14.90 μs →       13.41 μs  (-10.01%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      213.99 ms →      212.45 ms   (-0.72%) |       2   →       2              |      427.98 ms →      424.91 ms   (-0.72%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.20 ms →       15.14 ms   (-0.45%) |       2   →       2              |       30.41 ms →       30.27 ms   (-0.45%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.28 ms →       13.27 ms   (-0.07%) |       1   →       1              |       13.28 ms →       13.27 ms   (-0.07%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.60 ms →       56.36 ms   (-0.44%) |       2   →       2              |      113.21 ms →      112.72 ms   (-0.44%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.31 ms →       45.06 ms   (-0.56%) |       2   →       2              |       90.63 ms →       90.12 ms   (-0.56%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.51 ms →       60.20 ms   (-0.51%) |       4   →       4              |      242.04 ms →      240.80 ms   (-0.51%) | 
  │   ├ sddk::Gvec::init                                                |       96.54 ms →       93.91 ms   (-2.72%) |       2   →       2              |      193.08 ms →      187.82 ms   (-2.72%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       71.29 ms →       70.56 ms   (-1.03%) |       2   →       2              |      142.58 ms →      141.11 ms   (-1.03%) | 
+ │   ├ sddk::Gvec_shells                                               |      124.95 ms →       96.50 ms  (-22.77%) |       1   →       1              |      124.95 ms →       96.50 ms  (-22.77%) | 
- │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.69 ms →        1.94 ms  (+14.95%) |       1   →       1              |        1.69 ms →        1.94 ms  (+14.95%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      518.81 ms →      565.83 ms   (+9.06%) |       2   →       2              |        1.04 s  →        1.13 s    (+9.06%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |      157.75 ms →      154.81 ms   (-1.86%) |       1   →       1              |      157.75 ms →      154.81 ms   (-1.86%) | 
- │ ├ sirius::K_point::K_point                                          |        1.37 μs →        2.02 μs  (+47.40%) |       4   →       4              |        5.48 μs →        8.08 μs  (+47.40%) | 
  │ └ sirius::K_point_set::initialize                                   |      157.68 ms →      154.71 ms   (-1.88%) |       1   →       1              |      157.68 ms →      154.71 ms   (-1.88%) | 
  │   └ sirius::K_point::initialize                                     |       29.98 ms →       28.41 ms   (-5.25%) |       1   →       1              |       29.98 ms →       28.41 ms   (-5.25%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       12.20 ms →       11.13 ms   (-8.77%) |       1   →       1              |       12.20 ms →       11.13 ms   (-8.77%) | 
  │     │ └ sddk::Gvec::init                                            |        5.30 ms →        4.99 ms   (-5.89%) |       1   →       1              |        5.30 ms →        4.99 ms   (-5.89%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        7.95 μs →        7.50 μs   (-5.71%) |       1   →       1              |        7.95 μs →        7.50 μs   (-5.71%) | 
  │     └ sirius::K_point::update                                       |       14.58 ms →       14.41 ms   (-1.13%) |       1   →       1              |       14.58 ms →       14.41 ms   (-1.13%) | 
  │       └ sirius::Beta_projectors                                     |       10.21 ms →       10.39 ms   (+1.72%) |       1   →       1              |       10.21 ms →       10.39 ms   (+1.72%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.27 ms →        8.44 ms   (+2.12%) |       1   →       1              |        8.27 ms →        8.44 ms   (+2.12%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.59 ms →        2.57 ms   (-0.86%) |       2   →       2              |        5.19 ms →        5.14 ms   (-0.86%) | 
  ├ sirius::Potential                                                   |       54.90 ms →       50.65 ms   (-7.74%) |       1   →       1              |       54.90 ms →       50.65 ms   (-7.74%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.93 ms →        2.90 ms   (-0.81%) |       6   →       6              |       17.56 ms →       17.42 ms   (-0.81%) | 
+ │ └ sirius::Potential::update                                         |       36.70 ms →       32.66 ms  (-11.01%) |       1   →       1              |       36.70 ms →       32.66 ms  (-11.01%) | 
+ │   └ sirius::Potential::generate_local_potential                     |       36.33 ms →       32.26 ms  (-11.20%) |       1   →       1              |       36.33 ms →       32.26 ms  (-11.20%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       25.69 ms →       24.23 ms   (-5.70%) |       1   →       1              |       25.69 ms →       24.23 ms   (-5.70%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       10.35 ms →        7.52 ms  (-27.30%) |       1   →       1              |       10.35 ms →        7.52 ms  (-27.30%) | 
+ ├ sirius::Density                                                     |       44.96 ms →       38.69 ms  (-13.95%) |       1   →       1              |       44.96 ms →       38.69 ms  (-13.95%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.81 ms →        2.84 ms   (+1.04%) |       2   →       2              |        5.61 ms →        5.67 ms   (+1.04%) | 
+ │ └ sirius::Density::update                                           |       39.21 ms →       32.88 ms  (-16.15%) |       1   →       1              |       39.21 ms →       32.88 ms  (-16.15%) | 
+ │   └ sirius::Density::generate_pseudo_core_charge_density            |       38.99 ms →       32.64 ms  (-16.29%) |       1   →       1              |       38.99 ms →       32.64 ms  (-16.29%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |                        77.97 μs            |                   1              |                        77.97 μs            | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       28.85 ms →       24.10 ms  (-16.46%) |       1   →       1              |       28.85 ms →       24.10 ms  (-16.46%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        9.85 ms →        8.16 ms  (-17.16%) |       1   →       1              |        9.85 ms →        8.16 ms  (-17.16%) | 
  ├ sirius::Density::initial_density                                    |       61.83 ms →       56.01 ms   (-9.41%) |       1   →       1              |       61.83 ms →       56.01 ms   (-9.41%) | 
+ │ ├ sirius::Simulation_context::make_periodic_function                |       28.29 ms →       25.06 ms  (-11.41%) |       1   →       1              |       28.29 ms →       25.06 ms  (-11.41%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        7.10 ms →        6.40 ms   (-9.94%) |       2   →       2              |       14.21 ms →       12.79 ms   (-9.94%) | 
+ │ └ sirius::Periodic_function::integrate                              |        5.93 ms →        4.51 ms  (-24.05%) |       1   →       1              |        5.93 ms →        4.51 ms  (-24.05%) | 
  ├ sirius::Potential::generate                                         |      369.98 ms →      365.58 ms   (-1.19%) |       1   →       1              |      369.98 ms →      365.58 ms   (-1.19%) | 
+ │ ├ sirius::Potential::poisson                                        |       43.52 ms →       38.18 ms  (-12.28%) |       1   →       1              |       43.52 ms →       38.18 ms  (-12.28%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       12.06 ms →        9.06 ms  (-24.84%) |       1   →       1              |       12.06 ms →        9.06 ms  (-24.84%) | 
- │ │ └ sirius::Periodic_function|inner                                 |        4.98 ms →        6.09 ms  (+22.37%) |       1   →       1              |        4.98 ms →        6.09 ms  (+22.37%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.63 ms →        4.64 ms   (+0.19%) |       1   →       1              |        4.63 ms →        4.64 ms   (+0.19%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.63 ms →        4.63 ms   (+0.03%) |       1   →       1              |        4.63 ms →        4.63 ms   (+0.03%) | 
  │ ├ sirius::Periodic_function::add                                    |      796.49 μs →      785.56 μs   (-1.37%) |       2   →       2              |        1.59 ms →        1.57 ms   (-1.37%) | 
  │ ├ sirius::Potential::xc                                             |       50.80 ms →       51.99 ms   (+2.34%) |       1   →       1              |       50.80 ms →       51.99 ms   (+2.34%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       50.80 ms →       50.82 ms   (+0.04%) |       1   →       1              |       50.80 ms →       50.82 ms   (+0.04%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.55 ms →        2.55 ms   (+0.05%) |       2   →       2              |        5.10 ms →        5.10 ms   (+0.05%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.69 ms →        5.01 ms   (+6.82%) |       1   →       1              |        4.69 ms →        5.01 ms   (+6.82%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.58 ms →        3.70 ms   (+3.21%) |       1   →       1              |        3.58 ms →        3.70 ms   (+3.21%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      269.06 ms →      268.77 ms   (-0.11%) |       1   →       1              |      269.06 ms →      268.77 ms   (-0.11%) | 
- │ └ sirius::Potential::generate_PAW_effective_potential               |      198.00 ns →      326.00 ns  (+64.65%) |       1   →       1              |      198.00 ns →      326.00 ns  (+64.65%) | 
- ├ sirius::Hamiltonian0                                                |        7.50 ms →        8.62 ms  (+14.90%) |       1   →       1              |        7.50 ms →        8.62 ms  (+14.90%) | 
- │ ├ sirius::Local_operator                                            |        6.83 ms →        7.69 ms  (+12.61%) |       1   →       1              |        6.83 ms →        7.69 ms  (+12.61%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.74 ms →        2.74 ms   (-0.18%) |       1   →       1              |        2.74 ms →        2.74 ms   (-0.18%) | 
- │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        3.24 ms →        3.84 ms  (+18.53%) |       1   →       1              |        3.24 ms →        3.84 ms  (+18.53%) | 
- │ ├ sirius::Non_local_operator                                        |      171.45 μs →      330.35 μs  (+92.68%) |       2   →       2              |      342.90 μs →      660.69 μs  (+92.68%) | 
+ │ ├ sirius::D_operator::initialize                                    |      152.71 μs →      107.21 μs  (-29.79%) |       1   →       1              |      152.71 μs →      107.21 μs  (-29.79%) | 
  │ └ sirius::Q_operator::initialize                                    |       90.60 μs →       91.88 μs   (+1.41%) |       1   →       1              |       90.60 μs →       91.88 μs   (+1.41%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.29 s  →        1.28 s    (-0.95%) |       1   →       1              |        1.29 s  →        1.28 s    (-0.95%) | 
  │ ├ sirius::Hamiltonian_k                                             |       58.18 ms →       52.48 ms   (-9.79%) |       1   →       1              |       58.18 ms →       52.48 ms   (-9.79%) | 
+ │ │ ├ sirius::Local_operator::prepare_k                               |      275.02 μs →      215.61 μs  (-21.60%) |       1   →       1              |      275.02 μs →      215.61 μs  (-21.60%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       57.90 ms →       52.26 ms   (-9.73%) |       1   →       1              |       57.90 ms →       52.26 ms   (-9.73%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.23 s  →        1.22 s    (-0.53%) |       1   →       1              |        1.23 s  →        1.22 s    (-0.53%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       77.15 ms →       76.40 ms   (-0.97%) |       4   →       4              |      308.60 ms →      305.62 ms   (-0.97%) | 
+ │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       48.56 ms →       42.81 ms  (-11.84%) |       1   →       1              |       48.56 ms →       42.81 ms  (-11.84%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        7.92 ms →        8.63 ms   (+9.04%) |       1   →       1              |        7.92 ms →        8.63 ms   (+9.04%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      316.77 ms →      337.11 ms   (+6.42%) |       1   →       1              |      316.77 ms →      337.11 ms   (+6.42%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      247.57 ms →      250.27 ms   (+1.09%) |       1   →       1              |      247.57 ms →      250.27 ms   (+1.09%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        4.45 μs →        3.94 μs  (-11.27%) |       1   →       1              |        4.45 μs →        3.94 μs  (-11.27%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.38 μs →        2.88 μs  (-14.81%) |       1   →       1              |        3.38 μs →        2.88 μs  (-14.81%) | 
- │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      508.00 ns →      670.00 ns  (+31.89%) |       1   →       1              |      508.00 ns →      670.00 ns  (+31.89%) | 
- │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      760.00 ns →      861.00 ns  (+13.29%) |       1   →       1              |      760.00 ns →      861.00 ns  (+13.29%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.23 ms →        3.06 ms   (-5.10%) |       1   →       1              |        3.23 ms →        3.06 ms   (-5.10%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.32 ms →       21.25 ms   (-0.35%) |       1   →       1              |       21.32 ms →       21.25 ms   (-0.35%) | 
- │ │ │ └ sirius::Non_local_operator::apply                             |       22.30 ms →       31.24 ms  (+40.10%) |       2   →       2              |       44.60 ms →       62.48 ms  (+40.10%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.70 ms →       14.80 ms   (+0.68%) |       2   →       2              |       29.40 ms →       29.60 ms   (+0.68%) | 
  │ │ │ ├ sddk::inner                                                   |       14.49 ms                             |       2                          |       28.98 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       25.54 μs                             |       2                          |       51.08 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        14.59 ms            |                   2              |                        29.18 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        22.00 ns            |                   2              |                        44.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        14.47 ms            |                   2              |                        28.93 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                        23.00 ns            |                   2              |                        46.00 ns            | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      248.35 ms →      233.28 ms   (-6.07%) |       1   →       1              |      248.35 ms →      233.28 ms   (-6.07%) | 
  │ │ ├ sddk::transform                                                 |        2.82 ms                             |       1                          |        2.82 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       14.90 μs                             |       1                          |       14.90 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       18.34 μs                             |       1                          |       18.34 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                         2.62 ms            |                   1              |                         2.62 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                         2.61 ms            |                   1              |                         2.61 ms            | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      418.00 ns →      550.00 ns  (+31.58%) |       1   →       1              |      418.00 ns →      550.00 ns  (+31.58%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |       67.37 s  →       61.76 s    (-8.33%) |       1   →       1              |       67.37 s  →       61.76 s    (-8.33%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.43 ms →        2.46 ms   (+1.22%) |      19   →      19              |       46.15 ms →       46.71 ms   (+1.22%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.36 s  →        3.24 s    (-3.52%) |      20   →      19     (-5.00%) |       67.16 s  →       61.56 s    (-8.34%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        5.79 ms →        5.53 ms   (-4.48%) |      20   →      19     (-5.00%) |      115.83 ms →      105.11 ms   (-9.26%) | 
  │ │ │ ├ sirius::Local_operator                                        |        5.05 ms →        4.90 ms   (-2.91%) |      20   →      19     (-5.00%) |      101.03 ms →       93.18 ms   (-7.76%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      538.52 μs →      556.97 μs   (+3.43%) |      20   →      19     (-5.00%) |       10.77 ms →       10.58 ms   (-1.75%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.30 ms →        3.12 ms   (-5.40%) |      20   →      19     (-5.00%) |       66.04 ms →       59.35 ms  (-10.13%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |      227.14 μs →      175.44 μs  (-22.76%) |      40   →      38     (-5.00%) |        9.09 ms →        6.67 ms  (-26.62%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |      113.92 μs →      110.98 μs   (-2.58%) |      20   →      19     (-5.00%) |        2.28 ms →        2.11 ms   (-7.45%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       94.00 μs →       90.81 μs   (-3.39%) |      20   →      19     (-5.00%) |        1.88 ms →        1.73 ms   (-8.23%) | 
  │ │ ├ sirius::Band::solve                                             |        2.11 s  →        2.02 s    (-4.27%) |      20   →      19     (-5.00%) |       42.29 s  →       38.46 s    (-9.05%) | 
+ │ │ │ ├ sirius::Hamiltonian_k                                         |      215.40 μs →      197.07 μs   (-8.51%) |      20   →      19     (-5.00%) |        4.31 ms →        3.74 ms  (-13.08%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      205.99 μs →      187.31 μs   (-9.07%) |      20   →      19     (-5.00%) |        4.12 ms →        3.56 ms  (-13.61%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        7.45 μs →        6.95 μs   (-6.70%) |      20   →      19     (-5.00%) |      148.94 μs →      132.01 μs  (-11.36%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.96 s  →        1.96 s    (+0.16%) |      20   →      19     (-5.00%) |       39.16 s  →       37.27 s    (-4.84%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       96.02 ms →       79.44 ms  (-17.28%) |      20   →      19     (-5.00%) |        1.92 s  →        1.51 s   (-21.41%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |       11.34 ms →        8.41 ms  (-25.82%) |     120   →     114     (-5.00%) |        1.36 s  →      959.29 ms  (-29.53%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       17.48 ms →       15.53 ms  (-11.16%) |      20   →      19     (-5.00%) |      349.57 ms →      295.02 ms  (-15.60%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      466.59 μs →      492.89 μs   (+5.64%) |      20   →      19     (-5.00%) |        9.33 ms →        9.36 ms   (+0.36%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        8.31 ms →        7.08 ms  (-14.79%) |      40   →      38     (-5.00%) |      332.37 ms →      269.04 ms  (-19.05%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.84 s  →        1.86 s    (+1.11%) |      20   →      19     (-5.00%) |       36.76 s  →       35.31 s    (-3.94%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       60.96 ms →       55.02 ms   (-9.74%) |     250   →     356    (+42.40%) |       15.24 s  →       19.59 s   (+28.53%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       36.01 ms →       33.66 ms   (-6.53%) |     250   →     356    (+42.40%) |        9.00 s  →       11.98 s   (+33.10%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.05 μs →        1.83 μs  (-10.55%) |     250   →     356    (+42.40%) |      512.44 μs →      652.75 μs  (+27.38%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.68 μs →        1.57 μs   (-6.62%) |     250   →     356    (+42.40%) |      419.40 μs →      557.66 μs  (+32.97%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      499.99 ns →      365.78 ns  (-26.84%) |     250   →     356    (+42.40%) |      125.00 μs →      130.22 μs   (+4.18%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      518.65 ns →      496.28 ns   (-4.31%) |     250   →     356    (+42.40%) |      129.66 μs →      176.68 μs  (+36.26%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.85 ms →        2.82 ms   (-0.94%) |     250   →     356    (+42.40%) |      712.58 ms →        1.01 s   (+41.06%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.48 ms →        3.34 ms   (-4.16%) |     250   →     356    (+42.40%) |      870.21 ms →        1.19 s   (+36.47%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        9.30 ms →        7.60 ms  (-18.34%) |     500   →     712    (+42.40%) |        4.65 s  →        5.41 s   (+16.29%) | 
+ │ │ │ │   ├ sddk::orthogonalize                                       |        8.73 ms →        5.90 ms  (-32.33%) |     250   →     356    (+42.40%) |        2.18 s  →        2.10 s    (-3.64%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        1.20 ms                             |     480                          |      574.03 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       23.72 μs                             |     480                          |       11.39 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                         1.16 ms            |                 693              |                       806.71 ms            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                        56.38 ns            |                 693              |                        39.07 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                         1.00 ms            |                 693              |                       694.65 ms            | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                        45.28 ns            |                 693              |                        31.38 μs            | 
+ │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      183.38 μs →      129.76 μs  (-29.24%) |     250   →     356    (+42.40%) |       45.84 ms →       46.19 ms   (+0.76%) | 
+ │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        3.16 ms →        1.52 ms  (-51.97%) |     250   →     356    (+42.40%) |      789.83 ms →      540.25 ms  (-31.60%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        3.35 ms                             |     230                          |      770.59 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       19.55 μs                             |     230                          |        4.50 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |        7.98 μs                             |     690                          |        5.50 ms                             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                         2.10 ms            |                 337              |                       707.32 ms            | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                       698.89 μs            |                1.01 K            |                       706.58 ms            | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.95 ms →        1.34 ms  (-31.25%) |     250   →     356    (+42.40%) |      486.32 ms →      476.11 ms   (-2.10%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        1.74 ms                             |     250                          |      434.67 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       24.76 μs                             |     250                          |        6.19 ms                             | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                         1.27 ms            |                 356              |                       451.65 ms            | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                        46.64 ns            |                 356              |                        16.60 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                         1.11 ms            |                 356              |                       393.83 ms            | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                        38.60 ns            |                 356              |                        13.74 μs            | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       71.95 ms →       33.52 ms  (-53.42%) |     250   →     356    (+42.40%) |       17.99 s  →       11.93 s   (-33.67%) | 
- │ │ │ │   ├ sirius::residuals                                         |        2.82 ms →        2.49 ms  (-11.53%) |     245   →     340    (+38.78%) |      690.89 ms →      848.24 ms  (+22.77%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        1.78 ms                             |     231                          |      411.18 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       16.26 μs                             |     231                          |        3.76 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       10.85 μs                             |     462                          |        5.01 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                         1.21 ms            |                 337              |                       407.17 ms            | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                       602.77 μs            |                 674              |                       406.27 ms            | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.14 ms →        1.18 ms   (+3.87%) |     231   →     337    (+45.89%) |      262.25 ms →      397.41 ms  (+51.54%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        6.56 ms →        6.59 ms   (+0.47%) |      25   →      54   (+116.00%) |      163.99 ms →      355.90 ms (+117.02%) | 
  │ │ │ │     ├ sddk::transform                                         |        5.38 ms                             |      30                          |      161.48 ms                             | 
  │ │ │ │     │ ├ sddk::transform|init                                  |       10.64 μs                             |      30                          |      319.18 μs                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       12.06 μs                             |      35                          |      422.05 μs                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                         3.95 ms            |                  89              |                       351.70 ms            | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                         2.83 ms            |                 124              |                       351.53 ms            | 
  │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      414.65 ns →      395.16 ns   (-4.70%) |      20   →      19     (-5.00%) |        8.29 μs →        7.51 μs   (-9.47%) | 
+ │ │ │ └ sirius::K_point_set::sync_band_energies                       |       22.80 μs →       19.67 μs  (-13.72%) |      20   →      19     (-5.00%) |      456.05 μs →      373.81 μs  (-18.03%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.50 ms →        1.52 ms   (+1.03%) |      20   →      19     (-5.00%) |       30.01 ms →       28.81 ms   (-4.02%) | 
  │ │ ├ sirius::Density::generate                                       |      580.95 ms →      564.56 ms   (-2.82%) |      20   →      19     (-5.00%) |       11.62 s  →       10.73 s    (-7.68%) | 
+ │ │ │ ├ sirius::Density::generate_valence                             |      427.32 ms →      394.57 ms   (-7.66%) |      20   →      19     (-5.00%) |        8.55 s  →        7.50 s   (-12.28%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.20 μs →        8.00 μs   (-2.43%) |      20   →      19     (-5.00%) |      164.05 μs →      152.07 μs   (-7.30%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.50 μs →        7.46 μs   (-0.49%) |      20   →      19     (-5.00%) |      150.03 μs →      141.83 μs   (-5.47%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       35.56 ms →       39.74 ms  (+11.75%) |      20   →      19     (-5.00%) |      711.24 ms →      755.05 ms   (+6.16%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.73 μs →        7.16 μs   (-7.47%) |      20   →      19     (-5.00%) |      154.70 μs →      135.99 μs  (-12.09%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        5.66 ms →       22.65 ms (+300.39%) |      20   →      19     (-5.00%) |      113.12 ms →      430.26 ms (+280.37%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       28.87 ms →       16.02 ms  (-44.50%) |      20   →      19     (-5.00%) |      577.44 ms →      304.45 ms  (-47.28%) | 
  │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      504.55 ns →      537.84 ns   (+6.60%) |      20   →      19     (-5.00%) |       10.09 μs →       10.22 μs   (+1.27%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      110.28 ms →       99.41 ms   (-9.86%) |      20   →      19     (-5.00%) |        2.21 s  →        1.89 s   (-14.37%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.22 ms →        2.35 ms   (+5.68%) |      20   →      19     (-5.00%) |       44.39 ms →       44.57 ms   (+0.40%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |      246.47 ms →      210.17 ms  (-14.73%) |      20   →      19     (-5.00%) |        4.93 s  →        3.99 s   (-18.99%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |      246.26 ms →      209.95 ms  (-14.75%) |      20   →      19     (-5.00%) |        4.93 s  →        3.99 s   (-19.01%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      122.56 ms →      141.62 ms  (+15.56%) |      20   →      19     (-5.00%) |        2.45 s  →        2.69 s    (+9.78%) | 
- │ │ │ │ └ sirius::symmetrize_function|fpw                             |      122.56 ms →      141.62 ms  (+15.56%) |      20   →      19     (-5.00%) |        2.45 s  →        2.69 s    (+9.78%) | 
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       39.12 ms →       58.63 ms  (+49.88%) |      20   →      19     (-5.00%) |      782.36 ms →        1.11 s   (+42.38%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       68.12 ms →       69.66 ms   (+2.27%) |      20   →      19     (-5.00%) |        1.36 s  →        1.32 s    (-2.84%) | 
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       14.68 ms →       12.67 ms  (-13.68%) |      20   →      19     (-5.00%) |      293.62 ms →      240.77 ms  (-18.00%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.84 ms →       23.67 ms   (-0.74%) |      20   →      19     (-5.00%) |      476.87 ms →      449.66 ms   (-5.71%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        7.22 ms →        4.70 ms  (-34.99%) |      20   →      19     (-5.00%) |      144.44 ms →       89.21 ms  (-38.24%) | 
  │ │ ├ sirius::Density::mix                                            |      132.22 ms →      133.01 ms   (+0.60%) |      20   →      19     (-5.00%) |        2.64 s  →        2.53 s    (-4.43%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      940.23 μs →      937.17 μs   (-0.33%) |      20   →      19     (-5.00%) |       18.80 ms →       17.81 ms   (-5.31%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |        4.68 ms →        4.85 ms   (+3.61%) |     244   →     229     (-6.15%) |        1.14 s  →        1.11 s    (-2.76%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.64 ms →        4.81 ms   (+3.66%) |     244   →     229     (-6.15%) |        1.13 s  →        1.10 s    (-2.71%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.64 ms →        4.81 ms   (+3.66%) |     244   →     229     (-6.15%) |        1.13 s  →        1.10 s    (-2.71%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        5.35 ms →        5.46 ms   (+2.09%) |      20   →      19     (-5.00%) |      107.01 ms →      103.78 ms   (-3.02%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        4.71 ms →        4.70 ms   (-0.38%) |      20   →      19     (-5.00%) |       94.27 ms →       89.21 ms   (-5.36%) | 
  │ │ ├ sirius::Potential::generate                                     |      362.87 ms →      357.24 ms   (-1.55%) |      20   →      19     (-5.00%) |        7.26 s  →        6.79 s    (-6.47%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |       43.68 ms →       36.77 ms  (-15.80%) |      20   →      19     (-5.00%) |      873.54 ms →      698.72 ms  (-20.01%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       12.25 ms →        8.73 ms  (-28.74%) |      20   →      19     (-5.00%) |      244.96 ms →      165.83 ms  (-32.30%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |        4.98 ms →        4.98 ms   (-0.07%) |      20   →      19     (-5.00%) |       99.64 ms →       94.59 ms   (-5.07%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.63 ms →        4.63 ms   (+0.06%) |      20   →      19     (-5.00%) |       92.55 ms →       87.97 ms   (-4.95%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.63 ms →        4.63 ms   (+0.05%) |      20   →      19     (-5.00%) |       92.53 ms →       87.95 ms   (-4.95%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      823.45 μs →      780.20 μs   (-5.25%) |      40   →      38     (-5.00%) |       32.94 ms →       29.65 ms   (-9.99%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       43.67 ms →       45.39 ms   (+3.94%) |      20   →      19     (-5.00%) |      873.34 ms →      862.37 ms   (-1.26%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       43.66 ms →       44.20 ms   (+1.22%) |      20   →      19     (-5.00%) |      873.29 ms →      839.76 ms   (-3.84%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |      641.26 μs →      692.91 μs   (+8.05%) |      40   →      38     (-5.00%) |       25.65 ms →       26.33 ms   (+2.65%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.65 ms →        4.82 ms   (+3.54%) |      20   →      19     (-5.00%) |       93.02 ms →       91.50 ms   (-1.63%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.59 ms →        3.69 ms   (+2.73%) |      20   →      19     (-5.00%) |       71.90 ms →       70.17 ms   (-2.40%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.81 ms →      268.41 ms   (-0.15%) |      20   →      19     (-5.00%) |        5.38 s  →        5.10 s    (-5.14%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      219.25 ns →      339.95 ns  (+55.05%) |      20   →      19     (-5.00%) |        4.38 μs →        6.46 μs  (+47.30%) | 
+ │ │ ├ sirius::Field4D::symmetrize                                     |      101.64 ms →       96.15 ms   (-5.40%) |      20   →      19     (-5.00%) |        2.03 s  →        1.83 s   (-10.13%) | 
+ │ │ │ └ sirius::symmetrize_function|fpw                               |      101.64 ms →       96.15 ms   (-5.40%) |      20   →      19     (-5.00%) |        2.03 s  →        1.83 s   (-10.13%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       18.13 ms →       13.53 ms  (-25.33%) |      20   →      19     (-5.00%) |      362.51 ms →      257.14 ms  (-29.07%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       68.17 ms →       69.35 ms   (+1.74%) |      20   →      19     (-5.00%) |        1.36 s  →        1.32 s    (-3.34%) | 
+ │ │ │   └ sddk::Gvec_shells::remap_backward                           |       14.71 ms →       12.62 ms  (-14.21%) |      20   →      19     (-5.00%) |      294.28 ms →      239.83 ms  (-18.50%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        6.47 ms →        4.21 ms  (-34.97%) |      20   →      19     (-5.00%) |      129.45 ms →       79.97 ms  (-38.22%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.66 ms →        4.79 ms   (+2.76%) |     140   →     133     (-5.00%) |      652.81 ms →      637.26 ms   (-2.38%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.57 ms →        4.68 ms   (+2.27%) |     140   →     133     (-5.00%) |      640.48 ms →      622.28 ms   (-2.84%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.57 ms →        4.68 ms   (+2.27%) |     140   →     133     (-5.00%) |      640.38 ms →      622.18 ms   (-2.84%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.76 ms →        4.94 ms   (+3.85%) |      60   →      57     (-5.00%) |      285.64 ms →      281.80 ms   (-1.34%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.73 ms →        4.94 ms   (+4.34%) |      60   →      57     (-5.00%) |      283.89 ms →      281.41 ms   (-0.87%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.96 ms →        4.76 ms   (-3.94%) |      20   →      19     (-5.00%) |       99.16 ms →       90.48 ms   (-8.75%) | 
  │ │ └ sirius::Density::get_magnetisation                              |       74.35 μs →       78.24 μs   (+5.23%) |      20   →      19     (-5.00%) |        1.49 ms →        1.49 ms   (-0.03%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |       69.45 μs →       72.98 μs   (+5.08%) |      20   →      19     (-5.00%) |        1.39 ms →        1.39 ms   (-0.17%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.64 ms →        5.45 ms   (-3.47%) |       2   →       2              |       11.29 ms →       10.90 ms   (-3.47%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.57 ms →        4.58 ms   (+0.30%) |       6   →       6              |       27.42 ms →       27.50 ms   (+0.30%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.57 ms →        4.57 ms   (+0.20%) |       6   →       6              |       27.39 ms →       27.45 ms   (+0.20%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.56 ms →        4.57 ms   (+0.17%) |       6   →       6              |       27.39 ms →       27.43 ms   (+0.17%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.76 ms →        5.00 ms   (+5.08%) |       3   →       3              |       14.28 ms →       15.00 ms   (+5.08%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.74 ms →        5.00 ms   (+5.49%) |       3   →       3              |       14.21 ms →       14.99 ms   (+5.49%) | 
  ├ sirius::Periodic_function|inner                                     |        4.54 ms →        4.53 ms   (-0.17%) |       2   →       2              |        9.08 ms →        9.07 ms   (-0.17%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.54 ms →        4.53 ms   (-0.11%) |       2   →       2              |        9.07 ms →        9.06 ms   (-0.11%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.54 ms →        4.53 ms   (-0.10%) |       2   →       2              |        9.07 ms →        9.06 ms   (-0.10%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.73 ms →        4.92 ms   (+4.05%) |       1   →       1              |        4.73 ms →        4.92 ms   (+4.05%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.71 ms →        4.91 ms   (+4.20%) |       1   →       1              |        4.71 ms →        4.91 ms   (+4.20%) | 
+ └ sirius::finalize                                                    |      936.33 ms →      165.81 ms  (-82.29%) |       1   →       1              |      936.33 ms →      165.81 ms  (-82.29%) | 
  ====================================================================================================================================================================================================
```
