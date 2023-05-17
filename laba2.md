# Сортировки

## Шейкерная сортировка

### Проход слева на право
```
bool left_right(int arr[], int n){
    bool flag = 0;
    for(int i = 0; i<n-1; ++i){

        if(arr[i+1]>arr[i]){
            int c = arr[i];
            arr[i]=arr[i+1];
            arr[i+1]=c;
            flag = 1;
    }
    }
    return(flag);
}
```

### Проход справа на лево
```
bool right_left(int arr[], int n){
    bool flag = 0;
    for(int i = n-2; i>0; --i){
        if(arr[i]>arr[i-1]){
            int c = arr[i];
            arr[i]=arr[i-1];
            arr[i-1]=c;
            flag = 1;
    }
    }
    return(flag);
}
```

### Шейкерная сортировка
```
void sheik+sort(int arr[], int n){
    while (right_left(a,n) || left_right(a,n)){
        left_right(a,n);
        right_left(a,n);
    }
}
```
### Проверка сортировки
```
bool check(int arr[], int n){
    bool flag =0;
    int counter=0;
    for(int i =0; i<n-1; ++i){
        if(arr[i]<arr[i+1]){
            return(flag);
        }
    }
    for(int i=0; i<n; ++i){
        for(int j=0; j<n; ++j){
            if(arr[i]==arr[j]){
                counter=counter+1;
                break;
            }
        }
    }
    if(counter==n){
        flag=1;
    }
    return(flag);
}
```

## Сортировка расчёской

### Проверка порядка
```
int check_order(int arr[], int n, int gap){
int change =0;
for(int i =0; i<n-gap; ++i){
    if(arr[i]<arr[i+gap]){
        int c = arr[i];
        arr[i]=arr[i+gap];
        arr[i+gap]=c;
        change = change + 1;
    }
}
return(change);
}
```

### Сортировка расчёской
```
int rasch(int arr[],int n){
bool swap =1;
int gap = n;
int changes =0;
while(swap || gap>1){
        swap =0;
        gap = gap/2;
        if(gap<1){
            gap=1;
        }
    check_order(arr,n,gap);
    if(check_order(arr,n,gap)!=0){
        changes = changes + check_order(arr,n,gap);
        swap =1;
    }
}
return(changes);
}
```

### Асимптотика

![](/images/image/rasch(time).png) 

Зависимость от времени.

![](/images/image/rp.png)

Зависимость от перестановок.

# Сортировка Шелла

## Первый пункт

```
void insertionSort(int a[], int n)
{
    for(int gap = n/2; gap>0; gap/=2){

        for(int i =gap; i<n; ++i){
            int temp = a[i];
            for(int j =i-gap; j>=0 && a[j]<temp; j-=gap){

                a[j+gap]=a[j];
                a[j]=temp;
                temp = a[j];

            }

        }
    }
}
```
## Асимптотика

![](/images/image/shell.png)

![](/images/image/shell(log).png)

Логарифмический масштаб, O(n^1,52).

# сортировка Хиббарда
```
void HibbardSort(int a[], int n, int deg)
{
    int gap;


        for(; deg>0; --deg){
            int gap = 2^(deg) - 1;
            for(int i =gap; i<n; ++i){
            int temp = a[i];
            for(int j =i-gap; j>=0 && a[j]<temp; j-=gap){

                a[j+gap]=a[j];
                a[j]=temp;
                temp = a[j];

            }

        }

    }
}
```

## Асимптотика 

![](/images/image/Hibbard1.png)


![](/images/image/hibbard.png)

Логарифмический масштаб, O(n^1,7)

# Сортировка Фибоначчи

```
void FibSort(int a[], int n, std::vector <int> vect){
    int size_posl = vect.size();

    for(int gap: vect){

        for(int i =gap; i<n; ++i){
            int temp = a[i];
            for(int j =i-gap; j>=0 && a[j]<temp; j-=gap){

                a[j+gap]=a[j];
                a[j]=temp;
                temp = a[j];

            }

        }
    }
}
```

## Асимптотика

![](/images/image/Fibsort.png)


![](/images/image/Fibsort_log.png)

Логарифмический масштаб, O(n^1,9)

Shell: O(n^1,52) Hibbard: O(n^1,7) Fib: O(n^1,9) Странно, непонятно, возможно связано с архитектурой процессора.
