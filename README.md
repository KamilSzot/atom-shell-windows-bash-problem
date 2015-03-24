# atom-shell-windows-bash-problem
When atom-shell application is ran using atom.exe that's inside this application directory from bash on windows then it can load same modules from node_modules more than once. This is minimal test case that reproduces this behaviour.



# To reproduce the issue:

1. On Windows machine (for example Windows 7) download and install Bash (for example Git Bash that's packaged with windows Git console client).
2. Run bash terminal.
3. Go to main folder of this project.
4. Run `npm install` to install atom-shell in node_modules folder.
5. Run `node_modules/atom-shell/dist/atom.exe .` to start this atom-shell application in downloaded atom shell.
6. You'll notice that text "dep loaded" appears in console twice. It might lead to some serious elusive trouble especially when writing your atom-shell application using react and react-router modules.

# Issue goes away if:

- Applicaiton is run from PowerShell or cmd.
- atom.exe is moved outside of the application folder before using it to run the application.
- Applicaiton is run on Linux or Mac
- In file index.html, the file app.js is loaded using `<script>require('./app')</script>` instead of `<script src="app.js"></script>`
