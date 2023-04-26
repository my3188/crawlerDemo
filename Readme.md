使用page.setRequestInterception拦截AJAX请求,手动发送请求获取响应数据:
js
const browser = await puppeteer.launch()
const page = await browser.newPage()
await page.setRequestInterception(true)
page.on('request', request => {
  if (request.url() === 'https://example.com/api/data') {
    request.respond({
      status: 200,
      content: 'data content'
    })
  }
})
await page.goto('https://example.com')
const content = await page.$eval('#content', el => el.textContent)





https://juejin.cn/post/6844903518390714381

https://juejin.cn/post/6844903967655198727

https://juejin.cn/post/6844903697047257101