# Runtime Verification with TeSSLa: A Practical Case Study

This repository contains the implementation of a prototypical [Runtime Verification](https://www.sciencedirect.com/science/article/pii/S1567832608000775) demonstrator developed during a project at Infineon Austria's post-silicon V&V. The associated research paper is under review and will be published soon.

## System under Test (SuT)
The tested system is part of a verification and validation (V&V) management software used for post-silicon validation of semiconductor components. Periodically, this sub-system synchronizes requirements and related data from an external requirements management system. Those requirements describe the microelectronic correctness properties that subsequent verification runs, managed by the software, must fulfil. For every synchronization procedure, the system under test (SuT) must check the accuracy and overlap of the received data with the existing data. 

However, this check proved to be faulty at times and difficult to verify using traditional methods, such as testing, because the system's correctness depends mainly on its reaction to the external system's behavior (which may be faulty and unexpected as well). Hence, a verification of the SuT's behavior at operational runtime was planned and implemented by this prototypical demonstrator. 

## Methodology
This prototype used the [TeSSLa](https://tessla.io/) tool and language to develop an exemplary Runtime Verification approach with the following steps:

1. Created a specification written in the TeSSLa language. The specification contains all correctness properties that the SuT must fulfill to be considered correct. 
2. Utilized TeSSLa's interpreter/compiler to generate a monitor that compares the SuT behavior at runtime with the correctness properties of the specification.
3. Instrumented the SuT to yield a TeSSLa-conform log trace by extending its native logging system. The final extended logging functionality can store the log trace for offline verification or send each event immediately to an online Runtime Verification monitor.
4. Developed a server to receive log events dispatched by the instrumented SuT and provide a user interface for executing the generated monitor on log traces and viewing the output verdict.

## Repository Structure
* `/specification`: Contains the TeSSLa specification with a description of a correct system run.
* `/monitoring`: Implements the monitoring user interface and server-side trace processing to handle logged traces and execute the monitor on them.