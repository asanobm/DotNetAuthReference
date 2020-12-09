## Individual Auth Reference

This Project is .NET Core WebApp with Individual Authentication.

## Create Project

```Shell
# Templete
dotnet new webapp --auth Individual -o [Project Name]
```

## add solution

```
--solution_path
  └── IndividualAuthReference
```

next command run

```
dotnet sln add ./[Project Name]
```

## Check Project Details

```
.
├── Areas
│   └── Identity
├── Data
│   ├── ApplicationDbContext.cs
│   └── Migrations
├── IndividualAuthReference.csproj
├── Pages
│   ├── Error.cshtml
│   ├── Error.cshtml.cs
│   ├── Index.cshtml
│   ├── Index.cshtml.cs
│   ├── Privacy.cshtml
│   ├── Privacy.cshtml.cs
│   ├── Shared
│   ├── _ViewImports.cshtml
│   └── _ViewStart.cshtml
├── Program.cs
├── Properties
│   └── launchSettings.json
├── README.md
├── Startup.cs
├── app.db
├── appsettings.Development.json
├── appsettings.json
├── bin
│   └── Debug
├── obj
│   ├── Debug
│   ├── IndividualAuthReference.csproj.nuget.dgspec.json
│   ├── IndividualAuthReference.csproj.nuget.g.props
│   ├── IndividualAuthReference.csproj.nuget.g.targets
│   ├── project.assets.json
│   └── project.nuget.cache
├── tree.txt
└── wwwroot
    ├── css
    ├── favicon.ico
    ├── js
    └── lib
```

## Database Migration

```
$ dotnet ef database update
Build started...
Build succeeded.
Done.
```

## Edit Authentication Config

```C#k
//!HERE START
      services.Configure<IdentityOptions>(options =>
      {
        // Password settings
        options.Password.RequireDigit = true;
        options.Password.RequireLowercase = true;
        options.Password.RequireNonAlphanumeric = true;
        options.Password.RequireUppercase = true;
        options.Password.RequiredLength = 6;
        options.Password.RequiredUniqueChars = 1;

        // Lockout settings
        options.Lockout.DefaultLockoutTimeSpan = TimeSpan.FromMinutes(5);
        options.Lockout.MaxFailedAccessAttempts = 5;
        options.Lockout.AllowedForNewUsers = true;

        // User settings
        options.User.AllowedUserNameCharacters = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789-._@+";
        options.User.RequireUniqueEmail = false;
      });

      services.ConfigureApplicationCookie(options =>
      {
        // Cookie settings
        options.Cookie.HttpOnly = true;
        options.ExpireTimeSpan = TimeSpan.FromMinutes(5);
        options.LoginPath = "/Identity/Account/Login";
        options.AccessDeniedPath = "/Identity/Account/AccessDenied";
        options.SlidingExpiration = true;
      });
      //!HERE END
```

## start app

## register

## ca

## login

## check PersnalData

### Download

```json
{
  "Id": "bcf4ed63-a202-46d4-9b81-389c836d517a",
  "UserName": "asanobm@outlook.com",
  "Email": "asanobm@outlook.com",
  "EmailConfirmed": "True",
  "PhoneNumber": "null",
  "PhoneNumberConfirmed": "False",
  "TwoFactorEnabled": "False",
  "Authenticator Key": null
}
```

## Check your database.

# RegisterConfirmation

```
dotnet add package Microsoft.VisualStudio.Web.CodeGeneration.Design
dotnet aspnet-codegenerator identity -dc [Project name].Data.ApplicationDbContext --files "Account.Register;Account.Login;Account.Logout;Account.RegisterConfirmation"
```

```
dotnet add package Microsoft.VisualStudio.Web.CodeGeneration.Design
dotnet aspnet-codegenerator identity -dc IndividualAuthReference.Data.ApplicationDbContext --files "Account.Register;Account.Login;Account.Logout;Account.RegisterConfirmation"
```
