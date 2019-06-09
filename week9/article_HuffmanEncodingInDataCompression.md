
Compression is useful when we try to cram more things onto a disk or to shorten the time needed to send a file over a network. Without using compression, we often encode file with one of Dozens of encoding methods, like UTF-8、UTF-16、GBK. Just to simplify, we choose the standard ASCII encoding for comparison, then we will introduce the variable-length encoding, which can be implemented by our discussing topic, the Huffman encoding.
We use a particular string `abanana_` as our experimental sample. 
#### ASCII Encoding
ASCII Encoding represents the string by simply replacing each character with its responding ASCII number.

|char|ASCII|Binary|
|--|--|--|
|a|97|01100001|
|space|32|0010000|
|b|98|01100010|
|_|95|01011111|

from above table, we generate the ASCII encoding result of `abanana `:
`01100001|01100010|01100001|01101110|01100001|01101110|01100001|01011111`(no `|` in real storage), which requires 64 bits.

#### fixed-length encoding 
As you know, the 256 different characters of ASCII table are all popular characters, and in order to distinguish these characters, we need 8 bits to represent one ASCII character. The string `abanana_` requires `8 * 8 = 64` bits. There're only three different characters, what if we use 2 bits for each character starting from 0 instead of 8 bits in the ASCII table? The following table describes the encoding details:
|char|ASCII|Binary|
|--|--|--|
|a|0|00|
|b|1|01|
|n|2|10|
|_|3|11|
The compression result is `00|01|00|10|00|10|00|11`. the total bits needed for `abanana_` are `8 * 2 = 16` bits, compressing to 25% of its original size.  There is one thing to note, we also need a mapping of the original character with its `2bits` encoding. 

#### A variable-length encoding
The above compression gets a compressing rate of 75%, it's quite effective. However, the string `abanana ` is just a experimental example, string or file in real world is much more complicated. It probably consist of a lot of different characters, may be more than 64, so the compression will degenerate to the ASCII encoding and the compression is no compression.
What if we drop the requirement that all characters takes up the same number of bits? For `abanana_`, we encode `a` and `n` with fewer bits, encode `b` and `_` with more bits. 
Again, the encoding table:
|char|Binary|
|--|--|
|a|0|
|b|110|
|n|10|
|_|111|
The encoding result is `0|110|0|10|0|10|0|111` and its size is 14 bits, less than the fixed-length encoding. You might wonder how we decode the encoding result to get the original string if we don't know how to seperate the result string by character? I understand what you are concerned. But if you look at the above table carefully, you will see that there is no binary code of a character is another character's prefix. So the decoding result can only be unique. 

#### Huffman codes
So how we generate variable-length encoding binary codes of each character? as we know, they are unique and have prefix property, we can plot them onto a binary tree. Each character is stored at a leaf node, left-going edge represents a 0 and right-going edge represents a 1, and the path from the root to a leaf node is the encoding result of a character. 
How we generate the tree? it's what Huffman algorithm doing.
Huffman algorithm is an example of a greedy algorithm. Huffman codes have been greatly used for data compression, mainly distributed to its convenience and effectiveness.

#### References
[Entropy in Compression - Computerphile - Youtube](https://www.youtube.com/watch?v=M5c_RFKVkko)
[stanford Huffman Encoding](https://web.stanford.edu/class/archive/cs/cs106b/cs106b.1126/handouts/220%20Huffman%20Encoding.pdf)








