---
title: "What is DNS and Why Should You Care?"
seoTitle: "Understanding DNS: How Domain Name System Works & Why It’s Important"
seoDescription: "Learn how DNS works, its importance for fast browsing. Explore the DNS hierarchy and how it translates domain names into IP addresses."
datePublished: Sat Feb 01 2025 09:08:42 GMT+0000 (Coordinated Universal Time)
cuid: cm6lz0ws2000v09jv5qby2zo7
slug: understanding-how-dns-works
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1738331586516/ed32eb0f-d3ff-4270-9dbb-6e26f5754e3b.webp
tags: dns, dns-resolver, chaicode

---

### **📢** Imagine this:

You want to call your friend Rahul. But instead of remembering his phone number, you just save his name in your contact list. Whenever you want to call him, you simply search for "Rahul," and your phone dials the correct number for you.

👉 **This is exactly how DNS works for the internet!**

**DNS (Domain Name System)** is like a phonebook for websites. Instead of remembering long numbers (IP addresses), we use easy-to-read names like google.com or facebook.com. DNS translates these domain names into IP addresses so that your computer can find and load the correct website.

### **🧐** Why is DNS Important?

DNS makes using the internet easy by allowing us to type website names instead of remembering long numbers (IP addresses). It also helps **websites load faster** by storing previous searches in caches at different levels—your browser, computer, and even your internet provider keep records of past lookups to avoid repeating the process each time. This **reduces lookup times** and improves browsing speed. DNS also supports large websites by **handling heavy traffic** smoothly. Plus, it **keeps the internet reliable**—if one server fails, others step in to keep websites running without issues.

## How DNS Works: Recursive vs. Iterative Queries

There are two main ways DNS works: **recursive** and **iterative** queries.

#### **Recursive DNS Query:**

In a **recursive DNS query**, you ask the DNS resolver to find the IP address. If it doesn’t know, it will check with other servers and get the answer for you. Once it finds it, the resolver gives you the final IP address, so you don’t have to do anything.

#### **Iterative DNS Query:**

With an **iterative DNS query**, the DNS resolver doesn’t give you the final answer. Instead, it tells you the next server to ask. You keep asking different servers until you get the IP address.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1738400534898/db622523-2170-4cd4-bee9-f039de2ff0fb.png align="left")

## The DNS Hierarchy (From Root to Your Browser) 🔝

DNS follows a structured hierarchy that resolves domain names into IP addresses efficiently. This system distributes the workload across multiple levels, ensuring speed and reliability. Let’s break down the process from the top-level root servers to your browser request.

### 1\. Root DNS Servers – The Starting Point

At the top of the hierarchy are the **Root DNS servers (also called name servers)**, which act as the internet’s entry point. They don’t store actual domain-to-IP mappings but instead direct queries to the correct Top-Level Domain (TLD) servers.

There are **13 sets of root servers** worldwide, managed by organizations like ICANN. These servers ensure global availability through Anycast technology, allowing multiple copies of each root server to exist in different locations.

For example, if a user types `www.example.com`, the root server does not know the IP address but directs the query to the `.com` TLD server, which manages all `.com` domains.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1738398905505/2aeaad45-87d2-4777-88d0-24a55344f252.png align="left")

### **2\. TLD (Top-Level Domain) Servers – Managing Domain Extensions**

TLD servers handle requests based on domain extensions such as `.com`, `.org`, `.net`, and `.edu`. Each TLD is managed by a registry organization. For instance, Verisign manages `.com`, while Public Interest Registry manages `.org`.

When the root server directs a query to the `.com` TLD, it does not return the website’s IP address but instead points to the **Authoritative Name Server** responsible for that specific domain, such as `example.com`.

### **3\. Authoritative Name Servers – The Final Answer**

The Authoritative Name Server stores the actual DNS records for a domain. It contains various record types, such as A records (IP address mappings), CNAME records (aliases), and MX records (email routing).

When a TLD server directs a query to an authoritative server, it looks up the requested domain and returns the correct IP address. For example, if a request is made for `www.example.com`, the authoritative server may respond with:

```plaintext
www.example.com → A Record → 192.168.1.100
```

This is the final answer that allows a user’s browser to connect to the website.

### **4\. Recursive DNS Resolvers – The Middleman**

Your browser does not directly contact root, TLD, or authoritative servers. Instead, it relies on a **Recursive DNS Resolver**, which acts as a middleman, fetching DNS records on behalf of the user.

A recursive resolver first checks its **cache** to see if it has the requested domain’s IP address. If cached, it replies instantly, avoiding a full lookup. If not, it contacts the root server, then the TLD server, and finally the authoritative server to retrieve the answer.

Recursive resolvers are usually provided by Internet Service Providers (ISPs) or public DNS services like **Google DNS (8.8.8.8)** and **Cloudflare DNS (1.1.1.1)**.

### **5\. Browser and Operating System – Using the DNS Result**

Once the recursive resolver retrieves the IP address, it stores it in cache for future use and sends it to the browser. The browser then establishes a connection to the IP address and loads the requested website.

To improve speed, DNS caching happens at multiple levels:

* **Browser Cache** – Saves DNS lookups for frequently visited sites.
    
* **Operating System Cache** – Stores DNS responses locally on your computer.
    
* **ISP Cache** – Keeps temporary records of domain lookups to reduce traffic.
    

By using caching, DNS reduces lookup times, making websites load faster.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1738398739711/7c9fce7a-5756-4e20-b751-537014fef9ae.png align="left")

## **Step-by-Step Process 🛠**

Let’s break it down into simple steps with an analogy!

Imagine you want to find a new pizza shop in your city. You ask a friend, who checks an online directory, finds the address, and tells you where to go.

**DNS Works in a Similar Way!**  
  
👉 Example: You type **www.google.com** in your browser.  
👉 Your browser doesn’t know Google’s IP address, so it asks a DNS resolver (like a friend who knows where to look).  
👉 The resolver asks a **Root DNS Server**, which is like the main index in a phonebook—it tells where to find the next piece of information.  
👉 The root server directs the query to a **Top-Level Domain (TLD) Server** (for example, if you asked for google.com, it checks the .com directory).  
👉 Finally, the request reaches an **Authoritative DNS Server** that has Google’s actual IP address.  
👉 Your browser gets the correct IP address and loads the website for you!

**This entire process happens in milliseconds!**

> DNS was created in 1983, and without it, we'd still be typing in long IP addresses instead of easy-to-remember domain names! ⌨️