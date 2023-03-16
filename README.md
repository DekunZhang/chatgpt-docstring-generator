# ChatGPT Docstring Generator

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

[English](README.md) [简体中文](README-zh_CN.md)

Welcome to ChatGPT Docstring Generator, a collection of instructions designed to 
help you generate high-quality docstrings for your code using ChatGPT, a 
powerful language model developed by OpenAI.

## Overview

Docstrings are an essential component of any well-documented codebase, 
providing context and information about the purpose and functionality of your 
code to both yourself and other developers who may work on your project. This 
repository provides a series of prompts and guidelines that can be used with 
ChatGPT to generate accurate and comprehensive docstrings for your code.

## Instructions

The instructions in this repository can be used to generate clear, concise, and 
informative docstrings that will enhance the usability and maintainability of 
your codebase. Whether you're a seasoned developer looking to improve your 
documentation skills or a newcomer to the world of programming, these 
instructions can help you create high-quality docstrings for your code.

## Usage

To use these instructions, simply follow the prompts and guidelines provided in 
each section. You can copy and paste the prompts directly into ChatGPT to 
generate a docstring for your code. Feel free to modify the prompts as needed 
to suit the specific needs of your project.

## Contributing

Contributions to this repository are welcome! If you have additional prompts or 
guidelines that you'd like to share, please feel free to open a pull request. 

## License

This repository is licensed under the MIT license. See the [LICENSE](LICENSE) 
file for more information.

## Effects and Research Process
If you are curious about the effect of the prompts or my research process,
please checkout the [Research Process](Research-Process.md) for more 
information.

## Prompts
Input prompt 1-7 in sequence and put your code in prompt 8.

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
