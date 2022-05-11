# ASP NET tips

## Data Transfer Object

Encapsulate information back from calls using a standard model that can return data, messages and more

```
public class DataTransferObject
{
  public List<DTOMessage> Messages {get;set;}
  public dynamic Result {get;set;}
}
```
  
## Logging

If you want to see the logging messages from dependant assemblies you must reference them directly from Top Project. Its not enough to have them referenced by another dependency

## IIS Logging
1. create "logs" folder under IIS application direction
2. grant everyone permissions on this folder
3. update web.config: stdoutLogEnabled="true" 

## ViewComponents in a seperate assembly
1. Define the ViewComponent in the library assembly e.g. MyTestViewComponent
2. When using the ViewComponent in the calling application, remember to omit the "ViewComponent" in the name!
e.g. @await Component.InvokeAsync("MyTest",null)
