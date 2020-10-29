# Tor Browser Research-Project

The goal of this research is to break a part of the [anti-fingerprinting mechanisms](https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=&cad=rja&uact=8&ved=2ahUKEwjh8OCn8djsAhVHYs0KHS2CDSgQFjAAegQIARAC&url=https%3A%2F%2Fblog.torproject.org%2Fbrowser-fingerprinting-introduction-and-challenges-ahead&usg=AOvVaw34jj5T_qmVn1llshL1Sjq_) built into the Tor Browser, specifically the aspect which attempts to obscure the loading time of a specific element of a page. While it may seem like an arbitrary statistic, when a website is able to glean any uniquely identifying information from a user it then becomes possible to track the actions taken by that user across the web, without necessarily tripping the alerts the Tor browser might typically produce of [certain fingerprinting events](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d4/Typical_Tor_Browser_notification_of_a_canvas_read_attempt.png/600px-Typical_Tor_Browser_notification_of_a_canvas_read_attempt.png). 

In the context of this research, a user on the native Firefox or Chrome browser loads a webpage with Javascript enabled. The Javascript runs an arbitrary calculation while tracking the time to completion. This run-time statistic can then be shared to alternate web-pages, which would run the same calculation to identify if the same computer was used to load a webpage.

It is seen that the Tor Browser attempts to simplify the loading time for a page in order to help maximize the availability of identifying information. When compared directly with data from native installations of Firefox and Chrome, the time to finish the calculation varied in a randomized manner. The browser would report times of loading from 0 ms to 300 ms with no identifiable pattern.

In order to break this randomization, an iterative approach was used to run a significant amount of arbitrary calculations. Although the mode of the iterations would be 0,100,200, or 300, it was possible to generate an average calculation time when given enough iterations. Given this distinct average loading time, it is possible to run the same number of arbitrary calculations on a sister site to determine if the same computer is loading a webpage.

For a graphic that details the data gathered and conclusions drawn in this research, please view the PDF under `./Tor-Research-Poster.pdf`.
