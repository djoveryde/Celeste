# Celeste - Add shooting stars to your Minecraft server
Celeste is a simple plugin that adds shooting stars to your Minecraft server. Inspired by the shooting stars from Animal Crossing and the falling stars from Breath of the Wild, this plugin brings some celestial ambience to your Minecraft world. 
## Features
- Add shooting stars to the night sky, with configurable frequency
- Find rare falling stars that deliver precious materials in a sparkling package
- Watch meteor showers that occur every new moon, increasing the rate of shooting and falling stars

![Shooting stars and a falling star in the corner](/images/meteor_shower.gif)

### Shooting stars
Shooting stars occur once every 10 seconds by default (6 times a minute), but due to how large the area around a player is, you would usually only see one every few minutes unless you were stargazing. They have no functional purpose and are only there to sparkle and look pretty.
To more accurately emulate real world meteors, these virtual shooting stars vary in speed, length, and can even break up into multiple parts while burning up!

![Falling star](/images/falling_star_close.gif)

### Falling stars
Inspired by the star fragments from The Legend of Zelda: Breath of the Wild, these rare stars are fall from the sky only once or twice a night! They are marked by a streak of light and resonating sound as they fall towards the earth, and once they land the stars spark and sizzle for 10 seconds by default to help players find them. They can be easy to miss, with players only knowing one has fallen by the distinctly resonating sound they make on impact. But if a player is lucky enough to find one, they may receive a rare treasure as well as some experience! This loot is completely customizable, and the documentation for that can be found further below.

## In-Depth Functionality
Shooting stars and falling stars spawn on a per-world basis. This means that the number of players in a world does not affect the spawning rate. When either type of star is given a chance to spawn, the plugin will find a random player within that world and center the spawn in a large radius around said player, in order to avoid sending stars to unloaded chunks where they would never be found.
Additionally, the worlds that shooting and falling stars can spawn in must meet the following conditions:
- Must have players in the world currently
- Must be nighttime (between 13000 and 23000 in game time)
- Must be clear weather (no rain or snow)
- Will not spawn in the nether or end

## Configuration
Installation is as simple as copying the newest build jar to your plugins folder. **A configuration file is not added by default**, but can be easily created by making a "Celeste" directory in your plugins folder and creating a "config.yml" within that directory. It is not necessary (nor recommended) to copy everything from the default config shown below, instead copy only the lines you wish to change.
### Defaults
``` yaml
# The average number of shooting stars to create per minute for each world
shooting-stars-per-minute: 6
# Whether to create falling stars or not
falling-stars-enabled: true
# The average number of falling stars to create per minute for each world
falling-stars-per-minute: 0.2
# The maximum distance around a player within which a falling star may spawn
falling-stars-radius: 75
# How many ticks a falling star should spark for once it has landed (20 ticks is a second)
falling-stars-spark-time: 200
# How many experience points (not levels) to provide from catching a falling star
falling-stars-experience: 100
# The possible loot from a falling star, and the weighted chance of each item appearing
falling-stars-loot:
  diamond: 60
  emerald: 20
  fire_charge: 20
# Whether to have meteor showers on nights with a new moon, increasing the spawn rates
new-moon-meteor-shower: true
# The number of shooting stars to create per minute during meteor showers
shooting-stars-per-minute-during-meteor-showers: 15
# The number of falling stars to create per minute during meteor showers
falling-stars-per-minute-during-meteor-showers: 0.3
```
### Falling Star Loot
Falling stars drop loot wherever they fall, and spark for 10 seconds (200 ticks) by default to show their location. The loot they drop is randomly selected from the loot table in the config, with each material being given a weight. For instance, in the default config, there is a 60% chance for a diamond, 20% of an emerald, and 20% chance of a fire_charge. Experience also drops from falling stars, 100 points (not levels) by default.

To define your own loot tables, add the `falling-stars-loot` attribute to your config (remember, you will have to create the plugin config if you haven't already done so) and list each item you want as well as the probability for it to appear. **The names of the items must be from the list provided [here](https://hub.spigotmc.org/javadocs/spigot/org/bukkit/Material.html)**. Remember to only add materials available in your server version.

Here is an example of a custom loot configuration:

``` yaml
falling-stars-loot:
  nether_star: 0.05
  apple: 33
  blaze_spawn_egg: 33
  blue_orchid: 33
 ```

## Commands
**/shootingstar**  summons a shooting star in the sky around the player, however because the area a shooting star can spawn is quite large, it is easy to miss just a single one. I am currently working on making it appear exactly above the player for easy testing

**/fallingstar** summons a falling star at the exact location of the player

