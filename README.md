# pfa-week03

After last week's class, I was impressed by how brilliant everyone's assignments were and how they incorporated their own unique ideas; inspired by this, I decided to refine my own project. I used Python to generate a castle featuring a movable soldier, and I also implemented functions to undo actions and delete elements.You can click on my YouTube video to watch the content I have remade and optimized.

# 【Watch Demo Video】{https://youtu.be/-gl1XuDx6Cw}

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
