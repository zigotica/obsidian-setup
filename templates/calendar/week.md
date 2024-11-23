---
---

> [!note] Life highlights of the week
> ```dataview
> TABLE life-hl
> FROM "pkm/calendar/daily"
> WHERE life-hl != null
> AND length(life-hl) > 1 
> AND file.day.year = number(substring(string(this.file.name), 0, 4))
> AND file.day.weekyear = number(substring(string(this.file.name), 6, 8))
> SORT file.day
> ```

> [!success] Work objectives reached during the week
> ```dataview
> TABLE work-obj
> FROM "pkm/calendar/daily"
> WHERE work-obj != null
> AND length(work-obj) > 1 
> AND file.day.year = number(substring(string(this.file.name), 0, 4))
> AND file.day.weekyear = number(substring(string(this.file.name), 6, 8))
> SORT file.day
> ```

> [!example] Work highlights of the week
> ```dataview
> TABLE work-hl
> FROM "pkm/calendar/daily"
> WHERE work-hl != null
> AND length(work-hl) > 1 
> AND file.day.year = number(substring(string(this.file.name), 0, 4))
> AND file.day.weekyear = number(substring(string(this.file.name), 6, 8))
> SORT file.day
> ```
