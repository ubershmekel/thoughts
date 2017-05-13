# Version Control for Generated Files

## My opinion for most of my use-cases

Don't commit generated files.

## Advantages to committing generated files

* A small change in a code generator can affect a large amount of files. Committing and diffing the resulting change communicates its true impact.
* The build is simpler and faster
* Less dependance on external resources

## Advantages to not committing generated files

* Smaller source control footprint.
* Smaller diffs that are denser in information.
* For library developers - it allows library users to consolidate dependencies.
* No chance of a mismatch between the generated and source files.
* No chance of accidentally editing the generated files.

##  Examples of when to commit generated files

* Your build environment can't handle the additional build step automatically. If you have to generate the files by hand for every build anyway, you might as well put them in the VCS. Then it actually reduces the risk of a version mismatch due to fewer people having to do the generation step.
* The generation step significantly slows down your build
* After generating them, the files are further modified by hand. In that case, they are not really generated files any more and thus belong in the VCS.
* The source files change very rarely (e.g. they come from a third party that only provides updates every few months or so).
* You need to vet every line change in your system for safety, security or compliance.


## Story of committing generated files gone wrong

At a previous employer we committed generated code. We had more than 10 active branches with overall about 100 commits per day. Spanning 2 products, 2 live releases, 4 releases in to the future for all of: art, server, client, data and code. The code repository and data repository both needed generated output from the other. There was an auto-merger that would make sure if you commit a hotfix to live that it would also reach the future release branches. A small change in source can be giant in generated. With different versions of the source file - a merge in source does not equal a merge in the generated output. So every merge required automating detection of source changes and triggering the various generation processes. We also had automated rules to never merge changes in the generated code because those were always local rebuilds to fix a previous bad merge in a branch.

It was buggy and complicated. Everyone I spoke to regretted having the generated code committed except for the engineer that made that decision 10 years ago.

## References

* https://softwareengineering.stackexchange.com/questions/192113/do-i-check-generated-code-in-to-source-control-or-not
* https://softwareengineering.stackexchange.com/questions/120477/what-part-of-your-project-should-be-in-source-code-control?lq=1
* https://guides.cocoapods.org/using/using-cocoapods.html#should-i-check-the-pods-directory-into-source-control
* https://medium.com/@kentcdodds/why-i-don-t-commit-generated-files-to-master-a4d76382564
