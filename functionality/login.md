Login
=====

Some ideas for login post-MVP:

[SQRL](https://www.grc.com/sqrl/sqrl.html)
------------------------------------------

This method of authentication is incredibly secure, and implements our current
method of storing a single-use access token, but saves it on the user's phone,
using the phone as a source of truth, which is reliable most of the time. The
rest of the time, when that is not a correct source of truth, SQRL allows for
a master user password. Seems like a general all-around improvement to the
current system, excepting the fact that users will have to take out their phone
on every login (Which isn't much more annoying that retyping/copy-pasting their
access token).

Voice Recognition
-----------------

This method of authentication falls in the "Ideal, but Potentially Impractical"
category. It would be super nice just to be able to speak to log in, however
this would need to be intensively tested and we would need to be extremely
confident to ship it at all.
