1.post传一个数组
后端：
@PostMapping("")
public String testPost(@RequestBody Integer[] ids){}
前端：
body:
[1,2,3]

2.get传数组到后端
&ids=1,2,3