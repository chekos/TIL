---
title: "you can't use special characters in unix commands if you use single-quotes"
categories: ["unix"]
---

## what i learned
You can't insert variables in Unix commands if you're using single quotes.

this won't work
```shell
export SECRET="huh"

echo 'you can not see my secret $secret'
```

but this will
```shell
export SECRET="huh"

echo "you can see my secret $SECRET"
```

## how i learned
while setting up a GitHub action for the social tech collaborative website that would send a url to a specific slack channel, i would get `$TARGET_URL` instead of the actual url. 

turns out special characters are interpreted as literals with single-quotes. 

when you use double-quotes, special characters `$`, `\` and `\\` remain special 🙄

> Single quotes (' ') operate similarly to double quotes, but do not permit referencing variables, since the special meaning of $ is turned off. Within single quotes, every special character except ' gets interpreted literally. Consider single quotes ("full quoting") to be a stricter method of quoting than double quotes ("partial quoting"). <br> - https://www.tldp.org/LDP/abs/html/quotingvar.html
