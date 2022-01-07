[![.github/workflows/ant.yml](https://github.com/Funz/plugin-Jupyter/actions/workflows/ant.yml/badge.svg)](https://github.com/Funz/plugin-Jupyter/actions/workflows/ant.yml)

# Funz plugin: Jupyter

This plugin is dedicated to launch Jupyter calculations from Funz.
It supports the following syntax and features:

* Input
  * file type supported: '*.ipynb', any other format for resources
  * parameter syntax: 
    * variable syntax: `?[...]`
    * formula syntax: `${...}`
    * comment char: `#`
  * example input file:
  ```
  {
   "cells": [
    {
     "cell_type": "markdown",
     "metadata": {},
     "source": [{
      "def branin(x1,x2):\n",
      "    x1 = x1*15-5\n",
      "    x2 = x2*15\n",
      "\n",
      "    return (x2 - 5/(4*m.pi**2)*(x1**2) + 5/m.pi*x1 -6 )**2 + 10*(1-1/(8*m.pi))*m.cos(x1) +10"
     ]
    },
    {
     "cell_type": "raw",
     "metadata": {},
     "source": [
      "then, eval branin:"
     ]
    },
    {
     "cell_type": "code",
     "execution_count": null,
     "metadata": {},
     "outputs": [],
     "source": [
      "print('z={0}'.format( branin( ?[x1~[1,2]] , ${?[x2] +1.23} ) ) )"
     ]
    },
    {
     "cell_type": "code",
     "execution_count": null,
     "metadata": {},
     "outputs": [],
     "source": []
    }
   ],
   "metadata": {
    "kernelspec": {
     "display_name": "Python 3",
     "language": "python",
     "name": "python3"
    },
    "language_info": {
     "codemirror_mode": {
      "name": "ipython",
      "version": 3
     },
     "file_extension": ".py",
     "mimetype": "text/x-python",
     "name": "python",
     "nbconvert_exporter": "python",
     "pygments_lexer": "ipython3",
     "version": "3.7.6"
    }
   },
   "nbformat": 4,
   "nbformat_minor": 4
  }
  ```
     * will identify input:
       * x1, expected to vary inside [1,2]
       * x2, expected to vary inside [0,1] (by default)
     * replace `${?[x2] + 1.23}` expression by its evaluation

* Output
  * file type supported: '*.ipynb'
  * read any named value printed with `=`, like `print("z={0}".format(1.234))`
  * example output file:
  ```
  {
   "cells": [
    {
     "cell_type": "markdown",
     "metadata": {},
     "source": [
      "# Branin in jupyter"
     ]
    },
    {
     "cell_type": "code",
     "execution_count": 1,
     "metadata": {
      "execution": {
       "iopub.execute_input": "2022-01-07T13:37:11.375854Z",
       "iopub.status.busy": "2022-01-07T13:37:11.374259Z",
       "iopub.status.idle": "2022-01-07T13:37:11.395234Z",
       "shell.execute_reply": "2022-01-07T13:37:11.392893Z"
      }
     },
     "outputs": [],
     "source": [
      "import math as m\n",
      "def branin(x1,x2):\n",
      "    x1 = x1*15-5\n",
      "    x2 = x2*15\n",
      "\n",
      "    return (x2 - 5/(4*m.pi**2)*(x1**2) + 5/m.pi*x1 -6 )**2 + 10*(1-1/(8*m.pi))*m.cos(x1) +10"
     ]
    },
    {
     "cell_type": "raw",
     "metadata": {},
     "source": [
      "then, eval branin:"
     ]
    },
    {
     "cell_type": "code",
     "execution_count": 2,
     "metadata": {
      "execution": {
       "iopub.execute_input": "2022-01-07T13:37:11.405704Z",
       "iopub.status.busy": "2022-01-07T13:37:11.404308Z",
       "iopub.status.idle": "2022-01-07T13:37:11.411921Z",
       "shell.execute_reply": "2022-01-07T13:37:11.413079Z"
      }
     },
     "outputs": [
      {
       "name": "stdout",
       "output_type": "stream",
       "text": [
        "z=3.000715003051446\n"
       ]
      }
     ],
     "source": [
      "print('z={0}'.format( branin( 0.5, 0.132) ) )"
     ]
    },
    {
     "cell_type": "code",
     "execution_count": null,
     "metadata": {},
     "outputs": [],
     "source": []
    }
   ],
   "metadata": {
    "kernelspec": {
     "display_name": "Python 3",
     "language": "python",
     "name": "python3"
    },
    "language_info": {
     "codemirror_mode": {
      "name": "ipython",
      "version": 3
     },
     "file_extension": ".py",
     "mimetype": "text/x-python",
     "name": "python",
     "nbconvert_exporter": "python",
     "pygments_lexer": "ipython3",
     "version": "3.9.7"
    }
   },
   "nbformat": 4,
   "nbformat_minor": 4
  }
  ```
  * will return output:
    * z=3.000715


![Analytics](https://ga-beacon.appspot.com/UA-109580-20/plugin-Jupyter)
