---
layout: post
title: "7zip: Create an archive from a file containing pathnames"
---

    7z a -spf2 -t7z -ir@"files_to_include.txt" blah.7z

| Command | Action |
|---------|--------|
|a |add files|
|   -spf2      |  use full path names (but omit the drive letter (2))      |
| t7z        | type: 7zip  |
| ir@ | include recusively the paths in the subsequent file       |
| blah.7z | the actual file name of the resulting archive       |
