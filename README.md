
# Great Expectations quick start guide


- THIS STEP IS PREREQUSITITE. Clone the git repo with data files in it.:

``` 
git clone git@github.com:katerina-tw/data_ml_lunch_and_learn.git
```

- Create the directory next to the great_expectations git repo and switch to that:
  
```
mkdir ge_example
cd ge_example
```  

- Install python virtual environment if does not have yet, and create virtual environment _env_. Activate this environment
as we will be working there to install and proceed with Great Expectations
```
pip3 install virtualenv
python3 -m venv genv
source genv/bin/activate
``` 

- Install Great Expectations in the virtual environment:

```
python3 -m pip install great_expectations
``` 

- Run the command for Great Expectations initialisation:

```
great_expectations init
```

You should see something like this:

```Let's configure a new Data Context.

First, Great Expectations will create a new directory:

    great_expectations
    |-- great_expectations.yml
    |-- expectations
    |-- checkpoints
    |-- notebooks
    |-- plugins
    |-- .gitignore
    |-- uncommitted
        |-- config_variables.yml
        |-- documentation
        |-- validations

OK to proceed? [Y/n]: 
```

-  Press Y for the command output above.
-  We will proceeding with local data files (pandas), so press 1 for the following output:

```What data would you like Great Expectations to connect to?
    1. Files on a filesystem (for processing with Pandas or Spark)
    2. Relational database (SQL)
: 1
```
- ... and press 1 for the next output as well:

```What are you processing your files with?
    1. Pandas
    2. PySpark
: 1
```
- Enter the relative path _**../data_ml_lunch_and_learn/data/**_ to titanic.csv data file in the git repo:

```
Enter the path (relative or absolute) of the root directory where the data files are stored.
: ../data_ml_lunch_and_learn/data/ 
```

- Enter the name of the new datasource - _**example_dir**_:
```
Give your new Datasource a short name.
 [data__dir]: example_dir
```

- Click Y to proceed after the following command to configure Great Expectation deployment
and add data source to that:

```
Great Expectations will now add a new Datasource 'example_dir' to your deployment, by adding this entry to your great_expectations.yml:

  example_dir:
    data_asset_type:
      class_name: PandasDataset
      module_name: great_expectations.dataset
    batch_kwargs_generators:
      subdir_reader:
        class_name: SubdirReaderBatchKwargsGenerator
        base_directory: ../../data_ml_lunch_and_learn/data/
    class_name: PandasDatasource
    module_name: great_expectations.datasource


Would you like to proceed? [Y/n]: y
```

 - Lest get started with some data validations already and profile our data!
 
 ```
Would you like to profile new Expectations for a single data asset within your new Datasource? [Y/n]: Y
```

 - Pick titanic file by pressing 1 twice to the following commands:
 
 ```
Would you like to:
    1. choose from a list of data assets in this datasource
    2. enter the path of a data file
: 1

Would you like to:
    1. choose from a list of data assets in this datasource
    2. enter the path of a data file
: 1
```

- Keep the name for the data warnings (if any ) to the default titanic.warning :

```
Name the new Expectation Suite [titanic.warning]:
```

 - Proceed with the creation of Expectation Suite where all data validations will be stored:
 
 ```
Great Expectations will choose a couple of columns and generate expectations about them
to demonstrate some examples of assertions you can make about your data.

Great Expectations will store these expectations in a new Expectation Suite 'titanic.warning' here:

  file:///.../ge_example/great_expectations/expectations/titanic.warning.json

Would you like to proceed? [Y/n]: y
```

- Lets build documentation and see how our validations run thru. Press Y to all of the commans below:

```
================================================================================

Would you like to build Data Docs? [Y/n]: y

The following Data Docs sites will be built:

 - local_site: file:///.../ge_example/great_expectations/uncommitted/data_docs/local_site/index.html

Would you like to proceed? [Y/n]: y

Building Data Docs...

Done building Data Docs

Would you like to view your new Expectations in Data Docs? This will open a new browser window. [Y/n]: y

================================================================================
```