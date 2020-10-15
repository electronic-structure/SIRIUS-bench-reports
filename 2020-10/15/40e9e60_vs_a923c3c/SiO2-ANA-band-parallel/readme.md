# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs 40e9e6046ebfdd2424926f76cb043caae175bee0
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      242.74 s  →      223.07 s    (-8.10%) |       1   →       1              |      242.74 s  →      223.07 s    (-8.10%) | 
  ├ sirius::initialize                                                  |        2.71 s  →        2.77 s    (+2.13%) |       1   →       1              |        2.71 s  →        2.77 s    (+2.13%) | 
  ├ sirius::Simulation_context::initialize                              |        2.94 s  →        2.91 s    (-0.99%) |       1   →       1              |        2.94 s  →        2.91 s    (-0.99%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       41.29 ms →      206.80 μs  (-99.50%) |       1   →       1              |       41.29 ms →      206.80 μs  (-99.50%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      172.86 ms →      153.00 ms  (-11.49%) |       1   →       1              |      172.86 ms →      153.00 ms  (-11.49%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       73.70 ms →       64.34 ms  (-12.69%) |       2   →       2              |      147.40 ms →      128.69 ms  (-12.69%) | 
  │ │ └ sirius::Unit_cell::update                                       |       25.38 ms →       24.23 ms   (-4.55%) |       1   →       1              |       25.38 ms →       24.23 ms   (-4.55%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.58 ms →        6.54 ms   (-0.64%) |       1   →       1              |        6.58 ms →        6.54 ms   (-0.64%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       18.76 ms →       17.65 ms   (-5.92%) |       1   →       1              |       18.76 ms →       17.65 ms   (-5.92%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       18.74 ms →       17.63 ms   (-5.92%) |       1   →       1              |       18.74 ms →       17.63 ms   (-5.92%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.15 ms →        4.16 ms   (+0.23%) |       1   →       1              |        4.15 ms →        4.16 ms   (+0.23%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.36 ms →        2.34 ms   (-0.54%) |       1   →       1              |        2.36 ms →        2.34 ms   (-0.54%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      105.19 μs →      104.58 μs   (-0.58%) |       1   →       1              |      105.19 μs →      104.58 μs   (-0.58%) | 
  │ └ sirius::Simulation_context::update                                |        2.68 s  →        2.72 s    (+1.40%) |       1   →       1              |        2.68 s  →        2.72 s    (+1.40%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.84 ms →       10.92 ms   (+0.69%) |       1   →       1              |       10.84 ms →       10.92 ms   (+0.69%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.43 ms →        4.49 ms   (+1.28%) |       1   →       1              |        4.43 ms →        4.49 ms   (+1.28%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.37 ms →        6.39 ms   (+0.32%) |       1   →       1              |        6.37 ms →        6.39 ms   (+0.32%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.35 ms →        6.38 ms   (+0.35%) |       1   →       1              |        6.35 ms →        6.38 ms   (+0.35%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.86 ms →        3.86 ms   (+0.18%) |       1   →       1              |        3.86 ms →        3.86 ms   (+0.18%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.33 ms   (+0.27%) |       1   →       1              |        2.33 ms →        2.33 ms   (+0.27%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      104.16 μs →      104.20 μs   (+0.04%) |       1   →       1              |      104.16 μs →      104.20 μs   (+0.04%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       64.64 ms →       64.04 ms   (-0.94%) |       2   →       2              |      129.29 ms →      128.08 ms   (-0.94%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.13 ms →        5.20 ms   (+1.43%) |       2   →       2              |       10.26 ms →       10.41 ms   (+1.43%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.48 ms →        4.46 ms   (-0.44%) |       1   →       1              |        4.48 ms →        4.46 ms   (-0.44%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.78 ms →       21.76 ms   (-0.09%) |       2   →       2              |       43.55 ms →       43.51 ms   (-0.09%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.82 ms →       14.83 ms   (+0.08%) |       2   →       2              |       29.64 ms →       29.66 ms   (+0.08%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.83 ms →       19.57 ms   (-1.28%) |       4   →       4              |       79.31 ms →       78.29 ms   (-1.28%) | 
  │   ├ sddk::Gvec::init                                                |      174.41 ms →      171.43 ms   (-1.71%) |       2   →       2              |      348.82 ms →      342.86 ms   (-1.71%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      131.90 ms →      129.10 ms   (-2.13%) |       2   →       2              |      263.81 ms →      258.19 ms   (-2.13%) | 
  │   ├ sddk::Gvec_shells                                               |      173.80 ms →      179.90 ms   (+3.51%) |       1   →       1              |      173.80 ms →      179.90 ms   (+3.51%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.32 ms →        1.32 ms   (-0.25%) |       1   →       1              |        1.32 ms →        1.32 ms   (-0.25%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      295.95 ms →      296.48 ms   (+0.18%) |       2   →       2              |      591.91 ms →      592.95 ms   (+0.18%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       74.88 ms →       77.69 ms   (+3.75%) |       1   →       1              |       74.88 ms →       77.69 ms   (+3.75%) | 
  │ ├ sirius::K_point::K_point                                          |        2.73 μs →        2.77 μs   (+1.52%) |       4   →       4              |       10.90 μs →       11.07 μs   (+1.52%) | 
  │ └ sirius::K_point_set::initialize                                   |       74.78 ms →       77.59 ms   (+3.76%) |       1   →       1              |       74.78 ms →       77.59 ms   (+3.76%) | 
  │   └ sirius::K_point::initialize                                     |       18.68 ms →       19.38 ms   (+3.71%) |       4   →       4              |       74.74 ms →       77.51 ms   (+3.71%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       14.10 ms →       14.80 ms   (+4.95%) |       4   →       4              |       56.41 ms →       59.20 ms   (+4.95%) | 
  │     │ └ sddk::Gvec::init                                            |        3.88 ms →        3.83 ms   (-1.25%) |       4   →       4              |       15.51 ms →       15.32 ms   (-1.25%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        9.06 μs →        9.44 μs   (+4.15%) |       4   →       4              |       36.24 μs →       37.75 μs   (+4.15%) | 
  │     └ sirius::K_point::update                                       |        3.28 ms →        3.29 ms   (+0.17%) |       4   →       4              |       13.13 ms →       13.15 ms   (+0.17%) | 
  │       └ sirius::Beta_projectors                                     |        1.76 ms →        1.79 ms   (+1.86%) |       4   →       4              |        7.03 ms →        7.16 ms   (+1.86%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |      920.31 μs →      936.65 μs   (+1.78%) |       4   →       4              |        3.68 ms →        3.75 ms   (+1.78%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.51 ms →        5.36 ms   (-2.76%) |       2   →       2              |       11.03 ms →       10.72 ms   (-2.76%) | 
  ├ sirius::Potential                                                   |      159.84 ms →      158.52 ms   (-0.83%) |       1   →       1              |      159.84 ms →      158.52 ms   (-0.83%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        6.29 ms →        5.75 ms   (-8.59%) |       6   →       6              |       37.74 ms →       34.49 ms   (-8.59%) | 
  │ └ sirius::Potential::update                                         |      121.31 ms →      123.33 ms   (+1.67%) |       1   →       1              |      121.31 ms →      123.33 ms   (+1.67%) | 
  │   └ sirius::Potential::generate_local_potential                     |      120.58 ms →      122.58 ms   (+1.66%) |       1   →       1              |      120.58 ms →      122.58 ms   (+1.66%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      110.96 ms →      111.43 ms   (+0.43%) |       1   →       1              |      110.96 ms →      111.43 ms   (+0.43%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        8.72 ms →       10.28 ms  (+17.93%) |       1   →       1              |        8.72 ms →       10.28 ms  (+17.93%) | 
  ├ sirius::Density                                                     |      135.18 ms →      134.86 ms   (-0.24%) |       1   →       1              |      135.18 ms →      134.86 ms   (-0.24%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.25 ms →        5.24 ms   (-0.19%) |       2   →       2              |       10.50 ms →       10.48 ms   (-0.19%) | 
  │ └ sirius::Density::update                                           |      124.41 ms →      124.12 ms   (-0.24%) |       1   →       1              |      124.41 ms →      124.12 ms   (-0.24%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      123.98 ms →      123.70 ms   (-0.23%) |       1   →       1              |      123.98 ms →      123.70 ms   (-0.23%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |      102.56 μs →      102.53 μs   (-0.03%) |       1   →       1              |      102.56 μs →      102.53 μs   (-0.03%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      111.65 ms →      112.51 ms   (+0.77%) |       1   →       1              |      111.65 ms →      112.51 ms   (+0.77%) | 
  │     └ sirius::Smooth_periodic_function::fft_transform               |       11.78 ms →       10.65 ms   (-9.61%) |       1   →       1              |       11.78 ms →       10.65 ms   (-9.61%) | 
  ├ sirius::Density::initial_density                                    |      174.56 ms →      174.56 ms   (+0.00%) |       1   →       1              |      174.56 ms →      174.56 ms   (+0.00%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      110.03 ms →      111.06 ms   (+0.93%) |       1   →       1              |      110.03 ms →      111.06 ms   (+0.93%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |       10.97 ms →       10.96 ms   (-0.10%) |       2   →       2              |       21.95 ms →       21.92 ms   (-0.10%) | 
  │ └ sirius::Periodic_function::integrate                              |       10.03 ms →        9.81 ms   (-2.26%) |       1   →       1              |       10.03 ms →        9.81 ms   (-2.26%) | 
  ├ sirius::Potential::generate                                         |      592.04 ms →      593.56 ms   (+0.26%) |       1   →       1              |      592.04 ms →      593.56 ms   (+0.26%) | 
  │ ├ sirius::Potential::poisson                                        |      136.57 ms →      138.04 ms   (+1.08%) |       1   →       1              |      136.57 ms →      138.04 ms   (+1.08%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       16.84 ms →       18.40 ms   (+9.23%) |       1   →       1              |       16.84 ms →       18.40 ms   (+9.23%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        9.95 ms →       10.31 ms   (+3.63%) |       1   →       1              |        9.95 ms →       10.31 ms   (+3.63%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        9.81 ms →       10.23 ms   (+4.21%) |       1   →       1              |        9.81 ms →       10.23 ms   (+4.21%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.81 ms →       10.23 ms   (+4.21%) |       1   →       1              |        9.81 ms →       10.23 ms   (+4.21%) | 
  │ ├ sirius::Periodic_function::add                                    |      559.53 μs →      543.90 μs   (-2.79%) |       2   →       2              |        1.12 ms →        1.09 ms   (-2.79%) | 
  │ ├ sirius::Potential::xc                                             |       53.65 ms →       54.35 ms   (+1.29%) |       1   →       1              |       53.65 ms →       54.35 ms   (+1.29%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.29 ms →       52.07 ms   (+1.52%) |       1   →       1              |       51.29 ms →       52.07 ms   (+1.52%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.73 ms →        5.61 ms   (-2.09%) |       2   →       2              |       11.47 ms →       11.23 ms   (-2.09%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.22 ms →        5.38 ms   (+3.07%) |       1   →       1              |        5.22 ms →        5.38 ms   (+3.07%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.74 ms →        5.76 ms   (+0.46%) |       1   →       1              |        5.74 ms →        5.76 ms   (+0.46%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.57 ms →       93.44 ms   (+0.94%) |       1   →       1              |       92.57 ms →       93.44 ms   (+0.94%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      301.00 ms →      299.56 ms   (-0.48%) |       1   →       1              |      301.00 ms →      299.56 ms   (-0.48%) | 
  ├ sirius::Hamiltonian0                                                |        8.45 ms →        8.35 ms   (-1.17%) |       1   →       1              |        8.45 ms →        8.35 ms   (-1.17%) | 
  │ ├ sirius::Local_operator                                            |        8.10 ms →        8.00 ms   (-1.18%) |       1   →       1              |        8.10 ms →        8.00 ms   (-1.18%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.77 ms →        4.75 ms   (-0.55%) |       1   →       1              |        4.77 ms →        4.75 ms   (-0.55%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.41 ms →        2.35 ms   (-2.69%) |       1   →       1              |        2.41 ms →        2.35 ms   (-2.69%) | 
  │ ├ sirius::Non_local_operator                                        |       63.42 μs →       63.47 μs   (+0.08%) |       2   →       2              |      126.84 μs →      126.94 μs   (+0.08%) | 
  │ ├ sirius::D_operator::initialize                                    |       95.21 μs →       96.07 μs   (+0.90%) |       1   →       1              |       95.21 μs →       96.07 μs   (+0.90%) | 
  │ └ sirius::Q_operator::initialize                                    |       70.25 μs →       68.95 μs   (-1.85%) |       1   →       1              |       70.25 μs →       68.95 μs   (-1.85%) | 
  ├ sirius::Band::initialize_subspace                                   |        3.10 s  →        3.08 s    (-0.64%) |       1   →       1              |        3.10 s  →        3.08 s    (-0.64%) | 
  │ ├ sirius::Hamiltonian_k                                             |      381.64 μs →      373.16 μs   (-2.22%) |       4   →       4              |        1.53 ms →        1.49 ms   (-2.22%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      376.04 μs →      367.92 μs   (-2.16%) |       4   →       4              |        1.50 ms →        1.47 ms   (-2.16%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |        3.54 μs →        3.28 μs   (-7.25%) |       4   →       4              |       14.15 μs →       13.13 μs   (-7.25%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |      775.07 ms →      770.11 ms   (-0.64%) |       4   →       4              |        3.10 s  →        3.08 s    (-0.64%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       32.56 ms →       32.81 ms   (+0.78%) |      16   →      16              |      520.95 ms →      525.00 ms   (+0.78%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       14.49 ms →       14.44 ms   (-0.33%) |       4   →       4              |       57.97 ms →       57.78 ms   (-0.33%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        5.39 ms →        5.29 ms   (-1.82%) |       4   →       4              |       21.56 ms →       21.16 ms   (-1.82%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      352.84 ms →      354.63 ms   (+0.51%) |       4   →       4              |        1.41 s  →        1.42 s    (+0.51%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      256.05 ms →      257.79 ms   (+0.68%) |       4   →       4              |        1.02 s  →        1.03 s    (+0.68%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       61.68 ms →       63.02 ms   (+2.17%) |       4   →       4              |      246.71 ms →      252.06 ms   (+2.17%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |       16.93 ms →       16.36 ms   (-3.35%) |       4   →       4              |       67.70 ms →       65.44 ms   (-3.35%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       16.92 ms →       16.36 ms   (-3.35%) |       4   →       4              |       67.69 ms →       65.43 ms   (-3.35%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       38.33 ms →       40.24 ms   (+4.98%) |       4   →       4              |      153.31 ms →      160.94 ms   (+4.98%) | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |       16.64 ms →       16.54 ms   (-0.61%) |       4   →       4              |       66.55 ms →       66.14 ms   (-0.61%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc                 |       16.63 ms →       16.53 ms   (-0.60%) |       4   →       4              |       66.53 ms →       66.13 ms   (-0.60%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |       52.90 ms →       53.50 ms   (+1.14%) |       4   →       4              |      211.60 ms →      214.02 ms   (+1.14%) | 
  │ │ │ │   └ sddk::matrix_storage::remap_backward|mpi                  |       34.90 ms →       35.44 ms   (+1.54%) |       4   →       4              |      139.62 ms →      141.77 ms   (+1.54%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        1.95 ms →        1.94 ms   (-0.46%) |       4   →       4              |        7.79 ms →        7.75 ms   (-0.46%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       40.48 ms →       40.16 ms   (-0.80%) |       4   →       4              |      161.93 ms →      160.64 ms   (-0.80%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                    |        7.33 ms →        7.01 ms   (-4.34%) |       4   →       4              |       29.31 ms →       28.03 ms   (-4.34%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       27.16 ms →       27.35 ms   (+0.72%) |       8   →       8              |      217.26 ms →      218.83 ms   (+0.72%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.91 ms →       14.78 ms   (-0.84%) |       8   →       8              |      119.29 ms →      118.28 ms   (-0.84%) | 
  │ │ │ └ sddk::wf_inner                                                |       14.87 ms →       14.74 ms   (-0.85%) |       8   →       8              |      118.93 ms →      117.93 ms   (-0.85%) | 
+ │ │ │   ├ sddk::wf_inner|scale                                        |       32.13 ns →       21.62 ns  (-32.68%) |       8   →       8              |      257.00 ns →      173.00 ns  (-32.68%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       14.69 ms →       14.56 ms   (-0.92%) |       8   →       8              |      117.55 ms →      116.47 ms   (-0.92%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       21.25 ns →       25.25 ns  (+18.82%) |       8   →       8              |      170.00 ns →      202.00 ns  (+18.82%) | 
  │ │ ├ Eigensolver_scalapack|pzhegvx                                   |      122.38 ms →      117.26 ms   (-4.18%) |       4   →       4              |      489.52 ms →      469.06 ms   (-4.18%) | 
  │ │ └ sddk::wf_trans                                                  |       23.51 ms →       23.61 ms   (+0.43%) |       4   →       4              |       94.02 ms →       94.43 ms   (+0.43%) | 
  │ │   └ sddk::wf_trans|pw                                             |       23.35 ms →       23.33 ms   (-0.09%) |       4   →       4              |       93.40 ms →       93.32 ms   (-0.09%) | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      432.00 ns →      408.25 ns   (-5.50%) |       4   →       4              |        1.73 μs →        1.63 μs   (-5.50%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      232.02 s  →      212.33 s    (-8.49%) |       1   →       1              |      232.02 s  →      212.33 s    (-8.49%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.76 ms →        5.80 ms   (+0.72%) |      19   →      19              |      109.51 ms →      110.29 ms   (+0.72%) | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        8.91 s  →        7.85 s   (-11.93%) |      26   →      27     (+3.85%) |      231.71 s  →      211.92 s    (-8.54%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        4.52 ms →        4.44 ms   (-1.83%) |      26   →      27     (+3.85%) |      117.62 ms →      119.90 ms   (+1.94%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.16 ms →        4.09 ms   (-1.88%) |      26   →      27     (+3.85%) |      108.26 ms →      110.31 ms   (+1.90%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      954.37 μs →      954.31 μs   (-0.01%) |      26   →      27     (+3.85%) |       24.81 ms →       25.77 ms   (+3.84%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.32 ms →        2.25 ms   (-3.12%) |      26   →      27     (+3.85%) |       60.33 ms →       60.69 ms   (+0.60%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.96 μs →       64.60 μs   (-0.55%) |      52   →      54     (+3.85%) |        3.38 ms →        3.49 ms   (+3.27%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       94.54 μs →       93.27 μs   (-1.34%) |      26   →      27     (+3.85%) |        2.46 ms →        2.52 ms   (+2.45%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       66.47 μs →       65.99 μs   (-0.73%) |      26   →      27     (+3.85%) |        1.73 ms →        1.78 ms   (+3.09%) | 
+ │ │ ├ sirius::Band::solve                                             |        6.81 s  →        5.75 s   (-15.58%) |      26   →      27     (+3.85%) |      177.15 s  →      155.30 s   (-12.33%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      349.35 μs →      321.85 μs   (-7.87%) |     104   →     108     (+3.85%) |       36.33 ms →       34.76 ms   (-4.33%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      343.51 μs →      316.56 μs   (-7.85%) |     104   →     108     (+3.85%) |       35.73 ms →       34.19 ms   (-4.30%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.23 μs →        3.88 μs   (-8.38%) |     104   →     108     (+3.85%) |      440.37 μs →      418.99 μs   (-4.86%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.70 s  →        1.44 s   (-15.58%) |     104   →     108     (+3.85%) |      177.11 s  →      155.26 s   (-12.34%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       12.11 ms →       12.15 ms   (+0.33%) |     104   →     108     (+3.85%) |        1.26 s  →        1.31 s    (+4.19%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |      670.79 ns →      697.32 ns   (+3.96%) |     624   →     648     (+3.85%) |      418.57 μs →      451.86 μs   (+7.95%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        1.83 ms →        1.83 ms   (-0.31%) |     104   →     108     (+3.85%) |      190.56 ms →      197.27 ms   (+3.52%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      355.19 μs →      353.85 μs   (-0.37%) |     104   →     108     (+3.85%) |       36.94 ms →       38.22 ms   (+3.46%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |      549.94 μs →      548.08 μs   (-0.34%) |     208   →     216     (+3.85%) |      114.39 ms →      118.38 ms   (+3.49%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.68 s  →        1.41 s   (-15.80%) |     104   →     108     (+3.85%) |      174.72 s  →      152.78 s   (-12.56%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       68.26 ms →       66.76 ms   (-2.20%) |     919   →     998     (+8.60%) |       62.73 s  →       66.62 s    (+6.20%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       43.40 ms →       42.68 ms   (-1.68%) |     919   →     998     (+8.60%) |       39.89 s  →       42.59 s    (+6.78%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        8.25 ms →        8.45 ms   (+2.42%) |     919   →     998     (+8.60%) |        7.58 s  →        8.43 s   (+11.23%) | 
  │ │ │ │   │ │ │ ├ sddk::matrix_storage::set_num_extra                 |      228.95 μs →      216.02 μs   (-5.65%) |     919   →     998     (+8.60%) |      210.40 ms →      215.59 ms   (+2.46%) | 
  │ │ │ │   │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc         |        2.01 ms →        1.98 ms   (-1.39%) |     104   →     108     (+3.85%) |      208.62 ms →      213.64 ms   (+2.40%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::remap_forward|mpi             |        6.46 ms →        6.53 ms   (+1.06%) |     919   →     998     (+8.60%) |        5.94 s  →        6.52 s    (+9.75%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |       88.45 μs →       82.80 μs   (-6.39%) |     919   →     998     (+8.60%) |       81.29 ms →       82.63 ms   (+1.65%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra|alloc           |      758.36 μs →      741.07 μs   (-2.28%) |     104   →     108     (+3.85%) |       78.87 ms →       80.04 ms   (+1.48%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |        9.38 ms →        9.46 ms   (+0.80%) |     919   →     998     (+8.60%) |        8.62 s  →        9.44 s    (+9.46%) | 
- │ │ │ │   │ │   └ sddk::matrix_storage::remap_backward|mpi            |        5.79 ms →        6.00 ms   (+3.77%) |     919   →     998     (+8.60%) |        5.32 s  →        5.99 s   (+12.69%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        1.52 ms →        1.51 ms   (-0.17%) |     919   →     998     (+8.60%) |        1.39 s  →        1.51 s    (+8.41%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        8.59 ms →        8.19 ms   (-4.64%) |     919   →     998     (+8.60%) |        7.90 s  →        8.18 s    (+3.56%) | 
  │ │ │ │   │ │ └ sirius::Beta_projectors_base::inner|comm              |        1.31 ms →        1.19 ms   (-8.80%) |     919   →     998     (+8.60%) |        1.20 s  →        1.19 s    (-0.96%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.36 ms →        7.17 ms   (-2.55%) |    1.84 K →    2.00 K   (+8.60%) |       13.53 s  →       14.32 s    (+5.83%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       27.66 ms →       25.80 ms   (-6.74%) |     919   →     998     (+8.60%) |       25.42 s  →       25.74 s    (+1.28%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        2.03 ms →        1.84 ms   (-9.36%) |    1.73 K →    1.89 K   (+8.88%) |        3.53 s  →        3.48 s    (-1.31%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       85.99 ns →       48.24 ns  (-43.91%) |    1.73 K →    1.89 K   (+8.88%) |      149.11 μs →       91.07 μs  (-38.92%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        2.02 ms →        1.83 ms   (-9.42%) |    1.73 K →    1.89 K   (+8.88%) |        3.51 s  →        3.46 s    (-1.37%) | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       64.45 ns →       62.69 ns   (-2.73%) |    1.73 K →    1.89 K   (+8.88%) |      111.75 μs →      118.35 μs   (+5.91%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|potrf                               |      789.12 μs →      808.29 μs   (+2.43%) |     919   →     998     (+8.60%) |      725.21 ms →      806.67 ms  (+11.23%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|trtri                               |      767.33 μs →      703.90 μs   (-8.27%) |     919   →     998     (+8.60%) |      705.18 ms →      702.50 ms   (-0.38%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |        5.33 ms →        4.96 ms   (-6.84%) |    3.57 K →    3.88 K   (+8.73%) |       19.02 s  →       19.27 s    (+1.30%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        3.63 ms →        3.37 ms   (-7.11%) |    5.20 K →    5.66 K   (+8.88%) |       18.86 s  →       19.07 s    (+1.14%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        5.58 ms →        5.13 ms   (-8.13%) |     919   →     998     (+8.60%) |        5.13 s  →        5.12 s    (-0.23%) | 
+ │ │ │ │   │ └ sddk::wf_inner                                          |        3.74 ms →        3.37 ms  (-10.01%) |     919   →     998     (+8.60%) |        3.44 s  →        3.36 s    (-2.27%) | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       69.62 ns →       66.88 ns   (-3.95%) |     919   →     998     (+8.60%) |       63.99 μs →       66.74 μs   (+4.31%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        3.73 ms →        3.36 ms  (-10.04%) |     919   →     998     (+8.60%) |        3.43 s  →        3.35 s    (-2.30%) | 
+ │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       52.98 ns →       45.68 ns  (-13.78%) |     919   →     998     (+8.60%) |       48.69 μs →       45.59 μs   (-6.36%) | 
+ │ │ │ │   ├ Eigensolver_scalapack|pzheevx                             |       66.45 ms →       33.10 ms  (-50.19%) |     919   →     998     (+8.60%) |       61.07 s  →       33.03 s   (-45.91%) | 
  │ │ │ │   ├ sirius::residuals                                         |       10.66 ms →        9.81 ms   (-7.94%) |     899   →     970     (+7.90%) |        9.58 s  →        9.52 s    (-0.67%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       10.29 ms →        9.36 ms   (-9.05%) |     853   →     928     (+8.79%) |        8.78 s  →        8.69 s    (-1.06%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        5.11 ms →        4.64 ms   (-9.09%) |    1.71 K →    1.86 K   (+8.79%) |        8.71 s  →        8.62 s    (-1.10%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      637.22 μs →      630.06 μs   (-1.12%) |     853   →     928     (+8.79%) |      543.55 ms →      584.69 ms   (+7.57%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       51.48 ms →       36.43 ms  (-29.24%) |     209   →     349    (+66.99%) |       10.76 s  →       12.71 s   (+18.16%) | 
- │ │ │ │     └ sddk::wf_trans                                          |       34.15 ms →       21.42 ms  (-37.28%) |     314   →     590    (+87.90%) |       10.72 s  →       12.64 s   (+17.86%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |       25.43 ms →       15.11 ms  (-40.58%) |     419   →     831    (+98.33%) |       10.66 s  →       12.56 s   (+17.84%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      576.90 ns →      492.94 ns  (-14.55%) |     104   →     108     (+3.85%) |       60.00 μs →       53.24 μs  (-11.27%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       20.89 μs →       22.71 μs   (+8.73%) |      26   →      27     (+3.85%) |      543.15 μs →      613.28 μs  (+12.91%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      590.93 μs →      592.15 μs   (+0.21%) |      26   →      27     (+3.85%) |       15.36 ms →       15.99 ms   (+4.06%) | 
  │ │ ├ sirius::Density::generate                                       |      892.83 ms →      890.85 ms   (-0.22%) |      26   →      27     (+3.85%) |       23.21 s  →       24.05 s    (+3.62%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      521.53 ms →      523.99 ms   (+0.47%) |      26   →      27     (+3.85%) |       13.56 s  →       14.15 s    (+4.34%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |       23.46 ms →       24.53 ms   (+4.57%) |     104   →     108     (+3.85%) |        2.44 s  →        2.65 s    (+8.59%) | 
  │ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                       |        8.55 μs →        8.33 μs   (-2.68%) |     104   →     108     (+3.85%) |      889.72 μs →      899.14 μs   (+1.06%) | 
  │ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra|alloc               |       14.66 μs →       15.67 μs   (+6.87%) |       8   →       8              |      117.30 μs →      125.35 μs   (+6.87%) | 
  │ │ │ │ │ └ sddk::matrix_storage::remap_forward|mpi                   |       19.33 ms →       20.40 ms   (+5.56%) |     104   →     108     (+3.85%) |        2.01 s  →        2.20 s    (+9.62%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       29.86 ms →       29.63 ms   (-0.75%) |     104   →     108     (+3.85%) |        3.11 s  →        3.20 s    (+3.07%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        9.65 μs →        9.74 μs   (+0.96%) |     104   →     108     (+3.85%) |        1.00 ms →        1.05 ms   (+4.84%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        1.45 ms →        1.45 ms   (-0.13%) |     104   →     108     (+3.85%) |      151.14 ms →      156.75 ms   (+3.71%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       27.92 ms →       27.71 ms   (-0.75%) |     104   →     108     (+3.85%) |        2.90 s  →        2.99 s    (+3.06%) | 
  │ │ │ │ │ │ └ sirius::Beta_projectors_base::inner|comm                |        3.79 ms →        3.58 ms   (-5.71%) |     104   →     108     (+3.85%) |      394.36 ms →      386.14 ms   (-2.09%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      656.02 ns →      735.44 ns  (+12.11%) |     104   →     108     (+3.85%) |       68.23 μs →       79.43 μs  (+16.42%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       42.73 ms →       42.35 ms   (-0.87%) |     104   →     108     (+3.85%) |        4.44 s  →        4.57 s    (+2.94%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.63 ms →        1.64 ms   (+0.33%) |      26   →      27     (+3.85%) |       42.48 ms →       44.26 ms   (+4.18%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.86 ms →       88.90 ms   (+0.04%) |      26   →      27     (+3.85%) |        2.31 s  →        2.40 s    (+3.89%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.63 ms →       88.66 ms   (+0.04%) |      26   →      27     (+3.85%) |        2.30 s  →        2.39 s    (+3.88%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      278.05 ms →      273.79 ms   (-1.53%) |      26   →      27     (+3.85%) |        7.23 s  →        7.39 s    (+2.26%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      278.05 ms →      273.79 ms   (-1.53%) |      26   →      27     (+3.85%) |        7.23 s  →        7.39 s    (+2.26%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.75 ms →       24.22 ms   (-2.11%) |      26   →      27     (+3.85%) |      643.39 ms →      654.07 ms   (+1.66%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      227.38 ms →      223.86 ms   (-1.55%) |      26   →      27     (+3.85%) |        5.91 s  →        6.04 s    (+2.24%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       24.17 ms →       23.92 ms   (-1.03%) |      26   →      27     (+3.85%) |      628.30 ms →      645.73 ms   (+2.77%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       82.20 ms →       80.73 ms   (-1.79%) |      26   →      27     (+3.85%) |        2.14 s  →        2.18 s    (+1.99%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        7.47 ms →        8.76 ms  (+17.28%) |      26   →      27     (+3.85%) |      194.16 ms →      236.48 ms  (+21.79%) | 
  │ │ ├ sirius::Density::mix                                            |      219.32 ms →      223.42 ms   (+1.87%) |      26   →      27     (+3.85%) |        5.70 s  →        6.03 s    (+5.79%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      965.63 μs →      938.83 μs   (-2.78%) |      26   →      27     (+3.85%) |       25.11 ms →       25.35 ms   (+0.96%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.74 ms →       11.04 ms   (+2.80%) |     334   →     349     (+4.49%) |        3.59 s  →        3.85 s    (+7.41%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.47 ms →       10.38 ms   (-0.88%) |     334   →     349     (+4.49%) |        3.50 s  →        3.62 s    (+3.57%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.47 ms →       10.38 ms   (-0.88%) |     334   →     349     (+4.49%) |        3.50 s  →        3.62 s    (+3.57%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        6.25 ms →        7.00 ms  (+12.14%) |      26   →      27     (+3.85%) |      162.41 ms →      189.13 ms  (+16.45%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.41 ms →        6.19 ms  (+14.32%) |      26   →      27     (+3.85%) |      140.67 ms →      167.00 ms  (+18.72%) | 
  │ │ ├ sirius::Potential::generate                                     |      578.38 ms →      579.90 ms   (+0.26%) |      26   →      27     (+3.85%) |       15.04 s  →       15.66 s    (+4.12%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      136.83 ms →      138.01 ms   (+0.87%) |      26   →      27     (+3.85%) |        3.56 s  →        3.73 s    (+4.75%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       16.90 ms →       17.38 ms   (+2.86%) |      26   →      27     (+3.85%) |      439.37 ms →      469.34 ms   (+6.82%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.24 ms →       10.58 ms   (+3.31%) |      26   →      27     (+3.85%) |      266.23 ms →      285.63 ms   (+7.29%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        9.92 ms →       10.28 ms   (+3.63%) |      26   →      27     (+3.85%) |      257.93 ms →      277.57 ms   (+7.62%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        9.92 ms →       10.28 ms   (+3.64%) |      26   →      27     (+3.85%) |      257.90 ms →      277.56 ms   (+7.62%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      560.31 μs →      552.04 μs   (-1.48%) |      52   →      54     (+3.85%) |       29.14 ms →       29.81 ms   (+2.31%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       48.82 ms →       49.02 ms   (+0.40%) |      26   →      27     (+3.85%) |        1.27 s  →        1.32 s    (+4.26%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.49 ms →       46.72 ms   (+0.50%) |      26   →      27     (+3.85%) |        1.21 s  →        1.26 s    (+4.36%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.00 ms →        2.99 ms   (-0.22%) |      52   →      54     (+3.85%) |      155.77 ms →      161.40 ms   (+3.62%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.29 ms →        5.39 ms   (+1.87%) |      26   →      27     (+3.85%) |      137.62 ms →      145.59 ms   (+5.79%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.53 ms →        6.68 ms   (+2.25%) |      26   →      27     (+3.85%) |      169.79 ms →      180.29 ms   (+6.19%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.94 ms →       90.88 ms   (-0.06%) |      26   →      27     (+3.85%) |        2.36 s  →        2.45 s    (+3.78%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      292.82 ms →      292.93 ms   (+0.04%) |      26   →      27     (+3.85%) |        7.61 s  →        7.91 s    (+3.88%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      281.79 ms →      276.02 ms   (-2.05%) |      26   →      27     (+3.85%) |        7.33 s  →        7.45 s    (+1.72%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      281.79 ms →      276.02 ms   (-2.05%) |      26   →      27     (+3.85%) |        7.33 s  →        7.45 s    (+1.72%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.05 ms →       27.21 ms   (+0.56%) |      26   →      27     (+3.85%) |      703.41 ms →      734.58 ms   (+4.43%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      227.00 ms →      221.24 ms   (-2.54%) |      26   →      27     (+3.85%) |        5.90 s  →        5.97 s    (+1.21%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.95 ms →       23.80 ms   (-0.61%) |      26   →      27     (+3.85%) |      622.69 ms →      642.69 ms   (+3.21%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.64 ms →        5.55 ms   (-1.52%) |      26   →      27     (+3.85%) |      146.54 ms →      149.86 ms   (+2.27%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.28 ms →       10.61 ms   (+3.20%) |     182   →     189     (+3.85%) |        1.87 s  →        2.01 s    (+7.17%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        9.98 ms →       10.25 ms   (+2.67%) |     182   →     189     (+3.85%) |        1.82 s  →        1.94 s    (+6.62%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.98 ms →       10.25 ms   (+2.67%) |     182   →     189     (+3.85%) |        1.82 s  →        1.94 s    (+6.62%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       11.06 ms →       10.55 ms   (-4.62%) |      78   →      81     (+3.85%) |      862.45 ms →      854.26 ms   (-0.95%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.77 ms →       10.22 ms   (-5.16%) |      78   →      81     (+3.85%) |      840.40 ms →      827.65 ms   (-1.52%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        9.98 ms →        9.95 ms   (-0.26%) |      26   →      27     (+3.85%) |      259.41 ms →      268.69 ms   (+3.58%) | 
  │ │ └ sirius::Density::get_magnetisation                              |      115.90 μs →      111.19 μs   (-4.06%) |      26   →      27     (+3.85%) |        3.01 ms →        3.00 ms   (-0.37%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |      110.28 μs →      105.90 μs   (-3.97%) |      26   →      27     (+3.85%) |        2.87 ms →        2.86 ms   (-0.28%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.21 ms →        4.99 ms   (-4.27%) |       2   →       2              |       10.42 ms →        9.98 ms   (-4.27%) | 
  │ ├ sirius::Periodic_function|inner                                   |        9.80 ms →       10.29 ms   (+5.01%) |       6   →       6              |       58.81 ms →       61.76 ms   (+5.01%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        9.72 ms →       10.22 ms   (+5.18%) |       6   →       6              |       58.32 ms →       61.34 ms   (+5.18%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        9.72 ms →       10.22 ms   (+5.17%) |       6   →       6              |       58.31 ms →       61.33 ms   (+5.17%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.59 ms →       10.32 ms   (-2.54%) |       3   →       3              |       31.78 ms →       30.97 ms   (-2.54%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.48 ms →       10.27 ms   (-2.02%) |       3   →       3              |       31.43 ms →       30.80 ms   (-2.02%) | 
  ├ sirius::Periodic_function|inner                                     |        9.71 ms →       10.13 ms   (+4.33%) |       2   →       2              |       19.41 ms →       20.25 ms   (+4.33%) | 
  │ └ sirius::Periodic_function|inner_local                             |        9.66 ms →       10.12 ms   (+4.80%) |       2   →       2              |       19.31 ms →       20.24 ms   (+4.80%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.66 ms →       10.12 ms   (+4.80%) |       2   →       2              |       19.31 ms →       20.24 ms   (+4.80%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       10.80 ms →       10.11 ms   (-6.35%) |       1   →       1              |       10.80 ms →       10.11 ms   (-6.35%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       10.79 ms →       10.02 ms   (-7.16%) |       1   →       1              |       10.79 ms →       10.02 ms   (-7.16%) | 
  └ sirius::finalize                                                    |      304.43 ms →      313.51 ms   (+2.98%) |       1   →       1              |      304.43 ms →      313.51 ms   (+2.98%) | 
  ====================================================================================================================================================================================================
```
