---
layout: default
description: Material for the University of Manitoba course MATH 4370-7370, Linear Algebra and Matrix Analysis
---

## MATH 4370-7370 <br> Linear Algebra and Matrix Analysis <br> Fall 2023 outline

### Objectives of the course

Matrices are ubiquitous in many aspects of mathematics. They show up, for instance, when considering the local asymptotic stability of equilibria of systems of ordinary differential equations, the long term behaviour of Markov chains, the study of graphs and the discretization of reaction-diffusion equations.

Objectives of the course: 
1. explore the role of matrices in several fields of mathematics;
2. study properties of these matrices;
3. develop an understanding of how to deal with matrices in software.

### Rough course program

Note that some content could change.

1. *Matrices are everywhere*:
    - Linear systems of differences equations
    - Ordinary differential equations
    - Discrete-time Markov chains
    - Discretisation of partial differential equations
2. *Eigenvalues, eigenvectors, Gershgorin disks*:
    - Eigenpairs
    - Algebraic multiplicity
    - Similarity
    - Geometric multiplicity
    - The Gershgorin Theorem and friends
3. *Factorisations, canonical forms and decompositions*:
    - Unitary matrices and QR factorisation
    - Schur's form
    - Normal matrices
    - Jordan canonical form
    - Singular values and the SVD
4. *Nonnegative matrices*:
    - Perron-Frobenius Theorem
    - Stochastic matrices
5. *M-matrices*
6. *Norms and matrix norms*
    - Vector norms on matrices
    - Matrix norms
    - Matrix norms and singular values

Although not detailed explicitly above, we will also repeatedly consider links between matrices and graphs.

### Prerequisites

For University of Manitoba students: MATH 2090, Linear Algebra 2. 

For the information of students not having taken 2090, when I teach that course, I usually use Axler's *Linear algebra done right* with some notes added to compensate for the quasi-absence of determinants in Axler.

While the prereqs are quite low, you should be comfortable with the content of a solid second-year linear algebra course: the pace of the course is sustained, so you will not have time to work on prereqs.

### Who's teaching?

- Instructor: Julien Arino
- Office: 432 Machray Hall
- Email: [julien.arino@umanitoba.ca](mailto:julien.arino@umanitoba.ca)
- I do not answer the telephone in my office, don't bother.

### Where and when?

- Class schedule: 10:00-11:15 (Central) Tuesday & Thursday.
- Class location: TBD.
- Office hours: TBD. There will be both in-person and zoom sessions.
- Course page: UMLearn (and this repository for some content).

### Video for remote attendance

Courses will be live cast (precise method TBD, most likely zoom or YouTube Live) and recorded. A zoom link will also be open throughout the lectures to let remote participants ask questions if they want. 

It would be greatly appreciated if local students did attend class rather than watch the videos and if remote students turned on their cameras.


### Course number

This course is available to undergraduate students only as MATH 4370 and to University of Manitoba graduate students as either MATH 4370 or MATH 7370. Offsite PIMS students must register in MATH 7370.

Assignments and the project are less involved for those enrolled in MATH 4370 (see separate MATH 4370 syllabus).


### Textbook
We will not be using a textbook in the regular way, but most of the material will be based on Horn & Johnson, *Matrix Analysis* (Second Edition), Cambridge University Press, 2013 and Fiedler, *Special Matrices and Their Applications in Numerical Mathematics: Second Edition*, Dover, 2013.
Lecture notes were developed during the Fall 2018 session and will be available for download on UMLearn. Please bear in mind that they may contain typos.
Extracts from other books as well as slides will also be distributed as we progress. A list of useful books (all available online from the Libraries) will be distributed and updated throughout the term.

As indicated, the course notes might contain typos. It is also possible that the videos will have issues. If you see a problem, please let me know.


### Evaluation

There will be no formal tests or examinations. Evaluation of the performance in this course will involve two components: eleven assignments and one final project. The final mark will be decomposed as follows:

| Type of evaluation | Weight per evaluation | Total weight |
|--------------------|-----------------------|--------------|
| Mathematics assignments (4) | 5% each | 20% |
| Coding assignments (4) | 5% each | 20% |
| Project assignments (2) | 10% each | 20% |
| Final project (1) | 30% | 40% |


