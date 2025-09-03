# Lab 01 - Get basic skills

Welcome to the first lab of the semester! This lab marks the beginning of an exciting journey where you will progressively build and improve the foundation of your final project. Each lab is part of a larger chain, designed to guide you through key concepts and techniques. Over the weeks, you’ll iterate on your initial work, refining and expanding it into a fully realized project.

Here’s what you need to know:

1. **Iterative Development**: The labs are interconnected, and each step builds upon the previous one. Treat each lab as a building block for your final project.
1. **Constructive Feedback**: You’ll receive feedback on your labs to help you improve. While labs themselves won’t directly affect your final grade, the improvements you make based on this feedback will prepare you for success.
1. **Final Evaluation**: Your final grade will consider both the quality of your completed project and the clarity and consistency of your commit history. Maintaining a well-documented and thoughtful development process is just as important as the final outcome.

Dive in, experiment, and make the most of this hands-on learning experience!

## Course repository subscription

Navigate to the course repository on GitHub and subscribe to it by selecting `Watch > All Activity`. This will ensure you receive notifications about new content, assignments, and updates.

## Exercises

### Practice basic shell commands

Terminal commands are the most efficient way to interact with your computer. Here are some essential commands:

- `pwd`: Print working directory.
- `ls`: List files and directories.
- `cd`: Change directory.
- `mkdir`: Make directory.
- `touch`: Create a file.
- `rm`: Remove a file or directory.
- `mv`: Move or rename a file or directory.
- `cp`: Copy a file or directory.
- `cat`: Concatenate and display file content.
- `man`: Display the manual page of a command.
- `grep`: Search for patterns in files.
- `find`: Search for files in a directory hierarchy.
- `sudo`: Execute a command as the superuser.

Open a terminal window to achieve the following tasks:

1. Print the current working directory.
1. List the files and directories in the current directory.
1. Create a new directory called `practice`.
1. Change into the `practice` directory.
1. Confirm your location again by printing the current working directory.
1. Create an empty file called `notes.txt`.
1. List the files in the directory to confirm the file was created.
1. Add some content to `notes.txt`.
1. Display the content of `notes.txt`.
1. Copy `notes.txt` to a new file called `notes_backup.txt`.
1. Rename `notes_backup.txt` to `notes_old.txt`.
1. Create a subdirectory called `archive`.
1. Move `notes_old.txt` into the `archive` directory.
1. List the files inside the `archive` directory, without changing into it.
1. Create 2 more files in the `practice` directory:
    - `ring.txt`, containing "One ring to rule them all"
    - `clue.txt`, containing "The butler did it"
1. Consult the manual page for the `grep` command.
1. Search for the word "butler" in all `.txt` files.
1. Remove the `archive` directory and all its contents.
1. Remove all `.txt` files in the `practice` directory.
1. Change back to the parent directory.
1. Remove the `practice` directory.
1. Consult the manual page for the `sudo` command.

### Resolving a domain name to an IP address

Resolve the domain name `example.com` to an IP address using:

- The `dig` command.
- The `nslookup` command.

You can consult the manual pages for each command to learn more about their usage.

### Tracing a web page load in developer tools

1. Open a New Browser Window
    - Open Firefox (or another modern browser like Edge or Google Chrome).
    - (Optional) Use an Incognito/Private window to reduce the effect of cached files.
1. Open Developer Tools
    - Right-click anywhere on the page and select _Inspect Element_ (or press F12).
    - Switch to the Network tab in the Developer Tools panel.
1. Clear & Prepare the Network Tab
    - Ensure the Network tab is recording. If not, click the round record button (typically a red dot).
    - Check "Disable cache" to see a full request flow (this ensures the browser won’t load resources from cache).
1. Enter a URL & Watch the Requests
    - In the address bar, type <https://example.com> (or any site you choose) and press Enter.
    - Observe how multiple rows (requests) appear in the Network tab:
      - The main HTML file (e.g., example.com/).
      - CSS files.
      - JavaScript files.
      - Images or other media.
1. Inspect Each Request in Detail
    - Status Code & Headers:
      - Click on the main HTML request.
      - Look under the Headers sub-tab to view the Request Headers (e.g., `GET / HTTP/1.1`) and Response Headers (e.g., `HTTP/1.1 200 OK`).
    - Timing:
      - Look at the Timing (or Waterfall) view to see how long DNS, TCP, SSL handshake, and content download took.
      - Notice how some stages, like DNS lookup or Initial connection, appear as separate phases in the waterfall chart.
    - Content:
      - Check the Preview (or Response) sub-tab to see the actual content (HTML, JSON, etc.) returned from the server.
