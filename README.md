# WaybackURLs

Alright — here’s the **ultimate quick guide** to using `waybackurls` with **practical examples** so you can start using it right away for recon, bug bounty, or pentesting.

---

## **Basic Usage**

```bash
waybackurls example.com
```

* Fetches all known archived URLs for `example.com` from Wayback Machine + Common Crawl.

---

## **1. Save Output to a File**

```bash
waybackurls example.com > urls.txt
```

* Stores all URLs in a file for later processing.

---

## **2. Multiple Domains at Once**

```bash
cat domains.txt | waybackurls
```

Where `domains.txt` contains:

```
example.com
test.com
site.org
```

* Useful for bulk recon.

---

## **3. Filter for Specific File Types**

Example: Only `.php` files

```bash
waybackurls example.com | grep "\.php$"
```

Example: Only `.js` files

```bash
waybackurls example.com | grep "\.js$"
```

---

## **4. Combine with Other Tools**

Extract live URLs with `httpx`:

```bash
waybackurls example.com | httpx
```

Check for parameters (potential XSS, SQLi points):

```bash
waybackurls example.com | grep "?"
```

---

## **5. Find Interesting Endpoints**

Look for admin or login pages:

```bash
waybackurls example.com | grep -Ei "admin|login|dashboard"
```

Look for API endpoints:

```bash
waybackurls example.com | grep -Ei "api|v1|v2"
```

---

## **6. Find Old & Hidden Pages**

```bash
waybackurls example.com | grep -Ei "\.bak|\.old|\.backup|\.zip|\.tar|\.gz"
```

* These might contain backups, source code, or sensitive data.

---

## **7. Combine with Nuclei for Vulnerability Scanning**

```bash
waybackurls example.com | nuclei -t vulnerabilities/
```

---

💡 **Pro Tips for Better Results**

* Always clean and deduplicate:

```bash
waybackurls example.com | sort -u
```

* Combine with `gf` (Gf Patterns) for parameter hunting:

```bash
waybackurls example.com | gf xss
```

---

If you want, I can make you a **ready-to-use Bash script** that runs `waybackurls` + filters + live check + parameter hunting automatically in Kali.
That way you can just run one command and get all the juicy endpoints.
