## FrogJmp
~~~java
public class TestClass {

	public static void main(String[] args) {
		System.out.println(new TestClass().solution(10, 85,75));
	}

	public int solution(int X, int Y, int D) {
		int returnVal = 0;
		Y = Y-X;
		if(D > Y) {
			return 0;
		}else {
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

## TapeEquilibrium
~~~java
//오답노트
//1. min값을 주어진 조건이 아닌 total값으로 지정함
// total값으로 min값을 할 경우, 배열에 음수가 들어갈 경우 total값이 0이하가 나올수도 있기 대문에
// 음수가 들어간 배열에서는 정확한 값이  안나올 수 있다.
public class Test {
	static public void main(String args[]){
		int A[] = {-1,-2,-3,3,4,13,10,0};
		System.out.println(new Test().solution(A));
	}

	public int solution(int[] A) {
		//1. 배열의 총 합을 구한다.
		//2. A[0]~ A[p-1]까지의 합을 구한다.
		//3. (1) - (2)에서  min 값을 찾는다.


		int totalSum = 0;
		int indexPSum = 0;
		int indexNSum = 0;
		int aLenght = A.length;
		int min = 1001;
		for(int i=0; i< aLenght; i++){
			totalSum += A[i];
		}

		for(int i=0; i< aLenght-1; i++){
			for(int j=0; j< i+1; j++){
				indexPSum += A[j];
			}
			indexNSum = totalSum - indexPSum;
			if(min > Math.abs(indexNSum - indexPSum) ){
				min = Math.abs(indexNSum - indexPSum);
			}
			indexPSum = 0;
			indexNSum = 0;
		}
		return min;
    }
}


~~~

