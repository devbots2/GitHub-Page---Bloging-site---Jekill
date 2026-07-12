---
layout: post
title: "ජාල ඉංජිනේරු විද්‍යාව - Cisco Packet Tracer LAB (ප්‍රායෝගික)"
date: 2026-07-11 10:00:00 +0530
categories: [network-engineering, sinhala, labs]
tags: [cisco, networks, labs, sinhala]
description: "Packet Tracer භාවිතයෙන් සරල LAN ජාලයක් සැකසීම සහ IP ලිපින වින්‍යාසගත කිරීම් සිදුකරන ආකාරය පියවරෙන් පියවර සිංහලෙන්."
image: "https://images.unsplash.com/photo-1558494949-ef010cbdcc31?auto=format&fit=crop&w=600&q=80"
---

Cisco Packet Tracer යනු ජාලකරණ සිසුන්ට සහ ඉංජිනේරුවන්ට ජාල වින්‍යාසගත කිරීම් අත්හදා බැලීමට ඇති ඉතාම ජනප්‍රිය මෘදුකාංගයකි. මෙම LAB ලිපියෙන් අප සරල Local Area Network (LAN) එකක් සාදා පරිගණක අතර සම්බන්ධතාවය පරීක්ෂා කරමු.

## පියවර 1: මූලික උපකරණ එකතු කිරීම
Packet Tracer හි පහළ වම් කෙළවරින් පහත දැක්වෙන උපකරණ තෝරා Workspace එකට එක්කරන්න:
*   **Switch:** Cisco 2960 Switch 1ක්.
*   **PCs:** පරිගණක (PCs) 3ක්.

## පියවර 2: උපකරණ කේබල් මඟින් සම්බන්ධ කිරීම
*   තඹ සෘජු කේබල් (**Copper Straight-Through**) තෝරාගන්න.
*   පරිගණකයේ `FastEthernet0` තොට Switch එකෙහි ඇති ඕනෑම `FastEthernet` තොටකට සම්බන්ධ කරන්න.
*   සියලුම පරිගණක Switch එකට මේ ආකාරයට සම්බන්ධ කරන්න.

## පියවර 3: IP ලිපින (IP Addresses) සැකසීම
සෑම පරිගණකයකටම පහත පරිදි Static IP ලිපින ලබාදෙමු:

| Device Name | IP Address | Subnet Mask |
|:---|:---|:---|
| PC0 | `192.168.1.10` | `255.255.255.0` |
| PC1 | `192.168.1.11` | `255.255.255.0` |
| PC2 | `192.168.1.12` | `255.255.255.0` |

### IP ඇතුළත් කරන ආකාරය:
1.  PC0 මත ක්ලික් කරන්න.
2.  **Desktop** ටැබ් එකට ගොස් **IP Configuration** තෝරන්න.
3.  `192.168.1.10` ඇතුළත් කරන්න. Subnet Mask එක ස්වයංක්‍රීයව `255.255.255.0` ලෙස පිරවෙනු ඇත.

## පියවර 4: Ping මඟින් සම්බන්ධතාවය පරීක්ෂා කිරීම
1.  PC0 මත ක්ලික් කර **Command Prompt** තෝරන්න.
2.  පහත විධානය (Command) ඇතුළත් කර Enter ඔබන්න:
    ```bash
    ping 192.168.1.11
    ```
3.  සම්බන්ධතාවය සාර්ථක නම් ඔබට `Reply from 192.168.1.11...` ලෙස ලැබෙනු ඇත.
