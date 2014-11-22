---
layout: post
categories: blog
tags: [medical misconduct, rCharts, ggplot2]
preview_pic: /assets/images/2014-07-09-medical-misconduct-ggplot2.png
comments: true
title: Medical Misconduct - Introduction & Time-Series Plots
---

This is part of the "Medical Misconduct" series in collaboration with [Frank Chen](http://frankchen07.github.io) in which we explore the [Professional Medical Conduct Board Actions](https://health.data.ny.gov/Health/Professional-Medical-Conduct-Board-Actions-Beginni/ebmi-8ctw) data set on [health.data.ny.gov](http://health.data.ny.gov).

## Introduction

If you have ever taken a ride on an NYC subway, chances are you've seen this hilarious advertisement:

<img src = "/assets/images/2014-07-09-medical-misconduct-drz.png" class = "fullw">

As funny as this may be, did you know that the New York State Department of Health has taken disciplinary action against Dr. Zizmor... twice?

Thanks to New York State Public Health Law [Section 230](https://www.health.ny.gov/professionals/doctors/conduct/laws.htm), all physicians who have had disciplinary action taken against them are placed on an "offender's list" that is open to the public. Acts of medical misconduct may range from negligence in care to sexual abuse to grand larceny. Unfortunately, this list is not very accessible on NYS Department of Health's [website](http://w3.health.state.ny.us/opmc/factions.nsf/physiciansearch?openform).

<img src = "/assets/images/2014-07-09-medical-misconduct-1.png" class = "fullw">

With the open data movement putting the power of information directly into the people's hands (check out [IQuantNY](http://iquantny.tumblr.com/)'s Tumblr for more fun), my collaborator Frank and I decided it was time to join the fray and tell the data-driven story of doctors behaving badly. 

## Time-Series Plots

### Loading Data

You can find the open dataset on Professional Medical Conduct Board Actions on [health.data.ny.gov](https://health.data.ny.gov/Health/Professional-Medical-Conduct-Board-Actions-Beginni/ebmi-8ctw?category=Health&view_name=Professional-Medical-Conduct-Board-Actions-Beginni).

<script src="https://gist.github.com/rcquan/f05a235a84321896386c.js"></script>

### Pre-Processing and Feature Selection

`Effective.Date` is a feature in the dataset that denotes the date on which the board action against the physician took effect. Since disciplinary actions must be authorized, the frequency of this variable in the dataset can be used to determine the number of physicians disciplined on a daily, monthly, and yearly interval. To make use of this variable, we convert it to the 
date class.

<script src="https://gist.github.com/rcquan/7122c5ad7bcb1440e6ff.js"></script>

### Static Visualization

Our first set of visualizations will simply track the number of physcians disciplined by the New York State Department of Health from 1990-2013.

<script src="https://gist.github.com/rcquan/b8b4f9cf58b6343f648b.js"></script>

<img src = "/assets/images/2014-07-09-medical-misconduct-ggplot2.png" class = "halfw">

### Interactive Visualization

I really wanted to practice making interactive charts with the 
`rCharts` library. `rCharts` supports multiple javascript charting libraries and allows one to build beautiful graphs all within R - no javascript knowledge required (although highly recommended if one wants better customization). The code below uses `morris.js` to display the same graph above with the exception of being able to see the frequency of disciplinary actions at each month upon hover.

<script src="https://gist.github.com/rcquan/5aa0ab1475fb57c2d36d.js"></script>

<link rel='stylesheet' href=http://cdn.oesmith.co.uk/morris-0.4.2.min.css>

<script type='text/javascript' src=http://ajax.googleapis.com/ajax/libs/jquery/1.9.0/jquery.min.js></script>

<script type='text/javascript' src=http://cdnjs.cloudflare.com/ajax/libs/raphael/2.1.0/raphael-min.js></script>

<script type='text/javascript' src=http://cdn.oesmith.co.uk/morris-0.4.2.min.js></script> 

<p><style>
  .rChart {
    display: block;
    margin-left: auto; 
    margin-right: auto;
    width: 600px;
    height: 400px;
  }<br/>
  </style></p>

<div id = 'chart1' class = 'rChart morris'></div>

<script type='text/javascript'>
    var chartParams = {
 "element": "chart1",
"width":            600,
"height":            400,
"xkey": "Month",
"ykeys": [
 "MedicalMisconductCount" 
],
"data": [
 {
 "Month": "Jan 1990",
"MedicalMisconductCount": 3 
},
{
 "Month": "Feb 1990",
"MedicalMisconductCount": 10 
},
{
 "Month": "Mar 1990",
"MedicalMisconductCount": 5 
},
{
 "Month": "Apr 1990",
"MedicalMisconductCount": 13 
},
{
 "Month": "May 1990",
"MedicalMisconductCount": 7 
},
{
 "Month": "Jun 1990",
"MedicalMisconductCount": 7 
},
{
 "Month": "Jul 1990",
"MedicalMisconductCount": 10 
},
{
 "Month": "Aug 1990",
"MedicalMisconductCount": 13 
},
{
 "Month": "Sep 1990",
"MedicalMisconductCount": 1 
},
{
 "Month": "Oct 1990",
"MedicalMisconductCount": 10 
},
{
 "Month": "Nov 1990",
"MedicalMisconductCount": 9 
},
{
 "Month": "Dec 1990",
"MedicalMisconductCount": 9 
},
{
 "Month": "Jan 1991",
"MedicalMisconductCount": 3 
},
{
 "Month": "Feb 1991",
"MedicalMisconductCount": 7 
},
{
 "Month": "Mar 1991",
"MedicalMisconductCount": 10 
},
{
 "Month": "Apr 1991",
"MedicalMisconductCount": 3 
},
{
 "Month": "May 1991",
"MedicalMisconductCount": 6 
},
{
 "Month": "Jun 1991",
"MedicalMisconductCount": 6 
},
{
 "Month": "Jul 1991",
"MedicalMisconductCount": 2 
},
{
 "Month": "Aug 1991",
"MedicalMisconductCount": 5 
},
{
 "Month": "Sep 1991",
"MedicalMisconductCount": 5 
},
{
 "Month": "Oct 1991",
"MedicalMisconductCount": 4 
},
{
 "Month": "Nov 1991",
"MedicalMisconductCount": 11 
},
{
 "Month": "Dec 1991",
"MedicalMisconductCount": 12 
},
{
 "Month": "Jan 1992",
"MedicalMisconductCount": 10 
},
{
 "Month": "Feb 1992",
"MedicalMisconductCount": 4 
},
{
 "Month": "Mar 1992",
"MedicalMisconductCount": 8 
},
{
 "Month": "Apr 1992",
"MedicalMisconductCount": 12 
},
{
 "Month": "May 1992",
"MedicalMisconductCount": 6 
},
{
 "Month": "Jun 1992",
"MedicalMisconductCount": 5 
},
{
 "Month": "Jul 1992",
"MedicalMisconductCount": 8 
},
{
 "Month": "Aug 1992",
"MedicalMisconductCount": 8 
},
{
 "Month": "Sep 1992",
"MedicalMisconductCount": 7 
},
{
 "Month": "Oct 1992",
"MedicalMisconductCount": 10 
},
{
 "Month": "Nov 1992",
"MedicalMisconductCount": 13 
},
{
 "Month": "Dec 1992",
"MedicalMisconductCount": 14 
},
{
 "Month": "Jan 1993",
"MedicalMisconductCount": 10 
},
{
 "Month": "Feb 1993",
"MedicalMisconductCount": 14 
},
{
 "Month": "Mar 1993",
"MedicalMisconductCount": 18 
},
{
 "Month": "Apr 1993",
"MedicalMisconductCount": 10 
},
{
 "Month": "May 1993",
"MedicalMisconductCount": 15 
},
{
 "Month": "Jun 1993",
"MedicalMisconductCount": 10 
},
{
 "Month": "Jul 1993",
"MedicalMisconductCount": 15 
},
{
 "Month": "Aug 1993",
"MedicalMisconductCount": 25 
},
{
 "Month": "Sep 1993",
"MedicalMisconductCount": 16 
},
{
 "Month": "Oct 1993",
"MedicalMisconductCount": 15 
},
{
 "Month": "Nov 1993",
"MedicalMisconductCount": 24 
},
{
 "Month": "Dec 1993",
"MedicalMisconductCount": 9 
},
{
 "Month": "Jan 1994",
"MedicalMisconductCount": 16 
},
{
 "Month": "Feb 1994",
"MedicalMisconductCount": 16 
},
{
 "Month": "Mar 1994",
"MedicalMisconductCount": 16 
},
{
 "Month": "Apr 1994",
"MedicalMisconductCount": 6 
},
{
 "Month": "May 1994",
"MedicalMisconductCount": 12 
},
{
 "Month": "Jun 1994",
"MedicalMisconductCount": 19 
},
{
 "Month": "Jul 1994",
"MedicalMisconductCount": 22 
},
{
 "Month": "Aug 1994",
"MedicalMisconductCount": 31 
},
{
 "Month": "Sep 1994",
"MedicalMisconductCount": 30 
},
{
 "Month": "Oct 1994",
"MedicalMisconductCount": 24 
},
{
 "Month": "Nov 1994",
"MedicalMisconductCount": 18 
},
{
 "Month": "Dec 1994",
"MedicalMisconductCount": 23 
},
{
 "Month": "Jan 1995",
"MedicalMisconductCount": 22 
},
{
 "Month": "Feb 1995",
"MedicalMisconductCount": 30 
},
{
 "Month": "Mar 1995",
"MedicalMisconductCount": 28 
},
{
 "Month": "Apr 1995",
"MedicalMisconductCount": 31 
},
{
 "Month": "May 1995",
"MedicalMisconductCount": 20 
},
{
 "Month": "Jun 1995",
"MedicalMisconductCount": 19 
},
{
 "Month": "Jul 1995",
"MedicalMisconductCount": 25 
},
{
 "Month": "Aug 1995",
"MedicalMisconductCount": 28 
},
{
 "Month": "Sep 1995",
"MedicalMisconductCount": 34 
},
{
 "Month": "Oct 1995",
"MedicalMisconductCount": 18 
},
{
 "Month": "Nov 1995",
"MedicalMisconductCount": 35 
},
{
 "Month": "Dec 1995",
"MedicalMisconductCount": 19 
},
{
 "Month": "Jan 1996",
"MedicalMisconductCount": 18 
},
{
 "Month": "Feb 1996",
"MedicalMisconductCount": 18 
},
{
 "Month": "Mar 1996",
"MedicalMisconductCount": 25 
},
{
 "Month": "Apr 1996",
"MedicalMisconductCount": 32 
},
{
 "Month": "May 1996",
"MedicalMisconductCount": 23 
},
{
 "Month": "Jun 1996",
"MedicalMisconductCount": 17 
},
{
 "Month": "Jul 1996",
"MedicalMisconductCount": 29 
},
{
 "Month": "Aug 1996",
"MedicalMisconductCount": 16 
},
{
 "Month": "Sep 1996",
"MedicalMisconductCount": 30 
},
{
 "Month": "Oct 1996",
"MedicalMisconductCount": 26 
},
{
 "Month": "Nov 1996",
"MedicalMisconductCount": 30 
},
{
 "Month": "Dec 1996",
"MedicalMisconductCount": 23 
},
{
 "Month": "Jan 1997",
"MedicalMisconductCount": 29 
},
{
 "Month": "Feb 1997",
"MedicalMisconductCount": 11 
},
{
 "Month": "Mar 1997",
"MedicalMisconductCount": 26 
},
{
 "Month": "Apr 1997",
"MedicalMisconductCount": 24 
},
{
 "Month": "May 1997",
"MedicalMisconductCount": 24 
},
{
 "Month": "Jun 1997",
"MedicalMisconductCount": 30 
},
{
 "Month": "Jul 1997",
"MedicalMisconductCount": 24 
},
{
 "Month": "Aug 1997",
"MedicalMisconductCount": 25 
},
{
 "Month": "Sep 1997",
"MedicalMisconductCount": 15 
},
{
 "Month": "Oct 1997",
"MedicalMisconductCount": 23 
},
{
 "Month": "Nov 1997",
"MedicalMisconductCount": 33 
},
{
 "Month": "Dec 1997",
"MedicalMisconductCount": 43 
},
{
 "Month": "Jan 1998",
"MedicalMisconductCount": 29 
},
{
 "Month": "Feb 1998",
"MedicalMisconductCount": 15 
},
{
 "Month": "Mar 1998",
"MedicalMisconductCount": 10 
},
{
 "Month": "Apr 1998",
"MedicalMisconductCount": 14 
},
{
 "Month": "May 1998",
"MedicalMisconductCount": 20 
},
{
 "Month": "Jun 1998",
"MedicalMisconductCount": 22 
},
{
 "Month": "Jul 1998",
"MedicalMisconductCount": 31 
},
{
 "Month": "Aug 1998",
"MedicalMisconductCount": 32 
},
{
 "Month": "Sep 1998",
"MedicalMisconductCount": 27 
},
{
 "Month": "Oct 1998",
"MedicalMisconductCount": 22 
},
{
 "Month": "Nov 1998",
"MedicalMisconductCount": 29 
},
{
 "Month": "Dec 1998",
"MedicalMisconductCount": 37 
},
{
 "Month": "Jan 1999",
"MedicalMisconductCount": 17 
},
{
 "Month": "Feb 1999",
"MedicalMisconductCount": 23 
},
{
 "Month": "Mar 1999",
"MedicalMisconductCount": 15 
},
{
 "Month": "Apr 1999",
"MedicalMisconductCount": 17 
},
{
 "Month": "May 1999",
"MedicalMisconductCount": 23 
},
{
 "Month": "Jun 1999",
"MedicalMisconductCount": 21 
},
{
 "Month": "Jul 1999",
"MedicalMisconductCount": 43 
},
{
 "Month": "Aug 1999",
"MedicalMisconductCount": 30 
},
{
 "Month": "Sep 1999",
"MedicalMisconductCount": 26 
},
{
 "Month": "Oct 1999",
"MedicalMisconductCount": 15 
},
{
 "Month": "Nov 1999",
"MedicalMisconductCount": 25 
},
{
 "Month": "Dec 1999",
"MedicalMisconductCount": 38 
},
{
 "Month": "Jan 2000",
"MedicalMisconductCount": 24 
},
{
 "Month": "Feb 2000",
"MedicalMisconductCount": 32 
},
{
 "Month": "Mar 2000",
"MedicalMisconductCount": 31 
},
{
 "Month": "Apr 2000",
"MedicalMisconductCount": 29 
},
{
 "Month": "May 2000",
"MedicalMisconductCount": 29 
},
{
 "Month": "Jun 2000",
"MedicalMisconductCount": 21 
},
{
 "Month": "Jul 2000",
"MedicalMisconductCount": 15 
},
{
 "Month": "Aug 2000",
"MedicalMisconductCount": 26 
},
{
 "Month": "Sep 2000",
"MedicalMisconductCount": 25 
},
{
 "Month": "Oct 2000",
"MedicalMisconductCount": 24 
},
{
 "Month": "Nov 2000",
"MedicalMisconductCount": 33 
},
{
 "Month": "Dec 2000",
"MedicalMisconductCount": 29 
},
{
 "Month": "Jan 2001",
"MedicalMisconductCount": 22 
},
{
 "Month": "Feb 2001",
"MedicalMisconductCount": 27 
},
{
 "Month": "Mar 2001",
"MedicalMisconductCount": 24 
},
{
 "Month": "Apr 2001",
"MedicalMisconductCount": 25 
},
{
 "Month": "May 2001",
"MedicalMisconductCount": 29 
},
{
 "Month": "Jun 2001",
"MedicalMisconductCount": 16 
},
{
 "Month": "Jul 2001",
"MedicalMisconductCount": 15 
},
{
 "Month": "Aug 2001",
"MedicalMisconductCount": 24 
},
{
 "Month": "Sep 2001",
"MedicalMisconductCount": 25 
},
{
 "Month": "Oct 2001",
"MedicalMisconductCount": 27 
},
{
 "Month": "Nov 2001",
"MedicalMisconductCount": 39 
},
{
 "Month": "Dec 2001",
"MedicalMisconductCount": 36 
},
{
 "Month": "Jan 2002",
"MedicalMisconductCount": 40 
},
{
 "Month": "Feb 2002",
"MedicalMisconductCount": 22 
},
{
 "Month": "Mar 2002",
"MedicalMisconductCount": 26 
},
{
 "Month": "Apr 2002",
"MedicalMisconductCount": 29 
},
{
 "Month": "May 2002",
"MedicalMisconductCount": 60 
},
{
 "Month": "Jun 2002",
"MedicalMisconductCount": 20 
},
{
 "Month": "Jul 2002",
"MedicalMisconductCount": 20 
},
{
 "Month": "Aug 2002",
"MedicalMisconductCount": 40 
},
{
 "Month": "Sep 2002",
"MedicalMisconductCount": 26 
},
{
 "Month": "Oct 2002",
"MedicalMisconductCount": 34 
},
{
 "Month": "Nov 2002",
"MedicalMisconductCount": 19 
},
{
 "Month": "Dec 2002",
"MedicalMisconductCount": 20 
},
{
 "Month": "Jan 2003",
"MedicalMisconductCount": 20 
},
{
 "Month": "Feb 2003",
"MedicalMisconductCount": 28 
},
{
 "Month": "Mar 2003",
"MedicalMisconductCount": 39 
},
{
 "Month": "Apr 2003",
"MedicalMisconductCount": 24 
},
{
 "Month": "May 2003",
"MedicalMisconductCount": 25 
},
{
 "Month": "Jun 2003",
"MedicalMisconductCount": 23 
},
{
 "Month": "Jul 2003",
"MedicalMisconductCount": 21 
},
{
 "Month": "Aug 2003",
"MedicalMisconductCount": 34 
},
{
 "Month": "Sep 2003",
"MedicalMisconductCount": 25 
},
{
 "Month": "Oct 2003",
"MedicalMisconductCount": 32 
},
{
 "Month": "Nov 2003",
"MedicalMisconductCount": 37 
},
{
 "Month": "Dec 2003",
"MedicalMisconductCount": 36 
},
{
 "Month": "Jan 2004",
"MedicalMisconductCount": 14 
},
{
 "Month": "Feb 2004",
"MedicalMisconductCount": 25 
},
{
 "Month": "Mar 2004",
"MedicalMisconductCount": 26 
},
{
 "Month": "Apr 2004",
"MedicalMisconductCount": 37 
},
{
 "Month": "May 2004",
"MedicalMisconductCount": 24 
},
{
 "Month": "Jun 2004",
"MedicalMisconductCount": 26 
},
{
 "Month": "Jul 2004",
"MedicalMisconductCount": 30 
},
{
 "Month": "Aug 2004",
"MedicalMisconductCount": 27 
},
{
 "Month": "Sep 2004",
"MedicalMisconductCount": 26 
},
{
 "Month": "Oct 2004",
"MedicalMisconductCount": 31 
},
{
 "Month": "Nov 2004",
"MedicalMisconductCount": 31 
},
{
 "Month": "Dec 2004",
"MedicalMisconductCount": 41 
},
{
 "Month": "Jan 2005",
"MedicalMisconductCount": 18 
},
{
 "Month": "Feb 2005",
"MedicalMisconductCount": 20 
},
{
 "Month": "Mar 2005",
"MedicalMisconductCount": 23 
},
{
 "Month": "Apr 2005",
"MedicalMisconductCount": 29 
},
{
 "Month": "May 2005",
"MedicalMisconductCount": 32 
},
{
 "Month": "Jun 2005",
"MedicalMisconductCount": 26 
},
{
 "Month": "Jul 2005",
"MedicalMisconductCount": 28 
},
{
 "Month": "Aug 2005",
"MedicalMisconductCount": 32 
},
{
 "Month": "Sep 2005",
"MedicalMisconductCount": 22 
},
{
 "Month": "Oct 2005",
"MedicalMisconductCount": 38 
},
{
 "Month": "Nov 2005",
"MedicalMisconductCount": 36 
},
{
 "Month": "Dec 2005",
"MedicalMisconductCount": 33 
},
{
 "Month": "Jan 2006",
"MedicalMisconductCount": 15 
},
{
 "Month": "Feb 2006",
"MedicalMisconductCount": 21 
},
{
 "Month": "Mar 2006",
"MedicalMisconductCount": 30 
},
{
 "Month": "Apr 2006",
"MedicalMisconductCount": 23 
},
{
 "Month": "May 2006",
"MedicalMisconductCount": 36 
},
{
 "Month": "Jun 2006",
"MedicalMisconductCount": 22 
},
{
 "Month": "Jul 2006",
"MedicalMisconductCount": 26 
},
{
 "Month": "Aug 2006",
"MedicalMisconductCount": 33 
},
{
 "Month": "Sep 2006",
"MedicalMisconductCount": 18 
},
{
 "Month": "Oct 2006",
"MedicalMisconductCount": 24 
},
{
 "Month": "Nov 2006",
"MedicalMisconductCount": 33 
},
{
 "Month": "Dec 2006",
"MedicalMisconductCount": 53 
},
{
 "Month": "Jan 2007",
"MedicalMisconductCount": 19 
},
{
 "Month": "Feb 2007",
"MedicalMisconductCount": 27 
},
{
 "Month": "Mar 2007",
"MedicalMisconductCount": 22 
},
{
 "Month": "Apr 2007",
"MedicalMisconductCount": 19 
},
{
 "Month": "May 2007",
"MedicalMisconductCount": 29 
},
{
 "Month": "Jun 2007",
"MedicalMisconductCount": 19 
},
{
 "Month": "Jul 2007",
"MedicalMisconductCount": 27 
},
{
 "Month": "Aug 2007",
"MedicalMisconductCount": 46 
},
{
 "Month": "Sep 2007",
"MedicalMisconductCount": 24 
},
{
 "Month": "Oct 2007",
"MedicalMisconductCount": 34 
},
{
 "Month": "Nov 2007",
"MedicalMisconductCount": 25 
},
{
 "Month": "Dec 2007",
"MedicalMisconductCount": 30 
},
{
 "Month": "Jan 2008",
"MedicalMisconductCount": 21 
},
{
 "Month": "Feb 2008",
"MedicalMisconductCount": 17 
},
{
 "Month": "Mar 2008",
"MedicalMisconductCount": 25 
},
{
 "Month": "Apr 2008",
"MedicalMisconductCount": 34 
},
{
 "Month": "May 2008",
"MedicalMisconductCount": 16 
},
{
 "Month": "Jun 2008",
"MedicalMisconductCount": 43 
},
{
 "Month": "Jul 2008",
"MedicalMisconductCount": 28 
},
{
 "Month": "Aug 2008",
"MedicalMisconductCount": 19 
},
{
 "Month": "Sep 2008",
"MedicalMisconductCount": 30 
},
{
 "Month": "Oct 2008",
"MedicalMisconductCount": 28 
},
{
 "Month": "Nov 2008",
"MedicalMisconductCount": 22 
},
{
 "Month": "Dec 2008",
"MedicalMisconductCount": 29 
},
{
 "Month": "Jan 2009",
"MedicalMisconductCount": 15 
},
{
 "Month": "Feb 2009",
"MedicalMisconductCount": 18 
},
{
 "Month": "Mar 2009",
"MedicalMisconductCount": 26 
},
{
 "Month": "Apr 2009",
"MedicalMisconductCount": 27 
},
{
 "Month": "May 2009",
"MedicalMisconductCount": 38 
},
{
 "Month": "Jun 2009",
"MedicalMisconductCount": 24 
},
{
 "Month": "Jul 2009",
"MedicalMisconductCount": 35 
},
{
 "Month": "Aug 2009",
"MedicalMisconductCount": 25 
},
{
 "Month": "Sep 2009",
"MedicalMisconductCount": 19 
},
{
 "Month": "Oct 2009",
"MedicalMisconductCount": 21 
},
{
 "Month": "Nov 2009",
"MedicalMisconductCount": 24 
},
{
 "Month": "Dec 2009",
"MedicalMisconductCount": 20 
},
{
 "Month": "Jan 2010",
"MedicalMisconductCount": 21 
},
{
 "Month": "Feb 2010",
"MedicalMisconductCount": 21 
},
{
 "Month": "Mar 2010",
"MedicalMisconductCount": 27 
},
{
 "Month": "Apr 2010",
"MedicalMisconductCount": 16 
},
{
 "Month": "May 2010",
"MedicalMisconductCount": 29 
},
{
 "Month": "Jun 2010",
"MedicalMisconductCount": 26 
},
{
 "Month": "Jul 2010",
"MedicalMisconductCount": 24 
},
{
 "Month": "Aug 2010",
"MedicalMisconductCount": 32 
},
{
 "Month": "Sep 2010",
"MedicalMisconductCount": 20 
},
{
 "Month": "Oct 2010",
"MedicalMisconductCount": 34 
},
{
 "Month": "Nov 2010",
"MedicalMisconductCount": 40 
},
{
 "Month": "Dec 2010",
"MedicalMisconductCount": 29 
},
{
 "Month": "Jan 2011",
"MedicalMisconductCount": 21 
},
{
 "Month": "Feb 2011",
"MedicalMisconductCount": 27 
},
{
 "Month": "Mar 2011",
"MedicalMisconductCount": 37 
},
{
 "Month": "Apr 2011",
"MedicalMisconductCount": 21 
},
{
 "Month": "May 2011",
"MedicalMisconductCount": 22 
},
{
 "Month": "Jun 2011",
"MedicalMisconductCount": 25 
},
{
 "Month": "Jul 2011",
"MedicalMisconductCount": 25 
},
{
 "Month": "Aug 2011",
"MedicalMisconductCount": 28 
},
{
 "Month": "Sep 2011",
"MedicalMisconductCount": 21 
},
{
 "Month": "Oct 2011",
"MedicalMisconductCount": 22 
},
{
 "Month": "Nov 2011",
"MedicalMisconductCount": 24 
},
{
 "Month": "Dec 2011",
"MedicalMisconductCount": 22 
},
{
 "Month": "Jan 2012",
"MedicalMisconductCount": 16 
},
{
 "Month": "Feb 2012",
"MedicalMisconductCount": 15 
},
{
 "Month": "Mar 2012",
"MedicalMisconductCount": 23 
},
{
 "Month": "Apr 2012",
"MedicalMisconductCount": 34 
},
{
 "Month": "May 2012",
"MedicalMisconductCount": 29 
},
{
 "Month": "Jun 2012",
"MedicalMisconductCount": 21 
},
{
 "Month": "Jul 2012",
"MedicalMisconductCount": 15 
},
{
 "Month": "Aug 2012",
"MedicalMisconductCount": 30 
},
{
 "Month": "Sep 2012",
"MedicalMisconductCount": 17 
},
{
 "Month": "Oct 2012",
"MedicalMisconductCount": 30 
},
{
 "Month": "Nov 2012",
"MedicalMisconductCount": 42 
},
{
 "Month": "Dec 2012",
"MedicalMisconductCount": 20 
},
{
 "Month": "Jan 2013",
"MedicalMisconductCount": 23 
},
{
 "Month": "Feb 2013",
"MedicalMisconductCount": 14 
},
{
 "Month": "Mar 2013",
"MedicalMisconductCount": 33 
},
{
 "Month": "Apr 2013",
"MedicalMisconductCount": 26 
},
{
 "Month": "May 2013",
"MedicalMisconductCount": 37 
},
{
 "Month": "Jun 2013",
"MedicalMisconductCount": 40 
},
{
 "Month": "Jul 2013",
"MedicalMisconductCount": 24 
},
{
 "Month": "Aug 2013",
"MedicalMisconductCount": 38 
},
{
 "Month": "Sep 2013",
"MedicalMisconductCount": 35 
},
{
 "Month": "Oct 2013",
"MedicalMisconductCount": 42 
},
{
 "Month": "Nov 2013",
"MedicalMisconductCount": 36 
},
{
 "Month": "Dec 2013",
"MedicalMisconductCount": 43 
},
{
 "Month": "Jan 2014",
"MedicalMisconductCount": 26 
},
{
 "Month": "Feb 2014",
"MedicalMisconductCount": 20 
},
{
 "Month": "Mar 2014",
"MedicalMisconductCount": 38 
},
{
 "Month": "Apr 2014",
"MedicalMisconductCount": 33 
} 
],
"pointSize":              0,
"lineWidth":              1,
"parseTime": false,
"labels": [
 "MedicalMisconductCount" 
],
"id": "chart1" 
},
      chartType = "Line"
    new Morris[chartType](chartParams)
</script>