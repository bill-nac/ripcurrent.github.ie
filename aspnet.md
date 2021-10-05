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
  
