<%*
const year = tp.date.now("YYYY")
const weekNum = tp.date.now("WW")
const monthName = tp.date.now("MMMM-YYYY")
const monthDisplay = tp.date.now("MMMM YYYY")

// ── Folder Setup ──────────────────────────────────────────
const baseFolder    = `01-Daily-Diary/${year}/Summaries`
const weeklyFolder  = `${baseFolder}/Weekly`
const monthlyFolder = `${baseFolder}/Monthly`

await app.vault.createFolder(`01-Daily-Diary/${year}`).catch(()=>{})
await app.vault.createFolder(baseFolder).catch(()=>{})
await app.vault.createFolder(weeklyFolder).catch(()=>{})
await app.vault.createFolder(monthlyFolder).catch(()=>{})

// ── File Paths ─────────────────────────────────────────────
const weeklyPath  = `${weeklyFolder}/Week-${weekNum}-${year}.md`
const monthlyPath = `${monthlyFolder}/${monthName}.md`
const yearlyPath  = `${baseFolder}/${year}-Summary.md`

// ── Weekly Content ─────────────────────────────────────────
const weeklyContent = `---
type: weekly-summary
week: ${weekNum}
year: ${year}
---

# 📅 Weekly Summary - Week ${weekNum} (${year})

## ✅ Major Deliverables
- 

## 🐞 Major Issues Solved
- 

## 📚 Learnings This Week
- 

## 🔗 Daily Notes
\`\`\`dataview
TABLE date
FROM "01-Daily-Diary/${year}/Notes"
WHERE contains(file.name, "${year}")
SORT file.name ASC
\`\`\`
`

// ── Monthly Content ────────────────────────────────────────
const monthlyContent = `---
type: monthly-summary
month: ${monthName}
year: ${year}
---

# 📆 ${monthDisplay} Summary

## 🚀 Key Achievements
- 

## 📊 Productivity Review
- 

## 🧠 Technical Learnings
- 

## 🔗 Weekly Summaries
\`\`\`dataview
LIST
FROM "01-Daily-Diary/${year}/Summaries/Weekly"
SORT file.name ASC
\`\`\`
`

// ── Yearly Content ─────────────────────────────────────────
const yearlyContent = `---
type: yearly-summary
year: ${year}
---

# 🏆 ${year} Yearly Summary

## 🌟 Biggest Achievements
- 

## 📚 Top Learnings
- 

## 🚀 Career Progress
- 

## 🔗 Monthly Summaries
\`\`\`dataview
LIST
FROM "01-Daily-Diary/${year}/Summaries/Monthly"
SORT file.name ASC
\`\`\`
`

// ── Create Files (skip if already exists) ──────────────────
const vault = app.vault

if (!vault.getAbstractFileByPath(weeklyPath)) {
  await vault.create(weeklyPath, weeklyContent)
  new Notice(`✅ Created: Week-${weekNum}-${year}`)
} else {
  new Notice(`⚠️ Already exists: Week-${weekNum}-${year}`)
}

if (!vault.getAbstractFileByPath(monthlyPath)) {
  await vault.create(monthlyPath, monthlyContent)
  new Notice(`✅ Created: ${monthName}`)
} else {
  new Notice(`⚠️ Already exists: ${monthName}`)
}

if (!vault.getAbstractFileByPath(yearlyPath)) {
  await vault.create(yearlyPath, yearlyContent)
  new Notice(`✅ Created: ${year}-Summary`)
} else {
  new Notice(`⚠️ Already exists: ${year}-Summary`)
}

// ── Open Weekly file as the active note ───────────────────
const weeklyFile = vault.getAbstractFileByPath(weeklyPath)
if (weeklyFile) {
  await app.workspace.getLeaf(true).openFile(weeklyFile)
}

// ── Delete the blank launcher note Templater created ──────
const thisFile = tp.file.find_tfile(tp.file.title)
await app.vault.delete(thisFile)
await app.vault.delete(tp.config.target_file)
%>