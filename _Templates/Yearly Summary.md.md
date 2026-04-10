<%*
const year = tp.date.now("YYYY")
const folder = `03-Summaries/Yearly`
await app.vault.createFolder(folder).catch(()=>{})
const filePath = `${folder}/${year}-Summary`
await tp.file.move(filePath)
%>
# 🏆 <% tp.date.now("YYYY") %> Yearly Summary

## 🌟 Biggest Achievements
- 

## 📚 Top Learnings
- 

## 🚀 Career Progress
- 

## 🔗 Monthly Summaries
```dataview
LIST
FROM "03-Summaries/Monthly"
WHERE contains(file.name, "<% tp.date.now('YYYY') %>")
SORT file.name ASC
```