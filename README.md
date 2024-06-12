# ViA | KI1 | Informācijas sistēmu drošības inženierija (ISDI)

# EXERCISE 1 - Explore GnuPG

OS : Ubuntu

## Uzstāda GnuPG
```
sudo apt-get update
sudo apt-get install gnupg

```

## CMD uzstāda vajadzīgās python versijas
```
C:\Windows\System32>pyenv install 3.11.5
:: [Info] ::  Mirror: https://www.python.org/ftp/python
:: [Downloading] ::  3.11.5 ...
:: [Downloading] ::  From https://www.python.org/ftp/python/3.11.5/python-3.11.5-amd64.exe
:: [Downloading] ::  To   C:\Users\Lektors\.pyenv\pyenv-win\install_cache\python-3.11.5-amd64.exe
:: [Installing] ::  3.11.5 ...
:: [Info] :: completed! 3.11.5

C:\Windows\System32>pyenv install 2.7.2
:: [Info] ::  Mirror: https://www.python.org/ftp/python
:: [Downloading] ::  2.7.2 ...
:: [Downloading] ::  From https://www.python.org/ftp/python/2.7.2/python-2.7.2.amd64.msi
:: [Downloading] ::  To   C:\Users\Lektors\.pyenv\pyenv-win\install_cache\python-2.7.2.amd64.msi
:: [Installing] ::  2.7.2 ...
:: [Info] :: completed! 2.7.2
```

## Apskata uzstādītās versijas
```
C:\Windows\System32>python3 --version
Python 3.11.5

C:\Windows\System32>python --version
Python 2.7.2
```

## Maina versijas
```
C:\Windows\System32>pyenv global 2.7.2

C:\Windows\System32>pyenv version
2.7.2 (set by C:\Users\Lektors\.pyenv\pyenv-win\version)

C:\Windows\System32>pyenv global 3.11.5

C:\Windows\System32>pyenv version
3.11.5 (set by C:\Users\Lektors\.pyenv\pyenv-win\version)
```


# EXERCISE 2 - Harden SSH Security

## Uzstāda virtualenv
```
C:\Windows\System32>pip install virtualenv
Collecting virtualenv
  Obtaining dependency information for virtualenv from https://files.pythonhosted.org/packages/4e/8b/f0d3a468c0186c603217a6656ea4f49259630e8ed99558501d92f6ff7dc3/virtualenv-20.24.5-py3-none-any.whl.metadata
  Downloading virtualenv-20.24.5-py3-none-any.whl.metadata (4.5 kB)
Collecting distlib<1,>=0.3.7 (from virtualenv)
  Obtaining dependency information for distlib<1,>=0.3.7 from https://files.pythonhosted.org/packages/43/a0/9ba967fdbd55293bacfc1507f58e316f740a3b231fc00e3d86dc39bc185a/distlib-0.3.7-py2.py3-none-any.whl.metadata
  Downloading distlib-0.3.7-py2.py3-none-any.whl.metadata (5.1 kB)
Collecting filelock<4,>=3.12.2 (from virtualenv)
  Obtaining dependency information for filelock<4,>=3.12.2 from https://files.pythonhosted.org/packages/5e/5d/97afbafd9d584ff1b45fcb354a479a3609bd97f912f8f1f6c563cb1fae21/filelock-3.12.4-py3-none-any.whl.metadata
  Downloading filelock-3.12.4-py3-none-any.whl.metadata (2.8 kB)
Collecting platformdirs<4,>=3.9.1 (from virtualenv)
  Obtaining dependency information for platformdirs<4,>=3.9.1 from https://files.pythonhosted.org/packages/14/51/fe5a0d6ea589f0d4a1b97824fb518962ad48b27cd346dcdfa2405187997a/platformdirs-3.10.0-py3-none-any.whl.metadata
  Downloading platformdirs-3.10.0-py3-none-any.whl.metadata (11 kB)
Downloading virtualenv-20.24.5-py3-none-any.whl (3.7 MB)
   ---------------------------------------- 3.7/3.7 MB 12.0 MB/s eta 0:00:00
Downloading distlib-0.3.7-py2.py3-none-any.whl (468 kB)
   ---------------------------------------- 468.9/468.9 kB 28.7 MB/s eta 0:00:00
Downloading filelock-3.12.4-py3-none-any.whl (11 kB)
Downloading platformdirs-3.10.0-py3-none-any.whl (17 kB)
Installing collected packages: distlib, platformdirs, filelock, virtualenv
Successfully installed distlib-0.3.7 filelock-3.12.4 platformdirs-3.10.0 virtualenv-20.24.5
```


# EXERCISE 3 - Explore SMTP Vulnerabilities

