Login
=====


Criteria
--------
1. Secure - in the sense that brute force is not a potential threat
2. Involves a public unique generated identifier and private token

Issues
------
* The primary issue is how to generate and manage the user's token.

Ideas for login post-MVP:
-------------------------

#### [SQRL](https://www.grc.com/sqrl/sqrl.html) ("squirrel")
This method of authentication is secure. It also implements our current method of storing a single-use access token, but saves this "token" on the user's phone. Thus treating the phone as a source of truth. When the phone option is not reliable, SQRL allows for a master user password. 

Potentially an all-around improvement to the current system, excepting the fact that users will have to take out their phone on every login (Which isn't much more annoying that retyping/copy-pasting theiraccess token).

#### Voice Recognition
This method of authentication falls in the "Ideal, but Potentially Impractical" category. It would be super nice just to be able to speak to log in, however this would need to be intensively tested and we would need to be extremely
confident to ship it at all.
