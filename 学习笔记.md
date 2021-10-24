# ATOM学习笔记
  * ## 切换便携模式 (Portable Mode)
    In addition to using the *ATOM_HOME* environment variable, Atom can also be set to use "Portable Mode".<br>
    *Portable Mode is most useful for taking Atom with you, with all your custom setting and packages, from machine to machine*<br>
    This may take the form of keeping Atom on a USB drive or a cloud storage platform that syncs folders to different machines, like Dropbox. <br>
    Atom is in Portable Mode when there is a directory named .atom sibling to the directory in which the atom executable file lives. <br>
    For example, the installed Atom directory can be placed into a Dropbox folder next to a .atom folder.<br>
    Atom provides a command-line parameter option for setting Portable Mode.<br>
    *atom --portable*<br>
    Executing atom with the --portable option will take the .atom directory you have in the default location (~/.atom) and copy the relevant contents for your configuration to a new home directory in the Portable Mode location. <br>
    This enables easily moving from the default location to a portable operation without losing the customization you have already set up.
