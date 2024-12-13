<h1>Learning Objectives</h1>
<li>Understand how to utlize AWS CloudTrail to monitor activity within AWS environments.</li>
<li>Learn how to use tools such as jq to parse and filter JSON logs for log analysis.</li>

  
<p><p align="center"><i>As SOC-mas approached, so did the need,
To provide those without, with something to read.
Care4Wares tried, they made it their mission,
A gift for all wares, a SOC-mas tradition.</p>
<p align="center">Although they had some, they still needed more,
To pick up some books, they’d head to the store.
The town’s favourite books, would no doubt make them jolly,
They ticked off the list, as they filled up the trolley.</p>
<p align="center">With the last book ticked off, the shopping was done,
When asked for their card, the ware handed them one.
“I’m sorry” he said, as the shop clerk reclined,
“I can’t sell you these books, as your card has declined.”</i></p>
<p align="center">The ware put them back, as they walked in confusion, 
How could this be? An attack? An intrusion? 
And when they logged on, the ware got a scare,
To find the donations, they just weren’t there!</i></p>

<p align="center"><img src="https://github.com/user-attachments/assets/d1c34336-155e-4890-9ae2-78e4e70fc39e" width="350"/></p>

<p><i>We sent out a link on the 28th of November to everyone in our network that points to a flyer with the details of our charity. The details include the account number to receive donations. We received many donations the first day after sending out the link, but there were none from the second day on. I talked to multiple people who claimed to have donated a respectable sum. One showed his transaction, and I noticed the account number was wrong. I checked the link, and it was still the same. I opened the link, and the digital flyer was the same except for the account number.</i>

The day after the link was sent out, several donations were received.
Since the second day after sending the link, no more donations have been received.
A donator has shown proof of his transaction. It was made 3 days after he received the link. The account number in the transaction was not correct.
McSkidy put the digital flyer in the AWS S3 object named wareville-bank-account-qr.png under the bucket wareville-care4wares.
The link has not been altered.</p>


<p><h2>Q1: What is the other activity made by the user glitch aside from the ListObject action?</h2></p>

<details>
  <summary>Q1 Walkthrough</summary>
    <p>Open a Terminal and change directories to wareville_logs</p>
      <img src="https://github.com/user-attachments/assets/f0e86071-c0e8-4085-9f9a-13b689c2a980"/>
    <p>Execute the following command that filters for all actions from the user "glitch" that happened within the wareville-cares4wares bucket</p>
      <img src="https://github.com/user-attachments/assets/f936047d-dbb0-41e5-85f1-28464ce55f4a"/>
 <details> 
  <summary>Q1 Answer</summary>
   <p><b>PutObject</b>
    <p><img src="https://github.com/user-attachments/assets/059a5225-2190-4571-8dc4-5fe286b3c017"/></details>
</details>


<p><h2>Q2: What is the source IP related to the S3 bucket activities of the user glitch?</h2></p>

<details>
   <summary>Q2 Walkthrough</summary>
    <p>Open a Terminal and change directories to wareville_logs</p>
      <img src="https://github.com/user-attachments/assets/f0e86071-c0e8-4085-9f9a-13b689c2a980"/>
    <p>Execute the following command that filters for all activity from the user "glitch" where the event was logged from the S3 bucket</p>
      <img src="https://github.com/user-attachments/assets/b22885c4-0e71-4972-8b3f-90e74940bf83"/>
 <details> 
  <summary>Q2 Answer</summary>
   <p><b>53.94.201.69</b>
    <p><img src="https://github.com/user-attachments/assets/dc175587-d3ed-42e2-9c87-5e602c9d9113"/></details>
  </details>


  <p><h2>Q3: Based on the eventSource field, what AWS service generates the ConsoleLogin event?</h2></p>

<details>
  <summary>Q3 Walkthrough</summary>
    <p>Open a Terminal and change directories to wareville_logs</p>
      <img src="https://github.com/user-attachments/assets/f0e86071-c0e8-4085-9f9a-13b689c2a980"/>
    <p>Execute the following command that filters for events named "ConsoleLogin" and lists the source of the event</p>
      <img src="https://github.com/user-attachments/assets/239e6164-42ca-4d82-a73b-b43fd951e867"/>
 <details> 
  <summary>Q3 Answer</summary>
  <p><b>signin.aws.com</b></p>
    <img src="https://github.com/user-attachments/assets/bc1f94e4-87ce-48a9-b14f-a8ef25ae63d1"/></p></details>
  </details>


  <p><h2>Q4: When did the anomalous user trigger the ConsoleLogin event?</h2></p>

