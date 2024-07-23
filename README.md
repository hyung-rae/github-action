# Reusing Workflows

[Github actions notes](https://rea1994.notion.site/Github-actions-8f3df9d5072a4e08844ebda4b0cce684)   

[e2e test workflows](https://github.com/hyung-rae/end-to-end)

### Workflows

![스크린샷 2024-07-11 오후 3 43 48](https://github.com/hyung-rae/github-action/assets/174302871/aec241ac-6190-4d84-93fa-c88ff0fcd05a)


### Slack message Custom (slack.yml)
```YAML
jobs:
  slack-message:
    runs-on: ubuntu-latest
    steps:
      - name: success-message
        uses: 8398a7/action-slack@v3
        with:
          status: success
          author_name: 큐샵 어드민 E2E 테스트
          text: 🎉 E2E test 성공
          fields: repo,message,author,ref
        env:
          SLACK_WEBHOOK_URL: ${{ secrets.SLACK_WEBHOOK_URL }}

      - name: failure-message
        uses: 8398a7/action-slack@v3
        with:
          status: failure
          author_name: 큐샵 어드민 E2E 테스트
          text: ❌ E2E test 실패
          fields: repo,message,author,ref
        env:
          SLACK_WEBHOOK_URL: ${{ secrets.SLACK_WEBHOOK_URL }}        
          
      - name: cancelled-message
        uses: 8398a7/action-slack@v3
        with:
          status: cancelled
          author_name: 큐샵 어드민 E2E 테스트
          text: 😳 E2E test 취소
          fields: repo,message,author,ref
        env:
          SLACK_WEBHOOK_URL: ${{ secrets.SLACK_WEBHOOK_URL }}       
```