## Uzstāda virtualenv
```
C:\Windows\System32>pip install virtualenv
Collecting virtualenv
  Obtaining dependency information for virtualenv from https://files.pythonhosted.org/packages/4e/8b/f0d3a468c0186c603217a6656ea4f49259630e8ed99558501d92f6ff7dc3/virtualenv-20.24.5-py3-none-any.whl.metadata
  Downloading virtualenv-20.24.5-py3-none-any.whl.metadata (4.5 kB)
Collecting distlib<1,>=0.3.7 (from virtualenv)
  Obtaining dependency information for distlib<1,>=0.3.7 from https://files.pythonhosted.org/packages/43/a0/9ba967fdbd55293bacfc1507f58e316f740a3b231fc00e3d86dc39bc185a/distlib-0.3.7-py2.py3-none-any.whl.metadata
  Downloading distlib-0.3.7-py2.py3-none-any.whl.metadata (5.1 kB)
Collecting filelock<4,>=3.12.2 (from virtualenv)
  Obtaining dependency information for filelock<4,>=3.12.2 from https://files.pythonhosted.org/packages/5e/5d/97afbafd9d584ff1b45fcb354a479a3609bd97f912f8f1f6c563cb1fae21/filelock-3.12.4-py3-none-any.whl.metadata
  Downloading filelock-3.12.4-py3-none-any.whl.metadata (2.8 kB)
Collecting platformdirs<4,>=3.9.1 (from virtualenv)
  Obtaining dependency information for platformdirs<4,>=3.9.1 from https://files.pythonhosted.org/packages/14/51/fe5a0d6ea589f0d4a1b97824fb518962ad48b27cd346dcdfa2405187997a/platformdirs-3.10.0-py3-none-any.whl.metadata
  Downloading platformdirs-3.10.0-py3-none-any.whl.metadata (11 kB)
Downloading virtualenv-20.24.5-py3-none-any.whl (3.7 MB)
   ---------------------------------------- 3.7/3.7 MB 12.0 MB/s eta 0:00:00
Downloading distlib-0.3.7-py2.py3-none-any.whl (468 kB)
   ---------------------------------------- 468.9/468.9 kB 28.7 MB/s eta 0:00:00
Downloading filelock-3.12.4-py3-none-any.whl (11 kB)
Downloading platformdirs-3.10.0-py3-none-any.whl (17 kB)
Installing collected packages: distlib, platformdirs, filelock, virtualenv
Successfully installed distlib-0.3.7 filelock-3.12.4 platformdirs-3.10.0 virtualenv-20.24.5
```

# EXERCISE 4 - Network Tunnels (using Netcat)

## Uzstāda virtualenv
```
C:\Windows\System32>pip install virtualenv
Collecting virtualenv
  Obtaining dependency information for virtualenv from https://files.pythonhosted.org/packages/4e/8b/f0d3a468c0186c603217a6656ea4f49259630e8ed99558501d92f6ff7dc3/virtualenv-20.24.5-py3-none-any.whl.metadata
  Downloading virtualenv-20.24.5-py3-none-any.whl.metadata (4.5 kB)
Collecting distlib<1,>=0.3.7 (from virtualenv)
  Obtaining dependency information for distlib<1,>=0.3.7 from https://files.pythonhosted.org/packages/43/a0/9ba967fdbd55293bacfc1507f58e316f740a3b231fc00e3d86dc39bc185a/distlib-0.3.7-py2.py3-none-any.whl.metadata
  Downloading distlib-0.3.7-py2.py3-none-any.whl.metadata (5.1 kB)
Collecting filelock<4,>=3.12.2 (from virtualenv)
  Obtaining dependency information for filelock<4,>=3.12.2 from https://files.pythonhosted.org/packages/5e/5d/97afbafd9d584ff1b45fcb354a479a3609bd97f912f8f1f6c563cb1fae21/filelock-3.12.4-py3-none-any.whl.metadata
  Downloading filelock-3.12.4-py3-none-any.whl.metadata (2.8 kB)
Collecting platformdirs<4,>=3.9.1 (from virtualenv)
  Obtaining dependency information for platformdirs<4,>=3.9.1 from https://files.pythonhosted.org/packages/14/51/fe5a0d6ea589f0d4a1b97824fb518962ad48b27cd346dcdfa2405187997a/platformdirs-3.10.0-py3-none-any.whl.metadata
  Downloading platformdirs-3.10.0-py3-none-any.whl.metadata (11 kB)
Downloading virtualenv-20.24.5-py3-none-any.whl (3.7 MB)
   ---------------------------------------- 3.7/3.7 MB 12.0 MB/s eta 0:00:00
Downloading distlib-0.3.7-py2.py3-none-any.whl (468 kB)
   ---------------------------------------- 468.9/468.9 kB 28.7 MB/s eta 0:00:00
Downloading filelock-3.12.4-py3-none-any.whl (11 kB)
Downloading platformdirs-3.10.0-py3-none-any.whl (17 kB)
Installing collected packages: distlib, platformdirs, filelock, virtualenv
Successfully installed distlib-0.3.7 filelock-3.12.4 platformdirs-3.10.0 virtualenv-20.24.5
```

