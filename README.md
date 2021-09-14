[![Create Release][release-badge]][release-url]
[![Import Labels][import-labels-badge]][import-labels-url]
[![Sync Labels][sync-labels-badge]][sync-labels-url]
[![PR AutoLabeler][autolabeler-badge]][autolabeler-url]
[![Assigner][assigner-badge]][assigner-url]

Description

Composite Action for notifying users in slack when their github action fails

### Inputs
#### `token`
Token with API access
required: true

#### `actor`
GitHub user to notify in slack
default: `${GITHUB_ACTOR}`

#### `service`
The service being deployed/removed
required: true

#### `stage`
The stage being deployed/removed
required: true
default: `${{ matrix.stage }}`

#### `region`
The region the action is being performed in
required: true
default: `${{ matrix.region }}`

#### `icon`
Custom icon for slack message
required: false

#### `emoji`
Slack emoji to accompany message
required: false

#### `title`
Slack message title
required: false

#### `slack_webhook`
Slack webhook
required: true

#### `slack_color`
Color on the side of the message
required: false
default: `${{ job.status }}`

### Outputs
#### `user`
GitHub actor

#### `repo`
Repository name


### Example usage
```yaml
      - name: Notify on failure to remove
        if: failure()
        uses: Cumulusds/notify-user-action@v1
        with:
          token: ${{ secrets.TOKEN }}
          service: ${{ steps.role.outputs.service }}
          stage: ${{ steps.set-feature-stage.outputs.stage }}
          slack_webhook: ${{ secrets.SLACK_WEBHOOK }}
```

[release-badge]: https://github.com/CumulusDS/notify-user-action/actions/workflows/release.yml/badge.svg
[release-url]: https://github.com/CumulusDS/notify-user-action/actions/workflows/release.yml
[import-labels-badge]: https://github.com/CumulusDS/notify-user-action/actions/workflows/labels_import.yml/badge.svg
[import-labels-url]: https://github.com/CumulusDS/notify-user-action/actions/workflows/labels_import.yml
[sync-labels-badge]: https://github.com/CumulusDS/notify-user-action/actions/workflows/labels_sync.yml/badge.svg
[sync-labels-url]: https://github.com/CumulusDS/notify-user-action/actions/workflows/labels_sync.yml
[autolabeler-badge]: https://github.com/CumulusDS/notify-user-action/actions/workflows/autolabeler.yml/badge.svg
[autolabeler-url]: https://github.com/CumulusDS/notify-user-action/actions/workflows/autolabeler.yml
[assigner-badge]: https://github.com/CumulusDS/notify-user-action/actions/workflows/assign.yml/badge.svg
[assigner-url]: https://github.com/CumulusDS/notify-user-action/actions/workflows/assign.yml
