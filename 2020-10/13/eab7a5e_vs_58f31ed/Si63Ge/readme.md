# Benchmark 58f31ed08f2b4e9e6d289f9ed116027f00413e03 vs eab7a5e09a790e571ffec2b67e8d778bf317b1b5
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
- sirius                                                                |       71.87 s  →       81.19 s   (+12.97%) |       1   →       1              |       71.87 s  →       81.19 s   (+12.97%) | 
  ├ sirius::initialize                                                  |        2.96 s  →        2.92 s    (-1.43%) |       1   →       1              |        2.96 s  →        2.92 s    (-1.43%) | 
+ ├ sirius::Simulation_context::initialize                              |        3.97 s  →        3.57 s   (-10.11%) |       1   →       1              |        3.97 s  →        3.57 s   (-10.11%) | 
  │ ├ sirius::Simulation_context::init_comm                             |       28.46 ms →       26.37 ms   (-7.34%) |       1   →       1              |       28.46 ms →       26.37 ms   (-7.34%) | 
+ │ ├ sirius::Unit_cell::initialize                                     |      169.90 ms →      117.54 ms  (-30.82%) |       1   →       1              |      169.90 ms →      117.54 ms  (-30.82%) | 
+ │ │ ├ sirius::Atom_type::init                                         |       72.76 ms →       50.26 ms  (-30.92%) |       2   →       2              |      145.51 ms →      100.53 ms  (-30.92%) | 
+ │ │ └ sirius::Unit_cell::update                                       |       24.29 ms →       16.92 ms  (-30.32%) |       1   →       1              |       24.29 ms →       16.92 ms  (-30.32%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.58 ms →        3.57 ms   (-0.40%) |       1   →       1              |        3.58 ms →        3.57 ms   (-0.40%) | 
+ │ │   └ sirius::Unit_cell::get_symmetry                               |       20.62 ms →       13.26 ms  (-35.68%) |       1   →       1              |       20.62 ms →       13.26 ms  (-35.68%) | 
+ │ │     └ sirius::Unit_cell_symmetry                                  |       20.55 ms →       13.20 ms  (-35.76%) |       1   →       1              |       20.55 ms →       13.20 ms  (-35.76%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.75 ms →        2.74 ms   (-0.19%) |       1   →       1              |        2.75 ms →        2.74 ms   (-0.19%) | 
+ │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        3.85 ms →      498.46 μs  (-87.04%) |       1   →       1              |        3.85 ms →      498.46 μs  (-87.04%) | 
+ │ │       └ sirius::Unit_cell_symmetry|mag                            |       20.93 μs →       15.56 μs  (-25.66%) |       1   →       1              |       20.93 μs →       15.56 μs  (-25.66%) | 
+ │ └ sirius::Simulation_context::update                                |        3.71 s  →        3.23 s   (-13.13%) |       1   →       1              |        3.71 s  →        3.23 s   (-13.13%) | 
  │   ├ sirius::Unit_cell::update                                       |        7.17 ms →        7.05 ms   (-1.67%) |       1   →       1              |        7.17 ms →        7.05 ms   (-1.67%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.70 ms →        3.65 ms   (-1.38%) |       1   →       1              |        3.70 ms →        3.65 ms   (-1.38%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.43 ms →        3.35 ms   (-2.14%) |       1   →       1              |        3.43 ms →        3.35 ms   (-2.14%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.36 ms →        3.28 ms   (-2.24%) |       1   →       1              |        3.36 ms →        3.28 ms   (-2.24%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.80 ms →        2.73 ms   (-2.46%) |       1   →       1              |        2.80 ms →        2.73 ms   (-2.46%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      513.60 μs →      506.17 μs   (-1.45%) |       1   →       1              |      513.60 μs →      506.17 μs   (-1.45%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       13.81 μs →       14.90 μs   (+7.90%) |       1   →       1              |       13.81 μs →       14.90 μs   (+7.90%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      210.82 ms →      212.39 ms   (+0.74%) |       2   →       2              |      421.65 ms →      424.78 ms   (+0.74%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.14 ms →       15.20 ms   (+0.40%) |       2   →       2              |       30.29 ms →       30.41 ms   (+0.40%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.25 ms →       13.40 ms   (+1.18%) |       1   →       1              |       13.25 ms →       13.40 ms   (+1.18%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.48 ms →       56.37 ms   (-0.20%) |       2   →       2              |      112.97 ms →      112.75 ms   (-0.20%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.11 ms →       45.09 ms   (-0.05%) |       2   →       2              |       90.22 ms →       90.18 ms   (-0.05%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.19 ms →       60.14 ms   (-0.09%) |       4   →       4              |      240.78 ms →      240.56 ms   (-0.09%) | 
  │   ├ sddk::Gvec::init                                                |       92.76 ms →       93.63 ms   (+0.94%) |       2   →       2              |      185.53 ms →      187.27 ms   (+0.94%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       69.43 ms →       70.14 ms   (+1.02%) |       2   →       2              |      138.86 ms →      140.27 ms   (+1.02%) | 
- │   ├ sddk::Gvec_shells                                               |       92.25 ms →      105.65 ms  (+14.52%) |       1   →       1              |       92.25 ms →      105.65 ms  (+14.52%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.95 ms →        1.96 ms   (+0.87%) |       1   →       1              |        1.95 ms →        1.96 ms   (+0.87%) | 
+ │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      705.12 ms →      468.38 ms  (-33.57%) |       2   →       2              |        1.41 s  →      936.76 ms  (-33.57%) | 
- ├ sirius::K_point_set::create_k_mesh                                  |       28.46 ms →      157.20 ms (+452.40%) |       1   →       1              |       28.46 ms →      157.20 ms (+452.40%) | 
  │ ├ sirius::K_point::K_point                                          |        2.54 μs →        2.49 μs   (-2.06%) |       4   →       4              |       10.18 μs →        9.96 μs   (-2.06%) | 
- │ └ sirius::K_point_set::initialize                                   |       28.38 ms →      157.12 ms (+453.67%) |       1   →       1              |       28.38 ms →      157.12 ms (+453.67%) | 
  │   └ sirius::K_point::initialize                                     |       28.12 ms →       28.16 ms   (+0.15%) |       1   →       1              |       28.12 ms →       28.16 ms   (+0.15%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       11.09 ms →       11.05 ms   (-0.40%) |       1   →       1              |       11.09 ms →       11.05 ms   (-0.40%) | 
  │     │ └ sddk::Gvec::init                                            |        5.01 ms →        4.97 ms   (-0.68%) |       1   →       1              |        5.01 ms →        4.97 ms   (-0.68%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |       10.74 μs →       11.26 μs   (+4.88%) |       1   →       1              |       10.74 μs →       11.26 μs   (+4.88%) | 
  │     └ sirius::K_point::update                                       |       14.15 ms →       14.28 ms   (+0.88%) |       1   →       1              |       14.15 ms →       14.28 ms   (+0.88%) | 
  │       └ sirius::Beta_projectors                                     |       10.20 ms →       10.36 ms   (+1.54%) |       1   →       1              |       10.20 ms →       10.36 ms   (+1.54%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.32 ms →        8.35 ms   (+0.44%) |       1   →       1              |        8.32 ms →        8.35 ms   (+0.44%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.56 ms →        2.61 ms   (+2.00%) |       2   →       2              |        5.12 ms →        5.22 ms   (+2.00%) | 
  ├ sirius::Potential                                                   |       54.71 ms →       51.68 ms   (-5.54%) |       1   →       1              |       54.71 ms →       51.68 ms   (-5.54%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.91 ms →        2.94 ms   (+1.00%) |       6   →       6              |       17.47 ms →       17.64 ms   (+1.00%) | 
  │ └ sirius::Potential::update                                         |       36.67 ms →       33.44 ms   (-8.82%) |       1   →       1              |       36.67 ms →       33.44 ms   (-8.82%) | 
  │   └ sirius::Potential::generate_local_potential                     |       36.25 ms →       33.01 ms   (-8.94%) |       1   →       1              |       36.25 ms →       33.01 ms   (-8.94%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       31.86 ms →       26.34 ms  (-17.32%) |       1   →       1              |       31.86 ms →       26.34 ms  (-17.32%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        3.82 ms →        6.15 ms  (+60.87%) |       1   →       1              |        3.82 ms →        6.15 ms  (+60.87%) | 
  ├ sirius::Density                                                     |       41.77 ms →       41.71 ms   (-0.16%) |       1   →       1              |       41.77 ms →       41.71 ms   (-0.16%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.84 ms →        2.82 ms   (-0.71%) |       2   →       2              |        5.68 ms →        5.64 ms   (-0.71%) | 
  │ └ sirius::Density::update                                           |       35.95 ms →       35.92 ms   (-0.08%) |       1   →       1              |       35.95 ms →       35.92 ms   (-0.08%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       35.66 ms →       35.70 ms   (+0.10%) |       1   →       1              |       35.66 ms →       35.70 ms   (+0.10%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |       76.82 μs →       76.48 μs   (-0.44%) |       1   →       1              |       76.82 μs →       76.48 μs   (-0.44%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       32.31 ms →       26.38 ms  (-18.35%) |       1   →       1              |       32.31 ms →       26.38 ms  (-18.35%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        2.92 ms →        8.95 ms (+206.48%) |       1   →       1              |        2.92 ms →        8.95 ms (+206.48%) | 
  ├ sirius::Density::initial_density                                    |       64.51 ms →       61.42 ms   (-4.79%) |       1   →       1              |       64.51 ms →       61.42 ms   (-4.79%) | 
+ │ ├ sirius::Simulation_context::make_periodic_function                |       36.80 ms →       26.72 ms  (-27.40%) |       1   →       1              |       36.80 ms →       26.72 ms  (-27.40%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.27 ms →        7.84 ms  (+83.57%) |       2   →       2              |        8.54 ms →       15.68 ms  (+83.57%) | 
  │ └ sirius::Periodic_function::integrate                              |        5.42 ms →        5.35 ms   (-1.43%) |       1   →       1              |        5.42 ms →        5.35 ms   (-1.43%) | 
  ├ sirius::Potential::generate                                         |      371.80 ms →      368.93 ms   (-0.77%) |       1   →       1              |      371.80 ms →      368.93 ms   (-0.77%) | 
  │ ├ sirius::Potential::poisson                                        |       44.73 ms →       42.12 ms   (-5.83%) |       1   →       1              |       44.73 ms →       42.12 ms   (-5.83%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.87 ms →       10.82 ms (+276.62%) |       1   →       1              |        2.87 ms →       10.82 ms (+276.62%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        5.32 ms →        5.72 ms   (+7.61%) |       1   →       1              |        5.32 ms →        5.72 ms   (+7.61%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.64 ms →        4.64 ms   (-0.01%) |       1   →       1              |        4.64 ms →        4.64 ms   (-0.01%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.64 ms →        4.63 ms   (-0.08%) |       1   →       1              |        4.64 ms →        4.63 ms   (-0.08%) | 
  │ ├ sirius::Periodic_function::add                                    |      801.79 μs →      772.19 μs   (-3.69%) |       2   →       2              |        1.60 ms →        1.54 ms   (-3.69%) | 
  │ ├ sirius::Potential::xc                                             |       50.71 ms →       51.70 ms   (+1.95%) |       1   →       1              |       50.71 ms →       51.70 ms   (+1.95%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       49.53 ms →       50.52 ms   (+2.01%) |       1   →       1              |       49.53 ms →       50.52 ms   (+2.01%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.54 ms →        2.56 ms   (+0.73%) |       2   →       2              |        5.08 ms →        5.12 ms   (+0.73%) | 
- │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.22 ms →        4.99 ms  (+18.05%) |       1   →       1              |        4.22 ms →        4.99 ms  (+18.05%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.91 ms →        3.60 ms   (-8.01%) |       1   →       1              |        3.91 ms →        3.60 ms   (-8.01%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      269.46 ms →      268.58 ms   (-0.33%) |       1   →       1              |      269.46 ms →      268.58 ms   (-0.33%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      284.00 ns →      290.00 ns   (+2.11%) |       1   →       1              |      284.00 ns →      290.00 ns   (+2.11%) | 
  ├ sirius::Hamiltonian0                                                |        8.44 ms →        8.43 ms   (-0.10%) |       1   →       1              |        8.44 ms →        8.43 ms   (-0.10%) | 
  │ ├ sirius::Local_operator                                            |        7.36 ms →        7.37 ms   (+0.06%) |       1   →       1              |        7.36 ms →        7.37 ms   (+0.06%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.75 ms →        2.76 ms   (+0.06%) |       1   →       1              |        2.75 ms →        2.76 ms   (+0.06%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        3.60 ms →        3.58 ms   (-0.64%) |       1   →       1              |        3.60 ms →        3.58 ms   (-0.64%) | 
  │ ├ sirius::Non_local_operator                                        |      404.39 μs →      397.14 μs   (-1.79%) |       2   →       2              |      808.77 μs →      794.27 μs   (-1.79%) | 
  │ ├ sirius::D_operator::initialize                                    |      109.88 μs →      109.64 μs   (-0.22%) |       1   →       1              |      109.88 μs →      109.64 μs   (-0.22%) | 
  │ └ sirius::Q_operator::initialize                                    |       95.26 μs →       94.02 μs   (-1.30%) |       1   →       1              |       95.26 μs →       94.02 μs   (-1.30%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.32 s  →        1.28 s    (-2.99%) |       1   →       1              |        1.32 s  →        1.28 s    (-2.99%) | 
+ │ ├ sirius::Hamiltonian_k                                             |       72.69 ms →       48.29 ms  (-33.57%) |       1   →       1              |       72.69 ms →       48.29 ms  (-33.57%) | 
+ │ │ ├ sirius::Local_operator::prepare_k                               |      269.27 μs →      222.86 μs  (-17.24%) |       1   →       1              |      269.27 μs →      222.86 μs  (-17.24%) | 
+ │ │ └ sirius::Beta_projectors_base::prepare                           |       72.42 ms →       48.06 ms  (-33.64%) |       1   →       1              |       72.42 ms →       48.06 ms  (-33.64%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.25 s  →        1.23 s    (-1.21%) |       1   →       1              |        1.25 s  →        1.23 s    (-1.21%) | 
+ │ │ ├ sddk::matrix_storage::matrix_storage                            |      104.53 ms →       77.45 ms  (-25.91%) |       4   →       4              |      418.13 ms →      309.81 ms  (-25.91%) | 
+ │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       49.77 ms →       42.67 ms  (-14.27%) |       1   →       1              |       49.77 ms →       42.67 ms  (-14.27%) | 
- │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        7.55 ms →        8.86 ms  (+17.45%) |       1   →       1              |        7.55 ms →        8.86 ms  (+17.45%) | 
+ │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      448.32 ms →      334.98 ms  (-25.28%) |       1   →       1              |      448.32 ms →      334.98 ms  (-25.28%) | 
+ │ │ │ ├ sirius::Local_operator::apply_h                               |      376.35 ms →      246.73 ms  (-34.44%) |       1   →       1              |      376.35 ms →      246.73 ms  (-34.44%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.72 μs →        3.72 μs   (+0.03%) |       1   →       1              |        3.72 μs →        3.72 μs   (+0.03%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.80 μs →        2.86 μs   (+2.04%) |       1   →       1              |        2.80 μs →        2.86 μs   (+2.04%) | 
- │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      563.00 ns →      730.00 ns  (+29.66%) |       1   →       1              |      563.00 ns →      730.00 ns  (+29.66%) | 
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                        |        1.06 μs →      754.00 ns  (-28.87%) |       1   →       1              |        1.06 μs →      754.00 ns  (-28.87%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.06 ms →        3.21 ms   (+4.89%) |       1   →       1              |        3.06 ms →        3.21 ms   (+4.89%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::inner                           |       24.52 ms →       21.28 ms  (-13.22%) |       1   →       1              |       24.52 ms →       21.28 ms  (-13.22%) | 
- │ │ │ └ sirius::Non_local_operator::apply                             |       22.17 ms →       31.85 ms  (+43.69%) |       2   →       2              |       44.33 ms →       63.70 ms  (+43.69%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       16.09 ms →       14.79 ms   (-8.07%) |       2   →       2              |       32.19 ms →       29.59 ms   (-8.07%) | 
  │ │ │ └ sddk::wf_inner                                                |       15.88 ms →       14.58 ms   (-8.14%) |       2   →       2              |       31.75 ms →       29.17 ms   (-8.14%) | 
  │ │ │   ├ sddk::wf_inner|scale                                        |       19.50 ns →       20.50 ns   (+5.13%) |       2   →       2              |       39.00 ns →       41.00 ns   (+5.13%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       15.73 ms →       14.45 ms   (-8.16%) |       2   →       2              |       31.46 ms →       28.90 ms   (-8.16%) | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |       23.00 ns →       23.00 ns            |       2   →       2              |       46.00 ns →       46.00 ns            | 
- │ │ ├ Eigensolver_cuda|zhegvdx                                        |      116.29 ms →      239.36 ms (+105.84%) |       1   →       1              |      116.29 ms →      239.36 ms (+105.84%) | 
+ │ │ └ sddk::wf_trans                                                  |        4.96 ms →        2.61 ms  (-47.39%) |       1   →       1              |        4.96 ms →        2.61 ms  (-47.39%) | 
+ │ │   └ sddk::wf_trans|pw                                             |        4.96 ms →        2.61 ms  (-47.44%) |       1   →       1              |        4.96 ms →        2.61 ms  (-47.44%) | 
- │ └ sirius::Beta_projectors_base::dismiss                             |      595.00 ns →      762.00 ns  (+28.07%) |       1   →       1              |      595.00 ns →      762.00 ns  (+28.07%) | 
- ├ sirius::DFT_ground_state::scf_loop                                  |       61.94 s  →       71.62 s   (+15.62%) |       1   →       1              |       61.94 s  →       71.62 s   (+15.62%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.45 ms →        2.46 ms   (+0.51%) |      19   →      19              |       46.58 ms →       46.82 ms   (+0.51%) | 
- │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.25 s  →        3.10 s    (-4.45%) |      19   →      23    (+21.05%) |       61.71 s  →       71.38 s   (+15.67%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        4.74 ms →        5.03 ms   (+6.11%) |      19   →      23    (+21.05%) |       90.14 ms →      115.78 ms  (+28.45%) | 
- │ │ │ ├ sirius::Local_operator                                        |        4.03 ms →        4.35 ms   (+8.01%) |      19   →      23    (+21.05%) |       76.50 ms →      100.02 ms  (+30.75%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function                            |      546.71 μs →      565.84 μs   (+3.50%) |      19   →      23    (+21.05%) |       10.39 ms →       13.01 ms  (+25.29%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.38 ms →        2.65 ms  (+11.46%) |      19   →      23    (+21.05%) |       45.25 ms →       61.05 ms  (+34.92%) | 
- │ │ │ ├ sirius::Non_local_operator                                    |      207.73 μs →      201.87 μs   (-2.82%) |      38   →      46    (+21.05%) |        7.89 ms →        9.29 ms  (+17.64%) | 
+ │ │ │ ├ sirius::D_operator::initialize                                |      129.47 μs →      115.36 μs  (-10.90%) |      19   →      23    (+21.05%) |        2.46 ms →        2.65 ms   (+7.86%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       91.79 μs →       89.16 μs   (-2.87%) |      19   →      23    (+21.05%) |        1.74 ms →        2.05 ms  (+17.58%) | 
- │ │ ├ sirius::Band::solve                                             |        2.03 s  →        1.87 s    (-7.64%) |      19   →      23    (+21.05%) |       38.48 s  →       43.02 s   (+11.80%) | 
+ │ │ │ ├ sirius::Hamiltonian_k                                         |      242.52 μs →      205.32 μs  (-15.34%) |      19   →      23    (+21.05%) |        4.61 ms →        4.72 ms   (+2.49%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      233.11 μs →      194.67 μs  (-16.49%) |      19   →      23    (+21.05%) |        4.43 ms →        4.48 ms   (+1.09%) | 
- │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        6.93 μs →        7.68 μs  (+10.83%) |      19   →      23    (+21.05%) |      131.64 μs →      176.62 μs  (+34.17%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.96 s  →        1.75 s   (-10.72%) |      19   →      23    (+21.05%) |       37.20 s  →       40.21 s    (+8.07%) | 
- │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       71.59 ms →       70.53 ms   (-1.48%) |      19   →      23    (+21.05%) |        1.36 s  →        1.62 s   (+19.26%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        8.02 ms →        6.96 ms  (-13.23%) |     114   →     138    (+21.05%) |      914.40 ms →      960.41 ms   (+5.03%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       17.94 ms →       15.36 ms  (-14.40%) |      19   →      23    (+21.05%) |      340.87 ms →      353.21 ms   (+3.62%) | 
- │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      456.08 μs →      482.03 μs   (+5.69%) |      19   →      23    (+21.05%) |        8.67 ms →       11.09 ms  (+27.94%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        8.16 ms →        7.02 ms  (-13.98%) |      38   →      46    (+21.05%) |      310.03 ms →      322.82 ms   (+4.13%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.86 s  →        1.65 s   (-11.17%) |      19   →      23    (+21.05%) |       35.34 s  →       37.99 s    (+7.53%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       46.84 ms →       68.19 ms  (+45.57%) |     356   →     297    (-16.57%) |       16.68 s  →       20.25 s   (+21.44%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       28.41 ms →       45.06 ms  (+58.61%) |     356   →     297    (-16.57%) |       10.11 s  →       13.38 s   (+32.32%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.12 μs →        2.02 μs   (-4.34%) |     356   →     297    (-16.57%) |      753.38 μs →      601.27 μs  (-20.19%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.81 μs →        1.72 μs   (-4.78%) |     356   →     297    (-16.57%) |      644.47 μs →      511.96 μs  (-20.56%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      436.03 ns →      367.49 ns  (-15.72%) |     356   →     297    (-16.57%) |      155.23 μs →      109.14 μs  (-29.69%) | 
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      613.62 ns →      509.02 ns  (-17.05%) |     356   →     297    (-16.57%) |      218.45 μs →      151.18 μs  (-30.79%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.78 ms →        3.10 ms  (+11.46%) |     356   →     297    (-16.57%) |      990.97 ms →      921.49 ms   (-7.01%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.23 ms →        3.69 ms  (+14.49%) |     356   →     297    (-16.57%) |        1.15 s  →        1.10 s    (-4.48%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        6.20 ms →        8.16 ms  (+31.52%) |     712   →     594    (-16.57%) |        4.42 s  →        4.85 s    (+9.72%) | 
! │ │ │ │   ├ sddk::orthogonalize                                       |        5.84 ms →        6.36 ms   (+8.75%) |     356   →     297    (-16.57%) |        2.08 s  →        1.89 s    (-9.27%) | 
- │ │ │ │   │ ├ sddk::wf_inner                                          |      889.15 μs →        1.09 ms  (+22.98%) |     693   →     571    (-17.60%) |      616.18 ms →      624.37 ms   (+1.33%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       58.84 ns →       39.97 ns  (-32.07%) |     693   →     571    (-17.60%) |       40.77 μs →       22.82 μs  (-44.03%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |      728.86 μs →      929.00 μs  (+27.46%) |     693   →     571    (-17.60%) |      505.10 ms →      530.46 ms   (+5.02%) | 
+ │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       47.86 ns →       35.40 ns  (-26.02%) |     693   →     571    (-17.60%) |       33.16 μs →       20.22 μs  (-39.05%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      132.57 μs →      169.23 μs  (+27.65%) |     356   →     297    (-16.57%) |       47.20 ms →       50.26 ms   (+6.49%) | 
+ │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        1.91 ms →        1.93 ms   (+1.29%) |     356   →     297    (-16.57%) |      678.79 ms →      573.60 ms  (-15.50%) | 
+ │ │ │ │   │ └ sddk::wf_trans                                          |        2.19 ms →        2.33 ms   (+6.49%) |     337   →     274    (-18.69%) |      736.95 ms →      638.10 ms  (-13.41%) | 
+ │ │ │ │   │   └ sddk::wf_trans|pw                                     |      728.13 μs →      775.51 μs   (+6.51%) |    1.01 K →     822    (-18.69%) |      736.14 ms →      637.47 ms  (-13.40%) | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.46 ms →        1.44 ms   (-0.91%) |     356   →     297    (-16.57%) |      518.64 ms →      428.73 ms  (-17.34%) | 
+ │ │ │ │   │ └ sddk::wf_inner                                          |        1.39 ms →        1.34 ms   (-3.00%) |     356   →     297    (-16.57%) |      493.13 ms →      399.04 ms  (-19.08%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       43.92 ns →       34.31 ns  (-21.89%) |     356   →     297    (-16.57%) |       15.63 μs →       10.19 μs  (-34.83%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        1.22 ms →        1.18 ms   (-3.99%) |     356   →     297    (-16.57%) |      435.98 ms →      349.21 ms  (-19.90%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       38.57 ns →       64.21 ns  (+66.45%) |     356   →     297    (-16.57%) |       13.73 μs →       19.07 μs  (+38.87%) | 
- │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       42.06 ms →       47.47 ms  (+12.87%) |     356   →     297    (-16.57%) |       14.97 s  →       14.10 s    (-5.84%) | 
- │ │ │ │   ├ sirius::residuals                                         |        2.22 ms →        3.17 ms  (+42.57%) |     340   →     288    (-15.29%) |      755.58 ms →      912.46 ms  (+20.76%) | 
- │ │ │ │   │ ├ sddk::wf_trans                                          |        1.30 ms →        1.84 ms  (+42.30%) |     337   →     277    (-17.80%) |      436.86 ms →      510.98 ms  (+16.97%) | 
- │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      646.73 μs →      920.92 μs  (+42.40%) |     674   →     554    (-17.80%) |      435.90 ms →      510.19 ms  (+17.04%) | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |      835.72 μs →        1.32 ms  (+57.48%) |     337   →     277    (-17.80%) |      281.64 ms →      364.56 ms  (+29.44%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        5.98 ms →        7.14 ms  (+19.40%) |      54   →      57     (+5.56%) |      323.12 ms →      407.24 ms  (+26.03%) | 
- │ │ │ │     └ sddk::wf_trans                                          |        3.58 ms →        4.43 ms  (+23.68%) |      89   →      91     (+2.25%) |      318.57 ms →      402.87 ms  (+26.46%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |        2.57 ms →        3.22 ms  (+25.47%) |     124   →     125     (+0.81%) |      318.39 ms →      402.69 ms  (+26.48%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      409.53 ns →      375.26 ns   (-8.37%) |      19   →      23    (+21.05%) |        7.78 μs →        8.63 μs  (+10.92%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       19.49 μs →       20.26 μs   (+3.97%) |      19   →      23    (+21.05%) |      370.32 μs →      466.06 μs  (+25.85%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.51 ms →        1.49 ms   (-0.95%) |      19   →      23    (+21.05%) |       28.66 ms →       34.36 ms  (+19.91%) | 
- │ │ ├ sirius::Density::generate                                       |      563.50 ms →      568.05 ms   (+0.81%) |      19   →      23    (+21.05%) |       10.71 s  →       13.07 s   (+22.03%) | 
- │ │ │ ├ sirius::Density::generate_valence                             |      422.58 ms →      384.19 ms   (-9.08%) |      19   →      23    (+21.05%) |        8.03 s  →        8.84 s   (+10.06%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.24 μs →        8.26 μs   (+0.24%) |      19   →      23    (+21.05%) |      156.56 μs →      189.99 μs  (+21.35%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.64 μs →        7.71 μs   (+1.00%) |      19   →      23    (+21.05%) |      145.13 μs →      177.44 μs  (+22.27%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       21.92 ms →       41.55 ms  (+89.57%) |      19   →      23    (+21.05%) |      416.47 ms →      955.70 ms (+129.47%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.73 μs →        7.54 μs   (-2.46%) |      19   →      23    (+21.05%) |      146.84 μs →      173.38 μs  (+18.07%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        3.85 ms →       23.15 ms (+500.75%) |      19   →      23    (+21.05%) |       73.22 ms →      532.47 ms (+627.22%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       16.99 ms →       17.38 ms   (+2.30%) |      19   →      23    (+21.05%) |      322.73 ms →      399.67 ms  (+23.84%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      763.95 ns →      588.96 ns  (-22.91%) |      19   →      23    (+21.05%) |       14.52 μs →       13.55 μs   (-6.68%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      123.69 ms →       97.71 ms  (-21.00%) |      19   →      23    (+21.05%) |        2.35 s  →        2.25 s    (-4.37%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.28 ms →        2.13 ms   (-6.85%) |      19   →      23    (+21.05%) |       43.41 ms →       48.95 ms  (+12.75%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |      246.21 ms →      199.40 ms  (-19.01%) |      19   →      23    (+21.05%) |        4.68 s  →        4.59 s    (-1.96%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |      245.99 ms →      199.17 ms  (-19.03%) |      19   →      23    (+21.05%) |        4.67 s  →        4.58 s    (-1.99%) | 
- │ │ │ ├ sirius::Field4D::symmetrize                                   |      113.48 ms →      152.89 ms  (+34.72%) |      19   →      23    (+21.05%) |        2.16 s  →        3.52 s   (+63.08%) | 
- │ │ │ │ └ sirius::symmetrize_function|fpw                             |      113.48 ms →      152.89 ms  (+34.72%) |      19   →      23    (+21.05%) |        2.16 s  →        3.52 s   (+63.09%) | 
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       29.97 ms →       69.21 ms (+130.96%) |      19   →      23    (+21.05%) |      569.38 ms →        1.59 s  (+179.59%) | 
- │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       70.16 ms →       70.37 ms   (+0.31%) |      19   →      23    (+21.05%) |        1.33 s  →        1.62 s   (+21.42%) | 
- │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.70 ms →       12.65 ms   (-0.40%) |      19   →      23    (+21.05%) |      241.36 ms →      291.02 ms  (+20.57%) | 
- │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.69 ms →       23.60 ms   (-0.37%) |      19   →      23    (+21.05%) |      450.17 ms →      542.91 ms  (+20.60%) | 
- │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        3.74 ms →        7.36 ms  (+97.10%) |      19   →      23    (+21.05%) |       70.99 ms →      169.38 ms (+138.60%) | 
- │ │ ├ sirius::Density::mix                                            |      133.51 ms →      138.04 ms   (+3.39%) |      19   →      23    (+21.05%) |        2.54 s  →        3.17 s   (+25.15%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      716.08 μs →      861.13 μs  (+20.26%) |      19   →      23    (+21.05%) |       13.61 ms →       19.81 ms  (+45.57%) | 
- │ │ │ ├ sirius::Periodic_function|inner                               |        4.91 ms →        4.86 ms   (-1.03%) |     229   →     289    (+26.20%) |        1.12 s  →        1.40 s   (+24.90%) | 
- │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.82 ms →        4.82 ms   (+0.05%) |     229   →     289    (+26.20%) |        1.10 s  →        1.39 s   (+26.27%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.81 ms →        4.82 ms   (+0.05%) |     229   →     289    (+26.20%) |        1.10 s  →        1.39 s   (+26.27%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        5.44 ms →        5.95 ms   (+9.53%) |      19   →      23    (+21.05%) |      103.30 ms →      136.96 ms  (+32.59%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        4.73 ms →        5.23 ms  (+10.59%) |      19   →      23    (+21.05%) |       89.83 ms →      120.27 ms  (+33.88%) | 
- │ │ ├ sirius::Potential::generate                                     |      365.40 ms →      362.14 ms   (-0.89%) |      19   →      23    (+21.05%) |        6.94 s  →        8.33 s   (+19.97%) | 
- │ │ │ ├ sirius::Potential::poisson                                    |       44.88 ms →       41.88 ms   (-6.67%) |      19   →      23    (+21.05%) |      852.63 ms →      963.25 ms  (+12.97%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.94 ms →       10.69 ms (+263.35%) |      19   →      23    (+21.05%) |       55.87 ms →      245.76 ms (+339.84%) | 
- │ │ │ │ └ sirius::Periodic_function|inner                             |        5.30 ms →        5.71 ms   (+7.64%) |      19   →      23    (+21.05%) |      100.77 ms →      131.31 ms  (+30.30%) | 
- │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.63 ms →        4.64 ms   (+0.05%) |      19   →      23    (+21.05%) |       88.05 ms →      106.64 ms  (+21.12%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.63 ms →        4.64 ms   (+0.05%) |      19   →      23    (+21.05%) |       88.03 ms →      106.62 ms  (+21.12%) | 
- │ │ │ ├ sirius::Periodic_function::add                                |      837.60 μs →      787.11 μs   (-6.03%) |      38   →      46    (+21.05%) |       31.83 ms →       36.21 ms  (+13.75%) | 
- │ │ │ ├ sirius::Potential::xc                                         |       44.65 ms →       45.34 ms   (+1.55%) |      19   →      23    (+21.05%) |      848.31 ms →        1.04 s   (+22.92%) | 
- │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       43.48 ms →       44.16 ms   (+1.56%) |      19   →      23    (+21.05%) |      826.12 ms →        1.02 s   (+22.94%) | 
- │ │ │ │   ├ sirius::Smooth_periodic_function                          |      688.36 μs →      678.95 μs   (-1.37%) |      38   →      46    (+21.05%) |       26.16 ms →       31.23 ms  (+19.40%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.25 ms →        5.06 ms  (+19.08%) |      19   →      23    (+21.05%) |       80.81 ms →      116.49 ms  (+44.15%) | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.96 ms →        3.70 ms   (-6.54%) |      19   →      23    (+21.05%) |       75.25 ms →       85.13 ms  (+13.14%) | 
- │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.84 ms →      268.23 ms   (-0.23%) |      19   →      23    (+21.05%) |        5.11 s  →        6.17 s   (+20.78%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      323.32 ns →      312.00 ns   (-3.50%) |      19   →      23    (+21.05%) |        6.14 μs →        7.18 μs  (+16.82%) | 
- │ │ ├ sirius::Field4D::symmetrize                                     |       96.48 ms →       99.04 ms   (+2.65%) |      19   →      23    (+21.05%) |        1.83 s  →        2.28 s   (+24.26%) | 
- │ │ │ └ sirius::symmetrize_function|fpw                               |       96.48 ms →       99.03 ms   (+2.65%) |      19   →      23    (+21.05%) |        1.83 s  →        2.28 s   (+24.26%) | 
- │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.24 ms →       15.91 ms  (+20.17%) |      19   →      23    (+21.05%) |      251.54 ms →      365.92 ms  (+45.47%) | 
- │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       69.99 ms →       69.94 ms   (-0.08%) |      19   →      23    (+21.05%) |        1.33 s  →        1.61 s   (+20.96%) | 
- │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.62 ms →       12.56 ms   (-0.43%) |      19   →      23    (+21.05%) |      239.74 ms →      288.95 ms  (+20.53%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.50 ms →        6.61 ms  (+89.03%) |      19   →      23    (+21.05%) |       66.42 ms →      151.99 ms (+128.83%) | 
- │ │ ├ sirius::Periodic_function|inner                                 |        4.83 ms →        4.69 ms   (-2.89%) |     133   →     161    (+21.05%) |      643.04 ms →      755.89 ms  (+17.55%) | 
- │ │ │ └ sirius::Periodic_function|inner_local                         |        4.56 ms →        4.59 ms   (+0.50%) |     133   →     161    (+21.05%) |      607.13 ms →      738.62 ms  (+21.66%) | 
- │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.56 ms →        4.59 ms   (+0.50%) |     133   →     161    (+21.05%) |      607.04 ms →      738.52 ms  (+21.66%) | 
- │ │ ├ sirius::Smooth_periodic_function|inner                          |        5.06 ms →        4.95 ms   (-2.14%) |      57   →      69    (+21.05%) |      288.19 ms →      341.40 ms  (+18.46%) | 
- │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.94 ms →        4.94 ms   (+0.02%) |      57   →      69    (+21.05%) |      281.48 ms →      340.82 ms  (+21.08%) | 
- │ │ ├ sirius::Periodic_function::integrate                            |        4.54 ms →        4.54 ms   (+0.04%) |      19   →      23    (+21.05%) |       86.19 ms →      104.38 ms  (+21.10%) | 
- │ │ └ sirius::Density::get_magnetisation                              |       78.67 μs →       75.34 μs   (-4.24%) |      19   →      23    (+21.05%) |        1.49 ms →        1.73 ms  (+15.92%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |       73.55 μs →       70.34 μs   (-4.37%) |      19   →      23    (+21.05%) |        1.40 ms →        1.62 ms  (+15.76%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.57 ms →        5.52 ms   (-0.98%) |       2   →       2              |       11.14 ms →       11.03 ms   (-0.98%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.81 ms →        4.80 ms   (-0.14%) |       6   →       6              |       28.86 ms →       28.82 ms   (-0.14%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.81 ms →        4.80 ms   (-0.15%) |       6   →       6              |       28.84 ms →       28.80 ms   (-0.15%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.80 ms →        4.80 ms   (-0.14%) |       6   →       6              |       28.83 ms →       28.79 ms   (-0.14%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        5.17 ms →        5.23 ms   (+1.04%) |       3   →       3              |       15.51 ms →       15.68 ms   (+1.04%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        5.17 ms →        5.22 ms   (+1.04%) |       3   →       3              |       15.50 ms →       15.66 ms   (+1.04%) | 
  ├ sirius::Periodic_function|inner                                     |        4.76 ms →        4.54 ms   (-4.51%) |       2   →       2              |        9.52 ms →        9.09 ms   (-4.51%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.76 ms →        4.54 ms   (-4.52%) |       2   →       2              |        9.51 ms →        9.08 ms   (-4.52%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.75 ms →        4.54 ms   (-4.52%) |       2   →       2              |        9.51 ms →        9.08 ms   (-4.52%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        5.26 ms →        4.92 ms   (-6.48%) |       1   →       1              |        5.26 ms →        4.92 ms   (-6.48%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        5.26 ms →        4.92 ms   (-6.51%) |       1   →       1              |        5.26 ms →        4.92 ms   (-6.51%) | 
- └ sirius::finalize                                                    |      143.44 ms →      246.19 ms  (+71.63%) |       1   →       1              |      143.44 ms →      246.19 ms  (+71.63%) | 
  ====================================================================================================================================================================================================
```
