# Weapon System v1.0.2 for Unreal Engine 5.3.2

This is my Weapon System for **Counter Strike 2**, but it can be used for any other project you are working on. I am planning to improve it in the future, so if you're interested, stay tuned for updates.

## How to Use

1. **Engine Configuration:**
   - Open the `Engine Config/` folder and find the `!DefaultEngine_additional_commands.txt` file, copy all the text inside.
   - Go to the `PATH_TO_YOUR_PROJECT\Config` folder and find the `DefaultEngine.ini` file. Paste the text you copied at the very end.
   - *(Alternatively, you can copy my `DefaultEngine.ini` file, but this is not recommended as you will lose your project settings.)*

2. **Content Import:**
   - Copy everything inside the `Content` folder exactly into your Unreal Engine project's `Content` folder. This is essential for proper functionality.

3. **Add to Scene:**
   - Go to `Content\VFX\Weapon_system\Weapon_System_BPS` and drag any of the BP instances or the master BP into your scene. Select the weapon you want to use.

4. **Using the Weapon System:**
   - **Sequencer:**  
     Drag the Weapon System (WS) blueprint to your sequence and add a Trigger event. Double-click the created keyframe, and add the "Shoot" function, connecting the event node to the function. For the target, select the target from the event, and compile the script.
   - **Game:**  
     While the blueprint is primarily designed for cinematics, you can call the `Shoot` function in your control blueprint. Additionally, in the Weapon System master BP, change the `Muzzle Bones` array value to match your muzzle bone name.

After following these steps, your setup should be ready to use.

---

## Decals/Impacts

- **Sequencer Mode:**  
  The WS needs to be in simulation mode inside the sequencer to work properly.
  
- **Bullet Hole Decals:**  
  Bullet hole decals will automatically work in simulation mode, but impacts require manual setup. To add impacts for bullet collisions:
  - Go to the physics tab of the object your bullet may collide with.
  - Add a physical material from `Content\Materials\Physical_Materials`. 
  - Currently, only six surfaces with impacts are available, but more will be added in future updates.
  
Once the physical material is selected, your impacts should work correctly.

---

## Blood Splatters/Enemy Hit

To enable blood splashes upon hitting an enemy target:

1. Select the enemy's skeletal mesh in the content browser.
2. Right-click (RMB) -> Create -> Physics Asset -> Create and assign.
3. Transform the physics body parts to cover the model.
4. Select all parts using `ctrl-a`, go to the "Collision" tab, and find "Phys Material Override". Select `PM_Flesh`.
5. In the skeletal mesh actor, change the "Physics Asset Override" to the asset you created.
6. In the "Collision Presets", set it to `NoParticleCollision`.

---

## Common Problems

### Bullet is Not Colliding

1. **Static Mesh Collision:**
   - Filter all static meshes in the content browser, right-click (RMB) -> Asset Actions -> Edit Selection in Property Matrix. This may take a while.
   - In "Pinned Columns", go to the "StaticMesh" tab, open "Body Setup", and set "Collision Complexity" to `Use Complex Collision as Simple`.

2. **Project Settings:**
   - Go to project settings and type "complex" in the search bar.
   - Set both "Default Shape Complexity" and "Collision Mode" to `Use Complex Collision as Simple`.

### Textures for Particles/Decals Did Not Load

1. You may have imported the content folder incorrectly. Delete the files and repeat **Step 2**.

### Issue with Physical Surfaces / NoParticleCollision Preset Not Showing

1. Check the project settings to ensure the physical surfaces are loaded correctly.
2. If the `NoParticleCollision` preset is missing, repeat **Step 1** of the setup.

---

Stay tuned for future updates!
