# merge-sort
merge sort algo
#include <stdio.h>
#define max 100

void merge(int arr[max],int low,int mid,int high)
{
    int temp[max],left,right,i=0;
    left=low;
    right=mid+1;
    while(left<=mid && right<=high){
        if(arr[left]<=arr[right]){
            temp[i]=arr[left];
            left++;
            i++;
        }
        else{
            temp[i]=arr[right];
            right++;
            i++;
        }
    }
    while(left<=mid){
        temp[i]=arr[left];
        left++;
        i++;
    }
    while(right<=high){
        temp[i]=arr[right];
        right++;
        i++;
    }
    for(i=low;i<=high;i++)
    {
        arr[i]=temp[i-low];
    }
}

void mergesort(int arr[max],int low,int high)
{
    if(low>=high)
    return;
    int mid;
    mid=(low+high)/2;
    mergesort(arr,low,mid);
    mergesort(arr,mid+1,high);
    merge(arr,low,mid,high);
}

int main() {
   int arr[max],n,i;
   printf("enter the no of elements\n");
   scanf("%d",&n);
   printf("enter the elements\n");
   for(i=0;i<n;i++)
   {
       scanf("%d",&arr[i]);
   }
   printf("the unsorted array is\n");
   for(i=0;i<n;i++)
   {
       printf("%d ",arr[i]);
   }
   mergesort(arr,0,n);
   printf("\nthe sorted array is\n");
   for(i=1;i<=n;i++)
   {
      printf("%d ",arr[i]);
   }
    return 0;
}
