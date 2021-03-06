jucer_export_target_configuration
=================================

Define the settings specific to a configuration associated with an export target.

::

  jucer_export_target_configuration(
    <exporter>

    NAME <configuration_name>
    DEBUG_MODE <ON|OFF>

    [BINARY_NAME <binary_name>]
    [BINARY_LOCATION <binary_location>]
    [HEADER_SEARCH_PATHS <search_path> [<search_path> ...]]
    [EXTRA_LIBRARY_SEARCH_PATHS <search_path> [<search_path> ...]]
    [PREPROCESSOR_DEFINITIONS <preprocessor_definition> [<preprocessor_definition> ...]]

    [LINK_TIME_OPTIMISATION <ON|OFF>]
    [OPTIMISATION <optimisation>]

    [ENABLE_PLUGIN_COPY_STEP <ON|OFF>]  # [1]
    [VST_BINARY_LOCATION <binary_location>]  # [1]
    [VST3_BINARY_LOCATION <binary_location>]  # [1]
    [AU_BINARY_LOCATION <binary_location>]  # [2]
    [RTAS_BINARY_LOCATION <binary_location>]  # [1]
    [AAX_BINARY_LOCATION <binary_location>]  # [1]
    [UNITY_BINARY_LOCATION <binary_location>]  # [1]
    [VST_LEGACY_BINARY_LOCATION <binary_location>]  # [1]

    [OSX_BASE_SDK_VERSION <osx_sdk>]  # [2]
    [OSX_DEPLOYMENT_TARGET <osx_deployment_target>]  # [2]
    [OSX_ARCHITECTURE <osx_architecture>]  # [2]
    [CUSTOM_XCODE_FLAGS <xcode_flag> [<xcode_flag> ...]]  # [2]
    [CXX_LANGUAGE_STANDARD <cxx_standard>]  # [2]
    [CXX_LIBRARY <cxx_library>]  # [2]
    [CODE_SIGNING_IDENTITY <code_signing_identity>]  # [2]
    [STRIP_LOCAL_SYMBOLS <ON|OFF>]  # [2]

    [DEBUG_INFORMATION_FORMAT <debug_information_format>]  # [3]
    [WARNING_LEVEL <warning_level>]  # [3]
    [TREAT_WARNINGS_AS_ERRORS <ON|OFF>]  # [3]
    [RUNTIME_LIBRARY <runtime_library>]  # [3]
    [WHOLE_PROGRAM_OPTIMISATION <whole_program_optimisation>]  # [3]
    [MULTI_PROCESSOR_COMPILATION <ON|OFF>]  # [3]
    [INCREMENTAL_LINKING <ON|OFF>]  # [3]
    [FORCE_GENERATION_OF_DEBUG_SYMBOLS <ON|OFF>]  # [4]
    [PREBUILD_COMMAND <command_content>]  # [3]
    [POSTBUILD_COMMAND <command_content>]  # [3]
    [GENERATE_MANIFEST <ON|OFF>]  # [3]
    [CHARACTER_SET <character_set>]  # [3]

    [RELAX_IEEE_COMPLIANCE <ON|OFF>]  # [1]

    [ARCHITECTURE <architecture>]  # [5]
  )

``<exporter>`` must be one of the :ref:`supported exporters <supported-exporters>`.

Optional keywords support:

- ``[1]``: only supported by the ``"Xcode (MacOSX)"``, ``"Visual Studio 2019"``,
  ``"Visual Studio 2017"``, ``"Visual Studio 2015"``, and ``"Visual Studio 2013"``
  exporters.
- ``[2]``: only supported by the ``"Xcode (MacOSX)"`` exporter.
- ``[3]``: only supported by the ``"Visual Studio 2019"``, ``"Visual Studio 2017"``,
  ``"Visual Studio 2015"``, and ``"Visual Studio 2013"`` exporters.
- ``[4]``: only supported by the ``"Visual Studio 2019"``, ``"Visual Studio 2017"``,
  ``"Visual Studio 2015"``, and ``"Visual Studio 2013"`` exporters, when ``DEBUG_MODE`` is
  ``OFF``.
- ``[5]``: only supported by the ``"Visual Studio 2019"``, ``"Visual Studio 2017"``,
  ``"Visual Studio 2015"``, ``"Visual Studio 2013"``, ``"Linux Makefile"``,
  ``"Code::Blocks (Windows)"``, and ``"Code::Blocks (Linux)"`` exporters.


Examples
--------

From `the NetworkGraphicsDemo extra of JUCE 5.4.3 <https://github.com/McMartin/FRUT/blob/
master/generated/JUCE-5.4.3/extras/NetworkGraphicsDemo/CMakeLists.txt#L176-L182>`_:

.. code-block:: cmake
  :lineno-start: 176

  jucer_export_target_configuration(
    "Xcode (MacOSX)"
    NAME "Debug"
    DEBUG_MODE ON
    BINARY_NAME "JUCE Network Graphics Demo"
    OSX_DEPLOYMENT_TARGET "10.9"
  )


From `the UnitTestRunner extra of JUCE 5.4.3 <https://github.com/McMartin/FRUT/blob/
master/generated/JUCE-5.4.3/extras/UnitTestRunner/CMakeLists.txt#L277-L284>`_:

.. code-block:: cmake
  :lineno-start: 277

  jucer_export_target_configuration(
    "Visual Studio 2017"
    NAME "Release"
    DEBUG_MODE OFF
    BINARY_NAME "UnitTestRunner"
    TREAT_WARNINGS_AS_ERRORS ON
    DEBUG_INFORMATION_FORMAT "None"
  )


From `the Projucer extra of JUCE 5.4.3 <https://github.com/McMartin/FRUT/blob/master/
generated/JUCE-5.4.3/extras/Projucer/CMakeLists.txt#L726-L733>`_:

.. code-block:: cmake
  :lineno-start: 726

  jucer_export_target_configuration(
    "Linux Makefile"
    NAME "Debug"
    DEBUG_MODE ON
    BINARY_NAME "Projucer"
    # HEADER_SEARCH_PATHS
    # EXTRA_LIBRARY_SEARCH_PATHS
  )
