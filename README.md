[README (31).md](https://github.com/user-attachments/files/34594212/README.31.md)

# pfa-week03

After last week's class, I was impressed by how brilliant everyone's assignments were and how they incorporated their own unique ideas; inspired by this, I decided to refine my own project. I used Python to generate a castle featuring a movable soldier, and I also implemented functions to undo actions and delete elements.You can click on my YouTube video to watch the content I have remade and optimized.

# 【Watch Demo Video】{https://youtu.be/-gl1XuDx6Cw}

# How to run it

Tested in Autodesk Maya with the Script Editor's Python tab. No extra plugins needed.

1. Open Maya and start a new scene (File > New Scene).
2. Open the Script Editor: Windows > General Editors > Script Editor.
3. Click the **Python** tab (not MEL).
4. Open the file **My tool** in this repo, copy all of it, and paste it into the Python tab.
5. Select all the text (Ctrl+A) and press **Ctrl+Enter** to run it. The castle and the soldier appear, and the timeline is set to frames 1–720.
6. Press **Play**. The soldier walks one lap around the top of the walls every 720 frames (30 seconds at 24 fps) and keeps looping.
7. To undo the whole build, press **Ctrl+Z once**.
8. To delete only what the tool made, type `delete_castle_patrol()` in the Python tab and press Ctrl+Enter. To build it again, type `build_castle_patrol()` and press Ctrl+Enter.

Running the script again replaces the old castle instead of making a second one.

# The loop paragraph

The paragraph explaining the battlement loop (`while t <= 9.0 ...` in `build_castle()`) is at the end of **A detailed explanation of exactly what these ten lines of code do**.

# The ten lines of code I selected
1. TAG = "castlePatrolTool"
2. return cmds.ls(selection=True, uuid=True)[0] (in new_node())
3. return cmds.ls(uid, long=True)[0] (in N())
4. cmds.addAttr(node, longName=TAG, attributeType="bool", defaultValue=True, hidden=True) (in tag())
5. return cmds.ls("*." + TAG, objectsOnly=True, recursive=True, long=True) or [] (in find_owned())
6. cmds.polyCube(name=name, w=w, h=h, d=d) (in box())
7. cmds.xform(N(grp), worldSpace=True, pivots=pivot) (in limb())
8. cmds.setInfinity(node, attribute="rotateX", preInfinite="cycle", postInfinite="cycle") (in animate_walk())
9. cmds.undoInfo(openChunk=True, chunkName="Build Castle Patrol")
10. cmds.undoInfo(closeChunk=True) (inside finally:)
