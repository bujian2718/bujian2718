#include<stdio.h>
#include<windows.h> 
int menu_select();
void BubbleSort();
void select_sort();
void insert_sort(int arr[],int size);
void shellSort(int *a,int n);
void quick_sort(int arr[],int left,int right);
int menu_out;		//定义一个返回上一级菜单 
int main()
{
	while(1)
	{
		switch(menu_select())
		{
			case 1:
				system("cls");
				menu_out=1;				
				printf("这是冒泡排序\r\n"); 
				/*
				执行的功能函数
				*/
				BubbleSort();
				printf("输入0返回上一级菜单：\r\n"); 
				while(menu_out)			//只有当键盘输入为0时，才退出当前菜单 
				scanf("%d",&menu_out); //否则一直循环获取键盘输入 
				system("cls");
				break;
			case 2:
				system("cls");
				menu_out=1;
				printf("这是选择排序\r\n");
				/*
				执行的功能函数
				*/
				select_sort();
				printf("输入0返回上一级菜单：\r\n"); 
				while(menu_out)
				scanf("%d",&menu_out);
				system("cls");
				break;
			case 3:
				system("cls");
				menu_out=1;
				printf("这是快速排序\r\n");
				/*
				执行的功能函数
				*/
				{
				int n,i;
				printf("输入要排序的数个数\n");
				scanf("%d",&n);
				int arr[n];
				printf("输入要排序的数\n"); 
				for(int i=0;i<n;i++)
					scanf("%d",&arr[i]);
				int left;
				left=0;
				int right;
				right=n-1;
				quick_sort(arr,left,right);
				for(i=0;i<n;i++)
				printf("%d ",arr[i]);
				printf("\n");
				}
				printf("输入0返回上一级菜单：\r\n"); 
				while(menu_out)
				scanf("%d",&menu_out);
				system("cls");
				break;
			case 4:
				system("cls");
				menu_out=1;
				printf("这是插入排序\r\n");
				/*
				执行的功能函数
				*/
				{int n;
				printf("输入要排序的数个数\n");
				scanf("%d",&n);
				int arr[n];
				printf("输入要排序的数\n"); 
				for(int i=0;i<n;i++)
					scanf("%d",&arr[i]);
				insert_sort(arr,n);
				}
				printf("输入0返回上一级菜单：\r\n"); 
				while(menu_out)
				scanf("%d",&menu_out);
				system("cls");
				break;
			case 5:
				system("cls");
				menu_out=1;
				printf("这是希尔排序\r\n");
				/*
				执行的功能函数
				*/
				{
				int n,i;
				printf("输入要排序的数个数\n");
				scanf("%d",&n);
				int arr[n];
				printf("输入要排序的数\n"); 
				for(int i=0;i<n;i++)
					scanf("%d",&arr[i]);
				shellSort(arr,n);
				for (i = 0; i < n; i++) {
        			printf("%d ",arr[i]);
				}
				printf("\n");
				}
				printf("输入0返回上一级菜单：\r\n"); 
				while(menu_out)
				scanf("%d",&menu_out);
				system("cls");
				break;
			 case 6:
				return 0;
				break;
			default:break;
		}
	} 
	return 0;
}
int menu_select(void)
{
	int select;
	printf("输入对应标号选择排序方法：\r\n"); 
	printf("1、冒泡排序\r\n");
	printf("2、选择排序\r\n");
	printf("3、快速排序\r\n");
	printf("4、插入排序\r\n");
	printf("5、希尔排序\r\n");
	printf("6、退出程序\r\n");
	scanf("%d",&select);
	return select;
}
void BubbleSort() {
	int i = 0,n,j;
	printf("输入要排序的数个数\n");
	scanf("%d",&n);
	int arr[n];
	printf("输入要排序的数\n"); 
	for(i=0;i<n;i++)
		scanf("%d",&arr[i]);
	for (i = 0; i < n; i++) {
		int j = 0;
		for (j = 0; j < n- 1 - i; j++) { 
			if (arr[j] > arr[j + 1]) {
                // 两数进行交换
				int tmp = arr[j];
				arr[j] = arr[j + 1];
				arr[j + 1] = tmp;
			}
		}
	}
	for(i=0;i<n;i++)
		printf("%d ",arr[i]);
		printf("\n");
}
void select_sort()
{
	int i=0,j=0,k=0,n;
	printf("输入要排序的数个数\n");
	scanf("%d",&n);
	int arr[n];
	printf("输入要排序的数\n"); 
	for(i=0;i<n;i++)
		scanf("%d",&arr[i]);
	for(i=0;i<n;i++){
		k=i;
		for(j=i+1;j<n;j++){
			if(arr[k]<arr[j]){
				k=j;
			}

		}
		if(k!=i){
			int tmp=arr[k];
			arr[k]=arr[i];
			arr[i]=tmp;
		}
	}
	
	for(i=n-1;i>=0;i--)
		printf("%d ",arr[i]);
		printf("\n");
}
void quick_sort(int arr[],int left,int right)
{
	int i;
	if(left>=right){
		return;
	}
	int key=arr[left];
	int begin=left;
	int end=right;
	while(begin!=end){
		while(begin<end && arr[end]>=key){
			end--;
		}
		if(end>begin){
			arr[begin]=arr[end];
		}
		while(begin<end && arr[begin]<=key){
			begin++;
		}
		if(begin<end){
			arr[end]=arr[begin];
		}
	}
	arr[begin]=key;
	quick_sort(arr,left,begin-1);
	quick_sort(arr,begin+1,right);
}
void insert_sort(int arr[],int size)
{
	int i=0,j=0;
	int tmp=0;
	for(i=1;i<size;i++){
		tmp=arr[i];
		j=i;
		while(j>0 && arr[j-1]>tmp){
			arr[j]=arr[j-1];
			j--;
		}
		arr[j]=tmp;
	}
		for(i=0;i<size;i++)
		printf("%d ",arr[i]);
		printf("\n");
}
void shellSort(int *a,int n){

    int i,j,k,gap;
    for (gap = n / 2; gap > 0; gap = gap / 2) { //步长
        for (i = 0; i < gap; i++) {  
		//直接插入排序的次数；在每个分组中需要进行几次直接插入排序；
            //开始进行插入排序，每次加gap的步长；
            for (j = i + gap; j < n; j = j + gap) {
                if (a[j] < a[j - gap]) {

                    //保存后面的值；
                    int temp = a[j];
                    for (k = j - gap; k >= 0 && a[k] > temp; k = k - gap) {
                        //先把前面的数往后移；
                        a[k + gap] = a[k];
                    }
                    a[k + gap] = temp;

                }
            }

        }
    }

}
