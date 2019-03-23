# Jetpack Document

## Table of contents
   * [Jetpack Document](#jetpack-document)
      * [Table of contents](#table-of-contents)
      * [Functions](#functions)
         * [httpGet(url, headers)](#httpgeturl-headers)
         * [httpPost(url, body, headers)](#httpposturl-body-headers)
         * [httpUpload(url, filePath, headers)](#httpuploadurl-filepath-headers)
         * [httpDownload(url, filePath, headers)](#httpdownloadurl-filepath-headers)

## Functions

### httpGet(url, headers)
    Make http GET request

`Parameters`

| Parameter     | Type   |  Specification  | Optional |
| -------- | :-----:| :----: | -------- | 
| url    | String   |   Aim url. | NO |
| headers     |   table   |   Additional headers.    | YES |

`Return`

| Return     | Type   |  Specification  |
| -------- | :-----:| ----  |
| success     |   Boolean   |   If request was successful.  |
| result or error     |   String   |   If request was successful, this return value is the result you want, otherwise it's error message.  |

`Examples`
```lua
local headers = { "Accept" = "application/json" }
local url = "https://samples.openweathermap.org/data/2.5/weather?id=2172797&appid=b6907d289e10d714a6e88b30761fae22";

--  with headers
local success, data = httpGet(url, headers)
if success then
    alert(data) -- data is the result you want.
else
    alert(data) -- data is the error message.
end

-- Without headers
local success, data = httpGet(url)
```

---

### httpPost(url, body, headers)
    Make http POST request

`Parameters`

| Parameter     | Type   |  Specification  | Optional |
| -------- | :-----:| :----: | -------- | 
| url    | String   |   Aim url. | NO |
| body     |   String   |   Post body.    | YES |
| headers     |   table   |   Additional headers.    | YES |


`Return`

| Return     | Type   |  Specification  |
| -------- | :-----:| ----  |
| success     |   Boolean   |   If request was successful.  |
| result or error     |   String   |   If request was successful, this return value is the result you want, otherwise it's error message.  |


`Examples`

```lua
local headers = { "Accept" = "application/json" }
local url = "https://samples.openweathermap.org/data/2.5/weather?id=2172797&appid=b6907d289e10d714a6e88b30761fae22";
local body = "aaa=bbb&ccc=ddd"

--  with headers
local success, data = httpPost(url, body, headers)
if success then
    alert(data) -- data is the result you want.
else
    alert(data) -- data is the error message.
end

-- Without headers
local success, data = httpGet(url)
```

---

### httpUpload(url, filePath, headers)
    Make http upload request

`Parameters`

| Parameter     | Type   |  Specification  | Optional |
| -------- | :-----:| :----: | -------- | 
| url    | String   |   Aim url. | NO |
| filePath    | String   |   File path, relative path. | NO |
| headers     |   table   |   Additional headers.    | YES |


`Return`

| Return     | Type   |  Specification  |
| -------- | :-----:| ----  |
| success     |   Boolean   |   If request was successful.  |
| result or error     |   String   |   If request was successful, this return value is the result you want, otherwise it's error message.  |


`Examples`

```lua
local headers = { "Accept" = "application/json" }
local url = "https://samples.openweathermap.org/data/2.5/weather?id=2172797&appid=b6907d289e10d714a6e88b30761fae22";
local filePath = "/myscripts/aaa.lua"

--  with headers
local success, data = httpUpload(url, filePath, headers)
if success then
    alert(data) -- data is the result you want.
else
    alert(data) -- data is the error message.
end

-- Without headers
local success, data = httpUpload(url, filePath)
```

---

### httpDownload(url, filePath, headers)
    Make http download request

`Parameters`

| Parameter     | Type   |  Specification  | Optional |
| -------- | :-----:| :----: | -------- | 
| url    | String   |   Aim url. | NO |
| filePath    | String   |   Where you want the downloaded file be put at, relative path. | YES |
| headers     |   table   |   Additional headers.    | YES |


`Return`

| Return     | Type   |  Specification  |
| -------- | :-----:| ----  |
| success     |   Boolean   |   If request was successful.  |
| finalFilePath or error     |   String   |   If request was successful, this return value is the downloaded file final path, otherwise it's error message. If you provide filePath parameter while calling this function, it will automatically move the file to filePath, if not provide, it will return the temp file path.  |


`Examples`

```lua
local headers = { "Accept" = "application/json" }
local url = "https://samples.openweathermap.org/data/2.5/weather?id=2172797&appid=b6907d289e10d714a6e88b30761fae22";
local filePath = "/myscripts/aaa.lua"

--  with headers
local success, data = httpDownload(url, filePath, headers)
if success then
    alert(data) -- data is the downloaded file final path.
else
    alert(data) -- data is the error message.
end

-- Without headers
local success, data = httpDownload(url, filePath)

-- Without filePath, headers
local success, data = httpDownload(url)
    alert(data) -- data is the temp downloaded file final path.
else
    alert(data) -- data is the error message.
end

```