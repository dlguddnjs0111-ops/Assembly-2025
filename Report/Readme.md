//Digital Systems Problems with Answers

1. In an 8-bit binary number, which is the most significant bit (MSB)?

Answer: The leftmost bit is the MSB.
Example: In 10010110, MSB = 1.

2. What is the decimal representation of each of the following unsigned binary integers?

  a. 00110101 → 53

  b. 10010110 → 150

  c. 11001100 → 204

3. What is the sum of each pair of binary integers?

  a. 10101111 + 11011011 → 1 100010010 (394 decimal)

  b. 10010111 + 11111111 → 1 10010110 (406 decimal)

  c. 01110101 + 10101100 → 1 00100001 (289 decimal)

4. Calculate binary 00001101 minus 00000111.

  Answer: 00000110 → 6 decimal

5. How many bits are used by each of the following data types?
  
  word → 16 bits

  doubleword → 32 bits

  quadword → 64 bits

  double quadword → 128 bits

6. Minimum number of binary bits to represent unsigned decimal integers:

  4095 → 12 bits

  65534 → 16 bits

  42319 → 16 bits

7. Hexadecimal representation of the following binary numbers:

  0011 0101 1101 1010 → 35DA

  1100 1110 1010 0011 → CEA3

  1111 1110 1101 1011 → FEDB

8. Binary representation of the following hexadecimal numbers:

  0126F9D4 → 00000001001001101111100111010100

  6ACDFA95 → 01101010110011011111101010010101

  F69BDC2A → 11110110100110111101110000101010

9. Unsigned decimal representation of the following hexadecimal integers:

  3A → 58

  1BF → 447

  1001 → 4097

10. Unsigned decimal representation of hexadecimal integers:

  62 → 98
  
  4B3 → 1203

  29F → 671

11. 16-bit hexadecimal representation of signed decimal integers:

  –24 → FFE8

  –331 → FEB5

12. 16-bit hexadecimal representation of signed decimal integers:

  –21 → FFEB

  –45 → FFD3

13. 16-bit hexadecimal numbers to signed decimal:

  6BF9 → 27673

  C123 → –16157

14. 16-bit hexadecimal numbers to signed decimal:

  4CD2 → 19634

  8230 → –32272

15. Decimal representation of signed binary numbers:

  10110101 → –75

  00101010 → 42

  11110000 → –16

16. Decimal representation of signed binary numbers:

  10000000 → –128

  11001100 → –52

  10110111 → –73

17. 8-bit two’s-complement binary representation of signed decimal integers:

  –5 → 11111011

  –42 → 11010110

  –16 → 11110000

18. 8-bit two’s-complement binary representation of signed decimal integers:

  –72 → 10111000

  –98 → 10011110

  –26 → 11100110

19. Sum of each pair of hexadecimal integers:

  6B4 + 3FE → A12

  A49 + 6BD → 1106

20. Sum of each pair of hexadecimal integers:

  7C4 + 3BE → B82

  B69 + 7AD → 1316

21. Hexadecimal and decimal representations of ASCII character capital B:

  Hex → 0x42, Decimal → 66

22. Hexadecimal and decimal representations of ASCII character capital G:

  Hex → 0x47, Decimal → 71

23. Challenge: Largest decimal value using 129-bit unsigned integer:

  Answer: 2¹²⁹ – 1 ≈ 6.8056 × 10³⁸

24. Challenge: Largest decimal value using 86-bit signed integer:

  Answer: 2⁸⁵ – 1 ≈ 3.8686 × 10²⁵

25. Truth table for ¬( )

  Input 0 → Output 1

  Input 1 → Output 0

26. Truth table for ( ) and relation to #25

  If using De Morgan's law: ¬(A·B) ≡ ¬A + ¬B

  Rightmost column is the negation of the AND function from question 25.

27. Boolean function with 4 inputs: rows required for truth table:

  Answer: 2⁴ = 16 rows

28. Selector bits required for 4-input multiplexer:

  Answer: 2 bits



//Algorithm Workbench (1.7.2) Problems

1. Write a function that receives a string containing a 16-bit binary integer. The function must return the string’s integer value.

Answer / Example Implementation:

public static int binaryToInt(String bin) {
    int result = 0;
    for (int i = 0; i < bin.length(); i++) {
        result = result * 2 + (bin.charAt(i) - '0');
    }
    return result;
}

// Example
binaryToInt("0001001010110101") → 4773

2. Write a function that receives a string containing a 32-bit hexadecimal integer. The function must return the string’s integer value.

Answer / Example Implementation:

