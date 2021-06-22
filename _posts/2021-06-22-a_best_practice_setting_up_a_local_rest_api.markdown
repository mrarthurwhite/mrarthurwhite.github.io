---
layout: post
title:      "A Best Practice : Setting up a local REST API"
date:       2021-06-22 22:48:54 +0000
permalink:  a_best_practice_setting_up_a_local_rest_api
---


When testing out ideas for the front end I often have to copy over the entire backend in ROR (which is convenient) but rather memory intensive.

So I came across this "workaround" that allows for the creation of a local rest API.

So the steps are so : 

1. install the json-server

`npm install -g json-server`

This is important as a step & you should ensure that `json-server -v `  (in my case it returns 0.16.3) returns some output to ensure that json-server is actually installed. I followed some online examples and they did not do a good job of explaining that & for those reasons I could not even get json-server started.

2. create your seed data

Firstly create your db file, calling it `db.json` and you can enter text using any text editor, some people recommend nano or pico so 
`pico db.json`. Once you have the editor up enter the following data in the following format

```
{API_URL_KEYWORD
:
[
ARRAY_OF_DATA_FIELDS_&_VALUES
]
}
```

The `API_URL_KEYWORD` is what you use when you are accessing your API : `http://localhost:PORTNUMBER/API_URL_KEYWORD`

As for `ARRAY_OF_DATA_FIELDS_&_VALUES` they are formatted so:
```
{
FIELD_1
:
FIELD_1_VALUE
,
FIELD_2
:
FIELD_2_VALUE
,
.
.
.
FIELD_N
:
FIELD_N_VALUE
,
}
```

So an example of the above is so:

```
{
"wordlist"
:
[
{
"id"
:
1
,
"word"
:
"Avalon"
,
"definition"
:
"Bucolic paradisical place."
}
,
{
"id"
:
2
,
"word"
:
"Arthur"
,
"definition"
:
"Monarch."
}
]
}
```
Following is how seed data works in my file `db.json`  : you have to put a carriage return or end of line after every field or field value or delimiter.

Once you are done with this you can run your local API so:

`json-server DB_FILE -p PORTNUMBER`

In our case specifically it is:
`json-server db.json -p 1111`

So the screenshot of a running json-server looks so:
![running json server](https://github.com/mrarthurwhite/local_rest_api_demo/blob/master/imgs/screenshot1.jpg)

And the screenshot of a running api looks so : 
![running api](https://github.com/mrarthurwhite/local_rest_api_demo/blob/master/imgs/screenshot2.jpg)

And the entire src along with some references is here:
[src](https://github.com/mrarthurwhite/local_rest_api_demo/)
