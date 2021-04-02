---
title: Process for initial ingest of settings
layout: default
nav_order: 5
---

# Process for initial ingest of settings

## Part One: Gather credentials
1. Begin with a list of each provider you want to harvest from. You will need the following for each:
 1. Name
 2. SUSHI API URL
 3. Which reports to be harvested
2. Sources for provider information:
 1. CC-PLUS provider spreadsheet
 2. COUNTER Registry
 3. Ex Libris list

_Notes: Look at the COUNTER and Ex Libris lists closely. CC-PLUS works with Counter R5, not R4. They may or may not also list the type of credentials that will be needed in the next step and/or the types of reports they make available. These may or may not be up to date, so additional testing to verify these details will be important anyway._


3. Next, for the institutions you plan to work with, you will need some combination of the following credentials per provider:
 1. Requestor id
 2. Customer id
 3. API key
4. Additionally, some providers may require you to send them the IP address you will be making requests from (forthcoming). 
5. Your partner libraries will have to provide these to you unless you control these accounts at the consortium level. 

_Notes: I have found that customer id is almost always required, whereas others vary. Additionally, these details may be complex for your libraries to find and information on what exactly is needed is spotty. It may take some trial and error to figure out what exactly is needed._ 

_Some vendors email them when things are initially set up, others list them on some sort of admin dashboard, and others have the ability to generate new credentials themselves. Obtaining these, and following up when they don’t work is time-consuming._

## Part Two: test credentials and URLs
6. Now we can test that we have the correct URLs and credentials.

_Note: the following instructions describe how to create and test a SUSHI request in a browser. There is a spreadsheet template set up to do this for you at: SUSHI URL template_

_Just fill in columns B-H and then copy the correct URL from columns I-L depending on which credentials are required. Paste that URL into your browser and hit enter. Then jump to step 10 in these directions._

7. First open a browser tab and put in the SUSHI endpoint URL, such as “https://www.jstor.org/sushi/reports/” (don’t hit enter until we complete building the URL in step 10 )
8. Next, add the report you want to request (tr, dr, pr, or ir … tr is the most commonly available) and a “?”, i.e. “https://www.jstor.org/sushi/reports/tr?”
9. Next, add the parameters of your request, joining them with an ampersand:
 1. begin and end dates:(when testing I usually just do a single month) 
  1. Use “begin_date= and “end_date=” with ampersand at the beginning of each
  2. Add date in yyyy-mm-dd format
  3. The resulting URL should look like: https://www.jstor.org/sushi/reports/tr?&begin_date=2020-01-01&end_date=2020-01-31
 2. Requestor Id
  1. Use “requestor_id” to begin the parameter
  2. The text of the requestor id could be an alphanumeric code or an email address
  3. The resulting URL should look like: https://www.jstor.org/sushi/reports/tr?&begin_date=2020-01-01&end_date=2020-01-31&requestor_id=gretchen@palci.org
 3. Customer ID
  1. If the customer id is required, use “customer_id” to begin the parameter
  2. The customer id is usually an alphanumeric code
  3. The resulting URL should look like: https://www.jstor.org/sushi/reports/tr?&begin_date=2020-01-01&end_date=2020-01-31&requestor_id=gretchen@palci.org&customer_id=123456789
If the customer ID isn’t needed, don’t add anything
 4. API Key
  1. Finally, if the API Key is required, use “api_key” to begin the parameter
  2. API key is also usually a long numeric code
  3. The resulting URL should look like:https://www.jstor.org/sushi/reports/tr?&begin_date=2020-01-01&end_date=2020-01-31&requestor_id=gretchen@palci.org&customer_id=123456789&api_key=qjE5365843JNVs468652357
  4. The API Key may be added with or without the customer ID or requestor ID present. If any of these three parameters are not needed, you can just leave the entire statement out. For example, if the customer ID isn’t needed the URL would be: https://www.jstor.org/sushi/reports/tr?&begin_date=2020-01-01&end_date=2020-01-31&requestor_id=gretchen@palci.org&api_key=qjE5365843JNVs468652357
