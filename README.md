# Certificate Pinned Applications

A curated list of mobile and desktop applications that implement certificate pinning as part of their security measures.

## About Certificate Pinning

Certificate pinning is a security technique used by applications to prevent man-in-the-middle (MITM) attacks. When an application implements certificate pinning, it only trusts specific certificates or public keys rather than relying solely on the device's trust store. This makes it more difficult for attackers to intercept network traffic, even if they have installed a trusted root certificate on the device.

## The List

See [applications.md](applications.md) for a comprehensive list of applications known to implement certificate pinning.

## Purpose

This repository serves multiple purposes:

- **Security Research**: Help security researchers and penetration testers identify applications that use certificate pinning
- **Developer Reference**: Provide developers with examples of applications that implement this security measure
- **Testing Guidance**: Assist in testing scenarios where certificate pinning bypass may be necessary for legitimate purposes (e.g., corporate security audits, personal app testing)

## Use Cases

- Mobile application security testing
- Network traffic analysis for debugging
- Security auditing and penetration testing
- Understanding which applications require certificate pinning bypass tools

## Contributing

Contributions are welcome! If you know of applications that implement certificate pinning and are not on the list, please submit a pull request.

When contributing:
1. Verify the application actually implements certificate pinning
2. Include the platform(s) where pinning is implemented (iOS, Android, etc.)
3. Keep the list organized by category
4. Include any relevant notes about the implementation

## Disclaimer

This list is provided for educational and security research purposes only. Certificate pinning bypass should only be performed on applications you own or have explicit permission to test. Always comply with applicable laws and terms of service.

## License

This repository is provided as-is for informational purposes.