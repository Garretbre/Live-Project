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
