# ERAD26 Academy: "Open Precipitation Nowcasting"
The main goal of the Open Nowcasting course is to focus on practical aspects of nowcasting, for both (operational) users and developers. Participants will learn theory on nowcasting, blending with NWP and nowcasting with machine-learning tools. This is combined with hands-on sessions using the open-source library pysteps, to bring the theory into practice. The course will be useful for both researchers and operational meteorologists, with either no or average nowcasting experience. A part of the Open Nowcasting course will be devoted to gathering the nowcasting community around pysteps to discuss challenges and future developments. This course forms the second part of a two-day training sequence and uses the processed datasets from the Open Source Software Tools for Radar Data Processing course on Saturday as one of the inputs for the nowcasting applications.
**When:** Sunday August 23, 2026, from 09:00 - 17:00 local time.

**Where:** Hydrometeorological Service of Serbia (RHMZ), Kneza Višeslava 66, Belgrade, Serbia.

**Registration:** [ERAD26 Academy](https://erad2026.rs/courses) [registration is closed]

## Tutors

[Ruben Imhoff](https://github.com/RubenImhoff) - [Jenna Ritvanen](https://github.com/ritvje) - [Lesley De Cruz](https://github.com/ladc) - [Mats Veldhuizen](https://github.com/mats-knmi) - [Miguel Aldana](https://github.com/AldanaMF)

# Program

| Time  | Content                                   | Speaker                              | Duration |
|-------|-------------------------------------------|--------------------------------------|----------|
| 09:00 | Welcome / Course overview                 | Ruben                                | 20'      |
| 09:20 | Lecture: "Pysteps in operations"          | Ruben, Lesley                        | 40'      |
| 10:00 | Coffee break                              |                                      | 30'      |
| 10:30 | Hands-on session “Starting with pysteps”  | Jenna, Miguel, Mats                  | 120'     |
| 12:30 | Lunch break                               |                                      | 60'      |
| 13:30 | Hands-on session “Blending with NWP”      | Mats, Lesley, Ruben                  | 120'     |
| 15:30 | Coffee break                              |                                      | 30'      |
| 16:00 | Lecture: "AI for nowcasting"              | Lesley, Jenna, Ruben                 | 45'      |
| 16:45 | Discussion                                | All                                  | 15'      |
| 17:00 | End of the short course                   |                                      |          |

# Prerequisites

*Participants need to bring their own laptop (Linux, Windows, Mac)*. 

The exercises in this short course will be done by using Google Colab notebooks. Therefore the attendees are expected to create a Google account before the session and copy the example notebooks to their Google Drive. The material will be provided in the [GitHub repository](https://github.com/pySTEPS/ERAD-nowcasting-course-2022).

## 1. Create a Google account

If you do not have a Google account yet, create it [here](https://accounts.google.com/signin/v2/identifier?flowName=GlifWebSignIn&flowEntry=ServiceLogin).

## 2. Install Google Chrome

For the best experience, we recommend using [Google Chrome](https://www.google.com/chrome) for this session. In many Linux distributions, the browser is known as [Chromium](https://www.chromium.org/Home), and it can be installed through the distribution's package management system. [Firefox](https://www.mozilla.org), [Microsoft Edge](http://www.microsoft.com/en-us/windows/microsoft-edge) and [Safari](http://www.apple.com/safari) should also work, but they might not support all functionalities needed for using the Google services.

## 3. Clone GitHub Repositories and copy notebooks to Colab

This step is required for running the Colab notebooks shared through the [GitHub repository](https://github.com/pySTEPS/ERAD-nowcasting-course-2026). Sign in to your Google account, go to [Colab](https://colab.research.google.com/?utm_source=scs-index) and run the following commands in a new notebook.

    # mount your Google drive to access it from Colab
    import os
    from google.colab import drive
    drive.mount("mnt")
    %cd mnt/MyDrive
    # clone the repository from GitHub
    !git clone https://github.com/pySTEPS/ERAD-nowcasting-course-2026.git
    # create notebook directory (if it doesn't already exist)
    if not os.path.exists('Colab Notebooks'):
        !mkdir 'Colab Notebooks'
    # copy the course notebooks to the above folder
    !cp -r ERAD-nowcasting-course-2026 'Colab Notebooks'

Now you can open the example notebooks in Colab through "File" (in the top bar) > "Open Notebook" > [look for the specific file you want to get started with] or open it directly from your Google Drive.

# Running the notebooks locally (alternative to Colab)

Colab is the recommended route for the course, but every notebook also runs on a
local checkout. Each notebook detects its environment and skips the Colab-only
steps (Google Drive mounting and the `apt-get`/`pip` installs) when it is not
running on Colab.

You need [uv](https://docs.astral.sh/uv/getting-started/installation/). Then:

    git clone https://github.com/pySTEPS/ERAD-nowcasting-course-2026.git
    cd ERAD-nowcasting-course-2026
    uv sync
    uv run jupyter lab

`uv sync` creates a `.venv` with every dependency pinned in `uv.lock`, including
the ones Colab pre-installs and the notebooks therefore never mention (notably
OpenCV, which pysteps needs for Lucas-Kanade optical flow). It picks Python 3.12
by default; 3.13 also works, while 3.14 is not yet supported because cartopy
publishes no wheels for it.

Open any notebook from the JupyterLab file browser and run it top to bottom.
Note that the first notebook you run downloads ~450 MB of pysteps example data
into the notebook folder; this happens once and is git-ignored.
