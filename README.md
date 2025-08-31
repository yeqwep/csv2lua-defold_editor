# 📝 CSV to Lua Table Defold EditorScript

This EditorScript allows you to **convert CSV files into Lua tables** directly inside the [Defold game engine](https://defold.com) editor.

It supports both **keyed tables** and **array tables**, and is useful for importing game data like enemies, items, or maps from spreadsheets.

---

## ✨ Features

- ✅ Convert `.csv` files to Lua tables
- ✅ The first column of the CSV (key) can be used as the table key in the Lua output.
- ✅ Choose output format via dialog:
  - **Keyed table**: `id = { ... }`
  - **Array table**: `{ {...}, {...} }`
- ✅ Ignores metadata columns using `@` prefix (`@note`, etc.)
- ✅ Supports multiline CSV fields
- ✅ Automatically strips Notion-style `(https://...)` references
- ✅ Supports boolean values (`true` / `false`) correctly as Lua booleans
- ✅ Supports deep nested tables by combining related columns.
  - For example, CSV columns like `buffs_name` and `buffs_value` are converted into a nested Lua table:

   CSV:
   buffs_name,buffs_value
   "atk_up",5

   Lua output:
   buffs = {
       { name = "atk_up", value = 5 }
   }

---

## 📦 Installation

1. Copy `csv2lua.editor_script` into your project, e.g.:
/editor_scripts/csv2lua.editor_script

2. Project > Reload Editor Scripts

## 🚀 Usage
1. **Right-click** any .csv file in the **Assets panel**

2. Choose **“Convert CSV to Lua Table”** from the context menu.

3. A dialog will appear asking:
   > *"Use column as keys?"*
   - Click **"Use"** to generate a keyed Lua table (e.g. `id = {...}`)
   - Click **"No"** to generate an array-based table (e.g. `{ {...}, {...} }`)
4. A `.lua` file will be generated **alongside the CSV** with the converted content.

## 🧪 Example
**Example CSV(first column "key"):**

```csv
key,type,hp
slime,small,10
goblin,medium,20
```

**Output (keyed):**

```lua
return {
  slime = { type = "small", hp = 10 },
  goblin = { type = "medium", hp = 20 },
}
```

**Output (array):**

```lua
return {
  slime = { "small", 10 },
  goblin = { "medium", 20 },
}
```
**Example CSV(first column "not key"):**

```csv
id,type,hp
slime,small,10
goblin,medium,20
```

**Output (keyed):**

```lua
return {
  { id = "slime",type = "small", hp = 10 },
  { id = "goblin", type = "medium", hp = 20 },
}
```

**Output (array):**

```lua
return {
  {"slime", "small", 10 },
  {"goblin", "medium", 20 },
}
```

## 📄 License

CC0 1.0 Universal

## 🔗 Related Links
* [Defold Editor Scripts Documentation](https://defold.com/manuals/editor-scripts/)
