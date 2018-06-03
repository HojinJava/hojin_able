## FrogRiverOne
~~~java
public class Test {
	static public void main(String args[]) {
		int A[] = { 1, 3, 1, 4, 2, 3, 5, 4 };
		System.out.println(new Test().solution(5, A));
	}

	public int solution(int X, int[] A) {
		return this.test(X, A);
	}

	public int test(int goal, int[] array) {
		int resutlInt = 0;
		int lastIndex = 0;
		int[] checkAr = new int[array.length];
		checkAr[0] = 1;
		for (int i = 0; i < array.length; i++) {
			checkAr[array[i]] = 1;
			lastIndex = this.check(checkAr, i, lastIndex);
			if (lastIndex == goal) {
				return i;
			}
		}
		return resutlInt;
	}

	public int check(int[] checkAr, int i, int lastIndex) {
		if (lastIndex != 0) {
			for (int j = lastIndex; j < i; j++) {
				if (checkAr[j] != 0) {
					lastIndex = j;
				} else {
					break;
				}
			}
		} else {
			for (int j = 0; j < i; j++) {
				if (checkAr[j] != 0) {
					lastIndex = j;
				} else {
					break;
				}
			}
		}
		return lastIndex;
	}
}
~~~

## MissingInteger


~~~java
public class Test2 {
	static public void main(String args[]) {
		int A[] = {1,1,2,3,4,5,5,5};
		System.out.println(new Test2().solution( A));
	}

	public int solution(int[] A) {
		return this.test1(A);
    }
	
	public int test1(int[] array){
		int length = array.length;
		int[] checkAr = new int[1000000];
		checkAr[0]= array[0];
		for(int i=0; i< length; i++){
			if(array[i]<0)	return 1;
			checkAr[array[i]] = 1;
		}
		for(int i=0; i<1000000; i++){
			if(checkAr[i]==0)	return i;
		}
		return length+1;
	}
}
~~~

