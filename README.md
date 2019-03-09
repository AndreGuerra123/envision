# Envision

A (simple) environment variables manager for Python projects. 
The goal is to have declarative, explicitly defined settings variables in synchronicity both in development and production modes.

## Installation

Use the package manager [pip](https://pip.pypa.io/en/stable/) to install foobar.

```bash
pip install envision
```

## Usage:

First, in the root of your project just initialize envision:

```bash
envision init --token="YOURCUSTOMKEY"
```
Note: If your token argument is not set, a key will be automatically generated for you.

Three files will be created, a .envision, a .envision.lock and a .envision.key file. 
Some warnings will be produced if in your .gitignore file there is not a entry for exclusion of envision and envision.key files.
If you pretend to use envision in a git project please, add .envision and .envision.key to .gitignored.

Secondly, just add desired environment-like variables using the commands:

```bash
envision add
```

or remove with:

```bash
envision remove
```

The variables can se also manually set in the .envision file, just lock the file with:

```bash
envision lock
````

In production mode, you only have to declare one environment variable ENVISION with the key provided or generated, such as:

```bash
export ENVISION = 'YOURCUSTOMKEY'
```

The .envision.lock file containing the locked and encrypted key-values can then be accessed inproduction.
Then to have access to the remaining key-values encrypted just do the following in your project:

```python
from envison import envision

envision().get('A')
```

## FAQ

  ### How can I use the command line arguments in a directory outside my current directory?
  
  - Every CLI function has the --root parameter which can be set to the desired root of the project. 
  The envision constructor acepts exactly the same argument to define where to look for the envision files.
  
  ### How to change the key password?
  
  - On CLI just do:
  
  ```bash
  envision lock --token="MYNEWCUSTOMKEY"
  ```
  
  or manually by changing the .envision.key file entry and then lock the project.
  
## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.
Please make sure to update tests as appropriate.

## License
[MIT](https://choosealicense.com/licenses/mit/)
