<a href="https://codeclimate.com/github/HumanCellAtlas/ingest-validator/maintainability">
    <img src="https://api.codeclimate.com/v1/badges/acb71b5e1472ff38cbb2/maintainability" />
</a>
<a href="https://codecov.io/gh/HumanCellAtlas/ingest-validator">
  <img src="https://codecov.io/gh/HumanCellAtlas/ingest-validator/branch/master/graph/badge.svg" alt="Codecov" />
</a>
[![Build Status](https://travis-ci.org/HumanCellAtlas/ingest-validator.svg?branch=master)](https://travis-ci.org/HumanCellAtlas/ingest-validator)

# HCA ingest validation service

Scripts for metadata validation 


# CLI application 
## Validation service

This script listens for messages from ingest API messaging queue and validates each metadata created in the ingest service

```
python validation-app.py
```

Metadata JSON documents are validated against specified schemas. 
[A list of the current applicable schemas are located here](https://github.com/HumanCellAtlas/metadata-schema/tree/master/json_schema).
Documents must specify the schema against which they are to be validated. The URL of the schema must be located at the 
JSON path core.schema_url within the JSON document. After validation has completed, a validation report will be 
attached to the metadata document living in the ingestion-infrastructure database at api.ingest.dev.data.humancellatlas.org

## Development Notes

### Python's `virtualenv`

To easily facilitate development, it is recommended to set up a Python virtual environment tool, particularly the 
`virtualenv` to manage packages and dependencies necessary to develop, test, and run the code. The documentation for setting 
up `virtualenv` can be found on [Python 3's official documentation](https://packaging.python.org/guides/installing-using-pip-and-virtualenv).

#### `virtualenv` Best Practices

There are 2 general approaches to managing virtual environments on the local machine. One is to set up a common repository
for all virtual environments such as `$HOME/.venvs` (there's no widely accepted naming convention on this). Another
approach is to set up one locally in the specific root directory of the project. Further instructions on how exactly to 
create and manage virtual environments through `virtualenv` can be found on the documentation specified above.

In this repository, the `venv` directory has been set up to be ignored by version control. It can be used to contain
virtual environments for the local development machine. 
 
### Dependencies

#### Setting Up Dependencies

To install required modules needed to develop and run this codebase, the following command is used:

```
pip install -r requirements.txt
```

#### Keeping Dependencies Up to Date

The `requirements.txt` file specifies a list of modules that are needed to be installed to successfully run the code. 
When new modules are added through `pip`, it is advised to keep the list up to date by using `freeze`:

    pip freeze > requirements.txt
    
This command will overwrite the text file with all the modules needed including the last ones installed along with the
versions used for the local environment. 