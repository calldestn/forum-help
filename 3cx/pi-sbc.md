**Raspberry Pi SBC Troubleshooting:**

*   You can use this to check for trailing white spaces:

    ```bash
    grep -nP "\s+$" .env
    ```

*   Use this for hidden characters:

    ```bash
    grep -nP "[^\x00-\x7F]" .env
    ```

*   Run this also from your PI to see if it's even able to reach the 3CX SIP:

    ```bash
    nc -zvu [3CX_IP_OR_FQDN] 5060
    ```
    e.g. `nc -zvu 192.168.0.200 5060`
    
    e.g. `nc -zvu 3cx.kmcomputing.com 5060`

*   In my case it is:

    ```bash
    root@print:~# nc -zvu 10.0.0.3 5060
    Connection to 10.0.0.3 5060 port [udp/sip] succeeded!
    ```

---

**Make sure to turn OFF the SIP ALG garbage on any router at 192.168.0.1**

Check your 3CX Dashboard for **IP Blacklist** and make sure you didn't get yourself added to it by incorrect settings.
