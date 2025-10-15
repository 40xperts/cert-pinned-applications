# Applications with Certificate Pinning

This document lists applications that are known to implement certificate pinning in their security architecture. Certificate pinning helps prevent man-in-the-middle attacks by ensuring the application only trusts specific certificates or public keys.

## Banking & Finance

- **Bank of America Mobile Banking** - iOS and Android
- **Chase Mobile** - iOS and Android
- **Wells Fargo Mobile** - iOS and Android
- **PayPal** - iOS and Android
- **Venmo** - iOS and Android
- **Cash App** - iOS and Android
- **Revolut** - iOS and Android
- **Monzo** - iOS and Android
- **Coinbase** - iOS and Android
- **Binance** - iOS and Android

## Social Media & Communication

- **Twitter/X** - iOS and Android
- **Facebook** - iOS and Android
- **Instagram** - iOS and Android
- **WhatsApp** - iOS and Android
- **Signal** - iOS and Android
- **Telegram** - iOS and Android
- **Snapchat** - iOS and Android
- **LinkedIn** - iOS and Android
- **Discord** - iOS and Android
- **Slack** - iOS and Android

## Streaming & Entertainment

- **Netflix** - iOS and Android
- **Spotify** - iOS and Android
- **Disney+** - iOS and Android
- **HBO Max** - iOS and Android
- **YouTube** - iOS and Android
- **Twitch** - iOS and Android
- **Hulu** - iOS and Android

## E-Commerce & Shopping

- **Amazon** - iOS and Android
- **eBay** - iOS and Android
- **Walmart** - iOS and Android
- **Target** - iOS and Android
- **Shopify** - iOS and Android
- **Alibaba** - iOS and Android

## Security & Authentication

- **Google Authenticator** - iOS and Android
- **Microsoft Authenticator** - iOS and Android
- **Authy** - iOS and Android
- **1Password** - iOS and Android
- **LastPass** - iOS and Android
- **Duo Mobile** - iOS and Android

## Transportation & Travel

- **Uber** - iOS and Android
- **Lyft** - iOS and Android
- **Airbnb** - iOS and Android
- **Booking.com** - iOS and Android
- **Delta Airlines** - iOS and Android
- **American Airlines** - iOS and Android

## Health & Fitness

- **MyFitnessPal** - iOS and Android
- **Strava** - iOS and Android
- **Headspace** - iOS and Android
- **Calm** - iOS and Android

## Government & Official Apps

- **IRS2Go** - iOS and Android
- **NHS App** - iOS and Android
- **Gov.uk** - iOS and Android

## Cloud Storage & Productivity

- **Dropbox** - iOS and Android
- **Google Drive** - iOS and Android
- **Microsoft OneDrive** - iOS and Android
- **Box** - iOS and Android

## Notes

- Certificate pinning implementations may vary by version and platform
- Some applications may implement pinning only for specific API endpoints
- Pinning can be implemented at the certificate level or public key level
- This list is not exhaustive and may require updates as applications change their security practices

## Testing Certificate Pinning

Certificate pinning can be identified and tested using tools such as:

- **Frida** - Dynamic instrumentation toolkit
- **objection** - Runtime mobile exploration toolkit
- **SSL Kill Switch 2** - iOS jailbreak tweak for bypassing certificate pinning
- **TrustMeAlready** - Android Xposed module
- **Charles Proxy** - HTTP proxy for testing network traffic
- **Burp Suite** - Web application security testing tool
- **mitmproxy** - Interactive HTTPS proxy

## Contributing

If you know of other applications that implement certificate pinning, please contribute to this list by submitting a pull request.
