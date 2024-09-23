- 👋 Hi, Aldrin giving free tutorials.
- 👀 I’m interested in new concepts.
- 🌱 I’m currently learning in Micronaut.
- 💞️ I’m looking to collaborate on Micronaut Rest API.
- 📫 You can chat me.

![](https://komarev.com/ghpvc/?username=renboy1222&color=green)
<!---
renboy1222/renboy1222 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->

git log --format='%aN' | Sort-Object -Unique | ForEach-Object {
    $name = $_
    $addedLines = 0
    $removedLines = 0
    (git log --author="$name" --pretty=tformat: --numstat) | ForEach-Object {
        if ($_ -match '(\d+)\s+(\d+)') {
            $addedLines += [int]$matches[1]
            $removedLines += [int]$matches[2]
        }
    }
    [PSCustomObject]@{
        Author = $name
        AddedLines = $addedLines
        RemovedLines = $removedLines
        TotalLines = $addedLines - $removedLines
    }
} | Format-Table -AutoSize
