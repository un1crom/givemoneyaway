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

*some experiements*
https://github.com/un1crom/givemoneyaway/blob/master/sim.pdf
that's 25 simulations of 10 people with 10 bucks trading for 1000 rounds.

*notes on probabilities*
i arrived at some trickery...
the probability of giving up a dollar is 1 if you have money to start a round.
the probability of giving up a dollar is 0 if you have no money to start a round.
the probability of gaining at least 1 dollar in a round is equal to (1/number of people minus the giver) * number of people with a dollar (minus yourself).
the probability of gaining more than 1 dollar in a round is....???

consider just 3 people with 3 bucks... all 3 will decrement a dollar. each person as a 1/2 chance of getting a dollar from each of the other 2. there is 1 in 4 chance of getting 2 total bucks. there is 2 of 4 chance of getting at least 1 dollar. there is 1/4 of getting no dollars. so there's a 1/4 chance of profit, 2/4 chance of breaking even, 1/4 chance of losing money.

in round 2.... etc by round 4 someone can be out of money. so now the probability would change. say player 1, 2 have money, 3 doesn't. player 1,2 will decrement a dollar. player 1 has 1/2 chance breaking even, 1/2 chance losing 1 dollar, no chance of breaking even, player 2 as well. player 3 has 1/2 chance of gaining a dollar, 1/2 chance of staying at 0.

now this may not be right because I'm thinking about simultaneity. if player 2 has already given dollar to player 1, player 3 has zero chance of getting a dollar from player 2. so positive outcomes are now just 1/4 (1/2 of player one, 0/2 from player 2...)... 

this late hour could have me totally screwed up.

we're in Monty Hall problem land I feel like.
