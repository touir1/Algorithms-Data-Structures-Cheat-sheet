# Reverse elements in array (Java)

```java
public static char[] reverse(char[] arr, int begin, int end) {
	while(begin < end) {
		char tmp = arr[begin];
		arr[begin++] = arr[end];
		arr[end--] = tmp;
	}
	
	return arr;
}
```


