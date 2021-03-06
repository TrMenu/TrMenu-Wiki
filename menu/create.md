# Create

## Basics

TrMenu menus are loaded from **YAML** \(.yml\) file

In order to create a new menu, you need to create a new YAML file and configure it

## Loading Folders

By default, TrMenu load all the YAML files in the `menus` folder, as well as its subdirectories

You can also custom some loading paths in the `settings.yml`

The file name of each menu will be taken as its ID

## Configure

Menu configuration will be introduced in the next chapter

Learn the basic structure below

```yaml
# The title of the menu
Title: 'TrMenu'

# The update period of titles
Title-Update: 40

# Layout of the menu
Layout: [ ]

# Layout (Player Inventory)
PlayerInventory: [ ]

Options:
  # Whether to enable the arguments feature
  Arguments: false
  # Default arguments complete
  Default-Arguments: [ ]
  # Unlocked slots
  Free-Slots:
    - 71
    - 72
  # Default page
  Default-Layout: 0
  # Whether to hide player's items when viewing a menu
  Hide-Player-Inventory: false
  Min-Click-Delay: 200
  Depend-Expansions: [ 'server', 'player', 'progress', 'animations' ]

Bindings:
  Commands:
    - '(?i)example(-)?(gui)?(s)?'
  Items:
    - 'material:compass'
    - 'material:clock,lore:OPEN_MENU'
    - 'texture:eyJ0ZXh0dXJlcyI6eyJTS0lOIjp7InVybCI6Imh0dHA6Ly90ZXh0dXJlcy5taW5lY3JhZnQubmV0L3RleHR1cmUvNDRmNDUyZDk5OGVhYmFjNDY0MmM2YjBmZTVhOGY0ZTJlNjczZWRjYWUyYTZkZmQ5ZTZhMmU4NmU3ODZlZGFjMCJ9fX0='

Events:
  Open:
    - condition: 'perm *trmenu.use'
      actions:
        - 'sound: BLOCK_CHEST_OPEN-1-0'
      deny:
        - 'sound: ENTITY_ITEM_BREAK-1-0'
        - 'title: `&c&lPermission Required` `&7&lYou need permission &6&ltrmenu.use &7&lto open this menu` 15 20 15'
        - 'return'
  Close:
    - 'sound: BLOCK_CHEST_CLOSE-1-0'

Icons:
  # The ID of this icon
  'Close':
    # The update settings
    update: [ ]
    # The refresh period (to recalculate the sub-icons)
    refresh: -1
    # The display part
    display: [ ]
    # The click handler
    actions: [ ]

# Custom scheduled tasks
Tasks:
  # ID
  tikTok:
    # Period (in ticks)
    period: 80
    # Reactions
    task:
      - condition: '$ sender.isOp()'
        actions:
          - 'sound: BLOCK_NOTE_BLOCK_BIT-1-2'

# Internal JavaScript functions
Functions:
  id: 'content'
```

### Structure

* Title
  * Single for static or multiple for animation
  * The update period
* Layout
  * Layout for the container
  * Layout for the player's inventory
* Options
  * Default Arguments
  * Default Page Index
  * Hide Player Inventory Items
  * Unlocked Slots
  * Min click delay
  * Depend-on PlaceholderAPI expansions
* Bindings
  * Bound Commands \(Regex\)
  * Bound Items
* Events
  * Open Menu
  * Close Menu
* Icons
* Internal Functions
* Scheduled Tasks

