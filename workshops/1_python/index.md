# 1. Intro / How to manage your Python Project
30th October 2025 

For our first session, we (Sophie & Lawrence) gave an introduction to the workshop series and covered some tips & tricks on Python code development.

## Session Recording

```{iframe} https://liveuclac-my.sharepoint.com/personal/rmaplpb_ucl_ac_uk/_layouts/15/embed.aspx?UniqueId=1e425f23-8438-4b09-bc9c-74f4b9cbd7b0&embed=%7B%22ust%22%3Atrue%2C%22hv%22%3A%22CopyEmbedCode%22%7D&referrer=StreamWebApp&referrerScenario=EmbedDialog.Create>
:width: 100%

If you are having trouble viewing it above, try using the [link](https://liveuclac-my.sharepoint.com/personal/rmaplpb_ucl_ac_uk/_layouts/15/embed.aspx?UniqueId=1e425f23-8438-4b09-bc9c-74f4b9cbd7b0&embed=%7B%22ust%22%3Atrue%2C%22hv%22%3A%22CopyEmbedCode%22%7D&referrer=StreamWebApp&referrerScenario=EmbedDialog.Create) directly. 
```

```{note} You will need to be signed in with a UCL account to view our workshops recordings.
```

## Code examples

Below are some of the code examples that were shared during the session.


Here was an example of bad coding practice (hard coded values, poor variable naming, no comments or docstrings, etc.):

```{literalinclude} code_examples/example_bad_code.py
```

Then we looked at how argparse can be used to provide inputs to a function or script.

```{literalinclude} code_examples/argsparse_example.py
```
This can be useful when working with the cluster and submitting scripts or batch jobs where you may not want to hard code certain input parameters or arguments (like absolute filepaths). Here is an example bash script that can be used to submit the above code example. 

For full details and instructions on using the UCL CS Cluster, visit [the HPC website](www.hpc.cs.ucl.ac.uk).

```{literalinclude} code_examples/run_argsparse_example.sh
```

## Slides
To be updated.