<%*
const weekNum = tp.date.now("WW")
const year = tp.date.now("YYYY")
const folder = `03-Summaries/Weekly`
await app.vault.createFolder(folder).catch(()=>{})
const filePath = `${folder}/Week-${weekNum}-${year}`
await tp.file.move(filePath)
%>
# 📅 Weekly Summary - Week <% tp.date.now("WW") %>

## ✅ Major Deliverables
- 

## 🐞 Major Issues Solved
- 

## 📚 Learnings This Week
- 

## 🔗 Daily Notes
```dataview
TABLE date
FROM "01-Daily-Diary"
WHERE contains(file.name, "<% tp.date.now('YYYY') %>")
SORT file.name ASC
```