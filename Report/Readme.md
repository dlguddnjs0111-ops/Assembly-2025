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

1. In 32-bit mode, aside from the stack pointer (ESP), what other register points to variables on the stack?
👉 Answer: EBP (Base Pointer)
Explanation: EBP는 현재 함수의 스택 프레임 기준 주소를 가리키며, 지역 변수나 매개변수 접근에 사용됨.

2. Name at least four CPU status flags.
👉 Answer: CF (Carry Flag), ZF (Zero Flag), SF (Sign Flag), OF (Overflow Flag)
Explanation: 산술 연산 결과의 상태를 나타냄.

3. Which flag is set when the result of an unsigned arithmetic operation is too large to fit into the destination?
👉 Answer: Carry Flag (CF)

4. Which flag is set when the result of a signed arithmetic operation is either too large or too small to fit into the destination?
👉 Answer: Overflow Flag (OF)

5. (True/False): When a register operand size is 32 bits and the REX prefix is used, the R8D register is available for programs to use.
👉 Answer: True
Explanation: REX prefix는 64비트 모드에서 추가 레지스터(R8~R15)를 활성화함.

6. Which flag is set when an arithmetic or logical operation generates a negative result?
👉 Answer: Sign Flag (SF)

7. Which part of the CPU performs floating-point arithmetic?
👉 Answer: Floating Point Unit (FPU)
(= Numeric Coprocessor, x87 FPU)

8. On a 32-bit processor, how many bits are contained in each floating-point data register?
👉 Answer: 80 bits
Explanation: x87 FPU 레지스터는 80비트 확장 정밀도 형식 사용.

9. (True/False): The x86-64 instruction set is backward-compatible with the x86 instruction set.
👉 Answer: True

10. (True/False): In current 64-bit chip implementations, all 64 bits are used for addressing.
👉 Answer: False
Explanation: 현재는 실제로 48비트(또는 52비트 등)만 주소로 사용함.

11. (True/False): The Itanium instruction set is completely different from the x86 instruction set.
👉 Answer: True
Explanation: Itanium(IA-64)은 x86과 호환되지 않음.

12. (True/False): Static RAM is usually less expensive than dynamic RAM.
👉 Answer: False
Explanation: SRAM은 DRAM보다 훨씬 빠르지만 비쌈.

13. (True/False): The 64-bit RDI register is available when the REX prefix is used.
👉 Answer: True

14. (True/False): In native 64-bit mode, you can use 16-bit real mode, but not the virtual-8086 mode.
👉 Answer: True
Explanation: 64비트 모드에서는 Real Mode 전환 가능하지만 V8086 모드는 불가.

15. (True/False): The x86-64 processors have 4 more general-purpose registers than the x86 processors.
👉 Answer: False
Explanation: 8개 더 있음 (EAX~EDI + R8~R15 → 총 16개).

16. (True/False): The 64-bit version of Microsoft Windows does not support virtual-8086 mode.
👉 Answer: True

17. (True/False): DRAM can only be erased using ultraviolet light.
👉 Answer: False
Explanation: 그건 EPROM이고, DRAM은 주기적 리프레시 필요.

18. (True/False): In 64-bit mode, you can use up to eight floating-point registers.
👉 Answer: False
Explanation: x64에서는 SSE(XMM) 레지스터로 16개 사용 가능.

19. (True/False): A bus is a plastic cable that is attached to the motherboard at both ends, but does not sit directly on the motherboard.
👉 Answer: False
Explanation: 버스는 신호선 집합으로, 데이터 전송용 전자 회로.

20. (True/False): CMOS RAM is the same as static RAM, meaning that it holds its value without any extra power or refresh cycles.
👉 Answer: False
Explanation: CMOS RAM은 유지 전력(배터리)이 필요함.

21. (True/False): PCI connectors are used for graphics cards and sound cards.
👉 Answer: True

22. (True/False): The 8259A is a controller that handles external interrupts from hardware devices.
👉 Answer: True
Explanation: 8259A = Programmable Interrupt Controller (PIC)

