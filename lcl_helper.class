CLASS lcl_helper DEFINITION.
  PUBLIC SECTION.
    CLASS-METHODS:
      simple_alv
        IMPORTING
          iv_start_col  TYPE i         DEFAULT 25
          iv_start_line TYPE i         DEFAULT 6
          iv_end_col    TYPE i         DEFAULT 100
          iv_end_line   TYPE i         DEFAULT 10
          iv_popup      TYPE abap_bool DEFAULT abap_false
        CHANGING
          ct_table      TYPE ANY TABLE.
ENDCLASS.                    "lcl_helper DEFINITION

*----------------------------------------------------------------------*
*       CLASS lcl_helper IMPLEMENTATION
*----------------------------------------------------------------------*
*
*----------------------------------------------------------------------*
CLASS lcl_helper IMPLEMENTATION.
  METHOD simple_alv.
    DATA lo_alv TYPE REF TO cl_salv_table.

    TRY.
        cl_salv_table=>factory(
          IMPORTING
            r_salv_table = lo_alv
          CHANGING
            t_table      = ct_table[] ).

      CATCH cx_salv_msg.
    ENDTRY.

    DATA: lr_functions TYPE REF TO cl_salv_functions_list.

    lr_functions = lo_alv->get_functions( ).
    lr_functions->set_all( 'X' ).

    IF lo_alv IS BOUND.
      IF iv_popup = 'X'.   "display as popup?
        lo_alv->set_screen_popup(
          start_column = iv_start_col
          end_column   = iv_end_col
          start_line   = iv_start_line
          end_line     = iv_end_line ).
      ENDIF.

      lo_alv->display( ).

    ENDIF.
  ENDMETHOD.                    "simple_alv
ENDCLASS.                    "lcl_helper IMPLEMENTATION
