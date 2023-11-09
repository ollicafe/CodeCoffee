Reference guide to [[ASP.Net]]

It extends .NET with tools and libraries specifically for building web apps.

# Create app
```
dotnet new webapp -o <webapp_name> --no-https -f net7.0
```
- The `webApp` parameter selects what template to use when creating your app.
- The `-o` parameter creates a directory named `MyWebApp` where your app is stored.
- The `--no-https` flag specifies not to enable HTTPS.
- The `-f` parameter indicates you're creating a .NET 7 application.

# Running Web App

```
dotnet watch
```

# Razor Pages
[[Razor]] is a markup syntax for embedding .NET based code into webpages, consisting of Razor markup, [[C#]], and [[HTML]]. These files usually end in `.cshtml`

To see how to use, go to [[Razor Basics]]