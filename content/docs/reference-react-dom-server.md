---
id: react-dom-server
title: ReactDOMServer
layout: docs
category: Reference
permalink: docs/react-dom-server.html
---

С помощью объекта `ReactDOMServer` вы можете рендерить компоненты в статическую разметку. Обычно, это использует на Node JS сервере:

```js
// ES modules
import ReactDOMServer from 'react-dom/server';
// CommonJS
var ReactDOMServer = require('react-dom/server');
```

## Overview {#overview}

The following methods can be used in both the server and browser environments:

Следующие методы можно использовать как в серверном, так и браузерном окружении.
- [`renderToString()`](#rendertostring)
- [`renderToStaticMarkup()`](#rendertostaticmarkup)

These additional methods depend on a package (`stream`) that is **only available on the server**, and won't work in the browser.

Эти же методы имеют в зависимостях пакет (`stream`), **доступный только на сервере**, поэтому они не будут работать в браузере.
- [`renderToNodeStream()`](#rendertonodestream)
- [`renderToStaticNodeStream()`](#rendertostaticnodestream)

* * *

## Reference {#reference}

### `renderToString()` {#rendertostring}

```javascript
ReactDOMServer.renderToString(element)
```

Render a React element to its initial HTML. React will return an HTML string. You can use this method to generate HTML on the server and send the markup down on the initial request for faster page loads and to allow search engines to crawl your pages for SEO purposes.

Рендер React элемента в его начальную HTML разметку. Возвращает HTML строку. Вы можете использовать этот метод, чтобы создать HTML разметку на сервере и отдать её на инициирующий запрос. Это может помочь быстре загружать страницу и позволит поисковым движкам **TODO**

If you call [`ReactDOM.hydrate()`](/docs/react-dom.html#hydrate) on a node that already has this server-rendered markup, React will preserve it and only attach event handlers, allowing you to have a very performant first-load experience.

Если вызвать метод [`ReactDOM.hydrate()`](/docs/react-dom.html#hydrate) на элементе, у которого уже есть срендеренная на сервере разметка, React только добавить event handlers. Это позволит **TODO:**
* * *

### `renderToStaticMarkup()` {#rendertostaticmarkup}

```javascript
ReactDOMServer.renderToStaticMarkup(element)
```

Similar to [`renderToString`](#rendertostring), except this doesn't create extra DOM attributes that React uses internally, such as `data-reactroot`. This is useful if you want to use React as a simple static page generator, as stripping away the extra attributes can save some bytes.

Этот метод похож на [`renderToString`](#rendertostring), но он отличен тем, что не создает дополнительных DOM атрибутов, которые используются внутри React'а, например `data-reactroot`. Это может быть очень полезно, если вы хотите использовать React как генератор простых статических страниц, потому что избавление от дополнительных атрибутов может сохранить несколько байт.

If you plan to use React on the client to make the markup interactive, do not use this method. Instead, use [`renderToString`](#rendertostring) on the server and [`ReactDOM.hydrate()`](/docs/react-dom.html#hydrate) on the client.

Если вы планируете использовать React, чтобы клиентская часть была интерактивной – не используйте этот метод. Вместо него используйте [`renderToString`](#rendertostring) на сервере и [`ReactDOM.hydrate()`](/docs/react-dom.html#hydrate) на клиенте.
* * *

### `renderToNodeStream()` {#rendertonodestream}

```javascript
ReactDOMServer.renderToNodeStream(element)
```

Render a React element to its initial HTML. Returns a [Readable stream](https://nodejs.org/api/stream.html#stream_readable_streams) that outputs an HTML string. The HTML output by this stream is exactly equal to what [`ReactDOMServer.renderToString`](#rendertostring) would return. You can use this method to generate HTML on the server and send the markup down on the initial request for faster page loads and to allow search engines to crawl your pages for SEO purposes.

Рендер React элемента в его начальную HTML. Возвращает [Readable stream](https://nodejs.org/api/stream.html#stream_readable_streams), у которого выходной параметр – HTML строка. Полученный HTML будет в точности соответствовать тому, что возвращает метод [`ReactDOMServer.renderToString`](#rendertostring). Вы можете использовать этот метод, чтобы создать HTML разметку на сервере и отдать её на инициирующий запрос. Это может помочь быстре загружать страницу и позволит поисковым движкам **TODO**

If you call [`ReactDOM.hydrate()`](/docs/react-dom.html#hydrate) on a node that already has this server-rendered markup, React will preserve it and only attach event handlers, allowing you to have a very performant first-load experience.

Если вызвать метод [`ReactDOM.hydrate()`](/docs/react-dom.html#hydrate) на элементе, у которого уже есть срендеренная на сервере разметка, React только добавить event handlers. Это позволит **TODO:**
* * *

> Note:
>
> Server-only. This API is not available in the browser.
>
> The stream returned from this method will return a byte stream encoded in utf-8. If you need a stream in another encoding, take a look at a project like [iconv-lite](https://www.npmjs.com/package/iconv-lite), which provides transform streams for transcoding text.

> Замечание:
> 
> Используется только на сервере. Это API не доступно в браузере.
> 
> Метод возвращает поток, который вернет поток байт, закодированных в utf-8. Если вам нужен поток в другой кодировке, TODO:
* * *

### `renderToStaticNodeStream()` {#rendertostaticnodestream}

```javascript
ReactDOMServer.renderToStaticNodeStream(element)
```

Similar to [`renderToNodeStream`](#rendertonodestream), except this doesn't create extra DOM attributes that React uses internally, such as `data-reactroot`. This is useful if you want to use React as a simple static page generator, as stripping away the extra attributes can save some bytes.

Этот метод похож на [`renderToNodeStream`](#rendertonodestream), но он отличен тем, что не создает дополнительных DOM атрибутов, которые используются внутри React'а, например `data-reactroot`. Это может быть очень полезно, если вы хотите использовать React как генератор простых статических страниц, потому что избавление от дополнительных атрибутов может сохранить несколько байт.

The HTML output by this stream is exactly equal to what [`ReactDOMServer.renderToStaticMarkup`](#rendertostaticmarkup) would return.

HTML, полученная из этого потока в точности совпадает с тем, что возвращает метод [`ReactDOMServer.renderToStaticMarkup`](#rendertostaticmarkup) 

If you plan to use React on the client to make the markup interactive, do not use this method. Instead, use [`renderToNodeStream`](#rendertonodestream) on the server and [`ReactDOM.hydrate()`](/docs/react-dom.html#hydrate) on the client.

Если вы планируете использовать React, чтобы клиентская часть была интерактивной – не используйте этот метод. Вместо него используйте [`renderToString`](#rendertostring) на сервере и [`ReactDOM.hydrate()`](/docs/react-dom.html#hydrate) на клиенте.

> Note:
>
> Server-only. This API is not available in the browser.
>
> The stream returned from this method will return a byte stream encoded in utf-8. If you need a stream in another encoding, take a look at a project like [iconv-lite](https://www.npmjs.com/package/iconv-lite), which provides transform streams for transcoding text.

> Замечание:
> 
> Используется только на сервере. Это API не доступно в браузере.
> 
> Метод возвращает поток, который вернет поток байт, закодированных в utf-8. Если вам нужен поток в другой кодировке, TODO: