
# contraval (smart contract validation)

This repository hosts **epromela** ---a tool for
building models of smart contracts that can
be validated by the Spin model checker.
<br/>

### Validate your smart contracts before deployment
A particularity of smart contracts deployed on--blockchain 
is that because of their descentralisation and openess, 
they are hard to amend after deployment. Therefore, we 
suggest that smart contracts are thoroughly validated 
(for example, using conventional model checking tools) 
to uncover potential logical inconsistencies of their clauses 
(omissions, contradictions, duplications, etc.). In addition, 
we suggest that the actual implementation is systematically 
tested before deployment. In hybrid architectures 
(see for example,
[Implementation of Smart Contracts Using Hybrid Architectures with On- and Off-Blockchain Components](https://arxiv.org/pdf/1808.00093.pdf "implementation paper"))
that include on and off--blockchain components the risk of 
implementing buggy is exacerbated by the interaction between 
the the components.

<br/>

HelloWorld example: As an example, let as have a look
at a helloWorld example of a smart contract between
a buyer and a store:

```
1) The buyer is obliged to pay the store withing the
   next 3 days. 
2) The store is obliged to acknowledge the payment 
   withing 24 hrs after receiving it. 
3) The contract will be considered complete either
 * normally when the store submits the acknowledge.
 * abnormally when one or both parties fail to meet
  their deadlines.
```
The contract in natural language can be represented
schematically. Depending on the execution model of the
operations, diffent models can be built.

As an example, let us assume the execution model shown in the
following figure.

<p align="center">
  <img src="./figures/executionmodelTOtoComplete.png" width="550" title="Execution model that completes in success or timeout">
</p>

On the basis of the exedcution model shown above, we can
represent the contract example schematically.

<p align="center">
  <img src="./figures/helloWorldSmartContractBuyerStoreExecTO.png" width="550" title="Hello world contract: buyer-store">
</p>

In the figure, *pay*  represents the execution
of the *pay*  operation initiated by the buyer.
Similarly, *ack* represens the execution of the
*ack* operation initiated by the store.
These executions, result in the generation of
business events that are notified to the
smart contract (see below), for example, the
execution of the operation *pay* generates the
*pay* business event.

A diamon represents an alternative output 
produced by the execution of the operation
located at its left. In accordance with 
the execution model, the outcome is either
sucess or timeout. For example, *payto* (where
*to* stands for timeout)
presentes the failure of the execution of 
the operation *pay* to complete before the deadline.


The dashed lines 
represent abnormal paths to contract completion.
For instance, the dashed line associated to *payto* 
means that the buyer failed to observe its
obligation to pay within 3 days. Consequently,
the contract ends abnormally.


### What can Epromela do with smart contracts?
Epromela is a language for writing models that
can be model checked by the Spin model checker. 

We have built it by extending the standard Promela language
with primitives that help developers build
models of smart contracts using constructs that
are natural to smart contracts. Examples of
these constructs are *role players (e.g.,
buyer and seller)*, *rights*,
*obligations* and *prohibitions*; and operations
such as *assign obligation to pay 
to buyer*, *has buyer fulfilled obligation to pay?*,
*cancel buyer's obligation to pay*,
etc. 


An epromela model can be presented to Spin 
for **model checking** and **generating test 
cases (execution sequences)**.

### Model checking 
 Spin can verify the logical consistency of the model
 epromela of the smart contract against correctness 
 properties written 
 in LTL (Linear Temporal Logics) formulae. <br />

### Generation of execution sequences (test cases) 
 Spin can be instructed to generate all the execution
 sequences encoded in the epromela model of the
 smart contract. The basic idea is to use Spin as a
 generator of counterexamples produced against 
 LTL formulae.

### Business Event Generator of epromela
At the heart of epromela lies a Business Event
Generator (BEG) that is responsible for 
generating the events that correspond to the
execution of contractual operations. 

To appreciate its functionality, let us have a look
at the figure bellow that shows the interaction
between the buyer and store of the contract example.

<p align="center">
  <img src="./figures/executionModelBilateralOperationsWithoutFailures.png" 
   width="400" title="Execution model of contractual operations 
               without failures.">
</p>

As shown in the figure, the execution of each contractual 
operation results in the exchange of messages between the two 
contractual parties. A copy of each message can be sent to third 
parties (for example, to a smart contract) as shown in the 
figure.

To reduce the number of states of the model, the BEG abstracts 
away the communication between the contracting parties and
generates the business events by itself as shown in the figure.

<p align="center">
  <img src="./figures/executionModelBilateralOperationsWithoutFailuresBEG.png" 
   width="400" title="Execution model of bilateral operations 
                      without failures, BEG.">
</p>


### Epromela model of the contract example
The smart contract oriented primitives provided by epromela 
help developers build models
that describe the behaivour of contractual interactions in an
intuitive manner. The figure bellow shows the two main
components of an epromela model, namely, the *BEG* and
the *set of rules*. It is based on the contract example,
consequently, the set of rules (stored in the *rules.h*
files) includes only two rules, one for each 
business operation.

The two rules include the contruct *IS_O*, where *O* stands 
for obligation, therefore, the construct reads _is obligation_.
*IS_O* is an illustrative example of the contract oriented primitives
that epromela offers. In *Rule(pay)*, *IS_O* indicates that
the rule will trigger only when it receives
the event *pay* and the buyer has a pending obligation
to pay.

<p align="center">
  <img src="./figures/epromelaModelOfBuyerStoreContractOutputTO.png" 
   width="400" title="epromela model of the buyer-store example with
                      output TO.">
</p>

If you are motivated to run the hello world example,
you can find the complete code (and instructions to run it)
at the [example/helloWorldSmartContract](https://github.com/carlos-molina/contraval/tree/master/examples/helloWorldSmartContractExecOutSuccessOrTO) folder.
A run of the model will mechanically produce all (three) the execution
sequences encoded in the model, namely:

```
- payto
- pay -> ack
- pay -> ackto
```
Where *payto* and *ackto* stand for expiration of time out to pay 
and expiration of time out to ack, respectively. You will notice
that the rules (included in the *rules.h* file) are slightly
different in comparison with the rules of the previous
model.


### Alternative epromela model of the contract example
The execution model of operations shown above is not unique. Another
altrnative is shoen in the figure.

As an example, let us assume the execution model shown in the
following figure.

<p align="center">
  <img src="./figures/executionmodelTOtoInitiate.png" width="550" title="Execution model that initiates or times out">
</p>

On the basis of this execution model, we can
represent the contract example schematically
in the following manner.

<p align="center">
  <img src="./figures/helloWorldSmartContractBuyerStoreInitiateTO.png" width="550" title="Hello world contract: buyer-store with init TO">
</p>

In the figure, *pay*  represents the execution
of the *pay*  operation initiated by the buyer.
Similarly, *ack* represens the execution of the
*ack* operation initiated by the store.
These executions, result in the generation of
business events that are notified to the
smart contract (see below), for example, the
execution of the operation *pay* generates the
*pay* business event.
A diamon represents an alternative execution 
split, *O* stands for obligation and *TO* 
stands for Time Out. In this model (there
are other alternatives), the
box at the right side of a diamon represents
the sucessful execution of the operation,
while the *TO* represents the expiration of the
deadline to succssfully execute the operation.

The dashed lines represent abnormal paths to contract 
completion. They results from failures to meet
deadlines.


The epromela model includes four rules and is shown in
the figure. Observe that the model includes two separate
rules (for for the normal outcome and another for
the timed out outcome) for handling each business 
operation. For instance, there is a rule for handling
*pay* and another one independent rule for handling
*payto*.

<p align="center">
  <img src="./figures/epromelaModelOfBuyerStoreContractInitTO.png" 
   width="400" title="epromela model of the buyer-store example with
                      init  TO.">
</p>



Motivated readers are welcome to run this alternative
model of the  hello world example,
they can find the complete code (and instructions to run it)
at the [example/helloWorldSmartContract](https://github.com/carlos-molina/contraval/tree/master/examples/helloWorldSmartContractInitOrTO) 
folder.
As in the model discussed earlier, a run of this
model will mechanically produce all (three) the execution
sequences encoded in the model, namely:

```
- payto
- pay -> ack
- pay -> ackto
```
Where *payto* and *ackto* stand for expiration of time out to pay 
and expiration of time out to ack, respectively.



### Execution model of bilateral operations with potential exceptions 
A salient feature of epromela is that it can model
exceptions on the basis of the following execution model:
<br/>

Contractual operations are bilateral in the sense that
their execution requires the interaction of the two
business partners. 
Upon completion of the execution of a given operation
each party independently declares its local outcome:
success, business failure (bizfail) or technical 
failure (tecfail).

Since the parties operate in a loosely coupled mode,
their outcomes does not necessarily match. For instance
a party might declare success whereas its counterpart
declares business failure.

To agree on the outcome of each operation and be able
to progress to the next one in harmony, the parties
rely on an output synchronizer that is responsible for 
receiving the individual outcomes, compute a single
outcome and notify it to the contractual parties and
possibly to other parties that are entitled to
follow the execution of the contract.

An schematic view of the execution model is
shown in the following figure.

<p align="center">
  <img src="./figures/executionModelOfBilateralOperationsWithFailures.png" width="550" title="Execution model of contractual i
               operations with failures.">
</p>

In the figure, *oper* stands for contractual operation, such as
*BuyReq*, *Pay*, *Conf*, etc.

<br/>
In this execution model, the BEG abstracts 
away the communication between the contracting parties and
plays the role of the output synchronizer as shown in the
figure.
 
<p align="center">
  <img src="./figures/executionModelOfBilateralOperationsWithFailuresBEG.png" width="550" title="Execution model of contractual 
                  operations with failures, BEG.">
</p>

The event generated by the BEG are sent to a set of business rules
for evaluation for contract compliance.

# Installation

The directions for installation of epromela are documented in
the [UserGuide_v1.2.pdf](./UserGuide_v1.2.pdf) file. The document
also includes examples that demonstrate its operation.

# Contributors

*  Abubkr A. Abdelsadiq developed the macros as part of his
   PhD dissertation (2012) at University of Newcastle, UK.
*  Ionnis Sfyrakis from University of Newcastle, UK
   (Ioannis.Sfyrakis@newcastle.ac.uk) implemented 
   the Python parsers to extract execution sequences during his
   Masters degree (2012) at Newcastle.
*  [Carlos Molina-Jimenez](https://www.cl.cam.ac.uk/~cm770/ "MyWebPage")
    from **The Department of
    Computer Science and Technology (Computer Laboratory),
    University of Cambridge** 
   (Carlos.Molina@cl.cam.ac.uk) implemented shell scripts to 
   mechanise the extraction of execution sequences. He has been
   maintaining, documenting and testing the tool.
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
 
