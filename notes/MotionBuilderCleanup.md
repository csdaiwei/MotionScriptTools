
Raw motion capture data often has artifacts when mapped to a character model, such as self-intersections, floating or sinking  feet, and sliding contacts with the floor.  These notes assume that <a href="http://www.alinenormoyle.com/weblog/?p=406">we have already setup an actor and character</a>.

<strong>Post-processing using a control rig</strong>

From the character controls window, make sure character is selected. Currently, the input should be ‘Actor Input’.
<ul>
 	<li>First, select Edit/Control Rig Input. You will be prompted to create a control rig if one doesn’t already exist. Create a FK/IK control rig.</li>
 	<li>Next, re-select actor for your input.</li>
 	<li>Then, go to edit/plot character and plot to the control rig.</li>
 	<li>Now, the character input should be set to control rig.</li>
</ul>
Now, you can edit poses using the control rig effectors. For example, suppose an arm passes through the torso. We can go to the worst intersecting frame, select the hand effector, and drag the hand out of the body. Effectors can be selected from character control pane.

When you are happy with a pose, select whether you want the whole body to be keyed, or just the selected body part. Then choose ‘flat’ key. Make sure keys are on their own animation layer, so that the raw animation from the motion data is not changed.

NOTE: In the character settings (tab next to character definition), you can specify that you want contacts to be clamped to the floor.

When you are happy with the animation, plot the animation to the SKELETON (Edit, plot Motion, skeleton). It’s important to plot to the skeleton to ensure that
<ul>
 	<li>you do not lose all your control rig keyframes</li>
 	<li>you do not accidentally bake mistakes onto the original motion</li>
</ul>
Other tips can be found here from <a href="http://mocappys.com/?p=124">mocappys MotionBuilder tutorials</a>.

<strong>Fixing foot sliding</strong>

Now that we have a control rig setup, we can add additional constraints to prevent effectors from sliding when they shouldn’t. Make sure story mode is turned off.

These following notes are based from this <a href="http://www.youtube.com/watch?v=OEYVdfskWBU">video tutorial</a>.
<ul>
 	<li>First, scrub to the animation to the start of a contact.</li>
 	<li>Select the effector whose position and/or rotation you would like to pin. Right click and create an auxiliary effector.</li>
 	<li>In the character controls, the ‘K” keys will allow you to toggle keyframes. Make sure that the aux effector has 100% reach influence when the foot should be planted and 0% influence otherwise. Changing the reach influence for the rig effector to 0% will ensure that position does not change at all.</li>
 	<li>Use the FCurves window to tweak the transition from the pinned position to the original control rig motion.</li>
</ul>
<strong>Tweaking FCurves</strong>

Joints can be selected in the hierarchy view and edited directly in the FCurves window.
<ul>
 	<li>To fit the window to the curve, select curve on the left (for example, rotation), and then press the ‘f’ key.</li>
 	<li>To zero the rotations, select all keys and enter a zero in the value edit box on the right.</li>
 	<li>To offset the curve, change one of the key values to the desired value and then select ‘move’ from the animation controls window.</li>
</ul>
For more tips, check out <a href="http://mocappys.com/?p=207">mocappys</a>.