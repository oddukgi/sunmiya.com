---
title: "Measure of my skills with chart"
date: 2019-11-17T21:28:10+09:00
draft: false
tags: ["app project"]
series: ["app project"]
categories: ["app project"]
slug: "measure-of-my-skills-with-chart"
---

<html xmlns="http://www.w3.org/1999/xhtml" lang="" xml:lang="">
<head>
  <meta charset="utf-8" />
  <meta name="generator" content="pandoc" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=yes" />
  <title>measure of my skills</title>
  <style>
      code{white-space: pre-wrap;}
      span.smallcaps{font-variant: small-caps;}
      span.underline{text-decoration: underline;}
      div.column{display: inline-block; vertical-align: top; width: 50%;}
  </style>
  <!--[if lt IE 9]>
    <script src="//cdnjs.cloudflare.com/ajax/libs/html5shiv/3.7.3/html5shiv-printshiv.min.js"></script>
  <![endif]-->
</head>
<body>
<h3 id="list">List</h3>
<ul>
<li>Developing nice graphic design</li>
<li>Building the user interface with UIKit</li>
<li>Downloading data from an API</li>
<li>Persisting the data</li>
<li>Working through problems and bug to get the app working well.</li>
<li>Posting the app to the App Store (if you are planning on that)</li>
</ul>
<h3 id="chart">Chart</h3>
<html>
<head>
<title>
chart created with amCharts | amCharts
</title>
<meta name="description" content="chart created using amCharts live editor" />
<!-- amCharts javascript sources -->
<script type="text/javascript" src="https://www.amcharts.com/lib/3/amcharts.js"></script>
<script type="text/javascript" src="https://www.amcharts.com/lib/3/serial.js"></script>
<!-- amCharts javascript code -->
<script type="text/javascript">
            AmCharts.makeChart("chartdiv",
                {
                    "type": "serial",
                    "categoryField": "category",
                    "rotate": true,
                    "startDuration": 1,
                    "fontSize": 12,
                    "theme": "default",
                    "categoryAxis": {
                        "gridPosition": "start"
                    },
                    "trendLines": [],
                    "graphs": [
                        {
                            "balloonColor": "#FFFFFF",
                            "balloonText": "[[title]] of [[category]]:[[value]]",
                            "fillAlphas": 1,
                            "id": "skill level",
                            "title": "skill level",
                            "type": "column",
                            "valueField": "skill level"
                        }
                    ],
                    "guides": [],
                    "valueAxes": [
                        {
                            "axisTitleOffset": 5,
                            "id": "ValueAxis-1",
                            "offset": 5,
                            "title": ""
                        }
                    ],
                    "allLabels": [],
                    "balloon": {},
                    "legend": {
                        "enabled": true,
                        "useGraphSettings": true
                    },
                    "titles": [
                        {
                            "id": "category",
                            "size": 15,
                            "text": "How I complete making app"
                        }
                    ],
                    "dataProvider": [
                        {
                            "category": "Persisting the data",
                            "skill level": "3"
                        },
                        {
                            "category": "Downloading data from an API",
                            "skill level": "3"
                        },
                        {
                            "category": "Building the user interface with UIKit",
                            "skill level": "3"
                        },
                        {
                            "category": "Working through problems and bug to get the app working well",
                            "skill level": "4"
                        },
                        {
                            "category": "Developing nice graphic design",
                            "skill level": "5"
                        }
                    ]
                }
            );
        </script>
</head>
<body>
<div id="chartdiv" style="width: 100%; height: 400px; background-color: #FFFFFF;">

</div>
</body>
</html>
</body>
</html>


