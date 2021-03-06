# Milestone Project 3 - Riddle-Me-This Game
## Practical Python

*Developer: Anthony Bonello*

-------
**INDEX**

* [INTRODUCTION](#introduction)
* [UXD](#uxd)  
    * [Strategy](#strategy)
    * [Scope](#scope)
    * [Structure](#structure)
    * [Skeleton](#skeleton)
    * [Surface](#surface)
* [WIREFRAMES](#wireframes)
* [LOGIC FLOW DIAGRAM](#game-logic-flow-diagram)
* [FEATURES](#features)
* [TECHNOLOGIES USED](#technologies-used)
* [TESTING](#testing)
* [DEPLOYMENT](#deployment)
* [CREDITS](#credits)
---------

## INTRODUCTION
* [Back to TOP](#Milestone-Project-3---Riddle-Me-This-Game)

### **A Guessing Game**  
This is the milestone project for the “Practical Python” module, part of the New LMS in the “Full Stack Web Development Course” offered by Code Institute.

The purpose of the game is to guess a word or phrase from a given picture. Three attempts are allowed. With each subsequent attempt, further clues will be shown at the expense of reduced points.


### **What I plan to achieve? - An overview**  
The first decision I felt I have to make is whether to use a text-based or a picture-based riddle. I did a google search and I found some material that I can use as a picture-based riddle game. I also thought that a picture-based game would be more attractive to a wide range of users of different ages. I decided to go down this route. See [credits](#credits) for the pictures used.

Then I sketched a few layouts (pencil and paper) to get a general feel of how I would get the game to flow and an idea of layout of various parts. I sketched the logic of the game using a [flow diagram](#game-logic-flow-diagram).

The game will randomly select 10 riddles from a pool of riddles. The user will be presented with the first riddle. The user has to write the answer for the riddle and submit the answer by pressing a button. An option to pass is also provided. 

A submitted answer will be checked against the stored answer and if correct a second riddle is presented. If the answer is wrong or if the user chooses to pass, a second attempt at answering will be offered. This time the user will be told how many words are expected in the answer. Similar submit and pass options are offered. If the answer is wrong or the user passes, a third attempt is offered. This time, apart from the number of words in the answer, the user will be shown how many letters are in each word. After this final attempt the user will be directed to the next riddle, unless it is the final one, in which case the game will end and the user will be directed to the user page.

Points gained will be displayed on the user page and if they are high enough they will be added to the Hall of Fame.

### Security

**A note about security**  
For this project I do not need high security.
For better security the secret_key should be completely random to make it very difficult to guess.
Ideally use a random key generator.
The key should be placed in a separate configuration file which would then be imported (not pushed to github). Alternatively use environment variables.
I do not consider security to be an issue for this particular project considering the purpose.

For better security I would also implement a password that would be salted and hashed. Only the hash 
would then be stored. Again I am not doing this for this project.

---

## UXD
* [Back to TOP](#Milestone-Project-3---Riddle-Me-This-Game)

The idea is to have a riddle game based on the idea of Pictionary.

Some menus will not be available before a user logs in, namely USER and CURRENT GAME. CURRENT GAME will only be available while a game is beign played. I plan to hide the menu for the current page.  

There are arguments against this. The argument goes that it will disorient the user by having the order changing. My argument against this is that the menu is going to change anyway since the unavailable menus will not be shown. Also the actual ordering will not be changed, ie, the Game menu will always be after the User menu when available, etc. 

I think this is a small price to pay and the user should get used to it in a brief time. I do not think that it requires any appreciable learning curve. Some of the riddles are much tougher.

### **Strategy** 
* [Back to TOP](#Milestone-Project-3---Riddle-Me-This-Game)

The users of this site will be challenged with pictures which represent a word or a phrase and they have to guess this and gain as many points as possible to qualify to the Hall of Fame.

There are two halls of fame, one is for individual games, and the second for the overall points gained by the user. This will encourage the users to play more and raise their personal overall points gained.

-----------
People who might use the website would be looking for a mental challenge. Ages can vary but it does require a wide background knowledge of various topics and experiences.

-------

#### What does it do?
Once a user registers and logs in, this game will select a random selection of 10 riddles from the current 30 riddles. The user will have to guess the word or phrase that the picture represents.

This game is competitive through the employment of hall of fames.

It is targeted at users who like mental challenges.

Visitors have the ability to contact me by using a contact form.

#### How does it work


**Playing the Game - Instructions**

After logging in or registering you are taken to the user page. If you have navigated elsewhere you need to return to the user page. (Note the user page is not available in the navigation if you are not logged in.)

From the User page you can start a new game. Press the **Play a game** button.

An image is shown and your task is to guess the word or phrase that it represents. Type this in the space provided. Then click the **Submit Answer** button. If your guess is correct you will earn 10 points and will be moved to the next riddle.

If you have no clue of the answer, you can click on the **Pass** button.

Clicking the pass button, or if your first attempt was wrong will take you to the second attempt page.

Here you can see your previous answers for this riddle, and an indication of the number of words expected. Notice that the number of points for a successful guess has been reduced to 6. As previously, you can attempt a reply or pass.

Please note: the game has been coded in a way that it will accept the answer typed in a single input field. This has been done to facilitate typing.

If the answer is correct you will earn 6 points and the next riddle is presented. If your guess is wrong or you pass, you will be taken to the page for a third and final attempt.

This time round, apart from the number of words, you will be told how many letters are in each word. This is done at the expense of reduced number of points which, in case of a successful guess are reduced to 2 points.

If your guess is wrong or you pass, you will be taken to the next riddle. If it happens to be the last riddle in a game, then the game will be over and you will be taken to your User page. The points gained will be added to your scores and if you were good enough you might even make it to the Hall of Fame.

Each game has 10 riddles with a maximum of 100 points.


If you navigate away from the game, a new menu will appear that will allow you to return and continue the current game.



### **Scope** 
* [Back to TOP](#Milestone-Project-3---Riddle-Me-This-Game)

#### Features to implement

* Game
* Contact
* Instructions in home page and About page
* Hall of Fame:
    * Single game
    * Per user (all games played by user)


#### User stories

A person comes to this game to play:

1. **Case first time user, using available username**:  
The user tries to register. The username is checked. It is available. The user is allowed to proceed with the registration process. On completion the user is logged in, taken to the user page and ready to start playing. See [instructions](#how-does-it-work).

2. **Case first time user, trying to use unavailable username**:  
The user tries to register. The username used is found to be already in use. A message to this effect is shown to the user and asked to select another one. This continues until the user selects an available (not already in use) username. The user is allowed to proceed with the registration process. On completion the user is logged in, taken to the user page and ready to start playing. See [instructions](#how-does-it-work).

3. **Case returning user**:  
The user types in the username and clicks on the login button. The user is taken to the user page where there will be displayed a list of games already played and a button allowing for starting a new game. For playing the game see [instructions](#how-does-it-work).


### **Structure**
* [Back to TOP](#Milestone-Project-3---Riddle-Me-This-Game)

The data is held in json files. Databases can be used in later versions of the game.

There are 4 json files employed:
1. users.json - An object of objects; this holds information about each registered user. Example:  
    "user1": {
        "date_best_game": "27/07/2018",
        "games_played": [
            [
                "27/07/2018",
                14
            ]
        ],
        "number_of_games": 1,
        "points_best_game": 14,
        "total_user_points": 14,
        "username": "user1"
    }

    games_played stores the date of the game as well as the points gained for that game

2. riddles.json - List of objects; this holds data about all the riddles available. 10 will be chosen at random for each game. The code will make sure that the same riddle is not selected multiple times. Example:  
    {   
        "id":       1,
        "source":   "Obi-Wan-Kenobi.jpg",
        "answer":   "Obi Wan Kenobi"
    }

3. hof_individual.json - holds data about the best 10 games played. When new games are added, the code will sort the games and drop the 11th one.

4. hof_all_games.json - holds data about the best overall performance by users. It holds the total points for that user and the number of games played. The code will drop any entries beyond 10.


### Skeleton
* [Back to TOP](#Milestone-Project-3---Riddle-Me-This-Game)


1. Home Page
2. User Page
3. Current Game Page
4. Hall of Fame Page
5. About Page
6. Contact Page

Overall each page's structure includes:
* a header containing:
    * a logo, 
    * title,
    * logged in username (if any),
    * login/registration section,
    * navigation.
* Body section:  
    * This can be single column (all screen sizes), or
    * single column (for mobile / tablet) changing to two columns (for desktop).
* Footer section:
    * Copyright notice,
    * social links.


Not all the pages will be available from the start as some will require the user to be logged in. The unavailable pages will not show up in the menu. Since the menu items were going to change in this way, I decided to hide the menu item that the user is currently visiting.

I had experiences using other websites where I click on a menu item and nothing seem to happen only to discover that I am actually already on that page. The reason for hiding the current page from the menu is to avoid this situation while keeping in line with how the navigation is already functioning.


* [wireframe](#wireframes) - follow this link for further reading


### Surface
* [Back to TOP](#Milestone-Project-3---Riddle-Me-This-Game)


The idea is to have a responsive, mobile first design.

Header at the top, body and footer.

The overall color scheme is monochrome based on a grey scale.

Some accent colors where chosen for CTA buttons.

Error messages are in red. Some are highlighted with yellow background to make them stand out.  
Success messages are green.  

LOGO 
The logo is only present in screens of landscape tablets and above.

I wanted to accentuate the game by doing an interactive logo. This was designed in inkscape as an svg image. But I decided to use a png version for implementation. The base color is brownish to match the general color of the riddle pictures.

The animation of the logo uses [p5.js](https://p5js.org/) library. p5.js a JS client-side library for creating graphic and interactive experiences, based on the core principles of Processing.

I preload three images, one for the complete image - the logo at rest, one for the logo background missing the exclamation mark and its border, and a third one for a semi-transparent exclamation mark (no border). Using javascript, I switch the background image and handle the position of the floating exclamation mark to follow the mouse position.

By switching the images I achieve an effect as if there is a meniscus which reaches up around the exclamation mark creating a whitish border when it is at rest. As soon as the exclamation mark is lifted off its resting place and moves around this border is removed as if an item has been lifted out of a liquid surface.


The footer will be stacked in one column in mobile view and will get a two column layout for the tablet and desktop views.


#### Colors 

The overall color scheme is a scale of grey.
  

* **Logo Color / Brand**:  

Main color for Logo: #d67b34


* **Text color**:  rgb(0, 0, 0) 


* **footer &lt;a&gt; color**:  
Social Icons have a touch of red that floods the icons on hover.

* **Error message color**:  
red  
some errors are highlighted with background-color: #fde2eb;  
others are highlighted with background: yellow;

* **Success message color**: 
Green
accented with background-color: #dbffe4;


* **Button colors** (complementary colors):  
    * **CTA Buttons** : #f92fd6 with a hover of #d4ffae having a yellow shadow. 
    When active the background changes to #b093f7 with a blue shadow and text color becomes #d4ffae.
    Notice the text in active state uses the same color as the hover shadow. 

    * **Menu button**: The colors for this button were chosen from the logo image.  
    The main background is #d58535; with a hover of #e6c49a;.

#### Typography

Fonts used are from [google fonts](https://fonts.google.com/). The main font is **Averia Serif Libre** with a fall-back to Cursive. The other font used is **Gloria Hallelujah** with a fall-back to Cursive for H1 header. And **Bubblegum** witha a fall-back to Cursive for H2 and H3 headers.

The font used for both the logo and the favicon is **Savoye LET CC**. Even the exclamation mark started with this font but then it was warped.


## WIREFRAMES
* [Back to TOP](#Milestone-Project-3---Riddle-Me-This-Game)  
* [Back to Skeleton](#skeleton)

A mockup wireframes for this game has been prepared using  
![Pencil](static/img/Pencil-logo-shadow.png) [**Pencil Project**](https://pencil.evolus.vn/). If you click on the buttons it will mimic the general flow of the game.

You can reach these [here](https://abonello.github.io/project-3_wireframe/)  
Please note that a copy of the files for this wireframe are in this repository too at [WireFrame/index.html](https://github.com/abonello/project-3/tree/master/WireFrame)  

## GAME LOGIC FLOW DIAGRAM
* [Back to TOP](#Milestone-Project-3---Riddle-Me-This-Game)  
* [Back to Overview](#introduction)  

This is the flow diagram of the logic controlling the game.
![Logic Flow Diagram](WireFrame/pages/game_logic_flow_chart.png)



## FEATURES
* [Back to TOP](#Milestone-Project-3---Riddle-Me-This-Game)


### Existing Features

If a user tries to login with a non existent username, that user will be directed to the registration page.



* Game Logic - allows three attempts with each attempt giving more clues.
* For the second and third attempt of each riddle, in the case of answers with more than one word, the user can type in the whole answer in any of the input fields. The backend is able to sort things out.  


* USER is able to move away from the game and come back.

* Can have more than one user playing at the same time.



&nbsp;  
registration and login
* When registering, checking if username is not already in use
* username - keeps track of all played games, points gained and date
* keeps track of logged in users incase someone tries to log in from a different device
* The navigation will automatically hide the link for the current page of for any links that are not available. Ex. If you are not logged in, you cannot access the user page.  
Navigation appears as a button for mobiles and tablets, and as a menu in the header in larger views. 
* hall of fame - single game - all games
* About page has instructions of how to play the game
* contact form - enabled through flask_mail, enables users to get in touch.  
Upon sending, the message will be shown to the user. 
Validation of the form content is carried out including if the email lacks the top level domain.
* Interactive logo built using p5.js.



### Features Left to Implement

None unless I want to extend it beyond the scope of this project.


### Known Limitations
*These limitations fall beyond the scope of this project*.  

* Not using a password. Another person can use the same username that has already been registered.

* When Heroku sleeps, it will erase all new registrations, games played and hall of fame entries and reverts back to the state of when the game was deployed.



## TECHNOLOGIES USED
* [Back to TOP](#Milestone-Project-3---Riddle-Me-This-Game)

- [HTML5](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/HTML5) - used to build the structure and the content of this project.
- [CSS3](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS3) - used for creating the specific and custom styling of the game.
- [jQuery v3.3.1](https://jquery.com) - simplifies accessing the DOM.
- [Bootstrap v3.3.7](https://getbootstrap.com/docs/3.3/) - used for some of the styles (modified), as well as layout of the content.
- [Font Awesome v4.7.0](https://fontawesome.com/v4.7.0/) - used to display the GitHub and Linkedin Icons.
- [Google Fonts](https://fonts.google.com/) - Lobster and Roboto.
- [p5.js](https://p5js.org/) - controls interactivity of the logo image.
- [Python 3](https://www.python.org/) - for back end.
- [Flask](http://flask.pocoo.org/) - Back end micro framework. Upgrade Flask to v1.0.2, git reported that the previous version 0.12.2 had a known security vulnerability.
- [jinja2](http://jinja.pocoo.org/docs/2.10/) - for templating the various pages.
- [flask_mail](https://pythonhosted.org/Flask-Mail/) - used to enable the contact form to send emails to me.
- [unit test](https://docs.python.org/3/library/unittest.html) - used to unit test the python functions.
- [json](https://www.json.org/) - to hold data.
- [SVG](https://www.w3schools.com/graphics/svg_intro.asp) - This was used to build the logo image using [Inskscape](https://inkscape.org/). From this png files (with transparent background for the `!`) where produced.
- [Compress JPEG ](compressjpeg.com) - I use [GIMP](https://www.gimp.org/) to manipulate images. Once I export them as jpg, I use Compress Jpeg to minify them. Usually, I can gain between 25% and 50% reduction in file size.


## TESTING
* [Back to TOP](#Milestone-Project-3---Riddle-Me-This-Game)

### Final check on desktop

I tested the various scrollings on desktop using Safari v8.0.8, Chrome v70.0.3538.77 and Firefox v63.0.

On safari, the logo refuses to display even though the image is loaded.

### Manual testing using Chrome.
Example of testing steps:  
1. Test menu in various order both when logged in and when not. 
2. Test that user page and current game menus display only when a user is logged in.
3. Test that the menu for the current page does not show in all cases.
4. Test contact form for validation of entered data as well that it actually sends the email.
5. Manually test the logo.  
    * The excalmation mark follows the mouse when hovering over the logo image.
    * The background image of the logo is switched when hovering and switched back when the mouse moves out. 
6. User moves to another page while playing and is able to come back to the game by clicking the `CURRENT GAME` menu item in the navigation bar.

**All Tests passed on desktop and mobile** (*mobile testing does not apply to logo*) **.**


### Manual Testing - User Stories

* A student / parent is looking for a music teacher:  
    1. The user comes to the page
    2. Clicks on activites in the menu (or scrolls down manually to the activities section)
    3. Reaches the Music Tuition part
    4. Clicks on the *Tell me more ...* button (secondary CTA)
    5. Reads the content
    6. Press the *get in touch* button (primary CTA)
    7. Fills in the form and press the submit button

    **Test pass on desktop.**

----


* A person is using this game for the first time and has to register:  

    1. Options:  
        a. The user may click on the login button without entering a user name.  
        An error message alerting the user that a username is required is displayed in red text.

        b. The user may click on the login button but enters an unknown username.  
        [Please note if the username happens to exist the user will be logged in. This can be avoided by applying a password which is considered outside the scope of this project.]  
        I am using the case where the username entered does not exist.  
        The user is taken to the registration page.

        c. The user may click on the registration button and will be taken to the registration page

    2. On arriving at the registration page, the user is invited to enter a user name and check its availability. The user types in a username and clicks on the `Check Username Available` button.  
        a. **Case - Username not available**:  
        The error message *Username already exist. Please try another one.* will be displayed in red. The entered username is still displayed in the input box to facilitate usability. The user can modify the username or enter a completely new one and check again.  
        b. **Case - Username is available**:  
        The `Check Username Available` will be hidden and instead, a `Register` button is displayed.  
        The message *Username available. Please click the register button.* will be displayed in green letting the user know that this username is available and inviting the user to proceed with the registration.  
        The user will be automatically logged in and taken to the user page. Some information will be given including that this user has not played any games yet and that the points gained up to now is 0.
    
        An empty list that will hold future played games is displayed.  
        There is also a button to start a new game.  
        (Playing the game is covered in the next test)

    **Test pass on mobile and desktop.**

----



* A registered user returns to the game:  
    1. The user types in the username and clicks on the login button.
    2. The user is taken to the user page where there will be displayed some statistic information about the games played, a list of games already played including dates and points gained.
    3. The user clicks on the `Play a game` button. The user will be taken to the Game page.  
    &nbsp;  
    **Playing a game**  
    4. The user is shown a picture and the task is to guess the phrase or word represented by this picture, like in pictionary.
    5. The user types in the guess and clicks on the `Submit Answer` button. Alternatively the user can give up and clicks on the `Pass` button.
    6. If the user passes or the answer is wrong, the wrong answer (or a dash) is displayed for the first attempt. Clues are given to the user about the number of words expected in the answer and the user can have a second attempt.  
    The clues are both textual and visual. A textual message mentioning the number of words is displayed, while the entry fields change. There will be one entry field for each word, each labeled with `Word #` where # is the number of the word within the answer. This reduces the points from 10 to 6 for this riddle.  
    7. The user attempts to answer or passes.
    8. If the answer is wrong or the user passes, further clues are given. This time the user will be told how many letters there are in each word. An indication about this is given to the user in the text above the buttons as well as next to the input fields. The points are reduced to 2.
    9. In any of the attempts, if the user's answer is correct, the total number of points gained in this game will be displayed and the next riddle is shown.
    10. In the case of the last riddle, the user will be taken back to the user page. A message in green text will be displayed showing the total points gained in the game just finished.
    11. The user can start a new game as in step 3 above.

-----

* Testing the contact form  
The contact form can only be reached from the Contact menu item in the navigation bar. This works in all screen sizes.
&nbsp;  
Submitting message and entry validation:  
    1. Submitting empty form: **Error message shown to user prompting to fill in the name**
    2. User fills in only name and trying to submit: **Error message shown prompting user to fill in email**
    3. User fills in first part of email only (Ex. asdf): **Error message showing that the email lacks an @ symbol**
    4. User adds @ symbol and tries to submit: **Error message telling the user that the part following the @ symbol is missing**
    5. User completes the name and email and leaves the rest of the form empty: **Error message prompting the user to fill in a subject**
    6. User fills in the name, email with correct format and subject and tries to submit: **Error message prompting user to write a text message**  
        Following this typing less than 3 letters, an error message prompts the user that the message should be at least three letters long. (This is an arbitrary number.)
    7. Trying to send a filled in form with an email lacks a top level domain. An error message will be displayed showing the email address used and a note is displayed encouraging the user to check the email and return to the contact form. 
    8. In the case of the error raised in step 7, the user can click on the `Go Back` button to return to the contact form.
    


### Mobile / Tablet testing

Apart from using Chrome developer tools to test the layout and functionality of the page in mobile and tablet layouts, I also tested the site on my mobile phone and that of my friend. Both are android phones.  

The site is responsive and everything seems to work well in chrome developer tools and the mobile phones.



### Unit testing Code for Form Validation


I did unit tests for the index page as well as the functions read_from_file and createUser


----

### Cleaning and validating code

* **HTML** - https://validator.w3.org/  

    Home Page not logged - PASS  
    Home Page Logged - PASS  
    Register page - ~~Duplicate ID username~~ ~~Empty name attribute~~ - PASS  
    Register page continue ERROR -  PASS  
    Register page continue AVAILABLE - PASS  
    User page NEW - PASS  
    User page old user - PASS  
    Game 1st attempt - ~~alt for button~~ - PASS  
    Game 2st attempt - PASS  
    Game 3st attempt - PASS  
    Game finished User page - PASS  
    Hall of Fame - PASS  
    About - PASS  
    Contact - ~~role unneccessary for Form element~~ - PASS  
    Message error - PASS  
    Message sent - PASS  

* **CSS** - https://jigsaw.w3.org/css-validator/  
It complains about vendor prefixes for transition. I 
am leaving these in for older versions of browsers.


* **JavaScript** - http://esprima.org/demo/validate.html
Testing `p5-script.js`  
Code is syntactically valid.


* **jshint Linter** - http://jshint.com/  
Note: Linter complains that there are 9 undefined variables.   
These are defined and initialised using let.  
It also complains that there are three unused variables which are actually functions. These functions form part of the 
required structure for p5.js.



## DEPLOYMENT
* [Back to TOP](#Milestone-Project-3---Riddle-Me-This-Game)

The repository of this project is at [**github repository**](https://github.com/abonello/project-3),  
and it is deployed on Heroku [**here**](http://riddlegame-ab.herokuapp.com/).



### Version Control and Deployment
This is the [github repository](https://github.com/abonello/project-3),
and this project is deployed on Heroku [here](https://riddlegame-ab.herokuapp.com).

I am basing this project on an earlier exploratory exercise that I did. This previous exercise was meant to be a draft to practice the techniques and skills I need for this project. It can be found [here](https://github.com/abonello/riddle-game-app).
Another project that I built to learn the techniques I need is an addition game. The code can be found [here](https://github.com/abonello/addition_game).

The main change I did from my earlier riddle game project is to base the current one on OOP. In this way I can have multiple users logged in without interfering with each other. This is what I learnt from the addition game.


## CREDITS
* [Back to TOP](#Milestone-Project-3---Riddle-Me-This-Game)

### Code from other sources
I am linking to bootstrap cdn as well as using p5 code which is stored in its own file, static/vendor/p5.min.js


### IMAGES

**Logo**:  
The image and design of the logo is my work.

**Favicon**:  
The image and design of the favicon is my work.

**Riddle Images**:  
These are the work of **Marcus Connor** of [Brainless Tales](http://www.brainlesstales.com/) who gave me permission to use these images for the games in this project. I am very grateful for this.

One can read more about Marcus' work in the [About page of his website](http://www.brainlesstales.com/about). You can also see the 9 years' worth of daily pictures as well as visit his [store](http://www.brainlesstales.com/store).


### FONTS
**Averia Serif Libre**, **Gloria Hallelujah** and **Bubblegum** fonts from [google fonts](https://fonts.google.com/).
