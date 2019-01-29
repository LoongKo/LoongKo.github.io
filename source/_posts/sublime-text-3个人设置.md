---
title: sublime text 3个人设置
date: 2018-11-13 15:57:26
categories: 其他
tags: sublime text
---
# Preferences.sublime-settings
```json
{
  "color_scheme": "Packages/Color Scheme - Default/Monokai.sublime-color-scheme",
  "font_face": "Consolas",
  "font_options":
  [
    "gdi"
  ],
  "font_size": 21,
  "show_definitions": false,
  "tab_size": 2,
  "theme": "Adaptive.sublime-theme",
  "translate_tabs_to_spaces": true,
  "highlight_modified_tabs": true,
}

```

# PHP.sublime-build
```json
{
  "cmd": ["php", "$file"], 
  "file_regex": "php$",
  "selector": "source.php"
}
```

# Node.sublime-build
```json
{
  "cmd": ["node", "$file"],
  "selector": "source.js",
}
```