**Linux/macOS Shell**

`btfs config --json API.HTTPHeaders.Access-Control-Allow-Origin '["*"]'`

`btfs config --json API.HTTPHeaders.Access-Control-Allow-Methods '["PUT","GET","POST"]'`

**Windows Batch**

`btfs config --json API.HTTPHeaders.Access-Control-Allow-Origin "["""*"""]"`

`btfs config --json API.HTTPHeaders.Access-Control-Allow-Methods "["""PUT""", """GET""", """POST"""]"`

**Windows PowerShell**

`btfs config --json API.HTTPHeaders.Access-Control-Allow-Origin '[\"*\"]'`

`btfs config --json API.HTTPHeaders.Access-Control-Allow-Methods '[\"PUT\", \"GET\", \"POST\"]'`

**Modify .btfs/config directly**
> 
```
"API": {
  "HTTPHeaders": {
    "Access-Control-Allow-Methods": [
      "PUT",
      "GET",
      "POST"
    ],
    "Access-Control-Allow-Origin": [
      "*"
    ]
  }
}
```