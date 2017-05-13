# Version Control for Generated Files

# Pains of committing generated files

At Blizzard we had more than 10 active branches (2 products, 2 live releases, 4 releases in to the future for all of: art, server, client, data and code). The code repository and data repository both needed generated output from the other. There was an auto-merger that would make sure if you commit a hotfix to live that it would also reach the future release branches. A small change in source can be giant in generated. With different versions of the source file - a merge in source does not equal a merge in the generated output. So every merge required automating detection of source changes and triggering the various generation processes. We also had automated rules to never merge changes in the generated code because those were always local rebuilds to fix a previous bad merge in a branch.
It was buggy and complicated. Everyone I spoke to regretted having the generated code committed except for the engineer that made that decision 10 years ago.

## Upside to committing generated files

* Small changes to code generators can have giant impact. Committing and diffing the resulting change clarifies its impact.


##  Examples of when to commit generated files
https://softwareengineering.stackexchange.com/questions/192113/do-i-check-generated-code-in-to-source-control-or-not

* Your build environment can't handle the additional build step automatically. If you have to generate the files by hand for every build anyway, you might as well put them in the VCS. Then it actually reduces the risk of a version mismatch due to fewer people having to do the generation step.
* The generation step significantly slows down your build
* After generating them, the files are further modified by hand. In that case, they are not really generated files any more and thus belong in the VCS.
* The source files change very rarely (e.g. they come from a third party that only provides updates every few months or so).
* You need to vet every line change in your system for safety, security or compliance.
