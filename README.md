# python_test0
software test
def get_path_condition_expression_function(
        string_parameter,
        hardware_difference_function_list_parameter,
        hardware_list_parameter):
    """
    功能描述：获取路径条件表达式
    参数：string_parameter字符串参数，
         hardware_difference_function_list_parameter硬件差异函数列表参数，
         hardware_list_parameter硬件列表参数
    返回值：string_parameter字符串参数
    """
    for i, temp_str in enumerate(hardware_difference_function_list_parameter):
        # 条件语句中连续存在多个底层函数时，组合判断条件，修改时间2022-4-27
        if i < len(hardware_difference_function_list_parameter) - 1:
            if temp_str in string_parameter:
                # print(string_parameter)
                # print('======')
                if temp_str + '()' in string_parameter:
                    true_branch_string = string_parameter.replace( \
                        temp_str + '()', '*' + hardware_list_parameter[i])
                    false_branch_string = string_parameter.replace( \
                        temp_str + '()', '*' + hardware_list_parameter[i + 1])
                else:  # 条件中仅存在差异函数名时的组合情况，修改时间2022-4-27
                    true_branch_string = string_parameter.replace( \
                        temp_str, '*' + hardware_list_parameter[i])
                    false_branch_string = string_parameter.replace( \
                        temp_str, '*' + hardware_list_parameter[i + 1])
                string_parameter = "%s@%s" % ( \
                    true_branch_string, false_branch_string)
        print(string_parameter)
    return string_parameter