public static long hexToInt(String hex) {
    long result = 0;
    for (int i = 0; i < hex.length(); i++) {
        char c = hex.charAt(i);
        int digit = (c >= '0' && c <= '9') ? c - '0' : Character.toUpperCase(c) - 'A' + 10;
        result = result * 16 + digit;
    }
    return result;
}

// Example
hexToInt("1A2B3C4D") → 439041101

3. Write a function that receives an integer. The function must return a string containing the binary representation of the integer.

Answer / Example Implementation:

public static String intToBinaryString(int n) {
    if (n == 0) return "0";
    String result = "";
    while (n > 0) {
        result = (n % 2) + result;
        n /= 2;
    }
    return result;
}

// Example
intToBinaryString(4773) → "1001010110101"

4. Write a function that receives an integer. The function must return a string containing the hexadecimal representation of the integer.

Answer / Example Implementation:

public static String intToHexString(int n) {
    if (n == 0) return "0";
    String hexChars = "0123456789ABCDEF";
    String result = "";
    while (n > 0) {
        result = hexChars.charAt(n % 16) + result;
        n /= 16;
    }
    return result;
}

// Example
intToHexString(439041101) → "1A2B3C4D"

5. Write a function that adds two digit strings in base b (up to 1000 digits). Return the sum in a string that uses the same number base.

Answer / Example Implementation:

public static String addBaseStrings(String a, String b, int base) {
    int len = Math.max(a.length(), b.length());
    StringBuilder result = new StringBuilder();
    int carry = 0;
    for (int i = 0; i < len; i++) {
        int digitA = (i < a.length()) ? Character.digit(a.charAt(a.length() - 1 - i), base) : 0;
        int digitB = (i < b.length()) ? Character.digit(b.charAt(b.length() - 1 - i), base) : 0;
        int sum = digitA + digitB + carry;
        result.insert(0, Integer.toString(sum % base, base).toUpperCase());
        carry = sum / base;
    }
    if (carry > 0) result.insert(0, Integer.toString(carry, base).toUpperCase());
    return result.toString();
}

// Example
addBaseStrings("1234", "5678", 10) → "6912"

6. Write a function that adds two hexadecimal strings (up to 1000 digits). Return the sum as a hexadecimal string.

Answer / Example Implementation:

public static String addHexStrings(String a, String b) {
    return addBaseStrings(a, b, 16);
}

// Example
addHexStrings("1A2B", "3C4D") → "566E"

7. Write a function that multiplies a single hexadecimal digit by a hexadecimal digit string (up to 1000 digits). Return a hexadecimal string.

Answer / Example Implementation:

public static String multiplyHexDigitWithString(char digitChar, String hexString) {
    int digit = Character.digit(digitChar, 16);
    int carry = 0;
    StringBuilder result = new StringBuilder();
    for (int i = hexString.length() - 1; i >= 0; i--) {
        int hexDigit = Character.digit(hexString.charAt(i), 16);
        int prod = hexDigit * digit + carry;
        result.insert(0, Integer.toHexString(prod % 16).toUpperCase());
        carry = prod / 16;
    }
    if (carry > 0) result.insert(0, Integer.toHexString(carry).toUpperCase());
    return result.toString();
}

// Example
multiplyHexDigitWithString('A', "1F") → "13E"

8. Write a Java program that contains the calculation below. Use javap –c to disassemble your code.
int Y = 5;
int X = (Y + 4) * 3;
System.out.println(X); // Output: 27

Disassembly Explanation:

bipush 5 → push 5
istore_1 → store in Y
iload_1 → load Y
iconst_4 → load 4
iadd → Y + 4
iconst_3 → load 3
imul → multiply
istore_2 → store in X
getstatic → System.out
iload_2 → load X
invokevirtual → println(X)

9. Devise a way of subtracting unsigned binary integers. Test your technique.

Answer / Example Implementation:

public static int binaryToInt(String bin) {
    int result = 0;
    for (char c : bin.toCharArray()) result = result * 2 + (c - '0');
    return result;
}

public static String intToBinaryString(int n, int length) {
    String result = "";
    while (n > 0) { result = (n % 2) + result; n /= 2; }
    while (result.length() < length) result = "0" + result;
    return result;
}

public static String subtractBinary(String a, String b) {
    int diff = binaryToInt(a) - binaryToInt(b);
    return intToBinaryString(diff, a.length());
}

// Example Tests
subtractBinary("10001000", "00000101") → "10000011"
subtractBinary("11110000", "00001111") → "11100001"
subtractBinary("10101010", "00110011") → "01110111"






















