<%*
const year = tp.date.now("YYYY")
const folder = `01-Daily-Diary/${year}/Summaries`
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
FROM "01-Daily-Diary/<% tp.date.now('YYYY') %>/Summaries/Monthly"
SORT file.name ASC
```