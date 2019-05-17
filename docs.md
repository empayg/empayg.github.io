# Documentation

The docs guide you through all you need to know to integrate EMPAYG in your website and provide a paid option to your users. We recommend you to read it completely. We encourage you to contact us at support@empayg.com if you need any further assistance.

What is EMPAYG?

EMPAYG is a monetisation platform that allows creators to provide a paid option for their web content/service. You can decide the rate you want to charge the users. Users are charged based of the duration of their session.

How does it work?

EMPAYG requires any web service using EMPAYG's service to load a JavaScript widget on the webpage to enable its use. The widget is responsible for collecting user credentials from the webpage and starting the session. The web service gets access to session changes through HTML classes and JavaScript events that can be used to make necessary changes to webpage to make effect of login/logout, which may include changing display of advertisements or content load, by web service. The widget also reports, at periodic intervals, the time for which the web service has been used. The charge is calculated based on the duration for which the web service is used by the user as reported by the widget.

EMPAYG advantage

i.	You can integrate and provide a paid option along with serving advertisements to non-paying users. Empower the users to choose how they want to use the service.

ii.	You can provide your content at the price you decide instead of standard advertisement rates.

iii.	Higher adoption due to lack of any upfront paywall. Even as a paid option, users are charged per their usage.

iv.	You can customise how you serve with EMPAYG. You can provide an ad-free option or premium content.

v.	Setting up your website with EMPAYG is easier that setting up advertisements for the website.

vi.	Users do not have to create separate account to use your service. Users with EMPAYG account can discover, login and start using your service directly.

vii.	We manage accounts and payments so you don’t have to. Payments are secured by Stripe.

viii.	The EMPAYG widget takes up only a ribbon space on website that can be positioned per your preference.

Units

All the transactions and payments are processed and presented in USD cents.

All the session are tracked and charges calculated on the basis of duration for which service is used in seconds.

Tips for creating services

You can create two types of services with EMPAYG currently,

rate. A standard rate is charged to the user. Ideal where no monthly limits are to be set.

cap. User is charged at a rate but a monthly limit exists. So any usage beyond the limit is not charged. Ideal where high value users need to be encouraged with a fix amount of charge. Users will be charged at the rate if their usage is less than standard. It is advised to set a cap service where competitors provide fixed monthly-paid plans.

EMPAYG's charge of service
```
user’s charge * 0.8 = service's payout
```
The users’ charge rate is decided by service creator for self. A standard deduction of 20% is made from total revenue of service. This means the charge rate of service set by creator is inclusive of EMPAYG's charge. Creator must take it in account while deciding the rate. EMPAYG’s deduction is inclusive of payment processing and all other charges. So 80% of charge is transferred to the creator in full.

However, we estimate a 2% loss of sessions' data (partial or complete) due to disconnections, reporting and server errors, and other technical limitations. Such data may never reach us and we cannot process the same. Neither you nor we can receive any charge for such loss. Although, EMPAYG employs best procedures to minimise such loss, we recommend you to account for same when pricing your service.

You should integrate only one service on a website as user login is valid across all webpages on a domain and charge is based on aggregate time spent on website. Contact us for further details or queries.

Creating a service

i.	Signup for a EMPAYG Account.

ii.	Go to /port

iii.	Go to /create to create a service.

iv.	Connect or create your Stripe account, which will be used to pay out the revenues from the service you create.

v.	Create a new service.

vi.	Integrate the service in your website as the details given below.

Widget script code
```html
<script src="//cdn.empayg.net/js/1.0.min.js"></script>
```
Paste the script code in <head> of your html page. Widget tracks time but pauses after inactivity of 30 seconds up till any activity is again noticed. This is to prevent unintended charges. Also, session is closed if the connection to user is not respondent for 60 seconds.

Widget display code
```html
<div id="empayg-display" data-revenueid="UNIQUE-REVENUE-ID"></div>
```
Replace UNIQUE-REVENUE-ID with the revenue id of your service. Paste the display element in body of your html page (preferably at top). Ensure 100% width of window for the display element; else, certain elements may not appear as intended hampering user experience. However, this does not cause any technical issue in working but only frontend discrepancy. Therefore, feel free to play around with its placement if any other positioning suits your web design better. You can include data-position="bottom" in display element to stick widget to bottom of window until user login (if paid content is more prominent). Also, add data-text="Custom display text" to personalise the widget with a message.

Managing display of elements
```html
<div class="empayg-infomercial other-classes">
  Your advertisements and things you want to show non-paying users
</div>
<div class="empayg-content other-classes">
  Your content which you may want to hide until users' login
</div>
<div class="empayg-protect other-classes">
  Content which you do not want users to interact with
</div>
```
EMPAYG enables you to manage content display using classes for elements. Use empayg-infomercial for elements that are hidden after login. Use empayg-content for elements that are presented after login. You do not need to apply any class to consistent content that is not affected by login. Apply empayg-protect to elements that you want to protect from interactions such as selection, copy, download, pointing, and saving. However, don't use empayg-protect on elements where user clicks on link, provides input, or for similar interactions. EMPAYG ensures protection from any breach that may be caused to alter the display of contents.
Advanced content load
```javascript
element.addEventListener('unfold', function() { postmate({'session':cookier('empayguid')}, 'https://empayg.net/q/session').then(function(reply) {if (reply=='UNIQUE-REVENUE-ID') {
  code to load the content after login
}});});
element.addEventListener('fold', function() {
  code to delete the content after logout
});
```
For advanced applications, you can add listeners to our open and close events. EMPAYG broadcasts 'unfold' when a user successfully logins and 'fold' when a logout happens, either due to trigger by user or technical discrepancy. Note that such event listeners should be registered after loading the script code. Add the script code above it in the html file.

Remember if you face any issue, we are always available at support@empayg.com to assist you. Happy payging!

