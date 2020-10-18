# Benchmark a923c3c8853d846138a8b9a9c096494004b8d208 vs adff978c05fe0b8ea67eae5f2174d5616f15acab
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |       71.59 s  →       72.46 s    (+1.21%) |       1   →       1              |       71.59 s  →       72.46 s    (+1.21%) | 
  ├ sirius::initialize                                                  |        2.86 s  →        2.86 s    (-0.08%) |       1   →       1              |        2.86 s  →        2.86 s    (-0.08%) | 
  ├ sirius::Simulation_context::initialize                              |        3.82 s  →        3.54 s    (-7.36%) |       1   →       1              |        3.82 s  →        3.54 s    (-7.36%) | 
  │ ├ sirius::Simulation_context::init_comm                             |        5.83 ms →        6.28 ms   (+7.81%) |       1   →       1              |        5.83 ms →        6.28 ms   (+7.81%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      204.86 ms →      141.19 ms  (-31.08%) |       1   →       1              |      204.86 ms →      141.19 ms  (-31.08%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       93.68 ms →       62.29 ms  (-33.51%) |       2   →       2              |      187.36 ms →      124.57 ms  (-33.51%) | 
  │ │ └ sirius::Unit_cell::update                                       |       17.39 ms →       16.53 ms   (-4.93%) |       1   →       1              |       17.39 ms →       16.53 ms   (-4.93%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.60 ms →        3.60 ms   (-0.03%) |       1   →       1              |        3.60 ms →        3.60 ms   (-0.03%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       13.74 ms →       12.85 ms   (-6.46%) |       1   →       1              |       13.74 ms →       12.85 ms   (-6.46%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       13.66 ms →       12.78 ms   (-6.45%) |       1   →       1              |       13.66 ms →       12.78 ms   (-6.45%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.74 ms →        2.75 ms   (+0.16%) |       1   →       1              |        2.74 ms →        2.75 ms   (+0.16%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      518.03 μs →      492.76 μs   (-4.88%) |       1   →       1              |      518.03 μs →      492.76 μs   (-4.88%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       16.00 μs →       15.06 μs   (-5.91%) |       1   →       1              |       16.00 μs →       15.06 μs   (-5.91%) | 
  │ └ sirius::Simulation_context::update                                |        3.41 s  →        3.21 s    (-5.97%) |       1   →       1              |        3.41 s  →        3.21 s    (-5.97%) | 
  │   ├ sirius::Unit_cell::update                                       |        7.10 ms →        7.18 ms   (+1.09%) |       1   →       1              |        7.10 ms →        7.18 ms   (+1.09%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.75 ms →        3.78 ms   (+0.70%) |       1   →       1              |        3.75 ms →        3.78 ms   (+0.70%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.30 ms →        3.37 ms   (+2.15%) |       1   →       1              |        3.30 ms →        3.37 ms   (+2.15%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.26 ms →        3.33 ms   (+2.14%) |       1   →       1              |        3.26 ms →        3.33 ms   (+2.14%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.71 ms →        2.78 ms   (+2.44%) |       1   →       1              |        2.71 ms →        2.78 ms   (+2.44%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      505.43 μs →      509.61 μs   (+0.83%) |       1   →       1              |      505.43 μs →      509.61 μs   (+0.83%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       14.66 μs →       13.62 μs   (-7.06%) |       1   →       1              |       14.66 μs →       13.62 μs   (-7.06%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      211.48 ms →      211.68 ms   (+0.09%) |       2   →       2              |      422.96 ms →      423.36 ms   (+0.09%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.18 ms →       15.36 ms   (+1.18%) |       2   →       2              |       30.36 ms →       30.72 ms   (+1.18%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.26 ms →       13.25 ms   (-0.09%) |       1   →       1              |       13.26 ms →       13.25 ms   (-0.09%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.33 ms →       56.34 ms   (+0.00%) |       2   →       2              |      112.67 ms →      112.67 ms   (+0.00%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.02 ms →       45.10 ms   (+0.18%) |       2   →       2              |       90.04 ms →       90.21 ms   (+0.18%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.39 ms →       60.25 ms   (-0.23%) |       4   →       4              |      241.55 ms →      240.99 ms   (-0.23%) | 
  │   ├ sddk::Gvec::init                                                |       94.87 ms →       94.35 ms   (-0.55%) |       2   →       2              |      189.74 ms →      188.70 ms   (-0.55%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       71.09 ms →       70.85 ms   (-0.34%) |       2   →       2              |      142.17 ms →      141.69 ms   (-0.34%) | 
  │   ├ sddk::Gvec_shells                                               |       95.37 ms →      102.88 ms   (+7.88%) |       1   →       1              |       95.37 ms →      102.88 ms   (+7.88%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.96 ms →        1.95 ms   (-0.62%) |       1   →       1              |        1.96 ms →        1.95 ms   (-0.62%) | 
+ │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      553.01 ms →      457.15 ms  (-17.33%) |       2   →       2              |        1.11 s  →      914.31 ms  (-17.33%) | 
- ├ sirius::K_point_set::create_k_mesh                                  |      146.25 ms →      163.28 ms  (+11.64%) |       1   →       1              |      146.25 ms →      163.28 ms  (+11.64%) | 
+ │ ├ sirius::K_point::K_point                                          |        1.71 μs →        1.25 μs  (-26.61%) |       4   →       4              |        6.83 μs →        5.01 μs  (-26.61%) | 
- │ └ sirius::K_point_set::initialize                                   |      146.17 ms →      163.19 ms  (+11.65%) |       1   →       1              |      146.17 ms →      163.19 ms  (+11.65%) | 
  │   └ sirius::K_point::initialize                                     |       28.57 ms →       28.51 ms   (-0.18%) |       1   →       1              |       28.57 ms →       28.51 ms   (-0.18%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       11.17 ms →       10.89 ms   (-2.52%) |       1   →       1              |       11.17 ms →       10.89 ms   (-2.52%) | 
  │     │ └ sddk::Gvec::init                                            |        5.01 ms →        4.84 ms   (-3.32%) |       1   →       1              |        5.01 ms →        4.84 ms   (-3.32%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |       10.67 μs →       10.74 μs   (+0.66%) |       1   →       1              |       10.67 μs →       10.74 μs   (+0.66%) | 
  │     └ sirius::K_point::update                                       |       14.53 ms →       14.75 ms   (+1.56%) |       1   →       1              |       14.53 ms →       14.75 ms   (+1.56%) | 
  │       └ sirius::Beta_projectors                                     |       10.58 ms →       10.75 ms   (+1.58%) |       1   →       1              |       10.58 ms →       10.75 ms   (+1.58%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.63 ms →        8.54 ms   (-1.08%) |       1   →       1              |        8.63 ms →        8.54 ms   (-1.08%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.55 ms →        2.58 ms   (+1.39%) |       2   →       2              |        5.10 ms →        5.17 ms   (+1.39%) | 
  ├ sirius::Potential                                                   |       54.83 ms →       53.56 ms   (-2.32%) |       1   →       1              |       54.83 ms →       53.56 ms   (-2.32%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.95 ms →        2.92 ms   (-1.03%) |       6   →       6              |       17.71 ms →       17.52 ms   (-1.03%) | 
  │ └ sirius::Potential::update                                         |       36.55 ms →       35.39 ms   (-3.16%) |       1   →       1              |       36.55 ms →       35.39 ms   (-3.16%) | 
  │   └ sirius::Potential::generate_local_potential                     |       36.13 ms →       34.98 ms   (-3.18%) |       1   →       1              |       36.13 ms →       34.98 ms   (-3.18%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       30.53 ms →       26.54 ms  (-13.08%) |       1   →       1              |       30.53 ms →       26.54 ms  (-13.08%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        5.06 ms →        7.88 ms  (+55.92%) |       1   →       1              |        5.06 ms →        7.88 ms  (+55.92%) | 
  ├ sirius::Density                                                     |       41.28 ms →       41.29 ms   (+0.02%) |       1   →       1              |       41.28 ms →       41.29 ms   (+0.02%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.83 ms →        2.83 ms   (+0.20%) |       2   →       2              |        5.66 ms →        5.67 ms   (+0.20%) | 
  │ └ sirius::Density::update                                           |       35.49 ms →       35.48 ms   (-0.01%) |       1   →       1              |       35.49 ms →       35.48 ms   (-0.01%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       35.17 ms →       35.19 ms   (+0.06%) |       1   →       1              |       35.17 ms →       35.19 ms   (+0.06%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |       78.02 μs →       79.31 μs   (+1.66%) |       1   →       1              |       78.02 μs →       79.31 μs   (+1.66%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       30.92 ms →       27.00 ms  (-12.67%) |       1   →       1              |       30.92 ms →       27.00 ms  (-12.67%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        3.81 ms →        7.80 ms (+104.73%) |       1   →       1              |        3.81 ms →        7.80 ms (+104.73%) | 
  ├ sirius::Density::initial_density                                    |       64.29 ms →       61.33 ms   (-4.60%) |       1   →       1              |       64.29 ms →       61.33 ms   (-4.60%) | 
+ │ ├ sirius::Simulation_context::make_periodic_function                |       36.64 ms →       27.64 ms  (-24.56%) |       1   →       1              |       36.64 ms →       27.64 ms  (-24.56%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.65 ms →        7.32 ms  (+57.23%) |       2   →       2              |        9.31 ms →       14.64 ms  (+57.23%) | 
- │ └ sirius::Periodic_function::integrate                              |        4.61 ms →        5.38 ms  (+16.66%) |       1   →       1              |        4.61 ms →        5.38 ms  (+16.66%) | 
  ├ sirius::Potential::generate                                         |      370.98 ms →      371.42 ms   (+0.12%) |       1   →       1              |      370.98 ms →      371.42 ms   (+0.12%) | 
  │ ├ sirius::Potential::poisson                                        |       44.52 ms →       42.41 ms   (-4.74%) |       1   →       1              |       44.52 ms →       42.41 ms   (-4.74%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.67 ms →       10.44 ms (+184.75%) |       1   →       1              |        3.67 ms →       10.44 ms (+184.75%) | 
- │ │ └ sirius::Periodic_function|inner                                 |        4.64 ms →        5.91 ms  (+27.36%) |       1   →       1              |        4.64 ms →        5.91 ms  (+27.36%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.63 ms →        4.65 ms   (+0.49%) |       1   →       1              |        4.63 ms →        4.65 ms   (+0.49%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.62 ms →        4.64 ms   (+0.45%) |       1   →       1              |        4.62 ms →        4.64 ms   (+0.45%) | 
  │ ├ sirius::Periodic_function::add                                    |      764.35 μs →      770.37 μs   (+0.79%) |       2   →       2              |        1.53 ms →        1.54 ms   (+0.79%) | 
  │ ├ sirius::Potential::xc                                             |       51.43 ms →       53.46 ms   (+3.95%) |       1   →       1              |       51.43 ms →       53.46 ms   (+3.95%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       50.23 ms →       52.29 ms   (+4.09%) |       1   →       1              |       50.23 ms →       52.29 ms   (+4.09%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.59 ms →        2.55 ms   (-1.75%) |       2   →       2              |        5.19 ms →        5.10 ms   (-1.75%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.45 ms →        4.54 ms   (+1.95%) |       1   →       1              |        4.45 ms →        4.54 ms   (+1.95%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.60 ms →        2.94 ms  (-18.52%) |       1   →       1              |        3.60 ms →        2.94 ms  (-18.52%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      268.52 ms →      269.71 ms   (+0.44%) |       1   →       1              |      268.52 ms →      269.71 ms   (+0.44%) | 
+ │ └ sirius::Potential::generate_PAW_effective_potential               |      263.00 ns →      141.00 ns  (-46.39%) |       1   →       1              |      263.00 ns →      141.00 ns  (-46.39%) | 
- ├ sirius::Hamiltonian0                                                |        6.26 ms →        8.59 ms  (+37.30%) |       1   →       1              |        6.26 ms →        8.59 ms  (+37.30%) | 
- │ ├ sirius::Local_operator                                            |        5.80 ms →        7.81 ms  (+34.60%) |       1   →       1              |        5.80 ms →        7.81 ms  (+34.60%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.75 ms →        2.73 ms   (-0.67%) |       1   →       1              |        2.75 ms →        2.73 ms   (-0.67%) | 
- │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.33 ms →        3.88 ms  (+66.90%) |       1   →       1              |        2.33 ms →        3.88 ms  (+66.90%) | 
- │ ├ sirius::Non_local_operator                                        |       74.49 μs →      264.66 μs (+255.30%) |       2   →       2              |      148.98 μs →      529.32 μs (+255.30%) | 
+ │ ├ sirius::D_operator::initialize                                    |      111.98 μs →       96.53 μs  (-13.79%) |       1   →       1              |      111.98 μs →       96.53 μs  (-13.79%) | 
+ │ └ sirius::Q_operator::initialize                                    |      122.61 μs →       91.83 μs  (-25.11%) |       1   →       1              |      122.61 μs →       91.83 μs  (-25.11%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.28 s  →        1.27 s    (-1.35%) |       1   →       1              |        1.28 s  →        1.27 s    (-1.35%) | 
- │ ├ sirius::Hamiltonian_k                                             |       45.90 ms →       56.01 ms  (+22.01%) |       1   →       1              |       45.90 ms →       56.01 ms  (+22.01%) | 
+ │ │ ├ sirius::Local_operator::prepare_k                               |      310.27 μs →      216.16 μs  (-30.33%) |       1   →       1              |      310.27 μs →      216.16 μs  (-30.33%) | 
- │ │ └ sirius::Beta_projectors_base::prepare                           |       45.59 ms →       55.79 ms  (+22.37%) |       1   →       1              |       45.59 ms →       55.79 ms  (+22.37%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.24 s  →        1.21 s    (-2.21%) |       1   →       1              |        1.24 s  →        1.21 s    (-2.21%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       81.45 ms →       76.10 ms   (-6.57%) |       4   →       4              |      325.79 ms →      304.39 ms   (-6.57%) | 
+ │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       43.72 ms →       37.48 ms  (-14.29%) |       1   →       1              |       43.72 ms →       37.48 ms  (-14.29%) | 
+ │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        8.51 ms →        7.24 ms  (-14.95%) |       1   →       1              |        8.51 ms →        7.24 ms  (-14.95%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      335.76 ms →      316.85 ms   (-5.63%) |       1   →       1              |      335.76 ms →      316.85 ms   (-5.63%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      246.86 ms →      247.09 ms   (+0.09%) |       1   →       1              |      246.86 ms →      247.09 ms   (+0.09%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        4.06 μs →        4.21 μs   (+3.52%) |       1   →       1              |        4.06 μs →        4.21 μs   (+3.52%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.82 μs →        2.84 μs   (+0.57%) |       1   →       1              |        2.82 μs →        2.84 μs   (+0.57%) | 
+ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      511.00 ns →      454.00 ns  (-11.15%) |       1   →       1              |      511.00 ns →      454.00 ns  (-11.15%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      538.00 ns →      534.00 ns   (-0.74%) |       1   →       1              |      538.00 ns →      534.00 ns   (-0.74%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.20 ms →        3.21 ms   (+0.49%) |       1   →       1              |        3.20 ms →        3.21 ms   (+0.49%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.28 ms →       21.26 ms   (-0.14%) |       1   →       1              |       21.28 ms →       21.26 ms   (-0.14%) | 
+ │ │ │ └ sirius::Non_local_operator::apply                             |       32.19 ms →       22.62 ms  (-29.71%) |       2   →       2              |       64.37 ms →       45.25 ms  (-29.71%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       15.37 ms →       14.87 ms   (-3.24%) |       2   →       2              |       30.75 ms →       29.75 ms   (-3.24%) | 
  │ │ │ └ sddk::wf_inner                                                |       15.15 ms →       14.66 ms   (-3.23%) |       2   →       2              |       30.30 ms →       29.32 ms   (-3.23%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       20.50 ns →       27.50 ns  (+34.15%) |       2   →       2              |       41.00 ns →       55.00 ns  (+34.15%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       15.00 ms →       14.51 ms   (-3.26%) |       2   →       2              |       29.99 ms →       29.01 ms   (-3.26%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       18.50 ns →       20.50 ns  (+10.81%) |       2   →       2              |       37.00 ns →       41.00 ns  (+10.81%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      229.50 ms →      249.80 ms   (+8.85%) |       1   →       1              |      229.50 ms →      249.80 ms   (+8.85%) | 
  │ │ └ sddk::wf_trans                                                  |        2.60 ms →        2.60 ms   (+0.18%) |       1   →       1              |        2.60 ms →        2.60 ms   (+0.18%) | 
  │ │   └ sddk::wf_trans|pw                                             |        2.59 ms →        2.60 ms   (+0.20%) |       1   →       1              |        2.59 ms →        2.60 ms   (+0.20%) | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      395.00 ns →      385.00 ns   (-2.53%) |       1   →       1              |      395.00 ns →      385.00 ns   (-2.53%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |       61.86 s  →       63.00 s    (+1.84%) |       1   →       1              |       61.86 s  →       63.00 s    (+1.84%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.46 ms →        2.45 ms   (-0.64%) |      19   →      19              |       46.78 ms →       46.48 ms   (-0.64%) | 
! │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.24 s  →        2.99 s    (-7.83%) |      19   →      21    (+10.53%) |       61.63 s  →       62.78 s    (+1.87%) | 
! │ │ ├ sirius::Hamiltonian0                                            |        5.93 ms →        5.56 ms   (-6.19%) |      19   →      21    (+10.53%) |      112.60 ms →      116.74 ms   (+3.68%) | 
! │ │ │ ├ sirius::Local_operator                                        |        5.26 ms →        4.78 ms   (-9.24%) |      19   →      21    (+10.53%) |      100.03 ms →      100.34 ms   (+0.31%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function                            |      548.96 μs →      559.41 μs   (+1.90%) |      19   →      21    (+10.53%) |       10.43 ms →       11.75 ms  (+12.63%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.38 ms →        3.01 ms  (-10.99%) |      19   →      21    (+10.53%) |       64.18 ms →       63.15 ms   (-1.62%) | 
- │ │ │ ├ sirius::Non_local_operator                                    |      190.69 μs →      249.14 μs  (+30.65%) |      38   →      42    (+10.53%) |        7.25 ms →       10.46 ms  (+44.40%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |      114.23 μs →      116.24 μs   (+1.76%) |      19   →      21    (+10.53%) |        2.17 ms →        2.44 ms  (+12.47%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       89.95 μs →       90.04 μs   (+0.09%) |      19   →      21    (+10.53%) |        1.71 ms →        1.89 ms  (+10.63%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.03 s  →        1.76 s   (-13.11%) |      19   →      21    (+10.53%) |       38.52 s  →       37.00 s    (-3.96%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      203.30 μs →      205.03 μs   (+0.85%) |      19   →      21    (+10.53%) |        3.86 ms →        4.31 ms  (+11.47%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      193.20 μs →      195.94 μs   (+1.42%) |      19   →      21    (+10.53%) |        3.67 ms →        4.11 ms  (+12.10%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        7.40 μs →        6.66 μs  (-10.06%) |      19   →      21    (+10.53%) |      140.63 μs →      139.80 μs   (-0.59%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.97 s  →        1.64 s   (-16.60%) |      19   →      21    (+10.53%) |       37.37 s  →       34.45 s    (-7.82%) | 
! │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       79.06 ms →       72.00 ms   (-8.92%) |      19   →      21    (+10.53%) |        1.50 s  →        1.51 s    (+0.66%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.98 ms →        7.15 ms  (-10.34%) |     114   →     126    (+10.53%) |      909.52 ms →      901.32 ms   (-0.90%) | 
- │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       15.66 ms →       17.88 ms  (+14.15%) |      19   →      21    (+10.53%) |      297.61 ms →      375.49 ms  (+26.17%) | 
! │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      480.09 μs →      467.85 μs   (-2.55%) |      19   →      21    (+10.53%) |        9.12 ms →        9.82 ms   (+7.71%) | 
- │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        7.15 ms →        8.11 ms  (+13.45%) |      38   →      42    (+10.53%) |      271.52 ms →      340.48 ms  (+25.40%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.86 s  →        1.54 s   (-17.24%) |      19   →      21    (+10.53%) |       35.41 s  →       32.39 s    (-8.53%) | 
  │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       55.33 ms →       55.15 ms   (-0.31%) |     356   →     361     (+1.40%) |       19.70 s  →       19.91 s    (+1.09%) | 
+ │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       33.98 ms →       30.32 ms  (-10.78%) |     356   →     361     (+1.40%) |       12.10 s  →       10.94 s    (-9.52%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.75 μs →        2.18 μs  (+24.78%) |     356   →     361     (+1.40%) |      622.95 μs →      788.26 μs  (+26.54%) | 
- │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.49 μs →        1.81 μs  (+20.90%) |     356   →     361     (+1.40%) |      531.64 μs →      651.79 μs  (+22.60%) | 
- │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      398.48 ns →      454.72 ns  (+14.11%) |     356   →     361     (+1.40%) |      141.86 μs →      164.15 μs  (+15.72%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      524.56 ns →      630.73 ns  (+20.24%) |     356   →     361     (+1.40%) |      186.74 μs →      227.69 μs  (+21.93%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        3.14 ms →        2.98 ms   (-5.36%) |     356   →     361     (+1.40%) |        1.12 s  →        1.07 s    (-4.03%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.28 ms →        3.30 ms   (+0.44%) |     356   →     361     (+1.40%) |        1.17 s  →        1.19 s    (+1.85%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.45 ms →        9.27 ms  (+24.41%) |     712   →     722     (+1.40%) |        5.31 s  →        6.70 s   (+26.16%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |        5.99 ms →        6.86 ms  (+14.64%) |     356   →     361     (+1.40%) |        2.13 s  →        2.48 s   (+16.25%) | 
- │ │ │ │   │ ├ sddk::wf_inner                                          |        1.04 ms →        1.22 ms  (+17.52%) |     693   →     701     (+1.15%) |      721.53 ms →      857.72 ms  (+18.87%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       56.90 ns →       39.83 ns  (-30.00%) |     693   →     701     (+1.15%) |       39.43 μs →       27.92 μs  (-29.19%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |      879.08 μs →        1.06 ms  (+20.61%) |     693   →     701     (+1.15%) |      609.20 ms →      743.22 ms  (+22.00%) | 
+ │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       52.56 ns →       42.85 ns  (-18.48%) |     693   →     701     (+1.15%) |       36.43 μs →       30.04 μs  (-17.54%) | 
  │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      139.28 μs →      147.84 μs   (+6.15%) |     356   →     361     (+1.40%) |       49.58 ms →       53.37 ms   (+7.64%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        1.70 ms →        2.12 ms  (+25.22%) |     356   →     361     (+1.40%) |      603.80 ms →      766.67 ms  (+26.97%) | 
  │ │ │ │   │ └ sddk::wf_trans                                          |        2.24 ms →        2.35 ms   (+4.82%) |     337   →     340     (+0.89%) |      755.26 ms →      798.73 ms   (+5.76%) | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |      746.26 μs →      782.27 μs   (+4.82%) |    1.01 K →    1.02 K   (+0.89%) |      754.47 ms →      797.91 ms   (+5.76%) | 
- │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.30 ms →        1.48 ms  (+14.15%) |     356   →     361     (+1.40%) |      461.88 ms →      534.64 ms  (+15.75%) | 
- │ │ │ │   │ └ sddk::wf_inner                                          |        1.23 ms →        1.42 ms  (+15.99%) |     356   →     361     (+1.40%) |      436.95 ms →      513.91 ms  (+17.62%) | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       47.09 ns →       45.59 ns   (-3.19%) |     356   →     361     (+1.40%) |       16.76 μs →       16.46 μs   (-1.83%) | 
- │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        1.06 ms →        1.26 ms  (+18.46%) |     356   →     361     (+1.40%) |      378.36 ms →      454.48 ms  (+20.12%) | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       42.17 ns →       42.60 ns   (+1.04%) |     356   →     361     (+1.40%) |       15.01 μs →       15.38 μs   (+2.46%) | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       33.24 ms →       21.98 ms  (-33.87%) |     356   →     361     (+1.40%) |       11.83 s  →        7.93 s   (-32.94%) | 
- │ │ │ │   ├ sirius::residuals                                         |        2.64 ms →        3.00 ms  (+13.51%) |     340   →     346     (+1.76%) |      897.25 ms →        1.04 s   (+15.52%) | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |        1.38 ms →        1.36 ms   (-1.06%) |     337   →     342     (+1.48%) |      463.58 ms →      465.48 ms   (+0.41%) | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      686.42 μs →      679.13 μs   (-1.06%) |     674   →     684     (+1.48%) |      462.65 ms →      464.53 ms   (+0.41%) | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.17 ms →        1.56 ms  (+33.18%) |     337   →     342     (+1.48%) |      395.77 ms →      534.91 ms  (+35.16%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        7.07 ms →        5.43 ms  (-23.17%) |      54   →      90    (+66.67%) |      381.89 ms →      489.01 ms  (+28.05%) | 
- │ │ │ │     └ sddk::wf_trans                                          |        4.24 ms →        3.02 ms  (-28.74%) |      89   →     159    (+78.65%) |      377.67 ms →      480.81 ms  (+27.31%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |        3.04 ms →        2.11 ms  (-30.77%) |     124   →     228    (+83.87%) |      377.50 ms →      480.50 ms  (+27.29%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      328.68 ns →      540.86 ns  (+64.55%) |      19   →      21    (+10.53%) |        6.25 μs →       11.36 μs  (+81.87%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       19.19 μs →       20.59 μs   (+7.26%) |      19   →      21    (+10.53%) |      364.69 μs →      432.35 μs  (+18.55%) | 
! │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.53 ms →        1.53 ms   (-0.54%) |      19   →      21    (+10.53%) |       29.16 ms →       32.06 ms   (+9.93%) | 
- │ │ ├ sirius::Density::generate                                       |      562.65 ms →      570.44 ms   (+1.38%) |      19   →      21    (+10.53%) |       10.69 s  →       11.98 s   (+12.06%) | 
- │ │ │ ├ sirius::Density::generate_valence                             |      377.33 ms →      445.63 ms  (+18.10%) |      19   →      21    (+10.53%) |        7.17 s  →        9.36 s   (+30.53%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        7.87 μs →        8.27 μs   (+4.96%) |      19   →      21    (+10.53%) |      149.62 μs →      173.58 μs  (+16.01%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.40 μs →        7.78 μs   (+5.12%) |      19   →      21    (+10.53%) |      140.66 μs →      163.43 μs  (+16.18%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       44.25 ms →       37.64 ms  (-14.94%) |      19   →      21    (+10.53%) |      840.75 ms →      790.45 ms   (-5.98%) | 
! │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.27 μs →        7.11 μs   (-2.12%) |      19   →      21    (+10.53%) |      138.04 μs →      149.33 μs   (+8.18%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |       23.62 ms →        6.26 ms  (-73.49%) |      19   →      21    (+10.53%) |      448.73 ms →      131.46 ms  (-70.70%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       19.56 ms →       30.33 ms  (+55.09%) |      19   →      21    (+10.53%) |      371.58 ms →      636.94 ms  (+71.42%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      659.32 ns →      910.05 ns  (+38.03%) |      19   →      21    (+10.53%) |       12.53 μs →       19.11 μs  (+52.56%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |       95.33 ms →      108.47 ms  (+13.79%) |      19   →      21    (+10.53%) |        1.81 s  →        2.28 s   (+25.76%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.01 ms →        2.30 ms  (+14.68%) |      19   →      21    (+10.53%) |       38.12 ms →       48.33 ms  (+26.76%) | 
- │ │ │ │ └ sirius::Density::augment                                    |      195.00 ms →      266.23 ms  (+36.53%) |      19   →      21    (+10.53%) |        3.71 s  →        5.59 s   (+50.90%) | 
- │ │ │ │   └ sirius::Density::generate_rho_aug                         |      194.78 ms →      266.02 ms  (+36.58%) |      19   →      21    (+10.53%) |        3.70 s  →        5.59 s   (+50.95%) | 
+ │ │ │ ├ sirius::Field4D::symmetrize                                   |      156.82 ms →       96.48 ms  (-38.48%) |      19   →      21    (+10.53%) |        2.98 s  →        2.03 s   (-32.00%) | 
+ │ │ │ │ └ sirius::symmetrize_function|fpw                             |      156.82 ms →       96.48 ms  (-38.48%) |      19   →      21    (+10.53%) |        2.98 s  →        2.03 s   (-32.00%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       75.19 ms →       13.26 ms  (-82.36%) |      19   →      21    (+10.53%) |        1.43 s  →      278.49 ms  (-80.51%) | 
- │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       68.44 ms →       69.94 ms   (+2.19%) |      19   →      21    (+10.53%) |        1.30 s  →        1.47 s   (+12.95%) | 
- │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.53 ms →       12.62 ms   (+0.74%) |      19   →      21    (+10.53%) |      238.12 ms →      265.12 ms  (+11.34%) | 
! │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.62 ms →       23.49 ms   (-0.56%) |      19   →      21    (+10.53%) |      448.84 ms →      493.29 ms   (+9.90%) | 
! │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        4.87 ms →        4.83 ms   (-0.82%) |      19   →      21    (+10.53%) |       92.60 ms →      101.51 ms   (+9.62%) | 
- │ │ ├ sirius::Density::mix                                            |      130.51 ms →      135.82 ms   (+4.07%) |      19   →      21    (+10.53%) |        2.48 s  →        2.85 s   (+15.02%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      640.80 μs →      892.89 μs  (+39.34%) |      19   →      21    (+10.53%) |       12.18 ms →       18.75 ms  (+54.01%) | 
- │ │ │ ├ sirius::Periodic_function|inner                               |        4.72 ms →        4.85 ms   (+2.92%) |     229   →     259    (+13.10%) |        1.08 s  →        1.26 s   (+16.40%) | 
- │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.63 ms →        4.81 ms   (+3.95%) |     229   →     259    (+13.10%) |        1.06 s  →        1.25 s   (+17.56%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.63 ms →        4.81 ms   (+3.95%) |     229   →     259    (+13.10%) |        1.06 s  →        1.25 s   (+17.57%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        6.03 ms →        6.12 ms   (+1.47%) |      19   →      21    (+10.53%) |      114.62 ms →      128.55 ms  (+12.15%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.23 ms →        5.27 ms   (+0.71%) |      19   →      21    (+10.53%) |       99.46 ms →      110.71 ms  (+11.31%) | 
! │ │ ├ sirius::Potential::generate                                     |      364.62 ms →      362.70 ms   (-0.53%) |      19   →      21    (+10.53%) |        6.93 s  →        7.62 s    (+9.94%) | 
! │ │ │ ├ sirius::Potential::poisson                                    |       44.31 ms →       42.29 ms   (-4.54%) |      19   →      21    (+10.53%) |      841.80 ms →      888.14 ms   (+5.51%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        3.47 ms →       10.60 ms (+205.85%) |      19   →      21    (+10.53%) |       65.86 ms →      222.63 ms (+238.05%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |        4.78 ms →        5.68 ms  (+18.95%) |      19   →      21    (+10.53%) |       90.78 ms →      119.35 ms  (+31.47%) | 
- │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.64 ms →        4.64 ms   (+0.07%) |      19   →      21    (+10.53%) |       88.07 ms →       97.41 ms  (+10.60%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.63 ms →        4.64 ms   (+0.06%) |      19   →      21    (+10.53%) |       88.05 ms →       97.38 ms  (+10.60%) | 
- │ │ │ ├ sirius::Periodic_function::add                                |      765.55 μs →      787.98 μs   (+2.93%) |      38   →      42    (+10.53%) |       29.09 ms →       33.10 ms  (+13.76%) | 
! │ │ │ ├ sirius::Potential::xc                                         |       45.54 ms →       45.22 ms   (-0.72%) |      19   →      21    (+10.53%) |      865.34 ms →      949.58 ms   (+9.74%) | 
! │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       44.36 ms →       44.04 ms   (-0.73%) |      19   →      21    (+10.53%) |      842.88 ms →      924.83 ms   (+9.72%) | 
! │ │ │ │   ├ sirius::Smooth_periodic_function                          |      686.59 μs →      681.70 μs   (-0.71%) |      38   →      42    (+10.53%) |       26.09 ms →       28.63 ms   (+9.74%) | 
! │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.95 ms →        4.75 ms   (-3.99%) |      19   →      21    (+10.53%) |       94.06 ms →       99.81 ms   (+6.11%) | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.70 ms →        3.14 ms  (-14.94%) |      19   →      21    (+10.53%) |       70.23 ms →       66.03 ms   (-5.99%) | 
- │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.11 ms →      269.07 ms   (+0.36%) |      19   →      21    (+10.53%) |        5.09 s  →        5.65 s   (+10.92%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      226.37 ns →       84.62 ns  (-62.62%) |      19   →      21    (+10.53%) |        4.30 μs →        1.78 μs  (-58.68%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |       94.61 ms →       96.33 ms   (+1.82%) |      19   →      21    (+10.53%) |        1.80 s  →        2.02 s   (+12.54%) | 
- │ │ │ └ sirius::symmetrize_function|fpw                               |       94.61 ms →       96.33 ms   (+1.82%) |      19   →      21    (+10.53%) |        1.80 s  →        2.02 s   (+12.54%) | 
- │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.27 ms →       13.32 ms   (+0.37%) |      19   →      21    (+10.53%) |      252.19 ms →      279.76 ms  (+10.93%) | 
- │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       68.18 ms →       69.80 ms   (+2.38%) |      19   →      21    (+10.53%) |        1.30 s  →        1.47 s   (+13.15%) | 
- │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.52 ms →       12.58 ms   (+0.43%) |      19   →      21    (+10.53%) |      237.94 ms →      264.10 ms  (+11.00%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.96 ms →        4.21 ms   (+6.12%) |      19   →      21    (+10.53%) |       75.29 ms →       88.31 ms  (+17.29%) | 
! │ │ ├ sirius::Periodic_function|inner                                 |        4.72 ms →        4.62 ms   (-2.02%) |     133   →     147    (+10.53%) |      627.57 ms →      679.61 ms   (+8.29%) | 
! │ │ │ └ sirius::Periodic_function|inner_local                         |        4.62 ms →        4.57 ms   (-1.05%) |     133   →     147    (+10.53%) |      613.87 ms →      671.38 ms   (+9.37%) | 
! │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.61 ms →        4.57 ms   (-1.05%) |     133   →     147    (+10.53%) |      613.77 ms →      671.28 ms   (+9.37%) | 
! │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.87 ms →        4.75 ms   (-2.55%) |      57   →      63    (+10.53%) |      277.86 ms →      299.28 ms   (+7.71%) | 
- │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.74 ms →        4.74 ms   (+0.07%) |      57   →      63    (+10.53%) |      270.19 ms →      298.83 ms  (+10.60%) | 
- │ │ ├ sirius::Periodic_function::integrate                            |        4.54 ms →        4.57 ms   (+0.72%) |      19   →      21    (+10.53%) |       86.22 ms →       95.98 ms  (+11.32%) | 
! │ │ └ sirius::Density::get_magnetisation                              |       76.68 μs →       73.76 μs   (-3.81%) |      19   →      21    (+10.53%) |        1.46 ms →        1.55 ms   (+6.32%) | 
! │ │   └ sirius::Density::compute_atomic_mag_mom                       |       71.52 μs →       68.72 μs   (-3.92%) |      19   →      21    (+10.53%) |        1.36 ms →        1.44 ms   (+6.19%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.27 ms →        5.56 ms   (+5.52%) |       2   →       2              |       10.55 ms →       11.13 ms   (+5.52%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.70 ms →        4.81 ms   (+2.27%) |       6   →       6              |       28.22 ms →       28.86 ms   (+2.27%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.55 ms →        4.81 ms   (+5.73%) |       6   →       6              |       27.27 ms →       28.83 ms   (+5.73%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.54 ms →        4.81 ms   (+5.81%) |       6   →       6              |       27.25 ms →       28.83 ms   (+5.81%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.75 ms →        5.00 ms   (+5.38%) |       3   →       3              |       14.24 ms →       15.01 ms   (+5.38%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.74 ms →        4.99 ms   (+5.35%) |       3   →       3              |       14.22 ms →       14.98 ms   (+5.35%) | 
  ├ sirius::Periodic_function|inner                                     |        4.64 ms →        4.79 ms   (+3.22%) |       2   →       2              |        9.29 ms →        9.59 ms   (+3.22%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.64 ms →        4.79 ms   (+3.23%) |       2   →       2              |        9.28 ms →        9.58 ms   (+3.23%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.64 ms →        4.79 ms   (+3.23%) |       2   →       2              |        9.28 ms →        9.58 ms   (+3.23%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.84 ms →        4.97 ms   (+2.58%) |       1   →       1              |        4.84 ms →        4.97 ms   (+2.58%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.83 ms →        4.96 ms   (+2.65%) |       1   →       1              |        4.83 ms →        4.96 ms   (+2.65%) | 
  └ sirius::finalize                                                    |      750.17 ms →      755.37 ms   (+0.69%) |       1   →       1              |      750.17 ms →      755.37 ms   (+0.69%) | 
  ====================================================================================================================================================================================================
```
