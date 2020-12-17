# THIS IS FOR EDUCATION PURPOSE ONLY.

<br>

# Steps

If you have a better way to accomplish the same task with more ease, please create an issue or send a PR on this file and add your steps/instructions below.

<br>

## Command-line

Recommended to use [Cmder](https://cmder.net/) or [Windows terminal with WSL](https://docs.microsoft.com/en-us/windows/terminal/get-started) if you are on Windows.

<br>

## Copying site

Tools that helped in the process: [Wget](https://www.gnu.org/software/wget/)

Run on command-line:

```

wget --mirror --page-requisites --adjust-extension --convert-links -e robots=off https://example.com

```
or

```
wget -m -p -E -k -e robot=off https://example.com

```

<br>

![](https://i.imgur.com/hiJ2RXQ.png)

<br>

## Filtering Assets (PNG, JPG, SVG, GIF, WEBP)

Tools that helped in the process: [Everything](https://www.voidtools.com/)

- Go to the path where you copied the website earlier using Wget and filter by .png, .jpg, ... 

- Select all, right-click and click on `Copy Full Name to Clipboard` - This will copy the absolute path of files.

<br>

![](https://i.imgur.com/HJ2kark.png)

<br>

## VSCode arranging content

Tools that helped in the process: [Visual Studio Code](https://code.visualstudio.com/)

- Create a new file with any extension like `.md` and paste the earlier copied content from Everything and name it as `path.md` for example.

<br>

![](https://i.imgur.com/NmxrJEO.png)

<br>

- Replace the path till `../developer.android.com` with `https://developer.android.com/`

<br>

![](https://i.imgur.com/VGp9fDx.png)

<br>

- Replace `\` with `/`

- Create a new file called `title.md`, `image.md` in the same directory as `path.md`

- Copy contents of `path.md` in `title.md`

- Click on regex mode in VSCode and enter `.*/` in the field and replace all - This will remove all the content from the string until the last `/`

<br>

![](https://i.imgur.com/L17npSJ.png)

<br>

- Enter `.png` and replace it with an empty string to get the title.

<br>

![](https://i.imgur.com/UAyo9ub.png)

<br>

- Enter regex `^` and replace with `#### ` to get a nice heading.

<br>

![](https://i.imgur.com/jnOkDlj.png)

<br>

- Go to command-line and Merge `title.md` and `path.md` with `paste -d "^" title.md path.md > tp.md`

<br>

![](https://i.imgur.com/lC20aA4.png)

<br>

- Perform regex: `$(?<!\.png)(?<!\.gif)(?<!\.svg)(?<!\.jpg)(?<!\.webp)(\n)` on `tp.md` and replace with empty string - This will select all lines that do not end with .png, .gif, .svg, .jpg, .webp and remove their line breaks.

<br>

![](https://i.imgur.com/6qDn9ir.png)

<br>

- Copy contents in `path.md` and paste in `image.md`

- Replace `https:` with `![](https:` and Replace `.png` with `.png)` - This will make the image render in markdown.

<br>

![](https://i.imgur.com/eLyIHNT.png)

![](https://i.imgur.com/6jo2NbY.png)

<br>

- Go to command-line and Merge `tp.md` and `image.md` with `paste -d \n tp.md image.md > tpi.md`

<br>

![](blob:https://imgur.com/49c05947-9807-49f8-aee3-74aa4873cd1a)

<br>

- In `tpi.md` perform Regex `\^` to replace ^ with Ctrl+Enter (line break)

<br>

![](https://i.imgur.com/mu8DBj2.png)

<br>

- Perform regex `^https:` to replace `https:` with `Source: https:` - This will only replace the `https:` at the beginning of the line.

<br>

![](https://i.imgur.com/GbIbND3.png)

<br>

- Replace `####` with `<br> {Ctrl+Enter} ####` - Press {Ctrl + Enter} to give line break.

<br>

![](blob:https://imgur.com/fa96f2f4-b8fa-4c8d-830a-5751cf943d0c)

<br>

- Done. This will produce the same output as in the repository.

<br>

![](https://i.imgur.com/7ZgDRd4.png)