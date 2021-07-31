# Fix for npm install error on Mac systems

Some Mac users may experience the following error block (or similar):<br><br>

`npm ERR! code ERESOLVE`<br>
`npm ERR! ERESOLVE unable to resolve dependency tree`<br>
`npm ERR!`<br>
`npm ERR! While resolving: savvy-starter@1.0.0`<br>
`npm ERR! Found: stylelint@13.13.1`<br>
`npm ERR! node_modules/stylelint`<br>
`npm ERR!   dev stylelint@"^13.11.0" from the root project`<br>
`npm ERR!`<br>
`npm ERR! Could not resolve dependency:`<br>
`npm ERR! peer stylelint@"^9.1.1 || ^10.0.0 || ^11.0.0" from stylelint-config-prettier@6.0.0`<br>
`npm ERR! node_modules/stylelint-config-prettier`<br>
`npm ERR!   dev stylelint-config-prettier@"^6.0.0" from the root project`<br>
`npm ERR!`<br>
`npm ERR! Fix the upstream dependency conflict, or retry`<br>
`npm ERR! this command with --force, or --legacy-peer-deps`<br>
`npm ERR! to accept an incorrect (and potentially broken) dependency resolution.`<br>
`npm ERR!`<br>
`npm ERR! See /Users/spencerdunlap/.npm/eresolve-report.txt for a full report.`<br>
`npm ERR! A complete log of this run can be found in:`<br>
`npm ERR!     /Users/spencerdunlap/.npm/_logs/2021-07-29T01_00_17_570Z-debug.log`<br><br>

when attempting to run: <br><br>

    npm i

<br><br>

## This error appears to be a result of the user's node version being too recent. (may require further research)<br><br>

Try the following fix:<br><br>

<ol>
  <li> Have the user run the "node -v" command to confirm node version<br><br>
  <li> If node version is more recent than some variation of node v14 (e.g., v16.4.0), have the user rollback manually to v14 with the following steps:</ol>
    <ul>
      <li> Delete package-lock.json from file tree in VS Code
      <li> Run the following code block to remove the current version using homebrew:</ul><br>

    rm '/opt/homebrew/bin/npm'
<br>
    <ul>
      <li> Then run the following to install the v14:
      </ul><br>

    brew install node@14

<br>
    <ul>
      <li> Have them run npm install again. At this point they should be successful and receive the following response (or similar):
      </ul><br>

`> node@15.14.0 preinstall /Users/spencerdunlap/Code/SavvyCoders/practiceSPA/node_modules/node`<br>
`> node installArchSpecificPackage`<br>
`+ node-darwin-x64@15.14.0`<br>
`added 1 package in 4.033s`<br>
`found 0 vulnerabilities`<br>
`npm notice created a lockfile as package-lock.json. You should commit this file.`<br>
`npm WARN savvy-starter@1.0.0 No repository field.`<br>
`added 142 packages from 87 contributors and audited 142 packages in 8.227s`<br>
`12 packages are looking for funding`<br>
`  run 'npm fund' for details`<br>
`found 0 vulnerabilities`<br>

<br>
    <ul>
      <li> It may also be necessary to run the following, then re-attempt the install:
      </ul><br>

    brew link node@14

<br>

### This should resolve the issue and installation should be successful.


