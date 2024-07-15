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
