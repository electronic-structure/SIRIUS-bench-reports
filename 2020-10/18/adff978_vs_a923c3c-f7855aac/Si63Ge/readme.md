# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |       71.96 s  →       72.84 s    (+1.22%) |       1   →       1              |       71.96 s  →       72.84 s    (+1.22%) | 
  ├ sirius::initialize                                                  |        2.93 s  →        2.87 s    (-2.21%) |       1   →       1              |        2.93 s  →        2.87 s    (-2.21%) | 
  ├ sirius::Simulation_context::initialize                              |        3.78 s  →        3.95 s    (+4.67%) |       1   →       1              |        3.78 s  →        3.95 s    (+4.67%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       24.34 ms →       15.25 ms  (-37.35%) |       1   →       1              |       24.34 ms →       15.25 ms  (-37.35%) | 
  │ ├ sirius::Unit_cell::initialize                                     |      152.93 ms →      150.71 ms   (-1.45%) |       1   →       1              |      152.93 ms →      150.71 ms   (-1.45%) | 
  │ │ ├ sirius::Atom_type::init                                         |       67.30 ms →       65.57 ms   (-2.58%) |       2   →       2              |      134.61 ms →      131.14 ms   (-2.58%) | 
  │ │ └ sirius::Unit_cell::update                                       |       18.24 ms →       19.48 ms   (+6.81%) |       1   →       1              |       18.24 ms →       19.48 ms   (+6.81%) | 
+ │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.97 ms →        3.57 ms  (-28.14%) |       1   →       1              |        4.97 ms →        3.57 ms  (-28.14%) | 
- │ │   └ sirius::Unit_cell::get_symmetry                               |       13.22 ms →       15.84 ms  (+19.84%) |       1   →       1              |       13.22 ms →       15.84 ms  (+19.84%) | 
- │ │     └ sirius::Unit_cell_symmetry                                  |       13.15 ms →       15.76 ms  (+19.88%) |       1   →       1              |       13.15 ms →       15.76 ms  (+19.88%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.75 ms →        2.74 ms   (-0.11%) |       1   →       1              |        2.75 ms →        2.74 ms   (-0.11%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      525.46 μs →      559.41 μs   (+6.46%) |       1   →       1              |      525.46 μs →      559.41 μs   (+6.46%) | 
- │ │       └ sirius::Unit_cell_symmetry|mag                            |       16.11 μs →       27.65 μs  (+71.60%) |       1   →       1              |       16.11 μs →       27.65 μs  (+71.60%) | 
  │ └ sirius::Simulation_context::update                                |        3.40 s  →        3.73 s    (+9.79%) |       1   →       1              |        3.40 s  →        3.73 s    (+9.79%) | 
  │   ├ sirius::Unit_cell::update                                       |        6.98 ms →        6.99 ms   (+0.22%) |       1   →       1              |        6.98 ms →        6.99 ms   (+0.22%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.64 ms →        3.64 ms   (-0.15%) |       1   →       1              |        3.64 ms →        3.64 ms   (-0.15%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.29 ms →        3.31 ms   (+0.53%) |       1   →       1              |        3.29 ms →        3.31 ms   (+0.53%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.25 ms →        3.27 ms   (+0.51%) |       1   →       1              |        3.25 ms →        3.27 ms   (+0.51%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.70 ms →        2.72 ms   (+0.87%) |       1   →       1              |        2.70 ms →        2.72 ms   (+0.87%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      515.54 μs →      508.11 μs   (-1.44%) |       1   →       1              |      515.54 μs →      508.11 μs   (-1.44%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       14.07 μs →       14.12 μs   (+0.35%) |       1   →       1              |       14.07 μs →       14.12 μs   (+0.35%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      212.24 ms →      214.29 ms   (+0.96%) |       2   →       2              |      424.49 ms →      428.58 ms   (+0.96%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.29 ms →       15.29 ms   (+0.04%) |       2   →       2              |       30.58 ms →       30.59 ms   (+0.04%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.25 ms →       13.28 ms   (+0.27%) |       1   →       1              |       13.25 ms →       13.28 ms   (+0.27%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.33 ms →       56.34 ms   (+0.02%) |       2   →       2              |      112.66 ms →      112.68 ms   (+0.02%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.49 ms →       45.20 ms   (-0.63%) |       2   →       2              |       90.97 ms →       90.40 ms   (-0.63%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.31 ms →       60.47 ms   (+0.27%) |       4   →       4              |      241.23 ms →      241.89 ms   (+0.27%) | 
  │   ├ sddk::Gvec::init                                                |       92.95 ms →       92.98 ms   (+0.04%) |       2   →       2              |      185.90 ms →      185.96 ms   (+0.04%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       69.56 ms →       69.64 ms   (+0.12%) |       2   →       2              |      139.12 ms →      139.28 ms   (+0.12%) | 
  │   ├ sddk::Gvec_shells                                               |       91.74 ms →       92.36 ms   (+0.67%) |       1   →       1              |       91.74 ms →       92.36 ms   (+0.67%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.95 ms →        1.94 ms   (-0.93%) |       1   →       1              |        1.95 ms →        1.94 ms   (-0.93%) | 
- │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      546.60 ms →      707.62 ms  (+29.46%) |       2   →       2              |        1.09 s  →        1.42 s   (+29.46%) | 
+ ├ sirius::K_point_set::create_k_mesh                                  |      150.48 ms →       28.39 ms  (-81.13%) |       1   →       1              |      150.48 ms →       28.39 ms  (-81.13%) | 
  │ ├ sirius::K_point::K_point                                          |        2.50 μs →        2.52 μs   (+0.69%) |       4   →       4              |        9.99 μs →       10.06 μs   (+0.69%) | 
+ │ └ sirius::K_point_set::initialize                                   |      150.39 ms →       28.30 ms  (-81.18%) |       1   →       1              |      150.39 ms →       28.30 ms  (-81.18%) | 
  │   └ sirius::K_point::initialize                                     |       28.32 ms →       28.03 ms   (-1.02%) |       1   →       1              |       28.32 ms →       28.03 ms   (-1.02%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       11.16 ms →       10.89 ms   (-2.42%) |       1   →       1              |       11.16 ms →       10.89 ms   (-2.42%) | 
  │     │ └ sddk::Gvec::init                                            |        5.01 ms →        4.91 ms   (-1.94%) |       1   →       1              |        5.01 ms →        4.91 ms   (-1.94%) | 
- │     ├ sddk::matrix_storage::matrix_storage                          |        8.74 μs →       10.46 μs  (+19.70%) |       1   →       1              |        8.74 μs →       10.46 μs  (+19.70%) | 
  │     └ sirius::K_point::update                                       |       14.28 ms →       14.37 ms   (+0.60%) |       1   →       1              |       14.28 ms →       14.37 ms   (+0.60%) | 
  │       └ sirius::Beta_projectors                                     |       10.26 ms →       10.41 ms   (+1.52%) |       1   →       1              |       10.26 ms →       10.41 ms   (+1.52%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.27 ms →        8.47 ms   (+2.46%) |       1   →       1              |        8.27 ms →        8.47 ms   (+2.46%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.56 ms →        2.55 ms   (-0.48%) |       2   →       2              |        5.12 ms →        5.09 ms   (-0.48%) | 
  ├ sirius::Potential                                                   |       55.04 ms →       54.01 ms   (-1.87%) |       1   →       1              |       55.04 ms →       54.01 ms   (-1.87%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.91 ms →        2.91 ms   (-0.05%) |       6   →       6              |       17.45 ms →       17.44 ms   (-0.05%) | 
  │ └ sirius::Potential::update                                         |       37.07 ms →       36.09 ms   (-2.65%) |       1   →       1              |       37.07 ms →       36.09 ms   (-2.65%) | 
  │   └ sirius::Potential::generate_local_potential                     |       36.67 ms →       35.62 ms   (-2.86%) |       1   →       1              |       36.67 ms →       35.62 ms   (-2.86%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       32.28 ms →       31.23 ms   (-3.23%) |       1   →       1              |       32.28 ms →       31.23 ms   (-3.23%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |        3.84 ms →        3.82 ms   (-0.50%) |       1   →       1              |        3.84 ms →        3.82 ms   (-0.50%) | 
  ├ sirius::Density                                                     |       42.47 ms →       41.30 ms   (-2.74%) |       1   →       1              |       42.47 ms →       41.30 ms   (-2.74%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.84 ms →        2.82 ms   (-0.56%) |       2   →       2              |        5.67 ms →        5.64 ms   (-0.56%) | 
  │ └ sirius::Density::update                                           |       36.65 ms →       35.52 ms   (-3.09%) |       1   →       1              |       36.65 ms →       35.52 ms   (-3.09%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       36.37 ms →       35.24 ms   (-3.11%) |       1   →       1              |       36.37 ms →       35.24 ms   (-3.11%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |       77.81 μs →       80.16 μs   (+3.02%) |       1   →       1              |       77.81 μs →       80.16 μs   (+3.02%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       33.07 ms →       31.45 ms   (-4.90%) |       1   →       1              |       33.07 ms →       31.45 ms   (-4.90%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        2.88 ms →        3.37 ms  (+17.18%) |       1   →       1              |        2.88 ms →        3.37 ms  (+17.18%) | 
  ├ sirius::Density::initial_density                                    |       64.97 ms →       65.07 ms   (+0.14%) |       1   →       1              |       64.97 ms →       65.07 ms   (+0.14%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       37.02 ms →       37.30 ms   (+0.76%) |       1   →       1              |       37.02 ms →       37.30 ms   (+0.76%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.30 ms →        4.36 ms   (+1.28%) |       2   →       2              |        8.60 ms →        8.71 ms   (+1.28%) | 
  │ └ sirius::Periodic_function::integrate                              |        5.69 ms →        5.39 ms   (-5.23%) |       1   →       1              |        5.69 ms →        5.39 ms   (-5.23%) | 
  ├ sirius::Potential::generate                                         |      372.43 ms →      371.49 ms   (-0.25%) |       1   →       1              |      372.43 ms →      371.49 ms   (-0.25%) | 
  │ ├ sirius::Potential::poisson                                        |       45.12 ms →       44.48 ms   (-1.43%) |       1   →       1              |       45.12 ms →       44.48 ms   (-1.43%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.87 ms →        3.63 ms  (+26.62%) |       1   →       1              |        2.87 ms →        3.63 ms  (+26.62%) | 
+ │ │ └ sirius::Periodic_function|inner                                 |        5.34 ms →        4.64 ms  (-13.01%) |       1   →       1              |        5.34 ms →        4.64 ms  (-13.01%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.64 ms →        4.63 ms   (-0.19%) |       1   →       1              |        4.64 ms →        4.63 ms   (-0.19%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.63 ms →        4.63 ms   (-0.17%) |       1   →       1              |        4.63 ms →        4.63 ms   (-0.17%) | 
  │ ├ sirius::Periodic_function::add                                    |      796.35 μs →      770.74 μs   (-3.22%) |       2   →       2              |        1.59 ms →        1.54 ms   (-3.22%) | 
  │ ├ sirius::Potential::xc                                             |       50.99 ms →       51.09 ms   (+0.19%) |       1   →       1              |       50.99 ms →       51.09 ms   (+0.19%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       49.78 ms →       49.88 ms   (+0.21%) |       1   →       1              |       49.78 ms →       49.88 ms   (+0.21%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.55 ms →        2.54 ms   (-0.27%) |       2   →       2              |        5.10 ms →        5.08 ms   (-0.27%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.23 ms →        4.30 ms   (+1.71%) |       1   →       1              |        4.23 ms →        4.30 ms   (+1.71%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.94 ms →        3.84 ms   (-2.46%) |       1   →       1              |        3.94 ms →        3.84 ms   (-2.46%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      269.37 ms →      269.23 ms   (-0.05%) |       1   →       1              |      269.37 ms →      269.23 ms   (-0.05%) | 
+ │ └ sirius::Potential::generate_PAW_effective_potential               |      304.00 ns →      220.00 ns  (-27.63%) |       1   →       1              |      304.00 ns →      220.00 ns  (-27.63%) | 
- ├ sirius::Hamiltonian0                                                |        6.49 ms →        7.64 ms  (+17.80%) |       1   →       1              |        6.49 ms →        7.64 ms  (+17.80%) | 
- │ ├ sirius::Local_operator                                            |        6.04 ms →        6.98 ms  (+15.55%) |       1   →       1              |        6.04 ms →        6.98 ms  (+15.55%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.74 ms →        2.75 ms   (+0.10%) |       1   →       1              |        2.74 ms →        2.75 ms   (+0.10%) | 
- │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.58 ms →        3.16 ms  (+22.53%) |       1   →       1              |        2.58 ms →        3.16 ms  (+22.53%) | 
- │ ├ sirius::Non_local_operator                                        |       74.00 μs →      196.03 μs (+164.89%) |       2   →       2              |      148.00 μs →      392.06 μs (+164.89%) | 
  │ ├ sirius::D_operator::initialize                                    |       98.74 μs →      105.66 μs   (+7.01%) |       1   →       1              |       98.74 μs →      105.66 μs   (+7.01%) | 
+ │ └ sirius::Q_operator::initialize                                    |      116.72 μs →       88.43 μs  (-24.24%) |       1   →       1              |      116.72 μs →       88.43 μs  (-24.24%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.28 s  →        1.30 s    (+1.08%) |       1   →       1              |        1.28 s  →        1.30 s    (+1.08%) | 
- │ ├ sirius::Hamiltonian_k                                             |       47.99 ms →       57.89 ms  (+20.63%) |       1   →       1              |       47.99 ms →       57.89 ms  (+20.63%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      311.25 μs →      292.45 μs   (-6.04%) |       1   →       1              |      311.25 μs →      292.45 μs   (-6.04%) | 
- │ │ └ sirius::Beta_projectors_base::prepare                           |       47.67 ms →       57.59 ms  (+20.81%) |       1   →       1              |       47.67 ms →       57.59 ms  (+20.81%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.24 s  →        1.24 s    (+0.32%) |       1   →       1              |        1.24 s  →        1.24 s    (+0.32%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       78.84 ms →       77.24 ms   (-2.04%) |       4   →       4              |      315.38 ms →      308.94 ms   (-2.04%) | 
- │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       43.21 ms →       47.76 ms  (+10.54%) |       1   →       1              |       43.21 ms →       47.76 ms  (+10.54%) | 
+ │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        8.99 ms →        7.78 ms  (-13.43%) |       1   →       1              |        8.99 ms →        7.78 ms  (-13.43%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      335.94 ms →      336.83 ms   (+0.26%) |       1   →       1              |      335.94 ms →      336.83 ms   (+0.26%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      247.96 ms →      248.56 ms   (+0.24%) |       1   →       1              |      247.96 ms →      248.56 ms   (+0.24%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.77 μs →        3.55 μs   (-5.86%) |       1   →       1              |        3.77 μs →        3.55 μs   (-5.86%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.83 μs →        2.61 μs   (-7.77%) |       1   →       1              |        2.83 μs →        2.61 μs   (-7.77%) | 
+ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      880.00 ns →      472.00 ns  (-46.36%) |       1   →       1              |      880.00 ns →      472.00 ns  (-46.36%) | 
- │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      530.00 ns →      680.00 ns  (+28.30%) |       1   →       1              |      530.00 ns →      680.00 ns  (+28.30%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.14 ms →        3.16 ms   (+0.67%) |       1   →       1              |        3.14 ms →        3.16 ms   (+0.67%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.30 ms →       21.31 ms   (+0.03%) |       1   →       1              |       21.30 ms →       21.31 ms   (+0.03%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       31.75 ms →       31.87 ms   (+0.39%) |       2   →       2              |       63.50 ms →       63.75 ms   (+0.39%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.75 ms →       14.68 ms   (-0.43%) |       2   →       2              |       29.49 ms →       29.37 ms   (-0.43%) | 
  │ │ │ └ sddk::wf_inner                                                |       14.54 ms →       14.47 ms   (-0.44%) |       2   →       2              |       29.07 ms →       28.94 ms   (-0.44%) | 
  │ │ │   ├ sddk::wf_inner|scale                                        |       21.50 ns →       21.50 ns            |       2   →       2              |       43.00 ns →       43.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       14.38 ms →       14.34 ms   (-0.32%) |       2   →       2              |       28.77 ms →       28.68 ms   (-0.32%) | 
+ │ │ │   └ sddk::wf_inner|scale_back                                   |       27.00 ns →       20.50 ns  (-24.07%) |       2   →       2              |       54.00 ns →       41.00 ns  (-24.07%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      231.19 ms →      235.15 ms   (+1.71%) |       1   →       1              |      231.19 ms →      235.15 ms   (+1.71%) | 
  │ │ └ sddk::wf_trans                                                  |        2.60 ms →        2.62 ms   (+0.71%) |       1   →       1              |        2.60 ms →        2.62 ms   (+0.71%) | 
  │ │   └ sddk::wf_trans|pw                                             |        2.59 ms →        2.61 ms   (+0.69%) |       1   →       1              |        2.59 ms →        2.61 ms   (+0.69%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      632.00 ns →      483.00 ns  (-23.58%) |       1   →       1              |      632.00 ns →      483.00 ns  (-23.58%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |       62.17 s  →       63.03 s    (+1.39%) |       1   →       1              |       62.17 s  →       63.03 s    (+1.39%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.47 ms →        2.43 ms   (-1.39%) |      19   →      19              |       46.88 ms →       46.23 ms   (-1.39%) | 
! │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.26 s  →        2.99 s    (-8.25%) |      19   →      21    (+10.53%) |       61.93 s  →       62.80 s    (+1.40%) | 
+ │ │ ├ sirius::Hamiltonian0                                            |        5.44 ms →        4.83 ms  (-11.21%) |      19   →      21    (+10.53%) |      103.43 ms →      101.50 ms   (-1.87%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        4.73 ms →        4.12 ms  (-12.85%) |      19   →      21    (+10.53%) |       89.81 ms →       86.50 ms   (-3.68%) | 
! │ │ │ │ ├ sirius::Smooth_periodic_function                            |      556.37 μs →      530.42 μs   (-4.66%) |      19   →      21    (+10.53%) |       10.57 ms →       11.14 ms   (+5.37%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.11 ms →        2.58 ms  (-17.01%) |      19   →      21    (+10.53%) |       59.17 ms →       54.27 ms   (-8.27%) | 
! │ │ │ ├ sirius::Non_local_operator                                    |      212.77 μs →      198.02 μs   (-6.93%) |      38   →      42    (+10.53%) |        8.09 ms →        8.32 ms   (+2.87%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |      114.30 μs →      136.17 μs  (+19.14%) |      19   →      21    (+10.53%) |        2.17 ms →        2.86 ms  (+31.68%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       93.55 μs →       95.67 μs   (+2.27%) |      19   →      21    (+10.53%) |        1.78 ms →        2.01 ms  (+13.03%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.03 s  →        1.76 s   (-12.95%) |      19   →      21    (+10.53%) |       38.50 s  →       37.04 s    (-3.79%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      201.35 μs →      251.54 μs  (+24.93%) |      19   →      21    (+10.53%) |        3.83 ms →        5.28 ms  (+38.08%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      192.14 μs →      241.87 μs  (+25.88%) |      19   →      21    (+10.53%) |        3.65 ms →        5.08 ms  (+39.13%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        6.67 μs →        7.09 μs   (+6.23%) |      19   →      21    (+10.53%) |      126.75 μs →      148.82 μs  (+17.41%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.97 s  →        1.64 s   (-16.56%) |      19   →      21    (+10.53%) |       37.34 s  →       34.44 s    (-7.77%) | 
! │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       76.65 ms →       71.69 ms   (-6.47%) |      19   →      21    (+10.53%) |        1.46 s  →        1.51 s    (+3.38%) | 
! │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.94 ms →        7.20 ms   (-9.20%) |     114   →     126    (+10.53%) |      904.61 ms →      907.81 ms   (+0.35%) | 
- │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       17.94 ms →       18.16 ms   (+1.25%) |      19   →      21    (+10.53%) |      340.86 ms →      381.46 ms  (+11.91%) | 
- │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      452.92 μs →      456.16 μs   (+0.71%) |      19   →      21    (+10.53%) |        8.61 ms →        9.58 ms  (+11.31%) | 
- │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        8.16 ms →        8.24 ms   (+0.96%) |      38   →      42    (+10.53%) |      309.99 ms →      345.92 ms  (+11.59%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.86 s  →        1.54 s   (-17.24%) |      19   →      21    (+10.53%) |       35.38 s  →       32.36 s    (-8.53%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       50.98 ms →       53.30 ms   (+4.56%) |     356   →     361     (+1.40%) |       18.15 s  →       19.24 s    (+6.03%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       28.68 ms →       29.86 ms   (+4.10%) |     356   →     361     (+1.40%) |       10.21 s  →       10.78 s    (+5.57%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.09 μs →        2.20 μs   (+5.32%) |     356   →     361     (+1.40%) |      742.33 μs →      792.81 μs   (+6.80%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.79 μs →        1.86 μs   (+3.90%) |     356   →     361     (+1.40%) |      637.05 μs →      671.19 μs   (+5.36%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      416.35 ns →      481.75 ns  (+15.71%) |     356   →     361     (+1.40%) |      148.22 μs →      173.91 μs  (+17.33%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      541.78 ns →      725.39 ns  (+33.89%) |     356   →     361     (+1.40%) |      192.87 μs →      261.86 μs  (+35.77%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.84 ms →        2.96 ms   (+4.29%) |     356   →     361     (+1.40%) |        1.01 s  →        1.07 s    (+5.76%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.27 ms →        3.32 ms   (+1.61%) |     356   →     361     (+1.40%) |        1.16 s  →        1.20 s    (+3.03%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        8.09 ms →        8.57 ms   (+6.02%) |     712   →     722     (+1.40%) |        5.76 s  →        6.19 s    (+7.51%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |        6.74 ms →        7.38 ms   (+9.55%) |     356   →     361     (+1.40%) |        2.40 s  →        2.66 s   (+11.09%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        1.12 ms →        1.18 ms   (+4.88%) |     693   →     701     (+1.15%) |      779.07 ms →      826.56 ms   (+6.10%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       53.92 ns →       45.21 ns  (-16.16%) |     693   →     701     (+1.15%) |       37.37 μs →       31.69 μs  (-15.19%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |      962.48 μs →        1.02 ms   (+5.52%) |     693   →     701     (+1.15%) |      667.00 ms →      711.92 ms   (+6.73%) | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       51.46 ns →       47.53 ns   (-7.65%) |     693   →     701     (+1.15%) |       35.66 μs →       33.32 μs   (-6.59%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      142.65 μs →      146.03 μs   (+2.37%) |     356   →     361     (+1.40%) |       50.78 ms →       52.72 ms   (+3.81%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        2.24 ms →        2.62 ms  (+16.72%) |     356   →     361     (+1.40%) |      798.59 ms →      945.19 ms  (+18.36%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |        2.28 ms →        2.47 ms   (+8.15%) |     337   →     340     (+0.89%) |      768.63 ms →      838.65 ms   (+9.11%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |      759.49 μs →      821.36 μs   (+8.15%) |    1.01 K →    1.02 K   (+0.89%) |      767.85 ms →      837.79 ms   (+9.11%) | 
- │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.33 ms →        1.46 ms   (+9.71%) |     356   →     361     (+1.40%) |      473.31 ms →      526.57 ms  (+11.25%) | 
- │ │ │ │   │ └ sddk::wf_inner                                          |        1.25 ms →        1.41 ms  (+12.78%) |     356   →     361     (+1.40%) |      445.63 ms →      509.65 ms  (+14.37%) | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       39.49 ns →       42.44 ns   (+7.47%) |     356   →     361     (+1.40%) |       14.06 μs →       15.32 μs   (+8.98%) | 
- │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        1.09 ms →        1.25 ms  (+14.62%) |     356   →     361     (+1.40%) |      387.89 ms →      450.85 ms  (+16.23%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       39.69 ns →       43.81 ns  (+10.39%) |     356   →     361     (+1.40%) |       14.13 μs →       15.82 μs  (+11.94%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       36.68 ms →       23.58 ms  (-35.73%) |     356   →     361     (+1.40%) |       13.06 s  →        8.51 s   (-34.83%) | 
  │ │ │ │   ├ sirius::residuals                                         |        2.63 ms →        2.67 ms   (+1.44%) |     340   →     346     (+1.76%) |      894.08 ms →      922.97 ms   (+3.23%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |        1.29 ms →        1.26 ms   (-2.34%) |     337   →     342     (+1.48%) |      436.27 ms →      432.37 ms   (-0.89%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      645.91 μs →      630.67 μs   (-2.36%) |     674   →     684     (+1.48%) |      435.34 ms →      431.38 ms   (-0.91%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.24 ms →        1.30 ms   (+4.47%) |     337   →     342     (+1.48%) |      419.47 ms →      444.71 ms   (+6.02%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        7.38 ms →        5.39 ms  (-26.96%) |      54   →      90    (+66.67%) |      398.34 ms →      484.91 ms  (+21.73%) | 
- │ │ │ │     └ sddk::wf_trans                                          |        4.43 ms →        3.00 ms  (-32.30%) |      89   →     159    (+78.65%) |      394.01 ms →      476.55 ms  (+20.95%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |        3.18 ms →        2.09 ms  (-34.24%) |     124   →     228    (+83.87%) |      393.85 ms →      476.23 ms  (+20.92%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      394.74 ns →      563.10 ns  (+42.65%) |      19   →      21    (+10.53%) |        7.50 μs →       11.82 μs  (+57.67%) | 
! │ │ │ └ sirius::K_point_set::sync_band_energies                       |       19.87 μs →       19.68 μs   (-0.96%) |      19   →      21    (+10.53%) |      377.61 μs →      413.34 μs   (+9.46%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.52 ms →        1.53 ms   (+0.66%) |      19   →      21    (+10.53%) |       28.88 ms →       32.14 ms  (+11.26%) | 
! │ │ ├ sirius::Density::generate                                       |      572.43 ms →      568.92 ms   (-0.61%) |      19   →      21    (+10.53%) |       10.88 s  →       11.95 s    (+9.85%) | 
! │ │ │ ├ sirius::Density::generate_valence                             |      430.42 ms →      417.06 ms   (-3.10%) |      19   →      21    (+10.53%) |        8.18 s  →        8.76 s    (+7.09%) | 
! │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.54 μs →        8.42 μs   (-1.38%) |      19   →      21    (+10.53%) |      162.27 μs →      176.87 μs   (+9.00%) | 
! │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.98 μs →        7.88 μs   (-1.25%) |      19   →      21    (+10.53%) |      151.62 μs →      165.49 μs   (+9.15%) | 
! │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       33.09 ms →       31.56 ms   (-4.63%) |      19   →      21    (+10.53%) |      628.77 ms →      662.79 ms   (+5.41%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.71 μs →        8.40 μs   (+8.84%) |      19   →      21    (+10.53%) |      146.56 μs →      176.32 μs  (+20.30%) | 
! │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        5.24 ms →        4.93 ms   (-5.93%) |      19   →      21    (+10.53%) |       99.52 ms →      103.47 ms   (+3.97%) | 
! │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       26.81 ms →       25.58 ms   (-4.56%) |      19   →      21    (+10.53%) |      509.30 ms →      537.22 ms   (+5.48%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      543.26 ns →      773.76 ns  (+42.43%) |      19   →      21    (+10.53%) |       10.32 μs →       16.25 μs  (+57.42%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      112.93 ms →      114.62 ms   (+1.49%) |      19   →      21    (+10.53%) |        2.15 s  →        2.41 s   (+12.18%) | 
! │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.96 ms →        1.93 ms   (-1.72%) |      19   →      21    (+10.53%) |       37.22 ms →       40.43 ms   (+8.63%) | 
! │ │ │ │ └ sirius::Density::augment                                    |      246.63 ms →      230.94 ms   (-6.36%) |      19   →      21    (+10.53%) |        4.69 s  →        4.85 s    (+3.50%) | 
! │ │ │ │   └ sirius::Density::generate_rho_aug                         |      246.41 ms →      230.72 ms   (-6.37%) |      19   →      21    (+10.53%) |        4.68 s  →        4.85 s    (+3.49%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      113.98 ms →      124.72 ms   (+9.42%) |      19   →      21    (+10.53%) |        2.17 s  →        2.62 s   (+20.94%) | 
- │ │ │ │ └ sirius::symmetrize_function|fpw                             |      113.98 ms →      124.72 ms   (+9.42%) |      19   →      21    (+10.53%) |        2.17 s  →        2.62 s   (+20.94%) | 
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       28.99 ms →       41.42 ms  (+42.87%) |      19   →      21    (+10.53%) |      550.81 ms →      869.75 ms  (+57.90%) | 
! │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       71.68 ms →       70.05 ms   (-2.27%) |      19   →      21    (+10.53%) |        1.36 s  →        1.47 s    (+8.02%) | 
! │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.66 ms →       12.60 ms   (-0.48%) |      19   →      21    (+10.53%) |      240.53 ms →      264.58 ms  (+10.00%) | 
! │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.70 ms →       23.47 ms   (-0.96%) |      19   →      21    (+10.53%) |      450.32 ms →      492.97 ms   (+9.47%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        4.33 ms →        3.66 ms  (-15.27%) |      19   →      21    (+10.53%) |       82.18 ms →       76.95 ms   (-6.35%) | 
- │ │ ├ sirius::Density::mix                                            |      132.75 ms →      134.57 ms   (+1.37%) |      19   →      21    (+10.53%) |        2.52 s  →        2.83 s   (+12.04%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |      964.38 μs →      485.04 μs  (-49.70%) |      19   →      21    (+10.53%) |       18.32 ms →       10.19 ms  (-44.41%) | 
- │ │ │ ├ sirius::Periodic_function|inner                               |        4.87 ms →        4.74 ms   (-2.59%) |     229   →     259    (+13.10%) |        1.12 s  →        1.23 s   (+10.17%) | 
! │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.81 ms →        4.62 ms   (-3.97%) |     229   →     259    (+13.10%) |        1.10 s  →        1.20 s    (+8.61%) | 
! │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.81 ms →        4.62 ms   (-3.98%) |     229   →     259    (+13.10%) |        1.10 s  →        1.20 s    (+8.60%) | 
! │ │ │ └ sirius::Density::mixer_output                                 |        5.44 ms →        5.26 ms   (-3.23%) |      19   →      21    (+10.53%) |      103.33 ms →      110.52 ms   (+6.95%) | 
! │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        4.73 ms →        4.38 ms   (-7.34%) |      19   →      21    (+10.53%) |       89.85 ms →       92.01 ms   (+2.41%) | 
- │ │ ├ sirius::Potential::generate                                     |      365.71 ms →      364.86 ms   (-0.23%) |      19   →      21    (+10.53%) |        6.95 s  →        7.66 s   (+10.27%) | 
! │ │ │ ├ sirius::Potential::poisson                                    |       45.49 ms →       44.51 ms   (-2.16%) |      19   →      21    (+10.53%) |      864.37 ms →      934.73 ms   (+8.14%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.88 ms →        3.03 ms   (+5.12%) |      19   →      21    (+10.53%) |       54.70 ms →       63.56 ms  (+16.19%) | 
! │ │ │ │ └ sirius::Periodic_function|inner                             |        5.70 ms →        5.17 ms   (-9.24%) |      19   →      21    (+10.53%) |      108.22 ms →      108.56 ms   (+0.31%) | 
- │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.64 ms →        4.63 ms   (-0.03%) |      19   →      21    (+10.53%) |       88.09 ms →       97.33 ms  (+10.49%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.64 ms →        4.63 ms   (-0.04%) |      19   →      21    (+10.53%) |       88.07 ms →       97.31 ms  (+10.49%) | 
! │ │ │ ├ sirius::Periodic_function::add                                |      800.73 μs →      793.32 μs   (-0.93%) |      38   →      42    (+10.53%) |       30.43 ms →       33.32 ms   (+9.50%) | 
- │ │ │ ├ sirius::Potential::xc                                         |       44.49 ms →       44.58 ms   (+0.21%) |      19   →      21    (+10.53%) |      845.29 ms →      936.21 ms  (+10.76%) | 
- │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       43.31 ms →       43.41 ms   (+0.23%) |      19   →      21    (+10.53%) |      822.80 ms →      911.51 ms  (+10.78%) | 
! │ │ │ │   ├ sirius::Smooth_periodic_function                          |      693.49 μs →      683.83 μs   (-1.39%) |      38   →      42    (+10.53%) |       26.35 ms →       28.72 ms   (+8.99%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.06 ms →        4.10 ms   (+0.91%) |      19   →      21    (+10.53%) |       77.22 ms →       86.13 ms  (+11.54%) | 
! │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.89 ms →        3.77 ms   (-2.89%) |      19   →      21    (+10.53%) |       73.83 ms →       79.24 ms   (+7.33%) | 
- │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.83 ms →      268.99 ms   (+0.06%) |      19   →      21    (+10.53%) |        5.11 s  →        5.65 s   (+10.60%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      345.42 ns →      260.57 ns  (-24.56%) |      19   →      21    (+10.53%) |        6.56 μs →        5.47 μs  (-16.62%) | 
! │ │ ├ sirius::Field4D::symmetrize                                     |       98.36 ms →       96.40 ms   (-1.99%) |      19   →      21    (+10.53%) |        1.87 s  →        2.02 s    (+8.32%) | 
! │ │ │ └ sirius::symmetrize_function|fpw                               |       98.36 ms →       96.40 ms   (-1.99%) |      19   →      21    (+10.53%) |        1.87 s  →        2.02 s    (+8.32%) | 
! │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.58 ms →       13.29 ms   (-2.11%) |      19   →      21    (+10.53%) |      257.98 ms →      279.13 ms   (+8.20%) | 
! │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       71.55 ms →       69.90 ms   (-2.31%) |      19   →      21    (+10.53%) |        1.36 s  →        1.47 s    (+7.98%) | 
- │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.60 ms →       12.57 ms   (-0.21%) |      19   →      21    (+10.53%) |      239.41 ms →      264.05 ms  (+10.29%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        4.16 ms →        3.59 ms  (-13.67%) |      19   →      21    (+10.53%) |       79.07 ms →       75.45 ms   (-4.58%) | 
- │ │ ├ sirius::Periodic_function|inner                                 |        4.71 ms →        4.72 ms   (+0.14%) |     133   →     147    (+10.53%) |      626.81 ms →      693.75 ms  (+10.68%) | 
- │ │ │ └ sirius::Periodic_function|inner_local                         |        4.56 ms →        4.55 ms   (-0.38%) |     133   →     147    (+10.53%) |      607.02 ms →      668.37 ms  (+10.11%) | 
- │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.56 ms →        4.55 ms   (-0.38%) |     133   →     147    (+10.53%) |      606.94 ms →      668.29 ms  (+10.11%) | 
! │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.96 ms →        4.73 ms   (-4.56%) |      57   →      63    (+10.53%) |      282.51 ms →      298.01 ms   (+5.49%) | 
! │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.93 ms →        4.72 ms   (-4.15%) |      57   →      63    (+10.53%) |      280.88 ms →      297.57 ms   (+5.94%) | 
! │ │ ├ sirius::Periodic_function::integrate                            |        4.77 ms →        4.52 ms   (-5.17%) |      19   →      21    (+10.53%) |       90.64 ms →       95.00 ms   (+4.81%) | 
! │ │ └ sirius::Density::get_magnetisation                              |       77.49 μs →       75.75 μs   (-2.25%) |      19   →      21    (+10.53%) |        1.47 ms →        1.59 ms   (+8.04%) | 
! │ │   └ sirius::Density::compute_atomic_mag_mom                       |       72.53 μs →       70.61 μs   (-2.64%) |      19   →      21    (+10.53%) |        1.38 ms →        1.48 ms   (+7.60%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.26 ms →        5.13 ms   (-2.47%) |       2   →       2              |       10.51 ms →       10.25 ms   (-2.47%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.69 ms →        4.82 ms   (+2.71%) |       6   →       6              |       28.15 ms →       28.91 ms   (+2.71%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.69 ms →        4.81 ms   (+2.71%) |       6   →       6              |       28.13 ms →       28.89 ms   (+2.71%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.69 ms →        4.81 ms   (+2.75%) |       6   →       6              |       28.11 ms →       28.88 ms   (+2.75%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        5.00 ms →        4.90 ms   (-1.95%) |       3   →       3              |       15.00 ms →       14.71 ms   (-1.95%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        5.00 ms →        4.90 ms   (-2.02%) |       3   →       3              |       14.99 ms →       14.69 ms   (-2.02%) | 
  ├ sirius::Periodic_function|inner                                     |        4.57 ms →        4.54 ms   (-0.53%) |       2   →       2              |        9.14 ms →        9.09 ms   (-0.53%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.56 ms →        4.54 ms   (-0.55%) |       2   →       2              |        9.12 ms →        9.07 ms   (-0.55%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.56 ms →        4.54 ms   (-0.55%) |       2   →       2              |        9.12 ms →        9.07 ms   (-0.55%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        5.07 ms →        4.71 ms   (-7.26%) |       1   →       1              |        5.07 ms →        4.71 ms   (-7.26%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.92 ms →        4.70 ms   (-4.49%) |       1   →       1              |        4.92 ms →        4.70 ms   (-4.49%) | 
+ └ sirius::finalize                                                    |      318.58 ms →      194.85 ms  (-38.84%) |       1   →       1              |      318.58 ms →      194.85 ms  (-38.84%) | 
  ====================================================================================================================================================================================================
```
