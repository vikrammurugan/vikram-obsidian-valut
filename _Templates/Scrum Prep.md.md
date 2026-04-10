<%*
const selectedDate = await tp.system.prompt("Scrum date (YYYY-MM-DD)", tp.date.now("YYYY-MM-DD"))
const day = window.moment(selectedDate).day()
if (day === 0 || day === 6) {
  tR += "# 🚫 Weekend\nNo scrum prep needed for weekends."
  return
}
const leaveToday = await tp.system.suggester(["No","Yes"],["No","Yes"], false, "Are you on leave?")
const year = window.moment(selectedDate).format("YYYY")
const folder = `02-Scrum-Prep/${year}/Sprint-Notes`
await app.vault.createFolder(`02-Scrum-Prep/${year}`).catch(()=>{})
await app.vault.createFolder(folder).catch(()=>{})
const filePath = `${folder}/Scrum - ${selectedDate}.md`
const existing = app.vault.getAbstractFileByPath(filePath)
if (existing) {
  const file = app.workspace.getLeaf(true)
  await file.openFile(existing)
  return
}
await tp.file.move(filePath.replace('.md',''))
%>
---
date: <% selectedDate %>
leave: <% leaveToday === "Yes" %>
summary_link: [[02-Scrum-Prep/<% year %>/Summary]]
---

# 🎯 Scrum Update - <% selectedDate %>

## ✅ Yesterday
[[01-Daily-Diary/<% year %>/Notes/<% window.moment(selectedDate).format("MM-MMMM") %>/<% window.moment(selectedDate).subtract(1, 'days').format("YYYY-MM-DD") %>]] > ✅ What happened today

## ✍️ Yesterday Talking Points
* 
* 
* 

## 🚧 Blockers
* 

## 🎯 Today Plan
* 

## 🌴 Leave
* <% leaveToday === "Yes" ? "On leave today" : "Working" %>