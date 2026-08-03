---
title: What I have done so far!
description: Everything currently running on my homelab
slug: current-config
date: 2026-08-02 00:00:00+0000
image: loginpage.png
tags:
    - Blogs
weight:      # You can add weight to some posts to override the default sorting (date descending)
---

## What services I have set up so far:

Currently I am running Proxmox and I have 4 virtual machines.


## Jellyfin-Server:
As the name suggests this is running Jellyfin. 

It is pulling from a media file share via Samba. I chose to do it this way so that I could download the media and upload it to the file share with my personal computer. No real reason, just ease of use considering I have to manually upload every file. 

I access this server via a Tailscale connection to my home network. My friends and family utilize my Jellyfin server so I update it with whatever media they want.


## ADDNS:

This is my domain controller! 

I am using Windows Server 2019 and have configured my domain. Currently I am organizing my domain through my "site" FakeCorp. This site is organized into 5 OUs consisting of Admins, HR, Sales, Servers, and a Test OU.

![Probably not the best organization but it'll work for me](ous.png)

I have one main admin account that I use for all my admin configuration tasks domain wide (Hoping to get more granular admin access soon). Then I have only have one user configured in my test OU.
The only configurations I have done so far are basic GPO configuration; setting a background, configuring password policies, etc... I have also configured LAPS for control of all local administrator passwords.

![Hopefully this cute BG will quench my rage when something isn't working properly](kitty.jpg)

It is functioning as domain wide DNS but it just forwards to my local network DNS.

I set up folder redirection so that I can (hopefully) log onto any future VM with any domain credentials and have all of their personal resources/settings.

## WINSRV:
This VM is also running Windows Server 2019 was originally created to be a central file share for all domain files. I slapped 2 drives on this VM one for the OS and the other for the file share. This is where the global assets are stored such as the backgrounds, login scripts, and software.

This also holds all the file shares and folder redirections for each OU.

![Folder redirection for my admin account inside the Admins file share. This was a massive headache to configure because I started it before the file share was created. Therefore I had to migrate the redirects from a local folder on the ADDNS server...](fdrd.png)

## Saitama:
This is merely a test VM for a domain joined computer. I use this computer to log in as all the users I create and verify that policies are being applied. Most of my troubleshooting consists of bouncing between ADDNS/WINSRV and Saitama over and over again.