23. (True/False): The acronym PCI stands for programmable component interface.
👉 Answer: False
Explanation: PCI = Peripheral Component Interconnect

24. (True/False): VRAM stands for virtual random access memory.
👉 Answer: False
Explanation: VRAM = Video Random Access Memory

25. At which level(s) can an assembly language program manipulate input/output?
👉 Answer: Hardware level and Operating System level
Explanation: 포트 접근(in/out 명령) 또는 OS API를 통해 I/O 제어 가능.

26. Why do game programs often send their sound output directly to the sound card’s hardware ports?
👉 Answer: To reduce latency and improve performance
Explanation: OS를 거치면 지연이 생기므로, 하드웨어 직접 접근이 더 빠름.

🧩 1. Provide examples of three different instruction mnemonics.

Answer: MOV, ADD, SUB
Explanation: Mnemonic은 CPU 명령어를 사람이 읽을 수 있도록 표현한 약어임.

🧩 2. What is a calling convention, and how is it used in assembly language declarations?

Answer:
A calling convention defines how functions receive parameters and return values — for example, which registers or stack locations are used.
Explanation: Assembly에서는 함수 호출 시 PROTO나 INVOKE에서 호출 규약(stdcall, cdecl 등)을 지정함.

🧩 3. How do you reserve space for the stack in a program?

Answer:
By setting a stack segment size or using a stack directive such as:

.stack 4096


This reserves 4096 bytes for the stack.

🧩 4. Explain why the term assembler language is not quite correct.

Answer:
Because the assembler is a program, while the language is properly called assembly language.

🧩 5. Explain the difference between big endian and little endian.

Answer:

Little endian: Least significant byte stored first (lowest address).

Big endian: Most significant byte stored first.
Origin: The term comes from Gulliver’s Travels, where people argued about which end of an egg to break first (“big-endians” vs. “little-endians”).

🧩 6. Why might you use a symbolic constant rather than an integer literal in your code?

Answer:
To make the code easier to read and maintain. You can change the constant’s value in one place instead of updating every occurrence.

🧩 7. How is a source file different from a listing file?

Answer:

Source file: contains only the code written by the programmer (.asm).

Listing file: includes the original source plus addresses, opcodes, and symbol tables produced by the assembler (.lst).

🧩 8. How are data labels and code labels different?

Answer:

Data labels: identify memory locations for variables.

Code labels: identify locations in the instruction stream (used for jumps, loops, etc.).

🧩 9. (True/False): An identifier cannot begin with a numeric digit.

✅ True

🧩 10. (True/False): A hexadecimal literal may be written as 0x3A.

✅ True (MASM also allows 3Ah format.)

🧩 11. (True/False): Assembly language directives execute at runtime.

❌ False
Directives are processed by the assembler before runtime.

🧩 12. (True/False): Assembly language directives can be written in any combination of uppercase and lowercase letters.

✅ True

🧩 13. Name the four basic parts of an assembly language instruction.

Answer:

Label

Mnemonic

Operand(s)

Comment

🧩 14. (True/False): MOV is an example of an instruction mnemonic.

✅ True

🧩 15. (True/False): A code label is followed by a colon (:), but a data label does not end with a colon.

✅ True

🧩 16. Show an example of a block comment.
COMMENT !
This is a block comment.
It can span multiple lines.
!

🧩 17. Why is it not a good idea to use numeric addresses when writing instructions that access variables?

Answer:
Because addresses can change when code is modified or relocated; labels are safer and more readable.

🧩 18. What type of argument must be passed to the ExitProcess procedure?

Answer:
A 32-bit integer (DWORD) exit code.

🧩 19. Which directive ends a procedure?

Answer:
ENDP

🧩 20. In 32-bit mode, what is the purpose of the identifier in the END directive?

Answer:
It tells the assembler the entry point of the program (usually the main procedure).

Example:

END main

🧩 21. What is the purpose of the PROTO directive?

Answer:
Declares the prototype of an external procedure before it is called with INVOKE.

🧩 22. (True/False): An Object file is produced by the Linker.