10. Hit enter
11. Now, parse the results…
 1. You will likely receive a response in JSON, a data format. (If you use Google Chrome as your browser, you might want to add this extension to make it easier to read: https://chrome.google.com/webstore/detail/json-formatter/bcjindcccaagfpapjjmafapmmgkkhgoa. This extension is good for Firefox: https://addons.mozilla.org/en-US/firefox/addon/basic-json-formatter/?utm_source=addons.mozilla.org&utm_medium=referral&utm_content=search) 
 2. If the request was successful, you will see something like this, with report items:

[hold for image]

 3. If it is not successful, you may see different types of errors:
  1. HTML errors: this means that the URL is invalid or you’ve made a typo in the root URL. Alternatively, it could mean that the IP address needs to be added to a permissions list by the vendor. In these errors you won’t get any JSON response.
   1. First check that you have all the credentials and URL correct
   2. Next follow up with the provider to see if their server is down or you need the IP address added.
 2. SUSHI errors: with these errors you will see a JSON response, as the example above, but something is preventing your specific request from working. Here is an example:

[hold for image]

 3. Looking underneath the “Exceptions” element, you will see a code, severity, and message. A list of the typical codes we see and what needs to be fixed is at: https://docs.google.com/spreadsheets/d/1aNatq9KDmwYHTn0EYugGEKJF20q0C6fIcYe24xbvFTA/edit#gid=0 
12. If you got a successful response, you may want to query to see which reports are available. You can do this by 
 1. removing the part of your URL with the report name,(e.g. “/tr”)
 2. removing begin and end dates
 3. Your URL will look like this: https://www.jstor.org/sushi/reports?&requestor_id=gretchen@palci.org&customer_id=123456789&api_key=qjE5365843JNVs468652357
 4. The response will list every Master report and “View” provided. CC-PLUS will only retrieve the master reports, so make a note of those if you wish.
13. If this process was successful, the credentials and URL are correct and you can add them to your bulk upload spreadsheet.

## Part Three: format spreadsheets
14. Begin with the providers spreadsheet template https://docs.google.com/spreadsheets/d/16O1FNPN5dWK_H0A8PDZ7V5avq8jmj7Sxy-AK8azRyfM/edit#gid=0: 
 1. On each row fill in the following:
  1. ID: assign a number that will be the id for the provider. Any number is fine as long as it doesn’t duplicate. We suggest you just number them sequentially as you add them: 1, 2, 3, etc.
  2. Active: this requires either a “Y” or “N”. You will want all of the providers to be “Y” to start.
  3. Server URL: put the complete URL here with the beginning “http://” etc.
  4. Harvest Day: this is the day each month that CC-PLUS will try to harvest data from the provider. Just put in a number for the day you’d like it to run, such as “15” or “28”. Don’t use anything higher than 28 to ensure that the harvest will work each month
  5. Institution ID: The number in this column will correspond with which institutions can be connected to this provider. To start, put a “1” in this column for every row. This will allow the provider to be seen by all institutions.
  6. Master Reports: this column contains which reports should be harvested for each provider. They are separated by a comma. The numbers for each report are the following:
   1. TR - 1
   2. DR = 2
   3. PR = 3
   4. IR = 4
 2. You can see an example of a filled in spreadsheet at: https://docs.google.com/spreadsheets/d/1RToVaKecmdigbTOQzXA0K2aKFiBzZOD7UteQvI7KvyU/edit#gid=798046110 

 3. Save the file (a single sheet) as a comma separated values file, or “.csv”
15. Go to the “Providers” page in CC-PLUS and hit the “import providers” button.
16. Follow the steps on the dialog box that pops up to add your spreadsheet.
17. Next, you will create your institutions spreadsheet https://docs.google.com/spreadsheets/d/1Uw2Q0mxkLvtXJs25sw2iVvjcIAPBCKchdBs5j836Wzc/edit#gid=0.  
This one is more complicated and you will need to re-use the id numbers from the provider spreadsheet, so keep it open for reference.
 1. Each institution will have a numeric ID number. These are just numbers. They cannot be repeated within the institution list, but can be the same as those used for providers. DO NOT USE THE ID “1.” This is reserved for the Entire Consortium as a group and should not be overwritten.
 2. On the first line fill in the following for your first institution:
  1. ID: number to identify the institution of “2” or higher
  2. Active: this requires either a “Y” or “N”. You will want all of the institutions to be “Y” to start.
  3. TypeID: these correspond to the Institution Types. You can choose an ID from the list at: https://drive.google.com/file/d/1WjqW4Htn0pgdCp3bxVnXbHEjGMNXBWh-/view?usp=sharing, or just use “1” for “not classified”. You can also create and upload a new list of institution types of your own. This will need to be done before uploading the institution list.
  4. Group IDs: similar to type ID, these are for groupings that you will create in CC-PLUS. For now, leave this column blank.
  5. FTE: this is for a numeric count of FTE at the institution if you would like to record it. You may leave this field blank.
  6. Notes: if you would like to make any kind of textual note in this field you may. 
 3. From column H - forward, we will be recording specific credentials for the institution you are creating and a specific provider. Other than H, any of these may be blank if they are not needed:
  1. Provider ID: Look back and your provider list and find the ID number of the one you want to work with first. Put that ID in column H
  2. Customer ID: now record the customer ID for this institution and that specific provider
  3. Requestor ID: again, the requestor ID for that provider
  4. API Key: and the API Key if it is needed
  5. Support email: you may also add the email of a support contact at the provider if you wish
 3. If you want to connect this institution with another provider, in the next row, fill in:
  1. ID: repeat the institution ID here. IDs must be unique between institutions, but will be repeated in this spreadsheet for every provider you are connecting them with
  2. Columns B-G are blank
  3. Fill in columns H - L with information pertaining to the next provider
 4. When you have added all the providers to the institution, begin back at step “b” for the next institution on the next row.
 5. You can see an example of a filled-in spreadsheet at: https://docs.google.com/spreadsheets/d/1UMEaGL1nMzd0r7TGgIYm6qyV_tYQhVOmsSKcX481d80/edit#gid=769174846 

18. Go to the Institution page and click the “Import Institutions” button. Again, follow the instructions in the dialog to add the spreadsheet.

## Part Four: User Accounts
_NOTE: BULK UPLOAD FOR USERS IS NOT YET WORKING!!!_

19. Finally, you can also create an import spreadsheet for User accounts: https://docs.google.com/spreadsheets/d/1qZEZpMlzHfpj8PcOK-XjjTUVO5D6S3r1L67m6L9f6eI/edit#gid=0 
 1. Id: As with the other spreadsheets, create a unique ID number within the sheet for each user
 2. Email: a unique email address is required for each user. They will use this email as their login username
 3. Password: create an initial password for the user that you will share with them
 4. Name: Full name of the user in one field
 5. Phone: This field is optional
 6. Active: default to “Y” for new users
 7. Roles: This field must contain some combination of the following roles, separated by columns:
  1. Admin: can create and manage settings for all users, institutions, and providers
  2. Manager: can manage settings for their own institutions and can create and manage users within their institution
  3. User: can view statistics for their own institution
  4. Viewer: can view statistics for all institutions

_Note: Roles other than Admin are meant to be used in combination. So Managers must also be either users or viewers in order to both see reports and manage settings._

 8. PWChangeReq: Using “Y” in this field will prompt the user to change the initial password on their first login. “N” will allow them to continue to use the temporary password you put in column C
 9. Institution ID: put the numeric ID from the Institution Spreadsheet for the institution this user belongs to
20. Save as a .csv file. An example of a filled in spreadsheet is at: https://docs.google.com/spreadsheets/d/1v6mImadDPRXE5rcbMIDwzbrVF3_lJ2bKcQgyh_x7Nf0/edit#gid=765756035 
21. Go to the Institution page and click the “Import Institutions” button. Again, follow the instructions in the dialog to add the spreadsheet.