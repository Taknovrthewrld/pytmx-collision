# pytmx-collision
pygame pytmx Tiled collision detection

This is a simple outline of how pytmx connects Tiled or any tmx map editor to Pygame.

RENDERING THE MAP
1. A tmx map built in Tiled is loaded into Pygame using pytmx.
2. Tiles are pulled from the tmx map as surfaces
3. The tile surfaces are used to build Tile() objects
4. Tile() objects are added to a pygame.sprite.Group and drawn to the screen

PLAYER MOVEMENT
1. Give player a direction attribute = "None"
2. Key down events should change the direction
3. Key up events should reset direction to "None"
4. Main loop logic:
      If player.direction = "Right" then player.rect.x += change_in_x
      If player.direction = "Up" then player.rect.x += -change_in_y    ##remember, adding a negative is subtracting
      etc.

COLLISION DETECTION
1. Main loop logic:
      FOR sprite IN pygame.sprite.Group:     ##sprites are Tile() in this case, the group is layer2_list
          IF player.rect.colliderect(sprite):
              If player.direction = "Right":    ##collisions subtract the change_in_x
                  player.rect.x -= change_in_x  ##thus canceling out the key down event movement
              If player.direction = "Up":
                  player.rect.y -= -change_in_y
              etc.