❌ False
It’s produced by the Assembler.

🧩 23. (True/False): A Listing file is produced by the Assembler.

✅ True

🧩 24. (True/False): A link library is added to a program just before producing an Executable file.

✅ True

🧩 25. Which data directive creates a 32-bit signed integer variable?

Answer: SDWORD

🧩 26. Which data directive creates a 16-bit signed integer variable?

Answer: SWORD

🧩 27. Which data directive creates a 64-bit unsigned integer variable?

Answer: QWORD

🧩 28. Which data directive creates an 8-bit signed integer variable?

Answer: SBYTE

🧩 29. Which data directive creates a 10-byte packed BCD variable?

Answer: TBYTE (Ten bytes = 80 bits)

🧮 Additional Questions (Data Definition Practice)
1️⃣ Define four symbolic constants that represent integer 25 in decimal, binary, octal, and hexadecimal.
DEC25  EQU 25
BIN25  EQU 11001b
OCT25  EQU 31o
HEX25  EQU 19h

2️⃣ Can a program have multiple code and data segments?

Answer:
Yes, but only one can be active at a time. Multiple segments are allowed logically, but not simultaneously used without switching.

3️⃣ Create a data definition for a doubleword stored in memory in big endian format.
myData BYTE 12h, 34h, 56h, 78h   ; Big endian order

4️⃣ Can you declare a variable of type DWORD and assign it a negative value?

Answer:
Yes — the assembler stores the two’s complement representation.
This shows that the assembler does not enforce strict type checking.

5️⃣ Compare machine code: ADD EAX,5 vs. ADD EDX,5

Answer:
Both have similar opcodes, but the register encoding bits differ (EAX = 000, EDX = 010).
Machine code will differ in one byte.

6️⃣ Given the number 456789ABh, list its bytes in little-endian order.

Answer: AB 89 67 45

7️⃣ Declare an array of 120 uninitialized unsigned doubleword values.
array DWORD 120 DUP(?)

8️⃣ Declare an array of bytes initialized to the first 5 letters of the alphabet.
letters BYTE 'A','B','C','D','E'

9️⃣ Declare a 32-bit signed integer variable with the smallest possible negative decimal value.
minInt SDWORD -2147483648

🔟 Declare an unsigned 16-bit integer array named wArray with three initializers.
wArray WORD 1000, 2000, 3000

11️⃣ Declare a string variable containing the name of your favorite color (null-terminated).
colorName BYTE "Blue", 0

12️⃣ Declare an uninitialized array of 50 signed doublewords named dArray.
dArray SDWORD 50 DUP(?)

13️⃣ Declare a string variable containing the word “TEST” repeated 500 times.
bigStr BYTE 500 DUP("TEST")

14️⃣ Declare an array of 20 unsigned bytes named bArray and initialize all elements to zero.
bArray BYTE 20 DUP(0)

15️⃣ Show the order of bytes in memory (lowest → highest) for a doubleword variable:

Example:

val DWORD 12345678h


Memory order (little endian): 78 56 34 12

1. Which instruction pushes all 32-bit general-purpose registers on the stack?
PUSHAD (32-bit MASM/IA-32) — EAX, ECX, EDX, EBX, ESP, EBP, ESI, EDI를 순서대로 푸시.

2. Which instruction pushes the 32-bit EFLAGS register on the stack?
PUSHFD (또는 PUSHF의 32-bit 버전)

3. Which instruction pops the stack into the EFLAGS register?
POPFD (또는 POPF의 32-bit 버전)

4. Challenge — NASM permitting PUSH EAX EBX ECX: why might this be better than PUSHAD?

NASM의 다중 레지스터 PUSH는 명시적으로 어떤 레지스터들만 푸시하는지 보여주므로 불필요한 레지스터(예: ESP)까지 푸시하는 PUSHAD보다 안전하고 효율적이다.

PUSHAD는 항상 고정된 순서와 모든 GPR을 푸시하므로 레지스터 일부만 보존하면 될 때 불필요한 메모리/시간 낭비가 생긴다.

