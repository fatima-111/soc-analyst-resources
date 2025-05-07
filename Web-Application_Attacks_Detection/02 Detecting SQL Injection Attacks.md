SQL injections are serious attacks where a web application uses user input in SQL queries without properly checking or cleaning it first.

![](https://miro.medium.com/v2/resize:fit:389/0*xdzQeJhAcPxsBBns)

# Detecting Automated SQL Injection Tools

Attackers use many automated tools to detect SQL injection vulnerabilities. One of the well-known tools is Sqlmap.

**1. Analyse the User-Agent Header:**  
Automated tools often include their name and version in the `User-Agent` header. By inspecting this field, you can sometimes identify requests coming from known tools.

**2. Monitor Request Frequency:**  
Tools like SQLMap are designed to send many requests quickly to test various payloads. If you notice an unusually high number of requests per second (e.g., more than 1–2 per second), it may indicate automated activity.

**3. Inspect the Payload Content:**  
Many tools include their names or identifiable patterns in the payload. For instance, a request might contain something like `'sqlmap' OR 1=1`, which clearly indicates automation.

**4. Watch for Unusually Complex Payloads:**  
While not always a reliable method, complex or obfuscated payloads are often a sign of automated tools at work. These tools may chain multiple techniques together, producing longer and more intricate injection strings.

# A Detection Example

An example log

![](https://miro.medium.com/v2/resize:fit:1050/0*2iUS1TEzNBd563nT.png)

If we look at the requests, we can easily see that there are readable words such as “UNION”, “SELECT”, “AND”, and “CHR” next to the % symbols. As these are specific words belonging to SQL, we can see that we are facing an SQL injection attack.

Since the payloads are URL-encoded, analysing them directly can be difficult. You can use an online encoder/decoder to decode the payloads and better understand what they’re trying to do.

![](https://miro.medium.com/v2/resize:fit:1050/0*gtnledzrEv857krF.png)

When we decode the URL, we can see more clearly that this is a SQL injection attack.

![](https://miro.medium.com/v2/resize:fit:1050/0*-17mOLYHb1fE2fuC.png)

Let’s examine the request timestamps. All the SQL injection payloads were sent on ‘19/Feb/2022 11:09:24’, with over 50 requests made within just one second. This unusually high frequency strongly suggests an automated attack.

Now Let’s Examine if the attack was successful

For correctly configured web servers, we can find the response size in the access logs. You can examine this area to see if there is a noticeable difference in response sizes. If there is a noticeable difference, then you can assume that the attack was successful.