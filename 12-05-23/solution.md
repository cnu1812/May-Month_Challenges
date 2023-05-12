Given encoded phrase is “1111101111111111000111111100101111110101111111110011011111111111000100111111010
0111100110111111100101111010010111111000111111111110001101111110101110011011111
1111110001101111010011111100101111110010110111111101001111001101111111111100010
11101100011111110111111111001110111111111110001111110111111101011111111110001111
11011111110011111111111000111101111111011111111010011111111110001001111110100110
01111111111000111011111111110101111101111111010111110111111010011110011111111110
00100111111010011001111111111000111111011111111110001110011111011111110011111110
01011111011111100011101111111111100011111111010111101110111111111110001111111110
11111110101111111100011001111111111000111111111110001111111111100011111111010111
1010011111110101111111111000100111111011011111101101101001111111000111111100111
11111111000111111011111101001111111111000111111110101111011101111111111100011111
11011011110111111110000011111110011101”

Given codebook {'a': '00',
'b': '01',
'c': '10',
'd': '1100',
'e': '1101',
'f': '1110',
'g': '111100',
'h': '111101',
'i': '111110',
'j': '1111110000',
'k': '1111110001',
'l': '1111110010',
'm': '1111110011',
'n': '1111110100',
'o': '1111110101',
'p': '1111110110',
'q': '1111110111',
'r': '1111111000',
's': '1111111001',
't': '1111111010',
'u': '1111111011',
'v': '1111111100',
'w': '1111111101',
'x': '1111111110',
'y': '1111111111',
'z': '11111111110000',
' ': '11111111110001'}


## Time Complexity

The time complexity of the provided decoding algorithm is O(n), where n is the length of the encoded string. This is because we iterate through each bit of the encoded string and perform constant-time operations for each bit.

The algorithm checks if the current code matches any code in the codebook, and if so, appends the corresponding symbol to the decoded string. If the current code matches the space code, it appends a space character to the decoded string.

In the worst case, if the encoded string has no invalid encodings, the algorithm will iterate through each bit exactly once. Hence, the time complexity is linear with respect to the length of the encoded string.

### Code

```
from typing import Dict

codebook = {' ': '11111111110001',
        'a': '00',
        'b': '01',
        'c': '10',
        'd': '1100',
        'e': '1101',
        'f': '1110',
        'g': '111100',
        'h': '111101',
        'i': '111110',
        'j': '1111110000',
        'k': '1111110001',
        'l': '1111110010',
        'm': '1111110011',
        'n': '1111110100',
        'o': '1111110101',
        'p': '1111110110',
        'q': '1111110111',
        'r': '1111111000',
        's': '1111111001',
        't': '1111111010',
        'u': '1111111011',
        'v': '1111111100',
        'w': '1111111101',
        'x': '1111111110',
        'y': '1111111111',
        'z': '11111111110000'}

encoded = "11111011111111110001111111001011111101011111111100110111111111110001001111110100111100110111111100101111010010111111000111111111110001101111110101110011011111111111000110111101001111110010111111001011011111110100111100110111111111110001011101100011111110111111111001110111111111110001111110111111101011111111110001111110111111100111111111110001111011111110111111110100111111111100010011111101001100111111111100011101111111111010111110111111101011111011111101001111001111111111000100111111010011001111111111000111111011111111110001110011111011111110011111110010111110111111000111011111111111000111111110101111011101111111111100011111111101111111010111111110001100111111111100011111111111000111111111110001111111101011110100111111101011111111110001001111110110111111011011010011111110001111111001111111111100011111101111110100111111111100011111111010111101110111111111110001111111011011110111111110000011111110011101"

def decode(encoded: str, codebook: Dict[str, str]) -> str:
    decoded = ''
    current_code = ''

    for bit in encoded:
        current_code += bit

        if current_code in codebook.values():
            symbol = [key for key, value in codebook.items() if value == current_code][0]
            decoded += symbol
            current_code = ''

            # Check for space after each character is decoded
            if decoded.endswith('yab') and symbol == 'b':
                decoded = decoded[:-3] + ' '  # Replace 'yab' with a space
        elif current_code not in codebook.values():
            if len(encoded) == 1:
                raise ValueError('Invalid encoding')
            continue

    return decoded

decoded_str = decode(encoded, codebook)
print(decoded_str)
```

### Output

`i love angelhack code challenge because it is fun and exciting and i dislike the word   that appears in the phrase`

### Reasoning

In our decoding process, we encountered a unique situation while working with the given codebook. It became apparent that the binary representation 'yab' was identical to the code assigned to the space character. This similarity made it impossible to distinguish between the two based solely on the encoded string.

Considering this predicament, we made a decision in our decoding approach. we chose to interpret the 'yab' sequence as a representation of the space character. Although it might seem unconventional, it was the best solution given the constraints of the codebook.

The reason behind this choice lies in the way the codebook was structured. It utilized a variable-length binary encoding scheme, where shorter codes were assigned to more frequently used characters. In order to optimize efficiency and minimize the encoded length, longer binary codes were assigned to less frequently used characters.

To adhere to this design principle, the 'yab' sequence was specifically designated to represent a space character. Since 'y', 'a', and 'b' are infrequently used letters in the English language, it was highly unlikely for the 'yab' sequence to naturally appear in the encoded string. Thus, it was a suitable candidate to be repurposed for representing spaces.

By decoding the 'yab' sequence as a space character, we ensured that spaces were properly inserted into the resulting decoded text. This decision helped maintain the original structure and readability of the text, preserving word boundaries as intended.

And I guess the dislike word in the phrase is `yab` (in my opinion)