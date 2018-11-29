# BulletWhale.HoloToolkit.AnchorManagement
The AnchorManagement system developed for league of lasers. This package was originally intended for Unity 2017.4.3f1, it also requires the HoloToolkit: https://github.com/Microsoft/MixedRealityToolkit-Unity

This system will share HoloLens anchors using web requests or store them on a local disk. 
The servir to post and retrieve from can be configured, it is recommended to deploy a simple webserver that implements endpoints for
posting anchors and retrieving them. This server is not provided in this package.

The package includes some scripts and prefabs to use this sharing solution. 

# Prefabs:
- Anchor: This is the anchor who will be serialized and send by a master client or received by slave clients. Just place it in the game scene that needs anchors.
- AnchorManager: This needs to be in the starting scene.
- WebService: The web service needs to be present in the starting scene if you want to use anchor sharing via webrequests.

# Usage:
Sending commands to the anchor manager is easy for example to send an export command is as follows:
``AnchorManagerBehaviour.Instance.AnchorManagerController.EnqueueCommand(new ExportAnchorsToWebServerCommand(SomeCustomCallbackMethod, WebService.Instance));``
Here we simply call the AnchorManagerBehaviours instance (this class is a singleton) and ask the controller on the instance to enqeue the command.
Note: most commands will require the user to provide a custom callback method that is called once a task has been completed. Most of these commands are executed asynchronous.

Custom commands can be implemented aswell simply by implementing the ``IAnchorManagerCommand``.

For further questions please place an ussue or contact us at n.a.miedema@student.tudelft.nl or j.vermeer-1@student.tudelft.nl
