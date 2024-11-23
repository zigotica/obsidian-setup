---
---

Quick Navigation:
```dataviewjs
/*
    previous/next note by date for Daily Notes
    Also works for other files having a `date:` YAML entry.
    MCH 2021-06-14
*/
var none = '(none)';
var p = dv.pages('"' + dv.current().file.folder + '"').where(p => p.file.day).map(p => [p.file.name, p.file.day.toISODate()]).sort(p => p[1]);
var t = dv.current().file.day ? dv.current().file.day.toISODate() : luxon.DateTime.now().toISODate();
// Obsidian uses moment.js; Luxon’s format strings differ!
var format = app['internalPlugins']['plugins']['daily-notes']['instance']['options']['format'] || 'YYYY-MM-DD';
var current = '(' + moment(t).format(format) + ')';
var nav = [];
var today = p.find(p => p[1] == t);
var next = p.find(p => p[1] > t);
var prev = undefined;
p.forEach(function (p, i) {
    if (p[1] < t) {
        prev = p;
    }
});
nav.push(prev ? '[[' + prev[0] + ']]' : none);
//nav.push(today ? today[0] : none);
//nav.push(today ? today[0] : current);
nav.push(next ? '[[' + next[0] + ']]' : none);

//dv.list(nav);
//dv.paragraph(nav.join(" · "));
dv.paragraph('< ' + nav[0] + ' | ' + nav[1] + ' >');
```

---

# Notes
(Remember to use life-hl, work-hl or work-obj where needed)

- <% tp.file.cursor() %>

---

> [!note] Notes created today
> ```dataview
> List FROM "" AND !"calendar" AND !"utils"
> WHERE file.cday = date("<%tp.date.now("YYYY-MM-DD")%>") 
> SORT file.ctime asc
> ```

> [!note] Notes last modified today
> ```dataview
> List FROM "" AND !"calendar" AND !"utils" 
> WHERE file.mday = date("<%tp.date.now("YYYY-MM-DD")%>") 
> SORT file.mtime asc
> ```
