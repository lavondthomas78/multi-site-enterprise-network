# Publishing preparation

## Suggested repository

Existing repository: `lavondthomas78/multi-site-enterprise-network`  
Description: Three-stage Cisco Packet Tracer portfolio: campus/branch, Enterprise campus, and integrated multi-site network with ASA firewalls, OSPF, HSRP, web, email, and voice.

## Ready in this package

- Main portfolio README with the three-design progression.
- Separate design pages and actual screenshots of both originals and the final integrated topology.
- Detailed operational record with addressing, routes, ACLs, and recovery history.
- LinkedIn post and resume entry drafts.

## Still needed before a complete three-design release

1. Attach the two final original `.pkt` files. Both original topology screenshots are now included.
2. Attach the final integrated `.pkt` file corresponding to the completed October 29 topology.
3. Use publishing copies of `.pkt` files: replace real or reused passwords with dedicated lab values. Hashed/encrypted password lines can still contain credential material. Do not publish unreviewed full console transcripts.
4. The GitHub connection is confirmed. This portfolio is being proposed under `portfolio/` in the existing repository; approved project files can be added under the relevant design folders.
5. Open the published README and verify the screenshot and document links. Add the actual repository URL to the LinkedIn draft and resume.

This portfolio addition contains no new `.pkt` binaries. Its three topology screenshots were supplied by the owner. The technical record is an excerpt-based reconstruction, not a complete device backup. This portfolio is staged for a GitHub draft pull request. The LinkedIn text remains an unpublished draft.

## Saving the completed lab

On modified IOS routers/switches, save the running configuration using `copy running-config startup-config` or `write memory`. On the ASAs use `write memory`. Save the final `.pkt` file with a distinct completed version name and retain the earlier working originals.
