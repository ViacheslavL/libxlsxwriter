add_subdirectory(src)

set(xlsxw_test_bin_dir ${CMAKE_BINARY_DIR}/bin/test_functional)
set(xlsxw_test_data_dir ${xlsxw_test_bin_dir}/xlsx_files)
set(xlsxw_test_image_dir ${xlsxw_test_bin_dir}/images)

set(CMAKE_RUNTIME_OUTPUT_DIRECTORY ${xlsxw_test_bin_dir})

set(py_sources
    base_test_class.py
    conftest.py
    helper_functions.py
    test_array_formula.py
    test_autofilter.py
    test_chart_area.py
    test_chart_axis.py
    test_chart_bar.py
    test_chart_column.py
    test_chart_doughnut.py
    test_chart_line.py
    test_chart_order.py
    test_chart_pie.py
    test_chart_radar.py
    test_chart_scatter.py
    test_chart_size.py
    test_chart_sparse.py
    test_chart_str.py
    test_chart_title.py
    test_default_row.py
    test_defined_name.py
    test_escapes.py
    test_fit_to_pages.py
    test_formatting.py
    test_gridlines.py
    test_hyperlink.py
    test_image.py
    test_merge_range.py
    test_misc.py
    test_optimize.py
    test_page_breaks.py
    test_page_setup.py
    test_panes.py
    test_print_area.py
    test_print_options.py
    test_print_scale.py
    test_properties.py
    test_protect.py
    test_repeat.py
    test_row_col_format.py
    test_set_selection.py
    test_set_start_page.py
    test_simple.py
    test_tmpdir.py
    test_types.py
    test_write_data.py)

foreach(py_source ${py_sources})
    configure_file(${py_source} ${xlsxw_test_bin_dir}/${py_source} COPYONLY)
endforeach()

set(xlsxw_test_env PATH=${xlsxw_test_bin_dir}:$ENV{PATH}
    XLSXW_DATA_DIR=${xlsxw_test_data_dir} XLSXW_EXE_DIR=${xlsxw_test_bin_dir})

add_test(NAME functional_all COMMAND
    py.test ${xlsxw_test_bin_dir} -v --exec_dir=${xlsxw_test_bin_dir}
    --data_dir=${xlsxw_test_data_dir})

