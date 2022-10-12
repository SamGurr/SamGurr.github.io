---
layout: post
title: RShiny calculator app (algae feed)
date: '2022-07-14'
categories: Protocol
tags: RShiny, application, algae, efficiency, R,
---

# How to build an RShiny - algae feed calculator:
----------
Showcase an simple example of an RShiny built for calculating the volume of known algae culture for feeding bivalve larvae


* Here's my code!
[github link to raw code](https://github.com/SamGurr/Airradians_multigen_OA/tree/main/RAnalysis/Scripts/RShiny)

* Use the app [here!](https://sam-geoduck.shinyapps.io/larvae_feed_ui_and_server/)


# Getting started
----------

## on the internet...

* [sign up](https://www.shinyapps.io/) for an RShiny account - there is a free option for up to 5 active applications (this is what I did)

* record the following user info for ease of use when writing your code. You can find this information in your RShiny dashboard (online) under the 'Account' tab

  - username
  - token
  - secret

## in your R script...

### I prefer to use the following folder+file layout:

* RShiny (folder)

  * worksheet_filename.R (R file with ui and server, rsconnect info for upload)

  * ui_and_server_foldername (folder)

    * ui (text file)

    * server (text file)

### What are these files?

* the worksheet file is completed in R with necessary packages installed to run your ui and server in one place - this will pop-up a window (or not depending on error(s)) to test your RShiny app *before* uploading to the server. This is great for the building stage - you can then copy and paste your updated ui and server chunks to separate txt files to connect your app to your RShiny server!



# If you build it.. !
----------

* download/install necessary package(s)

      'library(shiny)' # main package for setting up the user interface ('ui') and server

## (1) User interface (ui)!

About:

This is the interactive part of your RShiny app - the user will see and and fill your desired
variables before viewing the corresponding output


a few commands:

      - 'shinyUI' # start your shinyUI

      - 'fluidPage'

      - 'div'  

      - 'h1', 'h2', 'h3', etc # headings with increasing number decreasing size - can use for subheading

      - 'dateInput' # insert the date, automatically updated for the user
        - EX (code): 'dateInput('date', "Choose today's date:", value = NULL, min = NULL, max = NULL,
                    format = "yyyy-mm-dd", startview = "month", weekstart = 0,
                    language = "en", width = NULL)'

      - 'numericInput' # user chooses a numeric value
        - EX (code): 'numericInput("< insert variable name to call later >", "< insert what you want to read >", < default numeric value >, min = < min numeric threshold >, max = < max numeric threshold >)'
        - EX (filled):'numericInput("how_many_tanks", "How many tanks? (all same volume)", 18, min = 1, max = 50)'

      - 'selectInput' # user chooses from a list of categorical variables
        - EX (code): 'selectInput("< insert variable name to call later >", "< insert what you want to read >", list("< list of characters - first in order will be the displayed >"))'
        - EX (filled): 'selectInput("algae_species_1", "Choose species for Algae #1:",
                        list("T-iso", "Pavlova", "Chaetoceros","Nano","Tetraselmis, NA"))'

      - 'actionButton' # aesthetic to input and calculate - customize the message!
        - EX (filled): 'actionButton("submit", "Feed 'em!", icon("Submit") , width = NULL, style="color: #fff; background-color: #337ab7; border-color: #2e6da4")'


## (2) Server!


About:

This goes on behind the curtain. Filled options of the user interface each contain a variable ID unknown to the user (but known to you!). As the writter, you can take these IDs (i.e. how_many_tanks?) to calculate outputs you want the user to see!


a few comands

      - 'shinyServer' # start your server!
        - EX (filled): 'shinyServer(function(input, output,session){
          < insert all serve code between these brackets > }

      - 'reactiveValues' # these contain the outputs to call (i.e. printed or as a table)

      - 'observeEvent' # insert you calculations (i.e. name them the same as your reactiveValues for example)

      - 'renderDataTable' # speaks for itself..

      - 'observe' # what do you want the user to see?
        - EX (filled): 'observe({print(colnames(tableValues$m))})
                       observe({print(!is.null(tableValues$m))})''


# It will Shiny!
----------------------

About:

Now with your ui and server built in R, you can initiate the app!
Use 'setAccountInfo' and 'deployApp' to upload your ui and server to RShiny.io

Before you run these commands:

- Run your R worksheet script in full (cmd+A+Enter) - are there any teaks or errors?
- save your R worksheet script
- save your UI and server as separate txt files in a folder to call below


Connect your work to the world-wide Shiny web

      - 'setAccountInfo' # connect to your RShiny account
        - EX (code): 'rsconnect::setAccountInfo(name='< username here >',
                            token='< token here >',
                            secret='< secret here >')'



      - 'deployApp'  # Call the ui and server you want to upload
        - EX (code): 'rsconnect::deployApp(', path to the FOLDER containing BOTH the ui and server as separate txt files >')'

After run, this should automatically display your new RShiny app online!

Ready to plug n' play!

### Let's take a look shall we?

#### *the user interface*

![RShiny_bivalve_feeder](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/RShiny_bivalve_feeder.jpg "RShiny_bivalve_feeder")


#### *the output table*

![RShiny_bivalve_feeder_output](https://samgurr.github.io/SamJGurr_Lab_Notebook/images/RShiny_bivalve_feeder_output.jpg "RShiny_bivalve_feeder_output")
