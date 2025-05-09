<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Notes on Apps Script</title>
    <style>
        body {
            background-color: #0f0f0f;
            color: #f0f0f0;
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            margin: 0;
            padding: 0;
            line-height: 1.6;
        }
        
        .container {
            max-width: 800px;
            margin: 0 auto;
            padding: 20px;
        }
        
        header {
            text-align: center;
            padding: 40px 0;
            border-bottom: 1px solid #333;
        }
        
        h1 {
            font-size: 36px;
            margin-bottom: 10px;
            color: #f0f0f0;
        }
        
        h2 {
            font-size: 24px;
            margin-top: 30px;
            color: #f0f0f0;
            border-bottom: 1px solid #333;
            padding-bottom: 5px;
        }
        
        ul, ol {
            margin-left: 20px;
            margin-bottom: 20px;
        }
        
        li {
            margin-bottom: 10px;
        }
        
        a {
            color: #72b6ff;
            text-decoration: none;
        }
        
        a:hover {
            text-decoration: underline;
        }
        
        .section {
            margin: 40px 0;
        }
        
        .highlight {
            background-color: #1a1a1a;
            padding: 15px;
            border-radius: 5px;
            margin: 20px 0;
        }
        
        .pros-cons {
            display: flex;
            flex-wrap: wrap;
            gap: 20px;
            margin: 20px 0;
        }
        
        .pros, .cons {
            flex: 1;
            min-width: 300px;
            background-color: #1a1a1a;
            padding: 15px;
            border-radius: 5px;
        }
        
        .pros h3 {
            color: #72ffa2;
        }
        
        .cons h3 {
            color: #ff7272;
        }
        
        .interactive-demo {
            background-color: #1a1a1a;
            padding: 20px;
            border-radius: 5px;
            margin: 30px 0;
        }
        
        .interactive-demo h3 {
            color: #72b6ff;
            margin-top: 0;
        }
        
        .timeline {
            position: relative;
            max-width: 1200px;
            margin: 40px auto;
        }
        
        .timeline::after {
            content: '';
            position: absolute;
            width: 6px;
            background-color: #333;
            top: 0;
            bottom: 0;
            left: 50%;
            margin-left: -3px;
        }
        
        .timeline-container {
            padding: 10px 40px;
            position: relative;
            background-color: inherit;
            width: 50%;
        }
        
        .timeline-container::after {
            content: '';
            position: absolute;
            width: 20px;
            height: 20px;
            right: -10px;
            background-color: #1a1a1a;
            border: 4px solid #72b6ff;
            top: 15px;
            border-radius: 50%;
            z-index: 1;
        }
        
        .left {
            left: 0;
        }
        
        .right {
            left: 50%;
        }
        
        .left::before {
            content: " ";
            height: 0;
            position: absolute;
            top: 22px;
            width: 0;
            z-index: 1;
            right: 30px;
            border: medium solid #333;
            border-width: 10px 0 10px 10px;
            border-color: transparent transparent transparent #333;
        }
        
        .right::before {
            content: " ";
            height: 0;
            position: absolute;
            top: 22px;
            width: 0;
            z-index: 1;
            left: 30px;
            border: medium solid #333;
            border-width: 10px 10px 10px 0;
            border-color: transparent #333 transparent transparent;
        }
        
        .right::after {
            left: -10px;
        }
        
        .timeline-content {
            padding: 20px;
            background-color: #1a1a1a;
            position: relative;
            border-radius: 6px;
        }
        
        .back-link {
            display: inline-block;
            margin-top: 40px;
            background-color: #72b6ff;
            color: #0f0f0f;
            padding: 10px 20px;
            border-radius: 5px;
            font-weight: bold;
            transition: background-color 0.3s;
        }
        
        .back-link:hover {
            background-color: #5a9ae6;
            text-decoration: none;
        }
        
        .code-snippet {
            background-color: #252525;
            padding: 15px;
            border-radius: 5px;
            overflow-x: auto;
            font-family: 'Courier New', Courier, monospace;
            margin: 20px 0;
        }
    </style>
