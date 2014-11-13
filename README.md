guzzle-fireclient
=================

A GuzzleHttp plugin that allows a remote HTTP call to act as a FirePHP client, proxying remote logs to the original caller.


Typical FirePHP Usage -- Works great!
1. Client browser requests a resource from Server A, with Firebug/FirePHP plugins installed
2. Server A delivers requested resource, writing FirePHP headers into the response to Client Browser (things like DB queries, errors, timing, etc.).
3. Client browser picks up FirePHP entries in response headers, which are formatted and displayed in the development console.
4. Client is able to transparently see what the server is doing at all times, can add additional FirePHP logs when necessary

SOA/Microservice Usage -- Client left in the dark
1. Client browser requests resource from Server A, with Firebug/FirePHP plugins installed
2. Server A builds resource for Client Browser by aggregating results from several internal microservices, hosted on servers B, C, D. Server A can not see work being performed by Servers B, C and D.
3. Client Browser receives only FirePHP entries that Server A is directly doing, which is
4. Client is not able to gain any insight into work being performed by other services, making debug difficult.

Solution!
1. Use microservices directly from client (not necessarily possible)

or.

2. Microservices are accessed via GuzzleHttp + Fireclient plugin. HTTP request acts as FirePHP client, and proxies those logs back to the original caller.