<details>
  <summary>Q4 Walkthrough</summary>
    <p>Open a Terminal and change directories to wareville_logs</p>
      <img src="https://github.com/user-attachments/assets/f0e86071-c0e8-4085-9f9a-13b689c2a980"/>
    <p>Execute the following command that filters for events named "ConsoleLogin" where the user is "glitch" and lists the time an event occurred</p>
      <img src="https://github.com/user-attachments/assets/de6f2b5b-d3a6-404d-a3e9-d24e9c717995"/>
 <details> 
  <summary>Q4 Answer</summary>
  <p><b>2024-11-28T15:21:54Z</b></p>
    <img src="https://github.com/user-attachments/assets/66fcdc32-6238-4853-95ed-64d2d2a97d6a"/></p></details>
  </details>


  <p><h2>Q5: What was the name of the user that was created by the mcskidy user?</h2></p>

<details>
  <summary>Q5 Walkthrough</summary>
    <p>Open a Terminal and change directories to wareville_logs</p>
      <img src="https://github.com/user-attachments/assets/f0e86071-c0e8-4085-9f9a-13b689c2a980"/>
    <p>Execute the following command that filters for events logged by the AWS Identity and Access Management web service where a user was created by "mcskidy"</p>
      <img src="https://github.com/user-attachments/assets/73ccd837-06f7-4892-bbad-415f13620e23"/>
 <details> 
  <summary>Q5 Answer</summary>
  <p><b>glitch</b></p>
    <img src="https://github.com/user-attachments/assets/7770b523-8b12-438f-85c7-e4db8bd60614"/></p></details>
  </details>


  <p><h2>Q6: What type of access was assigned to the anomalous user?</h2></p>

<details>
  <summary>Q6 Walkthrough</summary>
    <p>Open a Terminal and change directories to wareville_logs</p>
      <img src="https://github.com/user-attachments/assets/f0e86071-c0e8-4085-9f9a-13b689c2a980"/>
    <p>Execute the following command that filters for events logged by the AWS Identity and Access Management web service where a "AttachUserPolicy" event occurred</p>
      <img src="https://github.com/user-attachments/assets/f9d8d137-dfe4-4d6e-a993-ddcd2442ed71"/>
 <details> 
  <summary>Q6 Answer</summary>
  <p><b>AdministratorAccess</b></p>
    <img src="https://github.com/user-attachments/assets/4f9855ce-23cc-45ce-a36c-5b1e3afaaa81"/></p></details>
  </details>


  <p><h2>Q7: Which IP does Mayor Malware typically use to log into AWS?</h2></p>

<details>
  <summary>Q7 Walkthrough</summary>
        <p>Open a Terminal and change directories to wareville_logs</p>
      <img src="https://github.com/user-attachments/assets/f0e86071-c0e8-4085-9f9a-13b689c2a980"/>
    <p>Execute the following command that filters for the source IP of console logins from "mayor_malware"</p>
      <img src="https://github.com/user-attachments/assets/9cc1f828-396b-4b8f-9877-795e31d4f4a9"/>
 <details> 
  <summary>Q7 Answer</summary>
  <p><b>53.94.201.69</b></p>
    <img src="https://github.com/user-attachments/assets/06e29ae4-e31b-4458-bf6c-7ac0de5dd9dc"/></p></details>
  </details>


  <p><h2>Q8: What is McSkidy's actual IP address?</h2></p>

<details>
  <summary>Q8 Walkthrough</summary>
      <p>Open a Terminal and change directories to wareville_logs</p>
      <img src="https://github.com/user-attachments/assets/f0e86071-c0e8-4085-9f9a-13b689c2a980"/>
    <p>Execute the following command that filters for the source IP of console logins from "mcskidy"</p>
      <img src="https://github.com/user-attachments/assets/61e873ec-1b49-40dd-abf6-5823ffa2e602"/>
 <details> 
  <summary>Q8 Answer</summary>
  <p><b>31.210.15.79</b></p>
    <img src="https://github.com/user-attachments/assets/3cde3b7f-d659-47fd-95e5-c7ff0c1ea56a"/></p></details>
  </details>


  <p><h2>Q9: What is the bank account number owned by Mayor Malware?</h2></p>

<details>
  <summary>Q9 Walkthrough</summary>
    <p>Open a Terminal and change directories to wareville_logs</p>
      <img src="https://github.com/user-attachments/assets/f0e86071-c0e8-4085-9f9a-13b689c2a980"/>
    <p>Execute the following command to search for all INSERT queries from the RDS log</p>
      <img src="https://github.com/user-attachments/assets/4f2974e5-61cf-459f-bab6-0cd27a6d5372"/>    
 <details> 
  <summary>Q9 Answer</summary>
  <p><b>2394 6912 7723 1294</b></p>
    <img src="https://github.com/user-attachments/assets/59fc286d-5fd3-4dcc-9bb1-2234a50f4092"/></p></details>
  </details>
