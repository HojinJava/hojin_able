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
    if(a.length==1) {
        return a[0];
    }
    int collspanArray[] = this.collspanArray(a);
    if(collspanArray.length==1) {
        //모두 같은 부호
        Arrays.sort(a);
        if(a[a.length-1] > 0) {
            return this.sumArray(a);
        }else {
            return a[0];
        }
    }else if(collspanArray.length==2){
        //음수 하나 양수 하나
        Arrays.sort(collspanArray);
        return collspanArray[1];
    }
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
- [채점결과링크](https://app.codility.com/demo/results/trainingKYRW93-5TD/?showingAll=1)

| Task Score | Correctness | Performance |
| ---------- | ----------- | ----------- |
| 46%        | 50%         | 40%         |

## 해결 해야되는 점

* 길이가 1인경우 예외처리
* { -2, 1, -2} 인 경우 처리
* 나머지 정확도 향상
* 시간 복잡도 해결