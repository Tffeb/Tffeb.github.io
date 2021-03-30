---
layout: post
title: '百度翻译api'
date: 2021-01-30

tag:
  - js
---


#### 百度翻译api的使用
```js

 baiduTranslate=()=>{
        const option = {
            appid: '20190216000267610',   //申请的appid
            key: 'avc5ndaA3W9TK7E1oHPO',  //
            from: 'auto',
            to: 'en',   // 翻译后的语言
        };
        const salt = new Date().getTime();
        let content = null; // 需要翻译的内容
        content = content.replace(/\/:\d{3}/g, ' ');
        content = content.replace(/<br \/>/g, '\n');
        const str1 = option.appid + content + salt + option.key;
        const sign = MD5(str1);
        const formData = new FormData();
        formData.append('q', content);
        formData.append('appid', option.appid);
        formData.append('salt', salt);
        formData.append('from', option.from);
        formData.append('to', option.to);
        formData.append('sign', sign);
        $.ajax({
            url: 'https://fanyi-api.baidu.com/api/trans/vip/translate',
            type: 'get',
            dataType: 'jsonp',
            data: {
                q: content,
                appid: option.appid,
                salt,
                from: option.from,
                to: option.to,
                sign,
            },
            success: (data) => {
                if (data && data.trans_result && data.trans_result.length) {
                  const transResult = data.trans_result.map(v => `${v.dst}<br />`).join('');
                }
            },
        });
    }
```