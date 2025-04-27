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

clone DiffCSP and use the dependencies set in your localenv 

`git clone -b remove-config https://github.com/karishmathakrar/DiffCSP_kt.git`

Clone the ActiveStructOpt repo from Akshay into ICE

`git clone -b update-sampler https://github.com/akshaydaf/ActiveStructOpt.git`
`cd ActiveStructOpt`

In `diffusion.py` within ActiveStructOpt's sampler (`/home/hice1/**username**/ActiveStructOpt/activestructopt/sampler/diffusion.py`)

change `new_structure` so that:

`new_structure = sample.main(self.model_path, self.save_path, self.formula, self.num_evals, self.batch_size, self.step_lr, self.lengths, self.angles)`

Copy `config.yaml` file from DiffCSP into `activestructopt` (if it's not there already)

In `config.yaml` for DiffCSP and ActiveStructOpt
Change the username in the listed directories to reflect your own


Download DiffCSP checkpoints from here: https://drive.google.com/drive/folders/11WOc9lTZN4hkIY7SKLCIrbsTMGy9TsoW

Unzip the file, and copy it to ICE 

from `mp_csp` in `diffcsp-checkpoints`:

copy the `last.ckpt` to pretrained-checkpoints in diffcsp-kt (`/home/hice1/**username**/DiffCSP_kt/pretrained_checkpoints`)

Run the following but with updated paths for your system (Obtain API key from materials project: https://www.materialsproject.org) (This has to be run at each initialization): 

`export PROJECT_ROOT=/home/hice1/**username**/ActiveStructOpt-DiffCSP/ActiveStructOpt export HYDRA_JOBS=/home/hice1/**username**/ActiveStructOpt-DiffCSP/ActiveStructOpt/hydra_jobs export WANDB_DIR=/home/hice1/**username**/ActiveStructOpt-DiffCSP/ActiveStructOpt/wandb_dir export API_KEY=**insert api key here**`


To confirm the integration is successful:

``python test_aso_diff.py``

## Week 7 <a name="week7"></a>

### Meeting Notes

-Focused on getting everyone to successfully run the test_aso_diff.py file successfully
-Reinstalling DiffCSP-kt as a python package in conda env using the following command seemes to have fixed the issue:
`pip install -e. git+https://github.com/karishmathakrar/DiffCSP_kt.git@remove-config#egg=DiffCSP --no-deps`
-I was able to run the file without DiffCSP-kt as an installed package (had the needed files in my root directory, ActiveStructOpt pointed to the directories in DiffCSP using the config.yaml file)

## Week 8 <a name="week8"></a>

### Meeting Notes

-Forked and merged changes for ActiveStructOpt and DiffCSP
-Shared admin role with Ian for both repos to ensure continuity of work into the future


### Tasks 
- [X]  Notify team of new repo 
- [X]  Share link in slack


## Week 9 <a name="week9"></a>

### Meeting Notes
-Midterm presentations


### Code 
```print("hello world") ```

### Tasks 
- [ ]  Task 1
- [ ]  Task 2
- [ ]  Task 3

### Links
[Text](link)

## Week 10 <a name="week10"></a>

Spring Break - No Meetings this week


## Week 11 <a name="week11"></a>

### Meeting Notes
-split into two subteams: obtaining the gradient outputs of diffusion models, and modifying the loss weighting on torch.py

Obtaining the model/outputs of diffusion.py, specifically pred_x (max 4 people)
Yash Agrawal
Min Han
Tanju Ozdemir
Rohan Konanki

Changing torch.py to include a new loss function and weighting (max 3 people)
Stephen mezyk
Jerry Wang
Colin Hakes


-Discussed goals with Ian:

Ian - build an optimizer that uses the loss from the diffCSP and its gradients in addition to the loss from the forward model and its gradients. And combines those together, essentially by adding gradients together with some weighting factor, then optimize the structure using that
o   There's an optimizer already called torch that does the forward model, we need to combine the diffCSP loss gradients into that to bias it into the direction of possible crystals
o   There's a couple of tasks
§  Get diff csp to output gradients of its loss after each iteration 
§  be able to pass in a particular structure and get the gradients with respect to diff csp loss – likely the harder task
§  Create optimizer in active struct op that adds additional loss to the gradients from the model.
·  	“Take gradient of loss from diff csp and gradient of loss from forward and weight them of different values and add them together”
o   Probably make the weight a hyperparameter, not training
o   Files to be modifying
§  Diffcsp/pl_modules/diffusion.py inside of DIFFCSP
·  	This is for outputting gradients of loss after each iteration
·  	Pred_x and pred_lat are likely our gradients/noise
·  	We need to communicate these gradients/noise as outputs to activestructopt
§  activestructop/optimizer/torch.py


## Week 12 <a name="week12"></a>

### Meeting Notes
03.31
Need to edit Diffusion.py in DiffCSP
Work completed on ActiveStructOpt side


04.05
Team worked on diffusion.py but unable to test due to Materials Project site being down

## Week 13 <a name="week13"></a>

### Meeting Notes
-Got outputs, but results unsatisfactory (lots of bugs)



## Week 14 <a name="week14"></a>

### Meeting Notes

-Started work to prepare for final presentation

### Tasks 
- [X]  Work on slides

## Week 15 <a name="week15"></a>

### Meeting Notes
- Presented Final Presentation 


### Tasks 
- [x]  Follow up on group paper assignment


## Week 16 <a name="week16"></a>

### Meeting Notes
-Worked on completing final group paper
`

### Tasks 
- [x]  Add edits to group paper

