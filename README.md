# The Qwt Widget Library
Qwt is an extension to the libraries of the Qt Project.  

The Qwt library contains widgets and components which are 
primarily useful for technical and scientifical purposes.
It includes a 2-D plotting widget, different kinds of sliders, 
and much more.

Qwt is officialy hosted at http://qwt.sf.net, the cmake version at https://github.com/Sani7/qwt

# Usage
You can add qwt as a submodule to your git project and using:
```cmake
add_subdirectory(${QWT_FOLDER_LOCATION})
target_link_libraries(executabe PRIVATE qwt)
# OR
target_link_libraries(executabe PUBLIC qwt)
```

# Copyright
Qwt Widget Library 
* Copyright (C) 1997   Josef Wilgen
* Copyright (C) 2002   Uwe Rathmann
* Copyright (C) 2024-2026 Sander Speetjens

Qwt is published under the Qwt License, Version 1.0.
You should have received a copy of this licence in the file
COPYING.

This library is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  

  
