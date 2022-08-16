# VS Code

## Reason

Code is fast, extendable, open source and works with multitude of programming languages

## How To

### Download

Go to [link](https://code.visualstudio.com/download) and download the `.deb` file
```
https://code.visualstudio.com/download
```

### Install 

Execute:

```bash
sudo apt install ./code.deb
```

The file is not called `code.deb` put something similar

### Configure

Go to `File -> Preferences -> Settings -> Open Settings(JSON)` and replace what you see for this:

```json
{
    "cSpell.language": "en,es",
    "diffEditor.ignoreTrimWhitespace": true,
    "editor.bracketPairColorization.enabled": true,
    "editor.codeActionsOnSave": {
        "source.fixAll.eslint": true
    },
    "editor.fontLigatures": true,
    "editor.guides.bracketPairs": true,
    "editor.inlineSuggest.enabled": true,
    "extensions.ignoreRecommendations": true,
    "javascript.updateImportsOnFileMove.enabled": "always",
    "jestrunner.codeLensSelector": "**/*.{test,spec,serial-test}.{js,jsx,ts,tsx}",
    "search.followSymlinks": false,
    "security.workspace.trust.untrustedFiles": "open",
    "timeline.excludeSources": [
        "timeline.localHistory"
    ],
    "window.zoomLevel": 2,
    "workbench.colorTheme": "Monokai",
    "workbench.startupEditor": "newUntitledFile"
}
```

### Configure Shortcuts

Go to `File -> Preferences -> Keyboard Shortcuts -> Open Keyboard Shortcuts(JSON)` and replace what you see for this:

```json
// Place your key bindings in this file to override the defaultsauto[]
[
    {
        "key": "ctrl+[Backslash]",
        "command": "editor.action.commentLine",
        "when": "editorTextFocus && !editorReadonly"
    },
    {
        "key": "ctrl+shift+7",
        "command": "-editor.action.commentLine",
        "when": "editorTextFocus && !editorReadonly"
    },
    {
        "key": "ctrl+d",
        "command": "editor.action.copyLinesUpAction",
        "when": "editorTextFocus && !editorReadonly"
    },
    {
        "key": "ctrl+shift+alt+up",
        "command": "-editor.action.copyLinesUpAction",
        "when": "editorTextFocus && !editorReadonly"
    }
]
```

### Extensions

List of useful extensions

- Color Highlight
- EditorConfig for VS Code
- ESLint
- Go
- Highlight Matching Tag
- Jenkins Pipeline Linter Connector
- Markdown All in One
- SVG Viewer
