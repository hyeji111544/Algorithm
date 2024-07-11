# 알고리즘 내용 정리

## 알고리즘이란?
- 특정 문제를 해결하기 위해 정해진 일련의 절차나 방법을 말한다.

<details>

<summary>Sorting</summary>

<details>

<summary> 버블 정렬 Bubble Sort</summary>

### 소개
인접한 두 요소를 비교하여 정렬하는 가장 단순한 정렬 알고리즘 중 하나로, 각 패스마다 가장 큰 요소가 배열의 끝으로 이동한다.

### 특징
- 시간 복잡도: O(n^2)
- 안정 정렬: 동일한 값의 요소들이 정렬 후에도 상대적인 순서가 유지된다.

### 예제

```java
public class BubbleSort {
    public static void bubbleSort(int[] arr) {
        int n = arr.length;
        for (int i = 0; i < n-1; i++) {
            for (int j = 0; j < n-i-1; j++) {
                if (arr[j] > arr[j+1]) {
                    // swap arr[j] and arr[j+1]
                    int temp = arr[j];
                    arr[j] = arr[j+1];
                    arr[j+1] = temp;
                }
            }
        }
    }

    public static void main(String[] args) {
        int[] arr = {64, 34, 25, 12, 22, 11, 90};
        bubbleSort(arr);
        System.out.println("Sorted array:");
        for (int i : arr) {
            System.out.print(i + " ");
        }
    }
}

```

</details>

<details>

<summary> 선택 정렬 Selection Sort</summary>

### 소개
배열에서 가장 작은 요소를 찾아 첫 번째 위치와 교환하고, 다음 작은 요소를 찾아 두 번째 위치와 교환하는 방식으로 정렬한다.

### 특징
- 시간 복잡도: O(n^2)
- 불안정 정렬: 동일한 값의 요소들이 정렬 후에 상대적인 순서가 바뀔 수 있습니다.

### 예제

```java
public class SelectionSort {
    public static void selectionSort(int[] arr) {
        int n = arr.length;
        for (int i = 0; i < n-1; i++) {
            int min_idx = i;
            for (int j = i+1; j < n; j++) {
                if (arr[j] < arr[min_idx]) {
                    min_idx = j;
                }
            }
            // Swap the found minimum element with the first element
            int temp = arr[min_idx];
            arr[min_idx] = arr[i];
            arr[i] = temp;
        }
    }

    public static void main(String[] args) {
        int[] arr = {64, 25, 12, 22, 11};
        selectionSort(arr);
        System.out.println("Sorted array:");
        for (int i : arr) {
            System.out.print(i + " ");
        }
    }
}


```


</details>

<details>

<summary> 삽입 정렬 Insert Sort</summary>

### 소개
배열을 두 부분으로 나누고, 정렬된 부분에 요소를 하나씩 삽입하여 정렬하는 방식이다.

### 특징
- 시간 복잡도: O(n^2)
- 안정 정렬: 동일한 값의 요소들이 정렬 후에도 상대적인 순서가 유지

### 예제

```java
public class InsertionSort {
    public static void insertionSort(int[] arr) {
        int n = arr.length;
        for (int i = 1; i < n; ++i) {
            int key = arr[i];
            int j = i - 1;
            while (j >= 0 && arr[j] > key) {
                arr[j + 1] = arr[j];
                j = j - 1;
            }
            arr[j + 1] = key;
        }
    }

    public static void main(String[] args) {
        int[] arr = {12, 11, 13, 5, 6};
        insertionSort(arr);
        System.out.println("Sorted array:");
        for (int i : arr) {
            System.out.print(i + " ");
        }
    }
}


```

</details>

<details>

<summary> 병합 정렬 Merge Sort</summary>

### 소개
분할 정복 알고리즘의 일종으로, 배열을 반으로 나누고 각각을 정렬한 후 병합하여 정렬
이 과정은 **재귀호출**을 통해 이루어진다.

합병 정렬은 다음의 단계들로 이루어져 있는데.

- **분할(Divide)**: 입력 배열을 같은 크기의 2개의 부분 배열로 **분할**한다.
- **정복(Conquer)**: 부분 배열을 **정렬**합니다. 부분 배열의 크기가 조금 큰 편이라고 생각이 들면 재귀 호출을 통해 다시 분할 정복 방법을 진행한다.

### 특징
- 시간 복잡도: O(n log n)
- 안정 정렬: 동일한 값의 요소들이 정렬 후에도 상대적인 순서가 유지

### 예제

```java
public class MergeSort {
    public static void mergeSort(int[] arr, int l, int r) {
        if (l < r) {
            int m = (l + r) / 2;
            mergeSort(arr, l, m);
            mergeSort(arr, m + 1, r);
            merge(arr, l, m, r);
        }
    }

    public static void merge(int[] arr, int l, int m, int r) {
        int n1 = m - l + 1;
        int n2 = r - m;

        int[] L = new int[n1];
        int[] R = new int[n2];

        for (int i = 0; i < n1; ++i)
            L[i] = arr[l + i];
        for (int j = 0; j < n2; ++j)
            R[j] = arr[m + 1 + j];

        int i = 0, j = 0;
        int k = l;
        while (i < n1 && j < n2) {
            if (L[i] <= R[j]) {
                arr[k] = L[i];
                i++;
            } else {
                arr[k] = R[j];
                j++;
            }
            k++;
        }

        while (i < n1) {
            arr[k] = L[i];
            i++;
            k++;
        }

        while (j < n2) {
            arr[k] = R[j];
            j++;
            k++;
        }
    }

    public static void main(String[] args) {
        int[] arr = {12, 11, 13, 5, 6, 7};
        mergeSort(arr, 0, arr.length - 1);
        System.out.println("Sorted array:");
        for (int i : arr) {
            System.out.print(i + " ");
        }
    }
}


```

</details>

<details>

<summary> 퀵 정렬 Quick Sort</summary>

### 소개
분할 정복 알고리즘의 일종으로, 피벗을 기준으로 배열을 나누고 각각을 정렬하는 방식

### 특징
- 시간 복잡도: 평균 O(n log n), 최악의 경우 O(n^2)
- 불안정 정렬: 동일한 값의 요소들이 정렬 후에 상대적인 순서가 바뀔 수 있다.

### 예제

```java
public class QuickSort {
    public static void quickSort(int[] arr, int low, int high) {
        if (low < high) {
            int pi = partition(arr, low, high);
            quickSort(arr, low, pi - 1);
            quickSort(arr, pi + 1, high);
        }
    }

    public static int partition(int[] arr, int low, int high) {
        int pivot = arr[high];
        int i = (low - 1);
        for (int j = low; j < high; j++) {
            if (arr[j] < pivot) {
                i++;
                int temp = arr[i];
                arr[i] = arr[j];
                arr[j] = temp;
            }
        }
        int temp = arr[i + 1];
        arr[i + 1] = arr[high];
        arr[high] = temp;
        return i + 1;
    }

    public static void main(String[] args) {
        int[] arr = {10, 7, 8, 9, 1, 5};
        quickSort(arr, 0, arr.length - 1);
        System.out.println("Sorted array:");
        for (int i : arr) {
            System.out.print(i + " ");
        }
    }
}


```

</details>


</details>
