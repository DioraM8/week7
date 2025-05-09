<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Notes on Apps Script</title>
    <link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@400;700&family=Quicksand:wght@400;700&display=swap" rel="stylesheet">
    <style>
        :root {
            --purple-primary: #8A2BE2;
            --blue-primary: #4169E1;
            --pink-primary: #FF69B4;
            --dark-bg: #0F1234;
            --light-text: #F2F2FF;
        }
        
        body {
            font-family: 'Quicksand', sans-serif;
            line-height: 1.6;
            margin: 0;
            padding: 0;
            background: linear-gradient(135deg, #0F1234, #1F1456);
            color: var(--light-text);
            perspective: 1000px;
            min-height: 100vh;
            overflow-x: hidden;
        }
        
        .container {
            max-width: 850px;
            margin: 40px auto;
            background: rgba(25, 25, 50, 0.8);
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 15px 35px rgba(138, 43, 226, 0.3), 
                        0 5px 15px rgba(65, 105, 225, 0.4);
            backdrop-filter: blur(5px);
            border: 1px solid rgba(255, 105, 180, 0.2);
            transform-style: preserve-3d;
            animation: float 6s ease-in-out infinite;
        }
        
        @keyframes float {
            0% { transform: translateY(0px) rotateX(2deg) rotateY(-2deg); }
            50% { transform: translateY(-15px) rotateX(3deg) rotateY(2deg); }
            100% { transform: translateY(0px) rotateX(2deg) rotateY(-2deg); }
        }
        
        h1 {
            font-family: 'Orbitron', sans-serif;
            color: var(--pink-primary);
            text-align: center;
            border-bottom: 2px solid var(--blue-primary);
            padding-bottom: 15px;
            text-shadow: 0 0 10px rgba(255, 105, 180, 0.7);
            letter-spacing: 2px;
            font-size: 2.5rem;
            margin-bottom: 30px;
            animation: glow 3s ease-in-out infinite alternate;
        }
        
        @keyframes glow {
            from { text-shadow: 0 0 5px rgba(255, 105, 180, 0.7), 0 0 10px rgba(138, 43, 226, 0.5); }
            to { text-shadow: 0 0 15px rgba(255, 105, 180, 0.9), 0 0 20px rgba(138, 43, 226, 0.8), 0 0 30px rgba(65, 105, 225, 0.7); }
        }
        
        h2 {
            font-family: 'Orbitron', sans-serif;
            color: var(--blue-primary);
            margin-top: 40px;
            padding-left: 15px;
            border-left: 4px solid var(--purple-primary);
            text-shadow: 0 0 5px rgba(65, 105, 225, 0.5);
            letter-spacing: 1px;
            transform: translateZ(10px);
        }
        
        .section {
            margin: 40px 0;
        }
        
        ul, ol {
            margin-left: 20px;
            margin-bottom: 20px;
        }
        
        li {
            margin-bottom: 10px;
        }
        
        a {
            color: var(--pink-primary);
            text-decoration: none;
            text-shadow: 0 0 3px rgba(255, 105, 180, 0.5);
            transition: all 0.3s ease;
        }
        
        a:hover {
            text-decoration: underline;
            color: var(--blue-primary);
        }
        
        .report {
            text-align: justify;
            margin-bottom: 30px;
            padding: 20px;
            border-radius: 10px;
            background: rgba(15, 18, 52, 0.5);
            box-shadow: inset 0 0 15px rgba(138, 43, 226, 0.2);
            transform: translateZ(5px);
        }
        
        .highlight {
            background: rgba(15, 18, 52, 0.5);
            padding: 15px;
            border-radius: 10px;
            margin: 20px 0;
            box-shadow: inset 0 0 15px rgba(138, 43, 226, 0.2);
            transform: translateZ(5px);
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
            background: rgba(15, 18, 52, 0.5);
            padding: 20px;
            border-radius: 10px;
            box-shadow: inset 0 0 15px rgba(138, 43, 226, 0.2);
            transform: translateZ(5px);
        }
        
        .pros h3 {
            color: #00FF9C;
            font-family: 'Orbitron', sans-serif;
            text-shadow: 0 0 5px rgba(0, 255, 156, 0.5);
        }
        
        .cons h3 {
            color: var(--pink-primary);
            font-family: 'Orbitron', sans-serif;
            text-shadow: 0 0 5px rgba(255, 105, 180, 0.5);
        }
        
        .interactive-demo {
            background: rgba(15, 18, 52, 0.5);
            padding: 20px;
            border-radius: 10px;
            margin: 30px 0;
            box-shadow: inset 0 0 15px rgba(138, 43, 226, 0.2);
            transform: translateZ(5px);
        }
        
        .interactive-demo h3 {
            color: var(--blue-primary);
            font-family: 'Orbitron', sans-serif;
            margin-top: 0;
            text-shadow: 0 0 5px rgba(65, 105, 225, 0.5);
        }
        
        .code-snippet {
            font-family: 'Courier New', monospace;
            background: rgba(25, 25, 60, 0.7);
            padding: 25px;
            border-radius: 10px;
            border-left: 4px solid var(--blue-primary);
            overflow-x: auto;
            color: #00FF9C;
            text-shadow: 0 0 5px rgba(0, 255, 156, 0.5);
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.3);
            transform: translateZ(15px);
            animation: mapPulse 4s infinite alternate;
            margin: 20px 0;
            line-height: 1.5;
        }
        
        @keyframes mapPulse {
            0% { box-shadow: 0 0 10px rgba(65, 105, 225, 0.5); }
            100% { box-shadow: 0 0 20px rgba(138, 43, 226, 0.8), 0 0 30px rgba(255, 105, 180, 0.5); }
        }
        
        strong {
            color: var(--pink-primary);
            font-weight: 700;
            text-shadow: 0 0 3px rgba(255, 105, 180, 0.5);
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
            background: var(--purple-primary);
            top: 0;
            bottom: 0;
            left: 50%;
            margin-left: -3px;
            box-shadow: 0 0 10px rgba(138, 43, 226, 0.8);
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
            background-color: var(--dark-bg);
            border: 4px solid var(--blue-primary);
            top: 15px;
            border-radius: 50%;
            z-index: 1;
            box-shadow: 0 0 10px rgba(65, 105, 225, 0.8);
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
            border: medium solid var(--purple-primary);
            border-width: 10px 0 10px 10px;
            border-color: transparent transparent transparent var(--purple-primary);
        }
        
        .right::before {
            content: " ";
            height: 0;
            position: absolute;
            top: 22px;
            width: 0;
            z-index: 1;
            left: 30px;
            border: medium solid var(--purple-primary);
            border-width: 10px 10px 10px 0;
            border-color: transparent var(--purple-primary) transparent transparent;
        }
        
        .right::after {
            left: -10px;
        }
        
        .timeline-content {
            padding: 20px;
            background: rgba(15, 18, 52, 0.5);
            position: relative;
            border-radius: 10px;
            box-shadow: inset 0 0 15px rgba(138, 43, 226, 0.2), 0 5px 15px rgba(0, 0, 0, 0.3);
            transform: translateZ(5px);
        }
        
        .timeline-content h3 {
            color: var(--blue-primary);
            font-family: 'Orbitron', sans-serif;
            margin-top: 0;
            text-shadow: 0 0 5px rgba(65, 105, 225, 0.5);
        }
        
        .back-link {
            display: inline-block;
            margin-top: 40px;
            background: linear-gradient(45deg, var(--purple-primary), var(--blue-primary));
            color: var(--light-text);
            padding: 10px 20px;
            border-radius: 10px;
            font-weight: bold;
            transition: all 0.3s ease;
            text-shadow: 0 0 5px rgba(255, 255, 255, 0.5);
            box-shadow: 0 5px 15px rgba(138, 43, 226, 0.5);
            transform: translateZ(10px);
            border: 1px solid rgba(255, 105, 180, 0.3);
            animation: borderGlow 3s infinite alternate;
        }
        
        @keyframes borderGlow {
            from { border-color: var(--purple-primary); }
            to { border-color: var(--pink-primary); }
        }
        
        .back-link:hover {
            background: linear-gradient(45deg, var(--blue-primary), var(--purple-primary));
            transform: translateZ(15px) scale(1.05);
            box-shadow: 0 8px 20px rgba(138, 43, 226, 0.7);
            text-decoration: none;
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
            <div class="report">
                <ul>
                    <li><strong>What?</strong> It's a cloud-based scripting language that uses a modified version of JavaScript with built-in libraries specific to Google services</li>
                    <li><strong>Who?</strong> Anyone who has an account on Google {especially students, teachers, coders}</li>
                    <li><strong>Where?</strong> Inside Google Sheets/Docs → Extensions → Apps Script<br>Or directly: <a href="https://script.google.com" target="_blank">script.google.com</a></li>
                    <li><strong>When?</strong> When prototyping ideas before building more complex solutions</li>
                    <li><strong>Why?</strong> Saves time; Serverless; No cost for most use cases</li>
                </ul>
            </div>
        </div>
        
        <div class="section">
            <h2>Potential Uses of Apps Script</h2>
            <div class="report">
                <ol>
                    <li><strong>Build an auto grader for quizzes or exams:</strong> Use Forms to take student answers, and Apps Script to auto-grade and email results.</li>
                    <li><strong>Simple Login System for sites</strong></li>
                    <li><strong>Goal Tracker with Reminders:</strong> Log goals in Sheets to get weekly progress emails see person's growth visualized.</li>
                </ol>
            </div>
        </div>
        
        <div class="section">
            <h2>AI Conversation Reference</h2>
            <div class="report">
                <p>Check out this conversation about Apps Script: <a href="https://chatgpt.com/share/680dd228-3f5c-8006-a261-69a2276b2a35" target="_blank">ChatGPT Conversation Link</a></p>
            </div>
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
function sendReminderEmails() {
  // Get the spreadsheet and sheet
  var sheet = SpreadsheetApp.getActiveSpreadsheet().getSheetByName("Goals");
  var dataRange = sheet.getDataRange();
  var values = dataRange.getValues();
  
  // Get today's date
  var today = new Date();
  
  // Loop through each row
  for (var i = 1; i < values.length; i++) {
    var row = values[i];
    var email = row[0];       // Email in column A
    var goalName = row[1];    // Goal name in column B
    var deadline = row[2];    // Deadline in column C
    var status = row[3];      // Status in column D
    
    // Calculate days until deadline
    var daysUntil = Math.round((deadline - today) / (1000 * 60 * 60 * 24));
    
    // If deadline is within 3 days and status is not "Complete"
    if (daysUntil <= 3 && daysUntil >= 0 && status != "Complete") {
      // Send reminder email
      var subject = "Goal Reminder: " + goalName;
      var message = "Hello,\n\n" +
                   "This is a reminder that your goal '" + goalName + "' is due in " + daysUntil + " days.\n\n" +
                   "Current Status: " + status + "\n\n" +
                   "Keep up the good work!\n\n" +
                   "Goal Tracker System";
      
      MailApp.sendEmail(email, subject, message);
    }
  }
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
                    <circle cx="400" cy="200" r="60" fill="var(--blue-primary)" />
                    <text x="400" y="200" text-anchor="middle" alignment-baseline="middle" fill="var(--light-text)" font-weight="bold" font-size="14" font-family="Orbitron">Google Apps Script</text>
                    
                    <!-- Outer Service Nodes -->
                    <circle cx="200" cy="100" r="40" fill="rgba(15, 18, 52, 0.7)" stroke="var(--pink-primary)" stroke-width="2" />
                    <text x="200" y="100" text-anchor="middle" alignment-baseline="middle" fill="var(--light-text)" font-size="12" font-family="Quicksand">Sheets</text>
                    
                    <circle cx="600" cy="100" r="40" fill="rgba(15, 18, 52, 0.7)" stroke="var(--pink-primary)" stroke-width="2" />
                    <text x="600" y="100" text-anchor="middle" alignment-baseline="middle" fill="var(--light-text)" font-size="12" font-family="Quicksand">Docs</text>
                    
                    <circle cx="200" cy="300" r="40" fill="rgba(15, 18, 52, 0.7)" stroke="var(--pink-primary)" stroke-width="2" />
                    <text x="200" y="300" text-anchor="middle" alignment-baseline="middle" fill="var(--light-text)" font-size="12" font-family="Quicksand">Forms</text>
                    
                    <circle cx="600" cy="300" r="40" fill="rgba(15, 18, 52, 0.7)" stroke="var(--pink-primary)" stroke-width="2" />
                    <text x="600" y="300" text-anchor="middle" alignment-baseline="middle" fill="var(--light-text)" font-size="12" font-family="Quicksand">Calendar</text>
                    
                    <circle cx="100" cy="200" r="40" fill="rgba(15, 18, 52, 0.7)" stroke="var(--pink-primary)" stroke-width="2" />
                    <text x="100" y="200" text-anchor="middle" alignment-baseline="middle" fill="var(--light-text)" font-size="12" font-family="Quicksand">Gmail</text>
                    
                    <circle cx="700" cy="200" r="40" fill="rgba(15, 18, 52, 0.7)" stroke="var(--pink-primary)" stroke-width="2" />
                    <text x="700" y="200" text-anchor="middle" alignment-baseline="middle" fill="var(--light-text)" font-size="12" font-family="Quicksand">Drive</text>
                    
                    <!-- Connection Lines -->
                    <line x1="400" y1="200" x2="200" y2="100" stroke="var(--purple-primary)" stroke-width="2" />
                    <line x1="400" y1="200" x2="600" y2="100" stroke="var(--purple-primary)" stroke-width="2" />
                    <line x1="400" y1="200" x2="200" y2="300" stroke="var(--purple-primary)" stroke-width="2" />
                    <line x1="400" y1="200" x2="600" y2="300" stroke="var(--purple-primary)" stroke-width="2" />
                    <line x1="400" y1="200" x2="100" y2="200" stroke="var(--purple-primary)" stroke-width="2" />
                    <line x1="400" y1="200" x2="700" y2="200" stroke="var(--purple-primary)" stroke-width="2" />
                </svg>
            </div>
        </div>
        
        <a href="https://dioram8.github.io/website/" class="back-link">Back to Main Website</a>
    </div>
</body>
</html>
