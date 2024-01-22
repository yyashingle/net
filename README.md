

1. Create New WebApplication ASP.NET Core WebAPI(MVC Controller)
  Click ->Next
2.Untick Https

3.Click Create

4.In Models->Add Class (Entity Name)(eg:Fruit) Add all attributes with Properties

5.Dependencies Download
  Tools-> Manage NugetPackages for solutins
  click on Browse
  DownLoad Dependencies
  I.EntityFrameWorkCore
  II. EntityFrameWorkCore.Tools
  III.EntityFrameWorkCore.sqlServer
  IV.Microsoft.Data.sqlClient

6.Create Context Folder in solution
  in that Add class name accordingly(ex:FruitContext)

  write class like this:

 public class FruitContext:DbContext
 {
     public FruitContext(DbContextOptions<FruitContext> options): base(options)
     {
         
     }

     public DbSet<Fruit> fruits { get; set; }
 }

7.In AppSetting.Json

"ConnectionStrings": {
  "FruitContext": "string will be youe local MSSQL String"
}

Add Above Connection String Object

8.In Program.cs

add DI like this:

builder.Services.AddDbContext<FruitContext>(options =>
options.UseSqlServer(builder.Configuration.GetConnectionString("FruitContext")));

9. Tools->NugetPackageManager->Package Manager Console

Run Command-> Add-Migration "Initial migration"

after build Success..

Run Commane-> Update-Database

After build Success.. 

10.Add new Controller in Controller Folder named as(Eg:FruitsControlller)

choose-> MVC Controller with Views using EntityFramework

Choose Model Class as ->Fruit.cs

choose DBContext class as-> FruitDbContext

Click ->Add
(Controller will genrate in some time)
after succesfull generation....


11.In Program.cs

in Default Controlller chnage Home to Fruits(your Controller name)

12.Run solution


 
