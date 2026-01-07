# OPAC-Counter-ValACE

# ValACE Digital Portal: E-Resources Kiosk System

![Platform](https://img.shields.io/badge/Platform-Touchscreen_Kiosk-orange)
![Frontend](https://img.shields.io/badge/Frontend-Next.js_14-black)
![Security](https://img.shields.io/badge/Security-Kiosk_Mode-red)
![Context](https://img.shields.io/badge/Valenzuela_City_Library-Public_Sector-green)

> **Project Context:** The **ValACE Digital Portal** is a specialized touch-interface application deployed on standalone kiosks within the Valenzuela City Public Library. It provides patrons with secure, curated access to premium academic databases (e.g., EBSCO, ProQuest), digitized local history archives, and government e-services.

## 📖 Project Overview

Providing public access to digital resources presents a unique challenge: How do you offer a rich browsing experience while restricting users from accessing unauthorized sites or tampering with the operating system?

This project is a **Progressive Web Application (PWA)** designed specifically for public touchscreens. It features a "walled garden" browsing environment that authenticates users, centralizes access to subscription-based research tools, and ensures user privacy by automating session cleanup after every use.

## 🎯 Key Objectives

* **Democratize Information:** Provide free access to expensive academic journals and e-books that are usually behind paywalls, leveraging the library's IP-authenticated subscriptions.
* **Hardware Security:** Prevent "jailbreaking" or unauthorized OS access through a strictly controlled UI environment.
* **User Privacy:** Implement auto-logout and cache-clearing mechanisms to protect patron data on shared devices.
* **Intuitive UX:** A "Big Button," touch-first interface designed for users of all digital literacy levels.

## ✨ Core Features

### 🖥️ Kiosk Interface
* **Touch-Optimized Dashboard:** Large, high-contrast navigation cards for easy category selection (e.g., "Academic Journals," "Newspapers," "Gov Services").
* **Virtual Keyboard:** Custom on-screen keyboard integration for inputs without physical hardware.
* **In-App Browser:** Opens external resources (like EBSCOhost) in a controlled frame, preventing navigation to unauthorized domains (Whitelisting).

### 🛡️ Security & Kiosk Mode
* **Idle Timeout:** Automatically resets the session and redirects to the homepage after 3 minutes of inactivity.
* **Session Wipe:** Clears local storage, cookies, and browsing history upon logout to ensure the next user starts fresh.
* **Right-Click Disable:** Prevents access to context menus and developer tools.

### 📊 Usage Analytics
* **Resource Tracking:** Logs which databases are accessed most frequently to justify budget allocation for subscriptions.
* **Heatmaps:** Tracks touch interactions to optimize button placement and UI layout.

## 🛠️ Technology Stack

| Component | Technology | Description |
| :--- | :--- | :--- |
| **Frontend Framework** | **Next.js (React)** | Chosen for its speed, routing capabilities, and SPA (Single Page App) feel essential for kiosks. |
| **Styling** | **Tailwind CSS** | Used to create a responsive, "app-like" touch interface. |
| **Kiosk Wrapper** | **Electron / Chrome Kiosk** | Wraps the web application to run fullscreen, restricting OS access. |
| **Backend API** | **PHP / Laravel** | Handles logging, analytics storage, and dynamic resource link management. |
| **Database** | **MySQL** | Stores usage logs and resource metadata. |

## 📸 Interface Preview

| **Main Dashboard** | **Resource View (In-App)** |
|:------------------:|:--------------------------:|
| *[Insert screenshot of the icon grid]* | *[Insert screenshot of a journal open]* |

## 🔒 Security Implementation: "The Walled Garden"

This system utilizes a **Domain Whitelisting** strategy.
1.  User clicks "Access Science Direct."
2.  System checks the URL against the `allowed_domains.json` config.
3.  If valid, the link opens. If the user tries to click a Facebook link *inside* that page, the internal router blocks the request and displays a "Restricted Access" modal.

## 🚀 Installation (Dev Mode)

1.  **Clone the Repository**
    ```bash
    git clone [https://github.com/YourUsername/valace-kiosk.git](https://github.com/YourUsername/valace-kiosk.git)
    ```

2.  **Install Dependencies**
    ```bash
    npm install
    ```

3.  **Configure Whitelist**
    Edit `config/whitelist.js` to add allowed domains:
    ```javascript
    export const allowedDomains = [
      'search.ebscohost.com',
      'proquest.com',
      'valenzuela.gov.ph'
    ];
    ```

4.  **Run Locally**
    ```bash
    npm run dev
    ```

## 👤 Author

**James Dean San Miguel**
*IT Lead, Valenzuela City Library*
*Full Stack Developer*

---
*© 2025 Valenzuela City Library IT Division*
