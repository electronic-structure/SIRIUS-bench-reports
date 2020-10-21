# Benchmark 58f31ed08f2b4e9e6d289f9ed116027f00413e03 vs 8cf25a48a521cee28df94fe46e001c67fed20f54
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      133.62 s  →      130.66 s    (-2.22%) |       1   →       1              |      133.62 s  →      130.66 s    (-2.22%) | 
  ├ sirius::initialize                                                  |        2.65 s  →        2.70 s    (+1.97%) |       1   →       1              |        2.65 s  →        2.70 s    (+1.97%) | 
  ├ sirius::Simulation_context::initialize                              |        2.89 s  →        2.89 s    (+0.06%) |       1   →       1              |        2.89 s  →        2.89 s    (+0.06%) | 
- │ ├ sirius::Simulation_context::init_comm                             |      325.48 μs →       14.02 ms (+4208.08%) |       1   →       1              |      325.48 μs →       14.02 ms (+4208.08%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      108.35 ms →       77.70 ms  (-28.29%) |       1   →       1              |      108.35 ms →       77.70 ms  (-28.29%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       42.69 ms →       27.30 ms  (-36.07%) |       2   →       2              |       85.39 ms →       54.59 ms  (-36.07%) | 
  │ │ └ sirius::Unit_cell::update                                       |       22.88 ms →       23.03 ms   (+0.67%) |       1   →       1              |       22.88 ms →       23.03 ms   (+0.67%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.74 ms →        6.36 ms   (-5.60%) |       1   →       1              |        6.74 ms →        6.36 ms   (-5.60%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       16.10 ms →       16.63 ms   (+3.30%) |       1   →       1              |       16.10 ms →       16.63 ms   (+3.30%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       16.08 ms →       16.61 ms   (+3.29%) |       1   →       1              |       16.08 ms →       16.61 ms   (+3.29%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.14 ms →        4.12 ms   (-0.51%) |       1   →       1              |        4.14 ms →        4.12 ms   (-0.51%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.32 ms   (-0.62%) |       1   →       1              |        2.33 ms →        2.32 ms   (-0.62%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      106.53 μs →      105.08 μs   (-1.36%) |       1   →       1              |      106.53 μs →      105.08 μs   (-1.36%) | 
  │ └ sirius::Simulation_context::update                                |        2.73 s  →        2.75 s    (+0.68%) |       1   →       1              |        2.73 s  →        2.75 s    (+0.68%) | 
  │   ├ sirius::Unit_cell::update                                       |       11.01 ms →       10.64 ms   (-3.41%) |       1   →       1              |       11.01 ms →       10.64 ms   (-3.41%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.56 ms →        4.27 ms   (-6.48%) |       1   →       1              |        4.56 ms →        4.27 ms   (-6.48%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.42 ms →        6.34 ms   (-1.28%) |       1   →       1              |        6.42 ms →        6.34 ms   (-1.28%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.40 ms →        6.32 ms   (-1.28%) |       1   →       1              |        6.40 ms →        6.32 ms   (-1.28%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.90 ms →        3.83 ms   (-1.93%) |       1   →       1              |        3.90 ms →        3.83 ms   (-1.93%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.32 ms →        2.32 ms   (+0.03%) |       1   →       1              |        2.32 ms →        2.32 ms   (+0.03%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      105.72 μs →      102.99 μs   (-2.58%) |       1   →       1              |      105.72 μs →      102.99 μs   (-2.58%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       63.18 ms →       62.57 ms   (-0.97%) |       2   →       2              |      126.36 ms →      125.14 ms   (-0.97%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.14 ms →        5.12 ms   (-0.39%) |       2   →       2              |       10.28 ms →       10.24 ms   (-0.39%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.47 ms →        4.46 ms   (-0.18%) |       1   →       1              |        4.47 ms →        4.46 ms   (-0.18%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.76 ms →       22.03 ms   (+1.23%) |       2   →       2              |       43.52 ms →       44.06 ms   (+1.23%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       15.01 ms →       14.82 ms   (-1.24%) |       2   →       2              |       30.02 ms →       29.65 ms   (-1.24%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.67 ms →       19.73 ms   (+0.32%) |       4   →       4              |       78.68 ms →       78.94 ms   (+0.32%) | 
  │   ├ sddk::Gvec::init                                                |      174.17 ms →      175.15 ms   (+0.56%) |       2   →       2              |      348.33 ms →      350.30 ms   (+0.56%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      130.77 ms →      132.06 ms   (+0.99%) |       2   →       2              |      261.54 ms →      264.13 ms   (+0.99%) | 
  │   ├ sddk::Gvec_shells                                               |      181.59 ms →      179.57 ms   (-1.11%) |       1   →       1              |      181.59 ms →      179.57 ms   (-1.11%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.32 ms →        1.32 ms   (+0.00%) |       1   →       1              |        1.32 ms →        1.32 ms   (+0.00%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      293.20 ms →      298.31 ms   (+1.74%) |       2   →       2              |      586.40 ms →      596.62 ms   (+1.74%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       35.47 ms →       35.89 ms   (+1.17%) |       1   →       1              |       35.47 ms →       35.89 ms   (+1.17%) | 
  │ ├ sirius::K_point::K_point                                          |        2.31 μs →        2.25 μs   (-2.68%) |       4   →       4              |        9.23 μs →        8.98 μs   (-2.68%) | 
  │ └ sirius::K_point_set::initialize                                   |       35.37 ms →       35.78 ms   (+1.17%) |       1   →       1              |       35.37 ms →       35.78 ms   (+1.17%) | 
  │   └ sirius::K_point::initialize                                     |       35.28 ms →       35.68 ms   (+1.14%) |       1   →       1              |       35.28 ms →       35.68 ms   (+1.14%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       18.08 ms →       17.96 ms   (-0.65%) |       1   →       1              |       18.08 ms →       17.96 ms   (-0.65%) | 
  │     │ └ sddk::Gvec::init                                            |        8.10 ms →        8.09 ms   (-0.20%) |       1   →       1              |        8.10 ms →        8.09 ms   (-0.20%) | 
- │     ├ sddk::matrix_storage::matrix_storage                          |        8.72 μs →        9.75 μs  (+11.81%) |       1   →       1              |        8.72 μs →        9.75 μs  (+11.81%) | 
  │     └ sirius::K_point::update                                       |       12.40 ms →       12.85 ms   (+3.59%) |       1   →       1              |       12.40 ms →       12.85 ms   (+3.59%) | 
  │       └ sirius::Beta_projectors                                     |        6.13 ms →        6.08 ms   (-0.83%) |       1   →       1              |        6.13 ms →        6.08 ms   (-0.83%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.52 ms →        3.50 ms   (-0.66%) |       1   →       1              |        3.52 ms →        3.50 ms   (-0.66%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.28 ms →        5.38 ms   (+1.84%) |       2   →       2              |       10.56 ms →       10.75 ms   (+1.84%) | 
  ├ sirius::Potential                                                   |      158.27 ms →      160.68 ms   (+1.52%) |       1   →       1              |      158.27 ms →      160.68 ms   (+1.52%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.87 ms →        5.77 ms   (-1.55%) |       6   →       6              |       35.19 ms →       34.65 ms   (-1.55%) | 
  │ └ sirius::Potential::update                                         |      122.32 ms →      125.32 ms   (+2.45%) |       1   →       1              |      122.32 ms →      125.32 ms   (+2.45%) | 
  │   └ sirius::Potential::generate_local_potential                     |      121.52 ms →      124.57 ms   (+2.51%) |       1   →       1              |      121.52 ms →      124.57 ms   (+2.51%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      110.19 ms →      110.89 ms   (+0.63%) |       1   →       1              |      110.19 ms →      110.89 ms   (+0.63%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |       10.42 ms →       12.78 ms  (+22.57%) |       1   →       1              |       10.42 ms →       12.78 ms  (+22.57%) | 
  ├ sirius::Density                                                     |      134.74 ms →      136.26 ms   (+1.13%) |       1   →       1              |      134.74 ms →      136.26 ms   (+1.13%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.41 ms →        5.16 ms   (-4.61%) |       2   →       2              |       10.83 ms →       10.33 ms   (-4.61%) | 
  │ └ sirius::Density::update                                           |      123.63 ms →      125.67 ms   (+1.65%) |       1   →       1              |      123.63 ms →      125.67 ms   (+1.65%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      123.19 ms →      125.22 ms   (+1.65%) |       1   →       1              |      123.19 ms →      125.22 ms   (+1.65%) | 
- │     ├ sirius::rho_core_ri_pseudo|values                             |      108.65 μs →      141.16 μs  (+29.93%) |       1   →       1              |      108.65 μs →      141.16 μs  (+29.93%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      112.20 ms →      110.98 ms   (-1.09%) |       1   →       1              |      112.20 ms →      110.98 ms   (-1.09%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |       10.42 ms →       13.67 ms  (+31.16%) |       1   →       1              |       10.42 ms →       13.67 ms  (+31.16%) | 
  ├ sirius::Density::initial_density                                    |      175.18 ms →      175.29 ms   (+0.06%) |       1   →       1              |      175.18 ms →      175.29 ms   (+0.06%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |      111.71 ms →      110.25 ms   (-1.31%) |       1   →       1              |      111.71 ms →      110.25 ms   (-1.31%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |       10.61 ms →       11.49 ms   (+8.33%) |       2   →       2              |       21.22 ms →       22.98 ms   (+8.33%) | 
  │ └ sirius::Periodic_function::integrate                              |        9.72 ms →       10.12 ms   (+4.04%) |       1   →       1              |        9.72 ms →       10.12 ms   (+4.04%) | 
  ├ sirius::Potential::generate                                         |      590.61 ms →      594.56 ms   (+0.67%) |       1   →       1              |      590.61 ms →      594.56 ms   (+0.67%) | 
  │ ├ sirius::Potential::poisson                                        |      136.78 ms →      137.58 ms   (+0.58%) |       1   →       1              |      136.78 ms →      137.58 ms   (+0.58%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |       16.63 ms →       16.97 ms   (+2.00%) |       1   →       1              |       16.63 ms →       16.97 ms   (+2.00%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        9.97 ms →       10.88 ms   (+9.19%) |       1   →       1              |        9.97 ms →       10.88 ms   (+9.19%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        9.89 ms →       10.86 ms   (+9.86%) |       1   →       1              |        9.89 ms →       10.86 ms   (+9.86%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        9.88 ms →       10.86 ms   (+9.87%) |       1   →       1              |        9.88 ms →       10.86 ms   (+9.87%) | 
  │ ├ sirius::Periodic_function::add                                    |      552.35 μs →      545.50 μs   (-1.24%) |       2   →       2              |        1.10 ms →        1.09 ms   (-1.24%) | 
  │ ├ sirius::Potential::xc                                             |       53.55 ms →       56.04 ms   (+4.66%) |       1   →       1              |       53.55 ms →       56.04 ms   (+4.66%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       51.14 ms →       53.74 ms   (+5.08%) |       1   →       1              |       51.14 ms →       53.74 ms   (+5.08%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.73 ms →        5.59 ms   (-2.57%) |       2   →       2              |       11.47 ms →       11.17 ms   (-2.57%) | 
- │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.11 ms →        6.20 ms  (+21.34%) |       1   →       1              |        5.11 ms →        6.20 ms  (+21.34%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.96 ms →        5.79 ms   (-2.86%) |       1   →       1              |        5.96 ms →        5.79 ms   (-2.86%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.80 ms →       92.84 ms   (+0.04%) |       1   →       1              |       92.80 ms →       92.84 ms   (+0.04%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      299.02 ms →      299.87 ms   (+0.28%) |       1   →       1              |      299.02 ms →      299.87 ms   (+0.28%) | 
  ├ sirius::Hamiltonian0                                                |        8.39 ms →        8.35 ms   (-0.51%) |       1   →       1              |        8.39 ms →        8.35 ms   (-0.51%) | 
  │ ├ sirius::Local_operator                                            |        8.04 ms →        8.00 ms   (-0.40%) |       1   →       1              |        8.04 ms →        8.00 ms   (-0.40%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.74 ms →        4.69 ms   (-0.94%) |       1   →       1              |        4.74 ms →        4.69 ms   (-0.94%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.39 ms →        2.40 ms   (+0.54%) |       1   →       1              |        2.39 ms →        2.40 ms   (+0.54%) | 
  │ ├ sirius::Non_local_operator                                        |       62.86 μs →       62.40 μs   (-0.72%) |       2   →       2              |      125.71 μs →      124.80 μs   (-0.72%) | 
  │ ├ sirius::D_operator::initialize                                    |      102.07 μs →       95.59 μs   (-6.35%) |       1   →       1              |      102.07 μs →       95.59 μs   (-6.35%) | 
  │ └ sirius::Q_operator::initialize                                    |       73.97 μs →       71.12 μs   (-3.85%) |       1   →       1              |       73.97 μs →       71.12 μs   (-3.85%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.85 s  →        1.85 s    (-0.04%) |       1   →       1              |        1.85 s  →        1.85 s    (-0.04%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.62 ms →       18.63 ms   (+0.07%) |       1   →       1              |       18.62 ms →       18.63 ms   (+0.07%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      184.73 μs →      189.24 μs   (+2.44%) |       1   →       1              |      184.73 μs →      189.24 μs   (+2.44%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       18.43 ms →       18.44 ms   (+0.05%) |       1   →       1              |       18.43 ms →       18.44 ms   (+0.05%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.83 s  →        1.83 s    (-0.04%) |       1   →       1              |        1.83 s  →        1.83 s    (-0.04%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      126.90 ms →      126.52 ms   (-0.30%) |       4   →       4              |      507.59 ms →      506.08 ms   (-0.30%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       52.35 ms →       51.90 ms   (-0.86%) |       1   →       1              |       52.35 ms →       51.90 ms   (-0.86%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.00 ms →       21.03 ms   (+0.14%) |       1   →       1              |       21.00 ms →       21.03 ms   (+0.14%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      634.13 ms →      636.67 ms   (+0.40%) |       1   →       1              |      634.13 ms →      636.67 ms   (+0.40%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      297.35 ms →      297.24 ms   (-0.04%) |       1   →       1              |      297.35 ms →      297.24 ms   (-0.04%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.33 μs →        3.24 μs   (-2.61%) |       1   →       1              |        3.33 μs →        3.24 μs   (-2.61%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.40 μs →        2.25 μs   (-6.49%) |       1   →       1              |        2.40 μs →        2.25 μs   (-6.49%) | 
+ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      419.00 ns →      371.00 ns  (-11.46%) |       1   →       1              |      419.00 ns →      371.00 ns  (-11.46%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      508.00 ns →      506.00 ns   (-0.39%) |       1   →       1              |      508.00 ns →      506.00 ns   (-0.39%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.23 ms →        9.23 ms   (+0.02%) |       1   →       1              |        9.23 ms →        9.23 ms   (+0.02%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      120.59 ms →      121.20 ms   (+0.51%) |       1   →       1              |      120.59 ms →      121.20 ms   (+0.51%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      103.47 ms →      104.49 ms   (+0.99%) |       2   →       2              |      206.93 ms →      208.97 ms   (+0.99%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       40.18 ms →       40.18 ms   (-0.02%) |       2   →       2              |       80.37 ms →       80.35 ms   (-0.02%) | 
  │ │ │ └ sddk::wf_inner                                                |       39.63 ms →       39.61 ms   (-0.07%) |       2   →       2              |       79.27 ms →       79.21 ms   (-0.07%) | 
  │ │ │   ├ sddk::wf_inner|scale                                        |       18.50 ns →       19.00 ns   (+2.70%) |       2   →       2              |       37.00 ns →       38.00 ns   (+2.70%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       39.16 ms →       39.13 ms   (-0.07%) |       2   →       2              |       78.31 ms →       78.26 ms   (-0.07%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       13.00 ns →       29.00 ns (+123.08%) |       2   →       2              |       26.00 ns →       58.00 ns (+123.08%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       56.48 ms →       56.25 ms   (-0.41%) |       1   →       1              |       56.48 ms →       56.25 ms   (-0.41%) | 
  │ │ └ sddk::wf_trans                                                  |       30.74 ms →       30.77 ms   (+0.08%) |       1   →       1              |       30.74 ms →       30.77 ms   (+0.08%) | 
  │ │   └ sddk::wf_trans|pw                                             |       30.74 ms →       30.77 ms   (+0.08%) |       1   →       1              |       30.74 ms →       30.77 ms   (+0.08%) | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      433.00 ns →      463.00 ns   (+6.93%) |       1   →       1              |      433.00 ns →      463.00 ns   (+6.93%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      124.10 s  →      121.09 s    (-2.43%) |       1   →       1              |      124.10 s  →      121.09 s    (-2.43%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.87 ms →        5.79 ms   (-1.34%) |      19   →      19              |      111.45 ms →      109.95 ms   (-1.34%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.76 s  →        4.83 s    (+1.45%) |      26   →      25     (-3.85%) |      123.72 s  →      120.69 s    (-2.45%) | 
  │ │ ├ sirius::Hamiltonian0                                            |        5.13 ms →        5.33 ms   (+3.80%) |      26   →      25     (-3.85%) |      133.39 ms →      133.14 ms   (-0.19%) | 
  │ │ │ ├ sirius::Local_operator                                        |        4.77 ms →        4.96 ms   (+4.02%) |      26   →      25     (-3.85%) |      123.90 ms →      123.92 ms   (+0.01%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      982.94 μs →      979.81 μs   (-0.32%) |      26   →      25     (-3.85%) |       25.56 ms →       24.50 ms   (-4.15%) | 
  │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.90 ms →        3.08 ms   (+6.29%) |      26   →      25     (-3.85%) |       75.31 ms →       76.97 ms   (+2.21%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.45 μs →       63.94 μs   (-0.79%) |      52   →      50     (-3.85%) |        3.35 ms →        3.20 ms   (-4.61%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       86.99 μs →       88.23 μs   (+1.42%) |      26   →      25     (-3.85%) |        2.26 ms →        2.21 ms   (-2.48%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       77.24 μs →       77.84 μs   (+0.77%) |      26   →      25     (-3.85%) |        2.01 ms →        1.95 ms   (-3.10%) | 
  │ │ ├ sirius::Band::solve                                             |        2.77 s  →        2.85 s    (+3.10%) |      26   →      25     (-3.85%) |       72.00 s  →       71.37 s    (-0.87%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      150.66 μs →      154.84 μs   (+2.78%) |      26   →      25     (-3.85%) |        3.92 ms →        3.87 ms   (-1.17%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      143.69 μs →      146.96 μs   (+2.27%) |      26   →      25     (-3.85%) |        3.74 ms →        3.67 ms   (-1.66%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        5.06 μs →        5.83 μs  (+15.12%) |      26   →      25     (-3.85%) |      131.59 μs →      145.66 μs  (+10.70%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.62 s  →        2.73 s    (+3.94%) |      26   →      25     (-3.85%) |       68.17 s  →       68.13 s    (-0.06%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       94.52 ms →       97.02 ms   (+2.65%) |      26   →      25     (-3.85%) |        2.46 s  →        2.43 s    (-1.30%) | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.61 ms →        7.95 ms   (+4.46%) |     156   →     150     (-3.85%) |        1.19 s  →        1.19 s    (+0.44%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        5.92 ms →        5.89 ms   (-0.43%) |      26   →      25     (-3.85%) |      153.93 ms →      147.37 ms   (-4.26%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      347.29 μs →      349.71 μs   (+0.70%) |      26   →      25     (-3.85%) |        9.03 ms →        8.74 ms   (-3.18%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.28 ms →        2.29 ms   (+0.70%) |      52   →      50     (-3.85%) |      118.48 ms →      114.72 ms   (-3.18%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.49 s  →        2.59 s    (+4.04%) |      26   →      25     (-3.85%) |       64.63 s  →       64.66 s    (+0.04%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      126.61 ms →      126.49 ms   (-0.10%) |     279   →     277     (-0.72%) |       35.32 s  →       35.04 s    (-0.81%) | 
  │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       50.44 ms →       50.34 ms   (-0.20%) |     279   →     277     (-0.72%) |       14.07 s  →       13.94 s    (-0.92%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.01 μs →        2.04 μs   (+1.61%) |     279   →     277     (-0.72%) |      561.31 μs →      566.29 μs   (+0.89%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.70 μs →        1.74 μs   (+2.34%) |     279   →     277     (-0.72%) |      474.68 μs →      482.29 μs   (+1.60%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      353.47 ns →      373.60 ns   (+5.69%) |     279   →     277     (-0.72%) |       98.62 μs →      103.49 μs   (+4.94%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      432.70 ns →      520.49 ns  (+20.29%) |     279   →     277     (-0.72%) |      120.72 μs →      144.18 μs  (+19.43%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.42 ms →        7.42 ms   (-0.04%) |     279   →     277     (-0.72%) |        2.07 s  →        2.05 s    (-0.75%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       23.14 ms →       23.12 ms   (-0.09%) |     279   →     277     (-0.72%) |        6.46 s  →        6.40 s    (-0.81%) | 
  │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       22.80 ms →       22.80 ms   (+0.01%) |     558   →     554     (-0.72%) |       12.72 s  →       12.63 s    (-0.71%) | 
  │ │ │ │   ├ sddk::orthogonalize                                       |       34.13 ms →       34.04 ms   (-0.27%) |     279   →     277     (-0.72%) |        9.52 s  →        9.43 s    (-0.98%) | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |        5.93 ms →        5.90 ms   (-0.45%) |     532   →     529     (-0.56%) |        3.15 s  →        3.12 s    (-1.01%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       79.01 ns →       76.76 ns   (-2.84%) |     532   →     529     (-0.56%) |       42.03 μs →       40.61 μs   (-3.39%) | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        4.82 ms →        4.79 ms   (-0.48%) |     532   →     529     (-0.56%) |        2.56 s  →        2.54 s    (-1.04%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       52.74 ns →       58.16 ns  (+10.27%) |     532   →     529     (-0.56%) |       28.06 μs →       30.76 μs   (+9.65%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      603.34 μs →      598.21 μs   (-0.85%) |     279   →     277     (-0.72%) |      168.33 ms →      165.70 ms   (-1.56%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        9.49 ms →        9.37 ms   (-1.25%) |     279   →     277     (-0.72%) |        2.65 s  →        2.60 s    (-1.96%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |       14.03 ms →       14.06 ms   (+0.20%) |     253   →     252     (-0.40%) |        3.55 s  →        3.54 s    (-0.19%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |        4.68 ms →        4.69 ms   (+0.20%) |     759   →     756     (-0.40%) |        3.55 s  →        3.54 s    (-0.20%) | 
  │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       10.28 ms →       10.23 ms   (-0.46%) |     279   →     277     (-0.72%) |        2.87 s  →        2.83 s    (-1.17%) | 
  │ │ │ │   │ └ sddk::wf_inner                                          |       10.00 ms →        9.97 ms   (-0.38%) |     279   →     277     (-0.72%) |        2.79 s  →        2.76 s    (-1.10%) | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       46.93 ns →       46.82 ns   (-0.24%) |     279   →     277     (-0.72%) |       13.09 μs →       12.97 μs   (-0.95%) | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        8.89 ms →        8.86 ms   (-0.39%) |     279   →     277     (-0.72%) |        2.48 s  →        2.45 s    (-1.10%) | 
+ │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       85.03 ns →       72.72 ns  (-14.48%) |     279   →     277     (-0.72%) |       23.72 μs →       20.14 μs  (-15.09%) | 
  │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       33.36 ms →       35.46 ms   (+6.29%) |     279   →     277     (-0.72%) |        9.31 s  →        9.82 s    (+5.53%) | 
  │ │ │ │   ├ sirius::residuals                                         |       13.44 ms →       13.36 ms   (-0.62%) |     270   →     268     (-0.74%) |        3.63 s  →        3.58 s    (-1.36%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |       12.12 ms →       12.02 ms   (-0.89%) |     260   →     259     (-0.38%) |        3.15 s  →        3.11 s    (-1.27%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        6.06 ms →        6.01 ms   (-0.89%) |     520   →     518     (-0.38%) |        3.15 s  →        3.11 s    (-1.27%) | 
  │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.59 ms →        1.57 ms   (-1.22%) |     260   →     259     (-0.38%) |      412.57 ms →      405.99 ms   (-1.60%) | 
  │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       74.93 ms →       75.91 ms   (+1.32%) |      53   →      52     (-1.89%) |        3.97 s  →        3.95 s    (-0.60%) | 
  │ │ │ │     └ sddk::wf_trans                                          |       49.40 ms →       49.73 ms   (+0.68%) |      80   →      79     (-1.25%) |        3.95 s  →        3.93 s    (-0.58%) | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |       36.93 ms →       37.06 ms   (+0.36%) |     107   →     106     (-0.93%) |        3.95 s  →        3.93 s    (-0.58%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      642.85 ns →      555.08 ns  (-13.65%) |      26   →      25     (-3.85%) |       16.71 μs →       13.88 μs  (-16.97%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       29.54 μs →       33.13 μs  (+12.18%) |      26   →      25     (-3.85%) |      767.93 μs →      828.35 μs   (+7.87%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      614.14 μs →      594.23 μs   (-3.24%) |      26   →      25     (-3.85%) |       15.97 ms →       14.86 ms   (-6.96%) | 
  │ │ ├ sirius::Density::generate                                       |      776.17 ms →      773.42 ms   (-0.35%) |      26   →      25     (-3.85%) |       20.18 s  →       19.34 s    (-4.19%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      402.08 ms →      403.34 ms   (+0.31%) |      26   →      25     (-3.85%) |       10.45 s  →       10.08 s    (-3.54%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.38 μs →        3.74 μs  (-55.35%) |      26   →      25     (-3.85%) |      217.98 μs →       93.59 μs  (-57.06%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.73 μs →        3.40 μs  (-55.94%) |      26   →      25     (-3.85%) |      200.89 μs →       85.11 μs  (-57.63%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |      100.23 ms →      100.44 ms   (+0.20%) |      26   →      25     (-3.85%) |        2.61 s  →        2.51 s    (-3.65%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.66 μs →       11.35 μs  (+48.18%) |      26   →      25     (-3.85%) |      199.08 μs →      283.65 μs  (+42.48%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.12 ms →        7.13 ms   (+0.11%) |      26   →      25     (-3.85%) |      185.14 ms →      178.21 ms   (-3.74%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       91.20 ms →       91.39 ms   (+0.21%) |      26   →      25     (-3.85%) |        2.37 s  →        2.28 s    (-3.64%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      686.23 ns →      866.20 ns  (+26.23%) |      26   →      25     (-3.85%) |       17.84 μs →       21.66 μs  (+21.37%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      162.42 ms →      163.56 ms   (+0.71%) |      26   →      25     (-3.85%) |        4.22 s  →        4.09 s    (-3.17%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.64 ms →        1.64 ms   (+0.18%) |      26   →      25     (-3.85%) |       42.65 ms →       41.08 ms   (-3.68%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.32 ms →       88.32 ms   (+0.01%) |      26   →      25     (-3.85%) |        2.30 s  →        2.21 s    (-3.84%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.09 ms →       88.04 ms   (-0.06%) |      26   →      25     (-3.85%) |        2.29 s  →        2.20 s    (-3.91%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      283.51 ms →      270.42 ms   (-4.62%) |      26   →      25     (-3.85%) |        7.37 s  →        6.76 s    (-8.29%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      283.51 ms →      270.42 ms   (-4.62%) |      26   →      25     (-3.85%) |        7.37 s  →        6.76 s    (-8.29%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       26.02 ms →       24.50 ms   (-5.85%) |      26   →      25     (-3.85%) |      676.57 ms →      612.47 ms   (-9.47%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      230.78 ms →      221.31 ms   (-4.10%) |      26   →      25     (-3.85%) |        6.00 s  →        5.53 s    (-7.79%) | 
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       25.52 ms →       23.42 ms   (-8.24%) |      26   →      25     (-3.85%) |      663.55 ms →      585.48 ms  (-11.77%) | 
- │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       81.29 ms →       90.42 ms  (+11.22%) |      26   →      25     (-3.85%) |        2.11 s  →        2.26 s    (+6.94%) | 
  │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        5.69 ms →        5.65 ms   (-0.63%) |      26   →      25     (-3.85%) |      147.84 ms →      141.25 ms   (-4.46%) | 
  │ │ ├ sirius::Density::mix                                            |      217.66 ms →      210.85 ms   (-3.13%) |      26   →      25     (-3.85%) |        5.66 s  →        5.27 s    (-6.85%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      956.19 μs →      960.54 μs   (+0.45%) |      26   →      25     (-3.85%) |       24.86 ms →       24.01 ms   (-3.41%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.67 ms →       10.18 ms   (-4.56%) |     334   →     319     (-4.49%) |        3.56 s  →        3.25 s    (-8.85%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.40 ms →        9.94 ms   (-4.40%) |     334   →     319     (-4.49%) |        3.47 s  →        3.17 s    (-8.70%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.40 ms →        9.94 ms   (-4.40%) |     334   →     319     (-4.49%) |        3.47 s  →        3.17 s    (-8.70%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        6.87 ms →        5.98 ms  (-12.92%) |      26   →      25     (-3.85%) |      178.61 ms →      149.55 ms  (-16.27%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        6.02 ms →        5.14 ms  (-14.56%) |      26   →      25     (-3.85%) |      156.40 ms →      128.49 ms  (-17.85%) | 
  │ │ ├ sirius::Potential::generate                                     |      581.33 ms →      578.90 ms   (-0.42%) |      26   →      25     (-3.85%) |       15.11 s  →       14.47 s    (-4.25%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      136.91 ms →      137.52 ms   (+0.44%) |      26   →      25     (-3.85%) |        3.56 s  →        3.44 s    (-3.42%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |       16.90 ms →       17.04 ms   (+0.82%) |      26   →      25     (-3.85%) |      439.33 ms →      425.91 ms   (-3.06%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |       10.31 ms →       10.87 ms   (+5.38%) |      26   →      25     (-3.85%) |      268.14 ms →      271.70 ms   (+1.33%) | 
  │ │ │ │   └ sirius::Periodic_function|inner_local                     |        9.99 ms →       10.34 ms   (+3.53%) |      26   →      25     (-3.85%) |      259.67 ms →      258.51 ms   (-0.45%) | 
  │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        9.99 ms →       10.34 ms   (+3.54%) |      26   →      25     (-3.85%) |      259.65 ms →      258.49 ms   (-0.45%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      544.69 μs →      550.54 μs   (+1.07%) |      52   →      50     (-3.85%) |       28.32 ms →       27.53 ms   (-2.81%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       49.90 ms →       48.96 ms   (-1.87%) |      26   →      25     (-3.85%) |        1.30 s  →        1.22 s    (-5.65%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       47.53 ms →       46.59 ms   (-1.98%) |      26   →      25     (-3.85%) |        1.24 s  →        1.16 s    (-5.75%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.04 ms →        3.04 ms   (+0.17%) |      52   →      50     (-3.85%) |      157.89 ms →      152.07 ms   (-3.69%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.89 ms →        5.39 ms   (-8.63%) |      26   →      25     (-3.85%) |      153.24 ms →      134.63 ms  (-12.14%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.55 ms →        6.57 ms   (+0.40%) |      26   →      25     (-3.85%) |      170.22 ms →      164.33 ms   (-3.46%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       90.94 ms →       91.10 ms   (+0.18%) |      26   →      25     (-3.85%) |        2.36 s  →        2.28 s    (-3.67%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      294.64 ms →      292.33 ms   (-0.78%) |      26   →      25     (-3.85%) |        7.66 s  →        7.31 s    (-4.60%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      288.39 ms →      276.66 ms   (-4.07%) |      26   →      25     (-3.85%) |        7.50 s  →        6.92 s    (-7.76%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      288.39 ms →      276.66 ms   (-4.07%) |      26   →      25     (-3.85%) |        7.50 s  →        6.92 s    (-7.76%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       29.38 ms →       27.60 ms   (-6.08%) |      26   →      25     (-3.85%) |      763.92 ms →      689.88 ms   (-9.69%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      228.70 ms →      221.50 ms   (-3.15%) |      26   →      25     (-3.85%) |        5.95 s  →        5.54 s    (-6.87%) | 
+ │ │ │   └ sddk::Gvec_shells::remap_backward                           |       26.46 ms →       23.77 ms  (-10.17%) |      26   →      25     (-3.85%) |      688.05 ms →      594.30 ms  (-13.63%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.19 ms →        5.62 ms   (+8.27%) |      26   →      25     (-3.85%) |      134.99 ms →      140.52 ms   (+4.10%) | 
- │ │ ├ sirius::Periodic_function|inner                                 |       10.26 ms →       11.54 ms  (+12.44%) |     182   →     175     (-3.85%) |        1.87 s  →        2.02 s    (+8.11%) | 
- │ │ │ └ sirius::Periodic_function|inner_local                         |        9.99 ms →       11.03 ms  (+10.32%) |     182   →     175     (-3.85%) |        1.82 s  →        1.93 s    (+6.08%) | 
- │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        9.99 ms →       11.02 ms  (+10.32%) |     182   →     175     (-3.85%) |        1.82 s  →        1.93 s    (+6.08%) | 
+ │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.91 ms →       10.07 ms   (-7.75%) |      78   →      75     (-3.85%) |      851.35 ms →      755.15 ms  (-11.30%) | 
+ │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.61 ms →        9.70 ms   (-8.59%) |      78   →      75     (-3.85%) |      827.89 ms →      727.65 ms  (-12.11%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        9.93 ms →        9.90 ms   (-0.29%) |      26   →      25     (-3.85%) |      258.19 ms →      247.53 ms   (-4.13%) | 
  │ │ └ sirius::Density::get_magnetisation                              |      111.32 μs →      109.18 μs   (-1.92%) |      26   →      25     (-3.85%) |        2.89 ms →        2.73 ms   (-5.69%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |      106.36 μs →      104.29 μs   (-1.95%) |      26   →      25     (-3.85%) |        2.77 ms →        2.61 ms   (-5.72%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.25 ms →        5.25 ms   (-0.18%) |       2   →       2              |       10.51 ms →       10.49 ms   (-0.18%) | 
- │ ├ sirius::Periodic_function|inner                                   |       10.00 ms →       11.31 ms  (+13.13%) |       6   →       6              |       59.98 ms →       67.86 ms  (+13.13%) | 
- │ │ └ sirius::Periodic_function|inner_local                           |        9.72 ms →       11.24 ms  (+15.59%) |       6   →       6              |       58.32 ms →       67.41 ms  (+15.59%) | 
- │ │   └ sirius::Smooth_periodic_function|inner_local                  |        9.72 ms →       11.24 ms  (+15.59%) |       6   →       6              |       58.32 ms →       67.41 ms  (+15.59%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |       10.67 ms →        9.76 ms   (-8.48%) |       3   →       3              |       32.00 ms →       29.29 ms   (-8.48%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.47 ms →        9.67 ms   (-7.63%) |       3   →       3              |       31.42 ms →       29.02 ms   (-7.63%) | 
- ├ sirius::Periodic_function|inner                                     |       10.06 ms →       11.30 ms  (+12.36%) |       2   →       2              |       20.11 ms →       22.60 ms  (+12.36%) | 
- │ └ sirius::Periodic_function|inner_local                             |       10.05 ms →       11.29 ms  (+12.36%) |       2   →       2              |       20.10 ms →       22.58 ms  (+12.36%) | 
- │   └ sirius::Smooth_periodic_function|inner_local                    |       10.05 ms →       11.29 ms  (+12.36%) |       2   →       2              |       20.10 ms →       22.58 ms  (+12.36%) | 
  ├ sirius::Smooth_periodic_function|inner                              |       11.05 ms →        9.96 ms   (-9.83%) |       1   →       1              |       11.05 ms →        9.96 ms   (-9.83%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |       11.04 ms →        9.95 ms   (-9.81%) |       1   →       1              |       11.04 ms →        9.95 ms   (-9.81%) | 
  └ sirius::finalize                                                    |      206.45 ms →      199.49 ms   (-3.37%) |       1   →       1              |      206.45 ms →      199.49 ms   (-3.37%) | 
  ====================================================================================================================================================================================================
```
