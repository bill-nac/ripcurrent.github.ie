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

