*givemoney*

based on this blog post and the thought experiement here's some code to study the strange world that is randomly giving money to people.

http://www.decisionsciencenews.com/2017/06/19/counterintuitive-problem-everyone-room-keeps-giving-dollars-random-others-youll-never-guess-happens-next/

*code inspiration*

I borrowed code from commenter on blog to get going.

Philip says:
I seem to be incorrect in the above. Tried it in Mathematica and even after millions of steps it does not converge to anything close to a single owner of all wealth.

ReverseSort@
Last@With[{n = 100, m = 1000000},
NestList[
Block[{x = #},
Scan[(If[x[[#]] > 0, x[[#]]–;
With[{j = RandomChoice[Delete[Range@n, #]]}, x[[j]]++]]) &,
Range@n]; x] &, ConstantArray[n, n], m]]
