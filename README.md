# Live-Project
C# and .Net- 2 week live project 

I received a story to change the reponsiveness of specific images. Using the inspect feature on the internet browser I was able to find where in the CSS code to change the varying sizes of screen. 

~~~/*Adding CSS for Theatre Vertigo About page*/
.aboutPage-Card {
    display: inline-flex;
    flex-wrap: wrap;
    width: auto;
    height: auto;
}
.aboutPage-Card-Img {
    display: flex;
    width: auto;
    max-width: 100%;
    height: 75%;
    object-fit: cover;
}
}
.aboutPage-Card-Text {
    height: 25%;
    text-align: center;
    word-break:break-word;
    color: var(--light-color);
}
/*Created @media at 3 different screen sizes to check work and customize at each layer*/
/*This @media will apply when the screen is sized below 992px*/
@media screen and (max-width: 992px) {
    .aboutPage-Card-Img {
        display: flex;
        width: auto;
        height: 60%;  
    }
    .aboutPage-Card-Text {
        height: 40%;
        text-align: center;
        word-break: break-word;
        color: var(--light-color);
    }
}
/*This @media will apply when the screen is sized below 767px*/
@media screen and (max-width: 767px) {
    .aboutPage-Card-Img {
        display: flex;
        width: auto;
        height: 40%;
    }
    .aboutPage-Card-Text {
        height: 60%;
        text-align: center;
        word-break: break-word;
        color: var(--light-color);
    }
}
/*This @media will apply when the screen is sized below 576px*/
@media screen and (max-width: 577px) {
    .aboutPage-Card-Img {
        display: flex;
        width: 100%;
        height: 60%;
    }
    .aboutPage-Card-Text {
        height: 40%;
        text-align: center;
        word-break: break-word;
        color: var(--light-color);
    }
}
.aboutPage-History {
    text-align: left;
    color: var(--light-color);
About.cshtml
-3+2
/TheatreCMS3/Views/Home/About.cshtml
View
  <p>We seek to engage audiences through compelling, ensemble-driven productions<br /> with a focus on developing new works.</p>
</div>
<div>
@*Align center is keeping aboutPage-Card images centered on the screens instead of the Card bodies moving right or left.*@
<div align="center">
  <h1 class="aboutPage-h1">Ensemble</h1>
  <div class="card-deck">
    <div class="card aboutPage-Card">
      <img class="card-img-top aboutPage-Card-Img"  src="@Url.Content("~/Content/images/Cast_Img_1.jpg")" alt="Kaia Maarja Hillier">
      <div class="card-body aboutPage-Card-Bdy">
      </div>
    </div>
</div>
</div>
~~~



Personally I had not coded a CRUD page before. Truly a great experiance. I tried to code on my own, then I asked my teammates and instructors. To achieve finishing my story on time and debugged. I enjoyed the team experiance and how many coding skills I got to learn in 2 weeks time. A highlight of my Tech Academy experiance.



~~~using System;
using System.Collections.Generic;
using System.Data;
using System.Data.Entity;
using System.Linq;
using System.Net;
using System.Web;
using System.Web.Mvc;
using TheatreCMS3.Areas.Rent.Models;
using TheatreCMS3.Models;
namespace TheatreCMS3.Areas.Rent.Controllers
{
    public class RentalsController : Controller
    {
        private ApplicationDbContext db = new ApplicationDbContext();
        // GET: Rent/Rentals
        public ActionResult Index()
        {
            return View(db.Rentals.ToList());
        }
        // GET: Rent/Rentals/Details/5
        public ActionResult Details(int? id)
        {
            if (id == null)
            {
                return new HttpStatusCodeResult(HttpStatusCode.BadRequest);
            }
            Rental rental = db.Rentals.Find(id);
            if (rental == null)
            {
                return HttpNotFound();
            }
            return View(rental);
        }
        // GET: Rent/Rentals/Create
        public ActionResult Create()
        {
            return View();
        }
        // POST: Rent/Rentals/Create
        // To protect from overposting attacks, enable the specific properties you want to bind to, for 
        // more details see https://go.microsoft.com/fwlink/?LinkId=317598.
        [HttpPost]
        [ValidateAntiForgeryToken]
        public ActionResult Create([Bind(Include = "RentalID,RentalName,RentalCost,FlawsAndDamages")] Rental rental)
        {
            if (ModelState.IsValid)
            {
                db.Rentals.Add(rental);
                db.SaveChanges();
                return RedirectToAction("Index");
            }
            return View(rental);
        }
        // GET: Rent/Rentals/Edit/5
        public ActionResult Edit(int? id)
        {
            if (id == null)
            {
                return new HttpStatusCodeResult(HttpStatusCode.BadRequest);
            }
            Rental rental = db.Rentals.Find(id);
            if (rental == null)
            {
                return HttpNotFound();
            }
            return View(rental);
        }
        // POST: Rent/Rentals/Edit/5
        // To protect from overposting attacks, enable the specific properties you want to bind to, for 
        // more details see https://go.microsoft.com/fwlink/?LinkId=317598.
        [HttpPost]
        [ValidateAntiForgeryToken]
        public ActionResult Edit([Bind(Include = "RentalID,RentalName,RentalCost,FlawsAndDamages")] Rental rental)
        {
            if (ModelState.IsValid)
            {
                db.Entry(rental).State = EntityState.Modified;
                db.SaveChanges();
                return RedirectToAction("Index");
            }
            return View(rental);
        }
        // GET: Rent/Rentals/Delete/5
        public ActionResult Delete(int? id)
        {
            if (id == null)
            {
                return new HttpStatusCodeResult(HttpStatusCode.BadRequest);
            }
            Rental rental = db.Rentals.Find(id);
            if (rental == null)
            {
                return HttpNotFound();
            }
            return View(rental);
        }
        // POST: Rent/Rentals/Delete/5
        [HttpPost, ActionName("Delete")]
        [ValidateAntiForgeryToken]
        public ActionResult DeleteConfirmed(int id)
        {
            Rental rental = db.Rentals.Find(id);
            db.Rentals.Remove(rental);
            db.SaveChanges();
            return RedirectToAction("Index");
        }
        protected override void Dispose(bool disposing)
        {
            if (disposing)
            {
                db.Dispose();
            }
            base.Dispose(disposing);
        }
    }
}
Rental Equipment.cs
+15
/TheatreCMS3/Areas/Rent/Models/Rental Equipment.cs
View
using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
namespace TheatreCMS3.Areas.Rent.Models
{
    public class RentalEquipment : Rental
    {
        public bool ChokingHazard { get; set; }
        public bool SuffocationHazard { get; set; }
        public int PurchasePrice { get; set; }
    }
}
Rental.cs
+18
/TheatreCMS3/Areas/Rent/Models/Rental.cs
View
using System;
using System.Collections.Generic;
using System.ComponentModel.DataAnnotations;
using System.Linq;
using System.Web;
namespace TheatreCMS3.Areas.Rent.Models
{
    public class Rental
    {
        [Key]
        public int RentalID { get; set; }
        public string RentalName { get; set; }
        public int RentalCost { get; set; }
        public string FlawsAndDamages { get; set; }
    }
}
RentalRoom.cs
+15
/TheatreCMS3/Areas/Rent/Models/RentalRoom.cs
View
using System;
using System.Collections.Generic;
using System.Linq;
using System.Web;
namespace TheatreCMS3.Areas.Rent.Models
{
    public class RentalRoom
    {
        public int RoomNumber { get; set; }
        public int SquareFootage { get; set; }
        public int MaxOccupancy { get; set; }
    }
}
Create.cshtml
+57
/TheatreCMS3/Areas/Rent/Views/Rentals/Create.cshtml
View
@model TheatreCMS3.Areas.Rent.Models.Rental
@{
    ViewBag.Title = "Create";
}
<h2>Create</h2>
@using (Html.BeginForm()) 
{
    @Html.AntiForgeryToken()
    
    <div class="form-horizontal">
        <h4>Rental</h4>
        <hr />
        @Html.ValidationSummary(true, "", new { @class = "text-danger" })
        <div class="form-group">
            @Html.LabelFor(model => model.RentalName, htmlAttributes: new { @class = "control-label col-md-2" })
            <div class="col-md-10">
                @Html.EditorFor(model => model.RentalName, new { htmlAttributes = new { @class = "form-control" } })
                @Html.ValidationMessageFor(model => model.RentalName, "", new { @class = "text-danger" })
            </div>
        </div>
        <div class="form-group">
            @Html.LabelFor(model => model.RentalCost, htmlAttributes: new { @class = "control-label col-md-2" })
            <div class="col-md-10">
                @Html.EditorFor(model => model.RentalCost, new { htmlAttributes = new { @class = "form-control" } })
                @Html.ValidationMessageFor(model => model.RentalCost, "", new { @class = "text-danger" })
            </div>
        </div>
        <div class="form-group">
            @Html.LabelFor(model => model.FlawsAndDamages, htmlAttributes: new { @class = "control-label col-md-2" })
            <div class="col-md-10">
                @Html.EditorFor(model => model.FlawsAndDamages, new { htmlAttributes = new { @class = "form-control" } })
                @Html.ValidationMessageFor(model => model.FlawsAndDamages, "", new { @class = "text-danger" })
            </div>
        </div>
        <div class="form-group">
            <div class="col-md-offset-2 col-md-10">
                <input type="submit" value="Create" class="btn btn-default" />
            </div>
        </div>
    </div>
}
<div>
    @Html.ActionLink("Back to List", "Index")
</div>
@section Scripts {
    @Scripts.Render("~/bundles/jqueryval")
}
Delete.cshtml
+49
/TheatreCMS3/Areas/Rent/Views/Rentals/Delete.cshtml
View
@model TheatreCMS3.Areas.Rent.Models.Rental
@{
    ViewBag.Title = "Delete";
}
<h2>Delete</h2>
<h3>Are you sure you want to delete this?</h3>
<div>
    <h4>Rental</h4>
    <hr />
    <dl class="dl-horizontal">
        <dt>
            @Html.DisplayNameFor(model => model.RentalName)
        </dt>
        <dd>
            @Html.DisplayFor(model => model.RentalName)
        </dd>
        <dt>
            @Html.DisplayNameFor(model => model.RentalCost)
        </dt>
        <dd>
            @Html.DisplayFor(model => model.RentalCost)
        </dd>
        <dt>
            @Html.DisplayNameFor(model => model.FlawsAndDamages)
        </dt>
        <dd>
            @Html.DisplayFor(model => model.FlawsAndDamages)
        </dd>
    </dl>
    @using (Html.BeginForm()) {
        @Html.AntiForgeryToken()
        <div class="form-actions no-color">
            <input type="submit" value="Delete" class="btn btn-default" /> |
            @Html.ActionLink("Back to List", "Index")
        </div>
    }
</div>
Details.cshtml
+43
/TheatreCMS3/Areas/Rent/Views/Rentals/Details.cshtml
View
@model TheatreCMS3.Areas.Rent.Models.Rental
@{
    ViewBag.Title = "Details";
}
<h2>Details</h2>
<div>
    <h4>Rental</h4>
    <hr />
    <dl class="dl-horizontal">
        <dt>
            @Html.DisplayNameFor(model => model.RentalName)
        </dt>
        <dd>
            @Html.DisplayFor(model => model.RentalName)
        </dd>
        <dt>
            @Html.DisplayNameFor(model => model.RentalCost)
        </dt>
        <dd>
            @Html.DisplayFor(model => model.RentalCost)
        </dd>
        <dt>
            @Html.DisplayNameFor(model => model.FlawsAndDamages)
        </dt>
        <dd>
            @Html.DisplayFor(model => model.FlawsAndDamages)
        </dd>
    </dl>
</div>
<p>
    @Html.ActionLink("Edit", "Edit", new { id = Model.RentalID }) |
    @Html.ActionLink("Back to List", "Index")
</p>
Edit.cshtml
+59
/TheatreCMS3/Areas/Rent/Views/Rentals/Edit.cshtml
View
@model TheatreCMS3.Areas.Rent.Models.Rental
@{
    ViewBag.Title = "Edit";
}
<h2>Edit</h2>
@using (Html.BeginForm())
{
    @Html.AntiForgeryToken()
    
    <div class="form-horizontal">
        <h4>Rental</h4>
        <hr />
        @Html.ValidationSummary(true, "", new { @class = "text-danger" })
        @Html.HiddenFor(model => model.RentalID)
        <div class="form-group">
            @Html.LabelFor(model => model.RentalName, htmlAttributes: new { @class = "control-label col-md-2" })
            <div class="col-md-10">
                @Html.EditorFor(model => model.RentalName, new { htmlAttributes = new { @class = "form-control" } })
                @Html.ValidationMessageFor(model => model.RentalName, "", new { @class = "text-danger" })
            </div>
        </div>
        <div class="form-group">
            @Html.LabelFor(model => model.RentalCost, htmlAttributes: new { @class = "control-label col-md-2" })
            <div class="col-md-10">
                @Html.EditorFor(model => model.RentalCost, new { htmlAttributes = new { @class = "form-control" } })
                @Html.ValidationMessageFor(model => model.RentalCost, "", new { @class = "text-danger" })
            </div>
        </div>
        <div class="form-group">
            @Html.LabelFor(model => model.FlawsAndDamages, htmlAttributes: new { @class = "control-label col-md-2" })
            <div class="col-md-10">
                @Html.EditorFor(model => model.FlawsAndDamages, new { htmlAttributes = new { @class = "form-control" } })
                @Html.ValidationMessageFor(model => model.FlawsAndDamages, "", new { @class = "text-danger" })
            </div>
        </div>
        <div class="form-group">
            <div class="col-md-offset-2 col-md-10">
                <input type="submit" value="Save" class="btn btn-default" />
            </div>
        </div>
    </div>
}
<div>
    @Html.ActionLink("Back to List", "Index")
</div>
@section Scripts {
    @Scripts.Render("~/bundles/jqueryval")
}
Index.cshtml
+46
/TheatreCMS3/Areas/Rent/Views/Rentals/Index.cshtml
View
@model IEnumerable<TheatreCMS3.Areas.Rent.Models.Rental>
@{
    ViewBag.Title = "Index";
}
<h2>Index</h2>
<p>
    @Html.ActionLink("Create New", "Create")
</p>
<table class="table">
    <tr>
        <th>
            @Html.DisplayNameFor(model => model.RentalName)
        </th>
        <th>
            @Html.DisplayNameFor(model => model.RentalCost)
        </th>
        <th>
            @Html.DisplayNameFor(model => model.FlawsAndDamages)
        </th>
        <th></th>
    </tr>
@foreach (var item in Model) {
    <tr>
        <td>
            @Html.DisplayFor(modelItem => item.RentalName)
        </td>
        <td>
            @Html.DisplayFor(modelItem => item.RentalCost)
        </td>
        <td>
            @Html.DisplayFor(modelItem => item.FlawsAndDamages)
        </td>
        <td>
            @Html.ActionLink("Edit", "Edit", new { id=item.RentalID }) |
            @Html.ActionLink("Details", "Details", new { id=item.RentalID }) |
            @Html.ActionLink("Delete", "Delete", new { id=item.RentalID })
        </td>
    </tr>
}
</table>
IdentityModels.cs
-1+3
/TheatreCMS3/Models/IdentityModels.cs
View
        public System.Data.Entity.DbSet<TheatreCMS3.Areas.Blog.Models.BlogPost> BlogPosts { get; set; }
        public System.Data.Entity.DbSet<TheatreCMS3.Areas.Rent.Models.RentalSurvey> RentalSurveys { get; set; }
        public System.Data.Entity.DbSet<TheatreCMS3.Areas.Prod.Models.ProductionPhoto> ProductionPhotos { get; set; }
        public System.Data.Entity.DbSet<TheatreCMS3.Areas.Rent.Models.Rental> Rentals { get; set; }
        public System.Data.Entity.DbSet<TheatreCMS3.Areas.Rent.Models.RentalRequest> RentalRequests { get; set; }
        public System.Data.Entity.DbSet<TheatreCMS3.Areas.Rent.Models.RentalRequest> RentalRequests { get; set; }
        
    }
}
_Navbar.cshtml
-1+1
/TheatreCMS3/Views/Shared/_Navbar.cshtml
View
				</a>
                <div class="dropdown-menu dropdownbckgrndclr" aria-labelledby="navbarDropdownMenuLink">
                    @Html.ActionLink("Rental Requests", "Index", "RentalRequests", new { Area = "Rent" }, new { @class = "dropdown-item dropdowntxt" })
                    @Html.ActionLink("Rental", "Index", "Rental", new { Area = "Rent" }, new { @class = "dropdown-item dropdowntxt disabled" })
                    @Html.ActionLink("Rental", "Index", "Rentals", new { Area = "Rent" }, new { @class = "dropdown-item dropdowntxt" })
                    @Html.ActionLink("Rental History", "Index", "RentalHistory", new { Area = "Rent" }, new { @class = "dropdown-item dropdowntxt disabled" })
                    @Html.ActionLink("Rental Survey", "Index", "RentalSurvey", new { Area = "Rent" }, new { @class = "dropdown-item dropdowntxt disabled" })
                </div>
