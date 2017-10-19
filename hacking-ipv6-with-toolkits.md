# Hacking IPv6 with Toolkits

A number of IPv6 security toolkits exist, and should be used for checking your networks and devices.

Overview of main IPv6 hacking tools, note this is a subjective list. Feel free to suggest tools to me. It is highly recommended to install a small scale lab with a few virtualized devices, and try out running some of these tools.

Specialised toolkits and packages

* THC IPv6 Attack Toolkit  [https://github.com/vanhauser-thc/thc-ipv6](https://github.com/vanhauser-thc/thc-ipv6)
* SI6 Networks' IPv6 Toolkit
  A security assessment and troubleshooting tool for the IPv6 protocols [https://www.si6networks.com/tools/ipv6toolkit/](https://www.si6networks.com/tools/ipv6toolkit/) 

Unknown by me, but looks interesting

* https://github.com/ElevenPaths/EvilFOCA/



Regular pentesting and security tools with IPv6 support:

* Nmap \("Network Mapper"\) port scanner and accompanying software Nping, Ndiff, Ncat [https://nmap.org/](https://nmap.org/) has support for IPv6. Due to most subnets being /64 it cannot perform a full subnet scan, just too many IPs.
* Metasploit Framework, a tool for developing and executing exploit code against a remote target machine.

## Example Metasploit IPv6

It is recommended to try out Metasploit and doing a search show IPv6 support and modules.

```
msf > search ipv6

Matching Modules
================

   Name                                                            Disclosure Date  Rank    Description
   ----                                                            ---------------  ----    -----------
   auxiliary/scanner/discovery/ipv6_multicast_ping                                  normal  IPv6 Link Local/Node Local Ping Discovery
   auxiliary/scanner/discovery/ipv6_neighbor                                        normal  IPv6 Local Neighbor Discovery
   auxiliary/scanner/discovery/ipv6_neighbor_router_advertisement                   normal  IPv6 Local Neighbor Discovery Using Router Advertisement
   payload/bsd/x64/shell_bind_ipv6_tcp                                              normal  BSD x64 Command Shell, Bind TCP Inline (IPv6)
   payload/bsd/x64/shell_reverse_ipv6_tcp                                           normal  BSD x64 Command Shell, Reverse TCP Inline (IPv6)
   payload/bsd/x86/shell/bind_ipv6_tcp                                              normal  BSD Command Shell, Bind TCP Stager (IPv6)
   payload/bsd/x86/shell/reverse_ipv6_tcp                                           normal  BSD Command Shell, Reverse TCP Stager (IPv6)
   payload/bsd/x86/shell_bind_tcp_ipv6                                              normal  BSD Command Shell, Bind TCP Inline (IPv6)
   payload/bsd/x86/shell_reverse_tcp_ipv6                                           normal  BSD Command Shell, Reverse TCP Inline (IPv6)
   payload/cmd/unix/bind_netcat_gaping_ipv6                                         normal  Unix Command Shell, Bind TCP (via netcat -e) IPv6
   payload/cmd/unix/bind_perl_ipv6                                                  normal  Unix Command Shell, Bind TCP (via perl) IPv6
   payload/cmd/unix/bind_ruby_ipv6                                                  normal  Unix Command Shell, Bind TCP (via Ruby) IPv6
   payload/cmd/windows/bind_perl_ipv6                                               normal  Windows Command Shell, Bind TCP (via perl) IPv6
   payload/linux/x86/meterpreter/bind_ipv6_tcp                                      normal  Linux Mettle x86, Bind IPv6 TCP Stager (Linux x86)
   payload/linux/x86/meterpreter/bind_ipv6_tcp_uuid                                 normal  Linux Mettle x86, Bind IPv6 TCP Stager with UUID Support (Linux x86)
   payload/linux/x86/meterpreter/reverse_ipv6_tcp                                   normal  Linux Mettle x86, Reverse TCP Stager (IPv6)
   payload/linux/x86/shell/bind_ipv6_tcp                                            normal  Linux Command Shell, Bind IPv6 TCP Stager (Linux x86)
   payload/linux/x86/shell/bind_ipv6_tcp_uuid                                       normal  Linux Command Shell, Bind IPv6 TCP Stager with UUID Support (Linux x86)
   payload/linux/x86/shell/reverse_ipv6_tcp                                         normal  Linux Command Shell, Reverse TCP Stager (IPv6)
   payload/linux/x86/shell_bind_ipv6_tcp                                            normal  Linux Command Shell, Bind TCP Inline (IPv6)
   payload/php/bind_perl_ipv6                                                       normal  PHP Command Shell, Bind TCP (via perl) IPv6
   payload/php/bind_php_ipv6                                                        normal  PHP Command Shell, Bind TCP (via php) IPv6
   payload/php/meterpreter/bind_tcp_ipv6                                            normal  PHP Meterpreter, Bind TCP Stager IPv6
   payload/php/meterpreter/bind_tcp_ipv6_uuid                                       normal  PHP Meterpreter, Bind TCP Stager IPv6 with UUID Support
   payload/ruby/shell_bind_tcp_ipv6                                                 normal  Ruby Command Shell, Bind TCP IPv6
   payload/windows/dllinject/bind_ipv6_tcp                                          normal  Reflective DLL Injection, Bind IPv6 TCP Stager (Windows x86)
   payload/windows/dllinject/bind_ipv6_tcp_uuid                                     normal  Reflective DLL Injection, Bind IPv6 TCP Stager with UUID Support (Windows x86)
   payload/windows/dllinject/reverse_ipv6_tcp                                       normal  Reflective DLL Injection, Reverse TCP Stager (IPv6)
   payload/windows/meterpreter/bind_ipv6_tcp                                        normal  Windows Meterpreter (Reflective Injection), Bind IPv6 TCP Stager (Windows x86)
   payload/windows/meterpreter/bind_ipv6_tcp_uuid                                   normal  Windows Meterpreter (Reflective Injection), Bind IPv6 TCP Stager with UUID Support (Windows x86)
   payload/windows/meterpreter/reverse_ipv6_tcp                                     normal  Windows Meterpreter (Reflective Injection), Reverse TCP Stager (IPv6)
   payload/windows/meterpreter_reverse_ipv6_tcp                                     normal  Windows Meterpreter Shell, Reverse TCP Inline (IPv6)
   payload/windows/patchupdllinject/bind_ipv6_tcp                                   normal  Windows Inject DLL, Bind IPv6 TCP Stager (Windows x86)
   payload/windows/patchupdllinject/bind_ipv6_tcp_uuid                              normal  Windows Inject DLL, Bind IPv6 TCP Stager with UUID Support (Windows x86)
   payload/windows/patchupdllinject/reverse_ipv6_tcp                                normal  Windows Inject DLL, Reverse TCP Stager (IPv6)
   payload/windows/patchupmeterpreter/bind_ipv6_tcp                                 normal  Windows Meterpreter (skape/jt Injection), Bind IPv6 TCP Stager (Windows x86)
   payload/windows/patchupmeterpreter/bind_ipv6_tcp_uuid                            normal  Windows Meterpreter (skape/jt Injection), Bind IPv6 TCP Stager with UUID Support (Windows x86)
   payload/windows/patchupmeterpreter/reverse_ipv6_tcp                              normal  Windows Meterpreter (skape/jt Injection), Reverse TCP Stager (IPv6)
   payload/windows/shell/bind_ipv6_tcp                                              normal  Windows Command Shell, Bind IPv6 TCP Stager (Windows x86)
   payload/windows/shell/bind_ipv6_tcp_uuid                                         normal  Windows Command Shell, Bind IPv6 TCP Stager with UUID Support (Windows x86)
   payload/windows/shell/reverse_ipv6_tcp                                           normal  Windows Command Shell, Reverse TCP Stager (IPv6)
   payload/windows/upexec/bind_ipv6_tcp                                             normal  Windows Upload/Execute, Bind IPv6 TCP Stager (Windows x86)
   payload/windows/upexec/bind_ipv6_tcp_uuid                                        normal  Windows Upload/Execute, Bind IPv6 TCP Stager with UUID Support (Windows x86)
   payload/windows/upexec/reverse_ipv6_tcp                                          normal  Windows Upload/Execute, Reverse TCP Stager (IPv6)
   payload/windows/vncinject/bind_ipv6_tcp                                          normal  VNC Server (Reflective Injection), Bind IPv6 TCP Stager (Windows x86)
   payload/windows/vncinject/bind_ipv6_tcp_uuid                                     normal  VNC Server (Reflective Injection), Bind IPv6 TCP Stager with UUID Support (Windows x86)
   payload/windows/vncinject/reverse_ipv6_tcp                                       normal  VNC Server (Reflective Injection), Reverse TCP Stager (IPv6)
   payload/windows/x64/meterpreter/bind_ipv6_tcp                                    normal  Windows Meterpreter (Reflective Injection x64), Windows x64 IPv6 Bind TCP Stager
   payload/windows/x64/meterpreter/bind_ipv6_tcp_uuid                               normal  Windows Meterpreter (Reflective Injection x64), Windows x64 IPv6 Bind TCP Stager with UUID Support
   payload/windows/x64/meterpreter_reverse_ipv6_tcp                                 normal  Windows Meterpreter Shell, Reverse TCP Inline (IPv6) (x64)
   payload/windows/x64/shell/bind_ipv6_tcp                                          normal  Windows x64 Command Shell, Windows x64 IPv6 Bind TCP Stager
   payload/windows/x64/shell/bind_ipv6_tcp_uuid                                     normal  Windows x64 Command Shell, Windows x64 IPv6 Bind TCP Stager with UUID Support
   payload/windows/x64/vncinject/bind_ipv6_tcp                                      normal  Windows x64 VNC Server (Reflective Injection), Windows x64 IPv6 Bind TCP Stager
   payload/windows/x64/vncinject/bind_ipv6_tcp_uuid                                 normal  Windows x64 VNC Server (Reflective Injection), Windows x64 IPv6 Bind TCP Stager with UUID Support
   post/multi/gather/resolve_hosts                                                  normal  Multi Gather Resolve Hosts
   post/windows/manage/portproxy                                                    normal  Windows Manage Set Port Forwarding With PortProxy


msf >
```



