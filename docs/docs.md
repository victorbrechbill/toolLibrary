This project has the following dependencies:

Node.js
MongoDB
Docker


User roles:

There will be admin accounts, and general accounts. There should be a user roles dashboard for admins to access. Users can only be added or removed via this dashboard. This is because each user needs to be verified by an admin.  As this is a neighborhood tool, the admin might want to meet the person, check their ID, or take payment in exchange for giving them access.

Login page:

The login credentials should be stored in a browser cookie for up to a year, so the user should be redirected to the login page only if they don't have this login cookie.

Configuration page:

This is a page only accessible to admins.  It allows the admin to set notifications, change the title or logo of the site, and view an activity log.

Home page:

There should be a nice looking home page, that includes a couple of fields that can be set on the configuration page.  It should be possible to set up and customize this entire application without changing any code.

The home page will have links to each of the various tools that the application provides (these tools can be enabled or disabled on the configuration page)





Notifications:

Sending Notifications via Email and SMS
This application supports sending notifications to users for free via both:

Email, and

SMS, using carrier-provided email-to-text gateways

🛠️ How It Works
Instead of using a paid service like Twilio, this system uses email-to-SMS gateways provided by mobile carriers. These gateways allow a standard email to be converted into a text message. The message is delivered to the user’s phone number via their carrier’s special domain.

For example:

Verizon: 1234567890@vtext.com

AT&T: 1234567890@txt.att.net

T-Mobile: 1234567890@tmomail.net

The app simply sends one email to the user’s regular email address and a second one to their SMS gateway address, both using a built-in email sender (via Nodemailer).

📋 What Users Must Provide
To receive notifications, users must fill out the following fields in their profile:

Phone number (digits only, no spaces or dashes)

Mobile carrier (e.g., Verizon, AT&T, T-Mobile)

Email address

📤 How Messages Are Sent
When the system sends a notification:

It uses the user's email address to send a standard message.

It looks up the user’s carrier and phone number, then constructs the SMS gateway address:

ini
Copy
Edit
sms_address = phone_number + carrier_gateway_domain
It sends a second copy of the same message to that address via email.

For example:

Phone: 3135551234

Carrier: Verizon

SMS address: 3135551234@vtext.com

Both messages are sent using the same email-sending function.

📡 Carrier Gateway Domains
Here are some common carriers and their gateways:

Carrier	SMS Gateway Domain
Verizon	vtext.com
AT&T	txt.att.net
T-Mobile	tmomail.net
Sprint	messaging.sprintpcs.com
Boost Mobile	sms.myboostmobile.com
US Cellular	email.uscc.net

Full list may vary. Users should confirm their gateway with their carrier if needed.

🔍 Monitoring Delivery & Follow-up
Because the system uses email to send notifications, it cannot fully guarantee SMS delivery. However, it can:

Track email delivery success (via SMTP status codes)

Retry failed sends

Optionally send a follow-up message to the user’s email asking them to update their contact info if SMS fails repeatedly

To support this:

The app logs delivery attempts

A periodic job can check for failures and notify users

🔐 Privacy & Consent
Users must explicitly opt in to receive SMS alerts.

Their contact info is only used for notification purposes and is never shared.

Users can opt out anytime via their profile settings.
