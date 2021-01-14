---
title: "notices/add_comment"
pre: "<i class='fa fa-flag'></i>	"
draft: false
chapter: false
---

| Namespace | Name | Admin Only | Log Summary | Generates Event | Version Added
|:----------------:|:--------:|:--------:|:--------:|:--------:|:---:|
| notices | add_comment | no | no | yes | 1 |

#### Description
Add a comment to an alert notice. This can be done for any notice, even ones that have been marked as resolved.

### Input Arguments
* Required inputs:
   * "aid" : (string) ID for the alert notice to comment on
   * "comment" : (string) Text to add as a comment

* Optional:
   * none ({})


### Request Example Arguments
**ARGUMENTS ONLY**: See the {{< api-link "basics" >}} of API requests for additional formatting information.

```
{
  "aid" : "3",
  "comment" : "Anybody looking into this?"
}
```

### Reply Example
```
{
  "3" : {
    "aid" : "3",
    "caid" : "alert_rule_4",
    "tvid" : "server_id_1",
    "source" : "memory",
    "resolved" : false,
    "resolved_by" : "",
    "resolved_time" : "",
    "priority" : "warning",
    "system_time_triggered" : [1104541261]
    "alert_rule" : {
      "caid" : "alert_rule_4",
      "tvid" : "",
      "source" : "memory",
      "type" : "memory-free",
      "dataset" : "value",
      "alerttype" : "less_than",
      "value" : "20%",
      "priority" : "warning",
      "isactive" : true
    },
    "comments" : [
       "[20180102T15:32:55Z](admin_1) Anybody looking into this?"
    ]
  }
}
```


### Events
Events from this change will be sent to all administrators and any user with read access to impacted server(s). 

Example:
```
{
  "namespace" : "event",
  "name" : "",
  "id" : "event",
  "args" : {

  }
}
```

### Log Summary
This API call does not generate a detailed log summary item


#### See Also
* {{< api-link "notices/list" >}}
* {{< api-link "notices/set_resolved" >}}
* {{< api-link "notices/delete_comment" >}}
* {{< api-link "notices/delete" >}}
* {{< api-link "notices/create_fake" >}}
