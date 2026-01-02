# Phone Number Normalizer

A Google Tag Manager variable template for both web and server containers that normalizes phone numbers to E.164 format without plus sign. Removes non-numeric characters, leading zeros, and adds country calling code.

## Overview

This template normalizes phone numbers for hashing and transmission to advertising platforms (Facebook CAPI, Google Ads, TikTok) by converting local formats into the international E.164 standard.
For Google Ads, the “+” prefix must be added manually.

## Installation

1. In your GTM container (web or server-side), go to **Templates** → **Variable Templates** → **Search Gallery**
2. Search for "Phone Number Normalizer"
3. Click **Add to workspace**

## Configuration

| Field | Description |
|-------|-------------|
| **Phone Number** | The phone number to normalize |
| **Country Code (ISO)** | ISO country code (e.g., HR, US, DE) |

## Examples

| Phone Number | Country | Output |
|--------------|---------|--------|
| `091 234 5678` | HR | `385912345678` |
| `(555) 123-4567` | US | `15551234567` |
| `+385 91 234 5678` | HR | `385912345678` |
| `0171 1234567` | DE | `491711234567` |
| `07911 123456` | GB | `447911123456` |

## Features

- Removes all non-numeric characters (spaces, dashes, parentheses, plus sign)
- Strips leading zeros from local numbers
- Adds country calling code based on ISO country code
- Detects if country code is already present (avoids duplication)
- Supports 200+ countries and territories
- Returns `undefined` for invalid input
- Output format: digits only, no plus sign (E.164 without +). As mentioned above, for Google Ads you must add the “+” prefix manually. Field example: "+{{UDA - phone_number - formatted}}"

## Supported Countries

All countries with ISO 3166-1 alpha-2 codes are supported, including:
- Europe: HR, DE, GB, FR, IT, ES, PL, NL, etc.
- Americas: US, CA, MX, BR, AR, etc.
- Asia: CN, JP, KR, IN, ID, etc.
- And all other UN member states and territories

## Usage Example

1. Create a variable using this template
2. Set **Phone Number** to your phone data source (e.g., `{{Event Data - phone}}`)
3. Set **Country Code** to user's country (e.g., `{{Event Data - country}}` or static value)
4. Use the normalized output in your tracking tags or hash it for CAPI

## Important Notes

- The country code parameter should be the ISO 2-letter code (e.g., `HR` not `385`)
- If the phone number already includes the country calling code, it won't be duplicated
- Local numbers with leading zero (e.g., `091...` in Croatia) are handled automatically

## Compatibility

This template works in both:
- **Web GTM** containers
- **Server-side GTM** containers

## Author

**Metryx Studio**  
Website: [metryx.studio](https://metryx.studio)  
Contact: filip@metryx.studio

## License

Apache License 2.0
