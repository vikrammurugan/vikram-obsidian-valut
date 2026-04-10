<%*
const monthName = tp.date.now("MMMM-YYYY")
const year = tp.date.now("YYYY")
const folder = `01-Daily-Diary/${year}/Summaries/Monthly`
await app.vault.createFolder(`01-Daily-Diary/${year}/Summaries`).catch(()=>{})
await app.vault.createFolder(folder).catch(()=>{})
const filePath = `${folder}/${monthName}`
await tp.file.move(filePath)
%>
# 📆 <% tp.date.now("MMMM YYYY") %> Summary

## 🚀 Key Achievements
- 

## 📊 Productivity Review
- 

## 🧠 Technical Learnings
- 

## 🔗 Weekly Summaries
```dataview
LIST
FROM "01-Daily-Diary/<% tp.date.now('YYYY') %>/Summaries/Weekly"
SORT file.name ASC
```