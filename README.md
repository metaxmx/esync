esync - Encrypted Synchronization
=================================

About
-----

`esync` is a perl script, which will run primarily on linux systems.
It's main purpose is it to create a connection to a rootserver via ssh (e.g. `sshfs` mount) and upload or download files.
You can encrypt any uploaded file with a public key via [gpg][1], so that this file is safe to anyone, who does not have the corresponding private key.
When uploading, `esync` can create a tarball archive, compress the file with gzip, encrypt the file with any public key and the upload it. While downloading, esync does it the other way round.

You can access `esync` as a normal user - you don't ever need root-privileges. You call `esync` from the commandline with parameters, but it will also ask for confirmation sometimes. You can configure the tool with a config file in your homedirectory.

If there are several people/systems using one rootserver account, any user can store his public key in a "key-directory". So, other people can import this public key and encrypt packages with that key (for him to use).

`esync` is performing temporary actions in a "sandbox" directory and saving downloaded files in a special "incoming" directory, so that the system can not be damaged.

These actions are implemented in esync so far:
* display help
* display usage
* list available packages
* upload (and encrypt) a package
* download (and decrypt) a package
* list keys in the storage
* export a public key to the key-storage
* import all keys from the key-storage
* clean temporary directory

Of course, esync needs all used programs (`gpg`, `tar`, `cp`, `mv`, `mount`, etc.) to be installed.

Warning
-------

While I believe that the concepts of this tool still work, I want to point out that this program was developed in *2006* and that some of the commandline parameters or the behaviour of the used 3rd-party tool (like gpg) could have changed in the meantime.

If you find such an incompatibility, feel free to create a patch, if you are able to.

The tool `esync` comes with NO WARRANTY.

License
-------

`esync` is licensed under the [GNU Public License (GPL), Version 2][2].


[1]: http://www.gnupg.org/
[2]: http://www.gnu.org/licenses/gpl-2.0.html