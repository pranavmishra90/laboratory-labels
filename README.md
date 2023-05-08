# Laboratory Labels

<img src="./deploy/media/images/rush_university_with_logo.jpg">

## Project Details

Datalad repoistory for programmatically generated laboratory labels

<img src="https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fpranavmishra90%2Fbadges%2Fmain%2FRush/BFGI/datalad.json&amp;color=3e4c75" alt="datalad">
<img src="https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fpranavmishra90%2Fbadges%2Fmain%2FRush/BFGI/python.json&amp;color=3e4c75" alt="python">
<img src="https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fpranavmishra90%2Fbadges%2Fmain%2Fone-sided-badge/docker.json&amp;color=3e4c75" alt="docker">
<img src="https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fpranavmishra90%2Fbadges%2Fmain%2Fone-sided-badge/jupyter.json&amp;color=3e4c75" alt="jupyter">
<img src="https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fpranavmishra90%2Fbadges%2Fmain%2Fone-sided-badge/anaconda.json&amp;color=3e4c75" alt="anaconda">

### Repository Maintainer

<strong>Pranav Kumar Mishra, MBBS</strong>Post-Doctoral Research FellowDepartments of Surgery and Orthopedic SurgeryRush University Medical Center

Email: pranav\_k\_mishra@rush.eduOffice: 312-942-3146
<a href="https://orcid.org/0000-0001-5219-6269"><img src="https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fpranavmishra90%2Fbadges%2Fmain%2FPranav/orchid.json&amp;color=3e4c75" alt="orchid"></a>
<a href="https://github.com/pranavmishra90"><img src="https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fpranavmishra90%2Fbadges%2Fmain%2FPranav/github.json&amp;color=3e4c75" alt="github"></a>

### Laboratory of Anna Spagnoli, MD

Details <strong>Anna Spagnoli, M.D.</strong> John W. and Helen H. Watzek Professor Orthopaedic Surgery and Pediatrics Director Section of Molecular Medicine Email: anna\_spagnoli@rush.edu Cohn Research Building 1735 W. Harrison St., Ste 563 Chicago, IL 60612

# Working with Datalad

## Starting workspace

1. Open a Terminal window to the repository root directory
2. `cd deploy/docker`
3. Execute the docker-compose file with `docker-compose up -d`

### Using VSCode

4. Open a new VSCode window with this repository folder opened
5. On the bottom left, click the 'remote' button
6. Select `Attach to Runninng Container`
7. Select `datalad`

### Using Terminal

4. In a new terminal window, run `docker exec -it datalad bash`

### Alternative VSCode

1. Open directory in VSCode directly
2. Use the automatic feature to re-open directory in remote container

## Creating a subdataset

1. Inside of the datalad docker container, run
<br>
    `datalad create -c <text2git / yoda> -D "Insert description here" --dataset <new_dataset_name>`
2. `cd` into the newly created subdataset
3. Add the directory as a safe directory for it (otherwise, it may produce an error)
<br>
    `git config --global --add safe.directory .`
4. Initialize git-annex for this dataset, which will store files outside of Git and on the project's secure Microsoft SharePoint environment
<br>
    `git annex -v initremote datalad-rush type=directory directory="C:/Users/pmishra3/OneDrive - rush.edu/Datalad/datalad-git-annex" encryption=none`
5. Add to remote git repository
<br>
    `datalad siblings add -s gitea --publish-depends rushdrive-annex --url <git repo url>`.
<br>
    (You may get an error which says "Could not detect whether gitea carries an annex". This is normal.)
<br>
    Alternative: For if you are hosting your git repository with Gitea, you can use a datalad-gitea API with:

    ```
    DATALAD_CREDENTIAL_GITEA_TOKEN=<token here>
    
    datalad create-sibling-gitea --api https://gitea.example.com --credential GITEA --publish-depends datalad-rush --private --name gitea Rush/<repo name>
    ```
6. Try a push the dataset to the sibling / remote by `datalad push --to gitea`

### Installing datalad / git repositories as subdatasets

1. `datalad install -d . --source=<git repo url>`
2. `cd` into directory
3. `datalad siblings` to list remotes
4. `git annex -v initremote datalad-rush type=directory directory="C:/Users/pmishra3/OneDrive - rush.edu/Datalad/datalad-git-annex" encryption=none`
5. `datalad siblings configure -s gitea --publish-depends datalad-rush`
6. `datalad publish --to gitea`

# Licenses

For more about the licenses provided by this repository, please visit the [Licenses page](./licenses/readme.md).

### Repository Code

<img src="https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fpranavmishra90%2Fbadges%2Fmain%2Fone-sided-badge/source_code_MIT.json&amp;color=3e4c75" alt="source_code_MIT">

The repository code, unless otherwise specified, is licensed under the [MIT License](./licenses/MIT-license).

### Repository Media

<img src="https://img.shields.io/endpoint?url=https%3A%2F%2Fraw.githubusercontent.com%2Fpranavmishra90%2Fbadges%2Fmain%2Fone-sided-badge/media_CCBY4.json&amp;color=3e4c75" alt="media_CCBY4">

Media files, when directly specified, are licensed and available for use under Creative Commons Attribution 4.0 International [CC-BY-4.0](./licenses/cc-by-4.0.md).

### Default copyright

All other research works in this repository are copyrighted without explicit useage / sharing permissions from the authors.

Copyright © 2022 Pranav Kumar Mishra