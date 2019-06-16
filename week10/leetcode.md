
### 20. Valid Parentheses

Question:
```
Given a string containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.
Note that an empty string is also considered valid.
```

Solution:
```
public boolean isValid(String s) {
        HashMap<Character, Character> mapping = new HashMap<>();
        mapping.put('}', '{');
        mapping.put(')', '(');
        mapping.put(']', '[');
        Stack<Character> stack = new Stack<>();
        for (int i = 0; i < s.length(); i++){
            Character c = s.charAt(i);
            if (mapping.containsKey(c)){
                if (stack.isEmpty()){
                    return false;
                }
                Character co = stack.pop();
                if (!co.equals(mapping.get(c))){
                    return false;
                }
            } else{
                stack.add(c);
            }
        }
        return stack.isEmpty();
    }
```
Note:  
