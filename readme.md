# Khan Academy Answer Revealer

If this script helped or interested you, please consider starring the repo above. That number looks cool when it's big.

## Usage
1. Download a userscript manager like [TamperMonkey for Chrome](https://chrome.google.com/webstore/detail/tampermonkey/dhdgffkkebhmkfjojejmpbldmpobfkfo?hl=en) or [Greasemonkey for Firefox](https://addons.mozilla.org/en-US/firefox/addon/greasemonkey/) if you haven't already.
2. Use [this link](https://github.com/walesworksltd/khanhack/raw/main/khanrevealer.user.js) to install the script. 
3. Click the extension while in Khan Academy and ensure both the extension and the script are on.
4. Open Developer Tools and go to the Console tab. The script will console log answers as the browser gets them.

## Tips
- Khan Academy always requests the current and next question, so **expect the second to last console log message to be the correct answer**.
- Change your console log settings to the following for a much better experience.
- <img width="332" alt="Screenshot 2022-04-17 at 2 36 25 PM" src="https://user-images.githubusercontent.com/87256750/163703658-693f8e57-ab63-4cbc-aa91-b1b981a17064.png">
- Make sure the console-logged answer makes sense before entering it. This can eliminate question-answer errors.

## Drawbacks
- This works only for expression, free response, multiple choice, and dropdown questions.
- The script will do its best to find the answer in the question data, but some edge case questions do not follow the same structure, therefore they can't be accounted for. Do not be surprised to find a question that you actually have to do.

## Implementation
This should work on any browser supporting userscript integration. It essentially hooks into the browser's `fetch`, which is what Khan Academy uses now instead of `XMLHttpRequest` (this is why the some old exploits no longer work, along with the endpoint change), and when `/getAssessmentItem` is requested, it logs the "important" part of the response.
