# 📝 Defold CSV to Lua Table EditorScript

This EditorScript allows you to **convert CSV files into Lua tables** directly inside the [Defold game engine](https://defold.com) editor.

It supports both **keyed tables** and **array tables**, and is useful for importing game data like enemies, items, or maps from spreadsheets.

---

## ✨ Features

- ✅ Convert `.csv` files to Lua tables
- ✅ Choose output format via dialog:
  - **Keyed table**: `id = { ... }`
  - **Array table**: `{ {...}, {...} }`
- ✅ Ignores metadata columns using `@` prefix (`@note`, `@script`, etc.)
- ✅ Supports multiline CSV fields
- ✅ Supports embedded Lua functions (in `@script` columns)
- ✅ Automatically strips Notion-style `(https://...)` references

---

## 📦 Installation

1. Copy `csv_to_lua.lua` into your project, e.g.:
/main/editor_scripts/csv_to_lua.lua

go
コピーする
編集する

2. Add it to your `game.project` file:
```ini
[editor]
scripts = /main/editor_scripts/csv_to_lua.lua
Restart the Defold Editor (if already open)

🚀 Usage
Right-click any .csv file in the Assets panel

Choose “Convert CSV to Lua Table”

A dialog will appear asking if you want to use the first column as the key

A .lua file will be generated alongside the CSV

🧪 Example
CSV:
bash
コピーする
編集する
key,type,hp
slime,small,10
goblin,medium,20
Output (keyed):
lua
コピーする
編集する
return {
  slime = { type = "small", hp = 10 },
  goblin = { type = "medium", hp = 20 },
}
Output (array):
lua
コピーする
編集する
return {
  { key = "slime", type = "small", hp = 10 },
  { key = "goblin", type = "medium", hp = 20 },
}
🛠 Special Behavior
Columns with header names starting with @ (e.g. @note) are ignored

Columns named @script can contain raw Lua functions, which are injected without quotes:

lua
コピーする
編集する
function() return 1 end
Links in the form of (https://...) are stripped from CSV fields, making it Notion-compatible

🤝 License
MIT License

🙌 Contributions
Feel free to submit pull requests or open issues for improvements, bugs, or suggestions!

🔗 Related
Defold Editor Scripts Documentation