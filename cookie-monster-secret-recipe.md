# picoCTF - Cookie Monster Secret Recipe  



## Challenge Overview  
**Category:** Web Exploitation  
**Difficulty:** Easy  
**Platform:** picoCTF  
  
This challenge focuses on understanding how websites use cookies and why storing sensitive information in them can be insecure.

---

## Objective  
Find the hidden flag by analyzing how the website stores data related to authentication or secrets.

---

## Tools Used  
• Burp Suite (Proxy / HTTP history)  
• Browser Developer Tools (for cookies)  
• Basic knowledge of URL encoding and Base64  

---

## Approach & Methodology  
1. I accessed the challenge website and used Burp Suite to inspect the HTTP traffic between the browser and the server.  
2. Based on the challenge title (Cookie Monster Secret Recipe), I suspected that the flag or secret might be stored inside a cookie.  
3. While inspecting the request/response headers, I found a cookie named:  ``` secret_recipe=<ENCODED DATA> ```  
4. The value of the `secret_recipe` cookie appeared to be encoded.
5. I copied the encoded value and decoded it step by step:  
• First decoded it from **URL encoding**  
• Then decoded the result using **Base64**
6. After decoding, the plaintext revealed the flag.  
7. I also attempted to intercept the **POST** request using Burp Suite to see if the cookie changed, but the cookie remained the same — confirming the secret was stored client-side.

---

## Result/Flag  
After decoding the cookie value, I successfully obtained the flag:  
``` picoCTF{redacted} ```

---

## Key Takeaways  
• Cookies are fully controllable by the client  
• Encoding ≠ encryption  
• Sensitive data should never be stored client-side without proper protection  

---

## Defensive Perspective  
From a defensive standpoint, this challenge highlights a common web security mistake:  
• ❌ Storing secrets or flags directly in cookies  
• ❌ Relying on encoding (URL/Base64) instead of encryption  
• ❌ Trusting client-side data for security decisions  
**Secure Design Recommendations:**  
• ✅ Store sensitive data server-side, not in cookies  
• ✅ Use cookies only for opaque session identifiers  
• ✅ Apply proper encryption and server-side validation  
• ✅ Treat all client-controlled data as untrusted input  
This vulnerability aligns with **OWASP Top 10 – Broken Access Control & Cryptographic Failures**.

---

## Lessons Learned  
This challenge reinforced how tools like Burp Suite can be used to:  
• Inspect cookies and headers  
• Identify insecure data storage  
• Understand real-world web security flaws caused by excessive trust in the client  
