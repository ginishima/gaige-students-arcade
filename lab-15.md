# Initial Questions

OS: Windows 11
Docker version : 29.9.3
Whether you used Docker Desktop or Docker Engine: Desktop
The output of docker info summarized in one or two sentences:
How many containers are contained w/i docker, how many are running/paused/stopped, the amount of images w/i docker, docker version, drivers and plugins, and computer hardware/software information, to name a few things of the output.

# Hello-World Questions

Did Docker create a container?
 - Yes

Did the container remain running after printing its message?
 - It did not.

What is the difference between the hello-world image and the container created from it?
 - The image is the template for creating the container, and the container is the localized running executable version of the image. Images are read-only.

Why can a container stop successfully even though it was useful?
 - To stop itself from consuming any more resources than it needs to, that's actually the whole idea behind the containerization. That, and the ability to segment programs. If a process (container) runs successfully and requires no more resources/it has completed its tasks, it comes back with an exit code of 0.

# Docker Inspection
...
"State": {
            "Status": "exited",
            "Running": false,
            "Paused": false,
            "Restarting": false,
            "OOMKilled": false,
            "Dead": false,
            "Pid": 0,
            "ExitCode": 0,
            "Error": "",
            "StartedAt": "2026-11-17T16:15:19.645813711Z",
            "FinishedAt": "2026-11-17T16:15:19.848434752Z"
        },
        "Image": "sha256:1e4c05b897a751332ce85c7e9449da2d93514ea2dea6dbb0e2753c9e949b2bfa"
...
"Cmd": [
                "/hello"
],

# Nginx Docker Questions

What port does Nginx use inside the container?
 - 80

What port did you use on your computer?
 - 8080

What would happen if you used -p 9090:80 instead?
 - http://localhost:9090 would be the address instead, as we are mapping our computer's port 9090 to the container's port 80.

Why does localhost:80 differ from localhost:8080 in this example?
 - localhost:80 is not on our computer, but within the container -- that is the container's port. Our computer's port is the 8080 assignment.

# Arcade Launcher Questions

The command that worked:
 - python main.py

Whether the launcher completed:
 - Yes

The output produced by the plugins:

==================================================
PLUGIN RUNNER
==================================================

Coin Flipper by David Christian
  🎱 Coin Flipper says: Heads!

Card Generator by Eliad Spraggins
  🃏 Card Generator says: Your random card is Q♦

plugins.Matt-Rak by Unknown author
  [skipped] no run() function defined
Suleman Saddet
Magic 8-Ball
69

Magic 8-Ball by Suleman Saddet
  182

Daily Tip Generator by Gemini
  💡 Tip of the Day: Always write descriptive commit messages (e.g., 'Fix header bug' instead of 'fix').

Number Addition by Gaige Szy
  Your total number is: 39.

D20 roller by Mackenzie Klupp
  🎱 D20 roller rolled at: 1

plugins.rockpaperscissors by Unknown author
  [skipped] no run() function defined

Magic 8-Ball by Sravya Sambaturu
  🎱 Magic 8-Ball says: Outlook not so good.

Any warnings or errors:
plugins.rockpaperscissors by Unknown author
  [skipped] no run() function defined

plugins.Matt-Rak by Unknown author
  [skipped] no run() function defined

# Docker Ignore/file

Why is FROM required?
 - it indicates what image to use

What does WORKDIR /app do?
 - uses a dedicated directory within the image for use during the process runtime

Why are main.py and plugins/ copied into the image?
 - so that the container has them ready/available for use

Why should .git and .env be excluded?
 - .git can be very large from time to time and the idea behind containers is short execution times/up to speed times. We don't need commit histories within (most) containers. .env can have secret information, you do not want that baked into the container/image.

What command will Docker run because of CMD?
 - "python main.py"

# Part 6 - Comparing docker run vs python run

Did the same launcher execute?
 - Yes

Which files were available inside the image?
 - All plugins of the launcher/main.py

Did the container need your local Python installation?
 - It did not!

Why does the image provide a more repeatable environment?
 - The containerization is essentially a vm (not actually, but conceptually), in that it can contain all necessary lib installs and runs perfectly without needing installs on the computer. (images hold all packages and their dependencies)

# Step 16 Questions

The error message:
 - python: can't open file '/app/missing.py': [Errno 2] No such file or directory

The process exit status, if available:
 - Unavailable, but I assume 1.

Whether container remains running:
 - It did not (the --rm saw to that)

Why this type of failure should be caught before delivery:
 - If you cannot build and run a container due to a misnamed file or missing file, your "delivery" was not complete and your task will go unfinished.