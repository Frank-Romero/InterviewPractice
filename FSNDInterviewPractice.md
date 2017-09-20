Question 1

What is the most influential book or blog post you’ve read regarding web development?

I do not have a specific blog post or book, but I will say that the entrepreneur subreddit had been the most influential
in getting me to pursue a career in web development over game design. At the time, which was a few years back now, I had
been attempting to develop an independent game but was feeling burnt out from the unending grind. I had stumbled across
the entrepreneur subreddit in an attempt to find a new career path, and came across a number of posts talking about web
development. What really caught my attention was how every industry is entering the digital era, and there are tons of
opportunities to actually help companies engage and enrich clients and consumers. I felt encouraged to learn about how
design can retain and enhance the user experience, how optimization is a necessity, and how vital yet ignored cybersecurity
is even in the government! Thanks to that subreddit, I delved deeper into the ever expanding world of web development!

One thing to note, before entering the world of game development I did consider web development and took courses in Perl,
Ruby, and front-end web design. It only seems natural that I would return to it, and have added to my formal education with 
Udacity's Full Stack Web Development Nanodegree.

Question 2

Tell me about a web application you have built. Why did you choose to build it? What did you learn?
What challenges did you face and how did you overcome them?

I have built a timer web application that was easy for the user to modify and suited my workout needs. I chose to build
it not only because I was dissastified with the timers I found online, but in order to grow my experience with javascript.
Getting it up and running was not difficult, but figuring out good UX and how to store user preferences was a little difficult. 
I settled on keeping the timer numbers large, centered on the page and popping against the background colors in order to keep attention
directed towards it during workouts no matter the device resolution. And I made a seperate side menu that is normally hidden for
changing options in order to prevent distractions from the timer. In addition, the color of the background changes as the timer
runs out in order to provide another easily visible cue. As to the storage of the user preferences, initially I wanted to store it locally,
which was easy enough with HTML5's localStorage. But afterwards I instead wanted the user's information to be accessed on other
computers/browsers, and this proved to be a little more difficult. I eventually figured out how to store user information in a PostgreSQL
database with a Python backend. Next I want to try and migrate over to mongodb and implement Node.js for the experience.

Question 3

Write a function in Python that takes a list of strings and returns a single string that is an HTML
unordered list (<ul>...</ul>) of those strings. You should include a brief explanation of your code.
Then, what would you have to consider if the original list was provided by user input?

# function takes in a list of strings and returns a string that is an HTML unordered list
def view_list(string_list):
	# html_ul is the HTML string, beginning with the unordered list tag
	html_ul = "<ul>"
	# iterate over the list of strings and add to the string each entry surrounded by list tags to increase readibility
	for r in string_list:
		html_ul += "<li>" + r + "<li>"
# close the HTML unordered list string
html_ul += "</ul>"
# return the HTML unordered list string
return html_ul

If the original list was provided by user input, I would do three things:
- Check to see if the input is a list
- Check to see if the list is empty, if not check to see if all items are strings
- Sanitize the list to prevent HTML escaping

Question 4

List 2-3 attacks that web applications are vulnerable to. How do these attacks work? How can we prevent those attacks?

XSS or cross-site scripting involves capturing a user's session token, hijacking the session, and then making use of the
application as the user. This allows the attacker to take ownership of the user's account, or even attempt to inject
malicious code through HTML markup or scripts to capture other users' data. This kind of attack can be prevented by using
content filtering to ensure that all user input is properly sanitzed (preferably with a library designed for security), 
by tying session cookies to the user's IP address or by setting the HTTPOnly flag on the session cookie or any custom cookies, 
and by creating a Content Security Policy that whitelists client side resources for your web application.

Example: Site has a comment section, user writes a comment such as "<script>...</script>" and the code within the script tags
is executed for all visitors to the site if there is no sanitization of the user input.

CSRF/XSRF or cross-site request forgery involves exploiting a website with a trusted, authenticated user who is tricked into
executing unauthorized commands. Because the attacker cannot see the response to the unauthorized commands, the victim is usually
tricked into things like changing email address, sending funds, and things along that nature. Sometimes it is possible that the
CSRF attack can be stored on the site itself, increasing the chances of fooling the victim who is already authenticated on the site.
To protect against this kind of attack, check standard headers to make sure the request is the same origin and check the CSRF
token(which should be a secure random token that is unique for each user session) when the response to authentication is returned.

Example: If a site uses GET requests to transfer parameters, an attacker may modify the legitimate URL to do an unauthorized action
on the victim's side. And by sending the victim a fake image link using the modified URL through email, the modified URL will be run
as soon as the email is opened by the victim. 
legitimate GET request: GET http://mybank.com/transfer.do?acct=TOM&amount=20 HTTP/1.1
emailed image with modified URL: <a href="http://mybank.com/transfer.do?acct=ATTACKER&amount=20000>Aren't they cute???</a>

Question 5

Here is some starter code for a Flask Web Application. Expand on that and include a route that simulates
rolling two dice and returns the result in JSON. You should include a brief explanation of your code.

from flask import Flask
app = Flask(__name__)

import json
import random

@app.route('/')
def hello_world():
 return 'Hello World!'

@app.route('/rolldice/JSON')
def rolldice():
	# the dice are randomly assigned a value from 1 to 6
	die1 = random.randint(1,6)
	die2 = random.randint(1,6)
	dice = die1 + die2
	# the total results of the dice, along with the individual results, are returned as a json string
	return json.dumps({'dice total': dice, 'die 1': die1, 'die 2': die2}, ensure_ascii=False)
	

if __name__ == '__main__':
 app.debug = True
 app.run()

 
Question 6

If you were to start your full-stack developer position today, what would be your goals a year from now?

I would have the goal of helping businesses succeed in properly implementing web technologies and leveraging
them to their benefit. I would be looking to further deepen my understanding of full stack web development,
taking direction from the more senior developers I am working with. I would have my eyes set on perfecting UX.
I would like to contribute to the open source community and become very respected for helpful additions.
I finally would be looking to increase my responsibilities in helping my teammates accomplish our tasks more
efficiently while boosting our morale, and eventually making my way to a management position.