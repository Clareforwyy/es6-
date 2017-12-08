# es6-笔记

## forEach，for in ,for of循环
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
````

## filter

````
//filter 不操作原数组，返回过滤后的新数组
//回调函数返回true,这一项放入新数组中
let narr = arr.filter(function (item) {
    return item>2&&item<6
})
console.log(narr)//[4,5]
console.log(arr)//[1,2,4,5,6]

````

## map映射

````
//map映射 将原有数组映射成一个新数组[]
//不操作原数组，return什么就返回什么
let arr1 = arr.map(function (item) {
    return `<li>${item}</li>`; //反引号是es6中的模板字符串，遇到变量用${}取值
})
console.log(arr1)//[ '<li>1</li>','<li>2</li>','<li>4</li>','<li>5</li>','<li>6</li>' ]

````
## includes，find ，some，every

````
let arr2 = [1,2,3,4,55,555];

//includes是否包含
console.log(arr2.includes(5));//返回bool false
//find 返回找到的一项，不改变原数组 返回true表示找到，停止循环、

let narr2 = arr2.find(function (item,index) {
    return item.toString().indexOf(5)>-1
})
console.log(narr2); //55

//some 找到true,返回true
let narr3 = arr2.some(function (item,index) {
    return item.toString().indexOf(5)>-1
})
console.log(narr3); //true

//every 找到false,找到false,返回false
let narr4 = arr2.every(function (item,index) {
    return item.toString().indexOf(5)>-1
})
console.log(narr4); //找到1就是false停止循环

````

## reduce 收敛

````
//reduce 收敛 4个参数 返回叠加后的结果，原数组不变，回调函数返回的结果
let arr3 = [1,2,3,4,5];
//prev代表的数组的第一项到二次是return的返回值没有return 则为undefined，next代表数组第二项
arr3.reduce(function (prev,next,index,item) {
    console.log(arguments)
});
//{ '0': 1, '1': 2, '2': 1, '3': [ 1, 2, 3, 4, 5 ] }
//{ '0': undefined, '1': 3, '2': 2, '3': [ 1, 2, 3, 4, 5 ] }
//{ '0': undefined, '1': 4, '2': 3, '3': [ 1, 2, 3, 4, 5 ] }
//{ '0': undefined, '1': 5, '2': 4, '3': [ 1, 2, 3, 4, 5 ] }

//求和
let arr4 = [{price:20,count:2},{price:30,count:3},{price:40,count:4}]
let narr5 = arr4.reduce(function (prev,next,index,item) {
    return prev + next.price*next.count;
},0);
//加0指定默认第一次的prev
console.log(narr5)//290

let  arr5 = [[1,2,3],[4,5,6],[6,7,8]];
let nnarr5 = arr5.reduce(function (prev,next) {
    return prev.concat(next)//prev是上一次的返回结果
})
console.log(nnarr5);//[1,2,3,4,5,6,7,8]

````
