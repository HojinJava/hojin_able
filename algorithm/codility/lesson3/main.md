## FrogJmp
~~~java
public class Test4 {
	static public void main(String args[]) {
		System.out.println(new Test4().solution(1,1,3));
	}

	public int solution(int X, int Y, int D) {
		int returnVal = 0;
		Y = Y-X;
		if(D > Y) {
			if(Y==0){
				return 0;
			}else{
				return 1;
			}
			
		}else{
			returnVal = Y%D;
			if(returnVal ==0) {
				return (Y/D);
			}else {
				return (Y/D)+1;
			}
		}
    }
}
~~~

## TapeEquilibrium (score : 100)
~~~java
//오답노트
//1. min값을 주어진 조건이 아닌 total값으로 지정함
// total값으로 min값을 할 경우, 배열에 음수가 들어갈 경우 total값이 0이하가 나올수도 있기 대문에
// 음수가 들어간 배열에서는 정확한 값이  안나올 수 있다.
public class Test3 {
	static public void main(String args[]) {
		int A[] = {1,1 };
		System.out.println(new Test3().solution(A));
	}

	public int solution(int[] A) {
		// 1. 배열의 총 합을 구한다.
		// 2. A[0]~ A[p-1]까지의 합을 구한다.
		// 3. (1) - (2)에서 min 값을 찾는다.

		int totalSum = 0;
		int aLenght = A.length;
		int min = 100001;
		
		int leftSum = 0;
		int rightSum = 0;
		for (int i = 0; i < aLenght; i++) {
			totalSum += A[i];
		}
		for (int i = 0; i < aLenght-1; i++) {
			leftSum += A[i];
			rightSum = totalSum-leftSum;
			if(min  > Math.abs(leftSum-rightSum )){
				min = Math.abs(leftSum-rightSum);
			}
		}
		return min;
	}
}


~~~

