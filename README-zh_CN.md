# ChatGPT 代码注释生成器

[![许可证](https://img.shields.io/cran/l/pixarfilms)](LICENSE)

[English](README.md) [简体中文](README-zh_CN.md)

欢迎使用 ChatGPT 代码注释生成器，ChatGPT是一个由 OpenAI 开发的强大语言模型。本仓库提供了一系列提示和指南，帮助您使用 ChatGPT 为您的代码生成高质量的注释。

## 概述

注释是任何文档完备的代码库的必要组成部分，为您的代码提供上下文和信息，以便自己和其他开发人员在项目中工作。本仓库提供了一系列提示和指南，可与 ChatGPT 配合使用，为您的代码生成准确而全面的注释。

## 使用说明

要使用本仓库中的提示和指南，请按照每个部分中提供的提示和指南操作。您可以直接将提示复制粘贴到 ChatGPT 中，为您的代码生成注释。如有需要，可以根据您项目的具体需求修改提示。

## 贡献

欢迎贡献本仓库！如果您有额外的提示或指南要分享，请随时提交拉取请求。

## 许可证

本仓库采用 CC0 1.0 通用许可证授权。有关详细信息，请参见 [LICENSE](LICENSE) 文件。

## 效果和研究过程
如果您对提示的效果或我的研究过程感到好奇，请查看 [研究过程](Research-Process.md) 获取更多信息。

## Prompts
按顺序输入 prompt 1-7，并将您的代码放在 prompt 8 中。

### prompt 1
```
I will give you a series of instructions on how to write docstrings of code 
snippets. Let's do it step by step.
After I enter "@#INSTRUCTION_START#@", the contents I write will be 
instructions, samples and examples. At this stage, instructions are the rules 
you need to follow when generating the output. Samples and examples are for 
your reference. Whatever I input at this stage, you need to reply "OK". 
When I enter "@#END_INSTRUCTION#@", you need to explain the instructions step 
by step to me.
After your reply, I will enter "#@CODE_START@#" to indicate the following 
contents are code snippets, and the code ends with "#@END_CODE@#". 
Do you understand? Reply "Yes" or "No".
```

### prompt 2
````
@#INSTRUCTION_START#@
Instruction 1: I want you to write docstrings for the code snippet in Google 
style. 
````

### prompt 3
````
Sample 1: I will give you a sample of the code snippets with docstrings, which
is for your reference.
The following contents are a sample of the code snippets with docstrings in 
Google style.
```Python
def module_level_function(param1, param2=None, *args, **kwargs):
    """This is an example of a module level function.

    Args:
        param1 (int): The first parameter.
        param2 (:obj:`str`, optional): The second parameter. Defaults to None.
            Second line of description should be indented.
        *args: Variable length argument list.
        **kwargs: Arbitrary keyword arguments.

    Returns:
        bool: True if successful, False otherwise.

    Raises:
        AttributeError: The ``Raises`` section is a list of all exceptions
            that are relevant to the interface.
        ValueError: If `param2` is equal to `param1`.

    """
    if param1 == param2:
        raise ValueError('param1 may not be equal to param2')
    return True


def example_generator(n):
    """Generators have a ``Yields`` section instead of a ``Returns`` section.

    Args:
        n (int): The upper limit of the range to generate, from 0 to `n` - 1.

    Yields:
        int: The next number in the range of 0 to `n` - 1.

    Examples:
        Examples should be written in doctest format, and should illustrate how
        to use the function.

        >>> print([i for i in example_generator(4)])
        [0, 1, 2, 3]

    """
    for i in range(n):
        yield i


class ExampleClass(object):
    """The summary line for a class docstring should fit on one line.

    Args:
        param1 (str): Description of `param1`.
        param2 (:obj:`int`, optional): Description of `param2`. Multiple lines 
            are supported.

    Attributes:
        attr1 (str): Description of `attr1`.
        attr2 (:obj:`int`, optional): Description of `attr2`.

    """
    def __init__(self, param1, param2):
        self.attr1 = param1
        self.attr2 = param2
```
````

### prompt 4
````
Instruction 2: When producing the output, keep the line length less or equal to 
80 characters.
````

### prompt 5
```
Instruction 3: When producing the output, skip the method body, and only keep 
the signature of class and method.
```

### prompt 6
````
Example 1: I will give you an example that shows you how you can generate
docstrings for me.
Here is an example code snippet I may input:
```Python
class Slicer:
    def __init__(self, country: File, output: Directory, _slice=True):
        self.__country_name = country.get_filename()
        self.__country_path = country.get_filepath()
        self.__slice = _slice
        self.__output_folder = output

    def __start(self):
        try:
            df = pd.read_csv(self.__country_path)
        except pd.errors.EmptyDataError:
            return
```
Here is an example code with docstrings that I want you reply:
```Python
class Slicer:
    """A class that slices a CSV file of disaster data for a specific country 
    into separate CSV files for each type of disaster.

    Args:
        country (File): The input CSV file of disaster data.
        output (Directory): The output directory for the sliced CSV files
        _slice (bool): Whether to slice the data by removing the first 5% of
            rows. Default is True.

    Attributes:
        __country_name (str): The name of the country derived from the input
            file name.
        __country_path (str): The path to the input file.
        __slice (bool): Whether to slice the data by removing the first 5% of
            rows.
        __output_folder (Directory): The output directory for the sliced CSV
            files.

    Methods:
        __start: Slices the input data and saves the sliced data as separate 
            CSV files for each type of disaster.
    """
    def __init__(self, country: File, output_folder: Directory, _slice=True):
        pass

    def __start(self):
        """
        Reads the input data, splits it by type of disaster, slices it for each
        disaster, and saves the sliced data.
        """
        pass
```
````

### prompt 7
```
@#END_INSTRUCTION#@
```

### prompt 8
````
Please write docstrings for the following code.
#@CODE_START@#

#@END_CODE@#
````
