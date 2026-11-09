# pfa-week03 — Castle Patrol

A Python tool for Autodesk Maya. One command builds a small castle with a soldier who walks around the top of the walls in a loop. One Ctrl+Z removes the whole thing, and a second command deletes only what this tool made, never anything else in your scene.

After last week's class, I was impressed by how brilliant everyone's assignments were and how they incorporated their own unique ideas; inspired by this, I decided to refine my own project. I used Python to generate a castle featuring a movable soldier, and I also implemented functions to undo actions and delete elements.

**Demo video:** https://youtu.be/-gl1XuDx6Cw

## What you need

- Autodesk Maya (the tool runs in Maya's Script Editor, Python tab)
- Nothing else: no plugins, no extra files, no installs

## Files in this repo

| File | What it is |
|---|---|
| `My tool` | The whole tool (Python code). This is the only file you need to run it. |
| `A detailed explanation of exactly what these ten lines of code do` | My explanation of ten lines from the tool, plus the loop paragraph |
| `README.md` | This page |

## How to run it

1. Open Maya and start a new scene (File > New Scene).
2. Open the Script Editor: Windows > General Editors > Script Editor.
3. Click the **Python** tab (not MEL).
4. Open the file **My tool** in this repo, copy all of it, and paste it into the Python tab.
5. Select all the text (Ctrl+A) and press **Ctrl+Enter** to run it. The castle and the soldier appear, and the timeline is set to frames 1–720.
6. Press **Play**. The soldier walks one lap around the top of the walls every 720 frames (30 seconds at 24 fps) and keeps looping.
7. To undo the whole build, press **Ctrl+Z once**.
8. To delete only what the tool made, type `delete_castle_patrol()` in the Python tab and press Ctrl+Enter. To build it again, type `build_castle_patrol()` and press Ctrl+Enter.

Running the script again replaces the old castle instead of making a second one.

**If something goes wrong:** if you see a syntax error, check that you pasted into the **Python** tab, not the MEL tab. If nothing moves when you press Play, check that the timeline is at frame 1 and press Play again.

## The line I changed by hand

`STEP_FRAMES = 16`

I don't remember which line I changed by hand in class, so I changed this one by hand again: it sets how many frames one full walking step takes, so changing it from 24 to 16 makes the soldier's legs swing faster.

## Something I undid, and why

I undid a stray attachment link that GitHub added to the top of this README when I dragged the file into the editor, because it wasn't part of the README and made the page confusing (see the commit "Update README to remove outdated link").

## The loop paragraph

The paragraph explaining the battlement loop (`while t <= 9.0 ...` in `build_castle()`) is at the end of **A detailed explanation of exactly what these ten lines of code do**.

## The ten lines of code I selected

1. `TAG = "castlePatrolTool"`
2. `return cmds.ls(selection=True, uuid=True)[0]` (in `new_node()`)
3. `return cmds.ls(uid, long=True)[0]` (in `N()`)
4. `cmds.addAttr(node, longName=TAG, attributeType="bool", defaultValue=True, hidden=True)` (in `tag()`)
5. `return cmds.ls("*." + TAG, objectsOnly=True, recursive=True, long=True) or []` (in `find_owned()`)
6. `cmds.polyCube(name=name, w=w, h=h, d=d)` (in `box()`)
7. `cmds.xform(N(grp), worldSpace=True, pivots=pivot)` (in `limb()`)
8. `cmds.setInfinity(node, attribute="rotateX", preInfinite="cycle", postInfinite="cycle")` (in `animate_walk()`)
9. `cmds.undoInfo(openChunk=True, chunkName="Build Castle Patrol")`
10. `cmds.undoInfo(closeChunk=True)` (inside `finally:`)
