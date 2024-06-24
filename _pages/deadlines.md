---
layout: single
permalink: /deadlines
author_profile: false
title: "Deadlines"
toc: false
---

<!-- Display the countdown timer in an element -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/countdown/2.6.0/countdown.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.5.1/jquery.min.js"></script>


<div id="0"></div>
<div id="1"></div>
<div id="2"></div>
<div id="3"></div>
<div id="4"></div>
<div id="5"></div>
<div id="6"></div>
<div id="7"></div>
<div id="8"></div>

<script>
    $("countdown").ready(function () {

        function create_countdown(name, date, id) {
            countdown(date,
                function (ts) {
                    let color = "";
                    let text_after = "";
                    if (ts.start < ts.end) {
                        color="red";
                        text_after = " past due";
                    }                    
                    $(id).html(
                    "<h4 style='color:" + color + "'>" + name + "</h4>" + "<p style='color:" + color + "'>" + 
                    
                    ts.toHTML() + text_after + "</p>"
                    );
                },
                countdown.MONTHS|countdown.DAYS | countdown.HOURS | countdown.MINUTES | countdown.SECONDS);
        }
        
        var events = [        
        {'name': "(Lizhen) CHI 2021", 'date': new Date("September 10, 2020 23:59:59 GMT-04:00")},        
        {'name': "(Han) Submit Novelty and CBS papers", 'date': new Date("July 31, 2020 23:59:59 GMT-04:00")},
        {'name': "(Han) Submit misleading graph detection", 'date': new Date("August 31, 2020 23:59:59 GMT-04:00")},  
        ];
        
        var sorted_events = events.sort(function (a, b) { return a.date - b.date }); 
        
        for (i=0; i < sorted_events.length; i++) {
            create_countdown(sorted_events[i].name, sorted_events[i].date, "#" + String(i));
        }
        
    });
</script>

