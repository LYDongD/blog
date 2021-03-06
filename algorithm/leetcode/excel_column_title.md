## Excel Sheet Column Title

### 问题

```
Given a positive integer, return its corresponding column title as appear in an Excel sheet.

For example:

    1 -> A
    2 -> B
    3 -> C
    ...
    26 -> Z
    27 -> AA
    28 -> AB 
    ...
    
Example 1:
Input: 1
Output: "A"

Example 2:
Input: 28
Output: "AB"

Example 3:
Input: 701
Output: "ZY"

```

### 思路

* 相当于10进制转26进制
* 求模取位，然后更新基数
* 由于映射关系是从1开始，每次求模前基数-1


```

public String convertToTitle(int n) {

    String charTable = "ABCDEFGHIJKLMNOPQRSTUVWXYZ";

    StringBuilder result = new StringBuilder();

    while (n > 0){
        n--;
        result.insert(0, charTable.charAt(n % 26));
        n = n / 26;
    }

    return result.toString();
}

```