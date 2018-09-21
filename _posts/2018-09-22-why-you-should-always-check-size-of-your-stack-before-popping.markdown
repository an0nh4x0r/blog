---
title: Why you should always check size of stack before popping
layout: post
date: '2018-09-22 01:05:00 +0530'
categories: competitive-programming
---

So I was solving problems related to Stacks data structure on HackerRank.
The mistake that I was doing was popping elements from Stack before even checking that if it already
has any element in it or not.

Problems like these leads to RunTime Errors while submitted solutions on online judges.

Here is the updated code ... Now in the method ```popAndCheck()``` I've implemented condition to check
whether the stack size is greater than 0.

```
import java.util.Stack;

public class BalancedBrackets {

    private static Stack<Character> characterStack = new Stack<>();

    public static void main(String[] args) {
        String tokens = "[}}}";
//        {[()]}
//        {[(])}
//        {{[[(())]]}}
        if (processItem(tokens))
            System.out.println("OK");
        else
            System.out.println("Not OK");
    }

    public static boolean processItem(String tokens) {
        if (checkCloseBracketInitially(tokens.charAt(0))) {
            return false;
        }
        for (int i = 0; i < tokens.length(); ++i) {
            if (isOpenItem(tokens.charAt(i)))
                characterStack.push(tokens.charAt(i));
            else {
                // pop stack and check if it's actually the opening bracket corresponding to the closing bracket
                if (!popAndCheck(tokens.charAt(i))) {
                    return false;
                }
            }
        }
        return characterStack.isEmpty();
    }

    public static boolean isOpenItem(Character character) {
        if (character == '{' || character == '[' || character == '(') {
            return true;
        } else {
            return false;
        }
    }

    public static boolean popAndCheck(Character closingBracket) {
        if (characterStack.size() > 0) {
            char poppedCharacter = characterStack.pop();
            return ((poppedCharacter == '{' && closingBracket == '}')
                    || (poppedCharacter == '[' && closingBracket == ']')
                    || (poppedCharacter == '(' && closingBracket == ')'));
        }
        return false;
    }

    public static boolean checkCloseBracketInitially(Character character) {
        return (character == '}' || character == ']' || character == ')');
    }

}
```

{% include disqus.html %}