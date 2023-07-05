# Google Calendar Shoe Release Scheduler

    #### Description:

        This program allows a user to schedule a notification to their Google calendar for sneaker releases. This program accomplishes this by first displaying a main menu which asks a user to enter a number associated with a menu option. The option is validated so the user is only allowed to select a number in the range 1-4. If the user enters 4 it quits the program.

        If another option in range is selected, the program has a pre determined list of links that webscrape shoe release information for a single link or all links in the list depending on your menu selection. The data comes from "sneakernews.com" which tracks shoe releases for Jordans, Yeezys, and all other high-end sneakers. Once the info is scraped, each item's release date can come formatted in 1 of 3 ways. The program uses regex to determine what format is being recieved then reformats it into an actual date object. Once the release date is "cleaned", all info per item scraped is then saved as a dictionary object stored in a list containing all items scraped.

        The program then nicely outputs each sneaker release to the terminal prepended by a number and asks the user if they would like to schedule a notification. If they select no, the program ends. If they do wish to schedule a notification, they must enter y. Once it's determined a notification would like to be created, the user is then prompted to enter the number of the release they wish to schedule. Both of these prompts are validated and won't let you continue if the selection isn't valid. 

        Once the user inputs a valid release option, a confirmation message appears asking the user to verify their selection. Since there may be multiple releases with the same name, the confirmation also shows the "size run" of that release which shows if the release is for mens, womans, kids, or toddler/infants. The size run determines what the cost will be so the verification is done so the accurate data ends up on the calendar. 

        Finally, once the user's release selection is confirmed, the program uses the Google api to connect to your Google calendar. This must be enabled before you run the program on the Google Cloud console side - you'll need to follow these instructions to set this up: https://developers.google.com/calendar/api/quickstart/python

        After you enable the caledar api on your Google account, and the program is running, if it's the program's first run - you will be prompted through the browser to login to your Google account. Once logged in, a token.json file is created to allow access on all following runs. After the account login is complete, the program uses the details from the selected shoe release's dict object to create an event on the sneaker's release date populating the body with the cost, size run, color, style code, and reigon being released. The user then is prompted to create another event if they desire. If not (they select n), then the program ends, but if they do, the entire process starts again.