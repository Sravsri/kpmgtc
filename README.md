# kpmgtc
challenge 1
Template Solution Architecture

This template will deploy:

One Virtual Network with four subnets
4 Network Security Group, one for each subnet
External Load Balancer to load balance Web Traffic(HTTP & HTTPS) to web servers
Internal Load Balancer to load balance traffic for app VM's
2 Public IP’s, one for external Load balancer and other for Jump VM
Virtual Machine Availability sets for Web Tier, Application Tier and Database tier
One Jump VM to faclitate RDP access to all other tier VMs
Multiple windows VMs with nics

Challenge  2
To do challenge 2 i have created a virutal machine on azure using the rest api querying VMs metadata in jason format

API get request would look like following
GET https://management.azure.com/subscriptions/[subscriptionId]/resourceGroups/sudhaEX/providers/Microsoft.Compute/virtualMachines/samplevm1?api-version=2021-07-01 Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiIsIng1dCI6Imwzc1EtNTBjQ0g0eEJWWkxIVEd3blNSNzY4MCIsImtpZCI6Imwzc1EtNTBjQ0g0eEJWWkxIVEd3blNSNzY4MCJ9.eyJhdWQiOiJodHRwczovL21hbmFnZW1lbnQuY29yZS53aW5kb3dzLm5ldC8iLCJpc3MiOiJodHRwczovL3N0cy53aW5kb3dzLm5ldC9kMWZlOGU0NC00ZDM1LTRkYWQtOGVhOS1kOWQ5Y2I5YTk4OGMvIiwiaWF0IjoxNjMyOTA3MDA3LCJuYmYiOjE2MzI5MDcwMDcsImV4cCI6MTYzMjkxMDkwNywiYWNyIjoiMSIsImFpbyI6IkFZUUFlLzhUQUFBQSthR3l6YktmVmpOTkE1TDc5a3I3S0VDVUpCdzh6V3FWRzFaLzQxSFV5Z0NYV0ZtK25SZmRkeWd1VG9QblhtWnZTQjNHeFpQK0xBNVYvV1BoWjl0c3VWWTdlS1hDM0J5a3ViRVJPMThhTHN1VmZta1V2cEdOa1dxM2hRbjAzOXdrdHdBT0s4SWhPTktieEkwOVlCcmxtKzc2eGZ4SkZXRFVWOFBBTUpjWUpnST0iLCJhbHRzZWNpZCI6IjU6OjEwMDMyMDAwODQwMDM1MDkiLCJhbXIiOlsicHdkIiwibWZhIl0sImFwcGlkIjoiN2Y1OWE3NzMtMmVhZi00MjljLWEwNTktNTBmYzViYjI4YjQ0IiwiYXBwaWRhY3IiOiIyIiwiZW1haWwiOiJzdWRoYS5iYWxhZ3VydUBhdmV2YS5jb20iLCJmYW1pbHlfbmFtZSI6IkJhbGFndXJ1IiwiZ2l2ZW5fbmFtZSI6IlN1ZGhhIiwiZ3JvdXBzIjpbIjA4YzY3NTc5LTZhOGUtNGZiMi04ZTlmLTBiNTAxNTIwMTQzNCIsIjI5OTIxYzFjLTAyY2MtNDZmNi04ZjFkLWQ3OGE0YjkyYThhNCIsImRkNTc3NDU2LTZlNTktNDg1Yi05MGUyLTY0Y2UzYzdlZTFhZiIsImE2YWFlMjRhLTE1ZTYtNDQ5NC04MjZlLTE1ZjIzZmQ5YmFkNSIsImM3ZjkxNzZlLWM0MzctNDFiYy04NzVjLThmZjg0NGUyYWYxZSJdLCJpZHAiOiJodHRwczovL3N0cy53aW5kb3dzLm5ldC80MjVhNTU0Ni01YTZlLTRmMWItYWI2Mi0yM2Q5MWQwN2Q4OTMvIiwiaXBhZGRyIjoiNDkuMzcuMTY3LjQ4IiwibmFtZSI6IlN1ZGhhIEJhbGFndXJ1Iiwib2lkIjoiMThlNmU0NGEtZGQxNi00YTgzLTljZDYtYTQ3NmQ4OTUwNzA4IiwicHVpZCI6IjEwMDMyMDAwQTlCQTQ4MzciLCJyaCI6IjAuQVRvQVJJNy0wVFZOclUyT3Fkblp5NXFZakhPbldYLXZMcHhDb0ZsUV9GdXlpMFE2QU5BLiIsInNjcCI6InVzZXJfaW1wZXJzb25hdGlvbiIsInN1YiI6InA1MG0zaDlRbTlXV2xxSHVSY0p2SnB1b3l5U1VEajlwR1ZHRVlILThxNHMiLCJ0aWQiOiJkMWZlOGU0NC00ZDM1LTRkYWQtOGVhOS1kOWQ5Y2I5YTk4OGMiLCJ1bmlxdWVfbmFtZSI6InN1ZGhhLmJhbGFndXJ1QGF2ZXZhLmNvbSIsInV0aSI6Inh5enkxNWxBTlVlNEtYQVpjZm1EQUEiLCJ2ZXIiOiIxLjAiLCJ3aWRzIjpbIjEzYmQxYzcyLTZmNGEtNGRjZi05ODVmLTE4ZDNiODBmMjA4YSJdLCJ4bXNfdGNkdCI6MTU1NjI2NjU2MX0.AUhefddVgQGWNuhk9hrSzqtHFA6ojKzW7yUZARtRhccTO-l28WNHVZ5GajNbyEVHJzgZ9hfuWsiYTmqjhAdHmHbUZajGuESagmqVfv-mriAFuTNPjm4EWT3V2KePynFGjSuXVblicS5Tt-q73lP98Sk5PjXdlg9PtqaVH0K76CB7BC_E0cwzGT3zIucFMFxcJsINuxfPav7fF1Xju2Oqm3ivjZEnjC6JZzdNXBmU5CdiyEkQL6pP5KZuPOPCkvuFmeGTF8-lbz5KKvvsHkGTAw56lBe8YriQbqxCFcKMk2Q6LelDvi232JawVSIZQ63bHWzv4MP9UWx7g9FBVRWWig

