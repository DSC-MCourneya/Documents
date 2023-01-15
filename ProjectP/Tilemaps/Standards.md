# TileMap Build Standards
## TileMap Custom Properties
The custom properties defined below are defined on all tilemaps for Project P. Unused properties should be filled with *NULL*.

| Field Name | Field Type | Description | Default Value | Required |
| :----: | :----: | :----: | :---: | :---: |
| *background1* | string | Reference ID of primary background layer. Appears under all other backgrounds and tiles. | *testBack01* | **Yes** |
| *background2* | string | Reference ID of background Layer 2. Drawn over *background1*. | *NULL* | No |
| *background3* | string | Reference ID of background Layer 3. Drawn over *background2*. | *NULL* | No |
| *bgmId* | string | Reference ID for Music played during gameplay | *testBgm01* | **Yes** |

## Standard Layers
The layers defined below are the defined on all tilemaps for Project P, even if that layer has nothing within it.

| Layer Name | Description |
| ---- | ---- |
| Tiles | Drawn tiles on tilemap. Non-interactable. Drawn over all background layers. |
| Collisions | Defines solid collision masks for entities to interact with |
| Entity | Defines all objects such as player and enemy spawns, collectables, etc. |
| Foreground | Tiles drawn in front of all tiles and objects |

#### Tiles Layer
The *Tiles* Layer defines the general visual look of the stage. It is used to define (visually) the slopes, ground, and other visual pieces that will be layered over in the *Collisions* layer.

#### Collisions Layer
The *Collisions* Layer defines the blocks that stop (either totally or in a single direction) objects in the stage. This programatically defines the stage and playspace.  All collision objects have the following properties:

*IsSlope* [bool] - *FALSE* by default. Flags the collision as a slope. If set to *TRUE* then the following X fields must be defined correctly.

*SlopeLeftHeight* [int] - Required if *IsSlope* is TRUE. This defines which pixel along the left margin of the tile is the first to border transparency. This is always counted from the top-left of the tile going downward. E.g. on an upward slope, it should be transparent in the top-left, but the first filled pixel may be the 7th pixel from the top. This value would be 7 in that case. On a downward slope, where the left margin is higher up than the right margin, this would be 7 if the 7th pixel is the last used pixel before transparency.

*SlopeRate* [float] - Required if *IsSlope* is TRUE. This defines how many pixels the slope increases when moving 1 pixel right. For slow slopes, where the slope only increases every few pixels, this value should be a decimal fraction (0.25 or 0.33 for 1/4 and 1/3, where you increase by 1px every 4 or 3 pixels right, respectively). On inverted slopes, such as ceilings, this should be a negative number.

*StopDirection* [string] - *ALL* by default. Defines the directions of movement stopped by this collision. Default value should be *ALL* to stop entities traveling in any direction. Other options are *Right*, *Left*, *Up*, *Down*, *Horizontal*, and *Vertical*.

*StopPlayerOnly* [bool] - *FALSE* by default. If set to TRUE, this collision is ignored by non-player entities.