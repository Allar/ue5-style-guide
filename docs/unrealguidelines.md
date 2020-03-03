# Unreal Engine Marketplace Guidelines

This page covers how Linter implements rule sets based off of the [Unreal Engine Marketplace Guidelines](https://www.unrealengine.com/marketplace-guidelines). Not every guideline is currently supported but it is the goal of Linter to continually improve support for the Unreal Engine Marketplace Guidelines as well as other commonly used style guides.

If you would like to contribute by adding support for additional guidelines, please join the discussion in the [Gamemakin LLC Community Discord](http://discord.gamemak.in).

## 2.3.6 Particle Effects

### 2.3.6.b [Particle emitter names must be accurate and relevant and must not be "Particle Emitter" unless they're the only emitter in a given particle system](https://www.unrealengine.com/en-US/marketplace-guidelines#236b)

Linter's interpretation of this is to simply check to see if a `UParticleSystem` asset has 2 or more emitters, and if it does, check to see if any of the emitters are named "Particle Emitter". If they are, then this rule is being violated.

This is handled by `Blueprint'/Linter/MarketplaceLinter/LintRules/MPLR_Particles_EmitterNames.MPLR_Particles_EmitterNames'`.

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

### 2.7.1.c [Folder and file names must contain only English alphanumeric characters and underscores](https://www.unrealengine.com/en-US/marketplace-guidelines#271c)

Linter's interpretation of this is that all path elements are tested against a Regular Expression `[^a-zA-Z0-9_]` which is only valid if the entire path element does not have any character except the letters "a through z", "A through Z", "0 through 9", and the '_' character.

This is handled by `Blueprint'/Linter/MarketplaceLinter/LintRules/MPLR_Path_AlphaNumeric.MPLR_Path_AlphaNumeric'`.