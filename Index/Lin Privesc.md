+ [Agent T](../THM/Agent%20T.md) 

In this machine a vulnerable version was found PHP 8.1.0, which after exploited took us straight to root.

+ [Archangel](../THM/Archangel.md) 

Here linpeas was used, it discovered a vulnerable cronjob that lets us privesc to another user, from which it was discovered that the cp command had root permissions.

+ [Cap](../HBT/Machines/Cap.md)

Linpeas was used and it discovered that the file python3.8 had the CAP_SETUID capability, which was used to privesc to root.

+ [Cat Pictures 2](../THM/Cat%20Pictures%202.md) 

In this machine linpeas discovered that sudo version 1.8.21p2 was being used, with a cve exploit it was exploited and got root priv.

+ [Dreaming](../THM/Dreaming.md) 

Here after enumerating it was discovered that there was file that when executed would run another file with root privileges, so it was replaced with a reverse shell to get root.

+ [Easy Peasy](../THM/Easy%20Peasy.md) 

It was dicovered that a cronjob was running a file with root privileges, so an reverse shell was added to get those permissions.

+ [Expressway](../HBT/Machines/Expressway.md) 

With linpeas a vuln version of sudo was discovered, exploiting a cve got the root perm.

+ [Fowsniff CTF](../THM/Fowsniff%20CTF.md) 

The file that had the banner for when a user connected through ssh was editable by a user and ran with root priv, so a reverse shell was added to it.

+ [Gallery](../THM/Gallery.md) 

Credentials found by linpeas where used for first scalation, then it was discovered that the user had access to a file with root priv, so gtfo bins was used to privesc to root.

+ [GLITCH](../THM/GLITCH.md) 

Thank to linpeas a doas privesc was found.

+ [Lian_Yu](../THM/Lian_Yu.md) 

After enumeration it was dicovered that the user could run pkexec as root, so it was used to read the CTF root flag.

+ [Mustacchio](../THM/Mustacchio.md) 


+ [Plotted-TMS](../THM/Plotted-TMS.md) 
+ [Poster](../THM/Poster.md) 
+ [RootMe](../THM/RootMe.md) 
+ [Smag Grotto](../THM/Smag%20Grotto.md) 
+ [tomghost](../THM/tomghost.md) 