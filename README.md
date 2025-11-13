# rube_automation
Here is a automated workflow to send sponsorship emails to companies with AI automation using rube.app.

What is rube.app?
  Rube.app is a platform that connects AI assistants like ChatGPT or Claude to hundreds of apps—such as Gmail, Slack, Notion, and Google Sheets—so they can actually perform actions instead of just giving      advice. Once you link your accounts, you can tell the AI to automate multi-step workflows across your tools, like turning an email into a task or updating a spreadsheet and posting a summary in Slack.       It’s designed to simplify automation for individuals and teams without coding, though it still requires careful setup and permission management since it handles access to multiple connected services.

How to use this to send sponsorship emails to companies:

1) **Prep your Google files**

Open this Google Sheet on the account you want to send emails to companies with (ACM sponsorship email): [https://docs.google.com/spreadsheets/d/1bRzLqmsVaQ_jcUhSCImegs8BoNCb4_Dkvp1NB5l4x8s/edit?usp=sharing](url)
Open the Google Doc template on the account you want to send emails to companies with (ACM sponsorship email): [https://docs.google.com/document/d/1iFhftFxQAon6HYov4kv6kw0hX-3y959WstTwjT8d_1Q/edit?usp=sharing](url)

Share settings: give your rube.app Google connection access. Practically, this means:
The Sheet and Doc must be accessible to the same Google account you connect in rube.app.
If your org locks sharing down, add your own Google account and confirm you can open both links in the same browser profile you’ll use for rube.app.


**2) Set up rube.app
**Log in to rube.app and paste the YAML workflow into the textbox.
After that, follow the instructions it gives you. This may include connecting apps such as gmail and google sheets, docs, etc...


**3) Provide the inputs
**When you run the workflow, rube.app will prompt you for these:

user_cc_email: Your email to CC on every message. Example: you@school.edu

sender_full_name: The name to appear in the “From” display. Example: Taylor Nguyen

sheet_url: Your Sheet link. You can keep the default if it’s your link already, or paste yours.

template_doc_url: Your Google Doc template link. You can keep the default if it’s your link already, or paste yours.

batch_size (optional): Defaults to 10. Change only if you want smaller/larger batches.

column_map (optional): Only touch this if your Sheet uses different header names. Otherwise leave as is.



**4) Do a quick test (strongly recommended)
**
In your Sheet, add a single test row with your own email in Recruiter Email.
Run the workflow. When it shows the preview of the first batch, confirm sending.
Check your Gmail “Sent” to see the email and formatting.
Check the Sheet to see the tracking columns updated for that row.

**It is configured to send 10 emails at a time after explicit confirmation from the user. This is because we do not want Gmail to flag the ACM Sponsorship email as a potential spam account.
**

If the email does not show up the way you want it, then you can always prompt rube.app to change it how you want it. Make sure to not make too many changes though...

**5) Run the real thing
**
Run the workflow again with your real Sheet.
rube.app will show a preview list of up to 10 recipients in the batch:
You’ll see the company, contact name, and email for each.

It will ask:
Confirm sending this batch? Type yes to send or no to skip.
What name should I use (first and last name)? Enter the sender name you want on the emails.
After sending a batch, you’ll get a summary and a question to continue. Say yes to process the next 10, or no to stop.

**6) How personalization works
**
The subject line is always BeachHacks Sponsorship.
The placeholders in your Doc will be replaced with:
Company → the value in Company
Recruiter/Contact name → the value in Recruiter Name, or “University Relations Team” if blank
Sender → the sender_full_name you provide at run time
Each email is sent:
To: the contact’s Recruiter Email
CC: your user_cc_email
From name: your sender_full_name (the Gmail account connected to rube.app actually sends it)


**8) Common problems and quick fixes
**
Missing permissions: If rube.app can’t read or write, reconnect Google in rube.app, then ensure the Sheet and Doc are accessible to that same Google account.
Header names don’t match: Either rename your Sheet headers to the defaults or edit column_map in the input to match your actual header text exactly.
Placeholders not changing: Make sure your Doc uses one of the listed placeholder patterns. If your placeholders are different, add them to the replacement list in the YAML or change the Doc to match.
Recruiter name is blank: The workflow uses “University Relations Team.” That’s expected.
Gmail sending limits: If you’re sending lots of emails, keep batch sending spread out if your account has limits.

**9) Tips for a smooth run
**
Keep your Sheet clean: one header row, then data. No merged cells in the header.
Make sure every row has a valid Recruiter Email.
If you need to pause between batches, just answer no when asked to continue. You can re-run later, and it will pick up unsent rows.
Want a different batch size? Change batch_size when starting.
