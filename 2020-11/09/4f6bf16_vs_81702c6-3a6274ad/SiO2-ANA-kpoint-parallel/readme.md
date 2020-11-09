# Benchmark 81702c64a8be67a2936e3e8bb8ca2c9083dee03b vs 4f6bf1684449bb549717c67734c215f779f51100
```diff
  ====================================================================================================================================================================================================
                                                                        |                                       Mean |                                # |                                      Total | 
  ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
  sirius                                                                |      129.55 s  →      132.03 s    (+1.91%) |       1   →       1              |      129.55 s  →      132.03 s    (+1.91%) | 
  ├ sirius::initialize                                                  |        2.68 s  →        2.68 s    (+0.09%) |       1   →       1              |        2.68 s  →        2.68 s    (+0.09%) | 
  ├ sirius::Simulation_context::initialize                              |        3.11 s  →        3.40 s    (+9.37%) |       1   →       1              |        3.11 s  →        3.40 s    (+9.37%) | 
+ │ ├ sirius::Simulation_context::init_comm                             |      112.88 ms →       70.39 ms  (-37.64%) |       1   →       1              |      112.88 ms →       70.39 ms  (-37.64%) | 
- │ ├ sirius::Unit_cell::initialize                                     |      226.65 ms →      554.20 ms (+144.51%) |       1   →       1              |      226.65 ms →      554.20 ms (+144.51%) | 
- │ │ ├ sirius::Atom_type::init                                         |      101.79 ms →      265.27 ms (+160.61%) |       2   →       2              |      203.58 ms →      530.54 ms (+160.61%) | 
  │ │ └ sirius::Unit_cell::update                                       |       23.00 ms →       23.58 ms   (+2.52%) |       1   →       1              |       23.00 ms →       23.58 ms   (+2.52%) | 
  │ │   ├ sirius::Unit_cell::find_nearest_neighbours                    |        6.31 ms →        6.38 ms   (+0.99%) |       1   →       1              |        6.31 ms →        6.38 ms   (+0.99%) | 
  │ │   └ sirius::Unit_cell::get_symmetry                               |       16.64 ms →       17.15 ms   (+3.07%) |       1   →       1              |       16.64 ms →       17.15 ms   (+3.07%) | 
  │ │     └ sirius::Unit_cell_symmetry                                  |       16.62 ms →       17.13 ms   (+3.08%) |       1   →       1              |       16.62 ms →       17.13 ms   (+3.08%) | 
  │ │       ├ sirius::Unit_cell_symmetry|spg                            |        4.16 ms →        4.15 ms   (-0.18%) |       1   →       1              |        4.16 ms →        4.15 ms   (-0.18%) | 
  │ │       ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.34 ms   (+0.45%) |       1   →       1              |        2.33 ms →        2.34 ms   (+0.45%) | 
  │ │       └ sirius::Unit_cell_symmetry|mag                            |      106.20 μs →      106.84 μs   (+0.61%) |       1   →       1              |      106.20 μs →      106.84 μs   (+0.61%) | 
  │ └ sirius::Simulation_context::update                                |        2.72 s  →        2.73 s    (+0.28%) |       1   →       1              |        2.72 s  →        2.73 s    (+0.28%) | 
  │   ├ sirius::Unit_cell::update                                       |       10.79 ms →       10.86 ms   (+0.68%) |       1   →       1              |       10.79 ms →       10.86 ms   (+0.68%) | 
  │   │ ├ sirius::Unit_cell::find_nearest_neighbours                    |        4.41 ms →        4.48 ms   (+1.60%) |       1   →       1              |        4.41 ms →        4.48 ms   (+1.60%) | 
  │   │ └ sirius::Unit_cell::get_symmetry                               |        6.35 ms →        6.35 ms   (+0.01%) |       1   →       1              |        6.35 ms →        6.35 ms   (+0.01%) | 
  │   │   └ sirius::Unit_cell_symmetry                                  |        6.33 ms →        6.33 ms   (-0.01%) |       1   →       1              |        6.33 ms →        6.33 ms   (-0.01%) | 
  │   │     ├ sirius::Unit_cell_symmetry|spg                            |        3.83 ms →        3.84 ms   (+0.21%) |       1   →       1              |        3.83 ms →        3.84 ms   (+0.21%) | 
  │   │     ├ sirius::Unit_cell_symmetry|equiv                          |        2.33 ms →        2.32 ms   (-0.16%) |       1   →       1              |        2.33 ms →        2.32 ms   (-0.16%) | 
  │   │     └ sirius::Unit_cell_symmetry|mag                            |      104.80 μs →       99.24 μs   (-5.31%) |       1   →       1              |      104.80 μs →       99.24 μs   (-5.31%) | 
  │   ├ sirius::Radial_integrals|aug                                    |       62.75 ms →       64.15 ms   (+2.23%) |       2   →       2              |      125.50 ms →      128.30 ms   (+2.23%) | 
  │   ├ sirius::Radial_integrals|rho_core_pseudo                        |        5.33 ms →        5.34 ms   (+0.05%) |       2   →       2              |       10.67 ms →       10.67 ms   (+0.05%) | 
  │   ├ sirius::Radial_integrals|rho_pseudo                             |        4.86 ms →        4.47 ms   (-7.94%) |       1   →       1              |        4.86 ms →        4.47 ms   (-7.94%) | 
  │   ├ sirius::Radial_integrals|vloc                                   |       21.73 ms →       22.19 ms   (+2.12%) |       2   →       2              |       43.45 ms →       44.37 ms   (+2.12%) | 
  │   ├ sirius::Radial_integrals|beta                                   |       14.82 ms →       15.08 ms   (+1.75%) |       2   →       2              |       29.64 ms →       30.16 ms   (+1.75%) | 
  │   ├ sirius::Radial_integrals|atomic_wfs                             |       19.75 ms →       19.71 ms   (-0.23%) |       4   →       4              |       79.01 ms →       78.83 ms   (-0.23%) | 
  │   ├ sddk::Gvec::init                                                |      172.95 ms →      171.99 ms   (-0.56%) |       2   →       2              |      345.90 ms →      343.98 ms   (-0.56%) | 
  │   │ └ sddk::Gvec::find_gvec_shells                                  |      130.59 ms →      129.64 ms   (-0.73%) |       2   →       2              |      261.18 ms →      259.27 ms   (-0.73%) | 
  │   ├ sddk::Gvec_shells                                               |      172.66 ms →      163.47 ms   (-5.32%) |       1   →       1              |      172.66 ms →      163.47 ms   (-5.32%) | 
  │   ├ sirius::Simulation_context::init_atoms_to_grid_idx              |        1.32 ms →        1.32 ms   (+0.10%) |       1   →       1              |        1.32 ms →        1.32 ms   (+0.10%) | 
  │   └ sirius::Augmentation_operator::generate_pw_coeffs               |      292.43 ms →      293.14 ms   (+0.24%) |       2   →       2              |      584.86 ms →      586.28 ms   (+0.24%) | 
  ├ sirius::K_point_set::create_k_mesh                                  |       35.73 ms →       35.48 ms   (-0.70%) |       1   →       1              |       35.73 ms →       35.48 ms   (-0.70%) | 
+ │ ├ sirius::K_point::K_point                                          |        2.89 μs →        2.52 μs  (-12.54%) |       4   →       4              |       11.55 μs →       10.10 μs  (-12.54%) | 
  │ └ sirius::K_point_set::initialize                                   |       35.62 ms →       35.38 ms   (-0.70%) |       1   →       1              |       35.62 ms →       35.38 ms   (-0.70%) | 
  │   └ sirius::K_point::initialize                                     |       35.52 ms →       35.16 ms   (-1.01%) |       1   →       1              |       35.52 ms →       35.16 ms   (-1.01%) | 
  │     ├ sirius::K_point::generate_gkvec                               |       18.31 ms →       17.96 ms   (-1.95%) |       1   →       1              |       18.31 ms →       17.96 ms   (-1.95%) | 
  │     │ └ sddk::Gvec::init                                            |        8.31 ms →        8.04 ms   (-3.19%) |       1   →       1              |        8.31 ms →        8.04 ms   (-3.19%) | 
- │     ├ sddk::matrix_storage::matrix_storage                          |        8.88 μs →        9.93 μs  (+11.81%) |       1   →       1              |        8.88 μs →        9.93 μs  (+11.81%) | 
  │     └ sirius::K_point::update                                       |       12.39 ms →       12.32 ms   (-0.62%) |       1   →       1              |       12.39 ms →       12.32 ms   (-0.62%) | 
  │       └ sirius::Beta_projectors                                     |        6.25 ms →        6.10 ms   (-2.30%) |       1   →       1              |        6.25 ms →        6.10 ms   (-2.30%) | 
  │         └ sirius::Beta_projectors::generate_pw_coefs_t              |        3.79 ms →        3.65 ms   (-3.47%) |       1   →       1              |        3.79 ms →        3.65 ms   (-3.47%) | 
  ├ sirius::Smooth_periodic_function                                    |        5.49 ms →        5.49 ms   (-0.14%) |       2   →       2              |       10.99 ms →       10.97 ms   (-0.14%) | 
  ├ sirius::Potential                                                   |      152.85 ms →      158.73 ms   (+3.85%) |       1   →       1              |      152.85 ms →      158.73 ms   (+3.85%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.86 ms →        5.87 ms   (+0.20%) |       6   →       6              |       35.18 ms →       35.25 ms   (+0.20%) | 
  │ └ sirius::Potential::update                                         |      116.89 ms →      122.74 ms   (+5.01%) |       1   →       1              |      116.89 ms →      122.74 ms   (+5.01%) | 
  │   └ sirius::Potential::generate_local_potential                     |      116.04 ms →      121.93 ms   (+5.08%) |       1   →       1              |      116.04 ms →      121.93 ms   (+5.08%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      106.86 ms →      114.62 ms   (+7.26%) |       1   →       1              |      106.86 ms →      114.62 ms   (+7.26%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        8.27 ms →        6.42 ms  (-22.28%) |       1   →       1              |        8.27 ms →        6.42 ms  (-22.28%) | 
  ├ sirius::Density                                                     |      127.17 ms →      134.22 ms   (+5.54%) |       1   →       1              |      127.17 ms →      134.22 ms   (+5.54%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.27 ms →        5.30 ms   (+0.63%) |       2   →       2              |       10.54 ms →       10.60 ms   (+0.63%) | 
  │ └ sirius::Density::update                                           |      116.36 ms →      123.34 ms   (+6.00%) |       1   →       1              |      116.36 ms →      123.34 ms   (+6.00%) | 
  │   └ sirius::Density::generate_pseudo_core_charge_density            |      115.93 ms →      122.89 ms   (+6.00%) |       1   →       1              |      115.93 ms →      122.89 ms   (+6.00%) | 
  │     ├ sirius::rho_core_ri_pseudo|values                             |      106.95 μs →      114.87 μs   (+7.41%) |       1   →       1              |      106.95 μs →      114.87 μs   (+7.41%) | 
  │     ├ sirius::Simulation_context::make_periodic_function            |      109.17 ms →      117.18 ms   (+7.33%) |       1   →       1              |      109.17 ms →      117.18 ms   (+7.33%) | 
+ │     └ sirius::Smooth_periodic_function::fft_transform               |        6.19 ms →        5.14 ms  (-16.97%) |       1   →       1              |        6.19 ms →        5.14 ms  (-16.97%) | 
- ├ sirius::Density::initial_density                                    |      161.93 ms →      179.58 ms  (+10.90%) |       1   →       1              |      161.93 ms →      179.58 ms  (+10.90%) | 
- │ ├ sirius::Simulation_context::make_periodic_function                |      109.19 ms →      122.03 ms  (+11.75%) |       1   →       1              |      109.19 ms →      122.03 ms  (+11.75%) | 
- │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.08 ms →        6.30 ms  (+23.90%) |       2   →       2              |       10.17 ms →       12.60 ms  (+23.90%) | 
- │ └ sirius::Periodic_function::integrate                              |       10.00 ms →       12.75 ms  (+27.48%) |       1   →       1              |       10.00 ms →       12.75 ms  (+27.48%) | 
  ├ sirius::Potential::generate                                         |      578.85 ms →      594.13 ms   (+2.64%) |       1   →       1              |      578.85 ms →      594.13 ms   (+2.64%) | 
- │ ├ sirius::Potential::poisson                                        |      123.99 ms →      137.64 ms  (+11.01%) |       1   →       1              |      123.99 ms →      137.64 ms  (+11.01%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.27 ms →        5.35 ms   (+1.50%) |       1   →       1              |        5.27 ms →        5.35 ms   (+1.50%) | 
  │ │ └ sirius::Periodic_function|inner                                 |       10.56 ms →       10.83 ms   (+2.58%) |       1   →       1              |       10.56 ms →       10.83 ms   (+2.58%) | 
  │ │   └ sirius::Periodic_function|inner_local                         |       10.54 ms →       10.24 ms   (-2.82%) |       1   →       1              |       10.54 ms →       10.24 ms   (-2.82%) | 
  │ │     └ sirius::Smooth_periodic_function|inner_local                |       10.53 ms →       10.23 ms   (-2.83%) |       1   →       1              |       10.53 ms →       10.23 ms   (-2.83%) | 
  │ ├ sirius::Periodic_function::add                                    |      545.93 μs →      550.71 μs   (+0.88%) |       2   →       2              |        1.09 ms →        1.10 ms   (+0.88%) | 
  │ ├ sirius::Potential::xc                                             |       54.66 ms →       55.14 ms   (+0.89%) |       1   →       1              |       54.66 ms →       55.14 ms   (+0.89%) | 
  │ │ └ sirius::Potential::xc_rg_nonmagnetic                            |       52.27 ms →       52.73 ms   (+0.88%) |       1   →       1              |       52.27 ms →       52.73 ms   (+0.88%) | 
  │ │   ├ sirius::Smooth_periodic_function                              |        5.76 ms →        5.78 ms   (+0.39%) |       2   →       2              |       11.52 ms →       11.57 ms   (+0.39%) | 
- │ │   └ sirius::Smooth_periodic_function::fft_transform               |        5.23 ms →        6.56 ms  (+25.48%) |       1   →       1              |        5.23 ms →        6.56 ms  (+25.48%) | 
  │ ├ sirius::Smooth_periodic_function::fft_transform                   |        5.84 ms →        6.01 ms   (+3.02%) |       1   →       1              |        5.84 ms →        6.01 ms   (+3.02%) | 
  │ ├ sirius::Potential::generate_D_operator_matrix                     |       92.78 ms →       92.72 ms   (-0.06%) |       1   →       1              |       92.78 ms →       92.72 ms   (-0.06%) | 
  │ └ sirius::Potential::generate_PAW_effective_potential               |      299.08 ms →      300.12 ms   (+0.35%) |       1   →       1              |      299.08 ms →      300.12 ms   (+0.35%) | 
  ├ sirius::Hamiltonian0                                                |        8.40 ms →        8.66 ms   (+3.19%) |       1   →       1              |        8.40 ms →        8.66 ms   (+3.19%) | 
  │ ├ sirius::Local_operator                                            |        8.05 ms →        8.32 ms   (+3.34%) |       1   →       1              |        8.05 ms →        8.32 ms   (+3.34%) | 
  │ │ ├ sirius::Smooth_periodic_function                                |        4.78 ms →        5.11 ms   (+6.82%) |       1   →       1              |        4.78 ms →        5.11 ms   (+6.82%) | 
  │ │ └ sirius::Smooth_periodic_function::fft_transform                 |        2.34 ms →        2.31 ms   (-1.29%) |       1   →       1              |        2.34 ms →        2.31 ms   (-1.29%) | 
  │ ├ sirius::Non_local_operator                                        |       61.90 μs →       62.87 μs   (+1.55%) |       2   →       2              |      123.81 μs →      125.73 μs   (+1.55%) | 
  │ ├ sirius::D_operator::initialize                                    |       93.57 μs →       93.55 μs   (-0.02%) |       1   →       1              |       93.57 μs →       93.55 μs   (-0.02%) | 
  │ └ sirius::Q_operator::initialize                                    |       75.84 μs →       73.69 μs   (-2.83%) |       1   →       1              |       75.84 μs →       73.69 μs   (-2.83%) | 
  ├ sirius::Band::initialize_subspace                                   |        1.86 s  →        1.90 s    (+2.62%) |       1   →       1              |        1.86 s  →        1.90 s    (+2.62%) | 
  │ ├ sirius::Hamiltonian_k                                             |       18.67 ms →       18.69 ms   (+0.14%) |       1   →       1              |       18.67 ms →       18.69 ms   (+0.14%) | 
  │ │ ├ sirius::Local_operator::prepare_k                               |      163.28 μs →      172.60 μs   (+5.71%) |       1   →       1              |      163.28 μs →      172.60 μs   (+5.71%) | 
  │ │ └ sirius::Beta_projectors_base::prepare                           |       18.50 ms →       18.52 ms   (+0.09%) |       1   →       1              |       18.50 ms →       18.52 ms   (+0.09%) | 
  │ ├ sirius::Band::initialize_subspace|kp                              |        1.84 s  →        1.89 s    (+2.65%) |       1   →       1              |        1.84 s  →        1.89 s    (+2.65%) | 
  │ │ ├ sddk::matrix_storage::matrix_storage                            |      125.63 ms →      134.12 ms   (+6.76%) |       4   →       4              |      502.54 ms →      536.50 ms   (+6.76%) | 
  │ │ ├ sirius::K_point::generate_atomic_wave_functions                 |       53.04 ms →       52.39 ms   (-1.22%) |       1   →       1              |       53.04 ms →       52.39 ms   (-1.22%) | 
  │ │ ├ sirius::Band::initialize_subspace|kp|wf                         |       21.01 ms →       21.02 ms   (+0.06%) |       1   →       1              |       21.01 ms →       21.02 ms   (+0.06%) | 
  │ │ ├ sirius::Hamiltonian_k::apply_h_s                                |      637.25 ms →      637.10 ms   (-0.02%) |       1   →       1              |      637.25 ms →      637.10 ms   (-0.02%) | 
  │ │ │ ├ sirius::Local_operator::apply_h                               |      298.42 ms →      298.10 ms   (-0.11%) |       1   →       1              |      298.42 ms →      298.10 ms   (-0.11%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.12 μs →        3.51 μs  (+12.40%) |       1   →       1              |        3.12 μs →        3.51 μs  (+12.40%) | 
- │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        2.16 μs →        2.56 μs  (+18.31%) |       1   →       1              |        2.16 μs →        2.56 μs  (+18.31%) | 
+ │ │ │ │ ├ sddk::matrix_storage::set_num_extra                         |      582.00 ns →      456.00 ns  (-21.65%) |       1   →       1              |      582.00 ns →      456.00 ns  (-21.65%) | 
- │ │ │ │ └ sddk::matrix_storage::remap_backward                        |      494.00 ns →      564.00 ns  (+14.17%) |       1   →       1              |      494.00 ns →      564.00 ns  (+14.17%) | 
  │ │ │ ├ sirius::Beta_projectors_base::generate                        |        9.23 ms →        9.23 ms   (+0.02%) |       1   →       1              |        9.23 ms →        9.23 ms   (+0.02%) | 
  │ │ │ ├ sirius::Beta_projectors_base::inner                           |      121.38 ms →      121.84 ms   (+0.38%) |       1   →       1              |      121.38 ms →      121.84 ms   (+0.38%) | 
  │ │ │ └ sirius::Non_local_operator::apply                             |      104.09 ms →      103.94 ms   (-0.14%) |       2   →       2              |      208.19 ms →      207.89 ms   (-0.14%) | 
  │ │ ├ sirius::Band::set_subspace_mtrx                                 |       40.22 ms →       40.01 ms   (-0.53%) |       2   →       2              |       80.44 ms →       80.01 ms   (-0.53%) | 
  │ │ │ └ sddk::wf_inner                                                |       39.63 ms →       39.47 ms   (-0.40%) |       2   →       2              |       79.26 ms →       78.94 ms   (-0.40%) | 
  │ │ │   ├ sddk::wf_inner|scale                                        |       30.50 ns →       29.50 ns   (-3.28%) |       2   →       2              |       61.00 ns →       59.00 ns   (-3.28%) | 
  │ │ │   ├ sddk::wf_inner|pw                                           |       39.16 ms →       39.00 ms   (-0.39%) |       2   →       2              |       78.31 ms →       78.01 ms   (-0.39%) | 
  │ │ │   └ sddk::wf_inner|scale_back                                   |       23.50 ns →       25.00 ns   (+6.38%) |       2   →       2              |       47.00 ns →       50.00 ns   (+6.38%) | 
  │ │ ├ Eigensolver_cuda|zhegvdx                                        |       56.43 ms →       57.27 ms   (+1.49%) |       1   →       1              |       56.43 ms →       57.27 ms   (+1.49%) | 
  │ │ └ sddk::wf_trans                                                  |       30.69 ms →       30.70 ms   (+0.03%) |       1   →       1              |       30.69 ms →       30.70 ms   (+0.03%) | 
  │ │   └ sddk::wf_trans|pw                                             |       30.69 ms →       30.70 ms   (+0.03%) |       1   →       1              |       30.69 ms →       30.70 ms   (+0.03%) | 
+ │ └ sirius::Beta_projectors_base::dismiss                             |      453.00 ns →      369.00 ns  (-18.54%) |       1   →       1              |      453.00 ns →      369.00 ns  (-18.54%) | 
  ├ sirius::DFT_ground_state::scf_loop                                  |      119.28 s  →      121.80 s    (+2.11%) |       1   →       1              |      119.28 s  →      121.80 s    (+2.11%) | 
  │ ├ sirius::Smooth_periodic_function                                  |        5.87 ms →        5.89 ms   (+0.46%) |      19   →      19              |      111.46 ms →      111.97 ms   (+0.46%) | 
  │ ├ sirius::DFT_ground_state::scf_loop|iteration                      |        4.58 s  →        4.85 s    (+6.02%) |      26   →      25     (-3.85%) |      118.96 s  →      121.27 s    (+1.94%) | 
+ │ │ ├ sirius::Hamiltonian0                                            |        5.63 ms →        4.56 ms  (-19.02%) |      26   →      25     (-3.85%) |      146.26 ms →      113.88 ms  (-22.14%) | 
+ │ │ │ ├ sirius::Local_operator                                        |        5.26 ms →        4.19 ms  (-20.45%) |      26   →      25     (-3.85%) |      136.81 ms →      104.65 ms  (-23.51%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function                            |        1.02 ms →        1.02 ms   (-0.12%) |      26   →      25     (-3.85%) |       26.51 ms →       25.46 ms   (-3.96%) | 
+ │ │ │ │ └ sirius::Smooth_periodic_function::fft_transform             |        3.35 ms →        2.27 ms  (-32.08%) |      26   →      25     (-3.85%) |       87.04 ms →       56.85 ms  (-34.69%) | 
  │ │ │ ├ sirius::Non_local_operator                                    |       64.29 μs →       64.10 μs   (-0.29%) |      52   →      50     (-3.85%) |        3.34 ms →        3.21 ms   (-4.12%) | 
  │ │ │ ├ sirius::D_operator::initialize                                |       87.91 μs →       88.18 μs   (+0.31%) |      26   →      25     (-3.85%) |        2.29 ms →        2.20 ms   (-3.54%) | 
  │ │ │ └ sirius::Q_operator::initialize                                |       76.80 μs →       79.46 μs   (+3.46%) |      26   →      25     (-3.85%) |        2.00 ms →        1.99 ms   (-0.52%) | 
- │ │ ├ sirius::Band::solve                                             |        2.60 s  →        2.88 s   (+11.01%) |      26   →      25     (-3.85%) |       67.48 s  →       72.03 s    (+6.74%) | 
  │ │ │ ├ sirius::Hamiltonian_k                                         |      152.06 μs →      157.82 μs   (+3.79%) |      26   →      25     (-3.85%) |        3.95 ms →        3.95 ms   (-0.20%) | 
  │ │ │ │ ├ sirius::Local_operator::prepare_k                           |      145.72 μs →      151.31 μs   (+3.84%) |      26   →      25     (-3.85%) |        3.79 ms →        3.78 ms   (-0.16%) | 
  │ │ │ │ └ sirius::Beta_projectors_base::prepare                       |        4.67 μs →        4.64 μs   (-0.51%) |      26   →      25     (-3.85%) |      121.38 μs →      116.12 μs   (-4.34%) | 
  │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson                  |        2.47 s  →        2.71 s    (+9.66%) |      26   →      25     (-3.85%) |       64.15 s  →       67.65 s    (+5.44%) | 
- │ │ │ │ ├ sirius::Band::diag_pseudo_potential_davidson|alloc          |       96.41 ms →      155.56 ms  (+61.35%) |      26   →      25     (-3.85%) |        2.51 s  →        3.89 s   (+55.15%) | 
! │ │ │ │ │ └ sddk::matrix_storage::matrix_storage                      |        7.57 ms →        7.04 ms   (-7.05%) |     156   →     175    (+12.18%) |        1.18 s  →        1.23 s    (+4.27%) | 
  │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag                         |        5.81 ms →        6.00 ms   (+3.20%) |      26   →      25     (-3.85%) |      151.14 ms →      149.98 ms   (-0.77%) | 
  │ │ │ │ │ ├ sirius::Hamiltonian_k::get_h_o_diag|1                     |      353.97 μs →      351.57 μs   (-0.68%) |      26   →      25     (-3.85%) |        9.20 ms →        8.79 ms   (-4.50%) | 
  │ │ │ │ │ └ sirius::Hamiltonian_k::get_h_o_diag|3                     |        2.30 ms →        2.38 ms   (+3.52%) |      52   →      50     (-3.85%) |      119.69 ms →      119.14 ms   (-0.46%) | 
  │ │ │ │ └ sirius::Band::diag_pseudo_potential_davidson|iter           |        2.33 s  →        2.44 s    (+4.92%) |      26   →      25     (-3.85%) |       60.57 s  →       61.10 s    (+0.88%) | 
- │ │ │ │   ├ sirius::Hamiltonian_k::apply_h_s                          |      137.11 ms →      186.28 ms  (+35.86%) |     262   →     187    (-28.63%) |       35.92 s  →       34.83 s    (-3.03%) | 
- │ │ │ │   │ ├ sirius::Local_operator::apply_h                         |       55.46 ms →       80.95 ms  (+45.96%) |     262   →     187    (-28.63%) |       14.53 s  →       15.14 s    (+4.18%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::remap_forward                   |        1.88 μs →        1.96 μs   (+4.42%) |     262   →     187    (-28.63%) |      491.86 μs →      366.59 μs  (-25.47%) | 
+ │ │ │ │   │ │ │ └ sddk::matrix_storage::set_num_extra                 |        1.58 μs →        1.70 μs   (+7.27%) |     262   →     187    (-28.63%) |      415.23 μs →      317.90 μs  (-23.44%) | 
+ │ │ │ │   │ │ ├ sddk::matrix_storage::set_num_extra                   |      360.47 ns →      331.10 ns   (-8.15%) |     262   →     187    (-28.63%) |       94.44 μs →       61.92 μs  (-34.44%) | 
- │ │ │ │   │ │ └ sddk::matrix_storage::remap_backward                  |      420.34 ns →      501.72 ns  (+19.36%) |     262   →     187    (-28.63%) |      110.13 μs →       93.82 μs  (-14.81%) | 
+ │ │ │ │   │ ├ sirius::Beta_projectors_base::generate                  |        7.45 ms →        7.63 ms   (+2.41%) |     262   →     187    (-28.63%) |        1.95 s  →        1.43 s   (-26.90%) | 
- │ │ │ │   │ ├ sirius::Beta_projectors_base::inner                     |       25.24 ms →       34.58 ms  (+36.99%) |     262   →     187    (-28.63%) |        6.61 s  →        6.47 s    (-2.22%) | 
- │ │ │ │   │ └ sirius::Non_local_operator::apply                       |       24.47 ms →       31.55 ms  (+28.93%) |     524   →     374    (-28.63%) |       12.82 s  →       11.80 s    (-7.98%) | 
- │ │ │ │   ├ sddk::orthogonalize                                       |       35.87 ms →       50.59 ms  (+41.02%) |     262   →     187    (-28.63%) |        9.40 s  →        9.46 s    (+0.65%) | 
- │ │ │ │   │ ├ sddk::wf_inner                                          |        6.23 ms →        8.77 ms  (+40.78%) |     498   →     349    (-29.92%) |        3.10 s  →        3.06 s    (-1.34%) | 
+ │ │ │ │   │ │ ├ sddk::wf_inner|scale                                  |       54.93 ns →       50.66 ns   (-7.76%) |     498   →     349    (-29.92%) |       27.35 μs →       17.68 μs  (-35.36%) | 
- │ │ │ │   │ │ ├ sddk::wf_inner|pw                                     |        5.11 ms →        7.53 ms  (+47.36%) |     498   →     349    (-29.92%) |        2.55 s  →        2.63 s    (+3.27%) | 
- │ │ │ │   │ │ └ sddk::wf_inner|scale_back                             |       28.62 ns →       79.97 ns (+179.40%) |     498   →     349    (-29.92%) |       14.25 μs →       27.91 μs  (+95.80%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|tmtrx                               |      656.51 μs →      940.47 μs  (+43.25%) |     262   →     187    (-28.63%) |      172.01 ms →      175.87 ms   (+2.24%) | 
- │ │ │ │   │ ├ sddk::orthogonalize|transform                           |       10.30 ms →       14.50 ms  (+40.74%) |     262   →     187    (-28.63%) |        2.70 s  →        2.71 s    (+0.45%) | 
- │ │ │ │   │ └ sddk::wf_trans                                          |       14.51 ms →       21.68 ms  (+49.39%) |     236   →     162    (-31.36%) |        3.42 s  →        3.51 s    (+2.55%) | 
- │ │ │ │   │   └ sddk::wf_trans|pw                                     |        4.84 ms →        7.23 ms  (+49.40%) |     708   →     486    (-31.36%) |        3.42 s  →        3.51 s    (+2.55%) | 
- │ │ │ │   ├ sirius::Band::set_subspace_mtrx                           |       10.38 ms →       14.31 ms  (+37.93%) |     262   →     187    (-28.63%) |        2.72 s  →        2.68 s    (-1.56%) | 
- │ │ │ │   │ └ sddk::wf_inner                                          |       10.18 ms →       14.05 ms  (+38.04%) |     262   →     187    (-28.63%) |        2.67 s  →        2.63 s    (-1.48%) | 
- │ │ │ │   │   ├ sddk::wf_inner|scale                                  |       27.11 ns →       44.86 ns  (+65.50%) |     262   →     187    (-28.63%) |        7.10 μs →        8.39 μs  (+18.12%) | 
- │ │ │ │   │   ├ sddk::wf_inner|pw                                     |        9.06 ms →       12.82 ms  (+41.44%) |     262   →     187    (-28.63%) |        2.37 s  →        2.40 s    (+0.95%) | 
- │ │ │ │   │   └ sddk::wf_inner|scale_back                             |       47.18 ns →       56.82 ns  (+20.43%) |     262   →     187    (-28.63%) |       12.36 μs →       10.62 μs  (-14.04%) | 
- │ │ │ │   ├ Eigensolver_cuda|zheevdx                                  |       17.74 ms →       30.61 ms  (+72.61%) |     262   →     187    (-28.63%) |        4.65 s  →        5.72 s   (+23.20%) | 
- │ │ │ │   ├ sirius::residuals                                         |       13.12 ms →       19.18 ms  (+46.24%) |     252   →     185    (-26.59%) |        3.31 s  →        3.55 s    (+7.36%) | 
- │ │ │ │   │ ├ sddk::wf_trans                                          |       11.71 ms →       16.65 ms  (+42.26%) |     242   →     184    (-23.97%) |        2.83 s  →        3.06 s    (+8.16%) | 
- │ │ │ │   │ │ └ sddk::wf_trans|pw                                     |        5.85 ms →        8.33 ms  (+42.26%) |     484   →     368    (-23.97%) |        2.83 s  →        3.06 s    (+8.17%) | 
- │ │ │ │   │ └ sirius::normalized_preconditioned_residuals             |        1.71 ms →        2.32 ms  (+35.19%) |     242   →     184    (-23.97%) |      414.74 ms →      426.31 ms   (+2.79%) | 
- │ │ │ │   └ sirius::Band::diag_pseudo_potential_davidson|update_phi   |       53.74 ms →       73.51 ms  (+36.77%) |      85   →      66    (-22.35%) |        4.57 s  →        4.85 s    (+6.20%) | 
- │ │ │ │     └ sddk::wf_trans                                          |       31.46 ms →       45.04 ms  (+43.15%) |     144   →     107    (-25.69%) |        4.53 s  →        4.82 s    (+6.37%) | 
- │ │ │ │       └ sddk::wf_trans|pw                                     |       22.32 ms →       32.56 ms  (+45.90%) |     203   →     148    (-27.09%) |        4.53 s  →        4.82 s    (+6.37%) | 
- │ │ │ ├ sirius::Beta_projectors_base::dismiss                         |      424.92 ns →        1.14 μs (+167.44%) |      26   →      25     (-3.85%) |       11.05 μs →       28.41 μs (+157.15%) | 
- │ │ │ └ sirius::K_point_set::sync_band_energies                       |       41.03 μs →       61.10 μs  (+48.92%) |      26   →      25     (-3.85%) |        1.07 ms →        1.53 ms  (+43.19%) | 
  │ │ ├ sirius::K_point_set::find_band_occupancies                      |      614.87 μs →      586.77 μs   (-4.57%) |      26   →      25     (-3.85%) |       15.99 ms →       14.67 ms   (-8.24%) | 
  │ │ ├ sirius::Density::generate                                       |      777.44 ms →      768.06 ms   (-1.21%) |      26   →      25     (-3.85%) |       20.21 s  →       19.20 s    (-5.01%) | 
  │ │ │ ├ sirius::Density::generate_valence                             |      402.10 ms →      401.82 ms   (-0.07%) |      26   →      25     (-3.85%) |       10.45 s  →       10.05 s    (-3.91%) | 
- │ │ │ │ ├ sddk::matrix_storage::remap_forward                         |        3.63 μs →        4.09 μs  (+12.80%) |      26   →      25     (-3.85%) |       94.30 μs →      102.28 μs   (+8.46%) | 
  │ │ │ │ │ └ sddk::matrix_storage::set_num_extra                       |        3.35 μs →        3.66 μs   (+9.18%) |      26   →      25     (-3.85%) |       87.15 μs →       91.48 μs   (+4.98%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_dm                |      100.49 ms →      100.39 ms   (-0.10%) |      26   →      25     (-3.85%) |        2.61 s  →        2.51 s    (-3.94%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::prepare                     |       10.40 μs →       10.81 μs   (+3.95%) |      26   →      25     (-3.85%) |      270.40 μs →      270.26 μs   (-0.05%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::generate                    |        7.12 ms →        7.13 ms   (+0.02%) |      26   →      25     (-3.85%) |      185.24 ms →      178.16 ms   (-3.83%) | 
  │ │ │ │ │ ├ sirius::Beta_projectors_base::inner                       |       91.44 ms →       91.35 ms   (-0.10%) |      26   →      25     (-3.85%) |        2.38 s  →        2.28 s    (-3.94%) | 
- │ │ │ │ │ └ sirius::Beta_projectors_base::dismiss                     |      553.38 ns →      702.96 ns  (+27.03%) |      26   →      25     (-3.85%) |       14.39 μs →       17.57 μs  (+22.14%) | 
  │ │ │ │ ├ sirius::Density::add_k_point_contribution_rg                |      162.72 ms →      162.67 ms   (-0.03%) |      26   →      25     (-3.85%) |        4.23 s  →        4.07 s    (-3.87%) | 
  │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        1.65 ms →        1.65 ms   (-0.36%) |      26   →      25     (-3.85%) |       42.96 ms →       41.16 ms   (-4.19%) | 
  │ │ │ │ └ sirius::Density::augment                                    |       88.38 ms →       88.38 ms   (+0.00%) |      26   →      25     (-3.85%) |        2.30 s  →        2.21 s    (-3.84%) | 
  │ │ │ │   └ sirius::Density::generate_rho_aug                         |       88.15 ms →       88.15 ms   (+0.00%) |      26   →      25     (-3.85%) |        2.29 s  →        2.20 s    (-3.84%) | 
  │ │ │ ├ sirius::Field4D::symmetrize                                   |      279.78 ms →      272.31 ms   (-2.67%) |      26   →      25     (-3.85%) |        7.27 s  →        6.81 s    (-6.42%) | 
  │ │ │ │ └ sirius::symmetrize_function|fpw                             |      279.78 ms →      272.31 ms   (-2.67%) |      26   →      25     (-3.85%) |        7.27 s  →        6.81 s    (-6.42%) | 
  │ │ │ │   ├ sddk::Gvec_shells::remap_forward                          |       24.63 ms →       24.45 ms   (-0.76%) |      26   →      25     (-3.85%) |      640.50 ms →      611.16 ms   (-4.58%) | 
  │ │ │ │   ├ sirius::symmetrize_function|fpw|local                     |      230.81 ms →      223.47 ms   (-3.18%) |      26   →      25     (-3.85%) |        6.00 s  →        5.59 s    (-6.90%) | 
  │ │ │ │   └ sddk::Gvec_shells::remap_backward                         |       23.14 ms →       23.19 ms   (+0.20%) |      26   →      25     (-3.85%) |      601.71 ms →      579.71 ms   (-3.66%) | 
  │ │ │ ├ sirius::Density::symmetrize_density_matrix                    |       81.08 ms →       80.89 ms   (-0.23%) |      26   →      25     (-3.85%) |        2.11 s  →        2.02 s    (-4.07%) | 
+ │ │ │ └ sirius::Smooth_periodic_function::fft_transform               |       10.88 ms →        9.45 ms  (-13.13%) |      26   →      25     (-3.85%) |      282.93 ms →      236.32 ms  (-16.47%) | 
  │ │ ├ sirius::Density::mix                                            |      219.01 ms →      217.27 ms   (-0.80%) |      26   →      25     (-3.85%) |        5.69 s  →        5.43 s    (-4.61%) | 
  │ │ │ ├ sirius::Density::mixer_input                                  |      917.15 μs →      964.05 μs   (+5.11%) |      26   →      25     (-3.85%) |       23.85 ms →       24.10 ms   (+1.07%) | 
  │ │ │ ├ sirius::Periodic_function|inner                               |       10.75 ms →       10.64 ms   (-1.03%) |     334   →     319     (-4.49%) |        3.59 s  →        3.39 s    (-5.48%) | 
  │ │ │ │ └ sirius::Periodic_function|inner_local                       |       10.50 ms →       10.44 ms   (-0.57%) |     334   →     319     (-4.49%) |        3.51 s  →        3.33 s    (-5.04%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function|inner_local              |       10.50 ms →       10.44 ms   (-0.57%) |     334   →     319     (-4.49%) |        3.51 s  →        3.33 s    (-5.04%) | 
+ │ │ │ └ sirius::Density::mixer_output                                 |        6.76 ms →        6.21 ms   (-8.21%) |      26   →      25     (-3.85%) |      175.76 ms →      155.13 ms  (-11.74%) | 
+ │ │ │   └ sirius::Smooth_periodic_function::fft_transform             |        5.91 ms →        5.35 ms   (-9.53%) |      26   →      25     (-3.85%) |      153.61 ms →      133.63 ms  (-13.01%) | 
  │ │ ├ sirius::Potential::generate                                     |      567.60 ms →      579.45 ms   (+2.09%) |      26   →      25     (-3.85%) |       14.76 s  →       14.49 s    (-1.84%) | 
  │ │ │ ├ sirius::Potential::poisson                                    |      125.29 ms →      136.75 ms   (+9.15%) |      26   →      25     (-3.85%) |        3.26 s  →        3.42 s    (+4.95%) | 
+ │ │ │ │ ├ sirius::Smooth_periodic_function::fft_transform             |        6.05 ms →        5.36 ms  (-11.38%) |      26   →      25     (-3.85%) |      157.34 ms →      134.07 ms  (-14.79%) | 
+ │ │ │ │ └ sirius::Periodic_function|inner                             |       11.36 ms →       10.27 ms   (-9.59%) |      26   →      25     (-3.85%) |      295.41 ms →      256.81 ms  (-13.07%) | 
+ │ │ │ │   └ sirius::Periodic_function|inner_local                     |       11.34 ms →       10.19 ms  (-10.15%) |      26   →      25     (-3.85%) |      294.89 ms →      254.76 ms  (-13.61%) | 
+ │ │ │ │     └ sirius::Smooth_periodic_function|inner_local            |       11.34 ms →       10.19 ms  (-10.15%) |      26   →      25     (-3.85%) |      294.87 ms →      254.75 ms  (-13.61%) | 
  │ │ │ ├ sirius::Periodic_function::add                                |      548.40 μs →      544.46 μs   (-0.72%) |      52   →      50     (-3.85%) |       28.52 ms →       27.22 ms   (-4.54%) | 
  │ │ │ ├ sirius::Potential::xc                                         |       49.08 ms →       49.07 ms   (-0.02%) |      26   →      25     (-3.85%) |        1.28 s  →        1.23 s    (-3.86%) | 
  │ │ │ │ └ sirius::Potential::xc_rg_nonmagnetic                        |       46.67 ms →       46.64 ms   (-0.06%) |      26   →      25     (-3.85%) |        1.21 s  →        1.17 s    (-3.90%) | 
  │ │ │ │   ├ sirius::Smooth_periodic_function                          |        3.08 ms →        3.10 ms   (+0.63%) |      52   →      50     (-3.85%) |      160.23 ms →      155.04 ms   (-3.24%) | 
  │ │ │ │   └ sirius::Smooth_periodic_function::fft_transform           |        5.46 ms →        5.45 ms   (-0.19%) |      26   →      25     (-3.85%) |      141.84 ms →      136.13 ms   (-4.03%) | 
  │ │ │ ├ sirius::Smooth_periodic_function::fft_transform               |        6.51 ms →        6.59 ms   (+1.32%) |      26   →      25     (-3.85%) |      169.17 ms →      164.81 ms   (-2.58%) | 
  │ │ │ ├ sirius::Potential::generate_D_operator_matrix                 |       91.04 ms →       91.18 ms   (+0.16%) |      26   →      25     (-3.85%) |        2.37 s  →        2.28 s    (-3.69%) | 
  │ │ │ └ sirius::Potential::generate_PAW_effective_potential           |      293.25 ms →      293.40 ms   (+0.05%) |      26   →      25     (-3.85%) |        7.62 s  →        7.34 s    (-3.80%) | 
  │ │ ├ sirius::Field4D::symmetrize                                     |      288.61 ms →      278.13 ms   (-3.63%) |      26   →      25     (-3.85%) |        7.50 s  →        6.95 s    (-7.34%) | 
  │ │ │ └ sirius::symmetrize_function|fpw                               |      288.61 ms →      278.13 ms   (-3.63%) |      26   →      25     (-3.85%) |        7.50 s  →        6.95 s    (-7.34%) | 
  │ │ │   ├ sddk::Gvec_shells::remap_forward                            |       27.44 ms →       27.75 ms   (+1.10%) |      26   →      25     (-3.85%) |      713.54 ms →      693.64 ms   (-2.79%) | 
  │ │ │   ├ sirius::symmetrize_function|fpw|local                       |      233.42 ms →      222.64 ms   (-4.62%) |      26   →      25     (-3.85%) |        6.07 s  →        5.57 s    (-8.29%) | 
  │ │ │   └ sddk::Gvec_shells::remap_backward                           |       23.88 ms →       23.90 ms   (+0.09%) |      26   →      25     (-3.85%) |      620.98 ms →      597.61 ms   (-3.76%) | 
  │ │ ├ sirius::Smooth_periodic_function::fft_transform                 |        5.47 ms →        5.88 ms   (+7.63%) |      26   →      25     (-3.85%) |      142.12 ms →      147.08 ms   (+3.49%) | 
  │ │ ├ sirius::Periodic_function|inner                                 |       10.67 ms →       10.65 ms   (-0.24%) |     182   →     175     (-3.85%) |        1.94 s  →        1.86 s    (-4.08%) | 
  │ │ │ └ sirius::Periodic_function|inner_local                         |       10.48 ms →       10.37 ms   (-1.00%) |     182   →     175     (-3.85%) |        1.91 s  →        1.82 s    (-4.81%) | 
  │ │ │   └ sirius::Smooth_periodic_function|inner_local                |       10.48 ms →       10.37 ms   (-1.00%) |     182   →     175     (-3.85%) |        1.91 s  →        1.81 s    (-4.81%) | 
  │ │ ├ sirius::Smooth_periodic_function|inner                          |       10.20 ms →       10.13 ms   (-0.72%) |      78   →      75     (-3.85%) |      795.80 ms →      759.71 ms   (-4.54%) | 
  │ │ │ └ sirius::Smooth_periodic_function|inner_local                  |       10.09 ms →        9.88 ms   (-2.12%) |      78   →      75     (-3.85%) |      787.01 ms →      740.74 ms   (-5.88%) | 
  │ │ ├ sirius::Periodic_function::integrate                            |        9.93 ms →       10.40 ms   (+4.76%) |      26   →      25     (-3.85%) |      258.06 ms →      259.95 ms   (+0.73%) | 
- │ │ └ sirius::Density::get_magnetisation                              |      129.89 μs →      179.06 μs  (+37.85%) |      26   →      25     (-3.85%) |        3.38 ms →        4.48 ms  (+32.55%) | 
- │ │   └ sirius::Density::compute_atomic_mag_mom                       |      125.24 μs →      174.27 μs  (+39.15%) |      26   →      25     (-3.85%) |        3.26 ms →        4.36 ms  (+33.79%) | 
  │ ├ sirius::Smooth_periodic_function::gather_f_pw                     |        5.03 ms →        5.07 ms   (+0.71%) |       2   →       2              |       10.06 ms →       10.14 ms   (+0.71%) | 
  │ ├ sirius::Periodic_function|inner                                   |       10.22 ms →       10.50 ms   (+2.76%) |       6   →       6              |       61.30 ms →       62.99 ms   (+2.76%) | 
  │ │ └ sirius::Periodic_function|inner_local                           |       10.15 ms →       10.49 ms   (+3.27%) |       6   →       6              |       60.93 ms →       62.92 ms   (+3.27%) | 
  │ │   └ sirius::Smooth_periodic_function|inner_local                  |       10.15 ms →       10.49 ms   (+3.27%) |       6   →       6              |       60.93 ms →       62.92 ms   (+3.27%) | 
  │ └ sirius::Smooth_periodic_function|inner                            |        9.75 ms →       10.44 ms   (+7.06%) |       3   →       3              |       29.25 ms →       31.31 ms   (+7.06%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |        9.63 ms →       10.43 ms   (+8.33%) |       3   →       3              |       28.88 ms →       31.29 ms   (+8.33%) | 
  ├ sirius::Periodic_function|inner                                     |       10.21 ms →       10.26 ms   (+0.49%) |       2   →       2              |       20.42 ms →       20.52 ms   (+0.49%) | 
  │ └ sirius::Periodic_function|inner_local                             |       10.18 ms →       10.25 ms   (+0.74%) |       2   →       2              |       20.35 ms →       20.50 ms   (+0.74%) | 
  │   └ sirius::Smooth_periodic_function|inner_local                    |       10.18 ms →       10.25 ms   (+0.74%) |       2   →       2              |       20.35 ms →       20.50 ms   (+0.74%) | 
  ├ sirius::Smooth_periodic_function|inner                              |        9.70 ms →        9.72 ms   (+0.24%) |       1   →       1              |        9.70 ms →        9.72 ms   (+0.24%) | 
  │ └ sirius::Smooth_periodic_function|inner_local                      |        9.64 ms →        9.71 ms   (+0.78%) |       1   →       1              |        9.64 ms →        9.71 ms   (+0.78%) | 
+ └ sirius::finalize                                                    |      239.16 ms →      202.58 ms  (-15.30%) |       1   →       1              |      239.16 ms →      202.58 ms  (-15.30%) | 
  ====================================================================================================================================================================================================
```
