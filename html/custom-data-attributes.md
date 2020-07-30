# Custom data attributes

Name is transformed:

- prefix `data-` is removed
- for any dash + lowercase letter a to z: dash is removed + letter is uppercased
- other characters (including other dashes) are left unchanged.

```html
<div id="user" data-id="1234567890" data-user-2="johndoe" data-date-of-birth>
  John Doe
</div>
```

`element.dataset` will be the following DOMStringMap:

    {
    "id": "1234567890",
    "user-2": "johndoe",
    "dateOfBirth": ""
    }

```javascript
element.dataset['user-2] = 'janedoe';
```
