<%*

const selectedDate = await tp.system.prompt("Enter date (YYYY-MM-DD)", tp.date.now("YYYY-MM-DD"))

const year = window.moment(selectedDate).format("YYYY")

const month = window.moment(selectedDate).format("MM-MMMM")

const folder = `01-Daily-Diary/${year}/Notes/${month}`

await app.vault.createFolder(`01-Daily-Diary/${year}`).catch(()=>{})

await app.vault.createFolder(`01-Daily-Diary/${year}/Notes`).catch(()=>{})

await app.vault.createFolder(folder).catch(()=>{})

  

const filePath = `${folder}/${selectedDate}.md`

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

leave: false

summary_link: [[01-Daily-Diary/<% year %>/Summary]]

---

  

# 📔 Daily Diary - <% selectedDate %>

  

## ✅ What happened today

-

  

## 🐞 Issues / Debugging

-

  

## 👥 Meetings / Discussions

-

  

## 📚 Learnings

-

  

## 🌴 Leave / Personal Note

- If leave, mention reason here

  

## 🔗 Scrum Link

[[Scrum - <% selectedDate %>]]