## File Structure
<img width="280" height="586" alt="image" src="https://github.com/user-attachments/assets/2a44651a-fb0a-43a0-a4fd-a4d31138ca0b" />

## Program.cs
```csharp
namespace Assign1
{
    public class Program
    {
        public static void Main(string[] args)
        {
            var builder = WebApplication.CreateBuilder(args);

            // Add services to the container.
            builder.Services.AddControllersWithViews();
            //for session
            builder.Services.AddDistributedMemoryCache();
            builder.Services.AddSession(Options =>
            {
                Options.IdleTimeout = TimeSpan.FromMinutes(20);
            });
            var app = builder.Build();

           

            // Configure the HTTP request pipeline.
            if (!app.Environment.IsDevelopment())
            {
                app.UseExceptionHandler("/Home/Error");
                // The default HSTS value is 30 days. You may want to change this for production scenarios, see https://aka.ms/aspnetcore-hsts.
                app.UseHsts();
            }

            app.UseHttpsRedirection();
            app.UseRouting();

            app.UseSession();

            app.UseAuthorization();

            app.MapStaticAssets();
            app.MapControllerRoute(
                name: "default",
                pattern: "{controller=Home}/{action=Index}/{id?}")
                .WithStaticAssets();

            app.Run();
        }
    }
}
```

HomeController.cs
```csharp
using System.Diagnostics;
using Assign1.Models;
using Microsoft.AspNetCore.Mvc;

namespace Assign1.Controllers
{
    public class HomeController : Controller
    {
        public IActionResult Index()
        {
            return View();
        }

        [HttpPost]
        public IActionResult SetSession(string uname, int age)
        {
            HttpContext.Session.SetString("uname", uname);
            HttpContext.Session.SetInt32("age", age);
            return RedirectToAction("GetSession", "User");
        }

    }
}
```

## UserController.cs
```csharp
using Microsoft.AspNetCore.Mvc;

namespace Assign1.Controllers
{
    public class UserController : Controller
    {
        [HttpGet]   
        public IActionResult GetSession()
        {
            ViewBag.username = HttpContext.Session.GetString("uname");
            ViewBag.age = HttpContext.Session.GetInt32("age");
            return View();
        }
    }
}
```

## Index.cshtml
```cshtml
@{
    ViewData["Title"] = "Home Page";
}
<form asp-controller="Home" asp-action="SetSession" method="post">
    Username: <input type="text" name="uname" />
    Age: <input type="number" name="age" />
    <input type="submit" value="Submit" />
</form>
```

## GetSession.cshtml
```cshtml
@*
    For more information on enabling MVC for empty projects, visit https://go.microsoft.com/fwlink/?LinkID=397860
*@
@{
}

<p>@ViewBag.username</p>
<p>@ViewBag.age</p>
```



