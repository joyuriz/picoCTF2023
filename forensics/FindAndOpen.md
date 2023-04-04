# forensics/MSB
Write-up by: [ptrckstuns](https://github.com/ptrckstuns)

## Description
Someone might have hidden the password in the trace file. Find the key to unlock this file (`flag.zip`). This tracefile (`dump.pcap`) might be good to analyze.

- [dump.pcap](/attachments/dump.pcap)
- [flag.zip](/attachments/flag.zip)

Official Hint:
> "Flag is splitted"

## Solution
1. Open and analyze the PCAP file in Wireshark.
2. **FIND** - A Base64 string found in the PCAP
   ![](/attachments/findandopen1.png)
3. `This is the secret: picoCTF{R34DING_LOKd_` decoded from Base64
4. **OPEN** - Use the secret `picoCTF{R34DING_LOKd_` to enter the password to `flag.zip`
   ![](/attachments/findandopen2.png)

**Flag:** `picoCTF{R34DING_LOKd_fil56_succ3ss_c2e6d949}`