1. Observe the Page Rendering Sequence
    - As the HTML file loads, the browser sees references to CSS and JavaScript. These appear in the Network tab as subsequent requests.
    - Note any rendering-blocking resources (e.g., large CSS files or scripts).
    - Watch the Timeline or Waterfall to see which assets load first and how they influence the overall page load time.
1. Confirm HTTPS & Security
    - Look at the Security tab (Chrome/Firefox) in Developer Tools (or click the padlock icon next to the address bar).
    - Observe if a TLS/SSL handshake was performed and if the site’s certificate is valid.

### Basic Git usage

Git is the most popular version control system. Here are some essential commands:

- `init`: Initialize a new Git repository.
- `clone`: Clone a repository into a new directory.
- `add`: Add file contents to the index (or staging area).
- `commit`: Record changes to the repository.
- `push`: Update remote refs along with associated objects.
- `merge`: Join two or more development histories together.
- `rebase`: Reapply commits on top of another base tip.
- `fetch`: Download objects and refs from another repository.
- `status`: Show the working tree status.
- `log`: Show commit logs.
- `switch`: Switch branches.

First, ensure you have Git installed on your system. You can check by running `git --version` in your terminal.

1. Create and initialize a local repository.
    1. Create a new directory called `git-practice`.
    1. Change into the `git-practice` directory.
    1. Initialize a new Git repository.
    1. Check the status of the repository.
1. Add and commit your first file
    1. Create a new file called `README.md` with some content.
    1. Check the status of the repository.
    1. Add the `README.md` file to the staging area.
    1. Check the status of the repository.
    1. Commit the changes with a meaningful message.
    1. Check the status of the repository.
    1. Verify the commit history.
1. Make Changes & Commit Again
    1. Edit the `README.md` file to modify existing content.
    1. Check the status of the repository.
    1. Add the changes to the staging area.
    1. Commit the changes with a meaningful message.
    1. Verify the commit history.
1. Create a new branch and merge changes
    1. Create a new branch called `feature`.
    1. Switch to the `feature` branch.
    1. Edit the `README.md` file again to add a new line.
    1. Commit the changes on the `feature` branch.
    1. Verify the commit history on the `feature` branch.
1. Introduce a merge conflict
    1. Switch back to the `main` branch.
    1. Add a different line to the `README.md` file on the `main` branch (same line but different content than the `feature` branch).
    1. Commit the changes on the `main` branch.
    1. Attempt to merge the `feature` branch into the `main` branch.
    1. Resolve the merge conflict.
        1. Open the `README.md` file.
        1. Locate the conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`).
        1. Edit the file to resolve the conflict.
    1. Add the resolved file to the staging area.
    1. Commit the merge.
    1. Verify the commit history.
    1. Inspect the `README.md` file to ensure the conflict is resolved.
    1. Delete the `feature` branch.

Try to practice the `rebase` command on your own. Note the differences between `merge` and `rebase`.

When you are done practicing, clean up and delete the `git-practice` directory.

## Project

### Team up and create a private repository

Form a team of 3 students.

Create a private repository on GitHub and add your team members as collaborators. The repository should be named `webtech-<team-name>`. The team name should be a unique identifier for your group.

Each member of the team should clone the repository to their local machine.

Invite your instructor as a collaborator to the repository. Your group and repository must appear on the instructor's spreadsheet by the end of the class.

Note: The repository will be used from now until the final project. Make sure to keep it private and only share it with your team members and the instructor.

### Project brainstorming

Discuss with your team members and decide on a project idea. Project innpmstructions are provided in the course repository.

### Project README.md

Add a `README.md` file to your repository with at least the following information:

- Team members' names and email addresses.
- A brief description of the project you will be working on.

Keep the `README.md` file updated with the project's progress and any other relevant information (usage instructions, deployment steps, etc.).

Note: Don't forget to follow the conventional commit convention for your commits messages. This will be taken into account when grading your final project.

### Project self-assessment

Import the given self-assessment file into your repository. Name it `PROJECT.md`.

### Environment setup

Set up your development environment. Make sure you have the necessary tools and dependencies installed to start working on your project:

- UNIX-like operating system (Linux, macOS)
- Git
- At least one modern web browser (Firefox, Chrome, Edge)
- A code editor (VS Code, Zed, etc.)

More informations are available on the PREREQUISITES.md file. Node.js and NPM will be installed in the next lab.
