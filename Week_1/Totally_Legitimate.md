# Totally Legitimate Writeup

- When opening the file, there was nothing too special other than a document full of question marks
- Enabling the content and macro for the file also did nothing
- Knowing that word documents and any microsoft document in general is just a zip file, I renamed the file extension from `.docm` to `.zip`
- Opening the zip and inspecting the files lead me to find `vbaData.xml` and `vbaProject.bin`
- Inside `vbaData.xml` there contains information about the macro `<wne:mcd wne:macroName="PROJECT.SECURITY.AUTOOPEN" wne:name="Project.Security.AutoOpen" wne:bEncrypt="00" wne:cmg="56"/>`
- With no previous knowledge about microsoft macros, this confirms the thought that the file in question will be either `vbaData.xml` or `vbaProject.bin` and since there is nothing else in `vbaData.xml` the sus file has to be `vbaProject.bin`
- Using strings on the file gives:

![strings](https://cdn.discordapp.com/attachments/996791615576363183/1007735415991713882/unknown.png)

- opening the https://metaproblems.com/1cc3d2c915979753ac418b503a99bbdb/c2.php?u= shows: `{"success":true,"flag":"flag{did_you_end_up_running_this_while_solving_the_challenge}"}`

- At first I didn't notice the link, so I went and found this post that talks about finding macros in file: https://book.hacktricks.xyz/generic-methodologies-and-resources/basic-forensic-methodology/specific-software-file-type-tricks/office-file-analysis
- this post utilizes the python library oletools to scan for macros within Microsoft documents and retrieving its contents

![strings](https://media.discordapp.net/attachments/996791615576363183/1007733541116850196/unknown.png)
