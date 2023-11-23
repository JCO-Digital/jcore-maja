# Module development process
Normally the modules are either developed against a customer project, and then pushed to their respective repos. They can alternatively be developed in the dedicated development repo [JCORE-Kehitys](https://github.com/jco-digital/jcore-kehitys)

## Module workflow
Modules main branch is push protected, and all changes needs to be done through pull-requests. Commits should be done using [Conventional Commit](https://www.conventionalcommits.org) standard.
When a pull-request is merged, the version will be bumped according to the commits made. (Refer to the conventional commit page to find out which version number is bumped).


## Module Do's & Don'ts
- Modules are (and should) always be deployed to packagist.org, for easy installing in other projects.
- Modules versioning should follow semver, and commits should always follow [Conventional Commit](https://www.conventionalcommits.org) standard.
    - If the module is dependent on JCORE-Ydin, the SemVer major version should match that of the JCORE-Ydin version, however if it is not possible, follow SemVer versioning.
- Although modules should follow SemVer, the starting version should always be v3.0.0, as to indicate the work that has been put into them from before JCORE 2.
- Modules should never be dependant on other modules, except JCORE-Ydin, which modules freely can depend on. (Locking the major version is highly encouraged)
- To be expanded


# Theme development process
[JCORE 3 (Ilme)](https://github.com/jco-digital/jcore-ilme), is best developed using the development repo, as all projects uses a copy of the latest version (branch). 
Development should be done on the main branch, and when a new version can be released, a new branch is made from the main branch.

## Theme Do's & Don'ts
- If a feature is project specific, do not commit it into the jcore-ilme repository.
- Do backport bugfixes to older versions, as far back as feasible.

## Versioning
