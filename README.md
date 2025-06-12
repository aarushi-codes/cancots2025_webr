# Your WebR Project Setup Guide

This guide provides instructions for setting up and deploying your WebR project using GitHub Pages.

---

## Prerequisites

> [!important]
> You will need the following software installed on your computer to create your own exercise files.

- **R**: Download from <https://cran.r-project.org/>
- **RStudio**: Download from <https://posit.co/download/rstudio-desktop/>
- **Quarto**: Install from <https://quarto.org/docs/get-started/>
- **TinyTex**:
    - **Windows**: Open Command Prompt (Windows Key + R, type `cmd`, press Enter) and run:
        ```bash
        quarto uninstall tinytex
        quarto install tinytex
        ```
    - **Mac**: Open Terminal (found in Launchpad) and run:
        ```bash
        quarto uninstall tinytex
        quarto install tinytex
        ```

## Forking this Repository and Hosting Your WebR Files

> [!tip]
> This is the quickest way for you to get started with WebR exercises.

The following instructions assume that you will have a GitHub repository to contain your WebR exercises (the .qmd files) and a GitHub repository that will host the WebR exercises as HTML files.

This separates out what students would see (the hosting GitHub) and your work (the repository with the .qmd files).

### Initial Setup

1.  **Create a GitHub Account**: If you don't already have one, create a GitHub account by visiting <https://github.com/> and clicking "Sign up".
2.  **Fork the WebR Repository**:
    - Navigate to the WebR project repository on GitHub.
    - Click the "**Fork**" button in the top right corner of the page. This creates a copy of the repository in your personal GitHub account.  
    You will use this repository to create and modify your WebR Quarto (.qmd) files. You may want to make this repository private if you do not want to share the content with others (e.g., students).
3. **Make Your Repository Private** (optional):
    - If you want to keep your exercises private, go to your repository settings, "Leave Fork Network", refresh the page, and change the "Change Repository Visibility" to private.  
    This is useful if you do not want students to see the exercises before they are ready.
3. Create a lesson in RStudio based on the Quarto (.qmd) templates provided or available at and that you want to share with students.  
This lesson .qmd file should be created in the same directory as the `_extensions` folder that was created when you forked the repository.
4. Render the lesson to HTML. You will create a .html file and a `<your_file_name>_files/` directory.
5. Create a new directory on your computer and copy over:
    - `_extensions/` folder
    - `<your_file_name>_files/`
    - `<your_file_name>.html`
    - `CHANGEMYNAME.md` - change this to `README.md` and ensure that you have edited the contents of this file to match your the filenames that you are using. The `README.md` file is the landing page of your `https://<your_github_username>.github.io/<your_respository_name>`  
    This allows a single link that students can use to access your exercises.
    Your directory structure should look like:
    ```
    <directory name you just created>
    ├── _extensions
    ├── <your_filename>_files
    ├── <your_filename>.html
    └── README.md
    ```
6.  **Create a New GitHub Repository**:
> [!NOTE]
> This will be the repository you will use for the course for the semester.
    - Go to <https://github.com/new> to create a new, empty repository. Give it a meaningful name (e.g., `math200-fall2025`).
    - Do **NOT** initialize it with a `README`, `.gitignore`, or license, as you will push your local files.
7.  **Push Your Project to GitHub**:
    - Open your terminal or Git Bash.
    - Navigate to your project directory.
    - Initialize a Git repository: `git init`
    - Add your files: `git add .`
    - Commit your changes: `git commit -m "Initial WebR project"`
    - Add the remote origin (replace `YOUR_USERNAME` and `YOUR_REPOSITORY_NAME` with your actual GitHub username and repository name):
        ```bash
        git remote add origin [https://github.com/YOUR_USERNAME/YOUR_REPOSITORY_NAME.git](https://github.com/YOUR_USERNAME/YOUR_REPOSITORY_NAME.git)
        ```
    - Push your local project to GitHub: `git push -u origin main` (or `master` if that's your default branch name).
8.  **Enable GitHub Pages**:
    - Go to your forked repository on GitHub.
    - Click on "**Settings**" (usually found near "Insights").
    - In the left-hand menu, click on "**Pages**".
    - Under "Source", ensure "**Deploy from a branch**" is selected.
    - Under "Branch", select `main` (or `master` if your default branch is named `master`) and click "**Save**".

    GitHub Pages will then build and deploy your WebR HTML file. This process may take a few minutes. Once deployed, a link to your live site will appear on the same "Pages" settings page.
    
The `README.md` file in the Pages GitHub repository should contain links to your lesson `.html` files.

```markdown
[The text that will be displayed](https://your_username.github.io/your_file.html)
```

# Limitations

Any work that is done in a WebR document is not retained after the webpage is closed, refreshed, etc.

The webpage can be printed to retain the information.

The packages that are directly supported are listed and searchable at [https://repo.r-wasm.org/](https://repo.r-wasm.org/).  
These can be installed by placing the package names in the YAML of the `.qmd` file and/or can be made available using `install.packages()` as per usual.

A minimal example of making the `tibble` and `ggplot2` packages available once the WebR exercise is loaded by the student would be:

```yaml
format: html
filters:
  - webr
webr:
  packages: ["tibble", "ggplot2"]
```