---
theme: zhozhoba
layout: cover
company: EchoYzd
download: false
date: 2022.06.25

---
# Web Components 分享


<style>
.slidev-layout h1 {
  font-size: 47px;
}
</style>

---
layout: content-1
---
# 大纲

- web-components的介绍
- 入门Demo
- Web-components Awesome
- 下期预告

<br>
<br>

Some text with [link](#)

---
layout: section-1
---

# web-components的介绍

Some Section break slide text

[Documentations](https://developer.mozilla.org/zh-CN/docs/Web/Web_Components)

[popup-info-box-web-component](https://mdn.github.io/web-components-examples/popup-info-box-web-component/)

<style>
.slidev-layout.section-1 h1{
  font-size: 51px;
}
</style>

---
layout: section-2
---

# Demo1

Code description

```js
class EchoDiv extends HTMLElement{
    constructor(){
        super();
        this.attachShadow({
            mode: 'open'
        });
        // this.shadowRoot.innerHTML = `
        // <div style="background-color: pink; width:100px; height: 100px;color:#fff;">
        //     <slot></slot>
        // </div>
        // `;
        this.shadowRoot.innerHTML = `
        <style>
            div {
                background-color: pink;
                width: 100px;
                height: 100px;
                color: #fff;
            }
        </style>
        <div>
            <slot></slot>
        </div>
        `
    }
}

customElements.define("echo-div", EchoDiv);
```

<style>
pre[class*='language-'] {
  overflow-x: hidden; overflow-y: auto;
}
</style>


---
layout: section-2
---

# Demo2

Code description

```js
class EchoBtn extends HTMLElement {

    static get observedAttributes() {
        console.log('observedAttributes...')
        return ['count'];
    }

    get count() {
        return this.getAttribute('count') ? this.getAttribute('count') : 0 ;
    }

    set count(count) {
        this.setAttribute('count', count);
    }


    constructor() {
        console.log('constructor...')
        super();

        this.attachShadow({
            mode: 'open'
        });

        this.shadowRoot.innerHTML = `
            <div>
                <button>${this.count}</button>
            </div>
        `;

        // 添加事件
        this.btn = this.shadowRoot.querySelector('button');
        this.btn.addEventListener('click', () => {
            console.log('click...')
            this.count++;
        }, false);
    }


    // 属性改变的通知事件
    attributeChangedCallback(attr, oldVal, newVal) {
        console.log('attributeChangedCallback...attr=', attr,' oldVal=', oldVal, ' newVal=', newVal);

        if('count' === attr && oldVal !== newVal) {
            this.btn.textContent = newVal;
        }
    }
}

customElements.define("echo-btn", EchoBtn);
```

<style>
pre[class*='language-'] {
  overflow-x: hidden; overflow-y: auto;
}
</style>

---
layout: content-2
---
# Web-components Awesome List

* [kor-ui](https://kor-ui.com/components/app-bar)
* [shoelace](https://shoelace.style/components)
* [wu-component](https://wu-component.github.io/)
* [spectrum-web-components](https://opensource.adobe.com/spectrum-web-components/components)
* [ui5-webcomponents](https://sap.github.io/ui5-webcomponents/playground/components)
* [css-doodle](https://css-doodle.com/#usage)


---
layout: content-1
---
# 下期预告

使用web-components开发chrome插件

---
layout: end
---

# Thanks!

祝大家有一个美好的夜晚
