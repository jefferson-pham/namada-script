# Namada Script
This script is build for 3 purposes:
1. Scan all Validators address if they are opening RPC 26657 port that will be a vulnerability for a Security Scanning.
2. Attack with a heavy payload to that Validators to slowing down the performance.
3. Self-Testing the owner validator.

In this script, the work flow will be:
1. **Dependency Setup** (_setupDeps_): This function installs necessary dependencies (dialog, wget, curl, jq) if they are not already installed.
2. **Existence Check** (_exists_): This function checks if essential commands are available. If not, it invokes setupDeps to install them.
3. **Parsing Vulnerable Validators** (_parseVulnValidators_): This function performs the following steps:
Retrieves information about peers from a given source (127.0.0.1:26657/net_info) using curl and jq.
Checks connectivity to each peer using nc.
Extracts additional information from connected peers and stores it in files.
Analyzes collected data regarding peers.
4. **Sending Requests with a Parallel multithread** (_sendRequests_): This function presents results and initiates testing if there are vulnerable hosts. It performs the following actions:
Displays results obtained during the vulnerability check.
If there are vulnerable hosts, it initiates testing by sending requests to them.
Logs responses to a file (/namada_test_payload_${agtimestart}.txt).
5. **Main Function** (_main_): This function presents a menu for the user to choose various options, including initiating testing, retrieving vulnerable hosts, testing the machine, or exiting the program.

Here are some proof of testing process:
1. Analyzed the Validators that opening 26657 port:
<img width="525" alt="image" src="https://github.com/jefferson-pham/namada-script/assets/87713875/d274d1b9-774a-4936-ae94-32cc662e5120">

2. Start testing with sending heavy payload with multithreading x100 thread:
<img width="553" alt="image" src="https://github.com/jefferson-pham/namada-script/assets/87713875/e24e7ef8-fd27-4aa7-a2ee-fca82ccb6cbe">

