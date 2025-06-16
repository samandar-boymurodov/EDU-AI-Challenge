**Title**
Logout button unresponsive on Safari browser

---

**Description**
When using our application in Safari, clicking the “Logout” button does not trigger any action. No network request is sent, no UI change occurs, and the user remains logged in. Other browsers (Chrome, Firefox) handle the logout flow correctly.

---

**Steps to Reproduce**

1. Open Safari (macOS or iOS) and navigate to the application.
2. Log in with valid credentials.
3. Click the “Logout” button (usually in the top-right corner/menu).
4. Observe that nothing happens: no redirect to the login page, no network call to the logout endpoint, and no console errors or feedback.

---

**Expected vs Actual Behavior**

* **Expected:**

    * A network request to `POST /api/auth/logout` (or equivalent) is fired.
    * The user’s session cookie/local storage token is cleared.
    * The UI redirects to the login page or home page in a logged‑out state.

* **Actual:**

    * No network request is fired.
    * The session remains active.
    * The user stays on the same page, still authenticated, with no visible error message.

---

**Environment**

* **Browser:** Safari 16.x (macOS Monterey) and Safari on iOS 16
* **OS:** macOS 12.6.4 (Monterey), iOS 16.4
* **App Version:** v2.3.1 (build 20250610)
* **Auth Flow:** JWT stored in HTTP‑only cookie
* **Relevant Config:**

    * Frontend: React 18, Next.js 13
    * Backend: Node.js 18, Express 4, CORS enabled

---

**Severity / Impact**

* **Severity:** High
* **Impact:** Users on Safari are unable to log out, posing a security concern (cannot terminate sessions) and causing confusion/frustration.
