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
