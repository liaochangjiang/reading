- [JavaScript 异步编程之路](https://juejin.im/post/5e436233518825497312189f)
- [阮一峰 - Promise 对象](http://es6.ruanyifeng.com/#docs/promise)
- [阮一峰 - async 函数](http://es6.ruanyifeng.com/#docs/async)

# 回调函数

异步网络请求：
```javascript
// loadData.js
// 参数 callback 即为回调函数
const loadData = (item, callback) => {	// line: 9
  if (item === 'score') {
    let xhr = new XMLHttpRequest()
    xhr.open('GET', './score.json')
    xhr.onreadystatechange = function () {
      // 待到结果返回时，调回调函数
      if (xhr.readyState === XMLHttpRequest.DONE && xhr.status === 200) {
        callback(xhr.responseText)	// line: 16
      }
    }
    xhr.open()
  }
}

const displayData = data => {	// line: 23
  console.log(`data: ${data}`)
}
```

麻烦在于：当连续出现“后一个异步操作依赖上一个异步操作的返回结果”时，回调函数会变得难以使用。

```javascript
load('score', data => {
    console.log(`score: ${data.score}`)
    if (data.score < 60) {
		sendToMon(data.score, res => {
            console.log(`message: ${res}`)
            sendToTeacher(res, comment => {
                console.log(`comment: ${comment}`)
                showComment(comment, state => {
                    if (state === 'success') {
                        console.log('complete')
                    }
                })
            })
        })
    }
})
```

# Promise

# Generator

# Async / Await