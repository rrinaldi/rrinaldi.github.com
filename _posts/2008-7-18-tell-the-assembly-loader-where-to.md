…shove find it.

I’m working on a project right now that has me doing a lot of dynamic
loading of assemblies.  To make things easier on me, I wanted to place
all of the assemblies I will be loading dynamically in a plugins
directory that is above the ApplicationBase (so, not in the \\bin
folder, but above that in the folder hierarchy).  This was working just
fine using Assembly.LoadFile(), but started bombing out when I was using
NHibernate.

One of NHibernate’s configuration options is that it looks for it’s
configuration file as an embedded resource in the current executing
assembly.  The problem is that Assembly.GetManifestResourceStream()
seems to look for the file on disk in your private path. (I say seems
because after reflecting the code, it hits unmanaged quickly and is
pretty much a black box.).  So I kept getting Fusion errors because it
couldn’t find my assembly, since it was looking in the private
path. Here is the nifty thing: The .NET framework doesn’t assume it is
the most intelligent, end all be all of assembly name resolution and you
can hook into it and load the assembly for the framework if it can’t
find it.  All you need to do is subscribe to the AssemblyResolve event
on the AppDomain.CurrentDomain.  Here is an example of the code you
could place in the event handler:

private System.Reflection.Assembly CurrentDomain\_AssemblyResolve(object
sender, ResolveEventArgs args)

{

string assemName = args.Name;

string[] assemblyInfo = assemName.Split(",".ToCharArray());

string fileName = “c:\\app\\plugins\\” + assemblyInfo[0] + ".dll";

System.Reflection.Assembly lastChanceAssem = null;

lastChanceAssem = System.Reflection.Assembly.LoadFrom(fileName);

return lastChanceAssem;

}

That’s it!  Enjoy!
