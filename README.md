# .NET Core on Azure Cloud Services
This repository containes some examples of different approaches to run .NET Core apps as Worker Roles on Azure Cloud Services.
**This repository focuses on Worker Roles.** For Web Roles please refer to this [this article by Oren Novotny](https://oren.codes/2017/10/16/using-asp-net-core-with-azure-cloud-services/ "this article by Oren Novotny")  or to the [PoC available here](https://github.com/ACsharp/NetCoreWS/tree/master/NetCoreOnCloudServices  "PoC available here") 

## Approach 1 - .NET Standard
This is the simplest approach as id does not require any hack with the project files.
With this approach, you place your worker role logic in a .NET Standard library and you reference it from the classic .NET Framework based worker role project.
**[SEE EXAMPLE HERE](NetStandardApproach "See example here")**
## Approach 2 - SCD with EXE Role Entrypoint
This approach is based on a Self Contained Deployment (SCD) of a .NET Core console application. The csdef file in the cloud service project points directly to the executable of the .NET Core app as role entrypoint.
In order to get the .NET Core app deployed, we need to hack a dummy WorkerRole project so that it will trigger dotnet publish against the .NET Core project and include its output.
The benefit of this approach is performance as the .NET Core will work on the native .NET Core runtime. Using SCD means you do not need to add a startup task to install the .NET Core runtime on the VMs.
**[SEE EXAMPLE HERE](ScdWithExeEntrypointApproach  "See example here")**
## Approach 3 - FDD with EXE Role Entrypoint
## Approach 4 - Classic Worker Role entry point running SCD .NET Core app
## Approach 5 - Classic Worker Role entry point running FDD .NET Core app
