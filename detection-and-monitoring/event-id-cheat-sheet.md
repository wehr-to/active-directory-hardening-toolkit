Event ID	Meaning	Why It Matters
4624 > Successful logon	> Identify user sessions & logon types.
4625 > Failed logon	> Brute-force, password spray detection.
4672 > Special privileges assigned > User logged in with admin rights.
4688 > Process creation > Track suspicious binaries (like cmd.exe, powershell.exe, mimikatz.exe).
4697 > Service installed > Rare and often suspicious in production.
4769 > Kerberos service ticket requested > Investigate for Kerberoasting attempts.
4771 > Kerberos pre-auth failed	> Possible AS-REP roasting signal.
5140 > Network share accessed	> Can reveal lateral movement.
