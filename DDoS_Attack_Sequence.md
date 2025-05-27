sequenceDiagram
    participant Attacker
    participant BotNet
    participant Firewall
    participant WebServer

    Attacker->>BotNet: Sends a command to start DDoS attack
    loop Flood Request
        BotNet->>Firewall: Sends a high volume of HTTP requests
        Firewall->>WebServer: Forwards requests from BotNet
    end
    WebServer-->>Firewall: Overloaded response
    Firewall-->>BotNet: Analyzed traffic pattern
    Firewall-->>Attacker: Attempts to trace source of attack
    Firewall-->>Firewall: Identifies suspicious IPs
    Firewall-->>BotNet: Blocks IP addresses
    Firewall-->>WebServer: Activates rate limiting
    WebServer-->>Firewall: Returns to normal use

## Participants

* Attacker: Starts the DDoS attack and does so by commanding the BotNet to flood the server.
* BotNet: This is a group of compromised machines that is controlled by the attacker to send lots of traffic to the server.
* Firewall: A network security system that monitors and controls traffic.
* WebServer: The primary target of DDoS attacks and hosts web services for users.

## Step-By-Step Sequence
1. Initiation of Commmand - The Attacker sends a command to the BotNet to begin flooding the server with traffic
2. Traffic Flooding - The BotNet sends lots of HTTP requests to the Firewall protecting the server, and the Firewall initially sends the request to server with no harm detected.
3. Server Overload - The server begins to struggle due to the large amounts of HTTP requests, usually crashing the server.
4. Traffic Analysis - The Firewall then detects this unsual amount of traffic to the server and analyzes the traffic for any signs of attack. The firewall then attempts to track the source of the attack to differentiate real users from the bots.
5. IP Blocking and Rate Limiting - Firewall blocks suspicious IP addresses used by the BotNet to reduce traffic and it enforces rate limiting and  filters requests, in order to reduce load on the server.
6. Server Restoration - As the attack is stopped, the server resumes its normal actions.