Request Header

cache-control: no-cache content-type: application/json; charset=utf-8 date: Wed, 29 Sep 2021 09:25:19 GMT expires: -1 pragma: no-cache server: Microsoft-HTTPAPI/2.0, Microsoft-HTTPAPI/2.0 strict-transport-security: max-age=31536000; includeSubDomains x-ms-correlation-request-id: 93170955-050c-42d8-997a-adfe35573c03 x-ms-ratelimit-remaining-resource: Microsoft.Compute/LowCostGet3Min;3997,Microsoft.Compute/LowCostGet30Min;31997 x-ms-ratelimit-remaining-subscription-reads: 11992 x-ms-request-id: 1da4dda7-bf8e-4829-97f0-d993dacc5208 x-ms-routing-request-id: JIOINDIAWEST:20210929T092520Z:93170955-050c-42d8-997a-adfe35573c03


Response.json
{
  "name": "samplevm1",
  "id": "/subscriptions/[subscriptionId]/resourceGroups/sudhaEX/providers/Microsoft.Compute/virtualMachines/samplevm1",
  "type": "Microsoft.Compute/virtualMachines",
  "location": "centralus",
  "properties": {
    "vmId": "247fe3c7-a9c8-4d14-a864-1d4923014e23",
    "availabilitySet": {
      "id": "/subscriptions/[subscriptionId]/resourceGroups/sudhaEX/providers/Microsoft.Compute/availabilitySets/SAMPLE-AS"
    },
    "hardwareProfile": {
      "vmSize": "Standard_DS1_v2"
    },
    "storageProfile": {
      "imageReference": {
        "publisher": "MicrosoftWindowsServer",
        "offer": "WindowsServer",
        "sku": "2016-Datacenter-Server-Core",
        "version": "latest",
        "exactVersion": "14393.4651.2109130103"
      },
      "osDisk": {
        "osType": "Windows",
        "name": "samplevm1_OsDisk_1_1b018d9509b1469a902c827e166a5aa0",
        "createOption": "FromImage",
        "caching": "ReadWrite",
        "managedDisk": {
          "storageAccountType": "StandardSSD_LRS",
          "id": "/subscriptions/[subscriptionId]/resourceGroups/sudhaEx/providers/Microsoft.Compute/disks/samplevm1_OsDisk_1_1b018d9509b1469a902c827e166a5aa0"
        },
        "diskSizeGB": 127
      },
      "dataDisks": []
    },
    "osProfile": {
      "computerName": "samplevm1",
      "adminUsername": "samplevm1",
      "windowsConfiguration": {
        "provisionVMAgent": true,
        "enableAutomaticUpdates": true,
        "patchSettings": {
          "patchMode": "AutomaticByOS",
          "assessmentMode": "ImageDefault",
          "enableHotpatching": false
        }
      },
      "secrets": [],
      "allowExtensionOperations": true,
      "requireGuestProvisionSignal": true
    },
    "networkProfile": {
      "networkInterfaces": [
        {
          "id": "/subscriptions/[subscriptionId]/resourceGroups/sudhaEx/providers/Microsoft.Network/networkInterfaces/samplevm1830"
        }
      ]
    },
    "diagnosticsProfile": {
      "bootDiagnostics": {
        "enabled": true
      }
    },
    "provisioningState": "Succeeded"
  }
}
