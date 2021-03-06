#============================================================================
#
# Copyright (c) Kitware Inc.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
# http://www.apache.org/licenses/LICENSE-2.0.txt
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#
#============================================================================

#-----------------------------------------------------------------------------
set(MODULE_NAME InteractiveSegmentTubes)

#-----------------------------------------------------------------------------
if(NOT Slicer_SOURCE_DIR)
  find_package(Slicer REQUIRED)
  include(${Slicer_USE_FILE})
endif()

#-----------------------------------------------------------------------------
set(MODULE_PYTHON_SCRIPTS
  InteractiveSegmentTubes.py
  InteractiveSegmentTubesLogic/__init__.py
  InteractiveSegmentTubesLogic/InteractiveSegmentTubesLogic.py
  InteractiveSegmentTubesLogic/SegmentTubesLogic.py
  InteractiveSegmentTubesWidget/__init__.py
  InteractiveSegmentTubesWidget/InteractiveSegmentTubesWidget.py
  )

set(MODULE_PYTHON_RESOURCES
  Resources/Icons/AnnotationPointWithArrow.png
  Resources/Icons/Broken.png
  Resources/Icons/Link.png
  Resources/Icons/InteractiveSegmentTubesIcon.png
  Resources/Icons/README
  Resources/UI/InteractiveSegmentTubes.ui
  Resources/ParameterFiles/Default_Parameters.mtp
  )

#-----------------------------------------------------------------------------
ctkMacroCompilePythonScript(
  TARGET_NAME ${MODULE_NAME}
  SCRIPTS "${MODULE_PYTHON_SCRIPTS}"
  RESOURCES "${MODULE_PYTHON_RESOURCES}"
  DESTINATION_DIR ${CMAKE_BINARY_DIR}/${Slicer_QTSCRIPTEDMODULES_LIB_DIR}
  INSTALL_DIR ${Slicer_INSTALL_QTSCRIPTEDMODULES_LIB_DIR}
  NO_INSTALL_SUBDIR
  )


#-----------------------------------------------------------------------------
if(BUILD_TESTING)
  # this will regiester the unittest subclass in the main script
  # as a ctest (note that it is also usable as a runtime test).
  slicer_add_python_unittest(SCRIPT InteractiveSegmentTubes.py)
endif()

#-----------------------------------------------------------------------------
if(NOT Slicer_SOURCE_DIR)
  include(${Slicer_EXTENSION_CPACK})
endif()
