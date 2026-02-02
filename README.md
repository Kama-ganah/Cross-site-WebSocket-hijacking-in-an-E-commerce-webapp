# Overview
I assessed the application’s WebSocket implementation to evaluate whether authenticated chat sessions could be hijacked from a cross-site context. During testing, I identified that the WebSocket handshake lacked origin validation and CSRF protections. By crafting a malicious webpage, I was able to initiate a WebSocket connection on behalf of an authenticated victim, retrieve their chat history, and extract sensitive credentials. This project demonstrates how insecure WebSocket configurations can be exploited to achieve full account takeover without additional user interaction.

# Methodology

Step 1: Analyzed the live chat WebSocket communication using Burp Suite.

Step 2: Verified that the WebSocket handshake did not enforce origin checks or CSRF protections.

Step 3: Crafted a malicious HTML/JavaScript payload to connect to the WebSocket endpoint from an external origin.

Step 4: Used Burp Collaborator to receive exfiltrated chat messages and sensitive data.

Step 5: Extracted victim credentials from chat history and successfully logged in as the user.

# Conclusion

This assessment confirmed a critical Cross-site WebSocket Hijacking vulnerability that allowed unauthorized access to chat data and user credentials. Implementing strict origin validation, session checks, and CSRF protections is essential to secure real-time WebSocket features and prevent account compromise.
