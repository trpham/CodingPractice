# Letter Combinations of a Phone Number
------------

Given a digit string, return all possible letter combinations that the number could represent.

**Ideas**:

- "23" -> ["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"].
- DFS

```java

public List < String > letterCombinations(String digits) {

	List <String> res = new LinkedList < >();
	if (digits.length() < 1) {
		return res;
	}

	HashMap <Character, String > map = new HashMap < >();
	map.put('2', "abc");
	map.put('3', "def");
	map.put('4', "ghi");
	map.put('5', "jkl");
	map.put('6', "mno");
	map.put('7', "pqrs");
	map.put('8', "tuv");
	map.put('9', "wxyz");

	StringBuilder sb = new StringBuilder();
	dfs(digits, 0, sb, map, res);
	return res;
}

public void dfs(String digits, int n, StringBuilder sb, HashMap < Character, String > map, List < String > result) {

	if (n == digits.length()) {
		result.add(sb.toString());
		return;
	}

	char curr = digits.charAt(n);
	String s = map.get(curr);

	for (char c: s.toCharArray()) {
		sb.append(c);
		dfs(digits, n + 1, sb, map, result);
		sb.deleteCharAt(sb.length() - 1);
	}
}

```



