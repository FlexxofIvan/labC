# Поиск

## Измерение времени
```
int main(){
std :: cin >> n;
int value[] = {100,200,400,800,1600,3200,5000,7000,10000,15000,20000,
25000,35000,45000,60000,75000,95000,115000,140000,165000,
195000,225000,260000,295000,335000,375000,420000,465000,500000};
int linear_time[29];
int k =0;
for(int rate: value){
int a[rate];
for(int j =0; j<rate; ++j){
a[j]=j;
}
auto begin = std :: chrono :: steady_clock :: now ( );
for ( int j = 0; j<100000; ++j ){
f(a,rate);
}
auto end = std :: chrono :: steady_clock :: now ( );
auto time_span =std :: chrono :: duration_cast<std :: chrono :: microseconds >(end - begin );
std :: cout << "\n";
std :: cout << k<<rate<<"linear search: ";
std :: cout << time_span.count ( ) << ", ";
linear_time[k] = time_span.count ( );
++k;
}
}
```
## Используемые библиотеки

```
#include <iostream>
#include <chrono>
#include <random>
```

## Функция обычного поиска

```
int n;
int search(int arr[],int size){
    for(int i =0; i<size; ++i){
        if (arr[i]==n){
            return(1);
        }
    }
    return(-1);
}
```

## Асимптотика
![](FlexxofIvan/labC/images/usr.png)
O(n)
# Бинарный поиск

```
int bin search(int arr[], int size) {
    int left = 0;
    int right = size-1;
    int mid = (right+left)/2;
    while(n != arr[mid]){
        mid = (left+right)/2;
        if(n<arr[mid]){
            right = mid;
        }else if(n>arr[mid]){
            left = mid;
        }
        if(left==right){
            return(-1);
        }
    }
    return(mid);
}
```

## Асимптотика
![](\images\bins.png)
O(log n) - работает быстрее обычного поиска.

# Сумма двух 
## Полный перебор
```
int sum_of_two(int arr[], int size){
for(int i=0; i<size; ++i){
    for(int j=0; j<size; ++j){
        if(arr[i]+arr[i+j+1]==n){
            return(0);
        }
    }
}
return(-1);
}
```
## Асимптотика

![](\images\sum2.png)
O(n^2) 
## Линейный поиск

```
int sum_of_two_lin(int arr[], int size){
int left = 0;
int right = size-1;
while(arr[right]+arr[left]!=n){
  if(arr[right]+arr[left]<n){
    left=left+1;
  }else if(arr[right]+arr[left]>n){
  right=right-1;
  }
  if(arr[right]+arr[left]==n){
    return(0);
  }
  if(right==l){
    return(1);
  }
}
return(-1);
}
```
 ## Асимптотика

![](\images\suml.png)
Действуя похожим образом как с бин поиском, можно улучшить скорость - O(n)
# Часто используемый аргумент

## Стратегия А

```
int str A(int arr[],int size, int n){

    for(int i =0; i<size; ++i){
        if (arr[i]==n and i!=0){ 
                int b = arr[0];
                int c = arr[i];
                a[0] = c;
                a[i] = b;
            return(1);
        if (a[0]==n and i==0){
            return(0);
        }
        }
    }
    return(-1);
}
```
### Равномерный поиск 

![](\images\Aravn.png)

### Неравномерный поиск

![](\images\Aneravn.png)

O(log n), вне зависимости от равномеррности поиска.
## Стратегия B

```
int strB(int arr[],int size, int n){

    for(int i =0; i<size; ++i){
        if (arr[i]==n and i!=0){
                int b = arr[i-1];
                int c = arr[i];
                arr[i-1] = c;
                arr[i] = b;
            return(1);
        if (arr[0]==n and i==0){
            return(0);
        }
        }
    }
    return(-1);
}
```

### Равномерный поиск
![](\images\Bravn.png)

### Неравномерный поиск
![](\images\Bneravn.png)

(log n), вне зависимости от равномеррности поиска.
## Стратегия С
```

int strC(int arr[], int counter[], int size, int n){

    for(int i =0; i<size; ++i){
        if(arr[i]==n){
          counter[i]=counter[i]+1; //увеличиваем счетчик i-ого элемента на 1
        }
        if(counter[i]>counter[i-1] and i!=0){ //если счётчик i-ого элемента больше счетчика i+1, тогда меняем местами элементы
            int v = a[i];
            int u =a[i-1];
            int s = b[i];
            int t = b[i-1];
            counter[i] = t;
            counter[i-1] = s;
            arr[i]= u;
            arr[i-1]= v;
        }
        }

    return(-1);
}
```
### Равномерный поиск
![](\images\Cravn.png)

### Неавномерный поиск
![](\images\Cneravn.png)

O(n), вне зависимости от равномерности поиска.

Вне зависимости от поиска асимптотика не меняется, однако на других устройствах получаются другие результаты, так что это может быть связано не с самой стратегией, а с железом. 
