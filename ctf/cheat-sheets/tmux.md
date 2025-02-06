# tmux

Here’s a list of common `tmux` commands and keybindings to help you manage your terminal sessions effectively:

#### Basic Commands

1.  **Start a New Session**:

    ```sh
    tmux
    ```

    Or give it a name:

    ```sh
    tmux new -s session_name
    ```
2. **Detach from a Session**:
   * Press `Ctrl-b` followed by `d`.
3.  **List Sessions**:

    ```sh
    tmux ls
    ```
4.  **Attach to a Session**:

    ```sh
    tmux attach -t session_name
    ```
5.  **Kill a Session**:

    ```sh
    tmux kill-session -t session_name
    ```

#### Window and Pane Management

1. **Create a New Window**:
   * Press `Ctrl-b` followed by `c`.
2. **Switch Between Windows**:
   * Press `Ctrl-b` followed by `n` (next) or `p` (previous).
   * Or press `Ctrl-b` followed by the window number (e.g., `1`, `2`).
3. **Rename a Window**:
   * Press `Ctrl-b` followed by `,` (comma), then type the new name.
4. **Close the Current Window**:
   * Type `exit` in the current window or press `Ctrl-d`.
5. **Split the Window Horizontally**:
   * Press `Ctrl-b` followed by `%`.
6. **Split the Window Vertically**:
   * Press `Ctrl-b` followed by `"` (double quote).
7. **Navigate Between Panes**:
   * Press `Ctrl-b` followed by the arrow keys.
8. **Resize Panes**:
   * Press `Ctrl-b` followed by `:` to enter command mode, then use the resize commands:
     * `resize-pane -L` (left)
     * `resize-pane -R` (right)
     * `resize-pane -U` (up)
     * `resize-pane -D` (down)
9. **Close the Current Pane**:
   * Type `exit` in the current pane or press `Ctrl-d`.

#### Session and Pane Commands

1. **Create a New Pane**:
   * Press `Ctrl-b` followed by `%` (vertical split) or `"` (horizontal split).
2. **Swap Panes**:
   * Press `Ctrl-b` followed by `o` to swap between panes.
3. **Synchronize Panes**:
   * Press `Ctrl-b` followed by `:` and type `setw synchronize-panes on` to type the same command in all panes. Use `setw synchronize-panes off` to turn off synchronization.
4. **Send a Command to All Panes**:
   * Press `Ctrl-b` followed by `:` and type `send-keys 'command' C-m` to send a command to all panes in the current window.

#### Copy and Paste Mode

1. **Enter Copy Mode**:
   * Press `Ctrl-b` followed by `[`.
2. **Navigate in Copy Mode**:
   * Use arrow keys, `Page Up`, and `Page Down`.
3. **Start Selection**:
   * Press `Space` to start selecting text.
4. **Copy Selection**:
   * Press `Enter` to copy the selected text to the clipboard.
5. **Paste Text**:
   * Press `Ctrl-b` followed by `]`.

#### Configuration

*   **Edit the `.tmux.conf` File**: Create or edit `~/.tmux.conf` to customize keybindings and settings. After editing, reload the configuration with:

    ```sh
    tmux source-file ~/.tmux.conf
    ```