</head>
<body>
    <div class="container">
        <header>
            <h1>Notes on Apps Script (AS)</h1>
            <p>A comprehensive guide to Google Apps Script</p>
        </header>
        
        <div class="section">
            <h2>Understanding Apps Script (5Ws)</h2>
            <ul>
                <li><strong>What?</strong> It's a cloud-based scripting language that uses a modified version of JavaScript with built-in libraries specific to Google services</li>
                <li><strong>Who?</strong> Anyone who has an account on Google {especially students, teachers, coders}</li>
                <li><strong>Where?</strong> Inside Google Sheets/Docs → Extensions → Apps Script<br>Or directly: <a href="https://script.google.com" target="_blank">script.google.com</a></li>
                <li><strong>When?</strong> When prototyping ideas before building more complex solutions</li>
                <li><strong>Why?</strong> Saves time; Serverless; No cost for most use cases</li>
            </ul>
        </div>
        
        <div class="section">
            <h2>Potential Uses of Apps Script</h2>
            <ol>
                <li><strong>Build an auto grader for quizzes or exams:</strong> Use Forms to take student answers, and Apps Script to auto-grade and email results.</li>
                <li><strong>Simple Login System for sites</strong></li>
                <li><strong>Goal Tracker with Reminders:</strong> Log goals in Sheets to get weekly progress emails see person's growth visualized.</li>
            </ol>
        </div>
        
        <div class="section">
            <h2>AI Conversation Reference</h2>
            <p>Check out this conversation about Apps Script: <a href="https://chatgpt.com/share/680dd228-3f5c-8006-a261-69a2276b2a35" target="_blank">ChatGPT Conversation Link</a></p>
        </div>
        
        <div class="section">
            <h2>Pros and Cons of Using Apps Script</h2>
            <div class="pros-cons">
                <div class="pros">
                    <h3>Pros</h3>
                    <ol>
                        <li>Seamless Google integration</li>
                        <li>No installation needed</li>
                        <li>Free for Most Use Cases</li>
                        <li>Minimal setup for creating functional applications</li>
                        <li>Can connect to other services</li>
                    </ol>
                </div>
                <div class="cons">
                    <h3>Cons</h3>
                    <ol>
                        <li>Limited usage: 6-minute runtime limit per execution</li>
                        <li>Internet required</li>
                        <li>A bit slow for some parts</li>
                        <li>Script sharing can potentially expose sensitive data</li>
                        <li>Doesn't have advanced debugging tools</li>
                    </ol>
                </div>
            </div>
        </div>
        
        <div class="section">
            <h2>My Learning Journey</h2>
            <div class="timeline">
                <div class="timeline-container left">
                    <div class="timeline-content">
                        <h3>Initial Discovery</h3>
                        <p>At first I didn't understand what AS was after hearing the name. It was definitely something brand new to me.</p>
                    </div>
                </div>
                <div class="timeline-container right">
                    <div class="timeline-content">
                        <h3>Information Gathering</h3>
                        <p>I started gathering information from GPT and Google and got a lot of information, but still didn't have an overall understanding.</p>
                    </div>
                </div>
                <div class="timeline-container left">
                    <div class="timeline-content">
                        <h3>First Attempts</h3>
                        <p>I began writing notes and gained some basic knowledge about AS. However, I mostly understood after trying to do it by myself.</p>
                    </div>
                </div>
                <div class="timeline-container right">
                    <div class="timeline-content">
                        <h3>Practical Application</h3>
                        <p>I created a CWG by looking at the professor's table, but I realized that I had some errors and again I asked GPT about my problems.</p>
                    </div>
                </div>
                <div class="timeline-container left">
                    <div class="timeline-content">
                        <h3>Problem Solving</h3>
                        <p>After fixing my problem and creating my script with grades, I had some difficulties finding a link to my script and Diana helped with this.</p>
                    </div>
                </div>
                <div class="timeline-container right">
                    <div class="timeline-content">
                        <h3>Iteration & Improvement</h3>
                        <p>I rewrote my notes by using GPT again with better prompts and got even more information. I think I gained much more understanding after rewriting my notes.</p>
                    </div>
                </div>
            </div>
        </div>
        
        <div class="section">
            <h2>Interactive Demo: Simple Apps Script</h2>
            <div class="interactive-demo">
                <h3>Sample Code: Email Reminder Script</h3>
                <div class="code-snippet">
