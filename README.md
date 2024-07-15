Given 2 strings A and B, print all the interleavings of the 2 strings. An interleaved string of given two strings preserves the order of characters in individual strings and uses all the characters of both the strings. For simplicity, you can assume that the strings have unique characters.

Input Format

First line of input contains T - number of test cases. Its followed by T lines, each contains 2 space separated strings A and B.

Constraints

1 <= T <= 100
'a' <= A[i], B[i] <= 'z'
1 <= len(A), len(B) <= 10

Output Format

For each test case, print the test case number, followed by the interleavings of the 2 strings in a sorted order, separated by newline.

Inputcopy	Outputcopy
2
nkb gl
bn zh
Case #1:
glnkb
gnkbl
gnklb
gnlkb
ngkbl
ngklb
nglkb
nkbgl
nkgbl
nkglb
Case #2:
bnzh
bzhn
bznh
zbhn
zbnh
zhbn
# Interleavings 
def generate_interleavings(A, B):
    result = []
    def backtrack(current, i, j):
        if i == len(A) and j == len(B):
            result.append(current)
            return
        if i < len(A):
            backtrack(current + A[i], i + 1, j)
        if j < len(B):
            backtrack(current + B[j], i, j + 1)
    backtrack("", 0, 0)
    return sorted(result)
if __name__ == "__main__":
    import sys
    input = sys.stdin.read().strip().split("\n")
    T = int(input[0])
    case_number = 1
    index = 1
    while index < len(input):
        A, B = input[index].split()
        index += 1
        interleavings = generate_interleavings(A, B)
        print(f"Case #{case_number}:")
        for interleaving in interleavings:
            print(interleaving)
        case_number += 1
