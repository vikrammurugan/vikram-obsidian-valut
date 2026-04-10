<%*
const year = tp.date.now("YYYY")
const month = tp.date.now("MMMM-YYYY")
const summaryType = await tp.system.suggester(
  ["Weekly", "Monthly", "Yearly"],
  ["Weekly", "Monthly", "Yearly"],
  false,
  "What type of Scrum Summary?"
)

let folder, filePath

if (summaryType === "Weekly") {
  const weekNum = tp.date.now("WW")
  folder = `02-Scrum-Prep/${year}/Summaries/Weekly`
  await app.vault.createFolder(`02-Scrum-Prep/${year}/Summaries`).catch(()=>{})
  await app.vault.createFolder(folder).catch(()=>{})
  filePath = `${folder}/Scrum-Week-${weekNum}-${year}`

} else if (summaryType === "Monthly") {
  folder = `02-Scrum-Prep/${year}/Summaries/Monthly`
  await app.vault.createFolder(`02-Scrum-Prep/${year}/Summaries`).catch(()=>{})
  await app.vault.createFolder(folder).catch(()=>{})
  filePath = `${folder}/Scrum-${month}`

} else if (summaryType === "Yearly") {
  folder = `02-Scrum-Prep/${year}/Summaries`
  await app.vault.createFolder(folder).catch(()=>{})
  filePath = `${folder}/${year}-Scrum-Summary`
}

const existing = app.vault.getAbstractFileByPath(filePath + ".md")
if (existing) {
  const file = app.workspace.getLeaf(true)
  await file.openFile(existing)
  return
}
await tp.file.move(filePath)
%>
---
type: Scrum-<% summaryType %>-Summary
period: <% summaryType === "Weekly" ? tp.date.now("WW") : summaryType === "Monthly" ? tp.date.now("MMMM YYYY") : tp.date.now("YYYY") %>
year: <% year %>
---

# 🎯 Scrum <% summaryType %> Summary - <% summaryType === "Weekly" ? "Week " + tp.date.now("WW") + " · " + year : summaryType === "Monthly" ? tp.date.now("MMMM YYYY") : year %>

## ✅ Completed Tasks
- 

## 🚧 Carried Over / Unfinished
- 

## 🐞 Blockers Encountered
- 

## 🏆 Wins This <% summaryType === "Weekly" ? "Week" : summaryType === "Monthly" ? "Month" : "Year" %>
- 

## 📚 Learnings & Takeaways
- 

## 🔗 Scrum Notes
```dataview
LIST
FROM "02-Scrum-Prep/<% year %>/Sprint-Notes"
<% summaryType === "Weekly" ? 'WHERE contains(file.name, "' + tp.date.now("YYYY-WW") + '")' : summaryType === "Monthly" ? 'WHERE contains(file.name, "' + tp.date.now("YYYY-MM") + '")' : '' %>
SORT file.name ASC
```