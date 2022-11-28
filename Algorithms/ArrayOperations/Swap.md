# Swap 2 elements in an array (Java)

```java
public static char[] swap(char[] arr, int i, int j) {
	char tmp = arr[i];
	arr[i] = arr[j];
	arr[j] = tmp;
	
	return arr;
}
```


