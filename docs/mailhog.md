# MailHog

MailHog is installed as a separate container and can be accessed through [http://localhost:8025](http://localhost:8025) when the project is running. 
It is set up to be used if the new `JCORE_IS_LOCAL` constant is present and true, meaning all emails are rerouted to the MailHog instance and can be inspected there. 
No further configuration is needed. Mailgun conflicts with this plugin, so that plugin is by default disabled if the `JCORE_IS_LOCAL` constant is defined as true.
