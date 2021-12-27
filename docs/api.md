# Introduction

Welcome to the documentation of Rūrusetto API. You can get the information about all API methods here.

# Warning

This API is still in development. It may change without notice. You can check the breaking changes in the [breaking changes](api-breaking-changes.md).

# Terms of Use

This API is not required key. You can use it without any restrictions. Just don't abuse it.

Current limit rate is set at an insane rate of 1200 requests per minutes. If you use more than that, you should be idiot.

# Endpoints

## Base URL

The base URL of the API is `https://rulesets.info/api/`.

## Files

All file that's available in the API must start with `https://rulesets.info/media/`.

# Timezones

All dates and times are in UTC.

# Rulesets

## Listing

Get the list of all rulesets that's use in rendering the [listing](https://rulesets.info/listing) page.

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
| owner_detail | user_detail | The [user_detail](#user_detail) of the ruleset's current owner                |

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

## Details

Get the full details of a request ruleset.

    GET https://rulesets.info/api/rulesets/{slug}

### Response format

| Name                     | Type        | Description                                                                                    |
|--------------------------|-------------|------------------------------------------------------------------------------------------------|
| id                       | integer     | The ID of the ruleset in Rūrusetto database.                                                   |
| name                     | string      | The name of the ruleset.                                                                       |
| slug                     | string      | The slug of the ruleset. Use in the URL of the ruleset's wiki page.                            |
| description              | string      | The short description of the rulesets.                                                         |
| icon                     | string      | The URL of the ruleset icon that use in website's default theme (dark theme).                  |
| light_icon               | string      | The URL of the ruleset icon that use in website's light theme.                                 |
| logo                     | string      | The URL of the ruleset logo that use in the infobox.                                           |
| cover_image              | string      | The URL of the cover image in ruleset's wiki page in website's default theme (dark theme).     |
| cover_image_light        | string      | The URL of the cover image in ruleset's wiki page in website's light theme.                    |
| opengraph_image          | string      | The URL of the image that use in the opengraph part of the wiki URL.                           |
| custom_css               | string      | The URL of the CSS file that's override the website's default styling.                         |
| content                  | string      | Wiki main content in markdown format.                                                          |
| source                   | string      | The URL source of the rulesets.                                                                |
| github_download_filename | string      | Filename that use in rendering the direct download link with the source link.                  |
| creator_detail           | user_detail | The [user_detail](#user_detail) of the user who create this wiki page, not the owner.          |
| created_at               | string      | The UTC time that the wiki page has create in JSON time format.                                |
| owner_detail             | user_detail | The [user_detail](#user_detail) of the ruleset's current owner                                 |
| last_edited_at           | string      | The UTC time of the latest wiki edit.                                                          |
| last_edited_by_detail    | user_detail | The [user_detail](#user_detail) of the user who edit the wiki page last time.                  |
| verified                 | boolean     | True if the wiki maintainer has verified that the the owner is the real owner of this ruleset. |
| archive                  | boolean     | True if this ruleset is stop update or archived by rulesets creator.                           |


### Example response (200)

```json
{
  "id": 1,
  "name": "sentakki",
  "slug": "sentakki",
  "description": "TAP, HOLD and SLIDE to the beat",
  "icon": "/media/rulesets_icon/lol_icon.png",
  "light_icon": "/media/rulesets_icon_light/lol_icon.png",
  "logo": "/media/rulesets_logo/LOL_logo.png",
  "cover_image": "/media/wiki_cover/osu_2021-10-10_16-01-40.png",
  "cover_image_light": "/media/wiki_cover_light/osu_2021-10-10_16-01-40.png",
  "opengraph_image": "/media/rulesets_opengraph_image/LOL_logo.png",
  "custom_css": "/media/default.css",
  "content": "![Logo](https://rulesets.info/media/rulesets_logo/LOL_logo.png)\r\n\r\nWelcome to the sentakki wiki!\r\n\r\nThank you for showing interest in sentakki.\r\n\r\nSentakki is a custom osu!lazer ruleset based on Sega's maimai. \r\n\r\nRefer to the subpages for instructions to install the ruleset and learn about the various note types.",
  "source": "https://github.com/LumpBloom7/sentakki",
  "github_download_filename": "osu.Game.Rulesets.Sentakki.dll",
  "creator_detail": {
    "id": 4,
    "user": {
      "username": "Bloom",
      "email": ""
    },
    "image": "/media/profile_pics/Very_not_so_pink_avatar_trnsprncy.png"
  },
  "created_at": "2021-10-10T14:05:32.013895Z",
  "owner_detail": {
    "id": 4,
    "user": {
      "username": "Bloom",
      "email": ""
    },
    "image": "/media/profile_pics/Very_not_so_pink_avatar_trnsprncy.png"
  },
  "last_edited_at": "2021-10-12T21:34:18.429132Z",
  "last_edited_by_detail": {
    "id": 4,
    "user": {
      "username": "Bloom",
      "email": ""
    },
    "image": "/media/profile_pics/Very_not_so_pink_avatar_trnsprncy.png"
  },
  "verified": true,
  "archive": false
}
```

### Example response (404)

```json
{
  "detail": "The ruleset is not found"
}
```

# Object Structure

## user_detail

Represents a user's detail that's mainly use in listing and wiki.

### Response format

| Name       | Type    | Description                               |
|------------|---------|-------------------------------------------|
| id         | integer | The ID of the user in Rūrusetto database. |
| user       |         |                                           |
| - username | string  | Username of request user.                 |
| - email    | string  | Email of request user. (Can be blank)     |
| image      | string  | The URL of the user's profile image.      |


# Website resource

We also provide the API about the resource that use in the website. You can follow the table below to get the resource via API.

Note : The endpoint is different from the other files. The endpoint is `https://rulesets.info/static/`

## Logo

| Link                                 | Preview                                                                                         | Description                                                                            |
|--------------------------------------|-------------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------|
| `/logo/rurusetto-logo-black.svg`     | ![rurusetto-logo-black.svg](https://rulesets.info/static/logo/rurusetto-logo-black.svg)         | Rūrusetto logo in black                                                                |
| `/logo/rurusetto-logo-white.svg`     | ![rurusetto-logo-white.svg](https://rulesets.info/static/logo/rurusetto-logo-white.svg)         | Rūrusetto logo in white                                                                |
| `/logo/rurusetto-logo-with-name.svg` | ![rurusetto-logo-with-name.svg](https://rulesets.info/static/logo/rurusetto-logo-with-name.svg) | Rūrusetto logo with name                                                               |
| `/logo/rurusetto-logo.svg`           | ![rurusetto-logo.svg](https://rulesets.info/static/logo/rurusetto-logo.svg)                     | Normal Rūrusetto logo with gradient pink color that's the signature color of Rūrusetto |

## Image resource

| Link                              | Preview                                                                                    | Description                                                          |
|-----------------------------------|--------------------------------------------------------------------------------------------|----------------------------------------------------------------------|
| `/img/home-cover-night.png`       | ![home-cover-night.png](https://rulesets.info/static/img/home-cover-night.png)             | The cover image of the homepage in default theme (Dark theme).       |
| `/img/home-cover-light.jpeg`      | ![home-cover-light.jpeg](https://rulesets.info/static/img/home-cover-light.jpeg)           | The cover image of the homepage in light theme.                      |
| `/img/listing-cover-night.png`    | ![listing-cover-night.png](https://rulesets.info/static/img/listing-cover-night.png)       | The cover image of the listing page in default theme (Dark theme).   |
| `/img/listing-cover-light.png`    | ![listing-cover-light.png](https://rulesets.info/static/img/listing-cover-light.png)       | The cover image of the listing page in light theme.                  |
| `/img/status-cover-night.jpg`     | ![status-cover-night.jpg](https://rulesets.info/static/img/status-cover-night.jpg)         | The cover image of the status page in default theme (Dark theme).    |
| `/img/status-cover-light.png`     | ![status-cover-light.png](https://rulesets.info/static/img/status-cover-light.png)         | The cover image of the status page in light theme.                   |
| `/img/install-cover-night.png`    | ![install-cover-night.png](https://rulesets.info/static/img/install-cover-night.png)       | The cover image of the install page in default theme (Dark theme).   |
| `/img/install-cover-light.png`    | ![install-cover-light.png](https://rulesets.info/static/img/install-cover-light.png)       | The cover image of the install page in light theme.                  |
| `/img/changelog-cover-night2.png` | ![changelog-cover-night2.png](https://rulesets.info/static/img/changelog-cover-night2.png) | The cover image of the changelog page in default theme (Dark theme). |
| `/img/changelog-cover-light3.png` | ![changelog-cover-light3.png](https://rulesets.info/static/img/changelog-cover-light3.png) | The cover image of the changelog page in light theme.                |



----------------------------------------------------------------------------------------------------

Thanks for Netlify to sponsors us the open source plan!

<a href="https://www.netlify.com">
  <img src="https://www.netlify.com/img/global/badges/netlify-color-accent.svg" alt="Deploys by Netlify" />
</a>