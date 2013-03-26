In a ASP.NET application I'm working on, we use NT Authentication but we
don't use full blown Impersonation.  This has been fine until I needed
to write some files out to some directories on the network.  Not wanting
to open up the network permissions to the ASPNET system user, I needed
to find a way to only impersonate for the period of time that I would be
writing files out.  The following lines of code is all the magic you
need to accomplish it:

System.Security.Principal.WindowsImpersonationContext
impersonationContext;\
  impersonationContext = \
   ((System.Security.Principal.WindowsIdentity)
Thread.CurrentPrincipal.Identity ).Impersonate();

//Do your impersonation code.

impersonationContext.Undo();

That's it.  .NET can't make it any easier then this.
