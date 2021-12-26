# Introduction

Welcome to the documentation of Rūrusetto API. You can get the information about all API methods here.

# Warning

This API is still in development. It may change without notice. You can check the breaking changes in the [breaking changes](api-breaking-changes.md).

# Terms of Use

This API is not required key. You can use it without any restrictions. Just don't abuse it.

Current limit rate is set at an insane rate of 1200 requests per minutes. If you use more than that, you should DDOS the server.

# Endpoints

## Base URL

The base URL of the API is `https://rulesets.info/api/`.

## Files

All file that's available in the API must start with `https://rulesets.info/media/`.

# Rulesets

## Listing

Get all details of all rulesets that's use in rendering the [listing](https://rulesets.info/listing) page.

    GET https://rulesets.info/api/rulesets

### Response format

| Name         | Type        | Description                                                                   |
|--------------|-------------|-------------------------------------------------------------------------------|
| id           | integer     | The ID of the ruleset in Rūrusetto database.                                  |
| name         | string      | The name of the ruleset.                                                      |
| slug         | string      | The slug of the ruleset. Use in the URL of the ruleset's wiki page.           |
| description  | string      | The short description of the rulesets.                                        |
| icon         | string      | The URL of the ruleset icon that use in website's default theme (dark theme). |
| light_icon   | string      | The URL of the ruleset icon that use in website's light theme.                |
| owner_detail | user_detail | The `user_detail` of the ruleset's current owner                              |

### Example response (200)

```json
[
    {
        "id": 3,
        "name": "Sentakki",
        "slug": "sentakki",
        "description": "A custom ruleset based on Sega's arcade rhythm game maimai",
        "icon": "/media/default_icon.png",
        "light_icon": "/media/default_icon.png",
        "owner_detail": {
            "id": 3,
            "user": {
                "username": "Bloom",
                "email": "bloom@727mail.com"
            },
            "image": "/media/default.jpeg"
        }
    }, {...}, {...}
]
```
# Users