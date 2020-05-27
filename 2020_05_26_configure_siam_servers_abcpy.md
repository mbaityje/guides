# Guide on how to be operative on siam-linuxXX with ABCpy 0.5.2

Note: first of all check if Python 3.6 is installed.

## 1. Create virtualenv

Here the goal is to create a virtualenv to run the simulations with ABCpy 0.5.2

Move to the local folder in the server

```bash
cd /local/dalmolma/
```

This folder will contain two folders:

- abcpy052: virtualenv

- BitBucket: all the repositories needed to run the code

We can initialize the virtualenv

```bash
python3.6 -m venv abcpy052
```

Activate the virtualenv. The following step will be executed automatically
from now on when starting the terminal (it is in the ~/.bashrc).

```bash
source /local/dalmolma/abcpy052/bin/activate
```

Install the packages needed. Note that the dependencies of abcpy have to be
installed manually because they are messed up.

```bash
pip install --upgrade pip
pip install abcpy==0.5.2 --no-deps
pip install numpy==1.14.6
pip install scipy
pip install scikit-learn==0.19.1
pip install Cython
pip install gfort2py==1.0.12
pip install pandas
pip install wheel
pip install glmnet
```

## 2. Clone the repositories

All the repo will be cloned in the folder BitBucket. Create the folder

```bash
mkdir /local/dalmolma/BitBucket
cd /local/dalmolma/BitBucket
```

Clone the repositories. Note that we are not using ssh authentication.

- **abcpy_extension**
```bash
git clone https://dalmo1991@bitbucket.org/dalmo1991/abcpy_extension.git
```

- **sigcalthur**
```bash
git clone https://dalmo1991@bitbucket.org/dalmo1991/sigcalthur.git
```

- **superflexPython** (remember to change the capitalization)
```bash
git clone https://dalmo1991@bitbucket.org/dalmo1991/superflexpython.git
mv superflexpython/ superflexPython/
```

- **dalmo**
```bash
git clone https://dalmo1991@bitbucket.org/dalmo1991/dalmo.git
```

The library **abcpy_extension** should be used in the OnServer branch
```bash
cd /local/dalmolma/BitBucket/abcpy_extension/
git checkout OnServer
```

## 3. Compile the code

Some code uses Fortran code interfaced to Python that has to be compiled.
**It is always better to have a look at the compile scripts before running**
**them**.

### abcpy_extension

```bash
cd /local/dalmolma/BitBucket/abcpy_extension/add_error/
cat compile.sh
```

```bash
bash compile.sh
```

### superflexPython

For this purpose only the C_so version.

```bash
cd /local/dalmolma/BitBucket/superflexPython/C_so/
cat compile.sh
```

```bash
bash compile.sh
```

## 4. Install the dalmo library

The **dalmo** library contains some useful general purpose code derived from
single applications.

Move to the right folder
```bash
cd /local/dalmolma/BitBucket/dalmo/
```

Create the package
```bash
python setup.py sdist bdist_wheel
```

Install the package
```bash
cd /local/dalmolma/BitBucket/
pip install dalmo/
```

## 5. Test the installation

There is a short ABC simulation that can be used to test if the configuration
works.

Move to the folder where the code is
```bash
cd /local/dalmolma/BitBucket/sigcalthur/Simulations/StocABC/And_01_T1/
```

The file modelInfo.dat has to be modified in order to work. Change the path in
the second line to
```bash
"$(CASE_STUDIES)$" "/local/dalmolma/BitBucket"
```

The file can be opened using Nano (ctrl+x to exit, y to save the file)

```bash
nano modelInfo.dat
```

Try running the script
```bash
python NonConcomitant_01_T1.py
```

If everything works, the script should run a quick ABCpy simulation.