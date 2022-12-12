# Unity-Machine-Learning-Agent
This represents how to make a machine learning agent in Unity while collecting data through a python virtual environment
The first step you want to do is make sure you have python and Unity on your device. 
Then you will want to create a new unity project in the Unity app. 
Once you save the project you can go and minimize Unity. 
You will then want to open command prompt and change directory to wherever you want to save your files. Putting it with the Unity project would be the easiest
Changing directory: cd (copy and paste the path in the file explorer of where you want to save your files)
After you've changed directories, you will then want to create a python virtual environment. You accomplish this by typing: py -m venv venv
This creates the virtual environment wherever you changed your directory to and if you check the file explorer, you should see a venv folder
Activating the virtual environment will be the next step. You can do this by typing: venv\Scripts\activate
You will be in the virtual environment at this point and you will want to make sure that your installer is properly upgraded: python -m pip install --upgrade pip
At this point, you're installer should be upgraded. 
The next step will be to install pytorch, which provides machine learning and neural network access
pytorch installation: pip install torch=1.13.0 -f https://download.pytorch.org/whl/torch_stable.html
You should change the "torch=" to whatever the latest stable version of Pytorch is. 
After this, you can download mlagents: pip install mlagents
Mlagents should be installed at this point, but you can make sure it is downloaded by typing: mlagents-learn --help

You will want to then open up Unity again. and go to window and open the package manager. In the top of the package manager, click on packages and go to Unity Registry. Scroll down until you find mlagents and install the pacakge
After mlagents is installed in Unity, you can create a new gameobject and go to add component and you should see an Mlagents tab. This confirms that you have successfully installed mlagents. 

Now that mlagents is installed correctly, you will want to create a floor, a sphere, four cubes and a capsule. The sphere will be used as a goal or collectable, the capsule will be used as the agent and the cubes will be stretched out to be walls around the floor. 

For the capsule agent, you will want to go to Add Component and add the Behavior Parameters, Decision Requester, rigidbody and a new script called Collect. (I named my script Collect, but this will be the main goal of the agent, to collect the sphere)

In the Behavior Parameters you'll want to change the Behavior Name to whatever you named the new script above (Mine is changed to Collect). You will want to change the Space Size to 6 as it will take in values of the x, y, and z coordinates. Finally, you will want to change the continous Actions to 2 since we will be taking in data from the x and z coordinates. 

Once this has been completed, refer to the collect script to understand how it works. 
Once the Collect script has been made, you will want to right click on your assets and create two new materials. You can choose any color, but one material will be used for a winning floor and the other will be used for a losing floor. You will want to click and drag the materials to either the win or lose part of the collect script. Ontop of this, you will want to drag your sphere into the Target part of the collect script and your floor into the Floor part of the Collect script. 
Now we will go to the sphere collectable. Click on the sphere and go to add component, new script and name it as Goal. This is important as the Goal script will be used as a name tag so the Agent knows when it collides with it. 
Similar to the step above, you will want to go to each of your walls, Add Component, new script and name it Wall. This will be used so the agent knows that when it hits a wall, negative reinforcement occurs. 

At this point, your Unity should be setup correctly and we can now begin the machine learning.

Now you want to go back into the command prompt. using the command: mlagents-learn --run-id=Test1, you will be able to conduct the first data collection of your agent. After you run this command, you will have to wait a couple of seconds until Unity appears in your command prompt. Once it does appear, you can go back to Unity and press the play button and your agent will start its machine learning through reinforcement. It will take a very long time for the agents to properly work.
Once you are done with your test, you can click the play arrow again and it will stop the test. You can go back into your command prompt and the data you will be gathered and put into a folder called Results. This is where you can get the data that you collected and this can be a brain or neural network for newer agents that you want to test or train. The .onnx file will hold this data and you can copy and paste it from the Results folder into the Assets of Unity. Once you've copied and pasted it into Unity, you can drag and drop that file into the Behavior Parameters under Model and it will have the data accessible to it. 

After this, you have completed making a machine learning agent using reinforcement learning in Unity. 

**Note the id=Test1, Test1 needs to be changed every time you run a new test as it will collect data and put that data into a folder named Results.
