# resolution-hooks
Run custom scripts when screen resolution changes. 
It uses two scripts: <code>resolution-hooks</code> and <code>resolution-monitor</code>. The first one groups all detected hooks and runs them one per one, while the second one calls xeventbind.

<code>resolution-hooks</code> supports two types of hooks: user-level and system-level. To create user-level hooks, put them in <code>~/.local/share/resolution-hooks.d/</code> and make them executable. System-level hooks should be included as part of certain packages, like Betterlockscreen. Default directory for system-level hooks is <code>/usr/share/resolution-hooks.d/</code>, if you want to modify them, put them at <code>/etc/resolution-hooks.d/</code> as the first path will be overwritten with updates.

## Notes
- All hooks are run using <code>/bin/sh -c</code>.
- At this moment, if the same hook is in both user-level and system-level paths, it will run twice. Please avoid doing this.
- The <code>resolution-hooks.d</code> included in this repository is intended only as a demonstration. Hooks will included as part of other packages, or packaged apart.

## Installation
For XBPS distributions, <code>resolution-hooks</code> is available in <a href="https://sourceforge.net/projects/cereus-linux/files/repos/cereus-extra/">cereus-extra</a> repository. If using Cereus Linux LXQt, it is already included in the live image. To install it manually, run:

    # xbps-install -S resolution-hooks

For other distributions, you will need to build <a href=https://github.com/ritave/xeventbind>xeventbind</a> and add it to your PATH. Next, you must place your hooks in the correspondant directories. Finally, you should add <code>resolution-monitor</code> to your autostart. There is a desktop file in this repository which helps you on that.

## TO-DO
[ ] Allow enable/disable hooks without removing them.
