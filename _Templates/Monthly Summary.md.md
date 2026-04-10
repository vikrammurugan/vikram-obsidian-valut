<%*
const month = tp.date.now("MMMM-YYYY")
const folder = `03-Summaries/Monthly`
await app.vault.createFolder(folder).catch(()=>{})
const filePath = `${folder}/${month}`
await tp.file.move(filePath)
%>
# 📆 <% tp.date.now("MMMM YYYY") %> Summary

## 🚀 Key Achievements
- 

## 📊 Productivity Review
- 

## 🧠 Technical Learnings
- 

## 🔗 Weekly Links
```dataview
LIST
FROM "03-Summaries/Weekly"
WHERE contains(file.name, "<% tp.date.now('YYYY') %>")
SORT file.name ASC
```