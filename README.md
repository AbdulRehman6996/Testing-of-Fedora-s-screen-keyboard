# Fedora28InstallationTestingUsingOpenQA
		
		openQA is an automated test system designed around operating system-level testing. Its key feature is that it interacts with the system under test much like a human would, by sending input using a virtual keyboard and mouse (or serial console input), and monitoring the screen, serial console and audio outputs for output. This makes it ideally suited to running operating system-level tests without making any modifications to the software being tested.

# How Fedora uses openQA

There are currently two official Fedora openQA deployments: production and staging.

At present, Fedora uses openQA for release validation type testing. We have developed a set of tests oriented around testing a complete Fedora distribution compose. These tests are run:

    On every nightly compose of Rawhide or Branched
    On every 'candidate' compose (including release candidates)

A subset of tests is run on every nightly two-week Atomic compose, and on each refresh of the semi-official post-release live respins.

The results of all openQA tests are forwarded to ResultsDB. When there is a release validation test event for a compose, openQA results are mapped to Wikitcms test cases and reported to the appropriate wiki pages: results you see from the user coconut are results derived from openQA testing.

An email summary of most of these runs is produced and mailed to test and devel by the check-compose tool.

The fedora_nightlies tool which produces the nightly compose finder page considers openQA results (as well as Autocloud results) in determining the test pass/fail status of the images it tracks.

Future plans include 'gating' Rawhide composes on openQA test results (i.e. not pushing a Rawhide compose into the mirror system if it fails the openQA tests), and using openQA to run tests on package updates and provide feedback to Bodhi. 

# Fedora openQA tests and tools

The Fedora openQA tests can be found in the os-autoinst-distri-fedora repository. The library, CLI and Fedmsg consumers that handle scheduling openQA jobs and forwarding results to ResultsDB and Wikitcms can be found in the fedora_openqa repository. The createhdds tool used to create disk image files required by some of the tests can be found in the createhdds repository.

Each of these repositories includes documentation relating to its specific role in the overall system. The fedora_openqa repository includes instructions on installing and using the scheduler and report forwarding features, and the os-autoinst-distri-fedora repository includes Fedora-specific instructions for test development and documentation of Fedora test conventions, functions and settings.

The official Fedora openQA deployments are managed via Ansible playbooks in the Fedora Infrastructure ansible repository. The roles can be found in roles/openqa, and we attempt to maintain them in such a way that you can use them to deploy openQA instances outside of Fedora infrastructure, though this is not tested very often and may bitrot from time to time. 
	


#This project deals with the testing of whole installation process of the Fedora 28 using the tool OpenQA, all the test scripts written for the testing are with respect to keyboard key's & without any interaction of mouse.
The chained process here include the testing of the on screen keyboard of fedora.