TheatreCMS3.csproj
+9
/TheatreCMS3/TheatreCMS3.csproj
View
    <Compile Include="Areas\Prod\Models\ProductionPhoto.cs" />
    <Compile Include="Areas\Prod\ProdAreaRegistration.cs" />
    <Compile Include="Areas\Rent\Controllers\RentalRequestsController.cs" />
    <Compile Include="Areas\Rent\Controllers\RentalsController.cs" />
    <Compile Include="Areas\Rent\Controllers\RentalSurveysController.cs" />
    <Compile Include="Areas\Rent\Models\RentalRoom.cs" />
    <Compile Include="Areas\Rent\Models\Rental Equipment.cs" />
    <Compile Include="Areas\Rent\Models\Rental.cs" />
    <Compile Include="Areas\Rent\Models\RentalRequest.cs" />
    <Compile Include="Areas\Rent\Models\RentalSurvey.cs" />
    <Compile Include="Areas\Rent\RentAreaRegistration.cs" />
    <Content Include="Content\bootstrap-reboot.css.map" />
    <Content Include="Content\bootstrap-grid.min.css.map" />
    <Content Include="Content\bootstrap-grid.css.map" />
    <Content Include="Areas\Rent\Views\Rentals\Create.cshtml" />
    <Content Include="Areas\Rent\Views\Rentals\Delete.cshtml" />
    <Content Include="Areas\Rent\Views\Rentals\Details.cshtml" />
    <Content Include="Areas\Rent\Views\Rentals\Edit.cshtml" />
    <Content Include="Areas\Rent\Views\Rentals\Index.cshtml" />
    <None Include="Scripts\jquery-3.5.1.intellisense.js" />
    <Content Include="Scripts\jquery-3.5.1.js" />
    <Content Include="Scripts\jquery-3.5.1.min.js" />
~~~
