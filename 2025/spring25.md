# Tanju Ozdemir VIP Notebook Spring 2025
Group:\
Tanju Ozdemir\
Stephen Mezyk\
Rohan Konanki\
Yash Agrawal\
Colin Hakes\
Han Min


## Index
[Week 1](#week1)\
[Week 2](#week2)\
[Week 3](#week3)\
[Week 4](#week4)\
[Week 5](#week5)\
[Week 6](#week6)\
[Week 7](#week7)\
[Week 8](#week8)\
[Week 9](#week9)\
[Week 10](#week10)\
[Week 11](#week11)\
[Week 12](#week12)\
[Week 13](#week13)\
[Week 14](#week14)\
[Week 15](#week15)\
[Week 16](#week16)

## Week 1 <a name="week1"></a>

### Meeting Notes

- Went over the syllabus and timeline for the semester
- Subteams were discussed
- Will be joining Inverse Spectra subteam

### Tasks 
- [x]  Fill in signup sheet
- [x]  Read Syllabus and Slides
- [x]  Set up PACE ICE and VSCode environment 

## Week 2 <a name="week2"></a>

### Meeting Notes

- Recap of Timeline
- Subteam annnounced
- PACE ICE down for maintainence Jan 13-16
- Went over basics of Inverse Spectra problem (XRD, Rietveld Refinement, Materials Project) (See Slides)
### Main Point 
- Simulation of XRD Spectra is exceptionally computationally expensive, using existing methods (eg. Reverse Monte Carlo)
- Use Active Learning to figure out crystal structure based on existing XRD Spectra
- Crystal Structure represented as graphs with nodes as specific atoms and edges as bonds 
  - Fit must be close
  - Better than existing methods (Beat the Reverse Monte Carlo) 
Surrogate model takes over the work of running multiple simulations

Possible goals
Conditional Diffusion to replace existing packages
Building surrogate model


### Tasks 
- [x]  Meet with team before 1/27

## Week 3 <a name="week3"></a>
- Monday was MLK Jr Day (no meeting)
  

### Meeting Notes

01/24
- Group meeting 3:15PM Friday recurring 
- Stephen is group leader
- Established plan to gather research papers on inverse problems
- Shared DiffCSP and ActiveStructOp Github Repos
- Briefly shared what was worked on last semester (fixing version issues between DiffCSP and ActiveStructOp)
  
### Tasks 
- [x]  Ask Ian for his draft research paper
- [x]  Read DiffCSP paper
- [x]  Read over slack chat


## Week 4 <a name="week4"></a>

### Meeting Notes
- Continued presentation on ActiveStructOp
- Recap of last semeser's work using DiffCSP
- ActiveStructOp outperforms reverse Monte Carlo

New ideas:
**Project 1**
-Replace GNN with conditional DIffCSP as surrogate model
-Update DiffCSP values

**Project 2**
-Instead of random weights, use MatterTune (pre-trained GNN) 


### Code 
``` ```

### Tasks 
- [ ]  Task 1
- [ ]  Task 2
- [ ]  Task 3

### Links
[Text](link)

## Week 5 <a name="week5"></a>

### Meeting Notes

- Joined Project 1
- Encountered issues with ActiveStructOpt and DiffCSP branches 
- Errors likely due to incorrect branches being installed 


### Code 
Obtain API key from materials project: https://www.materialsproject.org 

``export API_KEY=**insert api key here**``

install DiffCSP and use the dependencies set in your localenv 

``pip install git+https://github.com/karishmathakrar/DiffCSP_kt.git@main#egg=DiffCSP --no-deps`` 

ActiveStructOpt repo from Akshay

`git clone https://github.com/akshaydaf/ActiveStructOpt/blob/incorporate-diff-sampling/test_aso_diff.py`\
`cd **whatever you named the cloned repo**`

Copy config.yaml file from DiffCSP into ActiveStructOpt

Run the following but with updated paths for your system: 

''export PROJECT_ROOT=/home/hice1/**username**/ActiveStructOpt-DiffCSP/ActiveStructOpt export HYDRA_JOBS=/home/hice1/**username**/ActiveStructOpt-DiffCSP/ActiveStructOpt/hydra_jobs export WANDB_DIR=/home/hice1/**username**/ActiveStructOpt-DiffCSP/ActiveStructOpt/wandb_dir'''

To confirm the integration is successful:

``python test_aso_diff.py``

### Tasks 
- [X]  sucessfully run test aso file
- [X]  fix bugs
- [X]  download checkpoint files

### Links
[Text](link)

## Week 6 <a name="week6"></a>

### Meeting Notes
- Resolved integration issues with DiffCSP and ActiveStructOpt
- Required the installation of checkpoint files from original DiffCSP
- Successfully ran test aso file

### Code 

- Updated the installation instructions from last week
- Deleted cloned ActiveStructOpt and DiffCSP and installed correct versions

Obtain API key from materials project: https://www.materialsproject.org 

``export API_KEY=**insert api key here**``\

clone DiffCSP and use the dependencies set in your localenv 

``git clone -b remove-config https://github.com/karishmathakrar/DiffCSP_kt.git``\ 

Clone the ActiveStructOpt repo from Akshay into ICE

`git clone https://github.com/akshaydaf/ActiveStructOpt/blob/incorporate-diff-sampling/test_aso_diff.py`\
`cd **whatever you named the cloned repo**`

In diffusion.py within ActiveStructOpt
change new_structure so that:

`new_structure = sample.main(self.model_path, self.save_path, self.formula, self.num_evals, self.batch_size, self.step_lr, self.lengths, self.angles)`

Copy config.yaml file from DiffCSP into ActiveStructOpt (if it's not there already)\
Change the username in the directories of the config.yaml to reflect your own\

Run the following but with updated paths for your system: 

''export PROJECT_ROOT=/home/hice1/**username**/ActiveStructOpt-DiffCSP/ActiveStructOpt  export HYDRA_JOBS=/home/hice1/**username**/ActiveStructOpt-DiffCSP/ActiveStructOpt/hydra_jobs export WANDB_DIR=/home/hice1/**username**/ActiveStructOpt-DiffCSP/ActiveStructOpt/wandb_dir'''

Download DiffCSP checkpoints from here: https://drive.google.com/drive/folders/11WOc9lTZN4hkIY7SKLCIrbsTMGy9TsoW

Unzip the file, and copy it to ICE 

from mp_csp in diffcsp-checkpoints:

copy the last.ckpt to  pretrained-checkpoints in diffcsp-kt

To confirm the integration is successful:

``python test_aso_diff.py``

### Tasks 
- [ ]  Task 1
- [ ]  Task 2
- [ ]  Task 3

### Links
[Text](link)

## Week 7 <a name="week7"></a>

### Meeting Notes

-


### Code 
```print("hello world") ```

### Tasks 
- [ ]  Task 1
- [ ]  Task 2
- [ ]  Task 3

### Links
[Text](link)

## Week 8 <a name="week8"></a>

### Meeting Notes

Insert Notes Here


### Code 
```print("hello world") ```

### Tasks 
- [ ]  Task 1
- [ ]  Task 2
- [ ]  Task 3

### Links
[Text](link)

## Week 9 <a name="week9"></a>

### Meeting Notes

Insert Notes Here


### Code 
```print("hello world") ```

### Tasks 
- [ ]  Task 1
- [ ]  Task 2
- [ ]  Task 3

### Links
[Text](link)

## Week 10 <a name="week10"></a>

### Meeting Notes

Insert Notes Here


### Code 
```print("hello world") ```

### Tasks 
- [ ]  Task 1
- [ ]  Task 2
- [ ]  Task 3

### Links
[Text](link)

## Week 11 <a name="week11"></a>

### Meeting Notes

Insert Notes Here


### Code 
```print("hello world") ```

### Tasks 
- [ ]  Task 1
- [ ]  Task 2
- [ ]  Task 3

### Links
[Text](link)

## Week 12 <a name="week12"></a>

### Meeting Notes

Insert Notes Here


### Code 
```print("hello world") ```

### Tasks 
- [ ]  Task 1
- [ ]  Task 2
- [ ]  Task 3

### Links
[Text](link)

## Week 13 <a name="week13"></a>

### Meeting Notes

Insert Notes Here


### Code 
```print("hello world") ```

### Tasks 
- [ ]  Task 1
- [ ]  Task 2
- [ ]  Task 3

### Links
[Text](link)

## Week 14 <a name="week14"></a>

### Meeting Notes

Insert Notes Here


### Code 
```print("hello world") ```

### Tasks 
- [ ]  Task 1
- [ ]  Task 2
- [ ]  Task 3

### Links
[Text](link)

## Week 15 <a name="week15"></a>

### Meeting Notes

Insert Notes Here


### Code 
```print("hello world") ```

### Tasks 
- [ ]  Task 1
- [ ]  Task 2
- [ ]  Task 3

### Links
[Text](link)

## Week 16 <a name="week16"></a>

### Meeting Notes

Insert Notes Here


### Code 
```print("hello world") ```

### Tasks 
- [ ]  Task 1
- [ ]  Task 2
- [ ]  Task 3

### Links
[Text](link)
