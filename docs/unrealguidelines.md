# Unreal Engine Marketplace Guidelines

This page covers how Linter implements rule sets based off of the [Unreal Engine Marketplace Guidelines](https://www.unrealengine.com/marketplace-guidelines). Not every guideline is currently supported but it is the goal of Linter to continually improve support for the Unreal Engine Marketplace Guidelines as well as other commonly used style guides.

If you would like to contribute by adding support for additional guidelines, please join the discussion in the [Gamemakin LLC Community Discord](http://discord.gamemak.in).

## Disclaimer

You are not guaranteed to have your product submission accepted by the Unreal Engine Marketplace simply because you might pass all these rules, however failing these rules will make your submission incredibly more likely to be rejected.

## 2.3.6 Particle Effects

### 2.3.6.b [Particle emitter names must be accurate and relevant and must not be "Particle Emitter" unless they're the only emitter in a given particle system](https://www.unrealengine.com/en-US/marketplace-guidelines#236b)

Linter's interpretation of this is to simply check to see if a `UParticleSystem` asset has 2 or more emitters, and if it does, check to see if any of the emitters are named "Particle Emitter". If they are, then this rule is being violated.

This is handled by `Blueprint'/Linter/MarketplaceLinter/LintRules/MPLR_Particles_EmitterNames.MPLR_Particles_EmitterNames'`.

## 2.3.7 Textures

### 2.3.7.a [Both dimensions of each texture should have a size that is a power of 2 where applicable (e.g. 1024x512 or 1024x4096)](https://www.unrealengine.com/en-US/marketplace-guidelines#237a)

Linter's interpretation is to do a simple "power of two" math test on both the width and the height of all textures. If a texture fails this power of two math test, it then is checked to see if it's `LODGROUP` is exempt from this rule. For the Unreal Engine Marketplace Guidelines, this rule set is configured to only allow textures of the `UI` `LODGROUP` to not have power of two sizes.

This is handled by `Blueprint'/Linter/MarketplaceLinter/LintRules/MPLR_Texture2D_PowerOfTwo.MPLR_Texture2D_PowerOfTwo'`.

### 2.3.7.b [Textures must have a maximum size in either dimension of 8192](https://www.unrealengine.com/en-US/marketplace-guidelines#237b)

Linter's interpretation of this is to make sure a texture's width or height isn't bigger than 8192. That simple.

This is handled by `Blueprint'/Linter/MarketplaceLinter/LintRules/MPLR_Texture2D_Size_NotTooBig.MPLR_Texture2D_Size_NotTooBig'`.

## 2.4 Audio

### 2.4.c [Audio files must have a sample rate of 22050 Hz or 44100 Hz with no audio defects](https://www.unrealengine.com/en-US/marketplace-guidelines#24c)

Linter's interpretation of this is pretty straight forward. `USoundWave` assets must have sample rates of either 22050 or 44100.

This is handled by `Blueprint'/Linter/MarketplaceLinter/LintRules/MPLR_SoundWave_SampleRate.MPLR_SoundWave_SampleRate'`.

## 2.5 Blueprints

### 2.5.d [Blueprints must have no loose nodes unless they’re commented for example/tutorial purposes](https://www.unrealengine.com/en-US/marketplace-guidelines#25d)

Linter's interpretation of this is that a `UBlueprint` that has any node on any of its graphs that has zero connections to any other node.

This is handled by `Blueprint'/Linter/MarketplaceLinter/LintRules/MPLR_Blueprint_LooseNodes.MPLR_Blueprint_LooseNodes'`.

### 2.5.e [Blueprints must generate no errors or consequential warnings](https://www.unrealengine.com/en-US/marketplace-guidelines#25e)

Linter's interpretation of this is that a `UBlueprint` must not have a compile status of `BS_Error` or `BS_UpToDateWithWarnings`. 

That is, the compile button for this Blueprint should not have any error or warning icon on it.

This is handled by `Blueprint'/Linter/MarketplaceLinter/LintRules/MPLR_Blueprint_Compiles.MPLR_Blueprint_Compiles'`.

## 2.7 File Structure

### 2.7.1.a [Folder and files must be accurate and consistent in naming convention within the context of their project](https://www.unrealengine.com/en-US/marketplace-guidelines#271a)

Linter's interpretation of this is that all assets should match a pattern defined in the rule set's `NamingConvention` asset.

The Marketplace `NamingConvention` asset is `MarketplaceNamingConvention'/Linter/MarketplaceLinter/MarketplaceNamingConvention.MarketplaceNamingConvention'` and the rule that checks for this is `Blueprint'/Linter/MarketplaceLinter/LintRules/MPLR_IsNamedCorrectly.MPLR_IsNamedCorrectly'`.

### 2.7.1.b [Folders and files must not be vaguely-named such as \"Assets\", \"NewFolder\", etc.](https://www.unrealengine.com/en-US/marketplace-guidelines#271b)

Linter's interpretation of this is that all path elements must never be "Assets" or "NewFolder". 

This is handled by `Blueprint'/Linter/MarketplaceLinter/LintRules/MPLR_Path_DisallowedPathNames.MPLR_Path_DisallowedPathNames'`.

### 2.7.1.c [Folder and file names must contain only English alphanumeric characters and underscores](https://www.unrealengine.com/en-US/marketplace-guidelines#271c)

Linter's interpretation of this is that all path elements are tested against a Regular Expression `[^a-zA-Z0-9_]` which is only valid if the entire path element does not have any character except the letters "a through z", "A through Z", "0 through 9", and the '_' character.

This is handled by `Blueprint'/Linter/MarketplaceLinter/LintRules/MPLR_Path_AlphaNumeric.MPLR_Path_AlphaNumeric'`.

### 2.7.2.b [In order to reduce migration conflicts after importing project files from the Epic Games Launcher, all project-specific assets must be stored in one top level folder; there must be no other folders or files directly under the Content folder](https://www.unrealengine.com/en-US/marketplace-guidelines#272b)

Linter's interpretation of this is that the parent folder of any asset should not be the path `/Content/`.

This is handled by `Blueprint'/Linter/MarketplaceLinter/LintRules/MPLR_Path_NoTopLevelAssets.MPLR_Path_NoTopLevelAssets'`.

### 2.7.2.d [Including the name of the top level folder under the Content folder, all asset file paths must be 140 characters or less](https://www.unrealengine.com/en-US/marketplace-guidelines#272d)

Linter's interpretation of this is that the path of any asset returned by `UObject::GetPathName()`, with the redundant asset name chopped off, should not be longer than 140 characters.

This is handled by `Blueprint'/Linter/MarketplaceLinter/LintRules/MPLR_Path_IsNotTooLong.MPLR_Path_IsNotTooLong'`. The path name that is used for this asset for example would be `/Linter/MarketplaceLinter/LintRules/MPLR_Path_IsNotTooLong'`.