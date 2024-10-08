---
permalink: /
title: "About me"
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---

<!-- This is the front page of a website that is powered by the [Academic Pages template](https://github.com/academicpages/academicpages.github.io) and hosted on GitHub pages. [GitHub pages](https://pages.github.com) is a free service in which websites are built and hosted from code and data stored in a GitHub repository, automatically updating when a new commit is made to the respository. This template was forked from the [Minimal Mistakes Jekyll Theme](https://mmistakes.github.io/minimal-mistakes/) created by Michael Rose, and then extended to support the kinds of content that academics have: publications, talks, teaching, a portfolio, blog posts, and a dynamically-generated CV. You can fork [this repository](https://github.com/academicpages/academicpages.github.io) right now, modify the configuration and markdown files, add your own PDFs and other content, and have your own site for free, with no ads! An older version of this template powers my own personal website at [stuartgeiger.com](http://stuartgeiger.com), which uses [this Github repository](https://github.com/staeiou/staeiou.github.io).

A data-driven personal website
======
Like many other Jekyll-based GitHub Pages templates, Academic Pages makes you separate the website's content from its form. The content & metadata of your website are in structured markdown files, while various other files constitute the theme, specifying how to transform that content & metadata into HTML pages. You keep these various markdown (.md), YAML (.yml), HTML, and CSS files in a public GitHub repository. Each time you commit and push an update to the repository, the [GitHub pages](https://pages.github.com/) service creates static HTML pages based on these files, which are hosted on GitHub's servers free of charge.

Many of the features of dynamic content management systems (like Wordpress) can be achieved in this fashion, using a fraction of the computational resources and with far less vulnerability to hacking and DDoSing. You can also modify the theme to your heart's content without touching the content of your site. If you get to a point where you've broken something in Jekyll/HTML/CSS beyond repair, your markdown files describing your talks, publications, etc. are safe. You can rollback the changes or even delete the repository and start over -- just be sure to save the markdown files! Finally, you can also write scripts that process the structured data on the site, such as [this one](https://github.com/academicpages/academicpages.github.io/blob/master/talkmap.ipynb) that analyzes metadata in pages about talks to display [a map of every location you've given a talk](https://academicpages.github.io/talkmap.html).

Getting started
======
1. Register a GitHub account if you don't have one and confirm your e-mail (required!)
1. Fork [this repository](https://github.com/academicpages/academicpages.github.io) by clicking the "fork" button in the top right.
1. Go to the repository's settings (rightmost item in the tabs that start with "Code", should be below "Unwatch"). Rename the repository "[your GitHub username].github.io", which will also be your website's URL.
1. Set site-wide configuration and create content & metadata (see below -- also see [this set of diffs](http://archive.is/3TPas) showing what files were changed to set up [an example site](https://getorg-testacct.github.io) for a user with the username "getorg-testacct")
1. Upload any files (like PDFs, .zip files, etc.) to the files/ directory. They will appear at https://[your GitHub username].github.io/files/example.pdf.
1. Check status by going to the repository settings, in the "GitHub pages" section

The main configuration file for the site is in the base directory in [_config.yml](https://github.com/academicpages/academicpages.github.io/blob/master/_config.yml), which defines the content in the sidebars and other site-wide features. You will need to replace the default variables with ones about yourself and your site's github repository. The configuration file for the top menu is in [_data/navigation.yml](https://github.com/academicpages/academicpages.github.io/blob/master/_data/navigation.yml). For example, if you don't have a portfolio or blog posts, you can remove those items from that navigation.yml file to remove them from the header.

Create content & metadata
------
For site content, there is one markdown file for each type of content, which are stored in directories like _publications, _talks, _posts, _teaching, or _pages. For example, each talk is a markdown file in the [_talks directory](https://github.com/academicpages/academicpages.github.io/tree/master/_talks). At the top of each markdown file is structured data in YAML about the talk, which the theme will parse to do lots of cool stuff. The same structured data about a talk is used to generate the list of talks on the [Talks page](https://academicpages.github.io/talks), each [individual page](https://academicpages.github.io/talks/2012-03-01-talk-1) for specific talks, the talks section for the [CV page](https://academicpages.github.io/cv), and the [map of places you've given a talk](https://academicpages.github.io/talkmap.html) (if you run this [python file](https://github.com/academicpages/academicpages.github.io/blob/master/talkmap.py) or [Jupyter notebook](https://github.com/academicpages/academicpages.github.io/blob/master/talkmap.ipynb), which creates the HTML for the map based on the contents of the _talks directory). -->

I am a third year master student from School of Automation, Beijing Institute of Technology. My research interest includes model predictive control.

I did some research on these topics:

Control methods in PMSM
------
**Deadbeat current predictive control**

In the traditional PMSM vector control scheme, the current loop is controlled by a PI regulator, which is corrected multiple times according to the current error, and then through PWM, inverter output, sampling and other delay links, the current response has a large hysteresis. In order to make the sampled current have a faster response speed and smaller current ripple, I used a deadbeat predictive control model instead of a PI regulator as the control law of the current loop.

The deadbeat current control calculates the voltage of the next switching cycle through the state equation of the PMSM, the motor current feedback signal and the current reference output by the speed loop.

<!-- I used $\ i(k+2) = Ai(k+1)+Bu(k+1)+D(k+1) = i^*(k) \$.

Then I could get $\ u(k+1) = B^{-1}(i^*(k)-A(Ai(k)+Bu(k)+D(k))-D(k+1)) \$. -->

This is my control algorithm model.
![](/images/Deadbeat1.png)
It can be seen that the current waveform is smooth.
![](/images/Deadbeat2.png)

**Disturbance observer**

I added a disturbance observer. When a load mutation occurs in the motor, the disturbance observer first estimates the load torque information based on the change in rotational speed, and uses it as a compensation amount for the q-axis current at a certain ratio, thus correcting a new reference current so that the system can respond to sudden changes. Current response speed under load is significantly improved, solving the problem of poor anti-interference in traditional deadbeat current prediction control systems.

This is my control algorithm model.
![](/images/DO1.png)
<!-- Disturbance observer structure diagram is here.
![](/images/DO2.png) -->
It can be seen that the motor has better anti-disturbance performance and the disturbance estimation is also good.
![](/images/DO3.png)

**SVPWM dead time compensation**

When we design the inverter, in order to prevent the upper and lower bridge arms from being directly connected, we need to set a dead time to delay the conduction of the switch device. However, the existence of the dead time will cause the inverter output voltage waveform to have a certain amplitude and phase error, which is not what we want to see. Therefore, I designed a dead time compensation strategy, using the volt-second product balance principle to obtain the compensation time.

This is my control algorithm model.
![](/images/SVPWM1.png)
It can be seen that the motor torque ripple is significantly reduced.
![](/images/SVPWM2.png)

**State estimation based on EKF**

I used EKF to estimate the state of PMSM. I discretized the PMSM current equation in the stationary coordinate system, and then predicted and corrected the state.

This is my control algorithm model.
![](/images/EKF1.png)
It can be seen that the error of estimation is small.
![](/images/EKF2.png)
Here is my paper. [Current Prediction Control Strategy of Permanent Magnet Synchronous Motor Based on Extended Kalman Filter](https://ieeexplore.ieee.org/document/9634498)

Secure MPC
------
I considered a Denial-of-Service (DoS) attack which could disrupt the channels of communication between sensor, controller and actuator when designing MPC in networked systems.
![](/images/SecureMPC1.png)

To mitigate the impact of DoS attack and maintain stability even under adverse conditions, I proposed a resilient MPC algorithm with a suitable sampling update strategy, combined with an actuator buffer for storing feasible control inputs.

Moreover, I am interested in inherent robustness properties of MPC. That is to say, MPC with a nominal prediction model and persistent but bounded disturbances has some degree of inherent robustness when the terminal control law and the terminal penalty matrix are chosen as the linear quadratic control law and the related Lyapunov matrix, respectively. In this case, I combined it with the duration of DoS attack to derive the bound of disturbances.

Here are my papers. [Stabilizing nonlinear model predictive control under Denial-of-Service attack via dynamic samples selection](https://www.sciencedirect.com/science/article/abs/pii/S0005109824000839?via%3Dihub) and [Inherent attack tolerance properties of model predictive control under DoS attacks](https://www.sciencedirect.com/science/article/abs/pii/S0016003223007573?via%3Dihub).

Learning MPC
------
**Learning the system dynamics**

I used ELM network to fit the system dynamics model and then applied nonlinear MPC to control the system state trajectory to a specified equilibrium point. I studied the closed-loop stability and derived that with the bound of error on the training set, the system is input-to-state stable.

**Learning the controller design**

I studied a paper named "MPC-Inspired Reinforcement Learning for Verifiable Model-Free Control". The authors proposed a new type of controller which was in structure similar to QP. However, its parameters were being trained via DRL method instead of deriving from system models. I applied this controller to PMSM in both simulation and experiments.
![](/images/PMSM.png)
Click here to see my video. [PMSM with FOC](https://youtu.be/RWU3KpIIk64) and [PMSM with LQP](https://www.youtube.com/watch?v=nCaUqFcvqo0). The LQP result was not satisfactory since the microcontroller could not run the algorithm on time.

<!-- How to edit your site's GitHub repository
------
Many people use a git client to create files on their local computer and then push them to GitHub's servers. If you are not familiar with git, you can directly edit these configuration and markdown files directly in the github.com interface. Navigate to a file (like [this one](https://github.com/academicpages/academicpages.github.io/blob/master/_talks/2012-03-01-talk-1.md) and click the pencil icon in the top right of the content preview (to the right of the "Raw | Blame | History" buttons). You can delete a file by clicking the trashcan icon to the right of the pencil icon. You can also create new files or upload files by navigating to a directory and clicking the "Create new file" or "Upload files" buttons. 

Example: editing a markdown file for a talk
![Editing a markdown file for a talk](/images/editing-talk.png)

For more info
------
More info about configuring Academic Pages can be found in [the guide](https://academicpages.github.io/markdown/). The [guides for the Minimal Mistakes theme](https://mmistakes.github.io/minimal-mistakes/docs/configuration/) (which this theme was forked from) might also be helpful. -->
