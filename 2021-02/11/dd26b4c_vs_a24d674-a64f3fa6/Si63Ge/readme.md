# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs dd26b4c3a8b510264c2723458c0ccaf5eeca6037
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |       77.33 s  →       48.71 s   (-37.01%) |       1   →       1              |       77.33 s  →       48.71 s   (-37.01%) | 
  ├ sirius::initialize                                                  |        2.88 s  →        2.88 s    (-0.16%) |       1   →       1              |        2.88 s  →        2.88 s    (-0.16%) | 
  ├ sirius::Simulation_context::initialize                              |        3.75 s  →        3.80 s    (+1.32%) |       1   →       1              |        3.75 s  →        3.80 s    (+1.32%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |      432.98 μs →      268.88 μs  (-37.90%) |       1   →       1              |      432.98 μs →      268.88 μs  (-37.90%) | 
  │ ├ sirius::Unit_cell::initialize                                     |      188.97 ms →      192.59 ms   (+1.91%) |       1   →       1              |      188.97 ms →      192.59 ms   (+1.91%) | 
  │ │ ├ sirius::Atom_type::init                                         |       84.63 ms →       86.09 ms   (+1.72%) |       2   →       2              |      169.26 ms →      172.17 ms   (+1.72%) | 
  │ │ └ sirius::Unit_cell::update                                       |       19.63 ms →       20.27 ms   (+3.25%) |       1   →       1              |       19.63 ms →       20.27 ms   (+3.25%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.93 ms →        3.58 ms   (-9.02%) |       1   →       1              |        3.93 ms →        3.58 ms   (-9.02%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       15.65 ms →       16.63 ms   (+6.31%) |       1   →       1              |       15.65 ms →       16.63 ms   (+6.31%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       15.58 ms →       16.56 ms   (+6.32%) |       1   →       1              |       15.58 ms →       16.56 ms   (+6.32%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.75 ms →        2.98 ms   (+8.40%) |       1   →       1              |        2.75 ms →        2.98 ms   (+8.40%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      512.21 μs →      519.59 μs   (+1.44%) |       1   →       1              |      512.21 μs →      519.59 μs   (+1.44%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       15.62 μs →       16.52 μs   (+5.76%) |       1   →       1              |       15.62 μs →       16.52 μs   (+5.76%) | 
  │ └ sirius::Simulation_context::update                                |        3.37 s  →        3.55 s    (+5.48%) |       1   →       1              |        3.37 s  →        3.55 s    (+5.48%) | 
  │   ├ sirius::Unit_cell::update                                       |        7.04 ms →        7.06 ms   (+0.22%) |       1   →       1              |        7.04 ms →        7.06 ms   (+0.22%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.64 ms →        3.65 ms   (+0.24%) |       1   →       1              |        3.64 ms →        3.65 ms   (+0.24%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.35 ms →        3.37 ms   (+0.59%) |       1   →       1              |        3.35 ms →        3.37 ms   (+0.59%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.30 ms →        3.32 ms   (+0.54%) |       1   →       1              |        3.30 ms →        3.32 ms   (+0.54%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.75 ms →        2.76 ms   (+0.58%) |       1   →       1              |        2.75 ms →        2.76 ms   (+0.58%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      516.99 μs →      511.86 μs   (-0.99%) |       1   →       1              |      516.99 μs →      511.86 μs   (-0.99%) | 
- │   │     └ sirius::Unit_cell_symmetry|mag                            |       13.70 μs →       18.09 μs  (+32.01%) |       1   →       1              |       13.70 μs →       18.09 μs  (+32.01%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      212.53 ms →      213.80 ms   (+0.60%) |       2   →       2              |      425.06 ms →      427.61 ms   (+0.60%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.14 ms →       15.16 ms   (+0.18%) |       2   →       2              |       30.27 ms →       30.33 ms   (+0.18%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.28 ms →       13.28 ms   (-0.00%) |       1   →       1              |       13.28 ms →       13.28 ms   (-0.00%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.83 ms →       56.20 ms   (-1.10%) |       2   →       2              |      113.65 ms →      112.40 ms   (-1.10%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.01 ms →       45.11 ms   (+0.23%) |       2   →       2              |       90.02 ms →       90.22 ms   (+0.23%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.13 ms →       60.22 ms   (+0.16%) |       4   →       4              |      240.50 ms →      240.89 ms   (+0.16%) | 
  │   ├ sddk::Gvec::init                                                |       97.89 ms →       93.24 ms   (-4.75%) |       2   →       2              |      195.77 ms →      186.48 ms   (-4.75%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       71.69 ms →       69.88 ms   (-2.52%) |       2   →       2              |      143.38 ms →      139.76 ms   (-2.52%) | 
+ │   ├ sddk::Gvec_shells                                               |      109.08 ms →       96.47 ms  (-11.57%) |       1   →       1              |      109.08 ms →       96.47 ms  (-11.57%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.67 ms →        1.83 ms   (+9.58%) |       1   →       1              |        1.67 ms →        1.83 ms   (+9.58%) | 
- │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      508.36 ms →      610.23 ms  (+20.04%) |       2   →       2              |        1.02 s  →        1.22 s   (+20.04%) | 
+ ├ sirius::K_point_set::create_k_mesh                                  |      154.26 ms →       83.76 ms  (-45.70%) |       1   →       1              |      154.26 ms →       83.76 ms  (-45.70%) | 
- │ ├ sirius::K_point::K_point                                          |        1.32 μs →        4.13 μs (+212.91%) |       4   →       4              |        5.28 μs →       16.51 μs (+212.91%) | 
+ │ └ sirius::K_point_set::initialize                                   |      154.20 ms →       83.68 ms  (-45.73%) |       1   →       1              |      154.20 ms →       83.68 ms  (-45.73%) | 
  │   └ sirius::K_point::initialize                                     |       30.58 ms →       29.15 ms   (-4.68%) |       1   →       1              |       30.58 ms →       29.15 ms   (-4.68%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       12.23 ms →       11.05 ms   (-9.64%) |       1   →       1              |       12.23 ms →       11.05 ms   (-9.64%) | 
  │     │ └ sddk::Gvec::init                                            |        5.27 ms →        4.90 ms   (-6.92%) |       1   →       1              |        5.27 ms →        4.90 ms   (-6.92%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |       10.60 μs →       10.39 μs   (-2.01%) |       1   →       1              |       10.60 μs →       10.39 μs   (-2.01%) | 
  │     └ sirius::K_point::update                                       |       15.09 ms →       15.20 ms   (+0.77%) |       1   →       1              |       15.09 ms →       15.20 ms   (+0.77%) | 
  │       └ sirius::Beta_projectors                                     |       10.77 ms →       11.24 ms   (+4.29%) |       1   →       1              |       10.77 ms →       11.24 ms   (+4.29%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.88 ms →        9.04 ms   (+1.70%) |       1   →       1              |        8.88 ms →        9.04 ms   (+1.70%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.58 ms →        2.59 ms   (+0.51%) |       2   →       2              |        5.15 ms →        5.18 ms   (+0.51%) | 
  ├ sirius::Potential                                                   |       48.50 ms →       53.19 ms   (+9.67%) |       1   →       1              |       48.50 ms →       53.19 ms   (+9.67%) | 
+ │ ├ sirius::Smooth_periodic_function                                  |        2.89 ms →        2.94 ms   (+1.83%) |       6   →       5    (-16.67%) |       17.34 ms →       14.71 ms  (-15.14%) | 
- │ └ sirius::Potential::update                                         |       30.54 ms →       37.85 ms  (+23.94%) |       1   →       1              |       30.54 ms →       37.85 ms  (+23.94%) | 
- │   └ sirius::Potential::generate_local_potential                     |       30.16 ms →       37.47 ms  (+24.22%) |       1   →       1              |       30.16 ms →       37.47 ms  (+24.22%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       25.05 ms →       27.15 ms   (+8.37%) |       1   →       1              |       25.05 ms →       27.15 ms   (+8.37%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        4.80 ms →        7.21 ms  (+50.22%) |       1   →       1              |        4.80 ms →        7.21 ms  (+50.22%) | 
  ├ sirius::Density                                                     |       40.27 ms →       43.27 ms   (+7.45%) |       1   →       1              |       40.27 ms →       43.27 ms   (+7.45%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.84 ms →        2.82 ms   (-0.77%) |       2   →       2              |        5.68 ms →        5.64 ms   (-0.77%) | 
  │ └ sirius::Density::update                                           |       34.44 ms →       37.47 ms   (+8.77%) |       1   →       1              |       34.44 ms →       37.47 ms   (+8.77%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |       34.13 ms →       37.24 ms   (+9.13%) |       1   →       1              |       34.13 ms →       37.24 ms   (+9.13%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |                        75.60 μs            |                   1              |                        75.60 μs            | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       30.13 ms →       28.61 ms   (-5.04%) |       1   →       1              |       30.13 ms →       28.61 ms   (-5.04%) | 
- │     └ sirius::Smooth_periodic_function::fft_transform               |        3.65 ms →        8.25 ms (+125.80%) |       1   →       1              |        3.65 ms →        8.25 ms (+125.80%) | 
  ├ sirius::Density::initial_density                                    |       58.40 ms →       62.01 ms   (+6.17%) |       1   →       1              |       58.40 ms →       62.01 ms   (+6.17%) | 
  │ ├ sirius::Simulation_context::make_periodic_function                |       28.91 ms →       29.63 ms   (+2.48%) |       1   →       1              |       28.91 ms →       29.63 ms   (+2.48%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        4.98 ms →        6.46 ms  (+29.75%) |       2   →       2              |        9.96 ms →       12.93 ms  (+29.75%) | 
  │ └ sirius::Periodic_function::integrate                              |        5.77 ms →        5.40 ms   (-6.41%) |       1   →       1              |        5.77 ms →        5.40 ms   (-6.41%) | 
  ├ sirius::Potential::generate                                         |      363.20 ms →      356.64 ms   (-1.80%) |       1   →       1              |      363.20 ms →      356.64 ms   (-1.80%) | 
- │ ├ sirius::Potential::poisson                                        |       37.34 ms →       42.30 ms  (+13.29%) |       1   →       1              |       37.34 ms →       42.30 ms  (+13.29%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        2.86 ms →        6.61 ms (+130.68%) |       1   →       1              |        2.86 ms →        6.61 ms (+130.68%) | 
  │ │ └ sirius::Periodic_function|inner                                 |        6.06 ms →        6.32 ms   (+4.22%) |       1   →       1              |        6.06 ms →        6.32 ms   (+4.22%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |        4.83 ms →        4.85 ms   (+0.45%) |       1   →       1              |        4.83 ms →        4.85 ms   (+0.45%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |        4.83 ms →        4.85 ms   (+0.46%) |       1   →       1              |        4.83 ms →        4.85 ms   (+0.46%) | 
  │ ├ sirius::Periodic_function::add                                    |      776.47 μs →      771.96 μs   (-0.58%) |       2   →       2              |        1.55 ms →        1.54 ms   (-0.58%) | 
+ │ ├ sirius::Potential::xc                                             |       50.66 ms →       37.99 ms  (-25.01%) |       1   →       1              |       50.66 ms →       37.99 ms  (-25.01%) | 
+ │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       50.66 ms →       36.79 ms  (-27.38%) |       1   →       1              |       50.66 ms →       36.79 ms  (-27.38%) | 
+ │ │   ├ sirius::Smooth_periodic_function                              |        2.57 ms →        2.18 ms  (-15.25%) |       2   →       1    (-50.00%) |        5.14 ms →        2.18 ms  (-57.62%) | 
  │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        4.76 ms                             |       1                          |        4.76 ms                             | 
  │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                    |                        14.03 ms            |                   2              |                        28.06 ms            | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.74 ms →        3.79 ms   (+1.31%) |       1   →       1              |        3.74 ms →        3.79 ms   (+1.31%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      268.53 ms →      269.63 ms   (+0.41%) |       1   →       1              |      268.53 ms →      269.63 ms   (+0.41%) | 
+ │ └ sirius::Potential::generate_PAW_effective_potential               |      229.00 ns →      139.00 ns  (-39.30%) |       1   →       1              |      229.00 ns →      139.00 ns  (-39.30%) | 
- ├ sirius::Hamiltonian0                                                |        7.53 ms →       12.78 ms  (+69.70%) |       1   →       1              |        7.53 ms →       12.78 ms  (+69.70%) | 
+ │ ├ sirius::Local_operator                                            |        7.04 ms →        5.84 ms  (-17.05%) |       1   →       1              |        7.04 ms →        5.84 ms  (-17.05%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.75 ms →        2.74 ms   (-0.12%) |       1   →       1              |        2.75 ms →        2.74 ms   (-0.12%) | 
+ │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        3.19 ms →        2.38 ms  (-25.40%) |       1   →       1              |        3.19 ms →        2.38 ms  (-25.40%) | 
+ │ ├ sirius::Non_local_operator                                        |      110.54 μs →       68.49 μs  (-38.04%) |       2   →       2              |      221.07 μs →      136.97 μs  (-38.04%) | 
- │ ├ sirius::D_operator::initialize                                    |      111.52 μs →        2.29 ms (+1955.51%) |       1   →       1              |      111.52 μs →        2.29 ms (+1955.51%) | 
- │ └ sirius::Q_operator::initialize                                    |       90.43 μs →        4.44 ms (+4809.45%) |       1   →       1              |       90.43 μs →        4.44 ms (+4809.45%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.30 s  →        1.30 s    (+0.37%) |       1   →       1              |        1.30 s  →        1.30 s    (+0.37%) | 
+ │ ├ sirius::Hamiltonian_k                                             |       53.86 ms →       43.16 ms  (-19.87%) |       1   →       1              |       53.86 ms →       43.16 ms  (-19.87%) | 
+ │ │ ├ sirius::Local_operator::prepare_k                               |      311.41 μs →      219.06 μs  (-29.66%) |       1   →       1              |      311.41 μs →      219.06 μs  (-29.66%) | 
+ │ │ └ sirius::Beta_projectors_base::prepare                           |       53.55 ms →       42.93 ms  (-19.82%) |       1   →       1              |       53.55 ms →       42.93 ms  (-19.82%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.24 s  →        1.26 s    (+1.16%) |       1   →       1              |        1.24 s  →        1.26 s    (+1.16%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       77.86 ms →       82.84 ms   (+6.39%) |       4   →       4              |      311.44 ms →      331.34 ms   (+6.39%) | 
- │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       47.62 ms →       54.37 ms  (+14.19%) |       1   →       1              |       47.62 ms →       54.37 ms  (+14.19%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        7.96 ms →        8.72 ms   (+9.60%) |       1   →       1              |        7.96 ms →        8.72 ms   (+9.60%) | 
+ │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      355.96 ms →      315.42 ms  (-11.39%) |       1   →       1              |      355.96 ms →      315.42 ms  (-11.39%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      249.01 ms →      246.39 ms   (-1.05%) |       1   →       1              |      249.01 ms →      246.39 ms   (-1.05%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        4.41 μs →        3.34 μs  (-24.27%) |       1   →       1              |        4.41 μs →        3.34 μs  (-24.27%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.10 μs →        2.38 μs  (-23.51%) |       1   →       1              |        3.10 μs →        2.38 μs  (-23.51%) | 
- │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      488.00 ns →      728.00 ns  (+49.18%) |       1   →       1              |      488.00 ns →      728.00 ns  (+49.18%) | 
  │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      684.00 ns →      681.00 ns   (-0.44%) |       1   →       1              |      684.00 ns →      681.00 ns   (-0.44%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.20 ms →        3.21 ms   (+0.36%) |       1   →       1              |        3.20 ms →        3.21 ms   (+0.36%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.37 ms →       21.32 ms   (-0.21%) |       1   →       1              |       21.37 ms →       21.32 ms   (-0.21%) | 
+ │ │ │ └ sirius::Non_local_operator::apply                             |       41.17 ms →       22.22 ms  (-46.03%) |       2   →       2              |       82.34 ms →       44.44 ms  (-46.03%) | 
- │ │ ├ sirius::Band::set_subspace_mtrx                                 |        5.36 ms →       14.96 ms (+179.05%) |       2   →       2              |       10.72 ms →       29.91 ms (+179.05%) | 
  │ │ │ ├ sddk::inner                                                   |        5.15 ms                             |       2                          |       10.29 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       26.52 μs                             |       2                          |       53.03 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        14.74 ms            |                   2              |                        29.48 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        92.50 ns            |                   2              |                       185.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        14.59 ms            |                   2              |                        29.18 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                       473.00 ns            |                   2              |                       946.00 ns            | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      234.59 ms →      250.08 ms   (+6.60%) |       1   →       1              |      234.59 ms →      250.08 ms   (+6.60%) | 
  │ │ ├ sddk::transform                                                 |        5.24 ms                             |       1                          |        5.24 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       15.83 μs                             |       1                          |       15.83 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       18.92 μs                             |       1                          |       18.92 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                         2.61 ms            |                   1              |                         2.61 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                         2.61 ms            |                   1              |                         2.61 ms            | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      556.00 ns →      379.00 ns  (-31.83%) |       1   →       1              |      556.00 ns →      379.00 ns  (-31.83%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |       67.36 s  →       38.64 s   (-42.63%) |       1   →       1              |       67.36 s  →       38.64 s   (-42.63%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.42 ms →        2.62 ms   (+7.95%) |      19   →      18     (-5.26%) |       46.05 ms →       47.09 ms   (+2.27%) | 
  │ ├ sirius::Density                                                   |                        56.55 ms            |                   1              |                        56.55 ms            | 
  │ │ ├ sirius::Smooth_periodic_function                                |                         2.81 ms            |                   2              |                         5.63 ms            | 
  │ │ └ sirius::Density::update                                         |                        50.75 ms            |                   1              |                        50.75 ms            | 
  │ │   └ sirius::Density::generate_pseudo_core_charge_density          |                        50.38 ms            |                   1              |                        50.38 ms            | 
  │ │     ├ sirius::rho_core_ri_pseudo|values                           |                       101.21 μs            |                   1              |                       101.21 μs            | 
  │ │     ├ sirius::Simulation_context::make_periodic_function          |                        29.06 ms            |                   1              |                        29.06 ms            | 
  │ │     └ sirius::Smooth_periodic_function::fft_transform             |                        20.88 ms            |                   1              |                        20.88 ms            | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.36 s  →        2.56 s   (-23.74%) |      20   →      15    (-25.00%) |       67.12 s  →       38.39 s   (-42.81%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        5.10 ms →       10.74 ms (+110.42%) |      20   →      15    (-25.00%) |      102.04 ms →      161.03 ms  (+57.81%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        4.43 ms →        3.79 ms  (-14.42%) |      20   →      15    (-25.00%) |       88.62 ms →       56.88 ms  (-35.81%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function                            |      551.28 μs →      492.99 μs  (-10.57%) |      20   →      15    (-25.00%) |       11.03 ms →        7.39 ms  (-32.93%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        2.73 ms →        2.26 ms  (-17.23%) |      20   →      15    (-25.00%) |       54.69 ms →       33.95 ms  (-37.92%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |      182.88 μs →       93.04 μs  (-49.12%) |      40   →      30    (-25.00%) |        7.32 ms →        2.79 ms  (-61.84%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |      129.17 μs →        2.30 ms (+1683.44%) |      20   →      15    (-25.00%) |        2.58 ms →       34.56 ms (+1237.58%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       95.76 μs →        4.39 ms (+4479.42%) |      20   →      15    (-25.00%) |        1.92 ms →       65.78 ms (+3334.56%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.12 s  →        1.29 s   (-39.08%) |      20   →      15    (-25.00%) |       42.42 s  →       19.38 s   (-54.31%) | 
+ │ │ │ ├ sirius::Hamiltonian_k                                         |      218.64 μs →      190.85 μs  (-12.71%) |      20   →      15    (-25.00%) |        4.37 ms →        2.86 ms  (-34.53%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      209.45 μs →      180.53 μs  (-13.81%) |      20   →      15    (-25.00%) |        4.19 ms →        2.71 ms  (-35.36%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        7.13 μs →        5.60 μs  (-21.45%) |      20   →      15    (-25.00%) |      142.66 μs →       84.04 μs  (-41.09%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.97 s  →        1.12 s   (-42.99%) |      20   →      15    (-25.00%) |       39.36 s  →       16.83 s   (-57.24%) | 
+ │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       89.42 ms →       84.77 ms   (-5.20%) |      20   →      15    (-25.00%) |        1.79 s  →        1.27 s   (-28.90%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |       11.27 ms →       10.58 ms   (-6.14%) |     120   →      90    (-25.00%) |        1.35 s  →      951.98 ms  (-29.61%) | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       17.38 ms →       17.45 ms   (+0.41%) |      20   →      15    (-25.00%) |      347.68 ms →      261.82 ms  (-24.69%) | 
+ │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      460.52 μs →      458.37 μs   (-0.47%) |      20   →      15    (-25.00%) |        9.21 ms →        6.88 ms  (-25.35%) | 
+ │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        8.26 ms →        7.87 ms   (-4.76%) |      40   →      30    (-25.00%) |      330.35 ms →      235.96 ms  (-28.57%) | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.85 s  →        1.01 s   (-45.47%) |      20   →      15    (-25.00%) |       37.08 s  →       15.16 s   (-59.11%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       55.15 ms →       73.35 ms  (+33.01%) |     250   →     116    (-53.60%) |       13.79 s  →        8.51 s   (-38.28%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       34.29 ms →       46.58 ms  (+35.82%) |     250   →     116    (-53.60%) |        8.57 s  →        5.40 s   (-36.98%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        2.10 μs →        2.01 μs   (-4.08%) |     250   →     116    (-53.60%) |      524.23 μs →      233.32 μs  (-55.49%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.78 μs →        1.67 μs   (-5.96%) |     250   →     116    (-53.60%) |      444.84 μs →      194.11 μs  (-56.36%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      471.44 ns →      470.56 ns   (-0.19%) |     250   →     116    (-53.60%) |      117.86 μs →       54.58 μs  (-53.69%) | 
+ │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      619.66 ns →      672.43 ns   (+8.52%) |     250   →     116    (-53.60%) |      154.92 μs →       78.00 μs  (-49.65%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.77 ms →        3.02 ms   (+9.23%) |     250   →     116    (-53.60%) |      692.19 ms →      350.83 ms  (-49.32%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.46 ms →        4.45 ms  (+28.39%) |     250   →     116    (-53.60%) |      866.03 ms →      515.92 ms  (-40.43%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        7.30 ms →        9.64 ms  (+32.00%) |     500   →     232    (-53.60%) |        3.65 s  →        2.24 s   (-38.75%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |        8.13 ms →        8.95 ms  (+10.05%) |     250   →     116    (-53.60%) |        2.03 s  →        1.04 s   (-48.94%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        1.07 ms                             |     480                          |      514.19 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       23.01 μs                             |     480                          |       11.04 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                         1.15 ms            |                 217              |                       249.08 ms            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                        90.07 ns            |                 217              |                        19.55 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                       984.40 μs            |                 217              |                       213.62 ms            | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                       232.17 ns            |                 217              |                        50.38 μs            | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      314.55 μs →      473.88 μs  (+50.66%) |     250   →     116    (-53.60%) |       78.64 ms →       54.97 ms  (-30.10%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        2.92 ms →        3.66 ms  (+25.40%) |     250   →     116    (-53.60%) |      729.24 ms →      424.32 ms  (-41.81%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        3.08 ms                             |     230                          |      709.52 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       18.90 μs                             |     230                          |        4.35 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |        7.79 μs                             |     690                          |        5.38 ms                             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                         3.06 ms            |                 101              |                       309.04 ms            | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                         1.02 ms            |                 303              |                       308.80 ms            | 
- │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.96 ms →        2.36 ms  (+20.71%) |     250   →     116    (-53.60%) |      489.49 ms →      274.15 ms  (-43.99%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        1.75 ms                             |     250                          |      437.90 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       24.18 μs                             |     250                          |        6.05 ms                             | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                         2.29 ms            |                 116              |                       265.09 ms            | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                       119.21 ns            |                 116              |                        13.83 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                         2.12 ms            |                 116              |                       245.64 ms            | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                       193.56 ns            |                 116              |                        22.45 μs            | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       79.57 ms →       41.57 ms  (-47.76%) |     250   →     116    (-53.60%) |       19.89 s  →        4.82 s   (-75.76%) | 
+ │ │ │ │   ├ sirius::residuals                                         |        2.84 ms →        2.64 ms   (-7.00%) |     245   →     114    (-53.47%) |      694.82 ms →      300.68 ms  (-56.72%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        1.70 ms                             |     231                          |      392.94 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       15.86 μs                             |     231                          |        3.66 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |       10.76 μs                             |     462                          |        4.97 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                         1.35 ms            |                 101              |                       136.13 ms            | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                       672.41 μs            |                 202              |                       135.83 ms            | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.23 ms →        1.38 ms  (+12.33%) |     231   →     101    (-56.28%) |      284.32 ms →      139.64 ms  (-50.89%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        7.02 ms →        4.49 ms  (-35.93%) |      25   →      47    (+88.00%) |      175.39 ms →      211.26 ms  (+20.45%) | 
  │ │ │ │     ├ sddk::transform                                         |        5.76 ms                             |      30                          |      172.92 ms                             | 
  │ │ │ │     │ ├ sddk::transform|init                                  |       10.57 μs                             |      30                          |      317.04 μs                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       11.78 μs                             |      35                          |      412.27 μs                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                         2.61 ms            |                  79              |                       205.94 ms            | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                         1.85 ms            |                 111              |                       205.79 ms            | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      452.10 ns →      384.27 ns  (-15.00%) |      20   →      15    (-25.00%) |        9.04 μs →        5.76 μs  (-36.25%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       21.54 μs →      873.10 μs (+3953.90%) |      20   →      15    (-25.00%) |      430.75 μs →       13.10 ms (+2940.43%) | 
- │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.49 ms →       65.91 ms (+4325.59%) |      20   →      15    (-25.00%) |       29.79 ms →      988.71 ms (+3219.19%) | 
+ │ │ ├ sirius::Density::generate                                       |      574.47 ms →      565.16 ms   (-1.62%) |      20   →      15    (-25.00%) |       11.49 s  →        8.48 s   (-26.22%) | 
+ │ │ │ ├ sirius::Density::generate_valence                             |      409.13 ms →      406.41 ms   (-0.66%) |      20   →      15    (-25.00%) |        8.18 s  →        6.10 s   (-25.50%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        8.66 μs →        7.30 μs  (-15.69%) |      20   →      15    (-25.00%) |      173.12 μs →      109.47 μs  (-36.77%) | 
+ │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        8.19 μs →        6.42 μs  (-21.70%) |      20   →      15    (-25.00%) |      163.85 μs →       96.23 μs  (-41.27%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       19.44 ms →       41.80 ms (+115.03%) |      20   →      15    (-25.00%) |      388.77 ms →      626.98 ms  (+61.27%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.73 μs →        8.79 μs  (+13.75%) |      20   →      15    (-25.00%) |      154.54 μs →      131.84 μs  (-14.68%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        3.30 ms →        3.34 ms   (+1.24%) |      20   →      15    (-25.00%) |       65.97 ms →       50.09 ms  (-24.07%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       15.08 ms →       17.31 ms  (+14.74%) |      20   →      15    (-25.00%) |      301.64 ms →      259.59 ms  (-13.94%) | 
+ │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      836.90 ns →      708.53 ns  (-15.34%) |      20   →      15    (-25.00%) |       16.74 μs →       10.63 μs  (-36.50%) | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      125.85 ms →       90.98 ms  (-27.71%) |      20   →      15    (-25.00%) |        2.52 s  →        1.36 s   (-45.78%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.95 ms →        2.10 ms   (+7.82%) |      20   →      15    (-25.00%) |       38.91 ms →       31.47 ms  (-19.13%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |      225.98 ms →      223.49 ms   (-1.11%) |      20   →      15    (-25.00%) |        4.52 s  →        3.35 s   (-25.83%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |      225.76 ms →      223.26 ms   (-1.11%) |      20   →      15    (-25.00%) |        4.52 s  →        3.35 s   (-25.83%) | 
+ │ │ │ ├ sirius::Field4D::symmetrize                                   |      136.97 ms →      130.83 ms   (-4.48%) |      20   →      15    (-25.00%) |        2.74 s  →        1.96 s   (-28.36%) | 
+ │ │ │ │ └ sirius::symmetrize_function|fpw                             |      136.96 ms →      130.83 ms   (-4.48%) |      20   →      15    (-25.00%) |        2.74 s  →        1.96 s   (-28.36%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       48.43 ms →       51.70 ms   (+6.76%) |      20   →      15    (-25.00%) |      968.56 ms →      775.52 ms  (-19.93%) | 
+ │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       72.42 ms →       65.55 ms   (-9.48%) |      20   →      15    (-25.00%) |        1.45 s  →      983.32 ms  (-32.11%) | 
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       15.48 ms →       12.90 ms  (-16.65%) |      20   →      15    (-25.00%) |      309.59 ms →      193.52 ms  (-37.49%) | 
+ │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.85 ms →       23.76 ms   (-0.40%) |      20   →      15    (-25.00%) |      477.08 ms →      356.37 ms  (-25.30%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        4.52 ms →        4.14 ms   (-8.31%) |      20   →      15    (-25.00%) |       90.35 ms →       62.13 ms  (-31.23%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |                         5.00 ms            |                 135              |                       675.41 ms            | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |                         4.77 ms            |                 135              |                       643.82 ms            | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |                         4.77 ms            |                 135              |                       643.72 ms            | 
+ │ │ ├ sirius::Density::mix                                            |      136.66 ms →       74.44 ms  (-45.52%) |      20   →      15    (-25.00%) |        2.73 s  →        1.12 s   (-59.14%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      831.83 μs →      972.00 μs  (+16.85%) |      20   →      15    (-25.00%) |       16.64 ms →       14.58 ms  (-12.36%) | 
+ │ │ │ ├ sirius::Periodic_function|inner                               |        5.06 ms →        4.57 ms   (-9.73%) |     244   →     169    (-30.74%) |        1.23 s  →      771.99 ms  (-37.48%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner_local                       |        5.01 ms →        4.55 ms   (-9.15%) |     244   →     169    (-30.74%) |        1.22 s  →      768.53 ms  (-37.08%) | 
+ │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        5.00 ms →        4.55 ms   (-9.15%) |     244   →     169    (-30.74%) |        1.22 s  →      768.42 ms  (-37.08%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        5.40 ms →        5.46 ms   (+0.97%) |      20   →      15    (-25.00%) |      108.08 ms →       81.85 ms  (-24.27%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        4.70 ms →        4.52 ms   (-3.82%) |      20   →      15    (-25.00%) |       93.97 ms →       67.78 ms  (-27.87%) | 
+ │ │ ├ sirius::Potential::generate                                     |      356.68 ms →      354.13 ms   (-0.72%) |      20   →      15    (-25.00%) |        7.13 s  →        5.31 s   (-25.54%) | 
- │ │ │ ├ sirius::Potential::poisson                                    |       37.65 ms →       43.34 ms  (+15.10%) |      20   →      15    (-25.00%) |      753.07 ms →      650.11 ms  (-13.67%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        3.20 ms →        7.89 ms (+146.72%) |      20   →      15    (-25.00%) |       63.96 ms →      118.34 ms  (+85.04%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner                             |        6.10 ms →        6.15 ms   (+0.85%) |      20   →      15    (-25.00%) |      121.92 ms →       92.22 ms  (-24.36%) | 
+ │ │ │ │   └ sirius::Periodic_function|inner_local                     |        4.84 ms →        4.87 ms   (+0.53%) |      20   →      15    (-25.00%) |       96.85 ms →       73.02 ms  (-24.60%) | 
+ │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |        4.84 ms →        4.87 ms   (+0.53%) |      20   →      15    (-25.00%) |       96.83 ms →       73.01 ms  (-24.60%) | 
+ │ │ │ ├ sirius::Periodic_function::add                                |      760.18 μs →      771.45 μs   (+1.48%) |      40   →      30    (-25.00%) |       30.41 ms →       23.14 ms  (-23.89%) | 
+ │ │ │ ├ sirius::Potential::xc                                         |       43.27 ms →       35.19 ms  (-18.67%) |      20   →      15    (-25.00%) |      865.40 ms →      527.86 ms  (-39.00%) | 
+ │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       43.27 ms →       33.99 ms  (-21.43%) |      20   →      15    (-25.00%) |      865.35 ms →      509.90 ms  (-41.08%) | 
+ │ │ │ │   ├ sirius::Smooth_periodic_function                          |      649.10 μs →      655.06 μs   (+0.92%) |      40   →      15    (-62.50%) |       25.96 ms →        9.83 ms  (-62.16%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |        4.21 ms                             |      20                          |       84.11 ms                             | 
  │ │ │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                |                        13.62 ms            |                  30              |                       408.61 ms            | 
+ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.84 ms →        3.73 ms   (-2.95%) |      20   →      15    (-25.00%) |       76.80 ms →       55.90 ms  (-27.21%) | 
+ │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.98 ms →      268.88 ms   (-0.04%) |      20   →      15    (-25.00%) |        5.38 s  →        4.03 s   (-25.03%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      209.40 ns →      157.33 ns  (-24.86%) |      20   →      15    (-25.00%) |        4.19 μs →        2.36 μs  (-43.65%) | 
+ │ │ ├ sirius::Field4D::symmetrize                                     |      104.62 ms →       91.94 ms  (-12.12%) |      20   →      15    (-25.00%) |        2.09 s  →        1.38 s   (-34.09%) | 
+ │ │ │ └ sirius::symmetrize_function|fpw                               |      104.61 ms →       91.93 ms  (-12.13%) |      20   →      15    (-25.00%) |        2.09 s  →        1.38 s   (-34.09%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       16.25 ms →       13.36 ms  (-17.80%) |      20   →      15    (-25.00%) |      324.99 ms →      200.37 ms  (-38.35%) | 
+ │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       72.27 ms →       65.08 ms   (-9.95%) |      20   →      15    (-25.00%) |        1.45 s  →      976.20 ms  (-32.46%) | 
+ │ │ │   └ sddk::Gvec_shells::remap_backward                           |       15.47 ms →       12.86 ms  (-16.91%) |      20   →      15    (-25.00%) |      309.43 ms →      192.83 ms  (-37.68%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.78 ms →        3.46 ms   (-8.51%) |      20   →      15    (-25.00%) |       75.69 ms →       51.94 ms  (-31.38%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.77 ms                             |     140                          |      668.45 ms                             | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.76 ms                             |     140                          |      666.37 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.76 ms                             |     140                          |      666.25 ms                             | 
+ │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.60 ms →        4.77 ms   (+3.76%) |      60   →      45    (-25.00%) |      275.91 ms →      214.70 ms  (-22.18%) | 
+ │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.54 ms →        4.77 ms   (+4.88%) |      60   →      45    (-25.00%) |      272.61 ms →      214.44 ms  (-21.34%) | 
+ │ │ ├ sirius::Periodic_function::integrate                            |        4.56 ms →        4.58 ms   (+0.39%) |      20   →      15    (-25.00%) |       91.22 ms →       68.68 ms  (-24.71%) | 
- │ │ └ sirius::Density::get_magnetisation                              |       73.33 μs →       25.55 ms (+34743.06%) |      20   →      15    (-25.00%) |        1.47 ms →      383.25 ms (+26032.29%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |       68.35 μs →       25.54 ms (+37268.14%) |      20   →      15    (-25.00%) |        1.37 ms →      383.11 ms (+27926.10%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.56 ms →        5.68 ms   (+2.20%) |       2   →       2              |       11.11 ms →       11.36 ms   (+2.20%) | 
  │ ├ sirius::Periodic_function|inner                                   |        4.74 ms →        4.73 ms   (-0.23%) |       6   →       6              |       28.46 ms →       28.39 ms   (-0.23%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |        4.74 ms →        4.72 ms   (-0.38%) |       6   →       6              |       28.43 ms →       28.32 ms   (-0.38%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        4.74 ms →        4.72 ms   (-0.38%) |       6   →       6              |       28.43 ms →       28.32 ms   (-0.38%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        4.56 ms →        4.74 ms   (+3.87%) |       3   →       3              |       13.68 ms →       14.21 ms   (+3.87%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.51 ms →        4.73 ms   (+4.84%) |       3   →       3              |       13.53 ms →       14.19 ms   (+4.84%) | 
  ├ sirius::Periodic_function|inner                                     |        4.76 ms →        4.73 ms   (-0.66%) |       2   →       2              |        9.52 ms →        9.46 ms   (-0.66%) | 
  │ └ sirius::Periodic_function|inner_local                             |        4.76 ms →        4.72 ms   (-0.79%) |       2   →       2              |        9.51 ms →        9.44 ms   (-0.79%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.76 ms →        4.72 ms   (-0.79%) |       2   →       2              |        9.51 ms →        9.44 ms   (-0.79%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.53 ms →        4.73 ms   (+4.33%) |       1   →       1              |        4.53 ms →        4.73 ms   (+4.33%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.53 ms →        4.72 ms   (+4.39%) |       1   →       1              |        4.53 ms →        4.72 ms   (+4.39%) | 
+ └ sirius::finalize                                                    |      927.98 ms →      425.19 ms  (-54.18%) |       1   →       1              |      927.98 ms →      425.19 ms  (-54.18%) | 
  ====================================================================================================================================================================================================
```
