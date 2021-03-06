[简体中文](README.zh-CN.md) | English


# Object.defineProperty Sham For IE&nbsp;&nbsp;![Version](https://img.shields.io/npm/v/object-defineproperty-ie.svg)

A `Object.defineProperty` sham based on **VBScript** for IE. It also provides `Object.defineProperties`, `Object.getOwnPropertyDescriptor`, `Object.getOwnPropertyDescriptors`.


#### Notice
1. Use native method for `Element` object in IE8;
1. In other case, `Object.defineProperty` will return a new VB object;
1. VB object can't add or delete properties freely;
1. VB object doesn't have `[[Prototype]]` or `__proto__`;
1. The properties of VB object is enumerable even if descriptor `enumerable` is `false`;


#### Installation
1. Use NPM: `npm install -S object-defineproperty-ie`
1. Download directly: <a href="src/object-defineproperty-ie.js" target="_blank">Development Version</a>, <a href="dist/object-defineproperty-ie.js" target="_blank">Production Version</a>


#### Usage
```html
<script src="path/to/object-defineproperty-ie.js" type="text/javascript"></script>
<script type="text/javascript">
    var oldObj = Object.defineProperty({}, 'string', {
        value: 'Ambit Tsai',
        enumerable: true
    });
    // oldObj => {string: "Ambit Tsai"}

    var newObj = Object.defineProperties(oldObj, {
        getter: {
            get: function () {
                return this.string;
            }
        },
        setter: {
            set: function (value) {
                this.string = value;
            }
        }
    });
    // newObj => {
    //     getter: "Ambit Tsai",
    //     setter: undefined,
    //     string: "Ambit Tsai"
    // }

    var desc = Object.getOwnPropertyDescriptor(newObj, 'string');
    // desc => {
    //     configurable: false,
    //     enumerable: true,
    //     value: "Ambit Tsai",
    //     writable: false
    // }
</script>
```


#### Testing
Accessing `test/index.html` with browser


#### Contact Us
1. *WeChat*: ambit_tsai
1. *QQ Group*: 663286147
1. *E-mail*: ambit_tsai@qq.com


#### Reference
1. <a href="https://www.cnblogs.com/rubylouvre/p/3598133.html" target="_blank">迷你MVVM框架avalon在兼容旧式IE做的努力</a>
