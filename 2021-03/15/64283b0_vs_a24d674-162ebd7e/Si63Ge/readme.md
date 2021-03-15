# Benchmark a24d674330b97675090853be47ef2269f1f7185e vs 64283b0bdde21ce92493e897e38c4105358cbbe3
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
+ sirius                                                                |       77.30 s  →       47.30 s   (-38.81%) |       1   →       1              |       77.30 s  →       47.30 s   (-38.81%) | 
  ├ sirius::initialize                                                  |        2.84 s  →        2.92 s    (+2.66%) |       1   →       1              |        2.84 s  →        2.92 s    (+2.66%) | 
  ├ sirius::Simulation_context::initialize                              |        3.60 s  →        3.73 s    (+3.68%) |       1   →       1              |        3.60 s  →        3.73 s    (+3.68%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |       31.77 ms →      390.99 μs  (-98.77%) |       1   →       1              |       31.77 ms →      390.99 μs  (-98.77%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      126.96 ms →      163.49 ms  (+28.77%) |       1   →       1              |      126.96 ms →      163.49 ms  (+28.77%) | 
- │ │ ├ sirius::Atom_type::init                                         |       54.22 ms →       72.28 ms  (+33.30%) |       2   →       2              |      108.45 ms →      144.56 ms  (+33.30%) | 
  │ │ └ sirius::Unit_cell::update                                       |       18.42 ms →       18.76 ms   (+1.87%) |       1   →       1              |       18.42 ms →       18.76 ms   (+1.87%) | 
+ │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        5.01 ms →        3.59 ms  (-28.41%) |       1   →       1              |        5.01 ms →        3.59 ms  (-28.41%) | 
- │ │   └ sirius::Unit_cell::get_symmetry                               |       13.34 ms →       15.10 ms  (+13.23%) |       1   →       1              |       13.34 ms →       15.10 ms  (+13.23%) | 
- │ │     └ sirius::Unit_cell_symmetry                                  |       13.26 ms →       15.03 ms  (+13.34%) |       1   →       1              |       13.26 ms →       15.03 ms  (+13.34%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        2.71 ms →        2.69 ms   (-0.57%) |       1   →       1              |        2.71 ms →        2.69 ms   (-0.57%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |      509.43 μs →      520.67 μs   (+2.21%) |       1   →       1              |      509.43 μs →      520.67 μs   (+2.21%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |       17.06 μs →       15.90 μs   (-6.80%) |       1   →       1              |       17.06 μs →       15.90 μs   (-6.80%) | 
  │ └ sirius::Simulation_context::update                                |        3.24 s  →        3.37 s    (+4.03%) |       1   →       1              |        3.24 s  →        3.37 s    (+4.03%) | 
  │   ├ sirius::Unit_cell::update                                       |        6.75 ms →        6.72 ms   (-0.34%) |       1   →       1              |        6.75 ms →        6.72 ms   (-0.34%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        3.43 ms →        3.44 ms   (+0.44%) |       1   →       1              |        3.43 ms →        3.44 ms   (+0.44%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        3.27 ms →        3.22 ms   (-1.69%) |       1   →       1              |        3.27 ms →        3.22 ms   (-1.69%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        3.23 ms →        3.16 ms   (-2.09%) |       1   →       1              |        3.23 ms →        3.16 ms   (-2.09%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        2.67 ms →        2.64 ms   (-1.36%) |       1   →       1              |        2.67 ms →        2.64 ms   (-1.36%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |      518.99 μs →      489.55 μs   (-5.67%) |       1   →       1              |      518.99 μs →      489.55 μs   (-5.67%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |       13.96 μs →       13.55 μs   (-2.94%) |       1   →       1              |       13.96 μs →       13.55 μs   (-2.94%) | 
  │   ├ sirius::Radial_integrals|aug                                    |      213.59 ms →      213.29 ms   (-0.14%) |       2   →       2              |      427.19 ms →      426.59 ms   (-0.14%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |       15.16 ms →       15.15 ms   (-0.07%) |       2   →       2              |       30.32 ms →       30.30 ms   (-0.07%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |       13.30 ms →       13.25 ms   (-0.36%) |       1   →       1              |       13.30 ms →       13.25 ms   (-0.36%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       56.41 ms →       56.67 ms   (+0.45%) |       2   →       2              |      112.83 ms →      113.34 ms   (+0.45%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       45.34 ms →       44.93 ms   (-0.90%) |       2   →       2              |       90.68 ms →       89.87 ms   (-0.90%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       60.22 ms →       59.86 ms   (-0.60%) |       4   →       4              |      240.88 ms →      239.44 ms   (-0.60%) | 
  │   ├ sddk::Gvec::init                                                |       94.58 ms →       96.36 ms   (+1.88%) |       2   →       2              |      189.16 ms →      192.72 ms   (+1.88%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |       70.83 ms →       70.27 ms   (-0.79%) |       2   →       2              |      141.66 ms →      140.55 ms   (-0.79%) | 
  │   ├ sddk::Gvec_shells                                               |       95.25 ms →       99.73 ms   (+4.70%) |       1   →       1              |       95.25 ms →       99.73 ms   (+4.70%) | 
- │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.70 ms →        1.96 ms  (+15.31%) |       1   →       1              |        1.70 ms →        1.96 ms  (+15.31%) | 
- │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      458.41 ms →      515.93 ms  (+12.55%) |       2   →       2              |      916.83 ms →        1.03 s   (+12.55%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |      149.82 ms →      149.41 ms   (-0.28%) |       1   →       1              |      149.82 ms →      149.41 ms   (-0.28%) | 
- │ ├ sirius::K_point::K_point                                          |        1.39 μs →        4.56 μs (+229.05%) |       4   →       4              |        5.55 μs →       18.26 μs (+229.05%) | 
  │ └ sirius::K_point_set::initialize                                   |      149.76 ms →      149.31 ms   (-0.30%) |       1   →       1              |      149.76 ms →      149.31 ms   (-0.30%) | 
  │   └ sirius::K_point::initialize                                     |       28.57 ms →       29.12 ms   (+1.95%) |       1   →       1              |       28.57 ms →       29.12 ms   (+1.95%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       11.58 ms →       11.28 ms   (-2.54%) |       1   →       1              |       11.58 ms →       11.28 ms   (-2.54%) | 
  │     │ └ sddk::Gvec::init                                            |        4.87 ms →        5.02 ms   (+3.15%) |       1   →       1              |        4.87 ms →        5.02 ms   (+3.15%) | 
  │     ├ sddk::matrix_storage::matrix_storage                          |        6.76 μs                             |       1                          |        6.76 μs                             | 
  │     └ sirius::K_point::update                                       |       14.18 ms →       14.92 ms   (+5.25%) |       1   →       1              |       14.18 ms →       14.92 ms   (+5.25%) | 
  │       └ sirius::Beta_projectors                                     |       10.26 ms →       10.91 ms   (+6.35%) |       1   →       1              |       10.26 ms →       10.91 ms   (+6.35%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        8.31 ms →        8.96 ms   (+7.89%) |       1   →       1              |        8.31 ms →        8.96 ms   (+7.89%) | 
  ├ sirius::Smooth_periodic_function                                    |        2.57 ms                             |       2                          |        5.14 ms                             | 
  ├ sirius::Potential                                                   |       56.79 ms →       53.17 ms   (-6.38%) |       1   →       1              |       56.79 ms →       53.17 ms   (-6.38%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.89 ms                             |       6                          |       17.35 ms                             | 
  │ └ sirius::Potential::update                                         |       39.03 ms →       38.01 ms   (-2.61%) |       1   →       1              |       39.03 ms →       38.01 ms   (-2.61%) | 
  │   └ sirius::Potential::generate_local_potential                     |       38.64 ms →       37.63 ms   (-2.62%) |       1   →       1              |       38.64 ms →       37.63 ms   (-2.62%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |       24.91 ms →       26.62 ms   (+6.87%) |       1   →       1              |       24.91 ms →       26.62 ms   (+6.87%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |       13.44 ms →        7.68 ms  (-42.86%) |       1   →       1              |       13.44 ms →        7.68 ms  (-42.86%) | 
  ├ sirius::Density                                                     |       44.13 ms →       39.81 ms   (-9.77%) |       1   →       1              |       44.13 ms →       39.81 ms   (-9.77%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.81 ms                             |       2                          |        5.62 ms                             | 
+ │ └ sirius::Density::update                                           |       38.36 ms →       33.97 ms  (-11.44%) |       1   →       1              |       38.36 ms →       33.97 ms  (-11.44%) | 
+ │   └ sirius::Density::generate_pseudo_core_charge_density            |       38.15 ms →       33.74 ms  (-11.56%) |       1   →       1              |       38.15 ms →       33.74 ms  (-11.56%) | 
+ │     ├ sirius::Simulation_context::make_periodic_function            |       30.16 ms →       26.82 ms  (-11.08%) |       1   →       1              |       30.16 ms →       26.82 ms  (-11.08%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        7.70 ms →        6.50 ms  (-15.66%) |       1   →       1              |        7.70 ms →        6.50 ms  (-15.66%) | 
  ├ sirius::Density::initial_density                                    |       61.55 ms →       56.13 ms   (-8.80%) |       1   →       1              |       61.55 ms →       56.13 ms   (-8.80%) | 
+ │ ├ sirius::Simulation_context::make_periodic_function                |       29.58 ms →       26.34 ms  (-10.95%) |       1   →       1              |       29.58 ms →       26.34 ms  (-10.95%) | 
+ │ ├ sirius::Smooth_periodic_function::fft_transform                   |        6.30 ms →        5.57 ms  (-11.63%) |       2   →       2              |       12.61 ms →       11.14 ms  (-11.63%) | 
+ │ └ sirius::Periodic_function::integrate                              |        5.70 ms →        4.93 ms  (-13.53%) |       1   →       1              |        5.70 ms →        4.93 ms  (-13.53%) | 
  ├ sirius::Potential::generate                                         |      379.58 ms →      369.10 ms   (-2.76%) |       1   →       1              |      379.58 ms →      369.10 ms   (-2.76%) | 
  │ ├ sirius::Potential::poisson                                        |       42.49 ms →       43.38 ms   (+2.08%) |       1   →       1              |       42.49 ms →       43.38 ms   (+2.08%) | 
- │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        7.13 ms →       11.36 ms  (+59.33%) |       1   →       1              |        7.13 ms →       11.36 ms  (+59.33%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        6.09 ms                             |       1                          |        6.09 ms                             | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.83 ms                             |       1                          |        4.83 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.83 ms                             |       1                          |        4.83 ms                             | 
  │ │ └ sirius::inner                                                   |                         5.87 ms            |                   1              |                         5.87 ms            | 
+ │ ├ sirius::Periodic_function::add                                    |      771.60 μs →      693.69 μs  (-10.10%) |       2   →       2              |        1.54 ms →        1.39 ms  (-10.10%) | 
+ │ ├ sirius::Potential::xc                                             |       62.00 ms →       49.28 ms  (-20.51%) |       1   →       1              |       62.00 ms →       49.28 ms  (-20.51%) | 
+ │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       61.99 ms →       48.10 ms  (-22.41%) |       1   →       1              |       61.99 ms →       48.10 ms  (-22.41%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        2.54 ms                             |       2                          |        5.08 ms                             | 
  │ │   ├ sirius::Smooth_periodic_function::fft_transform               |        4.99 ms                             |       1                          |        4.99 ms                             | 
  │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                    |                        20.01 ms            |                   2              |                        40.02 ms            | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        3.29 ms →        3.53 ms   (+7.26%) |       1   →       1              |        3.29 ms →        3.53 ms   (+7.26%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |      268.88 ms →      268.65 ms   (-0.08%) |       1   →       1              |      268.88 ms →      268.65 ms   (-0.08%) | 
+ │ └ sirius::Potential::generate_PAW_effective_potential               |      240.00 ns →      191.00 ns  (-20.42%) |       1   →       1              |      240.00 ns →      191.00 ns  (-20.42%) | 
- ├ sirius::Hamiltonian0                                                |        6.34 ms →       13.66 ms (+115.46%) |       1   →       1              |        6.34 ms →       13.66 ms (+115.46%) | 
- │ ├ sirius::Local_operator                                            |        5.86 ms →        6.98 ms  (+19.18%) |       1   →       1              |        5.86 ms →        6.98 ms  (+19.18%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        2.75 ms                             |       1                          |        2.75 ms                             | 
- │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.35 ms →        3.20 ms  (+36.00%) |       1   →       1              |        2.35 ms →        3.20 ms  (+36.00%) | 
  │ ├ sirius::Non_local_operator                                        |       81.55 μs →       74.29 μs   (-8.90%) |       2   →       2              |      163.09 μs →      148.58 μs   (-8.90%) | 
- │ ├ sirius::D_operator::initialize                                    |      134.88 μs →        2.18 ms (+1514.08%) |       1   →       1              |      134.88 μs →        2.18 ms (+1514.08%) | 
- │ └ sirius::Q_operator::initialize                                    |      108.48 μs →        4.27 ms (+3836.92%) |       1   →       1              |      108.48 μs →        4.27 ms (+3836.92%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.28 s  →        1.28 s    (+0.29%) |       1   →       1              |        1.28 s  →        1.28 s    (+0.29%) | 
- │ ├ sirius::Hamiltonian_k                                             |       46.99 ms →       54.96 ms  (+16.98%) |       1   →       1              |       46.99 ms →       54.96 ms  (+16.98%) | 
+ │ │ ├ sirius::Local_operator::prepare_k                               |      326.62 μs →      211.25 μs  (-35.32%) |       1   →       1              |      326.62 μs →      211.25 μs  (-35.32%) | 
- │ │ └ sirius::Beta_projectors_base::prepare                           |       46.65 ms →       54.75 ms  (+17.34%) |       1   →       1              |       46.65 ms →       54.75 ms  (+17.34%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.23 s  →        1.23 s    (-0.40%) |       1   →       1              |        1.23 s  →        1.23 s    (-0.40%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |       77.98 ms                             |       4                          |      311.93 ms                             | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       44.08 ms →       46.85 ms   (+6.28%) |       1   →       1              |       44.08 ms →       46.85 ms   (+6.28%) | 
+ │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |        8.86 ms →        7.83 ms  (-11.63%) |       1   →       1              |        8.86 ms →        7.83 ms  (-11.63%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      315.89 ms →      336.47 ms   (+6.51%) |       1   →       1              |      315.89 ms →      336.47 ms   (+6.51%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      245.59 ms →      248.45 ms   (+1.16%) |       1   →       1              |      245.59 ms →      248.45 ms   (+1.16%) | 
  │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.84 μs →        3.72 μs   (-3.15%) |       1   →       1              |        3.84 μs →        3.72 μs   (-3.15%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.96 μs                             |       1                          |        2.96 μs                             | 
  │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      410.00 ns                             |       1                          |      410.00 ns                             | 
+ │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      714.00 ns →      517.00 ns  (-27.59%) |       1   →       1              |      714.00 ns →      517.00 ns  (-27.59%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        3.26 ms →        3.21 ms   (-1.52%) |       1   →       1              |        3.26 ms →        3.21 ms   (-1.52%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |       21.29 ms →       21.29 ms   (-0.03%) |       1   →       1              |       21.29 ms →       21.29 ms   (-0.03%) | 
- │ │ │ └ sirius::Non_local_operator::apply                             |       22.85 ms →       31.74 ms  (+38.87%) |       2   →       2              |       45.71 ms →       63.47 ms  (+38.87%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       14.70 ms →       14.58 ms   (-0.84%) |       2   →       2              |       29.40 ms →       29.15 ms   (-0.84%) | 
  │ │ │ ├ sddk::inner                                                   |       14.49 ms                             |       2                          |       28.98 ms                             | 
  │ │ │ │ └ sddk::inner|local                                           |       24.33 μs                             |       2                          |       48.66 μs                             | 
  │ │ │ └ sddk::wf_inner                                                |                        14.36 ms            |                   2              |                        28.71 ms            | 
  │ │ │   ├ sddk::wf_inner|scale                                        |                        72.00 ns            |                   2              |                       144.00 ns            | 
  │ │ │   ├ sddk::wf_inner|pw                                           |                        14.20 ms            |                   2              |                        28.41 ms            | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |                       352.50 ns            |                   2              |                       705.00 ns            | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |      247.79 ms →      231.19 ms   (-6.70%) |       1   →       1              |      247.79 ms →      231.19 ms   (-6.70%) | 
  │ │ ├ sddk::transform                                                 |        2.81 ms                             |       1                          |        2.81 ms                             | 
  │ │ │ ├ sddk::transform|init                                          |       17.82 μs                             |       1                          |       17.82 μs                             | 
  │ │ │ └ sddk::transform|local                                         |       18.74 μs                             |       1                          |       18.74 μs                             | 
  │ │ └ sddk::wf_trans                                                  |                         4.95 ms            |                   1              |                         4.95 ms            | 
  │ │   └ sddk::wf_trans|pw                                             |                         4.94 ms            |                   1              |                         4.94 ms            | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      459.00 ns →      361.00 ns  (-21.35%) |       1   →       1              |      459.00 ns →      361.00 ns  (-21.35%) | 
+ ├ sirius::DFT_ground_state::scf_loop                                  |       67.56 s  →       37.59 s   (-44.36%) |       1   →       1              |       67.56 s  →       37.59 s   (-44.36%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        2.43 ms                             |      19                          |       46.08 ms                             | 
  │ ├ sirius::Density                                                   |                        50.72 ms            |                   1              |                        50.72 ms            | 
  │ │ └ sirius::Density::update                                         |                        44.95 ms            |                   1              |                        44.95 ms            | 
  │ │   └ sirius::Density::generate_pseudo_core_charge_density          |                        44.73 ms            |                   1              |                        44.73 ms            | 
  │ │     ├ sirius::Simulation_context::make_periodic_function          |                        26.82 ms            |                   1              |                        26.82 ms            | 
  │ │     └ sirius::Smooth_periodic_function::fft_transform             |                         7.09 ms            |                   1              |                         7.09 ms            | 
+ │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        3.37 s  →        2.49 s   (-26.06%) |      20   →      15    (-25.00%) |       67.33 s  →       37.34 s   (-44.55%) | 
- │ │ ├ sirius::Hamiltonian0                                            |        5.54 ms →       10.68 ms  (+92.90%) |      20   →      15    (-25.00%) |      110.70 ms →      160.16 ms  (+44.68%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        4.78 ms →        3.95 ms  (-17.26%) |      20   →      15    (-25.00%) |       95.59 ms →       59.32 ms  (-37.95%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |      529.76 μs                             |      20                          |       10.60 ms                             | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.13 ms →        2.40 ms  (-23.43%) |      20   →      15    (-25.00%) |       62.57 ms →       35.94 ms  (-42.57%) | 
+ │ │ │ ├ sirius::Non_local_operator                                    |      230.14 μs →       76.69 μs  (-66.67%) |      40   →      30    (-25.00%) |        9.21 ms →        2.30 ms  (-75.01%) | 
- │ │ │ ├ sirius::D_operator::initialize                                |      118.26 μs →        2.20 ms (+1759.68%) |      20   →      15    (-25.00%) |        2.37 ms →       32.99 ms (+1294.76%) | 
- │ │ │ └ sirius::Q_operator::initialize                                |       97.49 μs →        4.29 ms (+4305.02%) |      20   →      15    (-25.00%) |        1.95 ms →       64.42 ms (+3203.76%) | 
+ │ │ ├ sirius::Band::solve                                             |        2.12 s  →        1.29 s   (-39.19%) |      20   →      15    (-25.00%) |       42.46 s  →       19.36 s   (-54.40%) | 
+ │ │ │ ├ sirius::Hamiltonian_k                                         |      222.90 μs →      183.81 μs  (-17.54%) |      20   →      15    (-25.00%) |        4.46 ms →        2.76 ms  (-38.15%) | 
+ │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      214.76 μs →      173.96 μs  (-19.00%) |      20   →      15    (-25.00%) |        4.30 ms →        2.61 ms  (-39.25%) | 
+ │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        6.31 μs →        5.36 μs  (-14.97%) |      20   →      15    (-25.00%) |      126.17 μs →       80.46 μs  (-36.23%) | 
+ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        1.96 s  →        1.12 s   (-42.93%) |      20   →      15    (-25.00%) |       39.28 s  →       16.81 s   (-57.20%) | 
  │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       96.47 ms                             |      20                          |        1.93 s                              | 
  │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |       11.58 ms                             |     120                          |        1.39 s                              | 
+ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |       17.73 ms →       18.47 ms   (+4.18%) |      20   →      15    (-25.00%) |      354.61 ms →      277.07 ms  (-21.87%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      460.07 μs                             |      20                          |        9.20 ms                             | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        8.43 ms                             |      40                          |      337.15 ms                             | 
+ │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        1.84 s  →        1.01 s   (-45.28%) |      20   →      15    (-25.00%) |       36.86 s  →       15.13 s   (-58.96%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |       61.04 ms →       73.95 ms  (+21.15%) |     250   →     116    (-53.60%) |       15.26 s  →        8.58 s   (-43.79%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       35.84 ms →       46.63 ms  (+30.12%) |     250   →     116    (-53.60%) |        8.96 s  →        5.41 s   (-39.62%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.86 μs →        1.83 μs   (-1.58%) |     250   →     116    (-53.60%) |      464.11 μs →      211.93 μs  (-54.34%) | 
  │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.58 μs                             |     250                          |      394.51 μs                             | 
  │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      389.80 ns                             |     250                          |       97.45 μs                             | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      426.71 ns →      596.21 ns  (+39.72%) |     250   →     116    (-53.60%) |      106.68 μs →       69.16 μs  (-35.17%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        2.62 ms →        3.06 ms  (+16.68%) |     250   →     116    (-53.60%) |      655.59 ms →      354.92 ms  (-45.86%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |        3.43 ms →        4.52 ms  (+31.89%) |     250   →     116    (-53.60%) |      856.95 ms →      524.42 ms  (-38.80%) | 
+ │ │ │ │   │ └ sirius::Non_local_operator::apply                       |        9.57 ms →        9.86 ms   (+3.02%) |     500   →     232    (-53.60%) |        4.78 s  →        2.29 s   (-52.20%) | 
+ │ │ │ │   ├ sddk::orthogonalize                                       |        8.84 ms →        9.54 ms   (+7.88%) |     250   →     116    (-53.60%) |        2.21 s  →        1.11 s   (-49.95%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        1.27 ms                             |     480                          |      607.82 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       20.90 μs                             |     480                          |       10.03 ms                             | 
  │ │ │ │   │ ├ sddk::wf_inner                                          |                         1.33 ms            |                 217              |                       288.34 ms            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |                       117.49 ns            |                 217              |                        25.50 μs            | 
  │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |                         1.16 ms            |                 217              |                       251.47 ms            | 
  │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |                       284.21 ns            |                 217              |                        61.67 μs            | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      315.83 μs →      491.76 μs  (+55.70%) |     250   →     116    (-53.60%) |       78.96 ms →       57.04 ms  (-27.75%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |        3.09 ms →        4.06 ms  (+31.68%) |     250   →     116    (-53.60%) |      771.70 ms →      471.52 ms  (-38.90%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        3.26 ms                             |     230                          |      750.67 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       16.57 μs                             |     230                          |        3.81 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |        6.98 μs                             |     690                          |        4.82 ms                             | 
  │ │ │ │   │ └ sddk::wf_trans                                          |                         2.86 ms            |                 101              |                       288.91 ms            | 
  │ │ │ │   │   └ sddk::wf_trans|pw                                     |                       952.67 μs            |                 303              |                       288.66 ms            | 
+ │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |        1.99 ms →        1.89 ms   (-4.72%) |     250   →     116    (-53.60%) |      497.21 ms →      219.81 ms  (-55.79%) | 
  │ │ │ │   │ ├ sddk::inner                                             |        1.79 ms                             |     250                          |      446.89 ms                             | 
  │ │ │ │   │ │ └ sddk::inner|local                                     |       22.39 μs                             |     250                          |        5.60 ms                             | 
  │ │ │ │   │ └ sddk::wf_inner                                          |                         1.83 ms            |                 116              |                       212.07 ms            | 
  │ │ │ │   │   ├ sddk::wf_inner|scale                                  |                        77.66 ns            |                 116              |                         9.01 μs            | 
  │ │ │ │   │   ├ sddk::wf_inner|pw                                     |                         1.66 ms            |                 116              |                       192.02 ms            | 
  │ │ │ │   │   └ sddk::wf_inner|scale_back                             |                       265.92 ns            |                 116              |                        30.85 μs            | 
+ │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       71.68 ms →       40.36 ms  (-43.70%) |     250   →     116    (-53.60%) |       17.92 s  →        4.68 s   (-73.88%) | 
+ │ │ │ │   ├ sirius::residuals                                         |        3.20 ms →        2.78 ms  (-13.00%) |     245   →     114    (-53.47%) |      783.76 ms →      317.29 ms  (-59.52%) | 
  │ │ │ │   │ ├ sddk::transform                                         |        1.92 ms                             |     231                          |      444.37 ms                             | 
  │ │ │ │   │ │ ├ sddk::transform|init                                  |       14.57 μs                             |     231                          |        3.37 ms                             | 
  │ │ │ │   │ │ └ sddk::transform|local                                 |        9.59 μs                             |     462                          |        4.43 ms                             | 
  │ │ │ │   │ ├ sddk::wf_trans                                          |                         1.51 ms            |                 101              |                       152.91 ms            | 
  │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |                       755.54 μs            |                 202              |                       152.62 ms            | 
+ │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.39 ms →        1.41 ms   (+1.00%) |     231   →     101    (-56.28%) |      322.02 ms →      142.20 ms  (-55.84%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |        7.20 ms →        4.62 ms  (-35.83%) |      25   →      47    (+88.00%) |      180.02 ms →      217.19 ms  (+20.65%) | 
  │ │ │ │     ├ sddk::transform                                         |        5.92 ms                             |      30                          |      177.57 ms                             | 
  │ │ │ │     │ ├ sddk::transform|init                                  |       10.42 μs                             |      30                          |      312.47 μs                             | 
  │ │ │ │     │ └ sddk::transform|local                                 |       11.58 μs                             |      35                          |      405.40 μs                             | 
  │ │ │ │     └ sddk::wf_trans                                          |                         2.70 ms            |                  79              |                       213.19 ms            | 
  │ │ │ │       └ sddk::wf_trans|pw                                     |                         1.92 ms            |                 111              |                       213.03 ms            | 
+ │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      442.40 ns →      454.33 ns   (+2.70%) |      20   →      15    (-25.00%) |        8.85 μs →        6.81 μs  (-22.98%) | 
  │ │ │ ├ sirius::K_point_set::sync_band_energies                       |       21.02 μs                             |      20                          |      420.39 μs                             | 
  │ │ │ └ sirius::K_point_set::sync_band                                |                        64.46 μs            |                  15              |                       966.84 μs            | 
+ │ │ ├ sirius::K_point_set::find_band_occupancies                      |        1.51 ms →      996.44 μs  (-33.85%) |      20   →      15    (-25.00%) |       30.13 ms →       14.95 ms  (-50.39%) | 
  │ │ │ └ sirius::K_point_set::sync_band                                |                        14.86 μs            |                  15              |                       222.92 μs            | 
+ │ │ ├ sirius::Density::generate                                       |      573.59 ms →      560.54 ms   (-2.28%) |      20   →      15    (-25.00%) |       11.47 s  →        8.41 s   (-26.71%) | 
+ │ │ │ ├ sirius::Density::generate_valence                             |      418.62 ms →      410.79 ms   (-1.87%) |      20   →      15    (-25.00%) |        8.37 s  →        6.16 s   (-26.40%) | 
+ │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        7.43 μs →        5.03 μs  (-32.34%) |      20   →      15    (-25.00%) |      148.66 μs →       75.44 μs  (-49.25%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        7.03 μs                             |      20                          |      140.57 μs                             | 
+ │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |       36.24 ms →       25.13 ms  (-30.66%) |      20   →      15    (-25.00%) |      724.80 ms →      376.95 ms  (-47.99%) | 
- │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |        7.97 μs →        9.16 μs  (+14.95%) |      20   →      15    (-25.00%) |      159.43 μs →      137.45 μs  (-13.79%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        5.92 ms →        4.47 ms  (-24.41%) |      20   →      15    (-25.00%) |      118.39 ms →       67.12 ms  (-43.31%) | 
+ │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       29.29 ms →       19.58 ms  (-33.15%) |      20   →      15    (-25.00%) |      585.76 ms →      293.70 ms  (-49.86%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      563.30 ns →      622.13 ns  (+10.44%) |      20   →      15    (-25.00%) |       11.27 μs →        9.33 μs  (-17.17%) | 
- │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      109.36 ms →      120.85 ms  (+10.50%) |      20   →      15    (-25.00%) |        2.19 s  →        1.81 s   (-17.12%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        2.14 ms →        2.15 ms   (+0.87%) |      20   →      15    (-25.00%) |       42.72 ms →       32.32 ms  (-24.35%) | 
+ │ │ │ │ └ sirius::Density::augment                                    |      232.42 ms →      235.31 ms   (+1.25%) |      20   →      15    (-25.00%) |        4.65 s  →        3.53 s   (-24.06%) | 
+ │ │ │ │   └ sirius::Density::generate_rho_aug                         |      232.19 ms →      235.10 ms   (+1.25%) |      20   →      15    (-25.00%) |        4.64 s  →        3.53 s   (-24.06%) | 
+ │ │ │ ├ sirius::Field4D::symmetrize                                   |      126.14 ms →      122.36 ms   (-3.00%) |      20   →      15    (-25.00%) |        2.52 s  →        1.84 s   (-27.25%) | 
+ │ │ │ │ └ sirius::symmetrize_function|fpw                             |      126.14 ms →      122.35 ms   (-3.00%) |      20   →      15    (-25.00%) |        2.52 s  →        1.84 s   (-27.25%) | 
+ │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       42.35 ms →       43.63 ms   (+3.03%) |      20   →      15    (-25.00%) |      846.90 ms →      654.45 ms  (-22.72%) | 
+ │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |       70.54 ms →       65.16 ms   (-7.62%) |      20   →      15    (-25.00%) |        1.41 s  →      977.36 ms  (-30.72%) | 
+ │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       12.62 ms →       12.90 ms   (+2.26%) |      20   →      15    (-25.00%) |      252.37 ms →      193.55 ms  (-23.31%) | 
+ │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       23.60 ms →       23.60 ms   (+0.01%) |      20   →      15    (-25.00%) |      472.01 ms →      354.04 ms  (-24.99%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |        5.23 ms →        3.78 ms  (-27.80%) |      20   →      15    (-25.00%) |      104.61 ms →       56.64 ms  (-45.85%) | 
  │ │ ├ sirius::inner                                                   |                         4.94 ms            |                 180              |                       888.89 ms            | 
+ │ │ ├ sirius::Density::mix                                            |      137.34 ms →       74.68 ms  (-45.62%) |      20   →      15    (-25.00%) |        2.75 s  →        1.12 s   (-59.22%) | 
- │ │ │ ├ sirius::Density::mixer_input                                  |      845.22 μs →      988.09 μs  (+16.90%) |      20   →      15    (-25.00%) |       16.90 ms →       14.82 ms  (-12.32%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |        5.03 ms                             |     244                          |        1.23 s                              | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |        5.00 ms                             |     244                          |        1.22 s                              | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |        5.00 ms                             |     244                          |        1.22 s                              | 
  │ │ │ ├ sirius::inner                                                 |                         4.56 ms            |                 169              |                       770.92 ms            | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        5.19 ms →        4.97 ms   (-4.20%) |      20   →      15    (-25.00%) |      103.79 ms →       74.57 ms  (-28.15%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        4.51 ms →        4.01 ms  (-11.02%) |      20   →      15    (-25.00%) |       90.14 ms →       60.15 ms  (-33.27%) | 
+ │ │ ├ sirius::Potential::generate                                     |      372.55 ms →      365.96 ms   (-1.77%) |      20   →      15    (-25.00%) |        7.45 s  →        5.49 s   (-26.33%) | 
+ │ │ │ ├ sirius::Potential::poisson                                    |       42.31 ms →       42.65 ms   (+0.80%) |      20   →      15    (-25.00%) |      846.27 ms →      639.81 ms  (-24.40%) | 
- │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        6.93 ms →       10.71 ms  (+54.50%) |      20   →      15    (-25.00%) |      138.60 ms →      160.60 ms  (+15.88%) | 
  │ │ │ │ ├ sirius::Periodic_function|inner                             |        6.05 ms                             |      20                          |      121.09 ms                             | 
  │ │ │ │ │ └ sirius::Periodic_function|inner_local                     |        4.84 ms                             |      20                          |       96.70 ms                             | 
  │ │ │ │ │   └ sirius::Smooth_periodic_function|inner_local            |        4.83 ms                             |      20                          |       96.68 ms                             | 
  │ │ │ │ └ sirius::inner                                               |                         5.76 ms            |                  15              |                        86.39 ms            | 
+ │ │ │ ├ sirius::Periodic_function::add                                |      785.81 μs →      712.12 μs   (-9.38%) |      40   →      30    (-25.00%) |       31.43 ms →       21.36 ms  (-32.03%) | 
+ │ │ │ ├ sirius::Potential::xc                                         |       55.48 ms →       46.85 ms  (-15.55%) |      20   →      15    (-25.00%) |        1.11 s  →      702.78 ms  (-36.66%) | 
+ │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       55.48 ms →       45.66 ms  (-17.70%) |      20   →      15    (-25.00%) |        1.11 s  →      684.91 ms  (-38.27%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |      629.41 μs                             |      40                          |       25.18 ms                             | 
  │ │ │ │   ├ sirius::Smooth_periodic_function::fft_transform           |        4.67 ms                             |      20                          |       93.35 ms                             | 
  │ │ │ │   └ sirius::Potential::xc_rg_nonmagnetic|libxc                |                        19.55 ms            |                  30              |                       586.50 ms            | 
- │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        3.06 ms →        3.63 ms  (+18.81%) |      20   →      15    (-25.00%) |       61.11 ms →       54.45 ms  (-10.89%) | 
+ │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |      268.74 ms →      268.52 ms   (-0.08%) |      20   →      15    (-25.00%) |        5.37 s  →        4.03 s   (-25.06%) | 
+ │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      217.55 ns →      186.07 ns  (-14.47%) |      20   →      15    (-25.00%) |        4.35 μs →        2.79 μs  (-35.85%) | 
+ │ │ ├ sirius::Field4D::symmetrize                                     |       96.97 ms →       91.78 ms   (-5.35%) |      20   →      15    (-25.00%) |        1.94 s  →        1.38 s   (-29.02%) | 
+ │ │ │ └ sirius::symmetrize_function|fpw                               |       96.97 ms →       91.77 ms   (-5.36%) |      20   →      15    (-25.00%) |        1.94 s  →        1.38 s   (-29.02%) | 
+ │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       13.28 ms →       13.53 ms   (+1.90%) |      20   →      15    (-25.00%) |      265.57 ms →      202.96 ms  (-23.58%) | 
+ │ │ │   ├ sirius::symmetrize_function|fpw|local                       |       70.43 ms →       64.77 ms   (-8.03%) |      20   →      15    (-25.00%) |        1.41 s  →      971.62 ms  (-31.03%) | 
+ │ │ │   └ sddk::Gvec_shells::remap_backward                           |       12.63 ms →       12.85 ms   (+1.73%) |      20   →      15    (-25.00%) |      252.57 ms →      192.71 ms  (-23.70%) | 
+ │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        3.78 ms →        3.59 ms   (-5.02%) |      20   →      15    (-25.00%) |       75.59 ms →       53.84 ms  (-28.76%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |        4.87 ms                             |     140                          |      681.82 ms                             | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |        4.74 ms                             |     140                          |      663.81 ms                             | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |        4.74 ms                             |     140                          |      663.71 ms                             | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |        4.53 ms                             |      60                          |      271.83 ms                             | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |        4.52 ms                             |      60                          |      271.43 ms                             | 
+ │ │ ├ sirius::Periodic_function::integrate                            |        4.53 ms →        4.58 ms   (+1.06%) |      20   →      15    (-25.00%) |       90.61 ms →       68.68 ms  (-24.20%) | 
- │ │ └ sirius::Density::get_magnetisation                              |       74.94 μs →       23.65 ms (+31462.08%) |      20   →      15    (-25.00%) |        1.50 ms →      354.79 ms (+23571.56%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |       70.02 μs →       23.65 ms (+33671.31%) |      20   →      15    (-25.00%) |        1.40 ms →      354.69 ms (+25228.48%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.56 ms →        5.68 ms   (+2.16%) |       2   →       2              |       11.12 ms →       11.37 ms   (+2.16%) | 
  │ ├ sirius::Periodic_function|inner                                   |        5.00 ms                             |       6                          |       30.02 ms                             | 
  │ │ └ sirius::Periodic_function|inner_local                           |        5.00 ms                             |       6                          |       30.00 ms                             | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |        5.00 ms                             |       6                          |       30.00 ms                             | 
  │ ├ sirius::Smooth_periodic_function|inner                            |        4.80 ms                             |       3                          |       14.39 ms                             | 
  │ │ └ sirius::Smooth_periodic_function|inner_local                    |        4.79 ms                             |       3                          |       14.38 ms                             | 
  │ └ sirius::inner                                                     |                         4.75 ms            |                   9              |                        42.79 ms            | 
  ├ sirius::Periodic_function|inner                                     |        4.98 ms                             |       2                          |        9.95 ms                             | 
  │ └ sirius::Periodic_function|inner_local                             |        4.97 ms                             |       2                          |        9.95 ms                             | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        4.97 ms                             |       2                          |        9.94 ms                             | 
  ├ sirius::Smooth_periodic_function|inner                              |        4.78 ms                             |       1                          |        4.78 ms                             | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        4.78 ms                             |       1                          |        4.78 ms                             | 
  ├ sirius::inner                                                       |                         4.81 ms            |                   3              |                        14.44 ms            | 
+ └ sirius::finalize                                                    |      937.28 ms →      182.32 ms  (-80.55%) |       1   →       1              |      937.28 ms →      182.32 ms  (-80.55%) | 
  ====================================================================================================================================================================================================
```
