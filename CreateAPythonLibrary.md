# Create a Python Library
### We have created a library for a command line program. This is the digest of it.

## The setup:

* `Programfolder`
    * ```__init__.py```
    * ```programfile.py```
* ```README.md```
* ```setup.py```
* ```testfolder```
    * ```__init__.py```
    * ```testfile.py```


Our code lies in the ```Programfolder``` together with an ```__init.py__``` file. The init file can be empty, but it has to be there for the library to work. And the programfolder can be called whatever you like. The ```setup.py``` file is the configurationfile for the library. 

### Example of a setup file:
```
import setuptools

with open("README.md", "r") as fh:
    long_description = fh.read()

setuptools.setup(
    name="mergepdfs", 
    version="0.9.1",
    author="Isabel Sandstrøm, Terje Sandstrom,",
    author_email="isabel@hermit.no",
    description="Python command line program for merging multiple PDF-files to one PDF",
    long_description=long_description,
    long_description_content_type="text/markdown",
    url="https://github.com/HermitAS/mergepdfs",
    packages=['pdfmerger'],
    install_requires=['PyPDF2>=1.26.0'],
    entry_points={'console_scripts': ['mergepdfs = pdfmerger.mergepdfs:main']},
    classifiers=[
        "Programming Language :: Python :: 3",
        "License :: OSI Approved :: MIT License",
        "Operating System :: OS Independent",
    ],
    python_requires='>=3.6',
)
```

### The breakdown of the setup file:

* ```name``` : The name of the library.
* ```version``` : The version number.
* ```author``` : Pretty selfexplanitory, the person who wrote the code.
* ```author_email``` : and the authors email.
* ```description``` : One line description of the program.
* ```long_description``` : The longer descrption of the program. Here we have linked it to the README file.
* ```long_description_content_type``` : The filetype of the long description.
* ```url``` : Here we have linked the git hub page.
* ```packages``` : The name of the programfolder.
* ```install_requires``` : The name of the modules that needs to be installed. The standard libraries in Python does not have to be included. Write both the modulename and the version. 
* ```entry_points``` : Tells where the program should start when the command is called.
* ```classifier``` : Tags for referencing on PyPi
* ```python_requires``` : Tells which version of python that has to be installed for the program.

## The code:
To get the program to run when called, we use 

```
if __name__ == 'main':
    main()
```
in the code. This makes the code run the function ```main()``` when it is called.

## Building and uploading the library:

Now to building and uploading of the library. Make sure to have the modules ```wheel```, ```setuptools``` and ```twine```, which can be installed with ```pip```.

### Building:
To build the library run
```
python setup.py sdist bdist_wheel
```
Now you have the library locally. By using ```pip``` you can install it from the whl file in the dist folder. 
```
pip install dist\[whl file]
```

When you make changes in the code, you need to build the library again. When doing this the version number has to be updated.

### Uploading:
To upload your library to PyPi you need to create a user. With your user create a token, where you will get a password for this token.
Run the command 
```
python -m twine upload dist\*
```
for the username write ```__token__```, and for the password copy paste the one you were given. 
OBS: In Windows you can`t use 'Ctrl' + 'V', but the right click on the mouse will paste it directly in.

## Read more:
* https://medium.com/analytics-vidhya/how-to-create-a-python-library-7d5aea80cc3f
* https://towardsdatascience.com/deep-dive-create-and-publish-your-first-python-library-f7f618719e14