### Notes on evaluations
1. All assignments will be posted on UMLearn shortly after the start of term.
There are 3 types of assignments. 
    - **4 mathematics assignments (MA)**. Each of these assignments involves answering a certain number of questions selected from a list. These assignments roughly correspond to topics in the course but can be returned at any time and in any order, bearing in mind the constraint of *cumulative evaluation weight* detailed below. (Numbering is just there to distinguish them.) MATH 7370 students must pick more questions and some harder questions than students in MATH 4370. (This is clearly indicated in the assignments.)
	- **4 coding assignments (CA)**. Each of these assignments involves writing some matrix analysis functions. Authorised languages are `R`, `Python` and `Octave` (a `MatLab` lookalike), although `R` is preferred. (syzygy.ca is now available to UofM students and works well with `R`.)  Coding assignments 1-3 can be returned in any order and at any time before coding assignment 4, bearing in mind the constraint of *cumulative evaluation weight* detailed below. Coding assignment 4 is summative of preceding assignments and due (electronically) Friday 3 December at 23:59.
	- **2 project assignments (PA)**. These assignments are designed to help you define and get started on your final project. They must be returned in sequence and have due dates. Project assignment 1 is due at 23:59 on 6 October, project assignment 2 is due at 23:59 on 17 November.
2. Further remarks on assignments.
    - **Cumulative evaluation weight constraint**. Although most assignments do not have due dates, it is *imperative* that by 16 November at 23:59, I have received 3 out of the 4 mathematics assignments, 3 out of the 4 coding assignments and, of course, the 2 project assignments due before then. I will only mark 1 more mathematics assignment, 1 more coding assignments and 1 project assignment received after that date.
	- All *assignments* (i.e., except the *Final project*) must have been handed out by the last day of classes, 11 December 2023 at 23:59. Any assignment handed in after that date will receive a mark of zero.
	- All assignments should be submitted electronically on UMLearn. Hand-written mathematics or project assignments are **not** acceptable for students registered in MATH 7370. $\LaTeX$ is preferred, but projects using LibreOffice or Word are acceptable. Instructions on typesetting will be distributed during the term.
	- For those assignments with due dates, late assignments will not be accepted.
3. The **Final project** will be assigned during the term using project assignments. Some remarks.
    - The Final project is due during the Final Examination period (11-23 December).
	- The project must be typeset. $\LaTeX$ is preferred, but projects using LibreOffice or Word are acceptable. Instructions on project typesetting will be distributed during the term.
	- If time and class enrolment permit it, oral presentations of the projects will be organised. If that is the case, then this presentation will count as part of the mark for the project. (This will be discussed during term.)


### Note on self-declarations of absences

The University of Manitoba now allows self-declaration of short duration absences of less than 5 days. In the interest of fairness, this measure is also available to students attending remotely as PIMS students.

Self-declarations are meant to be used for sporadic absences, not as a general mechanism to delay evaluations. As a consequence, I will not admit more than two submissions during the term.

The self-declaration form is available [here](https://umanitoba.ca/sites/default/files/2022-09/Self%20Declaration%20Fillable%20Form-%20FINAL%20for%20Website.pdf). For students from other universities: replace "U of M email account" in the sentence "submitting this form electronically from a U of M email account will be accepted in lieu of a signature" with your home institution.


### Voluntary Withdrawal deadline

The Voluntary Withdrawal deadline is 23 November 2023.


### Academic Dishonesty Policy
The Department of Mathematics, the Faculty of Science and the University of Manitoba all regard acts of academic dishonesty in quizzes, tests, examinations or assignments as serious offences and may assess a variety of penalties depending on the nature of the offence.

Acts of academic dishonesty include bringing unauthorized materials into a test or exam, copying from another student, plagiarism and examination personation. Students are advised to read section 7 (Academic Integrity) and section 4.2.8 (Examinations: Personations) in the General Academic Regulations and Requirements of the current Undergraduate Calendar. Note, in particular, that cell phones and pagers are explicitly listed as unauthorized materials, and hence may not be present during tests or examinations.

Penalties for violation include being assigned a grade of zero on a test or assignment, being assigned a grade of "F" in a course, compulsory withdrawal from a course or program, suspension from a course/program/faculty or even expulsion from the University. For specific details about the nature of penalties that may be assessed upon conviction of an act of academic dishonesty, students are referred to University Policy 1202 (Student Discipline Bylaw) and to the Department of Mathematics policy concerning minimum penalties for acts of academic dishonesty.

All students are advised to familiarize themselves with the Student Discipline Bylaw, which is printed in its entirety in the Student Guide, and is also available on-line or through the Office of the University Secretary. Minimum penalties assessed by the Department of Mathematics for acts of academic dishonesty are available on the Department of Mathematics web-page.
