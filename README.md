# Weapon System v1.0.1 for Unreal Engine 5.3.2

This is the v1.0.1 version of my **Weapon System** for **Counter Strike 2** ported in Unreal Engine, but it can be used for any other project you are working on. I plan to improve it in the future, so if you're interested, stay tuned for updates

---

## How to Use

### Step 1: Copy Content
- Copy everything from the `Content` folder inside your Unreal Engine project `Content` folder.
- **Important**: It will not work otherwise.

### Step 2: Add Weapon System
- Go to `Content\VFX\Weapon_system\Weapon_System_BPS` and drag any BP instance to your scene.
- You can also create your own by selecting the master BP and creating a new BP class.
- Open the BP instance and customize the settings as needed.
- 
### Step 3: Integrating the Weapon System
- **For Sequencer**:
  - Drag the WS (Weapon System) blueprint into your Sequence and add a Trigger event.
  - Double-click the created keyframe and add the **Shoot** function. Connect the event node to the function, and for the target, select the target from the event.
  - Enable the "Call in editor" field and compile the script.
  
- **For Game**:
  - Although this blueprint is designed for cinematics, you can still use it in-game.
  - In your control blueprint, call the **Shoot** function when needed.

---

## Decals, Impacts, and Simulation

### Simulation Mode
- For the WS to function inside Sequencer, you must enter simulation mode, otherwise, it won't work.

### Bullet Hole Decals & Impacts
- Bullet hole decals will automatically work in simulation mode, but impacts won't.
  
  **To Add Impacts**:
  1. Go to the **Physics** tab of the object your bullet may collide with.
  2. Add a physical material from `Content\Materials\Physical_Materials`.
  3. Select the physical material, and your impacts should work properly.

  There are currently 6 surfaces with impacts, but more will be added in future updates.

---

## Common Problems & Solutions

### Problem 1: Bullet is not Colliding
1. **Fixing Static Mesh Collisions**:
   - Select all static meshes in your project by filtering them in the content browser (or choose the specific meshes you want to fix).
   - Right-click -> **Asset Actions** -> **Edit Selection in Property Matrix**.
   - In the "Pinned Columns" tab, go to the **StaticMesh** tab, open **Body Setup**, and set **Collision Complexity** to "Use Complex Collision as Simple".
   - Wait for it to complete.

2. **Project Settings**:
   - In project settings, search for "complex".
   - Set **Default Shape Complexity** to "Use Complex Collision as Simple".
   - Set **Collision Mode** to "Use Complex Collision as Simple".

These changes should fix most collision issues for WS, Niagara Particles, Niagara Fluids, and other collision types.

### Problem 2: Textures for Particles/Decals Did Not Load
1. **Fix Import Issues**:
   - If textures did not load, it's likely you imported the content folder incorrectly.
   - Delete everything you imported and repeat Step 1 from the "How to Use" section.
