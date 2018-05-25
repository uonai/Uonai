---
layout: post
title: "Aggregating JSON Feeds From Multiple Systems"
comments: true
description: "Aggregating JSON Feeds From Multiple Systems"
keywords: "Aggregating JSON Feeds From Multiple Systems"
categories:
- Projects
---

Last month I solved a problem World Bicycle Relief was struggling with for a long time -- integrating all of our international donation feeds into one single feed to show the impact with a campaign.

Generally when we launch a campaign, it starts as a US initiative and gradually changes into an international initiative that accepts currencies throughout Europe. We'd had now way to show that until now.

The landing page is here: [https://worldbicyclerelief.org/en/cyclofemme/](https://worldbicyclerelief.org/en/cyclofemme/)
The technologies used on the page are:
* Javascript & JQuery
* HTML
* CSS
* PHP
* JSON
* Feeds from Various Platforms (Causevox + Altruja)

The code looks like this. When it runs, it loops into each individual JSON endpoint and pulls the funds raised. We then divide this number by the amount of bikes this produces for each currency. This number is populated on the page. The final step is taking this number and running it up to a grand total. 

```
$(function () {
    $.when(
      //this is for US microsite
        $.ajax({
            dataType: "jsonp",
            url: "https://cyclofemme.causevox.com/api_endpoint/info",
            success: function (data) {
              console.log(data);
                var campaignfirst =Math.round(data.funds_raised);
                $(".campaignfirst").html(campaignfirst);
            }
        }),
  //this is for UK team within UK microsite
        $.ajax({
            dataType: "jsonp",
            url: "https://worldbicyclereliefuk.causevox.com/api_endpoint/teams",
            success: function (data) {
              console.log(data);
                var campaignsecond = Math.round(data[6].funds_raised);
                $(".campaignsecond").html(campaignsecond);
            }
    
        }),
  //this is for Altruja Team within Altruja page
         $.ajax({
            dataType: "jsonp",
            url: "https://www.altruja.de/api/page/YG1A?details=1&num=10&ort=1&callback",
            success: function (data) {

              console.log(data);
		var altrujaFundraiser = data.page.collected.replace(/\./g,'').slice(0,-2);
                //var altrujaFundraiser = data.page.collected.replace(/\./g,'').slice(0, -3);
                $(".altrujaFundraiser").html(altrujaFundraiser);
            }
        }),
//this is for Canada team within Canada microsite
           $.ajax({
            dataType: "jsonp",
            url: "https://fundraisecanada.causevox.com/api_endpoint/teams",
            success: function (data) {

              console.log(data);

                var teamCanada = parseInt(data[8].funds_raised);
                $(".teamCanada").html(teamCanada);
            }
        }),
//this is for Australia team within Australia microsite
          $.ajax({
            dataType: "jsonp",
            url: "https://fundraiseau.causevox.com/api_endpoint/teams",
            success: function (data) {

              console.log(data);

                var teamAustralia = parseInt(data[0].funds_raised);
                $(".teamAustralia").html(teamAustralia);
            }
        })

//assign the above three functions as a, b, and c. from there, they are referenced in the
    ).done(function (a, b, c, d, e) {
        var total = +Math.round(a[0].funds_raised / 147) + +Math.round(b[0][6].funds_raised / 95)  + +Math.round(c[0].page.collected.replace(/\./g,'').slice(0, -2) / 100) + +Math.round(d[0][8].funds_raised / 147) +Math.round(e[0][0].funds_raised / 195)
        $('.ticker').append(total);
    });
});
```








