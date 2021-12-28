# Introduction

Welcome to the documentation of Rūrusetto API. You can get the information about all API methods here.

# Warning

This API is still in development. It may change without notice. You can check the breaking changes in the [changelog and breaking changes](api-change-and-breaking-changes.md).

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

| Name                 | Type        | Description                                                                                                                                                     |
|----------------------|-------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| id                   | integer     | The ID of the ruleset in Rūrusetto database.                                                                                                                    |
| name                 | string      | The name of the ruleset.                                                                                                                                        |
| slug                 | string      | The slug of the ruleset. Use in the URL of the ruleset's wiki page.                                                                                             |
| description          | string      | The short description of the rulesets.                                                                                                                          |
| icon                 | string      | The URL of the ruleset icon that use in website's default theme (dark theme).                                                                                   |
| light_icon           | string      | The URL of the ruleset icon that use in website's light theme.                                                                                                  |
| owner_detail         | user_detail | The [user_detail](#user_detail) of the ruleset's current owner                                                                                                  |
| verified             | boolean     | True if the wiki maintainer has verified that the the owner is the real owner of this ruleset.                                                                  |
| direct_download_link | string      | URL for download the latest release of ruleset from GitHub                                                                                                      |
| can_download         | boolean     | True if website can render the direct download link from the `source` and `github_download_filename` so user can download directly from `direct_download_link`. |
| status               | status      | The [status](#status) of the ruleset.                                                                                                                           |

### Example response (200)

```json
[
    {
        "id": 1,
        "name": "sentakki",
        "slug": "sentakki",
        "description": "TAP, HOLD and SLIDE to the beat",
        "icon": "/media/rulesets_icon/lol_icon.png",
        "light_icon": "/media/rulesets_icon_light/lol_icon.png",
        "owner_detail": {
            "id": 4,
            "user": {
                "username": "Bloom",
                "email": ""
            },
            "image": "/media/profile_pics/Very_not_so_pink_avatar_trnsprncy.png"
        },
        "verified": true,
        "direct_download_link": "https://github.com/LumpBloom7/sentakki/releases/latest/download/osu.Game.Rulesets.Sentakki.dll",
        "can_download": true,
        "status": {
            "latest_version": "2021.1127.0",
            "latest_update": "2021-11-27T10:41:54Z",
            "pre_release": false,
            "changelog": "Thank you for showing interest in this ruleset. This is a tagged release (2021.1127.0).\r\nIf you like this ruleset, do consider [supporting me](https://lumpbloom7.github.io/sponsor).\r\n\r\n**This release resolves a minor SR incompatibility that could occur on the `2021.1127.0` release of osu!lazer**\r\n\r\n## What's Changed\r\n* Bump ppy.osu.Game from 2021.1120.0 to 2021.1127.0 by @dependabot in https://github.com/LumpBloom7/sentakki/pull/286\r\n\r\n\r\n**Full Changelog**: https://github.com/LumpBloom7/sentakki/compare/2021.1120.0...2021.1127.0\r\n\r\n## Feedback\r\nComplaints? Suggestion? Or just want to discuss stuff?\r\n\r\nFeel free to join the [sentakki discord](https://discord.gg/CQPNADu) for a direct communication line to devs, and exclusive access to insider test builds.\r\n\r\n## Installation\r\n[Refer to this wiki page](https://github.com/LumpBloom7/sentakki/wiki/Ruleset-installation-guide)",
            "file_size": 927744,
            "playable": "yes"
        }
    }, {...}, {...}
]
```

## Details

Get the full details of a request ruleset.

    GET https://rulesets.info/api/rulesets/{slug}

### Response format

| Name                     | Type        | Description                                                                                                                                                     |
|--------------------------|-------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------|
| id                       | integer     | The ID of the ruleset in Rūrusetto database.                                                                                                                    |
| name                     | string      | The name of the ruleset.                                                                                                                                        |
| slug                     | string      | The slug of the ruleset. Use in the URL of the ruleset's wiki page.                                                                                             |
| description              | string      | The short description of the rulesets.                                                                                                                          |
| icon                     | string      | The URL of the ruleset icon that use in website's default theme (dark theme).                                                                                   |
| light_icon               | string      | The URL of the ruleset icon that use in website's light theme.                                                                                                  |
| logo                     | string      | The URL of the ruleset logo that use in the infobox.                                                                                                            |
| cover_image              | string      | The URL of the cover image in ruleset's wiki page in website's default theme (dark theme).                                                                      |
| cover_image_light        | string      | The URL of the cover image in ruleset's wiki page in website's light theme.                                                                                     |
| opengraph_image          | string      | The URL of the image that use in the opengraph part of the wiki URL.                                                                                            |
| custom_css               | string      | The URL of the CSS file that's override the website's default styling.                                                                                          |
| content                  | string      | Wiki main content in markdown format.                                                                                                                           |
| source                   | string      | The URL source of the rulesets.                                                                                                                                 |
| github_download_filename | string      | Filename that use in rendering the direct download link with the source link.                                                                                   |
| direct_download_link     | string      | URL for download the latest release of ruleset from GitHub                                                                                                      |
| can_download             | boolean     | True if website can render the direct download link from the `source` and `github_download_filename` so user can download directly from `direct_download_link`. |
| creator_detail           | user_detail | The [user_detail](#user_detail) of the user who create this wiki page, not the owner.                                                                           |
| created_at               | string      | The UTC time that the wiki page has create in JSON time format.                                                                                                 |
| owner_detail             | user_detail | The [user_detail](#user_detail) of the ruleset's current owner                                                                                                  |
| last_edited_at           | string      | The UTC time of the latest wiki edit.                                                                                                                           |
| last_edited_by_detail    | user_detail | The [user_detail](#user_detail) of the user who edit the wiki page last time.                                                                                   |
| verified                 | boolean     | True if the wiki maintainer has verified that the the owner is the real owner of this ruleset.                                                                  |
| archive                  | boolean     | True if this ruleset is stop update or archived by rulesets creator.                                                                                            |


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
  "direct_download_link": "https://github.com/LumpBloom7/sentakki/releases/latest/download/osu.Game.Rulesets.Sentakki.dll",
  "can_download": true,
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

Represents a user's detail that's mainly use in listing and wiki. Will return `{}` if the user is not found or mark as unknown in database.

### Response format

| Name       | Type    | Description                               |
|------------|---------|-------------------------------------------|
| id         | integer | The ID of the user in Rūrusetto database. |
| user       |         |                                           |
| - username | string  | Username of request user.                 |
| - email    | string  | Email of request user. (Can be blank)     |
| image      | string  | The URL of the user's profile image.      |

## status

Use in some element that required to show the status of the ruleset.

### Response format

| Name           | Type    | Description                                                                    |
|----------------|---------|--------------------------------------------------------------------------------|
| latest_version | string  | The latest version name of the ruleset.                                        |
| latest_update  | string  | The time on ruleset's latest update in JSON time format.                       |
| pre_realase    | boolean | True if the ruleset is marked as pre-release in GitHub Release.                |
| change_log     | string  | The latest changelog of the ruleset in markdown format.                        |
| file_size      | int     | The size of the latest release file in bytes.                                  |
| playable       | string  | The status about the playable of the ruleset. Has 3 choices (yes, no, unknown) |

# Website resource

We also provide the API about the resource that use in the website. You can find it in [Website resource](website-resource.md).

----------------------------------------------------------------------------------------------------

Thanks for Netlify to sponsors us the open source plan!

<a href="https://www.netlify.com">
  <img src="https://www.netlify.com/img/global/badges/netlify-color-accent.svg" alt="Deploys by Netlify" />
</a>