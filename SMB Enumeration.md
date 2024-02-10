# SMB Enumeration

### Nmap

1. **SMB Protocol and Dialect Scan:**
    - `nmap -p445 --script smb-protocols 10.0.17.200`
    - to check what versions of the SMB protocol are supported by the target server
        - Different versions of SMB have different features and security levels.
2. **SMB Security Mode Scan:**
    - `nmap -p445 --script smb-security-mode 10.0.17.200`
    - Retrieves information about the SMB security level.
        - The security mode indicates how the server handles authentication and encryption of SMB connections.
3. **Enumerate Users (Guest Access):**
    - `nmap -p445 --script smb-enum-sessions 10.0.17.200`
    - Lists users logged in without credentials (requires guest login enabled).
        - to list the users who are currently logged in to the SMB server without providing any credentials
4. **Enumerate Users (Valid Credentials):**
    - `nmap -p445 --script smb-enum-sessions --script-args smbusername=administrator,smbpassword=smbserver_771 10.0.17.200`
    - Lists users logged in with provided credentials (if valid).
5. **Enumerate Shares (Guest Access):**
    - `nmap -p445 --script smb-enum-shares 10.0.17.200`
    - Lists available shares and permissions using guest access.
        - list the shares and permissions that are available on the SMB server
6. **Enumerate Shares (Valid Credentials):**
    - `nmap -p445 --script smb-enum-shares --script-args smbusername=administrator,smbpassword=smbserver_771 10.0.17.200`
    - Lists available shares and permissions using provided credentials.
7. **Enumerate Users (Valid Credentials):**
    - `nmap -p445 --script smb-enum-users --script-args smbusername=administrator,smbpassword=smbserver_771 10.0.17.200`
        - Lists users on the target machine using provided credentials.
8. **Server Statistics (Valid Credentials):**
    - `nmap -p445 --script smb-server-stats --script-args smbusername=administrator,smbpassword=smbserver_771 10.0.17.200`
    - Retrieves server statistics like login attempts, errors, and open files.
9. identifies the operating system
    - **`nmap --script smb-os-discovery.nse -p 445 192.126.66.3`**
    - It checks what kind of server software is running on that IP address
10. Shared folders
    - **`nmap -p445 --script smb-enum-shares,smb-ls --script-args smbusername=administrator,smbpassword=smbserver_771 10.0.17.200`**
    - It finds out what folders are shared on the server and lists their contents.
11. **Enumerate Domains (Valid Credentials):**
    - `nmap -p445 --script smb-enum-domains --script-args smbusername=administrator,smbpassword=smbserver_771 10.0.17.200`
    - Identifies domains the target machine is part of (if applicable).

## msfconsole

1. use auxiliary/scanner/smb/smb_version
2. use auxiliary/scanner/smb/smb_enumusers
3. use auxiliary/scanner/smb/smb2 **(version enumeration smb2)**
4. use auxiliary/scanner/smb/smb_login (**Brute-Forcing**)
    1. set PASS_FILE /usr/share/wordlists/metasploit/unix_passwords.txt
    2. set SMBUser jane
5. use auxiliary/scanner/smb/pipe_auditor (**named pipes** are accessible over SMB)
    1. set SMBPass password1
    2. set SMBUser admin
    

## SMBmap

Samba Share Enumerator

**--download** PATH  **- -upload** SRC DST - -**delete** PATH TO FILE

- discover all shared folders and drives.`-d .`
- Execute the command on the target **`-x 'ipconfig'`**
- Listing all drives on the specified host **`-L`**
- List contents of the directory of C:\ drive **`-r 'C$'`**

```jsx
smbmap -H 10.0.28.123 -u Administrator -p 'smbserver_771' -d . -x **-x 'ipconfig' -L -r 'C$'**
```

## [Smbclient](https://medium.com/@ibo1916a/smbclient-command-2803de274e46)

**ftp-like client to access SMB/CIFS resources on servers**

**`smbclient -L 192.126.66.3 -N`**

- **List SMB Shares Providing Username**
    - **`smbclient -L [192.212.251.3](notion://192.212.251.3/jane)-U jane`**
- **List Specified Share Path Content**
    - `smbclient -L \\192.168.1.10\Backup\2021`
- **-`N` : no Password**
- **Smb Client Interactive Shell**
    - smbclient "\\fileserver\Backup" -U ismail

### enum4linux

- List all users that exists on the samba server  using enum4Linux.
    
    **`enum4linux -U 192.144.106.3``**
    
- Find the OS version of samba server using enum4Linux.
    - `**enum4linux -o 192.144.106.3**`
- Pulls usernames from the default RID range (500-550,1000-1050).
    - `**enum4linux -r -u "admin" -p "password1" 192.212.251.3**`
-  List all available shares on  the samba server using enum4Linu
      - `enum4linux -G 192.144.106.3`
- Is samba server configured for printing?
      -`-i` 

### [rpcclient](https://book.hacktricks.xyz/network-services-pentesting/pentesting-smb/rpcclient-enumeration)

- `**rpcclient -U "" -N 192.126.66.3**`
- Find SID of user “admin” using rpcclient.
    - **`lookupnames admin`**
- List all users that exists on the samba server using rpcclient
    - **`enumdomusers` (Enumerate domain users)**
