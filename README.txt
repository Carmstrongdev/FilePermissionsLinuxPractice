<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">

    <title>Linux File Permissions Management</title>

    <link rel="stylesheet" href="style.css">
</head>

<body>

    <header class="hero">
        <div class="container">
            <p class="eyebrow">LINUX • CYBERSECURITY • FILE PERMISSIONS</p>

            <h1>Linux File Permissions Management</h1>

            <p class="hero-text">
                A hands-on Linux project focused on inspecting and modifying
                file and directory permissions using <code>ls</code> and
                <code>chmod</code>.
            </p>
        </div>
    </header>


    <main class="container">

        <!-- PROJECT OVERVIEW -->

        <section class="section">
            <div class="section-heading">
                <span class="step-number">01</span>
                <div>
                    <p class="section-label">PROJECT OVERVIEW</p>
                    <h2>Managing Linux Permissions</h2>
                </div>
            </div>

            <p>
                The research team needed to update the permissions for
                specific files and directories within the
                <code>projects</code> directory.
            </p>

            <p>
                The existing permissions did not match the required level
                of authorization. I used Linux commands to inspect the
                permissions and make the necessary changes.
            </p>
        </section>


        <!-- STEP 1 -->

        <section class="section">
            <div class="section-heading">
                <span class="step-number">02</span>
                <div>
                    <p class="section-label">STEP 1</p>
                    <h2>Create the Project Directory</h2>
                </div>
            </div>

            <p>
                I created the <code>projects</code> directory and moved
                into it using the following commands:
            </p>

            <div class="code-block">
                <code>
                    mkdir projects<br>
                    cd projects
                </code>
            </div>

            <div class="screenshot">
                <img src="images/step1.png"
                     alt="Creating and entering the projects directory">
                <span>Creating the projects directory</span>
            </div>
        </section>


        <!-- STEP 2 -->

        <section class="section">
            <div class="section-heading">
                <span class="step-number">03</span>
                <div>
                    <p class="section-label">STEP 2</p>
                    <h2>Inspect File and Directory Details</h2>
                </div>
            </div>

            <p>
                I used <code>ls -la</code> to display detailed information
                about the directory contents, including hidden files.
            </p>

            <div class="code-block">
                <code>ls -la</code>
            </div>

            <p>
                The output contained the <code>drafts</code> directory,
                the hidden <code>.project_x.txt</code> file, and the
                remaining project files.
            </p>

            <div class="screenshot">
                <img src="images/permissions.png"
                     alt="Linux ls -la directory listing">
                <span>Initial directory listing</span>
            </div>
        </section>


        <!-- PERMISSIONS -->

        <section class="section">
            <div class="section-heading">
                <span class="step-number">04</span>
                <div>
                    <p class="section-label">UNDERSTANDING PERMISSIONS</p>
                    <h2>Reading Linux Permission Strings</h2>
                </div>
            </div>

            <p>
                The first column returned by <code>ls -la</code> contains
                a 10-character permission string.
            </p>

            <div class="permission-display">
                <span class="file-type">-</span>
                <span class="user">rwx</span>
                <span class="group">rwx</span>
                <span class="other">rwx</span>
            </div>

            <div class="permission-grid">

                <div class="permission-card">
                    <strong>1st Character</strong>
                    <p>
                        Identifies the file type.
                        <code>d</code> = directory,
                        <code>-</code> = regular file.
                    </p>
                </div>

                <div class="permission-card">
                    <strong>Characters 2–4</strong>
                    <p>
                        Permissions for the file owner:
                        read, write, and execute.
                    </p>
                </div>

                <div class="permission-card">
                    <strong>Characters 5–7</strong>
                    <p>
                        Permissions assigned to the file's group.
                    </p>
                </div>

                <div class="permission-card">
                    <strong>Characters 8–10</strong>
                    <p>
                        Permissions assigned to other users.
                    </p>
                </div>

            </div>

            <div class="permission-table">

                <div class="table-row table-header">
                    <div>Permission</div>
                    <div>Meaning</div>
                </div>

                <div class="table-row">
                    <div><code>r</code></div>
                    <div>Read</div>
                </div>

                <div class="table-row">
                    <div><code>w</code></div>
                    <div>Write</div>
                </div>

                <div class="table-row">
                    <div><code>x</code></div>
                    <div>Execute</div>
                </div>

                <div class="table-row">
                    <div><code>-</code></div>
                    <div>Permission not granted</div>
                </div>

            </div>

            <div class="screenshot">
                <img src="images/breakdown.png"
                     alt="Linux file permission breakdown">
                <span>Permission string breakdown</span>
            </div>
        </section>


        <!-- PROJECT K -->

        <section class="section">
            <div class="section-heading">
                <span class="step-number">05</span>
                <div>
                    <p class="section-label">FILE PERMISSIONS</p>
                    <h2>Updating <code>project_k.txt</code></h2>
                </div>
            </div>

            <p>
                The organization determined that
                <strong>other users should not have write access</strong>
                to the project files.
            </p>

            <p>
                I removed write permission from other users with:
            </p>

            <div class="code-block">
                <code>chmod o-w project_k.txt</code>
            </div>

            <div class="command-explanation">
                <span><strong>o</strong> = other users</span>
                <span><strong>-w</strong> = remove write permission</span>
            </div>

            <div class="screenshot">
                <img src="images/project-k.png"
                     alt="Changing project_k.txt permissions">
                <span>Updated project_k.txt permissions</span>
            </div>
        </section>


        <!-- PROJECT X -->

        <section class="section">
            <div class="section-heading">
                <span class="step-number">06</span>
                <div>
                    <p class="section-label">HIDDEN FILE</p>
                    <h2>Updating <code>.project_x.txt</code></h2>
                </div>
            </div>

            <p>
                The team archived <code>.project_x.txt</code> and required
                that no user have write access. The user and group should
                retain read access.
            </p>

            <div class="code-block">
                <code>chmod u-w,g-w,g+r .project_x.txt</code>
            </div>

            <div class="command-list">
                <div>
                    <strong>u-w</strong>
                    <span>Remove write permission from the user</span>
                </div>

                <div>
                    <strong>g-w</strong>
                    <span>Remove write permission from the group</span>
                </div>

                <div>
                    <strong>g+r</strong>
                    <span>Add read permission to the group</span>
                </div>
            </div>

            <div class="screenshot">
                <img src="images/project-x.png"
                     alt="Changing hidden project_x.txt permissions">
                <span>Updated .project_x.txt permissions</span>
            </div>
        </section>


        <!-- DRAFTS -->

        <section class="section">
            <div class="section-heading">
                <span class="step-number">07</span>
                <div>
                    <p class="section-label">DIRECTORY PERMISSIONS</p>
                    <h2>Updating the <code>drafts</code> Directory</h2>
                </div>
            </div>

            <p>
                The organization wanted only <code>researcher2</code>
                to have access to the <code>drafts</code> directory
                and its contents.
            </p>

            <p>
                The group previously had execute permission, so I removed
                it with:
            </p>

            <div class="code-block">
                <code>chmod g-x drafts</code>
            </div>

            <div class="command-explanation">
                <span><strong>g</strong> = group</span>
                <span><strong>-x</strong> = remove execute permission</span>
            </div>

            <div class="screenshot">
                <img src="images/drafts.png"
                     alt="Changing drafts directory permissions">
                <span>Updated drafts directory permissions</span>
            </div>
        </section>


        <!-- SUMMARY -->

        <section class="summary">

            <p class="section-label">FINAL RESULT</p>

            <h2>Permissions Updated Successfully</h2>

            <p>
                I used Linux permission management commands to bring the
                files and directory in <code>projects</code> into
                compliance with the organization's requirements.
            </p>

            <div class="summary-grid">

                <div>
                    <strong>01</strong>
                    <span>Inspected permissions with <code>ls -la</code></span>
                </div>

                <div>
                    <strong>02</strong>
                    <span>Removed unauthorized write access</span>
                </div>

                <div>
                    <strong>03</strong>
                    <span>Updated hidden-file permissions</span>
                </div>

                <div>
                    <strong>04</strong>
                    <span>Restricted directory permissions</span>
                </div>

            </div>

        </section>

    </main>


    <footer>
        <div class="container">
            <p>Linux File Permissions Management</p>
            <p>Linux • chmod • File Permissions • Cybersecurity</p>
        </div>
    </footer>

</body>
</html>
