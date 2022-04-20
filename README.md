# Currying-in-Javascript
Currying to pass arguments in different different ways in the same function

        <h2 style="text-align:center">1. Total sum of infinite arguments</h2>
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
        </pre>
