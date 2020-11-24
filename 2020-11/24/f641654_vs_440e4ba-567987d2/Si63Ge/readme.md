# Benchmark 440e4baa3b03646988c956603d0cb2cbea939e9f vs f641654ae8bc5cecb285c326c4cb5850ab38d32a
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
- sirius                                                                |       71.60 s  →       97.62 s   (+36.34%) |       1   →       1              |       71.60 s  →       97.62 s   (+36.34%) | 
  ├ sirius::initialize                                                  |        2.91 s  →        2.93 s    (+0.61%) |       1   →       1              |        2.91 s  →        2.93 s    (+0.61%) | 
  ├ sirius::Simulation_context::initialize                              |        3.72 s  →        3.67 s    (-1.38%) |       1   →       1              |        3.72 s  →        3.67 s    (-1.38%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       11.97 ms →        7.45 ms  (-37.74%) |       1   →       1              |       11.97 ms →        7.45 ms  (-37.74%) | 
  │ ├ sirius::Unit_cell::initialize                                     |      146.70 ms →      158.95 ms   (+8.35%) |       1   →       1              |      146.70 ms →      158.95 ms   (+8.35%) | 
  │ │ ├ sirius::Atom_type::init                                         |       64.97 ms →       69.83 ms   (+7.48%) |       2   →       2              |      129.94 ms →      139.66 ms   (+7.48%) | 
- │ │ └ sirius::Unit_cell::update                                       |       16.66 ms →       19.19 ms  (+15.16%) |       1   →       1              |       16.66 ms →       19.19 ms  (+15.16%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.96 ms →        4.99 ms   (+0.48%) |       1   →       1              |        4.96 ms →        4.99 ms   (+0.48%) | 
- │ │   └ sirius::Unit_cell::get_symmetry                               |       11.61 ms →       14.15 ms  (+21.85%) |       1   →       1              |       11.61 ms →       14.15 ms  (+21.85%) | 
- │ │     └ sirius::Unit_cell_symmetry                                  |       11.54 ms →       14.08 ms  (+21.95%) |       1   →       1              |       11.54 ms →       14.08 ms  (+21.95%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.73 ms →        2.76 ms   (+1.08%) |       1   →       1              |        2.73 ms →        2.76 ms   (+1.08%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      557.18 μs →      519.84 μs   (-6.70%) |       1   →       1              |      557.18 μs →      519.84 μs   (-6.70%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       16.07 μs →       16.39 μs   (+1.97%) |       1   →       1              |       16.07 μs →       16.39 μs   (+1.97%) | 
  │ └ sirius::Simulation_context::update                                |        3.37 s  →        3.45 s    (+2.49%) |       1   →       1              |        3.37 s  →        3.45 s    (+2.49%) | 
  │   ├ sirius::Unit_cell::update                                       |        6.93 ms →        6.98 ms   (+0.78%) |       1   →       1              |        6.93 ms →        6.98 ms   (+0.78%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.61 ms →        3.60 ms   (-0.29%) |       1   →       1              |        3.61 ms →        3.60 ms   (-0.29%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.28 ms →        3.35 ms   (+2.07%) |       1   →       1              |        3.28 ms →        3.35 ms   (+2.07%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.24 ms →        3.30 ms   (+2.05%) |       1   →       1              |        3.24 ms →        3.30 ms   (+2.05%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.71 ms →        2.76 ms   (+1.76%) |       1   →       1              |        2.71 ms →        2.76 ms   (+1.76%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      487.28 μs →      505.23 μs   (+3.68%) |       1   →       1              |      487.28 μs →      505.23 μs   (+3.68%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       14.08 μs →       14.43 μs   (+2.44%) |       1   →       1              |       14.08 μs →       14.43 μs   (+2.44%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      212.39 ms →      210.76 ms   (-0.77%) |       2   →       2              |      424.78 ms →      421.51 ms   (-0.77%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.37 ms →       15.15 ms   (-1.40%) |       2   →       2              |       30.74 ms →       30.31 ms   (-1.40%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.26 ms →       13.25 ms   (-0.02%) |       1   →       1              |       13.26 ms →       13.25 ms   (-0.02%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.34 ms →       56.34 ms   (-0.01%) |       2   →       2              |      112.69 ms →      112.67 ms   (-0.01%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.10 ms →       45.21 ms   (+0.24%) |       2   →       2              |       90.20 ms →       90.42 ms   (+0.24%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.11 ms →       60.33 ms   (+0.37%) |       4   →       4              |      240.45 ms →      241.33 ms   (+0.37%) | 
  │   ├ sddk::Gvec::init                                                |       94.82 ms →       97.15 ms   (+2.46%) |       2   →       2              |      189.64 ms →      194.31 ms   (+2.46%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       70.26 ms →       70.97 ms   (+1.01%) |       2   →       2              |      140.52 ms →      141.94 ms   (+1.01%) | 
  │   ├ sddk::Gvec_shells                                               |       96.05 ms →      104.06 ms   (+8.34%) |       1   →       1              |       96.05 ms →      104.06 ms   (+8.34%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.96 ms →        1.96 ms   (-0.02%) |       1   →       1              |        1.96 ms →        1.96 ms   (-0.02%) | 
- │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      508.98 ms →      567.73 ms  (+11.54%) |       2   →       2              |        1.02 s  →        1.14 s   (+11.54%) | 
+ ├ sirius::K_point_set::create_k_mesh                                  |      152.79 ms →       86.83 ms  (-43.17%) |       1   →       1              |      152.79 ms →       86.83 ms  (-43.17%) | 
+ │ ├ sirius::K_point::K_point                                          |        2.40 μs →        1.12 μs  (-53.37%) |       4   →       4              |        9.62 μs →        4.49 μs  (-53.37%) | 
+ │ └ sirius::K_point_set::initialize                                   |      152.71 ms →       86.76 ms  (-43.19%) |       1   →       1              |      152.71 ms →       86.76 ms  (-43.19%) | 
  │   └ sirius::K_point::initialize                                     |       28.52 ms →       28.67 ms   (+0.50%) |       1   →       1              |       28.52 ms →       28.67 ms   (+0.50%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       10.94 ms →       10.92 ms   (-0.20%) |       1   →       1              |       10.94 ms →       10.92 ms   (-0.20%) | 
  │     │ └ sddk::Gvec::init                                            |        4.89 ms →        4.97 ms   (+1.61%) |       1   →       1              |        4.89 ms →        4.97 ms   (+1.61%) | 
+ │     ├ sddk::matrix_storage::matrix_storage                          |        8.74 μs →        7.10 μs  (-18.77%) |       1   →       1              |        8.74 μs →        7.10 μs  (-18.77%) | 
  │     └ sirius::K_point::update                                       |       14.78 ms →       14.84 ms   (+0.40%) |       1   →       1              |       14.78 ms →       14.84 ms   (+0.40%) | 
  │       └ sirius::Beta_projectors                                     |       10.80 ms →       10.89 ms   (+0.87%) |       1   →       1              |       10.80 ms →       10.89 ms   (+0.87%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.82 ms →        8.96 ms   (+1.50%) |       1   →       1              |        8.82 ms →        8.96 ms   (+1.50%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.53 ms →        2.56 ms   (+1.30%) |       2   →       2              |        5.06 ms →        5.12 ms   (+1.30%) | 
  ├ sirius::Potential                                                   |       55.12 ms →       53.04 ms   (-3.78%) |       1   →       1              |       55.12 ms →       53.04 ms   (-3.78%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.91 ms →        2.91 ms   (-0.07%) |       6   →       6              |       17.48 ms →       17.47 ms   (-0.07%) | 
  │ └ sirius::Potential::update                                         |       37.05 ms →       34.95 ms   (-5.66%) |       1   →       1              |       37.05 ms →       34.95 ms   (-5.66%) | 
  │   └ sirius::Potential::generate_local_potential                     |       36.63 ms →       34.55 ms   (-5.67%) |       1   →       1              |       36.63 ms →       34.55 ms   (-5.67%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       31.83 ms →       26.28 ms  (-17.43%) |       1   →       1              |       31.83 ms →       26.28 ms  (-17.43%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        4.25 ms →        7.75 ms  (+82.24%) |       1   →       1              |        4.25 ms →        7.75 ms  (+82.24%) | 
  ├ sirius::Density                                                     |       41.28 ms →       40.30 ms   (-2.37%) |       1   →       1              |       41.28 ms →       40.30 ms   (-2.37%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.83 ms →        2.82 ms   (-0.59%) |       2   →       2              |        5.67 ms →        5.63 ms   (-0.59%) | 
  │ └ sirius::Density::update                                           |       35.46 ms →       34.53 ms   (-2.63%) |       1   →       1              |       35.46 ms →       34.53 ms   (-2.63%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       35.13 ms →       34.23 ms   (-2.57%) |       1   →       1              |       35.13 ms →       34.23 ms   (-2.57%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |       55.82 μs →       56.75 μs   (+1.66%) |       1   →       1              |       55.82 μs →       56.75 μs   (+1.66%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       31.84 ms →       26.28 ms  (-17.46%) |       1   →       1              |       31.84 ms →       26.28 ms  (-17.46%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        2.89 ms →        7.57 ms (+162.27%) |       1   →       1              |        2.89 ms →        7.57 ms (+162.27%) | 
  ├ sirius::Density::initial_density                                    |       64.78 ms →       60.88 ms   (-6.02%) |       1   →       1              |       64.78 ms →       60.88 ms   (-6.02%) | 
+ │ ├ sirius::Simulation_context::make_periodic_function                |       36.91 ms →       26.26 ms  (-28.86%) |       1   →       1              |       36.91 ms →       26.26 ms  (-28.86%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.47 ms →        8.28 ms  (+85.12%) |       2   →       2              |        8.94 ms →       16.56 ms  (+85.12%) | 
+ │ └ sirius::Periodic_function::integrate                              |        5.27 ms →        4.50 ms  (-14.60%) |       1   →       1              |        5.27 ms →        4.50 ms  (-14.60%) | 
  ├ sirius::Potential::generate                                         |      373.11 ms →      369.32 ms   (-1.02%) |       1   →       1              |      373.11 ms →      369.32 ms   (-1.02%) | 
  │ ├ sirius::Potential::poisson                                        |       45.02 ms →       42.28 ms   (-6.09%) |       1   →       1              |       45.02 ms →       42.28 ms   (-6.09%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.89 ms →       11.82 ms (+309.18%) |       1   →       1              |        2.89 ms →       11.82 ms (+309.18%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        5.47 ms →        5.04 ms   (-7.90%) |       1   →       1              |        5.47 ms →        5.04 ms   (-7.90%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.64 ms →        5.03 ms   (+8.43%) |       1   →       1              |        4.64 ms →        5.03 ms   (+8.43%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.63 ms →        5.02 ms   (+8.44%) |       1   →       1              |        4.63 ms →        5.02 ms   (+8.44%) | 
  │ ├ sirius::Periodic_function::add                                    |      807.47 μs →      804.99 μs   (-0.31%) |       2   →       2              |        1.61 ms →        1.61 ms   (-0.31%) | 
  │ ├ sirius::Potential::xc                                             |       51.39 ms →       51.36 ms   (-0.06%) |       1   →       1              |       51.39 ms →       51.36 ms   (-0.06%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       50.20 ms →       50.16 ms   (-0.06%) |       1   →       1              |       50.20 ms →       50.16 ms   (-0.06%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.55 ms →        2.54 ms   (-0.36%) |       2   →       2              |        5.09 ms →        5.07 ms   (-0.36%) | 
- │ │   └ sirius::Smooth_periodic_function::fft_transform               |        3.89 ms →        4.55 ms  (+17.12%) |       1   →       1              |        3.89 ms →        4.55 ms  (+17.12%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.85 ms →        3.59 ms   (-6.88%) |       1   →       1              |        3.85 ms →        3.59 ms   (-6.88%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      269.82 ms →      269.12 ms   (-0.26%) |       1   →       1              |      269.82 ms →      269.12 ms   (-0.26%) | 
+ │ └ sirius::Potential::generate_PAW_effective_potential               |      276.00 ns →      221.00 ns  (-19.93%) |       1   →       1              |      276.00 ns →      221.00 ns  (-19.93%) | 
- ├ sirius::Hamiltonian0                                                |        6.48 ms →        8.79 ms  (+35.71%) |       1   →       1              |        6.48 ms →        8.79 ms  (+35.71%) | 
- │ ├ sirius::Local_operator                                            |        6.04 ms →        8.16 ms  (+35.14%) |       1   →       1              |        6.04 ms →        8.16 ms  (+35.14%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.73 ms →        2.73 ms   (-0.19%) |       1   →       1              |        2.73 ms →        2.73 ms   (-0.19%) | 
- │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.54 ms →        3.99 ms  (+57.03%) |       1   →       1              |        2.54 ms →        3.99 ms  (+57.03%) | 
- │ ├ sirius::Non_local_operator                                        |       72.77 μs →      179.91 μs (+147.23%) |       2   →       2              |      145.54 μs →      359.82 μs (+147.23%) | 
  │ ├ sirius::D_operator::initialize                                    |      116.22 μs →      110.64 μs   (-4.81%) |       1   →       1              |      116.22 μs →      110.64 μs   (-4.81%) | 
+ │ └ sirius::Q_operator::initialize                                    |      108.84 μs →       93.31 μs  (-14.27%) |       1   →       1              |      108.84 μs →       93.31 μs  (-14.27%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.27 s  →        1.29 s    (+1.04%) |       1   →       1              |        1.27 s  →        1.29 s    (+1.04%) | 
- │ ├ sirius::Hamiltonian_k                                             |       16.51 ms →       61.01 ms (+269.63%) |       1   →       1              |       16.51 ms →       61.01 ms (+269.63%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      242.54 μs →      260.15 μs   (+7.26%) |       1   →       1              |      242.54 μs →      260.15 μs   (+7.26%) | 
- │ │ └ sirius::Beta_projectors_base::prepare                           |       16.26 ms →       60.74 ms (+273.62%) |       1   →       1              |       16.26 ms →       60.74 ms (+273.62%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.26 s  →        1.23 s    (-2.48%) |       1   →       1              |        1.26 s  →        1.23 s    (-2.48%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       85.41 ms →       77.06 ms   (-9.77%) |       4   →       4              |      341.65 ms →      308.26 ms   (-9.77%) | 
+ │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       51.09 ms →       37.09 ms  (-27.41%) |       1   →       1              |       51.09 ms →       37.09 ms  (-27.41%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        6.82 ms →        7.28 ms   (+6.85%) |       1   →       1              |        6.82 ms →        7.28 ms   (+6.85%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      312.39 ms →      335.15 ms   (+7.29%) |       1   →       1              |      312.39 ms →      335.15 ms   (+7.29%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      244.62 ms →      246.93 ms   (+0.94%) |       1   →       1              |      244.62 ms →      246.93 ms   (+0.94%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.63 μs →        4.11 μs  (+13.30%) |       1   →       1              |        3.63 μs →        4.11 μs  (+13.30%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.72 μs →        3.13 μs  (+15.07%) |       1   →       1              |        2.72 μs →        3.13 μs  (+15.07%) | 
- │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      346.00 ns →      439.00 ns  (+26.88%) |       1   →       1              |      346.00 ns →      439.00 ns  (+26.88%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      584.00 ns →      584.00 ns            |       1   →       1              |      584.00 ns →      584.00 ns            | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.23 ms →        3.06 ms   (-5.32%) |       1   →       1              |        3.23 ms →        3.06 ms   (-5.32%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.32 ms →       21.29 ms   (-0.11%) |       1   →       1              |       21.32 ms →       21.29 ms   (-0.11%) | 
- │ │ │ └ sirius::Non_local_operator::apply                             |       21.59 ms →       31.92 ms  (+47.82%) |       2   →       2              |       43.18 ms →       63.84 ms  (+47.82%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       16.04 ms →       14.75 ms   (-8.07%) |       2   →       2              |       32.08 ms →       29.49 ms   (-8.07%) | 
  │ │ │ └ sddk::wf_inner                                                |       15.83 ms →       14.54 ms   (-8.17%) |       2   →       2              |       31.66 ms →       29.07 ms   (-8.17%) | 
- │ │ │   ├ sddk::wf_inner|scale                                        |       23.00 ns →       39.00 ns  (+69.57%) |       2   →       2              |       46.00 ns →       78.00 ns  (+69.57%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       15.68 ms →       14.39 ms   (-8.22%) |       2   →       2              |       31.37 ms →       28.79 ms   (-8.22%) | 
- │ │ │   └ sddk::wf_inner|scale_back                                   |       23.50 ns →       32.50 ns  (+38.30%) |       2   →       2              |       47.00 ns →       65.00 ns  (+38.30%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      249.56 ms →      239.34 ms   (-4.10%) |       1   →       1              |      249.56 ms →      239.34 ms   (-4.10%) | 
- │ │ └ sddk::wf_trans                                                  |        2.61 ms →        4.78 ms  (+83.30%) |       1   →       1              |        2.61 ms →        4.78 ms  (+83.30%) | 
- │ │   └ sddk::wf_trans|pw                                             |        2.60 ms →        4.78 ms  (+83.42%) |       1   →       1              |        2.60 ms →        4.78 ms  (+83.42%) | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      386.00 ns →      363.00 ns   (-5.96%) |       1   →       1              |      386.00 ns →      363.00 ns   (-5.96%) | 
- ├ sirius::DFT_ground_state::scf_loop                                  |       61.90 s  →       88.01 s   (+42.19%) |       1   →       1              |       61.90 s  →       88.01 s   (+42.19%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.41 ms →        2.39 ms   (-0.60%) |      17   →      17              |       40.91 ms →       40.67 ms   (-0.60%) | 
- │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        2.93 s  →        4.62 s   (+57.45%) |      21   →      19     (-9.52%) |       61.62 s  →       87.79 s   (+42.45%) | 
+ │ │ ├ sirius::Hamiltonian0                                            |        5.16 ms →        4.70 ms   (-8.83%) |      21   →      19     (-9.52%) |      108.36 ms →       89.38 ms  (-17.51%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        4.52 ms →        4.08 ms   (-9.81%) |      21   →      19     (-9.52%) |       94.97 ms →       77.50 ms  (-18.40%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function                            |      556.20 μs →      549.26 μs   (-1.25%) |      21   →      19     (-9.52%) |       11.68 ms →       10.44 ms  (-10.65%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.84 ms →        2.38 ms  (-16.41%) |      21   →      19     (-9.52%) |       59.69 ms →       45.14 ms  (-24.37%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |      165.34 μs →      163.65 μs   (-1.02%) |      42   →      38     (-9.52%) |        6.94 ms →        6.22 ms  (-10.45%) | 
+ │ │ │ ├ sirius::D_operator::initialize                                |      127.70 μs →      123.83 μs   (-3.03%) |      21   →      19     (-9.52%) |        2.68 ms →        2.35 ms  (-12.27%) | 
+ │ │ │ └ sirius::Q_operator::initialize                                |       95.96 μs →       92.72 μs   (-3.38%) |      21   →      19     (-9.52%) |        2.02 ms →        1.76 ms  (-12.58%) | 
- │ │ ├ sirius::Band::solve                                             |        1.76 s  →        3.46 s   (+96.39%) |      21   →      19     (-9.52%) |       36.95 s  →       65.65 s   (+77.68%) | 
- │ │ │ ├ sirius::Hamiltonian_k                                         |      192.76 μs →      240.39 μs  (+24.71%) |      21   →      19     (-9.52%) |        4.05 ms →        4.57 ms  (+12.83%) | 
- │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      183.31 μs →      231.81 μs  (+26.46%) |      21   →      19     (-9.52%) |        3.85 ms →        4.40 ms  (+14.41%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        7.02 μs →        6.40 μs   (-8.76%) |      21   →      19     (-9.52%) |      147.36 μs →      121.65 μs  (-17.45%) | 
- │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.63 s  →        3.33 s  (+104.44%) |      21   →      19     (-9.52%) |       34.21 s  →       63.28 s   (+84.97%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       71.89 ms →       71.12 ms   (-1.07%) |      21   →      19     (-9.52%) |        1.51 s  →        1.35 s   (-10.49%) | 
- │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.36 ms →        8.14 ms  (+10.57%) |     126   →     114     (-9.52%) |      927.06 ms →      927.43 ms   (+0.04%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       17.83 ms →       17.74 ms   (-0.50%) |      21   →      19     (-9.52%) |      374.41 ms →      337.05 ms   (-9.98%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      453.62 μs →      456.75 μs   (+0.69%) |      21   →      19     (-9.52%) |        9.53 ms →        8.68 ms   (-8.90%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        8.08 ms →        8.06 ms   (-0.26%) |      42   →      38     (-9.52%) |      339.20 ms →      306.09 ms   (-9.76%) | 
- │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.53 s  →        3.23 s  (+111.10%) |      21   →      19     (-9.52%) |       32.15 s  →       61.40 s   (+91.00%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       53.46 ms →       87.05 ms  (+62.84%) |     361   →     363     (+0.55%) |       19.30 s  →       31.60 s   (+63.74%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       30.32 ms →       59.80 ms  (+97.23%) |     361   →     363     (+0.55%) |       10.95 s  →       21.71 s   (+98.33%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.00 μs →        2.08 μs   (+4.14%) |     361   →     363     (+0.55%) |      720.49 μs →      754.44 μs   (+4.71%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.70 μs →        1.74 μs   (+2.77%) |     361   →     363     (+0.55%) |      612.27 μs →      632.71 μs   (+3.34%) | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      397.42 ns →      393.39 ns   (-1.01%) |     361   →     363     (+0.55%) |      143.47 μs →      142.80 μs   (-0.46%) | 
  │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      623.18 ns →      631.69 ns   (+1.37%) |     361   →     363     (+0.55%) |      224.97 μs →      229.30 μs   (+1.93%) | 
  │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.84 ms →        2.87 ms   (+0.95%) |     361   →     363     (+0.55%) |        1.02 s  →        1.04 s    (+1.51%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.30 ms →        4.93 ms  (+49.72%) |     361   →     363     (+0.55%) |        1.19 s  →        1.79 s   (+50.55%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        8.50 ms →        9.72 ms  (+14.40%) |     722   →     726     (+0.55%) |        6.13 s  →        7.06 s   (+15.04%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |        7.23 ms →       11.27 ms  (+56.00%) |     361   →     363     (+0.55%) |        2.61 s  →        4.09 s   (+56.86%) | 
- │ │ │ │   │ ├ sddk::wf_inner                                          |        1.15 ms →        1.46 ms  (+26.85%) |     701   →     707     (+0.86%) |      805.28 ms →        1.03 s   (+27.93%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       59.16 ns →       71.28 ns  (+20.50%) |     701   →     707     (+0.86%) |       41.47 μs →       50.40 μs  (+21.53%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |      984.88 μs →        1.29 ms  (+30.91%) |     701   →     707     (+0.86%) |      690.40 ms →      911.57 ms  (+32.03%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       43.45 ns →       50.33 ns  (+15.83%) |     701   →     707     (+0.86%) |       30.46 μs →       35.58 μs  (+16.82%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      260.21 μs →      705.52 μs (+171.13%) |     361   →     363     (+0.55%) |       93.94 ms →      256.10 ms (+172.63%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        2.40 ms →        3.88 ms  (+61.87%) |     361   →     363     (+0.55%) |      864.84 ms →        1.41 s   (+62.76%) | 
- │ │ │ │   │ └ sddk::wf_trans                                          |        2.48 ms →        4.06 ms  (+63.71%) |     340   →     344     (+1.18%) |      842.73 ms →        1.40 s   (+65.64%) | 
- │ │ │ │   │   └ sddk::wf_trans|pw                                     |      825.40 μs →        1.35 ms  (+63.77%) |    1.02 K →    1.03 K   (+1.18%) |      841.91 ms →        1.40 s   (+65.70%) | 
- │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.46 ms →        2.05 ms  (+40.14%) |     361   →     363     (+0.55%) |      527.74 ms →      743.67 ms  (+40.92%) | 
- │ │ │ │   │ └ sddk::wf_inner                                          |        1.42 ms →        1.97 ms  (+39.09%) |     361   →     363     (+0.55%) |      511.42 ms →      715.30 ms  (+39.86%) | 
- │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       29.62 ns →       51.74 ns  (+74.68%) |     361   →     363     (+0.55%) |       10.69 μs →       18.78 μs  (+75.65%) | 
- │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        1.25 ms →        1.80 ms  (+44.10%) |     361   →     363     (+0.55%) |      451.75 ms →      654.56 ms  (+44.89%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       40.78 ns →       65.53 ns  (+60.71%) |     361   →     363     (+0.55%) |       14.72 μs →       23.79 μs  (+61.60%) | 
- │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       23.25 ms →       60.39 ms (+159.70%) |     361   →     363     (+0.55%) |        8.39 s  →       21.92 s  (+161.14%) | 
- │ │ │ │   ├ sirius::residuals                                         |        2.50 ms →        5.16 ms (+106.21%) |     346   →     345     (-0.29%) |      865.54 ms →        1.78 s  (+105.61%) | 
- │ │ │ │   │ ├ sddk::wf_trans                                          |        1.10 ms →        2.51 ms (+128.40%) |     342   →     344     (+0.58%) |      376.00 ms →      863.80 ms (+129.74%) | 
- │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      548.28 μs →        1.25 ms (+128.73%) |     684   →     688     (+0.58%) |      375.02 ms →      862.81 ms (+130.07%) | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.29 ms →        2.13 ms  (+64.95%) |     342   →     344     (+0.58%) |      441.23 ms →      732.04 ms  (+65.91%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        4.94 ms →        7.95 ms  (+60.91%) |      90   →     158    (+75.56%) |      444.43 ms →        1.26 s  (+182.49%) | 
- │ │ │ │     └ sddk::wf_trans                                          |        2.74 ms →        4.17 ms  (+52.01%) |     159   →     297    (+86.79%) |      436.15 ms →        1.24 s  (+183.94%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |        1.91 ms →        2.84 ms  (+48.52%) |     228   →     436    (+91.23%) |      435.85 ms →        1.24 s  (+184.00%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      419.33 ns →      327.53 ns  (-21.89%) |      21   →      19     (-9.52%) |        8.81 μs →        6.22 μs  (-29.33%) | 
  │ │ │ └ sirius::K_point_set::sync_band_energies                       |       19.82 μs →       20.18 μs   (+1.84%) |      21   →      19     (-9.52%) |      416.18 μs →      383.47 μs   (-7.86%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.54 ms →        1.53 ms   (-0.39%) |      21   →      19     (-9.52%) |       32.26 ms →       29.07 ms   (-9.87%) | 
+ │ │ ├ sirius::Density::generate                                       |      570.26 ms →      563.09 ms   (-1.26%) |      21   →      19     (-9.52%) |       11.98 s  →       10.70 s   (-10.66%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      414.87 ms →      431.01 ms   (+3.89%) |      21   →      19     (-9.52%) |        8.71 s  →        8.19 s    (-6.00%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        7.47 μs →        8.49 μs  (+13.60%) |      21   →      19     (-9.52%) |      156.87 μs →      161.23 μs   (+2.78%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        6.77 μs →        7.76 μs  (+14.62%) |      21   →      19     (-9.52%) |      142.20 μs →      147.47 μs   (+3.71%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       33.61 ms →       24.05 ms  (-28.44%) |      21   →      19     (-9.52%) |      705.80 ms →      456.98 ms  (-35.25%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       10.50 μs →       10.40 μs   (-0.94%) |      21   →      19     (-9.52%) |      220.43 μs →      197.56 μs  (-10.37%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        5.39 ms →        4.27 ms  (-20.75%) |      21   →      19     (-9.52%) |      113.14 ms →       81.12 ms  (-28.30%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       27.18 ms →       18.75 ms  (-31.03%) |      21   →      19     (-9.52%) |      570.79 ms →      356.18 ms  (-37.60%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      538.24 ns →      807.89 ns  (+50.10%) |      21   →      19     (-9.52%) |       11.30 μs →       15.35 μs  (+35.80%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      112.23 ms →      121.48 ms   (+8.24%) |      21   →      19     (-9.52%) |        2.36 s  →        2.31 s    (-2.07%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.88 ms →        2.27 ms  (+21.09%) |      21   →      19     (-9.52%) |       39.40 ms →       43.16 ms   (+9.56%) | 
- │ │ │ │ └ sirius::Density::augment                                    |      229.25 ms →      255.04 ms  (+11.25%) |      21   →      19     (-9.52%) |        4.81 s  →        4.85 s    (+0.66%) | 
- │ │ │ │   └ sirius::Density::generate_rho_aug                         |      229.03 ms →      254.84 ms  (+11.27%) |      21   →      19     (-9.52%) |        4.81 s  →        4.84 s    (+0.67%) | 
+ │ │ │ ├ sirius::Field4D::symmetrize                                   |      127.54 ms →      103.69 ms  (-18.70%) |      21   →      19     (-9.52%) |        2.68 s  →        1.97 s   (-26.44%) | 
+ │ │ │ │ └ sirius::symmetrize_function|fpw                             |      127.54 ms →      103.69 ms  (-18.70%) |      21   →      19     (-9.52%) |        2.68 s  →        1.97 s   (-26.44%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       44.58 ms →       21.38 ms  (-52.04%) |      21   →      19     (-9.52%) |      936.24 ms →      406.28 ms  (-56.61%) | 
+ │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       69.69 ms →       68.93 ms   (-1.09%) |      21   →      19     (-9.52%) |        1.46 s  →        1.31 s   (-10.51%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.61 ms →       12.71 ms   (+0.82%) |      21   →      19     (-9.52%) |      264.82 ms →      241.57 ms   (-8.78%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.64 ms →       23.70 ms   (+0.25%) |      21   →      19     (-9.52%) |      496.53 ms →      450.37 ms   (-9.30%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        4.21 ms →        4.68 ms  (+11.18%) |      21   →      19     (-9.52%) |       88.35 ms →       88.88 ms   (+0.59%) | 
  │ │ ├ sirius::Density::mix                                            |       79.90 ms →       81.32 ms   (+1.78%) |      21   →      19     (-9.52%) |        1.68 s  →        1.55 s    (-7.92%) | 
+ │ │ │ ├ sirius::Density::mixer_input                                  |        1.08 ms →      954.78 μs  (-11.56%) |      21   →      19     (-9.52%) |       22.67 ms →       18.14 ms  (-19.98%) | 
! │ │ │ ├ sirius::Periodic_function|inner                               |        4.59 ms →        4.84 ms   (+5.42%) |     259   →     229    (-11.58%) |        1.19 s  →        1.11 s    (-6.79%) | 
! │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.55 ms →        4.79 ms   (+5.39%) |     259   →     229    (-11.58%) |        1.18 s  →        1.10 s    (-6.82%) | 
! │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.55 ms →        4.79 ms   (+5.39%) |     259   →     229    (-11.58%) |        1.18 s  →        1.10 s    (-6.82%) | 
  │ │ │ └ sirius::Density::mixer_output                                 |        5.58 ms →        5.67 ms   (+1.70%) |      21   →      19     (-9.52%) |      117.09 ms →      107.74 ms   (-7.99%) | 
  │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        4.66 ms →        4.70 ms   (+0.93%) |      21   →      19     (-9.52%) |       97.85 ms →       89.35 ms   (-8.69%) | 
+ │ │ ├ sirius::Potential::generate                                     |      365.32 ms →      362.07 ms   (-0.89%) |      21   →      19     (-9.52%) |        7.67 s  →        6.88 s   (-10.33%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |       44.89 ms →       41.79 ms   (-6.91%) |      21   →      19     (-9.52%) |      942.69 ms →      794.00 ms  (-15.77%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.87 ms →       11.51 ms (+300.41%) |      21   →      19     (-9.52%) |       60.35 ms →      218.63 ms (+262.28%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner                             |        5.45 ms →        4.94 ms   (-9.36%) |      21   →      19     (-9.52%) |      114.43 ms →       93.84 ms  (-18.00%) | 
+ │ │ │ │   └ sirius::Periodic_function|inner_local                     |        5.16 ms →        4.63 ms  (-10.22%) |      21   →      19     (-9.52%) |      108.27 ms →       87.95 ms  (-18.77%) | 
+ │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        5.15 ms →        4.63 ms  (-10.23%) |      21   →      19     (-9.52%) |      108.25 ms →       87.92 ms  (-18.78%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      767.71 μs →      810.24 μs   (+5.54%) |      42   →      38     (-9.52%) |       32.24 ms →       30.79 ms   (-4.51%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       44.68 ms →       44.99 ms   (+0.71%) |      21   →      19     (-9.52%) |      938.19 ms →      854.89 ms   (-8.88%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       43.49 ms →       43.81 ms   (+0.73%) |      21   →      19     (-9.52%) |      913.34 ms →      832.36 ms   (-8.87%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |      685.07 μs →      682.48 μs   (-0.38%) |      42   →      38     (-9.52%) |       28.77 ms →       25.93 ms   (-9.87%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.09 ms →        4.58 ms  (+12.01%) |      21   →      19     (-9.52%) |       85.85 ms →       87.01 ms   (+1.35%) | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.84 ms →        3.65 ms   (-5.20%) |      21   →      19     (-9.52%) |       80.74 ms →       69.26 ms  (-14.22%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.97 ms →      268.59 ms   (-0.14%) |      21   →      19     (-9.52%) |        5.65 s  →        5.10 s    (-9.65%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      201.90 ns →      261.89 ns  (+29.71%) |      21   →      19     (-9.52%) |        4.24 μs →        4.98 μs  (+17.36%) | 
+ │ │ ├ sirius::Field4D::symmetrize                                     |       96.16 ms →       95.30 ms   (-0.89%) |      21   →      19     (-9.52%) |        2.02 s  →        1.81 s   (-10.33%) | 
+ │ │ │ └ sirius::symmetrize_function|fpw                               |       96.15 ms →       95.30 ms   (-0.89%) |      21   →      19     (-9.52%) |        2.02 s  →        1.81 s   (-10.33%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.25 ms →       13.27 ms   (+0.21%) |      21   →      19     (-9.52%) |      278.15 ms →      252.19 ms   (-9.33%) | 
+ │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       69.71 ms →       68.79 ms   (-1.32%) |      21   →      19     (-9.52%) |        1.46 s  →        1.31 s   (-10.72%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.57 ms →       12.61 ms   (+0.27%) |      21   →      19     (-9.52%) |      263.99 ms →      239.50 ms   (-9.28%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.93 ms →        4.11 ms   (+4.61%) |      21   →      19     (-9.52%) |       82.47 ms →       78.05 ms   (-5.36%) | 
+ │ │ ├ sirius::Periodic_function|inner                                 |        4.88 ms →        4.83 ms   (-0.94%) |     147   →     133     (-9.52%) |      717.37 ms →      642.93 ms  (-10.38%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.76 ms →        4.75 ms   (-0.19%) |     147   →     133     (-9.52%) |      700.09 ms →      632.19 ms   (-9.70%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.76 ms →        4.75 ms   (-0.20%) |     147   →     133     (-9.52%) |      699.99 ms →      632.08 ms   (-9.70%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.56 ms →        4.73 ms   (+3.61%) |      63   →      57     (-9.52%) |      287.50 ms →      269.51 ms   (-6.26%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.56 ms →        4.53 ms   (-0.48%) |      63   →      57     (-9.52%) |      287.00 ms →      258.42 ms   (-9.96%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.55 ms →        4.54 ms   (-0.27%) |      21   →      19     (-9.52%) |       95.56 ms →       86.23 ms   (-9.77%) | 
  │ │ └ sirius::Density::get_magnetisation                              |       74.32 μs →       76.30 μs   (+2.67%) |      21   →      19     (-9.52%) |        1.56 ms →        1.45 ms   (-7.11%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |       69.22 μs →       71.42 μs   (+3.17%) |      21   →      19     (-9.52%) |        1.45 ms →        1.36 ms   (-6.66%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.30 ms →        5.27 ms   (-0.54%) |       2   →       2              |       10.60 ms →       10.54 ms   (-0.54%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.83 ms →        4.84 ms   (+0.07%) |       6   →       6              |       28.99 ms →       29.01 ms   (+0.07%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.73 ms →        4.83 ms   (+2.05%) |       6   →       6              |       28.39 ms →       28.97 ms   (+2.05%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.73 ms →        4.83 ms   (+2.05%) |       6   →       6              |       28.39 ms →       28.97 ms   (+2.05%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.74 ms →        4.63 ms   (-2.37%) |       3   →       3              |       14.22 ms →       13.88 ms   (-2.37%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.73 ms →        4.62 ms   (-2.35%) |       3   →       3              |       14.20 ms →       13.87 ms   (-2.35%) | 
  ├ sirius::Periodic_function|inner                                     |        4.75 ms →        4.83 ms   (+1.69%) |       2   →       2              |        9.50 ms →        9.66 ms   (+1.69%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.75 ms →        4.83 ms   (+1.68%) |       2   →       2              |        9.49 ms →        9.65 ms   (+1.68%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.75 ms →        4.83 ms   (+1.68%) |       2   →       2              |        9.49 ms →        9.65 ms   (+1.68%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.54 ms →        4.63 ms   (+1.91%) |       1   →       1              |        4.54 ms →        4.63 ms   (+1.91%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.52 ms →        4.62 ms   (+2.23%) |       1   →       1              |        4.52 ms →        4.62 ms   (+2.23%) | 
  └ sirius::finalize                                                    |      752.72 ms →      756.29 ms   (+0.48%) |       1   →       1              |      752.72 ms →      756.29 ms   (+0.48%) | 
  ====================================================================================================================================================================================================
```
