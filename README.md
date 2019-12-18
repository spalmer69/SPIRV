# SPIRV
A MSBuild Build Customization which adds support for Google **glslc** compiler producing SPIR-V, the one included with the LunarG Vulkan SDK.

Beats using the Custom Build Tool!

To use, simply copy these files to

    %ProgramFilesx86%\Microsoft Visual Studio\20??\Community\MSBuild\Microsoft\VC\v???\BuildCustomizations\

then restart Visual Studio, and open the **Project** menu, and select **Build Customizations...** and select **spirv**

It's likely they can be used from the project or solution folder as well, after browsing for them.

*FIXME* there's still a few problems:
* the build output doesn't show up at Minimal verbosity
* no auto dependencies!
* somehow now when using this custom build target, the project containing the usage
  now always seems to get built (and then says it's up-to-date, but *succeeded*)
  whereas other projects not using it will simply succeed immediately without running any rules.
  idk what I'm doing wrong.  It's not a huge issue as it doesn't take long, and seems to be necessary to
  actually run these custom rules, but does tend to clutter up the build log on normal verbosity.
* unfortunately, before, with Custom Build, all the dependencies were specified relative to the input file's folder ($RelativeDir)
  but with this, the AdditionalDependencies are treated as relative to the current folder $(ProjectDir)

Much of this is from the MASM target included with VC, with heavy modifications.

This tool is not affiliated with Google or LunarG corporation and all such marks are own by the respective entities.  In fact I'm not really sure who to attribute the glslc compiler tool to, or if I should even mention such an entity in the descriptions; I originally was attributing LunarG with it, but Google in fact wrote and maintains it.  In fact it's right over here:  https://github.com/google/shaderc/tree/master/glslc  I just wrote this build customization to help use it from Visual Studio.

contact author at sean.palmer`at`ymail.com
