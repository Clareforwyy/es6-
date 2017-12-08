# es6-笔记
````
let arr = [1,2,4,5,6];
//forEach不支持return,属于声明式，不关心如何实现
arr.forEach(function (value) {
    console.log(value);//1,2,4,5,6
})
for(let key in arr){
    console.log(key);
    //key会变成字符串类型（index），数组的私有属性也会打印出来
}
for(let val of arr){
    console.log(val);
    //支持retur，只能of数组的value
}
//filter 不操作原数组，返回过滤后的新数组
//回调函数返回true,这一项放入新数组中
let narr = arr.filter(function (item) {
    return item>2&&item<6
})
console.log(narr)//[4,5]
console.log(arr)//[1,2,4,5,6]

//map映射 将原有数组映射成一个新数组[]
//不操作原数组，return什么就返回什么
let arr1 = arr.map(function (item) {
    return `<li>${item}</li>`; //反引号是es6中的模板字符串，遇到变量用${}取值
})
console.log(arr1)//[ '<li>1</li>','<li>2</li>','<li>4</li>','<li>5</li>','<li>6</li>' ]
````
