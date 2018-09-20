## MaxSliceSum
# Problem Link
- [Codility-Lesson09-[MaxSliceSum](https://app.codility.com/programmers/lessons/9-maximum_slice_problem/max_slice_sum/)
 ## 접근 방법
### 1차
- 연속된 배열이 같은 부호 일 경우 하나로 합친다.
- 맨처음이 음수일 경우는 버린다.
- 맨처음(양수)값을 max값으로 지정 한다.
- 다음 음수 값 + 양수 값이 +일 경우 max값을 변경 한다.
- 2중 for문으로 가장 큰 max 값을 찾아본다.
 #### 코드 (테스트케이스를 제외한)
```java
public int solution(int[] a) {
    if(a.length==1) return a[0];

    int collspanArray[] = this.collspanArray(a);

    if(collspanArray.length==1) return this.returnValWhereLenghIsOne(a);

    if(collspanArray.length==2) return this.returnValWhereLenghIsTwo(collspanArray);

    collspanArray = this.deleteFirstMinusElement(collspanArray);
    collspanArray = this.deleteLastMinusElement(collspanArray);

    if(collspanArray.length==1) return collspanArray[0];
    System.out.println(Arrays.toString(collspanArray));
    return this.returnValWhereLenghTwoUp_2(collspanArray);

}
//음수 하나 양수 하나
public int returnValWhereLenghIsTwo(int array[]) {
    Arrays.sort(array);
    return array[1];
}
//짝꿍끼리 더했을 때, 0보다 크면 합치면 되는거 아닌가???

//음수를 만났을 때
//		이전의 합이 더 클 경우는 더한다
//		아닐경우 더할필요가 없다

public int returnValWhereLenghTwoUp_2(int collspanArray[]) {
    int beforeSum = 0;

    int plusVal = 0;
    int minusVal = 0;

    int nowSum = 0;

    int max = 0;
    for(int i=0; i<collspanArray.length-1; i+=2) {
        plusVal = collspanArray[i];
        minusVal = collspanArray[i+1];

        nowSum = plusVal + minusVal;

        System.out.print("i::"+i+", nowSum::"+nowSum);
        System.out.println(", max:::"+max+", beforeSum::"+beforeSum);
        if(nowSum < 0) {
            if(  (beforeSum + nowSum) > 0 ) {
                max += nowSum;
                beforeSum += nowSum;
            }else {
                //이전까지 데이터는 필요 없다.
                max = 0;
                beforeSum = 0;
            }

        }else {
            max += nowSum;
            beforeSum += nowSum;
        }

    }
    return max;
}
public int returnValWhereLenghTwoUp(int collspanArray[]) {
    int tempSum = 0;
    int max = collspanArray[0];
    int tempRangeSum = 0;
    for(int i=0; i<collspanArray.length-1; i++) {
        tempSum = collspanArray[i];
        for(int j=i+1; j<collspanArray.length; j+=2) {
            tempRangeSum = this.getRangeSum(collspanArray, j);
            if(tempRangeSum > max) {
                max = tempRangeSum;
            }else if(tempSum+ tempRangeSum > max){
                max = tempSum+tempRangeSum;
            }
        }
    }
    return max;
}
public int returnValWhereLenghIsOne(int array[]) {
    Arrays.sort(array);
    if(array[array.length-1] > 0) {
        return this.sumArray(array);
    }else {
        return array[0];
    }
}
public int[] deleteFirstMinusElement(int array[]) {

    if(array[0] < 0) {
        int returnArray[] = new int[array.length-1];
        for(int i=1; i<array.length;i++) {
            returnArray[i-1] = array[i];
        }
        return returnArray;
    }
    return array;
}

public int[] deleteLastMinusElement(int array[]) {
    if(array[array.length-1] < 0) {
        return Arrays.copyOf(array, array.length-1);
    }
    return array;
}

public int sumArray(int array[]) {
    int sum = 0;
    for(int val : array) {
        sum += val;
    }
    return sum;
}
public int getRangeSum(int array[], int start) {

    if(start == array.length-1) {
        return array[start];
    }else {
        return array[start] + array[start+1];
    }
}

//연속된 인덱스가 같은 부호 일 경우 하나로 합친다.
//결과 배열 : 연속된 배열의 값은 서로 다른 부호 이다.
public int[] collspanArray(int[] array) {
    int[] temp = new int[array.length];
    int tempSum = 0;
    int nowVal = 0;
    int nextVal = 0;
    int resultIndex = 0;

    //같으면 합치고, 다르면 배열에 추가한다.
    for(int i=0; i<array.length-1; i++) {
        nowVal = array[i];
        nextVal = array[i+1];
        tempSum = nowVal;

        //같은 부호 일 경우는 합친다.
        while((nowVal * nextVal) > 0) {
            i++;
            if(i == array.length-1) {
                break;
            }
            nowVal = array[i];
            nextVal = array[i+1];
            tempSum += nowVal;
        }

        //i가 마지지막 일 경우는 같은 부호
        //i가 마지막-2일 경우는 다른 부호
        if(i == array.length-1) {
            tempSum += array[i];
            temp[resultIndex++] = tempSum;
        }else if(i == array.length-2){
            temp[resultIndex++] = tempSum;
            temp[resultIndex++] = array[i+1];
        }else {
            temp[resultIndex++] = tempSum;
            tempSum = 0;
        }
    }
    int result[] = new int[resultIndex];
    for(int i=0; i<resultIndex;i++) {
        result[i] = temp[i];
    }
    return result;
}
```
 ## 채점 결과
- [채점결과링크](https://app.codility.com/demo/results/trainingG7EP8X-47U/?showingAll=1)

| Task Score | Correctness | Performance |
| ---------- | ----------- | ----------- |
| 69%        | 87%         | 40%         |

## 해결 해야되는 점

* 나머지 정확도 향상	

  * 로직

    * 선택된 양수값은 max가 될 수 있다.

    * 선택된 양수값 + 다음 음수값을 더한다

      * 양수 일 경우

        * 현재 값 + 다음 양수가 max

        * beforeSum에 값을 삽입한다.

      * 음수 일 경우

        * beforeSum과 "+" 연산을 한다.
          * 결과가 음수 일 경우
            * 버린다.
          * 결과가 양수 일 경우
            * beforeSum += nowSum

    * beforeSum 과 max를 비교한다

      * max가 더  작을 경우 max값 변경

  * returnValWhereLenghTwoUp_2()

    * 첫번째 선택된 양수 값이 max값이다.
      * max값을 저장하는 배열을 생성한다.
    * 양수 + 음수를 했을 경우, beforeSum에 저장을 한다.
    * 
* 시간 복잡도 해결
* 쉽게 해결 할 수 있는 방법이 있다고 한다. 힌트 : 뒤를 정한다.
* 위 방법으로 해결 못함 진행중