function sendReminderEmails() {<br>
  // Get the spreadsheet and sheet<br>
  var sheet = SpreadsheetApp.getActiveSpreadsheet().getSheetByName("Goals");<br>
  var dataRange = sheet.getDataRange();<br>
  var values = dataRange.getValues();<br>
  <br>
  // Get today's date<br>
  var today = new Date();<br>
  <br>
  // Loop through each row<br>
  for (var i = 1; i < values.length; i++) {<br>
    var row = values[i];<br>
    var email = row[0];       // Email in column A<br>
    var goalName = row[1];    // Goal name in column B<br>
    var deadline = row[2];    // Deadline in column C<br>
    var status = row[3];      // Status in column D<br>
    <br>
    // Calculate days until deadline<br>
    var daysUntil = Math.round((deadline - today) / (1000 * 60 * 60 * 24));<br>
    <br>
    // If deadline is within 3 days and status is not "Complete"<br>
    if (daysUntil <= 3 && daysUntil >= 0 && status != "Complete") {<br>
      // Send reminder email<br>
      var subject = "Goal Reminder: " + goalName;<br>
      var message = "Hello,\n\n" +<br>
                   "This is a reminder that your goal '" + goalName + "' is due in " + daysUntil + " days.\n\n" +<br>
                   "Current Status: " + status + "\n\n" +<br>
                   "Keep up the good work!\n\n" +<br>
                   "Goal Tracker System";<br>
      <br>
      MailApp.sendEmail(email, subject, message);<br>
    }<br>
  }<br>
}
                </div>
                <p>This script reads a Google Sheet containing goals, deadlines, and statuses, then sends reminder emails for goals that are due within 3 days and are not yet complete.</p>
                <p>To implement this:</p>
                <ol>
                    <li>Create a Google Sheet with columns for Email, Goal Name, Deadline, and Status</li>
                    <li>Go to Extensions → Apps Script</li>
                    <li>Paste this code and save</li>
                    <li>Set up a time-based trigger to run the script daily</li>
                </ol>
            </div>
        </div>

        <div class="section">
            <h2>Visualization: Apps Script Ecosystem</h2>
            <div class="highlight">
                <svg viewBox="0 0 800 400" xmlns="http://www.w3.org/2000/svg">
                    <!-- Central Apps Script Node -->
                    <circle cx="400" cy="200" r="60" fill="#72b6ff" />
                    <text x="400" y="200" text-anchor="middle" alignment-baseline="middle" fill="#0f0f0f" font-weight="bold" font-size="14">Google Apps Script</text>
                    
                    <!-- Outer Service Nodes -->
                    <circle cx="200" cy="100" r="40" fill="#1a1a1a" stroke="#72b6ff" stroke-width="2" />
                    <text x="200" y="100" text-anchor="middle" alignment-baseline="middle" fill="#f0f0f0" font-size="12">Sheets</text>
                    
                    <circle cx="600" cy="100" r="40" fill="#1a1a1a" stroke="#72b6ff" stroke-width="2" />
                    <text x="600" y="100" text-anchor="middle" alignment-baseline="middle" fill="#f0f0f0" font-size="12">Docs</text>
                    
                    <circle cx="200" cy="300" r="40" fill="#1a1a1a" stroke="#72b6ff" stroke-width="2" />
                    <text x="200" y="300" text-anchor="middle" alignment-baseline="middle" fill="#f0f0f0" font-size="12">Forms</text>
                    
                    <circle cx="600" cy="300" r="40" fill="#1a1a1a" stroke="#72b6ff" stroke-width="2" />
                    <text x="600" y="300" text-anchor="middle" alignment-baseline="middle" fill="#f0f0f0" font-size="12">Calendar</text>
                    
                    <circle cx="100" cy="200" r="40" fill="#1a1a1a" stroke="#72b6ff" stroke-width="2" />
                    <text x="100" y="200" text-anchor="middle" alignment-baseline="middle" fill="#f0f0f0" font-size="12">Gmail</text>
                    
                    <circle cx="700" cy="200" r="40" fill="#1a1a1a" stroke="#72b6ff" stroke-width="2" />
                    <text x="700" y="200" text-anchor="middle" alignment-baseline="middle" fill="#f0f0f0" font-size="12">Drive</text>
                    
                    <!-- Connection Lines -->
                    <line x1="400" y1="200" x2="200" y2="100" stroke="#72b6ff" stroke-width="2" />
                    <line x1="400" y1="200" x2="600" y2="100" stroke="#72b6ff" stroke-width="2" />
                    <line x1="400" y1="200" x2="200" y2="300" stroke="#72b6ff" stroke-width="2" />
                    <line x1="400" y1="200" x2="600" y2="300" stroke="#72b6ff" stroke-width="2" />
                    <line x1="400" y1="200" x2="100" y2="200" stroke="#72b6ff" stroke-width="2" />
                    <line x1="400" y1="200" x2="700" y2="200" stroke="#72b6ff" stroke-width="2" />
                </svg>
            </div>
        </div>
        
        <a href="https://dioram8.github.io/website/" class="back-link">Back to Main Website</a>
    </div>
</body>
</html>
