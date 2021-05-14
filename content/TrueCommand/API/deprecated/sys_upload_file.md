---
title: "sys/upload_file"
pre: "<i class='fa fa-upload'></i>	"
draft: false
chapter: false
---

| Namespace | Name | Admin Only | Log Summary | Generates Event | Version Added | Version Removed |
|:----------------:|:--------:|:--------:|:--------:|:--------:|:---:|:---:|
| sys | upload_file | yes | no | no | 1 | 2.0 |

#### Description
Request a temporary authentication token for uploading a file to the TrueCommand system.
Access credentials are only valid for 10 minutes after the request, and can be used to send a POST request to the "[TrueCommand system IP]/upload" URL to upload the file.
Files that are uploaded are **temporary**. They will be removed the next time the system is rebooted.

### Input Arguments
* Required:
   * none ({})
* Optional:
   * none ({})


### Reply Example Arguments
**ARGUMENTS ONLY**: See the {{< api-link "basics" >}} of API requests for additional formatting information.

```
  "args" : {
    "upload_user" : "ihgUyfkljh",
    "upload_pass" : "oihvUIiu8yvU6y75786yv",
    "upload_expires" : "yyyyMMddhhmmss"
  }
```

### Log Summary
This API call does not generate a detailed log summary item

### Events
This API call does not emit any middleware events.

#### See Also
* {{< api-link "sys/info" >}}
* {{< api-link "sys/middleware_log" >}}