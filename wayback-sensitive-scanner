#!/usr/bin/env python3
import requests
import sys
from urllib.parse import urlparse, parse_qs
from termcolor import colored

# ===== ONLY SENSITIVE PARAMS =====
SENSITIVE_PARAMS = {
    'token', 'access_token', 'auth', 'auth_token', 'password', 'passwd',
    'apikey', 'api_key', 'secret', 'credentials', 'jwt', 'sessionid', 'sso',
    'private_key', 'client_secret', 'encryption_key', 'csrf_token', 'otp',
    'verification_code', 'file', 'filename', 'filepath', 'download',
    'attachment', 'doc', 'pdf', 'img', 'image', 'picture', 'photo', 'media',
    'upload', 'export', 'import', 'backup', 'user', 'admin', 'login'
}

# ===== TOOL BANNER =====
print(colored(r"""
███████╗███╗   ██╗██████╗ ██████╗  ██████╗ ██╗███╗   ██╗████████╗
██╔════╝████╗  ██║██╔══██╗██╔══██╗██╔═══██╗██║████╗  ██║╚══██╔══╝
█████╗  ██╔██╗ ██║██║  ██║██████╔╝██║   ██║██║██╔██╗ ██║   ██║   
██╔══╝  ██║╚██╗██║██║  ██║██╔═══╝ ██║   ██║██║██║╚██╗██║   ██║   
███████╗██║ ╚████║██████╔╝██║     ╚██████╔╝██║██║ ╚████║   ██║   
╚══════╝╚═╝  ╚═══╝╚═════╝ ╚═╝      ╚═════╝ ╚═╝╚═╝  ╚═══╝   ╚═╝   
""", 'cyan'))
print(colored(" " * 20 + "Sensitive Param Scanner v3.0", 'yellow'))
print(colored("═" * 65, 'blue'))

# ===== MAIN FUNCTION =====
if len(sys.argv) < 2:
    print(colored("[!] Usage: python3 scanner.py domain.com", 'red'))
    sys.exit()

domain = sys.argv[1]
api_url = f"http://web.archive.org/cdx/search/cdx?url=*.{domain}/*&output=text&fl=original&collapse=urlkey"

try:
    print(colored("[*] Fetching URLs from Wayback...", 'blue'))
    urls = requests.get(api_url, timeout=15).text.splitlines()
    
    if not urls:
        print(colored("[!] No URLs found in archive", 'red'))
        sys.exit()

    print(colored(f"[+] Found {len(urls)} URLs | Scanning for sensitive params and paths...", 'green'))
    
    found = False
    for url in urls:
        parsed_url = urlparse(url)

        # === Check for sensitive keywords in path or filename ===
        full_path = parsed_url.path.lower()
        for keyword in SENSITIVE_PARAMS:
            if keyword in full_path:
                print(colored(f"[MATCH]    {url}", 'magenta') +
                      colored(f" | keyword in path: {keyword}", 'cyan'))
                found = True
                break  # avoid duplicate prints for same URL

        # === Check for sensitive query parameters ===
        if '?' in url:
            params = parse_qs(parsed_url.query)
            for param in params:
                if param.lower() in SENSITIVE_PARAMS:
                    print(colored(f"[SENSITIVE] {url.split('?')[0]}", 'white') + 
                          colored(f"?{url.split('?')[1]}", 'yellow') + 
                          colored(f" | param: {param}", 'red'))
                    found = True

    if not found:
        print(colored("[!] No sensitive parameters or paths found", 'red'))

except Exception as e:
    print(colored(f"[X] Error: {str(e)}", 'red'))
finally:
    print(colored("═" * 65, 'blue'))
