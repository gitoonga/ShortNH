# ShortNH

The ShortNH class provides methods for encoding and decoding numbers into short, unique, and non-sequential strings. This can be useful for generating shortened URLs or for encoding ids for storage in databases.

The class defines several methods for encoding and decoding numbers. The methods make use of the BC Math library for arbitrary precision mathematics in PHP.

The base62 method takes a number as an argument and converts it into a string using a base 62 encoding. The method first initializes an empty string $key and then enters a loop that continues as long as the argument $int is greater than 0. In each iteration of the loop, the method finds the modulo of $int and 62 and converts this number into its corresponding ASCII character. The method then adds this character to the $key string. The argument $int is then divided by 62, and the loop repeats until $int is 0. The final string is then returned, reversed.

The hash method takes a number and an optional length argument and returns a unique short string encoding of the number. The method first calculates the ceiling value of 62 to the power of the length argument, then finds the closest prime number to this value. The method then multiplies the number by the prime number and finds the modulo with the ceiling value. The resulting decimal value is then encoded into a base 62 string using the base62 method and is returned, padded with zeros on the left to the specified length.

The unbase62 method takes a string encoded in base 62 and returns the decimal representation of the string. The method initializes a variable $int to 0, then loops through the characters in the reversed string and calculates the decimal value of each character using the array_search method. The decimal value is then added to $int multiplied by 62 to the power of the current iteration's index. The final value of $int is then returned.

The unhash method takes a string encoded by the hash method and returns the original decimal representation of the number. The method first calculates the length of the string, the ceiling value of 62 to the power of the length, and finds the modular multiplicative inverse of the closest prime number to the ceiling value. The method then decodes the base 62 string into a decimal using the unbase62 method, multiplies the decimal value by the modular multiplicative inverse, and takes the modulo of the product with the ceiling value. The resulting decimal value is returned.

Please note that this is not a secure hashing algorithm and is intended to create shorter strings for use in links(at-least thats why I wrote it)
