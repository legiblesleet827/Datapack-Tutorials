As Mojang removed custom structures in 1.18, we have to resort to different methods to do structure generation.

Firstly, we need a structure.nbt file. It can be called whatever you want to call it.\
Then, we need another structure nbt file named `empty.nbt`, which, as the name suggests, should be completely empty, containing no blocks or entities.

Usually, we would need a `configured_structure_feature` with the old system, but now we need a `configured_feature`.

Put the following code in the file `Tutuorial Datapack/data/tutorial/worldgen/placed_feature/tutorial_structure.json`, replacing `Tutorial Datapack`, `tutorial` and `tutorial_structure.json` with your datapack name, namespace and structure name respectively.
```json
{
  "feature": {
    "type": "minecraft:fossil",
    "config": {
      "max_empty_corners_allowed": 4,
      "fossil_structures": [
        "tutorial:tutorial_structure"
      ],
      "overlay_structures": [
        "tutorial:empty"
      ],
      "fossil_processors": "minecraft:empty",
      "overlay_processors": "minecraft:empty"
    }
  },
  "placement": [
    {
      "type": "minecraft:count",
      "count": 10
    },
    {
      "type": "minecraft:heightmap",
      "heightmap": "WORLD_SURFACE_WG"
    }
  ]
}
```
You can change `tutorial` and `tutorial_structure` with your namespace and structure.nbt file name, but do not change `empty` unless you named your empty structure nbt differently.\
`count` is self-explanatory, the heightmap with `WORLD_SURFACE_WG` makes it generate on the world surface.\
You can also change the `placement` to something like this:
```json
{
  "feature": {
    "type": "minecraft:fossil",
    "config": {
      "max_empty_corners_allowed": 4,
      "fossil_structures": [
        "tutorial:tutorial_structure"
      ],
      "overlay_structures": [
        "tutorial:empty"
      ],
      "fossil_processors": "minecraft:empty",
      "overlay_processors": "minecraft:empty"
    }
  },
  "placement": [
    {
      "type": "minecraft:count",
      "count": 10
    },
    {
      "type": "minecraft:height_range",
      "height": {
        "above_bottom": 128
      }
    },
    {
      "type": "minecraft:height_range",
      "height": {
        "below_top": 256
      }
    }
  ]
}
```
This generates the structure on specific Y levels in relation to the bottom and top of the world, in this case on Y 64.

And that is how to do structure generation in 1.18.x!