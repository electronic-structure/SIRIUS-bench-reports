# Benchmark 81702c64a8be67a2936e3e8bb8ca2c9083dee03b vs e1ce68d49d41c91f8b269558d6cb9276c8e4e886
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |       72.35 s  →       74.68 s    (+3.22%) |       1   →       1              |       72.35 s  →       74.68 s    (+3.22%) | 
  ├ sirius::initialize                                                  |        2.97 s  →        2.86 s    (-3.92%) |       1   →       1              |        2.97 s  →        2.86 s    (-3.92%) | 
  ├ sirius::Simulation_context::initialize                              |        3.76 s  →        3.68 s    (-2.29%) |       1   →       1              |        3.76 s  →        3.68 s    (-2.29%) | 
- │ ├ sirius::Simulation_context::init_comm                             |       26.37 ms →       62.65 ms (+137.54%) |       1   →       1              |       26.37 ms →       62.65 ms (+137.54%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      163.40 ms →      180.68 ms  (+10.58%) |       1   →       1              |      163.40 ms →      180.68 ms  (+10.58%) | 
  │ │ ├ sirius::Atom_type::init                                         |       74.00 ms →       81.11 ms   (+9.61%) |       2   →       2              |      148.00 ms →      162.22 ms   (+9.61%) | 
- │ │ └ sirius::Unit_cell::update                                       |       15.31 ms →       18.37 ms  (+19.96%) |       1   →       1              |       15.31 ms →       18.37 ms  (+19.96%) | 
+ │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.97 ms →        3.62 ms  (-27.08%) |       1   →       1              |        4.97 ms →        3.62 ms  (-27.08%) | 
- │ │   └ sirius::Unit_cell::get_symmetry                               |       10.28 ms →       14.67 ms  (+42.78%) |       1   →       1              |       10.28 ms →       14.67 ms  (+42.78%) | 
- │ │     └ sirius::Unit_cell_symmetry                                  |       10.21 ms →       14.60 ms  (+42.99%) |       1   →       1              |       10.21 ms →       14.60 ms  (+42.99%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.77 ms →        2.77 ms   (+0.12%) |       1   →       1              |        2.77 ms →        2.77 ms   (+0.12%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      505.26 μs →      522.35 μs   (+3.38%) |       1   →       1              |      505.26 μs →      522.35 μs   (+3.38%) | 
- │ │       └ sirius::Unit_cell_symmetry|mag                            |       15.65 μs →       17.40 μs  (+11.22%) |       1   →       1              |       15.65 μs →       17.40 μs  (+11.22%) | 
  │ └ sirius::Simulation_context::update                                |        3.35 s  →        3.35 s    (+0.05%) |       1   →       1              |        3.35 s  →        3.35 s    (+0.05%) | 
  │   ├ sirius::Unit_cell::update                                       |        7.10 ms →        7.02 ms   (-1.20%) |       1   →       1              |        7.10 ms →        7.02 ms   (-1.20%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.64 ms →        3.65 ms   (+0.21%) |       1   →       1              |        3.64 ms →        3.65 ms   (+0.21%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.41 ms →        3.34 ms   (-2.09%) |       1   →       1              |        3.41 ms →        3.34 ms   (-2.09%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.36 ms →        3.29 ms   (-2.15%) |       1   →       1              |        3.36 ms →        3.29 ms   (-2.15%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.80 ms →        2.74 ms   (-2.07%) |       1   →       1              |        2.80 ms →        2.74 ms   (-2.07%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      529.87 μs →      514.53 μs   (-2.89%) |       1   →       1              |      529.87 μs →      514.53 μs   (-2.89%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       14.49 μs →       14.50 μs   (+0.08%) |       1   →       1              |       14.49 μs →       14.50 μs   (+0.08%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      211.78 ms →      211.25 ms   (-0.25%) |       2   →       2              |      423.56 ms →      422.50 ms   (-0.25%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.18 ms →       15.33 ms   (+0.96%) |       2   →       2              |       30.36 ms →       30.66 ms   (+0.96%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.28 ms →       13.25 ms   (-0.21%) |       1   →       1              |       13.28 ms →       13.25 ms   (-0.21%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.52 ms →       56.38 ms   (-0.26%) |       2   →       2              |      113.04 ms →      112.75 ms   (-0.26%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.06 ms →       45.06 ms   (-0.01%) |       2   →       2              |       90.12 ms →       90.11 ms   (-0.01%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.31 ms →       60.33 ms   (+0.02%) |       4   →       4              |      241.25 ms →      241.30 ms   (+0.02%) | 
  │   ├ sddk::Gvec::init                                                |       94.32 ms →       96.96 ms   (+2.80%) |       2   →       2              |      188.63 ms →      193.92 ms   (+2.80%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       70.03 ms →       72.53 ms   (+3.57%) |       2   →       2              |      140.06 ms →      145.06 ms   (+3.57%) | 
  │   ├ sddk::Gvec_shells                                               |       96.05 ms →      104.52 ms   (+8.82%) |       1   →       1              |       96.05 ms →      104.52 ms   (+8.82%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.95 ms →        1.94 ms   (-0.40%) |       1   →       1              |        1.95 ms →        1.94 ms   (-0.40%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      511.53 ms →      510.27 ms   (-0.25%) |       2   →       2              |        1.02 s  →        1.02 s    (-0.25%) | 
- ├ sirius::K_point_set::create_k_mesh                                  |      122.76 ms →      161.19 ms  (+31.31%) |       1   →       1              |      122.76 ms →      161.19 ms  (+31.31%) | 
+ │ ├ sirius::K_point::K_point                                          |        2.26 μs →        1.45 μs  (-35.69%) |       4   →       4              |        9.04 μs →        5.82 μs  (-35.69%) | 
- │ └ sirius::K_point_set::initialize                                   |      122.68 ms →      161.10 ms  (+31.32%) |       1   →       1              |      122.68 ms →      161.10 ms  (+31.32%) | 
  │   └ sirius::K_point::initialize                                     |       28.27 ms →       28.49 ms   (+0.76%) |       1   →       1              |       28.27 ms →       28.49 ms   (+0.76%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       10.94 ms →       10.89 ms   (-0.42%) |       1   →       1              |       10.94 ms →       10.89 ms   (-0.42%) | 
  │     │ └ sddk::Gvec::init                                            |        4.90 ms →        4.88 ms   (-0.42%) |       1   →       1              |        4.90 ms →        4.88 ms   (-0.42%) | 
- │     ├ sddk::matrix_storage::matrix_storage                          |        8.32 μs →       10.70 μs  (+28.54%) |       1   →       1              |        8.32 μs →       10.70 μs  (+28.54%) | 
  │     └ sirius::K_point::update                                       |       14.43 ms →       14.75 ms   (+2.21%) |       1   →       1              |       14.43 ms →       14.75 ms   (+2.21%) | 
  │       └ sirius::Beta_projectors                                     |       10.54 ms →       11.00 ms   (+4.27%) |       1   →       1              |       10.54 ms →       11.00 ms   (+4.27%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.64 ms →        8.93 ms   (+3.35%) |       1   →       1              |        8.64 ms →        8.93 ms   (+3.35%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.58 ms →        2.61 ms   (+1.25%) |       2   →       2              |        5.15 ms →        5.22 ms   (+1.25%) | 
  ├ sirius::Potential                                                   |       49.70 ms →       52.56 ms   (+5.74%) |       1   →       1              |       49.70 ms →       52.56 ms   (+5.74%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.93 ms →        2.92 ms   (-0.40%) |       6   →       6              |       17.58 ms →       17.50 ms   (-0.40%) | 
  │ └ sirius::Potential::update                                         |       31.55 ms →       34.40 ms   (+9.04%) |       1   →       1              |       31.55 ms →       34.40 ms   (+9.04%) | 
  │   └ sirius::Potential::generate_local_potential                     |       31.15 ms →       33.99 ms   (+9.13%) |       1   →       1              |       31.15 ms →       33.99 ms   (+9.13%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       26.66 ms →       25.78 ms   (-3.32%) |       1   →       1              |       26.66 ms →       25.78 ms   (-3.32%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        3.95 ms →        7.70 ms  (+94.64%) |       1   →       1              |        3.95 ms →        7.70 ms  (+94.64%) | 
- ├ sirius::Density                                                     |       37.77 ms →       42.87 ms  (+13.50%) |       1   →       1              |       37.77 ms →       42.87 ms  (+13.50%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.83 ms →        2.82 ms   (-0.54%) |       2   →       2              |        5.67 ms →        5.64 ms   (-0.54%) | 
- │ └ sirius::Density::update                                           |       31.96 ms →       37.09 ms  (+16.05%) |       1   →       1              |       31.96 ms →       37.09 ms  (+16.05%) | 
- │   └ sirius::Density::generate_pseudo_core_charge_density            |       31.75 ms →       36.87 ms  (+16.15%) |       1   →       1              |       31.75 ms →       36.87 ms  (+16.15%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |       78.81 μs →       78.91 μs   (+0.12%) |       1   →       1              |       78.81 μs →       78.91 μs   (+0.12%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       26.44 ms →       25.60 ms   (-3.18%) |       1   →       1              |       26.44 ms →       25.60 ms   (-3.18%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        4.93 ms →       10.90 ms (+120.96%) |       1   →       1              |        4.93 ms →       10.90 ms (+120.96%) | 
- ├ sirius::Density::initial_density                                    |       55.68 ms →       62.31 ms  (+11.91%) |       1   →       1              |       55.68 ms →       62.31 ms  (+11.91%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       26.72 ms →       25.96 ms   (-2.87%) |       1   →       1              |       26.72 ms →       25.96 ms   (-2.87%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.00 ms →        8.39 ms  (+67.83%) |       2   →       2              |       10.00 ms →       16.78 ms  (+67.83%) | 
  │ └ sirius::Periodic_function::integrate                              |        5.35 ms →        5.51 ms   (+2.90%) |       1   →       1              |        5.35 ms →        5.51 ms   (+2.90%) | 
  ├ sirius::Potential::generate                                         |      363.54 ms →      371.32 ms   (+2.14%) |       1   →       1              |      363.54 ms →      371.32 ms   (+2.14%) | 
- │ ├ sirius::Potential::poisson                                        |       36.53 ms →       44.53 ms  (+21.91%) |       1   →       1              |       36.53 ms →       44.53 ms  (+21.91%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        4.76 ms →       13.80 ms (+189.84%) |       1   →       1              |        4.76 ms →       13.80 ms (+189.84%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        5.90 ms →        6.10 ms   (+3.29%) |       1   →       1              |        5.90 ms →        6.10 ms   (+3.29%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.85 ms →        5.25 ms   (+8.33%) |       1   →       1              |        4.85 ms →        5.25 ms   (+8.33%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.83 ms →        5.24 ms   (+8.32%) |       1   →       1              |        4.83 ms →        5.24 ms   (+8.32%) | 
  │ ├ sirius::Periodic_function::add                                    |      833.98 μs →      796.62 μs   (-4.48%) |       2   →       2              |        1.67 ms →        1.59 ms   (-4.48%) | 
  │ ├ sirius::Potential::xc                                             |       50.82 ms →       50.97 ms   (+0.31%) |       1   →       1              |       50.82 ms →       50.97 ms   (+0.31%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       49.65 ms →       49.76 ms   (+0.23%) |       1   →       1              |       49.65 ms →       49.76 ms   (+0.23%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.57 ms →        2.55 ms   (-0.76%) |       2   →       2              |        5.14 ms →        5.11 ms   (-0.76%) | 
  │ │   └ sirius::Smooth_periodic_function::fft_transform               |        4.06 ms →        4.07 ms   (+0.18%) |       1   →       1              |        4.06 ms →        4.07 ms   (+0.18%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.53 ms →        3.54 ms   (+0.24%) |       1   →       1              |        3.53 ms →        3.54 ms   (+0.24%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      269.66 ms →      269.30 ms   (-0.13%) |       1   →       1              |      269.66 ms →      269.30 ms   (-0.13%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      202.00 ns →      219.00 ns   (+8.42%) |       1   →       1              |      202.00 ns →      219.00 ns   (+8.42%) | 
  ├ sirius::Hamiltonian0                                                |        8.37 ms →        8.63 ms   (+3.04%) |       1   →       1              |        8.37 ms →        8.63 ms   (+3.04%) | 
  │ ├ sirius::Local_operator                                            |        7.77 ms →        7.73 ms   (-0.57%) |       1   →       1              |        7.77 ms →        7.73 ms   (-0.57%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.74 ms →        2.76 ms   (+0.41%) |       1   →       1              |        2.74 ms →        2.76 ms   (+0.41%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        3.79 ms →        3.81 ms   (+0.63%) |       1   →       1              |        3.79 ms →        3.81 ms   (+0.63%) | 
- │ ├ sirius::Non_local_operator                                        |      164.32 μs →      314.87 μs  (+91.63%) |       2   →       2              |      328.63 μs →      629.75 μs  (+91.63%) | 
  │ ├ sirius::D_operator::initialize                                    |      109.57 μs →      108.62 μs   (-0.86%) |       1   →       1              |      109.57 μs →      108.62 μs   (-0.86%) | 
  │ └ sirius::Q_operator::initialize                                    |       93.59 μs →       91.26 μs   (-2.49%) |       1   →       1              |       93.59 μs →       91.26 μs   (-2.49%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.30 s  →        1.28 s    (-1.23%) |       1   →       1              |        1.30 s  →        1.28 s    (-1.23%) | 
- │ ├ sirius::Hamiltonian_k                                             |       58.86 ms →       67.22 ms  (+14.21%) |       1   →       1              |       58.86 ms →       67.22 ms  (+14.21%) | 
- │ │ ├ sirius::Local_operator::prepare_k                               |      226.02 μs →      270.03 μs  (+19.47%) |       1   →       1              |      226.02 μs →      270.03 μs  (+19.47%) | 
- │ │ └ sirius::Beta_projectors_base::prepare                           |       58.63 ms →       66.95 ms  (+14.19%) |       1   →       1              |       58.63 ms →       66.95 ms  (+14.19%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.24 s  →        1.22 s    (-1.96%) |       1   →       1              |        1.24 s  →        1.22 s    (-1.96%) | 
- │ │ ├ sddk::matrix_storage::matrix_storage                            |       82.93 ms →       91.24 ms  (+10.02%) |       4   →       4              |      331.73 ms →      364.97 ms  (+10.02%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       36.13 ms →       37.65 ms   (+4.21%) |       1   →       1              |       36.13 ms →       37.65 ms   (+4.21%) | 
- │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        6.52 ms →        7.40 ms  (+13.47%) |       1   →       1              |        6.52 ms →        7.40 ms  (+13.47%) | 
- │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      334.19 ms →      381.48 ms  (+14.15%) |       1   →       1              |      334.19 ms →      381.48 ms  (+14.15%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      246.34 ms →      270.87 ms   (+9.96%) |       1   →       1              |      246.34 ms →      270.87 ms   (+9.96%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.75 μs →        3.86 μs   (+2.80%) |       1   →       1              |        3.75 μs →        3.86 μs   (+2.80%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.83 μs →        2.93 μs   (+3.39%) |       1   →       1              |        2.83 μs →        2.93 μs   (+3.39%) | 
- │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      358.00 ns →      408.00 ns  (+13.97%) |       1   →       1              |      358.00 ns →      408.00 ns  (+13.97%) | 
- │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      650.00 ns →      869.00 ns  (+33.69%) |       1   →       1              |      650.00 ns →      869.00 ns  (+33.69%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.14 ms →        3.02 ms   (-3.87%) |       1   →       1              |        3.14 ms →        3.02 ms   (-3.87%) | 
- │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.26 ms →       38.54 ms  (+81.23%) |       1   →       1              |       21.26 ms →       38.54 ms  (+81.23%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |       31.70 ms →       34.51 ms   (+8.84%) |       2   →       2              |       63.41 ms →       69.01 ms   (+8.84%) | 
+ │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.98 ms →        6.61 ms  (-55.88%) |       2   →       2              |       29.97 ms →       13.22 ms  (-55.88%) | 
+ │ │ │ └ sddk::wf_inner                                                |       14.78 ms →        6.41 ms  (-56.64%) |       2   →       2              |       29.55 ms →       12.81 ms  (-56.64%) | 
+ │ │ │   ├ sddk::wf_inner|scale                                        |       37.00 ns →       30.00 ns  (-18.92%) |       2   →       2              |       74.00 ns →       60.00 ns  (-18.92%) | 
+ │ │ │   ├ sddk::wf_inner|pw                                           |       14.65 ms →        6.28 ms  (-57.13%) |       2   →       2              |       29.30 ms →       12.56 ms  (-57.13%) | 
+ │ │ │   └ sddk::wf_inner|scale_back                                   |       38.50 ns →       20.50 ns  (-46.75%) |       2   →       2              |       77.00 ns →       41.00 ns  (-46.75%) | 
+ │ │ ├ Eigensolver_cuda|zhegvdx                                        |      232.13 ms →      200.92 ms  (-13.44%) |       1   →       1              |      232.13 ms →      200.92 ms  (-13.44%) | 
  │ │ └ sddk::wf_trans                                                  |        2.61 ms →        2.62 ms   (+0.47%) |       1   →       1              |        2.61 ms →        2.62 ms   (+0.47%) | 
  │ │   └ sddk::wf_trans|pw                                             |        2.61 ms →        2.62 ms   (+0.49%) |       1   →       1              |        2.61 ms →        2.62 ms   (+0.49%) | 
  │ └ sirius::Beta_projectors_base::dismiss                             |      423.00 ns →      465.00 ns   (+9.93%) |       1   →       1              |      423.00 ns →      465.00 ns   (+9.93%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |       62.58 s  →       64.98 s    (+3.84%) |       1   →       1              |       62.58 s  →       64.98 s    (+3.84%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.47 ms →        2.43 ms   (-1.23%) |      19   →      19              |       46.84 ms →       46.26 ms   (-1.23%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        2.97 s  →        2.94 s    (-0.77%) |      21   →      22     (+4.76%) |       62.31 s  →       64.78 s    (+3.96%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        5.15 ms →        5.63 ms   (+9.23%) |      21   →      22     (+4.76%) |      108.22 ms →      123.84 ms  (+14.43%) | 
- │ │ │ ├ sirius::Local_operator                                        |        4.53 ms →        4.83 ms   (+6.55%) |      21   →      22     (+4.76%) |       95.19 ms →      106.26 ms  (+11.63%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      557.99 μs →      531.37 μs   (-4.77%) |      21   →      22     (+4.76%) |       11.72 ms →       11.69 ms   (-0.24%) | 
- │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.86 ms →        3.23 ms  (+12.75%) |      21   →      22     (+4.76%) |       60.10 ms →       70.98 ms  (+18.11%) | 
- │ │ │ ├ sirius::Non_local_operator                                    |      160.69 μs →      260.88 μs  (+62.35%) |      42   →      44     (+4.76%) |        6.75 ms →       11.48 ms  (+70.08%) | 
+ │ │ │ ├ sirius::D_operator::initialize                                |      125.33 μs →      107.81 μs  (-13.98%) |      21   →      22     (+4.76%) |        2.63 ms →        2.37 ms   (-9.88%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       91.96 μs →       91.32 μs   (-0.69%) |      21   →      22     (+4.76%) |        1.93 ms →        2.01 ms   (+4.04%) | 
  │ │ ├ sirius::Band::solve                                             |        1.75 s  →        1.71 s    (-2.54%) |      21   →      22     (+4.76%) |       36.81 s  →       37.58 s    (+2.11%) | 
+ │ │ │ ├ sirius::Hamiltonian_k                                         |      241.30 μs →      187.67 μs  (-22.23%) |      21   →      22     (+4.76%) |        5.07 ms →        4.13 ms  (-18.52%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      231.75 μs →      178.95 μs  (-22.78%) |      21   →      22     (+4.76%) |        4.87 ms →        3.94 ms  (-19.11%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        7.22 μs →        6.36 μs  (-11.95%) |      21   →      22     (+4.76%) |      151.70 μs →      139.93 μs   (-7.76%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.63 s  →        1.57 s    (-3.35%) |      21   →      22     (+4.76%) |       34.18 s  →       34.61 s    (+1.26%) | 
- │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       66.49 ms →       78.23 ms  (+17.66%) |      21   →      22     (+4.76%) |        1.40 s  →        1.72 s   (+23.26%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.23 ms →        5.99 ms  (-17.21%) |     126   →     154    (+22.22%) |      911.51 ms →      922.31 ms   (+1.18%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       18.00 ms →       12.87 ms  (-28.50%) |      21   →      22     (+4.76%) |      377.94 ms →      283.08 ms  (-25.10%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      458.48 μs →      459.38 μs   (+0.19%) |      21   →      22     (+4.76%) |        9.63 ms →       10.11 ms   (+4.97%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        8.21 ms →        5.70 ms  (-30.64%) |      42   →      44     (+4.76%) |      344.92 ms →      250.64 ms  (-27.33%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.53 s  →        1.46 s    (-4.80%) |      21   →      22     (+4.76%) |       32.22 s  →       32.13 s    (-0.27%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       50.29 ms →      102.81 ms (+104.45%) |     361   →     180    (-50.14%) |       18.15 s  →       18.51 s    (+1.94%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       29.48 ms →       77.53 ms (+162.96%) |     361   →     180    (-50.14%) |       10.64 s  →       13.96 s   (+31.12%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.18 μs →        2.35 μs   (+7.79%) |     361   →     180    (-50.14%) |      788.20 μs →      423.61 μs  (-46.26%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.82 μs →        1.97 μs   (+8.25%) |     361   →     180    (-50.14%) |      656.18 μs →      354.18 μs  (-46.02%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      479.32 ns →      418.77 ns  (-12.63%) |     361   →     180    (-50.14%) |      173.03 μs →       75.38 μs  (-56.44%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      684.85 ns →      786.94 ns  (+14.91%) |     361   →     180    (-50.14%) |      247.23 μs →      141.65 μs  (-42.71%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.94 ms →        2.96 ms   (+0.62%) |     361   →     180    (-50.14%) |        1.06 s  →      532.89 ms  (-49.83%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.19 ms →        5.54 ms  (+73.38%) |     361   →     180    (-50.14%) |        1.15 s  →      996.52 ms  (-13.55%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.33 ms →        8.38 ms  (+14.45%) |     722   →     360    (-50.14%) |        5.29 s  →        3.02 s   (-42.94%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |        6.54 ms →        8.99 ms  (+37.45%) |     361   →     180    (-50.14%) |        2.36 s  →        1.62 s   (-31.46%) | 
- │ │ │ │   │ ├ sddk::wf_inner                                          |        1.10 ms →        1.32 ms  (+20.50%) |     701   →     338    (-51.78%) |      768.98 ms →      446.78 ms  (-41.90%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       54.26 ns →       52.30 ns   (-3.62%) |     701   →     338    (-51.78%) |       38.04 μs →       17.68 μs  (-53.53%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |      934.52 μs →        1.14 ms  (+22.28%) |     701   →     338    (-51.78%) |      655.10 ms →      386.26 ms  (-41.04%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       45.37 ns →       57.50 ns  (+26.74%) |     701   →     338    (-51.78%) |       31.80 μs →       19.44 μs  (-38.89%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      139.02 μs →      282.15 μs (+102.96%) |     361   →     180    (-50.14%) |       50.18 ms →       50.79 ms   (+1.20%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        1.95 ms →        3.21 ms  (+65.13%) |     361   →     180    (-50.14%) |      702.46 ms →      578.37 ms  (-17.66%) | 
- │ │ │ │   │ └ sddk::wf_trans                                          |        2.46 ms →        3.42 ms  (+39.03%) |     340   →     158    (-53.53%) |      837.36 ms →      540.99 ms  (-35.39%) | 
- │ │ │ │   │   └ sddk::wf_trans|pw                                     |      820.12 μs →        1.14 ms  (+39.06%) |    1.02 K →     474    (-53.53%) |      836.52 ms →      540.57 ms  (-35.38%) | 
- │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.34 ms →        1.71 ms  (+28.26%) |     361   →     180    (-50.14%) |      482.54 ms →      308.60 ms  (-36.05%) | 
- │ │ │ │   │ └ sddk::wf_inner                                          |        1.29 ms →        1.64 ms  (+27.31%) |     361   →     180    (-50.14%) |      464.91 ms →      295.12 ms  (-36.52%) | 
+ │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       45.25 ns →       40.00 ns  (-11.60%) |     361   →     180    (-50.14%) |       16.33 μs →        7.20 μs  (-55.92%) | 
- │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        1.12 ms →        1.46 ms  (+30.07%) |     361   →     180    (-50.14%) |      405.25 ms →      262.82 ms  (-35.15%) | 
+ │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       43.67 ns →       47.32 ns   (+8.36%) |     361   →     180    (-50.14%) |       15.76 μs →        8.52 μs  (-45.97%) | 
- │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       27.30 ms →       58.97 ms (+116.02%) |     361   →     180    (-50.14%) |        9.85 s  →       10.62 s    (+7.71%) | 
- │ │ │ │   ├ sirius::residuals                                         |        2.66 ms →        3.59 ms  (+34.71%) |     346   →     179    (-48.27%) |      921.07 ms →      641.91 ms  (-30.31%) | 
- │ │ │ │   │ ├ sddk::wf_trans                                          |        1.28 ms →        1.95 ms  (+52.40%) |     342   →     179    (-47.66%) |      438.61 ms →      349.85 ms  (-20.24%) | 
- │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |      639.81 μs →      975.69 μs  (+52.50%) |     684   →     358    (-47.66%) |      437.63 ms →      349.30 ms  (-20.18%) | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.32 ms →        1.52 ms  (+14.69%) |     342   →     179    (-47.66%) |      451.93 ms →      271.29 ms  (-39.97%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        4.89 ms →        6.27 ms  (+28.36%) |      90   →      70    (-22.22%) |      439.98 ms →      439.25 ms   (-0.17%) | 
- │ │ │ │     └ sddk::wf_trans                                          |        2.71 ms →        3.67 ms  (+35.09%) |     159   →     118    (-25.79%) |      431.48 ms →      432.58 ms   (+0.25%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |        1.89 ms →        2.60 ms  (+37.73%) |     228   →     166    (-27.19%) |      431.16 ms →      432.34 ms   (+0.27%) | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      564.71 ns →      393.82 ns  (-30.26%) |      21   →      22     (+4.76%) |       11.86 μs →        8.66 μs  (-26.94%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       19.80 μs →       30.56 μs  (+54.38%) |      21   →      22     (+4.76%) |      415.76 μs →      672.43 μs  (+61.73%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.53 ms →        1.48 ms   (-3.64%) |      21   →      22     (+4.76%) |       32.19 ms →       32.49 ms   (+0.95%) | 
  │ │ ├ sirius::Density::generate                                       |      565.95 ms →      567.99 ms   (+0.36%) |      21   →      22     (+4.76%) |       11.88 s  →       12.50 s    (+5.14%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      411.98 ms →      414.64 ms   (+0.65%) |      21   →      22     (+4.76%) |        8.65 s  →        9.12 s    (+5.44%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.17 μs →        7.11 μs  (-12.97%) |      21   →      22     (+4.76%) |      171.63 μs →      156.48 μs   (-8.83%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.48 μs →        6.51 μs  (-12.91%) |      21   →      22     (+4.76%) |      157.06 μs →      143.29 μs   (-8.76%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       22.48 ms →       30.55 ms  (+35.89%) |      21   →      22     (+4.76%) |      472.03 ms →      672.02 ms  (+42.37%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       10.95 μs →       10.77 μs   (-1.65%) |      21   →      22     (+4.76%) |      229.85 μs →      236.83 μs   (+3.04%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        3.97 ms →        4.65 ms  (+17.05%) |      21   →      22     (+4.76%) |       83.46 ms →      102.35 ms  (+22.63%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       17.44 ms →       24.87 ms  (+42.62%) |      21   →      22     (+4.76%) |      366.18 ms →      547.13 ms  (+49.42%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |        1.08 μs →      844.59 ns  (-21.80%) |      21   →      22     (+4.76%) |       22.68 μs →       18.58 μs  (-18.08%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      122.88 ms →      115.12 ms   (-6.32%) |      21   →      22     (+4.76%) |        2.58 s  →        2.53 s    (-1.86%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.91 ms →        1.93 ms   (+1.35%) |      21   →      22     (+4.76%) |       40.08 ms →       42.56 ms   (+6.18%) | 
  │ │ │ │ └ sirius::Density::augment                                    |      234.61 ms →      227.74 ms   (-2.93%) |      21   →      22     (+4.76%) |        4.93 s  →        5.01 s    (+1.69%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |      234.38 ms →      227.51 ms   (-2.93%) |      21   →      22     (+4.76%) |        4.92 s  →        5.01 s    (+1.69%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      123.37 ms →      126.18 ms   (+2.28%) |      21   →      22     (+4.76%) |        2.59 s  →        2.78 s    (+7.15%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      123.37 ms →      126.18 ms   (+2.28%) |      21   →      22     (+4.76%) |        2.59 s  →        2.78 s    (+7.15%) | 
- │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       40.08 ms →       43.44 ms   (+8.38%) |      21   →      22     (+4.76%) |      841.67 ms →      955.65 ms  (+13.54%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       69.85 ms →       68.88 ms   (-1.39%) |      21   →      22     (+4.76%) |        1.47 s  →        1.52 s    (+3.31%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.78 ms →       13.21 ms   (+3.35%) |      21   →      22     (+4.76%) |      268.48 ms →      290.68 ms   (+8.27%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.69 ms →       23.54 ms   (-0.63%) |      21   →      22     (+4.76%) |      497.40 ms →      517.80 ms   (+4.10%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        6.91 ms →        3.63 ms  (-47.52%) |      21   →      22     (+4.76%) |      145.12 ms →       79.78 ms  (-45.02%) | 
- │ │ ├ sirius::Density::mix                                            |      134.85 ms →      143.38 ms   (+6.33%) |      21   →      22     (+4.76%) |        2.83 s  →        3.15 s   (+11.39%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      313.81 μs →        1.08 ms (+244.80%) |      21   →      22     (+4.76%) |        6.59 ms →       23.80 ms (+261.22%) | 
- │ │ │ ├ sirius::Periodic_function|inner                               |        4.75 ms →        5.28 ms  (+11.20%) |     259   →     274     (+5.79%) |        1.23 s  →        1.45 s   (+17.64%) | 
- │ │ │ │ └ sirius::Periodic_function|inner_local                       |        4.63 ms →        5.20 ms  (+12.26%) |     259   →     274     (+5.79%) |        1.20 s  →        1.42 s   (+18.76%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        4.63 ms →        5.20 ms  (+12.26%) |     259   →     274     (+5.79%) |        1.20 s  →        1.42 s   (+18.77%) | 
- │ │ │ └ sirius::Density::mixer_output                                 |        5.13 ms →        5.45 ms   (+6.14%) |      21   →      22     (+4.76%) |      107.79 ms →      119.85 ms  (+11.19%) | 
- │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        4.37 ms →        4.75 ms   (+8.63%) |      21   →      22     (+4.76%) |       91.80 ms →      104.47 ms  (+13.80%) | 
  │ │ ├ sirius::Potential::generate                                     |      355.75 ms →      363.96 ms   (+2.31%) |      21   →      22     (+4.76%) |        7.47 s  →        8.01 s    (+7.18%) | 
- │ │ │ ├ sirius::Potential::poisson                                    |       35.74 ms →       43.72 ms  (+22.30%) |      21   →      22     (+4.76%) |      750.64 ms →      961.73 ms  (+28.12%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        4.00 ms →       12.82 ms (+220.29%) |      21   →      22     (+4.76%) |       84.03 ms →      281.95 ms (+235.54%) | 
  │ │ │ │ └ sirius::Periodic_function|inner                             |        5.93 ms →        6.21 ms   (+4.83%) |      21   →      22     (+4.76%) |      124.50 ms →      136.72 ms   (+9.82%) | 
- │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.85 ms →        5.23 ms   (+7.88%) |      21   →      22     (+4.76%) |      101.82 ms →      115.07 ms  (+13.02%) | 
- │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.85 ms →        5.23 ms   (+7.89%) |      21   →      22     (+4.76%) |      101.79 ms →      115.05 ms  (+13.03%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      779.75 μs →      811.27 μs   (+4.04%) |      42   →      44     (+4.76%) |       32.75 ms →       35.70 ms   (+9.00%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       44.98 ms →       45.24 ms   (+0.57%) |      21   →      22     (+4.76%) |      944.59 ms →      995.18 ms   (+5.36%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       43.79 ms →       44.06 ms   (+0.60%) |      21   →      22     (+4.76%) |      919.63 ms →      969.24 ms   (+5.39%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |      681.71 μs →      664.54 μs   (-2.52%) |      42   →      44     (+4.76%) |       28.63 ms →       29.24 ms   (+2.12%) | 
- │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        4.48 ms →        4.86 ms   (+8.43%) |      21   →      22     (+4.76%) |       94.11 ms →      106.90 ms  (+13.60%) | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.60 ms →        3.13 ms  (-13.08%) |      21   →      22     (+4.76%) |       75.63 ms →       68.87 ms   (-8.94%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.42 ms →      268.85 ms   (+0.16%) |      21   →      22     (+4.76%) |        5.64 s  →        5.91 s    (+4.93%) | 
- │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      173.67 ns →      189.18 ns   (+8.93%) |      21   →      22     (+4.76%) |        3.65 μs →        4.16 μs  (+14.12%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |       95.87 ms →       95.18 ms   (-0.72%) |      21   →      22     (+4.76%) |        2.01 s  →        2.09 s    (+4.01%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |       95.87 ms →       95.18 ms   (-0.72%) |      21   →      22     (+4.76%) |        2.01 s  →        2.09 s    (+4.01%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.27 ms →       13.26 ms   (-0.08%) |      21   →      22     (+4.76%) |      278.62 ms →      291.65 ms   (+4.67%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       69.42 ms →       68.73 ms   (-0.99%) |      21   →      22     (+4.76%) |        1.46 s  →        1.51 s    (+3.72%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.56 ms →       12.57 ms   (+0.12%) |      21   →      22     (+4.76%) |      263.66 ms →      276.55 ms   (+4.89%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        4.43 ms →        3.57 ms  (-19.32%) |      21   →      22     (+4.76%) |       93.01 ms →       78.62 ms  (-15.48%) | 
- │ │ ├ sirius::Periodic_function|inner                                 |        4.59 ms →        4.93 ms   (+7.44%) |     147   →     154     (+4.76%) |      674.34 ms →      759.01 ms  (+12.56%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.55 ms →        4.77 ms   (+4.75%) |     147   →     154     (+4.76%) |      669.30 ms →      734.48 ms   (+9.74%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.55 ms →        4.77 ms   (+4.75%) |     147   →     154     (+4.76%) |      669.21 ms →      734.37 ms   (+9.74%) | 
- │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.74 ms →        5.17 ms   (+9.19%) |      63   →      66     (+4.76%) |      298.40 ms →      341.33 ms  (+14.39%) | 
- │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.73 ms →        5.13 ms   (+8.53%) |      63   →      66     (+4.76%) |      297.87 ms →      338.67 ms  (+13.70%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        4.54 ms →        4.75 ms   (+4.81%) |      21   →      22     (+4.76%) |       95.26 ms →      104.60 ms   (+9.80%) | 
  │ │ └ sirius::Density::get_magnetisation                              |       75.18 μs →       75.62 μs   (+0.59%) |      21   →      22     (+4.76%) |        1.58 ms →        1.66 ms   (+5.38%) | 
  │ │   └ sirius::Density::compute_atomic_mag_mom                       |       69.99 μs →       70.75 μs   (+1.09%) |      21   →      22     (+4.76%) |        1.47 ms →        1.56 ms   (+5.90%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.08 ms →        5.54 ms   (+9.14%) |       2   →       2              |       10.15 ms →       11.08 ms   (+9.14%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.83 ms →        4.86 ms   (+0.81%) |       6   →       6              |       28.95 ms →       29.18 ms   (+0.81%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.78 ms →        4.84 ms   (+1.31%) |       6   →       6              |       28.69 ms →       29.07 ms   (+1.31%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.78 ms →        4.84 ms   (+1.28%) |       6   →       6              |       28.69 ms →       29.06 ms   (+1.28%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.99 ms →        5.14 ms   (+3.00%) |       3   →       3              |       14.97 ms →       15.41 ms   (+3.00%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.98 ms →        5.13 ms   (+2.93%) |       3   →       3              |       14.95 ms →       15.38 ms   (+2.93%) | 
  ├ sirius::Periodic_function|inner                                     |        4.79 ms →        4.84 ms   (+1.02%) |       2   →       2              |        9.58 ms →        9.67 ms   (+1.02%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.79 ms →        4.83 ms   (+1.03%) |       2   →       2              |        9.57 ms →        9.67 ms   (+1.03%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.78 ms →        4.83 ms   (+1.03%) |       2   →       2              |        9.57 ms →        9.67 ms   (+1.03%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.99 ms →        5.15 ms   (+3.29%) |       1   →       1              |        4.99 ms →        5.15 ms   (+3.29%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.98 ms →        5.10 ms   (+2.39%) |       1   →       1              |        4.98 ms →        5.10 ms   (+2.39%) | 
  └ sirius::finalize                                                    |      765.64 ms →      787.53 ms   (+2.86%) |       1   →       1              |      765.64 ms →      787.53 ms   (+2.86%) | 
  ====================================================================================================================================================================================================
```
