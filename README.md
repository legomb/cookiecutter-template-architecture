# Architecture Proposal - cookiecutter template

Cookiecutter template for an architecture project proposal.

## Usage

1. Install [cookiecutter](https://www.cookiecutter.io/)
    e.g.:

    ```sh
    brew install cookiecutter
    ```
  
2. Run:
   - From local directory:

     ```sh
     cookiecutter <location-of-current-dir>/cookiecutter-template-architecture/
     ```
     
   - Remotely:

     ```sh
     cookiecutter gh:legomb/cookiecutter-template-architecture
     ```

    This will prompt some questions:
      - `new_directory_name`: Name of the directory to be created based on this template
      - `project_name`: Name of the project
      - `markdown_file_name`: Proposal filename
