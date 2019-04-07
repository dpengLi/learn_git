just for learning git!

/**
 *快排代码
 */
#include <stdio.h>
void swap(int *arr, int low, int high)
{
	int temp = arr[low];
	arr[low] = arr[high];
	arr[high] = temp;
}

int partition(int *arr, int low, int high)
{
	int pilotKey = arr[low];
	while(low < high)
	{
		while((low<high) && (arr[high] >= pilotKey))
			high--;
		swap(arr, low, high);
		
		while((low < high) && (arr[low] <= pilotKey))
			low++;
		swap(arr, low, high);		
	}
	return low;
}

void quickSort(int *arr, int low, int high)
{
	int pilot;
	if(low < high)
	{
		pilot = partition(arr, low, high);
		quickSort(arr, low, pilot-1);
		quickSort(arr, pilot+1, high);
	}	
}

int main()
{
    int data_in[10] = {10, 19, 8, 7, 60, 5, 4, 73, 2, 101};
    quickSort(data_in, 0, 9);
	for(int i=0;i<10;i++)
		printf("%d ", data_in[i]);
   return 0;
}