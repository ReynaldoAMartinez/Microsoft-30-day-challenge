# Mini Project # 2
# Objective: Simulate a phishing attack, investigate it using MS Defender, and document the incident like a real SOC analyst

# Sent a fake email to Bob Smith's email

<img width="587" height="523" alt="image" src="https://github.com/user-attachments/assets/59c8982a-2a55-44b3-adb3-1d5bdb39b9de" />


# Checked the Safe Link with the email sent to Bob
<img width="1020" height="435" alt="image (1)" src="https://github.com/user-attachments/assets/f147755e-3913-42f2-8809-fa2452654432" />

# Checked the email in Explorer
<img width="1585" height="762" alt="image (2)" src="https://github.com/user-attachments/assets/b534e596-e2c1-44b6-b3e2-d98e58009957" />

# Examined the email details
<img width="1587" height="678" alt="image (3)" src="https://github.com/user-attachments/assets/070b9763-5363-4eef-b279-53d730337723" />

# Sent a second email to Bob with an image attached
<img width="909" height="595" alt="image (10)" src="https://github.com/user-attachments/assets/bd714ace-378c-4a1b-96e7-381efc99d016" />

# Bob clicked on the URL 
<img width="584" height="644" alt="image (5)" src="https://github.com/user-attachments/assets/0cd732ad-762d-464c-b49e-fb847aff1c91" />


# Checked the Authentication fields. Both email passed ok.
<img width="559" height="207" alt="image (6)" src="https://github.com/user-attachments/assets/a080f518-9e85-4895-a39b-9b9bd160ff95" />


# Identified the sender and sender IPs.
<img width="1597" height="712" alt="image (7)" src="https://github.com/user-attachments/assets/6d42c94a-ad4a-49cf-9ed9-2efc231da736" />


# Checked sender IPs using AbuseIPDB (OSINT tool). IPs are not malicious. 
<img width="908" height="835" alt="image (8)" src="https://github.com/user-attachments/assets/aff18537-e2db-4e02-a5d2-c8c0f8d9647f" />

<img width="908" height="835" alt="image (9)" src="https://github.com/user-attachments/assets/f0fb0342-56e7-4229-a8cb-28899a9c9e82" />

# Findings 
- Time: from 2025-18-11 15:34:00 UTC to 2025-18-11 15:53:00 UTC
- Hosts: N/A
- IOC Domain: N/A
- IOC IP: N/A
- Possible Malware Family: N/A
- Filename: N/A
- SHA256 Hash: N/A

# Investigation Summary
Using the subject line "Urgent: Password Expiration Notice" to generate a false feeling of urgency, two suspicious emails were sent from elproton1111@proton.me to bob@30mydfir.onmicrosoft.com. Even if the messages passed Composite Authentication, SPF, DKIM, and DMARC, these tests only verify that the email originated from a trustworthy server (proton.me), not that it is secure. A typical warning sign in phishing efforts is the sender's use of a free proton.me account, which is a common indicator in phishing attacks.The user clicked on the link, but fortunately we did not find any signal that his credentials, or another machine has been compromised. 

# Who, What, When, Why, How
- Who - Who was involved? 109.224.244.29, 79.135.106.101 (Sender IPs)
- What - What happened?  Malicious emails were sent with a URL link http://secure-update-help.com/verify-login, and an attachment.
- When - When did this occur and is it still happening?  from 2025-18-11 15:34:00 UTC to 2025-18-11 15:53:00 UTC
- Where - Where in the environment did this happen? [bob@30mydfir.onmicrosoft.com](mailto:bob@30mydfir.onmicrosoft.com)
- Why - Why did this happen? (If known) The attacker intended to deceive the victim in order to obtain credentials.
- How - How did this happen? If the user clicked on the link, he would be taken to a phony login page, where the attacker would obtain his credentials.


# Recommendations
To reduce the risk of future phishing attacks, the organization should:

- Strengthen email security controls by enabling advanced anti-phishing, Safe Links, and Safe Attachments policies in Microsoft Defender
- Block the sender (elproton1111@proton.me), IPs (109.224.244.29, 79.135.106.101)
- Enforce MFA for all users to prevent credential theft even if password phished
- Force password reset for Bob Smith’s account for suspicious activity
- Conduct a phishing awareness training for the impacted user



