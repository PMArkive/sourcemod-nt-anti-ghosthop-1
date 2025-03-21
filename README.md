# sourcemod-nt-anti-ghosthop
SourceMod plugin for Neotokyo that limits the max movement speed while bunnyhopping with the ghost:

![velocity vector plot](https://github.com/Rainyan/sourcemod-nt-anti-ghosthop/assets/6595066/8ecaf061-85e6-4cd9-b45b-937427fada8f)

where:
* v<sub>0</sub> = initial lateral velocity
* Δv = velocity impulse (inverse of current overspeed)
* v<sub>f</sub> = final lateral velocity, clamped within max ghost carry speed.

## Some background
NT has a max speed limitation for the ghost carrier to make rushy quick capping less effective.
However, players could circumvent this limitation by bhopping and/or using the recon AUX jump (dubbed "*ghost hopping*").

For a long time, there's been a sort of gentlemen's agreement not to abuse ghost hopping,
and anti-ghosthop rules have also made their way into many competitive rulesets.

This plugin suggests a different approach, whereby ghost hopping is restricted programmatically, rather than by ambiguous case-by-case rulings.

## Gameplay changes

* **Attempting to ghost hop becomes fully allowed**
  * The plugin will enforce max ghost hop speed limits, adjusted for competitive gameplay balance. Whatever ghost movement you can get away with, is by definition allowed.

## Motivations

* **Encourage skill based movement**, but strike a balance with not breaking game timings.
* **Make tournament rulings less ambiguous** — the server will automatically decide what is too fast, instead of relying on subjective human admin intervention.

<hr>


## More info for server operators

### Build requirements
* SourceMod version 1.8 or newer
* The [Neotokyo include](https://github.com/softashell/sourcemod-nt-include) .inc file (place inside <i>scripting/includes</i>)

### Plugin requirements
* The [nt_ghostcap plugin](https://github.com/softashell/nt-sourcemod-plugins/blob/master/scripting/nt_ghostcap.sp) is required to use this plugin.

### Other requirements
* The [translations](translations) must be included in the server's `addons/sourcemod/translations` directory.

### Cvars
* sm_nt_anti_ghosthop_version
  * Default value: `PLUGIN_VERSION`
  * Description: `NT Anti Ghosthop plugin version`
  * Bit flags: `FCVAR_DONTRECORD`
* sm_nt_anti_ghosthop_ratio
  * Default value: `1.0`
  * Description: `Scale for the max carry speed.  1 means original carry speed.  2 means double speed.  0.5 means half speed.`
  * Min: `0.01`
* sm_nt_anti_ghosthop_verbosity
  * Default value: `0.0`
  * Description: `How verbosely should the speed limiting be announced.  0: no announcement.  1: announce to the ghoster in chat.`
  * Min: `float(false)`
  * Max: `float(true)`


### What happened to the older versions?
The old versions are still available [from the tags](https://github.com/Rainyan/sourcemod-nt-anti-ghosthop/tags). Note that any tags older than the newest non-prerelease are no longer supported.
