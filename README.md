# Currying-in-Javascript
Currying to pass arguments in different ways in the same function
<ol><li><h2 style="text-align:center"> Total sum of infinite arguments - </h2>
<h3 style="text-align:center"><i>sum(1,2..n)(5,6…n)…(n)()</i></h3>
<pre>
const sum = function(...arg){
    const a = arg.reduce((a,b)=>a+b,0);
    return function(...arg1){
        const b = arg1.reduce((a,b)=>a+b,0);
        if(b) return sum(a+b);
        else return a;
    }
}
</pre></li><li><h2 style="text-align:center"> Making any existing function a currying function - </h2><h3 style="text-align:center"><i>A Function which will take another function as an argument and will return a new function which is curried version of the previous passed function</i></h3><pre>
const curryingFunc = (fn, ...args) => {
  if(args.length>=fn.length){
    return fn.apply(this,args);
  }
  else{
    return function(...args2){
      return curryingFunc(fn,...args.concat(args2));
    }
  }
}
</pre></li>
    <li><h2 style="text-align:center"> Making any existing function a currying function with infinite arguments - </h2>
<pre>
const curryingFunc = (fn) => {
  const initialArgs = [];
  return (...args) => {
    const allArgs = initialArgs.concat(args);
    if (allArgs.length >= fn.length) {
      return fn.apply(this, allArgs);
    } else {
      return curryingFunc(fn, ...allArgs); // Return a function for remaining arguments
    }
  };
};</pre></li></ol>
