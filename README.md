# doxy2swig (improved)

Doxygen XML to SWIG docstring converter (improved version).

Converts Doxygen generated XML files into a file containing docstrings
for use by SWIG.

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

# Note:

To attach docstrings to classes with SWIG for python and using the `-builtin` option,
a version of SWIG >= 3.0.7 (currently this means the development version) is required.
Without this, the class documentation including constructor lists (`-c`) and attribute
lists (`-a`) will not be available from python.