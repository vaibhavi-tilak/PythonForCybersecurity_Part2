<img src="https://r2cdn.perplexity.ai/pplx-full-logo-primary-dark%402x.png" style="height:64px;margin-right:32px"/>

# create a README.md file for this to upload on the GitHub Cybersecurity with Python- Part 2 : Parsing Network Logs in Python Using Split \& Strip(Clean and Fast)

[](https://medium.com/@vaibhavitilak17?source=post_page---byline--0b22d5bfd2bf---------------------------------------)
[Vaibhavi Tilak](https://medium.com/@vaibhavitilak17?source=post_page---byline--0b22d5bfd2bf---------------------------------------)
3 min read
·
Apr 16, 2025
[](https://medium.com/plans?dimension=post_audio_button&postId=0b22d5bfd2bf&source=upgrade_membership---post_audio_button-----------------------------------------)
Introduction
Analyzing network logs is crucial for identifying security threats, monitoring system performance, and troubleshooting network issues. Python provides several methods for efficiently reading and processing log files. In this article, we will cover:
Methods for reading a text file line by line.
Storing parsed data in dictionaries.
Extracting unique IP addresses and identifying the ports they are hitting.
Reading a File in Python
We will be performing operations on the below Logfile.txt
Logfile.txt

# Open and read log file

with open("Logfile.txt", "r") as file:
logs = file.readlines()

unique_ips = set()
ip_port_map = {}

# Loop through each log line

for line in logs:
parts = line.strip().split()  \# Split the line by whitespace
if len(parts) >= 2:  \# Check if at least IP and Port are present
ip = parts[0]
port = parts[1]
unique_ips.add(ip)  \# Store the unique IP
ip_port_map.setdefault(ip, set()).add(port)  \# Map the port to the IP
Display Unique IP Addresses
print("Unique IP Addresses:")
for ip in sorted(unique_ips):
print(ip)
Press enter or click to view image in full size
Display Unique IPs with Their Ports
print("\nUnique IP Addresses with Ports:")
for ip, ports in ip_port_map.items():
port_list = ', '.join(sorted(ports))
print(f"{ip} -> Ports: {port_list}")
Press enter or click to view image in full size
Press enter or click to view image in full size
In this example, the log file was clearly formatted, with each line following a consistent structure of an IP address, a port number, and a message, all separated by spaces. Because of this well-defined and predictable format, we used Python’s split() and strip() functions to extract the IP addresses and ports, rather than relying on regular expressions. This approach is not only simpler to implement but also more efficient in terms of execution time and memory usage, as split() and strip() are optimized native string operations. Regular expressions are typically more powerful for handling unstructured or irregular log formats, but in cases like this, where the data is clean and structured, string manipulation offers a faster and more resource-friendly solution.
Press enter or click to view image in full size
Conclusion
Using Python, we can efficiently read and parse log files to extract valuable network information. This method helps in identifying security threats, monitoring network activity, and improving system administration.

```markdown
# Cybersecurity with Python - Part 2: Parsing Network Logs in Python Using Split & Strip (Clean and Fast)

This repository contains the Python scripts and explanations for learning how to efficiently parse network log files using Python’s built-in string operations. This tutorial focuses on reading log files line by line, extracting and storing key data, and summarizing network activity by identifying unique IP addresses and the ports they access.

---

## Introduction

Analyzing network logs is crucial for identifying security threats, monitoring system performance, and troubleshooting network issues. Python provides several methods for efficiently reading and processing log files. In this part of the series, you will learn:

- How to read a text log file line by line  
- How to parse log data using `strip()` and `split()` string methods  
- How to store parsed data in data structures like sets and dictionaries  
- How to extract unique IP addresses and map the ports they are hitting

---

## Log File Format

The logs are expected to have a clear, consistent format—each line contains:

- An IP address  
- A port number  
- Additional message or metadata (optional)

Example line:

```

192.168.1.10 80 Connection accepted

```

---

## Parsing Implementation

The following Python script demonstrates how to read the log file, extract unique IP addresses, map corresponding ports, and display the results.

```


# Open and read log file

with open("Logfile.txt", "r") as file:
logs = file.readlines()

unique_ips = set()
ip_port_map = {}

# Loop through each log line

for line in logs:
parts = line.strip().split()  \# Split the line by whitespace
if len(parts) >= 2:  \# Ensure IP and port are present
ip = parts
port = parts[^1]
unique_ips.add(ip)  \# Store unique IPs
ip_port_map.setdefault(ip, set()).add(port)  \# Map ports to IPs

# Display Unique IP Addresses

print("Unique IP Addresses:")
for ip in sorted(unique_ips):
print(ip)

# Display Unique IP Addresses with Ports

print("\nUnique IP Addresses with Ports:")
for ip, ports in ip_port_map.items():
port_list = ', '.join(sorted(ports))
print(f"{ip} -> Ports: {port_list}")

```

---

## Why Use `split()` and `strip()`?

- The `strip()` method removes leading and trailing whitespace including newline characters, cleaning each line before processing.  
- The `split()` method splits the line into components based on spaces, allowing easy extraction of IPs and ports.  
- These methods are straightforward and efficient for well-formatted, consistent logs.  
- Using these instead of regular expressions reduces complexity and improves performance when dealing with clean log data.

---

## Conclusion

By using Python's native string handling functions, you can create clean, fast, and efficient log parsing scripts suitable for network security monitoring and analysis. This foundational skill enables rapid extraction of key network information — such as unique IP addresses and accessed ports — critical for identifying suspicious activity and maintaining network health.

---

## Next Steps

Stay tuned for upcoming parts of this series where we will expand to more advanced log analysis techniques, including pattern matching with regular expressions and automated threat detection.

---

*Happy Coding,*  
*Vai (Vaibhavi)*
```

This `README.md` provides a clear overview and instructions on the parsing script, suitable for sharing on GitHub with your project "Cybersecurity with Python - Part 2". Let me know if you want me to help with additional sections or formatting.

<div style="text-align: center">⁂</div>

[^1]: https://medium.com/@vaibhavitilak17

