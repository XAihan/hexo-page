---
title: 使用rem进行前端样式适配的方法
date:  2019-11-18 18:35:11
tags: 实战技巧 rem转换
---

```js
 /*设置Rem*/
        (function (w, d, psd_w) {
            var resizeTime = null,
                waitTime = 300;

            //设置FontSize
            function changeRem() {
                var width = d.documentElement.clientWidth,
                    height = d.documentElement.clientHeight,
                    fontSize = width / psd_w * 100;

                if (fontSize > 100) fontSize = 100;
                // if (width / height >= 0.75) fontSize = 85;
                d.documentElement.style.fontSize = fontSize + 'px';
            }

            //监听屏幕变化
            w.addEventListener('onorientationchange' in w ? 'orientationchange' : 'resize', function () {
                clearTimeout(resizeTime);
                resizeTime = setTimeout(changeRem, waitTime);
            }, false);
            w.addEventListener('pageshow', function (win) {
                win.persisted && (clearTimeout(resizeTime), resizeTime = setTimeout(changeRem, waitTime));
            }, false);
            d.addEventListener('DOMContentLoaded', changeRem, false);
        }(window, document, 2560));

```