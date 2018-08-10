# TECOmate: 

**Tools for the Enforcement of Smart Contracts On-line with MAthematics and TEchnology**.
</br>


The word **tecomate** is pronunced [te.koˈma.te] in Spanish  and probably
[te.koˈmeit] in English is the name of tree that grows in Mexico 
and Central American countries. 
<p align="center">
  <img src="./figures/tecomate.png" 
   width="300" title="tecomate tree">
</p>
</br>

We use **TECOmate** to name our Git repository that hosts the implementation
of an hybrid achitecture for the enforcement of smart contracts. 
Hybrid means that it is composed of on and off blockchain
components. 

**The main idea:** split the clauses of the smart
contract of interest into two sets and enforce them
separately:

* on--blockchain set: enforced by a smart contract running on-blockchain.
* off-blockchain set: enforced by a smart contract running off-blocchain.

The main arguments in support of hybrid architectures are
detailed in 
[On and Off-Blockchain Enforcement Of Smart Contracts](https://arxiv.org/pdf/1805.00626.pdf "position paper")). In summary the argument is that:

* the hybrid approach help in meeting some QoS requirements imposed on
smart contracts that neither on of off blockchain approaches
can meet individually. 

* application that involve several
smart contracts running independent on and off blockchain
components will become common practice in the near future. 


As shown in the figure, to implement such architeture we 
integrate several smart contract technologies and
tools.

<p align="center">
  <img src="./figures/ccc-ethereum-integrationToolsTechnologies.png" 
   width="800" title="ccc-ethereum integration, tools and technologies">
</p>

An elaborated discussion of the components and their
integration is presented in 
[Implementation of Smart Contracts Using Hybrid Architectures with On- and Off-Blockchain Components](https://arxiv.org/pdf/1808.00093.pdf "implementation paper")).
The following explanation of the figures is a brief summary:

* Contract Compliance Checker:
* epromela:




# Installation

The directions for installation of epromela are documented in
the [UserGuide_v1.2.pdf](./UserGuide_v1.2.pdf) file. The document
also includes examples that demonstrate its operation.

# Contributors

*  Massimo Strano developed the underlying Java components
   that integrate drools with the Contract Compliance
   Checker as part of his PhD dissertation (2010) at University 
   of Newcastle, UK.
*  Ionnis Sfyrakis from University of Newcastle, UK
   (Ioannis.Sfyrakis@newcastle.ac.uk) implemented
   the Web server interfaces to the Contract Compliance
   Checker as part of his Masters degree (2012) at 
   Newcastle and since them he has been actively
   contributing to the hybrid architecture. 
*  [Carlos Molina-Jimenez](https://www.cl.cam.ac.uk/~cm770/ "MyWebPage")
   from **The Department of
   Computer Science and Technology (Computer Laboratory),
   University of Cambridge**
   (Carlos.Molina@cl.cam.ac.uk) has been the main
   architect of the architecture.
   He has been maintaining, documenting and testing the tool.
   He is currently (2018) working in the
   [TESCON project](https://www.cl.cam.ac.uk/~cm770/tescon/tescon.html
   "TESCON webpage") (EPSRC grant Grant: RG90413 NRAG/536).



# Bug reporting and comments

Feel free to email
[carlos.molina + @ + cl.cam.a.uk](mailto:carlos.molina@cl.cam.ac.uk)
if you have comments, bugs to report or questions.


# Licence
The contraval tool is released under the Apache License,
Version 2.0 which is available from Apache’s web pages.
