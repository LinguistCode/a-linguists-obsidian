---
tags: 
icon: TiWritingSign
aliases: 
daily-reading: 
daily-writing: 
cssclasses:
  - dailynote
---
![[sunrise.jpeg|banner-fade]]
# <% tp.date.now("dddd, MMMM, Do YYYY") %>

>[!tracker]+
> - @ Lectures : `=this.daily-reading`
> - -w Rédaction :  `=this.daily-writing`
> - Autre : 

>[!column|no-t]
>
>> [!tasklist] Due Today
>> ```tasks
>> not done
>> happens <% tp.date.now("YYYY-MM-DD")%>
>> hide recurrence rule
>> hide due date
>> hide scheduled date
>> sort by priority
>> ```
>
>> [!urgent] Overdue !
>> ```tasks
>> not done
>> (due before <% tp.date.now("YYYY-MM-DD")%>) OR ((happens before <% tp.date.now("YYYY-MM-DD")%>) AND (priority is above none))
>> hide recurrence rule
>> sort by due date
>> ```


## Quick Notes

![[QN - <%tp.date.now("YYYY-MM-DD")%>]]

<br>

## Thoughts

*Not a single recorded thought today*


## Here's what you checked today : 

 ```tasks
 done <%tp.date.now("YYYY-MM-DD")%>
 hide due date
 hide scheduled date
 ```

> *Well done !*



## A glance to the future

 ```tasks
not done
due before in 7 days
hide scheduled date
```


<br>

---

<% tp.web.daily_quote() %>