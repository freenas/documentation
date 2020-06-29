---
title: "Software Development Life Cycle"
weight: 2
---

## TrueNAS Software Development Life Cycle
 
The TrueNAS (and FreeNAS) software development life cycle (SDLC) is the process for planning, creating, testing, deploying, and maintaining FreeNAS and TrueNAS releases.

In TrueNAS there are five stages to the SDLC: requirement analysis, design and development, testing and evaluation, documentation, and maintenance.

### Requirement Analysis

Determine the objectives, nature, and scope of future versions of the software.
This involves gathering feedback and interpreting customer needs and requirements, diagnosing existing problems, and weighing the pros and cons of potential solutions.
The end result is a list of recommended improvements to be integrated into future versions of TrueNAS.

### Design and Development

Required and planned changes are investigated in detail and development steps are determined.
Proposed alterations are reviewed by peers for completeness, correctness, and proper coding style.
TrueNAS developers then begin altering the software to include new features, resolve software bugs, or implement security improvements. 

### Testing and Evaluation

Code is integrated into the existing TrueNAS source tree, then built and tested by the Quality Engineering (QE) department.
QE verifies that all requirements and objectives are properly met and the updated software is reliable and fault-tolerant according to the determined requirements.
If issues are found, code is reworked to meet the development requirements.
Simultaneously, a security evaluation of the TrueNAS code is completed, with any discovered issues sent to the engineering team for resolution.

### Documentation

The Technical Documentation Department audits all development changes to the software and resolves any inconsistencies with the current software documentation.
This is to verify that end user documentation is as accurate as possible.
Any security notices, errata, or best practices are also drafted for inclusion on the iX Security website.

### Maintenance

The new release of TrueNAS is evaluated to determine further feature development, bug fixes, or security vulnerability patches.
During this stage, security patches and software erratum are corrected, updated versions of existing branches are pushed, and feedback is solicited for future versions of the software.

### SDLC Application

The TrueNAS SDLC applies to the latest two release branches.
As new releases are created for TrueNAS, the oldest TrueNAS release branch is dropped out of the SDLC and labeled as End of Life (EoL).
For example, TrueNAS/FreeNAS 11.2 and 11.3 branches were in active development under the SDLC in January 2020.
By May 2020, TrueNAS/FreeNAS 12.0 and 11.3 were the active development branches under the SDLC.
Users are encouraged to actively keep their software updated to an active development version to continue to receive security patches and other software improvements.
