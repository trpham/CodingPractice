# Longest Absolute File Path

Suppose we abstract our file system by a string in the following manner:

The string `"dir\n\tsubdir1\n\tsubdir2\n\t\tfile.txt" `represents:

```
dir 
    subdir1 
    subdir2 
        file.ext
```

- Directory `dir` contains `subdir1` and `subdir2` 
- subdir2 contains `file.txt`.

The string `"dir\n\tsubdir1\n\t\tfile1.txt\n\t\tsubsubdir1\n\tsubdir2\n\t\tsubsubdir2\n\t\t\tfile2.txt"` represents:

```
dir 
    subdir1 
        file1.txt 
        subsubdir1 
    subdir2 
        subsubdir2 
            file2.txt
```

- Directory `dir` contains `subdir1` and `subdir2`. 
- `subdir1` contains `file1.txt` and an empty `subsubdir1`.
- `subdir2` contains subsubdir2 
- `subsubdir2` contains `file2.txt`.
- The longest absolute path is `"dir/subdir2/subsubdir2/file2.txt"`, and its length is 32 (not including the double quotes)


Find the **longest (number of characters) absolute path** to a file within our file system. 

**Ideas**:

- The name of a file contains at least a . and an extension.
- Time complexity is O(n) where n is the size of the input string.
- `a/aa/file1.txt` is not the longest file path, if there is another path `aaaaaaaa/file2.txt`.
- Seperate each file/sub-directory by '\n'. Keep track of **how deep** (**level**) that the file/sub-directory lies on by counting how many `'\t'` upfront. 
- Reach the end of a file path when seeing a dot (e.g: xyz.txt).

```java
public int lengthLongestPath(String path) {

    // Map each level in the directory to the length 
    // up to that level. Level 0, length 0.
    Map<Integer, Integer> m = new HashMap<>();
    m.put(0,0);

    String[] arr = path.split("\n");
    int res = 0;

    for (String s: arr) {     
        // If s is:'\tAB', last index of '\t' is 1 -> AB at level 2.
        int level = s.lastIndexOf("\t") + 1;
        int lenLevel = m.get(level);
        int lenS = s.substring(level).length();
        int len = lenLevel + lenS;
        
        if (!s.contains(".")) {
            // len + 1 because extra "/" in between each level
            m.put(level + 1, len + 1);
        } else {
            // End of a file's path, calculate max len
            res = Math.max(res, len);
        }
    }

    return res;
}


```














