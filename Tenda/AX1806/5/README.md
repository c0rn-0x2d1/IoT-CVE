Affect device: Tenda Router AX1806 v1.0.0.1(https://www.tenda.com.cn/download/detail-3306.html)

Vulnerability Type: Stack overflow

Impact: Denial of Service(DoS)

# Vulnerability description

This vulnerability lies in the `/goform/SetDDNSCfg` page which influences the lastest version of Tenda Router AX1806 v1.0.0.1: https://www.tenda.com.cn/download/detail-3306.html



There is a stack overflow vulnerability in the `formSetSysToolDDNS` function.



The `v3` variable is obtained directly from the http request parameter `serverName`.

This function uses strcpy to copy the **variable v3 to the stack variable s2** without any sercuity check.

![image-20220208222338204](image/1.png)

So attacker can construct **a long serverName parameter** in the http request,which causes stack overflow.

# POC

Poc of Denial of Service(DoS):
