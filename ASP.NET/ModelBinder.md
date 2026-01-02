## File Structure
<img width="227" height="649" alt="image" src="https://github.com/user-attachments/assets/f13b60d9-9955-49a2-ab5d-84d57b2d7344" />


## Program.cs
```csharp
namespace ModelBinder
{
    public class Program
    {
        public static void Main(string[] args)
        {
            var builder = WebApplication.CreateBuilder(args);

            // Add services to the container.
            builder.Services.AddControllersWithViews();

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

            app.UseAuthorization();

            app.MapStaticAssets();
            app.MapControllerRoute(
                name: "default",
                pattern: "{controller=Home}/{action=Create}/{id?}")
                .WithStaticAssets();

            app.Run();
        }
    }
}
```

## Class.cs
```csharp
namespace ModelBinder.Models
{
    public class Student
    {
        public int Id { get; set; }
        public string Name { get; set; }
        public int Age { get; set; }
    }
}
```

## HomeController.cs
```csharp
using System.Diagnostics;
using Microsoft.AspNetCore.Mvc;
using ModelBinder.Models;

namespace ModelBinder.Controllers
{
    public class HomeController : Controller
    {
        public IActionResult Create()
        {
            return View();
        }

        [HttpPost]
        public IActionResult Create(Student student)
        {
            return Content("Name= " + student.Name + ", " + "Age= " + student.Age);
        }

        public IActionResult Privacy()
        {
            return View();
        }

        
    }
}
```

## Create.cshtml
```cshtml
@*
    For more information on enabling MVC for empty projects, visit https://go.microsoft.com/fwlink/?LinkID=397860
*@

@page
@model ModelBinder.Models.Student
@{

    <h2>Student Form</h2>

    @using (Html.BeginForm())
    {
        <label>Name:</label>
        @Html.TextBoxFor(m => m.Name)
        <br/><br/>

        <label>Age:</label>
        @Html.TextBoxFor(m => m.Age)
        <br />
        <br />

        <input type="submit" value="Submit" />

    }
}
```
