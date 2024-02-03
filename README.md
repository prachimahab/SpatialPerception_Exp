# A data-driven generalization of spatial representations in natural images across individuals, tasks, and viewing time 

OSF Pre-Registration: https://osf.io/28vjd

## Project Abstract
Visual representations incorporate multiple cues into unified percepts that can support a variety of tasks, making them powerful but difficult to study. Here, we leverage natural scene databases and a series of pre-registered behavioral studies to identify task-general spatial representations. We presented 156 unique scenes to independent groups of participants who performed numerical egocentric distance estimation or distance discrimination tasks. We found remarkable scene-specific systematicity and generalization; participants’ numerical estimates showed strong sensitivity to target distance and highly reliable biases within individual scenes. These scene-specific deviations strongly predicted discrimination performance in independent participants. Results generalized across participants, tasks, durations, and outcome measures, indicating systematic biases for individual scenes. These scene-specific deviations, where the only shared factor was the stimuli themselves, suggest responsiveness to the same set of cues across tasks. These results implicate a finely-tuned, rapid mechanism for integrating object spatial information towards percepts of distance in natural images. All experiment details included in this repository can be used to replicate our findings, and extend them to new stimuli. 

## Experiments
Numerical Estimate: Participants gave numerical estimates of distance for 156 unique scenes for target objects at variable distances. Participants were instructed to imagine themselves standing in each scene at the camera position and estimate distance from their toes to the object the target was placed on, with responses typed into a designated box on the screen. Participants selected whether they preferred to respond in meters or feet and then continued on to three practice trials before beginning the experiment. The viewing duration (125 ms, 250 ms, 1000 ms) was manipulated between participants to quantify the development of distance representations over time. No error feedback was provided on practice trials, or in the following experiment trials. The aim was to familiarize participants with the speed of stimulus viewing duration and explicit distance estimation. 
Each trial began with a black central fixation cross presented for 500 ms followed by the stimulus at the assigned viewing duration. Stimulus presentation was immediately followed by a colored checkered mask for 500 ms. Participants were then shown a response page where they were prompted to enter their estimate for ‘How far away was the target?’ in a text box. Once a response was entered, the next trial automatically began. Participants completed a total of 156 distance estimation trials and 8 additional attention check trials evenly distributed throughout the experiment to verify data quality. 

Discrimination: An independent group of participants completed a distance discrimination task in the same set of images. Discrimination pairs (78 trials, 156 images) were chosen such that they evenly spanned a range of depth differences (0.2 m - 1.3 m). Unlike past discrimination studies having subjects compare the distance of two targets within the same scene, this experiment had two unique images in each discrimination trial, forcing participants to create independent representations of distance for each image and avoiding any repetition effects from seeing the same image twice. We hypothesized that larger differences in distance between the two targets would result in higher accuracy and lower response times. Images were presented for a variable duration (125 ms, 250 ms, 1000 ms), matching the numerical estimate task.  
Each trial began with a black central fixation cross for 500 ms, followed by a green fixation cross for 500 ms to indicate the trial was about to begin. Participants were then shown two images and responded which target object was closer to them if they were to imagine themselves in the scene. After each scene was presented, a colored checkered mask was shown for 500 ms. Responses were given via keypress (‘z’ or ‘m’, counterbalanced). Participants were encouraged to respond as quickly and accurately as possible. In total 78 distance discrimination trials and eight additional attention check trials were evenly distributed throughout the experiment. 
 

## What does this repository contain?

The folder for each experiment (numerical estimate, discrimination) contains the following:
1. Analysis  
2. Counterbalancing
3. Data
4. Frontend Experiment Code

The numerical estimate folder additionally contains 'stimuli_prep', which includes scripts for the process of creating our stimuli. We emply a novel deisgn for spatial judgements using SUN RGB-D images (https://rgbd.cs.princeton.edu/). Ground truth depth data from a kinect v2 sensor is used to place targets in the vertical midline of the image. Targets are selected such that there is an even distribution across the range of available depths (1 meter - 5 meters)

### Analysis 
Scripts for data analysis. 

### Counterbalancing
A main goal of this project is to understand how stimulus-specific cues drive spatial perception. Therefore, it is critical for stimulus order, hysteresis effects, and duration to be carefully balanced. Individual participants within any task and duration condition see a unique stimulus order. Participants were only eligible to complete either the numerical estimate or the discrimination task at one of three stimulus durations (125, 250, 1000 ms) to prevent stimulus repetition effects. Sample sizes for both experiments (n=156 per duration) were matched in the number of stimuli to enable a latin square counterbalancing method so that each individual scene occurred in each trial position an equal number of times across all participants in each task and duration. See our OSF Pre-Registration for a more detailed explanation (https://osf.io/28vjd).

### Frontend Experiment Code
All participants were recruited via Amazon’s Mechanical Turk, presented with an IRB compliant comprehensive consent form, and paid for their efforts according to the time each task took. This folder contains all frontend code necessary to collect data. An Apache server was used to run the experiment, and needs to be configured to allow for CORS in order for the web content to load. A copy of the Amazon Machine Image (AMI) created to host this experiment can be used for easy replication (provided upon request). 

- The main files for running the experiment are [exp-name]_CSS.css, [exp-name]_JS.js, and [exp-name]_HTML.html 
- The data is logged and saved as a CSV on the server in saveFile.php
- Participants receive an unique completion code via revealCode.html 
- source_withFeedback.html is adapted source code provided by Amazon Mechanical Turk for providing instructions, setting the survey link, and getting feedback from participants 
- experiment_variables.csv contains the variables that are needed for source_withFeedback.html (e.g. survey link). This method allows experimenters to publish a batch of multiple HITs (Human Intelligence Task) on Mechanical Turk

Unique, counterbalanced trial sequences were made using SUN-RGBD images. All images in the dataset were taken with Kinectv2 sensors, so the “ground truth” distance of the targets was extracted from the depth array for each image in the SUN-RGBD dataset. The following files allow for a balanced design in terms of images, duration, and range of target distances. 
- The folder 'jsons' contains the unique trial structures for a particular duration - one for each participant. Each json file contains the duration, image path, and masking image path for each trial, for a total of 156 trials.
- Participants were given a few practice trials to acclimate themselves to the experiment. The file practice_data.json reflects the trial structure for these trials.
- Image files: example.png (sample scene from SUN-RGBD) & fixation.jpg (standard fixation image) 
- counterbalancing.csv is a file that is referenced in [exp-name]_JS.js to select the correct trial sequence (JSON file) for a given HIT 

Note: A subset of the images available in the SUN-RGB D data set were used here (see numerical_estimate/frontend_experiment_code/numerical_estimate_exp/stimuli.) All images are available at https://rgbd.cs.princeton.edu/.

# Citations:

S. Song, S. Lichtenberg, and J. Xiao.
SUN RGB-D: A RGB-D Scene Understanding Benchmark Suite
Proceedings of 28th IEEE Conference on Computer Vision and Pattern Recognition (CVPR2015)

# Contact:
If you are interested in learning more about our work or have any questions feel free to contact us! 

Prachi Mahableshwarkar: pmahable@gwu.edu, George Washington University


Dwight Kravitz: kravitzd@gwu.edu, George Washington University 

John Philbeck: philbeck@gwu.edu, George Washington University
