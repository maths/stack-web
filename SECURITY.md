# Security Policy

## Reporting a Vulnerability

The STACK team takes security issues seriously. We appreciate your efforts to responsibly disclose your findings.

### How to Report a Security Vulnerability

If you discover a security vulnerability within the STACK website repository, please report it by emailing:

**Chris Sangwin**: C.J.Sangwin@ed.ac.uk

Please include the following information in your report:

- A description of the vulnerability and its potential impact
- Steps to reproduce the issue
- Any relevant screenshots or proof of concept
- Your contact information for follow-up questions

### What to Expect

- We will acknowledge receipt of your vulnerability report within 3 business days
- We will provide an estimated timeline for a fix
- We will notify you when the vulnerability has been fixed
- We will credit you for the discovery (unless you prefer to remain anonymous)

### Please Do Not

- Disclose the vulnerability publicly before it has been addressed
- Test the vulnerability on the production website (https://stack-assessment.org) without permission
- Access, modify, or delete data that does not belong to you
- Perform any actions that could negatively impact the availability of the service

## Supported Versions

The STACK website is continuously deployed from the `master` branch. Security updates are applied to the latest version only.

| Version | Supported          |
| ------- | ------------------ |
| Latest  | :white_check_mark: |
| Older   | :x:                |

## Known Security Considerations

### External Dependencies

This website uses the following external resources:

- **MathJax** (via Cloudflare CDN) - for mathematical rendering
- **Google Fonts** - for icon fonts
- **Google Maps** - for case study location visualization

Users should be aware that these services may set cookies or track usage according to their respective privacy policies.

### Data Collection

The STACK website itself does not collect personal data. However:

- GitHub Pages (our hosting provider) may collect IP addresses and request logs
- Third-party embedded services (Google Maps, YouTube) may collect data according to their privacy policies

For more information, see our [Privacy Statement](https://stack-assessment.org/Legal/PrivacyStatement).

## Best Practices for Contributors

When contributing to this repository:

1. **Never commit secrets** - API keys, passwords, tokens should never be in the code
2. **Validate user input** - If adding interactive features, sanitize all inputs
3. **Use HTTPS** - Always link to external resources using HTTPS URLs
4. **Keep dependencies updated** - Dependabot will help, but review and merge updates promptly
5. **Follow accessibility guidelines** - Security includes making the site accessible to all users

## Security Updates

Security updates are handled through:

1. **Dependabot** - Automated dependency updates (enabled)
2. **GitHub Security Advisories** - Monitoring for known vulnerabilities
3. **Manual review** - Regular security audits by maintainers

## Additional Resources

- [STACK Main Project Security](https://github.com/maths/moodle-qtype_stack) - For security issues in the STACK system itself
- [GitHub Security Best Practices](https://docs.github.com/en/code-security)
- [OWASP Web Security](https://owasp.org/www-project-web-security-testing-guide/)

---

**Last Updated:** December 2025
