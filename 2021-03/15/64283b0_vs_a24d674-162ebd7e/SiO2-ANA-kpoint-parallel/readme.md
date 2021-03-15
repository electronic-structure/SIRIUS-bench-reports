# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs 64283b0bdde21ce92493e897e38c4105358cbbe3
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      176.09 s  →      118.43 s   (-32.74%) |       1   →       1              |      176.09 s  →      118.43 s   (-32.74%) | 
  ├ sirius::initialize                                                  |        2.77 s  →        2.72 s    (-1.80%) |       1   →       1              |        2.77 s  →        2.72 s    (-1.80%) | 
  ├ sirius::Simulation_context::initialize                              |        2.97 s  →        2.92 s    (-1.55%) |       1   →       1              |        2.97 s  →        2.92 s    (-1.55%) | 
- │ ├ sirius::Simulation_context::init_comm                             |      207.68 μs →       32.55 ms (+15572.16%) |       1   →       1              |      207.68 μs →       32.55 ms (+15572.16%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      196.08 ms →      153.14 ms  (-21.90%) |       1   →       1              |      196.08 ms →      153.14 ms  (-21.90%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       84.94 ms →       64.45 ms  (-24.12%) |       2   →       2              |      169.87 ms →      128.89 ms  (-24.12%) | 
  │ │ └ sirius::Unit_cell::update                                       |       26.13 ms →       24.07 ms   (-7.89%) |       1   →       1              |       26.13 ms →       24.07 ms   (-7.89%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.36 ms →        6.37 ms   (+0.21%) |       1   →       1              |        6.36 ms →        6.37 ms   (+0.21%) | 
+ │ │   └ sirius::Unit_cell::get_symmetry                               |       19.73 ms →       17.65 ms  (-10.56%) |       1   →       1              |       19.73 ms →       17.65 ms  (-10.56%) | 
+ │ │     └ sirius::Unit_cell_symmetry                                  |       19.71 ms →       17.62 ms  (-10.58%) |       1   →       1              |       19.71 ms →       17.62 ms  (-10.58%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        5.36 ms →        5.20 ms   (-2.87%) |       1   →       1              |        5.36 ms →        5.20 ms   (-2.87%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.34 ms →        2.32 ms   (-0.87%) |       1   →       1              |        2.34 ms →        2.32 ms   (-0.87%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      100.93 μs →      105.23 μs   (+4.26%) |       1   →       1              |      100.93 μs →      105.23 μs   (+4.26%) | 
  │ └ sirius::Simulation_context::update                                |        2.73 s  →        2.69 s    (-1.32%) |       1   →       1              |        2.73 s  →        2.69 s    (-1.32%) | 
  │   ├ sirius::Unit_cell::update                                       |       12.02 ms →       11.89 ms   (-1.05%) |       1   →       1              |       12.02 ms →       11.89 ms   (-1.05%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.46 ms →        4.53 ms   (+1.57%) |       1   →       1              |        4.46 ms →        4.53 ms   (+1.57%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        7.53 ms →        7.33 ms   (-2.63%) |       1   →       1              |        7.53 ms →        7.33 ms   (-2.63%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        7.51 ms →        7.31 ms   (-2.67%) |       1   →       1              |        7.51 ms →        7.31 ms   (-2.67%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        5.03 ms →        4.82 ms   (-4.12%) |       1   →       1              |        5.03 ms →        4.82 ms   (-4.12%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.32 ms   (+0.32%) |       1   →       1              |        2.32 ms →        2.32 ms   (+0.32%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      100.08 μs →       99.67 μs   (-0.41%) |       1   →       1              |      100.08 μs →       99.67 μs   (-0.41%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       64.94 ms →       64.36 ms   (-0.88%) |       2   →       2              |      129.88 ms →      128.73 ms   (-0.88%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.14 ms →        5.14 ms   (+0.03%) |       2   →       2              |       10.27 ms →       10.27 ms   (+0.03%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.47 ms →        4.49 ms   (+0.40%) |       1   →       1              |        4.47 ms →        4.49 ms   (+0.40%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.76 ms →       21.79 ms   (+0.17%) |       2   →       2              |       43.51 ms →       43.59 ms   (+0.17%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.76 ms →       14.75 ms   (-0.01%) |       2   →       2              |       29.51 ms →       29.51 ms   (-0.01%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.84 ms →       19.64 ms   (-0.97%) |       4   →       4              |       79.34 ms →       78.57 ms   (-0.97%) | 
  │   ├ sddk::Gvec::init                                                |      172.94 ms →      177.25 ms   (+2.49%) |       2   →       2              |      345.87 ms →      354.49 ms   (+2.49%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      130.41 ms →      130.60 ms   (+0.15%) |       2   →       2              |      260.81 ms →      261.20 ms   (+0.15%) | 
  │   ├ sddk::Gvec_shells                                               |      166.88 ms →      173.91 ms   (+4.21%) |       1   →       1              |      166.88 ms →      173.91 ms   (+4.21%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.33 ms →        1.32 ms   (-0.70%) |       1   →       1              |        1.33 ms →        1.32 ms   (-0.70%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      299.26 ms →      294.20 ms   (-1.69%) |       2   →       2              |      598.53 ms →      588.41 ms   (-1.69%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       35.55 ms →       36.05 ms   (+1.38%) |       1   →       1              |       35.55 ms →       36.05 ms   (+1.38%) | 
- │ ├ sirius::K_point::K_point                                          |        3.06 μs →        6.65 μs (+117.15%) |       4   →       4              |       12.24 μs →       26.58 μs (+117.15%) | 
  │ └ sirius::K_point_set::initialize                                   |       35.46 ms →       35.88 ms   (+1.17%) |       1   →       1              |       35.46 ms →       35.88 ms   (+1.17%) | 
  │   └ sirius::K_point::initialize                                     |       35.38 ms →       35.79 ms   (+1.17%) |       1   →       1              |       35.38 ms →       35.79 ms   (+1.17%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       18.15 ms →       18.30 ms   (+0.80%) |       1   →       1              |       18.15 ms →       18.30 ms   (+0.80%) | 
  │     │ └ sddk::Gvec::init                                            |        8.05 ms →        8.17 ms   (+1.43%) |       1   →       1              |        8.05 ms →        8.17 ms   (+1.43%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        9.19 μs                             |       1                          |        9.19 μs                             | 
  │     └ sirius::K_point::update                                       |       12.43 ms →       12.65 ms   (+1.82%) |       1   →       1              |       12.43 ms →       12.65 ms   (+1.82%) | 
  │       └ sirius::Beta_projectors                                     |        6.15 ms →        6.43 ms   (+4.61%) |       1   →       1              |        6.15 ms →        6.43 ms   (+4.61%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.55 ms →        3.84 ms   (+8.09%) |       1   →       1              |        3.55 ms →        3.84 ms   (+8.09%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.23 ms                             |       2                          |       10.46 ms                             | 
+ ├ sirius::Potential                                                   |      173.29 ms →      153.99 ms  (-11.13%) |       1   →       1              |      173.29 ms →      153.99 ms  (-11.13%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.78 ms                             |       6                          |       34.65 ms                             | 
  │ └ sirius::Potential::update                                         |      137.91 ms →      124.25 ms   (-9.90%) |       1   →       1              |      137.91 ms →      124.25 ms   (-9.90%) | 
  │   └ sirius::Potential::generate_local_potential                     |      137.14 ms →      123.54 ms   (-9.92%) |       1   →       1              |      137.14 ms →      123.54 ms   (-9.92%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |      124.96 ms →      108.96 ms  (-12.80%) |       1   →       1              |      124.96 ms →      108.96 ms  (-12.80%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       11.63 ms →        7.50 ms  (-35.56%) |       1   →       1              |       11.63 ms →        7.50 ms  (-35.56%) | 
  ├ sirius::Density                                                     |      139.95 ms →      130.41 ms   (-6.81%) |       1   →       1              |      139.95 ms →      130.41 ms   (-6.81%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.16 ms                             |       2                          |       10.33 ms                             | 
  │ └ sirius::Density::update                                           |      129.35 ms →      119.79 ms   (-7.40%) |       1   →       1              |      129.35 ms →      119.79 ms   (-7.40%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      128.93 ms →      119.31 ms   (-7.46%) |       1   →       1              |      128.93 ms →      119.31 ms   (-7.46%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      123.31 ms →      112.13 ms   (-9.07%) |       1   →       1              |      123.31 ms →      112.13 ms   (-9.07%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        5.17 ms →        5.33 ms   (+3.16%) |       1   →       1              |        5.17 ms →        5.33 ms   (+3.16%) | 
  ├ sirius::Density::initial_density                                    |      177.09 ms →      164.16 ms   (-7.30%) |       1   →       1              |      177.09 ms →      164.16 ms   (-7.30%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      122.01 ms →      110.45 ms   (-9.48%) |       1   →       1              |      122.01 ms →      110.45 ms   (-9.48%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.18 ms →        5.16 ms   (-0.47%) |       2   →       2              |       10.36 ms →       10.31 ms   (-0.47%) | 
  │ └ sirius::Periodic_function::integrate                              |       10.39 ms →        9.86 ms   (-5.09%) |       1   →       1              |       10.39 ms →        9.86 ms   (-5.09%) | 
  ├ sirius::Potential::generate                                         |      703.16 ms →      673.51 ms   (-4.22%) |       1   →       1              |      703.16 ms →      673.51 ms   (-4.22%) | 
  │ ├ sirius::Potential::poisson                                        |      137.33 ms →      127.56 ms   (-7.11%) |       1   →       1              |      137.33 ms →      127.56 ms   (-7.11%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.59 ms →        5.49 ms   (-1.75%) |       1   →       1              |        5.59 ms →        5.49 ms   (-1.75%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.64 ms                             |       1                          |       10.64 ms                             | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |       10.32 ms                             |       1                          |       10.32 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |       10.32 ms                             |       1                          |       10.32 ms                             | 
  │ │ └ sirius::inner                                                   |                        11.89 ms            |                   1              |                        11.89 ms            | 
+ │ ├ sirius::Periodic_function::add                                    |      580.22 μs →      462.38 μs  (-20.31%) |       2   →       2              |        1.16 ms →      924.77 μs  (-20.31%) | 
+ │ ├ sirius::Potential::xc                                             |       58.24 ms →       39.45 ms  (-32.25%) |       1   →       1              |       58.24 ms →       39.45 ms  (-32.25%) | 
+ │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       58.23 ms →       37.16 ms  (-36.19%) |       1   →       1              |       58.23 ms →       37.16 ms  (-36.19%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.72 ms                             |       2                          |       11.43 ms                             | 
  │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        5.22 ms                             |       1                          |        5.22 ms                             | 
  │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                    |                        12.11 ms            |                   2              |                        24.21 ms            | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.68 ms →        4.80 ms  (-15.55%) |       1   →       1              |        5.68 ms →        4.80 ms  (-15.55%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       93.63 ms →       93.55 ms   (-0.08%) |       1   →       1              |       93.63 ms →       93.55 ms   (-0.08%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      405.76 ms →      403.00 ms   (-0.68%) |       1   →       1              |      405.76 ms →      403.00 ms   (-0.68%) | 
- ├ sirius::Hamiltonian0                                                |        8.51 ms →       11.81 ms  (+38.83%) |       1   →       1              |        8.51 ms →       11.81 ms  (+38.83%) | 
  │ ├ sirius::Local_operator                                            |        8.16 ms →        8.01 ms   (-1.82%) |       1   →       1              |        8.16 ms →        8.01 ms   (-1.82%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.73 ms                             |       1                          |        4.73 ms                             | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.52 ms →        2.43 ms   (-3.48%) |       1   →       1              |        2.52 ms →        2.43 ms   (-3.48%) | 
  │ ├ sirius::Non_local_operator                                        |       61.90 μs →       63.41 μs   (+2.45%) |       2   →       2              |      123.79 μs →      126.83 μs   (+2.45%) | 
- │ ├ sirius::D_operator::initialize                                    |       96.78 μs →        1.26 ms (+1203.91%) |       1   →       1              |       96.78 μs →        1.26 ms (+1203.91%) | 
- │ └ sirius::Q_operator::initialize                                    |       74.93 μs →        2.36 ms (+3043.61%) |       1   →       1              |       74.93 μs →        2.36 ms (+3043.61%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.88 s  →        1.85 s    (-1.66%) |       1   →       1              |        1.88 s  →        1.85 s    (-1.66%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.71 ms →       18.70 ms   (-0.03%) |       1   →       1              |       18.71 ms →       18.70 ms   (-0.03%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      194.94 μs →      201.28 μs   (+3.25%) |       1   →       1              |      194.94 μs →      201.28 μs   (+3.25%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       18.51 ms →       18.50 ms   (-0.08%) |       1   →       1              |       18.51 ms →       18.50 ms   (-0.08%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.86 s  →        1.83 s    (-1.76%) |       1   →       1              |        1.86 s  →        1.83 s    (-1.76%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      134.40 ms                             |       4                          |      537.61 ms                             | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       51.87 ms →       51.93 ms   (+0.12%) |       1   →       1              |       51.87 ms →       51.93 ms   (+0.12%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.06 ms →       21.02 ms   (-0.22%) |       1   →       1              |       21.06 ms →       21.02 ms   (-0.22%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      637.25 ms →      636.73 ms   (-0.08%) |       1   →       1              |      637.25 ms →      636.73 ms   (-0.08%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      297.45 ms →      297.94 ms   (+0.16%) |       1   →       1              |      297.45 ms →      297.94 ms   (+0.16%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.46 μs →        3.27 μs   (-5.60%) |       1   →       1              |        3.46 μs →        3.27 μs   (-5.60%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.56 μs                             |       1                          |        2.56 μs                             | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      359.00 ns                             |       1                          |      359.00 ns                             | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      514.00 ns →      502.00 ns   (-2.33%) |       1   →       1              |      514.00 ns →      502.00 ns   (-2.33%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.21 ms →        9.21 ms   (-0.04%) |       1   →       1              |        9.21 ms →        9.21 ms   (-0.04%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      121.20 ms →      121.06 ms   (-0.12%) |       1   →       1              |      121.20 ms →      121.06 ms   (-0.12%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      104.67 ms →      104.24 ms   (-0.41%) |       2   →       2              |      209.34 ms →      208.48 ms   (-0.41%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       38.56 ms →       40.05 ms   (+3.86%) |       2   →       2              |       77.12 ms →       80.10 ms   (+3.86%) | 
  │ │ │ ├ sddk::inner                                                   |       38.02 ms                             |       2                          |       76.04 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       26.56 μs                             |       2                          |       53.13 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        39.47 ms            |                   2              |                        78.94 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        98.50 ns            |                   2              |                       197.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        38.99 ms            |                   2              |                        77.99 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                       440.00 ns            |                   2              |                       880.00 ns            | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       56.42 ms →       56.29 ms   (-0.23%) |       1   →       1              |       56.42 ms →       56.29 ms   (-0.23%) | 
  │ │ ├ sddk::transform                                                 |       31.56 ms                             |       1                          |       31.56 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       26.36 μs                             |       1                          |       26.36 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       11.95 μs                             |       1                          |       11.95 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                        30.74 ms            |                   1              |                        30.74 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                        30.74 ms            |                   1              |                        30.74 ms            | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      795.00 ns →      527.00 ns  (-33.71%) |       1   →       1              |      795.00 ns →      527.00 ns  (-33.71%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      165.83 s  →      108.74 s   (-34.43%) |       1   →       1              |      165.83 s  →      108.74 s   (-34.43%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.78 ms                             |      19                          |      109.83 ms                             | 
  │ ├ sirius::Density                                                   |                       143.04 ms            |                   1              |                       143.04 ms            | 
  │ │ └ sirius::Density::update                                         |                       132.54 ms            |                   1              |                       132.54 ms            | 
  │ │   └ sirius::Density::generate_pseudo_core_charge_density          |                       132.11 ms            |                   1              |                       132.11 ms            | 
  │ │     ├ sirius::Simulation_context::make_periodic_function          |                       111.97 ms            |                   1              |                       111.97 ms            | 
  │ │     └ sirius::Smooth_periodic_function::fft_transform             |                         5.65 ms            |                   1              |                         5.65 ms            | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.73 s  →        4.70 s    (-0.48%) |      35   →      23    (-34.29%) |      165.46 s  →      108.21 s   (-34.60%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        4.52 ms →        7.92 ms  (+75.21%) |      35   →      23    (-34.29%) |      158.21 ms →      182.16 ms  (+15.14%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        4.15 ms →        4.11 ms   (-1.07%) |      35   →      23    (-34.29%) |      145.38 ms →       94.51 ms  (-34.99%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      963.87 μs                             |      35                          |       33.74 ms                             | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.30 ms →        2.28 ms   (-0.99%) |      35   →      23    (-34.29%) |       80.60 ms →       52.44 ms  (-34.94%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |       64.74 μs →       64.84 μs   (+0.16%) |      70   →      46    (-34.29%) |        4.53 ms →        2.98 ms  (-34.18%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |       93.27 μs →        1.24 ms (+1228.24%) |      35   →      23    (-34.29%) |        3.26 ms →       28.49 ms (+772.85%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       76.53 μs →        2.38 ms (+3010.60%) |      35   →      23    (-34.29%) |        2.68 ms →       54.75 ms (+1944.11%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.63 s  →        2.70 s    (+2.91%) |      35   →      23    (-34.29%) |       91.99 s  →       62.21 s   (-32.38%) | 
+ │ │ │ ├ sirius::Hamiltonian_k                                         |      159.82 μs →      171.60 μs   (+7.37%) |      35   →      23    (-34.29%) |        5.59 ms →        3.95 ms  (-29.44%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      153.39 μs →      163.87 μs   (+6.83%) |      35   →      23    (-34.29%) |        5.37 ms →        3.77 ms  (-29.79%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.84 μs →        3.99 μs  (-17.54%) |      35   →      23    (-34.29%) |      169.42 μs →       91.80 μs  (-45.81%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.56 s  →        2.51 s    (-1.87%) |      35   →      23    (-34.29%) |       89.46 s  →       57.69 s   (-35.52%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |      102.65 ms                             |      35                          |        3.59 s                              | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        8.84 ms                             |     210                          |        1.86 s                              | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        5.96 ms →        5.91 ms   (-0.82%) |      35   →      23    (-34.29%) |      208.72 ms →      136.04 ms  (-34.82%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      352.91 μs                             |      35                          |       12.35 ms                             | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.30 ms                             |      70                          |      161.13 ms                             | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.41 s  →        2.37 s    (-1.89%) |      35   →      23    (-34.29%) |       84.39 s  →       54.41 s   (-35.53%) | 
+ │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      108.95 ms →      107.02 ms   (-1.77%) |     355   →     301    (-15.21%) |       38.68 s  →       32.21 s   (-16.71%) | 
+ │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       42.11 ms →       41.01 ms   (-2.61%) |     355   →     301    (-15.21%) |       14.95 s  →       12.34 s   (-17.42%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.87 μs →        1.63 μs  (-12.85%) |     355   →     301    (-15.21%) |      662.87 μs →      489.82 μs  (-26.11%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.59 μs                             |     355                          |      563.37 μs                             | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      305.27 ns                             |     355                          |      108.37 μs                             | 
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      417.97 ns →      384.82 ns   (-7.93%) |     355   →     301    (-15.21%) |      148.38 μs →      115.83 μs  (-21.94%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.36 ms →        7.35 ms   (-0.15%) |     355   →     301    (-15.21%) |        2.61 s  →        2.21 s   (-15.34%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       19.95 ms →       19.56 ms   (-1.98%) |     355   →     301    (-15.21%) |        7.08 s  →        5.89 s   (-16.89%) | 
+ │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       19.76 ms →       19.54 ms   (-1.09%) |     710   →     602    (-15.21%) |       14.03 s  →       11.76 s   (-16.13%) | 
+ │ │ │ │   ├ sddk::orthogonalize                                       |       35.32 ms →       32.54 ms   (-7.89%) |     355   →     301    (-15.21%) |       12.54 s  →        9.79 s   (-21.90%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        4.49 ms                             |     675                          |        3.03 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       21.64 μs                             |     675                          |       14.61 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                         4.97 ms            |                 579              |                         2.88 s             | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                       110.58 ns            |                 579              |                        64.03 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                         3.86 ms            |                 579              |                         2.24 s             | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                       204.11 ns            |                 579              |                       118.18 μs            | 
+ │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |        5.59 ms →        5.21 ms   (-6.85%) |     355   →     301    (-15.21%) |        1.99 s  →        1.57 s   (-21.02%) | 
+ │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        8.31 ms →        7.83 ms   (-5.79%) |     355   →     301    (-15.21%) |        2.95 s  →        2.36 s   (-20.12%) | 
  │ │ │ │   │ ├ sddk::transform                                         |       14.28 ms                             |     320                          |        4.57 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       18.42 μs                             |     320                          |        5.90 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       34.39 μs                             |     960                          |       33.01 ms                             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                        10.75 ms            |                 278              |                         2.99 s             | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                         3.58 ms            |                 834              |                         2.99 s             | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        9.55 ms →        8.44 ms  (-11.61%) |     355   →     301    (-15.21%) |        3.39 s  →        2.54 s   (-25.06%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        8.65 ms                             |     355                          |        3.07 s                              | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       28.38 μs                             |     355                          |       10.07 ms                             | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                         8.04 ms            |                 301              |                         2.42 s             | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                       113.24 ns            |                 301              |                        34.09 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                         6.92 ms            |                 301              |                         2.08 s             | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                       174.90 ns            |                 301              |                        52.64 μs            | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       64.65 ms →       12.76 ms  (-80.27%) |     355   →     301    (-15.21%) |       22.95 s  →        3.84 s   (-83.27%) | 
+ │ │ │ │   ├ sirius::residuals                                         |       14.01 ms →        7.67 ms  (-45.26%) |     344   →     291    (-15.41%) |        4.82 s  →        2.23 s   (-53.70%) | 
  │ │ │ │   │ ├ sddk::transform                                         |       12.93 ms                             |     331                          |        4.28 s                              | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       15.03 μs                             |     331                          |        4.97 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       35.67 μs                             |     662                          |       23.61 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                         6.47 ms            |                 278              |                         1.80 s             | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                         3.23 ms            |                 556              |                         1.80 s             | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.41 ms →        1.17 ms  (-16.64%) |     331   →     278    (-16.01%) |      466.15 ms →      326.36 ms  (-29.99%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       54.16 ms →       43.84 ms  (-19.06%) |      37   →      86   (+132.43%) |        2.00 s  →        3.77 s   (+88.14%) | 
  │ │ │ │     ├ sddk::transform                                         |       51.18 ms                             |      39                          |        2.00 s                              | 
  │ │ │ │     │ ├ sddk::transform|init                                  |       12.04 μs                             |      39                          |      469.46 μs                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       12.87 μs                             |      41                          |      527.49 μs                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                        25.05 ms            |                 149              |                         3.73 s             | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                        17.61 ms            |                 212              |                         3.73 s             | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      483.89 ns →      722.70 ns  (+49.35%) |      35   →      23    (-34.29%) |       16.94 μs →       16.62 μs   (-1.85%) | 
  │ │ │ ├ sirius::K_point_set::sync_band_energies                       |       30.91 μs                             |      35                          |        1.08 ms                             | 
  │ │ │ └ sirius::K_point_set::sync_band                                |                        98.19 μs            |                  23              |                         2.26 ms            | 
+ │ │ ├ sirius::K_point_set::find_band_occupancies                      |      598.20 μs →      463.47 μs  (-22.52%) |      35   →      23    (-34.29%) |       20.94 ms →       10.66 ms  (-49.09%) | 
  │ │ │ └ sirius::K_point_set::sync_band                                |                        28.85 μs            |                  23              |                       663.45 μs            | 
+ │ │ ├ sirius::Density::generate                                       |      771.72 ms →      757.88 ms   (-1.79%) |      35   →      23    (-34.29%) |       27.01 s  →       17.43 s   (-35.46%) | 
+ │ │ │ ├ sirius::Density::generate_valence                             |      401.66 ms →      404.84 ms   (+0.79%) |      35   →      23    (-34.29%) |       14.06 s  →        9.31 s   (-33.77%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.03 μs →        2.40 μs  (-70.07%) |      35   →      23    (-34.29%) |      281.17 μs →       55.30 μs  (-80.33%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.23 μs                             |      35                          |      253.17 μs                             | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       99.88 ms →      100.60 ms   (+0.72%) |      35   →      23    (-34.29%) |        3.50 s  →        2.31 s   (-33.82%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.28 μs →        8.87 μs  (+21.83%) |      35   →      23    (-34.29%) |      254.73 μs →      203.93 μs  (-19.94%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.12 ms →        7.12 ms   (-0.02%) |      35   →      23    (-34.29%) |      249.18 ms →      163.71 ms  (-34.30%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       90.89 ms →       91.55 ms   (+0.73%) |      35   →      23    (-34.29%) |        3.18 s  →        2.11 s   (-33.81%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      575.83 ns →      523.43 ns   (-9.10%) |      35   →      23    (-34.29%) |       20.15 μs →       12.04 μs  (-40.26%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      162.59 ms →      163.28 ms   (+0.42%) |      35   →      23    (-34.29%) |        5.69 s  →        3.76 s   (-34.01%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.64 ms   (-0.23%) |      35   →      23    (-34.29%) |       57.57 ms →       37.74 ms  (-34.44%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |       88.25 ms →       88.39 ms   (+0.16%) |      35   →      23    (-34.29%) |        3.09 s  →        2.03 s   (-34.18%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.02 ms →       88.16 ms   (+0.15%) |      35   →      23    (-34.29%) |        3.08 s  →        2.03 s   (-34.18%) | 
+ │ │ │ ├ sirius::Field4D::symmetrize                                   |      276.04 ms →      260.82 ms   (-5.51%) |      35   →      23    (-34.29%) |        9.66 s  →        6.00 s   (-37.91%) | 
+ │ │ │ │ └ sirius::symmetrize_function|fpw                             |      276.04 ms →      260.81 ms   (-5.52%) |      35   →      23    (-34.29%) |        9.66 s  →        6.00 s   (-37.91%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       25.10 ms →       25.42 ms   (+1.28%) |      35   →      23    (-34.29%) |      878.48 ms →      584.70 ms  (-33.44%) | 
+ │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      226.00 ms →      210.79 ms   (-6.73%) |      35   →      23    (-34.29%) |        7.91 s  →        4.85 s   (-38.71%) | 
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       23.74 ms →       23.45 ms   (-1.21%) |      35   →      23    (-34.29%) |      830.83 ms →      539.36 ms  (-35.08%) | 
+ │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       80.96 ms →       81.01 ms   (+0.05%) |      35   →      23    (-34.29%) |        2.83 s  →        1.86 s   (-34.25%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        9.50 ms →        7.50 ms  (-21.01%) |      35   →      23    (-34.29%) |      332.48 ms →      172.57 ms  (-48.09%) | 
  │ │ ├ sirius::inner                                                   |                        10.69 ms            |                 276              |                         2.95 s             | 
+ │ │ ├ sirius::Density::mix                                            |      236.27 ms →      153.40 ms  (-35.08%) |      35   →      23    (-34.29%) |        8.27 s  →        3.53 s   (-57.34%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      960.77 μs →        1.09 ms  (+13.68%) |      35   →      23    (-34.29%) |       33.63 ms →       25.12 ms  (-25.29%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       11.23 ms                             |     469                          |        5.26 s                              | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.87 ms                             |     469                          |        5.10 s                              | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.87 ms                             |     469                          |        5.10 s                              | 
  │ │ │ ├ sirius::inner                                                 |                        10.20 ms            |                 289              |                         2.95 s             | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        6.88 ms →        6.26 ms   (-9.05%) |      35   →      23    (-34.29%) |      240.79 ms →      143.91 ms  (-40.23%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        6.03 ms →        5.17 ms  (-14.25%) |      35   →      23    (-34.29%) |      211.22 ms →      119.02 ms  (-43.65%) | 
+ │ │ ├ sirius::Potential::generate                                     |      685.90 ms →      660.51 ms   (-3.70%) |      35   →      23    (-34.29%) |       24.01 s  →       15.19 s   (-36.72%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |      137.41 ms →      127.67 ms   (-7.09%) |      35   →      23    (-34.29%) |        4.81 s  →        2.94 s   (-38.95%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        5.55 ms →        6.01 ms   (+8.35%) |      35   →      23    (-34.29%) |      194.29 ms →      138.33 ms  (-28.80%) | 
  │ │ │ │ ├ sirius::Periodic_function|inner                             |       10.91 ms                             |      35                          |      382.00 ms                             | 
  │ │ │ │ │ └ sirius::Periodic_function|inner_local                     |       10.66 ms                             |      35                          |      372.93 ms                             | 
  │ │ │ │ │   └ sirius::Smooth_periodic_function|inner_local            |       10.65 ms                             |      35                          |      372.91 ms                             | 
  │ │ │ │ └ sirius::inner                                               |                        11.82 ms            |                  23              |                       271.88 ms            | 
+ │ │ │ ├ sirius::Periodic_function::add                                |      560.89 μs →      461.60 μs  (-17.70%) |      70   →      46    (-34.29%) |       39.26 ms →       21.23 ms  (-45.92%) | 
+ │ │ │ ├ sirius::Potential::xc                                         |       52.34 ms →       34.37 ms  (-34.33%) |      35   →      23    (-34.29%) |        1.83 s  →      790.49 ms  (-56.84%) | 
+ │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       52.33 ms →       32.06 ms  (-38.74%) |      35   →      23    (-34.29%) |        1.83 s  →      737.39 ms  (-59.74%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        1.23 ms                             |      70                          |       86.27 ms                             | 
  │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |       11.78 ms                             |      35                          |      412.24 ms                             | 
  │ │ │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                |                        11.82 ms            |                  46              |                       543.51 ms            | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        7.71 ms →        4.78 ms  (-37.95%) |      35   →      23    (-34.29%) |      269.83 ms →      110.03 ms  (-59.22%) | 
+ │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.88 ms →       90.89 ms   (+0.01%) |      35   →      23    (-34.29%) |        3.18 s  →        2.09 s   (-34.28%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      395.13 ms →      398.00 ms   (+0.73%) |      35   →      23    (-34.29%) |       13.83 s  →        9.15 s   (-33.81%) | 
+ │ │ ├ sirius::Field4D::symmetrize                                     |      278.31 ms →      258.25 ms   (-7.21%) |      35   →      23    (-34.29%) |        9.74 s  →        5.94 s   (-39.02%) | 
+ │ │ │ └ sirius::symmetrize_function|fpw                               |      278.31 ms →      258.24 ms   (-7.21%) |      35   →      23    (-34.29%) |        9.74 s  →        5.94 s   (-39.02%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       26.98 ms →       24.20 ms  (-10.29%) |      35   →      23    (-34.29%) |      944.17 ms →      556.64 ms  (-41.04%) | 
+ │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      226.00 ms →      208.93 ms   (-7.55%) |      35   →      23    (-34.29%) |        7.91 s  →        4.81 s   (-39.25%) | 
+ │ │ │   └ sddk::Gvec_shells::remap_backward                           |       24.19 ms →       23.98 ms   (-0.88%) |      35   →      23    (-34.29%) |      846.80 ms →      551.55 ms  (-34.87%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.56 ms →        5.54 ms   (-0.29%) |      35   →      23    (-34.29%) |      194.63 ms →      127.53 ms  (-34.48%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.74 ms                             |     245                          |        2.63 s                              | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |       10.32 ms                             |     245                          |        2.53 s                              | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |       10.32 ms                             |     245                          |        2.53 s                              | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.22 ms                             |     105                          |        1.07 s                              | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        9.85 ms                             |     105                          |        1.03 s                              | 
+ │ │ ├ sirius::Periodic_function::integrate                            |       10.02 ms →       10.11 ms   (+0.90%) |      35   →      23    (-34.29%) |      350.62 ms →      232.48 ms  (-33.70%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      115.30 μs →       13.93 ms (+11979.99%) |      35   →      23    (-34.29%) |        4.04 ms →      320.36 ms (+7838.28%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      110.23 μs →       13.92 ms (+12531.49%) |      35   →      23    (-34.29%) |        3.86 ms →      320.23 ms (+8200.69%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.33 ms →        5.01 ms   (-5.99%) |       2   →       2              |       10.65 ms →       10.02 ms   (-5.99%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.54 ms                             |       6                          |       63.24 ms                             | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.22 ms                             |       6                          |       61.31 ms                             | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.22 ms                             |       6                          |       61.31 ms                             | 
  │ ├ sirius::Smooth_periodic_function|inner                            |       10.06 ms                             |       3                          |       30.17 ms                             | 
  │ │ └ sirius::Smooth_periodic_function|inner_local                    |        9.66 ms                             |       3                          |       28.98 ms                             | 
  │ └ sirius::inner                                                     |                        10.57 ms            |                   9              |                        95.17 ms            | 
  ├ sirius::Periodic_function|inner                                     |       10.44 ms                             |       2                          |       20.89 ms                             | 
  │ └ sirius::Periodic_function|inner_local                             |       10.08 ms                             |       2                          |       20.17 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.08 ms                             |       2                          |       20.17 ms                             | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.07 ms                             |       1                          |       10.07 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        9.60 ms                             |       1                          |        9.60 ms                             | 
  ├ sirius::inner                                                       |                        10.60 ms            |                   3              |                        31.81 ms            | 
  └ sirius::finalize                                                    |      227.44 ms →      219.22 ms   (-3.61%) |       1   →       1              |      227.44 ms →      219.22 ms   (-3.61%) | 
  ====================================================================================================================================================================================================
```
