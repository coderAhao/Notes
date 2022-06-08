###### 1.对象数组扁平化

```javascript
let s = [
{
  id: '1',
  name: '第一级1',
  children: [
    {
      id: '1-1',
      name: '第二级1-1',
      children: [
        {id: '1-1-1',name: '第三级1-1-1'},
        {id: '1-1-2',name: '第三级1-1-2'}
      ]
    },
    {
      id: '1-2',
      children: [
        {
          id: '1-2-1',
          children: [{id: '1-2-1-1'}]
        }
      ]
    }
  ]
},
{
  id: '2',
  children: [
    {
      id: '2-1',
      children: [
        {id: '2-1-1'},
        {id: '2-1-2'}
      ]
    },
    {
      id: '2-2',
      children: [{id: '2-2-1'}]
    }
  ]
}
]
let Arr = []
function fun(arr,type) {
  arr.forEach(item => {
    item[type] ? Arr.push(item[type]) : '';
    item.children ? fun(item.children,[type]) : '';
  })
}
fun(s,'name');
console.log(Arr); // ["第一级1", "第二级1-1", "第三级1-1-1", "第三级1-1-2"]
// 树状结构数据 可根据需要将name/id等提取到一个数组里
```

###### 2. 对象数组去重

```javascript
let obj = [
	{id: 1,value: 1},
	{id: 2,value: 2},
	{id: 1,value: 1},
]
// 方法1
let indexArr = []
let valueArr = []
function removeDuplication() {
  obj.forEach(item => {
    if (!indexArr.includes(item.id)) {
       indexArr.push(item.id)
       valueArr.push(item)
      }
  })
}

// 方法2
const res = new Map()
return obj.filter(obj => !res.has(obj.id) && res.set(obj.id, 1))
// 上一行最后set设置的obj.id为1，也可为其他任意字符 
```

###### 3. 数组去重

- ```javascript
    const arr = [1, 2, 1, 3, 2]
    // 方式1
    const newArr = []
    for(const item of arr) {
      if(newArr.indexOf(item) !== -1) {
      	newArr.push(item)
      }
    }
    // 方式2
    const arrSet = new Set(arr)
    const newArr = Array.from(arrSet)
    // 方式3
    const arrSet = new Set(arr)
    const newArr = [...arrSet]
    // 方式2和3需要将set结构变为数组结构
    ```

    

###### 4. 生成随机字符串

```javascript
const str = Math.random().toString(36).substr(2,10)
// Math.random 生成[0,1)的数，然后调用Number的toString方法将其转为36进制（36进制包含a-z和0-9) 最后截取小数位
```

