# How can I log all commands and their outputs, including errors, to a file?

This post answers the question, "How can I log all commands and their outputs, including errors, to a file?"

## Log all Commands and their Outputs, Including Errors, to a File

```
exec&nbsp;&gt; &gt;(tee&nbsp;-i output.log) 2&gt;&amp;1
```

### Description

-   **Process Substitution Setup**:
    
-   The shell identifies the process substitution part **\>(tee -i output.log)**.
    
-   A subshell is created to execute **tee -i output.log**.
    
-   The subshell running **tee** provides a file descriptor (let's call it **FD1**) that acts like a temporary file.
    
-   **Exec Command with Stdout Redirection**:
    
-   **exec > FD1**: The exec command changes the file descriptor for the current shell.
    
-   The standard output (stdout, file descriptor 1) of the current shell is redirected to **FD1** (the file descriptor provided by the **tee** subshell).
    
-   **Stderr Redirection to Stdout**:
    
-   **2>&1**: The standard error (stderr, file descriptor 2) is redirected to the current destination of stdout (file descriptor 1).
    
-   Since stdout has already been redirected to **FD1** (the **tee** subshell), **stderr** will also be redirected to **FD1**.
    
-   **Execution of tee Command**:
    
-   The **tee** command reads from **FD1** (which now receives both **stdout** and **stderr** from the shell).
    
-   **tee** writes the received output to both **output.log** and the **console** (stdout of the **tee** subshell).
    

## Example Application

Trace and capture bash script execution.

```
set -x
exec&nbsp;&gt; &gt;(tee&nbsp;-i output.log) 2&gt;&amp;1
bash script
```

## Additional Information

See:

-   [<u><span>bash exec</span></u>](https://www.gnu.org/software/bash/manual/html_node/Bourne-Shell-Builtins.html#index-exec)
    
-   [<u><span>bash Redirections</span></u>](https://www.gnu.org/software/bash/manual/html_node/Redirections.html)
    
-   [<u><span>bash Process Substitution</span></u>](https://www.gnu.org/software/bash/manual/html_node/Process-Substitution.html) 
    
-   [<u><span>tee</span></u>](https://www.gnu.org/software/coreutils/manual/html_node/tee-invocation.html)

![gnu_logo_transparent](gnu_logo_transparent.png)