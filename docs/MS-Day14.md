
# Day 14 - Learned about two of most important tools to investigate email threats: Explorer and Quarantine.

Explorer is a powerful tool that lets me search through mail flow activity so I can answer questions like:

- **Who received a specific email?**
- **Was it blocked, delivered, or clicked?**
- **Was it detected by Safe Links or anti-phishing?**

<img width="1901" height="947" alt="image" src="https://github.com/user-attachments/assets/bd94fc84-8a6f-42ab-a10f-dc7815a17fb0" />

---
Explorer shows emails by categories and allows to search by specific fields such as Sender address, Recipients, Subject, and more.

<img width="611" height="830" alt="image1" src="https://github.com/user-attachments/assets/2dafda99-5fad-432d-93c7-cf3a243aa3c3" />

<img width="1590" height="772" alt="image2" src="https://github.com/user-attachments/assets/1bc6f217-8797-46a3-a7b5-5ae7cd71fce5" />
---
From here I can check the email header
<img width="1548" height="900" alt="image3" src="https://github.com/user-attachments/assets/b4544a05-33df-4bc7-872c-9b7576d9304c" />

---
Also, I can take actions such as Submit to Microsoft for review, or Initiate automated investigation
<img width="1350" height="537" alt="image (1)" src="https://github.com/user-attachments/assets/e1f017a8-4115-4623-8d51-5daf2dcfe08a" />

---
If I want to run an Advanced hunting using KQL, there is an option under "Go hunt" which allow me to see the tables and run the queries.

<img width="1575" height="856" alt="image (2)" src="https://github.com/user-attachments/assets/f950d355-3610-437d-8341-8dfd87bf1436" />

---
Quaratine is where suspicious emails are held when they are flagged as threats, before reaching users. They are not immediately deleted.

<img width="1489" height="771" alt="image" src="https://github.com/user-attachments/assets/ef1a0117-2937-494e-be00-b385bd376ae8" />
<img width="1605" height="457" alt="image (1)" src="https://github.com/user-attachments/assets/7a969e33-2eba-4ce5-b636-4589a1041851" />

---
If a user reports a suspicious email, we can see it under: Investigation & response / Actions & submissions / submissions
As an example, I marked an email from Bob's inbox as phishing, and it was sent to the submissions area. Once there, I marked it as a Phishing, and Bob got the notification.





