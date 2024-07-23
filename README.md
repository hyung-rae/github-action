# Reusing Workflows

[Github actions notes](https://rea1994.notion.site/Github-actions-8f3df9d5072a4e08844ebda4b0cce684)   

[e2e test workflows](https://github.com/hyung-rae/end-to-end)

### Workflows

![스크린샷 2024-07-11 오후 3 43 48](https://github.com/hyung-rae/github-action/assets/174302871/aec241ac-6190-4d84-93fa-c88ff0fcd05a)


### Slack message Custom (slack.yml)
- [slack api workflow](https://github.com/8398a7/action-slack) 
```YAML
name: slack

on:
  workflow_call:
    # alert 상태와 메시지를 Input으로 받음
    inputs:
      status:
        required: true
        type: string
      title:
        required: true
        type: string

    secrets:
      web_hook_url:
        required: true

jobs:
  slack-message:
    runs-on: ubuntu-latest
    steps:
      - name: success-message
        if: ${{ inputs.status == 'success' }}
        uses: 8398a7/action-slack@v3
        with:
          status: success
          author_name: '${{ inputs.title }}'
          text: '🎉 ${{ inputs.title }} 성공'
          fields: repo,message,author,ref
        env:
          SLACK_WEBHOOK_URL: ${{ secrets.web_hook_url }}

      - name: failure-message
        if: ${{ inputs.status == 'failure' }}
        uses: 8398a7/action-slack@v3
        with:
          status: failure
          author_name: '${{ inputs.title }}'
          text: '❌ ${{ inputs.title }} 실패'
          fields: repo,message,author,ref
        env:
          SLACK_WEBHOOK_URL: ${{ secrets.web_hook_url }}

      - name: cancelled-message
        if: ${{ inputs.status == 'cancelled' }}
        uses: 8398a7/action-slack@v3
        with:
          status: cancelled
          author_name: '${{ inputs.title }}'
          text: '😳 ${{ inputs.title }} 취소'
          fields: repo,message,author,ref
        env:
          SLACK_WEBHOOK_URL: ${{ secrets.web_hook_url }}  
```
