Microlab 1: Convergence study
===================================

Copy the test suite ``$MESA_DIR/star/test_suite/1.5M_with_diffusion`` somewhere outside ``$MESA_DIR``.

In the ``&star_job`` section of ``inlist_1.5M_with_diffusion``, add

.. code-block:: console

    write_profile_when_terminate = .true. 
    filename_for_profile_when_terminate = 'LOGS/mdcX_tdcY_nomaxdt/profile_mdcX_tdcY_nomaxdt_Xc010.data'


In the ``&controls`` section of ``inlist_1.5M_with_diffusion``, add

.. code-block:: console

    log_directory = ‘LOGS/mdcX_tdcY_nomaxdt’ 
    set_min_D_mix = .true. 
    min_D_mix =1d2 time_delta_coeff = Y 
    xa_central_lower_limit_species(1) = 'h1' 
    xa_central_lower_limit(1) = 0.1 

and change

.. code-block:: console

    D_mix_ignore_diffusion = 1d10 
    mesh_delta_coeff = X 
    max_years_for_timestep = 0 
    max_model_number = -1

Select a value for ``mesh_delta_coeff`` between 0.2 and 2.0, or a value for ``time_delta_coeff`` between 0.05 and 2.0. Set the other one equal to 0.5.

Run the model.