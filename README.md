class Solution:
    def isBalanced(self, s):
        # Use a list as a stack
        stack = []
        
        # Dictionary to store the pairs for quick lookup
        bracket_map = {')': '(', '}': '{', ']': '['}
        
        for char in s:
            # If the character is a closing bracket
            if char in bracket_map:
                # Pop the top element if stack is not empty
                if not stack:
                    return False
                
                top_element = stack.pop()
                
                # Check if the popped opening bracket matches the current closing one
                if bracket_map[char] != top_element:
                    return False
            else:
                # It is an opening bracket, push it onto the stack
                stack.append(char)
        
        # The expression is balanced only if the stack is empty at the end
        return len(stack) == 0
