# JavaScript Pitfall
* Function can be initialized anywhere
'''
var canFly = function(){ return true; }; 
window.isDeadly = function(){ return true; }; 
assert( isNimble() && canFly() && isDeadly(), "Still works, even though isNimble is moved." ); 
function isNimble(){ return true; }
'''
* 很好的处理判断Null的方法
'''
(request.headers['accept-encoding'] || '').indexOf('gzip') //indexOf is method of String, use || to make sure it is string type!
'''
* Use array join to concatenate string for performance consideration
* arguments is not a real array; Must convert to array before using array function
'''
function highest(){ 
  return makeArray(arguments).sort(function(a,b){ 
    return b - a; 
  }); 
} 
 
function makeArray(array){ 
  return Array().slice.call( array ); 
} 
'''
* Wrapper function to deal with asyn loop
'''
var count = 0; 
for ( var i = 0; i < 4; i++ ) (function(i){ 
  setTimeout(function(){ 
    assert( i == count++, "Check the value of i." ); 
  }, i * 200); 
})(i);
'''
# NODEJS Tips
* 每个模块只会初始化一次