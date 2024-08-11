# test-request
** All following exams please using Javascript only **
# 1.
/**
There is an array, each item has such format:
{firstName: 'xxx', lastName: 'xxx', customerID: 'xxx', note: 'xxx', 
profession: ‘xxx’}
lastName, note can be empty, customerID can only be a set of digital 
numbers.
profession can only have ‘student’, ‘freelancer’, ‘productOwner’, 
‘engineer’ or ‘systemAnalytics’.
**/
/**
# Q1. Please follow the principle (‘firstName’ + ‘lastName’ + ‘customerID’) 
to sort this array and print it out.
**/
function sortUserName(user) {
const newABC = [...user];
 let { note, profession, ...rest } = newABC[0];
 console.log("rest", [rest]);
}
/**
# Q2. Please sort by ‘profession’ to follow the principle. 
(‘systemAnalytics’ > ‘engineer’ > ‘productOwner’ > ‘freelancer’ > 
‘student’’)
**/
function sortByType(user) {
const newABC = [...user]; 
 console.log(
 " sortByType ",
 abc.sort(
 (a, b) =>
 professionOrder.indexOf(a.profession) -
 professionOrder.indexOf(b.profession)
 )
 );
}
# 2.
/** HTML
<div class="container">
<div class="header">5/8 外出確認表</div>
<div class="content">
<ol class="shop-list">
<li class="item">麵包</li>
<li class="item">短袖衣服</li>
<li class="item">飲用水</li>
<li class="item">帳篷</li>
</ol>
<ul class="shop-list">
<li class="item">暈車藥</li>
<li class="item">感冒藥</li>
<li class="item">丹木斯</li>
<li class="item">咳嗽糖漿</li>
</ul>
</div>
<div class="footer">以上僅共參考</div>
</div>
**/
/** CSS
.container {
font-size: 14px;
}
.container .header 
{ font-size: 18px;
}
.container .shop-list 
{ list-style: none; 
margin-left: -15px;
}
.container .shop-list li.item 
{ color: green;
}
.container .shop-list .item {
/* Explain why does this color not works, and how to fix make it work on 
1st list */
/* Answer: 因為CSS優先級綠色多一個元素li跟選擇器不夠明確， 改
成 .container .shop-list li.item 就會變成藍色了 */
color: blue;
}
/* Write styling make every other line give background color to next one */
.container ol.shop-list li.item:nth-child(2n+1),.container ul.shop-list 
li.item:nth-child(2n+1){
 background-color: red;
 }
**/
# 3.
/**
let items = [1, 1, 1, 5, 2, 3, 4, 3, 3, 3, 3, 3, 3, 7, 8, 5, 4, 9, 0, 1,
3, 2, 6, 7, 5, 4, 4, 7, 8, 8, 0, 1, 2, 3, 1];
Please write down a function to console log unique value from this array.
**/
function getUniqueNumber (items) {
const newItems = new Set(items);
console.log("Answer",[ ...newItems].sort());
}
# 4.
/** Can you explain about Interface and Enum, and where will you be using, 
please make some examples. **/
Interface是一種介面，定義對象內部結構，用於串接後端api回傳的資料型態，或是前端資料轉型用。
Enum是枚舉，是一種定義同系列的常數，管理狀態使用，後端回傳的response的status code。
# 5.
/** Can you explain the problem with the following code, and how to fix 
it. **/
class Count extends React.Component 
{ constructor(props) {
super(props);
this.state = { count: 0 };
this.handleAddCount = this.handleAddCount.bind(this);
}
handleAddCount(){
this.setState({ count: this.state.count + 1 }); 
this.setState({ count: this.state.count + 1 }); 
this.setState({ count: this.state.count + 1 });
}
render() 
{ return 
(
<div>
<h2>{this.state.count}</h2>
<button onClick={this.handleAddCount}>Add</button>
</div>
);
}
}
ReactDOM.render(
<Count />, 
document.getElementById('root')
);
如果想實現一次加3，可以改成 this.setState((prev) => ({ count: prev.count + 1 }))，用setState回調函式確保式最新
的狀態。
因為setSate是異步處理，加上React會批量處裡setState，如果只更改當前的this.status.count會
被React合併更新一次
# 6.
/** Please write the sample code to debounce handleOnChange **/
var SearchBox = 
React.createClass({ render: 
function() {
return <input type="search" name="p" value={ inputValue }
onChange={this.handleOnChange}
/>;
},
const [inputValue, setInputValue] = useState("");
const [result, setResult] = useState("");
const callApi = async (value: string) => {
 const apiResult = await new Promise<string>((res, rej) => {
 setTimeout(() => {
 console.log("api response");
 res("api Result");
 }, 1000);
 });
 setResult(apiResult);
 };
const debounce = (func: (val: string) => void) => {
 let timeOut: NodeJS.Timeout;
 return (arg: string) => {
 if (timeOut) clearTimeout(timeOut);
 timeOut = setTimeout(() => {
 func(arg);
 }, 2000);
 };
 };
 const updateDebouncedValue = useCallback(
 debounce((value: string) => {
 callApi(value);
 }),
 []
 );
handleOnChange: function(event) {
setInputValue(event.target.value);
 updateDebouncedValue(event.target.value);
}
})
