# gswitch & autocomplete_gswitch

This is a utility to improve your Git branch switching workflow:

- `gswitch`: A shell script that stashes your current changes, switches to another Git branch, and restores stashed changes automatically when you return to the previous branch.
- `_gswitch`: A zsh autocompletion file that enables auto-completion of branch names when using `gswitch`.

---

## 📜 gswitch - Branch Switch with Auto-Stash and Restore

### 🧠 What it does:
- Automatically stashes your current changes with a custom message
- Switches to the specified branch
- If you previously left this target branch with changes, it will restore them automatically when you return

---

## ✅ Why use `gswitch` instead of a built-in `git switch`

| Feature | `git switch` | `gswitch` |
|--------|--------------|-----------|
| Switch branches | ✅ | ✅ |
| Detects and handles uncommitted changes | ❌ (throws error) | ✅ (auto stash) |
| Automatically restores changes when returning | ❌ | ✅ |
| Safe and automated branch swapping | ❌ | ✅ |

With `git switch`, you need to manually stash and unstash. `gswitch` does it for you with zero effort.

---

## 🔧 Installation

### 1. Install the `gswitch` script
1. **Download the file `gswitch`**
2. **Create folder (if needed):**
   ```bash
   mkdir -p ~/bin
   ```
3. **Move the file**:
   ```bash
   mv gswitch ~/bin
   ```
4. **Make `gswitch` executable:**
   ```bash
   chmod +x ~/bin/gswitch
   ```
5. Add `~/bin` to your `$PATH` (if it's missing):
   - Open your shell config file:
      ```bash
      nano ~/.zshrc
      ```
   - Add this line:
      ```bash
      export PATH="$HOME/bin:$PATH"
      ```
   - Save and reload:
      ```bash
      source ~/.zshrc
      ```

---

### 2. Install the autocomplete script for gswitch (`_gswitch`):
1. **Download** the file `_gswitch`
2. **Create folder (if needed)**:
   ```bash
   mkdir -p ~/.zsh/completions
   ```
3. **Move the file**:
   ```bash
   mv _gswitch ~/.zsh/completions/
   ```
4. **Edit `~/.zshrc` and add:**
   - Open your shell config file:
      ```bash
      nano ~/.zshrc
      ```
   - Add this line:
      ```zsh
      fpath=(~/.zsh/completions $fpath)
      autoload -Uz compinit && compinit
      ```
   - Save and reload:
      ```bash
      source ~/.zshrc
      ```

---

## 🚀 Usage

```bash
gswitch <branch-name>
```

### Example:

```bash
gswitch feature/awesome-upgrade
```

This will:
1. Stash your current changes with a message like `gswitch:<current-branch>`
2. Switch to `feature/awesome-upgrade`
3. Apply stash for that branch if one exists

---

## 📄 License

MIT License – feel free to use and modify.
