# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs 8d4c8fb637741d881d5cdc9faf167adefd93fb67
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      862.64 s  →      295.11 s   (-65.79%) |       1   →       1              |      862.64 s  →      295.11 s   (-65.79%) | 
  ├ sirius::initialize                                                  |        2.77 s  →        2.80 s    (+1.16%) |       1   →       1              |        2.77 s  →        2.80 s    (+1.16%) | 
  ├ sirius::Simulation_context::initialize                              |        2.86 s  →        2.88 s    (+0.68%) |       1   →       1              |        2.86 s  →        2.88 s    (+0.68%) | 
- │ ├ sirius::Simulation_context::init_comm                             |      211.38 μs →      245.84 μs  (+16.31%) |       1   →       1              |      211.38 μs →      245.84 μs  (+16.31%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      124.24 ms →      140.50 ms  (+13.08%) |       1   →       1              |      124.24 ms →      140.50 ms  (+13.08%) | 
- │ │ ├ sirius::Atom_type::init                                         |       49.35 ms →       58.20 ms  (+17.94%) |       2   →       2              |       98.69 ms →      116.40 ms  (+17.94%) | 
  │ │ └ sirius::Unit_cell::update                                       |       25.48 ms →       23.90 ms   (-6.17%) |       1   →       1              |       25.48 ms →       23.90 ms   (-6.17%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.40 ms →        6.25 ms   (-2.27%) |       1   →       1              |        6.40 ms →        6.25 ms   (-2.27%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       19.04 ms →       17.61 ms   (-7.50%) |       1   →       1              |       19.04 ms →       17.61 ms   (-7.50%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       19.02 ms →       17.59 ms   (-7.52%) |       1   →       1              |       19.02 ms →       17.59 ms   (-7.52%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        5.35 ms →        5.20 ms   (-2.86%) |       1   →       1              |        5.35 ms →        5.20 ms   (-2.86%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.34 ms →        2.35 ms   (+0.56%) |       1   →       1              |        2.34 ms →        2.35 ms   (+0.56%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      103.47 μs →      101.63 μs   (-1.78%) |       1   →       1              |      103.47 μs →      101.63 μs   (-1.78%) | 
  │ └ sirius::Simulation_context::update                                |        2.69 s  →        2.69 s    (+0.03%) |       1   →       1              |        2.69 s  →        2.69 s    (+0.03%) | 
  │   ├ sirius::Unit_cell::update                                       |       11.88 ms →       11.87 ms   (-0.10%) |       1   →       1              |       11.88 ms →       11.87 ms   (-0.10%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.28 ms →        4.49 ms   (+4.71%) |       1   →       1              |        4.28 ms →        4.49 ms   (+4.71%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        7.56 ms →        7.35 ms   (-2.84%) |       1   →       1              |        7.56 ms →        7.35 ms   (-2.84%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        7.54 ms →        7.33 ms   (-2.90%) |       1   →       1              |        7.54 ms →        7.33 ms   (-2.90%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        5.05 ms →        4.82 ms   (-4.47%) |       1   →       1              |        5.05 ms →        4.82 ms   (-4.47%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.34 ms   (+0.43%) |       1   →       1              |        2.33 ms →        2.34 ms   (+0.43%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      103.73 μs →       99.58 μs   (-4.01%) |       1   →       1              |      103.73 μs →       99.58 μs   (-4.01%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       64.91 ms →       64.59 ms   (-0.50%) |       2   →       2              |      129.83 ms →      129.18 ms   (-0.50%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.13 ms →        5.24 ms   (+2.03%) |       2   →       2              |       10.26 ms →       10.47 ms   (+2.03%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.58 ms →        4.88 ms   (+6.67%) |       1   →       1              |        4.58 ms →        4.88 ms   (+6.67%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.76 ms →       21.80 ms   (+0.18%) |       2   →       2              |       43.52 ms →       43.60 ms   (+0.18%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.76 ms →       14.75 ms   (-0.07%) |       2   →       2              |       29.53 ms →       29.51 ms   (-0.07%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.78 ms →       19.57 ms   (-1.09%) |       4   →       4              |       79.14 ms →       78.27 ms   (-1.09%) | 
  │   ├ sddk::Gvec::init                                                |      172.58 ms →      173.57 ms   (+0.57%) |       2   →       2              |      345.15 ms →      347.13 ms   (+0.57%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      130.23 ms →      130.97 ms   (+0.57%) |       2   →       2              |      260.45 ms →      261.94 ms   (+0.57%) | 
  │   ├ sddk::Gvec_shells                                               |      179.38 ms →      181.21 ms   (+1.02%) |       1   →       1              |      179.38 ms →      181.21 ms   (+1.02%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.31 ms →        1.33 ms   (+1.08%) |       1   →       1              |        1.31 ms →        1.33 ms   (+1.08%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      291.71 ms →      293.38 ms   (+0.57%) |       2   →       2              |      583.41 ms →      586.75 ms   (+0.57%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       77.74 ms →       75.49 ms   (-2.90%) |       1   →       1              |       77.74 ms →       75.49 ms   (-2.90%) | 
- │ ├ sirius::K_point::K_point                                          |        3.08 μs →        6.46 μs (+109.96%) |       4   →       4              |       12.30 μs →       25.84 μs (+109.96%) | 
  │ └ sirius::K_point_set::initialize                                   |       77.65 ms →       75.33 ms   (-2.98%) |       1   →       1              |       77.65 ms →       75.33 ms   (-2.98%) | 
  │   └ sirius::K_point::initialize                                     |       19.40 ms →       18.82 ms   (-2.99%) |       4   →       4              |       77.60 ms →       75.28 ms   (-2.99%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       14.81 ms →       14.25 ms   (-3.76%) |       4   →       4              |       59.22 ms →       56.99 ms   (-3.76%) | 
  │     │ └ sddk::Gvec::init                                            |        3.86 ms →        3.88 ms   (+0.45%) |       4   →       4              |       15.46 ms →       15.53 ms   (+0.45%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        8.80 μs                             |       4                          |       35.21 μs                             | 
  │     └ sirius::K_point::update                                       |        3.30 ms →        3.26 ms   (-1.11%) |       4   →       4              |       13.20 ms →       13.05 ms   (-1.11%) | 
  │       └ sirius::Beta_projectors                                     |        1.78 ms →        1.77 ms   (-0.72%) |       4   →       4              |        7.11 ms →        7.06 ms   (-0.72%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      926.21 μs →      937.03 μs   (+1.17%) |       4   →       4              |        3.70 ms →        3.75 ms   (+1.17%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.28 ms                             |       2                          |       10.56 ms                             | 
  ├ sirius::Potential                                                   |      171.68 ms →      158.13 ms   (-7.90%) |       1   →       1              |      171.68 ms →      158.13 ms   (-7.90%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.77 ms                             |       6                          |       34.61 ms                             | 
  │ └ sirius::Potential::update                                         |      136.35 ms →      128.42 ms   (-5.82%) |       1   →       1              |      136.35 ms →      128.42 ms   (-5.82%) | 
  │   └ sirius::Potential::generate_local_potential                     |      135.60 ms →      127.70 ms   (-5.83%) |       1   →       1              |      135.60 ms →      127.70 ms   (-5.83%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      112.54 ms →      108.47 ms   (-3.61%) |       1   →       1              |      112.54 ms →      108.47 ms   (-3.61%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       22.52 ms →       12.63 ms  (-43.90%) |       1   →       1              |       22.52 ms →       12.63 ms  (-43.90%) | 
  ├ sirius::Density                                                     |      141.08 ms →      136.06 ms   (-3.56%) |       1   →       1              |      141.08 ms →      136.06 ms   (-3.56%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.13 ms                             |       2                          |       10.27 ms                             | 
  │ └ sirius::Density::update                                           |      130.55 ms →      125.65 ms   (-3.75%) |       1   →       1              |      130.55 ms →      125.65 ms   (-3.75%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      130.08 ms →      125.24 ms   (-3.72%) |       1   →       1              |      130.08 ms →      125.24 ms   (-3.72%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      113.24 ms →      109.97 ms   (-2.89%) |       1   →       1              |      113.24 ms →      109.97 ms   (-2.89%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       16.40 ms →       13.08 ms  (-20.22%) |       1   →       1              |       16.40 ms →       13.08 ms  (-20.22%) | 
  ├ sirius::Density::initial_density                                    |      176.15 ms →      173.76 ms   (-1.36%) |       1   →       1              |      176.15 ms →      173.76 ms   (-1.36%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      111.49 ms →      108.65 ms   (-2.54%) |       1   →       1              |      111.49 ms →      108.65 ms   (-2.54%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |       10.75 ms →        8.96 ms  (-16.69%) |       2   →       2              |       21.50 ms →       17.91 ms  (-16.69%) | 
- │ └ sirius::Periodic_function::integrate                              |        9.80 ms →       10.86 ms  (+10.76%) |       1   →       1              |        9.80 ms →       10.86 ms  (+10.76%) | 
  ├ sirius::Potential::generate                                         |      705.39 ms →      682.92 ms   (-3.19%) |       1   →       1              |      705.39 ms →      682.92 ms   (-3.19%) | 
  │ ├ sirius::Potential::poisson                                        |      137.22 ms →      138.08 ms   (+0.62%) |       1   →       1              |      137.22 ms →      138.08 ms   (+0.62%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       16.44 ms →       19.66 ms  (+19.55%) |       1   →       1              |       16.44 ms →       19.66 ms  (+19.55%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.70 ms                             |       1                          |       10.70 ms                             | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |       10.30 ms                             |       1                          |       10.30 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |       10.30 ms                             |       1                          |       10.30 ms                             | 
  │ │ └ sirius::inner                                                   |                        11.14 ms            |                   1              |                        11.14 ms            | 
+ │ ├ sirius::Periodic_function::add                                    |      546.74 μs →      457.86 μs  (-16.26%) |       2   →       2              |        1.09 ms →      915.72 μs  (-16.26%) | 
+ │ ├ sirius::Potential::xc                                             |       57.99 ms →       40.08 ms  (-30.89%) |       1   →       1              |       57.99 ms →       40.08 ms  (-30.89%) | 
+ │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       57.98 ms →       37.77 ms  (-34.86%) |       1   →       1              |       57.98 ms →       37.77 ms  (-34.86%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.68 ms                             |       2                          |       11.35 ms                             | 
  │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        5.23 ms                             |       1                          |        5.23 ms                             | 
  │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                    |                        12.09 ms            |                   2              |                        24.19 ms            | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.75 ms →        4.87 ms  (-15.27%) |       1   →       1              |        5.75 ms →        4.87 ms  (-15.27%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.62 ms →       93.34 ms   (+0.77%) |       1   →       1              |       92.62 ms →       93.34 ms   (+0.77%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      409.34 ms →      401.70 ms   (-1.87%) |       1   →       1              |      409.34 ms →      401.70 ms   (-1.87%) | 
- ├ sirius::Hamiltonian0                                                |        8.45 ms →       11.80 ms  (+39.67%) |       1   →       1              |        8.45 ms →       11.80 ms  (+39.67%) | 
  │ ├ sirius::Local_operator                                            |        8.11 ms →        8.03 ms   (-1.04%) |       1   →       1              |        8.11 ms →        8.03 ms   (-1.04%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.74 ms                             |       1                          |        4.74 ms                             | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.44 ms →        2.42 ms   (-0.74%) |       1   →       1              |        2.44 ms →        2.42 ms   (-0.74%) | 
  │ ├ sirius::Non_local_operator                                        |       62.38 μs →       63.77 μs   (+2.22%) |       2   →       2              |      124.76 μs →      127.53 μs   (+2.22%) | 
- │ ├ sirius::D_operator::initialize                                    |       91.56 μs →        1.26 ms (+1273.01%) |       1   →       1              |       91.56 μs →        1.26 ms (+1273.01%) | 
- │ └ sirius::Q_operator::initialize                                    |       69.29 μs →        2.33 ms (+3267.07%) |       1   →       1              |       69.29 μs →        2.33 ms (+3267.07%) | 
  ├ sirius::Band::initialize_subspace                                   |        4.02 s  →        3.97 s    (-1.41%) |       1   →       1              |        4.02 s  →        3.97 s    (-1.41%) | 
- │ ├ sirius::Hamiltonian_k                                             |      206.74 μs →      389.70 μs  (+88.50%) |       4   →       4              |      826.97 μs →        1.56 ms  (+88.50%) | 
- │ │ ├ sirius::Local_operator::prepare_k                               |      201.72 μs →      382.43 μs  (+89.59%) |       4   →       4              |      806.88 μs →        1.53 ms  (+89.59%) | 
+ │ │ └ sirius::Beta_projectors_base::prepare                           |        3.55 μs →        3.16 μs  (-11.07%) |       4   →       4              |       14.20 μs →       12.63 μs  (-11.07%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.01 s  →      990.53 ms   (-1.47%) |       4   →       4              |        4.02 s  →        3.96 s    (-1.47%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       32.13 ms                             |      16                          |      514.00 ms                             | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       14.51 ms →       14.69 ms   (+1.28%) |       4   →       4              |       58.02 ms →       58.77 ms   (+1.28%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        5.28 ms →        5.39 ms   (+2.16%) |       4   →       4              |       21.12 ms →       21.58 ms   (+2.16%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      356.81 ms →      354.76 ms   (-0.57%) |       4   →       4              |        1.43 s  →        1.42 s    (-0.57%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      260.00 ms →      258.49 ms   (-0.58%) |       4   →       4              |        1.04 s  →        1.03 s    (-0.58%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       66.60 ms →       63.42 ms   (-4.78%) |       4   →       4              |      266.40 ms →      253.68 ms   (-4.78%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       16.06 ms                             |       4                          |       64.23 ms                             | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       16.06 ms                             |       4                          |       64.22 ms                             | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       44.20 ms →       40.49 ms   (-8.39%) |       4   →       4              |      176.80 ms →      161.98 ms   (-8.39%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |       16.25 ms                             |       4                          |       64.98 ms                             | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |       16.24 ms                             |       4                          |       64.97 ms                             | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |       52.75 ms →       54.55 ms   (+3.40%) |       4   →       4              |      211.02 ms →      218.20 ms   (+3.40%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |       34.72 ms →       36.50 ms   (+5.12%) |       4   →       4              |      138.89 ms →      146.00 ms   (+5.12%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        1.95 ms →        1.95 ms   (-0.21%) |       4   →       4              |        7.80 ms →        7.79 ms   (-0.21%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       40.48 ms →       40.01 ms   (-1.15%) |       4   →       4              |      161.92 ms →      160.06 ms   (-1.15%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |        7.32 ms →        6.94 ms   (-5.17%) |       4   →       4              |       29.29 ms →       27.78 ms   (-5.17%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       27.17 ms →       27.13 ms   (-0.13%) |       8   →       8              |      217.36 ms →      217.07 ms   (-0.13%) | 
- │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.37 ms →       16.01 ms  (+11.39%) |       8   →       8              |      114.98 ms →      128.07 ms  (+11.39%) | 
  │ │ │ ├ sddk::inner                                                   |       14.32 ms                             |       8                          |      114.56 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       54.27 μs                             |       8                          |      434.20 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        15.96 ms            |                   8              |                       127.69 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                       109.00 ns            |                   8              |                       872.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        15.68 ms            |                   8              |                       125.42 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                       329.63 ns            |                   8              |                         2.64 μs            | 
  │ │ ├ Eigensolver_scalapack|pzhegvx                                   |      350.29 ms →      321.80 ms   (-8.13%) |       4   →       4              |        1.40 s  →        1.29 s    (-8.13%) | 
  │ │ ├ sddk::transform                                                 |       27.88 ms                             |       4                          |      111.51 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       34.43 μs                             |       4                          |      137.71 μs                             | 
  │ │ │ ├ sddk::transform|mpi                                           |        1.35 ms                             |       4                          |        5.42 ms                             | 
  │ │ │ └ sddk::transform|local                                         |       23.75 μs                             |       4                          |       95.02 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                        27.98 ms            |                   4              |                       111.92 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                        27.83 ms            |                   4              |                       111.31 ms            | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      421.75 ns →      376.50 ns  (-10.73%) |       4   →       4              |        1.69 μs →        1.51 μs  (-10.73%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      850.75 s  →      283.34 s   (-66.70%) |       1   →       1              |      850.75 s  →      283.34 s   (-66.70%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.86 ms                             |      19                          |      111.39 ms                             | 
  │ ├ sirius::Density                                                   |                       138.95 ms            |                   1              |                       138.95 ms            | 
  │ │ └ sirius::Density::update                                         |                       128.31 ms            |                   1              |                       128.31 ms            | 
  │ │   └ sirius::Density::generate_pseudo_core_charge_density          |                       127.88 ms            |                   1              |                       127.88 ms            | 
  │ │     ├ sirius::Simulation_context::make_periodic_function          |                       111.10 ms            |                   1              |                       111.10 ms            | 
  │ │     └ sirius::Smooth_periodic_function::fft_transform             |                        12.45 ms            |                   1              |                        12.45 ms            | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |       18.90 s  →       11.31 s   (-40.15%) |      45   →      25    (-44.44%) |      850.40 s  →      282.76 s   (-66.75%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        4.51 ms →        7.88 ms  (+74.61%) |      45   →      25    (-44.44%) |      203.09 ms →      197.01 ms   (-2.99%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        4.16 ms →        4.08 ms   (-1.81%) |      45   →      25    (-44.44%) |      187.15 ms →      102.10 ms  (-45.45%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      968.13 μs                             |      45                          |       43.57 ms                             | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.30 ms →        2.22 ms   (-3.58%) |      45   →      25    (-44.44%) |      103.66 ms →       55.53 ms  (-46.43%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |       64.70 μs →       64.51 μs   (-0.30%) |      90   →      50    (-44.44%) |        5.82 ms →        3.23 ms  (-44.61%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |       90.87 μs →        1.23 ms (+1255.31%) |      45   →      25    (-44.44%) |        4.09 ms →       30.79 ms (+652.95%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       70.07 μs →        2.37 ms (+3287.13%) |      45   →      25    (-44.44%) |        3.15 ms →       59.34 ms (+1781.74%) | 
+ │ │ ├ sirius::Band::solve                                             |       16.67 s  →        9.18 s   (-44.90%) |      45   →      25    (-44.44%) |      750.06 s  →      229.58 s   (-69.39%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      206.66 μs →      324.80 μs  (+57.17%) |     180   →     100    (-44.44%) |       37.20 ms →       32.48 ms  (-12.69%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      200.55 μs →      317.70 μs  (+58.42%) |     180   →     100    (-44.44%) |       36.10 ms →       31.77 ms  (-11.99%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.71 μs →        3.84 μs  (-18.48%) |     180   →     100    (-44.44%) |      847.47 μs →      383.80 μs  (-54.71%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        4.17 s  →        2.30 s   (-44.91%) |     180   →     100    (-44.44%) |      750.02 s  →      229.54 s   (-69.39%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       14.80 ms                             |     180                          |        2.66 s                              | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |      469.01 μs                             |    1.08 K                        |      506.53 ms                             | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.84 ms →        1.83 ms   (-0.89%) |     180   →     100    (-44.44%) |      331.53 ms →      182.54 ms  (-44.94%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      355.29 μs                             |     180                          |       63.95 ms                             | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      545.33 μs                             |     360                          |      196.32 ms                             | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|iter           |        4.14 s                              |     180                          |      745.40 s                              | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::apply_h_s                          |       83.47 ms                             |     897                          |       74.87 s                              | 
  │ │ │ │ │ │ ├ sirius::Local_operator::apply_h                         |       53.59 ms                             |     897                          |       48.07 s                              | 
  │ │ │ │ │ │ │ ├ sddk::matrix_storage::remap_forward                   |        9.81 ms                             |     897                          |        8.80 s                              | 
  │ │ │ │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                 |       58.96 μs                             |     897                          |       52.89 ms                             | 
  │ │ │ │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |      283.87 μs                             |     180                          |       51.10 ms                             | 
  │ │ │ │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |        8.12 ms                             |     897                          |        7.28 s                              | 
  │ │ │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                   |       60.40 μs                             |     897                          |       54.18 ms                             | 
  │ │ │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |      289.17 μs                             |     180                          |       52.05 ms                             | 
  │ │ │ │ │ │ │ └ sddk::matrix_storage::remap_backward                  |       11.62 ms                             |     897                          |       10.42 s                              | 
  │ │ │ │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi            |        7.12 ms                             |     897                          |        6.38 s                              | 
  │ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                  |        1.56 ms                             |     897                          |        1.40 s                              | 
  │ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                     |       10.68 ms                             |     897                          |        9.58 s                              | 
  │ │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm              |        1.67 ms                             |     897                          |        1.50 s                              | 
  │ │ │ │ │ │ └ sirius::Non_local_operator::apply                       |        8.81 ms                             |    1.79 K                        |       15.81 s                              | 
  │ │ │ │ │ ├ sddk::orthogonalize                                       |       23.32 ms                             |     897                          |       20.92 s                              | 
  │ │ │ │ │ │ ├ sddk::inner                                             |        2.60 ms                             |    1.61 K                        |        4.20 s                              | 
  │ │ │ │ │ │ │ └ sddk::inner|local                                     |       32.96 μs                             |    1.77 K                        |       58.31 ms                             | 
  │ │ │ │ │ │ ├ sddk::orthogonalize|potrf                               |        1.29 ms                             |     897                          |        1.16 s                              | 
  │ │ │ │ │ │ ├ sddk::orthogonalize|trtri                               |        2.04 ms                             |     897                          |        1.83 s                              | 
  │ │ │ │ │ │ └ sddk::transform                                         |        3.49 ms                             |    3.41 K                        |       11.91 s                              | 
  │ │ │ │ │ │   ├ sddk::transform|init                                  |       13.96 μs                             |    3.41 K                        |       47.58 ms                             | 
  │ │ │ │ │ │   ├ sddk::transform|mpi                                   |      200.27 μs                             |    3.41 K                        |      682.51 ms                             | 
  │ │ │ │ │ │   └ sddk::transform|local                                 |       10.40 μs                             |    4.84 K                        |       50.38 ms                             | 
  │ │ │ │ │ ├ sirius::Band::set_subspace_mtrx                           |        6.53 ms                             |     897                          |        5.86 s                              | 
  │ │ │ │ │ │ └ sddk::inner                                             |        4.79 ms                             |     897                          |        4.29 s                              | 
  │ │ │ │ │ │   └ sddk::inner|local                                     |       28.40 μs                             |    1.09 K                        |       30.87 ms                             | 
  │ │ │ │ │ ├ Eigensolver_scalapack|pzheevx                             |      705.18 ms                             |     897                          |      632.54 s                              | 
  │ │ │ │ │ ├ sirius::residuals                                         |        9.00 ms                             |     885                          |        7.97 s                              | 
  │ │ │ │ │ │ ├ sddk::transform                                         |        8.14 ms                             |     823                          |        6.70 s                              | 
  │ │ │ │ │ │ │ ├ sddk::transform|init                                  |       24.02 μs                             |     823                          |       19.77 ms                             | 
  │ │ │ │ │ │ │ ├ sddk::transform|mpi                                   |      347.75 μs                             |     823                          |      286.20 ms                             | 
  │ │ │ │ │ │ │ └ sddk::transform|local                                 |       15.19 μs                             |    1.65 K                        |       25.00 ms                             | 
  │ │ │ │ │ │ └ sirius::normalized_preconditioned_residuals             |        1.01 ms                             |     823                          |      830.65 ms                             | 
  │ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       16.98 ms                             |     188                          |        3.19 s                              | 
  │ │ │ │ │   └ sddk::transform                                         |       16.24 ms                             |     196                          |        3.18 s                              | 
  │ │ │ │ │     ├ sddk::transform|init                                  |       19.60 μs                             |     196                          |        3.84 ms                             | 
  │ │ │ │ │     ├ sddk::transform|mpi                                   |        1.17 ms                             |     196                          |      228.50 ms                             | 
  │ │ │ │ │     └ sddk::transform|local                                 |       17.02 μs                             |     204                          |        3.47 ms                             | 
  │ │ │ │ ├ sirius::Hamiltonian_k::apply_h_s                            |                        64.86 ms            |                 916              |                        59.41 s             | 
  │ │ │ │ │ ├ sirius::Local_operator::apply_h                           |                        41.23 ms            |                 916              |                        37.76 s             | 
  │ │ │ │ │ │ ├ sddk::matrix_storage::remap_forward                     |                         8.33 ms            |                 916              |                         7.63 s             | 
  │ │ │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi               |                         6.41 ms            |                 916              |                         5.87 s             | 
  │ │ │ │ │ │ └ sddk::matrix_storage::remap_backward                    |                         8.96 ms            |                 916              |                         8.20 s             | 
  │ │ │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi              |                         5.64 ms            |                 916              |                         5.16 s             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |                         1.51 ms            |                 916              |                         1.38 s             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |                         7.97 ms            |                 916              |                         7.30 s             | 
  │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |                         1.19 ms            |                 916              |                         1.09 s             | 
  │ │ │ │ │ └ sirius::Non_local_operator::apply                         |                         7.06 ms            |                1.83 K            |                        12.94 s             | 
  │ │ │ │ ├ sddk::orthogonalize                                         |                        27.18 ms            |                 916              |                        24.90 s             | 
  │ │ │ │ │ ├ sddk::wf_inner                                            |                         1.73 ms            |                1.73 K            |                         2.99 s             | 
  │ │ │ │ │ │ ├ sddk::wf_inner|scale                                    |                       106.82 ns            |                1.73 K            |                       185.02 μs            | 
  │ │ │ │ │ │ ├ sddk::wf_inner|pw                                       |                         1.70 ms            |                1.73 K            |                         2.94 s             | 
  │ │ │ │ │ │ └ sddk::wf_inner|scale_back                               |                       301.27 ns            |                1.73 K            |                       521.79 μs            | 
  │ │ │ │ │ ├ sddk::orthogonalize|potrf                                 |                       830.93 μs            |                 916              |                       761.14 ms            | 
  │ │ │ │ │ ├ sddk::orthogonalize|trtri                                 |                         1.30 ms            |                 916              |                         1.19 s             | 
  │ │ │ │ │ └ sddk::wf_trans                                            |                         5.22 ms            |                3.56 K            |                        18.60 s             | 
  │ │ │ │ │   └ sddk::wf_trans|pw                                       |                         3.56 ms            |                5.20 K            |                        18.48 s             | 
  │ │ │ │ ├ sirius::Band::set_subspace_mtrx                             |                         3.79 ms            |                 916              |                         3.47 s             | 
  │ │ │ │ │ └ sddk::wf_inner                                            |                         3.10 ms            |                 916              |                         2.84 s             | 
  │ │ │ │ │   ├ sddk::wf_inner|scale                                    |                       100.23 ns            |                 916              |                        91.81 μs            | 
  │ │ │ │ │   ├ sddk::wf_inner|pw                                       |                         3.08 ms            |                 916              |                         2.82 s             | 
  │ │ │ │ │   └ sddk::wf_inner|scale_back                               |                       293.97 ns            |                 916              |                       269.28 μs            | 
  │ │ │ │ ├ Eigensolver_scalapack|pzheevx                               |                       131.96 ms            |                 916              |                       120.87 s             | 
  │ │ │ │ ├ sirius::residuals                                           |                         7.38 ms            |                 900              |                         6.64 s             | 
  │ │ │ │ │ ├ sddk::wf_trans                                            |                         6.95 ms            |                 816              |                         5.67 s             | 
  │ │ │ │ │ │ └ sddk::wf_trans|pw                                       |                         3.45 ms            |                1.63 K            |                         5.64 s             | 
  │ │ │ │ │ └ sirius::normalized_preconditioned_residuals               |                       533.26 μs            |                 816              |                       435.14 ms            | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|update_phi     |                        35.41 ms            |                 335              |                        11.86 s             | 
  │ │ │ │   └ sddk::wf_trans                                            |                        20.69 ms            |                 570              |                        11.79 s             | 
  │ │ │ │     └ sddk::wf_trans|pw                                       |                        14.59 ms            |                 805              |                        11.75 s             | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      512.38 ns →      502.50 ns   (-1.93%) |     180   →     100    (-44.44%) |       92.23 μs →       50.25 μs  (-45.52%) | 
  │ │ │ ├ sirius::K_point_set::sync_band_energies                       |       20.63 μs                             |      45                          |      928.14 μs                             | 
  │ │ │ └ sirius::K_point_set::sync_band                                |                       247.78 μs            |                  25              |                         6.19 ms            | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |      584.67 μs →      750.70 μs  (+28.40%) |      45   →      25    (-44.44%) |       26.31 ms →       18.77 ms  (-28.67%) | 
  │ │ │ └ sirius::K_point_set::sync_band                                |                        23.22 μs            |                  25              |                       580.59 μs            | 
+ │ │ ├ sirius::Density::generate                                       |      894.17 ms →      874.88 ms   (-2.16%) |      45   →      25    (-44.44%) |       40.24 s  →       21.87 s   (-45.64%) | 
+ │ │ │ ├ sirius::Density::generate_valence                             |      521.45 ms →      527.07 ms   (+1.08%) |      45   →      25    (-44.44%) |       23.47 s  →       13.18 s   (-43.85%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       23.48 ms →       24.38 ms   (+3.83%) |     180   →     100    (-44.44%) |        4.23 s  →        2.44 s   (-42.32%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |        7.66 μs                             |     180                          |        1.38 ms                             | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       14.70 μs                             |       8                          |      117.61 μs                             | 
+ │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       19.45 ms →       20.32 ms   (+4.49%) |     180   →     100    (-44.44%) |        3.50 s  →        2.03 s   (-41.95%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       30.04 ms →       29.70 ms   (-1.14%) |     180   →     100    (-44.44%) |        5.41 s  →        2.97 s   (-45.08%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.15 μs →        9.79 μs   (+6.93%) |     180   →     100    (-44.44%) |        1.65 ms →      978.93 μs  (-40.59%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        1.46 ms →        1.45 ms   (-0.54%) |     180   →     100    (-44.44%) |      262.38 ms →      144.98 ms  (-44.74%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       28.11 ms →       27.72 ms   (-1.39%) |     180   →     100    (-44.44%) |        5.06 s  →        2.77 s   (-45.21%) | 
+ │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        3.94 ms →        3.69 ms   (-6.13%) |     180   →     100    (-44.44%) |      708.53 ms →      369.48 ms  (-47.85%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      511.04 ns →      588.57 ns  (+15.17%) |     180   →     100    (-44.44%) |       91.99 μs →       58.86 μs  (-36.02%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       42.69 ms →       42.78 ms   (+0.20%) |     180   →     100    (-44.44%) |        7.68 s  →        4.28 s   (-44.33%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.65 ms →        1.65 ms   (+0.02%) |      45   →      25    (-44.44%) |       74.10 ms →       41.18 ms  (-44.43%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |       88.27 ms →       89.02 ms   (+0.86%) |      45   →      25    (-44.44%) |        3.97 s  →        2.23 s   (-43.97%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.04 ms →       88.78 ms   (+0.84%) |      45   →      25    (-44.44%) |        3.96 s  →        2.22 s   (-43.98%) | 
+ │ │ │ ├ sirius::Field4D::symmetrize                                   |      278.18 ms →      255.06 ms   (-8.31%) |      45   →      25    (-44.44%) |       12.52 s  →        6.38 s   (-49.06%) | 
+ │ │ │ │ └ sirius::symmetrize_function|fpw                             |      278.18 ms →      255.05 ms   (-8.32%) |      45   →      25    (-44.44%) |       12.52 s  →        6.38 s   (-49.06%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.11 ms →       24.63 ms   (+2.17%) |      45   →      25    (-44.44%) |        1.08 s  →      615.81 ms  (-43.24%) | 
+ │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      228.31 ms →      205.75 ms   (-9.88%) |      45   →      25    (-44.44%) |       10.27 s  →        5.14 s   (-49.94%) | 
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       24.05 ms →       23.43 ms   (-2.59%) |      45   →      25    (-44.44%) |        1.08 s  →      585.70 ms  (-45.88%) | 
+ │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       80.92 ms →       81.00 ms   (+0.10%) |      45   →      25    (-44.44%) |        3.64 s  →        2.03 s   (-44.39%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |       10.05 ms →        8.08 ms  (-19.63%) |      45   →      25    (-44.44%) |      452.47 ms →      202.02 ms  (-55.35%) | 
  │ │ ├ sirius::inner                                                   |                        10.84 ms            |                 300              |                         3.25 s             | 
+ │ │ ├ sirius::Density::mix                                            |      240.38 ms →      153.81 ms  (-36.01%) |      45   →      25    (-44.44%) |       10.82 s  →        3.85 s   (-64.45%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      927.07 μs →        1.11 ms  (+19.29%) |      45   →      25    (-44.44%) |       41.72 ms →       27.65 ms  (-33.73%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       11.18 ms                             |     619                          |        6.92 s                              | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.84 ms                             |     619                          |        6.71 s                              | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.84 ms                             |     619                          |        6.71 s                              | 
  │ │ │ ├ sirius::inner                                                 |                        10.07 ms            |                 319              |                         3.21 s             | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        7.94 ms →        6.48 ms  (-18.43%) |      45   →      25    (-44.44%) |      357.42 ms →      161.97 ms  (-54.68%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        7.13 ms →        5.38 ms  (-24.53%) |      45   →      25    (-44.44%) |      320.86 ms →      134.53 ms  (-58.07%) | 
+ │ │ ├ sirius::Potential::generate                                     |      685.45 ms →      670.27 ms   (-2.22%) |      45   →      25    (-44.44%) |       30.85 s  →       16.76 s   (-45.68%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |      137.45 ms →      137.82 ms   (+0.27%) |      45   →      25    (-44.44%) |        6.19 s  →        3.45 s   (-44.30%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       16.56 ms →       19.30 ms  (+16.49%) |      45   →      25    (-44.44%) |      745.42 ms →      482.40 ms  (-35.28%) | 
  │ │ │ │ ├ sirius::Periodic_function|inner                             |       10.74 ms                             |      45                          |      483.42 ms                             | 
  │ │ │ │ │ └ sirius::Periodic_function|inner_local                     |       10.38 ms                             |      45                          |      467.04 ms                             | 
  │ │ │ │ │   └ sirius::Smooth_periodic_function|inner_local            |       10.38 ms                             |      45                          |      467.01 ms                             | 
  │ │ │ │ └ sirius::inner                                               |                        10.65 ms            |                  25              |                       266.21 ms            | 
+ │ │ │ ├ sirius::Periodic_function::add                                |      546.95 μs →      461.12 μs  (-15.69%) |      90   →      50    (-44.44%) |       49.23 ms →       23.06 ms  (-53.16%) | 
+ │ │ │ ├ sirius::Potential::xc                                         |       53.92 ms →       34.54 ms  (-35.94%) |      45   →      25    (-44.44%) |        2.43 s  →      863.50 ms  (-64.41%) | 
+ │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       53.92 ms →       32.20 ms  (-40.29%) |      45   →      25    (-44.44%) |        2.43 s  →      804.89 ms  (-66.83%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.00 ms                             |      90                          |      269.86 ms                             | 
  │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |        5.68 ms                             |      45                          |      255.40 ms                             | 
  │ │ │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                |                        11.91 ms            |                  50              |                       595.75 ms            | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.70 ms →        5.00 ms  (-25.47%) |      45   →      25    (-44.44%) |      301.68 ms →      124.91 ms  (-58.60%) | 
+ │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.88 ms →       90.84 ms   (-0.04%) |      45   →      25    (-44.44%) |        4.09 s  →        2.27 s   (-44.47%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      394.10 ms →      397.30 ms   (+0.81%) |      45   →      25    (-44.44%) |       17.73 s  →        9.93 s   (-43.99%) | 
+ │ │ ├ sirius::Field4D::symmetrize                                     |      283.44 ms →      255.83 ms   (-9.74%) |      45   →      25    (-44.44%) |       12.75 s  →        6.40 s   (-49.86%) | 
+ │ │ │ └ sirius::symmetrize_function|fpw                               |      283.44 ms →      255.82 ms   (-9.74%) |      45   →      25    (-44.44%) |       12.75 s  →        6.40 s   (-49.86%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.30 ms →       24.01 ms  (-12.06%) |      45   →      25    (-44.44%) |        1.23 s  →      600.21 ms  (-51.14%) | 
+ │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      228.21 ms →      207.27 ms   (-9.18%) |      45   →      25    (-44.44%) |       10.27 s  →        5.18 s   (-49.54%) | 
+ │ │ │   └ sddk::Gvec_shells::remap_backward                           |       24.13 ms →       23.39 ms   (-3.06%) |      45   →      25    (-44.44%) |        1.09 s  →      584.75 ms  (-46.14%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.43 ms →        5.60 ms   (+3.22%) |      45   →      25    (-44.44%) |      244.26 ms →      140.06 ms  (-42.66%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.72 ms                             |     315                          |        3.38 s                              | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |       10.38 ms                             |     315                          |        3.27 s                              | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |       10.38 ms                             |     315                          |        3.27 s                              | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.17 ms                             |     135                          |        1.37 s                              | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        9.88 ms                             |     135                          |        1.33 s                              | 
+ │ │ ├ sirius::Periodic_function::integrate                            |        9.99 ms →       10.10 ms   (+1.13%) |      45   →      25    (-44.44%) |      449.48 ms →      252.54 ms  (-43.82%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      128.47 μs →       13.62 ms (+10503.93%) |      45   →      25    (-44.44%) |        5.78 ms →      340.57 ms (+5791.07%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      123.19 μs →       13.62 ms (+10953.67%) |      45   →      25    (-44.44%) |        5.54 ms →      340.42 ms (+6040.93%) | 
+ │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.28 ms →        4.54 ms  (-14.02%) |       2   →       2              |       10.56 ms →        9.08 ms  (-14.02%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.56 ms                             |       6                          |       63.34 ms                             | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.29 ms                             |       6                          |       61.73 ms                             | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.29 ms                             |       6                          |       61.73 ms                             | 
  │ ├ sirius::Smooth_periodic_function|inner                            |       10.02 ms                             |       3                          |       30.06 ms                             | 
  │ │ └ sirius::Smooth_periodic_function|inner_local                    |        9.71 ms                             |       3                          |       29.14 ms                             | 
  │ └ sirius::inner                                                     |                        10.45 ms            |                   9              |                        94.09 ms            | 
  ├ sirius::Periodic_function|inner                                     |       10.50 ms                             |       2                          |       21.00 ms                             | 
  │ └ sirius::Periodic_function|inner_local                             |       10.49 ms                             |       2                          |       20.99 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.49 ms                             |       2                          |       20.99 ms                             | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.09 ms                             |       1                          |       10.09 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.09 ms                             |       1                          |       10.09 ms                             | 
  ├ sirius::inner                                                       |                        11.21 ms            |                   3              |                        33.64 ms            | 
  └ sirius::finalize                                                    |      411.74 ms →      385.80 ms   (-6.30%) |       1   →       1              |      411.74 ms →      385.80 ms   (-6.30%) | 
  ====================================================================================================================================================================================================
```
