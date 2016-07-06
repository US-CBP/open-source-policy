## Practicing our open source policy

This document is meant to give specific team guidance on putting our [open source policy](policy.md) into practice.

* CBP releases software into the [international public domain](#public-domain).
* All team members should feel empowered to contribute back to outside open source projects.
* There are [narrow, documented exceptions](#exceptions) where source code may be delayed or withheld.

CBP team members should work with the strong presumption that all of their code under the US-CBP organization on GitHub will be public, throughout and after development.

Before deciding to release of source code, consult with the executive management for apprroval.

### Public domain

[By law](http://www.law.cornell.edu/uscode/text/17/105), works of the United States government are not copyrightable in the US, and so are public domain. But by default, US government works **are** copyrightable internationally, and so CBP intentionally waives this copyright abroad using [CC0](https://creativecommons.org/publicdomain/zero/1.0/).

There are potentially other cases where copyright is involved: where contractors produce the work, or where work was otherwise originally performed not in the capacity of a US government employee.

To the extent CBP has the rights to do so, CBP will normalize the copyright status of its work product under CC0.

As [the Free Software Foundation says](https://www.gnu.org/licenses/gpl-faq.html#GPLUSGovAdd) about government-contributed improvements to GPL software:

> Yes. If the improvements are written by US government employees in the course of their employment, then the improvements are in the public domain. However, the improved version, as a whole, is still covered by the GNU GPL. There is no problem in this situation.

#### How to license CBP repos

When creating a repo, add a [LICENSE.md](LICENSE.md) and [CONTRIBUTING.md](CONTRIBUTING.md) file, and add/edit the [README.md template](README_TEMPLATE.md).

The preceding links are to our standard boilerplate for each of those, so you can just copy and paste them. In some cases, you may need to customize them for your use -- for example, if you've forked a project that originated from outside the government.

You may wish make the following shell aliases

```bash
alias insert-license="curl -sO https://raw.githubusercontent.com/US-CBP/open-source-policy/master/LICENSE.md"
alias insert-contrib="curl -sO https://raw.githubusercontent.com/US-CBP/open-source-policy/master/CONTRIBUTING.md"
alias 18f-init="insert-license && insert-contrib && echo 'Licensed.'"
```

You can then initialize a new CBP repository's license information with:

```bash
US-CBP-init
```

Want to take it even further and create the repo at the same time?

```bash
alias create-repo="mkdir \!* && cd \!* && git init ."
alias create-readme="curl -s https://raw.githubusercontent.com/US-CBP/open-source-policy/master/README_TEMPLATE.md -o README.md"
alias create-US-CBP-repo="create-repo \!* && US-CBP-init && create-readme && sed 's/[Repo Name]/$(/usr/bin/basename $(pwd))/' README.md && git add . && git commit -m 'initial commit'"
```

Then create a repo and license it with:

```bash
create-US-CBP-repo new-project-name
```

Even if you don't create a repo, it's recommended to use [this README.md template](README_TEMPLATE.md) that sums up what's going on.

### Accepting contributions from the public

Any CBP project can (and should!) accept open source contributions from the public if under the public domain license.

Projects can **encourage public contributions** by:

* Creating open issues where public help would be especially welcome.
* Labeling those issues with `help wanted` so people can scan issues quickly and [services](http://www.codeforamerica.org/geeks/civicissues) can aggregate volunteer opportunities.
* Asking for it, in the README and in other public writing about the project.
* Providing solid documentation for any project setup process.
* Being super nice when communicating with volunteers.

As [described above](#public-domain), CBP projects are dedicated to the international public domain wherever possible. In this situation, contributors must agree to release their contributions into the international public domain. Projects can inform contributors of this agreement by copying the [`CONTRIBUTING.md`](CONTRIBUTING.md) file from this repo into new project repos, and copying the ["Public domain" section of this repo's README](README.md#public-domain) into the new project's README.

When a CBP project has a non-standard license status (e.g. it's a fork of a previously licensed project, or is a module/plugin for a GPL project), then that project needs to figure out an appropriate contributing agreement.

### Managing CBP resources

If a refactoring or feature makes the tool easier for CBP to use in its work, and the teammate doing it is otherwise meeting their duties, then that's time well spent for 18F and the taxpayer.

Open source projects can &mdash; and hopefully do! &mdash; get use and uptake from outside CBP. It's also okay for individual teammates to create projects they intend to use both at CBP and in their personal capacity.

Teammates need executive management permission to start new open source teams in the CBP GitHub organization. Once a team is created, that team may have n-number of repos.

When creating new open source projects:

* If you're creating a repo because it's primarily for your CBP work, and the work you perform in it is primarily to benefit CBP, start the repo's life in the CBP organization. 
* If you're creating a repo that isn't primarily for CBP work, but you think will likely see use at CBP, start it in your personal account. If you don't have strong feelings or concerns about ownership, consider releasing the project under CC0 to save yourself even having to ever think about it.

As people open issues and request features (no matter whether the repo is in your account or CBP's), continue to exercise professional judgment about how to spend CBP time.

If you think something will benefit CBP and is worth the time, then that's valuable CBP work. If it won't benefit CBP but makes the library better for other uses, that may best be done with personal time.

#### Exceptions

CBP currently has several, mission-critical projects for which we will not ever release the source code.
