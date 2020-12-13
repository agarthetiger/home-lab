# Ansible ADRs

## Roles

### Decisions

#### Roles will live in a folder in the home-lab repo, rather than as standalone repos

Having open-sourced a few Ansible Roles I've found the workflow to be time-consuming. A new role will often take at least as much time to document well than it takes to write the initial role in the first place. The workflow around making changes is onerous when including roles via Ansible Galaxy, or even from GitHub, using `ansible-galaxy` with a requirements file.

Roles can also happily live in the same Git repository because there are no requirements to version or support this code. See next ADR.

# Roles will not be versioned

None of the following enterprise requirements apply to my home lab:

* There is no test environment. Alternatively everything is a test environment. Either way, there is no need to maintain old versions of anything.
* Roles are not shared with anyone else or supported. Yes, the code is open-source on GitHub, but with a disclaimer of no support. I may choose to write tests with molecule but most often roles will be tested against the home lab itself. No backwards compatibility is required.

## Playbooks

### Decisions

#### Tags will be used to separate installation from configuration

* Uber playbooks which attempt to do everything often become slow to execute. If you've ever tried to automate the configuration of a MacBook with Ansible (been there, done it to some degree), managing homebrew packages quickly escalates to taking 5+ minutes to run just that step. For my home lab, this burns through my available time to work on anything. While I believe there is more chance of not ending up in a consistent state when running a partial playbook, that is a worthwhile tradeoff and an acceptable one for my home lab.
