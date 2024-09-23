# Weapon System v1.0.3 for Unreal Engine 5.3.2

This is a Weapon System for **Counter Strike 2** ported in Unreal Engine 5, but it can be used for any other project you're working on. I am planning to improve it in the future, so if you're interested, stay tuned for updates.

## How to Use

### Step 1: Engine Config Setup
1. Open the `Engine Config/` folder and find `!DefaultEngine_additional_commands.txt`. 
2. Copy all the text inside the file. 
3. Go to the `PATH_TO_YOUR_PROJECT/Config` folder and find the `DefaultEngine.ini` file.
4. Paste the copied text at the very end of the `DefaultEngine.ini` file.
   - Alternatively, you can copy my `DefaultEngine.ini` file, but it's not recommended since you will lose your project settings.

### Step 2: Content Folder Setup
1. Copy everything inside the `Content` folder to your Unreal Engine project `Content` folder. 
   - Note: The system will not work unless the files are in the correct folder.

### Step 3: Weapon Setup
1. Go to `Content\VFX\Weapon_system\Weapon_System_BPS` and drag any of the BP instances or the master BP into your scene.
2. Select the weapon and camera for POV, and just the weapon for Enemy WS.

### Step 4: Using the Weapon System

#### Sequencer:
1. Drag the WS (weapon system) blueprint to your sequence and add a trigger event.
2. Double-click the created keyframe, and add the `Shoot` function. Connect the event node to the function, and for the target, select the target from the event.
3. Compile the script.

#### Game:
- This blueprint was originally made for cinematics, but if you want to use it in-game, call the `Shoot` function in your control blueprint.
- In the weapon system master BP, change the muzzle bones array value to match your muzzle bone name.

After these steps, your weapon system should be ready.

## Decals and Impacts

- For the WS to work inside the sequencer, you need to enter simulation mode.
- Bullet hole decals work automatically in simulation mode, but impacts won't. To enable impacts on bullet collision:
  1. Go to the physics tab of the object the bullet may collide with.
  2. Add a physical material from `Content\Materials\Physical_Materials`.
  - Currently, only 6 surfaces have impacts, but more will be added in future updates.

## Blood Splatters and Enemy Hits

- For blood splashes when bullets hit enemies:
  1. Select the enemy's skeletal mesh in the content browser, right-click -> Create -> Physics Asset -> Create and assign.
  2. Adjust the physics body parts to cover the model.
  3. Select all parts (`Ctrl + A`), go to the "Collision" tab, and set the "Phys Material Override" to `PM_Flesh`.
  4. Go to the skeletal mesh actor and set the Physics Asset Override to the asset you just created. 
  5. In the "Collision" tab, change the preset to `NoParticleCollision`.

## Common Issues and Solutions

### Bullet Not Colliding
1. Filter and select all static meshes in the content browser, right-click -> Asset actions -> Edit selection in Property Matrix.
2. In the "Pinned columns" tab, go to `StaticMesh -> Body Setup` and set "Collision Complexity" to `Use Complex Collision as Simple`.
3. Go to project settings, search for "complex", and set both "Default Shape Complexity" and "Collision Mode" to `Use Complex Collision as Simple`.

### Textures for Particles/Decals Not Loading
1. You may have imported the content folder incorrectly. Delete everything and repeat **Step 2**.

### Issue with Physical Surfaces / `NoParticleCollision` Preset
1. Check if your physical surfaces loaded correctly in project settings.
2. If `NoParticleCollision` isn't available, repeat **Step 1**.

### Bullet Not Flying
1. Check the message log after simulation for "Trying to simulate physics on .../BP_Bullet_Master_C...Bullet".
2. Go to the WS master BP, find the Bullet object, then the Sphere mesh, and change the collision complexity to `Simple and Complex`.

## Planned Features
- More surfaces with impacts
- Additional features for game integration

## License
This project is licensed under the MIT License - see the LICENSE file for details.
