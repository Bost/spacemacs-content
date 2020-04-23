# Org Journal
An effective way to keep a daily record of discovery from work, personal study, hobbies or even a mood diary to help with mental wellness.

`SPC a o j j` opens a new journal entry for the current day in a new buffer.

`o` creates a new line automatically indented, or a new list item, `-` or check box list, `- [ ]`, if the previous line was that type.

`C-RET` creates a new heading at the same level.  `M-right-arrow` demotes the current heading (smaller heading) and `M-left-arrow` promotes the current heading. `M-up/down-arrow` moved heading up or down the list of headings.

`,` displays the org-mode major mode commands. `g` menu contains org related commands

`, i l` to add a link, prompting first for the URL (`C-y` to paste) followed by the text of the link and an optional tool tip.

`, p` and `, n` will show the previous and next days journal entries, providing a quick way to scroll through the diary.

`SPC f s` to save the journal entry.

![Spacemacs org journal - example journal entry](/images/spacemacs-org-journal-example-day-entry.png)

> #### Hint::Create a check box list
> `-` is a list and `- [ ]` adds a checkbox to the list.  `, T c` will toggle the mark in the checkbox, ticked or empty, for the current line.


## Tracking progress
Headings can be assigned [TODO states](/org-mode/todo-states.md) to demonstrate progress and use the journal to manage tasks for the day.

`, L` or `S-🡆` (`org-shiftright`) cycles through the states, which are `TODO` `DOING` and `DONE` by default.  `, H` or `S-🡄` to cycle the states in reverse.

If Headings are not in a DONE state are automatically carried over when creating the next days journal.


## Configure org-journal
[practicalli/spacemacs.d](https://github.com/practicalli/spacemacs.d/) includes this configuration

To manually add org-journal, edit `.spacemacs` and add these org layer variable with suggested settings from [Spacemacs org layer documentation](https://develop.spacemacs.org/layers/+emacs/org/README.html#org-journal-support)

```elisp
org-enable-org-journal-support t
org-journal-dir "~/projects/journal/"
org-journal-file-format "%Y-%m-%d"
org-journal-date-prefix "#+TITLE: "
org-journal-date-format "%A, %B %d %Y"
org-journal-time-prefix "* "
org-journal-time-format ""
```
