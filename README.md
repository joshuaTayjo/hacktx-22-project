# Inbox Zero
This project was created for the 2022 Hack Tx hosted at UT Austin. 
## Inspiration

Time is valuable. We wanted to find a way to better understand who you are getting the most emails from, where your email is subscribed to, and a lot more with a simple click of an icon and be able to manage that data. There is no need to go through all those unnecessary emails when trying to save storage with the chrome extension we created, it is a major time saver.

## What it does

Our program goes through and reads a large portion of your most recent emails when the gmail site is open, and evaluates data such as the opening rate of emails from certain domains, the domains themself, and the subdomain. In a separate webpage the data is shown and it gives you the ability to search a certain keyword (ex.- "utexas" or "canvas") and send those emails to your trash or clear filters.

## How we built it

Extension is built using ReactJs and Semantic React UI,
Backend is hosted on GCP
Data is sourced from Gmail's APIs for developers.
Data is cached in a file based DB.
APIs are server-less
Gmail API returns only 500 emails in a single request call, so periodically data is pulled with the help of a Google cron job. We trigger 10 asynchronous parallel calls using GCP multiple instance feature and cached it. The data is then parsed the data in server less function in GCP and it is sourced to the plugin .

## Challenges we ran into

Gmail API returns an array of only 500 email identified by an id in a single request call. Post which 500 individual calls had to be made to fetch information specific to an email. This consumed 2 minutes for a batch of 500 emails. We required on an average 5000 emails to perform analytics, which would have taken 20 minutes.

## Accomplishments that we're proud of

Created a MVP to get analytics on 5000 emails from a vague idea.

## What we learned

Researched services hosted on google infrastructure such as serverless APIs, Google Job, databases such as firebase and cockroachDB, authentication such as API keys and Oauth.

## What's next for Zero Inbox (Chrome Extension)

In depth analytics such as email categorization, frequency of emails and capability to perform operations such as unsubscribe.

