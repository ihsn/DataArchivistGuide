Running validations and diagnostics
======================================

The Metadata Editor includes a useful series of diagnostic and validation
modules (see the drop down menu *Tools*): these range from very simple
validations (such as the *Tools-Validate Metadata*) to complex visual
displays that iterate through each variable and provides feedback to the
archivist at the variable level.

-  *Validate Metadata*: verifies that all mandatory fields are filled
   in.

-  *Validate External Resources*: verifies all mandatory fields in the
   External Resources are filled in.

-  *Health Check*: displays a popup window that provides some information
   and diagnostics regarding the R package. The Metadata Editor uses R
   to import and export the data. The health check option tells the which
   version of R is being used on the machine. In addition, the Health
   Check will provide information on the Environment Path and the result
   of the execution of the R script.

-  *Validate Dataset Relations*: this option is used to validate
   hierarchically related datasets. The ‘Base key variables’ should be
   the variables that uniquely identify a case within that file.

-  *Translation Manager*: provides the user with the ability to translate
   the interface of the Metadata Editor into any language. Selecting this
   option will display the Translation Manager interface. When using the
   option for the first time, the English template will be displayed with
   all the labels that require translation.


In addition to these validations, it is recommended that you generate
the DDI document (in the Editor, use the Export DDI” function) and
verify the size of the resulting [.xml] file. A fully documented survey
with a large number of variables should not produce a file larger than
10Mb. Very large DDI files often indicate errors in the selection of
summary statistics (for example, frequencies are produced for a variable
like the household ID in a sample household file).