QuickSort
=========
QuickSort,Divide and Conquer algoritmasına dayanan bir elemanı pivot olarak seçip pivotu doğru konuma koyup yerleştiren bir algoritmadır.

*   Yeni bir array oluşmuyor array’e sorting yapıyoruz bundan dolayı void’dir.

![photo1](https://github.com/alpersener/QuickSort/blob/master/photo1.png)

Time Complexity
===============

![photo2](https://github.com/alpersener/QuickSort/blob/master/photo2.png)


Notlar
======

1.  Not stable

2.  Array’lerde merge sort yerine quick sort daha mantıklı çünkü merge sort o(n) extra space kullanıyor(mix array yüzünden),quick sort’ta extra space’i recursion’dan geliyor extra space alınmıyor çünkü yeni bir array oluşturulmuyor

3.  Merge sortu linked list’lerde kullanmak daha mantıklı **(linked list’lerde contigious memory allocation olmadığı için)**


```

    package QuickSort;
    
    import java.util.Arrays;
    
    public class QuickSort {
        public static void main(String[] args) {
            int[] arr={5,4,3,2,1};
            sort(arr,0,arr.length-1);
            System.out.println(Arrays.toString(arr));
            //Arrays.sort(arr);
    
        }
    
        //yeni bir array oluşturmadan işlemleri yapıyorsak index'leri kullanmalıyız onlarda low high tarzı falan
        //bu örnekte low ve high değeri array'in hangi kısmı üzerinde çalışacağız onu bulmak için
        //end ve start indexi ise swap için
        static void sort(int[] nums,int low,int high){
            //low değeri high değerini geçerse dur
            if(low>=high)
                return;
            int s=low;
            int e=high;
            int mid=s+(e-s)/2;
            int pivot=nums[mid];
    
            while(s<=e){
                //zaten sorted ise swap yapmaması için
                while(nums[s]<pivot){
                    s++;
                }
                while(nums[e]>pivot){
                    e--;
                }
                if(s<=e){
                    int temp=nums[s];
                    nums[s]=nums[e];
                    nums[e]=temp;
    //                swap(nums,s,e);
                    s++;
                    e--;
                }
            }
            //pivot dogru index'te ise 2 tane ayrılmış olan array için sort işlemi yap recursion ile
            sort(nums,low,e);
            sort(nums,s,high);
    
        }
        static void swap(int[] arr,int first,int second){
            int temp=arr[first];
            arr[first]=arr[second];
            arr[second]=temp;
        }
    
    
    
    }
```
