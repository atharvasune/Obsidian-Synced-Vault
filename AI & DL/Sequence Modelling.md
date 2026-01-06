![](https://miro.medium.com/v2/resize:fit:1400/1*CjiN_nD3nRYxIQ6elJUBug.png)

Sequence modelling is as it says - models that understand sequences and are able to encode / generate them. Sequences are present everywhere, text, video, audio, signals..  even photos (we'll come to that.. here's a video to think about that -> [Why are transformers replacing CNNs ?](https://www.youtube.com/watch?v=KnCRTP11p5U&t=2s)) 

So on a high level, if we look at it, sequence modelling is literally just saying -> i have 10 things before, what are the next k things - or - i have 10 things in sequence, what do they mean. Now if we look at traditional [[MLP]]  it is very good at predicting output standalone, but it assumes the input is timeless and that is generally not the case with sequences, so we need to think more. 

One easy way to think about this is -> giving the model access to past information when making the next prediction 
For example, in a sentence, if i want to predict the third word, i can say -> Hey why not give the second word as an input to my model and given this context, let my model predict what is the next possible word. If you think about it, its like conditional probabiliy. We are calculating 
Probability of next word given the input word, for all the words in our vocabulary. Mathematically 
$P(W_{i}|W_{i-1},W_{i-2},\dots,W_{i-k})$ i.e. Probability of Word at $i^{th}$  position given Words that occurred in last k positions. 

That simple intuition there forms the base of sequence modelling. This led to models like [[RNN]] and [[LSTM]] and finally to something which is foundational today [[Transformers]] and [[Self Attention]]. 

On a high level, LSTMs are the evolution of RNNs when we figured that RNNs are not very good at taking memory into account. Primarily in cases where something in the distant past, and not immediate past, impacts the next token / pattern. Transformers take a different approach than LSTMs. Instead of maintaining a recurrent memory, they allow each element in a sequence to directly attend to other elements and decide what information matters.

Gradually we have evolved from RNN, to LSTM and to transformers, its a fricking interesting journey of how we got here and just how much we are now using these models. 

Note: We don't just predict the next word, we predict the next token, so a group of words, or in case of signals next set of signals. The token could also be a single word, based on how the token is defined for a model