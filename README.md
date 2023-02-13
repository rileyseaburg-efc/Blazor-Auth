# Blazor Authentication and Authorization

This is the best way that I have found to record the knowledge that I have learned for Blazor and .Net.

If you are looking for an actual reference source for this repo use the [Microsoft Documentation](https://learn.microsoft.com/en-us/aspnet/core/blazor/security/?view=aspnetcore-7.0)


Below you will find code snippets and explanations for how they work. 

Later there will be separate pages to reference but for now they will stay here.

## Getting a logged in user. 
If you want to find out what user is logged in to your [Blazor](https://dotnet.microsoft.com/en-us/apps/aspnet/web-apps/blazor) application add this code into a blazor component.

```CS

// Set parameter
    [CascadingParameter]
    private Task<AuthenticationState> authenticationStateTask { get; set; }
    
// Get the current logged in user
/// This is the most important line
var currentUser = (authenticationStateTask.Result).User;
var userName = currentUser.Identity.Name;

// Trim off NYSEFC\\
userName = userName.Substring(7);
```