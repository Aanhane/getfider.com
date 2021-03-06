<h3 id="comments">Comments</h3>

<ul>
  <li><a href="#list-comments">List Comments</a></li>
  <li><a href="#get-comment">Get a Comment</a></li>
  <li><a href="#add-comment">Add a Comment</a></li>
  <li><a href="#edit-comment">Edit a Comment</a></li>
  <li><a href="#delete-comment">Delete a Comment</a></li>
</ul>

<h4 id="list-comments">List Comments</h4>

- <strong>Authentication:</strong> Optional

```
GET /api/v1/posts/{number}/comments
```

<strong>Parameters</strong>

<table>
  <tr>
    <th width="80">Name</th>
    <th width="90">Type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td><code>number</code></td>
    <td><code>number</code></td>
    <td><strong>Required.</strong> The number of the post to get comments from.</td>
  </tr>
  <tr>
</table>

<strong>Example</strong>

```
GET <baseURL>/api/v1/posts/47/comments
```

<strong>Response</strong>

```
[
  {
    "id":67,
    "content":"Sounds good, right?",
    "createdAt":"2017-07-26T04:15:22.72261Z",
    "user":{
      "id":54,
      "name":"Michael Jackson",
      "role":"visitor"
    }
  },
  {
    "id":68,
    "content":"Definitely. Just do it!",
    "createdAt":"2017-07-26T06:49:03.951383Z",
    "user":{
      "id":23,
      "name":"Darth Vader",
      "role":"visitor"
    },
    "editedAt":"2018-09-29T17:37:59.516909Z",
    "editedBy":{
      "id":1,
      "name":"Jon Snow",
      "role":"administrator"
    }
  }
]
```

<h4 id="get-comment">Get a Comment</h4>

- <strong>Authentication:</strong> Optional

```
GET /api/v1/posts/{number}/comments/{id}
```

<strong>Parameters</strong>

<table>
  <tr>
    <th width="80">Name</th>
    <th width="90">Type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td><code>number</code></td>
    <td><code>number</code></td>
    <td><strong>Required.</strong> The number of the post to retrieve.</td>
  </tr>
  <tr>
    <td><code>id</code></td>
    <td><code>number</code></td>
    <td><strong>Required.</strong> The id of the comment to be retrieved.</td>
  </tr>
  <tr>
</table>

<strong>Example</strong>

```
GET <baseURL>/api/v1/posts/47/comments/68
```

<strong>Response</strong>

```
200 OK
---
{
  "id":68,
  "content":"Definitely. Just do it!",
  "createdAt":"2017-07-26T06:49:03.951383Z",
  "user":{
    "id":23,
    "name":"Darth Vader",
    "role":"visitor"
  },
  "editedAt":"2018-09-29T17:37:59.516909Z",
  "editedBy":{
    "id":1,
    "name":"Jon Snow",
    "role":"administrator"
  }
}
```

<h4 id="add-comment">Add a Comment</h4>

```
POST /api/v1/posts/{number}/comments
```

<strong>Parameters</strong>

<table>
  <tr>
    <th width="120">Name</th>
    <th width="90">Type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td><code>number</code></td>
    <td><code>number</code></td>
    <td><strong>Required.</strong> The number of the post to add the comment.</td>
  </tr>
  <tr>
    <td><code>content</code></td>
    <td><code>string</code></td>
    <td><strong>Required.</strong> The content of the comment.</td>
  </tr>
</table>

<strong>Example</strong>

```
POST <baseURL>/api/v1/posts/47/comments
---
{
  "content": "Agreed, we'll soon need to act on this"
}
```

<strong>Response</strong>

```
200 OK
---
{
  "id":5675
}
```

<h4 id="edit-comment">Edit a Comment</h4>

- <strong>Authentication:</strong> Required
- <strong>Required Role:</strong> Collaborator or Administrator.

```
PUT /api/v1/posts/{number}/comments/{id}
```

<strong>Parameters</strong>

<table>
  <tr>
    <th width="120">Name</th>
    <th width="90">Type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td><code>number</code></td>
    <td><code>number</code></td>
    <td><strong>Required.</strong> The number of the post that has given comment.</td>
  </tr>
  <tr>
    <td><code>id</code></td>
    <td><code>number</code></td>
    <td><strong>Required.</strong> The id of the comment to be edited.</td>
  </tr>
  <tr>
    <td><code>content</code></td>
    <td><code>string</code></td>
    <td><strong>Required.</strong> The new content of the comment.</td>
  </tr>
</table>

<strong>Example</strong>

```
POST <baseURL>/api/v1/posts/47/comments/5675
---
{
  "content": "Agreed, we need to act on this as soon as possible"
}
```

<strong>Response</strong>

```
200 OK
---
{}
```

<h4 id="delete-comment">Delete a Comment</h4>

- <strong>Authentication:</strong> Required
- <strong>Required Role:</strong> Collaborator or Administrator.

```
DELETE /api/v1/posts/{number}/comments/{id}
```

<strong>Parameters</strong>

<table>
  <tr>
    <th width="120">Name</th>
    <th width="90">Type</th>
    <th>Description</th>
  </tr>
  <tr>
    <td><code>number</code></td>
    <td><code>number</code></td>
    <td><strong>Required.</strong> The number of the post that has given comment.</td>
  </tr>
  <tr>
    <td><code>id</code></td>
    <td><code>number</code></td>
    <td><strong>Required.</strong> The id of the comment to be edited.</td>
  </tr>
</table>

<strong>Example</strong>

```
DELETE <baseURL>/api/v1/posts/47/comments/5675
```

<strong>Response</strong>

```
200 OK
---
{}
```