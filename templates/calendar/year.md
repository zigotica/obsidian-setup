---
---

> [!note] Life highlights of the year
> ```dataview
> TABLE life-hl
> FROM "pkm/calendar/daily"
> WHERE life-hl != null
> AND length(life-hl) > 1 
> AND file.day.year = number(substring(string(this.file.name), 0, 4))
> SORT file.day
> ```

> [!success] Work objectives reached during the year
> ```dataview
> TABLE work-obj
> FROM "pkm/calendar/daily"
> WHERE work-obj != null
> AND length(work-obj) > 1 
> AND file.day.year = number(substring(string(this.file.name), 0, 4))
> SORT file.day
> ```

> [!example] Work highlights of the year
> ```dataview
> TABLE work-hl
> FROM "pkm/calendar/daily"
> WHERE work-hl != null
> AND length(work-hl) > 1 
> AND file.day.year = number(substring(string(this.file.name), 0, 4))
> SORT file.day
> ```

