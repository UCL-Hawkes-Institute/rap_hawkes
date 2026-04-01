Below are some of the code examples that were shared during the session.


Here was an example of bad coding practice (hard coded values, poor variable naming, no comments or docstrings, etc.):

```{literalinclude} code_examples/example_bad_code.py
```

Then we looked at how argparse can be used to provide inputs to a function or script.

```{literalinclude} code_examples/argsparse_example.py
:start-at: 1
```
This can be useful when working with the cluster and submitting scripts or batch jobs where you may not want to hard code certain input parameters or arguments (like absolute filepaths). Here is an example bash script that can be used to submit the above code example. 

For full details and instructions on using the UCL CS Cluster, visit [the HPC website](www.hpc.cs.ucl.ac.uk).

```{literalinclude} code_examples/run_argsparse_example.sh
```