결론: 선택적이고 최소한의 저장을 허용하므로 더 효율적이고 명확함.

5. Challenge — If no PUSH existed, give two instructions to mimic push eax.

sub esp, 4
mov [esp], eax


6. (T/F) RET pops the top of the stack into the instruction pointer.
True. RET pops the return address from the stack and jumps to it (실제론 EIP/RIP에 값을 로드).

7. (T/F) Nested procedure calls are not permitted by MASM unless the NESTED operator is used.
False. 일반적인 중첩 호출은 추가 키워드 없이 허용된다. (NESTED는 특정 컴파일러/옵션용 문법일 뿐).

8. (T/F) In protected mode, each procedure call uses a minimum of 4 bytes of stack space.
True. CALL 명령은 리턴 주소(32-bit)를 스택에 푸시하므로 최소 4바이트 사용(32-bit 환경 기준).

9. (T/F) The ESI and EDI registers cannot be used when passing 32-bit parameters to procedures.
False. ESI/EDI도 일반 레지스터이며 파라미터 전달에 사용할 수 있다(약속(conventions)에 따라 다름).

10. (T/F) The ArraySum procedure (Sec.5.2.5) receives a pointer to any array of doublewords.
True. (책의 기술대로라면 ArraySum은 doubleword(32-bit) 배열의 포인터를 받음.)

11. (T/F) The USES operator lets you name all registers that are modified within a procedure.
True. USES에 나열한 레지스터들을 보존하기 위해 컴파일러가 함수 진입/복귀 시 PUSH/POP을 생성한다.

12. (T/F) The USES operator only generates PUSH instructions, so you must code POP yourself.
False. MASM의 USES는 자동으로 진입부에 PUSH, 복귀부에 POP을 생성한다(즉, 양쪽을 처리함).

13. (T/F) The register list in the USES directive must use commas to separate register names.
False. MASM의 USES 보통은 공백으로 구분 (USES eax ebx ecx) — (버전/문법에 따라 다를 수 있지만 일반적 관행은 공백).

14. Which statement(s) in ArraySum must be modified to sum 16-bit words? Create such a version.

바꿔야 할 점:

인덱스 증가량(기본이 4바이트 → 2바이트)

배열 엘리먼트 읽기 시 movzx/movsx로 16비트 값을 적절히 32비트로 확장

누적 변수(합)는 32비트(DWORD)로 유지하는 것이 안전

MASM-style pseudocode (ArraySum for WORDs):

; Params: ESI -> pointer to array, ECX -> count (number of words)
; Returns: EAX = sum (32-bit)
ArraySumWords PROC
    push ebp
    mov  ebp, esp
    push esi       ; save if needed
    xor  eax, eax  ; sum = 0
    xor  edx, edx  ; index offset or temp

loop_start:
    cmp  ecx, 0
    je   loop_end

    ; load word and zero-extend to dword
    mov  dx, [esi]      ; dx = word
    movzx edx, dx       ; edx = zero-extended word
    add  eax, edx

    add  esi, 2         ; advance by 2 bytes for WORD array
    dec  ecx
    jmp  loop_start

loop_end:
    pop  esi
    mov  esp, ebp
    pop  ebp
    ret
ArraySumWords ENDP


(테스트 방법) 간단히 WORD array를 선언하고 ECX=count, ESI=OFFSET array로 호출하면 됨.

15. What will be final value in EAX after:

push 5
push 6
pop  eax
pop  eax


동작: pop eax → 6, 다음 pop eax → 5.

최종 EAX = 5.

16. Which statement is true for the code (push 10; push 20; call Ex2Sub; Ex2Sub: pop eax; ret): choices a–d?

실행 시 문제: call이 리턴주소를 푸시한 뒤 Ex2Sub가 pop eax를 수행하면 리턴주소가 EAX로 들어감. 이후 ret은 스택에서 다음 값을 꺼내서 EIP로 사용(이 값은 push 20으로 넣은 20이므로 잘못된 주소로 점프) — 결국 ret에서 잘못된 점프로 런타임 에러 발생.

