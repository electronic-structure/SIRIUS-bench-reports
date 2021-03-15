# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs 8d4c8fb637741d881d5cdc9faf167adefd93fb67
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |      169.19 s  →      126.77 s   (-25.07%) |       1   →       1              |      169.19 s  →      126.77 s   (-25.07%) | 
  ├ sirius::initialize                                                  |        2.78 s  →        2.97 s    (+6.95%) |       1   →       1              |        2.78 s  →        2.97 s    (+6.95%) | 
  ├ sirius::Simulation_context::initialize                              |        2.88 s  →        2.87 s    (-0.13%) |       1   →       1              |        2.88 s  →        2.87 s    (-0.13%) | 
  │ ├ sirius::Simulation_context::init_comm                             |      228.68 μs →      209.26 μs   (-8.49%) |       1   →       1              |      228.68 μs →      209.26 μs   (-8.49%) | 
  │ ├ sirius::Unit_cell::initialize                                     |      156.58 ms →      148.66 ms   (-5.06%) |       1   →       1              |      156.58 ms →      148.66 ms   (-5.06%) | 
  │ │ ├ sirius::Atom_type::init                                         |       66.58 ms →       61.88 ms   (-7.06%) |       2   →       2              |      133.16 ms →      123.76 ms   (-7.06%) | 
  │ │ └ sirius::Unit_cell::update                                       |       23.35 ms →       24.71 ms   (+5.84%) |       1   →       1              |       23.35 ms →       24.71 ms   (+5.84%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.01 ms →        6.31 ms   (+4.97%) |       1   →       1              |        6.01 ms →        6.31 ms   (+4.97%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       17.30 ms →       18.36 ms   (+6.16%) |       1   →       1              |       17.30 ms →       18.36 ms   (+6.16%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       17.28 ms →       18.34 ms   (+6.14%) |       1   →       1              |       17.28 ms →       18.34 ms   (+6.14%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        5.35 ms →        5.20 ms   (-2.66%) |       1   →       1              |        5.35 ms →        5.20 ms   (-2.66%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.40 ms →        2.32 ms   (-3.10%) |       1   →       1              |        2.40 ms →        2.32 ms   (-3.10%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      100.57 μs →      101.17 μs   (+0.60%) |       1   →       1              |      100.57 μs →      101.17 μs   (+0.60%) | 
  │ └ sirius::Simulation_context::update                                |        2.68 s  →        2.68 s    (+0.08%) |       1   →       1              |        2.68 s  →        2.68 s    (+0.08%) | 
  │   ├ sirius::Unit_cell::update                                       |       12.07 ms →       11.65 ms   (-3.44%) |       1   →       1              |       12.07 ms →       11.65 ms   (-3.44%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.45 ms →        4.32 ms   (-2.71%) |       1   →       1              |        4.45 ms →        4.32 ms   (-2.71%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        7.59 ms →        7.29 ms   (-3.91%) |       1   →       1              |        7.59 ms →        7.29 ms   (-3.91%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        7.57 ms →        7.27 ms   (-3.97%) |       1   →       1              |        7.57 ms →        7.27 ms   (-3.97%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        5.09 ms →        4.76 ms   (-6.38%) |       1   →       1              |        5.09 ms →        4.76 ms   (-6.38%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.31 ms →        2.34 ms   (+1.13%) |       1   →       1              |        2.31 ms →        2.34 ms   (+1.13%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      103.54 μs →       99.99 μs   (-3.44%) |       1   →       1              |      103.54 μs →       99.99 μs   (-3.44%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       65.35 ms →       64.49 ms   (-1.32%) |       2   →       2              |      130.71 ms →      128.98 ms   (-1.32%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.12 ms →        5.14 ms   (+0.39%) |       2   →       2              |       10.24 ms →       10.28 ms   (+0.39%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.47 ms →        4.46 ms   (-0.21%) |       1   →       1              |        4.47 ms →        4.46 ms   (-0.21%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.74 ms →       21.79 ms   (+0.27%) |       2   →       2              |       43.47 ms →       43.59 ms   (+0.27%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.75 ms →       14.75 ms   (+0.00%) |       2   →       2              |       29.50 ms →       29.50 ms   (+0.00%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.68 ms →       19.82 ms   (+0.70%) |       4   →       4              |       78.73 ms →       79.28 ms   (+0.70%) | 
  │   ├ sddk::Gvec::init                                                |      173.25 ms →      181.98 ms   (+5.04%) |       2   →       2              |      346.50 ms →      363.95 ms   (+5.04%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      130.71 ms →      138.18 ms   (+5.72%) |       2   →       2              |      261.42 ms →      276.36 ms   (+5.72%) | 
  │   ├ sddk::Gvec_shells                                               |      180.31 ms →      168.87 ms   (-6.35%) |       1   →       1              |      180.31 ms →      168.87 ms   (-6.35%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.32 ms →        1.32 ms   (+0.11%) |       1   →       1              |        1.32 ms →        1.32 ms   (+0.11%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      291.14 ms →      291.95 ms   (+0.28%) |       2   →       2              |      582.28 ms →      583.89 ms   (+0.28%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       35.51 ms →       35.80 ms   (+0.83%) |       1   →       1              |       35.51 ms →       35.80 ms   (+0.83%) | 
- │ ├ sirius::K_point::K_point                                          |        2.81 μs →        6.58 μs (+134.07%) |       4   →       4              |       11.25 μs →       26.32 μs (+134.07%) | 
  │ └ sirius::K_point_set::initialize                                   |       35.42 ms →       35.65 ms   (+0.64%) |       1   →       1              |       35.42 ms →       35.65 ms   (+0.64%) | 
  │   └ sirius::K_point::initialize                                     |       35.33 ms →       35.56 ms   (+0.65%) |       1   →       1              |       35.33 ms →       35.56 ms   (+0.65%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       18.09 ms →       18.20 ms   (+0.56%) |       1   →       1              |       18.09 ms →       18.20 ms   (+0.56%) | 
  │     │ └ sddk::Gvec::init                                            |        8.06 ms →        8.12 ms   (+0.75%) |       1   →       1              |        8.06 ms →        8.12 ms   (+0.75%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        8.64 μs                             |       1                          |        8.64 μs                             | 
  │     └ sirius::K_point::update                                       |       12.44 ms →       12.54 ms   (+0.75%) |       1   →       1              |       12.44 ms →       12.54 ms   (+0.75%) | 
  │       └ sirius::Beta_projectors                                     |        6.13 ms →        6.26 ms   (+2.16%) |       1   →       1              |        6.13 ms →        6.26 ms   (+2.16%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.56 ms →        3.67 ms   (+3.08%) |       1   →       1              |        3.56 ms →        3.67 ms   (+3.08%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.24 ms                             |       2                          |       10.48 ms                             | 
  ├ sirius::Potential                                                   |      159.81 ms →      151.13 ms   (-5.43%) |       1   →       1              |      159.81 ms →      151.13 ms   (-5.43%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.78 ms                             |       6                          |       34.69 ms                             | 
  │ └ sirius::Potential::update                                         |      124.39 ms →      121.68 ms   (-2.18%) |       1   →       1              |      124.39 ms →      121.68 ms   (-2.18%) | 
  │   └ sirius::Potential::generate_local_potential                     |      123.61 ms →      120.96 ms   (-2.15%) |       1   →       1              |      123.61 ms →      120.96 ms   (-2.15%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      112.75 ms →      109.00 ms   (-3.33%) |       1   →       1              |      112.75 ms →      109.00 ms   (-3.33%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       10.31 ms →        5.68 ms  (-44.89%) |       1   →       1              |       10.31 ms →        5.68 ms  (-44.89%) | 
  ├ sirius::Density                                                     |      129.85 ms →      129.97 ms   (+0.09%) |       1   →       1              |      129.85 ms →      129.97 ms   (+0.09%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.14 ms                             |       2                          |       10.27 ms                             | 
  │ └ sirius::Density::update                                           |      119.31 ms →      119.54 ms   (+0.20%) |       1   →       1              |      119.31 ms →      119.54 ms   (+0.20%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      118.85 ms →      119.13 ms   (+0.24%) |       1   →       1              |      118.85 ms →      119.13 ms   (+0.24%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      113.35 ms →      111.25 ms   (-1.86%) |       1   →       1              |      113.35 ms →      111.25 ms   (-1.86%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        5.04 ms →        5.79 ms  (+14.94%) |       1   →       1              |        5.04 ms →        5.79 ms  (+14.94%) | 
  ├ sirius::Density::initial_density                                    |      164.20 ms →      167.29 ms   (+1.88%) |       1   →       1              |      164.20 ms →      167.29 ms   (+1.88%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      111.24 ms →      109.10 ms   (-1.93%) |       1   →       1              |      111.24 ms →      109.10 ms   (-1.93%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.14 ms →        6.36 ms  (+23.73%) |       2   →       2              |       10.28 ms →       12.72 ms  (+23.73%) | 
- │ └ sirius::Periodic_function::integrate                              |        9.76 ms →       12.16 ms  (+24.66%) |       1   →       1              |        9.76 ms →       12.16 ms  (+24.66%) | 
  ├ sirius::Potential::generate                                         |      693.46 ms →      679.67 ms   (-1.99%) |       1   →       1              |      693.46 ms →      679.67 ms   (-1.99%) | 
  │ ├ sirius::Potential::poisson                                        |      127.08 ms →      133.84 ms   (+5.32%) |       1   →       1              |      127.08 ms →      133.84 ms   (+5.32%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.79 ms →        6.72 ms  (+16.08%) |       1   →       1              |        5.79 ms →        6.72 ms  (+16.08%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       11.00 ms                             |       1                          |       11.00 ms                             | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |       10.72 ms                             |       1                          |       10.72 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |       10.72 ms                             |       1                          |       10.72 ms                             | 
  │ │ └ sirius::inner                                                   |                        17.41 ms            |                   1              |                        17.41 ms            | 
+ │ ├ sirius::Periodic_function::add                                    |      556.66 μs →      456.25 μs  (-18.04%) |       2   →       2              |        1.11 ms →      912.50 μs  (-18.04%) | 
+ │ ├ sirius::Potential::xc                                             |       59.88 ms →       39.12 ms  (-34.67%) |       1   →       1              |       59.88 ms →       39.12 ms  (-34.67%) | 
+ │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       59.87 ms →       36.81 ms  (-38.52%) |       1   →       1              |       59.87 ms →       36.81 ms  (-38.52%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.66 ms                             |       2                          |       11.32 ms                             | 
  │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        5.82 ms                             |       1                          |        5.82 ms                             | 
  │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                    |                        12.14 ms            |                   2              |                        24.28 ms            | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.92 ms →        4.97 ms  (-15.92%) |       1   →       1              |        5.92 ms →        4.97 ms  (-15.92%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       93.65 ms →       93.75 ms   (+0.10%) |       1   →       1              |       93.65 ms →       93.75 ms   (+0.10%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      404.47 ms →      403.10 ms   (-0.34%) |       1   →       1              |      404.47 ms →      403.10 ms   (-0.34%) | 
- ├ sirius::Hamiltonian0                                                |        8.68 ms →       11.82 ms  (+36.07%) |       1   →       1              |        8.68 ms →       11.82 ms  (+36.07%) | 
  │ ├ sirius::Local_operator                                            |        8.33 ms →        8.02 ms   (-3.78%) |       1   →       1              |        8.33 ms →        8.02 ms   (-3.78%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.76 ms                             |       1                          |        4.76 ms                             | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.64 ms →        2.39 ms   (-9.75%) |       1   →       1              |        2.64 ms →        2.39 ms   (-9.75%) | 
  │ ├ sirius::Non_local_operator                                        |       63.11 μs →       63.31 μs   (+0.31%) |       2   →       2              |      126.22 μs →      126.61 μs   (+0.31%) | 
- │ ├ sirius::D_operator::initialize                                    |       96.49 μs →        1.23 ms (+1177.29%) |       1   →       1              |       96.49 μs →        1.23 ms (+1177.29%) | 
- │ └ sirius::Q_operator::initialize                                    |       75.49 μs →        2.38 ms (+3056.83%) |       1   →       1              |       75.49 μs →        2.38 ms (+3056.83%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.84 s  →        1.87 s    (+1.20%) |       1   →       1              |        1.84 s  →        1.87 s    (+1.20%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.69 ms →       18.67 ms   (-0.13%) |       1   →       1              |       18.69 ms →       18.67 ms   (-0.13%) | 
+ │ │ ├ sirius::Local_operator::prepare_k                               |      195.96 μs →      171.01 μs  (-12.74%) |       1   →       1              |      195.96 μs →      171.01 μs  (-12.74%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       18.50 ms →       18.49 ms   (-0.01%) |       1   →       1              |       18.50 ms →       18.49 ms   (-0.01%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.82 s  →        1.84 s    (+1.12%) |       1   →       1              |        1.82 s  →        1.84 s    (+1.12%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      125.92 ms                             |       4                          |      503.67 ms                             | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       52.30 ms →       51.98 ms   (-0.63%) |       1   →       1              |       52.30 ms →       51.98 ms   (-0.63%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.02 ms →       21.05 ms   (+0.11%) |       1   →       1              |       21.02 ms →       21.05 ms   (+0.11%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      636.29 ms →      637.52 ms   (+0.19%) |       1   →       1              |      636.29 ms →      637.52 ms   (+0.19%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      297.42 ms →      297.85 ms   (+0.15%) |       1   →       1              |      297.42 ms →      297.85 ms   (+0.15%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.08 μs →        3.23 μs   (+4.83%) |       1   →       1              |        3.08 μs →        3.23 μs   (+4.83%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.19 μs                             |       1                          |        2.19 μs                             | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      391.00 ns                             |       1                          |      391.00 ns                             | 
- │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      538.00 ns →      628.00 ns  (+16.73%) |       1   →       1              |      538.00 ns →      628.00 ns  (+16.73%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.22 ms →        9.23 ms   (+0.02%) |       1   →       1              |        9.22 ms →        9.23 ms   (+0.02%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      121.07 ms →      121.23 ms   (+0.13%) |       1   →       1              |      121.07 ms →      121.23 ms   (+0.13%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      104.27 ms →      104.58 ms   (+0.30%) |       2   →       2              |      208.54 ms →      209.16 ms   (+0.30%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       38.57 ms →       40.10 ms   (+3.98%) |       2   →       2              |       77.14 ms →       80.20 ms   (+3.98%) | 
  │ │ │ ├ sddk::inner                                                   |       38.00 ms                             |       2                          |       76.01 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       23.88 μs                             |       2                          |       47.76 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        39.54 ms            |                   2              |                        79.07 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        63.00 ns            |                   2              |                       126.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        39.06 ms            |                   2              |                        78.11 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                       398.50 ns            |                   2              |                       797.00 ns            | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       56.30 ms →       57.08 ms   (+1.39%) |       1   →       1              |       56.30 ms →       57.08 ms   (+1.39%) | 
  │ │ ├ sddk::transform                                                 |       31.57 ms                             |       1                          |       31.57 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       11.60 μs                             |       1                          |       11.60 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       11.80 μs                             |       1                          |       11.80 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                        30.99 ms            |                   1              |                        30.99 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                        30.99 ms            |                   1              |                        30.99 ms            | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      795.00 ns →      489.00 ns  (-38.49%) |       1   →       1              |      795.00 ns →      489.00 ns  (-38.49%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |      159.10 s  →      116.86 s   (-26.55%) |       1   →       1              |      159.10 s  →      116.86 s   (-26.55%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.82 ms                             |      19                          |      110.58 ms                             | 
  │ ├ sirius::Density                                                   |                       150.28 ms            |                   1              |                       150.28 ms            | 
  │ │ └ sirius::Density::update                                         |                       139.64 ms            |                   1              |                       139.64 ms            | 
  │ │   └ sirius::Density::generate_pseudo_core_charge_density          |                       139.22 ms            |                   1              |                       139.22 ms            | 
  │ │     ├ sirius::Simulation_context::make_periodic_function          |                       111.26 ms            |                   1              |                       111.26 ms            | 
  │ │     └ sirius::Smooth_periodic_function::fft_transform             |                         5.69 ms            |                   1              |                         5.69 ms            | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.81 s  →        4.65 s    (-3.33%) |      33   →      25    (-24.24%) |      158.77 s  →      116.27 s   (-26.77%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        5.48 ms →        7.91 ms  (+44.45%) |      33   →      25    (-24.24%) |      180.71 ms →      197.75 ms   (+9.43%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        5.11 ms →        4.09 ms  (-19.91%) |      33   →      25    (-24.24%) |      168.66 ms →      102.33 ms  (-39.32%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      972.16 μs                             |      33                          |       32.08 ms                             | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.25 ms →        2.21 ms  (-32.03%) |      33   →      25    (-24.24%) |      107.36 ms →       55.28 ms  (-48.51%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |       64.52 μs →       64.71 μs   (+0.28%) |      66   →      50    (-24.24%) |        4.26 ms →        3.24 ms  (-24.03%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |       92.67 μs →        1.24 ms (+1234.15%) |      33   →      25    (-24.24%) |        3.06 ms →       30.91 ms (+910.72%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       75.17 μs →        2.38 ms (+3071.27%) |      33   →      25    (-24.24%) |        2.48 ms →       59.60 ms (+2302.48%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.72 s  →        2.64 s    (-2.83%) |      33   →      25    (-24.24%) |       89.76 s  →       66.08 s   (-26.38%) | 
+ │ │ │ ├ sirius::Hamiltonian_k                                         |      158.22 μs →      170.14 μs   (+7.53%) |      33   →      25    (-24.24%) |        5.22 ms →        4.25 ms  (-18.54%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      152.57 μs →      161.03 μs   (+5.55%) |      33   →      25    (-24.24%) |        5.03 ms →        4.03 ms  (-20.04%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.06 μs →        4.95 μs  (+22.04%) |      33   →      25    (-24.24%) |      133.88 μs →      123.78 μs   (-7.54%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.66 s  →        2.41 s    (-9.15%) |      33   →      25    (-24.24%) |       87.64 s  →       60.32 s   (-31.17%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |      104.23 ms                             |      33                          |        3.44 s                              | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        9.03 ms                             |     198                          |        1.79 s                              | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        5.98 ms →        5.93 ms   (-0.97%) |      33   →      25    (-24.24%) |      197.45 ms →      148.13 ms  (-24.98%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      352.61 μs                             |      33                          |       11.64 ms                             | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.30 ms                             |      66                          |      152.09 ms                             | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.51 s                              |      33                          |       82.82 s                              | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::apply_h_s                          |      104.54 ms                             |     360                          |       37.63 s                              | 
  │ │ │ │ │ │ ├ sirius::Local_operator::apply_h                         |       40.15 ms                             |     360                          |       14.45 s                              | 
  │ │ │ │ │ │ │ ├ sddk::matrix_storage::remap_forward                   |        1.75 μs                             |     360                          |      629.65 μs                             | 
  │ │ │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.48 μs                             |     360                          |      532.54 μs                             | 
  │ │ │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                   |      303.76 ns                             |     360                          |      109.36 μs                             | 
  │ │ │ │ │ │ │ └ sddk::matrix_storage::remap_backward                  |      369.64 ns                             |     360                          |      133.07 μs                             | 
  │ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                  |        7.34 ms                             |     360                          |        2.64 s                              | 
  │ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                     |       18.94 ms                             |     360                          |        6.82 s                              | 
  │ │ │ │ │ │ └ sirius::Non_local_operator::apply                       |       19.05 ms                             |     720                          |       13.71 s                              | 
  │ │ │ │ │ ├ sddk::orthogonalize                                       |       34.39 ms                             |     360                          |       12.38 s                              | 
  │ │ │ │ │ │ ├ sddk::inner                                             |        4.34 ms                             |     687                          |        2.98 s                              | 
  │ │ │ │ │ │ │ └ sddk::inner|local                                     |       20.50 μs                             |     687                          |       14.08 ms                             | 
  │ │ │ │ │ │ ├ sddk::orthogonalize|tmtrx                               |        5.45 ms                             |     360                          |        1.96 s                              | 
  │ │ │ │ │ │ ├ sddk::orthogonalize|transform                           |        7.91 ms                             |     360                          |        2.85 s                              | 
  │ │ │ │ │ │ └ sddk::transform                                         |       14.03 ms                             |     327                          |        4.59 s                              | 
  │ │ │ │ │ │   ├ sddk::transform|init                                  |       17.65 μs                             |     327                          |        5.77 ms                             | 
  │ │ │ │ │ │   └ sddk::transform|local                                 |       32.53 μs                             |     981                          |       31.91 ms                             | 
  │ │ │ │ │ ├ sirius::Band::set_subspace_mtrx                           |        9.29 ms                             |     360                          |        3.35 s                              | 
  │ │ │ │ │ │ └ sddk::inner                                             |        8.41 ms                             |     360                          |        3.03 s                              | 
  │ │ │ │ │ │   └ sddk::inner|local                                     |       27.46 μs                             |     360                          |        9.88 ms                             | 
  │ │ │ │ │ ├ Eigensolver_cuda|zheevdx                                  |       63.34 ms                             |     360                          |       22.80 s                              | 
  │ │ │ │ │ ├ sirius::residuals                                         |       13.48 ms                             |     348                          |        4.69 s                              | 
  │ │ │ │ │ │ ├ sddk::transform                                         |       12.49 ms                             |     334                          |        4.17 s                              | 
  │ │ │ │ │ │ │ ├ sddk::transform|init                                  |       14.40 μs                             |     334                          |        4.81 ms                             | 
  │ │ │ │ │ │ │ └ sddk::transform|local                                 |       34.61 μs                             |     668                          |       23.12 ms                             | 
  │ │ │ │ │ │ └ sirius::normalized_preconditioned_residuals             |        1.34 ms                             |     334                          |      447.81 ms                             | 
  │ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       55.76 ms                             |      35                          |        1.95 s                              | 
  │ │ │ │ │   └ sddk::transform                                         |       52.53 ms                             |      37                          |        1.94 s                              | 
  │ │ │ │ │     ├ sddk::transform|init                                  |       12.24 μs                             |      37                          |      453.00 μs                             | 
  │ │ │ │ │     └ sddk::transform|local                                 |       13.63 μs                             |      39                          |      531.46 μs                             | 
  │ │ │ │ ├ sirius::Hamiltonian_k::apply_h_s                            |                       107.80 ms            |                 312              |                        33.63 s             | 
  │ │ │ │ │ ├ sirius::Local_operator::apply_h                           |                        41.58 ms            |                 312              |                        12.97 s             | 
  │ │ │ │ │ │ ├ sddk::matrix_storage::remap_forward                     |                         1.77 μs            |                 312              |                       552.86 μs            | 
  │ │ │ │ │ │ └ sddk::matrix_storage::remap_backward                    |                       471.08 ns            |                 312              |                       146.98 μs            | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |                         7.35 ms            |                 312              |                         2.29 s             | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |                        19.37 ms            |                 312              |                         6.04 s             | 
  │ │ │ │ │ └ sirius::Non_local_operator::apply                         |                        19.74 ms            |                 624              |                        12.32 s             | 
  │ │ │ │ ├ sddk::orthogonalize                                         |                        32.43 ms            |                 312              |                        10.12 s             | 
  │ │ │ │ │ ├ sddk::wf_inner                                            |                         4.97 ms            |                 599              |                         2.98 s             | 
  │ │ │ │ │ │ ├ sddk::wf_inner|scale                                    |                       102.62 ns            |                 599              |                        61.47 μs            | 
  │ │ │ │ │ │ ├ sddk::wf_inner|pw                                       |                         3.86 ms            |                 599              |                         2.31 s             | 
  │ │ │ │ │ │ └ sddk::wf_inner|scale_back                               |                       246.80 ns            |                 599              |                       147.83 μs            | 
  │ │ │ │ │ ├ sddk::orthogonalize|tmtrx                                 |                         5.19 ms            |                 312              |                         1.62 s             | 
  │ │ │ │ │ ├ sddk::orthogonalize|transform                             |                         7.91 ms            |                 312              |                         2.47 s             | 
  │ │ │ │ │ └ sddk::wf_trans                                            |                        10.62 ms            |                 287              |                         3.05 s             | 
  │ │ │ │ │   └ sddk::wf_trans|pw                                       |                         3.54 ms            |                 861              |                         3.05 s             | 
  │ │ │ │ ├ sirius::Band::set_subspace_mtrx                             |                         8.42 ms            |                 312              |                         2.63 s             | 
  │ │ │ │ │ └ sddk::wf_inner                                            |                         8.02 ms            |                 312              |                         2.50 s             | 
  │ │ │ │ │   ├ sddk::wf_inner|scale                                    |                       122.82 ns            |                 312              |                        38.32 μs            | 
  │ │ │ │ │   ├ sddk::wf_inner|pw                                       |                         6.91 ms            |                 312              |                         2.15 s             | 
  │ │ │ │ │   └ sddk::wf_inner|scale_back                               |                       211.65 ns            |                 312              |                        66.03 μs            | 
  │ │ │ │ ├ Eigensolver_cuda|zheevdx                                    |                        13.27 ms            |                 312              |                         4.14 s             | 
  │ │ │ │ ├ sirius::residuals                                           |                         7.85 ms            |                 302              |                         2.37 s             | 
  │ │ │ │ │ ├ sddk::wf_trans                                            |                         6.66 ms            |                 287              |                         1.91 s             | 
  │ │ │ │ │ │ └ sddk::wf_trans|pw                                       |                         3.33 ms            |                 574              |                         1.91 s             | 
  │ │ │ │ │ └ sirius::normalized_preconditioned_residuals               |                         1.21 ms            |                 287              |                       346.67 ms            | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|update_phi     |                        42.98 ms            |                  92              |                         3.95 s             | 
  │ │ │ │   └ sddk::wf_trans                                            |                        24.61 ms            |                 159              |                         3.91 s             | 
  │ │ │ │     └ sddk::wf_trans|pw                                       |                        17.31 ms            |                 226              |                         3.91 s             | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      489.42 ns →      458.60 ns   (-6.30%) |      33   →      25    (-24.24%) |       16.15 μs →       11.46 μs  (-29.01%) | 
  │ │ │ ├ sirius::K_point_set::sync_band_energies                       |       30.62 μs                             |      33                          |        1.01 ms                             | 
  │ │ │ └ sirius::K_point_set::sync_band                                |                        97.16 μs            |                  25              |                         2.43 ms            | 
+ │ │ ├ sirius::K_point_set::find_band_occupancies                      |      601.32 μs →      456.12 μs  (-24.15%) |      33   →      25    (-24.24%) |       19.84 ms →       11.40 ms  (-42.54%) | 
  │ │ │ └ sirius::K_point_set::sync_band                                |                        29.20 μs            |                  25              |                       730.09 μs            | 
+ │ │ ├ sirius::Density::generate                                       |      773.90 ms →      760.42 ms   (-1.74%) |      33   →      25    (-24.24%) |       25.54 s  →       19.01 s   (-25.56%) | 
+ │ │ │ ├ sirius::Density::generate_valence                             |      401.24 ms →      405.01 ms   (+0.94%) |      33   →      25    (-24.24%) |       13.24 s  →       10.13 s   (-23.53%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.02 μs →        2.39 μs  (-70.21%) |      33   →      25    (-24.24%) |      264.75 μs →       59.74 μs  (-77.43%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.35 μs                             |      33                          |      242.57 μs                             | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       99.84 ms →      100.34 ms   (+0.50%) |      33   →      25    (-24.24%) |        3.29 s  →        2.51 s   (-23.87%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.32 μs →        8.96 μs  (+22.39%) |      33   →      25    (-24.24%) |      241.58 μs →      224.00 μs   (-7.28%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.12 ms →        7.12 ms   (+0.01%) |      33   →      25    (-24.24%) |      234.92 ms →      177.99 ms  (-24.23%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       90.83 ms →       91.32 ms   (+0.54%) |      33   →      25    (-24.24%) |        3.00 s  →        2.28 s   (-23.83%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      622.33 ns →      575.36 ns   (-7.55%) |      33   →      25    (-24.24%) |       20.54 μs →       14.38 μs  (-29.96%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      163.07 ms →      164.35 ms   (+0.78%) |      33   →      25    (-24.24%) |        5.38 s  →        4.11 s   (-23.65%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.65 ms →        1.65 ms   (-0.06%) |      33   →      25    (-24.24%) |       54.39 ms →       41.18 ms  (-24.29%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |       88.27 ms →       88.41 ms   (+0.15%) |      33   →      25    (-24.24%) |        2.91 s  →        2.21 s   (-24.13%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.05 ms →       88.17 ms   (+0.14%) |      33   →      25    (-24.24%) |        2.91 s  →        2.20 s   (-24.14%) | 
+ │ │ │ ├ sirius::Field4D::symmetrize                                   |      277.83 ms →      262.07 ms   (-5.67%) |      33   →      25    (-24.24%) |        9.17 s  →        6.55 s   (-28.54%) | 
+ │ │ │ │ └ sirius::symmetrize_function|fpw                             |      277.83 ms →      262.06 ms   (-5.68%) |      33   →      25    (-24.24%) |        9.17 s  →        6.55 s   (-28.54%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.80 ms →       25.14 ms   (+1.37%) |      33   →      25    (-24.24%) |      818.38 ms →      628.50 ms  (-23.20%) | 
+ │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      228.69 ms →      210.88 ms   (-7.79%) |      33   →      25    (-24.24%) |        7.55 s  →        5.27 s   (-30.14%) | 
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       23.14 ms →       24.88 ms   (+7.52%) |      33   →      25    (-24.24%) |      763.57 ms →      621.94 ms  (-18.55%) | 
+ │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       80.83 ms →       81.57 ms   (+0.92%) |      33   →      25    (-24.24%) |        2.67 s  →        2.04 s   (-23.54%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |       10.43 ms →        8.10 ms  (-22.41%) |      33   →      25    (-24.24%) |      344.32 ms →      202.39 ms  (-41.22%) | 
  │ │ ├ sirius::inner                                                   |                        10.91 ms            |                 300              |                         3.27 s             | 
+ │ │ ├ sirius::Density::mix                                            |      233.90 ms →      156.00 ms  (-33.31%) |      33   →      25    (-24.24%) |        7.72 s  →        3.90 s   (-49.47%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      966.11 μs →        1.12 ms  (+15.75%) |      33   →      25    (-24.24%) |       31.88 ms →       27.96 ms  (-12.31%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       11.16 ms                             |     439                          |        4.90 s                              | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.82 ms                             |     439                          |        4.75 s                              | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.82 ms                             |     439                          |        4.75 s                              | 
  │ │ │ ├ sirius::inner                                                 |                        10.23 ms            |                 319              |                         3.26 s             | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        7.13 ms →        6.58 ms   (-7.75%) |      33   →      25    (-24.24%) |      235.40 ms →      164.50 ms  (-30.12%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        6.28 ms →        5.45 ms  (-13.23%) |      33   →      25    (-24.24%) |      207.29 ms →      136.26 ms  (-34.27%) | 
+ │ │ ├ sirius::Potential::generate                                     |      675.67 ms →      660.97 ms   (-2.17%) |      33   →      25    (-24.24%) |       22.30 s  →       16.52 s   (-25.89%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |      126.84 ms →      126.97 ms   (+0.10%) |      33   →      25    (-24.24%) |        4.19 s  →        3.17 s   (-24.16%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        5.84 ms →        6.69 ms  (+14.55%) |      33   →      25    (-24.24%) |      192.61 ms →      167.14 ms  (-13.22%) | 
  │ │ │ │ ├ sirius::Periodic_function|inner                             |       10.88 ms                             |      33                          |      358.97 ms                             | 
  │ │ │ │ │ └ sirius::Periodic_function|inner_local                     |       10.57 ms                             |      33                          |      348.97 ms                             | 
  │ │ │ │ │   └ sirius::Smooth_periodic_function|inner_local            |       10.57 ms                             |      33                          |      348.95 ms                             | 
  │ │ │ │ └ sirius::inner                                               |                        10.78 ms            |                  25              |                       269.50 ms            | 
+ │ │ │ ├ sirius::Periodic_function::add                                |      552.42 μs →      456.48 μs  (-17.37%) |      66   →      50    (-24.24%) |       36.46 ms →       22.82 ms  (-37.40%) | 
+ │ │ │ ├ sirius::Potential::xc                                         |       52.24 ms →       34.60 ms  (-33.76%) |      33   →      25    (-24.24%) |        1.72 s  →      865.07 ms  (-49.82%) | 
+ │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       52.24 ms →       32.22 ms  (-38.33%) |      33   →      25    (-24.24%) |        1.72 s  →      805.40 ms  (-53.28%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        1.25 ms                             |      66                          |       82.53 ms                             | 
  │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |       11.63 ms                             |      33                          |      383.94 ms                             | 
  │ │ │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                |                        11.82 ms            |                  50              |                       591.14 ms            | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        7.84 ms →        5.25 ms  (-33.03%) |      33   →      25    (-24.24%) |      258.64 ms →      131.22 ms  (-49.27%) | 
+ │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.94 ms →       90.93 ms   (-0.01%) |      33   →      25    (-24.24%) |        3.00 s  →        2.27 s   (-24.25%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      395.40 ms →      398.41 ms   (+0.76%) |      33   →      25    (-24.24%) |       13.05 s  →        9.96 s   (-23.67%) | 
+ │ │ ├ sirius::Field4D::symmetrize                                     |      280.93 ms →      257.72 ms   (-8.26%) |      33   →      25    (-24.24%) |        9.27 s  →        6.44 s   (-30.50%) | 
+ │ │ │ └ sirius::symmetrize_function|fpw                               |      280.93 ms →      257.71 ms   (-8.27%) |      33   →      25    (-24.24%) |        9.27 s  →        6.44 s   (-30.50%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.01 ms →       24.23 ms  (-10.29%) |      33   →      25    (-24.24%) |      891.23 ms →      605.69 ms  (-32.04%) | 
+ │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      228.66 ms →      208.77 ms   (-8.70%) |      33   →      25    (-24.24%) |        7.55 s  →        5.22 s   (-30.83%) | 
+ │ │ │   └ sddk::Gvec_shells::remap_backward                           |       24.12 ms →       23.56 ms   (-2.29%) |      33   →      25    (-24.24%) |      795.82 ms →      589.11 ms  (-25.97%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.63 ms →        5.76 ms   (+2.35%) |      33   →      25    (-24.24%) |      185.73 ms →      144.01 ms  (-22.46%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.64 ms                             |     231                          |        2.46 s                              | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |       10.34 ms                             |     231                          |        2.39 s                              | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |       10.34 ms                             |     231                          |        2.39 s                              | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.12 ms                             |      99                          |        1.00 s                              | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        9.83 ms                             |      99                          |      973.21 ms                             | 
+ │ │ ├ sirius::Periodic_function::integrate                            |        9.98 ms →       10.11 ms   (+1.29%) |      33   →      25    (-24.24%) |      329.27 ms →      252.67 ms  (-23.26%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      115.94 μs →       13.56 ms (+11598.84%) |      33   →      25    (-24.24%) |        3.83 ms →      339.09 ms (+8762.76%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      110.54 μs →       13.56 ms (+12164.20%) |      33   →      25    (-24.24%) |        3.65 ms →      338.93 ms (+9191.06%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.22 ms →        4.75 ms   (-9.00%) |       2   →       2              |       10.44 ms →        9.50 ms   (-9.00%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.54 ms                             |       6                          |       63.25 ms                             | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.23 ms                             |       6                          |       61.35 ms                             | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.23 ms                             |       6                          |       61.35 ms                             | 
  │ ├ sirius::Smooth_periodic_function|inner                            |       10.04 ms                             |       3                          |       30.11 ms                             | 
  │ │ └ sirius::Smooth_periodic_function|inner_local                    |        9.69 ms                             |       3                          |       29.08 ms                             | 
  │ └ sirius::inner                                                     |                        10.55 ms            |                   9              |                        94.98 ms            | 
  ├ sirius::Periodic_function|inner                                     |       11.09 ms                             |       2                          |       22.18 ms                             | 
  │ └ sirius::Periodic_function|inner_local                             |       10.42 ms                             |       2                          |       20.85 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.42 ms                             |       2                          |       20.85 ms                             | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.08 ms                             |       1                          |       10.08 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        9.94 ms                             |       1                          |        9.94 ms                             | 
  ├ sirius::inner                                                       |                        10.76 ms            |                   3              |                        32.29 ms            | 
  └ sirius::finalize                                                    |      216.91 ms →      203.24 ms   (-6.30%) |       1   →       1              |      216.91 ms →      203.24 ms   (-6.30%) | 
  ====================================================================================================================================================================================================
```
