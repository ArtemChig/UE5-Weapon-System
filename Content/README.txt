v1.0.0

This is the first version of my Weapon System for Counter Strike 2, but it can be used for any other project you are working on. i am planning to improve it in the future, so if youre interested stay tuned for updates. 

HOW TO USE

Step 1) Copy everything that "Content" folder contains inside your Unreal Engine project "Content" folder, it will not work otherwise.
Step 2) Go to the Content\VFX\Weapon_system\Weapon_System_BPS and drag to your scene any of the bp instances you want, or create your own by pressing on the master bp and creating a bp class. Open the bp instance and change the settings you want. If you want to change the Bullet settings, go to the Bullet Folder and create an instance of bullet master class, all the needed settings are exposed. Than go to your created Weapon System instance and select the created bullet instance in the "Bullet Type" field.
Step 3) After you've done that, drag your weapon system to the level. If you want to use it:
-Sequencer:
Drag the WS (weapon system) blueprint to your Sequence and add a Trigger event. Double click the created keyframe, and add the "Shoot" function, that should be called when event trigger (connect the event node to the function, and for the target select the target from event). Go to event and tick the "Call in editor" field and compile the script. 
-Game:
This blueprint wasn't originally made for the games but for the cinematics, but in case you want to in your control blueprint call the Shoot function when you need to.

After all that youre pretty much done. 


Decals/impacts/simulation

For your WS to work inside sequencer you need to enter the simulation mode, otherwise it won't work.

Bullet hole decals will work automaticly in simulation mode, but impacts won't. To add impacts on bullet collision, go to the phyiscs tab of the object your bullet may collide with, and add a physical material from the Content\Materials\Physical_Materials tab. For now there are only 6 surfaces with impacts, but i am planning on adding more in the next update. Once you selected the physical material, your impacts should work properly


PROBLEMS YOU MAY ENCOUNTER:
-Bullet is not colliding
1. Select all of the static meshes in your project by filtering them in content browser (or select any that you want to fix collision with, but i would reccommend selecting all of your meshes) press RMB -> Asset actions -> Edit selection in Property Matrix. This may take a while, so wait until it loads. In the "Pinned columns tab" go to the StaticMesh tab, open Body Setup, and select "use Complex collision as Simple" in the collision complexity tab. Wait until it finishes and your collision complexity must be fixed.
2. Go to the project settings, and start typing "complex" in the search bar. Look for "Default shape complexity" and select "use Complex collision as Simple". Find another variable called "Collision mode" and select "use Complex collision as Simple" as well. 
After that all of the collision problems you may encounter with WS, Niagara Particles, Niagara Fluids, and other type of collision should be fixed

-Textures for particles/decals did not load:
1. Probably you've imported the content folder files wrong. Delete everything that you've imported, and repeat the Step 1