정답: (d) The program will halt with a runtime error on Line 11 (the ret).

17. Which statement is true for code with pusha / popa (mov eax,30; push eax; push 40; call Ex3Sub; Ex3Sub: pusha; mov eax,80; popa; ret)?

흐름: main에서 EAX=30, push 30, push 40, call → Ex3Sub 진입 시 EAX=30. pusha는 EAX(=30)를 스택에 저장. mov eax,80으로 바꾼 뒤 popa는 pusha에 의해 저장된 레지스터들을 복원하고, EAX는 다시 30으로 돌아감. 정상 반환.

정답: (c) EAX will equal 30 on line 6 (i.e. after return).

18. Which statement is true for code using push offset Here then jmp Ex4Sub and Ex4Sub just ret?

흐름: push offset Here는 스택에 반환주소(라벨 Here)를 넣고 jmp Ex4Sub로 이동. Ex4Sub가 ret을 실행하면 스택에서 그 주소(Here)를 꺼내어 점프 → Here 코드 실행 (mov eax,30). 따라서 mov eax,30 실행됨.

정답: (a) EAX will equal 30 on line 7.

19. Which statement is true for code where Ex5Sub does pop eax ... pop edx; push eax; ret and main pushed eax=40 then called Ex5Sub?

시뮬레이션: main pushes 40 then call(리턴주소 푸시). Ex5Sub 첫 pop eax → 리턴주소가 eax로 들어감. 그 뒤 pop edx → 40이 edx로 들어감. push eax로 리턴주소를 다시 스택에 올려서 ret이 정상 동작. 결과: EDX = 40.

정답: (a) EDX will equal 40 on line 6.

20. What values will be written to array DWORD 4 DUP(0) by given nested calls?

시뮬레이션 결과 (초기 eax=10, esi=0):

proc_3 writes array[0] = 10

proc_2 then writes array[1] = 20

proc_1 then writes array[2] = 30

main after returning writes array[3] = 40

결과: array = {10, 20, 30, 40}

Algorithm Workbench (추가 연습문제) — answers & code snippets

1. Exchange EAX and EBX using only PUSH/POP.

; initial: EAX = a, EBX = b
push eax
push ebx
pop  eax    ; eax := b
pop  ebx    ; ebx := a
; now EAX=b, EBX=a


2. Make subroutine return to an address 3 bytes higher than the current return address.
(서브루틴의 RET 바로 전에)

add dword ptr [esp], 3   ; 스택에 있는 return address에 3을 더함
ret


설명: [esp]는 현재 스택의 return address(32-bit) 위치.

3. Reserve space for two doubleword locals and assign 1000h/2000h.

; at subroutine entry
sub esp, 8            ; 공간 8바이트(두 개의 DWORD) 확보
mov dword ptr [esp], 0x1000
mov dword ptr [esp+4], 0x2000
; ... use locals ...
add esp, 8            ; 복귀 전 원래대로
ret


4. Copy element in dword array to previous position (indexed addressing).
(예: array base in EDI, index in ECX — copy element ECX to ECX-1)

mov eax, dword ptr [edi + ecx*4]      ; eax := array[ecx]
mov dword ptr [edi + ecx*4 - 4], eax  ; array[ecx-1] := eax


또는 만약 ESI가 바이트 오프셋이면:

mov eax, [array + esi]        ; 읽어오기
mov [array + esi - 4], eax    ; 이전 슬롯에 쓰기


5. Display a subroutine’s return address without preventing normal return.

리턴 주소는 서브루틴 진입 시 [esp]에 있다(32-bit). 안전하게 복사해서 출력하고 스택은 건드리지 않으면 됨:

mov  eax, [esp]      ; EAX := return address (do not POP it)
; -- now call some display routine that uses/preserves EAX or we save it --
push eax
call DisplayHex     ; example: displays hex value on console
add  esp, 4
; continue and ret normally
ret


또는 레지스터에 복사한 뒤(예: mov ebx, [esp]) 출력 루틴에 전달해도 됨. 핵심은 [esp]를 pop 하지 않는 것.
















