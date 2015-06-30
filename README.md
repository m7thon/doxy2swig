# doxy2swig

Doxygen XML to SWIG docstring converter.

Converts Doxygen generated XML files into a file containing docstrings
that can be used by SWIG-1.3.x.  Note that you need to get SWIG
version > 1.3.23 or use Robin Dunn's docstring patch to be able to use
the resulting output.

# Usage:
```
doxy2swig.py [options] input.xml output.i

input.xml is your doxygen generated XML file and output.i is where the
output will be written (the file will be clobbered).


Options:
  -h, --help            show this help message and exit
  -f, --function-signature
                        include function signature in the documentation. This
                        is handy when not using swig auto-generated function
                        definitions %feature("autodoc", [0,1])
  -t, --type-info       include type information for arguments in function
                        signatures. This is similar to swig autodoc level 1
  -c, --constructor-list
                        generate a constructor list for class documentation.
                        Useful for target languages where the object
                        construction should be documented in the class
                        documentation.
  -a, --attribute-list  generate an attributes list for class documentation.
                        Useful for target languages where class attributes
                        should be documented in the class documentation.
  -o, --overloaded-functions
                        collect all documentation for overloaded functions.
                        Useful for target languages that have no concept of
                        overloaded functions, but also to avoid having to
                        attach the correct docstring to each function overload
                        manually
  -w W, --width=W       textwidth for wrapping (default: 80). Note that the
                        generated lines may include 2 additional spaces (for
                        markdown).
  -q, --quiet           be quiet and minimize output
```
