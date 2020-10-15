# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      131.60 s  →      128.99 s    (-1.99%) |       1   →       1              |      131.60 s  →      128.99 s    (-1.99%) | 
  ├ sirius::initialize                                                  |        2.69 s  →        2.72 s    (+1.03%) |       1   →       1              |        2.69 s  →        2.72 s    (+1.03%) | 
- ├ sirius::Simulation_context::initialize                              |        3.01 s  →        3.67 s   (+21.86%) |       1   →       1              |        3.01 s  →        3.67 s   (+21.86%) | 
- │ ├ sirius::Simulation_context::init_comm                             |       33.97 ms →      248.14 ms (+630.45%) |       1   →       1              |       33.97 ms →      248.14 ms (+630.45%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      224.77 ms →      679.55 ms (+202.33%) |       1   →       1              |      224.77 ms →      679.55 ms (+202.33%) | 
- │ │ ├ sirius::Atom_type::init                                         |      100.91 ms →      327.85 ms (+224.89%) |       2   →       2              |      201.82 ms →      655.69 ms (+224.89%) | 
  │ │ └ sirius::Unit_cell::update                                       |       22.87 ms →       23.78 ms   (+3.97%) |       1   →       1              |       22.87 ms →       23.78 ms   (+3.97%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.67 ms →        6.34 ms   (-4.89%) |       1   →       1              |        6.67 ms →        6.34 ms   (-4.89%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       16.15 ms →       17.39 ms   (+7.67%) |       1   →       1              |       16.15 ms →       17.39 ms   (+7.67%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       16.13 ms →       17.37 ms   (+7.69%) |       1   →       1              |       16.13 ms →       17.37 ms   (+7.69%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.17 ms →        4.14 ms   (-0.83%) |       1   →       1              |        4.17 ms →        4.14 ms   (-0.83%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.34 ms   (+0.58%) |       1   →       1              |        2.33 ms →        2.34 ms   (+0.58%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      101.15 μs →      107.60 μs   (+6.38%) |       1   →       1              |      101.15 μs →      107.60 μs   (+6.38%) | 
  │ └ sirius::Simulation_context::update                                |        2.71 s  →        2.70 s    (-0.38%) |       1   →       1              |        2.71 s  →        2.70 s    (-0.38%) | 
  │   ├ sirius::Unit_cell::update                                       |       11.03 ms →       10.71 ms   (-2.99%) |       1   →       1              |       11.03 ms →       10.71 ms   (-2.99%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.46 ms →        4.30 ms   (-3.68%) |       1   →       1              |        4.46 ms →        4.30 ms   (-3.68%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.54 ms →        6.37 ms   (-2.56%) |       1   →       1              |        6.54 ms →        6.37 ms   (-2.56%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.52 ms →        6.35 ms   (-2.54%) |       1   →       1              |        6.52 ms →        6.35 ms   (-2.54%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        4.02 ms →        3.86 ms   (-3.97%) |       1   →       1              |        4.02 ms →        3.86 ms   (-3.97%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.33 ms   (-0.16%) |       1   →       1              |        2.33 ms →        2.33 ms   (-0.16%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      100.97 μs →      102.48 μs   (+1.50%) |       1   →       1              |      100.97 μs →      102.48 μs   (+1.50%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       62.66 ms →       64.44 ms   (+2.84%) |       2   →       2              |      125.32 ms →      128.89 ms   (+2.84%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.14 ms →        5.42 ms   (+5.31%) |       2   →       2              |       10.28 ms →       10.83 ms   (+5.31%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.48 ms →        4.53 ms   (+1.21%) |       1   →       1              |        4.48 ms →        4.53 ms   (+1.21%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.70 ms →       21.78 ms   (+0.37%) |       2   →       2              |       43.40 ms →       43.56 ms   (+0.37%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.85 ms →       14.82 ms   (-0.22%) |       2   →       2              |       29.71 ms →       29.64 ms   (-0.22%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.75 ms →       19.79 ms   (+0.25%) |       4   →       4              |       78.98 ms →       79.18 ms   (+0.25%) | 
  │   ├ sddk::Gvec::init                                                |      171.29 ms →      171.04 ms   (-0.15%) |       2   →       2              |      342.59 ms →      342.08 ms   (-0.15%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      128.87 ms →      128.35 ms   (-0.40%) |       2   →       2              |      257.73 ms →      256.69 ms   (-0.40%) | 
  │   ├ sddk::Gvec_shells                                               |      172.61 ms →      175.54 ms   (+1.70%) |       1   →       1              |      172.61 ms →      175.54 ms   (+1.70%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.31 ms →        1.33 ms   (+1.73%) |       1   →       1              |        1.31 ms →        1.33 ms   (+1.73%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      293.82 ms →      293.66 ms   (-0.06%) |       2   →       2              |      587.64 ms →      587.32 ms   (-0.06%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       35.79 ms →       35.62 ms   (-0.48%) |       1   →       1              |       35.79 ms →       35.62 ms   (-0.48%) | 
- │ ├ sirius::K_point::K_point                                          |        1.94 μs →        2.23 μs  (+15.22%) |       4   →       4              |        7.74 μs →        8.92 μs  (+15.22%) | 
  │ └ sirius::K_point_set::initialize                                   |       35.68 ms →       35.52 ms   (-0.47%) |       1   →       1              |       35.68 ms →       35.52 ms   (-0.47%) | 
  │   └ sirius::K_point::initialize                                     |       35.52 ms →       35.40 ms   (-0.33%) |       1   →       1              |       35.52 ms →       35.40 ms   (-0.33%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       18.38 ms →       18.01 ms   (-1.98%) |       1   →       1              |       18.38 ms →       18.01 ms   (-1.98%) | 
  │     │ └ sddk::Gvec::init                                            |        8.25 ms →        8.10 ms   (-1.76%) |       1   →       1              |        8.25 ms →        8.10 ms   (-1.76%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        9.65 μs →        9.13 μs   (-5.39%) |       1   →       1              |        9.65 μs →        9.13 μs   (-5.39%) | 
  │     └ sirius::K_point::update                                       |       12.35 ms →       12.56 ms   (+1.66%) |       1   →       1              |       12.35 ms →       12.56 ms   (+1.66%) | 
  │       └ sirius::Beta_projectors                                     |        6.09 ms →        6.34 ms   (+4.01%) |       1   →       1              |        6.09 ms →        6.34 ms   (+4.01%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.51 ms →        3.73 ms   (+6.43%) |       1   →       1              |        3.51 ms →        3.73 ms   (+6.43%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.20 ms →        5.35 ms   (+2.75%) |       2   →       2              |       10.41 ms →       10.70 ms   (+2.75%) | 
  ├ sirius::Potential                                                   |      159.22 ms →      159.11 ms   (-0.07%) |       1   →       1              |      159.22 ms →      159.11 ms   (-0.07%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.75 ms →        5.82 ms   (+1.26%) |       6   →       6              |       34.47 ms →       34.91 ms   (+1.26%) | 
  │ └ sirius::Potential::update                                         |      123.95 ms →      123.48 ms   (-0.38%) |       1   →       1              |      123.95 ms →      123.48 ms   (-0.38%) | 
  │   └ sirius::Potential::generate_local_potential                     |      123.23 ms →      122.77 ms   (-0.38%) |       1   →       1              |      123.23 ms →      122.77 ms   (-0.38%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      110.65 ms →      109.01 ms   (-1.48%) |       1   →       1              |      110.65 ms →      109.01 ms   (-1.48%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |       11.68 ms →       12.86 ms  (+10.10%) |       1   →       1              |       11.68 ms →       12.86 ms  (+10.10%) | 
  ├ sirius::Density                                                     |      134.12 ms →      134.63 ms   (+0.38%) |       1   →       1              |      134.12 ms →      134.63 ms   (+0.38%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.17 ms →        5.16 ms   (-0.29%) |       2   →       2              |       10.34 ms →       10.31 ms   (-0.29%) | 
  │ └ sirius::Density::update                                           |      123.51 ms →      124.04 ms   (+0.43%) |       1   →       1              |      123.51 ms →      124.04 ms   (+0.43%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      123.07 ms →      123.60 ms   (+0.43%) |       1   →       1              |      123.07 ms →      123.60 ms   (+0.43%) | 
+ │     ├ sirius::rho_core_ri_pseudo|values                             |      132.84 μs →      101.86 μs  (-23.32%) |       1   →       1              |      132.84 μs →      101.86 μs  (-23.32%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      112.50 ms →      112.43 ms   (-0.06%) |       1   →       1              |      112.50 ms →      112.43 ms   (-0.06%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |       10.00 ms →       10.61 ms   (+6.18%) |       1   →       1              |       10.00 ms →       10.61 ms   (+6.18%) | 
  ├ sirius::Density::initial_density                                    |      175.47 ms →      173.60 ms   (-1.07%) |       1   →       1              |      175.47 ms →      173.60 ms   (-1.07%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      110.26 ms →      111.64 ms   (+1.25%) |       1   →       1              |      110.26 ms →      111.64 ms   (+1.25%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |       10.79 ms →        9.86 ms   (-8.65%) |       2   →       2              |       21.58 ms →       19.72 ms   (-8.65%) | 
  │ └ sirius::Periodic_function::integrate                              |       10.25 ms →        9.71 ms   (-5.29%) |       1   →       1              |       10.25 ms →        9.71 ms   (-5.29%) | 
  ├ sirius::Potential::generate                                         |      590.94 ms →      592.87 ms   (+0.33%) |       1   →       1              |      590.94 ms →      592.87 ms   (+0.33%) | 
  │ ├ sirius::Potential::poisson                                        |      136.30 ms →      136.52 ms   (+0.16%) |       1   →       1              |      136.30 ms →      136.52 ms   (+0.16%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       16.52 ms →       16.48 ms   (-0.26%) |       1   →       1              |       16.52 ms →       16.48 ms   (-0.26%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        9.90 ms →       10.21 ms   (+3.07%) |       1   →       1              |        9.90 ms →       10.21 ms   (+3.07%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        9.88 ms →        9.81 ms   (-0.73%) |       1   →       1              |        9.88 ms →        9.81 ms   (-0.73%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.88 ms →        9.80 ms   (-0.76%) |       1   →       1              |        9.88 ms →        9.80 ms   (-0.76%) | 
  │ ├ sirius::Periodic_function::add                                    |      548.48 μs →      538.87 μs   (-1.75%) |       2   →       2              |        1.10 ms →        1.08 ms   (-1.75%) | 
  │ ├ sirius::Potential::xc                                             |       53.77 ms →       53.57 ms   (-0.37%) |       1   →       1              |       53.77 ms →       53.57 ms   (-0.37%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.46 ms →       51.23 ms   (-0.45%) |       1   →       1              |       51.46 ms →       51.23 ms   (-0.45%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.55 ms →        5.71 ms   (+2.76%) |       2   →       2              |       11.11 ms →       11.41 ms   (+2.76%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.46 ms →        5.15 ms   (-5.71%) |       1   →       1              |        5.46 ms →        5.15 ms   (-5.71%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.70 ms →        6.28 ms  (+10.20%) |       1   →       1              |        5.70 ms →        6.28 ms  (+10.20%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.65 ms →       93.55 ms   (+0.98%) |       1   →       1              |       92.65 ms →       93.55 ms   (+0.98%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      300.08 ms →      300.52 ms   (+0.15%) |       1   →       1              |      300.08 ms →      300.52 ms   (+0.15%) | 
  ├ sirius::Hamiltonian0                                                |        8.41 ms →        9.06 ms   (+7.67%) |       1   →       1              |        8.41 ms →        9.06 ms   (+7.67%) | 
  │ ├ sirius::Local_operator                                            |        8.06 ms →        8.71 ms   (+8.02%) |       1   →       1              |        8.06 ms →        8.71 ms   (+8.02%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.72 ms →        4.75 ms   (+0.66%) |       1   →       1              |        4.72 ms →        4.75 ms   (+0.66%) | 
- │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.43 ms →        3.04 ms  (+25.19%) |       1   →       1              |        2.43 ms →        3.04 ms  (+25.19%) | 
  │ ├ sirius::Non_local_operator                                        |       63.63 μs →       62.42 μs   (-1.91%) |       2   →       2              |      127.27 μs →      124.84 μs   (-1.91%) | 
  │ ├ sirius::D_operator::initialize                                    |      100.24 μs →       96.69 μs   (-3.54%) |       1   →       1              |      100.24 μs →       96.69 μs   (-3.54%) | 
  │ └ sirius::Q_operator::initialize                                    |       74.99 μs →       75.22 μs   (+0.30%) |       1   →       1              |       74.99 μs →       75.22 μs   (+0.30%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.85 s  →        1.87 s    (+0.84%) |       1   →       1              |        1.85 s  →        1.87 s    (+0.84%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.71 ms →       18.71 ms   (+0.03%) |       1   →       1              |       18.71 ms →       18.71 ms   (+0.03%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      192.98 μs →      189.10 μs   (-2.01%) |       1   →       1              |      192.98 μs →      189.10 μs   (-2.01%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       18.51 ms →       18.52 ms   (+0.05%) |       1   →       1              |       18.51 ms →       18.52 ms   (+0.05%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.83 s  →        1.85 s    (+0.85%) |       1   →       1              |        1.83 s  →        1.85 s    (+0.85%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      128.64 ms →      129.53 ms   (+0.69%) |       4   →       4              |      514.58 ms →      518.14 ms   (+0.69%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       52.70 ms →       52.84 ms   (+0.27%) |       1   →       1              |       52.70 ms →       52.84 ms   (+0.27%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.03 ms →       21.71 ms   (+3.27%) |       1   →       1              |       21.03 ms →       21.71 ms   (+3.27%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      634.96 ms →      634.88 ms   (-0.01%) |       1   →       1              |      634.96 ms →      634.88 ms   (-0.01%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      297.94 ms →      297.64 ms   (-0.10%) |       1   →       1              |      297.94 ms →      297.64 ms   (-0.10%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.27 μs →        3.51 μs   (+7.41%) |       1   →       1              |        3.27 μs →        3.51 μs   (+7.41%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.36 μs →        2.35 μs   (-0.51%) |       1   →       1              |        2.36 μs →        2.35 μs   (-0.51%) | 
+ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      425.00 ns →      367.00 ns  (-13.65%) |       1   →       1              |      425.00 ns →      367.00 ns  (-13.65%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      468.00 ns →      478.00 ns   (+2.14%) |       1   →       1              |      468.00 ns →      478.00 ns   (+2.14%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.21 ms →        9.22 ms   (+0.10%) |       1   →       1              |        9.21 ms →        9.22 ms   (+0.10%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      120.77 ms →      120.69 ms   (-0.07%) |       1   →       1              |      120.77 ms →      120.69 ms   (-0.07%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      103.50 ms →      103.64 ms   (+0.14%) |       2   →       2              |      206.99 ms →      207.29 ms   (+0.14%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       40.13 ms →       40.09 ms   (-0.09%) |       2   →       2              |       80.25 ms →       80.18 ms   (-0.09%) | 
  │ │ │ └ sddk::wf_inner                                                |       39.59 ms →       39.55 ms   (-0.10%) |       2   →       2              |       79.18 ms →       79.11 ms   (-0.10%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       19.00 ns →       39.00 ns (+105.26%) |       2   →       2              |       38.00 ns →       78.00 ns (+105.26%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       39.11 ms →       39.08 ms   (-0.09%) |       2   →       2              |       78.23 ms →       78.15 ms   (-0.09%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       19.00 ns →       29.50 ns  (+55.26%) |       2   →       2              |       38.00 ns →       59.00 ns  (+55.26%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       56.71 ms →       55.74 ms   (-1.71%) |       1   →       1              |       56.71 ms →       55.74 ms   (-1.71%) | 
  │ │ └ sddk::wf_trans                                                  |       30.72 ms →       30.74 ms   (+0.08%) |       1   →       1              |       30.72 ms →       30.74 ms   (+0.08%) | 
  │ │   └ sddk::wf_trans|pw                                             |       30.71 ms →       30.74 ms   (+0.08%) |       1   →       1              |       30.71 ms →       30.74 ms   (+0.08%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      617.00 ns →      476.00 ns  (-22.85%) |       1   →       1              |      617.00 ns →      476.00 ns  (-22.85%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      121.88 s  →      118.55 s    (-2.74%) |       1   →       1              |      121.88 s  →      118.55 s    (-2.74%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.73 ms →        5.82 ms   (+1.56%) |      19   →      19              |      108.85 ms →      110.54 ms   (+1.56%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.86 s  →        4.67 s    (-3.93%) |      25   →      25              |      121.48 s  →      116.70 s    (-3.93%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        5.36 ms →        5.34 ms   (-0.49%) |      25   →      25              |      134.07 ms →      133.41 ms   (-0.49%) | 
  │ │ │ ├ sirius::Local_operator                                        |        5.00 ms →        4.96 ms   (-0.65%) |      25   →      25              |      124.93 ms →      124.12 ms   (-0.65%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |        1.01 ms →        1.01 ms   (+0.01%) |      25   →      25              |       25.23 ms →       25.23 ms   (+0.01%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.09 ms →        3.06 ms   (-1.09%) |      25   →      25              |       77.36 ms →       76.52 ms   (-1.09%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.28 μs →       64.99 μs   (+1.11%) |      50   →      50              |        3.21 ms →        3.25 ms   (+1.11%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       86.73 μs →       89.24 μs   (+2.90%) |      25   →      25              |        2.17 ms →        2.23 ms   (+2.90%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       77.70 μs →       79.49 μs   (+2.30%) |      25   →      25              |        1.94 ms →        1.99 ms   (+2.30%) | 
  │ │ ├ sirius::Band::solve                                             |        2.87 s  →        2.69 s    (-6.28%) |      25   →      25              |       71.81 s  →       67.30 s    (-6.28%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      157.87 μs →      156.63 μs   (-0.78%) |      25   →      25              |        3.95 ms →        3.92 ms   (-0.78%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      151.43 μs →      148.75 μs   (-1.77%) |      25   →      25              |        3.79 ms →        3.72 ms   (-1.77%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.55 μs →        5.96 μs  (+30.97%) |      25   →      25              |      113.69 μs →      148.90 μs  (+30.97%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.71 s  →        2.55 s    (-6.08%) |      25   →      25              |       67.84 s  →       63.72 s    (-6.08%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       98.28 ms →       98.96 ms   (+0.68%) |      25   →      25              |        2.46 s  →        2.47 s    (+0.68%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        8.01 ms →        8.13 ms   (+1.53%) |     150   →     150              |        1.20 s  →        1.22 s    (+1.53%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        5.94 ms →        5.93 ms   (-0.09%) |      25   →      25              |      148.38 ms →      148.24 ms   (-0.09%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      349.21 μs →      348.86 μs   (-0.10%) |      25   →      25              |        8.73 ms →        8.72 ms   (-0.10%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.31 ms →        2.31 ms   (+0.19%) |      50   →      50              |      115.36 ms →      115.58 ms   (+0.19%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.57 s  →        2.41 s    (-6.43%) |      25   →      25              |       64.34 s  →       60.20 s    (-6.43%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      125.88 ms →      132.17 ms   (+5.00%) |     277   →     266     (-3.97%) |       34.87 s  →       35.16 s    (+0.83%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       50.21 ms →       53.80 ms   (+7.15%) |     277   →     266     (-3.97%) |       13.91 s  →       14.31 s    (+2.89%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.02 μs →        2.02 μs   (-0.07%) |     277   →     266     (-3.97%) |      558.77 μs →      536.19 μs   (-4.04%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.69 μs →        1.70 μs   (+1.09%) |     277   →     266     (-3.97%) |      467.15 μs →      453.49 μs   (-2.92%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      375.20 ns →      378.34 ns   (+0.84%) |     277   →     266     (-3.97%) |      103.93 μs →      100.64 μs   (-3.17%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      453.83 ns →      512.60 ns  (+12.95%) |     277   →     266     (-3.97%) |      125.71 μs →      136.35 μs   (+8.46%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.41 ms →        7.44 ms   (+0.31%) |     277   →     266     (-3.97%) |        2.05 s  →        1.98 s    (-3.67%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       22.72 ms →       23.65 ms   (+4.10%) |     277   →     266     (-3.97%) |        6.29 s  →        6.29 s    (-0.03%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       22.76 ms →       23.63 ms   (+3.84%) |     554   →     532     (-3.97%) |       12.61 s  →       12.57 s    (-0.28%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       34.06 ms →       35.07 ms   (+2.95%) |     277   →     266     (-3.97%) |        9.44 s  →        9.33 s    (-1.14%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        5.91 ms →        6.05 ms   (+2.47%) |     529   →     507     (-4.16%) |        3.12 s  →        3.07 s    (-1.80%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       73.74 ns →       52.07 ns  (-29.38%) |     529   →     507     (-4.16%) |       39.01 μs →       26.40 μs  (-32.32%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        4.80 ms →        4.94 ms   (+2.98%) |     529   →     507     (-4.16%) |        2.54 s  →        2.50 s    (-1.30%) | 
+ │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       53.97 ns →       28.57 ns  (-47.06%) |     529   →     507     (-4.16%) |       28.55 μs →       14.49 μs  (-49.26%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      598.17 μs →      656.26 μs   (+9.71%) |     277   →     266     (-3.97%) |      165.69 ms →      174.57 ms   (+5.35%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        9.37 ms →        9.83 ms   (+4.89%) |     277   →     266     (-3.97%) |        2.60 s  →        2.61 s    (+0.73%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |       14.08 ms →       14.40 ms   (+2.24%) |     252   →     241     (-4.37%) |        3.55 s  →        3.47 s    (-2.22%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        4.69 ms →        4.80 ms   (+2.24%) |     756   →     723     (-4.37%) |        3.55 s  →        3.47 s    (-2.22%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       10.24 ms →       10.10 ms   (-1.35%) |     277   →     266     (-3.97%) |        2.84 s  →        2.69 s    (-5.27%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |        9.97 ms →        9.89 ms   (-0.83%) |     277   →     266     (-3.97%) |        2.76 s  →        2.63 s    (-4.77%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       46.20 ns →       40.20 ns  (-13.00%) |     277   →     266     (-3.97%) |       12.80 μs →       10.69 μs  (-16.46%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        8.86 ms →        8.78 ms   (-0.95%) |     277   →     266     (-3.97%) |        2.45 s  →        2.34 s    (-4.88%) | 
+ │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       68.05 ns →       23.14 ns  (-65.99%) |     277   →     266     (-3.97%) |       18.85 μs →        6.16 μs  (-67.34%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       34.79 ms →       19.35 ms  (-44.38%) |     277   →     266     (-3.97%) |        9.64 s  →        5.15 s   (-46.58%) | 
  │ │ │ │   ├ sirius::residuals                                         |       13.45 ms →       13.01 ms   (-3.29%) |     268   →     256     (-4.48%) |        3.60 s  →        3.33 s    (-7.62%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       12.10 ms →       11.54 ms   (-4.63%) |     259   →     247     (-4.63%) |        3.13 s  →        2.85 s    (-9.05%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        6.05 ms →        5.77 ms   (-4.63%) |     518   →     494     (-4.63%) |        3.13 s  →        2.85 s    (-9.05%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.58 ms →        1.69 ms   (+7.50%) |     259   →     247     (-4.63%) |      408.24 ms →      418.52 ms   (+2.52%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       75.89 ms →       58.22 ms  (-23.28%) |      52   →      78    (+50.00%) |        3.95 s  →        4.54 s   (+15.07%) | 
- │ │ │ │     └ sddk::wf_trans                                          |       49.72 ms →       34.40 ms  (-30.82%) |      79   →     131    (+65.82%) |        3.93 s  →        4.51 s   (+14.72%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |       37.05 ms →       24.49 ms  (-33.91%) |     106   →     184    (+73.58%) |        3.93 s  →        4.51 s   (+14.72%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      597.36 ns →      450.48 ns  (-24.59%) |      25   →      25              |       14.93 μs →       11.26 μs  (-24.59%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       37.45 μs →       40.42 μs   (+7.94%) |      25   →      25              |      936.18 μs →        1.01 ms   (+7.94%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      601.30 μs →      583.44 μs   (-2.97%) |      25   →      25              |       15.03 ms →       14.59 ms   (-2.97%) | 
  │ │ ├ sirius::Density::generate                                       |      781.00 ms →      777.77 ms   (-0.41%) |      25   →      25              |       19.52 s  →       19.44 s    (-0.41%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      402.34 ms →      402.50 ms   (+0.04%) |      25   →      25              |       10.06 s  →       10.06 s    (+0.04%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.45 μs →        8.44 μs   (-0.09%) |      25   →      25              |      211.23 μs →      211.04 μs   (-0.09%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.92 μs →        7.93 μs   (+0.10%) |      25   →      25              |      198.04 μs →      198.23 μs   (+0.10%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |      100.41 ms →      100.22 ms   (-0.20%) |      25   →      25              |        2.51 s  →        2.51 s    (-0.20%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.34 μs →        7.94 μs   (+8.21%) |      25   →      25              |      183.56 μs →      198.62 μs   (+8.21%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.12 ms →        7.12 ms   (-0.01%) |      25   →      25              |      177.96 ms →      177.93 ms   (-0.01%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       91.38 ms →       91.20 ms   (-0.20%) |      25   →      25              |        2.28 s  →        2.28 s    (-0.20%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      881.00 ns →      570.96 ns  (-35.19%) |      25   →      25              |       22.02 μs →       14.27 μs  (-35.19%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      164.27 ms →      163.20 ms   (-0.65%) |      25   →      25              |        4.11 s  →        4.08 s    (-0.65%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.66 ms   (+1.09%) |      25   →      25              |       40.99 ms →       41.43 ms   (+1.09%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.24 ms →       88.25 ms   (+0.01%) |      25   →      25              |        2.21 s  →        2.21 s    (+0.01%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.01 ms →       88.00 ms   (-0.01%) |      25   →      25              |        2.20 s  →        2.20 s    (-0.01%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      278.78 ms →      278.97 ms   (+0.07%) |      25   →      25              |        6.97 s  →        6.97 s    (+0.07%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      278.78 ms →      278.97 ms   (+0.07%) |      25   →      25              |        6.97 s  →        6.97 s    (+0.07%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.14 ms →       24.04 ms   (-0.39%) |      25   →      25              |      603.49 ms →      601.12 ms   (-0.39%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      230.30 ms →      230.80 ms   (+0.22%) |      25   →      25              |        5.76 s  →        5.77 s    (+0.22%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       23.14 ms →       22.94 ms   (-0.88%) |      25   →      25              |      578.60 ms →      573.51 ms   (-0.88%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       90.20 ms →       81.24 ms   (-9.93%) |      25   →      25              |        2.25 s  →        2.03 s    (-9.93%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        6.07 ms →       11.47 ms  (+88.88%) |      25   →      25              |      151.80 ms →      286.71 ms  (+88.88%) | 
  │ │ ├ sirius::Density::mix                                            |      218.33 ms →      211.65 ms   (-3.06%) |      25   →      25              |        5.46 s  →        5.29 s    (-3.06%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      954.07 μs →      955.63 μs   (+0.16%) |      25   →      25              |       23.85 ms →       23.89 ms   (+0.16%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.81 ms →       10.24 ms   (-5.27%) |     319   →     319              |        3.45 s  →        3.27 s    (-5.27%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.38 ms →        9.93 ms   (-4.34%) |     319   →     319              |        3.31 s  →        3.17 s    (-4.34%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.38 ms →        9.93 ms   (-4.34%) |     319   →     319              |        3.31 s  →        3.17 s    (-4.34%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        6.46 ms →        6.55 ms   (+1.37%) |      25   →      25              |      161.51 ms →      163.71 ms   (+1.37%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.61 ms →        5.73 ms   (+2.02%) |      25   →      25              |      140.30 ms →      143.14 ms   (+2.02%) | 
  │ │ ├ sirius::Potential::generate                                     |      578.96 ms →      578.47 ms   (-0.09%) |      25   →      25              |       14.47 s  →       14.46 s    (-0.09%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      136.36 ms →      136.46 ms   (+0.08%) |      25   →      25              |        3.41 s  →        3.41 s    (+0.08%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       15.76 ms →       16.04 ms   (+1.73%) |      25   →      25              |      394.12 ms →      400.93 ms   (+1.73%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.23 ms →       10.42 ms   (+1.81%) |      25   →      25              |      255.79 ms →      260.43 ms   (+1.81%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |       10.01 ms →        9.93 ms   (-0.84%) |      25   →      25              |      250.34 ms →      248.23 ms   (-0.84%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       10.01 ms →        9.93 ms   (-0.84%) |      25   →      25              |      250.33 ms →      248.21 ms   (-0.84%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      550.33 μs →      553.43 μs   (+0.56%) |      50   →      50              |       27.52 ms →       27.67 ms   (+0.56%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       50.06 ms →       49.60 ms   (-0.93%) |      25   →      25              |        1.25 s  →        1.24 s    (-0.93%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       47.63 ms →       47.22 ms   (-0.87%) |      25   →      25              |        1.19 s  →        1.18 s    (-0.87%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.08 ms →        3.07 ms   (-0.41%) |      50   →      50              |      154.21 ms →      153.58 ms   (-0.41%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.30 ms →        5.36 ms   (+1.12%) |      25   →      25              |      132.41 ms →      133.90 ms   (+1.12%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.47 ms →        6.61 ms   (+2.26%) |      25   →      25              |      161.70 ms →      165.35 ms   (+2.26%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       91.01 ms →       91.02 ms   (+0.02%) |      25   →      25              |        2.28 s  →        2.28 s    (+0.02%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      292.67 ms →      292.37 ms   (-0.10%) |      25   →      25              |        7.32 s  →        7.31 s    (-0.10%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      282.64 ms →      283.01 ms   (+0.13%) |      25   →      25              |        7.07 s  →        7.08 s    (+0.13%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      282.64 ms →      283.01 ms   (+0.13%) |      25   →      25              |        7.07 s  →        7.08 s    (+0.13%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       26.98 ms →       27.38 ms   (+1.50%) |      25   →      25              |      674.48 ms →      684.61 ms   (+1.50%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      228.16 ms →      228.13 ms   (-0.01%) |      25   →      25              |        5.70 s  →        5.70 s    (-0.01%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.69 ms →       23.68 ms   (-0.05%) |      25   →      25              |      592.29 ms →      591.97 ms   (-0.05%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.42 ms →        5.53 ms   (+1.99%) |      25   →      25              |      135.55 ms →      138.24 ms   (+1.99%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.20 ms →       10.24 ms   (+0.36%) |     175   →     175              |        1.79 s  →        1.79 s    (+0.36%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.80 ms →        9.75 ms   (-0.52%) |     175   →     175              |        1.71 s  →        1.71 s    (-0.52%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.80 ms →        9.75 ms   (-0.52%) |     175   →     175              |        1.71 s  →        1.71 s    (-0.52%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.95 ms →       10.53 ms   (-3.82%) |      75   →      75              |      821.30 ms →      789.96 ms   (-3.82%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.58 ms →       10.12 ms   (-4.34%) |      75   →      75              |      793.32 ms →      758.91 ms   (-4.34%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        9.93 ms →       10.00 ms   (+0.71%) |      25   →      25              |      248.24 ms →      250.01 ms   (+0.71%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      114.49 μs →      135.27 μs  (+18.15%) |      25   →      25              |        2.86 ms →        3.38 ms  (+18.15%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      109.57 μs →      130.35 μs  (+18.97%) |      25   →      25              |        2.74 ms →        3.26 ms  (+18.97%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.27 ms →        5.27 ms   (-0.03%) |       2   →       2              |       10.55 ms →       10.54 ms   (-0.03%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.40 ms →        9.87 ms   (-5.05%) |       6   →       6              |       62.37 ms →       59.22 ms   (-5.05%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        9.91 ms →        9.81 ms   (-0.97%) |       6   →       6              |       59.43 ms →       58.86 ms   (-0.97%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        9.91 ms →        9.81 ms   (-0.97%) |       6   →       6              |       59.43 ms →       58.86 ms   (-0.97%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.56 ms →       10.12 ms   (-4.16%) |       3   →       3              |       31.67 ms →       30.35 ms   (-4.16%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.47 ms →       10.08 ms   (-3.68%) |       3   →       3              |       31.40 ms →       30.24 ms   (-3.68%) | 
  ├ sirius::Periodic_function|inner                                     |       10.04 ms →       10.46 ms   (+4.20%) |       2   →       2              |       20.08 ms →       20.93 ms   (+4.20%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.03 ms →        9.99 ms   (-0.44%) |       2   →       2              |       20.06 ms →       19.98 ms   (-0.44%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.03 ms →        9.99 ms   (-0.44%) |       2   →       2              |       20.06 ms →       19.98 ms   (-0.44%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.78 ms →       10.52 ms   (-2.45%) |       1   →       1              |       10.78 ms →       10.52 ms   (-2.45%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.77 ms →       10.51 ms   (-2.47%) |       1   →       1              |       10.77 ms →       10.51 ms   (-2.47%) | 
  └ sirius::finalize                                                    |      220.04 ms →      238.26 ms   (+8.28%) |       1   →       1              |      220.04 ms →      238.26 ms   (+8.28%) | 
  ====================================================================================================================================================================================================
```