set(xlsxw_baselines
    array_formula01.xlsx
    array_formula02.xlsx
    autofilter00.xlsx
    autofilter01.xlsx
    chart_area01.xlsx
    chart_area02.xlsx
    chart_area03.xlsx
    chart_axis01.xlsx
    chart_axis02.xlsx
    chart_axis04.xlsx
    chart_axis05.xlsx
    chart_axis06.xlsx
    chart_axis07.xlsx
    chart_bar01.xlsx
    chart_bar02.xlsx
    chart_bar03.xlsx
    chart_bar04.xlsx
    chart_bar05.xlsx
    chart_bar06.xlsx
    chart_bar08.xlsx
    chart_bar09.xlsx
    chart_bar10.xlsx
    chart_bar11.xlsx
    chart_bar19.xlsx
    chart_bar20.xlsx
    chart_bar21.xlsx
    chart_bar22.xlsx
    chart_bar51.xlsx
    chart_column01.xlsx
    chart_column02.xlsx
    chart_column03.xlsx
    chart_column05.xlsx
    chart_column06.xlsx
    chart_column07.xlsx
    chart_column08.xlsx
    chart_column09.xlsx
    chart_column10.xlsx
    chart_column11.xlsx
    chart_column12.xlsx
    chart_doughnut01.xlsx
    chart_doughnut02.xlsx
    chart_doughnut03.xlsx
    chart_doughnut04.xlsx
    chart_doughnut05.xlsx
    chart_doughnut06.xlsx
    chart_line01.xlsx
    chart_order01.xlsx
    chart_pie01.xlsx
    chart_pie05.xlsx
    chart_radar01.xlsx
    chart_radar02.xlsx
    chart_radar03.xlsx
    chart_scatter01.xlsx
    chart_scatter02.xlsx
    chart_scatter03.xlsx
    chart_scatter04.xlsx
    chart_scatter05.xlsx
    chart_size01.xlsx
    chart_size04.xlsx
    chart_sparse01.xlsx
    chart_str01.xlsx
    chart_str02.xlsx
    chart_title01.xlsx
    chart_title02.xlsx
    data01.xlsx
    data02.xlsx
    data03.xlsx
    data04.xlsx
    data05.xlsx
    data06.xlsx
    data07.xlsx
    default_row01.xlsx
    default_row02.xlsx
    default_row03.xlsx
    default_row05.xlsx
    defined_name01.xlsx
    defined_name02.xlsx
    defined_name03.xlsx
    defined_name04.xlsx
    escapes04.xlsx
    escapes05.xlsx
    escapes06.xlsx
    escapes07.xlsx
    escapes08.xlsx
    firstsheet01.xlsx
    fit_to_pages01.xlsx
    fit_to_pages02.xlsx
    fit_to_pages03.xlsx
    fit_to_pages04.xlsx
    fit_to_pages05.xlsx
    format01.xlsx
    format02.xlsx
    format06.xlsx
    format07.xlsx
    format08.xlsx
    format09.xlsx
    format10.xlsx
    format12.xlsx
    gh42_01.xlsx
    gh42_02.xlsx
    gridlines01.xlsx
    hide01.xlsx
    hyperlink01.xlsx
    hyperlink02.xlsx
    hyperlink03.xlsx
    hyperlink04.xlsx
    hyperlink05.xlsx
    hyperlink06.xlsx
    hyperlink07.xlsx
    hyperlink08.xlsx
    hyperlink09.xlsx
    hyperlink10.xlsx
    hyperlink11.xlsx
    hyperlink12.xlsx
    hyperlink13.xlsx
    hyperlink14.xlsx
    hyperlink15.xlsx
    hyperlink16.xlsx
    hyperlink17.xlsx
    hyperlink18.xlsx
    hyperlink19.xlsx
    hyperlink20.xlsx
    image01.xlsx
    image02.xlsx
    image03.xlsx
    image04.xlsx
    image05.xlsx
    image07.xlsx
    image08.xlsx
    image09.xlsx
    image10.xlsx
    image11.xlsx
    image12.xlsx
    image13.xlsx
    image14.xlsx
    image15.xlsx
    image16.xlsx
    image17.xlsx
    image18.xlsx
    image19.xlsx
    image22.xlsx
    image23.xlsx
    image24.xlsx
    image25.xlsx
    image26.xlsx
    image27.xlsx
    image28.xlsx
    image29.xlsx
    image30.xlsx
    image31.xlsx
    image32.xlsx
    image33.xlsx
    image34.xlsx
    image35.xlsx
    landscape01.xlsx
    merge_range01.xlsx
    merge_range02.xlsx
    merge_range03.xlsx
    merge_range04.xlsx
    merge_range05.xlsx
    optimize01.xlsx
    optimize02.xlsx
    optimize06.xlsx
    optimize21.xlsx
    optimize22.xlsx
    optimize23.xlsx
    optimize24.xlsx
    optimize25.xlsx
    optimize26.xlsx
    page_breaks01.xlsx
    page_breaks02.xlsx
    page_breaks03.xlsx
    page_breaks04.xlsx
    page_breaks05.xlsx
    page_breaks06.xlsx
    page_view01.xlsx
    panes01.xlsx
    print_across01.xlsx
    print_area01.xlsx
    print_area02.xlsx
    print_area03.xlsx
    print_area04.xlsx
    print_area05.xlsx
    print_area06.xlsx
    print_area07.xlsx
    print_options01.xlsx
    print_options02.xlsx
    print_options03.xlsx
    print_options04.xlsx
    print_options05.xlsx
    print_options06.xlsx
    print_scale01.xlsx
    print_scale02.xlsx
    properties01.xlsx
    properties02.xlsx
    properties03.xlsx
    properties04.xlsx
    properties05.xlsx
    protect01.xlsx
    protect02.xlsx
    protect03.xlsx
    repeat01.xlsx
    repeat02.xlsx
    repeat03.xlsx
    repeat04.xlsx
    repeat05.xlsx
    repeat06.xlsx
    row_col_format01.xlsx
    row_col_format02.xlsx
    row_col_format03.xlsx
    row_col_format04.xlsx
    row_col_format05.xlsx
    row_col_format06.xlsx
    row_col_format07.xlsx
    row_col_format08.xlsx
    row_col_format09.xlsx
    row_col_format10.xlsx
    row_col_format11.xlsx
    row_col_format12.xlsx
    row_col_format13.xlsx
    row_col_format14.xlsx
    row_col_format15.xlsx
    row_col_format16.xlsx
    row_col_format17.xlsx
    row_col_format18.xlsx
    set_selection01.xlsx
    set_selection02.xlsx
    set_start_page01.xlsx
    set_start_page02.xlsx
    set_start_page03.xlsx
    shared_strings01.xlsx
    simple01.xlsx
    simple02.xlsx
    simple03.xlsx
    simple04.xlsx
    simple05.xlsx
    tab_color01.xlsx
    types02.xlsx
    types08.xlsx)

foreach(baseline ${xlsxw_baselines})
    configure_file(xlsx_files/${baseline}
        ${xlsxw_test_data_dir}/${baseline} COPYONLY)
endforeach()

set(xlsxw_images
    black_150e.png
    black_150.jpg
    black_150.png
    black_300e.png
    black_300.jpg
    black_300.png
    black_72e.png
    black_72.jpg
    black_72.png
    black_96.jpg
    black_96.png
    blue.jpg
    blue.png
    grey.jpg
    grey.png
    issue32.png
    logo.png
    mylogo.png
    red_208.png
    red_64x20.png
    red.bmp
    red.jpg
    red.png
    red_readonly.png
    train.jpg
    yellow.jpg
    yellow.png
    zero_dpi.jpg)

foreach(image ${xlsxw_images})
    configure_file(src/images/${image}
        ${xlsxw_test_image_dir}/${image} COPYONLY)
endforeach()
