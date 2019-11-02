## Using git

CLI is installed via brew on MacOS.

```bash
brew install git
```

Best MacOS client as of Nov 2019 is SourceTree by Atlassian. _Note: Atlassian account needed._
Download: https://www.sourcetreeapp.com/

## Common issues

### Changing the case of a filename

Git does not track changes in the casing by default.
Example error:

```
Cannot find file: 'fields.jsx' does not match the corresponding name on disk: 'components/Fields.jsx'.
```

The solution is to change the git configuration globally by running

```bash
git config core.ignorecase false
```

or by manually running this for each file:

```bash
git mv -f OldFileNameCase newfilenamecase
```
