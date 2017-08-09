# UE4 Marketplace TRC + Style Guide and Linter Compatibility

Epic's Marketplace TRC can be found here: https://forums.unrealengine.com/showthread.php?151905-Marketplace-Technical-Review-Checklist

This document shows its compatibility with the style guide on this repo, as well as the UE4 Marketplace Plugin Linter.

## Icon Guide:

* :white_check_mark: - Compatible
* :green_heart: - Linter Supported (Can currently be checked through automation)
* :x: - Not Compatible
* :o: - See note

## General

| Line  | Review Check Item                                                          | Compatibility Notes                                                             |
| :---: | :------------------------------------------------------------------------- | :------------------------------------------------------------------------------ |
| 4     | Submission is in Unreal Engine 4                                           | :white_check_mark::green_heart: If you can run Linter, you pass.                             |
| 5     | Project contains correct files and folders                                 | :white_check_mark: If you can run Linter, and distribute correctly, you pass.   |
| 6     | Submission contains enough primary assets                                  | :o: You should generally always pass this. Could automate if this were more specific. |
| 7     | Folder hierarchy is structured correctly                                   | :x: This style guide actively fights against the folder structure desired. [See #2](http://ue4.style#2) |
| 8     | First tier folders are named for asset type                                | :x: This style guide actively fights against the folder structure desired. [See #2](http://ue4.style#2) |
| 9     | All files in perspective folders                                           | :white_check_mark::green_heart: Although structure is incompatible, files are checked for structure. [See #2](http://ue4.style#2) |
| 10    | Project is free of unused folders and assets                               | :white_check_mark::o: [See #2.2](http://ue4.style#2.2), [See #2.3](http://ue4.style#2.9), [See #2.9](http://ue4.style#2.9), and remove unused Epic starter / example content |
| 11    | Naming conventions present, consistent, and acceptable                     | :white_check_mark::green_heart: [See #1](http://ue4.style#1)                    |
| 12    | Assets names are in English and Alpha-Numeric                              | :white_check_mark::green_heart: [See #2.1.3](http://ue4.style#2.1.3)            |
| 13    | Assets names identify asset types                                          | :white_check_mark::green_heart: [See #1](http://ue4.style#1)                    |
| 14    | Assets names are consistent                                                | :white_check_mark::green_heart: [See #1](http://ue4.style#1)                    |

## Maps

| Line  | Review Check Item                                                          | Compatibility Notes                                                             |
| :---: | :------------------------------------------------------------------------- | :------------------------------------------------------------------------------ |
| 16    | Pack contains Maps                                                         | :white_check_mark::green_heart: Linter will check for map issues if maps exist. |
| 17    | Pack contains Overview Map                                                 | :white_check_mark: [See #6.4.1](http://ue4.style#6.4.1)                         |
| 18    | Overview Map is set up appropriately and named correctly                   | :white_check_mark: [See #6.4.1](http://ue4.style#6.4.1)                         |
| 19    | Lighting has been built on all maps                                        | :white_check_mark: [See #6.2](http://ue4.style#6.2)                             |
| 20    | All maps are free of errors and/or warnings                                | :white_check_mark::green_heart: [See #6.1](http://ue4.style#6.1)                |
| 21    | No Z fighting or overlapping polygons in maps                              | :white_check_mark: [See #6.3](http://ue4.style#6.3)                             |
| 22    | Pack contains Demo Map                                                     | :white_check_mark: [See #6.4.2](http://ue4.style#6.4.2)                         |
| 23    | Demo Map is set up appropriately and named correctly                       | :white_check_mark: [See #6.4.2](http://ue4.style#6.4.2)                         |
| 24    | Displays functionality effectively                                         | :white_check_mark: [See #6.4.2](http://ue4.style#6.4.2)                         |
| 25    | In editor tutorial/documentation included                                  | :white_check_mark: [See #6.4.2](http://ue4.style#6.4.2)                         |

## Quality

| Line  | Review Check Item                                                          | Compatibility Notes                                                             |
| :---: | :------------------------------------------------------------------------- | :------------------------------------------------------------------------------ |
| 27    | Assets are free of visibly obvious discrepancies                           | :o: Currently a subjective check.                                               |
| 28    | Assets function without detriment to performance                           | :o: Currently a subjective check.                                               |
| 29    | All assets are complete and function as intended                           | :o: Currently a subjective check.                                               |
| 30    | Assets are not easily reproduced                                           | :o: Currently a subjective check.                                               |
| 31    | Pack contains overall good design and concepts                             | :o: Currently a subjective check.                                               |

## Legal

Gamemakin LLC and its product Linter makes no effort to check for legal compliance for your project on your behalf. We are not lawyers and do not have that capability and can not offer legal advice. That said, we vehemently recommend [not breaking the law](http://ue4.style#0.5).

| Line  | Review Check Item                                                          | Compatibility Notes                                                             |
| :---: | :------------------------------------------------------------------------- | :------------------------------------------------------------------------------ |
| 33    | Seller owns rights to distribute content                                   | :white_check_mark: See section note. [See #0.5](http://ue4.style#0.5)           |
| 34    | Does not contain copyrighted or trademarked content                        | :white_check_mark: See section note. [See #0.5](http://ue4.style#0.5)           |
| 35    | Pack is free of stolen/pirated content                                     | :white_check_mark: See section note. [See #0.5](http://ue4.style#0.5)           |
| 36    | Epic/Unreal content is used for display/example only                       | :white_check_mark: See section note. [See #0.5](http://ue4.style#0.5)           |
| 37    | Public Domain Content meets guideline requirements                         | :white_check_mark: See section note. [See #0.5](http://ue4.style#0.5)           |
| 38    | Project is self-sustained                                                  | :white_check_mark: See section note. [See #0.5](http://ue4.style#0.5)           |
| 39    | Additional requirements are available on the Marketplace                   | :white_check_mark: See section note. [See #0.5](http://ue4.style#0.5)           |
| 40    | Pack does not contain assets that could be considered offensive            | :white_check_mark: See section note. [See #0.5](http://ue4.style#0.5)           |

## Textures

| Line  | Review Check Item                                                          | Compatibility Notes                                                             |
| :---: | :------------------------------------------------------------------------- | :------------------------------------------------------------------------------ |
| 42    | Pack contains Textures                                                     | :white_check_mark::green_heart:                                                 |
| 43    | Textures are set to Power of 2                                             | :white_check_mark: [See #7.1](http://ue4.style#7.1)                             |
| 44    | All textures are appropriate resolutions for their respective assets       | :white_check_mark: [See #7.2](http://ue4.style#7.2)                             |
| 45    | Maximum texture size is 8192 for general use and/or 2048 for mobile textures in either dimension | :white_check_mark: [See #7.3](http://ue4.style#7.3)       |
| 46    | All textures use the correct texture group based on purpose                | :white_check_mark: [See #7.4](http://ue4.style#7.4)                             |

## Materials

| Line  | Review Check Item                                                          | Compatibility Notes                                                             |
| :---: | :------------------------------------------------------------------------- | :------------------------------------------------------------------------------ |
| 48    | Pack contains Materials                                                    | :white_check_mark::green_heart:                                                 |
| 49    | All Materials are set up correctly and are optimized for intended purpose  | :o: Currently a subjective check.                                               |
| 50    | Material instances used where appropriate                                  | :o: Currently a subjective check.                                               |
| 51    | Mobile material assets use only BaseColor, Roughness, and Normal from textures | :o: Style guide has no mobile-specific distinctions.                        |
| 52    | Specular is not specified unless used                                      | :o: If "Yes" then "Yes", otherwise "No"? Too vague to understand.            |

## Meshes

| Line  | Review Check Item                                                          | Compatibility Notes                                                             |
| :---: | :------------------------------------------------------------------------- | :------------------------------------------------------------------------------ |
| 54    | Pack contains Meshes                                                       | :white_check_mark::green_heart:                                                 |
| 55    | LOD's are set up correctly                                                 | :white_check_mark: [See #4.2](http://ue4.style#4.2)                             |
| 56    | Assets are modular                                                         | :o: 'Recommended Check'. It does not make sense to make this a hard rule, as hero assets are generally not modular. |
| 57    | Modular pieces are adaptable for repurposing                               | :white_check_mark: This is the definition of modular.                           |
| 58    | Assets snap cleanly on 10 cm grid                                          | :white_check_mark: [See #4.3](http://ue4.style#4.3)                             |
| 59    | Has collision                                                              | :white_check_mark: [See #4.4](http://ue4.style#4.4)                             |
| 60    | Collision set up correctly                                                 | :white_check_mark: [See #4.4](http://ue4.style#4.4)                             |
| 61    | PhysicsAssets correctly set up                                             | :o::white_check_mark: Style Guide currently does not have rules for Skeletal Meshes. This will be enforced however. |
| 62    | If less than 5 assets, all assets are rigged and animated                  | :o: Marketplace specific rule purely about quantity, guide does not apply.      |
| 63    | No overlapping Lightmap UVs                                                | :white_check_mark::green_heart: [See #4.4](http://ue4.style#4.4)                |
| 64    | Assets scaled correctly                                                    | :white_check_mark: [See #4.5](http://ue4.style#4.5)                             |

## Blueprints

| Line  | Review Check Item                                                          | Compatibility Notes                                                             |
| :---: | :------------------------------------------------------------------------- | :------------------------------------------------------------------------------ |
| 66    | Pack contains Blueprints                                                   | :white_check_mark::green_heart:                                                 |
| 67    | Blueprints use comments appropriately                                      | :white_check_mark: [See #3.4.4](http://ue4.style#3.4.4)                         |
| 68    | Blueprints are clean and easy to read                                      | :white_check_mark: [See #3.4](http://ue4.style#3.4) and its subsections.        |
| 69    | Casts contain both a pass and fail condition                               | :o: Sometimes a graceful no-logic fail is acceptable. [See #3.4.5](http://ue4.style#3.4.5) |
| 70    | Custom Blueprint nodes contain "Static" prefix                             | :x: If this refers to a node's name, this makes zero sense, and Epic doesn't follow this in any form. If this refers to the fact that a function might be static, this also makes no sense and this rule should be re-written. After several months I have not been able to get clarification from the marketplace team as to what is intended here. |
| 71    | Custom Blueprint nodes from plugins categorized with plugin name as preface | :o: Style guide only applies this to static functions in a plugin. [See #3.3.5](http://ue4.style#3.3.5) |
| 72    | Functions, variables, and events use names that reflect intended purposes  | :white_check_mark: [See #3.3.1](http://ue4.style#3.3.1)                         |
| 73    | No loose Blueprint nodes                                                   | :white_check_mark: [See #3.4.6](http://ue4.style#3.4.6)                         |
| 74    | Blueprint is free of errors and/or warnings                                | :white_check_mark::green_heart: [See #3.1](http://ue4.style#3.1)                |

## Audio

| Line  | Review Check Item                                                          | Compatibility Notes                                                             |
| :---: | :------------------------------------------------------------------------- | :------------------------------------------------------------------------------ |
| 76    | Pack contains Audio                                                        | :white_check_mark::green_heart:                                                 |
| 77    | All wav files have sound cues attached                                     | :o: This reads like a 1:1 relationship between SoundWaves and SoundCues, when its very common to have one SoundCue reference many SoundWaves. Not sure of Marketplace Team's intention. |
| 78    | Audio is clean and not bitcrunched                                         | :o: Currently a subjective check.                                               |
| 79    | Audio sample rate is appropriate (44100 Hz or 22050 Hz for Game Assets)    | :o: Style guide currently does not have rules for audio format.                 |
| 80    | Sound cues and wavs in separate "Cue" and "Wave" folders                   | :x: This style guide actively fights against the folder structure desired. [See #2](http://ue4.style#2) |

## Characters

Gamemakin LLC's Style Guide does not have character specfics as characters are quite diverse. Epic forces characters to adhere to the Epic Skeleton for marketplace assets even when a character should have a different skeleton due to things like having facial animations, having articulation and movements not supported by Epic's skeleton, having wildly different proportions to the point where using even re-targeted Epic animations don't make sense, and other factors.

When a humanoid does warrant being rigged to the Epic skeleton, we agree with every review item in this list. This checklist however is not fully compatible because we don't believe line item 83 should be enforced as strictly as it currently is. 

| Line  | Review Check Item                                                          | Compatibility Notes                                                             |
| :---: | :------------------------------------------------------------------------- | :------------------------------------------------------------------------------ |
| 82    | Pack contains Characters                                                   | :white_check_mark::green_heart:                                                 |
| 83    | Humanoid assets rigged to Epic skeleton                                    | :o: See section note above.                                                     |
| 84    | Bones are not renamed                                                      | :o::white_check_mark: If using Epic skeleton, agree completely. See Section note. |
| 85    | Character is not weighted to any IK joints                                 | :o::white_check_mark: If using Epic skeleton, agree completely. See Section note. |
| 86    | Epic Skeleton IK Joints are in skeleton hierarchy                          | :o::white_check_mark: If using Epic skeleton, agree completely. See Section note. |
| 87    | Joint orientations remain intact                                           | :o::white_check_mark: If using Epic skeleton, agree completely. See Section note. |
| 88    | Skeleton is not scaled                                                     | :o::white_check_mark: If using Epic skeleton, agree completely. See Section note. |

## Animation

| Line  | Review Check Item                                                          | Compatibility Notes                                                             |
| :---: | :------------------------------------------------------------------------- | :------------------------------------------------------------------------------ |
| 90    | Pack contains Animations                                                   | :white_check_mark::green_heart:                                                 |
| 91    | All animations imported from individual .FBX files                         | :x: Does not make sense. What about animations baked from physical simulations within UE4? What about single frame poses extracted from animations used for reference and additive posing within UE4? What about .FBX's with multiple takes in standard mo-cap pipelines using Motion Builder? |
| 92    | Animations are clean, consistent, and function as intended                 | :white_check_mark: All assets, regardless of type, should not be broken.        |

## Weapons

| Line  | Review Check Item                                                          | Compatibility Notes                                                             |
| :---: | :------------------------------------------------------------------------- | :------------------------------------------------------------------------------ |
| 94    | Pack contains Weapons                                                      | :white_check_mark::green_heart:                                                             |
| 95    | Weapons are scaled to epic skeleton and appear relatively scaled as intended when imported into a new project | :white_check_mark: [See #4.5](http://ue4.style#4.5) |
| 96    | Weapons with moving parts are rigged and animated                          | :white_check_mark: Definition of a weapon with moving parts. Otherwise it wouldn't have moving parts. |

## Particle Effects

| Line  | Review Check Item                                                          | Compatibility Notes                                                             |
| :---: | :------------------------------------------------------------------------- | :------------------------------------------------------------------------------ |
| 98    | Pack contains Particle Effects                                             | :white_check_mark::green_heart:                                                 |
| 99    | Emitter names are accurate and relevant to their displayed effects         |:white_check_mark::green_heart: [See #5.1](http://ue4.style#5.1)                 |
| 100   | Particle systems meant to be viewed at multiple distances have correct LODs | :o: Currently a subjective check.                                              |
| 101   | Effects optimized for their intended use                                   | :o: Currently a subjective check.                                               |

## Plugins

| Line  | Review Check Item                                                          | Compatibility Notes                                                             |
| :---: | :------------------------------------------------------------------------- | :------------------------------------------------------------------------------ |
| 103   | Pack utilizes Plugins                                                      | :white_check_mark:                                                              |
| 104   | Required plugins in project are available on UE Marketplace                | :o: Marketplace specific rule, style guide does not apply.                      |
| 105   | Unnecessary/Unused plugins are disabled                                    | :o: Blueprint only projects can sometimes be forced to need C++ compiling when disabling unused built-in plugins. Until this is fixed, can not recommend fully disabling every unused plugin. |

## Notes From Reviewer
| Line  | Review Check Item                                                          | Compatibility Notes                                                             |
| :---: | :------------------------------------------------------------------------- | :------------------------------------------------------------------------------ |
| 107   | Changes have previously been requested                                     | :o: Specific to Marketplace Review Process, style guide does not apply.         |
| 108   | Requested Changes Have Been Implemented                                    | :o: Specific to Marketplace Review Process, style guide does not apply.         |
